---
title: "Comment : récupérer l'empreinte numérique d'un certificat"
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], retrieving thumbprint
ms.assetid: da3101aa-78cd-4c34-9652-d1f24777eeab
ms.openlocfilehash: d827c2c5f407c3041a31efbc06fcfed205bef458
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492432"
---
# <a name="how-to-retrieve-the-thumbprint-of-a-certificate"></a>Comment : récupérer l'empreinte numérique d'un certificat
Lorsque vous écrivez une application Windows Communication Foundation (WCF) qui utilise un certificat X.509 pour l’authentification, il est souvent nécessaire de spécifier les revendications incluses dans le certificat. Par exemple, vous devez fournir une revendication d'empreinte numérique lors de l'utilisation de l'énumération <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> dans la méthode <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> . La recherche de la valeur de revendication s'effectue en deux étapes. En premier lieu, ouvrez le composant logiciel enfichable MMC (Microsoft Management Console) pour les certificats. (Consultez [Comment : afficher des certificats à l'aide du composant logiciel enfichable MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).) Ensuite, comme décrit ici, recherchez un certificat approprié et copiez son empreinte numérique (ou d'autres valeurs de revendication).  
  
 Si vous utilisez un certificat pour l'authentification du service, il est important de noter la valeur de la colonne **Délivré à** (la première colonne dans la console). Lors de l'utilisation du protocole SSL (Secure Sockets Layer) comme sécurité de transport, l'un des premiers contrôles effectués consiste à comparer l'URI (Uniform Resource Identifier) d'adresse de base d'un service à la valeur **Délivré à** . Les valeurs doivent correspondre ou le processus d'authentification s'interrompt.  
  
 Vous pouvez également vous servir de l'outil Makecert.exe dans le Kit de développement logiciel (SDK) [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour créer des certificats temporaires à utiliser uniquement lors du développement. Toutefois, par défaut, ce type de certificat n'est pas délivré par une autorité de certification, il est donc inutilisable à des fins de production. Pour plus d’informations, consultez [Comment : créer des certificats temporaires à utiliser pendant le développement](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md).  
  
### <a name="to-retrieve-a-certificates-thumbprint"></a>Pour récupérer l'empreinte numérique d'un certificat  
  
1.  Ouvrez le composant logiciel enfichable MMC (Microsoft Management Console) pour les certificats. (Consultez [Comment : afficher des certificats à l'aide du composant logiciel enfichable MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).)  
  
2.  Dans le volet gauche de la fenêtre **Racine de la console** , cliquez sur **Certificats (ordinateur local)**.  
  
3.  Cliquez sur le dossier **Personnel** pour le développer.  
  
4.  Cliquez sur le dossier **Certificats** pour le développer.  
  
5.  Dans la liste de certificats, notez le titre **Rôles prévus** . Recherchez un certificat qui répertorie **Authentification du client** comme rôle prévu.  
  
6.  Double-cliquez sur le certificat.  
  
7.  Dans la boîte de dialogue **Certificat** , cliquez sur l'onglet **Détails** .  
  
8.  Faites défiler la liste de champs et cliquez sur **Empreinte numérique**.  
  
9. Copiez les caractères hexadécimaux de la zone. Si cette empreinte numérique est utilisée dans le code pour `X509FindType`, supprimez les espaces entre les nombres hexadécimaux. Par exemple, l'empreinte numérique "a9 09 50 2d d8 2a e4 14 33 e6 f8 38 86 b0 0d 42 77 a3 2a 7b" doit être spécifiée sous la forme "a909502dd82ae41433e6f83886b00d4277a32a7b" dans le code.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>  
 [Guide pratique pour configurer un port avec un certificat SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [Guide pratique pour afficher des certificats à l’aide du composant logiciel enfichable MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [Guide pratique pour créer des certificats temporaires à utiliser au cours du développement](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
