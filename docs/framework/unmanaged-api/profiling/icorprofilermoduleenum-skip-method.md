---
title: "ICorProfilerModuleEnum::Skip, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerModuleEnum.Skip Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerModuleEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Skip method [.NET Framework profiling]
ms.assetid: 8dc29c6a-e2ba-41d8-a1e0-0fdd21421e0b
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7331c5221de1dc1bfdbbce77f8c40f4fbc95aea2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilermoduleenumskip-method"></a><span data-ttu-id="a2659-102">ICorProfilerModuleEnum::Skip, méthode</span><span class="sxs-lookup"><span data-stu-id="a2659-102">ICorProfilerModuleEnum::Skip Method</span></span>
<span data-ttu-id="a2659-103">Fait avancer le curseur de l'énumérateur depuis sa position actuelle de manière à ignorer le nombre spécifié d'éléments.</span><span class="sxs-lookup"><span data-stu-id="a2659-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2659-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2659-104">Syntax</span></span>  
  
```  
HRESULT Skip([in] ULONG celt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a2659-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a2659-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="a2659-106">[in] Le nombre d’éléments à ignorer.</span><span class="sxs-lookup"><span data-stu-id="a2659-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2659-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a2659-107">Return Value</span></span>  
 <span data-ttu-id="a2659-108">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="a2659-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a2659-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a2659-109">HRESULT</span></span>|<span data-ttu-id="a2659-110">Description</span><span class="sxs-lookup"><span data-stu-id="a2659-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a2659-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a2659-111">S_OK</span></span>|<span data-ttu-id="a2659-112">`celt`éléments ont été ignorés.</span><span class="sxs-lookup"><span data-stu-id="a2659-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="a2659-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a2659-113">S_FALSE</span></span>|<span data-ttu-id="a2659-114">Moins de `celt` éléments ont été ignorés, ce qui signifie qu’il n’y a plus d’éléments.</span><span class="sxs-lookup"><span data-stu-id="a2659-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2659-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="a2659-115">Remarks</span></span>  
 <span data-ttu-id="a2659-116">La nouvelle position du curseur de cet énumérateur est (position actuelle) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="a2659-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2659-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a2659-117">Requirements</span></span>  
 <span data-ttu-id="a2659-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2659-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2659-119">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a2659-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a2659-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2659-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2659-121">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2659-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2659-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2659-122">See Also</span></span>  
 [<span data-ttu-id="a2659-123">ICorProfilerModuleEnum (Interface)</span><span class="sxs-lookup"><span data-stu-id="a2659-123">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 [<span data-ttu-id="a2659-124">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="a2659-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)