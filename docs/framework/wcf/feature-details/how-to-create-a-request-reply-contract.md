---
title: 'Comment : créer un contrat demande-réponse'
ms.date: 03/30/2017
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
ms.openlocfilehash: 76a3bbb9415a34218896bc561066c7ac4a30e6b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489571"
---
# <a name="how-to-create-a-request-reply-contract"></a>Comment : créer un contrat demande-réponse
Un contrat demande-réponse spécifie une méthode qui retourne une réponse. La réponse doit être envoyée et corrélée à la demande selon les termes de ce contrat. Même si la méthode ne retourne aucune réponse (`void` dans C# ou un `Sub` dans Visual Basic), l'infrastructure crée et envoie un message vide à l'appelant. Pour empêcher l'envoi d'un message de réponse vide, utilisez un contrat unidirectionnel pour l'opération.  
  
### <a name="to-create-a-request-reply-contract"></a>Pour créer un contrat demande-réponse  
  
1.  Créez une interface dans le langage de programmation de votre choix.  
  
2.  Appliquez l'attribut <xref:System.ServiceModel.ServiceContractAttribute> à l'interface.  
  
3.  Appliquez l'attribut <xref:System.ServiceModel.OperationContractAttribute> à chaque méthode que les clients peuvent appeler.  
  
4.  Facultatif. Affectez à la propriété <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> la valeur `true` pour empêcher l'envoi d'un message de réponse vide. Par défaut, toutes les opérations sont des contrats demande-réponse.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant définit un contrat pour un service de calculatrice qui fournit des méthodes `Add` et `Subtract`. La méthode `Multiply` ne fait pas partie du contrat car elle n'est pas marquée par la classe <xref:System.ServiceModel.OperationContractAttribute> et n'est pas, par conséquent, accessible aux clients.  
  
```
using System.ServiceModel;

[ServiceContract]
public interface ICalculator
{
    [OperationContract]
    // It would be equivalent to write explicitly:
    // [OperationContract(IsOneWay=false)]
    int Add(int a, int b);
    
    [OperationContract]
    int Subtract(int a, int b);
    
    int Multiply(int a, int b)
}
```
  
-   Pour plus d’informations sur la façon de spécifier des contrats d’opération, consultez la <xref:System.ServiceModel.OperationContractAttribute> classe et le <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> propriété.  
  
-   Appliquer les attributs <xref:System.ServiceModel.ServiceContractAttribute> et <xref:System.ServiceModel.OperationContractAttribute> entraîne la génération automatique de définitions de contrat de service dans un document WSDL (Web Services Description Language) une fois le service déployé. Le document est téléchargé en ajoutant `?wsdl` à l'adresse de base HTTP du service. Par exemple, `http://microsoft/CalculatorService?wsdl`.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [Conception de contrats de service](../../../../docs/framework/wcf/designing-service-contracts.md)  
 [Guide pratique pour créer un contrat duplex](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
