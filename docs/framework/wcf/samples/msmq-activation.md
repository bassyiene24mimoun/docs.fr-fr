---
title: MSMQ Activation
ms.date: 03/30/2017
ms.assetid: e3834149-7b8c-4a54-806b-b4296720f31d
ms.openlocfilehash: 4dc8cc2a3c6d9178f6507c87ae512a8929bd1380
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33808128"
---
# <a name="msmq-activation"></a>MSMQ Activation
Cet exemple illustre comment héberger des applications dans le service d'activation des processus Windows (WAS, Windows Process Activation Service), qui sont lues à partir d'une file d'attente de messages. Cet exemple utilise le `netMsmqBinding` et est basé sur le [bidirectionnel Communication](../../../../docs/framework/wcf/samples/two-way-communication.md) exemple. Dans cet exemple, le service est une application hébergée par le Web et le client est auto-hébergé. Les résultats, qui s'affichent sur la console, permettent d'observer le statut des bons de commande envoyés.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
> [!NOTE]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  \<InstallDrive>:\WF_WCF_Samples  
>   
>  Si ce répertoire n’existe pas, accédez à Windows Communication Foundation (WCF) lien hypertexte «http://go.microsoft.com/fwlink/?LinkId=150780» \t « _blank » et des exemples Windows Workflow Foundation (WF) pour [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] pour télécharger tous les WCF et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples. Cet exemple se trouve dans le répertoire suivant.  
>   
>  \<InstallDrive>:\Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.  
  
 Le service WAS, c'est-à-dire le nouveau mécanisme d'activation des processus pour [!INCLUDE[lserver](../../../../includes/lserver-md.md)], offre des fonctionnalités IIS désormais disponibles avec des applications non HTTP (auparavant disponibles uniquement avec des applications HTTP). Windows Communication Foundation (WCF) utilise l’interface d’adaptateur d’écouteur pour communiquer les demandes d’activation qui sont reçues sur les protocoles non HTTP pris en charge par WCF, tels que TCP, canaux nommés et MSMQ. Les fonctionnalités de réception des demandes sur les protocoles non-HTTP sont hébergées par les services Windows managés qui s'exécutent dans SMSvcHost.exe.  
  
 Le service d'adaptateur (NetMsmqActivator) de l'écouteur Net.Msmq active les applications en file d'attente en fonction des messages figurant dans cette file.  
  
 Le client envoie des bons de commande au service dans les limites de l'étendue d'une transaction. Le service traite les bons de commande qu'il reçoit via cette transaction. Le service rappelle ensuite le client en utilisant l'état des bons de commande. Pour faciliter la communication bidirectionnelle, le client et service utilisent tous deux des files d'attente pour y placer les bons de commande et leur état.  
  
 Le contrat de service `IOrderProcessor` définit des opérations de service unidirectionnelles compatibles avec les files d'attente. L'opération de service utilise le point de terminaison de réponse pour envoyer les états de bon de commande au client. L'adresse du point de terminaison de réponse correspond à l'URI de la file d'attente utilisée pour renvoyer l'état des bons de commande au client. L'application de traitement des bons de commande implémente ce contrat.  
  
```csharp  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po,   
                                           string reportOrderStatusTo);  
}  
```  
  
 Le contrat de réponse auquel envoyer l'état des bons de commande est spécifié par le client. Le client implémente le contrat d'état des bons de commande. Le service utilise le client généré de ce contrat pour renvoyer l'état des bons de commande au client.  
  
```csharp  
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```  
  
 L'opération de service traite le bon de commande envoyé. L'attribut <xref:System.ServiceModel.OperationBehaviorAttribute> est appliqué à l'opération de service pour indiquer l'inscription automatique dans la transaction utilisée pour recevoir les messages depuis la file d'attente ainsi que pour spécifier l'arrivée à échéance automatique de cette transaction au terme de l'opération de service. La classe `Orders` encapsule la fonctionnalité de traitement des bons de commande. Dans cet exemple, elle ajoute les bons de commande à un dictionnaire. Les opérations peuvent accéder à la transaction à laquelle l'opération de service s'est inscrite depuis la classe `Orders`.  
  
 L'opération de service, outre traiter des bons de commande envoyés, envoie une réponse au client l'informant de l'état des commandes.  
  
```csharp  
public class OrderProcessorService : IOrderProcessor  
{  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po, string reportOrderStatusTo)  
    {  
        Orders.Add(po);  
        Console.WriteLine("Processing {0} ", po);  
        Console.WriteLine("Sending back order status information");  
        NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
        msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
        OrderStatusClient client = new OrderStatusClient(msmqCallbackBinding, new EndpointAddress(reportOrderStatusTo));  
        // please note that the same transaction that is used to dequeue purchase order is used  
        // to send back order status  
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
        {  
            client.OrderStatus(po.PONumber, po.Status);  
            scope.Complete();  
        }  
    }  
```  
  
 La liaison du client à utiliser est spécifiée à l'aide d'un fichier de configuration.  
  
 Le nom de la file d'attente MSMQ est spécifié dans la section appSettings de ce fichier de configuration. Le point de terminaison du service est défini dans la section System.ServiceModel de ce même fichier.  
  
> [!NOTE]
>  Le nom de la file d'attente MSMQ et l'adresse du point de terminaison utilisent des conventions d'adressage légèrement différentes. Le nom de la file d’attente MSMQ utilise un point (.) pour l’ordinateur local et des barres obliques inverses comme séparateur dans son chemin d’accès. L’adresse de point de terminaison WCF spécifie un modèle net.msmq : schéma, utilise « localhost » pour l’ordinateur local et utilise des barres obliques dans son chemin d’accès. Pour lire une file d'attente hébergée sur un ordinateur distant, remplacez « . » et « localhost » par le nom de cet ordinateur.  
  
 Un fichier .svc comportant le nom de la classe est utilisé pour héberger le code de service dans WAS.  
  
 Le fichier Service.svc contient une directive permettant de créer `OrderProcessorService`.  
  
```xml  
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.ServiceModel.Samples.OrderProcessorService"%>  
```  
  
 Ce fichier contient également une directive d'assembly permettant de vérifier que System.Transactions.dll est chargé.  
  
```xml  
<%@Assembly name="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"%>  
```  
  
 Le client crée une étendue de transaction. La communication avec le service s'effectuant dans les limites de l'étendue de la transaction, elle est considérée comme une unité atomique dans laquelle l'intégralité des messages réussissent ou échouent. La transaction est validée par l'appel de la méthode `Complete` sur l'étendue de la transaction.  
  
```csharp  
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderStatusService)))  
{  
    // Open the ServiceHostBase to create listeners and start listening   
    // for order status messages.  
    serviceHost.Open();  
  
    // Create a proxy with given client endpoint configuration  
    OrderProcessorClient client = new OrderProcessorClient();  
  
    // Create the purchase order  
    PurchaseOrder po = new PurchaseOrder();  
    po.CustomerId = "somecustomer.com";  
    po.PONumber = Guid.NewGuid().ToString();  
  
    PurchaseOrderLineItem lineItem1 = new PurchaseOrderLineItem();  
    lineItem1.ProductId = "Blue Widget";  
    lineItem1.Quantity = 54;  
    lineItem1.UnitCost = 29.99F;  
  
    PurchaseOrderLineItem lineItem2 = new PurchaseOrderLineItem();  
    lineItem2.ProductId = "Red Widget";  
    lineItem2.Quantity = 890;  
    lineItem2.UnitCost = 45.89F;  
  
    po.orderLineItems = new PurchaseOrderLineItem[2];  
    po.orderLineItems[0] = lineItem1;  
    po.orderLineItems[1] = lineItem2;  
  
    //Create a transaction scope.  
    using (TransactionScope scope = new   
        TransactionScope(TransactionScopeOption.Required))  
    {  
        // Make a queued call to submit the purchase order  
        client.SubmitPurchaseOrder(po,   
       "net.msmq://localhost/private/ServiceModelSamplesOrder/OrderStatus");  
        // Complete the transaction.  
        scope.Complete();  
    }  
  
    //Closing the client gracefully closes the connection and cleans up   
    //resources  
    client.Close();  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
  
    // Close the ServiceHostBase to shutdown the service.  
    serviceHost.Close();  
    }  
```  
  
 Le code du client implémente le contrat `IOrderStatus` pour pouvoir recevoir l'état des bons de commande depuis le service. Dans ce cas, le code imprime l'état des bons de commande.  
  
```csharp  
[ServiceBehavior]  
public class OrderStatusService : IOrderStatus  
{  
    [OperationBehavior(TransactionAutoComplete = true,   
                        TransactionScopeRequired = true)]  
    public void OrderStatus(string poNumber, string status)  
    {  
        Console.WriteLine("Status of order {0}:{1} ",   
                                         poNumber , status);  
    }  
}  
```  
  
 La file d'attente de l'état des bons de commande est créée dans la méthode `Main`. La configuration du client intègre la configuration du service de l'état des bons de commande pour héberger le service de l'état des bons de commande, comme illustré dans l'exemple de configuration suivant.  
  
```csharp  
<appSettings>  
    <!-- use appSetting to configure MSMQ queue name -->  
    <add key="targetQueueName" value=".\private$\ServiceModelSamples/service.svc" />  
    <add key="responseQueueName" value=".\private$\ServiceModelSamples/OrderStatus" />  
  </appSettings>  
  
<system.serviceModel>  
  
    <services>  
      <service   
         name="Microsoft.ServiceModel.Samples.OrderStatusService">  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address="net.msmq://localhost/private/ServiceModelSamples/OrderStatus"  
                  binding="netMsmqBinding"  
                  contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
      </service>  
    </services>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
                address="net.msmq://localhost/private/ServiceModelSamples/service.svc"   
                binding="netMsmqBinding"   
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
    </client>  
  
  </system.serviceModel>  
```  
  
 Lorsque vous exécutez l'exemple, les activités du client et du service s'affichent sur leur console respective. Sur ces consoles, vous pouvez voir le serveur recevoir des messages du client. Appuyez sur le bouton ENTER de chaque console pour fermer le serveur et le client.  
  
 Le client affiche les informations d'état des bons de commande envoyées par le serveur :  
  
```Output  
Press <ENTER> to terminate client.  
Status of order 70cf9d63-3dfa-4e69-81c2-23aa4478ebed :Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Vérifiez qu'[!INCLUDE[iisver](../../../../includes/iisver-md.md)] est installé, car il est obligatoire pour l'activation WAS.  
  
2.  Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md). En outre, vous devez installer les composants d’activation non-HTTP WCF :  
  
    1.  À partir de la **Démarrer** menu, choisissez **le panneau de configuration**.  
  
    2.  Sélectionnez **programmes et fonctionnalités**.  
  
    3.  Cliquez sur **activer ou désactiver des fonctionnalités Windows**.  
  
    4.  Sous **résumé des fonctionnalités**, cliquez sur **ajouter des fonctionnalités**.  
  
    5.  Développez le **Microsoft .NET Framework 3.0** nœud et cocher la **Activation Non-HTTP de Windows Communication Foundation** fonctionnalité.  
  
3.  Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Exécutez le client en exécutant client.exe depuis une fenêtre de commande. Cette exécution génère la file d'attente et envoie un message à celle-ci. Laissez le client s'exécuter pour connaître le résultat de la lecture de ce message par le service.  
  
5.  Le service d'activation MSMQ s'exécute comme service réseau par défaut. Par conséquent, la file d'attente utilisée pour activer l'application doit recevoir et lire les autorisations pour le service réseau. Cette spécification peut être ajoutée à l'aide de Message Queuing et de la console MMC :  
  
    1.  À partir de la **Démarrer** menu, cliquez sur **exécuter**, puis tapez `Compmgmt.msc` et appuyez sur ENTRÉE.  
  
    2.  Sous **Services et Applications**, développez **Message Queuing**.  
  
    3.  Cliquez sur **files d’attente privées**.  
  
    4.  Avec le bouton droit de la file d’attente (servicemodelsamples/service.svc) et choisissez **propriétés**.  
  
    5.  Sur le **sécurité** , cliquez sur **ajouter** et donnez à lire et reçoivent des autorisations pour le Service réseau.  
  
6.  Configurez le service d'activation des processus Windows de sorte à assurer la prise en charge de l'activation MSMQ.  
  
     Pour des raisons pratiques, les étapes suivantes sont implémentées dans le fichier de commandes AddMsmqSiteBinding.cmd se trouvant dans le répertoire de l'exemple.  
  
    1.  Pour assurer la prise en charge de l'activation de net.msmq, le site Web par défaut doit d'abord être lié au protocole net.msmq. Cela peut être fait à l'aide d'appcmd.exe, installé avec l'ensemble d'outils de gestion d'[!INCLUDE[iisver](../../../../includes/iisver-md.md)]. À partir d'une invite de commandes avec élévation de privilèges (administrateur), exécutez la commande suivante.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        -+bindings.[protocol='net.msmq',bindingInformation='localhost']  
        ```  
  
        > [!NOTE]
        >  Cette commande est une ligne unique de texte.  
  
         Cette commande ajoute une liaison de site net.msmq au site Web par défaut.  
  
    2.  Bien que toutes les applications d'un site partagent la même liaison net.msmq, chacune d'elles peut activer de manière individuelle la prise en charge de net.msmq. Pour activer net.msmq pour l'application /servicemodelsamples, exécutez la commande suivante à partir d'une invite de commandes avec élévation de privilèges.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.msmq  
        ```  
  
        > [!NOTE]
        >  Cette commande est une ligne unique de texte.  
  
         Cette commande permet d’accéder à l’aide de l’application http://localhost/servicemodelsamples et via NET.MSMQ://localhost/servicemodelsamples.  
  
7.  Si vous ne l'avez pas fait précédemment, assurez-vous que le service d'activation MSMQ est activé. À partir de la **Démarrer** menu, cliquez sur **exécuter**et le type `Services.msc`. Recherche dans la liste des services pour le **adaptateur d’écouteur Net.Msmq**. Avec le bouton droit et sélectionnez **propriétés**. Définir le **Type de démarrage** à **automatique**, cliquez sur **appliquer** et cliquez sur le **Démarrer** bouton. Cette étape doit être effectuée à une seule reprise, avant la première utilisation du service d'adaptateur de l'écouteur Net.Msmq.  
  
8.  Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md). En outre, modifiez le code du client qui envoie le bon de commande en fonction du nom de l'ordinateur figurant dans l'URI de la file d'attente lors de l'envoi de ce bon. Utilisez le code suivant :  
  
    ```  
    client.SubmitPurchaseOrder(po, "net.msmq://localhost/private/ServiceModelSamples/OrderStatus");  
    ```  
  
9. Supprimez la liaison de site net.msmq que vous avez ajoutée dans le cadre de cet exemple.  
  
     Pour des raisons pratiques, les étapes suivantes sont implémentées dans le fichier de commandes RemoveMsmqSiteBinding.cmd situé dans le répertoire de l'exemple :  
  
    1.  Supprimez net.msmq de la liste de protocoles actifs en exécutant la commande suivante à partir d'une invite de commandes avec élévation de privilèges.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  Cette commande est une ligne unique de texte.  
  
    2.  Supprimez la liaison du site net.msmq en exécutant la commande suivante à partir d'une invite de commandes avec élévation de privilèges.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.msmq',bindingInformation='localhost']  
        ```  
  
        > [!NOTE]
        >  Cette commande est une ligne unique de texte.  
  
    > [!WARNING]
    >  L'exécution du fichier de commandes réinitialise le DefaultAppPool de sorte qu'il s'exécute en utilisant .NET Framework version 2.0.  
  
 Avec le transport de liaison `netMsmqBinding`, la sécurité est activée par défaut. Les propriétés `MsmqAuthenticationMode` et `MsmqProtectionLevel` déterminent toutes deux le type de sécurité du transport. Par défaut, le mode d'authentification a la valeur `Windows` et le niveau de protection a la valeur `Sign`. Pour que MSMQ fournisse la fonctionnalité d'authentification et de signature, il doit faire partie d'un domaine. Si vous exécutez cet exemple sur un ordinateur ne faisant pas partie d'un domaine, vous obtenez l'erreur suivante : « Le certificat Message Queuing interne pour l'utilisateur n'existe pas ».  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Pour exécuter l'exemple sur un ordinateur joint à un groupe de travail  
  
1.  Si votre ordinateur ne fait pas partie d'un domaine, désactivez la sécurité du transport en affectant au mode d'authentification et au niveau de protection la valeur None, tel qu'indiqué dans l'exemple de configuration suivant.  
  
    ```xml  
    <bindings>  
        <netMsmqBinding>  
            <binding configurationName="TransactedBinding">  
                <security mode="None"/>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
    ```  
  
2.  Modifiez la configuration du serveur et du client avant d'exécuter l'exemple.  
  
    > [!NOTE]
    >  L'affectation de `security mode` à `None` revient à affecter `MsmqAuthenticationMode` aux modes de sécurité `MsmqProtectionLevel`, `Message` et `None`.  
  
3.  Pour permettre l'activation sur un ordinateur associé à un groupe de travail, le service d'activation et le processus de travail doivent tous deux être exécutés sous un compte d'utilisateur spécifique (compte identique pour les deux) et les listes ACL correspondant à ce compte doivent figurer dans la file d'attente.  
  
     Pour modifier l'identité sous laquelle s'exécute le processus de travail :  
  
    1.  Exécutez Inetmgr.exe.  
  
    2.  Sous **Pools d’applications**, avec le bouton droit le **AppPool** (généralement **DefaultAppPool**) et choisissez **définir par défaut de Pool d’applications...** .  
  
    3.  Modifiez les propriétés Identity en fonction du compte d'utilisateur à utiliser.  
  
     Pour modifier l'identité sous laquelle s'exécute le service d'activation :  
  
    1.  Exécutez Services.msc.  
  
    2.  Cliquez sur le **Net.MsmqListener Adapter**, puis choisissez **propriétés**.  
  
4.  Modifier le compte dans le **ouverture de session** onglet.  
  
5.  Au niveau des groupes de travail, le service doit également s'exécuter à l'aide d'un jeton non restreint. Pour ce faire, utilisez la ligne suivante dans une fenêtre de commande :  
  
    ```  
    sc sidtype netmsmqactivator unrestricted  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Hébergement de AppFabric et exemples de persistance](http://go.microsoft.com/fwlink/?LinkId=193961)
