---
title: ICorDebugEval2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2
helpviewer_keywords: ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: fce34531-2687-406d-9131-d6ad94f2ce0e
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fbcf36ff7aca84299c55083b4ae135ce0a9ec4f3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugeval2-interface1"></a><span data-ttu-id="d7c50-102">ICorDebugEval2 Interface1</span><span class="sxs-lookup"><span data-stu-id="d7c50-102">ICorDebugEval2 Interface1</span></span>
<span data-ttu-id="d7c50-103">Étend « ICorDebugEval » pour prendre en charge pour les types génériques.</span><span class="sxs-lookup"><span data-stu-id="d7c50-103">Extends "ICorDebugEval" to provide support for generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d7c50-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d7c50-104">Methods</span></span>  
  
|<span data-ttu-id="d7c50-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="d7c50-105">Method</span></span>|<span data-ttu-id="d7c50-106">Description</span><span class="sxs-lookup"><span data-stu-id="d7c50-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d7c50-107">CallParameterizedFunction (méthode)</span><span class="sxs-lookup"><span data-stu-id="d7c50-107">CallParameterizedFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)|<span data-ttu-id="d7c50-108">Définit un appel à « ICorDebugFunction spécifié », qui peut être imbriquée à l’intérieur d’un type dont le constructeur prend des paramètres de type, ou peut lui-même prendre des paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="d7c50-108">Sets up a call to the specified "ICorDebugFunction", which can be nested inside a type whose constructor takes type parameters, or can itself take type parameters.</span></span>|  
|[<span data-ttu-id="d7c50-109">CreateValueForType (méthode)</span><span class="sxs-lookup"><span data-stu-id="d7c50-109">CreateValueForType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)|<span data-ttu-id="d7c50-110">Obtient un pointeur vers un nouvel « ICorDebugValue » du type spécifié, avec une valeur initiale de zéro ou null.</span><span class="sxs-lookup"><span data-stu-id="d7c50-110">Gets a pointer to a new "ICorDebugValue" of the specified type, with an initial value of null or zero.</span></span>|  
|[<span data-ttu-id="d7c50-111">NewParameterizedArray (méthode)</span><span class="sxs-lookup"><span data-stu-id="d7c50-111">NewParameterizedArray Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)|<span data-ttu-id="d7c50-112">Alloue un nouveau tableau du type d’élément spécifié et de dimensions.</span><span class="sxs-lookup"><span data-stu-id="d7c50-112">Allocates a new array of the specified element type and dimensions.</span></span>|  
|[<span data-ttu-id="d7c50-113">NewParameterizedObject (méthode)</span><span class="sxs-lookup"><span data-stu-id="d7c50-113">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)|<span data-ttu-id="d7c50-114">Instancie un nouvel objet de type paramétré et appelle la méthode de constructeur de l’objet.</span><span class="sxs-lookup"><span data-stu-id="d7c50-114">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>|  
|[<span data-ttu-id="d7c50-115">NewParameterizedObjectNoConstructor (méthode)</span><span class="sxs-lookup"><span data-stu-id="d7c50-115">NewParameterizedObjectNoConstructor Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)|<span data-ttu-id="d7c50-116">Instancie un nouvel objet de type paramétré de la classe spécifiée sans essayer d’appeler une méthode de constructeur</span><span class="sxs-lookup"><span data-stu-id="d7c50-116">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method</span></span>|  
|[<span data-ttu-id="d7c50-117">NewStringWithLength (méthode)</span><span class="sxs-lookup"><span data-stu-id="d7c50-117">NewStringWithLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newstringwithlength-method.md)|<span data-ttu-id="d7c50-118">Crée une nouvelle chaîne de la longueur spécifiée avec le contenu spécifié.</span><span class="sxs-lookup"><span data-stu-id="d7c50-118">Creates a new string of the specified length with the specified contents.</span></span>|  
|[<span data-ttu-id="d7c50-119">RudeAbort, méthode</span><span class="sxs-lookup"><span data-stu-id="d7c50-119">RudeAbort Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-rudeabort-method.md)|<span data-ttu-id="d7c50-120">Abandonne le calcul par ce `ICorDebugEval2` est en cours.</span><span class="sxs-lookup"><span data-stu-id="d7c50-120">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7c50-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="d7c50-121">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7c50-122">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="d7c50-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7c50-123">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d7c50-123">Requirements</span></span>  
 <span data-ttu-id="d7c50-124">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7c50-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7c50-125">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7c50-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7c50-126">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7c50-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7c50-127">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7c50-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7c50-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7c50-128">See Also</span></span>  
 [<span data-ttu-id="d7c50-129">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="d7c50-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)