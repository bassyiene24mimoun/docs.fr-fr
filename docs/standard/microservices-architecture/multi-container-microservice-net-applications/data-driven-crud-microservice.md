---
title: Création d’un microservice CRUD simple piloté par les données
description: Architecture des microservices .NET pour les applications .NET en conteneur | Création d’un microservice CRUD simple piloté par les données
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: d99480c1b703bc46228e25f6acd7e7fbbcae6228
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106445"
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a>Création d’un microservice CRUD simple piloté par les données

Cette section explique comment créer un microservice simple devant effectuer des opérations de création, de lecture, de mise à jour et de suppression (CRUD) dans une source de données.

## <a name="designing-a-simple-crud-microservice"></a>Conception d’un microservice CRUD simple

La conception de ce type de microservice en conteneur est très simple. Le problème est peut-être simple à résoudre, ou l’implémentation n’est peut-être qu’une preuve de concept.

![](./media/image4.png)

**Figure 8-4**. Conception interne de microservices CRUD simples

Il peut s’agir, par exemple, du microservice de catalogue de l’exemple d’application eShopOnContainers. Ce type de service implémente toutes ses fonctionnalités dans un même projet d’API web ASP.NET Core, qui comprend des classes pour son modèle de données, sa logique métier et son code d’accès aux données. Il stocke également ses données associées dans une base de données qui exécute SQL Server (utilisée comme un conteneur à des fins de développement ou de test). Toutefois, il peut aussi s’agir d’un hôte SQL Server standard, comme illustré à la Figure 8-5.

![](./media/image5.png)

**Figure 8-5**. Conception d’un microservice CRUD simple piloté par les données

Lorsque vous développez ce type de service, vous avez seulement besoin [d’ASP.NET Core](https://docs.microsoft.com/aspnet/core/) et d’une API ou d’un outil ORM d’accès aux données, comme, par exemple, [Entity Framework Core](https://docs.microsoft.com/ef/core/index). Vous pouvez également générer automatiquement des métadonnées [Swagger](https://swagger.io/) par le biais de [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore), afin de fournir une description de votre service, comme l’explique la section suivante.

Notez que les serveurs de base de données, tels que SQL Server, qui sont situés dans un conteneur Docker constituent la solution idéale pour les environnements de développement. En effet, vous pouvez utiliser directement toutes vos dépendances, sans avoir à provisionner une base de données locale ou cloud. Ceci est très utile lorsque vous effectuez des tests d’intégration. Toutefois, pour les environnements de production, l’exécution d’un serveur de base de données dans un conteneur est déconseillée, car elle ne permet pas d’obtenir une haute disponibilité. Pour un environnement de production Azure, il est recommandé d’utiliser Azure SQL DB ou une autre technologie de base de données capable de fournir une haute disponibilité et une scalabilité importante. Par exemple, pour une approche NoSQL, vous pourriez utiliser DocumentDB.

Enfin, en modifiant les fichiers de métadonnées Dockerfile et docker-compose.yml, vous pouvez configurer la création de l’image de ce conteneur, c’est-à-dire, quelle image de base elle va utiliser, ainsi que les paramètres de conception, tels que le nom interne et externe, et les ports TCP. 

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a>Implémentation d’un microservice CRUD simple avec ASP.NET Core

Pour implémenter un microservice CRUD simple à l’aide de .NET Core et de Visual Studio, commencez par créer un projet d’API web ASP.NET Core simple (et exécutez-le sur .NET Core pour qu’il puisse s’exécuter sur un hôte Docker Linux), comme indiqué dans la Figure 8-6.

  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------
  ![](./media/image6.png)   ![](./media/image7.png)
  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------

**Figure 8-6**. Création d’un projet d’API web ASP.NET Core dans Visual Studio

Après avoir créé le projet, vous pouvez implémenter vos contrôleurs MVC comme vous le feriez dans n’importe quel autre projet d’API web, à l’aide de l’API Entity Framework ou d’une autre API. Dans un nouveau projet d’API web, vous pouvez voir que la seule dépendance de ce microservice se trouve au niveau d’ASP.NET Core. En interne, dans la dépendance `Microsoft.AspNetCore.All`, il référence Entity Framework et de nombreux autres packages Nuget .NET Core, comme indiqué dans la Figure 8-7.

![](./media/image8.PNG)

**Figure 8-7**. Dépendances d’un microservice d’API web CRUD simple

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a>Implémentation de services d’API web CRUD avec Entity Framework Core

Entity Framework (EF) Core est une version légère, extensible et multiplateforme de la technologie d’accès aux données Entity Framework populaire. Entity Framework Core est un outil de mappage objet-relationnel (ORM) qui permet aux développeurs .NET d’utiliser une base de données avec des objets .NET.

Le microservice de catalogue utilise Entity Framework et le fournisseur SQL Server, car sa base de données est exécutée dans un conteneur avec l’image SQL Server pour Linux Docker. Toutefois, la base de données peut être déployée sur n’importe quel serveur SQL Server (instance locale Windows ou Azure SQL DB). La seule chose que vous devez modifier est la chaîne de connexion située dans le microservice de l’API web ASP.NET.


#### <a name="the-data-model"></a>Modèle de données

Avec Entity Framework Core, l’accès aux données est effectué à l’aide d’un modèle. Un modèle est composé de classes d’entité et d’un contexte dérivé qui représente une session avec la base de données, ce qui vous permet d’interroger et d’enregistrer des données. Vous pouvez générer un modèle à partir d’une base de données existante, coder manuellement un modèle en fonction de votre base de données ou utiliser des migrations Entity Framework pour créer une base de données à partir de votre modèle (et la faire évoluer au même rythme que celui-ci). Pour le microservice de catalogue, nous utilisons la dernière méthode. Vous pouvez voir un exemple de la classe d’entité CatalogItem dans l’exemple de code suivant, qui est une classe d’entité [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object).

```csharp
public class CatalogItem
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Description { get; set; }
    public decimal Price { get; set; }
    public string PictureFileName { get; set; }
    public string PictureUri { get; set; }
    public int CatalogTypeId { get; set; }
    public CatalogType CatalogType { get; set; }
    public int CatalogBrandId { get; set; }
    public CatalogBrand CatalogBrand { get; set; }
    public int AvailableStock { get; set; }
    public int RestockThreshold { get; set; }
    public int MaxStockThreshold { get; set; }

    public bool OnReorder { get; set; }
    public CatalogItem() { }

    // Additional code ...
}
```

Vous avez également besoin d’un DbContext qui représente une session pour la base de données. Pour le microservice de catalogue, la classe CatalogContext est dérivée de la classe de base DbContext, comme le montre l’exemple suivant :

```csharp
public class CatalogContext : DbContext
{
    public CatalogContext(DbContextOptions<CatalogContext> options) : base(options)
    {
    }
    public DbSet<CatalogItem> CatalogItems { get; set; }
    public DbSet<CatalogBrand> CatalogBrands { get; set; }
    public DbSet<CatalogType> CatalogTypes { get; set; }

    // Additional code ...

}
```

Vous pouvez avoir d’autres implémentations `DbContext`. Par exemple, dans l’exemple de microservice Catalog.API, il existe un deuxième `DbContext` nommé `CatalogContextSeed` où des exemples de données sont automatiquement ajoutés lors du premier accès à la base de données. Cette méthode est utile pour les données de démonstration et pour les scénarios de tests automatisés. Dans le `DbContext`, utilisez la méthode `OnModelCreating` pour personnaliser les mappages d’entités objet/base de données, et d’autres [points d’extension Entity Framework](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).

##### <a name="querying-data-from-web-api-controllers"></a>Interrogation des données à partir de contrôleurs d’API web

Les instances des classes d’entité sont généralement récupérées dans la base de données à l’aide de LINQ, comme dans l’exemple suivant :

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    private readonly CatalogContext _catalogContext;
    private readonly CatalogSettings _settings;
    private readonly ICatalogIntegrationEventService _catalogIntegrationEventService;

    public CatalogController(CatalogContext context, 
                             IOptionsSnapshot<CatalogSettings> settings,
                             ICatalogIntegrationEventService catalogIntegrationEventService)
    {
        _catalogContext = context ?? throw new ArgumentNullException(nameof(context));
        _catalogIntegrationEventService = catalogIntegrationEventService ?? throw new ArgumentNullException(nameof(catalogIntegrationEventService));

        _settings = settings.Value;
        ((DbContext)context).ChangeTracker.QueryTrackingBehavior = QueryTrackingBehavior.NoTracking;
    }

    // GET api/v1/[controller]/items[?pageSize=3&pageIndex=10]
    [HttpGet]
    [Route("[action]")]
    [ProducesResponseType(typeof(PaginatedItemsViewModel<CatalogItem>), (int)HttpStatusCode.OK)]
    public async Task<IActionResult> Items([FromQuery]int pageSize = 10, 
                                           [FromQuery]int pageIndex = 0)

    {
        var totalItems = await _catalogContext.CatalogItems
            .LongCountAsync();

        var itemsOnPage = await _catalogContext.CatalogItems
            .OrderBy(c => c.Name)
            .Skip(pageSize * pageIndex)
            .Take(pageSize)
            .ToListAsync();

        itemsOnPage = ChangeUriPlaceholder(itemsOnPage);

        var model = new PaginatedItemsViewModel<CatalogItem>(
            pageIndex, pageSize, totalItems, itemsOnPage);

        return Ok(model);
    } 
    //...
}
```

##### <a name="saving-data"></a>Enregistrement de données

Les données sont créées, supprimées et modifiées dans la base de données à l’aide d’instances de vos classes d’entité. Vous pouvez ajouter du code similaire à celui de l’exemple codé en dur suivant (il s’agit ici de données fictives) dans vos contrôleurs d’API web.

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
                                     Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a>Injection de dépendances dans ASP.NET Core et dans les contrôleurs d’API web

Dans ASP.NET Core, vous pouvez utiliser une injection de dépendances prête à l’emploi. Il n’est pas nécessaire de configurer un conteneur IoC tiers. Toutefois, si vous le souhaitez, vous pouvez connecter votre conteneur IoC par défaut à l’infrastructure ASP.NET Core. Dans ce cas, vous pouvez injecter directement le DBContext Entity Framework (et autres dépôts) via le constructeur de contrôleur. Dans l’exemple situé au-dessus de la classe `CatalogController`, nous allons injecter un objet de type `CatalogContext`, ainsi que d’autres objets via le constructeur `CatalogController()`.

L’un des éléments importants à configurer pour le projet d’API web est l’inscription de la classe DbContext auprès du conteneur IoC du service. Pour cela, dans la classe `Startup`, appelez la méthode `services.AddDbContext<DbContext>()` à l’intérieur de la méthode `ConfigureServices()`, comme indiqué dans l’exemple suivant :

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // Additional code...

    services.AddDbContext<CatalogContext>(options =>
    {
        options.UseSqlServer(Configuration["ConnectionString"],
        sqlServerOptionsAction: sqlOptions =>
        {
           sqlOptions.
               MigrationsAssembly(
                   typeof(Startup).
                    GetTypeInfo().
                     Assembly.
                      GetName().Name);

           //Configuring Connection Resiliency:
           sqlOptions.
               EnableRetryOnFailure(maxRetryCount: 5,
               maxRetryDelay: TimeSpan.FromSeconds(30),
               errorNumbersToAdd: null);

       });

       // Changing default behavior when client evaluation occurs to throw.
       // Default in EFCore would be to log warning when client evaluation is done.
       options.ConfigureWarnings(warnings => warnings.Throw(
           RelationalEventId.QueryClientEvaluationWarning));
   });

  //...

}
```

### <a name="additional-resources"></a>Ressources supplémentaires

-   **Interrogation des données**
    [*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)

-   **Enregistrement de données**
    [*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a>Chaîne de connexion de la base de données et variables d’environnement utilisées par les conteneurs Docker

Vous pouvez utiliser les paramètres ASP.NET Core et ajouter une propriété ConnectionString à votre fichier settings.json, comme indiqué dans l’exemple suivant :

```csharp
{
    "ConnectionString": "Server=tcp:127.0.0.1,5433;Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word",
    "ExternalCatalogBaseUrl": "http://localhost:5101",
    "Logging": {
        "IncludeScopes": false,
        "LogLevel": {
            "Default": "Debug",
            "System": "Information",
            "Microsoft": "Information"
        }
    }
}
```

Le fichier settings.json peut avoir des valeurs par défaut pour la propriété ConnectionString ou pour toute autre propriété. Toutefois, ces propriétés seront remplacées par les valeurs des variables d’environnement que vous spécifiez dans le fichier docker-compose.override.yml lors de l’utilisation de Docker.

Dans les fichiers docker-compose.yml et docker-compose.override.yml, vous pouvez initialiser les variables d’environnement pour que Docker les configure comme des variables d’environnement du système d’exploitation, comme dans le fichier docker-compose.override.yml suivant (dans cet exemple, un retour automatique à la ligne est effectué pour la chaîne de connexion et les autres lignes, mais ce ne sera pas le cas dans votre fichier de code).

```yml
# docker-compose.override.yml

#
catalog.api:
  environment:
    - ConnectionString=Server=sql.data;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word
    # Additional environment variables for this service
  ports:
    - "5101:80"
```

Les fichiers docker-compose.yml situés au niveau de la solution non seulement sont plus flexibles que les fichiers de configuration situés au niveau du projet ou microservice, mais ils sont aussi plus sécurisés si vous remplacez les variables d’environnement déclarées dans les fichiers docker-compose par des valeurs définies dans vos outils de déploiement (par exemple, dans les tâches de déploiement VSTS Docker). 

Enfin, vous pouvez obtenir cette valeur à partir de votre code à l’aide de Configuration\["ConnectionString"\], comme illustré dans la méthode ConfigureServices de l’exemple de code précédent.

Toutefois, pour les environnements de production, vous pouvez explorer d’autres moyens de stocker des secrets, comme les chaînes de connexion. Ceci est généralement géré par l’orchestrateur de votre choix, comme pour la [gestion de secrets Docker Swarm](https://docs.docker.com/engine/swarm/secrets/).

### <a name="implementing-versioning-in-aspnet-web-apis"></a>Implémentation de la gestion de version dans les API web ASP.NET

L’évolution des exigences métier peut entraîner l’ajout de collections de ressources, le changement des relations entre les ressources et la modification de la structure des données contenues dans ces ressources. La modification d’une API web pour s’adapter aux nouvelles exigences est un processus relativement simple. Toutefois, vous devez prendre en compte les conséquences d’une telle modification sur l’utilisation de l’API web par les applications clientes. Même si le développeur qui conçoit et implémente une API web dispose d’un contrôle total sur cette API, il ne dispose pas du même degré de contrôle sur les applications clientes qui peuvent avoir été créées par des organisations tierces distantes.

La gestion de version permet à une API web d’indiquer les fonctionnalités et les ressources qu’elle expose. Une application cliente peut ensuite envoyer des requêtes à une version précise d’une fonctionnalité ou d’une ressource. Il existe plusieurs méthodes pour implémenter la gestion de version :

-   Gestion des versions d’URI

-   Gestion des versions de chaîne de requête

-   Gestion des versions d’en-tête

La gestion des versions de chaîne de requête et d’URI sont les plus simples à implémenter. La gestion des versions d’en-tête est une bonne méthode. Toutefois, elle n’est pas aussi explicite et directe que la gestion des versions d’URI. Étant donné que la gestion des versions d’URI est la plus simple et la plus explicite, c’est elle qu’utilise l’exemple d’application eShopOnContainers.

Avec la gestion des versions d’URI (comme dans l’exemple d’application eShopOnContainers), chaque fois que vous modifiez l’API web ou que vous modifiez le schéma des ressources, vous ajoutez un numéro de version à l’URI de chaque ressource. Les URI existants continuent de fonctionner comme avant, en retournant des ressources conformes au schéma de la version demandée.

Comme le montre l’exemple de code suivant, la version peut être définie à l’aide de l’attribut Route dans l’API web, ce qui rend la version explicite dans l’URI (v1, dans ce cas).

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

Ce mécanisme de gestion de version est simple et dépend du serveur qui achemine la demande vers le point de terminaison approprié. Toutefois, pour une gestion de version plus sophistiquée et pour une utilisation optimale avec REST, vous devez utiliser des hypermédias et implémenter [HATEOAS](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources).

### <a name="additional-resources"></a>Ressources supplémentaires

-   **Scott Hanselman. ASP.NET Core RESTful Web API versioning made easy**
    [*https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)

-   **Contrôle de version d’une API web RESTful**
    [*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)

-   **Roy Fielding. Versioning, Hypermedia, and REST**
    [*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a>Génération de métadonnées de description Swagger à partir de votre API web ASP.NET Core 

[Swagger](https://swagger.io/) est un framework open source couramment utilisé qui s’appuie sur un large écosystème d’outils permettant de concevoir, de générer, de documenter et de consommer vos API RESTful. C’est désormais une référence dans le domaine des métadonnées de description d’API. Vous devez ajouter des métadonnées de description Swagger à tous les microservices, qu’il s’agisse de microservices pilotés par les données ou de microservices plus avancés pilotés par le domaine (comme expliqué dans la section suivante).

Le principal intérêt de Swagger est la spécification Swagger, c’est-à-dire les métadonnées de description d’API contenues dans un fichier JSON ou YAML. La spécification crée le contrat RESTful pour votre API, en détaillant toutes ses ressources et opérations dans un format lisible par l’homme et par la machine, pour un développement, une découverte et une intégration facilités.

Cette spécification est la base de la spécification OpenAPI (OAS). Elle a été développée par une communauté ouverte, transparente et collaborative pour normaliser la façon dont les interfaces RESTful sont définies.

La spécification permet de définir la façon dont un service peut être découvert et la façon dont ses fonctionnalités sont comprises. Pour plus d’informations, notamment sur l’éditeur web Swagger, et pour obtenir les exemples de spécifications Swagger d’entreprises comme Spotify, Uber, Slack et Microsoft, consultez le site Swagger (<https://swagger.io/>).

### <a name="why-use-swagger"></a>Pourquoi utiliser Swagger ?

Voici pourquoi il est utile de générer des métadonnées Swagger pour votre API.

**Les autres produits peuvent consommer et intégrer automatiquement vos API**. Swagger est pris en charge par des dizaines de produits et [d’outils professionnels](https://swagger.io/commercial-tools/), ainsi que par un grand nombre de [bibliothèques et de frameworks](https://swagger.io/open-source-integrations/). Microsoft propose des produits et des outils de niveau supérieur qui peuvent consommer automatiquement les API Swagger, comme celles qui suivent :

-   [AutoRest](https://github.com/Azure/AutoRest). Vous pouvez générer automatiquement des classes client .NET pour appeler Swagger. Cet outil peut être utilisé à partir de l’interface CLI. En outre, il s’intègre à Visual Studio pour une utilisation facilitée via l’interface utilisateur graphique.

-   [Microsoft Flow](https://flow.microsoft.com/en-us/). Vous pouvez [utiliser et intégrer votre API](https://flow.microsoft.com/en-us/blog/integrating-custom-api/) automatiquement dans un flux de travail Microsoft Flow de haut niveau, sans avoir de compétences en programmation.

-   [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/). Vous pouvez consommer automatiquement votre API à partir [d’applications mobiles PowerApps](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/) créées dans [PowerApps Studio](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/), sans avoir de compétences en programmation.

-   [Applications logiques Azure App Service](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps). Vous pouvez [utiliser et intégrer votre API dans une application logique Azure App Service](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api) automatiquement, sans avoir de compétences en programmation.

**Vous pouvez générer automatiquement la documentation de l’API**. Lorsque vous créez des API RESTful à grande échelle, telles que des applications de microservice complexes, vous devez gérer de nombreux points de terminaison avec les différents modèles de données utilisés dans les charges utiles de demande et de réponse. Une documentation appropriée et un explorateur d’API solide (comme ceux fournis par Swagger) sont essentiels au succès de votre API et à son adoption par les développeurs.

Les métadonnées Swagger sont utilisées par Microsoft Flow, PowerApps et Azure Logic Apps pour comprendre comment utiliser les API et s’y connecter.

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a>Comment automatiser la génération de métadonnées d’API Swagger avec le package NuGet Swashbuckle

La génération manuelle de métadonnées Swagger (dans un fichier JSON ou YAML) peut être fastidieuse. Toutefois, vous pouvez automatiser la découverte d’API des services d’API web ASP.NET à l’aide du [package NuGet Swashbuckle](http://aka.ms/swashbuckledotnetcore) afin de générer dynamiquement les métadonnées d’API Swagger.

Swashbuckle génère automatiquement les métadonnées Swagger pour vos projets d’API web ASP.NET. Il prend en charge les projets d’API web ASP.NET Core et l’API web ASP.NET traditionnelle, ainsi que toutes les autres versions, telles qu’Azure API App, Azure Mobile App ou les microservices Azure Service Fabric reposant sur ASP.NET. Il prend également en charge les API web simples déployées dans des conteneurs, comme l’application de référence.

Swashbuckle associe l’explorateur d’API et Swagger (ou [swagger-ui](https://github.com/swagger-api/swagger-ui)) pour fournir aux utilisateurs de votre API des fonctionnalités avancées de découverte et de documentation. Outre son moteur de génération de métadonnées Swagger, Swashbuckle contient également une version intégrée de swagger-ui, qu’il fournit automatiquement après son installation.

Cela signifie que vous pouvez compléter votre API avec une interface utilisateur de découverte pour aider les développeurs à utiliser votre API. Elle nécessite très peu de code et de maintenance, car elle est générée automatiquement, ce qui vous permet de vous concentrer sur la création de votre API. Le résultat de l’explorateur d’API ressemble à celui de la Figure 8-8.

![](./media/image9.png)

**Figure 8-8**. L’explorateur d’API Swashbuckle basé sur les métadonnées Swagger - Microservice de catalogue eShopOnContainers

L’explorateur d’API n’est pas le plus important ici. Une fois que votre API web peut se décrire dans les métadonnées Swagger, elle peut être utilisée facilement dans les outils Swagger, y compris dans les générateurs de code de classe proxy client qui peuvent cibler plusieurs plateformes. Par exemple, [AutoRest](https://github.com/Azure/AutoRest) génère automatiquement des classes client .NET. Toutefois, d’autres outils comme [swagger-codegen](https://github.com/swagger-api/swagger-codegen) sont également disponibles, et permettent la génération automatique de code pour les bibliothèques clientes d’API, pour les stubs serveur et pour la documentation.

Actuellement, Swashbuckle se compose de deux packages NuGet internes situés sous le métapaquet de niveau supérieur [Swashbuckle.Swashbuckle.AspNetCoreSwaggerGen](https://www.nuget.org/packages/Swashbuckle.AspNetCore/) version 1.0.0 ou ultérieure pour les applications ASP.NET Core.

Lorsque vous avez installé ces packages NuGet dans votre projet d’API web, vous devez configurer Swagger dans la classe de démarrage, comme dans le code suivant :

```csharp
public class Startup
{
    public IConfigurationRoot Configuration { get; }
    // Other startup code...

    public void ConfigureServices(IServiceCollection services)
    {
        // Other ConfigureServices() code...

        // Add framework services.
        services.AddSwaggerGen(options =>
        {
            options.DescribeAllEnumsAsStrings();
            options.SwaggerDoc("v1", new Swashbuckle.AspNetCore.Swagger.Info
            {
                Title = "eShopOnContainers - Catalog HTTP API",
                Version = "v1",
                Description = "The Catalog Microservice HTTP API. This is a Data-Driven/CRUD microservice sample",
                TermsOfService = "Terms Of Service"
            });
        });

        // Other ConfigureServices() code...
    }

    public void Configure(IApplicationBuilder app,
        IHostingEnvironment env,
        ILoggerFactory loggerFactory)
    {
        // Other Configure() code...
        // ...
        app.UseSwagger()
            .UseSwaggerUI(c =>
            {
                c.SwaggerEndpoint("/swagger/v1/swagger.json", "My API V1");
            });
    }
}
```

Après cela, vous pouvez démarrer votre application et parcourir les points de terminaison JSON et d’interface utilisateur Swagger suivants à l’aide d’URL de ce type :

```json
  http://<your-root-url>/swagger/v1/swagger.json
  
  http://<your-root-url>/swagger/
```

Vous avez déjà vu l’interface utilisateur générée par Swashbuckle pour une URL telle que http://&lt;votre-url-racine&gt;/swagger/ui. Dans la Figure 8-9, vous pouvez également voir comment tester une méthode d’API.

![](./media/image10.png)

**Figure 8-9**. Interface utilisateur Swashbuckle UI testant la méthode d’API Catalog/Items

La Figure 8-10 montre les métadonnées JSON Swagger générées à partir du microservice eShopOnContainers (utilisé par les outils ci-dessous) lorsque vous envoyez une requête pour &lt;votre-url-racine&gt;/swagger/v1/swagger.json à l’aide de [Postman](https://www.getpostman.com/).

![](./media/image11.png)

**Figure 8-10**. Métadonnées JSON Swagger

C’est aussi simple que cela. Et parce qu’elles sont générées automatiquement, les métadonnées Swagger grandissent à mesure que vous ajoutez des fonctionnalités à votre API.

### <a name="additional-resources"></a>Ressources supplémentaires

-   **Pages d’aide d’API web ASP.NET Core à l’aide de Swagger**
    [*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)


>[!div class="step-by-step"]
[Précédent](microservice-application-design.md)
[Suivant](multi-container-applications-docker-compose.md)
