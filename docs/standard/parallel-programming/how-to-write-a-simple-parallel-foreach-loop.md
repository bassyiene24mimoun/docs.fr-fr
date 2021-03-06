---
title: 'Comment : écrire une boucle Parallel.ForEach simple'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e3fb5fd807971aed014ba98cbb207c4483b93f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581678"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a>Comment : écrire une boucle Parallel.ForEach simple
Cet exemple montre comment utiliser une boucle <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> pour activer le parallélisme des données sur n’importe quelle source de données <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.  
  
> [!NOTE]
>  Cette documentation utilise des expressions lambda pour définir les délégués en PLINQ. Si les expressions lambda en C# ou Visual Basic ne vous sont pas familières, consultez la page [Expressions lambda en PLINQ et dans la bibliothèque parallèle de tâches](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="example"></a>Exemple  
 [!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
 [!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]  
  
 Une boule <xref:System.Threading.Tasks.Parallel.ForEach%2A> fonctionne comme une boucle <xref:System.Threading.Tasks.Parallel.For%2A>. La collection source est partitionnée et le travail est planifié sur plusieurs threads en fonction de l’environnement système. Plus il y a de processeurs sur le système, plus la méthode parallèle s’exécute rapidement. Pour certaines collections sources, une boucle séquentielle peut être plus rapide, selon la taille de la source et le type de travail exécuté. Pour plus d’informations sur les performances, consultez [Pièges potentiels dans le parallélisme des données et des tâches](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)  
  
 Pour plus d’informations sur les boucles parallèles, consultez [Guide pratique : écrire une boucle Parallel.For simple](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).  
  
 Pour utiliser <xref:System.Threading.Tasks.Parallel.ForEach%2A> avec une collection non générique, vous pouvez utiliser la méthode d’extension <xref:System.Linq.Enumerable.Cast%2A> pour convertir la collection en une collection générique, comme indiqué dans l’exemple suivant :  
  
 [!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
 [!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]  
  
 Vous pouvez également utiliser PLINQ (Parallel LINQ) pour paralléliser le traitement des sources de données <xref:System.Collections.Generic.IEnumerable%601>. PLINQ vous permet d’utiliser la syntaxe de requête déclarative pour exprimer le comportement de la boucle. Pour plus d’informations, consultez [PLINQ (Parallel LINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
-   Copiez et collez ce code dans un projet d’application console Visual Studio 2010.  
  
-   Ajoutez une référence à System.Drawing.dll  
  
-   Appuyez sur F5  
  
## <a name="see-also"></a>Voir aussi  
 [Parallélisme de données](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [Programmation parallèle](../../../docs/standard/parallel-programming/index.md)  
 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
