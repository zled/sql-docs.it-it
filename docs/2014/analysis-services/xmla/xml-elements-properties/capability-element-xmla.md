---
title: Elemento Capability (XMLA) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Capability Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Capability
- http://schemas.microsoft.com/analysisservices/2003/engine#Capability
- microsoft.xml.analysis.capability
helpviewer_keywords:
- Capability element
ms.assetid: 544a733e-77fc-48a0-8f92-9cd1fdbcf824
caps.latest.revision: 16
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 7fd495ff0abf921b377526f6030d5207d962e1bd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065435"
---
# <a name="capability-element-xmla"></a>Elemento Capability (XMLA)
  Indica il supporto per una funzionalità del protocollo nell'elemento padre [ProtocolCapabilities](../xml-elements-headers/protocolcapabilities-element-xmla.md) elemento dell'intestazione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ProtocolCapabilities>  
   ...  
   <Capability>...</Capability>  
   ...  
</ProtocolCapabilities>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[ProtocolCapabilities](../xml-elements-headers/protocolcapabilities-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Il `Capability` elemento indica che una particolare funzionalità, ad esempio binaria o la compressione, è supportata dall'applicazione che è incluso il `ProtocolCapabilities` elemento dell'intestazione nell'intestazione SOAP della richiesta SOAP o dall'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] inclusi il `ProtocolCapabilities` elemento dell'intestazione nell'intestazione SOAP della risposta SOAP. Il valore dell'elemento `Capability` corrisponde al nome della funzionalità che deve essere supportata.  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] supporta le funzionalità elencate nella tabella seguente.  
  
|Nome della funzionalità|Description|  
|---------------------|-----------------|  
|sx|Supporto di XML binario|  
|xpress|Supporto della compressione|  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione di connessioni e sessioni di &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  