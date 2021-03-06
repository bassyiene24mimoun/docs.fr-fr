---
title: SQL Server Compact et LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: 74b8a7a6dfc9a4050dbba9a8c2f6969dba42656c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355784"
---
# <a name="sql-server-compact-and-linq-to-sql"></a>SQL Server Compact et LINQ to SQL
SQL Server Compact est la base de données par défaut installé avec Visual Studio. Pour plus d’informations, consultez [PAVE sur à l’aide de SQL Server Compact (Visual Studio)](http://msdn.microsoft.com/library/13320dd1-94e5-4077-bf76-8df253695ccc).  
  
 Cette rubrique décrit les principales différences dans l’utilisation, la configuration, ensembles de fonctionnalités et étendue de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] prend en charge.  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a>Caractéristiques de SQL Server Compact par rapport à LINQ to SQL  
 Par défaut, SQL Server Compact est installé pour toutes les éditions de Visual Studio et est par conséquent disponible sur l’ordinateur de développement pour une utilisation avec [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Mais le déploiement d’une application qui utilise SQL Server Compact et [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] diffère de celle pour une application SQL Server. SQL Server Compact ne fait pas partie du .NET Framework et doit par conséquent être fourni avec l'application ou téléchargé séparément depuis le site Microsoft.  
  
 Notez les caractéristiques suivantes :  
  
-   SQL Server Compact est fourni comme une DLL qui peut être utilisée directement sur les fichiers de base de données (extension .sdf).  
  
-   SQL Server Compact s’exécute dans le même processus que l’application cliente. L’efficacité de la communication avec SQL Server Compact peut par conséquent être beaucoup plus importante que la communication avec SQL Server. En revanche, SQL Server Compact requiert l’interopérabilité entre le code managé et avec ses coûts connexes.  
  
-   La taille de la DLL SQL Server Compact est faible. Cette fonctionnalité réduit la taille globale de l’application.  
  
-   Le runtime de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] et l'outil en ligne de commande SQLMetal prennent en charge SQL Server Compact.  
  
-   [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] ne prend pas en charge SQL Server Compact.  
  
## <a name="feature-set"></a>Jeu de fonctionnalités  
 L’ensemble de fonctionnalités SQL Server Compact est beaucoup plus simple que l’ensemble des fonctionnalités de SQL Server dans les domaines suivants peuvent affecter [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications :  
  
-   SQL Server Compact ne prend pas en charge de procédures stockées ou de vues.  
  
-   SQL Server Compact prend en charge uniquement un sous-ensemble de types de données et de fonctions SQL.  
  
-   SQL Server Compact prend en charge uniquement un sous-ensemble de constructions SQL.  
  
-   SQL Server Compact fournit uniquement un optimiseur minimal. Il est possible que certaines requêtes peuvent expirer.  
  
-   SQL Server Compact ne prend pas en charge la confiance partielle.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
