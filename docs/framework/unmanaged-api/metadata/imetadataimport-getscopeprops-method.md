---
title: "IMetaDataImport::GetScopeProps, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetScopeProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetScopeProps
helpviewer_keywords:
- IMetaDataImport::GetScopeProps method [.NET Framework metadata]
- GetScopeProps method [.NET Framework metadata]
ms.assetid: c8ba42d2-d9fa-43cb-bbc0-f33e1e592cb6
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5b0936a9f47e2d0fa52816b78a7eecf3d244d594
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetscopeprops-method"></a><span data-ttu-id="bcbf5-102">IMetaDataImport::GetScopeProps, méthode</span><span class="sxs-lookup"><span data-stu-id="bcbf5-102">IMetaDataImport::GetScopeProps Method</span></span>
<span data-ttu-id="bcbf5-103">Obtient le nom et éventuellement l'identificateur de version de l'assembly ou du module dans la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="bcbf5-103">Gets the name and optionally the version identifier of the assembly or module in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcbf5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bcbf5-104">Syntax</span></span>  
  
```  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bcbf5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bcbf5-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="bcbf5-106">[out] Une mémoire tampon pour le nom de l’assembly ou du module.</span><span class="sxs-lookup"><span data-stu-id="bcbf5-106">[out] A buffer for the assembly or module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="bcbf5-107">[in] La taille en caractères larges de `szName`.</span><span class="sxs-lookup"><span data-stu-id="bcbf5-107">[in] The size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="bcbf5-108">[out] Le nombre de caractères étendus retournés dans `szName`.</span><span class="sxs-lookup"><span data-stu-id="bcbf5-108">[out] The number of wide characters returned in `szName`.</span></span>  
  
 `pmvid`  
 <span data-ttu-id="bcbf5-109">[out, facultatif] Pointeur vers un GUID qui identifie de façon unique la version de l’assembly ou le module.</span><span class="sxs-lookup"><span data-stu-id="bcbf5-109">[out, optional] A pointer to a GUID that uniquely identifies the version of the assembly or module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bcbf5-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="bcbf5-110">Remarks</span></span>  
 <span data-ttu-id="bcbf5-111">Le [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) méthode est utilisée pour définir ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="bcbf5-111">The [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) method is used to set these properties.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcbf5-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="bcbf5-112">Requirements</span></span>  
 <span data-ttu-id="bcbf5-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcbf5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcbf5-114">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bcbf5-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bcbf5-115">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bcbf5-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bcbf5-116">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcbf5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcbf5-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bcbf5-117">See Also</span></span>  
 [<span data-ttu-id="bcbf5-118">IMetaDataImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="bcbf5-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="bcbf5-119">IMetaDataImport2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="bcbf5-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)