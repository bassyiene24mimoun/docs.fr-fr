---
title: AddHandler, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: bc0dce442db9d62b9fbee857b6e711696ad87fb8
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37936813"
---
# <a name="addhandler-statement"></a>AddHandler, instruction
Associe un événement à un gestionnaire d’événements en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>Composants  
|||
|---|---|
|événement|Le nom de l’événement à gérer.|  
|`eventhandler`|Le nom d’une procédure qui gère l’événement.|
|||
  
## <a name="remarks"></a>Notes  
 Le `AddHandler` et `RemoveHandler` vous permettent de démarrer et arrêter la gestion des événements à tout moment pendant l’exécution du programme.  
  
 La signature de la `eventhandler` procédure doit correspondre à la signature de l’événement `event`.  
  
 Le mot clé `Handles` et l'instruction `AddHandler` vous permettent de spécifier que des procédures particulières gèrent des événements particuliers, mais il existe des différences. L'instruction `AddHandler` connecte les procédures aux événements au moment de l'exécution. Utilisez le mot clé `Handles` quand vous définissez une procédure pour indiquer qu'elle gère un événement particulier. Pour plus d’informations, consultez [gère](../../../visual-basic/language-reference/statements/handles-clause.md).  
  
> [!NOTE]
>  Pour les événements personnalisés, le `AddHandler` instruction appelle de l’événement `AddHandler` accesseur. Pour plus d’informations sur les événements personnalisés, consultez [Event, instruction](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Exemple  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/addhandler-statement_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [RemoveHandler (instruction)](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [Event (instruction)](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Événements](../../../visual-basic/programming-guide/language-features/events/index.md)
