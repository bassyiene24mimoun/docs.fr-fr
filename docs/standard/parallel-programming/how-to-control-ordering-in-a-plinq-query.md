---
title: "Comment : contrôler l'ordre dans une requête PLINQ"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to control ordering
ms.assetid: c67eccc7-004d-4b2f-987e-919cbbd62ef7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 89e0abf711730326b6391184a2e3a1b55b303957
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580209"
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a>Comment : contrôler l'ordre dans une requête PLINQ
Ces exemples montrent comment contrôler le classement d’une requête PLINQ à l’aide de la méthode d’extension <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>.  
  
> [!WARNING]
>  Ces exemples, principalement destinés à illustrer l'utilisation, peuvent ou non s'exécuter plus rapidement que les requêtes LINQ to Objects séquentielle équivalentes.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant conserve l’ordre de la séquence source. Cela est parfois nécessaire, par exemple si certains opérateurs de requête nécessitent une séquence source classée pour produire des résultats corrects.  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre certains opérateurs de requête dont la séquence source est probablement prévue pour être classée. Ces opérateurs fonctionneront sur les séquences non classées, mais ils peuvent produire des résultats inattendus.  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 Pour exécuter cette méthode, collez-la dans la classe PLINQDataSample du projet [Exemple de données PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md), puis appuyez sur F5.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment conserver le classement pour la première partie d’une requête, comment supprimer le classement afin d’augmenter les performances d’une clause join, puis comment réappliquer le classement à la séquence de résultat finale.  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 Pour exécuter cette méthode, collez-la dans la classe PLINQDataSample du projet [Exemple de données PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md), puis appuyez sur F5.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Linq.ParallelEnumerable>  
 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
