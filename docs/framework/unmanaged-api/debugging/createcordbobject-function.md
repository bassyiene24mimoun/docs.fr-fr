---
title: Fonction CreateCordbObject
ms.date: 03/30/2017
api_name:
- CreateCoredbObject
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCordbObject
helpviewer_keywords:
- remote debugging API [Silverlight]
- CreateCordbObject function
- Silverlight, remote debugging
ms.assetid: b259821d-4fa7-464d-85cf-304dfffc8089
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12898f75d2575e539b018ea367bc870a3dc738a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406329"
---
# <a name="createcordbobject-function"></a>Fonction CreateCordbObject
Crée une interface de débogueur ([ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)) qui fournit des fonctionnalités d’instanciation d’une session de débogage managée sur un processus distant.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,   
       [out] IUnknown**  ppCordb  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `iDebuggerVersion`  
 [in] Version de débogage du processus cible. Ce paramètre doit être CorDebugVersion_2_0 pour le débogage distant.  
  
 `ppCordb`  
 [out] Pointeur vers un pointeur vers un objet qui sera converti en un [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface et retourné.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK  
 Le nombre de CLR dans le processus a été correctement déterminé, et les tableaux de handles et de chemins d'accès correspondants ont été correctement remplis.  
  
 E_INVALIDARG  
 `ppCordb` est null ou `iDebuggerVersion` n'est pas CorDebugVersion_2_0.  
  
 E_OUTOFMEMORY  
 Impossible d'allouer suffisamment de mémoire pour `ppCordb`.  
  
 E_FAIL (ou autres codes de retour E_)  
 Autres échecs.  
  
## <a name="remarks"></a>Notes  
 Le [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface retournée dans `ppCordb` est l’interface de débogage de niveau supérieur pour tous les services de débogage managés.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CoreClrRemoteDebuggingInterfaces.h  
  
 **Bibliothèque :** mscordbi_macx86.dll  
  
 **Versions du .NET framework :** 3.5 SP1
