---
title: '&lt;c&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 556c00fa761a1bce5e922a304706c78893550901
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599604"
---
# <a name="ltcgt-visual-basic"></a>&lt;c&gt; (Visual Basic)
Indique que le texte d’une description est code.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<c>text</c>  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---|---|  
|`text`|Texte que vous souhaitez indiquer comme étant du code.|  
  
## <a name="remarks"></a>Notes  
 Le `<c>` balise vous donne un moyen d’indiquer que le texte d’une description doit être marqué en tant que code. Utilisez [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) pour indiquer plusieurs lignes comme étant du code.  
  
 Compilez avec [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise le `<c>` balise dans la section Résumé pour indiquer que `Counter` est le code.  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/c_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Étiquettes XML pour les commentaires](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
