---
title: 'Procédure pas à pas : création de contenu WPF sur les Windows Forms au moment du design'
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
ms.openlocfilehash: 1ea0160530fea0f35c6d4746dc4bbca9439bc462
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529007"
---
# <a name="walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time"></a>Procédure pas à pas : création de contenu WPF sur les Windows Forms au moment du design
Cette rubrique montre comment créer un contrôle Windows Presentation Foundation (WPF) pour une utilisation dans vos applications Windows Forms.  
  
 Au cours de cette procédure pas à pas, vous allez exécuter les tâches suivantes :  
  
-   créer le projet ;  
  
-   créer un projet WPF ;  
  
-   ajouter le nouveau contrôle WPF à un Windows Form. Le contrôle WPF est hébergé dans un contrôle <xref:System.Windows.Forms.Integration.ElementHost>.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  
  
## <a name="creating-the-project"></a>Création du projet  
 La première étape consiste à créer le projet Windows Forms.  
  
> [!NOTE]
>  Lors de l'hébergement de contenu WPF, seuls les projets Visual Basic et C# sont pris en charge.  
  
#### <a name="to-create-the-project"></a>Pour créer le projet  
  
-   Créer un nouveau projet d’Application Windows Forms dans Visual Basic ou Visual c# nommé `HostingWpf`.  
  
## <a name="creating-a-new-wpf-control"></a>Création d'un contrôle WPF  
 La création d'un contrôle WPF et son ajout à votre projet sont des tâches aussi simples que l'ajout de tout autre élément à votre projet. Le Concepteur Windows Forms fonctionne avec un type particulier de contrôle nommé *contrôle composite*, ou *contrôle utilisateur*. Pour plus d'informations sur les contrôles utilisateur WPF, consultez <xref:System.Windows.Controls.UserControl>.  
  
> [!NOTE]
>  Le type <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> pour WPF est distinct du type de contrôle utilisateur fourni par Windows Forms, également nommé <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.  
  
#### <a name="to-create-a-new-wpf-control"></a>Pour créer un contrôle WPF  
  
1.  Dans **l’Explorateur de solutions**, ajoutez un nouveau **bibliothèque de contrôles utilisateur WPF** projet à la solution. Utilisez le nom par défaut pour la bibliothèque de contrôles, `WpfControlLibrary1`. Le nom du contrôle par défaut est `UserControl1.xaml`.  
  
     L'ajout du nouveau contrôle a les effets suivants.  
  
    -   Le fichier UserControl1.xaml est ajouté.  
  
    -   Le fichier UserControl1.xaml.cs ou UserControl1.xaml.vb est ajouté. Ce fichier contient le code-behind pour les gestionnaires d'événements et autre implémentation.  
  
    -   Les références aux assemblys WPF sont ajoutées.  
  
    -   Le fichier UserControl1.xaml s'ouvre dans le [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].  
  
2.  En mode Design, assurez-vous que `UserControl1` est sélectionné. Pour plus d’informations, consultez [Comment : sélectionner et déplacer des éléments sur l’aire de conception](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).  
  
3.  Dans le **propriétés** fenêtre, définissez la valeur de la <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> propriétés `200`.  
  
4.  À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> contrôle sur l’aire de conception.  
  
5.  Dans le **propriétés** fenêtre, définissez la valeur de la <xref:System.Windows.Controls.TextBox.Text%2A> propriété **le contenu hébergé**.  
  
    > [!NOTE]
    >  En général, vous devez héberger du contenu WPF plus sophistiqué. Le contrôle <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> est utilisé ici uniquement à titre d'illustration.  
  
6.  Générez le projet.  
  
## <a name="adding-a-wpf-control-to-a-windows-form"></a>Ajout d'un contrôle WPF à un Windows Form  
 Votre nouveau contrôle WPF est prêt à être utilisé sur le formulaire. Windows Forms utilise le contrôle <xref:System.Windows.Forms.Integration.ElementHost> pour héberger le contenu WPF  
  
#### <a name="to-add-a-wpf-control-to-a-windows-form"></a>Pour ajouter un contrôle WPF à un Windows Form  
  
1.  Ouvrez `Form1` dans le Concepteur Windows Forms.  
  
2.  Dans le **boîte à outils**, l’onglet **contrôles utilisateur WPF WPFUserControlLibrary**.  
  
3.  Faites glisser une instance de `UserControl1` sur le formulaire.  
  
    -   Un contrôle <xref:System.Windows.Forms.Integration.ElementHost> est créé automatiquement sur le formulaire pour héberger le contrôle WPF.  
  
    -   Le <xref:System.Windows.Forms.Integration.ElementHost> contrôle est nommé `elementHost1` et dans le **propriétés** fenêtre, vous pouvez voir son <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> est définie sur **UserControl1**.  
  
    -   des références aux assemblys WPF sont ajoutées au projet.  
  
    -   Le contrôle `elementHost1` a un panneau de Smart Tags qui affiche les options d'hébergement disponibles.  
  
4.  Dans le **tâches ElementHost** panneau des balises actives, sélectionnez **ancrer dans le conteneur parent**.  
  
5.  Appuyez sur F5 pour générer et exécuter l'application.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Windows Forms et WPF sont des technologies différentes, mais elles sont conçues pour interagir étroitement. Pour fournir une apparence et un comportement enrichis dans vos applications, essayez ce qui suit.  
  
-   Hébergez un contrôle Windows Forms dans une page WPF. Pour plus d’informations, consultez [procédure pas à pas : hébergement d’un contrôle Windows Forms dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).  
  
-   Appliquez des styles visuels Windows Forms à votre contenu WPF. Pour plus d’informations, consultez [Guide pratique pour activer des styles visuels dans une application hybride](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).  
  
-   Modifiez le style de votre contenu WPF. Pour plus d’informations, consultez [procédure pas à pas : conception de styles de contenu WPF](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Migration et interopérabilité](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [Utilisation de contrôles WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [Concepteur WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
