---
title: "Comment : personnaliser l'apparence des lignes du contrôle DataGridView Windows Forms"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- rows [Windows Forms], customizing in DataGridView control
- DataGridView control [Windows Forms], customizing rows
ms.assetid: d40b53d2-7e7c-48c5-8570-6e79d15c3bbb
ms.openlocfilehash: 343e637eb5250ff4d6a1e70660dc76453e632776
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526277"
---
# <a name="how-to-customize-the-appearance-of-rows-in-the-windows-forms-datagridview-control"></a>Comment : personnaliser l'apparence des lignes du contrôle DataGridView Windows Forms
Vous pouvez contrôler l'apparence des lignes <xref:System.Windows.Forms.DataGridView> en gérant l'un ou l'autre des événements <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> et <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> (ou les deux). Ces événements sont conçus pour que vous puissiez peindre uniquement ce que vous souhaitez, tout en laissant le contrôle <xref:System.Windows.Forms.DataGridView> peindre le reste. Par exemple, si vous souhaitez peindre un arrière-plan personnalisé, vous pouvez gérer l'événement <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> et laisser chaque cellule peindre son propre contenu de premier plan. Vous pouvez également laisser les cellules se peindre elles-mêmes et ajouter du contenu de premier plan personnalisé dans un gestionnaire pour l'événement <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>. Vous pouvez aussi désactiver la peinture des cellules et peindre tout vous-même dans un gestionnaire d'événements <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>.  
  
 L'exemple de code suivant implémente des gestionnaires pour les deux événements pour fournir un arrière-plan de sélection dégradé et du contenu de premier plan personnalisé qui s'étend sur plusieurs colonnes.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.Windows.Forms.DataGridViewRowPainting#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/CS/datagridviewrowpainting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewRowPainting#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/VB/datagridviewrowpainting.vb#00)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
-   Références aux assemblys System, System.Drawing et System.Windows.Forms.  
  
 Pour plus d’informations sur la création de cet exemple à partir de la ligne de commande pour Visual Basic ou Visual c#, consultez [génération à partir de la ligne de commande](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [de ligne de commande avec csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Vous pouvez également générer cet exemple dans Visual Studio en collant le code dans un nouveau projet.  Consultez également la page [Comment : compiler et exécuter un exemple complet de code Windows Forms à l’aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>  
 [Personnalisation du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [Architecture du contrôle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)
