---
title: Interfaces de profilage
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
caps.latest.revision: "31"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5c0423f9c8b01c1289e1107c0c16c59968a6e2a4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="profiling-interfaces"></a><span data-ttu-id="36c07-102">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="36c07-102">Profiling Interfaces</span></span>
<span data-ttu-id="36c07-103">Cette section décrit les interfaces non managées qui vous permettent de profiler un programme exécuté par le CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="36c07-103">This section describes the unmanaged interfaces that enable you to profile a program that is being executed by the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="36c07-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="36c07-104">In This Section</span></span>  
 [<span data-ttu-id="36c07-105">ICLRProfiling (Interface)</span><span class="sxs-lookup"><span data-stu-id="36c07-105">ICLRProfiling Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-interface.md)  
 <span data-ttu-id="36c07-106">Fournit la [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) (méthode), ce qui permet à un profileur de s’attacher à un processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="36c07-106">Provides the [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method, which enables a profiler to attach to a running process.</span></span>  
  
 [<span data-ttu-id="36c07-107">Icorprofilerassemblyreferenceprovider, Interface</span><span class="sxs-lookup"><span data-stu-id="36c07-107">ICorProfilerAssemblyReferenceProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 <span data-ttu-id="36c07-108">Permet au profileur d’informer le CLR de références d’assembly que le profileur ajoutera dans le [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) rappel.</span><span class="sxs-lookup"><span data-stu-id="36c07-108">Enables the profiler to inform the CLR of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
 [<span data-ttu-id="36c07-109">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="36c07-109">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 <span data-ttu-id="36c07-110">Fournit des méthodes qui sont utilisées par le CLR pour envoyer des notifications à un profileur de code quand les événements auxquels le profileur s'est abonné se produisent.</span><span class="sxs-lookup"><span data-stu-id="36c07-110">Provides methods that are used by the CLR to notify a code profiler when the events to which the profiler has subscribed occur.</span></span>  
  
 [<span data-ttu-id="36c07-111">ICorProfilerCallback2, Interface</span><span class="sxs-lookup"><span data-stu-id="36c07-111">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 <span data-ttu-id="36c07-112">Étend l'interface `ICorProfilerCallback` avec des rappels pris en charge dans .NET Framework 2.0 et ultérieur.</span><span class="sxs-lookup"><span data-stu-id="36c07-112">Extends the `ICorProfilerCallback` interface with callbacks supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="36c07-113">ICorProfilerCallback3 (Interface)</span><span class="sxs-lookup"><span data-stu-id="36c07-113">ICorProfilerCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 <span data-ttu-id="36c07-114">Fournit des méthodes de rappel que le CLR utilise pour communiquer au profileur des informations d'état d'attachement et de détachement.</span><span class="sxs-lookup"><span data-stu-id="36c07-114">Provides callback methods that the CLR uses to communicate attach and detach state information to the profiler.</span></span>  
  
 [<span data-ttu-id="36c07-115">ICorProfilerCallback4 (Interface)</span><span class="sxs-lookup"><span data-stu-id="36c07-115">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 <span data-ttu-id="36c07-116">Fournit des méthodes de rappel que le CLR utilise pour communiquer des informations au profileur.</span><span class="sxs-lookup"><span data-stu-id="36c07-116">Provides callback methods that the CLR uses to communicate information to the profiler.</span></span>  
  
 [<span data-ttu-id="36c07-117">ICorProfilerCallback5 (Interface)</span><span class="sxs-lookup"><span data-stu-id="36c07-117">ICorProfilerCallback5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)  
 <span data-ttu-id="36c07-118">Fournit une méthode qui identifie la fermeture transitive d’objets référencés par des racines de récupération de mémoire.</span><span class="sxs-lookup"><span data-stu-id="36c07-118">Provides a method that identifies the transitive closure of objects referenced by garbage collection roots.</span></span>  
  
 [<span data-ttu-id="36c07-119">Icorprofilercallback6, Interface</span><span class="sxs-lookup"><span data-stu-id="36c07-119">ICorProfilerCallback6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 <span data-ttu-id="36c07-120">Fournit une méthode de rappel utilisée par le CLR pour envoyer une notification à un profileur quand un assembly est en cours de chargement.</span><span class="sxs-lookup"><span data-stu-id="36c07-120">Provides a callback method that the CLR uses to notify a profiler that an assembly is loading.</span></span>  
  
 [<span data-ttu-id="36c07-121">Interface ICorProfilerCallback7</span><span class="sxs-lookup"><span data-stu-id="36c07-121">ICorProfilerCallback7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)  
 <span data-ttu-id="36c07-122">Fournit une méthode de rappel que le common language runtime utilise pour informer le profileur que le flux de symbole associé à un module en mémoire est mis à jour.</span><span class="sxs-lookup"><span data-stu-id="36c07-122">Provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
 [<span data-ttu-id="36c07-123">ICorProfilerFunctionControl (Interface)</span><span class="sxs-lookup"><span data-stu-id="36c07-123">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)  
 <span data-ttu-id="36c07-124">Fournit des méthodes qui permettent à un profileur de code de communiquer avec le CLR (Common Language Runtime) pour contrôler comment le compilateur juste-à-temps doit générer du code lors de la recompilation d'une méthode spécifique.</span><span class="sxs-lookup"><span data-stu-id="36c07-124">Provides methods that allow a code profiler to communicate with the CLR to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
 [<span data-ttu-id="36c07-125">ICorProfilerFunctionEnum (Interface)</span><span class="sxs-lookup"><span data-stu-id="36c07-125">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 <span data-ttu-id="36c07-126">Fournit des méthodes pour boucler séquentiellement dans une collection de fonctions dans le CLR.</span><span class="sxs-lookup"><span data-stu-id="36c07-126">Provides methods to sequentially iterate through a collection of functions in the CLR.</span></span>  
  
 [<span data-ttu-id="36c07-127">ICorProfilerInfo (Interface)</span><span class="sxs-lookup"><span data-stu-id="36c07-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 <span data-ttu-id="36c07-128">Fournit des méthodes utilisées par les profileurs de code pour communiquer avec le CLR pour contrôler la surveillance des événements et demander des informations.</span><span class="sxs-lookup"><span data-stu-id="36c07-128">Provides methods for use by code profilers to communicate with the CLR to control event monitoring and request information.</span></span>  
  
 [<span data-ttu-id="36c07-129">ICorProfilerInfo2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="36c07-129">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 <span data-ttu-id="36c07-130">Étend l'interface `ICorProfilerInfo` avec des méthodes prises en charge dans .NET Framework 2.0 et ultérieur.</span><span class="sxs-lookup"><span data-stu-id="36c07-130">Extends the `ICorProfilerInfo` interface with methods supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="36c07-131">ICorProfilerInfo3 (Interface)</span><span class="sxs-lookup"><span data-stu-id="36c07-131">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 <span data-ttu-id="36c07-132">Étend l'interface `ICorProfilerInfo2` avec des méthodes prises en charge dans [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] et ultérieur.</span><span class="sxs-lookup"><span data-stu-id="36c07-132">Extends the `ICorProfilerInfo2` interface with methods supported in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] and later versions.</span></span>  
  
 [<span data-ttu-id="36c07-133">Icorprofilerinfo4, Interface</span><span class="sxs-lookup"><span data-stu-id="36c07-133">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 <span data-ttu-id="36c07-134">Fournit des méthodes utilisées par les profileurs de code pour communiquer avec le CLR pour contrôler la surveillance des événements et demander des informations.</span><span class="sxs-lookup"><span data-stu-id="36c07-134">Provides methods that code profilers use to communicate with the CLR to control event monitoring and to request information.</span></span>  
  
 [<span data-ttu-id="36c07-135">Icorprofilerinfo5, Interface</span><span class="sxs-lookup"><span data-stu-id="36c07-135">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 <span data-ttu-id="36c07-136">Fournit des méthodes utilisées par les profileurs de code pour communiquer avec le CLR pour contrôler la surveillance des événements.</span><span class="sxs-lookup"><span data-stu-id="36c07-136">Provides methods for use by code profilers to communicate with the CLR to control event monitoring.</span></span>  
  
 [<span data-ttu-id="36c07-137">Interface de ICorProfilerInfo6</span><span class="sxs-lookup"><span data-stu-id="36c07-137">ICorProfilerInfo6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)  
 <span data-ttu-id="36c07-138">Fournit un énumérateur pour toutes les méthodes qui appartiennent à un module NGen donné et qui sont incorporées dans le corps d’une méthode donnée.</span><span class="sxs-lookup"><span data-stu-id="36c07-138">Provides an enumerator to all the methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>  
  
 [<span data-ttu-id="36c07-139">Interface de ICorProfilerInfo7</span><span class="sxs-lookup"><span data-stu-id="36c07-139">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)  
 <span data-ttu-id="36c07-140">Fournit une méthode à appliquer qui vient d’être défini des métadonnées à un module et qui fournit l’accès à un flux de symbole de mémoire.</span><span class="sxs-lookup"><span data-stu-id="36c07-140">Provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
 [<span data-ttu-id="36c07-141">ICorProfilerModuleEnum (Interface)</span><span class="sxs-lookup"><span data-stu-id="36c07-141">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 <span data-ttu-id="36c07-142">Fournit des méthodes pour boucler séquentiellement dans une collection de modules chargés par l’application ou par le profileur.</span><span class="sxs-lookup"><span data-stu-id="36c07-142">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
 [<span data-ttu-id="36c07-143">ICorProfilerObjectEnum (Interface)</span><span class="sxs-lookup"><span data-stu-id="36c07-143">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)  
 <span data-ttu-id="36c07-144">Fournit des méthodes pour itérer séquentiellement une collection d’objets figés qui sont générés par [Ngen.exe (Native Image Generator)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="36c07-144">Provides methods to sequentially iterate through a collection of frozen objects that are generated by [Ngen.exe (Native Image Generator)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>  
  
 [<span data-ttu-id="36c07-145">ICorProfilerThreadEnum (Interface)</span><span class="sxs-lookup"><span data-stu-id="36c07-145">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 <span data-ttu-id="36c07-146">Fournit des méthodes pour boucler séquentiellement dans une collection de threads dans le CLR.</span><span class="sxs-lookup"><span data-stu-id="36c07-146">Provides methods to sequentially iterate through a collection of threads in the CLR.</span></span>  
  
 [<span data-ttu-id="36c07-147">IMethodMalloc (Interface)</span><span class="sxs-lookup"><span data-stu-id="36c07-147">IMethodMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)  
 <span data-ttu-id="36c07-148">Fournit la [Alloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) méthode pour allouer de la mémoire pour un nouveau corps de fonction MSIL (intermediate language).</span><span class="sxs-lookup"><span data-stu-id="36c07-148">Provides the [Alloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="36c07-149">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="36c07-149">Related Sections</span></span>  
 [<span data-ttu-id="36c07-150">Vue d’ensemble du profilage</span><span class="sxs-lookup"><span data-stu-id="36c07-150">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="36c07-151">Fonctions statiques globales du profilage</span><span class="sxs-lookup"><span data-stu-id="36c07-151">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="36c07-152">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="36c07-152">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [<span data-ttu-id="36c07-153">Structures de profilage</span><span class="sxs-lookup"><span data-stu-id="36c07-153">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)