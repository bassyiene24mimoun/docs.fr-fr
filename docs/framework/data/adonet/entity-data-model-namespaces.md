---
title: 'Entity Data Model : espaces de noms'
ms.date: 03/30/2017
ms.assetid: 98ab4226-bb9f-44e7-af46-61a9b1a4e47c
ms.openlocfilehash: 0fdb007e70b7dd2e4a812d711cb6348e3f563bad
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765228"
---
# <a name="entity-data-model-namespaces"></a>Entity Data Model : espaces de noms
Un espace de noms dans le modèle EDM (Entity Data Model) est un conteneur abstrait pour [types d’entités](../../../../docs/framework/data/adonet/entity-type.md), [types complexes](../../../../docs/framework/data/adonet/complex-type.md), et [associations](../../../../docs/framework/data/adonet/association-type.md). Les espaces de noms dans le modèle EDM sont semblables aux espaces de noms dans un langage de programmation : ils fournissent le contexte pour les objets qu'ils contiennent et offrent un moyen de lever l'ambiguïté entre les objets qui portent le même nom (mais qui sont contenus dans des espaces de noms différents).  
  
## <a name="example"></a>Exemple  
 Le [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) pour définir des modèles conceptuels. Le CSDL suivant utilise un espace de noms pour identifier un type défini dans un modèle conceptuel différent. L'exemple définit un type d'entité (`Publisher`) qui a une propriété de type complexe (`Address`) importée à partir de l'espace de noms `ExtendedBooksModel`. Notez que l'élément `Using` indique qu'un espace de noms a été importé. Notez également que le type de la propriété `Address` est défini à l'aide de son nom qualifié complet (`ExtendedBooksModel.Address`), ce qui indique que ce type est défini dans l'espace de noms `ExtendedBooksModel`.  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts clés d’Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
