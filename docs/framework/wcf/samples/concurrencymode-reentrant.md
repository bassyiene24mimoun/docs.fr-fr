---
title: ConcurrencyMode Reentrant
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: d0ecd4b0c39c6a736a176a61490f454c2bab2e20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33502642"
---
# <a name="concurrencymode-reentrant"></a>ConcurrencyMode Reentrant
Cet exemple illustre la nécessité d'utiliser ConcurrencyMode.Reentrant sur une implémentation de service et les conséquences d'une telle utilisation. ConcurrencyMode.Reentrant implique que le service (plus exactement l'interface de rappel) traite un seul message à la fois à un instant donné (traitement similaire à celui proposé par le mode `ConcurencyMode.Single`). Pour garantir la sécurité des threads, Windows Communication Foundation (WCF) verrouille le `InstanceContext` traite un message afin qu’aucuns autres messages ne peuvent être traités. En mode ConcurrencyMode.Reentrant, le contexte `InstanceContext` est déverrouillé juste avant que le service n'effectue un appel externe, autorisant ainsi le prochain appel (lequel peut être réentrant tel qu'illustré dans l'exemple) et l'obtention du verrouillage lorsque le service reçoit la réponse à son appel. L'exemple illustre ce comportement en montrant comment un client et un service peuvent s'envoyer des messages en utilisant un contrat duplex.  
  
 Le contrat défini correspond à un contrat duplex dans lequel la méthode `Ping` est implémentée par le service et la méthode de rappel `Pong` par le client. Le client appelle la méthode `Ping` du serveur à l'aide d'un compteur de cycles initiant par la même l'appel. Le service s'assure que la valeur du compteur de cycles n'est pas égale à zéro, puis appelle la méthode de rappel `Pong` tout en décrémentant la valeur de ce compteur. Ce processus est illustré par l'exemple de code suivant.  
  
```  
public void Ping(int ticks)  
{  
     Console.WriteLine("Ping: Ticks = " + ticks);  
     //Keep pinging back and forth till Ticks reaches 0.  
     if (ticks != 0)  
     {  
         OperationContext.Current.GetCallbackChannel<IPingPongCallback>().Pong((ticks - 1));  
     }  
}  
```  
  
 L'implémentation de la méthode de rappel `Pong` obéit à la même logique que l'implémentation de la méthode `Ping`. Cela signifie, en d'autres termes, que cette méthode s'assure d'abord que le nombre de cycles n'est pas égal à zéro, puis qu'elle appelle la méthode `Ping` sur le canal de rappel (dans ce cas, il s'agit du canal utilisé pour envoyer le message `Ping` d'origine) tout en décrémentant la valeur du compteur de 1. Lorsque ce nombre atteint zéro, la méthode est retournée, désencapsulant toutes les réponses au premier appel initié par le client. Ce processus est illustré dans l'implémentation du rappel.  
  
```  
public void Pong(int ticks)  
{  
    Console.WriteLine("Pong: Ticks = " + ticks);  
    if (ticks != 0)  
    {  
        //Retrieve the Callback  Channel (in this case the Channel which was used to send the  
        //original message) and make an outgoing call until ticks reaches 0.  
        IPingPong channel = OperationContext.Current.GetCallbackChannel<IPingPong>();  
        channel.Ping((ticks - 1));  
    }  
}  
```  
  
 Les méthodes `Ping` et `Pong` sont toutes deux du type demande-réponse, ce qui signifie que le premier appel de la méthode `Ping` est retourné uniquement une fois l'appel de `CallbackChannel<T>.Pong()` retourné. Sur le client, la méthode `Pong` ne peut pas être retournée tant que le prochain appel de la méthode `Ping` effectué n'est pas retourné. Le rappel et le service devant tous deux effectuer des appels externes de type demande-réponse avant de pouvoir répondre à la demande en attente, le comportement ConcurrencyMode.Reentrant doit être spécifié pour leurs implémentations respectives.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="demonstrates"></a>Démonstrations  
 Pour exécuter l'exemple et générer les projets de client et de serveur. Ensuite, ouvrez deux fenêtres de commande et accédez à la \<exemple > \CS\Service\bin\debug et \<exemple > \CS\Client\bin\debug répertoires. Démarrez ensuite le service en tapant `service.exe` , puis appelez le Client.exe avec la valeur initiale du compteur de cycles comme argument d’entrée. Le code suivant illustre le résultat pour 10 cycles.  
  
```  
Prompt>Service.exe  
ServiceHost Started. Press Enter to terminate service.  
Ping: Ticks = 10  
Ping: Ticks = 8  
Ping: Ticks = 6  
Ping: Ticks = 4  
Ping: Ticks = 2  
Ping: Ticks = 0  
  
Prompt>Client.exe 10  
Pong: Ticks = 9  
Pong: Ticks = 7  
Pong: Ticks = 5  
Pong: Ticks = 3  
Pong: Ticks = 1  
```  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples Windows Workflow Foundation (WF) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples. Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
  
## <a name="see-also"></a>Voir aussi
