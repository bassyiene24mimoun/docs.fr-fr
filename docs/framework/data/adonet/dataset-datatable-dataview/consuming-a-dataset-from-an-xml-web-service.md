---
title: Consommation d’un DataSet à partir d’un service web XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: da3eca875df9b80f66241a2ecb72c5ba5c1df309
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758839"
---
# <a name="consuming-a-dataset-from-an-xml-web-service"></a>Consommation d’un DataSet à partir d’un service web XML
L'objet <xref:System.Data.DataSet> a été conçu avec une architecture déconnectée, en partie afin de faciliter le transport des données sur Internet. Le **DataSet** est « sérialisable » dans la mesure où il peut être spécifié en tant qu’entrée ou sortie de services Web XML sans aucun codage supplémentaire nécessaire pour transmettre le contenu de la **DataSet** à partir d’un service Web XML pour un client et l’arrière. Le **DataSet** est implicitement converti en flux XML à l’aide du format DiffGram, envoyé sur le réseau, puis reconstruit à partir du flux XML en tant qu’un **DataSet** sur l’extrémité de réception. Vous disposez ainsi d’une méthode alliant simplicité et souplesse pour la transmission et le retour de données relationnelles à l’aide des services web XML. Pour plus d’informations sur le format DiffGram, consultez [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).  
  
 L’exemple suivant montre comment créer un service Web XML et les clients qui utilisent la **DataSet** pour transporter des données relationnelles (notamment des données modifiées) et pour répercuter les mises à jour dans la source de données d’origine.  
  
> [!NOTE]
>  Nous recommandons de toujours tenir compte des impératifs de sécurité lorsque vous créez un service web XML. Pour plus d’informations sur la sécurisation d’un service Web XML, consultez [sécurisation des Services Web XML créés à l’aide d’ASP.NET](https://msdn.microsoft.com/library/354b2ab1-2782-4542-b32a-dc560178b90c).  
  
### <a name="to-create-an-xml-web-service-that-returns-and-consumes-a-dataset"></a>Pour créer un service web XML qui retourne et utilise un DataSet  
  
1.  Créez le service web XML.  
  
     Dans l’exemple, un service Web XML est créé qui retourne des données, dans ce cas, une liste de clients à partir de la **Northwind** de base de données et reçoit un **DataSet** avec les mises à jour les données, qui le service Web XML correspond à la source de données d’origine.  
  
     Le service Web XML expose deux méthodes : **GetCustomers**, pour retourner la liste des clients, et **UpdateCustomers**, pour répercuter les mises à jour dans la source de données. Le service Web XML est stocké sur le serveur web dans le fichier DataSetSample.asmx. Le code suivant représente le contenu de ce fichier.  
  
    ```vb  
    <% @ WebService Language = "vb" Class = "Sample" %>  
    Imports System  
    Imports System.Data  
    Imports System.Data.SqlClient  
    Imports System.Web.Services  
  
    <WebService(Namespace:="http://microsoft.com/webservices/")> _  
    Public Class Sample  
  
    Public connection As SqlConnection = New SqlConnection("Data Source=(local);Integrated Security=SSPI;Initial Catalog=Northwind")  
  
      <WebMethod( Description := "Returns Northwind Customers", EnableSession := False )> _  
      Public Function GetCustomers() As DataSet  
        Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
          "SELECT CustomerID, CompanyName FROM Customers", connection)  
  
        Dim custDS As DataSet = New DataSet()  
        adapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
        adapter.Fill(custDS, "Customers")  
  
        Return custDS  
      End Function  
  
      <WebMethod( Description := "Updates Northwind Customers", EnableSession := False )> _  
      Public Function UpdateCustomers(custDS As DataSet) As DataSet  
        Dim adapter As SqlDataAdapter = New SqlDataAdapter()  
  
        adapter.InsertCommand = New SqlCommand( _  
          "INSERT INTO Customers (CustomerID, CompanyName) " & _  
          "Values(@CustomerID, @CompanyName)", connection)  
        adapter.InsertCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        adapter.InsertCommand.Parameters.Add( _  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
  
        adapter.UpdateCommand = New SqlCommand( _  
          "UPDATE Customers Set CustomerID = @CustomerID, " & _  
          "CompanyName = @CompanyName WHERE CustomerID = " & _  
          @OldCustomerID", connection)  
        adapter.UpdateCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        adapter.UpdateCommand.Parameters.Add( _  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
  
        Dim parameter As SqlParameter = _  
          adapter.UpdateCommand.Parameters.Add( _  
          "@OldCustomerID", SqlDbType.NChar, 5, "CustomerID")  
        parameter.SourceVersion = DataRowVersion.Original  
  
        adapter.DeleteCommand = New SqlCommand( _  
          "DELETE FROM Customers WHERE CustomerID = @CustomerID", _  
          connection)  
        parameter = adapter.DeleteCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        parameter.SourceVersion = DataRowVersion.Original  
  
        adapter.Update(custDS, "Customers")  
  
        Return custDS  
      End Function  
    End Class  
    ```  
  
    ```csharp  
    <% @ WebService Language = "C#" Class = "Sample" %>  
    using System;  
    using System.Data;  
    using System.Data.SqlClient;  
    using System.Web.Services;  
  
    [WebService(Namespace="http://microsoft.com/webservices/")]  
    public class Sample  
    {  
      public SqlConnection connection = new SqlConnection("Data Source=(local);Integrated Security=SSPI;Initial Catalog=Northwind");  
  
      [WebMethod( Description = "Returns Northwind Customers", EnableSession = false )]  
      public DataSet GetCustomers()  
      {  
        SqlDataAdapter adapter = new SqlDataAdapter(  
          "SELECT CustomerID, CompanyName FROM Customers", connection);  
  
        DataSet custDS = new DataSet();  
        adapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
        adapter.Fill(custDS, "Customers");  
  
        return custDS;  
      }  
  
      [WebMethod( Description = "Updates Northwind Customers",  
        EnableSession = false )]  
      public DataSet UpdateCustomers(DataSet custDS)  
      {  
        SqlDataAdapter adapter = new SqlDataAdapter();  
  
        adapter.InsertCommand = new SqlCommand(  
          "INSERT INTO Customers (CustomerID, CompanyName) " +  
          "Values(@CustomerID, @CompanyName)", connection);  
        adapter.InsertCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        adapter.InsertCommand.Parameters.Add(  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName");  
  
        adapter.UpdateCommand = new SqlCommand(  
          "UPDATE Customers Set CustomerID = @CustomerID, " +  
          "CompanyName = @CompanyName WHERE CustomerID = " +  
          "@OldCustomerID", connection);  
        adapter.UpdateCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        adapter.UpdateCommand.Parameters.Add(  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName");  
        SqlParameter parameter = adapter.UpdateCommand.Parameters.Add(  
          "@OldCustomerID", SqlDbType.NChar, 5, "CustomerID");  
        parameter.SourceVersion = DataRowVersion.Original;  
  
        adapter.DeleteCommand = new SqlCommand(  
        "DELETE FROM Customers WHERE CustomerID = @CustomerID",  
         connection);  
        parameter = adapter.DeleteCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        parameter.SourceVersion = DataRowVersion.Original;  
  
        adapter.Update(custDS, "Customers");  
  
        return custDS;  
      }  
    }  
    ```  
  
     Dans un scénario classique, le **UpdateCustomers** méthode serait écrite pour intercepter les violations d’accès concurrentiel optimiste. Par souci de simplicité, cet exemple ne le fait pas. Pour plus d’informations sur l’accès concurrentiel optimiste, consultez [d’accès concurrentiel optimiste](../../../../../docs/framework/data/adonet/optimistic-concurrency.md).  
  
2.  Créez un proxy de service web XML.  
  
     Les clients du service Web XML ont besoin d'un proxy SOAP pour pouvoir utiliser les méthodes exposées. Vous pouvez faire en sorte que Visual Studio génère ce proxy pour vous. En définissant une référence Web à un service Web existant depuis Visual Studio, tout le comportement décrit dans cette étape se passe de façon transparente. Si vous souhaitez créer la classe proxy vous-même, passez à cette description. Le plus souvent, cependant, l'utilisation de Visual Studio pour créer la classe proxy pour l'application cliente suffit.  
  
     Un proxy peut être créé à l'aide de l'outil Web Services Description Language Tool. Par exemple, si le service Web XML est exposé à l’URL http://myserver/data/DataSetSample.asmx, émettre une commande telle que la suivante pour créer un proxy Visual Basic .NET avec un espace de noms **WebData.DSSample** et stockez-le dans le fichier sample.vb.  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     Pour créer un proxy C# dans le fichier sample.cs, écrivez la commande suivante.  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     Le proxy peut ensuite être compilé en tant que bibliothèque et importé dans le client du service Web XML. Pour compiler le code Visual Basic .NET du proxy stocké dans sample.vb en tant que sample.dll, écrivez la commande suivante.  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     Pour compiler le code C# du proxy stocké dans sample.cs en tant que sample.dll, écrivez la commande suivante.  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3.  Créez un client de service web XML.  
  
     Si vous souhaitez que Visual Studio génère la classe proxy du service Web pour vous, simplement créer le projet client et, dans la fenêtre Explorateur de solutions, cliquez sur le projet, cliquez sur **ajouter une référence Web**, puis sélectionnez le service Web à partir de la liste des services Web disponibles (Cela peut nécessiter en fournissant l’adresse du point de terminaison de service Web, si le service Web n’est pas disponible dans la solution actuelle ou sur l’ordinateur actuel.) Si vous créez le proxy de service web XML vous-même (comme décrit à l’étape précédente), vous pouvez l’importer dans votre code client et utiliser les méthodes de service web XML. L’exemple de code suivant importe la bibliothèque du proxy, appelle **GetCustomers** pour obtenir une liste de clients, ajoute un nouveau client, puis retourne un **DataSet** avec les mises à jour **UpdateCustomers** .  
  
     Notez que l’exemple passe le **DataSet** retourné par **DataSet.GetChanges** à **UpdateCustomers** , car seules les lignes modifiées doivent être passés à  **UpdateCustomers**. **UpdateCustomers** retourne le résolu **DataSet**, que vous pouvez ensuite **fusion** dans existants **DataSet** à intégrer les modifications résolues et toute informations d’erreur de ligne à partir de la mise à jour. Le code suivant suppose que vous avez utilisé Visual Studio pour créer la référence Web, et que vous avez renommé la référence Web en DsSample dans les **ajouter une référence Web** boîte de dialogue.  
  
    ```vb  
    Imports System  
    Imports System.Data  
  
    Public Class Client  
  
      Public Shared Sub Main()  
        Dim proxySample As New DsSample.Sample ()  ' Proxy object.  
        Dim customersDataSet As DataSet = proxySample.GetCustomers()  
        Dim customersTable As DataTable = _  
          customersDataSet.Tables("Customers")  
  
        Dim rowAs DataRow = customersTable.NewRow()  
        row("CustomerID") = "ABCDE"  
        row("CompanyName") = "New Company Name"  
        customersTable.Rows.Add(row)  
  
        Dim updateDataSet As DataSet = _  
          proxySample.UpdateCustomers(customersDataSet.GetChanges())  
  
        customersDataSet.Merge(updateDataSet)  
        customersDataSet.AcceptChanges()  
      End Sub  
    End Class  
    ```  
  
    ```csharp  
    using System;  
    using System.Data;  
  
    public class Client  
    {  
      public static void Main()  
      {  
        Sample proxySample = new DsSample.Sample();  // Proxy object.  
        DataSet customersDataSet = proxySample.GetCustomers();  
        DataTable customersTable = customersDataSet.Tables["Customers"];  
  
        DataRow row = customersTable.NewRow();  
        row["CustomerID"] = "ABCDE";  
        row["CompanyName"] = "New Company Name";  
        customersTable.Rows.Add(row);  
  
        DataSet updateDataSet = new DataSet();  
  
        updateDataSet =   
          proxySample.UpdateCustomers(customersDataSet.GetChanges());  
  
        customersDataSet.Merge(updateDataSet);  
        customersDataSet.AcceptChanges();  
      }  
    }  
    ```  
  
     Si vous décidez de créer la classe proxy vous-même, vous devez prendre les mesures supplémentaires suivantes. Pour compiler l'exemple, fournissez la bibliothèque de proxy qui a été créée (sample.dll) ainsi que les bibliothèques .NET connexes. Pour compiler la version Visual Basic .NET de l'exemple, stockée dans le fichier client.vb, écrivez la commande suivante.  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     Pour compiler la version C# de l'exemple, stockée dans le fichier client.cs, écrivez la commande suivante.  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 [DataSets, DataTables et DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [Remplissage d’un DataSet à partir d’un DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [Mise à jour de sources de données avec des DataAdapters](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [Paramètres DataAdapter](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 [Web Services Description Language Tool (Wsdl.exe)](https://msdn.microsoft.com/library/b9210348-8bc2-4367-8c91-d1a04b403e88)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
