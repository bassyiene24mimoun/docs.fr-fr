---
title: "Guide de d&#233;ploiement du .NET Framework pour les d&#233;veloppeurs | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "guide du développeur, déploiement du .NET Framework"
  - "déploiement (.NET Framework), guide du développeur"
ms.assetid: 094d043e-33c4-40ba-a503-e0b20b55f4cf
caps.latest.revision: 108
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 107
---
# Guide de d&#233;ploiement du .NET Framework pour les d&#233;veloppeurs
Cette rubrique fournit des informations destinées aux développeurs qui souhaitent installer le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], 4.5.1, 4.5.2, le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], 4.6.1 ou 4.6.2 avec leurs applications.  
  
 Pour obtenir des liens de téléchargement, consultez la section [Packages redistribuables](#redist). Vous pouvez également télécharger les packages redistribuables et les modules linguistiques aux pages suivantes du Centre de téléchargement Microsoft :  
  
-   [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] pour tous les systèmes d’exploitation \([programme d’installation web](http://go.microsoft.com/fwlink/?LinkId=780597) ou [programme d’installation hors connexion](http://go.microsoft.com/fwlink/p/?LinkId=780601)\)  
  
-   [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] pour tous les systèmes d’exploitation \([programme d’installation web](http://go.microsoft.com/fwlink/?LinkId=671729) ou [programme d’installation hors connexion](http://go.microsoft.com/fwlink/p/?LinkId=671744)\)  
  
-   [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] pour tous les systèmes d’exploitation \([programme d’installation web](http://go.microsoft.com/fwlink/?LinkId=528222) ou [programme d’installation hors connexion](http://go.microsoft.com/fwlink/p/?LinkId=528232)\)  
  
-   .NET Framework 4.5.2 pour tous les systèmes d’exploitation \([programme d’installation web](http://go.microsoft.com/fwlink/p/?LinkId=397703) ou [programme d’installation hors connexion](http://go.microsoft.com/fwlink/p/?LinkId=397706)\)  
  
-   .NET Framework 4.5.1 pour tous les systèmes d’exploitation \([programme d’installation web](http://go.microsoft.com/fwlink/p/?LinkId=310158) ou [programme d’installation hors connexion](http://go.microsoft.com/fwlink/p/?LinkId=310159)\)  
  
-   [.NET Framework 4.5](http://go.microsoft.com/fwlink/p/?LinkId=245484)  
  
 Remarques importantes :  
  
> [!NOTE]
>  L’expression « [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] et ses mises en production intermédiaires » fait référence au [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], 4.5.1, 4.5.2, 4.6, 4.6.1 et 4.6.2.  
  
-   Le [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], 4.5.2, 4.6, 4.6.1 et 4.6.2 sont des mises à jour sur place du [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], ce qui signifie qu’elles utilisent la même version du runtime. Cependant, les versions des assemblys sont mises à jour et incluent de nouveaux types et membres.  
  
-   [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] et ses versions intermédiaires sont générés de façon incrémentielle sur [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Quand vous installez le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], 4.5.1, 4.5.2, 4.6, 4.6.1 ou 4.6.2 sur un système où le [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] est installé, les assemblys de version 4 sont remplacés par les versions plus récentes.  
  
-   Si vous faites référence à un [package hors bande](http://msdn.microsoft.com/library/dn151288\(v=vs.110\).aspx) Microsoft dans votre application, l’assembly est inclus dans le package de l’application.  
  
-   Vous devez disposer de privilèges d'administrateur pour installer [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] et ses versions intermédiaires.  
  
-   [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] est inclus dans [!INCLUDE[win8](../../../includes/win8-md.md)] et [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], vous n'avez donc pas à le déployer avec votre application sur ces systèmes d'exploitation. De même, [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] est inclus dans [!INCLUDE[win81](../../../includes/win81-md.md)] et Windows Server 2012 R2. .NET Framework 4.5.2 n'est inclus dans aucun système d'exploitation. Le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] est fourni avec Windows 10, le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] est inclus dans la Mise à jour de novembre de Windows 10, et le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] est inclus dans la Mise à jour anniversaire Windows 10.  Pour obtenir la liste complète des configurations matérielle et logicielle requises, consultez [Configuration requise](../../../docs/framework/get-started/system-requirements.md).  
  
-   Depuis [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], vos utilisateurs peuvent afficher la liste des applications .NET Framework en cours d'exécution pendant l'installation et les fermer facilement. Cela peut contribuer à éviter les redémarrages système provoqués par les installations du .NET Framework. Consultez [Réduire le nombre de redémarrages système](../../../docs/framework/deployment/reducing-system-restarts.md).  
  
-   La désinstallation de [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ou de l’une de ses versions intermédiaires supprime également les fichiers [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] pré\-existants. Si vous souhaitez revenir au [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], vous devrez le réinstaller et effectuer toutes ses mises à jour. \(Consultez [Installation du .NET Framework 4](http://msdn.microsoft.com/library/5a4x27ek\(v=vs.100\).aspx).\)  
  
-   Le redistribuable .NET Framework 4.5 a été mis à jour le 9 octobre 2012 pour résoudre un problème lié à un horodatage incorrect sur un certificat numérique, ce qui a provoqué l'expiration prématurée de la signature numérique des fichiers produits et signés par Microsoft. Si vous avez installé précédemment le package redistribuable .NET Framework 4.5 daté du 16 août 2012, nous vous recommandons de mettre à jour votre copie avec le dernier redistribuable sur le site du [Centre de téléchargement Microsoft](http://go.microsoft.com/fwlink/p/?LinkId=245484). Pour plus d’informations sur ce problème, consultez l’[avis de sécurité Microsoft 2749655](http://technet.microsoft.com/security/advisory/2749655).  
  
 Pour plus d’informations sur la façon dont un administrateur système peut déployer le .NET Framework et ses dépendances système sur un réseau, consultez le [Guide de déploiement pour les administrateurs](../../../docs/framework/deployment/guide-for-administrators.md).  
  
<a name="deploy_options"></a>   
## Options de déploiement de votre application  
 Lorsque vous êtes prêt à publier votre application sur un serveur web ou dans un autre emplacement centralisé, afin que les utilisateurs puissent l'installer, vous pouvez choisir différentes méthodes de déploiement. Certaines de ces méthodes sont fournies avec Visual Studio. Le tableau ci\-dessous répertorie les options de déploiement de votre application et spécifie le package redistribuable du .NET Framework qui prend en charge chaque option. Outre ces options, vous pouvez écrire un programme d'installation personnalisé pour votre application. Pour plus d'informations, consultez la section [Chaînage de l'installation du .NET Framework à l'installation de votre application](#chaining).  
  
|Stratégie de déploiement de votre application|Méthodes de déploiement disponibles|Redistribuable du .NET Framework à utiliser|  
|---------------------------------------------------|-----------------------------------------|-------------------------------------------------|  
|Installation à partir du web|-   [InstallShield](#installshield)<br />-   [Ensemble d'outils WiX](#wix)<br />-   [Installation manuelle](#installing_manually)|[Programme d'installation web](#redist)|  
|Installation à partir d'un disque|-   [InstallShield](#installshield)<br />-   [Ensemble d'outils WiX](#wix)<br />-   [Installation manuelle](#installing_manually)|[Programme d'installation hors connexion](#redist)|  
|Installation à partir d'un réseau local \(pour applications d'entreprise\)|-   [ClickOnce](#clickonce)|[Programme d'installation web](#redist) \(voir [ClickOnce](#clickonce) pour connaître les restrictions\) ou [programme d'installation hors connexion](#redist)|  
  
<a name="redist"></a>   
## Packages redistribuables  
 Le .NET Framework est disponible dans deux packages redistribuables : le programme d'installation web \(programme d'amorçage\) et le programme d'installation hors connexion \(redistribuable autonome\). Le tableau ci\-dessous compare ces deux packages.  
  
||Programme d'installation web|Programme d'installation hors connexion|  
|-|----------------------------------|---------------------------------------------|  
|Fichier à télécharger|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] : <br />[NDP462\-KB3151802\-Web.exe](http://go.microsoft.com/fwlink/?LinkId=780596)<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] :<br />[NDP461\-KB3102438\-Web.exe](http://go.microsoft.com/fwlink/?LinkId=671728)<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] :<br />[NDP46\-KB3045560\-Web.exe](http://go.microsoft.com/fwlink/?LinkId=528222)<br /><br /> .NET Framework 4.5.2 : <br />[NDP452\-KB2901954\-Web.exe](http://go.microsoft.com/fwlink/?LinkId=397707)<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] : <br />[NDP451\-KB2859818\-Web.exe](http://go.microsoft.com/fwlink/?LinkId=322115)<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] : <br />[dotNetFx45\_Full\_setup.exe](http://go.microsoft.com/fwlink/?LinkId=225704)|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] : <br />[NDP462\-KB3151800\-x86\-x64\-AllOS\-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=780600)<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] : <br />[NDP461\-KB3102436\-x86\-x64\-AllOS\-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=671743)<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] : <br />[NDP46\-KB3045557\-x86\-x64\-AllOS\-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=528232)<br /><br /> .NET Framework 4.5.2 : <br /> [NDP452\-KB2901907\-x86\-x64\-AllOS\-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=397708)<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] : <br />[NDP451\-KB2858728\-x86\-x64\-AllOS\-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=322116)<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] : <br />[dotNetFx45\_Full\_x86\_x64.exe](http://go.microsoft.com/fwlink/?LinkId=225702)|  
|Connexion Internet requise ?|Oui|Non|  
|Taille du téléchargement|Réduite \(inclut le programme d'installation pour la plateforme cible uniquement\)\*|Étendue\*|  
|Modules linguistiques|Inclus\*\*|Doivent être [installés séparément](#chain_langpack), sauf si vous utilisez le package qui cible tous les systèmes d'exploitation|  
|Méthode de déploiement|Prend en charge toutes les méthodes :<br /><br /> -   [ClickOnce](#clickonce)<br />-   [InstallShield](#installshield)<br />-   [XML de Windows Installer \(WiX\)](#wix)<br />-   [Installation manuelle](#installing_manually)<br />-   [Installation personnalisée \(chaînage\)](#chaining)|Prend en charge toutes les méthodes :<br /><br /> -   [ClickOnce](#clickonce)<br />-   [InstallShield](#installshield)<br />-   [XML de Windows Installer \(WiX\)](#wix)<br />-   [Installation manuelle](#installing_manually)<br />-   [Installation personnalisée \(chaînage\)](#chaining)|  
|Site de téléchargement pour le déploiement ClickOnce|Centre de téléchargement Microsoft :<br /><br /> -   [.NET Framework 4.6.2](http://go.microsoft.com/fwlink/?LinkId=780596)<br />-   [.NET Framework 4.6.1](http://go.microsoft.com/fwlink/?LinkId=671728)<br />-   [.NET Framework 4.6](http://go.microsoft.com/fwlink/?LinkId=528222)<br />-   [.NET Framework 4.5.2](http://go.microsoft.com/fwlink/?LinkId=397703)<br />-   [.NET Framework 4.5.1](http://go.microsoft.com/fwlink/p/?LinkId=310158)<br />-   [.NET Framework 4.5](http://go.microsoft.com/fwlink/p/?LinkId=245484)|Votre propre serveur ou le Centre de téléchargement Microsoft :<br /><br /> -   [.NET Framework 4.6.2](http://go.microsoft.com/fwlink/?LinkId=780600)<br />-   [.NET Framework 4.6.1](http://go.microsoft.com/fwlink/?LinkId=671743)<br />-   [.NET Framework 4.6](http://go.microsoft.com/fwlink/?LinkId=528232)<br />-   [.NET Framework 4.5.2](http://go.microsoft.com/fwlink/p/?LinkId=397706)<br />-   [.NET Framework 4.5.1](http://go.microsoft.com/fwlink/p/?LinkId=310159)<br />-   [.NET Framework 4.5](http://go.microsoft.com/fwlink/p/?LinkId=245484)|  
  
 \* Le programme d'installation hors connexion est plus volumineux car il contient les composants pour toutes les plateformes cibles. Une fois que vous avez terminé l'installation, le système d'exploitation Windows met en cache uniquement le programme d'installation utilisé. Si le programme d'installation hors connexion est supprimé après l'installation, l'espace disque utilisé est identique à celui utilisé par le programme d'installation web. Si l'outil que vous utilisez \(par exemple, [InstallShield](#installshield)\) pour créer le programme d'installation de votre application fournit un dossier de fichiers d'installation qui est supprimé après l'installation, il est possible de supprimer automatiquement le programme d'installation hors connexion en le plaçant dans le dossier d'installation.  
  
 \*\* Si vous utilisez le programme d'installation web avec l'installation personnalisée, vous pouvez utiliser les paramètres de langue par défaut basés sur le paramètre de l'interface utilisateur multilingue de l'utilisateur ou vous pouvez spécifier un autre module linguistique en utilisant l'option `/LCID` sur la ligne de commande. Consultez la section [Chaînage à l'aide de l'interface utilisateur par défaut du .NET Framework](#chaining_default) pour obtenir des exemples.  
  
<a name="deployment_methods"></a>   
## Méthodes de déploiement  
 Trois méthodes de déploiement sont disponibles :  
  
-   Vous pouvez définir une dépendance sur le .NET Framework. Vous pouvez définir le .NET Framework comme condition préalable à l'installation de votre application, à l'aide de l'une des méthodes suivantes :  
  
    -   Utilisation du [déploiement ClickOnce](#clickonce) \(disponible dans Visual Studio\)  
  
    -   Création d'un [projet InstallShield](#installshield) \(disponible dans Visual Studio\)  
  
    -   Utilisation de l' [ensemble d'outils XML de Windows Installer \(WiX\)](#wix)  
  
-   Vous pouvez demander à vos utilisateurs d'[installer le .NET Framework manuellement](#installing_manually).  
  
-   Vous pouvez chaîner \(inclure\) le processus d'installation du .NET Framework dans l'installation de votre application, et déterminer la façon dont vous souhaitez gérer l'expérience d'installation du .NET Framework :  
  
    -   [Utilisez l'interface utilisateur par défaut](#chaining_default). Laissez le programme d'installation du .NET Framework fournir l'expérience d'installation.  
  
    -   [Personnalisez l'interface utilisateur](#chaining_custom) pour présenter une expérience d'installation unifiée et pour surveiller la progression de l'installation du .NET Framework.  
  
 Ces méthodes de déploiement sont discutées en détail dans les sections suivantes.  
  
## Définition d'une dépendance sur le .NET Framework  
 Si vous utilisez ClickOnce, InstallShield ou WiX pour déployer votre application, vous pouvez ajouter une dépendance sur le .NET Framework afin de pouvoir l'installer dans le cadre de votre application.  
  
<a name="clickonce"></a>   
### Déploiement ClickOnce  
 Le déploiement ClickOnce est disponible pour les projets créés avec Visual Basic et Visual C\#, mais pas Visual C\+\+.  
  
 Dans Visual Studio, choisissez le déploiement ClickOnce et ajoutez une dépendance sur le .NET Framework :  
  
1.  Ouvrez le projet d'application que vous souhaitez publier.  
  
2.  Dans l'Explorateur de solutions, ouvrez le menu contextuel de votre projet et choisissez **Propriétés**.  
  
3.  Choisissez le volet **Publier**.  
  
4.  Choisissez le bouton **Composants requis**.  
  
5.  Dans la boîte de dialogue **Composants requis**, vérifiez que la case à cocher **Créer un programme d'installation des composants requis** est activée.  
  
6.  Dans la liste des composants requis, recherchez la version du .NET Framework que vous avez utilisée pour générer votre projet et sélectionnez\-la.  
  
7.  Choisissez une option pour spécifier l'emplacement source des composants requis, puis choisissez **OK**.  
  
     Si vous indiquez une URL pour l’emplacement de téléchargement du .NET Framework, vous pouvez spécifier le site du Centre de téléchargement Microsoft ou un autre site de votre choix. Si vous placez le package redistribuable sur votre propre serveur, vous devez utiliser le programme d'installation hors connexion et non pas le programme d'installation web. Vous pouvez uniquement établir un lien vers le programme d'installation web dans le Centre de téléchargement Microsoft. L'URL peut également spécifier un disque sur lequel votre application est distribuée.  
  
8.  Dans la boîte de dialogue **Pages de propriétés**, choisissez **OK**.  
  
<a name="installshield"></a>   
### Déploiement d'InstallShield  
 Dans Visual Studio, choisissez le déploiement d'InstallShield et ajoutez une dépendance sur le .NET Framework :  
  
1.  Dans la barre de menus de Visual Studio, choisissez **Fichier**, **Nouveau**, **Projet**.  
  
2.  Dans le volet gauche de la boîte de dialogue **Nouveau projet**, choisissez **Autres types de projets**, **Configuration et déploiement**, **InstallShield LE**.  
  
3.  Dans la zone **Nom**, tapez un nom pour votre projet, puis choisissez **OK**.  
  
4.  Si vous créez un projet d’installation et de déploiement pour la première fois, choisissez **Accéder à InstallShield** ou **Activer InstallShield Limited Edition** pour télécharger InstallShield Limited Edition pour votre version de Microsoft Visual Studio. Redémarrez Visual Studio.  
  
5.  Ouvrez l'**Assistant Projet** et choisissez **Fichiers d'application** pour ajouter la sortie de projet. Vous pouvez configurer d'autres attributs de projet à l'aide de cet Assistant.  
  
6.  Accédez à **Configuration d'installation requise**, puis sélectionnez les systèmes d'exploitation et la version du .NET Framework que vous voulez installer.  
  
7.  Ouvrez le menu contextuel pour votre projet d'installation et choisissez **Générer**.  
  
<a name="wix"></a>   
### Déploiement via XML de Windows Installer \(WiX\)  
 L'ensemble d'outils XML de Windows Installer \(WiX\) génère des packages d'installation Windows à partir de code source XML. WiX prend en charge un environnement en ligne de commande qui peut être intégré dans vos processus de génération pour générer des packages d'installation MSI et MSM. Grâce à WiX, vous pouvez [spécifier le .NET Framework en tant que composant requis](http://wixtoolset.org/documentation/manual/v3/howtos/redistributables_and_install_checks/install_dotnet.html) ou [créer un programme de chaînage](http://wixtoolset.org/documentation/manual/v3/xsd/wix/exepackage.html) pour contrôler entièrement l’expérience de déploiement du .NET Framework. Pour plus d’informations sur WiX, consultez le site web [Ensemble d’outils du programme d’installation XML Windows \(WiX\)](http://wixtoolset.org/)  
  
<a name="installing_manually"></a>   
## Installation manuelle du .NET Framework  
 Il est parfois peu pratique d'installer automatiquement le .NET Framework avec votre application. Dans ce cas, vous pouvez faire en sorte que les utilisateurs installent le .NET Framework eux\-mêmes. Le package redistribuable est disponible dans [deux packages](#redist). Dans votre processus d'installation, fournissez des instructions sur la manière dont les utilisateurs doivent chercher et installer le .NET Framework.  
  
<a name="chaining"></a>   
## Chaînage de l'installation du .NET Framework à l'installation de votre application  
 Si vous créez un programme d'installation personnalisée pour votre application, vous pouvez chaîner \(inclure\) le processus d'installation du .NET Framework dans le processus d'installation de votre application. Le chaînage fournit deux options d'interface utilisateur pour l'installation du .NET Framework :  
  
-   Utiliser l'interface utilisateur par défaut fournie par le programme d'installation du .NET Framework.  
  
-   Créer une interface utilisateur personnalisée pour l'installation du .NET Framework pour des raisons de cohérence avec le programme d'installation de votre application.  
  
 Ces deux méthodes vous permettent d'utiliser le programme d'installation web ou le programme d'installation hors connexion. Chaque package présente ses propres avantages :  
  
-   Si vous utilisez le programme d'installation web, le processus d'installation du .NET Framework détermine quel package d'installation est obligatoire, et télécharge et installe uniquement ce package à partir du web.  
  
-   Si vous utilisez le programme d'installation hors connexion, vous pouvez inclure l'ensemble complet des packages d'installation du .NET Framework dans votre média de redistribution, afin que vos utilisateurs n'aient pas à télécharger de fichiers supplémentaires à partir d'Internet pendant l'installation.  
  
<a name="chaining_default"></a>   
### Chaînage à l'aide de l'interface utilisateur par défaut du .NET Framework  
 Pour chaîner en mode silencieux le processus d'installation du .NET Framework et laisser le programme d'installation du .NET Framework fournir l'interface utilisateur, ajoutez la commande suivante à votre programme d'installation :  
  
```  
<.NET Framework redistributable> /q /norestart /ChainingPackage <PackageName>  
```  
  
 Par exemple, si votre programme exécutable est Contoso.exe et que vous souhaitez installer en mode silencieux le package redistribuable [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] hors connexion, utilisez la commande :  
  
```  
dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage Contoso  
```  
  
 Vous pouvez utiliser des options de ligne de commande supplémentaires pour personnaliser l'installation. Par exemple :  
  
-   Pour permettre aux utilisateurs de fermer les applications .NET Framework en cours d'exécution, afin de réduire le nombre de redémarrages système, basculez en mode passif et utilisez l'option `/showrmui` comme suit :  
  
    ```  
    dotNetFx45_Full_x86_x64.exe /norestart /passive /showrmui /ChainingPackage Contoso  
    ```  
  
     Cette commande permet au Gestionnaire de redémarrage d'afficher une boîte de message permettant aux utilisateurs de fermer les applications .NET Framework avant d'installer .NET Framework.  
  
-   Si vous utilisez le programme d'installation web, vous pouvez utiliser l'option `/LCID` pour spécifier un module linguistique. Par exemple, pour chaîner le programme d'installation web [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] à votre programme d'installation Contoso et installer le module linguistique japonais, ajoutez la commande suivante au processus d'installation de votre application :  
  
    ```  
    dotNetFx45_Full_setup.exe /q /norestart /ChainingPackage Contoso /LCID 1041  
    ```  
  
     Si vous ne spécifiez pas l'option `/LCID`, le programme d'installation installe le module linguistique qui correspond au paramètre MUI de l'utilisateur.  
  
    > [!NOTE]
    >  Des modules linguistiques différents peuvent avoir des dates de publication différentes. Si le module linguistique spécifié n'est pas disponible dans le Centre de téléchargement, le programme d'installation installe le .NET Framework sans le module linguistique. Si le .NET Framework est déjà installé sur l'ordinateur de l'utilisateur, le programme d'installation installe uniquement le module linguistique.  
  
 Pour une liste complète des options, consultez la section [Options de ligne de commande](#command_line_options).  
  
 Pour les codes de retour courants, consultez la section [Codes de retour](#return_codes).  
  
<a name="chaining_custom"></a>   
### Chaînage à l'aide d'une interface utilisateur personnalisée  
 Si vous possédez un package d'installation personnalisée, vous pouvez lancer et suivre en mode silencieux l'installation du .NET Framework tout en affichant votre propre vue de la progression de l'installation. Dans ce cas, assurez\-vous que votre code prend en compte les points suivants :  
  
-   Vérifiez les [configurations matérielle et logicielle requises du .NET Framework](../../../docs/framework/get-started/system-requirements.md).  
  
-   [Détectez](#detect_net) si la version correcte du .NET Framework est déjà installée sur l'ordinateur de l'utilisateur.  
  
    > [!IMPORTANT]
    >  Pour déterminer si la version correcte du .NET Framework est déjà installée, vous devez vérifier si votre version cible *ou* une version ultérieure est installée, pas si votre version cible est installée. En d’autres termes, vous devez évaluer si la clé de version que vous récupérez à partir du Registre est supérieure ou égale à la clé de version de votre version cible, *pas* si elle est égale à la clé de version de votre version cible.  
  
-   [Détectez](#detect_langpack) si les modules linguistiques sont déjà installés sur l'ordinateur de l'utilisateur.  
  
-   Si vous souhaitez contrôler le déploiement, lancez et suivez en mode silencieux le processus d’installation du .NET Framework \(consultez [Comment : obtenir la progression à partir du programme d'installation du .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)\).  
  
-   Si vous déployez le programme d'installation hors connexion, [chaînez les modules linguistiques séparément](#chain_langpack).  
  
-   Personnalisez le déploiement à l'aide des [options de ligne de commande](#command_line_options). Par exemple, si vous chaînez le programme d'installation web du .NET Framework et que vous souhaitez remplacer le module linguistique par défaut, utilisez l'option `/LCID`, comme décrit dans la section précédente.  
  
-   [Résolvez les problèmes éventuels](#troubleshooting).  
  
<a name="detect_net"></a>   
### Détection du .NET Framework  
 Le programme d'installation du .NET Framework écrit des clés de Registre lorsque l'installation réussit. Vous pouvez savoir si le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ou version ultérieure est installé en vérifiant si le dossier `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` dans le Registre contient une valeur `DWORD` nommée `Release`. \(Notez que « NET Framework Setup » ne commence pas par un point.\) L’existence de cette clé indique que le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ou version ultérieure a été installé sur cet ordinateur. La valeur de `Release` indique quelle version du .NET Framework est installée.  
  
> [!IMPORTANT]
>  Vous devez rechercher une valeur **supérieure ou égale** à la valeur du mot clé de la mise en production quand vous tentez de détecter si une version spécifique est présente.  
  
|Version|Valeur du paramètre DWORD Release|  
|-------------|---------------------------------------|  
|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] installé sur Windows 10 Édition anniversaire|394802|  
|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] installé sur toutes les versions de système d’exploitation autres que Windows 10 Édition anniversaire|394806|  
|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] installé sur la mise à jour de novembre de Windows 10|394254|  
|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] installé sur toutes les versions de système d’exploitation autres que la mise à jour de novembre de Windows 10|394271|  
|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] installé sur Windows 10|393295|  
|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] installé sur toutes les versions du système d'exploitation autre que Windows 10|393297|  
|.NET Framework 4.5.2|379893|  
|[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] installé avec [!INCLUDE[win81](../../../includes/win81-md.md)] ou Windows Server 2012 R2|378675|  
|[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] installé sur [!INCLUDE[win8](../../../includes/win8-md.md)], Windows 7|378758|  
|[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]|378389|  
  
<a name="detect_langpack"></a>   
### Détection des modules linguistiques  
 Vous pouvez vérifier si un module linguistique spécifique est installé en recherchant le paramètre DWORD `Release` dans le dossier HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full\\*LCID* du Registre. \(Notez que « NET Framework Setup » ne commence pas par un point.\)*LCID* spécifie un identificateur de paramètres régionaux ; consultez la liste des [langues prises en charge](#supported_languages).  
  
 Par exemple, pour détecter si le module linguistique japonais complet \(LCID\=1041\) est installé, recherchez les valeurs suivantes dans le Registre :  
  
```  
Key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\1041  
Name: Release  
Type: DWORD  
```  
  
 Pour déterminer si la mise en production finale d’un module linguistique est installée pour le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], 4.5.1, 4.5.2, 4.6, 4.6.1 ou 4.6.2, vérifiez la valeur de la valeur DWORD RELEASE décrit dans la section précédente, [Détection du .NET Framework](#detect_net).  
  
<a name="chain_langpack"></a>   
### Chaînage des modules linguistiques à l'installation de votre application  
 Le .NET Framework fournit un ensemble de fichiers exécutables de modules linguistiques autonomes qui contiennent des ressources localisées pour des cultures spécifiques. Les modules linguistiques sont disponibles dans le Centre de téléchargement Microsoft :  
  
-   [Modules linguistiques .NET Framework 4.6.2](http://go.microsoft.com/fwlink/p/?LinkId=780604)  
  
-   [Modules linguistiques .NET Framework 4.6.1](http://go.microsoft.com/fwlink/p/?LinkId=671747)  
  
-   [Modules linguistiques .NET Framework 4.6](http://go.microsoft.com/fwlink/p/?LinkId=528314)  
  
-   [Modules linguistiques .NET Framework 4.5.2](http://go.microsoft.com/fwlink/p/?LinkId=397701)  
  
-   [Modules linguistiques .NET Framework 4.5.1](http://go.microsoft.com/fwlink/p/?LinkId=322101)  
  
-   [Modules linguistiques .NET Framework 4.5](http://go.microsoft.com/fwlink/p/?LinkId=245451)  
  
> [!IMPORTANT]
>  Les modules linguistiques ne contiennent pas les composants .NET Framework requis pour exécuter une application. Vous devez installer le .NET Framework à l'aide du programme d'installation web ou hors connexion avant d'installer un module linguistique.  
  
 À compter du [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], les noms de packages prennent la forme NDP\<`version`\>\-KB\<`number`\>\-x86\-x64\-AllOS\-\<`culture`\>.exe, où `version` est le numéro de version du .NET Framework, `number` est un numéro d’article de la Base de connaissances Microsoft, et `culture` spécifie un [pays\/région](#supported_languages). Exemple de ce type de package : `NDP452-KB2901907-x86-x64-AllOS-JPN.exe`. Les noms de packages sont répertoriés dans la section [Packages redistribuables](#redist) plus haut dans cet article.  
  
 Pour installer un module linguistique à l'aide du programme d'installation hors connexion du .NET Framework, vous devez le chaîner à l'installation de votre application. Par exemple, pour déployer le programme d'installation hors connexion de [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] avec le module linguistique japonais, utilisez la commande suivante :  
  
```  
NDP451-KB2858728-x86-x64-AllOS-JPN.exe/q /norestart /ChainingPackage <ProductName>  
```  
  
 Vous n'êtes pas tenu de chaîner les modules linguistiques si vous utilisez le programme d'installation web. Ce dernier installe le module linguistique qui correspond au paramètre MUI de l'utilisateur. Pour installer une autre langue, vous pouvez utiliser l'option `/LCID` pour spécifier un module linguistique.  
  
 Pour une liste complète des options de ligne de commande, consultez la section [Options de ligne de commande](#command_line_options).  
  
<a name="troubleshooting"></a>   
### Résolution des problèmes  
  
<a name="return_codes"></a>   
#### Codes de retour  
 Le tableau ci\-dessous répertorie les codes de retour les plus courants relatifs au programme d'installation redistribuable du .NET Framework. Les codes de retour sont identiques pour toutes les versions du programme d'installation. Pour obtenir des liens vers des informations détaillées, consultez la section suivante.  
  
|Code de retour|Description|  
|--------------------|-----------------|  
|0|Installation terminée.|  
|1602|L'utilisateur a annulé l'installation.|  
|1603|Une erreur irrécupérable s'est produite pendant l'installation.|  
|1641|Un redémarrage est nécessaire pour terminer l'installation. Ce message indique que l'opération a réussi.|  
|3010|Un redémarrage est nécessaire pour terminer l'installation. Ce message indique que l'opération a réussi.|  
|5100|L'ordinateur de l'utilisateur n'a pas la configuration requise.|  
  
#### Codes d'erreur de téléchargement  
 Consultez des articles sur les thèmes suivants dans MSDN Library :  
  
-   [Codes d’erreur du service de transfert intelligent en arrière\-plan \(BITS\)](http://go.microsoft.com/fwlink/?LinkId=180946)  
  
-   [Codes d’erreur du moniker d’URL](http://go.microsoft.com/fwlink/?LinkId=180947)  
  
-   [Codes d’erreur WinHttp](http://go.microsoft.com/fwlink/?LinkId=180948)  
  
#### Autres codes d'erreur  
 Consultez des articles sur les thèmes suivants dans MSDN Library :  
  
-   [Codes d’erreur Windows Installer](http://go.microsoft.com/fwlink/?LinkId=180949)  
  
-   [Codes de résultat de l’agent de mise à jour automatique Windows Update](http://go.microsoft.com/fwlink/?LinkId=180951)  
  
<a name="uninstalling_net_framework"></a>   
## Désinstallation du .NET Framework  
 À compter de [!INCLUDE[win8](../../../includes/win8-md.md)], vous pouvez désinstaller le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], 4.5.1, 4.5.2, 4.6, 4.6.1 ou 4.6.2 en utilisant l’option **Activer ou désactiver des fonctionnalités Windows** du Panneau de configuration. Dans les versions antérieures de Windows, vous pouvez désinstaller le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], 4.5.1, 4.5.2, 4.6, 4.6.1 ou 4.6.2 à l’aide de l’option **Ajout\/Suppression de programmes** du Panneau de configuration.  
  
> [!IMPORTANT]
>  Pour Windows 7 et les systèmes d’exploitation antérieurs, la désinstallation du [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], 4.5.2, 4.6, 4.6.1 ou 4.6.2 ne restaure pas les fichiers du [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], et la désinstallation du [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ne restaure pas les fichiers du [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. Si vous souhaitez revenir à la version antérieure, vous devez la réinstaller et effectuer toutes les mises à jour correspondantes.  
  
## Annexe  
  
<a name="command_line_options"></a>   
### Options de ligne de commande  
 Le tableau ci\-dessous répertorie les options que vous pouvez inclure lorsque vous chaînez le package redistribuable [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] à l'installation de votre application.  
  
|Option|Description|  
|------------|-----------------|  
|**\/CEIPConsent**|Remplace le comportement par défaut et envoie des commentaires anonymes à Microsoft pour améliorer les futurs déploiements. Cette option peut être utilisée uniquement si l'utilisateur accepte d'envoyer des commentaires anonymes à Microsoft lorsqu'il y est invité par le programme d'installation.|  
|**\/chainingpackage** `packageName`|Spécifie le nom du fichier exécutable qui effectue le chaînage. Ces informations sont envoyées à Microsoft sous forme de commentaires anonymes pour améliorer les futurs déploiements.<br /><br /> Si le nom du package inclut des espaces, utilisez des guillemets doubles comme délimiteurs. Par exemple : **\/chainingpackage "Lucerne Publishing"**. Pour obtenir un exemple de package de chaînage, consultez [Obtention d’informations sur la progression d’un package d’installation](http://go.microsoft.com/fwlink/?LinkId=181926) dans MSDN Library.|  
|**\/LCID**  `LCID`<br /><br /> où `LCID` spécifie un identificateur de paramètres régionaux \(consultez la liste des [langues prises en charge](#supported_languages)\)|Installe le module linguistique spécifié par `LCID` et force l'affichage de l'interface utilisateur dans cette langue à moins que le mode silencieux soit défini.<br /><br /> Pour le programme d'installation web, cette option installe de manière chaînée le module linguistique à partir du web. **Note:**  Utilisez cette option uniquement avec le programme d'installation web.|  
|**\/log** `file` &#124; `folder`|Spécifie l'emplacement du fichier journal. L'emplacement par défaut est le répertoire temporaire du processus et le nom par défaut du fichier est basé sur le module. Si l'extension de fichier est .txt, un journal textuel est généré. Si vous spécifiez une autre extension ou aucune extension, un journal HTML est créé.|  
|**\/msioptions**|Spécifie les options à transmettre pour des éléments .msi et .msp ; par exemple : `/msioptions "PROPERTY1='Value'"`.|  
|**\/norestart**|Empêche le programme d'installation de redémarrer automatiquement. Si vous utilisez cette option, l’application de chaînage doit capturer le code de retour et gérer le redémarrage \(consultez [Obtention d’informations sur la progression d’un package d’installation](http://go.microsoft.com/fwlink/?LinkId=179606) dans MSDN Library\).|  
|**\/passive**|Définit le mode passif. Affiche la barre de progression pour indiquer que l'installation est en cours, mais n'affiche aucune invite ni aucun message d'erreur pour l'utilisateur. Dans ce mode, lorsqu'il est chaîné par un programme d'installation, le package de chaînage doit gérer les [codes de retour](#return_codes).|  
|**\/pipe**|Crée un canal de communication pour permettre à un package de chaînage d'obtenir les données de progression.|  
|**\/promptrestart**|Mode passif uniquement, si le programme d'installation requiert un redémarrage, il invite l'utilisateur à redémarrer l'ordinateur. Cette option requiert une intervention de l'utilisateur si un redémarrage est requis.|  
|**\/q**|Définit le mode silencieux.|  
|**\/repair**|Déclenche la fonctionnalité de réparation.|  
|**\/serialdownload**|Force l'installation à démarrer une fois seulement que le package a été téléchargé.|  
|**\/showfinalerror**|Définit le mode passif. Affiche les erreurs uniquement si l'installation échoue. Cette option requiert une intervention de l'utilisateur si l'installation n'a pas réussi.|  
|**\/showrmui**|S’utilise uniquement avec l’option **\/passive**. Affiche un message invitant les utilisateurs à fermer les applications .NET Framework en cours d'exécution. Ce message se comporte de la même manière en mode passif et non passif.|  
|**\/uninstall**|Désinstalle le package redistribuable .NET Framework.|  
  
<a name="supported_languages"></a>   
### Langues prises en charge  
 Le tableau ci\-dessous répertorie les modules linguistiques du .NET Framework disponibles pour [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] et versions intermédiaires.  
  
|LCID|Langue – pays\/région|Culture|  
|----------|---------------------------|-------------|  
|1025|Arabe \- Arabie saoudite|ar|  
|1028|Chinois – Traditionnel|zh\-Hant|  
|1029|Tchèque|cs|  
|1030|Danois|da|  
|1031|Allemand – Allemagne|de|  
|1032|Grec|el|  
|1035|Finnois|fi|  
|1036|Français – France|fr|  
|1037|Hébreu|he|  
|1038|Hongrois|hu|  
|1040|Italien – Italie|it|  
|1041|Japonais|ja|  
|1042|Coréen|ko|  
|1043|Néerlandais – Pays\-Bas|nl|  
|1044|Norvégien \(Bokmål\)|non|  
|1045|Polonais|pl|  
|1046|Portugais – Brésil|pt\-BR|  
|1049|Russe|ru|  
|1053|Suédois|sv|  
|1055|Turc|tr|  
|2052|Chinois – Simplifié|zh\-Hans|  
|2070|Portugais – Portugal|pt\-PT|  
|3082|Espagnol \- Espagne \(moderne\)|es|  
  
## Voir aussi  
 [Guide de déploiement pour les administrateurs](../../../docs/framework/deployment/guide-for-administrators.md)   
 [Configuration requise](../../../docs/framework/get-started/system-requirements.md)   
 [Guide d'installation](../../../docs/framework/install/guide-for-developers.md)   
 [Dépannage](../../../docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)   
 [Reducing System Restarts During .NET Framework 4.5 Installations](../../../docs/framework/deployment/reducing-system-restarts.md)   
 [Comment : obtenir la progression à partir du programme d'installation du .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)