---
title: Suivi de workflow visuel
ms.date: 03/30/2017
ms.assetid: 0143448f-2044-40a0-8a3d-941f6d12468b
ms.openlocfilehash: f010bdcf6004e84fd346d0e8649c87c008cad122
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516911"
---
# <a name="visual-workflow-tracking"></a>Suivi de workflow visuel
Cet exemple montre comment écrire une application de suivi de workflow visuel à l'aide des fonctionnalités de débogage disponibles via le [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].  
  
## <a name="sample-details"></a>Détails de l'exemple  
 L'application exécute un workflow d'organigramme simple (défini dans Workflow.xaml) et héberge à nouveau le concepteur de workflow pour afficher le workflow en cours d'exécution. Lorsque le workflow est exécuté, l'activité en cours d'exécution est indiquée par un contour jaune et une flèche de débogage. En outre, les enregistrements de suivi générés par le workflow s'affichent également dans la fenêtre d'application. Pour plus d’informations sur le suivi de flux de travail, consultez [suivi et traçage de Workflow](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md). Pour plus d’informations sur le réhébergement du Concepteur de flux de travail, consultez [réhébergement du Concepteur de flux de travail](../../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md).  
  
 Le simulateur de workflow fonctionne en conservant deux dictionnaires. L'un contient un mappage entre l'objet d'activité en cours d'exécution et le numéro de ligne XAML dans lequel l'activité est instanciée. L'autre contient un mappage entre l'ID de l'instance d'activité et l'objet d'activité. Lorsque les enregistrements de suivi sont émis à l'aide d'un modèle de suivi personnalisé, l'application détermine l'ID d'instance de l'activité en cours d'exécution et le mappe à nouveau au fichier XAML qui l'a instancié. Le concepteur de workflow réhébergé a ensuite pour instruction de mettre en surbrillance l'activité sur l'aire du concepteur et d'utiliser la même méthode que le débogueur de workflow, en dessinant spécifiquement une bordure jaune autour de l'activité et en affichant une flèche jaune le long du côté gauche du concepteur.  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  Ouvrez le fichier WorkflowSimulator.sln à partir du répertoire de l'exemple dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Appuyez sur Ctrl+Maj+B pour générer la solution.  
  
3.  Appuyez sur CTRL+F5 pour exécuter l'exemple. Cela affiche le fichier Workflow.xaml dans une fenêtre de concepteur de workflow réhébergé.  
  
4.  Cliquez sur le **fichier** menu et sélectionnez **exécuter le flux de travail...** .  
  
5.  Notez que l'activité en cours d'exécution est mise en surbrillance comme décrit précédemment et que les enregistrements de suivi sont affichés à le côté droit de la fenêtre d'application.  
  
6.  Lorsque le workflow est terminé, vous pouvez cliquer sur l'un des enregistrements de suivi pour vérifier à quelle activité il correspond.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples Windows Workflow Foundation (WF) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples. Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\VisualWorkflowTracking`