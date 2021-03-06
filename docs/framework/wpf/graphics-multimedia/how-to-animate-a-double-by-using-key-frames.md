---
title: "Comment : animer un double à l'aide d'images clés"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Doubles [WPF], animating with key frames
- animation [WPF], Doubles with key frames
- key frames [WPF], animating Doubles with
ms.assetid: 3a1a7dba-7694-4907-8a2f-3408baebfa82
ms.openlocfilehash: 4adeb858ab1b69ef1b00f7bf3b6868dbcbbc4154
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557431"
---
# <a name="how-to-animate-a-double-by-using-key-frames"></a>Comment : animer un double à l'aide d'images clés
Cet exemple montre comment animer la valeur d’une propriété qui prend un <xref:System.Double> à l’aide d’images clés.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant déplace un rectangle sur l’écran. L’exemple utilise le <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> classe pour animer la <xref:System.Windows.Media.TranslateTransform.X%2A> propriété d’un <xref:System.Windows.Media.TranslateTransform> appliqué à un <xref:System.Windows.Shapes.Rectangle>. Cette animation, répétée indéfiniment, utilise trois images clés de la manière suivante :  
  
1.  Pendant les trois premières secondes, utilise une instance de la <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> classe pour déplacer le rectangle le long d’un chemin d’accès à un taux stable à partir de sa position de départ à la position 500. Images clés linéaires comme <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> créer une transition linéaire fluide entre les valeurs.  
  
2.  À la fin de la quatrième seconde, utilise une instance de la <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> classe pour déplacer soudainement le rectangle à la position suivante. Les images clés discrètes telles que <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> créer soudains entre les valeurs. Dans cet exemple, le rectangle se trouve à la position de départ et passe subitement à la position 500.  
  
3.  Dans les deux dernières secondes, utilise une instance de la <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> classe pour ramener le rectangle à sa position de départ. Les images clés spline comme <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> créer une transition entre des valeurs en fonction de la valeur de la <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> propriété. Dans cet exemple, le rectangle commence par se déplacer lentement, puis accélère de façon exponentielle jusqu’à la fin du segment temporel.  
  
 [!code-csharp[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/AltDoubleAnimationUsingKeyFramesExample.cs#altdoubleanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/altdoubleanimationusingkeyframesexample.vb#altdoubleanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/AltDoubleAnimationUsingKeyFramesExample.xaml#altdoubleanimationusingkeyframeswholepage)]  
  
 Pour l’exemple complet, consultez la page [Animation d’image clé, exemple](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
 Par souci de cohérence avec d’autres exemples d’animation, les versions de code de cet exemple montre comment utilisent un <xref:System.Windows.Media.Animation.Storyboard> objet pour appliquer le <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>. Lorsque vous appliquez une animation unique dans le code, il est également plus simple d’utiliser le <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> méthode au lieu d’utiliser un <xref:System.Windows.Media.Animation.Storyboard>. Si vous voulez voir un exemple, consultez l’article [Comment : animer une propriété sans utiliser de storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>  
 <xref:System.Windows.Shapes.Rectangle>  
 <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>  
 [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Guides pratiques relatifs aux images clés](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
