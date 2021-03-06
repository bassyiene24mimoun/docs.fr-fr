---
title: explicit, mot clé (référence C#)
ms.date: 07/20/2015
f1_keywords:
- explicit_CSharpKeyword
- explicit
helpviewer_keywords:
- explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
ms.openlocfilehash: 66d271fdac0bad356ee0bafc1732e2f410854da1
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027939"
---
# <a name="explicit-c-reference"></a>explicit (référence C#)

Le mot clé `explicit` déclare un opérateur de conversion de type défini par l’utilisateur qui doit être appelé avec un cast. Par exemple, cet opérateur effectue une conversion d’une classe nommée Fahrenheit vers une classe nommée Celsius :

[!code-csharp[csrefKeywordsConversion#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#2)]

Cet opérateur de conversion peut être appelé comme suit :

[!code-csharp[csrefKeywordsConversion#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#3)]

L’opérateur de conversion convertit un type source en type cible. Le type source fournit l’opérateur de conversion. Contrairement à une conversion implicite, les opérateurs de conversion explicite doivent être appelés au moyen d’un cast. Si une opération de conversion peut provoquer des exceptions ou la perte d’informations, vous devez la marquer comme `explicit`. Cela empêche que le compilateur appelle l’opération de conversion en mode silencieux, avec éventuellement des conséquences imprévisibles.

L’omission du cast provoque l’erreur de compilation CS0266.

Pour plus d’informations, consultez [Utilisation d’opérateurs de conversion](../../programming-guide/statements-expressions-operators/using-conversion-operators.md).

## <a name="example"></a>Exemple

L’exemple suivant fournit des classes `Fahrenheit` et `Celsius`, chacune fournissant un opérateur de conversion explicite à l’autre classe.

[!code-csharp[csrefKeywordsConversion#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#1)]

## <a name="example"></a>Exemple

L’exemple suivant définit un struct, `Digit`, qui représente un seul chiffre décimal. Un opérateur est défini pour les conversions de `byte` à `Digit`, mais étant donné que les octets ne peuvent pas tous être convertis en `Digit`, la conversion est explicite.

[!code-csharp[csrefKeywordsConversion#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#4)]

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

[Référence C#](../index.md)  
[Guide de programmation C#](../../programming-guide/index.md)  
[Mots clés C#](index.md)  
[implicit](implicit.md)  
[operator (référence C#)](operator.md)  
[Guide pratique pour implémenter des conversions définies par l’utilisateur entre des structs](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
[Conversions explicites définies par l’utilisateur chaînées en C#](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)  