---
title: -référence (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb5d3b4c50a9c22880bdcc8406835cf51481e3cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654367"
---
# <a name="-reference-visual-basic"></a>-référence (Visual Basic)
Indique au compilateur rendre les informations de type dans les assemblys spécifiés disponibles pour le projet en cours de compilation.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-reference:fileList  
' -or-  
-r:fileList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`fileList`|Obligatoire. Liste délimitée par des virgules des noms de fichiers d’assembly. Si le nom de fichier contient un espace, placez-le entre des guillemets.|  
  
## <a name="remarks"></a>Notes  
 Les fichiers que vous importez doivent contenir des métadonnées de l’assembly. Seuls les types publics sont visibles en dehors de l’assembly. Le [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) option importe des métadonnées à partir d’un module.  
  
 Si vous référencez un assembly (Assembly A) qui lui-même référence un autre assembly (Assembly B), vous devez référencer l’Assembly B si :  
  
-   Un type de l’Assembly A hérite d’un type ou implémente une interface de l’Assembly B.  
  
-   Un champ, une propriété, un événement ou une méthode qui a un type de retour ou un type de paramètre de l’Assembly B est appelé.  
  
 Utilisez [- libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) pour spécifier le répertoire dans lequel sont trouve une ou plusieurs références d’assembly.  
  
 Pour le compilateur de reconnaître un type dans un assembly (pas un module), il doit être forcé à résoudre le type. Un exemple de comment vous pouvez faire cela est pour définir une instance du type. Autres méthodes sont disponibles pour résoudre les noms de type dans un assembly pour le compilateur. Par exemple, si vous héritez d’un type dans un assembly, le nom de type puis devienne connu du compilateur.  
  
 Le fichier réponse Vbc.rsp, qui référence couramment utilisés [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblys, est utilisé par défaut. Utilisez `-noconfig` si vous ne souhaitez pas que le compilateur utilise Vbc.rsp.  
  
 La forme abrégée de `-reference` est `/r`.  
  
## <a name="example"></a>Exemple  
 La commande suivante compile le fichier source `Input.vb` et référencer des assemblys à partir de `Metad1.dll` et `Metad2.dll` pour produire `Out.exe`.  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [Public](../../../visual-basic/language-reference/modifiers/public.md)  
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
