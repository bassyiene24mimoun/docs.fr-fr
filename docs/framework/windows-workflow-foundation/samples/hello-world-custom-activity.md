---
title: Activité personnalisée Hello World
ms.date: 03/30/2017
ms.assetid: 72b1dd0a-9aad-47d5-95a9-a1024ee1d0a1
ms.openlocfilehash: 35ae5933515b3280b0d8d95157c8dd5f40f7b320
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515837"
---
# <a name="hello-world-custom-activity"></a>Activité personnalisée Hello World
Cet exemple illustre plusieurs fonctionnalités clés de Windows Workflow Foundation (WF), y compris la création d’une activité personnalisée simple. Certaines des fonctionnalités présentées dans cet exemple créent une activité personnalisée en C# et utilisent les arguments `in` et `out` (<xref:System.Activities.InArgument> et <xref:System.Activities.OutArgument>).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples Windows Workflow Foundation (WF) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples. Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\HelloWorld`  
  
## <a name="creating-a-workflow-in-code"></a>Création d'un workflow dans le code  
 Dans cet exemple, deux activités personnalisées sont créées à l'aide de code C#. Les deux activités personnalisées héritent directement ou indirectement d'<xref:System.Activities.Activity%601> pour retourner une valeur unique. L'avantage de l'utilisation de la valeur de retour générique, plutôt que d'hériter de la classe <xref:System.Activities.Activity> non générique, est que certaines activités (telles que <xref:System.Activities.Statements.Assign>) peuvent accéder à la valeur de retour lorsqu'elles sont utilisées dans le cadre d'une activité composée.  
  
 AppendString  
 Cette activité hérite d'<xref:System.Activities.Activity%601>, et utilise une activité <xref:System.Activities.Statements.Assign> qui concatène deux chaînes.  
  
 PrependString  
 Cette activité hérite directement de <xref:System.Activities.CodeActivity%601>, et crée des fonctionnalités semblables à l'activité `AppendString`, laquelle utilise la logique implémentée au lieu d'être composée d'une activité préexistante.  
  
 Les fichiers suivants sont inclus dans ce projet :  
  
 AppendString.cs  
 Activité personnalisée qui ajoute des chaînes ensemble. Il accepte une chaîne et combine avec une chaîne de texte littéral « says hello world », pour former un message complet en tant que sortie.  
  
 PrependString.cs  
 Cette activité fait précéder une chaîne d'entrée d'une chaîne prédéfinie.  
  
 Sequence1.xaml  
 Workflow qui utilise les activités personnalisées `AppendString` et `PrependString`.  
  
 Program.cs  
 Programme qui exécute le workflow.  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution HelloWorld.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl+Maj+B.  
  
3.  Pour exécuter la solution, appuyez sur F5.