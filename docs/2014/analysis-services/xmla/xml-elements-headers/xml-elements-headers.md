---
title: Intestazioni (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
topic_type:
- apiref
- apinav
helpviewer_keywords:
- XMLA, headers
- SOAP headers [XML for Analysis]
- XML for Analysis, headers
- headers [XML for Analysis]
ms.assetid: 36407b5c-d98d-47e4-8d36-d8896e15a748
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fdc6c9ebfef18b108c31870c5703cac3841cfc29
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48155696"
---
# <a name="headers-xmla"></a>Intestazioni (XMLA)
  Il protocollo XML for Analysis (XMLA) utilizza elementi XML all'interno dell'intestazione SOAP per gestire caratteristiche a livello di protocollo, ad esempio il supporto delle sessioni e la negoziazione di caratteristiche supportate.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 Gli argomenti seguenti descrivono gli elementi intestazione XMLA implementati da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
|Metodo|Description|  
|------------|-----------------|  
|[Elemento BeginSession &#40;XMLA&#41;](session-element-xmla.md)|Utilizza un'intestazione SOAP in un messaggio di richiesta SOAP per avviare una nuova sessione in un'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Elemento EndSession &#40;XMLA&#41;](endsession-element-xmla.md)|Utilizza l'intestazione SOAP in un messaggio di richiesta SOAP per terminare una sessione esistente in un'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Elemento Session &#40;XMLA&#41;](session-element-xmla.md)|Utilizza l'intestazione SOAP in un messaggio di richiesta SOAP per identificare una sessione esplicita esistente in un'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Elemento ProtocolCapabilities &#40;XMLA&#41;](protocolcapabilities-element-xmla.md)|Utilizza l'intestazione SOAP in un messaggio di richiesta SOAP per identificare funzionalità del protocollo tra un'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] e un'applicazione client.|  
  
## <a name="see-also"></a>Vedere anche  
 [Elementi XML &#40;XMLA&#41;](../../dev-guide/xml-elements-xmla.md)   
 [Tipi di dati XML &#40;XMLA&#41;](../xml-data-types/xml-data-types-xmla.md)   
 [Elementi XML &#40;XMLA&#41;](../../dev-guide/xml-elements-xmla.md)  
  
  
