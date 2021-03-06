---
title: Expression de fonction (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: 29bf95a336b6f6ed5c9c310c9ea7575a91089361
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604885"
---
# <a name="function-expression-visual-basic"></a>Expression de fonction (Visual Basic)
Déclare les paramètres et le code qui définissent une expression lambda de fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`parameterlist`|Facultatif. Liste des noms de variables locales qui représentent les paramètres de cette procédure. Les parenthèses doivent être présents même lorsque la liste est vide. Consultez [liste de paramètres](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`expression`|Obligatoire. Une expression unique. Le type de l’expression est le type de retour de la fonction.|  
|`statements`|Obligatoire. Une liste d’instructions qui retourne une valeur à l’aide de la `Return` instruction. (Consultez [instruction Return](../../../visual-basic/language-reference/statements/return-statement.md).) Le type de la valeur retournée est le type de retour de la fonction.|  
  
## <a name="remarks"></a>Notes  
 A *expression lambda* est une fonction sans nom qui calcule et retourne une valeur. Vous pouvez utiliser une expression lambda partout où vous pouvez utiliser un type délégué, sauf en tant qu’argument à `RemoveHandler`. Pour plus d’informations sur les délégués et l’utilisation d’expressions lambda avec les délégués, consultez [instruction Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md) et [Conversion souple en délégué](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="lambda-expression-syntax"></a>Syntaxe d’expression lambda  
 La syntaxe d’une expression lambda ressemble à celle d’une fonction standard. Les différences sont les suivantes :  
  
-   Une expression lambda n’a pas un nom.  
  
-   Expressions lambda ne peut pas avoir de modificateurs, tels que `Overloads` ou `Overrides`.  
  
-   Les expressions lambda n’utilisent pas une `As` clause pour désigner le type de retour de la fonction. Au lieu de cela, le type est déduit à partir de la valeur que le corps d’une expression lambda sur une ligne a la valeur ou la valeur de retour d’une expression lambda multiligne. Par exemple, si le corps d’une expression lambda sur une ligne est `Where cust.City = "London"`, son type de retour est `Boolean`.  
  
-   Le corps d’une expression lambda sur une ligne doit être une expression, pas une instruction. Le corps peut se composer d’un appel à une procédure function, mais pas d’un appel à une procédure sub.  
  
-   Tous les paramètres doivent avoir indiqué les types de données ou de l’ensemble doit être déduit.  
  
-   Paramètres facultatifs et Paramarray ne sont pas autorisées.  
  
-   Paramètres génériques ne sont pas autorisées.  
  
## <a name="example"></a>Exemple  
 Les exemples suivants montrent deux façons de créer des expressions lambda simples. Le premier utilise un `Dim` pour fournir un nom pour la fonction. Pour appeler la fonction, vous envoyez une valeur pour le paramètre.  
  
 [!code-vb[VbVbalrLambdas#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]  
  
 [!code-vb[VbVbalrLambdas#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]  
  
## <a name="example"></a>Exemple  
 Vous pouvez également déclarer et exécuter la fonction en même temps.  
  
 [!code-vb[VbVbalrLambdas#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]  
  
## <a name="example"></a>Exemple  
 Voici un exemple d’une expression lambda qui incrémente son argument et retourne la valeur. L’exemple montre les deux la syntaxe d’expression lambda multiligne ou de plusieurs lignes pour une fonction. Pour plus d’exemples, consultez [Expressions Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]  
  
## <a name="example"></a>Exemple  
 Expressions lambda sous-tendent à de nombreux opérateurs de requête de [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]et peuvent être utilisées explicitement dans les requêtes basées sur une méthode. L’exemple suivant montre une manière classique [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] requête, suivie de la traduction de la requête au format de la méthode.  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 Pour plus d’informations sur les méthodes de requête, consultez [requêtes](../../../visual-basic/language-reference/queries/queries.md). Pour plus d’informations sur les opérateurs de requête standard, consultez [vue d’ensemble des opérateurs de requête Standard](../../programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Expressions lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [Opérateurs et expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Instructions](../../../visual-basic/programming-guide/language-features/statements.md)  
 [Comparaisons de valeurs](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [Expressions booléennes](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [If (opérateur)](../../../visual-basic/language-reference/operators/if-operator.md)  
 [Conversion simplifiée des délégués](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
