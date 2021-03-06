---
title: '&lt;ajouter&gt; , élément pour bypasslist (paramètres réseau)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <bypasslist>, add element
- bypasslist, add element
- <add> element, bypasslist
- add element, bypasslist
ms.assetid: a0b86e28-86b4-4497-abe8-d5fd614c7926
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d786d4fd7e6663649408b36fb518db06063ef916
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754517"
---
# <a name="ltaddgt-element-for-bypasslist-network-settings"></a>&lt;ajouter&gt; , élément pour bypasslist (paramètres réseau)
Ajoute une adresse IP ou le nom DNS à la liste de contournement du proxy.  
  
 \<configuration>  
\<system.net>  
\<defaultProxy >  
\<BypassList >  
\<add>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<add   
  address="regular expression"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|**Attribut**|**Description**|  
|-------------------|---------------------|  
|**address**|Une expression régulière décrivant une adresse IP ou un nom DNS.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[BypassList](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|Fournit un ensemble d’expressions régulières décrivant les adresses qui n’utilisent pas un proxy.|  
  
## <a name="remarks"></a>Notes  
 Le `add` élément insère des expressions régulières décrivant les adresses IP ou des noms de serveur DNS à la liste des adresses qui contournent un serveur proxy.  
  
 La valeur de la `address` attribut doit être une expression régulière qui décrit un ensemble d’adresses IP ou des noms d’hôte.  
  
 Soyez prudent lorsque vous spécifiez une expression régulière pour cet élément. L’expression régulière « [a-z] +\\.contoso\\.com » correspond à tout hôte dans le domaine contoso.com, mais elle correspond également à n’importe quel hôte dans le domaine contoso.com.cpandl.com. Pour faire correspondre uniquement sur un ordinateur hôte dans le domaine contoso.com, utilisez une ancre (« $») : « [a-z] +\\.contoso\\.com$ ».  
  
 Pour plus d’informations sur les expressions régulières, consultez. [Expressions régulières .NET framework](../../../../../docs/standard/base-types/regular-expressions.md).  
  
## <a name="configuration-files"></a>Fichiers de configuration  
 Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant ajoute deux adresses à la liste d’exclusion. La première contourne le proxy pour tous les serveurs dans le domaine contoso.com ; la deuxième contourne le proxy pour tous les serveurs dont l’adresse IP commence par 192.168.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
