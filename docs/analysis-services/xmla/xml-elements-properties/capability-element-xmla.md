---
title: Elemento Capability (XMLA) | Documenti Microsoft
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
apiname: Capability Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Capability
- http://schemas.microsoft.com/analysisservices/2003/engine#Capability
- microsoft.xml.analysis.capability
helpviewer_keywords: Capability element
ms.assetid: 544a733e-77fc-48a0-8f92-9cd1fdbcf824
caps.latest.revision: "16"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: afaaf31c63854b13ee8928b1790f9011db6dcbf8
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="capability-element-xmla"></a>Elemento Capability (XMLA)
  Indica il supporto per una funzionalità del protocollo nell'elemento padre [ProtocolCapabilities](../../../analysis-services/xmla/xml-elements-headers/protocolcapabilities-element-xmla.md) elemento intestazione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ProtocolCapabilities>  
   ...  
   <Capability>...</Capability>  
   ...  
</ProtocolCapabilities>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[ProtocolCapabilities](../../../analysis-services/xmla/xml-elements-headers/protocolcapabilities-element-xmla.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il **funzionalità** elemento indica che una particolare funzionalità, ad esempio binaria o la compressione, è supportata dall'applicazione che è incluso il **ProtocolCapabilities** elemento intestazione di Intestazione SOAP della richiesta SOAP o dall'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] inclusi il **ProtocolCapabilities** elemento dell'intestazione nell'intestazione SOAP della risposta SOAP. Il valore di **funzionalità** elemento è il nome della funzionalità devono essere supportati.  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] supporta le funzionalità elencate nella tabella seguente.  
  
|Nome della funzionalità|Description|  
|---------------------|-----------------|  
|sx|Supporto di XML binario|  
|xpress|Supporto della compressione|  
  
## <a name="see-also"></a>Vedere anche  
 [La gestione delle connessioni e sessioni &#40; XMLA &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
