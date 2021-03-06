---
title: Address Headers
ms.date: 03/30/2017
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
ms.openlocfilehash: 276649c17a04822eb27eb4e3ed9cbe711b384edc
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803788"
---
# <a name="address-headers"></a>Address Headers
Cet exemple montre comment les clients peuvent passer des paramètres de référence à un service à l’aide de Windows Communication Foundation (WCF).  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 La spécification WS-Addressing définit la référence de point de terminaison permettant de s'adresser à un point de terminaison de service Web particulier. Dans WCF, les références de point de terminaison sont modélisées à l’aide de la `EndpointAddress` classe - `EndpointAddress` est le type du champ adresse de la `ServiceEndpoint` classe.  
  
 Chaque référence dans le modèle de référence de point de terminaison peut contenir des paramètres ajoutant des informations d'identification supplémentaires. Dans WCF, ces paramètres de référence sont modélisés comme des instances de `AddressHeader` classe.  
  
 Dans cet exemple, le client ajoute un paramètre de référence à l'adresse `EndpointAddress` de point de terminaison du client. Le service recherche ce paramètre et utilise sa valeur dans la logique de son opération « Hello ».  
  
## <a name="client"></a>Client  
 Pour que le client envoie un paramètre de référence, il doit ajouter un en-tête `AddressHeader` à l'adresse `EndpointAddress` du `ServiceEndpoint`. La classe `EndpointAddress` étant immuable, le changement d'une adresse de point de terminaison doit être effectué à l'aide de la classe `EndpointAddressBuilder`. Le code suivant initialise le client pour envoyer un paramètre de référence dans le cadre de son message.  
  
```csharp   
HelloClient client = new HelloClient();  
EndpointAddressBuilder builder =   
    new EndpointAddressBuilder(client.Endpoint.Address);  
AddressHeader header =   
    AddressHeader.CreateAddressHeader(IDName, IDNamespace, "John");  
builder.Headers.Add(header);  
client.Endpoint.Address = builder.ToEndpointAddress();  
```  
  
 Le code crée un `EndpointAddressBuilder` en utilisant comme valeur initiale l'adresse `EndpointAddress` d'origine. Il ajoute alors l'en-tête d'adresse récemment créé. L'appel de `CreateAddressHeadercreates` crée un en-tête avec une valeur, un nom et un espace de noms particuliers. Dans cet exemple, la valeur est « John ». Une fois l'en-tête ajouté au générateur, la méthode `ToEndpointAddress()` reconvertit le générateur (altérable) en une adresse de point de terminaison (immuable) assignée de nouveau au champ d'adresse de point de terminaison du client.  
  
 À présent, lorsque le client appelle la méthode `Console.WriteLine(client.Hello());`, le service peut obtenir la valeur de ce paramètre d'adresse, comme en témoigne le résultat obtenu par le client.  
  
 `Hello, John`  
  
## <a name="server"></a>Serveur  
 L'implémentation de l'opération de service `Hello()` utilise le contexte `OperationContext` actuel pour inspecter la valeur des en-têtes figurant dans le message entrant.  
  
```csharp   
string id = null;  
// look at headers on incoming message  
for (int i = 0;   
     i < OperationContext.Current.IncomingMessageHeaders.Count;   
     ++i)  
{  
    MessageHeaderInfo h = OperationContext.Current.IncomingMessageHeaders[i];  
    // for any reference parameters with the correct name & namespace  
    if (h.IsReferenceParameter &&   
        h.Name == IDName &&   
        h.Namespace == IDNamespace)  
    {  
        // read the value of that header  
        XmlReader xr = OperationContext.Current.IncomingMessageHeaders.GetReaderAtHeader(i);  
        id = xr.ReadElementContentAsString();  
    }  
}  
return "Hello, " + id;  
```  
  
 Le code recherche les en-têtes correspondant à des paramètres de référence contenant le nom défini en parcourant tous les en-têtes figurant dans le message entrant. Lorsqu'il trouve un tel paramètre, il lit sa valeur, puis la stocke dans la variable « id ».  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples Windows Workflow Foundation (WF) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples. Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`  
  
## <a name="see-also"></a>Voir aussi
