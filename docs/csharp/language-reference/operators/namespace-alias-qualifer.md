---
title: ::, opérateur (référence C#)
ms.date: 07/20/2015
f1_keywords:
- ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 668799a2d846d0f0bf1b3743e202602250a57ae5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33271771"
---
# <a name="-operator-c-reference"></a>::, opérateur (référence C#)
Le qualificateur d’alias d’espace de noms (`::`) s’utilise pour rechercher les identificateurs. Il se place toujours entre deux identificateurs, comme dans cet exemple :  
  
 [!code-csharp[csRefOperators#27](../../../csharp/language-reference/operators/codesnippet/CSharp/namespace-alias-qualifer_1.cs)]  
  
## <a name="remarks"></a>Notes  
 Le qualificateur d’alias d’espace de noms peut être `global`. Il appelle alors une recherche dans l’espace de noms global, plutôt que dans un espace de noms avec alias.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 Pour obtenir un exemple d’utilisation de l’opérateur `::`, consultez la section suivante :  
  
-   [Comment : utiliser l’alias d’espace de noms global](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)  
 [Mots clés d’espaces de noms](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [. Opérateur](../../../csharp/language-reference/operators/member-access-operator.md)  
 [extern alias](../../../csharp/language-reference/keywords/extern-alias.md)
