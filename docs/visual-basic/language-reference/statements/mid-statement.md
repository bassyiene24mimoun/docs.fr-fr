---
title: Mid, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.MidB
- vb.Mid
helpviewer_keywords:
- substrings [Visual Basic], Mid statement
- strings [Visual Basic], substrings
- Mid statement [Visual Basic]
- strings [Visual Basic], replacing
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
ms.openlocfilehash: 90b805df902dcdfebe85421583dd54e9af04bec9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602263"
---
# <a name="mid-statement"></a>Mid, instruction
Remplace un nombre spécifié de caractères dans un `String` variable avec des caractères d’une autre chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a>Composants  
 `Target`  
 Obligatoire. Nom de la `String` variable à modifier.  
  
 `Start`  
 Obligatoire. `Integer` Expression. Position du caractère dans `Target` où commence le remplacement de texte. `Start` utilise un index de base un.  
  
 `Length`  
 Facultatif. `Integer` Expression. Nombre de caractères à remplacer. Si omis, toutes les `String` est utilisé.  
  
 `StringExpression`  
 Obligatoire. `String` Expression qui remplace une partie de `Target`.  
  
## <a name="exceptions"></a>Exceptions  
  
|Type d'exception|Condition|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|`Start` < = 0 ou `Length` < 0.|  
  
## <a name="remarks"></a>Notes  
 Le nombre de caractères remplacés est toujours inférieur ou égal au nombre de caractères dans `Target`.  
  
 Visual Basic propose une <xref:Microsoft.VisualBasic.Strings.Mid%2A> (fonction) et un `Mid` instruction. Ces éléments fonctionnent à la fois sur un nombre spécifié de caractères dans une chaîne, mais la `Mid` fonction retourne les caractères lors de la `Mid` instruction remplace les caractères. Pour plus d'informations, consultez <xref:Microsoft.VisualBasic.Strings.Mid%2A>.  
  
> [!NOTE]
>  La `MidB` instruction des versions antérieures de Visual Basic remplace une sous-chaîne en octets, plutôt que des caractères. Il est utilisé principalement pour la conversion de chaînes dans les applications les caractères codés sur deux octets (DBCS) de jeu. Toutes les chaînes Visual Basic sont au format Unicode, et `MidB` n’est plus pris en charge.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la `Mid` instruction pour remplacer un nombre spécifié de caractères dans une variable de chaîne de caractères à partir d’une autre chaîne.  
  
 [!code-vb[VbVbalrStrings#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/mid-statement_1.vb)]  
  
## <a name="requirements"></a>Spécifications  
 **Namespace :** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Module :** `Strings`  
  
 **Assembly :** [!INCLUDE[vbprvbruntime](~/includes/vbprvbruntime-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 [Chaînes](../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [Introduction aux chaînes en Visual Basic](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
