---
title: ICorDebugExceptionObjectCallStackEnum, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugExceptionObjectCallStackEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugExceptionObjectCallStackEnum
helpviewer_keywords: ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 39dffa18-c71b-48c4-b11d-e814631ab1e9
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4814de2de71ba0fa4d1400f0be27fa4942febf54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a><span data-ttu-id="815ac-102">ICorDebugExceptionObjectCallStackEnum, interface</span><span class="sxs-lookup"><span data-stu-id="815ac-102">ICorDebugExceptionObjectCallStackEnum Interface</span></span>
<span data-ttu-id="815ac-103">Fournit un énumérateur pour les informations de la pile des appels qui sont incorporées dans un objet exception.</span><span class="sxs-lookup"><span data-stu-id="815ac-103">Provides an enumerator for call stack information that is embedded in an exception object.</span></span> <span data-ttu-id="815ac-104">Cette interface est une sous-classe de l’interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="815ac-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="815ac-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="815ac-105">Methods</span></span>  
  
|<span data-ttu-id="815ac-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="815ac-106">Method</span></span>|<span data-ttu-id="815ac-107">Description</span><span class="sxs-lookup"><span data-stu-id="815ac-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="815ac-108">ICorDebugExceptionObjectCallStackEnum::Next</span><span class="sxs-lookup"><span data-stu-id="815ac-108">ICorDebugExceptionObjectCallStackEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md)|<span data-ttu-id="815ac-109">Obtient un nombre spécifié de [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) les objets qui contiennent des informations sur la pile des appels d’un objet exception.</span><span class="sxs-lookup"><span data-stu-id="815ac-109">Gets a specified number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects that contain information about an exception object's call stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="815ac-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="815ac-110">Remarks</span></span>  
 <span data-ttu-id="815ac-111">Le `ICorDebugExceptionObjectCallStackEnum` interface implémente l’interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="815ac-111">The `ICorDebugExceptionObjectCallStackEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="815ac-112">Un `ICorDebugExceptionObjectCallStackEnum` instance est remplie avec [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objets en appelant le [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="815ac-112">An `ICorDebugExceptionObjectCallStackEnum` instance is populated with [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects by calling the [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) method.</span></span> <span data-ttu-id="815ac-113">Les éléments de la pile des appels dans la collection peuvent être énumérés en appelant le [ICorDebugExceptionObjectCallStackEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md) (méthode)</span><span class="sxs-lookup"><span data-stu-id="815ac-113">The call stack items in the collection can be enumerated by calling the [ICorDebugExceptionObjectCallStackEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md) method</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="815ac-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="815ac-114">Requirements</span></span>  
 <span data-ttu-id="815ac-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="815ac-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="815ac-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="815ac-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="815ac-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="815ac-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="815ac-118">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="815ac-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="815ac-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="815ac-119">See Also</span></span>  
 [<span data-ttu-id="815ac-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="815ac-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="815ac-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="815ac-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)