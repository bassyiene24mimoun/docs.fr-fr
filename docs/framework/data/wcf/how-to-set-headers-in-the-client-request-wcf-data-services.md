---
title: 'Procédure : définir des en-têtes dans la demande cliente (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 3d55168d-5901-4f48-8117-6c93da3ab5ae
ms.openlocfilehash: e6b9b01f18e8412857a38a8e22fadfa88faf9d24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361784"
---
# <a name="how-to-set-headers-in-the-client-request-wcf-data-services"></a>Procédure : définir des en-têtes dans la demande cliente (WCF Data Services)
Lorsque vous utilisez la bibliothèque cliente [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] pour accéder à un service de données qui prend en charge [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)], celle-ci définit automatiquement les en-têtes HTTP requis dans les messages de demande transmis au service de données. Toutefois, la bibliothèque cliente ne sait pas définir les en-têtes de message requis dans certains cas, par exemple, quand le service de données exige une authentification basée sur des revendication ou des cookies. Pour plus d’informations, consultez [sécurisation de WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md#clientAuthentication). Dans ces cas, vous devez définir manuellement les en-têtes dans le message de demande avant de le transmettre. L'exemple de cette rubrique illustre comment utiliser l'événement <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> pour ajouter un nouvel en-tête au message de demande avant qu'il ne soit envoyé au service de données.  
  
 L'exemple dans cette rubrique utilise l'exemple de service de données Northwind et des classes de service de données clientes générées automatiquement. Ce service et les classes de données clientes sont créés lorsque vous complétez le [démarrage rapide WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Vous pouvez également utiliser le [service de données exemple Northwind](http://go.microsoft.com/fwlink/?LinkId=187426) qui est publié sur le [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] site Web ; ces exemples de données service est en lecture seule et essayez d’enregistrer les modifications retourne une erreur. Les exemples de données des services sur le [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] site Web autorisent l’authentification anonyme.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant enregistre un gestionnaire pour l'événement <xref:System.Data.Services.Client.DataServiceContext.SendingRequest>, puis exécute une requête sur le service de données.  
  
> [!NOTE]
>  Lorsqu'un service de données exige que vous définissiez manuellement l'en-tête de message de chaque demande, considérez d'utiliser un gestionnaire pour l'événement <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> en remplaçant la méthode `OnContextCreated` partielle dans le conteneur d'entités qui représente le service de données, dans ce cas : `NorthwindEntities`.  
  
[!code-csharp[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#registerheadersquery)]   
[!code-vb[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#registerheadersquery)]
  
## <a name="example"></a>Exemple  
 La méthode suivante utilise l'événement <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> et ajoute un en-tête automatique à la demande.  
  
 [!code-csharp[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#onsendingrequest)]  
 [!code-vb[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#onsendingrequest)]  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurisation de WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)  
 [Bibliothèque cliente WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
