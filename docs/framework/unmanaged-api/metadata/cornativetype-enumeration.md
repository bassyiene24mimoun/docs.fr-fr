---
title: CorNativeType, énumération
ms.date: 03/30/2017
api_name:
- CorNativeType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeType
helpviewer_keywords:
- CorNativeType enumeration [.NET Framework metadata]
ms.assetid: e47a72f1-9609-48ed-bb34-97170d7f6890
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b28fe8e8fd8b602a01b6358f46f60cdf792ced0d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448623"
---
# <a name="cornativetype-enumeration"></a>CorNativeType, énumération
Contient des valeurs qui décrivent les types non managés natifs.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorNativeType {  
  
    NATIVE_TYPE_END                  = 0x0,  
    NATIVE_TYPE_VOID                 = 0x1,  
    NATIVE_TYPE_BOOLEAN              = 0x2,  
    NATIVE_TYPE_I1                   = 0x3,  
    NATIVE_TYPE_U1                   = 0x4,  
    NATIVE_TYPE_I2                   = 0x5,  
    NATIVE_TYPE_U2                   = 0x6,  
    NATIVE_TYPE_I4                   = 0x7,  
    NATIVE_TYPE_U4                   = 0x8,  
    NATIVE_TYPE_I8                   = 0x9,  
    NATIVE_TYPE_U8                   = 0xa,  
    NATIVE_TYPE_R4                   = 0xb,  
    NATIVE_TYPE_R8                   = 0xc,  
    NATIVE_TYPE_SYSCHAR              = 0xd,  
    NATIVE_TYPE_VARIANT              = 0xe,  
    NATIVE_TYPE_CURRENCY             = 0xf,  
    NATIVE_TYPE_PTR                  = 0x10,  
  
    NATIVE_TYPE_DECIMAL              = 0x11,  
    NATIVE_TYPE_DATE                 = 0x12,  
    NATIVE_TYPE_BSTR                 = 0x13,  
    NATIVE_TYPE_LPSTR                = 0x14,  
    NATIVE_TYPE_LPWSTR               = 0x15,  
    NATIVE_TYPE_LPTSTR               = 0x16,  
    NATIVE_TYPE_FIXEDSYSSTRING       = 0x17,  
    NATIVE_TYPE_OBJECTREF            = 0x18,  
    NATIVE_TYPE_IUNKNOWN             = 0x19,  
    NATIVE_TYPE_IDISPATCH            = 0x1a,  
    NATIVE_TYPE_STRUCT               = 0x1b,  
    NATIVE_TYPE_INTF                 = 0x1c,  
    NATIVE_TYPE_SAFEARRAY            = 0x1d,  
    NATIVE_TYPE_FIXEDARRAY           = 0x1e,  
    NATIVE_TYPE_INT                  = 0x1f,  
    NATIVE_TYPE_UINT                 = 0x20,  
  
    NATIVE_TYPE_NESTEDSTRUCT         = 0x21,  
    NATIVE_TYPE_BYVALSTR             = 0x22,  
    NATIVE_TYPE_ANSIBSTR             = 0x23,  
    NATIVE_TYPE_TBSTR                = 0x24,  
    NATIVE_TYPE_VARIANTBOOL          = 0x25,  
    NATIVE_TYPE_FUNC                 = 0x26,  
  
    NATIVE_TYPE_ASANY                = 0x28,  
    NATIVE_TYPE_ARRAY                = 0x2a,  
    NATIVE_TYPE_LPSTRUCT             = 0x2b,  
    NATIVE_TYPE_CUSTOMMARSHALER      = 0x2c,  
    NATIVE_TYPE_IINSPECTABLE         = 0x2e,  
    NATIVE_TYPE_HSTRING              = 0x2f,  
  
    NATIVE_TYPE_ERROR                = 0x2d,   
  
    NATIVE_TYPE_MAX                  = 0x50  
  
} CorNativeType;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`NATIVE_TYPE_END`|Obsolète.|  
|`NATIVE_TYPE_VOID`|Obsolète.|  
|`NATIVE_TYPE_BOOLEAN`|Une valeur booléenne de 4 octets, où la valeur TRUE est différente de zéro et la valeur FALSE est égale à zéro.|  
|`NATIVE_TYPE_I1`|Une valeur d’entier 8 bits signé.|  
|`NATIVE_TYPE_U1`|Valeur d’entier non signé 8 bits.|  
|`NATIVE_TYPE_I2`|Une valeur d’entier 16 bits signé.|  
|`NATIVE_TYPE_U2`|Valeur d’entier non signé 16 bits.|  
|`NATIVE_TYPE_I4`|Valeur d’entier 32 bits signé.|  
|`NATIVE_TYPE_U4`|Valeur d'entier 32 bits non signé.|  
|`NATIVE_TYPE_I8`|Une valeur d’entier signé 64 bits.|  
|`NATIVE_TYPE_U8`|Valeur d’entier non signé 64 bits.|  
|`NATIVE_TYPE_R4`|Une valeur numérique à virgule flottante de 4 octets.|  
|`NATIVE_TYPE_R8`|Une valeur numérique à virgule flottante de 8 octets.|  
|`NATIVE_TYPE_SYSCHAR`|Obsolète.|  
|`NATIVE_TYPE_VARIANT`|Obsolète.|  
|`NATIVE_TYPE_CURRENCY`|Type COM numérique qui correspond à la <xref:System.Decimal> type.|  
|`NATIVE_TYPE_PTR`|Obsolète.|  
|`NATIVE_TYPE_DECIMAL`|Obsolète.|  
|`NATIVE_TYPE_DATE`|Obsolète.|  
|`NATIVE_TYPE_BSTR`|COM Interop.|  
|`NATIVE_TYPE_LPSTR`|Une valeur de chaîne LPSTR.|  
|`NATIVE_TYPE_LPWSTR`|Une valeur de chaîne LPWSTR.|  
|`NATIVE_TYPE_LPTSTR`|Une valeur de chaîne LPTSTR.|  
|`NATIVE_TYPE_FIXEDSYSSTRING`|Valeur de chaîne fixe, définie par le système.|  
|`NATIVE_TYPE_OBJECTREF`|Obsolète.|  
|`NATIVE_TYPE_IUNKNOWN`|COM Interop.|  
|`NATIVE_TYPE_IDISPATCH`|COM Interop.|  
|`NATIVE_TYPE_STRUCT`|Une valeur de la structure native.|  
|`NATIVE_TYPE_INTF`|COM Interop.|  
|`NATIVE_TYPE_SAFEARRAY`|COM Interop.|  
|`NATIVE_TYPE_FIXEDARRAY`|Une valeur de tableau de longueur fixe.|  
|`NATIVE_TYPE_INT`|Une valeur d’entier signé de 16 bits natif.|  
|`NATIVE_TYPE_UINT`|Une valeur d’entier non signé de 16 bits natif.|  
|`NATIVE_TYPE_NESTEDSTRUCT`|Obsolète.<br /><br /> Utilisez NATIVE_TYPE_STRUCT.|  
|`NATIVE_TYPE_BYVALSTR`|COM Interop.|  
|`NATIVE_TYPE_ANSIBSTR`|COM Interop.|  
|`NATIVE_TYPE_TBSTR`|COM Interop.<br /><br /> Sélectionnez BSTR ou ANSIBSTR selon la plateforme.|  
|`NATIVE_TYPE_VARIANTBOOL`|Valeur booléenne sur 2 octets où TRUE est -1 et FALSE est nul.|  
|`NATIVE_TYPE_FUNC`|Pointeur de fonction.|  
|`NATIVE_TYPE_ASANY`|Une référence à n’importe quel type natif.|  
|`NATIVE_TYPE_ARRAY`|Une référence à un tableau avec les membres de type non spécifié.|  
|`NATIVE_TYPE_LPSTRUCT`|Un pointeur d’entier 32 bits vers une structure.|  
|`NATIVE_TYPE_CUSTOMMARSHALER`|Un type natif de marshaleur personnalisé.<br /><br /> Cela doit être suivi d’une chaîne au format suivant : « type de marshaleur nom/0Nom de type natif/0Cookie facultatif cookie/0 » ou « {Native de type GUID} / 0Nom marshaleur type/0Cookie facultatif cookie/0 »|  
|`NATIVE_TYPE_ERROR`|COM Interop.<br /><br /> Avec ELEMENT_TYPE_I4, ce type mappe vers VT_HRESULT.|  
|`NATIVE_TYPE_IINSPECTABLE`|Natif `IInspectable` type.|  
|`NATIVE_TYPE_HSTRING`|Natif `HString`.|  
|`NATIVE_TYPE_MAX`|Une valeur non valide.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorHdr.h  
  
 **Versions du .NET framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.InteropServices.UnmanagedType>  
 [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
