---
title: Guide pratique pour interroger LINQ to XML à l’aide de XPath (C#)
ms.date: 07/20/2015
ms.assetid: ee5af263-4ab1-45e5-b792-33a3221b426d
ms.openlocfilehash: a02149719afa19350a9baf15c41bd3548daa1344
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37959853"
---
# <a name="how-to-query-linq-to-xml-using-xpath-c"></a>Guide pratique pour interroger LINQ to XML à l’aide de XPath (C#)
Cette rubrique présente les méthodes d’extension qui vous permettent d’interroger une arborescence XML à l’aide de XPath. Pour plus d'informations sur l'utilisation de ces méthodes d'extension, consultez <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.  
  
 À moins que vous n’ayez une raison spécifique pour interroger à l’aide de XPath, par exemple en cas d’utilisation intensive de code hérité, l’utilisation de XPath avec LINQ to XML n’est pas recommandée. Les requêtes XPath présentent des performances inférieures à celles des requêtes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
## <a name="example"></a>Exemple  
 L'exemple suivant crée une petite arborescence XML et utilise <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> pour sélectionner un ensemble d'éléments.  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", 1),  
    new XElement("Child1", 2),  
    new XElement("Child1", 3),  
    new XElement("Child2", 4),  
    new XElement("Child2", 5),  
    new XElement("Child2", 6)  
);  
IEnumerable<XElement> list = root.XPathSelectElements("./Child2");  
foreach (XElement el in list)  
    Console.WriteLine(el);  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Techniques de requêtes avancées (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
