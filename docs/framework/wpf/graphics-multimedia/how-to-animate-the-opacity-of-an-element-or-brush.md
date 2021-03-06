---
title: "Comment : animer l'opacité d'un élément ou d'un pinceau"
ms.date: 03/30/2017
helpviewer_keywords:
- opacity [WPF], animating
- animation [WPF], Opacity property
ms.assetid: 572af23b-39dd-48d1-9db5-4bca56a4b3d3
ms.openlocfilehash: a45bf0344c10e1214aa5218e25e9bd9a87d5ea60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559658"
---
# <a name="how-to-animate-the-opacity-of-an-element-or-brush"></a>Comment : animer l'opacité d'un élément ou d'un pinceau
Pour rendre un élément d’infrastructure apparaître et disparaître, vous pouvez animer ses <xref:System.Windows.UIElement.Opacity%2A> propriété, ou vous pouvez animer la <xref:System.Windows.Media.Brush.Opacity%2A> propriété de la <xref:System.Windows.Media.Brush> (ou pinceaux) utilisé pour peindre. Animation opacité de l’élément rend et ses enfants apparaître et disparaître, mais animer le pinceau utilisé pour peindre l’élément vous permet d’être plus sélectif sur la partie de l’élément en fondu. Par exemple, vous pouvez animer l’opacité d’un pinceau utilisé pour peindre l’arrière-plan d’un bouton. Cela entraînerait l’arrière-plan du bouton à la disparition en fondu de vue, tout en laissant son texte complètement opaque.  
  
> [!NOTE]
>  Animation le <xref:System.Windows.Media.Brush.Opacity%2A> d’un <xref:System.Windows.Media.Brush> offre des avantages de performances sur l’animation le <xref:System.Windows.UIElement.Opacity%2A> propriété d’un élément.  
  
 Dans l’exemple suivant, deux boutons sont animés de sorte qu’elles disparaissent et. L’opacité de la première <xref:System.Windows.Controls.Button> est animée de `1.0` à `0.0` sur un <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de cinq secondes. Le deuxième bouton est également animé, mais l’opacité de SolidColorBrush utilisé pour peindre son <xref:System.Windows.Controls.Control.Background%2A> est animée au lieu de l’opacité du bouton entier. Lorsque l’exemple est exécuté, le premier bouton atténue complètement, et pendant que l’arrière-plan du deuxième bouton en fondu et. Son texte et sa bordure restent entièrement opaques.  
  
## <a name="example"></a>Exemple  
 [!code-xaml[timingbehaviors_snip#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/OpacityAnimationExample.xaml#10)]  
  
 Code a été omis de cet exemple. L’exemple complet montre également comment animer l’opacité d’un <xref:System.Windows.Media.Color> au sein d’un <xref:System.Windows.Media.LinearGradientBrush>.  Pour l’exemple complet, consultez la [animation de l’opacité d’un élément, exemple](http://go.microsoft.com/fwlink/?LinkID=159968).
