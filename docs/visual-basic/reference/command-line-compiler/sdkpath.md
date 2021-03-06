---
title: -sdkpath
ms.date: 07/20/2015
f1_keywords:
- sdkpath
- -sdkpath
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 162c7d58350c381ec667e8a4cd11c03e83fcdf44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="-sdkpath"></a>-sdkpath
Spécifie l’emplacement de mscorlib.dll et de Microsoft.VisualBasic.dll.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-sdkpath:path  
```  
  
## <a name="arguments"></a>Arguments  
 `path`  
 Le répertoire contenant les versions de mscorlib.dll et de Microsoft.VisualBasic.dll à utiliser pour la compilation. Ce chemin d’accès n’est pas vérifiée jusqu'à ce qu’il est chargé. Placez le nom de répertoire entre guillemets ( » «) si elle contient un espace.  
  
## <a name="remarks"></a>Notes  
 Cette option indique au compilateur de Visual Basic pour charger le mscorlib.dll et Microsoft.VisualBasic.dll fichiers à partir d’un emplacement non définis par défaut. Le `-sdkpath` option a été conçue pour être utilisé avec [- /netcf](../../../visual-basic/reference/command-line-compiler/netcf.md). Le [!INCLUDE[Compact](~/includes/compact-md.md)] utilise différentes versions de ces bibliothèques d’assistance pour éviter l’utilisation de types et de fonctionnalités de langage introuvables sur les appareils.  
  
> [!NOTE]
>  Le `-sdkpath` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande. Le `-sdkpath` option est définie lors du chargée d’un projet de périphérique Visual Basic.  
  
 Vous pouvez spécifier que le compilateur doit compiler sans référence à la bibliothèque Runtime Visual Basic à l’aide de la `-vbruntime` option du compilateur. Pour plus d’informations, consultez [- vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `Myfile.vb` avec la [!INCLUDE[Compact](~/includes/compact-md.md)], l’utilisation des versions de Mscorlib.dll et de Microsoft.VisualBasic.dll trouvées dans le répertoire d’installation par défaut de la [!INCLUDE[Compact](~/includes/compact-md.md)] sur le lecteur C. En règle générale, vous utiliseriez la version la plus récente de la [!INCLUDE[Compact](~/includes/compact-md.md)].  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)  
 [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
