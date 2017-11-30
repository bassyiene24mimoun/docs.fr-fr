---
title: "ICorDebugType2::GetTypeID (méthode)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugType2.GetTypeID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetTypeID
helpviewer_keywords:
- GetTypeID method, ICorDebugType2 interface [.NET Framework debugging]
- ICorDebugType2.GetTypeID method [.NET Framework debugging]
ms.assetid: 0b933686-226e-4373-92b7-fac579ee7b1a
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 30b5259bfd39ac0c8c8b717d59a8d3165f6b6cbf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugtype2gettypeid-method"></a><span data-ttu-id="14846-102">ICorDebugType2::GetTypeID (méthode)</span><span class="sxs-lookup"><span data-stu-id="14846-102">ICorDebugType2::GetTypeID Method</span></span>
<span data-ttu-id="14846-103">Obtient un [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) pour ce type.</span><span class="sxs-lookup"><span data-stu-id="14846-103">Gets a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14846-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14846-104">Syntax</span></span>  
  
```  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="14846-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="14846-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="14846-106">[out] Un pointeur vers le [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) pour ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="14846-106">[out] A pointer to the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this ICorDebugType.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="14846-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="14846-107">Return Value</span></span>  
 <span data-ttu-id="14846-108">La valeur de retour est `S_OK` en cas de réussite ou un code d'échec `HRESULT` en cas d'échec.</span><span class="sxs-lookup"><span data-stu-id="14846-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="14846-109">Le `HRESULT` codes incluent les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="14846-109">The `HRESULT` codes include the following:</span></span>  
  
|<span data-ttu-id="14846-110">Code de retour</span><span class="sxs-lookup"><span data-stu-id="14846-110">Return code</span></span>|<span data-ttu-id="14846-111">Description</span><span class="sxs-lookup"><span data-stu-id="14846-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="14846-112">La méthode a réussi.</span><span class="sxs-lookup"><span data-stu-id="14846-112">Method succeeded.</span></span> <span data-ttu-id="14846-113">La méthode a récupéré valide [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md).</span><span class="sxs-lookup"><span data-stu-id="14846-113">The method has retrieved a valid [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md).</span></span>|  
|`CORDBG_E_CLASS_NOT_LOADED`|<span data-ttu-id="14846-114">Le type n’a pas été chargé.</span><span class="sxs-lookup"><span data-stu-id="14846-114">The type has not been loaded.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="14846-115">Le type n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="14846-115">The type is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14846-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="14846-116">Remarks</span></span>  
 <span data-ttu-id="14846-117">Cette méthode fournit un mappage à partir de ICorDebugType, ce qui représente un type qui peut ou ont ne peut-être pas été chargé dans l’exécution, à un [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), qui sert un opaque gérer qui identifie un type chargé dans le runtime.</span><span class="sxs-lookup"><span data-stu-id="14846-117">This method provides a mapping from the ICorDebugType, which represents a type that may or may not have been loaded into the runtime, to a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), which serves as an opaque handle that identifies a type loaded into the runtime.</span></span>  
  
 <span data-ttu-id="14846-118">Lorsque le type représentant le ICorDebugType n’a pas encore été chargé, cette méthode retourne `CORDBG_E_CLASS_NOT_LOADED`.</span><span class="sxs-lookup"><span data-stu-id="14846-118">When the type that the ICorDebugType represents has not yet been loaded, this method returns `CORDBG_E_CLASS_NOT_LOADED`.</span></span>  <span data-ttu-id="14846-119">Si le type n’est pas pris en charge, elle retourne `CORDBG_E_UNSUPPORTED`.</span><span class="sxs-lookup"><span data-stu-id="14846-119">If the type is not supported, it returns `CORDBG_E_UNSUPPORTED`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14846-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="14846-120">Requirements</span></span>  
 <span data-ttu-id="14846-121">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14846-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14846-122">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="14846-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14846-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14846-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14846-124">**Versions du .NET framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14846-124">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14846-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14846-125">See Also</span></span>  
 [<span data-ttu-id="14846-126">Interface de ICorDebugType2</span><span class="sxs-lookup"><span data-stu-id="14846-126">ICorDebugType2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)