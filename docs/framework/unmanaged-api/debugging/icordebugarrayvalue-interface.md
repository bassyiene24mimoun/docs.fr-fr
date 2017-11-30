---
title: ICorDebugArrayValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugArrayValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugArrayValue interface
helpviewer_keywords: ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: dc437751-7093-44e2-bfdc-191d9ce3c192
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 13e226ccdcd6becc98d524c429b5cadae8d19c3e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugarrayvalue-interface1"></a><span data-ttu-id="6bf75-102">ICorDebugArrayValue Interface1</span><span class="sxs-lookup"><span data-stu-id="6bf75-102">ICorDebugArrayValue Interface1</span></span>
<span data-ttu-id="6bf75-103">Une sous-classe de ICorDebugHeapValue qui représente un tableau unidimensionnel ou multidimensionnel.</span><span class="sxs-lookup"><span data-stu-id="6bf75-103">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6bf75-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="6bf75-104">Methods</span></span>  
  
|<span data-ttu-id="6bf75-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="6bf75-105">Method</span></span>|<span data-ttu-id="6bf75-106">Description</span><span class="sxs-lookup"><span data-stu-id="6bf75-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6bf75-107">GetBaseIndicies (méthode)</span><span class="sxs-lookup"><span data-stu-id="6bf75-107">GetBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="6bf75-108">Obtient l’index de base de chaque dimension du tableau.</span><span class="sxs-lookup"><span data-stu-id="6bf75-108">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="6bf75-109">GetCount (méthode)</span><span class="sxs-lookup"><span data-stu-id="6bf75-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="6bf75-110">Obtient le nombre total d’éléments dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="6bf75-110">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="6bf75-111">GetDimensions (méthode)</span><span class="sxs-lookup"><span data-stu-id="6bf75-111">GetDimensions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="6bf75-112">Obtient les dimensions du tableau.</span><span class="sxs-lookup"><span data-stu-id="6bf75-112">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="6bf75-113">GetElement (méthode)</span><span class="sxs-lookup"><span data-stu-id="6bf75-113">GetElement Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="6bf75-114">Obtient une valeur qui représente l’élément donné dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="6bf75-114">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="6bf75-115">GetElementAtPosition (méthode)</span><span class="sxs-lookup"><span data-stu-id="6bf75-115">GetElementAtPosition Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="6bf75-116">Obtient l’élément à la position donnée, en traitant le tableau comme un tableau unidimensionnel de base zéro.</span><span class="sxs-lookup"><span data-stu-id="6bf75-116">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="6bf75-117">GetElementType (méthode)</span><span class="sxs-lookup"><span data-stu-id="6bf75-117">GetElementType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="6bf75-118">Obtient le type simple des éléments dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="6bf75-118">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="6bf75-119">GetRank (méthode)</span><span class="sxs-lookup"><span data-stu-id="6bf75-119">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="6bf75-120">Obtient le nombre de dimensions dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="6bf75-120">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="6bf75-121">HasBaseIndicies (méthode)</span><span class="sxs-lookup"><span data-stu-id="6bf75-121">HasBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="6bf75-122">Détermine si le tableau a des index de base.</span><span class="sxs-lookup"><span data-stu-id="6bf75-122">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6bf75-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="6bf75-123">Remarks</span></span>  
 <span data-ttu-id="6bf75-124">`ICorDebugArrayValue`prend en charge les tableaux unidimensionnels et multidimensionnels.</span><span class="sxs-lookup"><span data-stu-id="6bf75-124">`ICorDebugArrayValue` supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6bf75-125">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="6bf75-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bf75-126">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6bf75-126">Requirements</span></span>  
 <span data-ttu-id="6bf75-127">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bf75-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bf75-128">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6bf75-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6bf75-129">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6bf75-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bf75-130">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bf75-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bf75-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6bf75-131">See Also</span></span>  
 [<span data-ttu-id="6bf75-132">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="6bf75-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)