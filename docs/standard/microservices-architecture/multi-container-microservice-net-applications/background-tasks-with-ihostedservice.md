---
title: Implémenter des tâches en arrière-plan dans les microservices avec IHostedService et la classe BackgroundService
description: Architecture des microservices .NET pour les applications .NET en conteneur | Implémenter des tâches en arrière-plan dans les microservices avec IHostedService et la classe BackgroundService
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 79ad437ef809486b3315de223697ac78109556ba
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105899"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a>Implémenter des tâches en arrière-plan dans les microservices avec IHostedService et la classe BackgroundService

Vous pouvez être amené à implémenter des tâches en arrière-plan et des travaux planifiés dans une application basée sur des microservices ou tout autre genre d’application. Toutefois, il existe une certaine différence quand vous utilisez une architecture de microservices. Vous pouvez implémenter un processus/conteneur de microservice unique pour héberger ces tâches en arrière-plan et adapter l’architecture à vos besoins. Vous pouvez même vérifier que cette architecture exécute une seule instance de ce processus/conteneur de microservice.

D’un point de vue générique, dans .NET Core, nous avons appelé les tâches de ce type des services hébergés, car il s’agit de services/d’une logique que vous hébergez dans votre hôte/application/microservice. Notez que dans ce cas, le service hébergé représente simplement une classe avec la logique de tâche en arrière-plan.

Depuis .NET Core 2.0, le framework fournit une nouvelle interface nommée <xref:Microsoft.Extensions.Hosting.IHostedService>, qui vous aide à implémenter facilement les services hébergés. L’idée de base est que vous pouvez inscrire plusieurs tâches en arrière-plan (services hébergés), qui s’exécutent en arrière-plan pendant que votre hôte web ou votre hôte est en cours d’exécution, comme le montre l’image ci-dessous.

![](./media/image26.png)

**Figure 8-25.** Utilisation d’IHostedService dans un WebHost et un Host

Notez la différence faite entre `WebHost` et `Host`. En ASP.NET Core 2.0, `WebHost` (classe de base implémentant `IWebHost`) est l’artefact d’infrastructure qui vous permet de fournir des fonctionnalités de serveur HTTP à votre processus, par exemple si vous implémentez une application web MVC ou un service d’API web. Il fournit toute la qualité de l’infrastructure en ASP.NET Core, ce qui vous permet d’utiliser l’injection de dépendances, d’insérer des intergiciels (middleware) dans le pipeline HTTP, etc. et d’utiliser précisément les `IHostedServices` pour les tâches en arrière-plan.

Toutefois, `Host` (classe de base implémentant `IHost`) est une nouveauté dans .NET Core 2.1. En fait, `Host` vous permet d’avoir une infrastructure similaire à celle que vous avez avec `WebHost` (injection de dépendances, services hébergés, etc.), mais dans ce cas précis, vous souhaitez simplement avoir un processus simple et plus léger en tant qu’hôte, sans lien avec les fonctionnalités MVC, d’API web ou de serveur HTTP.

Ainsi, vous pouvez créer un processus hôte spécialisé avec IHost pour prendre en charge les services hébergés et rien d’autre, par exemple un microservice destiné uniquement à héberger `IHostedServices`, ou vous pouvez étendre un `WebHost` ASP.NET Core existant, par exemple une API web ou une application MVC ASP.NET Core existante. 

Chaque approche a des avantages et des inconvénients selon vos besoins professionnels et de scalabilité. En fin de compte, si vos tâches en arrière-plan n’ont rien à voir avec le protocole HTTP (IWebHost), utilisez IHost dans .NET Core 2.1 quand cela est possible.

## <a name="registering-hosted-services-in-your-webhost-or-host"></a>Inscription de services hébergés sur WebHost ou Host

Examinons plus en détail l’interface `IHostedService`, car son utilisation est assez similaire dans `WebHost` ou `Host`. 

SignalR est un exemple d’artefact qui utilise des services hébergés, mais vous pouvez également l’employer pour des choses beaucoup plus simples, par exemple :

-   Tâche en arrière-plan qui interroge une base de données à la recherche des changements survenus
-   Tâche planifiée qui met à jour un cache périodiquement
-   Implémentation de QueueBackgroundWorkItem qui permet l’exécution d’une tâche sur un thread d’arrière-plan
-   Traitement des messages d’une file d’attente de messages en arrière-plan d’une application web, avec un partage des services communs tels que `ILogger`
-   Tâche en arrière-plan démarrée avec `Task.Run()`

Vous pouvez tout simplement décharger l’une de ces actions vers une tâche en arrière-plan basée sur IHostedService.

Pour ajouter un ou plusieurs `IHostedServices` dans `WebHost` ou `Host`, vous devez les inscrire via l’injection de dépendances standard dans un `WebHost` ASP.NET Core (ou dans `Host` au sein de NET Core 2.1). En fait, vous devez inscrire les services hébergés dans la méthode `ConfigureServices()` bien connue de la classe `Startup`, comme dans le code suivant d’un WebHost ASP.NET classique. 

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{            
    //Other DI registrations;

    // Register Hosted Services
    services.AddSingleton<IHostedService, GracePeriodManagerService>();
    services.AddSingleton<IHostedService, MyHostedServiceB>();
    services.AddSingleton<IHostedService, MyHostedServiceC>();
    //...
}
```

Dans ce code, le service hébergé `GracePeriodManagerService` correspond au code réel du microservice de commandes d’eShopOnContainers, alors que les deux autres ne sont que deux exemples supplémentaires.

L’exécution de la tâche en arrière-plan `IHostedService` est coordonnée avec la durée de vie de l’application (hôte ou microservice). Vous inscrivez des tâches quand l’application démarre, et vous pouvez effectuer des actions normales ou de nettoyage quand l’application s’arrête.

Sans utiliser `IHostedService`, vous pouvez tout de même démarrer un thread d’arrière-plan pour exécuter une tâche. La différence se situe précisément au moment de l’arrêt de l’application, quand le thread est simplement tué sans avoir eu l’occasion d’exécuter des actions de nettoyage normales.


## <a name="the-ihostedservice-interface"></a>Interface IHostedService

Quand vous inscrivez `IHostedService`, .NET Core appelle les méthodes `StartAsync()` et `StopAsync()` de votre type `IHostedService` durant le démarrage et l’arrêt de l’application, respectivement. Plus précisément, le démarrage est appelé une fois que le serveur a démarré et que `IApplicationLifetime.ApplicationStarted` est déclenché.

`IHostedService`, tel qu’il est défini en .NET Core, ressemble à ce qui suit.

```csharp
namespace Microsoft.Extensions.Hosting
{
    //
    // Summary:
    //     Defines methods for objects that are managed by the host.
    public interface IHostedService
    {
        //
        // Summary:
        // Triggered when the application host is ready to start the service.
        Task StartAsync(CancellationToken cancellationToken);
        //
        // Summary:
        // Triggered when the application host is performing a graceful shutdown.
        Task StopAsync(CancellationToken cancellationToken);
    }
}
```
Naturellement, vous pouvez créer plusieurs implémentations d’IHostedService et les inscrire auprès de la méthode `ConfigureService()` dans le conteneur d’injection de dépendances, comme nous l’avons déjà indiqué. Tous ces services hébergés démarrent et s’arrêtent avec l’application/le microservice.

En tant que développeur, vous êtes responsable de la prise en charge de l’action d’arrêt ou de vos services quand la méthode `StopAsync()` est déclenchée par l’hôte.

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a>Implémentation d’IHostedService avec une classe de service hébergé personnalisé dérivant de la classe de base BackgroundService

Créez entièrement votre classe de service hébergé personnalisé, et implémentez `IHostedService`, comme vous le faites quand vous utilisez .NET Core 2.0. 

Toutefois, comme la plupart des tâches en arrière-plan ont des besoins similaires en ce qui concerne la gestion des jetons d’annulation et les autres opérations classiques, .NET Core 2.1 fournit une classe de base abstraite très pratique, nommée BackgroundService.

Cette classe fournit le travail principal nécessaire à la configuration de la tâche en arrière-plan. Notez que cette classe fait partie de la bibliothèque .NET Core 2.1, vous n’avez donc pas besoin de l’écrire.

Toutefois, au moment de la rédaction de ce document, .NET Core 2.1 n’est pas encore publié. Ainsi, dans eShopOnContainers qui utilise .NET Core 2.0, nous incorporons simplement cette classe de manière temporaire à partir du dépôt open source .NET Core 2.1 (pas besoin d’une licence propriétaire, à part la licence open source) en raison de sa compatibilité avec l’interface IHostedService actuelle dans .NET Core 2.0. Une fois que .NET Core 2.1 sera disponible, il vous suffira de pointer vers le bon package NuGet.

Le code suivant est la classe de base BackgroundService abstraite implémentée dans .NET Core 2.1.

```csharp
// Copyright (c) .NET Foundation. Licensed under the Apache License, Version 2.0. 
/// <summary>
/// Base class for implementing a long running <see cref="IHostedService"/>.
/// </summary>
public abstract class BackgroundService : IHostedService, IDisposable
{
    private Task _executingTask;
    private readonly CancellationTokenSource _stoppingCts = 
                                                   new CancellationTokenSource();

    protected abstract Task ExecuteAsync(CancellationToken stoppingToken);

    public virtual Task StartAsync(CancellationToken cancellationToken)
    {
        // Store the task we're executing
        _executingTask = ExecuteAsync(_stoppingCts.Token);

        // If the task is completed then return it, 
        // this will bubble cancellation and failure to the caller
        if (_executingTask.IsCompleted)
        {
            return _executingTask;
        }

        // Otherwise it's running
        return Task.CompletedTask;
    }
    
    public virtual async Task StopAsync(CancellationToken cancellationToken)
    {
        // Stop called without start
        if (_executingTask == null)
        {
            return;
        }

        try
        {
            // Signal cancellation to the executing method
            _stoppingCts.Cancel();
        }
        finally
        {
            // Wait until the task completes or the stop token triggers
            await Task.WhenAny(_executingTask, Task.Delay(Timeout.Infinite,
                                                          cancellationToken));
        }

    }

    public virtual void Dispose()
    {
        _stoppingCts.Cancel();
    }
}
```

Quand vous effectuez une dérivation à partir de la classe de base abstraite précédente, grâce à l’implémentation héritée, vous devez simplement implémenter la méthode `ExecuteAsync()` dans votre propre classe de service hébergé personnalisé, comme dans le code simplifié suivant d’eShopOnContainers. Ce code interroge une base de données et publie des événements d’intégration dans le bus d’événements, le cas échéant.

```csharp
public class GracePeriodManagerService : BackgroundService
{        
    private readonly ILogger<GracePeriodManagerService> _logger;
    private readonly OrderingBackgroundSettings _settings;

    private readonly IEventBus _eventBus;

    public GracePeriodManagerService(IOptions<OrderingBackgroundSettings> settings,
                                     IEventBus eventBus,
                                     ILogger<GracePeriodManagerService> logger)
        {
            //Constructor’s parameters validations...       
        }

        protected override async Task ExecuteAsync(CancellationToken stoppingToken)
        {
            _logger.LogDebug($"GracePeriodManagerService is starting.");

            stoppingToken.Register(() => 
                    _logger.LogDebug($" GracePeriod background task is stopping."));

            while (!stoppingToken.IsCancellationRequested)
            {
                _logger.LogDebug($"GracePeriod task doing background work.");

                // This eShopOnContainers method is querying a database table 
                // and publishing events into the Event Bus (RabbitMS / ServiceBus)
                CheckConfirmedGracePeriodOrders();

                await Task.Delay(_settings.CheckUpdateTime, stoppingToken);
            }
            
            _logger.LogDebug($"GracePeriod background task is stopping.");

        }

        protected override async Task StopAsync (CancellationToken stoppingToken)
        {
               // Run your graceful clean-up actions
        }
}
```

Dans ce cas de figure spécifique à eShopOnContainers, le code exécute une méthode d’application qui interroge une table de base de données à la recherche de commandes ayant un état spécifique. Quand des changements sont appliqués, il publie les événements d’intégration via le bus d’événements (il peut s’agir de RabbitMQ ou d’Azure Service Bus). 

Bien entendu, vous pouvez exécuter une autre tâche en arrière-plan à la place.

Par défaut, le jeton d’annulation est défini avec un délai d’expiration de 5 secondes. Toutefois, vous pouvez changer cette valeur quand vous générez votre `WebHost` à l’aide de l’extension `UseShutdownTimeout` de `IWebHostBuilder`. Cela signifie que notre service est censé être annulé dans les 5 secondes, sinon il est tué de manière brusque.

Le code suivant change ce délai en le portant à 10 secondes.

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a>Diagramme de classes récapitulatif

L’image 8-26 suivante montre un récapitulatif visuel des classes et des interfaces impliquées dans l’implémentation d’IHostedServices.
 
![](./media/image27.png)

**Figure 8-26.** Diagramme de classes montrant les multiples classes et interfaces liées à IHostedService

### <a name="deployment-considerations-and-takeaways"></a>Éléments importants à retenir et considérations relatives au déploiement

Il est important de noter que la façon dont vous déployez votre `WebHost` ASP.NET Core ou votre `Host` .NET Core peut avoir un impact sur la solution finale. Par exemple, si vous déployez votre `WebHost` sur IIS ou sur un Azure App Service normal, votre hôte peut être arrêté en raison des recyclages de pools d’applications. Mais si vous déployez votre hôte en tant que conteneur dans un orchestrateur comme Kubernetes ou Service Fabric, vous pouvez contrôler le nombre garanti d’instances dynamiques de l’hôte. En outre, vous pouvez envisager d’autres approches liées au cloud, spécialement conçues pour ces scénarios, par exemple Azure Functions. 

Toutefois, même pour un `WebHost` déployé dans un pool d’applications, il existe des scénarios tels que le repeuplement ou le vidage du cache en mémoire de l’application, qui sont toujours applicables.

L’interface `IHostedService` fournit un moyen pratique de démarrer des tâches en arrière-plan dans une application web ASP.NET Core (dans .NET Core 2.0) ou dans n’importe quel processus/hôte (à partir de .NET Core 2.1 avec `IHost`). Le principal avantage est le suivant : grâce à l’annulation normale, vous pouvez nettoyer le code de vos tâches en arrière-plan quand l’hôte s’arrête.


#### <a name="additional-resources"></a>Ressources supplémentaires

-   **Génération d’une tâche planifiée avec ASP.NET Core/Standard 2.0** 

    [*https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html*](https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html)

-   **Implémentation d’IHostedService avec ASP.NET Core 2.0** 

    [*https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice*](https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice)

-   **Exemples d’hébergement ASP.NET Core 2.1** 

    [*https://github.com/aspnet/Hosting/tree/dev/samples/GenericHostSample*](https://github.com/aspnet/Hosting/tree/dev/samples/GenericHostSample)



>[!div class="step-by-step"]
[Précédent](test-aspnet-core-services-web-apps.md)
[Suivant](../microservice-ddd-cqrs-patterns/index.md)
