---
title: ResolveTypeLib, méthode
ms.date: 03/30/2017
api_name:
- ResolveTypeLib
api_location:
- tlbref.dll
f1_keywords:
- ResolveTypeLib
helpviewer_keywords:
- ITypeLibResolver::ResolveTypeLib method [.NET Framework]
- ResolveTypeLib method [.NET Framework]
ms.assetid: 95d2aa0d-8eeb-4a9f-a216-5249f7e2c167
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 96a9672ee05cb1fe2573620bd1dea23e57339c93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460839"
---
# <a name="resolvetypelib-method"></a>ResolveTypeLib, méthode
Résout le nom simple d’une bibliothèque de types en retournant son chemin d’accès qualifié complet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ResolveTypeLib(  
    [in]  BSTR      bstrSimpleName,  
    [in]  GUID      tlbid,  
    [in]  LCID      lcid,  
    [in]  USHORT    wMajorVersion,  
    [in]  USHORT    wMinorVersion,  
    [in]  SYSKIND   syskind,  
    [out] BSTR     *pbstrResolvedTlbName);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `bstrSimpleName`  
 [in] A [BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) qui contient le nom simple de la bibliothèque de types.  
  
 `tlbid`  
 [in] Le GUID affecté à la bibliothèque de types dans le Registre.  
  
 `lcid`  
 [in] ID de localisation de la bibliothèque de types.  
  
 `wMajorVersion`  
 [in] Numéro de version principale de la bibliothèque de types. Par exemple, pour la version *x.y*, le numéro de version majeure est *x*.  
  
 `wMinorVersion`  
 [in] Numéro de version secondaire de la bibliothèque de types. Par exemple, pour la version *x.y*, le numéro de version mineure est *y*.  
  
 `syskind`  
 [in] A [SYSKIND](http://msdn.microsoft.com/library/662048b2-59a8-48ca-9e4f-2f9a5306faa1) indicateur qui identifie l’environnement d’exploitation. Les valeurs courantes sont SYS_WIN32 et SYS_WIN64.  
  
 `pbstrResolvedTlbName`  
 [out] Un pointeur vers un [BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) qui contient le chemin d’accès complet de la bibliothèque de types nommée dans le `bstrSimpleName` paramètre.  
  
## <a name="remarks"></a>Notes  
 Le `ResolveTypeLib` méthode est appelée par le [LoadTypeLibWithResolver, fonction](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) pendant [Tlbexp.exe (exportateur)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) de traitement.  
  
 Les implémentations personnalisées de cette interface doivent retourner un [BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) qui contient le chemin d’accès complet de la bibliothèque de types nommée dans le `bstrSimpleName` paramètre.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** TlbRef.idl, TlbRef.h  
  
 **Bibliothèque :** TlbRef.lib  
  
 **Versions du .NET framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’assistance Tlbexp](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [LoadTypeLibEx](http://msdn.microsoft.com/library/56a7f9e1-810b-4a42-aa4d-691f4304f5ef)
