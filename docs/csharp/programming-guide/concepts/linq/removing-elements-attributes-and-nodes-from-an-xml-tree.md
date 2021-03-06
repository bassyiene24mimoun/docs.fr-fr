---
title: Suppression d’éléments, d’attributs et de nœuds d’une arborescence XML (C#)
ms.date: 07/20/2015
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: 85c1adc06321abf90fe478abf5375882069f11ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339967"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-c"></a>Suppression d’éléments, d’attributs et de nœuds d’une arborescence XML (C#)
Vous pouvez modifier une arborescence XML en supprimant des éléments, des attributs et d’autres types de nœuds.  
  
 La suppression d'un seul élément ou attribut d'un document XML est simple. Toutefois, lors de la suppression de collections d'éléments ou d'attributs, vous devez tout d'abord matérialiser une collection dans une liste, puis supprimer les éléments ou attributs de la liste. La meilleure approche consiste à utiliser la méthode d'extension <xref:System.Xml.Linq.Extensions.Remove%2A>, qui effectuera cette tâche pour vous.  
  
 Cette opération est nécessaire car la plupart des collections que vous récupérez à partir d’une arborescence XML sont produites à l’aide de l’exécution différée. Si vous ne les matérialisez pas tout d’abord dans une liste, ou si vous n’utilisez pas les méthodes d’extension, vous risquez de rencontrer une certaine classe de bogues. Pour plus d’informations, consultez [Bogues liés à l’utilisation combinée de code déclaratif et de code impératif (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).  
  
 Les méthodes suivantes suppriment des nœuds et des attributs d’une arborescence XML.  
  
|Méthode|Description|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|Supprime un objet <xref:System.Xml.Linq.XAttribute> de son parent.|  
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|Supprime les nœuds enfants d'un objet <xref:System.Xml.Linq.XContainer>.|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|Supprime le contenu et les attributs d'un objet <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|Supprime les attributs d'un objet <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|Supprime l'attribut si vous passez `null` comme valeur.|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|Supprime l'élément enfant si vous passez `null` comme valeur.|  
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|Supprime un objet <xref:System.Xml.Linq.XNode> de son parent.|  
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|Supprime chaque attribut ou élément dans la collection source de son élément parent.|  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 Cet exemple illustre trois approches de la suppression d'éléments. Tout d'abord, il supprime un seul élément. Ensuite, il récupère une collection d'éléments, les matérialise à l'aide de l'opérateur <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, puis supprime la collection. Pour finir, il récupère une collection d'éléments et les supprime à l'aide de la méthode d'extension <xref:System.Xml.Linq.Extensions.Remove%2A>.  
  
 Pour plus d’informations sur l’opérateur <xref:System.Linq.Enumerable.ToList%2A>, consultez [Conversion des types de données (C#)](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md).  
  
### <a name="code"></a>Code  
  
```csharp  
XElement root = XElement.Parse(@"<Root>  
    <Child1>  
        <GrandChild1/>  
        <GrandChild2/>  
        <GrandChild3/>  
    </Child1>  
    <Child2>  
        <GrandChild4/>  
        <GrandChild5/>  
        <GrandChild6/>  
    </Child2>  
    <Child3>  
        <GrandChild7/>  
        <GrandChild8/>  
        <GrandChild9/>  
    </Child3>  
</Root>");  
root.Element("Child1").Element("GrandChild1").Remove();  
root.Element("Child2").Elements().ToList().Remove();  
root.Element("Child3").Elements().Remove();  
Console.WriteLine(root);  
```  
  
### <a name="comments"></a>Commentaires  
 Ce code génère la sortie suivante :  
  
```xml  
<Root>  
  <Child1>  
    <GrandChild2 />  
    <GrandChild3 />  
  </Child1>  
  <Child2 />  
  <Child3 />  
</Root>  
```  
  
 Notez que le premier élément petit-enfant a été supprimé de `Child1`. Tous les éléments petits-enfants ont été supprimés de `Child2` et de `Child3`.  
  
## <a name="see-also"></a>Voir aussi  
 [Modification d’arborescences XML (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
