---
title: Return, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: 2f614045be1b91b9c747d961cdefd526ba1bab98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603520"
---
# <a name="return-statement-visual-basic"></a>Return, instruction (Visual Basic)
Retourne le contrôle au code qui a appelé un `Function`, `Sub`, `Get`, `Set`, ou `Operator` procédure.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a>Élément  
 `expression`  
 Requis dans un `Function`, `Get`, ou `Operator` procédure. Expression qui représente la valeur à retourner au code appelant.  
  
## <a name="remarks"></a>Notes  
 Dans un `Sub` ou `Set` procédure, le `Return` instruction équivaut à un `Exit Sub` ou `Exit Property` instruction, et `expression` ne doit pas être fourni.  
  
 Dans un `Function`, `Get`, ou `Operator` procédure, le `Return` instruction doit inclure `expression`, et `expression` doit correspondre à un type de données qui peut être converti en type de retour de la procédure. Dans un `Function` ou `Get` procédure, vous avez également la possibilité d’assigner une expression au nom de la procédure pour servir de la valeur de retour et en exécutant ensuite une `Exit Function` ou `Exit Property` instruction. Dans un `Operator` procédure, vous devez utiliser `Return``expression`.  
  
 Vous pouvez inclure autant `Return` instructions comme il convient dans la même procédure.  
  
> [!NOTE]
>  Le code dans un `Finally` bloc s’exécute après un `Return` instruction dans un `Try` ou `Catch` bloc est rencontrée, mais avant que `Return` instruction s’exécute. A `Return` instruction ne peut pas être incluse dans un `Finally` bloc.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la `Return` instruction plusieurs fois pour retourner au code appelant lorsque la procédure ne doit pas faire autre chose.  
  
 [!code-vb[VbVbalrStatements#53](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/return-statement_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Get (instruction)](../../../visual-basic/language-reference/statements/get-statement.md)  
 [Set (instruction)](../../../visual-basic/language-reference/statements/set-statement.md)  
 [Operator (instruction)](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Exit (instruction)](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Try...Catch...Finally (instruction)](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
