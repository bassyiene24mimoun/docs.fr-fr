---
title: ICLRGCManager, interface
ms.date: 03/30/2017
api_name:
- ICLRGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager
helpviewer_keywords:
- ICLRGCManager interface [.NET Framework hosting]
ms.assetid: fb511c9b-3fe4-41b0-822a-6ba4a079d1f5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 045b924033630ea98d5a532a62f1037a5972df90
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433922"
---
# <a name="iclrgcmanager-interface"></a>ICLRGCManager, interface
Fournit des méthodes qui permettent à un hôte d’interagir avec le système de garbage collection du common language runtime.  
  
> [!NOTE]
>  En commençant par le [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], vous pouvez utiliser la [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) pour définir la taille d’un segment de garbage collection et la taille maximale de la génération du système de garbage collection 0 pour les valeurs supérieure (méthode) à la `DWORD` limite imposée par le [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) (méthode).  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Collect, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-collect-method.md)|Force une garbage collection pour la génération spécifiée.|  
|[GetStats, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)|Obtient un jeu de statistiques actuelles concernant le système de garbage collection.|  
|[SetGCStartupLimits, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)|Définit la taille d’un segment de garbage collection et la taille maximale de la génération du système de garbage collection 0.|  
  
## <a name="remarks"></a>Notes  
 Le common language runtime (CLR) implémente son mécanisme de garbage collection avec managé <xref:System.GC> type. Pour plus d’informations sur le système de garbage collection, consultez [le Garbage Collection](../../../../docs/standard/garbage-collection/index.md).  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion automatique de la mémoire](../../../../docs/standard/automatic-memory-management.md)  
 [COR_GC_STATS, structure](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [ICLRControl, interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [Interfaces d’hébergement CLR](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hébergement](../../../../docs/framework/unmanaged-api/hosting/index.md)
