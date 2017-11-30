---
title: "Comment : définir la largeur d’une fenêtre à partir d’une Page"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- width of windows [WPF], setting from a page
- windows [WPF], setting width from a page
- pages [WPF], setting window width from
ms.assetid: 31601c92-7889-472a-b07e-bf675ad21c92
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7354a6c3f1b913494da9ad45181a0c7741a1cfa2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-set-the-width-of-a-window-from-a-page"></a><span data-ttu-id="ed8cd-102">Comment : définir la largeur d’une fenêtre à partir d’une Page</span><span class="sxs-lookup"><span data-stu-id="ed8cd-102">How to: Set the Width of a Window from a Page</span></span>
<span data-ttu-id="ed8cd-103">Cet exemple illustre comment définir la largeur de la fenêtre à partir d’un <xref:System.Windows.Controls.Page>.</span><span class="sxs-lookup"><span data-stu-id="ed8cd-103">This example illustrates how to set the width of the window from a <xref:System.Windows.Controls.Page>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed8cd-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="ed8cd-104">Example</span></span>  
 <span data-ttu-id="ed8cd-105">A <xref:System.Windows.Controls.Page> pouvez définir la largeur de sa fenêtre hôte en définissant <xref:System.Windows.Controls.Page.WindowWidth%2A>.</span><span class="sxs-lookup"><span data-stu-id="ed8cd-105">A <xref:System.Windows.Controls.Page> can set the width of its host window by setting <xref:System.Windows.Controls.Page.WindowWidth%2A>.</span></span> <span data-ttu-id="ed8cd-106">Cette propriété autorise le <xref:System.Windows.Controls.Page> ne pas avoir une connaissance explicite du type de fenêtre qui l’héberge.</span><span class="sxs-lookup"><span data-stu-id="ed8cd-106">This property allows the <xref:System.Windows.Controls.Page> to not have explicit knowledge of the type of window that hosts it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ed8cd-107">Pour définir la largeur d’une fenêtre en utilisant <xref:System.Windows.Controls.Page.WindowWidth%2A>, un <xref:System.Windows.Controls.Page> doit être l’enfant d’une fenêtre.</span><span class="sxs-lookup"><span data-stu-id="ed8cd-107">To set the width of a window using <xref:System.Windows.Controls.Page.WindowWidth%2A>, a <xref:System.Windows.Controls.Page> must be the child of a window.</span></span>  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowWidthXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowWidthPage.xaml#setpagewindowwidthxaml)]