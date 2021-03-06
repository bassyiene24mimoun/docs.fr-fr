---
title: 'Comment : appeler des API Windows (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: de568c3273d4d040c6566136e5d59e2155b86f8b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643638"
---
# <a name="how-to-call-windows-apis-visual-basic"></a>Comment : appeler des API Windows (Visual Basic)
Cet exemple définit et appelle la `MessageBox` fonction dans user32.dll et lui passe une chaîne.  
  
## <a name="example"></a>Exemple  
 [!code-vb[VbVbalrInterop#1](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-call-windows-apis_1.vb)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
-   une référence à l'espace de noms <xref:System>.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les conditions ci-dessous peuvent générer une exception.  
  
-   La méthode n’est pas statique, est abstraite ou a été définie précédemment. Le type parent est une interface, ou la longueur de *nom* ou *dllName* est égal à zéro. (<xref:System.ArgumentException>)  
  
-   Le *nom* ou *dllName* est `Nothing`. (<xref:System.ArgumentNullException>)  
  
-   Le type conteneur a déjà été créé à l’aide de `CreateType`. (<xref:System.InvalidOperationException>)  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation détaillée de l’appel de code non managé](http://msdn.microsoft.com/library/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)  
 [Exemples d'appel de code non managé](../../../framework/interop/platform-invoke-examples.md)  
 [Consommation de fonctions DLL non managées](../../../framework/interop/consuming-unmanaged-dll-functions.md)  
 [Émission de la définition d’une méthode avec la réflexion](http://msdn.microsoft.com/library/84fd3bf6-628f-41aa-83d9-b990cf926e81)  
 [Procédure pas à pas : appel des API Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)
