---
title: Limitations du composant Timer Windows Forms&#39;propriété d’intervalle s
ms.date: 03/30/2017
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
ms.openlocfilehash: 4808d115ff842c6c0e6b036da9fe20bb1b48f8a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536024"
---
# <a name="limitations-of-the-windows-forms-timer-component39s-interval-property"></a>Limitations du composant Timer Windows Forms&#39;propriété d’intervalle s
Windows Forms <xref:System.Windows.Forms.Timer> composant a un <xref:System.Windows.Forms.Timer.Interval%2A> propriété qui spécifie le nombre de millisecondes qui s’écouler entre deux événements de minuterie suivant. À moins que le composant est désactivé, une minuterie continue à recevoir le <xref:System.Windows.Forms.Timer.Tick> événement à intervalles réguliers à peu près égales.  
  
 Ce composant est conçu pour un environnement Windows Forms. Si vous avez besoin d’un minuteur adapté à un environnement de serveur, consultez l’article [Introduction aux minuteurs serveur](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).  
  
## <a name="the-interval-property"></a>La propriété Interval  
 Le <xref:System.Windows.Forms.Timer.Interval%2A> propriété présente quelques limitations à prendre en compte les quand vous programmez un <xref:System.Windows.Forms.Timer> composant :  
  
-   Si votre application ou une autre application effectue des demandes importantes sur le système, telles que les boucles longues, calculs complexes, ou le lecteur, réseau ou des accès de port, votre application ne disposeront pas d’événements de la minuterie aussi souvent que le <xref:System.Windows.Forms.Timer.Interval%2A> propriété spécifie.  
  
-   L’intervalle n’est pas garantie devant s’écouler exactement le moment. Pour garantir l’exactitude, la minuterie doit consulter l’horloge système en fonction des besoins, plutôt que de suivre en interne le temps écoulé.  
  
-   La précision de la <xref:System.Windows.Forms.Timer.Interval%2A> propriété est exprimée en millisecondes. Certains ordinateurs fournissent un compteur haute résolution d’une résolution supérieure aux millisecondes. La disponibilité d’un tel compteur varie selon le matériel de processeur de votre ordinateur. Pour plus d’informations, consultez l’article 172338, « Comment utiliser QueryPerformanceCounter à temps Code, » dans la Base de connaissances Microsoft à http://support.microsoft.com.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.Timer>  
 [Timer, composant](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [Vue d’ensemble du composant Timer](../../../../docs/framework/winforms/controls/timer-component-overview-windows-forms.md)
