---
title: ByteStream Encoder
ms.date: 03/30/2017
ms.assetid: e674a8ab-f79a-4a93-b984-54b34392dafc
ms.openlocfilehash: ab9ccf47527dcf7f01f272f09b3b341d30fbd8d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="bytestream-encoder"></a>ByteStream Encoder
Cet exemple montre comment créer un `ByteStreamHttpBinding`, un <xref:System.ServiceModel.Channels.Binding> qui illustre les fonctionnalités de l'encodeur de flux d'octets.  
  
## <a name="discussion"></a>Discussion  
 Cet exemple montre comment créer un <xref:System.ServiceModel.Channels.Binding> standard à l'aide des éléments de liaison standard <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> et <xref:System.ServiceModel.Channels.HttpTransportBindingElement>. Cet exemple montre comment utiliser l'encodeur de flux d'octets pour charger et télécharger une image. L'encodeur de flux d'octets ne prend en charge que le transport HTTP et ne prend pas en charge les fonctionnalités telles que la messagerie fiable ou la sécurité. Le seul <xref:System.ServiceModel.Channels.MessageVersion> pris en charge est <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.  
  
> [!IMPORTANT]
>  Si vous exécutez cet exemple dans [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)] ou [!INCLUDE[win7_client_firstref](../../../../includes/win7-client-firstref-md.md)], veillez à exécuter [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] avec des privilèges élevés.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples Windows Workflow Foundation (WF) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples. Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\ByteStreamEncoder`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Ouvrez le fichier ByteStreamHttpBinding.sln dans [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Démarrer une nouvelle instance du projet ByteStreamHttpBindingServer en cliquant sur le projet dans l’Explorateur de solutions et en sélectionnant **déboguer**, puis **démarrer une nouvelle instance** dans le menu contextuel.  
  
3.  Démarrer une nouvelle instance du projet ByteStreamHttpBindingClient en cliquant sur le projet dans l’Explorateur de solutions et en sélectionnant **déboguer**, **démarrer une nouvelle instance** dans le menu contextuel.
