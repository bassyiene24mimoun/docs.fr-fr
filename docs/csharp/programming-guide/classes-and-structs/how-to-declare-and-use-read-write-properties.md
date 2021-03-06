---
title: 'Comment : déclarer et utiliser des propriétés en lecture-écriture (Guide de programmation C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: d6a7083e1c0cf0dc5c076a69dee15fc39e234d53
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172316"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a>Comment : déclarer et utiliser des propriétés en lecture-écriture (Guide de programmation C#)
Les propriétés offrent la commodité des membres de données publics sans les risques liés à un accès non protégé, non contrôlé et non vérifié aux données d’un objet. Cela se fait au moyen d’*accesseurs*, lesquels sont des méthodes spéciales qui affectent et récupèrent des valeurs du membre de données sous-jacent. L’accesseur [set](../../../csharp/language-reference/keywords/set.md) permet aux membres de données d’être affectés, et l’accesseur [get](../../../csharp/language-reference/keywords/get.md) récupère des valeurs de membres de données.  
  
 L’exemple suivant montre une classe `Person` qui possède deux propriétés : `Name` (string) et `Age` (int). Étant donné que les deux propriétés fournissent des accesseurs `get` et `set`, elles sont considérées comme des propriétés en lecture/écriture.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csProgGuideObjects#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_1.cs)]  
  
## <a name="robust-programming"></a>Programmation fiable  
 Dans l’exemple précédent, les propriétés `Name` et `Age` sont [publiques](../../../csharp/language-reference/keywords/public.md), et incluent un accesseur `get` et un accesseur `set`. Cela permet à n’importe quel objet de lire et d’écrire ces propriétés. Toutefois, il est parfois souhaitable d’exclure l’un des accesseurs. L’omission de l’accesseur `set`, par exemple, met la propriété en lecture seule :  
  
 [!code-csharp[csProgGuideObjects#87](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_2.cs)]  
  
 Vous pouvez également exposer publiquement un accesseur mais rendre l’autre private ou protected. Pour plus d’informations, consultez [Accessibilité de l’accesseur asymétrique](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).  
  
 Une fois les propriétés déclarées, vous pouvez les utiliser comme s’il s’agissait de champs de la classe. Cela permet une syntaxe très naturelle pour obtenir ou définir la valeur d’une propriété, comme dans les instructions suivantes :  
  
 [!code-csharp[csProgGuideObjects#35](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_3.cs)]  
  
 Notez qu’une variable `value` spéciale est disponible dans la méthode `set` d’une propriété. Cette variable contient la valeur que l’utilisateur a spécifiée, par exemple :  
  
 [!code-csharp[csProgGuideObjects#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_4.cs)]  
  
 Notez la syntaxe correcte pour incrémenter la propriété `Age` sur un objet `Person` :  
  
 [!code-csharp[csProgGuideObjects#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_5.cs)]  
  
 Si des méthodes `set` et `get` distinctes ont été utilisées pour modeler des propriétés, le code équivalent peut avoir la forme suivante :  
  
```csharp  
person.SetAge(person.GetAge() + 1);   
```  
  
 La méthode `ToString` est substituée dans cet exemple :  
  
 [!code-csharp[csProgGuideObjects#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_6.cs)]  
  
 Vous pouvez remarquer que `ToString` n’est pas utilisée de façon explicite dans le programme. Elle est appelée par défaut par les appels `WriteLine`.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)
