---
title: Méthode ICLRStrongName::StrongNameKeyGenEx
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGenEx
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyGenEx method [.NET Framework hosting]
- StrongNameKeyGenEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 1f8b59d0-5b72-45b8-ab74-c2b43ffc806e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b213285b3c533488cfa48198951275925c0e37ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436184"
---
# <a name="iclrstrongnamestrongnamekeygenex-method"></a>Méthode ICLRStrongName::StrongNameKeyGenEx
Génère une nouvelle paire de clés publique/privée avec la taille de clé spécifiée, pour l’utiliser avec un nom fort.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `wszKeyContainer`  
 [in] Le nom du conteneur de clé demandé. `wszKeyContainer` doit être une chaîne non vide ou la valeur null pour générer un nom temporaire.  
  
 `dwFlags`  
 [in] Une valeur qui spécifie s’il faut laisser la clé enregistrée. Les valeurs suivantes sont prises en charge :  
  
-   0 x 00000000 - utilisée lorsque `wszKeyContainer` a la valeur null pour générer un nom de conteneur de clé temporaire.  
  
-   0 x 00000001 (`SN_LEAVE_KEY`)-Spécifie que la clé doit rester enregistrée.  
  
 `dwKeySize`  
 [in] La taille demandée de la clé, en bits.  
  
 `ppbKeyBlob`  
 [out] La paire de clés publique/privée retournée.  
  
 `pcbKeyBlob`  
 [out] La taille, en octets, de `ppbKeyBlob`.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK` Si la méthode a réussi ; Sinon, une valeur HRESULT qui indique un échec (voir [valeurs HRESULT courantes](http://go.microsoft.com/fwlink/?LinkId=213878) pour obtenir la liste).  
  
## <a name="remarks"></a>Notes  
 Les versions de .NET Framework 1.0 et 1.1 requièrent un `dwKeySize` de 1 024 bits pour signer un assembly avec un nom fort ; version 2.0 ajoute la prise en charge de clés 2 048 bits.  
  
 Une fois la clé est récupérée, vous devez appeler la [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) méthode pour libérer la mémoire allouée.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MetaHost.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [StrongNameKeyGen, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)  
 [ICLRStrongName, interface](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
