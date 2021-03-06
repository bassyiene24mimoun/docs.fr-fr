---
title: double, mot clé (référence C#)
ms.date: 07/20/2015
f1_keywords:
- double
- double_CSharpKeyword
helpviewer_keywords:
- double data type [C#]
ms.assetid: 0980e11b-6004-4102-abcf-cfc280fc6991
ms.openlocfilehash: 8e3a94bb79d46f2815e46b86f1aca92acc73e5c2
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027848"
---
# <a name="double-c-reference"></a>double (référence C#)

Le mot clé `double` désigne un type simple qui stocke des valeurs à virgule flottante de 64 bits. Le tableau suivant montre la précision et la plage approximative pour le type `double`.

|Type|Plage approximative|Précision|Type .NET|
|----------|-----------------------|---------------|-------------------------|
|`double`|De ±5,0 × 10<sup>−324</sup> à ±1,7 × 10<sup>308</sup>|15 à 16 chiffres|<xref:System.Double?displayProperty=nameWithType>|

## <a name="literals"></a>Littéraux

Par défaut, un littéral numérique réel sur le côté droit de l’opérateur d’assignation est traité comme `double`. Toutefois, si vous souhaitez qu’un nombre entier soit traité comme `double`, utilisez le suffixe d ou D, par exemple :

```csharp
double x = 3D;
```

## <a name="conversions"></a>Conversions

Vous pouvez combiner des types numériques intégraux et des types virgule flottante dans une expression. Dans ce cas, les types intégraux sont convertis en types virgule flottante. L’évaluation de l’expression est exécutée d’après les règles suivantes :

- Si l’un des types virgule flottante est `double`, l’expression prend la valeur `double`, ou [bool](../../../csharp/language-reference/keywords/bool.md) dans les expressions relationnelles ou booléennes.

- S’il n’existe aucun type `double` dans l’expression, elle prend la valeur [float](../../../csharp/language-reference/keywords/float.md), ou [bool](../../../csharp/language-reference/keywords/bool.md) dans les expressions relationnelles ou booléennes.

 Une expression à virgule flottante peut contenir les ensembles de valeurs suivants :

- Zéro positif et négatif.

- Infini positif et négatif.

- Valeur NaN (N’est pas un nombre).

- L’ensemble fini de valeurs différentes de zéro.

Pour plus d’informations sur ces valeurs, consultez IEEE Standard for Binary Floating-Point Arithmetic, disponible sur le site web de l’[IEEE](https://www.ieee.org).

## <a name="example"></a>Exemple

Dans l’exemple suivant, un [int](../../../csharp/language-reference/keywords/int.md), un [short](../../../csharp/language-reference/keywords/short.md), un [float](../../../csharp/language-reference/keywords/float.md)et un `double` sont ajoutés pour donner un résultat `double`.

[!code-csharp[csrefKeywordsTypes#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#9)]

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

[Référence C#](../../../csharp/language-reference/index.md)  
[Guide de programmation C#](../../../csharp/programming-guide/index.md)  
[Mots clés C#](../../../csharp/language-reference/keywords/index.md)  
[Tableau des valeurs par défaut](../../../csharp/language-reference/keywords/default-values-table.md)  
[Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)  
[Tableau des types virgule flottante](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
[Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
[Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
