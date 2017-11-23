---
title: Intestazioni (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- XMLA, headers
- SOAP headers [XML for Analysis]
- XML for Analysis, headers
- headers [XML for Analysis]
ms.assetid: 36407b5c-d98d-47e4-8d36-d8896e15a748
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 854d879b85ad5e70c21bd87240215b343aab96e7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="xml-elements---headers"></a>Elementi XML - intestazioni
  Il protocollo XML for Analysis (XMLA) utilizza elementi XML all'interno dell'intestazione SOAP per gestire caratteristiche a livello di protocollo, ad esempio il supporto delle sessioni e la negoziazione di caratteristiche supportate.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 Gli argomenti seguenti descrivono gli elementi intestazione XMLA implementati da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
|Metodo|Description|  
|------------|-----------------|  
|[Elemento BeginSession &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md)|Utilizza un'intestazione SOAP in un messaggio di richiesta SOAP per avviare una nuova sessione in un'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Elemento EndSession &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-headers/endsession-element-xmla.md)|Utilizza l'intestazione SOAP in un messaggio di richiesta SOAP per terminare una sessione esistente in un'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Elemento Session &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-headers/session-element-xmla.md)|Utilizza l'intestazione SOAP in un messaggio di richiesta SOAP per identificare una sessione esplicita esistente in un'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Elemento ProtocolCapabilities &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-headers/protocolcapabilities-element-xmla.md)|Utilizza l'intestazione SOAP in un messaggio di richiesta SOAP per identificare funzionalità del protocollo tra un'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] e un'applicazione client.|  
  
## <a name="see-also"></a>Vedere anche  
 [Gli elementi XML &#40; XMLA &#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [Tipi di dati XML &#40; XMLA &#41;](../../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)   
 [Gli elementi XML &#40; XMLA &#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)  
  
  
