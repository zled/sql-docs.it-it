---
title: Elemento ProtocolCapabilities (XMLA) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ProtocolCapabilities Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.protocolcapabilities
- http://schemas.microsoft.com/analysisservices/2003/engine#ProtocolCapabilities
- urn:schemas-microsoft-com:xml-analysis#ProtocolCapabilities
helpviewer_keywords:
- ProtocolCapabilities element
ms.assetid: f923896a-3f32-46a3-9543-388c30b3465d
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 511cca07c0505db7bd1aaa21bed923498137e04f
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="protocolcapabilities-element-xmla"></a>Elemento ProtocolCapabilities (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Utilizza l'intestazione SOAP in un messaggio di richiesta SOAP per identificare le funzionalità del protocollo tra un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] e un'applicazione client.  
  
 **Namespace**`http://schemas.microsoft.com/analysisservices/2003/engine`  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
   <soap:Header>  
      ...  
      <ProtocolCapabilities xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
         <Capability>...</Capability>  
      </ProtocolCapabilities>  
      ...  
   </soap:Header>  
   <soap:Body>  
      ...  
   </soap:Body>  
</soap:Envelope>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|[Funzionalità](../../../analysis-services/xmla/xml-elements-properties/capability-element-xmla.md)|  
  
## <a name="remarks"></a>Remarks  
 Il **ProtocolCapabilities** elemento consente alle applicazioni client di negoziare funzionalità del protocollo, ad esempio XML binario o supporto della compressione, con un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza in qualsiasi momento. La negoziazione del protocollo comporta i passaggi seguenti:  
  
1.  L'applicazione client identifica la funzionalità del protocollo inviando una richiesta SOAP che include come parte dell'elemento **ProtocolCapabilities** l'intestazione SOAP.  
  
2.  L'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] riceve ed elabora la richiesta SOAP.  
  
3.  Se il [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza ha la stessa funzionalità del protocollo richiesto, l'istanza invia una risposta SOAP che include lo stesso **ProtocolCapabilities** elemento inviato nella richiesta SOAP e il protocollo è stato negoziate correttamente. In caso contrario le funzionalità del protocollo non vengono negoziate correttamente e l'istanza restituisce un errore SOAP.  
  
 Dopo aver negoziato correttamente le funzionalità del protocollo, quanto tempo l'applicazione client e il [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza utilizzano un particolare protocollo dipende dal se la sessione sia esplicita o implicita:  
  
-   Una sessione esplicita è una classe che viene creato utilizzando il [BeginSession](../../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md) elemento intestazione. Per una sessione esplicita viene utilizzato il protocollo negoziato, finché l'applicazione client non invia un elemento **ProtocolCapabilities** nuovo o la sessione termina.  
  
-   Una sessione implicita viene creata da un'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] e non viene specificata in modo esplicito dall'applicazione client in caso di invio di una richiesta SOAP. Per una sessione implicita, il protocollo negoziato viene utilizzato solo fino al completamento della richiesta SOAP.  
  
 Le funzionalità del protocollo non devono essere negoziate in modo esplicito. Ovvero, un'applicazione client non deve includere come parte di un elemento **ProtocolCapabilities** la richiesta SOAP. Se una richiesta SOAP non include un **ProtocolCapabilities** elemento, il [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza risponde utilizzando lo stesso formato della richiesta SOAP.  
  
## <a name="see-also"></a>Vedere anche  
 [La gestione delle connessioni e sessioni &#40; XMLA &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Intestazioni &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  
