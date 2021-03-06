---
title: IHostControl::SetAppDomainManager, méthode
ms.date: 03/30/2017
api_name:
- IHostControl.SetAppDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::SetAppDomainManager
helpviewer_keywords:
- IHostControl::SetAppDomainManager method [.NET Framework hosting]
- SetAppDomainManager method [.NET Framework hosting]
ms.assetid: 6562bbe7-0d67-4c50-a958-3a18cf680375
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb63f1e9d2b30ce764521aa68fbafe0407cbe922
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441872"
---
# <a name="ihostcontrolsetappdomainmanager-method"></a>IHostControl::SetAppDomainManager, méthode
Avertit l’hôte qu’un domaine d’application a été créé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwAppDomainID`  
 [in] L’identificateur numérique du <xref:System.AppDomain>.  
  
 `pUnkAppDomainManager`  
 [in] Un pointeur vers le <xref:System.AppDomainManager> objet que l’hôte implémente en tant que `IUnknown`.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`SetAppDomainManager` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.|  
|HOST_E_TIMEOUT|L’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.|  
|E_FAIL|Une défaillance grave et inconnue s’est produite. Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Notes  
 Le <xref:System.AppDomainManager> fournit à l’hôte avec un mécanisme d’amorçage dans du code managé et de contrôler la création et les paramètres de chaque <xref:System.AppDomain>. Le <xref:System.AppDomainManager> est chargé dans chaque <xref:System.AppDomain> lorsque qui <xref:System.AppDomain> est créé. Si elle choisit, le CLR informe l’hôte que le domaine d’application a été créé en définissant la valeur de le `pUnkAppDomainManager` paramètre.  
  
 Dans son implémentation de la `SetAppDomainManager` (méthode), l’hôte peut définir le nom de l’assembly et le type pour le Gestionnaire de domaine d’application.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.AppDomain>  
 <xref:System.AppDomainManager>  
 [IHostControl, interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
