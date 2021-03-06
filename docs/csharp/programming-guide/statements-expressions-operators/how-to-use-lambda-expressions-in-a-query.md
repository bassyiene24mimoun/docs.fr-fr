---
title: Guide pratique pour utiliser des expressions lambda dans une requête (Guide de programmation C#)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], in LINQ
ms.assetid: 3cac4d25-d11f-4abd-9e7c-0f02e97ae06d
ms.openlocfilehash: 97abbada9ff77c6e6d4fa401e956a6bd7edca9d5
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37936761"
---
# <a name="how-to-use-lambda-expressions-in-a-query-c-programming-guide"></a>Guide pratique pour utiliser des expressions lambda dans une requête (Guide de programmation C#)
Vous n’utilisez pas d’expressions lambda directement dans la syntaxe de requête, mais vous les utilisez dans les appels de méthode qui peuvent être contenus dans des expressions de requête. En effet, certaines opérations de requête ne peuvent être exprimées que dans une syntaxe de méthode. Pour plus d’informations sur la différence entre la syntaxe de requête et la syntaxe de méthode, consultez [Syntaxe de requête et syntaxe de méthode dans LINQ](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser une expression lambda dans une requête fondée sur une méthode à l’aide de l’opérateur de requête standard <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType>. Notez que la méthode <xref:System.Linq.Enumerable.Where%2A> de cet exemple a un paramètre d’entrée du type délégué <xref:System.Func%601>, et que ce délégué prend un entier comme entrée et retourne une valeur booléenne. L’expression lambda peut être convertie en ce délégué. S’il s’agissait d’une requête [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] utilisant la méthode <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>, le type de paramètre serait un `Expression<Func<int,bool>>`, mais l’expression lambda serait exactement la même. Pour plus d’informations sur le type Expression, consultez <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>.  
  
 [!code-csharp[csProgGuideLINQ#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-lambda-expressions-in-a-query_1.cs)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser une expression lambda dans un appel de méthode d’une expression de requête. L’expression lambda est nécessaire, car l’opérateur de requête standard <xref:System.Linq.Enumerable.Sum%2A> ne peut pas être appelé à l’aide de la syntaxe de requête.  
  
 La requête regroupe d’abord les étudiants selon leurs notes, comme défini dans l’enum `GradeLevel`. Ensuite, pour chaque groupe, elle ajoute la note totale obtenue par chaque étudiant. Cela nécessite deux opérations `Sum`. Le `Sum` interne calcule la note totale obtenue par chaque étudiant, et le `Sum` externe obtient un total combiné de tous les étudiants du groupe.  
  
 [!code-csharp[csProgGuideLINQ#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-lambda-expressions-in-a-query_2.cs)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Pour exécuter ce code, copiez-collez la méthode dans la `StudentClass` qui est fournie dans [Guide pratique pour interroger une collection d’objets](../../../csharp/programming-guide/linq-query-expressions/how-to-query-a-collection-of-objects.md), puis appelez-la à partir de la méthode `Main`.  
  
## <a name="see-also"></a>Voir aussi

[Expressions lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
[Arborescences d’expressions (C#)](../concepts/expression-trees/index.md)  
