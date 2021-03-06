---
title: Types valeur (référence C#)
ms.date: 07/20/2015
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 49043a9fe9eabbb54176a0106007ef0d26ed795f
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172210"
---
# <a name="value-types-c-reference"></a>Types valeur (référence C#)
Les types valeur se composent de deux catégories principales :  
  
-   [Structs](../../../csharp/language-reference/keywords/struct.md)  
  
-   [Énumérations](../../../csharp/language-reference/keywords/enum.md)  
  
 Les structs appartiennent aux catégories suivantes :  
  
-   Types numériques  
  
    -   [Types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md)  
  
    -   [Types virgule flottante](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
  
    -   [decimal](../../../csharp/language-reference/keywords/decimal.md)  
  
-   [bool](../../../csharp/language-reference/keywords/bool.md)  
  
-   Structs définis par l’utilisateur.  
  
## <a name="main-features-of-value-types"></a>Principales fonctionnalités des types valeur  
 Les variables basées sur des types valeur contiennent directement des valeurs. Le fait d’assigner une variable de type valeur à une autre a pour effet de copier la valeur contenue, contrairement à une opération d’assignation de variables de type référence, qui copie une référence à l’objet mais pas l’objet lui-même.  
  
 Tous les types valeur sont implicitement dérivés de <xref:System.ValueType?displayProperty=nameWithType>.  
  
 Contrairement aux types référence, vous ne pouvez pas faire dériver un nouveau type d’un type valeur. En revanche, comme les types référence, les structs peuvent implémenter des interfaces.  
  
 Contrairement aux types référence, un type valeur ne peut pas contenir la valeur `null`. Cependant, la fonctionnalité [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md) n’autorise pas l’assignation de types valeur à `null`.  
  
 Chaque type valeur a un constructeur par défaut implicite qui initialise la valeur par défaut de ce type. Pour plus d’informations sur les valeurs par défaut des types valeur, consultez [Tableau des valeurs par défaut](../../../csharp/language-reference/keywords/default-values-table.md).  
  
## <a name="main-features-of-simple-types"></a>Principales fonctionnalités des types simples  
 Tous les types simples (ceux qui font partie intégrante du langage C#) sont des alias des types du système .NET Framework. Par exemple, [int](../../../csharp/language-reference/keywords/int.md) est un alias de <xref:System.Int32?displayProperty=nameWithType>. Pour obtenir la liste complète des alias, consultez [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md).  
  
 Les expressions constantes, dont les opérandes sont tous des constantes de type simple, sont évaluées au moment de la compilation.  
  
 Les types simples peuvent être initialisés à l’aide de littéraux. Par exemple, « A » est un littéral de type `char`, tandis que 2001 est un littéral de type `int`.  
  
## <a name="initializing-value-types"></a>Initialisation des types valeur  
 En C#, les variables locales doivent être initialisées avant d’être utilisées. Par exemple, vous pouvez déclarer une variable locale sans l’initialiser comme dans l’exemple suivant :  
  
```csharp  
int myInt;  
```  
  
 Vous ne pouvez pas l’utiliser avant de l’avoir initialisée. Vous pouvez l’initialiser à l’aide de l’instruction suivante :  
  
```csharp  
myInt = new int();  // Invoke default constructor for int type.  
```  
  
 Cette instruction est équivalente à l’instruction suivante :  
  
```csharp  
myInt = 0;         // Assign an initial value, 0 in this example.  
```  
  
 Bien entendu, vous pouvez intégrer la déclaration et l’initialisation dans une même instruction comme dans les exemples suivants :  
  
```csharp  
int myInt = new int();  
```  
  
 – ou –  
  
```csharp  
int myInt = 0;  
```  
  
 L’opérateur [new](../../../csharp/language-reference/keywords/new.md) permet d’appeler le constructeur par défaut du type spécifique et d’assigner la valeur par défaut à la variable. Dans l’exemple précédent, le constructeur par défaut a assigné la valeur `0` à `myInt`. Pour plus d’informations sur les valeurs assignées par l’appel des constructeurs par défaut, consultez [Tableau des valeurs par défaut](../../../csharp/language-reference/keywords/default-values-table.md).  
  
 Avec les types définis par l’utilisateur, l’opérateur [new](../../../csharp/language-reference/keywords/new.md) permet d’appeler le constructeur par défaut. Par exemple, l’instruction suivante appelle le constructeur par défaut du struct `Point` :  
  
```csharp  
Point p = new Point(); // Invoke default constructor for the struct.  
```  
  
 Après cet appel, le struct est considéré comme définitivement assigné ; autrement dit, tous ses membres sont initialisés avec leurs valeurs par défaut.  
  
 Pour plus d’informations sur l’opérateur new, consultez [new](../../../csharp/language-reference/keywords/new.md).  
  
 Pour plus d’informations sur la mise en forme de la sortie des types numériques, consultez [Tableau des formats des résultats numériques](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)  
 [Types](../../../csharp/language-reference/keywords/types.md)  
 [Tableaux de référence des types](../../../csharp/language-reference/keywords/reference-tables-for-types.md)  
 [Types référence](../../../csharp/language-reference/keywords/reference-types.md)
