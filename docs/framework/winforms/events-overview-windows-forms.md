---
title: "Vue d&#39;ensemble des &#233;v&#233;nements (Windows Forms) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "délégués (Windows Forms), événements et"
  - "délégués (Windows Forms), multicast"
  - "événements (Windows Forms), à propos des événements"
  - "délégués d'événements multicast"
  - "contrôles Windows Forms, événements"
  - "Windows Forms, gestion des événements"
ms.assetid: 814a6a43-a312-4791-88d8-f75f9a4f8c4c
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Vue d&#39;ensemble des &#233;v&#233;nements (Windows Forms)
Un événement est une action à laquelle vous pouvez répondre ou que vous pouvez « gérer » dans le code.  Les événements peuvent être déclenchés par une action de l'utilisateur \(quand il clique sur un bouton de la souris ou appuie sur une touche\), par le code d'un programme ou par le système.  
  
 Les applications pilotées par événements exécutent du code en réponse à un événement.  Chaque formulaire et chaque contrôle exposent un ensemble prédéfini d'événements que vous pouvez programmer.  Si l'un de ces événements se produit et que le gestionnaire d'événements associé contient du code, celui\-ci est appelé.  
  
 Les types d'événements déclenchés par un objet sont divers, mais bon nombre d'entre eux sont communs à la plupart des contrôles.  Par exemple, la plupart des objets peuvent gérer un événement <xref:System.Windows.Forms.Control.Click>.  Si un utilisateur clique sur un formulaire, le code du gestionnaire de l'événement <xref:System.Windows.Forms.Control.Click> de ce dernier est exécuté.  
  
> [!NOTE]
>  De nombreux événements se produisent conjointement à d'autres événements.  Par exemple, les événements <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDown> et <xref:System.Windows.Forms.Control.MouseUp> se produisent en même temps que l'événement <xref:System.Windows.Forms.Control.Click>.  
  
 Pour plus d'informations sur la façon de déclencher et de consommer un événement, consultez [Événements](../../../docs/standard/events/index.md).  
  
## Rôle des délégués  
 Les délégués sont des classes qui sont communément utilisées dans [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] pour générer des mécanismes de gestion des événements.  Les délégués sont à peu près équivalents aux pointeurs de fonction communément utilisés dans [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)] et d'autres langages orientés objet.  Toutefois à la différence des pointeurs de fonction, les délégués sont orientés objet, de type sécurisé et sûrs.  De plus, alors qu'un pointeur de fonction ne contient qu'une référence à une fonction spécifique, un délégué consiste en une référence à un objet et des références à une ou plusieurs méthodes de cet objet.  
  
 Ce modèle d'événement utilise les *délégués* pour lier les événements aux méthodes servant à les gérer.  Le délégué permet aux autres classes de s'inscrire pour la notification d'événement en spécifiant une méthode de gestionnaire.  Quand l'événement se produit, le délégué appelle la méthode liée.  Pour plus d'informations sur la façon de définir des délégués, consultez [Événements](../../../docs/standard/events/index.md).  
  
 Les délégués peuvent être liés à une ou plusieurs méthodes \(ou multidiffusion\).  Quand vous créez un délégué pour un événement, vous \(ou le Concepteur Windows Forms\) créez généralement un événement multidiffusion.  Il existe cependant une exception à cette règle : quand un événement déclenche une procédure particulière \(par exemple, l'affichage d'une boîte de dialogue\) qui logiquement ne se répéterait pas plusieurs fois par événement.  Pour plus d'informations sur la façon de créer un délégué multicast, consultez [Comment : combiner des délégués \(délégués multicast\)](../Topic/How%20to:%20Combine%20Delegates%20\(Multicast%20Delegates\)\(C%23%20Programming%20Guide\).md).  
  
 Un délégué multidiffusion tient à jour une liste d'appel des méthodes auxquelles il est lié.  Celui\-ci prend en charge une méthode <xref:System.Delegate.Combine%2A> pour ajouter une méthode à la liste d'appel et une méthode <xref:System.Delegate.Remove%2A> pour la supprimer.  
  
 Quand un événement est enregistré par l'application, le contrôle le déclenche en appelant son délégué.  Le délégué appelle à son tour la méthode liée.  Dans le cas le plus courant \(délégué multidiffusion\), le délégué appelle à tour de rôle chaque méthode liée de la liste d'appel, ce qui produit une notification un à plusieurs.  Cette stratégie signifie que le contrôle n'a pas besoin de tenir à jour une liste des objets cible pour la notification d'événement car le délégué gère totalement l'inscription et la notification.  
  
 Les délégués permettent également de lier plusieurs événements à la même méthode et par conséquent de produire une notification plusieurs\-à\-un.  Par exemple, un événement button\-click et un événement menu\-command–click peuvent tous deux appeler le même délégué, lequel appelle à son tour une méthode unique pour qu'elle prenne en charge ces deux événements distincts de la même façon.  
  
 Le mécanisme de liaison utilisé avec les délégués est dynamique : un délégué peut être lié au moment de l'exécution à n'importe quelle méthode dont la signature correspond à celle du gestionnaire d'événements.  Cette fonctionnalité vous permet de configurer ou de modifier la méthode de liaison en fonction d'une condition et d'attacher dynamiquement un gestionnaire d'événements à un contrôle.  
  
## Voir aussi  
 [Création de gestionnaires d'événements dans les Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)   
 [Vue d'ensemble des gestionnaires d'événements](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)