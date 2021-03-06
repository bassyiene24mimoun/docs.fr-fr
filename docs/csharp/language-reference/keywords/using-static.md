---
title: using static, directive (référence C#)
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c9b7508c6e751f83fdc16a700ad68aa7de36e497
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33285133"
---
# <a name="using-static-directive-c-reference"></a>using static, directive (référence C#)

La directive `using static` désigne un type aux membres statiques duquel vous pouvez accéder sans spécifier un nom de type. Sa syntaxe est la suivante :

```csharp
using static <fully-qualified-type-name>
```

où *fully-qualified-type-name* est le nom du type dont les membres statiques peuvent être référencés sans spécifier de nom de type. Si vous ne fournissez pas de nom de type complet (le nom de l’espace de noms complet avec le nom du type), C# génère l’erreur du compilateur CS0246 : "Le nom du type ou de l’espace de noms '<nom_type>' est introuvable".

La directive `using static` s’applique à tout type ayant des membres statiques, même s’il a également des membres d’instance. Toutefois, les membres d’instance ne peuvent être appelés que par l’instance du type.

La directive `using static` a été introduite avec C# 6.

## <a name="remarks"></a>Notes
 
En général, quand vous appelez un membre statique, vous indiquez le nom du type, ainsi que le nom du membre. Entrer plusieurs fois le même nom de type pour appeler des membres du type peut produire du code détaillé et peu clair. Par exemple, la définition suivante d’une classe `Circle` référence un certain nombre de membres de la classe <xref:System.Math>.
  
[!code-csharp[using-static#1](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

En éliminant la nécessité de référencer explicitement la classe <xref:System.Math> chaque fois qu’un membre est référencé, la directive `using static` génère du code beaucoup plus clair :

[!code-csharp[using-static#2](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

`using static` importe uniquement les membres statiques accessibles et les types imbriqués déclarés dans le type spécifié.  Les membres hérités ne sont pas importés.  Vous pouvez importer à partir de n'importe quel type nommé avec une directive static, notamment des modules Visual Basic.  Si des fonctions de niveau supérieur F# apparaissent dans les métadonnées comme membres statiques d’un type nommé dont le nom est un identificateur C# valide, les fonctions F# peuvent être importées.  
  
 `using static` rend les méthodes d'extension déclarées dans le type spécifié disponibles pour la recherche de méthode d'extension.  Toutefois, les noms des méthodes d’extension ne sont pas importés dans la portée pour la référence non qualifiée dans le code.  
  
 Les méthodes portant le même nom et qui sont importées à partir de différents types par différentes directives `using static` dans la même unité de compilation ou le même espace de noms forment un groupe de méthodes.  La résolution de surcharge au sein de ces groupes de méthodes suit des règles C# normales.  
  
## <a name="example"></a>Exemple

L’exemple suivant utilise la directive `using static` pour que les membres statiques des classes <xref:System.Console>, <xref:System.Math> et <xref:System.String> soient disponibles sans que vous ayez à spécifier leur nom de type.

[!code-csharp[using-static#3](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

Dans cet exemple, la directive `using static` aurait également pu être appliquée au type <xref:System.Double>. Cela aurait permis d’appeler la méthode <xref:System.Double.TryParse(System.String,System.Double@)> sans spécifier un nom de type. Toutefois, cela crée un code moins lisible, car il est nécessaire de vérifier les instructions `using static` pour déterminer quelle méthode `TryParse` du type numérique est appelée.

## <a name="see-also"></a>Voir aussi

[using, directive](using-directive.md)   
[Référence du langage C#](../../../csharp/language-reference/index.md)   
[Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
[Utilisation d’espaces de noms](../../../csharp/programming-guide/namespaces/using-namespaces.md)   
[Mots clés d’espaces de noms](../../../csharp/language-reference/keywords/namespace-keywords.md)   
[Espaces de noms](../../../csharp/programming-guide/namespaces/index.md)   
