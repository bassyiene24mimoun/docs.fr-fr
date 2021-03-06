---
title: "Comment : supprimer des caractères non valides d'une chaîne"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, examples
- cleaning input
- user input, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- Regex.Replace method
- stripping invalid characters
- Replace method
- validating user input
ms.assetid: b4319c8a-9032-4129-a9d5-6f6fc28e7f32
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 66fe5dd1da148e8afd07ae69cec960438b53536a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567352"
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a>Comment : supprimer des caractères non valides d'une chaîne
L’exemple suivant utilise la méthode <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> statique pour supprimer des caractères non valides d’une chaîne.  
  
## <a name="example"></a>Exemple  
 Vous pouvez utiliser la méthode `CleanInput` définie dans cet exemple pour supprimer des caractères potentiellement nuisibles entrés dans un champ de texte qui accepte une entrée d’utilisateur. Dans ce cas, `CleanInput` supprime tous les caractères non alphanumériques à l’exception des points (.), des arrobases (@) et des traits d’union (-), puis retourne la chaîne restante. Toutefois, vous pouvez modifier le modèle d’expression régulière afin qu’il supprime tous les caractères qui ne doivent pas être inclus dans une chaîne d’entrée.  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 Le modèle d’expression régulière `[^\w\.@-]` recherche tout caractère qui n’est pas un caractère de mot, un point, un symbole @ ou un trait d’union. Un caractère de mot correspond aux lettres, chiffres décimaux ou connecteurs de ponctuation tel qu’un trait de soulignement. Tout caractère qui correspond à ce modèle est remplacé par <xref:System.String.Empty?displayProperty=nameWithType>, qui est la chaîne définie par le modèle de remplacement. Pour autoriser des caractères supplémentaires dans une entrée d’utilisateur, ajoutez-les à la classe de caractères dans le modèle d’expression régulière. Par exemple, le modèle d’expression régulière `[^\w\.@-\\%]` autorise également un symbole de pourcentage et une barre oblique inverse dans une chaîne d’entrée.  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions régulières .NET](../../../docs/standard/base-types/regular-expressions.md)
