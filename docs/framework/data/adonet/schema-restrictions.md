---
title: Restrictions de schéma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: c62f934561fa4a6c352ff84b8c1201461c42de39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357255"
---
# <a name="schema-restrictions"></a>Restrictions de schéma
Le deuxième paramètre facultatif de la **GetSchema** méthode est retournée par les restrictions qui sont utilisées pour limiter la quantité d’informations de schéma, et il est passé à la **GetSchema** sous forme de tableau de chaînes (méthode) . La position dans le tableau détermine les valeurs que vous pouvez passer et équivaut au numéro de restriction.  
  
 Par exemple, le tableau suivant décrit les restrictions prises en charge par la collection de schémas « Tables » utilisant le fournisseur de données .NET Framework pour SQL Server. Des restrictions supplémentaires pour les collections de schémas SQL Server figurent à la fin de cette rubrique.  
  
|Nom de restriction|Nom du paramètre|Valeur par défaut de la restriction|Numéro de restriction|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalogue|@Catalog|TABLE_CATALOG|1|  
|Propriétaire|@Owner|TABLE_SCHEMA|2|  
|Table|@Name|TABLE_NAME|3|  
|TableType|@TableType|TABLE_TYPE|4|  
  
## <a name="specifying-restriction-values"></a>Spécification des valeurs de restriction  
 Pour utiliser l’une des restrictions de la collection de schémas « Tables », créez simplement un tableau de chaînes contenant quatre éléments, puis placez une valeur dans l’élément correspondant au numéro de restriction. Par exemple, pour restreindre les tables retournées par la **GetSchema** méthode exclusivement aux tables dans le schéma « Sales », définissez le deuxième élément du tableau sur « Sales » avant de le transmettre à la **GetSchema** (méthode).  
  
> [!NOTE]
>  Les collections de restrictions pour `SqlClient` et `OracleClient` comportent une colonne `ParameterName` supplémentaire. La colonne par défaut de la restriction est encore là pour la compatibilité ascendante, mais est désormais ignorée. Il convient d'utiliser des requêtes paramétrées plutôt qu'un remplacement de chaîne afin de minimiser le risque d'attaque par injection SQL lors de la spécification de valeurs de restriction.  
  
> [!NOTE]
>  Le nombre d'éléments du tableau doit être inférieur ou égal au nombre de restrictions prises en charge pour la collection de schémas spécifiée, sans quoi une exception <xref:System.ArgumentException> est levée. Il peut y avoir moins de restrictions que le nombre maximal de restrictions. Les restrictions manquantes sont supposées avoir la valeur null (aucune restriction).  
  
 Vous pouvez interroger un fournisseur .NET Framework managé afin de déterminer la liste des restrictions prises en charge en appelant le **GetSchema** méthode portant le nom de la collection de schémas de restrictions, « restrictions ». Cette opération retourne un <xref:System.Data.DataTable> contenant une liste des noms de collections, des noms de restriction, des valeurs de restriction par défaut et des numéros de restriction.  
  
### <a name="example"></a>Exemple  
 Les exemples suivants montrent comment utiliser le <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> méthode du fournisseur de données .NET Framework pour SQL Server <xref:System.Data.SqlClient.SqlConnection> classe pour récupérer les informations de schéma sur toutes les tables contenues dans le **AdventureWorks**exemple de base de données et de restreindre les informations retournées exclusivement aux tables dans le schéma « Sales » :  
  
```vb  
Imports System.Data.SqlClient  
  
Module Module1  
Sub Main()  
  Dim connectionString As String = _  
    "Data Source=(local);Database=AdventureWorks;" & _  
       "Integrated Security=true;";  
  
  Dim restrictions(3) As String  
  Using connection As New SqlConnection(connectionString)  
    connection.Open()  
  
    'Specify the restrictions.  
    restrictions(1) = "Sales"  
    Dim table As DataTable = connection.GetSchema("Tables", _  
       restrictions)  
  
    ' Display the contents of the table.  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Using  
End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Program  
{  
  static void Main()  
  {  
    string connectionString =   
       "Data Source=(local);Database=AdventureWorks;" +  
       "Integrated Security=true;";  
    using (SqlConnection connection =  
       new SqlConnection(connectionString))  
    {  
        connection.Open();  
  
        // Specify the restrictions.  
        string[] restrictions = new string[4];  
        restrictions[1] = "Sales";  
        System.Data.DataTable table = connection.GetSchema(  
          "Tables", restrictions);  
  
        // Display the contents of the table.  
        foreach (System.Data.DataRow row in table.Rows)  
        {  
            foreach (System.Data.DataColumn col in table.Columns)  
            {  
                Console.WriteLine("{0} = {1}",   
                  col.ColumnName, row[col]);  
            }  
            Console.WriteLine("============================");  
        }  
        Console.WriteLine("Press any key to continue.");  
        Console.ReadKey();  
    }  
  }  
  
  private static string GetConnectionString()  
  {  
     // To avoid storing the connection string in your code,  
     // you can retrieve it from a configuration file.  
     return "Data Source=(local);Database=AdventureWorks;" +  
        "Integrated Security=true;";  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
     foreach (System.Data.DataRow row in table.Rows)  
     {  
        foreach (System.Data.DataColumn col in table.Columns)  
        {  
           Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
        }  
     Console.WriteLine("============================");  
     }  
  }  
}  
```  
  
## <a name="sql-server-schema-restrictions"></a>Restrictions de schéma SQL Server  
 Les tableaux suivants énumèrent les restrictions pour les collections de schémas SQL Server.  
  
### <a name="users"></a>Utilisateurs  
  
|Nom de restriction|Nom du paramètre|Valeur par défaut de la restriction|Numéro de restriction|  
|----------------------|--------------------|-------------------------|------------------------|  
|User_Name|@Name|name|1|  
  
### <a name="databases"></a>Bases de données  
  
|Nom de restriction|Nom du paramètre|Valeur par défaut de la restriction|Numéro de restriction|  
|----------------------|--------------------|-------------------------|------------------------|  
|Name|@Name|Name|1|  
  
### <a name="tables"></a>Tables  
  
|Nom de restriction|Nom du paramètre|Valeur par défaut de la restriction|Numéro de restriction|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalogue|@Catalog|TABLE_CATALOG|1|  
|Propriétaire|@Owner|TABLE_SCHEMA|2|  
|Table|@Name|TABLE_NAME|3|  
|TableType|@TableType|TABLE_TYPE|4|  
  
### <a name="columns"></a>Columns  
  
|Nom de restriction|Nom du paramètre|Valeur par défaut de la restriction|Numéro de restriction|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalogue|@Catalog|TABLE_CATALOG|1|  
|Propriétaire|@Owner|TABLE_SCHEMA|2|  
|Table|@Table|TABLE_NAME|3|  
|Colonne|@Column|COLUMN_NAME|4|  
  
### <a name="structuredtypemembers"></a>StructuredTypeMembers  
  
|Nom de restriction|Nom du paramètre|Valeur par défaut de la restriction|Numéro de restriction|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalogue|@Catalog|TABLE_CATALOG|1|  
|Propriétaire|@Owner|TABLE_SCHEMA|2|  
|Table|@Table|TABLE_NAME|3|  
|Colonne|@Column|COLUMN_NAME|4|  
  
### <a name="views"></a>Vues  
  
|Nom de restriction|Nom du paramètre|Valeur par défaut de la restriction|Numéro de restriction|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalogue|@Catalog|TABLE_CATALOG|1|  
|Propriétaire|@Owner|TABLE_SCHEMA|2|  
|Table|@Table|TABLE_NAME|3|  
  
### <a name="viewcolumns"></a>ViewColumns  
  
|Nom de restriction|Nom du paramètre|Valeur par défaut de la restriction|Numéro de restriction|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalogue|@Catalog|VIEW_CATALOG|1|  
|Propriétaire|@Owner|VIEW_SCHEMA|2|  
|Table|@Table|VIEW_NAME|3|  
|Colonne|@Column|COLUMN_NAME|4|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
|Nom de restriction|Nom du paramètre|Valeur par défaut de la restriction|Numéro de restriction|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalogue|@Catalog|SPECIFIC_CATALOG|1|  
|Propriétaire|@Owner|SPECIFIC_SCHEMA|2|  
|Name|@Name|SPECIFIC_NAME|3|  
|Paramètre|@Parameter|PARAMETER_NAME|4|  
  
### <a name="procedures"></a>Procédures  
  
|Nom de restriction|Nom du paramètre|Valeur par défaut de la restriction|Numéro de restriction|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalogue|@Catalog|SPECIFIC_CATALOG|1|  
|Propriétaire|@Owner|SPECIFIC_SCHEMA|2|  
|Name|@Name|SPECIFIC_NAME|3|  
|Type|@Type|ROUTINE_TYPE|4|  
  
### <a name="indexcolumns"></a>IndexColumns  
  
|Nom de restriction|Nom du paramètre|Valeur par défaut de la restriction|Numéro de restriction|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalogue|@Catalog|db_name()|1|  
|Propriétaire|@Owner|user_name()|2|  
|Table|@Table|o.name|3|  
|ConstraintName|@ConstraintName|x.name|4|  
|Colonne|@Column|c.name|5|  
  
### <a name="indexes"></a>Index  
  
|Nom de restriction|Nom du paramètre|Valeur par défaut de la restriction|Numéro de restriction|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalogue|@Catalog|db_name()|1|  
|Propriétaire|@Owner|user_name()|2|  
|Table|@Table|o.name|3|  
  
### <a name="userdefinedtypes"></a>UserDefinedTypes  
  
|Nom de restriction|Nom du paramètre|Valeur par défaut de la restriction|Numéro de restriction|  
|----------------------|--------------------|-------------------------|------------------------|  
|assembly_name|@AssemblyName|assemblies.name|1|  
|udt_name|@UDTName|types.assembly_class|2|  
  
### <a name="foreignkeys"></a>ForeignKeys  
  
|Nom de restriction|Nom du paramètre|Valeur par défaut de la restriction|Numéro de restriction|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalogue|@Catalog|CONSTRAINT_CATALOG|1|  
|Propriétaire|@Owner|CONSTRAINT_SCHEMA|2|  
|Table|@Table|TABLE_NAME|3|  
|Name|@Name|CONSTRAINT_NAME|4|  
  
## <a name="sql-server-2008-schema-restrictions"></a>Restrictions de schéma SQL Server 2008  
 Les tableaux suivants répertorient les restrictions pour les collections de schémas SQL Server 2008. Ces restrictions s'appliquent à partir de la version 3.5 SP1 de .NET Framework et SQL Server 2008. Elles ne sont pas prises en charge dans les versions précédentes de .NET Framework et SQL Server.  
  
### <a name="columnsetcolumns"></a>ColumnSetColumns  
  
|Nom de restriction|Nom du paramètre|Valeur par défaut de la restriction|Numéro de restriction|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalogue|@Catalog|TABLE_CATALOG|1|  
|Propriétaire|@Owner|TABLE_SCHEMA|2|  
|Table|@Table|TABLE_NAME|3|  
  
### <a name="allcolumns"></a>AllColumns  
  
|Nom de restriction|Nom du paramètre|Valeur par défaut de la restriction|Numéro de restriction|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalogue|@Catalog|TABLE_CATALOG|1|  
|Propriétaire|@Owner|TABLE_SCHEMA|2|  
|Table|@Table|TABLE_NAME|3|  
|Colonne|@Column|COLUMN_NAME|4|  
  
## <a name="see-also"></a>Voir aussi  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
