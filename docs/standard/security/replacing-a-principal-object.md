---
title: Remplacement d'un objet Principal
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- principal objects, replacing
- security [.NET Framework], replacing principal objects
- security [.NET Framework], principals
ms.assetid: c323687e-b196-487b-beba-f38f9b3f961b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 94391471fecd92aeadec4da39cdd5b6f80bb6949
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581162"
---
# <a name="replacing-a-principal-object"></a>Remplacement d'un objet Principal
Les applications qui fournissent des services d’authentification doivent pouvoir remplacer l’objet **Principal** (<xref:System.Security.Principal.IPrincipal>) d’un thread donné. En outre, le système de sécurité doit permettre de protéger la possibilité de remplacer les objets **Principal** si un **Principal** malveillant et incorrect attaché compromet la sécurité de votre application en simulant une fausse identité ou un faux rôle. Par conséquent, les applications qui requièrent la possibilité de remplacer **Principal** objets doivent être accordées les <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> objet pour le contrôle de l’entité. (Notez que cette autorisation n’est pas obligatoire pour effectuer des vérifications de sécurité basée sur les rôles ou créer des objets **Principal** .)  
  
 L’objet **Principal** actuel peut être remplacé en effectuant les tâches suivantes :  
  
1.  Créer l’objet **Principal** de remplacement et l’objet **Identity** associé.  
  
2.  Attacher le nouvel objet **Principal** au contexte d’appel.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment créer un objet principal générique et l’utiliser pour définir le principal d’un thread.  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>  
 [Objets Principal et Identity](../../../docs/standard/security/principal-and-identity-objects.md)
