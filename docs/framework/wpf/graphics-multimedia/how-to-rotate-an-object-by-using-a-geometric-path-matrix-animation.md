---
title: "Comment : faire pivoter un objet à l'aide d'un tracé géométrique (animation de matrice)"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
- matrix animation [WPF]
ms.assetid: 877dc9aa-6bdc-4beb-8772-3efaec32c0f0
ms.openlocfilehash: 6deb593ca059d49f744226be313adb6d8781b325
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561987"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation"></a>Comment : faire pivoter un objet à l'aide d'un tracé géométrique (animation de matrice)
Cet exemple montre comment utiliser un <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> et un <xref:System.Windows.Media.MatrixTransform> à pivoter un objet le long d’un tracé géométrique défini par un <xref:System.Windows.Media.PathGeometry> objet.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> objet à animer la <xref:System.Windows.Media.MatrixTransform.Matrix%2A> propriété d’un <xref:System.Windows.Media.MatrixTransform>. Le <xref:System.Windows.Media.MatrixTransform> est appliqué à un bouton et permet de déplacer sur un tracé courbé. Étant donné que la <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> est définie sur `true`, le rectangle pivote le long de la tangente du chemin d’accès.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 Pour obtenir un exemple complet, consultez [exemple d’Animation de chemin d’accès](http://go.microsoft.com/fwlink/?LinkID=160028).  
  
 La version de code de l’exemple précédent utilisé un <xref:System.Windows.Media.Animation.Storyboard> pour animer la <xref:System.Windows.Media.EllipseGeometry>, bien qu’une animation a été appliquée. Un moyen plus simple pour appliquer une seule animation à une propriété dans le code consiste à utiliser le <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> (méthode). Si vous voulez voir un exemple, consultez l’article [Comment : animer une propriété sans utiliser de storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de l’animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Guides pratiques relatifs aux animations de tracés](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)  
 [Animation de tracés, exemple](http://go.microsoft.com/fwlink/?LinkID=160028)
