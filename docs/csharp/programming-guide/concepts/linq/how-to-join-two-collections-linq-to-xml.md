---
title: Guide pratique pour joindre deux collections (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: d4e7c73262cce234dc8373d42b2a8cb366316622
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33324822"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a>Guide pratique pour joindre deux collections (LINQ to XML) (C#)
Un élément ou attribut dans un document XML peut parfois faire référence à un autre élément ou attribut. Par exemple, l’[Exemple de fichier XML : Clients et commandes (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md) contient une liste de clients et une liste de commandes. Chaque élément `Customer` contient un attribut `CustomerID`. Chaque élément `Order` contient un élément `CustomerID`. L'élément `CustomerID` dans chaque commande fait référence à l'attribut `CustomerID` dans un client.  
  
 La rubrique [Exemple de fichier XSD : Clients et commandes](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md) contient un XSD qui peut servir à valider ce document. Il utilise les fonctionnalités `xs:key` et `xs:keyref` de XSD pour déterminer que l'attribut `CustomerID` de l'élément `Customer` est une clé et pour établir une relation entre l'élément `CustomerID` dans chaque élément `Order` et l'attribut `CustomerID` dans chaque élément `Customer`.  
  
 Avec [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], vous pouvez tirer parti de cette relation en utilisant la clause `join`.  
  
 Notez que dans la mesure où aucun index n'est disponible, une telle jointure présentera de faibles performances à l'exécution.  
  
 Pour obtenir des informations détaillées sur `join`, consultez [Opérations de jointure (C#)](../../../../csharp/programming-guide/concepts/linq/join-operations.md).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant joint les éléments `Customer` aux éléments `Order` et génère un nouveau document XML qui inclut l'élément `CompanyName` dans les commandes.  
  
 Avant d’exécuter la requête, l’exemple vérifie que le document est conforme au schéma dans [Exemple de fichier XSD : Clients et commandes](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md). Cela permet de s'assurer que la clause de jointure fonctionnera toujours.  
  
 Cette requête récupère d'abord tous les éléments `Customer`, puis les joint aux éléments `Order`. Elle sélectionne uniquement les commandes pour les clients dont le `CustomerID` est supérieur à « K ». Elle projette ensuite un nouvel élément `Order` qui contient les informations relatives aux clients dans chaque commande.  
  
 Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Clients et commandes (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
 Cet exemple utilise le schéma XSD suivant : [Exemple de fichier XSD : Clients et commandes](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).  
  
 Notez que les performances d'une telle jointure ne seront pas très bonnes. Les jointures sont effectuées par le biais d'une recherche linéaire. Il n'y a aucun index ou table de hachage pour améliorer les performances.  
  
```csharp  
XmlSchemaSet schemas = new XmlSchemaSet();  
schemas.Add("", "CustomersOrders.xsd");  
  
Console.Write("Attempting to validate, ");  
XDocument custOrdDoc = XDocument.Load("CustomersOrders.xml");  
  
bool errors = false;  
custOrdDoc.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");  
  
if (!errors)  
{  
    // Join customers and orders, and create a new XML document with  
    // a different shape.  
  
    // The new document contains orders only for customers with a  
    // CustomerID > 'K'  
    XElement custOrd = custOrdDoc.Element("Root");  
    XElement newCustOrd = new XElement("Root",  
        from c in custOrd.Element("Customers").Elements("Customer")  
        join o in custOrd.Element("Orders").Elements("Order")  
                   on (string)c.Attribute("CustomerID") equals  
                      (string)o.Element("CustomerID")  
        where ((string)c.Attribute("CustomerID")).CompareTo("K") > 0  
        select new XElement("Order",  
            new XElement("CustomerID", (string)c.Attribute("CustomerID")),  
            new XElement("CompanyName", (string)c.Element("CompanyName")),  
            new XElement("ContactName", (string)c.Element("ContactName")),  
            new XElement("EmployeeID", (string)o.Element("EmployeeID")),  
            new XElement("OrderDate", (DateTime)o.Element("OrderDate"))  
        )  
    );  
    Console.WriteLine(newCustOrd);  
}  
```  
  
 Ce code génère la sortie suivante :  
  
```  
Attempting to validate, custOrdDoc validated  
<Root>  
  <Order>  
    <CustomerID>LAZYK</CustomerID>  
    <CompanyName>Lazy K Kountry Store</CompanyName>  
    <ContactName>John Steel</ContactName>  
    <EmployeeID>1</EmployeeID>  
    <OrderDate>1997-03-21T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LAZYK</CustomerID>  
    <CompanyName>Lazy K Kountry Store</CompanyName>  
    <ContactName>John Steel</ContactName>  
    <EmployeeID>8</EmployeeID>  
    <OrderDate>1997-05-22T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>1</EmployeeID>  
    <OrderDate>1997-06-25T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>8</EmployeeID>  
    <OrderDate>1997-10-27T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>6</EmployeeID>  
    <OrderDate>1997-11-10T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>4</EmployeeID>  
    <OrderDate>1998-02-12T00:00:00</OrderDate>  
  </Order>  
</Root>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Techniques de requêtes avancées (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
