---
title: Programmation de l’arborescence des éléments de modèle
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: c5bbbba4f599801c5bffdbd19e14295ff239dfcd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516472"
---
# <a name="programming-model-item-tree"></a>Programmation de l’arborescence des éléments de modèle
Cet exemple montre comment parcourir le <xref:System.Activities.Presentation.Model.ModelItem> arborescence à l’aide de la liaison de données déclarative à partir de l’arborescence de Windows Presentation Foundation (WPF).  
  
## <a name="sample-details"></a>Détails de l'exemple  
 L'arborescence <xref:System.Activities.Presentation.Model.ModelItem> est l'abstraction utilisée par l'infrastructure du [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] pour exposer les données relatives à l'instance sous-jacente en cours de modification. L'illustration suivante est une description des différentes couches d'infrastructure dans le [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].  
  
 ![Architecture du Concepteur de flux de travail](../../../../docs/framework/windows-workflow-foundation/samples/media/workflowdesignerarch.JPG "WorkflowDesignerArch")  
  
 Un <xref:System.Activities.Presentation.Model.ModelItem> se compose d'un pointeur vers la valeur sous-jacente, ainsi que d'une collection d'objets <xref:System.Activities.Presentation.Model.ModelProperty>. Un objet <xref:System.Activities.Presentation.Model.ModelProperty>, quant à lui, se compose de données telles que le nom et le type de la propriété, puis d'un pointeur vers la valeur qui, à son tout, est un autre <xref:System.Activities.Presentation.Model.ModelItem>. Un convertisseur de valeurs est utilisé pour manipuler certains des <xref:System.Activities.Presentation.Model.ModelItem> retournés à partir d'un <xref:System.Activities.Presentation.Model.ModelProperty> pour les faire apparaître correctement dans l'arborescence. L'exemple montre ensuite comment effectuer une programmation de façon impérative sur l'arborescence <xref:System.Activities.Presentation.Model.ModelItem> à l'aide de la syntaxe impérative.  
  
```csharp  
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;  
ModelProperty mp = mi.Properties["Activities"];  
mp.Collection.Add(new Persist());  
ModelItem justAdded = mp.Collection.Last();  
justAdded.Properties["DisplayName"].SetValue("new name");  
```  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  Ouvrez la solution ProgrammingModelItemTree.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Générez la solution en sélectionnant **générer la Solution** à partir de la **générer** menu.  
  
3.  Appuyez sur F5 pour exécuter l'application. Le formulaire [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] s'affiche alors.  
  
4.  Cliquez sur le **charger WF** bouton Charger le <xref:System.Activities.Presentation.Model.ModelItem> et la lier à l’arborescence.  
  
5.  En cliquant sur le **arborescence d’éléments de modèle de modification** bouton exécute le code précédent pour ajouter un élément dans l’arborescence et définir une propriété.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples Windows Workflow Foundation (WF) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples. Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Data.IValueConverter>
