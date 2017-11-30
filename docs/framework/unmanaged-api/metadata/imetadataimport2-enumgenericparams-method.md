---
title: "IMetaDataImport2::EnumGenericParams, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.EnumGenericParams
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::EnumGenericParams
helpviewer_keywords:
- EnumGenericParams method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParams method [.NET Framework metadata]
ms.assetid: b50488a5-3cf0-483c-82dc-2892a3ec61ac
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0e6a5dc6cd1d82a3ccd46b09e301a84f90a3f429
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2enumgenericparams-method"></a><span data-ttu-id="b361f-102">IMetaDataImport2::EnumGenericParams, méthode</span><span class="sxs-lookup"><span data-stu-id="b361f-102">IMetaDataImport2::EnumGenericParams Method</span></span>
<span data-ttu-id="b361f-103">Obtient un énumérateur pour un tableau de jetons de paramètres génériques associé avec le TypeDef spécifié ou MethodDef, jeton.</span><span class="sxs-lookup"><span data-stu-id="b361f-103">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b361f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b361f-104">Syntax</span></span>  
  
```  
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,   
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],   
   [in]  ULONG            cMax,   
   [out] ULONG            *pcGenericParams  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b361f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b361f-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="b361f-106">[dans, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="b361f-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="b361f-107">[in] Le jeton TypeDef ou MethodDef dont les paramètres génériques doivent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="b361f-107">[in] The TypeDef or MethodDef token whose generic parameters are to be enumerated.</span></span>  
  
 `rGenericParams`  
 <span data-ttu-id="b361f-108">[out] Le tableau de paramètres génériques à énumérer.</span><span class="sxs-lookup"><span data-stu-id="b361f-108">[out] The array of generic parameters to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b361f-109">[in] Nombre maximal demandé de jetons à placer dans `rGenericParams`.</span><span class="sxs-lookup"><span data-stu-id="b361f-109">[in] The requested maximum number of tokens to place in `rGenericParams`.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="b361f-110">[out] Le nombre retourné de jetons placé dans `rGenericParams`.</span><span class="sxs-lookup"><span data-stu-id="b361f-110">[out] The returned number of tokens placed in `rGenericParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b361f-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b361f-111">Return Value</span></span>  
  
|<span data-ttu-id="b361f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b361f-112">HRESULT</span></span>|<span data-ttu-id="b361f-113">Description</span><span class="sxs-lookup"><span data-stu-id="b361f-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b361f-114">`EnumGenericParams`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="b361f-114">`EnumGenericParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b361f-115">`phEnum`ne contient aucun élément de membre.</span><span class="sxs-lookup"><span data-stu-id="b361f-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="b361f-116">Dans ce cas, `pcGenericParams` est définie sur 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="b361f-116">In this case, `pcGenericParams` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b361f-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b361f-117">Requirements</span></span>  
 <span data-ttu-id="b361f-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b361f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b361f-119">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b361f-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b361f-120">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b361f-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b361f-121">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b361f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b361f-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b361f-122">See Also</span></span>  
 [<span data-ttu-id="b361f-123">IMetaDataImport2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="b361f-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="b361f-124">IMetaDataImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="b361f-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)