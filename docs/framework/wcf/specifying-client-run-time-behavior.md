---
title: Spécification du comportement du client au moment de l'exécution
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- behaviors [WCF], system-provided client
ms.assetid: d16d3405-be70-4edb-8f62-b5f614ddeca5
ms.openlocfilehash: bc104c4f51ebc64154bd3d9b39ac2bca13b2fab1
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33805354"
---
# <a name="specifying-client-run-time-behavior"></a>Spécification du comportement du client au moment de l'exécution
Windows Communication Foundation (WCF) clients, tels que les services Windows Communication Foundation (WCF), peuvent être configurés pour modifier le comportement d’exécution en fonction de l’application cliente. Trois attributs sont disponibles pour spécifier le comportement du client au moment de l'exécution. Les objets de rappel de client duplex peuvent utiliser les attributs <xref:System.ServiceModel.CallbackBehaviorAttribute> et <xref:System.ServiceModel.Description.CallbackDebugBehavior> pour modifier leur comportement à l'exécution. L'autre attribut, <xref:System.ServiceModel.Description.ClientViaBehavior>, peut être utilisé pour séparer la destination logique de la destination réseau immédiate. De plus, les types de rappel de client duplex peuvent utiliser certains des comportements du côté service. Pour plus d’informations, consultez [spécification du comportement de Service runtime](../../../docs/framework/wcf/specifying-service-run-time-behavior.md).  
  
## <a name="using-the-callbackbehaviorattribute"></a>Utilisation de CallbackBehaviorAttribute  
 Vous pouvez configurer ou étendre le comportement d'exécution d'une implémentation de contrat de rappel dans une application cliente en utilisant la classe <xref:System.ServiceModel.CallbackBehaviorAttribute>. Cet attribut exécute pour la classe de rappel une fonction semblable à la classe <xref:System.ServiceModel.ServiceBehaviorAttribute>, à l'exception du comportement d'instanciation et des paramètres de transaction.  
  
 La classe <xref:System.ServiceModel.CallbackBehaviorAttribute> doit être appliquée à la classe qui implémente le contrat de rappel. En cas d'application à une implémentation de contrat non-duplex, une exception <xref:System.InvalidOperationException> est levée au moment de l'exécution. L'exemple de code suivant illustre une classe <xref:System.ServiceModel.CallbackBehaviorAttribute> sur un objet de rappel qui utilise l'objet <xref:System.Threading.SynchronizationContext> pour déterminer le thread à marshaler, la propriété <xref:System.ServiceModel.CallbackBehaviorAttribute.ValidateMustUnderstand%2A> pour appliquer la validation de message et la propriété <xref:System.ServiceModel.CallbackBehaviorAttribute.IncludeExceptionDetailInFaults%2A> pour retourner des exceptions comme objets <xref:System.ServiceModel.FaultException> au service à des fins de débogage.  
  
 [!code-csharp[CallbackBehaviorAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/callbackbehaviorattribute/cs/client.cs#3)]
 [!code-vb[CallbackBehaviorAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/callbackbehaviorattribute/vb/client.vb#3)]  
  
## <a name="using-callbackdebugbehavior-to-enable-the-flow-of-managed-exception-information"></a>Utilisation de CallbackDebugBehavior pour activer le flux d'informations d'exceptions managées  
 Vous pouvez activer le flux d'informations d'exceptions managées dans un objet de rappel client au service à des fins de débogage en affectant à la propriété <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> la valeur `true` par programme ou à partir d'un fichier de configuration d'application.  
  
 Le retour d'informations sur les exceptions managées aux services peut constituer un problème de sécurité car les détails d'exception exposent des informations relatives à l'implémentation cliente interne que des services non autorisés pourraient utiliser. De plus, bien que les propriétés <xref:System.ServiceModel.Description.CallbackDebugBehavior> puissent également être définies par programme, il peut être facile d'oublier de désactiver <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> lors du déploiement.  
  
 Étant donné les problèmes de sécurité impliqués, il est vivement recommandé :  
  
-   d'utiliser un fichier de configuration d'application pour affecter à la propriété <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> la valeur `true` ;  
  
-   de ne procéder ainsi que dans des scénarios de débogage contrôlés.  
  
 L’exemple de code suivant illustre un client de fichier de configuration qui fait en sorte que WCF pour retourner les informations d’exception gérées à partir d’un client objet de rappel dans les messages SOAP.  
  
 [!code-xml[SCA.CallbackContract#4](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.callbackcontract/cs/client.exe.config#4)]  
 
## <a name="using-the-clientviabehavior-behavior"></a>Utilisation du comportement ClientViaBehavior  
 Vous pouvez utiliser le comportement <xref:System.ServiceModel.Description.ClientViaBehavior> pour spécifier l'URI pour lequel le canal de transport doit être créé. Utilisez ce comportement lorsque la destination réseau immédiate n'est pas le processeur prévu du message. Cela autorise les conversations à sauts multiples lorsque l'application appelante ne connaît pas nécessairement la destination ultime ou lorsque l'en-tête `Via` de destination n'est pas une adresse.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécification du comportement du service au moment de l’exécution](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
