---
title: QualifierSet_Get (fonction) (référence des API non managées)
description: La fonction QualifierSet_Get Obtient un qualificateur nommé.
ms.date: 11/06/2017
api_name:
- QualifierSet_Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Get
helpviewer_keywords:
- QualifierSet_Get function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1bc57ab45a0452d9e3a50f0ab2de786ad73204a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458645"
---
# <a name="qualifiersetget-function"></a>QualifierSet_Get (fonction)
Obtient le qualificateur nommé spécifié.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT QualifierSet_Get (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName,
   [in] LONG                 lFlags,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a>Paramètres

`vFunc`   
[in] Ce paramètre est inutilisé.

`ptr`   
[in] Un pointeur vers un [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.

`wszName`   
[in] Le nom du qualificateur dont la valeur est demandée.

`lFlags`   
[in] Réservé. Ce paramètre doit être 0.

`pVal`   
[out] Cas de réussite, le type correct et la valeur du qualificateur. Si la fonction échoue, la `VARIANT` vers lequel pointe `pVal` n’est pas modifié. Si ce paramètre est `null`, le paramètre est ignoré.

`plFlavor`   
[out] Pointeur vers un entier LONG qui reçoit les bits de la version qualificateur pour le qualificateur demandé. Si les informations de version ne sont pas souhaitées, ce paramètre peut être `null`. 

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Value  |Description  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0 x 80041008 | Un paramètre n’est pas valide. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Le qualificateur spécifié n’existe pas. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi.  |
  
## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la [IWbemQualifierSet::Get](https://msdn.microsoft.com/library/aa391867(v=vs.85).aspx) (méthode).

## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi  
[WMI et les compteurs de Performance (référence des API non managées)](index.md)
