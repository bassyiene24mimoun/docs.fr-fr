---
title: Caractéristiques des applications web modernes
description: Architecturer des applications web modernes avec ASP.NET Core et Azure | Caractéristiques des applications web modernes
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.openlocfilehash: cc4493bf8e45c41a94e8e6f719318b14ad5b05f1
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105805"
---
# <a name="characteristics-of-modern-web-applications"></a>Caractéristiques des applications web modernes

> "… avec une bonne conception, les fonctionnalités sont peu coûteuses. Cette approche est compliquée, mais continue à porter ses fruits. »  
> _\- Dennis Ritchie_

## <a name="summary"></a>Récapitulatif

Les attentes et les exigences des utilisateurs vis-à-vis des applications web modernes n’ont jamais été aussi élevées. Les applications web d’aujourd’hui sont censées être disponibles 24 heures sur 24, sept jours sur sept, depuis n’importe où dans le monde, et être utilisables avec presque n’importe quel appareil ou taille d’écran. Elles doivent être sécurisées, flexibles et scalables afin de répondre aux pics de demande. De plus en plus, des scénarios complexes doivent être gérés par des expériences utilisateur complexes générées sur le client à l’aide de JavaScript et qui communiquent efficacement par le biais d’API web.

ASP.NET Core est optimisé pour les applications web modernes et les scénarios d’hébergement cloud. Grâce à sa conception modulaire, les applications dépendent uniquement des fonctionnalités qu’elles utilisent réellement, ce qui améliore les performances et la sécurité de l’application tout en réduisant les besoins en ressources d’hébergement.

## <a name="reference-application-eshoponweb"></a>Référence d’application : eShopOnWeb

Ce guide comprend une application de référence, *eShopOnWeb*, qui illustre certains principes et recommandations. L’application est un magasin en ligne simple qui prend en charge la navigation dans un catalogue de chemises, tasses à café et autres articles marketing. Cette application de référence est délibérément simple afin de la rendre facile à comprendre.

**Figure 2-1.** eShopOnWeb

![](./media/image2-1.png)

> ### <a name="reference-application"></a>Application de référence
> - **eShopOnWeb**  
> <https://github.com/dotnet/eShopOnWeb>

## <a name="cloud-hosted-and-scalable"></a>Hébergées dans le cloud et scalables

ASP.NET Core est optimisé pour le cloud (cloud public, cloud privé, n’importe quel cloud), car il consomme peu de mémoire et offre un débit élevé. Le faible encombrement des applications ASP.NET Core signifie que vous pouvez en héberger davantage sur le même matériel, tout en réduisant les coûts de ressources lors de l’utilisation de services d’hébergement cloud de type Paiement à l’utilisation. Le débit plus élevé signifie que vous pouvez servir davantage de clients à partir d’une application avec le même matériel, réduisant ainsi la nécessité d’investir dans des serveurs et une infrastructure d’hébergement.

## <a name="cross-platform"></a>Multiplateforme

ASP.NET Core est multiplateforme et peut s’exécuter sur Linux et MacOS en plus de Windows. Cela donne accès à de nombreuses nouvelles options pour le développement et le déploiement d’applications créées avec ASP.NET Core. Les conteneurs Docker, qui exécutent généralement Linux aujourd’hui, peuvent héberger des applications ASP.NET Core, ce qui leur permet de tirer parti des avantages offerts par les [conteneurs et microservices](../microservices-architecture/index.md).

## <a name="modular-and-loosely-coupled"></a>Faiblement couplées et modulaires

Les packages NuGet sont des citoyens de première classe dans .NET Core, et les applications ASP.NET Core sont composées de nombreuses bibliothèques par le biais de NuGet. Avec ce niveau de granularité des fonctionnalités, les applications dépendent uniquement des fonctionnalités dont elles ont réellement besoin et déploient uniquement ces fonctionnalités, réduisant ainsi leur encombrement et leur surface d’exposition de vulnérabilité de sécurité.

ASP.NET Core prend aussi totalement en charge l’injection de dépendances, à la fois en interne et au niveau de l’application. Les interfaces peuvent avoir plusieurs implémentations qui peuvent être échangées en fonction des besoins. L’injection de dépendances permet aux applications d’être faiblement couplées avec ces interfaces, ce qui les rend plus faciles à étendre, mettre à jour et tester.

## <a name="easily-tested-with-automated-tests"></a>Facilement testées avec des tests automatisés

Les applications ASP.NET Core prennent en charge les tests unitaires, et leur faible couplage et leur prise en charge des injections de dépendances facilitent le remplacement des infrastructures à problème par des implémentations factices à des fins de test. ASP.NET Core est également fourni avec un TestServer qui peut être utilisé pour héberger des applications en mémoire. Des tests fonctionnels peuvent ensuite effectuer des demandes à ce serveur en mémoire en testant la pile d’application complète (notamment les middlewares, le routage, la liaison de modèle, les filtres, etc.) et en recevant une réponse, tout ceci en une fraction du temps qui serait nécessaire pour héberger l’application sur un serveur réel et effectuer des demandes par le biais de la couche réseau. Ces tests sont particulièrement faciles à écrire et utiles pour les API, qui sont de plus en plus importantes dans les applications web modernes.

## <a name="traditional-and-spa-behaviors-supported"></a>Comportements d’applications traditionnelles et SPA pris en charge

Les applications web traditionnelles impliquent peu de comportement côté client, mais repose sur le serveur pour la navigation, les requêtes et les mises à jour que l’application peut avoir besoin d’effectuer. Chaque nouvelle opération effectuée par l’utilisateur se traduit par une nouvelle requête web, le résultat étant un rechargement complet de la page dans le navigateur de l’utilisateur final. Les frameworks MVC (Model-View-Controller) classiques suivent généralement cette approche, chaque nouvelle requête correspondant à une action de contrôleur différente, qui à son tour fonctionne avec un modèle et retourne une vue. Certaines opérations individuelles dans une page donnée peuvent être améliorées avec des fonctionnalités AJAX (Asynchronous JavaScript and XML), mais l’architecture globale de l’application utilise de nombreuses vues MVC et points de terminaison d’URL différents.

Les applications monopages (SPA, Single-Page Applications), en revanche, impliquent très peu de chargements de page côté serveur générés de manière dynamique (voire aucun). De nombreuses applications SPA sont initialisées dans un fichier HTML statique qui charge les bibliothèques JavaScript nécessaires pour démarrer et exécuter l’application. Ces applications utilisent de manière intensive des API web pour leurs besoins en données, et peuvent fournir des expériences utilisateur beaucoup plus riches.

De nombreuses applications web impliquent une combinaison des comportements d’application web traditionnelle (en général pour le contenu) et d’application SPA (pour l’interactivité). ASP.NET Core prend en charge les API web et MVC dans la même application, à l’aide du même ensemble d’outils et de bibliothèques de framework sous-jacentes.

## <a name="simple-development-and-deployment"></a>Développement et déploiement simples

Les applications ASP.NET Core peuvent être écrites à l’aide d’éditeurs de texte et d’interfaces de ligne de commande simples, ou d’environnements de développement complets comme Visual Studio. Les applications monolithiques sont généralement déployées sur un seul point de terminaison. Les déploiements peuvent facilement être automatisés et faire partie d’un pipeline d’intégration continue (CI) et de livraison continue (CD). En plus des outils CI/CD traditionnels, Microsoft Azure offre une prise en charge intégrée des dépôts git et peut déployer automatiquement les mises à jour à mesure qu’elles sont apportées à une balise ou une branche git spécifiée.

## <a name="traditional-aspnet-and-web-forms"></a>ASP.NET traditionnel et Web Forms

En plus d’ASP.NET Core, la plateforme ASP.NET 4.x traditionnelle reste robuste et fiable pour la création d’applications web. ASP.NET prend en charge les modèles de développement d’API web et MVC, ainsi que Web Forms, qui convient parfaitement au développement d’applications sophistiquées basées sur des pages et propose un riche écosystème de composants tiers. Microsoft Azure offre depuis très longtemps la prise en charge des applications ASP.NET 4.x, et de nombreux développeurs connaissent très bien cette plateforme.

> ### <a name="references--modern-web-applications"></a>Informations de référence sur les applications web modernes
> - **Présentation d’ASP.NET Core**  
> <https://docs.microsoft.com/aspnet/core/>
> - **Six avantages clés d’ASP.NET Core qui le rendent différent et mieux**  
> <https://blog.trigent.com/six-key-benefits-of-asp-net-core-1-0-which-make-it-different-better/>
> - **Test dans ASP.NET Core**  
> <https://docs.microsoft.com/aspnet/core/testing/>

>[!div class="step-by-step"]
[Précédent](index.md)
[Suivant](choose-between-traditional-web-and-single-page-apps.md)
