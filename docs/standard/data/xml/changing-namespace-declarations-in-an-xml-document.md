---
title: Modification des déclarations d'espace de noms dans un document XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2fa41e8a4e8f5a15d789ddc81c2b94072c6f16b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568054"
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a>Modification des déclarations d'espace de noms dans un document XML
**XmlDocument** expose des déclarations d'espace de noms et des attributs **xmlns** dans le cadre du modèle objet de document. Ceux-ci sont stockés dans **XmlDocument**. C'est pourquoi le document peut préserver l'emplacement de ces attributs quand il est enregistré. Modifier ces attributs n’a aucun effet sur les propriétés **Name**, **NamespaceURI** et **Prefix** d’autres nœuds figurant déjà dans l’arborescence. Par exemple, si vous chargez le document suivant, l'élément `test` a un **NamespaceURI** `123.`.  
  
```xml  
<test xmlns="123"/>  
```  
  
 Si vous supprimez l'attribut `xmlns` comme suit, l'élément `test` a encore un **NamespaceURI** `123`.  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 De même, si vous ajoutez un autre attribut `xmlns` à l'élément `doc` comme suit, l'élément `test` a encore le **NamespaceURI** `123`.  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 C'est pourquoi, la modification d'attributs `xmlns` n'a aucune incidence tant que vous n'avez pas enregistré et rechargé l'objet **XmlDocument**.  
  
## <a name="see-also"></a>Voir aussi  
 [DOM (Document Object Model) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
