---
title: Implémentation du modèle de contrôle SelectionItem d'UI Automation
ms.date: 03/30/2017
helpviewer_keywords:
- Selection Item control pattern
- UI Automation, Selection Item control pattern
- control patterns, Selection Item
ms.assetid: 76b0949a-5b23-4cfc-84cc-154f713e2e12
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: abf1c1851e10036ecf46b04662d41a4d9f2667e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408656"
---
# <a name="implementing-the-ui-automation-selectionitem-control-pattern"></a>Implémentation du modèle de contrôle SelectionItem d’UI Automation
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique présente les conventions et directives à respecter pour implémenter <xref:System.Windows.Automation.Provider.ISelectionItemProvider>, notamment les informations sur les propriétés, les méthodes et les événements. Des liens vers des références supplémentaires sont répertoriés à la fin de la vue d'ensemble.  
  
 Le modèle de contrôle <xref:System.Windows.Automation.SelectionItemPattern> permet de prendre en charge les contrôles qui agissent en tant qu’éléments enfants individuels et sélectionnables de contrôles conteneurs qui implémentent <xref:System.Windows.Automation.Provider.ISelectionProvider>. Pour obtenir des exemples de contrôles qui implémentent le modèle de contrôle SelectionItem, consultez [mappage de modèle de contrôle pour les Clients UI Automation](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Conventions et recommandations en matière d'implémentation  
 Quand vous implémentez le modèle de contrôle SelectionItem, notez les conventions et recommandations suivantes :  
  
-   Les contrôles à sélection unique qui gèrent des contrôles enfants qui implémentent <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>, tels que le curseur **Résolution d’écran** dans la boîte de dialogue **Propriétés d’affichage** , doivent implémenter <xref:System.Windows.Automation.Provider.ISelectionProvider> et leurs enfants doivent implémenter <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> et <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iselectionitemprovider"></a>Membres requis pour ISelectionItemProvider  
 Les propriétés, les méthodes et les événements suivants sont requis pour implémenter <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
|Membres requis|Type de membre|Notes|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Propriété|Aucun|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Propriété|Aucun|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Méthode|Aucun|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|événement|Déclenché quand une sélection a changé de manière significative dans un conteneur et requiert l’envoi d’un plus grand nombre d’événements <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> et <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> que la constante <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> ne le permet.|  
  
-   Si le résultat d’une méthode <xref:System.Windows.Automation.SelectionItemPattern.Select%2A>, <xref:System.Windows.Automation.SelectionItemPattern.AddToSelection%2A>ou <xref:System.Windows.Automation.SelectionItemPattern.RemoveFromSelection%2A> est un élément sélectionné unique, vous devez déclencher un <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> . Sinon, envoyez <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>/ <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> selon le cas.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceptions  
 Les fournisseurs doivent lever les exceptions suivantes.  
  
|Type d'exception|Condition|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Quand l’une des tentatives suivantes est effectuée :<br /><br /> -   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A> est appelé sur un conteneur à sélection unique où <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  `true` et un élément est déjà sélectionné.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A> est appelée sur un conteneur à sélection multiple alors que <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty> = `true` et qu’un seul élément est sélectionné.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.AddToSelection%2A> est appelée sur un conteneur à sélection unique alors que <xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty> = `false` et qu’un autre élément est déjà sélectionné.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des modèles de contrôle UI Automation](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Prendre en charge des modèles de contrôle dans un fournisseur UI Automation](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Modèles de contrôle UI Automation pour les clients](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Implémentation du modèle de contrôle Selection d’UI Automation](../../../docs/framework/ui-automation/implementing-the-ui-automation-selection-control-pattern.md)  
 [Présentation de l’arborescence UI Automation](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Utiliser la mise en cache dans UI Automation](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)  
 [Exemple de fournisseur de fragment](http://msdn.microsoft.com/library/778ef1bc-8610-4bc9-886e-aeff94a8a13e)
