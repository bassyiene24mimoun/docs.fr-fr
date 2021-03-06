---
title: Options du compilateur Visual Basic par catégorie
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: fbe36f7a-7cfa-4f77-a8d4-2be5958568e3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13aeab52cfd43aa8dfd7fda69e2eb9be798473e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655822"
---
# <a name="visual-basic-compiler-options-listed-by-category"></a>Options du compilateur Visual Basic par catégorie
Le compilateur de ligne de commande Visual Basic est fourni comme alternative aux programmes de compilation dans l’environnement de développement intégré (IDE) Visual Studio. Voici une liste des options du compilateur de ligne de commande Visual Basic triées par catégorie fonctionnelle.  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
## <a name="compiler-output"></a>Sortie du compilateur  
  
|Option|Objectif|  
|---|---|  
|[-nologo](../../../visual-basic/reference/command-line-compiler/nologo.md)|Supprime les informations de bannière du compilateur.|  
|[-utf8output](../../../visual-basic/reference/command-line-compiler/utf8output.md)|Affiche les résultats de la compilation au format d'encodage UTF-8.|  
|[-verbose](../../../visual-basic/reference/command-line-compiler/verbose.md)|Génère des informations supplémentaires lors de la compilation.|  
|`-modulename:<string>`|Spécifiez le nom du module source.|  
|[/preferreduilang](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|Spécifiez un langage pour les résultats de la compilation.|
  
## <a name="optimization"></a>Optimisation  
  
|Option|Objectif|  
|---|---|  
|[-filealign](../../../visual-basic/reference/command-line-compiler/filealign.md)|Spécifie où les sections du fichier de sortie doivent être alignées.|  
|[-optimize](../../../visual-basic/reference/command-line-compiler/optimize.md)|Active/désactive les optimisations.|  
  
## <a name="output-files"></a>Fichiers de sortie  
  
|Option|Objectif|  
|---|---|  
|[-doc](../../../visual-basic/reference/command-line-compiler/doc.md)|Traite les commentaires de documentation pour les diriger vers un fichier XML.|  
|[-deterministic](../../../visual-basic/reference/command-line-compiler/deterministic.md)|Indique au compilateur de générer un assembly dont le contenu binaire est identique dans les compilations si les entrées sont identiques.|
|[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)|Configure le compilateur pour cibler le [!INCLUDE[Compact](~/includes/compact-md.md)].|  
|[-out](../../../visual-basic/reference/command-line-compiler/out.md)|Spécifie un fichier de sortie.|  
|[-refonly](refonly-compiler-option.md)|Génère un assembly de référence uniquement.|
|[/refout](refout-compiler-option.md)|Spécifie le chemin de sortie d’un assembly de référence.|
|[-target](../../../visual-basic/reference/command-line-compiler/target.md)|Spécifie le format de la sortie.|  
  
## <a name="net-assemblies"></a>Assemblys .NET  
  
|Option|Objectif|  
|---|---|  
|[-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)|Entraîne la mise à disposition par le compilateur de toutes les informations de type à partir du ou des fichiers spécifiés, pour le projet en cours de compilation.|  
|[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)|Spécifie si l'assembly sera complètement ou partiellement signé.|  
|[-imports](../../../visual-basic/reference/command-line-compiler/imports.md)|Importe un espace de noms à partir d'un assembly spécifié.|  
|[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)|Spécifie un nom de conteneur de clé pour une paire de clés afin d'attribuer un nom fort à un assembly.|  
|[-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)|Spécifie un fichier contenant une clé ou une paire de clés afin d'attribuer un nom fort à un assembly.|  
|[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)|Spécifie l’emplacement des assemblys référencés par le [-référence](../../../visual-basic/reference/command-line-compiler/reference.md) option.|  
|[-reference](../../../visual-basic/reference/command-line-compiler/reference.md)|Importe des métadonnées à partir d'un assembly.|  
|[-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)|Spécifie le nom de l'assembly dont un module fera partie.|  
|`-analyzer`|Exécute les analyseurs à partir de cet assembly (forme abrégée : -a).|  
|`-additionalfile`|Nomme des fichiers supplémentaires qui n'affectent pas directement la génération de code, mais peuvent être utilisés par des analyseurs pour produire des erreurs ou des avertissements.|  
  
## <a name="debuggingerror-checking"></a>Débogage/vérification des erreurs  
  
|Option|Objectif|  
|---|---|  
|[-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)|Crée un fichier qui contient des informations qui facilitent le signalement d'un bogue.|  
|[-debug](../../../visual-basic/reference/command-line-compiler/debug.md)|Génère des informations de débogage.|  
|[-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)|Supprime la capacité du compilateur à générer des avertissements.|  
|[-quiet](../../../visual-basic/reference/command-line-compiler/quiet.md)|Empêche le compilateur d'afficher le code pour les erreurs et les avertissements liés à la syntaxe.|  
|[-removeintchecks](../../../visual-basic/reference/command-line-compiler/removeintchecks.md)|Désactive les contrôles de dépassement sur les entiers.|  
|[-warnaserror](../../../visual-basic/reference/command-line-compiler/warnaserror.md)|Transforme les avertissements en erreurs.|  
|`-ruleset:<file>`|Spécifiez un fichier ruleset qui désactive des diagnostics spécifiques.|  
  
## <a name="help"></a>Help  
  
|Option|Objectif|  
|---|---|  
|[-?](../../../visual-basic/reference/command-line-compiler/help.md)|Affiche les options du compilateur. Cette commande est identique à l'option `-help`. Aucune compilation n'a lieu.|  
|[-help](../../../visual-basic/reference/command-line-compiler/help.md)|Affiche les options du compilateur. Cette commande est identique à l'option `-?`. Aucune compilation n'a lieu.|  
  
## <a name="language"></a>Langue  
  
|Option|Objectif|  
|---|---|  
|[-langversion](../../../visual-basic/reference/command-line-compiler/langversion.md)|Spécifiez la version de langage : 9&#124;9.0&#124;10&#124;10.0&#124;11&#124;11.0.|  
|[-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)|Applique la déclaration explicite des variables.|  
|[-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)|Applique une sémantique de type stricte.|  
|[-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)|Spécifie si les comparaisons de chaînes doivent être binaires ou utiliser une sémantique spécifique aux paramètres régionaux.|  
|[-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)|Permet l'utilisation de l'inférence de type de variable locale dans les déclarations de variable.|  
  
## <a name="preprocessor"></a>Préprocesseur  
  
|Option|Objectif|  
|---|---|  
|[-define](../../../visual-basic/reference/command-line-compiler/define.md)|Définit des symboles de compilation conditionnelle.|  
  
## <a name="resources"></a>Ressources  
  
|Option|Objectif|  
|---|---|  
|[-linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)|Crée un lien à une ressource managée.|  
|[-resource](../../../visual-basic/reference/command-line-compiler/resource.md)|Incorpore une ressource managée dans un assembly.|  
|[-win32icon](../../../visual-basic/reference/command-line-compiler/win32icon.md)|Insère un fichier .ico dans le fichier de sortie.|  
|[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)|Insère une ressource Win32 dans le fichier de sortie.|  
  
## <a name="miscellaneous"></a>Divers  
  
|Option|Objectif|  
|---|---|  
|[@ (spécifier un fichier réponse)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)|Spécifie un fichier réponse.|  
|[-baseaddress](../../../visual-basic/reference/command-line-compiler/baseaddress.md)|Spécifie l'adresse de base d'une DLL.|  
|[-codepage](../../../visual-basic/reference/command-line-compiler/codepage.md)|Spécifie la page de codes à utiliser pour tous les fichiers de code source inclus dans la compilation.|  
|[-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)|Spécifie comment le compilateur Visual Basic doit signaler les erreurs internes du compilateur.|  
|[-highentropyva](../../../visual-basic/reference/command-line-compiler/highentropyva.md)|Indique au noyau Windows si un fichier exécutable particulier prend en charge la randomisation du format d'espace d'adresse (ASLR) de forte entropie.|  
|[-main](../../../visual-basic/reference/command-line-compiler/main.md)|Spécifie la classe qui contient le `Sub Main` procédure à utiliser au démarrage.|  
|[-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)|Ne compilez pas avec Vbc.rsp.|  
|[-nostdlib](../../../visual-basic/reference/command-line-compiler/nostdlib.md)|Configure le compilateur pour ne pas référencer les bibliothèques standard.|  
|[-nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)|Indique au compilateur de ne pas incorporer de manifeste d'application dans le fichier exécutable.|  
|[-platform](../../../visual-basic/reference/command-line-compiler/platform.md)|Spécifie la plateforme de processeur ciblée par le compilateur pour le fichier de sortie.|  
|[-recurse](../../../visual-basic/reference/command-line-compiler/recurse.md)|Recherche des fichiers sources à compiler dans les sous-répertoires.|  
|[-rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)|Spécifie un espace de noms pour toutes les déclarations de type.|  
|[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)|Spécifie l'emplacement de Mscorlib.dll et de Microsoft.VisualBasic.dll.|  
|[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)|Spécifie que le compilateur doit compiler sans référence à la bibliothèque runtime Visual Basic, ou avec une référence à une bibliothèque runtime spécifique.|  
|[-win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md)|Identifie un fichier manifeste d'application Win32 défini par l'utilisateur à incorporer dans le fichier exécutable portable (PE) d'un projet.|  
|`-parallel[+&#124;-]`|Indique s'il faut utiliser la build simultanée (+).|  
|`-checksumalgorithm:<alg>`|Spécifiez l'algorithme de calcul de la somme de contrôle du fichier source stockée dans le fichier PDB.  Les valeurs prises en charge sont : SHA1 (par défaut) ou SHA256.|  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur Visual Basic par ordre alphabétique](../../../visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically.md)  
 [Présentation du Concepteur de projets](https://msdn.microsoft.com/en-us/library/898dd854-c98d-430c-ba1b-a913ce3c73d7(v=vs.100))  
 [Options du compilateur C# par ordre alphabétique](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
 [Options du compilateur C# par catégorie](../../../csharp/language-reference/compiler-options/listed-by-category.md)
