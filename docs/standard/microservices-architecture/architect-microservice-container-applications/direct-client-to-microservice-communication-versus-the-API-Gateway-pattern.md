---
title: Modèle de passerelle API et communication directe de client à microservice
description: Architecture de microservices .NET pour les applications .NET en conteneur | Modèle de passerelle d’API et communication directe de client à microservice
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/07/2018
ms.openlocfilehash: 83ec054239814ba20ebeec1f3d50b9f7e6dcdd87
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106276"
---
# <a name="the-api-gateway-pattern-versus-the-direct-client-to-microservice-communication"></a>Modèle de passerelle API et communication directe de client à microservice

Dans une architecture de microservices, chaque microservice expose un ensemble de points de terminaison (généralement) très ciblés. Ceci peut affecter la communication de client à microservice, comme expliqué dans cette section.

## <a name="direct-client-to-microservice-communication"></a>Communication directe de client à microservice

Une approche possible consiste à utiliser une architecture de communication directe de client à microservice. Dans cette approche, une application cliente peut envoyer des demandes directement à certains des microservices, comme le montre la figure 4-12.

![Diagramme montrant une architecture de communication directe de client à microservice](./media/image12.png)

**Figure 4-12**. Utilisation d’une architecture de communication directe de client à microservice

Dans cette approche, chaque microservice a un point de terminaison public, parfois avec un port TCP différent pour chaque microservice. Voici un exemple d’URL pour un service particulier dans Azure :

<http://eshoponcontainers.westus.cloudapp.azure.com:88/>

Dans un environnement de production basé sur un cluster, cette URL serait mappée à l’équilibreur de charge utilisé dans le cluster, qui à son tour distribue les demandes entre les microservices. Dans les environnements de production, vous pouvez avoir un contrôleur de livraison d’application comme [Azure Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction) entre vos microservices et Internet. Ceci fonctionne comme un niveau transparent qui non seulement effectue l’équilibrage de charge, mais permet aussi de sécuriser vos services en offrant un processus de terminaison SSL. Ceci allège la charge de vos hôtes en transférant à Azure Application Gateway les processus de terminaison SSL et d’autres tâches de routage qui consomment une grande quantité de ressources de l’UC. Dans tous les cas, un équilibreur de charge et un contrôleur de livraison d’application sont transparents du point de vue de l’architecture logique d’une application.

Une architecture de communication directe de client à microservice peut être suffisante pour une petite application basée sur des microservices, surtout si l’application cliente est une application web côté serveur, comme une application ASP.NET MVC. Cependant, quand vous créez des applications basées sur les microservices de grande taille et complexes (par exemple quand vous gérez des dizaines de types de microservice), et en particulier quand les applications clientes sont des applications mobiles distantes ou des applications web SPA, cette approche doit faire face à quelques problèmes.

Quand vous développez une application de grande taille basée sur les microservices, considérez les questions suivantes :

- *Comment les applications clientes peuvent-elles minimiser le nombre de demandes envoyées au backend et réduire le volume important des communications avec plusieurs microservices ?*

Interagir avec plusieurs microservices pour créer un seul écran de l’interface utilisateur augmente le nombre d’allers-retours sur Internet. Ceci accroît la latence et la complexité du côté de l’interface utilisateur. Dans l’idéal, les réponses doivent être agrégées de façon efficace côté serveur. Ceci réduit la latence, car plusieurs éléments de données reviennent en parallèle et certaines parties de l’interface utilisateur peuvent afficher les données dès qu’elles sont prêtes.

- *Comment pouvez-vous gérer des problèmes transversaux comme l’autorisation, les transformations de données et la distribution des requêtes dynamiques ?*

L’implémentation de la sécurité et de problèmes transversaux, comme la sécurité et l’autorisation, sur chaque microservice peut nécessiter un travail de développement considérable. Une approche possible consiste à avoir ces services au sein de l’hôte Docker ou du cluster interne, de façon à limiter leur l’accès direct depuis l’extérieur et à implémenter ces problèmes transversaux à un emplacement centralisé, comme une passerelle d’API.

- *Comment les applications clientes peuvent-elles communiquer avec des services qui utilisent des protocoles non adaptés à Internet ?*

Les protocoles utilisés du côté serveur (par exemple AMQP ou des protocoles binaires) ne sont généralement pas pris en charge dans les applications clientes. Ainsi, les requêtes doivent être exécutées via des protocoles comme HTTP/HTTPS et être traduites après cela pour les autres protocoles. Une approche par *intercepteur* peut aider dans cette situation.

- *Comment pouvez-vous mettre en forme une façade spécialement conçue pour les applications mobiles ?*

L’API de plusieurs microservices peut ne pas être bien conçue pour les besoins de différentes applications clientes. Par exemple, les besoins d’une application mobile peuvent être différents de ceux d’une application web. Pour les applications mobiles, une optimisation supplémentaire peut être nécessaire pour rendre les réponses des données plus efficaces. Vous pouvez faire cela en agrégeant les données de plusieurs microservices et en retournant un seul jeu de données, et parfois en éliminant de la réponse les données qui ne sont pas nécessaires pour l’application mobile. Bien sûr, vous pouvez aussi compresser les données. Là encore, une façade ou une API entre l’application mobile et les microservices peut être pratique pour ce scénario.

## <a name="why-consider-api-gateways-instead-of-direct-client-to-microservice-communication"></a>Pourquoi utiliser des passerelles d’API plutôt qu’une communication directe de client à microservice

Dans une architecture microservices, les applications clientes doivent généralement consommer la fonctionnalité de plusieurs microservices. Si cette consommation est effectuée directement, le client doit gérer plusieurs appels à des points de terminaison de microservices. Que se passe-t-il lorsque l’application évolue et que de nouveaux microservices sont introduits ou que des microservices existants sont mis à jour ? Si votre application comporte de nombreux microservices, la gestion d’autant de points de terminaison à partir des applications clientes peut être un cauchemar. Étant donné que l’application cliente est associée à ces points de terminaison internes, le futur développement des microservices peut avoir un fort impact sur les applications clientes.

Par conséquent, avoir un niveau ou une couche intermédiaire d’indirection (passerelle) peut être très pratique pour les applications basées sur des microservices. Si vous n’avez pas de passerelles d’API, les applications clientes doivent envoyer des requêtes directement aux microservices, ce qui entraîne les problèmes suivants :

- **Couplage** : sans le modèle de passerelle d’API, les applications clientes sont couplées aux microservices internes. Les applications clientes doivent savoir comment les différentes zones de l’application sont décomposées en microservices. Lors du développement ou de la refactorisation des microservices internes, ces actions ont un impact négatif sur la maintenance car elles entraînent des modifications avec rupture dans les applications clientes en raison de la référence directe aux microservices internes à partir des applications clientes. Les applications clientes doivent être fréquemment mises à jour, ce qui perturbe le développement de la solution.

- **Trop d’allers-retours**: un seul écran ou une seule page dans l’application cliente peut nécessiter plusieurs appels à différents services. Cela peut entraîner plusieurs allers-retours sur le réseau entre le client et le serveur, augmentant considérablement la latence. L’agrégation gérée dans un niveau intermédiaire peut améliorer les performances et l’expérience utilisateur pour l’application cliente.

- **Problèmes de sécurité** : sans une passerelle, tous les microservices doivent être exposés au « monde extérieur », augmentant ainsi la surface d’attaque même si vous masquez les microservices internes qui ne sont pas directement utilisés par les applications clientes. Plus la surface d’attaque est réduite, plus votre application peut être sécurisée.

- **Problèmes transversaux** : chaque microservice publié doit gérer des problèmes comme une autorisation, SSL, etc. Dans de nombreux cas, ces problèmes pourraient être traités dans un même niveau afin de simplifier les microservices internes.

## <a name="what-is-the-api-gateway-pattern"></a>Présentation du modèle Passerelle d’API

Quand vous concevez et que vous créez des applications de grande taille ou complexes basées sur des microservices avec plusieurs applications clientes, une [passerelle d’API](https://microservices.io/patterns/apigateway.html) peut être une bonne approche à considérer. Il s’agit d’un service qui fournit un point d’entrée unique pour certains groupes de microservices. Il est similaire au [modèle Façade](https://en.wikipedia.org/wiki/Facade_pattern) de la conception orientée objet, mais dans ce cas, il fait partie d’un système distribué.
Le modèle Passerelle d’API est également parfois appelé « backend for frontend » [(BFF)](https://samnewman.io/patterns/architectural/bff/), car vous le créez en pensant aux besoins de l’application cliente.

Par conséquent, la passerelle d’API se place entre les applications clientes et le microservices. Elle agit comme un proxy inverse, acheminant les requêtes des clients vers les services. Elle peut également fournir des fonctionnalités composites supplémentaires comme l’authentification; la terminaison SSL et le cache.

La figure 4-13 montre comment une passerelle d’API personnalisée peut s’intégrer dans une architecture simplifiée basée sur quelques microservices.

![Diagramme montrant une passerelle d’API implémentée comme service personnalisé](./media/image13.png)

**Figure 4-13**. Utilisation d’une passerelle d’API implémentée comme service personnalisé

Dans cet exemple, la passerelle d’API doit être implémentée comme un service ASP.NET Core WebHost personnalisé s’exécutant en tant que conteneur.

Il est important de souligner que dans ce diagramme, vous utilisez un seul service de passerelle d’API personnalisée faisant face à plusieurs applications clientes différentes. Ceci peut présenter un risque important, car votre service de passerelle d’API va croître et évoluer en fonction des nombreuses exigences différentes des applications clientes. Au final, il deviendra trop étendu en raison de ces différents besoins et sera effectivement très similaire à une application monolithique ou à un service monolithique. C’est pourquoi il est vivement recommandé de diviser la passerelle d’API en plusieurs services ou en plusieurs passerelles d’API plus petites, par exemple une par type de facteur de forme dans une application cliente.

Soyez prudent lors de l’implémentation du modèle Passerelle API. Il n’est en général pas judicieux d’avoir une seule passerelle d’API agrégeant tous les microservices internes de votre application. Dans ce cas, elle se comporte comme un agrégateur ou un orchestrateur monolithique, et contrevient au principe d’autonomie des microservices en couplant tous les microservices.

Par conséquent, les passerelles d’API doivent être séparées en fonction des limites métier et des applications clientes et ne pas agir comme un agrégateur pour tous les microservices internes.

Lorsque vous fractionnez le niveau de la passerelle d’API en plusieurs passerelles d’API, si votre application comporte plusieurs applications clientes, vous pouvez utiliser un tableau croisé dynamique primaire pour identifier les différents types de passerelles d’API, et vous pouvez ainsi utiliser une façade différente selon les besoins de chaque application cliente. Ce cas est un modèle intitulé « Backend for Frontend » ([BFF](http://samnewman.io/patterns/architectural/bff/)), dans lequel chaque passerelle d’API peut fournir une API différente adaptée à chaque type d’application cliente, voire même en fonction du facteur de forme du client en implémentant le code d’un adaptateur spécifique qui appelle plusieurs microservices internes de façon sous-jacente, comme le montre l’image suivante :

![Diagramme montrant plusieurs passerelles d’API personnalisées](./media/image13.1.png)

**Figure 4-13.1**. Utilisation de plusieurs passerelles d’API personnalisées

L’image précédente montre une architecture simplifiée avec plusieurs passerelles d’API affinées. Dans ce cas, les limites identifiées pour chaque passerelle d’API reposent uniquement sur le modèle « Backend for Frontend » ([BFF](http://samnewman.io/patterns/architectural/bff/)), et sont donc basées uniquement sur l’API nécessaire à l’application cliente. Mais dans les applications de grande taille, vous devez également aller plus loin et créer d’autres passerelles d’API basées sur les limites de l’entreprise sous forme d’un second tableau croisé dynamique de conception.

## <a name="main-features-in-the-api-gateway-pattern"></a>Principales fonctionnalités du modèle Passerelle d’API

Une passerelle d’API peut offrir plusieurs fonctionnalités. Selon le produit, elle peut proposer des fonctionnalités plus ou moins complètes, mais les fonctionnalités de bases les plus importantes pour toute passerelle d’API sont les modèles de conception suivants :

**Proxy inversé ou routage de passerelle**. La passerelle d’API offre un proxy inversé pour rediriger ou acheminer les requêtes (routage de couche 7, généralement les requêtes Http) vers les points de terminaison des microservices internes. La passerelle fournit un point de terminaison ou une URL unique pour les applications clientes puis mappe en interne les requêtes à un groupe de microservices internes. Cette fonctionnalité de routage permet de découpler les applications clientes des microservices mais elle est également très pratique pour moderniser une API monolithique en plaçant la passerelle d’API entre l’API monolithique et les applications clientes. Vous pouvez alors ajouter de nouvelles API sous forme de nouveaux microservices tout en utilisant l’API monolithique héritée jusqu'à ce qu’elle soit fractionnée en plusieurs microservices. En raison de la passerelle d’API, les applications clientes ne remarqueront pas si les API utilisées sont implémentées comme des microservices internes ou comme une API monolithique et, plus important encore, lors du développement et de la refactorisation de l’API monolithique dans les microservices, grâce au routage de passerelle d’API routage, les applications clientes ne seront pas affectées par une modification de l’URI.

Pour plus d’informations, consultez [Modèle de routage de passerelle](https://docs.microsoft.com/azure/architecture/patterns/gateway-routing).

**Agrégation de requêtes**. Dans le cadre du modèle de passerelle, vous pouvez agréger plusieurs requêtes de client (généralement des requêtes Http) ciblant plusieurs microservices internes dans une requête de client unique. Ce modèle est particulièrement pratique lorsqu’une page ou un écran d’un client a besoin d’informations provenant de plusieurs microservices. Avec cette approche, l’application cliente envoie une demande unique à la passerelle d’API qui répartit plusieurs requêtes aux microservices internes, puis agrège les résultats et envoie le tout à l’application cliente. Le principal avantage et l’objectif de ce modèle de conception est de réduire les échanges entre les applications clientes et l’API de service principal, ce qui est particulièrement important pour les applications à distance situées en dehors du centre de données où résident les microservices, notamment les applications mobiles ou les requêtes issues d’applications SPA provenant de JavaScript dans les navigateurs clients à distance. Pour les applications web normales effectuant les requêtes dans l’environnement du serveur (par exemple, une application web ASP.NET Core MVC), ce modèle n’est pas si important car la latence est bien plus faible que pour les applications clientes à distance.

Selon le produit Passerelle d’API que vous utilisez, il sera en mesure d’effectuer cette agrégation. Toutefois, dans de nombreux cas, il est plus pratique de créer des microservices d’agrégation dans le cadre de la passerelle d’API. Définissez par conséquent l’agrégation dans le code (autrement dit, le code C#).

Pour plus d’informations, consultez [Modèle d’agrégation de passerelle](https://docs.microsoft.com/azure/architecture/patterns/gateway-aggregation).

**Problèmes transversaux ou déchargement de passerelle**. Selon les fonctionnalités offertes par chaque produit Passerelle d’API, vous pouvez décharger des fonctionnalités de microservices individuels vers la passerelle, ce qui simplifie l’implémentation de chaque microservice en consolidant les problèmes transversaux dans un seul niveau. Ceci est particulièrement pratique pour les fonctionnalités spécialisées qui peuvent être difficiles à implémenter correctement dans chaque microservice interne, par exemple les fonctionnalités suivantes :

- Authentification et autorisation
- Intégration de la découverte de service
- Mise en cache des réponses
- Stratégies de nouvelle tentative, disjoncteur et qualité de service (QoS)
- Limitation du débit
- Équilibrage de charge
- Journalisation, suivi, corrélation
- Transformation des en-têtes, chaînes de requête et revendications
- Liste verte d’adresses IP

Pour plus d’informations, consultez [Modèle de déchargement de passerelle](https://docs.microsoft.com/azure/architecture/patterns/gateway-offloading).

## <a name="using-products-with-api-gateway-features"></a>Utilisation de produits avec les fonctionnalités de la Passerelle d’API

Il peut y avoir plusieurs problèmes transversaux générés par les produits de la passerelle d’API en fonction de chaque implémentation. Par exemple, [Gestion des API Azure](https://azure.microsoft.com/services/api-management/) (comme indiqué dans la Figure 4-14) non seulement solutionne les besoins de votre passerelle d’API, mais fournit aussi des fonctionnalités comme la collecte d’informations auprès de vos API. Si vous utilisez une solution de gestion des API, une passerelle d’API est seulement un composant au sein de cette solution globale de gestion des API.

![Diagramme montrant la passerelle d’API avec l’architecture de gestion des API Azure](./media/image14.png)

**Figure 4-14**. Utilisation de Gestion des API Azure pour votre passerelle d’API

Dans ce cas, lors l’utilisation d’un produit comme Gestion des API Azure, le fait d’avoir une seule passerelle d’API n’est pas si risqué, car ces types de passerelles d’API sont « plus fins », ce qui veut dire que vous n’implémentez pas de code C# personnalisé susceptible d’évoluer vers un composant monolithique.

Les produits Passerelle d’API agissent généralement comme un proxy inversé pour la communication en entrée, où vous pouvez aussi filtrer les API des microservices internes et appliquer une autorisation aux API publiées dans ce niveau unique.

Les informations disponibles provenant d’un système de gestion des API vous aident à comprendre comment vos API sont utilisées et comment elles fonctionnent. Ils font cela en vous permettant de voir des rapports d’analyse quasi en temps réel et en identifiant les tendances qui peuvent avoir un impact sur votre activité. De plus, vous pouvez avoir des journaux sur l’activité des demandes et des réponses, que vous pouvez alors analyser de façon plus approfondie en ligne et hors connexion.

Avec Gestion des API Azure, vous pouvez sécuriser vos API avec une clé, un jeton et un filtrage des adresses IP. Ces fonctionnalités vous permettent d’appliquer des quotas et des limites de débit de façon souple et précise, de modifier la forme et le comportement de vos API avec des stratégies, et d’améliorer les performances avec la mise en cache des réponses.

Dans ce guide et dans l’exemple d’application de référence (eShopOnContainers), l’architecture est limitée à une architecture en conteneurs plus simple et personnalisée, de façon à mettre l’accent sur des conteneurs ordinaires sans utiliser de produits PaaS comme Gestion des API Azure. Cependant, pour les applications de grande taille basées sur des microservices et déployées sur Microsoft Azure, nous vous encourageons à évaluer Gestion des API Azure comme base pour vos passerelles d’API en production.

**Ocelot.** Pour des approches plus simples, une passerelle d’API légère comme Ocelot est recommandée. [Ocelot](https://github.com/ThreeMammals/Ocelot) est une passerelle d’API .NET Core open source conçue spécifiquement pour une architecture de microservices nécessitant des points d’entrée unifiés dans son système. Elle est légère, rapide, évolutive et fournit le routage et l’authentification, parmi de nombreuses autres fonctionnalités.

La principale raison pour laquelle Ocelot a été utilisée dans l’[application de référence eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) vient du fait qu’Ocelot est une passerelle d’API .NET Core légère que vous pouvez déployer dans le même environnement de déploiement d’application où vous déployez vos microservices/conteneurs, notamment un Docker Host, Kubernetes, Service Fabric, etc. Et comme elle s’appuie sur .NET Core, elle est multiplateforme et peut donc être déployée sur Windows ou Linux.

Les diagrammes précédents montrant des passerelles d’API personnalisée en cours d’exécution dans les conteneurs expliquent précisément comment vous pouvez également exécuter Ocelot dans un conteneur et dans une application basée sur un microservice.

En outre, il existe plusieurs autres produits sur le marché qui offrent des fonctionnalités de passerelles d’API, par exemple Apigee, Kong, MuleSoft, WSO2, et d’autres produits comme Linkerd et Istio pour les fonctionnalités de contrôleur d’ingestion de maille de services.

Après les sections consacrées à l’architecture initiale et à la présentation des modèles, les sections suivantes expliquent comment implémenter des passerelles d’API avec [Ocelot](https://github.com/ThreeMammals/Ocelot).

## <a name="drawbacks-of-the-api-gateway-pattern"></a>Inconvénients du modèle Passerelle d’API

- L’inconvénient plus important est que, quand vous implémentez une passerelle d’API, vous couplez ce niveau avec les microservices internes. Un tel couplage peut introduire de graves difficultés pour votre application. Clemens Vaster, architecte de l’équipe Azure Service Bus, parle de cette difficulté potentielle comme de « la nouvelle ESB » dans la session « [Messaging and Microservices](https://www.youtube.com/watch?v=rXi5CLjIQ9k) » à GOTO 2016.

- L’utilisation d’une passerelle d’API de microservices crée un possible point de défaillance unique supplémentaire.

- Une passerelle d’API peut introduire des temps de réponse accrus en raison de l’appel réseau supplémentaire. Cependant, cet appel supplémentaire a généralement moins d’impact qu’un client de l’interface qui émet trop de communications en appelant directement les microservices internes.

- Si elle n’est pas montée pas en charge correctement, la passerelle d’API peut devenir un goulot d’étranglement.

- Une passerelle d’API nécessite des coûts de développement supplémentaires et une maintenance ultérieure si elle inclut une logique personnalisée et effectue une agrégation des données. Les développeurs doivent mettre à jour la passerelle d’API pour pouvoir exposer les points de terminaison de chaque microservice. En outre, les changements d’implémentation dans les microservices internes peuvent entraîner des modifications du code au niveau de la passerelle d’API. Cependant, si la passerelle d’API applique simplement la sécurité, la journalisation et la gestion des versions (comme quand vous utilisez Gestion des API Azure), ces coûts de développement supplémentaires peuvent ne pas s’appliquer.

- Si la passerelle d’API est développée par une même équipe, il peut y avoir un goulot d’étranglement en matière de développement. Ceci est une autre raison pour laquelle il est préférable d’avoir plusieurs passerelles d’API plus ciblées qui répondent aux besoins des différents clients. Vous pouvez aussi diviser la passerelle d’API en interne en plusieurs parties ou couches, affectées chacune aux différentes équipes travaillant sur les microservices internes.

## <a name="additional-resources"></a>Ressources supplémentaires

- **Charles Richardson. Modèle : Passerelle/backend d’API pour serveur frontal** [*https://microservices.io/patterns/apigateway.html*](https://microservices.io/patterns/apigateway.html)

- **Modèle de passerelle d’API** [*https://docs.microsoft.com/azure/architecture/microservices/gateway*](https://docs.microsoft.com/azure/architecture/microservices/gateway)

- **Modèle d’agrégation et de composition** [*http://microservices.io/patterns/data/api-composition.html*](http://microservices.io/patterns/data/api-composition.html)

- **Gestion des API Azure** [*https://azure.microsoft.com/services/api-management/*](https://azure.microsoft.com/services/api-management/)

- **Udi Dahan. Composition orientée service**\
    [*http://udidahan.com/2014/07/30/service-oriented-composition-with-video/*](http://udidahan.com/2014/07/30/service-oriented-composition-with-video/)

- **Clemens Vasters. Messaging and Microservices at GOTO 2016** (vidéo) [*https://www.youtube.com/watch?v=rXi5CLjIQ9k*](https://www.youtube.com/watch?v=rXi5CLjIQ9k)

>[!div class="step-by-step"]
[Précédent](identify-microservice-domain-model-boundaries.md)
[Suivant](communication-in-microservice-architecture.md)
