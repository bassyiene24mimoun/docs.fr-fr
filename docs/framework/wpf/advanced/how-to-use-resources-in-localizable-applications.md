---
title: Guide pratique pour utiliser des ressources dans des applications localisables
ms.date: 03/30/2017
helpviewer_keywords:
- applications [WPF], localizable
- localizable applications [WPF]
ms.assetid: 08539ad6-7fca-4f34-b82b-ff439e11dfa7
ms.openlocfilehash: 82a24feb4008b6cfd7c1751c6449c0d8515ffe87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544701"
---
# <a name="how-to-use-resources-in-localizable-applications"></a>Guide pratique pour utiliser des ressources dans des applications localisables
La localisation consiste à adapter une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] à différentes cultures. Pour ce faire, le texte (tels que les titres, légendes, éléments de liste et ainsi de suite) doit être traduit. Pour faciliter la traduction, les éléments à traduire sont rassemblés dans des fichiers de ressources. Consultez [localiser une Application](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md) pour plus d’informations sur la création d’un fichier de ressources pour la localisation. Pour rendre un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] localisable, les développeurs doivent générer toutes les ressources localisables dans un assembly de ressources d’application. L’assembly de ressources est localisé dans différentes langues, et le code-behind utilise la gestion des ressources [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] à charger. Un des fichiers requis pour un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application est un fichier projet (.proj). Toutes les ressources que vous utilisez dans votre application doivent être comprises dans le fichier projet. L'exemple de code suivant illustre ce point.  
  
## <a name="example"></a>Exemple  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `<Resource Include="data\picture1.jpg"/>`  
  
 `<EmbeddedResource Include="data\stringtable.en-US.restext"/>`  
  
 Pour utiliser une ressource dans votre application, vous instanciez <xref:System.Resources.ResourceManager> et charger la ressource que vous souhaitez utiliser. Le code suivant montre comment procéder.  
  
 [!code-csharp[LocalizationResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]
