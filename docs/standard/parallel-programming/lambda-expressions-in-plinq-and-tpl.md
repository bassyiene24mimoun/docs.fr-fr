---
title: Expressions lambda en PLINQ et dans la bibliothèque parallèle de tâches
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Func delegate, creating with lambda expression
- Action delegate, creating with lambda expression
- lambda expressions, with Action and Func
ms.assetid: 645b2c17-29d0-4ffa-8684-430743cc2f2d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf211a35cb8864e0271032d63b5b4e9e25697e96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581178"
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a>Expressions lambda en PLINQ et dans la bibliothèque parallèle de tâches
La bibliothèque parallèle de tâches (TPL) contient de nombreuses méthodes qui utilisent l’une des familles <xref:System.Func%601?displayProperty=nameWithType> ou <xref:System.Action?displayProperty=nameWithType> de délégués comme paramètres d’entrée. Vous utilisez ces délégués pour transmettre votre logique de programme personnalisée à la boucle, la tâche ou la requête parallèle. Les exemples de code de la bibliothèque parallèle de tâches, ainsi que PLINQ, utilisent des expressions lambda pour créer des instances de ces délégués comme blocs de code inline. Cette rubrique est une brève présentation de Func et Action et vous montre comment utiliser des expressions lambda dans la bibliothèque parallèle de tâches et PLINQ.  
  
 **Remarque** Pour plus d’informations sur les délégués en général, consultez [Délégués](../../csharp/programming-guide/delegates/index.md) et [Délégués](../../visual-basic/programming-guide/language-features/delegates/index.md). Pour plus d’informations sur les expressions lambda en C# et Visual Basic, consultez [Expressions lambda](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) et [Expressions lambda](~/docs/visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
## <a name="func-delegate"></a>Func (délégué)  
 Un délégué `Func` encapsule une méthode qui renvoie une valeur. Dans une signature Func, le dernier paramètre de type ou celui le plus à droite spécifie toujours le type de renvoi. L’une des causes courantes d’erreurs de compilation consiste à tenter de transmettre deux paramètres d’entrée à un <xref:System.Func%602?displayProperty=nameWithType>. En fait, ce type ne prend qu’un paramètre d’entrée. La bibliothèque de classes Framework définit 17 versions de `Func` : <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType>, et ainsi de suite jusqu'à <xref:System.Func%6017?displayProperty=nameWithType>.  
  
## <a name="action-delegate"></a>Action (délégué)  
 Un délégué <xref:System.Action?displayProperty=nameWithType> encapsule une méthode (Sub en Visual Basic) qui ne retourne pas de valeur, ou retourne [void](~/docs/csharp/language-reference/keywords/void.md). Dans une signature de type Action, les paramètres de type représentent uniquement des paramètres d’entrée. Comme pour Func, la bibliothèque de classes Framework définit 17 versions d’Action, à partir d’une version qui n’a aucun paramètre de type dans une version qui possède 16 paramètres de type.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant pour la méthode <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> montre comment exprimer les délégués Func et Action à l’aide d’expressions lambda.  
  
 [!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
 [!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation parallèle](../../../docs/standard/parallel-programming/index.md)
