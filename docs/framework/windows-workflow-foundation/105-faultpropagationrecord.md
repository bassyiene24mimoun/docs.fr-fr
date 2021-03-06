---
title: 105 - FaultPropagationRecord
ms.date: 03/30/2017
ms.assetid: 168473b1-b1e5-4e9f-8a2a-35bbdb2ef531
ms.openlocfilehash: c48f42a91ad9a15b49aad8c1ab684f2348954174
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514506"
---
# <a name="105---faultpropagationrecord"></a>105 - FaultPropagationRecord
## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|Id|105|  
|Mots clés|EndToEndMonitoring, Dépannage, HealthMonitoring, WFTracking|  
|Niveau|Avertissement|  
|Canal|Microsoft-Windows-Application Server-Applications/Analyse|  
  
## <a name="description"></a>Description  
 Le participant au suivi ETW émet cet événement lorsqu'une activité dans l'instance de workflow émet FaultPropagationRecord.  
  
## <a name="message"></a>Message  
 TrackRecord = FaultPropagationRecord, InstanceID=%1, RecordNumber=%2, EventTime=%3, FaultSourceActivityName=%4, FaultSourceActivityId=%5, FaultSourceActivityInstanceId=%6, FaultSourceActivityTypeName=%7, FaultHandlerActivityName=%8, FaultHandlerActivityId = %9, FaultHandlerActivityInstanceId =%10, FaultHandlerActivityTypeName=%11, Fault=%12, IsFaultSource=%13, Annotations=%14, ProfileName = %15  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|ID d'instance pour le workflow|  
|RecordNumber|xs:long|Numéro de séquence de l'enregistrement émis.|  
|EventTime|xs:dateTime|Heure au format UTC à laquelle l'événement a été émis|  
|FaultSourceActivityName|xs:string|Nom de l'activité qui a émis l'erreur|  
|FaultSourceActivityId|xs:string|ID de l'activité qui a émis l'erreur|  
|FaultSourceActivityInstanceId|xs:string|ID d'instance de l'activité qui a émis l'erreur|  
|FaultSourceActivityTypeName|xs:string|Type de l'activité qui a émis l'erreur|  
|FaultHandlerActivityName|xs:string|Nom complet de l'activité de gestionnaire d'erreur|  
|FaultHandlerActivityId|xs:string|ID de l'activité de gestionnaire d'erreur|  
|FaultHandlerActivityInstanceId|xs:string|ID d'instance de l'activité de gestionnaire d'erreur|  
|FaultHandlerActivityTypeName|xs:string|Type de l'activité de gestionnaire d'erreur|  
|Fault|xs:string|Détails d'erreur|  
|IsFaultSource|xs:unsignedByte|Indique si l'événement a été émis depuis la source ayant généré l'erreur|  
|Annotations|xs:string|Annotations ayant été ajoutées à cet événement.  Les valeurs sont stockées dans un élément xml au format \<éléments >\< nom d’élément = « annotationName » type = « > annotationValue\</élément > \< /éléments >.  Si aucune annotation n’est spécifiée, la chaîne contient \<éléments / >. La taille d'événement ETW est limitée par la taille de la mémoire tampon ETW ou par la charge utile maximale pour un événement ETW. Si la taille de l’événement dépasse les limites ETW, l’événement est tronqué en supprimant les annotations et en remplaçant la valeur de l’annotation avec \<éléments >... \</Items >.|  
|ProfileName|xs:string|Nom ou modèle de suivi qui a provoqué l'émission de cet événement|  
|HostReference|xs:string|Pour les services hébergés sur le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.  Son format est défini en tant que ' chemin d’accès virtuel de Site Web nom Application&#124;chemin d’accès virtuel du Service&#124;ServiceName' exemple : ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService »|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
