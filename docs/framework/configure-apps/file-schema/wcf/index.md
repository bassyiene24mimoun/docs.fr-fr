---
title: Schéma de configuration WCF
ms.date: 03/30/2017
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
ms.openlocfilehash: bcbc12d35dae59fcd43d5fbf2d4c936c8e4a4423
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357026"
---
# <a name="wcf-configuration-schema"></a>Schéma de configuration WCF
Éléments de configuration Windows Communication Foundation (WCF) permettent de configurer les applications clientes et de service WCF. Vous pouvez utiliser l’[outil Éditeur de configuration (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) pour créer et modifier des fichiers de configuration pour les clients et les services. Les fichiers de configuration étant au format XML, il est nécessaire de maîtriser ce format pour pouvoir modifier ces fichiers à l'aide d'un éditeur de texte, sans quoi vous risquez de rencontrer des problèmes tels qu'une balise ou un attribut d'élément XML manquant. Ce problème a lieu car les étiquettes et les attributs d’éléments XML respectent la casse.  
  
 Le système de configuration WCF est basé sur le <xref:System.Configuration> espace de noms. Par conséquent, vous pouvez utiliser tous les dispositifs standard fournis par l'espace de noms <xref:System.Configuration>, tel que le verrouillage, le chiffrement et la fusion de la configuration, afin de renforcer la sécurité de votre application et sa configuration. Pour plus d'informations sur ces concepts, consultez les rubriques suivantes :  
  
 [Chiffrement des informations de configuration](http://go.microsoft.com/fwlink/?LinkId=95337)  
  
 [Verrouillage des paramètres de configuration](http://go.microsoft.com/fwlink/?LinkId=95338)  
  
 Cette section décrit toutes les valeurs possibles de chaque élément de configuration et leur interaction avec d'autres éléments de configuration WCF. Le plan suivant illustre le schéma de configuration WCF.  
  
 ![Schéma de configuration WCF](../../../../../docs/framework/configure-apps/file-schema/wcf/media/orcasconfigschema.gif "OrcasConfigSchema")  
  
> [!CAUTION]
>  Vous devez protéger les sections de configuration WCF dans vos fichiers de configuration d’application (app.config) avec approprié contrôle listes accès (ACL) pour empêcher les menaces de sécurité potentielles.  Par exemple, vous devez vous assurer que seules les personnes appropriées peuvent accéder ou modifier les paramètres de sécurité relatifs aux liaisons d’application ou la section relative au modèle de service figurant dans le fichier de configuration d’un service.  
  
## <a name="in-this-section"></a>Dans cette section  
 [\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
 Décrit l'élément `ServiceModel`.  
  
 [\<system.serviceModel.activation>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)  
 Configure l'outil SMSvcHost.exe.  
  
 [\<system.runtime.serialization>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
 Élément de niveau supérieur permettant de définir les options lors de l'utilisation de sérialiseurs tels que le <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Configuration des applications Windows Communication Foundation](http://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 Décrit comment configurer les clients et les services WCF.
