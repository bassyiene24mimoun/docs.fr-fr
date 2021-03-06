---
title: Regroupement de connexions SQL Server (ADO.NET)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e51d44e-7c4e-4040-9332-f0190fe36f07
ms.openlocfilehash: 79749f5e593fbf4ea282cc5c8000be88098b702f
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874593"
---
# <a name="sql-server-connection-pooling-adonet"></a>Regroupement de connexions SQL Server (ADO.NET)
La connexion à un serveur de base de données consiste généralement en plusieurs étapes de longue durée. Un canal physique tel qu'un socket ou un canal nommé doit être établi, le contrôle initial avec le serveur doit avoir lieu, les informations de chaîne de connexion doivent être analysées, la connexion doit être authentifiée par le serveur, des contrôles doivent être effectués pour l'inscription dans la transaction en cours, etc.  
  
 Dans la pratique, la plupart des applications utilisent une seule des quelques configurations pour les connexions. Cela signifie que, durant l'exécution de l'application, de nombreuses connexions identiques seront ouvertes et fermées à plusieurs reprises. Pour réduire le coût de l’ouverture de connexions, [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] utilise une technique d’optimisation nommée *le regroupement de connexions*.  
  
 Le regroupement de connexions réduit le nombre de fois où il est nécessaire d'ouvrir de nouvelles connexions. Le *pooler* conserve la propriété de la connexion physique. Elle gère les connexions en conservant en vie un ensemble de connexions actives pour chaque configuration de connexion donnée. Chaque fois qu'un utilisateur appelle `Open` sur une connexion, le dispositif de regroupement de connexions recherche une connexion disponible dans le pool. Si une connexion regroupée est disponible, le dispositif de regroupement de connexions la retourne à l'appelant au lieu d'ouvrir une nouvelle connexion. Lorsque l'application appelle `Close` sur la connexion, le dispositif de regroupement de connexions la retourne à l'ensemble regroupé de connexions actives au lieu de la fermer. Une fois la connexion retournée au pool, elle est prête à être réutilisée sur l'appel de `Open` suivant.  
  
 Seules les connexions utilisant la même configuration peuvent être groupées par pools. [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] garde en même temps plusieurs pools, un pour chaque configuration. Les connexions sont séparées en pools par chaîne de connexion, ainsi que par identité Windows en cas d'utilisation de la sécurité intégrée. Les connexions sont également regroupées selon si elles sont inscrites dans une transaction. Lorsque vous utilisez <xref:System.Data.SqlClient.SqlConnection.ChangePassword%2A>, l'instance <xref:System.Data.SqlClient.SqlCredential> affecte le pool de connexions. Les différentes instances de <xref:System.Data.SqlClient.SqlCredential> utilisent différents pool de connexions, même si l'ID d'utilisateur et le mot de passe sont identiques.  
  
 Le regroupement de connexions peut considérablement améliorer les performances et l'évolutivité de votre application. Le regroupement de connexions est activé par défaut dans [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]. À moins que vous ne le désactiviez explicitement, le dispositif de regroupement de connexions optimise les connexions au fur et à mesure de leur ouverture et de leur fermeture dans votre application. Vous pouvez également fournir plusieurs modificateurs de chaîne de connexion pour contrôler le comportement de regroupement de connexions. Pour plus d'informations, voir la section sur le contrôle des pools de connexions avec les mots clés des chaînes de connexion, plus loin dans cette rubrique.  
  
> [!NOTE]
>  Lorsque le regroupement de connexions est activé, et si une erreur de délai d'attente ou toute autre erreur de connexion se produit, une exception est levée et les tentatives de connexion suivantes échouent pendant les cinq secondes suivantes, « la période de blocage ». Si l'application essaie de se connecter au cours de la période de blocage, la première exception sera levée de nouveau. Les échecs suivants à l'issue d'une période de blocage entraînent de nouvelles périodes de blocage deux fois plus longues que la période de blocage précédente, d'une durée maximale d'une minute.  
  
## <a name="pool-creation-and-assignment"></a>Création et assignation d'un pool  
 Lorsqu'une connexion est ouverte pour la première fois, un pool de connexions est créé sur la base d'un algorithme à correspondance exacte qui associe le pool à la chaîne de connexion dans la connexion. Chaque pool de connexions est associé à une chaîne de connexion distincte. Lorsqu'une nouvelle connexion est ouverte, si la chaîne de connexion ne correspond pas exactement à un pool existant, un nouveau pool est créé. Les connexions sont regroupées par processus, par domaine d'application, par chaîne de connexion et, en cas d'utilisation de la sécurité intégrée, par identité Windows. Les chaînes de connexion doivent également parfaitement correspondre ; les mots clés fournis dans un ordre différent pour la même connexion sont regroupés séparément.  
  
 Dans l'exemple C# suivant, trois nouveaux objets <xref:System.Data.SqlClient.SqlConnection> sont créés mais seuls deux pools sont nécessaires pour les gérer. Notez que les première et deuxième chaînes de connexion diffèrent par la valeur assignée pour `Initial Catalog`.  
  
```  
using (SqlConnection connection = new SqlConnection(  
  "Integrated Security=SSPI;Initial Catalog=Northwind"))  
    {  
        connection.Open();        
        // Pool A is created.  
    }  
  
using (SqlConnection connection = new SqlConnection(  
  "Integrated Security=SSPI;Initial Catalog=pubs"))  
    {  
        connection.Open();        
        // Pool B is created because the connection strings differ.  
    }  
  
using (SqlConnection connection = new SqlConnection(  
  "Integrated Security=SSPI;Initial Catalog=Northwind"))  
    {  
        connection.Open();        
        // The connection string matches pool A.  
    }  
```  
  
 Si `MinPoolSize` n'est pas spécifié dans la chaîne de connexion ou est spécifié comme zéro, les connexions du pool sont fermées après une période d'inactivité. En revanche, si le `MinPoolSize` spécifié est supérieur à zéro, le pool de connexion n'est pas détruit tant que le `AppDomain` n'a pas été déchargé et que le processus ne s'est pas terminé. La maintenance des pools inactifs ou vides implique une charge mémoire minimale du système.  
  
> [!NOTE]
>  Le pool est automatiquement effacé si une erreur irrécupérable survient, telle qu'un basculement.  
  
## <a name="adding-connections"></a>Ajout de connexions  
 Un pool de connexions est créé pour chaque chaîne de connexion unique. Lorsqu'un pool est créé, plusieurs objets de connexion sont créés et ajoutés au pool de sorte que l'exigence de taille minimale du pool soit remplie. Les connexions sont ajoutées au pool jusqu'à ce que sa taille maximale spécifiée soit atteinte (la valeur par défaut est 100). Les connexions sont libérées et retournées au pool en cas de fermeture ou de suppression.  
  
 Quand un objet <xref:System.Data.SqlClient.SqlConnection> est demandé, il est obtenu du pool si une connexion utilisable est disponible. Pour être utilisable, la connexion ne doit pas être en cours d'utilisation, doit avoir un contexte de transaction correspondant ou ne pas être associée à un contexte de transaction et doit avoir un lien valide vers le serveur.  
  
 Le dispositif de regroupement de connexions répond à ces requêtes de connexion en réallouant les connexions à mesure qu'elles se libèrent dans le pool. Si la taille maximale du pool est atteinte et qu'aucune connexion utilisable n'est disponible, la requête est mise en attente. Le dispositif de regroupement de connexions tente ensuite de récupérer des connexions jusqu'à ce que le délai de temporisation ait expiré (la valeur par défaut est de 15 secondes). Si le dispositif de regroupement de connexions ne peut pas répondre à la requête avant que le délai de temporisation de la connexion ait expiré, une exception est levée.  
  
> [!CAUTION]
>  Il est vivement recommandé de toujours fermer la connexion lorsque vous avez terminé de l'utiliser, de sorte qu'elle soit retournée au pool. Vous pouvez le faire à l’aide la `Close` ou `Dispose` méthodes de la `Connection` de l’objet, ou en ouvrant toutes les connexions à l’intérieur d’un `using` instruction en langage c#, ou un `Using` instruction en Visual Basic. Les connexions qui ne sont pas explicitement fermées risquent de ne pas être ajoutées ni retournées au pool. Pour plus d’informations, consultez [à l’aide d’instruction](~/docs/csharp/language-reference/keywords/using-statement.md) ou [Comment : supprimer une ressource système](~/docs/visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md) pour Visual Basic.  
  
> [!NOTE]
>  N'appelez pas une commande `Close` ou `Dispose` sur une `Connection`, un `DataReader` ou tout autre objet managé dans la méthode `Finalize` de votre classe. Dans un finaliseur, libérez seulement les ressources non managées que votre classe possède directement. Si votre classe ne possède pas de ressource non managée, n'incluez pas une méthode `Finalize` dans la définition de classe. Pour plus d’informations, consultez [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).  
  
Pour plus d’informations sur les événements liés à l’ouverture et fermeture des connexions, consultez [classe d’événements Audit Login](/sql/relational-databases/event-classes/audit-login-event-class) et [classe d’événements Audit Logout](/sql/relational-databases/event-classes/audit-logout-event-class) dans la documentation de SQL Server.  
  
## <a name="removing-connections"></a>Suppression de connexions  
 Le dispositif de regroupement de connexions supprime une connexion du pool restée inactive pendant environ 4 à 8 minutes ou s'il détecte que la connexion au serveur a été interrompue. Notez qu'une connexion interrompue ne peut être détectée qu'après une tentative de communication avec le serveur. Si une connexion n'est plus reliée au serveur, elle est marquée comme étant non valide. Les connexions non valides ne sont supprimées du pool de connexions que lorsqu'elles sont fermées ou récupérées.  
  
 Si une connexion existante à un serveur a disparu, il est possible de la retirer du pool même si le dispositif de regroupement de connexions n'a pas détecté d'interruption de la connexion et ne l'a pas marquée comme non valide. C'est le cas parce que la charge de vérifier que la connexion est encore valide éliminerait les avantages liés au fait de disposer d'une fonction de regroupement de connexions en entraînant un aller-retour supplémentaire vers le serveur. Lorsque cela se produit, la première tentative d'utilisation de la connexion détecte que la connexion a été interrompue et une exception est levée.  
  
## <a name="clearing-the-pool"></a>Effacement du pool  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0 introduit deux nouvelles méthodes pour effacer un pool : <xref:System.Data.SqlClient.SqlConnection.ClearAllPools%2A> et <xref:System.Data.SqlClient.SqlConnection.ClearPool%2A>. `ClearAllPools` efface les pools de connexions pour un fournisseur donné et `ClearPool` efface le pool de connexions associé à une connexion spécifique. Si des connexions sont utilisées au moment de l'appel, elles sont marquées de façon appropriée. Lors de leur fermeture, elles sont écartées au lieu d'être retournées au pool.  
  
## <a name="transaction-support"></a>Prise en charge des transactions  
 Les connexions sont retirées du pool et assignées en fonction du contexte de transaction. À moins que `Enlist=false` ne soit spécifié dans la chaîne de connexion, le pool de connexions s'assure que la connexion est inscrite dans le contexte <xref:System.Transactions.Transaction.Current%2A>. Lorsqu'une connexion est fermée et retournée au pool avec une transaction `System.Transactions` inscrite, elle est mise de côté de sorte que la demande suivante de ce pool de connexions avec la même transaction `System.Transactions` retourne la même connexion, si elle est disponible. Si une telle demande est émise et qu'aucune connexion regroupée n'est disponible, une connexion est retirée de la partie non traitée du pool et est inscrite. Si aucune connexion n'est disponible où que ce soit dans le pool, une nouvelle connexion est créée et inscrite.  
  
 Lorsqu'une connexion est fermée, elle est libérée à nouveau vers le pool et dans la sous-division appropriée en fonction de son contexte de transaction. Par conséquent, vous pouvez fermer la connexion sans générer d'erreur, même si une transaction distribuée est toujours en attente. Cela vous permet de valider ou d'abandonner ultérieurement la transaction distribuée.  
  
## <a name="controlling-connection-pooling-with-connection-string-keywords"></a>Contrôle des pools de connexions avec les mots clés des chaînes de connexion  
 La propriété `ConnectionString` de l'objet <xref:System.Data.SqlClient.SqlConnection> prend en charge les paires clé-valeur des chaînes de connexion qui peuvent être utilisées pour ajuster le comportement de la logique de regroupement des connexions. Pour plus d'informations, consultez <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
## <a name="pool-fragmentation"></a>Fragmentation de pool  
 La fragmentation de pool est un problème courant dans de nombreuses applications Web où l'application peut créer un grand nombre de pools qui ne sont pas libérés tant que le processus n'est pas terminé. Cela laisse un grand nombre de connexions ouvertes qui consomment de la mémoire et altèrent les performances.  
  
### <a name="pool-fragmentation-due-to-integrated-security"></a>Fragmentation de pool due à une sécurité intégrée  
 Les connexions sont regroupées en fonction de la chaîne de connexion et de l'identité de l'utilisateur. C'est pourquoi, si vous utilisez une authentification de base ou une authentification Windows sur le site Web ainsi qu'une connexion sécurisée intégrée, vous obtenez un pool par utilisateur. Bien que cela améliore les performances des requêtes de base de données suivantes pour un utilisateur donné, ce dernier ne peut pas tirer parti des connexions établies par d'autres utilisateurs. Cela génère également au moins une connexion au serveur de base de données par utilisateur. Il s'agit d'un effet secondaire d'une architecture d'application Web particulière que les développeurs doivent soupeser par rapport aux exigences de sécurité et d'audit.  
  
### <a name="pool-fragmentation-due-to-many-databases"></a>Fragmentation de pool due à un trop grand nombre de base de données  
 De nombreux fournisseurs de services Internet hébergent plusieurs sites Web sur un seul serveur. Ils peuvent utiliser une seule base de données pour confirmer une connexion d'authentification Forms, puis ouvrir une connexion à une base de données spécifique pour cet utilisateur ou ce groupe d'utilisateurs. La connexion à la base de données d'authentification est regroupée et utilisée par tout le monde. Toutefois, il existe un pool de connexions distinct à chaque base de données, ce qui augmente le nombre de connexions au serveur.  
  
 Cela est également un effet secondaire de la conception de l'application. Il existe une méthode relativement simple pour éviter cet effet secondaire sans compromettre la sécurité lors de la connexion à SQL Server. Au lieu d'établir une connexion à une base de données distincte pour chaque utilisateur ou groupe d'utilisateurs, établissez une connexion à la même base de données sur le serveur, puis exécutez l'instruction [!INCLUDE[tsql](../../../../includes/tsql-md.md)] USE pour accéder à la base de données souhaitée. Le fragment de code suivant montre comment créer une connexion initiale à la base de données `master`, puis basculer vers la base de données souhaitée spécifiée dans la variable chaîne `databaseName`.  
  
```vb  
' Assumes that command is a valid SqlCommand object and that  
' connectionString connects to master.  
    command.Text = "USE DatabaseName"  
Using connection As New SqlConnection(connectionString)  
    connection.Open()  
    command.ExecuteNonQuery()  
End Using  
```  
  
```csharp  
// Assumes that command is a SqlCommand object and that  
// connectionString connects to master.  
command.Text = "USE DatabaseName";  
using (SqlConnection connection = new SqlConnection(  
  connectionString))  
  {  
    connection.Open();  
    command.ExecuteNonQuery();  
  }  
```  
  
## <a name="application-roles-and-connection-pooling"></a>Rôles d'application et regroupement de connexions  
 Après qu'un rôle d'application SQL Server a été activé en appelant la procédure stockée système `sp_setapprole`, le contexte de sécurité de cette connexion ne peut pas être rétabli. Toutefois, lorsque le regroupement est activé, la connexion est retournée au pool et une erreur se produit en cas de réutilisation de la connexion regroupée. Pour plus d’informations, consultez l’article de la Base de connaissances, «[erreurs du rôle d’application SQL avec OLE DB resource pooling](http://support.microsoft.com/default.aspx?scid=KB;EN-US;Q229564). »  
  
### <a name="application-role-alternatives"></a>Alternatives aux rôles d'application  
 Il est recommandé de tirer parti des mécanismes de sécurité qui peuvent être employés à la place des rôles d'application. Pour plus d’informations, consultez [création de rôles d’Application dans SQL Server](../../../../docs/framework/data/adonet/sql/creating-application-roles-in-sql-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Regroupement de connexions](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [SQL Server et ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)  
 [Compteurs de performance](../../../../docs/framework/data/adonet/performance-counters.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
