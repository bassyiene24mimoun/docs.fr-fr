---
title: -delaysign (Options du compilateur C#)
ms.date: 05/15/2018
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
ms.openlocfilehash: 72dcba3b506dae42f67f0421ba92efee18274c37
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2018
ms.locfileid: "34472644"
---
# <a name="-delaysign-c-compiler-options"></a>-delaysign (Options du compilateur C#)

Cette option fait en sorte que le compilateur réserve de l’espace dans le fichier de sortie afin qu’une signature numérique puisse être ajoutée ultérieurement.

## <a name="syntax"></a>Syntaxe

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a>Arguments

`+` &#124; `-`

Utilisez **-delaysign-** si vous souhaitez obtenir un assembly complètement signé. Utilisez **-delaysign+** si vous souhaitez uniquement placer la clé publique dans l’assembly. **-delaysign-** est l’option par défaut.

## <a name="remarks"></a>Notes

L’option **-delaysign** est sans effet sauf si elle est utilisée avec [-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) ou [-keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).

Les options **-delaysign** et **-publicsign** s’excluent mutuellement.

Quand vous demandez un assembly totalement signé, le compilateur hache le fichier qui contient le manifeste (métadonnées de l’assembly) et signe ce hachage avec la clé privée. L’opération crée une signature numérique qui est stockée dans le fichier contenant le manifeste. Pour un assembly avec signature différée, le compilateur ne calcule pas, ni ne stocke la signature, mais réserve de l'espace dans le fichier pour que la signature puisse être ajoutée par la suite.

Par exemple, l’utilisation de **-delaysign+** permet à un testeur de placer l’assembly dans le cache global. Après un test, vous pouvez signer complètement l’assembly en plaçant la clé privée dans l’assembly à l’aide de l’utilitaire [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md).

Pour plus d’informations, consultez [Création et utilisation d’assemblys avec nom fort](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) et [Différer la signature d’un assembly](../../../framework/app-domains/delay-sign-assembly.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la page **Propriétés** du projet.
1. Modifiez la propriété **Différer la signature uniquement**.

Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.

## <a name="see-also"></a>Voir aussi

 [Option -publicsign C#](publicsign-compiler-option.md)  
 [Options du compilateur C#](index.md)  
 [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
