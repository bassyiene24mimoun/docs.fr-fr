---
title: 'Comment : créer des tâches précalculées'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, creating pre-computed
ms.assetid: a73eafa2-1f49-4106-a19e-997186029b58
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d5d688041c6a8947b4a30f067d969cb6cb3bbf0d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583901"
---
# <a name="how-to-create-pre-computed-tasks"></a>Comment : créer des tâches précalculées
Ce document décrit comment utiliser la méthode <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> pour récupérer les résultats d’opérations de téléchargement asynchrones qui sont conservées dans un cache. La méthode <xref:System.Threading.Tasks.Task.FromResult%2A> retourne un objet <xref:System.Threading.Tasks.Task%601> fini qui contient la valeur fournie en tant que sa propriété <xref:System.Threading.Tasks.Task%601.Result%2A>. Cette méthode est utile lorsque vous exécutez une opération asynchrone qui retourne un objet <xref:System.Threading.Tasks.Task%601>, et que le résultat de cet objet <xref:System.Threading.Tasks.Task%601> est déjà calculé.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant télécharge des chaînes à partir du web. Il définit la méthode `DownloadStringAsync`. Cette méthode télécharge des chaînes à partir du web de façon asynchrone. Cet exemple utilise également un objet <xref:System.Collections.Concurrent.ConcurrentDictionary%602> pour mettre en cache les résultats des opérations précédentes. Si l’adresse d’entrée est conservée dans ce cache, `DownloadStringAsync` utilise la méthode <xref:System.Threading.Tasks.Task.FromResult%2A> pour produire un objet <xref:System.Threading.Tasks.Task%601> qui contient le contenu à cette adresse. Dans le cas contraire, `DownloadStringAsync` télécharge le fichier à partir du web et ajoute le résultat dans le cache.  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 Cet exemple calcule le temps nécessaire pour télécharger plusieurs chaînes deux fois. Le deuxième ensemble d’opérations de téléchargement doit prendre moins de temps que le premier, car les résultats sont conservés dans le cache. La méthode <xref:System.Threading.Tasks.Task.FromResult%2A> permet à la méthode `DownloadStringAsync` de créer des objets <xref:System.Threading.Tasks.Task%601> qui contiennent ces résultats pré-calculés.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `CachedDownloads.cs` (`CachedDownloads.vb` pour Visual Basic), puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.  
  
 Visual C#  
  
 **csc.exe CachedDownloads.cs**  
  
 Visual Basic  
  
 **vbc.exe CachedDownloads.vb**  
  
## <a name="robust-programming"></a>Programmation fiable  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation asynchrone basée sur les tâches](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
