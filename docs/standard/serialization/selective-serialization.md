---
title: Sérialisation sélective
ms.date: 08/07/2017
dev_langs:
- CSharp
helpviewer_keywords:
- serialization, selective serialization
- binary serialization, selective serialization
ms.assetid: 39c56635-95d2-4afd-aff1-b022e7649bb3
ms.openlocfilehash: 6a91501c4c3763250a64c9849694bc4e5fa4829f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581535"
---
# <a name="selective-serialization"></a>Sérialisation sélective
Une classe contient souvent des champs qui ne doivent pas être sérialisés. Par exemple, supposez qu'une classe stocke un ID de thread dans une variable membre. Quand la classe est désérialisée, il se peut que le thread stocké pour l’ID au moment de la sérialisation de la classe ne s’exécute plus. La sérialisation de cette valeur est donc inutile. Vous pouvez empêcher des variables membres d’être sérialisées en les marquant avec l’attribut [NonSerialized](xref:System.NonSerializedAttribute) comme suit.  
  
```csharp  
[Serializable]  
public class MyObject   
{  
  public int n1;  
  [NonSerialized] public int n2;  
  public String str;  
}  
```

Si possible, faites en sorte qu'un objet pouvant contenir des données de sécurité sensibles soit non sérialisable. Si l’objet doit être sérialisé, appliquez l’attribut `NonSerialized` aux champs spécifiques qui stockent des données sensibles. Si vous n’excluez pas ces champs de la sérialisation, notez que les données qu’ils stockent sont exposées à tout code autorisé à sérialiser. Pour plus d’informations sur l’écriture de code de sérialisation sécurisé, consultez [Sécurité et sérialisation](../../../docs/framework/misc/security-and-serialization.md).

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a>Voir aussi  
 [Sérialisation binaire](binary-serialization.md)  
 [Sérialisation XML et SOAP](xml-and-soap-serialization.md)  
 [Sécurité et sérialisation](../../../docs/framework/misc/security-and-serialization.md)