---
title: Implémentation du modèle de contrôle Scroll d'UI Automation
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Scroll control pattern
- control patterns, Scroll
- Scroll control pattern
ms.assetid: 73d64242-6cbb-424c-92dd-dc69530b7899
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 8553bbf192a619ab5877e362b1642007432c8c64
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399538"
---
# <a name="implementing-the-ui-automation-scroll-control-pattern"></a>Implémentation du modèle de contrôle Scroll d’UI Automation
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique présente les conventions et recommandations à respecter pour implémenter <xref:System.Windows.Automation.Provider.IScrollProvider>, notamment des informations sur les événements et les propriétés. Des liens vers des références supplémentaires sont répertoriés à la fin de la rubrique.  
  
 Le modèle de contrôle <xref:System.Windows.Automation.ScrollPattern> permet de prendre en charge un contrôle qui agit comme un conteneur à défilement pour une collection d’objets enfants. Le contrôle n’est pas tenu d’utiliser les barres de défilement pour prendre en charge les fonctionnalités de défilement, bien que ce soit généralement le cas.  
  
 ![Contrôle du défilement sans barres de défilement. ] (../../../docs/framework/ui-automation/media/uia-scrollpattern-without-scrollbars.PNG "UIA_ScrollPattern_Without_Scrollbars")  
Exemple d’un contrôle de défilement qui n’utilise pas les barres de défilement  
  
 Pour obtenir des exemples de contrôles implémentant ce contrôle, consultez [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Conventions et recommandations en matière d'implémentation  
 Quand vous implémentez le modèle de contrôle Scroll, notez les conventions et recommandations suivantes :  
  
-   Les enfants de ce contrôle doivent implémenter <xref:System.Windows.Automation.Provider.IScrollItemProvider>.  
  
-   Les barres de défilement d’un contrôle conteneur ne prennent pas en charge le modèle de contrôle <xref:System.Windows.Automation.ScrollPattern> . Elles doivent prendre en charge le modèle de contrôle <xref:System.Windows.Automation.RangeValuePattern> à la place.  
  
-   Lorsque le défilement est mesuré sous forme de pourcentage, toutes les valeurs ou quantités liées à la graduation du défilement doivent être normalisées dans une plage de 0 à 100.  
  
-   Les propriétés<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> et <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> sont indépendantes de <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>.  
  
-   Si <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> = `false` alors <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> doit avoir la valeur 100 % et <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> la valeur <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>. De la même façon, si <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> = `false` alors <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> doit avoir la valeur 100 % et <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> la valeur <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>. Cela permet au client UI Automation d’utiliser ces valeurs de propriété dans la méthode <xref:System.Windows.Automation.ScrollPattern.SetScrollPercent%2A> tout en évitant une [condition de concurrence critique](http://support.microsoft.com/default.aspx?scid=kb;en-us;317723) si une direction de défilement qui n’intéresse pas le client est activée.  
  
-   <xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A> est spécifique aux paramètres régionaux. Le paramètre HorizontalScrollPercent = 100.0 doit définir l’emplacement de défilement du contrôle sur l’équivalent de sa position la plus à droite pour des langues telles que le français qui sont lues de gauche à droite. Par ailleurs, pour des langues telles que l’arabe, qui sont lues de droite à gauche, le paramètre HorizontalScrollPercent = 100.0 doit définir l’emplacement de défilement sur la position la plus à gauche.  
  
<a name="Required_Members_for_IScrollProvider"></a>   
## <a name="required-members-for-iscrollprovider"></a>Membres requis pour IScrollProvider  
 Les propriétés et méthodes suivantes sont nécessaires à l'implémentation d' <xref:System.Windows.Automation.Provider.IScrollProvider>.  
  
|Membre requis|Type de membre|Notes|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A>|Propriété|Aucun|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticalScrollPercent%2A>|Propriété|Aucun|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalViewSize%2A>|Propriété|Aucun|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticalViewSize%2A>|Propriété|Aucun|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontallyScrollable%2A>|Propriété|Aucun|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticallyScrollable%2A>|Propriété|Aucun|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A>|Méthode|Aucun|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>|Méthode|Aucune|  
  
 Ce modèle de contrôle n’est associé aucun événement.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceptions  
 Les fournisseurs doivent lever les exceptions suivantes.  
  
|Type d'exception|Condition|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> lève cette exception si un contrôle prend en charge les valeurs <xref:System.Windows.Automation.ScrollAmount.SmallIncrement> exclusivement pour le défilement horizontal ou vertical, mais qu’une valeur <xref:System.Windows.Automation.ScrollAmount.LargeIncrement> est passée.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> lève cette exception quand une valeur ne pouvant pas être convertie en valeur double est passée.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> lève cette exception quand une valeur supérieure à 100 ou inférieure à 0 est passée (sauf -1 qui est équivalent à <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>).|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> et <xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> lèvent cette exception lors d’une tentative de défilement dans une direction non prise en charge.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des modèles de contrôle UI Automation](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Prendre en charge des modèles de contrôle dans un fournisseur UI Automation](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Modèles de contrôle UI Automation pour les clients](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Présentation de l’arborescence UI Automation](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Utiliser la mise en cache dans UI Automation](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
