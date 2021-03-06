---
title: Overridable (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Overridable
- vb.Overridable
helpviewer_keywords:
- elements [Visual Basic], concrete
- properties [Visual Basic], redefining
- overriding, Overridable keyword
- elements [Visual Basic], virtual
- virtual [elements VB]
- procedures [Visual Basic], overriding
- concrete [elements VB]
- procedures [Visual Basic], redefining
- Overridable keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 612581e7-8a4c-4a5d-beff-3402fffa6f35
ms.openlocfilehash: 4844bf7f3ecf23335715b950a96be15e54ebc601
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603767"
---
# <a name="overridable-visual-basic"></a>Overridable (Visual Basic)
Spécifie qu’une propriété ou procédure peut être remplacée par une propriété portant le même nommée ou de la procédure dans une classe dérivée.  
  
## <a name="remarks"></a>Notes  
 Le `Overridable` modificateur permet à une propriété ou une méthode dans une classe de substitution dans une classe dérivée. Le [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) modificateur empêche une propriété ou méthode d’être substituée dans une classe dérivée.  Pour plus d’informations, consultez [Concepts de base de l’héritage](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Si le `Overridable` ou `NotOverridable` modificateur n’est pas spécifié, le paramètre par défaut varie selon que la propriété ou méthode se substitue à une méthode ou propriété de classe de base. Si la propriété ou méthode substitue une méthode ou propriété de classe de base, le paramètre par défaut est `Overridable`; sinon, elle est `NotOverridable`.  
  
 Vous pouvez masquer ou remplacer pour redéfinir un élément hérité, mais il existe des différences importantes entre les deux approches. Pour plus d’informations, consultez [occultation dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
 Un élément qui peut être substitué est parfois appelée une *virtuels* élément. Si elle peut être remplacée, mais pas nécessairement être, il est parfois également appelé un *concrète* élément.  
  
 Vous pouvez utiliser `Overridable` uniquement dans une instruction de déclaration de propriété ou de procédure.  
  
## <a name="combined-modifiers"></a>Modificateurs combinés  
 Vous ne pouvez pas spécifier `Overridable` ou `NotOverridable` pour un `Private` (méthode).  
  
 Vous ne pouvez pas spécifier `Overridable` avec `MustOverride`, `NotOverridable`, ou `Shared` dans la même déclaration.  
  
 Comme un élément de substitution est implicitement substituable, vous ne pouvez pas combiner `Overridable` avec `Overrides`.  
  
## <a name="usage"></a>Utilisation  
 Le modificateur `Overridable` peut être utilisé dans les contextes suivants :  
  
 [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Modificateurs](../../../visual-basic/language-reference/modifiers/index.md)  
 [Éléments fondamentaux de l’héritage](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Mots clés](../../../visual-basic/language-reference/keywords/index.md)  
 [Occultation dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
