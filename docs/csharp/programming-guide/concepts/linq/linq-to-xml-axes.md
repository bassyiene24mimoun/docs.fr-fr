---
title: Axes LINQ to XML (C#)
ms.date: 07/20/2015
ms.assetid: 3f7d54ff-b608-43a1-9e2d-e70668b72df8
ms.openlocfilehash: d12d35a6f9b02056946ba201a7bd5a961f64ba36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331488"
---
# <a name="linq-to-xml-axes-c"></a>Axes LINQ to XML (C#)
Après avoir créé une arborescence XML ou chargé un document XML dans une arborescence XML, vous pouvez l'interroger pour rechercher des éléments et des attributs et récupérer leurs valeurs.  
  
 Pour pouvoir écrire des requêtes, vous devez comprendre ce que sont les axes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Il existe deux sortes de méthodes d’axe : tout d’abord, il y a les méthodes que vous appelez sur un seul objet <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument> ou <xref:System.Xml.Linq.XNode>. Ces méthodes opèrent sur un seul objet et renvoient une collection d'objets <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XAttribute> ou <xref:System.Xml.Linq.XNode>. En second lieu, il y a des méthodes d'extension qui opèrent sur des collections et retournent des collections. Les méthodes d'extension énumèrent la collection source, appellent la méthode d'axe appropriée sur chaque élément dans la collection et concatènent les résultats.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Vue d’ensemble des axes LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)|Définit les axes et explique comment les utiliser dans le contexte des requêtes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].|  
|[Guide pratique pour récupérer une collection d’éléments (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-elements-linq-to-xml.md)|Présente la méthode <xref:System.Xml.Linq.XContainer.Elements%2A>. Cette méthode récupère une collection d’éléments enfants d’un élément.|  
|[Guide pratique pour récupérer la valeur d’un élément (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)|Montre comment obtenir les valeurs d'éléments.|  
|[Guide pratique pour filtrer sur des noms d’éléments (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-filter-on-element-names-linq-to-xml.md)|Montre comment filtrer les noms d'éléments lors de l'utilisation des axes.|  
|[Guide pratique pour chaîner des appels à des méthodes d’axe (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-chain-axis-method-calls-linq-to-xml.md)|Montre comment chaîner les appels aux méthodes d'axe.|  
|[Guide pratique pour récupérer un seul élément enfant (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md)|Montre comment récupérer un seul élément enfant d’un élément, étant donné le nom d’étiquette de l’élément enfant.|  
|[Guide pratique pour récupérer une collection d’attributs (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-attributes-linq-to-xml.md)|Présente la méthode <xref:System.Xml.Linq.XElement.Attributes%2A>. Cette méthode récupère les attributs d'un élément.|  
|[Guide pratique pour récupérer un seul attribut (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-attribute-linq-to-xml.md)|Montre comment récupérer un seul attribut d'un élément, étant donné le nom de l'attribut.|  
|[Guide pratique pour récupérer la valeur d’un attribut (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-attribute-linq-to-xml.md)|Montre comment obtenir les valeurs d'attributs.|  
|[Guide pratique pour récupérer la valeur superficielle d’un élément (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-shallow-value-of-an-element.md)|Indique comment récupérer la valeur superficielle d'un élément.|  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes d’extension](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
 [Guide de programmation (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
