---
title: Présentation des opérateurs de requête standard (C#)
ms.date: 07/20/2015
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
ms.openlocfilehash: 36bd5927e64ffacb97beac28b8e7790204e08c5c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337322"
---
# <a name="standard-query-operators-overview-c"></a>Présentation des opérateurs de requête standard (C#)
Les *opérateurs de requête standard* sont les méthodes qui forment le modèle de requête LINQ. La plupart de ces méthodes fonctionnent sur des séquences, où une séquence est un objet dont le type implémente l’interface <xref:System.Collections.Generic.IEnumerable%601> ou l’interface <xref:System.Linq.IQueryable%601>. Les opérateurs de requête standard fournissent des fonctionnalités de requête, dont notamment le filtrage, la projection, l’agrégation, le tri, etc.  
  
 Il existe deux ensembles d’opérateurs de requête standard LINQ, l’un opérant sur des objets de type <xref:System.Collections.Generic.IEnumerable%601> et l’autre sur des objets de type <xref:System.Linq.IQueryable%601>. Les méthodes qui composent chaque ensemble sont des membres statiques des classes <xref:System.Linq.Enumerable> et <xref:System.Linq.Queryable>, respectivement. Elles sont définies en tant que *méthodes d’extension* du type sur lequel elles opèrent. Cela signifie qu’elles peuvent être appelées à l’aide de la syntaxe de méthode statique ou de la syntaxe de méthode d’instance.  
  
 De plus, plusieurs méthodes d’opérateur de requête standard fonctionnent sur des types autres que ceux basés sur <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601>. Le type <xref:System.Linq.Enumerable> définit deux de ces méthodes qui fonctionnent toutes deux sur les objets de type <xref:System.Collections.IEnumerable>. Ces méthodes, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> et <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, vous permettent d’autoriser l’interrogation d’une collection non paramétrée, ou non générique, dans le modèle LINQ. Pour cela, elles créent une collection fortement typée d’objets. La classe <xref:System.Linq.Queryable> définit deux méthodes similaires, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> et <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, qui opèrent sur les objets de type <xref:System.Linq.Queryable>.  
  
 Les opérateurs de requête standard diffèrent dans le déroulement de leur exécution, selon qu’ils retournent une valeur singleton ou une séquence de valeurs. Les méthodes qui retournent une valeur de singleton (par exemple, <xref:System.Linq.Enumerable.Average%2A> et <xref:System.Linq.Enumerable.Sum%2A>) s’exécutent immédiatement. Les méthodes qui retournent une séquence diffèrent l’exécution de la requête et retournent un objet énumérable.  
  
 Dans le cas des méthodes qui opèrent sur des collections en mémoire, c’est-à-dire des méthodes qui étendent <xref:System.Collections.Generic.IEnumerable%601>, l’objet énumérable retourné capture les arguments passés à la méthode. Lorsque cet objet est énuméré, la logique de l’opérateur de requête est employée et les résultats de requête sont retournés.  
  
 En revanche, les méthodes qui étendent <xref:System.Linq.IQueryable%601> n’implémentent aucun comportement d’interrogation, mais créent une arborescence d’expressions qui représente la requête à exécuter. Le traitement des requêtes est géré par l’objet <xref:System.Linq.IQueryable%601> source.  
  
 Les appels aux méthodes de requête peuvent être chaînés dans une requête unique, ce qui permet de rendre les requêtes arbitrairement complexes.  
  
 L’exemple de code suivant illustre l’utilisation des opérateurs de requête standard pour obtenir des informations sur une séquence.  
  
```csharp  
string sentence = "the quick brown fox jumps over the lazy dog";  
// Split the string into individual words to create a collection.  
string[] words = sentence.Split(' ');  
  
// Using query expression syntax.  
var query = from word in words  
            group word.ToUpper() by word.Length into gr  
            orderby gr.Key  
            select new { Length = gr.Key, Words = gr };  
  
// Using method-based query syntax.  
var query2 = words.  
    GroupBy(w => w.Length, w => w.ToUpper()).  
    Select(g => new { Length = g.Key, Words = g }).  
    OrderBy(o => o.Length);  
  
foreach (var obj in query)  
{  
    Console.WriteLine("Words of length {0}:", obj.Length);  
    foreach (string word in obj.Words)  
        Console.WriteLine(word);  
}  
  
// This code example produces the following output:  
//  
// Words of length 3:  
// THE  
// FOX  
// THE  
// DOG  
// Words of length 4:  
// OVER  
// LAZY  
// Words of length 5:  
// QUICK  
// BROWN  
// JUMPS   
```  
  
## <a name="query-expression-syntax"></a>Syntaxe d'expression de requête  
 Certains des opérateurs de requête standard les plus courants ont une syntaxe de mots clés dédiée des langages C# et Visual Basic, qui permet de les appeler dans le cadre d’une *expression* de *requête*. Pour plus d’informations sur les opérateurs de requête standard qui ont des mots clés dédiés et sur leurs syntaxes correspondantes, consultez [Syntaxe des expressions de requête pour les opérateurs de requête standard (C#)](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).  
  
## <a name="extending-the-standard-query-operators"></a>Extension des opérateurs de requête standard  
 Vous pouvez augmenter l’ensemble d’opérateurs de requête standard en créant des méthodes spécifiques au domaine appropriées pour votre domaine ou technologie cible. Vous pouvez également remplacer les opérateurs de requête standard par vos propres implémentations qui fournissent des services supplémentaires, tels que l’évaluation à distance, la traduction des requêtes et l’optimisation. Pour obtenir un exemple, consultez <xref:System.Linq.Enumerable.AsEnumerable%2A>.  
  
## <a name="related-sections"></a>Rubriques connexes  
 Les liens suivants renvoient à des rubriques contenant des informations supplémentaires sur les divers opérateurs de requête standard, selon leurs fonctionnalités.  
  
 [Tri des données (C#)](../../../../csharp/programming-guide/concepts/linq/sorting-data.md)  
  
 [Opérations ensemblistes (C#)](../../../../csharp/programming-guide/concepts/linq/set-operations.md)  
  
 [Filtrage des données (C#)](../../../../csharp/programming-guide/concepts/linq/filtering-data.md)  
  
 [Opérations de quantificateur (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [Opérations de projection (C#)](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)  
  
 [Partitionnement des données (C#)](../../../../csharp/programming-guide/concepts/linq/partitioning-data.md)  
  
 [Opérations de jointure (C#)](../../../../csharp/programming-guide/concepts/linq/join-operations.md)  
  
 [Regroupement de données (C#)](../../../../csharp/programming-guide/concepts/linq/grouping-data.md)  
  
 [Opérations de génération (C#)](../../../../csharp/programming-guide/concepts/linq/generation-operations.md)  
  
 [Opérations d’égalité (C#)](../../../../csharp/programming-guide/concepts/linq/equality-operations.md)  
  
 [Opérations d’élément (C#)](../../../../csharp/programming-guide/concepts/linq/element-operations.md)  
  
 [Conversion des types de données (C#)](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md)  
  
 [Opérations de concaténation (C#)](../../../../csharp/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [Opérations d’agrégation (C#)](../../../../csharp/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Linq.Enumerable>  
 <xref:System.Linq.Queryable>  
 [Introduction aux requêtes LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 [Syntaxe des expressions de requête pour les opérateurs de requête standard (C#)](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)  
 [Classification des opérateurs de requête standard en fonction de leur mode d’exécution](../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)  
 [Méthodes d’extension](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
