---
title: EClrEvent, énumération
ms.date: 03/30/2017
api_name:
- EClrEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrEvent
helpviewer_keywords:
- EClrEvent enumeration [.NET Framework hosting]
ms.assetid: 7c36a7c2-75a2-4971-bc23-abf54c812154
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63d79b0c1fed0178f8463174fe981f250d6f6fb5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430705"
---
# <a name="eclrevent-enumeration"></a>EClrEvent, énumération
Décrit les événements du common language runtime (CLR) pour laquelle l’hôte peut enregistrer des rappels.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    Event_ClrDisabled,  
    Event_DomainUnload,  
    Event_MDAFired,  
    Event_StackOverflow  
} EClrEvent;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`Event_ClrDisabled`|Spécifie une erreur irrécupérable de CLR.|  
|`Event_DomainUnload`|Spécifie le déchargement d’un particulier <xref:System.AppDomain>.|  
|`Event_MDAFired`|Spécifie qu’un message d’Assistant Débogage managé (MDA) a été généré.|  
|`Event_StackOverflow`|Spécifie qu’une erreur de dépassement de capacité de pile s’est produite.|  
  
## <a name="remarks"></a>Notes  
 L’hôte peut enregistrer des rappels pour l’un des types d’événements décrits par `EClrEvent` en appelant des méthodes de la [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) interface. L’hôte obtient un pointeur vers cette interface en appelant le [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) (méthode).  
  
 Le `Event_CLRDisabled` et `Event_DomainUnload` peuvent être déclenchés plusieurs fois et à partir de threads différents pour signaler le déchargement ou la désactivation du CLR.  
  
 Le `Event_MDAFired` événement déclenche la création d’un [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance qui contient les détails du message d’Assistant Débogage MANAGÉ. Pour plus d’informations sur les Assistants Débogage managé, consultez [diagnostic d’erreurs avec les Assistants Débogage managé](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions du .NET framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [IActionOnCLREvent, interface](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [ICLRControl, interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [Énumérations d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
