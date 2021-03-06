---
title: Fonctions définies par l'utilisateur
ms.date: 03/30/2017
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
ms.openlocfilehash: f1222d9332d365c9c3c6ca2aa28cbb48e92c04e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33363598"
---
# <a name="user-defined-functions"></a>Fonctions définies par l'utilisateur
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] utilise des méthodes dans votre modèle objet pour représenter des fonctions définies par l'utilisateur. Vous désignez des méthodes comme des fonctions en appliquant l'attribut <xref:System.Data.Linq.Mapping.FunctionAttribute> et, si nécessaire, l'attribut <xref:System.Data.Linq.Mapping.ParameterAttribute>. Pour plus d’informations, consultez [le modèle LINQ to SQL objet](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).  
  
 Pour éviter une exception <xref:System.InvalidOperationException>, les fonctions définies par l'utilisateur dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] doivent prendre l'une des formes suivantes :  
  
-   Fonction encapsulée comme un appel de méthode disposant des attributs de mappage appropriés. Pour plus d’informations, consultez [mappage basé sur l’attribut](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
-   Méthode SQL statique spécifique à [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
-   Fonction prise en charge par une méthode [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].  
  
 Les rubriques de cette section montrent comment former et appeler ces méthodes dans votre application si vous écrivez vous-même le code. Les développeurs qui utilisent Visual Studio utilisent généralement le [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] pour mapper des fonctions définies par l’utilisateur.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour utiliser des fonctions scalaires définies par l’utilisateur](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-scalar-valued-user-defined-functions.md)  
 Décrit comment implémenter une fonction qui retourne des valeurs scalaires.  
  
 [Guide pratique pour utiliser des fonctions table définies par l’utilisateur](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-table-valued-user-defined-functions.md)  
 Décrit comment implémenter une fonction qui retourne des valeurs de table.  
  
 [Guide pratique pour appeler des fonctions inline définies par l’utilisateur](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md)  
 Décrit comment passer des appels inline à des fonctions et les différences d'exécution lorsque l'appel est rendu inline.
