---
title: "IHostSyncManager::CreateCrstWithSpinCount, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateCrstWithSpinCount
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateCrstWithSpinCount
helpviewer_keywords:
- CreateCrstWithSpinCount method [.NET Framework hosting]
- IHostSyncManager::CreateCrstWithSpinCount method [.NET Framework hosting]
ms.assetid: 7280fa8c-3639-4abf-91cb-bc343da742d1
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 41031a5e3d423f0c1d7459250073634592e0291e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsyncmanagercreatecrstwithspincount-method"></a><span data-ttu-id="612d0-102">IHostSyncManager::CreateCrstWithSpinCount, méthode</span><span class="sxs-lookup"><span data-stu-id="612d0-102">IHostSyncManager::CreateCrstWithSpinCount Method</span></span>
<span data-ttu-id="612d0-103">Crée un objet de section critique dont le nombre de sélection numérique pour la synchronisation.</span><span class="sxs-lookup"><span data-stu-id="612d0-103">Creates a critical section object with spin count for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="612d0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="612d0-104">Syntax</span></span>  
  
```  
HRESULT CreateCrstWithSpinCount (  
    [in]  DWORD dwSpinCount,  
    [out] IHostCrst** ppCrst  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="612d0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="612d0-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="612d0-106">[in] Spécifie le nombre de sélection numérique pour l’objet de section critique.</span><span class="sxs-lookup"><span data-stu-id="612d0-106">[in] Specifies the spin count for the critical section object.</span></span>  
  
 `ppCrst`  
 <span data-ttu-id="612d0-107">[out] Un pointeur vers l’adresse d’un [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) de l’instance, ou null si la section critique n’a pas pu être créée.</span><span class="sxs-lookup"><span data-stu-id="612d0-107">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="612d0-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="612d0-108">Return Value</span></span>  
  
|<span data-ttu-id="612d0-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="612d0-109">HRESULT</span></span>|<span data-ttu-id="612d0-110">Description</span><span class="sxs-lookup"><span data-stu-id="612d0-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="612d0-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="612d0-111">S_OK</span></span>|<span data-ttu-id="612d0-112">`CreateCrstWithSpinCount`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="612d0-112">`CreateCrstWithSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="612d0-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="612d0-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="612d0-114">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="612d0-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="612d0-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="612d0-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="612d0-116">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="612d0-116">The call timed out.</span></span>|  
|<span data-ttu-id="612d0-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="612d0-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="612d0-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="612d0-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="612d0-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="612d0-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="612d0-120">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="612d0-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="612d0-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="612d0-121">E_FAIL</span></span>|<span data-ttu-id="612d0-122">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="612d0-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="612d0-123">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="612d0-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="612d0-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="612d0-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="612d0-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="612d0-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="612d0-126">Pas assez de mémoire n’était disponible pour créer la section critique demandée.</span><span class="sxs-lookup"><span data-stu-id="612d0-126">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="612d0-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="612d0-127">Remarks</span></span>  
 <span data-ttu-id="612d0-128">Un nombre de sélection numérique est utilisé uniquement sur un système multiprocesseur.</span><span class="sxs-lookup"><span data-stu-id="612d0-128">A spin count is used only on a multi-processor system.</span></span> <span data-ttu-id="612d0-129">Le compteur de rotations Spécifie le nombre de fois où qu'un thread appelant doit lancer avant d’effectuer une opération d’attente sur un sémaphore qui est associé à une section critique non disponible.</span><span class="sxs-lookup"><span data-stu-id="612d0-129">The spin count specifies the number of times a calling thread must spin before it performs a wait operation on a semaphore that is associated with an unavailable critical section.</span></span> <span data-ttu-id="612d0-130">Si la section critique se libère pendant l’opération de sélection numérique, le thread appelant évite l’opération d’attente.</span><span class="sxs-lookup"><span data-stu-id="612d0-130">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span> <span data-ttu-id="612d0-131">`CreateCrstWithSpinCount`reflète Win32 `InitializeCriticalSectionAndSpinCount` (fonction).</span><span class="sxs-lookup"><span data-stu-id="612d0-131">`CreateCrstWithSpinCount` mirrors the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="612d0-132">Spécifications</span><span class="sxs-lookup"><span data-stu-id="612d0-132">Requirements</span></span>  
 <span data-ttu-id="612d0-133">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="612d0-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="612d0-134">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="612d0-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="612d0-135">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="612d0-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="612d0-136">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="612d0-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="612d0-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="612d0-137">See Also</span></span>  
 [<span data-ttu-id="612d0-138">ICLRSyncManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="612d0-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="612d0-139">IHostSemaphore (Interface)</span><span class="sxs-lookup"><span data-stu-id="612d0-139">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="612d0-140">IHostSyncManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="612d0-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)