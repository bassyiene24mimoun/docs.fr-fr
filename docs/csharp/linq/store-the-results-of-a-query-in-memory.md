---
title: Stocker les résultats d’une requête dans la mémoire
description: Comment enregistrer les résultats.
ms.date: 11/30/2016
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: 52d502a841c428bd90a26c803ba577e76c17197c
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404299"
---
# <a name="store-the-results-of-a-query-in-memory"></a>Stocker les résultats d’une requête dans la mémoire

Une requête est en fait un ensemble d’instructions permettant de récupérer et d’organiser des données. Les requêtes sont exécutées de manière différée, à mesure que chaque élément dans le résultat est demandé. Lorsque vous utilisez `foreach` pour effectuer une itération sur les résultats, les éléments sont retournés lorsque vous y accédez. Pour évaluer une requête et stocker ses résultats sans exécuter une boucle `foreach`, appelez simplement l’une des méthodes suivantes sur la variable de requête :

- <xref:System.Linq.Enumerable.ToList%2A>

- <xref:System.Linq.Enumerable.ToArray%2A>

- <xref:System.Linq.Enumerable.ToDictionary%2A>

- <xref:System.Linq.Enumerable.ToLookup%2A>

 Lorsque vous stockez les résultats de requête, nous vous recommandons d’assigner l’objet de collection retourné à une nouvelle variable, comme indiqué dans l’exemple suivant :

## <a name="example"></a>Exemple

[!code-csharp[csProgGuideLINQ#25](~/samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]

## <a name="see-also"></a>Voir aussi

[LINQ (Language Integrated Query)](index.md)