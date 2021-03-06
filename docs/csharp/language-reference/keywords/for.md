---
title: for (référence C#)
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: beac7727c8ce83d8ea20f0fc578f80ceef3053e7
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207920"
---
# <a name="for-c-reference"></a>for (référence C#)

L’instruction `for` exécute une instruction ou un bloc d’instructions jusqu’à ce qu’une expression booléenne spécifique corresponde à la valeur `true`.

À tout moment dans le bloc d’instructions `for`, vous pouvez sortir de la boucle à l’aide de l’instruction [break](break.md), ou passer à l’itération suivante de la boucle à l’aide de l’instruction [continue](continue.md). Vous pouvez également quitter une boucle `for` en utilisant les instructions [goto](goto.md), [return](return.md) ou [throw](throw.md).
  
## <a name="structure-of-the-for-statement"></a>Structure de l’instruction `for`

Chaque instruction `for` définit des sections *initialiseur*, *condition* et *itérateur* :
  
```csharp
for (initializer; condition; iterator)  
    body  
```

Ces trois sections sont facultatives. Le corps de la boucle est une instruction ou un bloc d’instructions.

L’exemple suivant montre l’instruction `for` avec toutes les sections définies :

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a>La section *initialiseur*

Les instructions figurant dans la section *initialiseur* sont exécutées une seule fois, avant d’entrer dans la boucle. La section *initialiseur* contient au choix :

- La déclaration et l’initialisation d’une variable de boucle locale, qui n’est pas accessible à partir de l’extérieur de la boucle, ou

- Zéro, une ou plusieurs expressions d’instruction parmi celles de la liste suivante, séparées par des virgules :

  - Instruction d’[assignation](../operators/assignment-operator.md)

  - Appel d’une méthode  

  - Expression d’[incrémentation](../operators/increment-operator.md) préfixée ou suffixée, telle que `++i` ou `i++`  

  - Expression de [décrémentation](../operators/decrement-operator.md) préfixée ou suffixée, telle que `--i` ou `i--`  

  - Création d’un objet à l’aide du mot clé [new](new-operator.md)

  - Expression [await](await.md)

La section *initialiseur* dans l’exemple ci-dessus déclare et initialise la variable de boucle locale `i` :

```csharp
int i = 0
```

### <a name="the-condition-section"></a>La section *condition*

La section *condition*, si elle est présente, doit être une expression booléenne. Cette expression est évaluée avant chaque itération de boucle. Si la section *condition* est absente ou que l’expression booléenne est `true`, l’itération suivante de la boucle est exécutée ; sinon, la boucle est fermée.

La section *condition* dans l’exemple ci-dessus détermine si la boucle se termine en fonction de la valeur de la variable de boucle locale :

```csharp
i < 5
```

### <a name="the-iterator-section"></a>La section *itérateur*

La section *itérateur* définit ce qui se produit après chaque itération du corps de la boucle. La section *itérateur* contient zéro, une ou plusieurs des expressions d’instruction suivantes, séparées par des virgules :  

- Instruction d’[assignation](../operators/assignment-operator.md)

- Appel d’une méthode  

- Expression d’[incrémentation](../operators/increment-operator.md) préfixée ou suffixée, telle que `++i` ou `i++`  

- Expression de [décrémentation](../operators/decrement-operator.md) préfixée ou suffixée, telle que `--i` ou `i--`  

- Création d’un objet à l’aide du mot clé [new](new-operator.md)

- Expression [await](await.md)

La section *itérateur* dans l’exemple ci-dessus incrémente la variable de boucle locale :

```csharp
i++
```

## <a name="examples"></a>Exemples

L’exemple suivant illustre plusieurs utilisations moins courantes des sections d’instruction `for` : l’attribution d’une valeur à une variable de boucle externe dans la section *initialiseur*, l’appel d’une méthode dans les sections *initialiseur* et *itérateur*, et la modification des valeurs de deux variables dans la section *itérateur*. Sélectionnez **Exécuter** pour exécuter l’exemple de code. Après cela, vous pouvez modifier le code et le réexécuter.
  
[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]
  
L’exemple suivant définit la boucle `for` infinie :
  
[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]
  
## <a name="c-language-specification"></a>Spécification du langage C#  

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
  
## <a name="see-also"></a>Voir aussi

[L’instruction for (spécification du langage C#)](/dotnet/csharp/language-reference/language-specification/statements#the-for-statement)  
[Référence C#](../index.md)  
[Guide de programmation C#](../../programming-guide/index.md)  
[Mots clés C#](index.md)  
[foreach, in](foreach-in.md)  
[for, instruction (C++)](/cpp/cpp/for-statement-cpp)  
[Instructions d’itération](iteration-statements.md)
