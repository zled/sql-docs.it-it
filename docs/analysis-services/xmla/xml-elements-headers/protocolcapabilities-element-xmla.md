---
title: Elemento ProtocolCapabilities (XMLA) | Documenti Microsoft
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
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5d2ff72b1fdc3a3e3a4b09a046933d3ead88fc78
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# Elemento ProtocolCapabilities (XMLA)
  Utilizza l'intestazione SOAP in un messaggio di richiesta SOAP per identificare le funzionalità del protocollo tra un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] e un'applicazione client.  
  
 **Namespace**`http://schemas.microsoft.com/analysisservices/2003/engine`  
  
## Sintassi  
  
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
  
## Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|Nessuno|  
|Elementi figlio|[Funzionalità](../../../analysis-services/xmla/xml-elements-properties/capability-element-xmla.md)|  
  
## Osservazioni  
 Il **ProtocolCapabilities** elemento consente alle applicazioni client di negoziare funzionalità del protocollo, ad esempio XML binario o supporto della compressione, con un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza in qualsiasi momento. La negoziazione del protocollo comporta i passaggi seguenti:  
  
1.  L'applicazione client identifica la funzionalità del protocollo inviando una richiesta SOAP che include come parte dell'elemento **ProtocolCapabilities** l'intestazione SOAP.  
  
2.  L'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] riceve ed elabora la richiesta SOAP.  
  
3.  Se il [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza ha la stessa funzionalità del protocollo richiesto, l'istanza invia una risposta SOAP che include lo stesso **ProtocolCapabilities** elemento inviato nella richiesta SOAP e il protocollo è stato negoziate correttamente. In caso contrario le funzionalità del protocollo non vengono negoziate correttamente e l'istanza restituisce un errore SOAP.  
  
 Dopo aver negoziato correttamente le funzionalità del protocollo, quanto tempo l'applicazione client e il [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza utilizzano un particolare protocollo dipende dal se la sessione sia esplicita o implicita:  
  
-   Una sessione esplicita è una classe che viene creato utilizzando il [BeginSession](../../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md) elemento intestazione. Per una sessione esplicita viene utilizzato il protocollo negoziato, finché l'applicazione client non invia un elemento **ProtocolCapabilities** nuovo o la sessione termina.  
  
-   Una sessione implicita viene creata da un'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] e non viene specificata in modo esplicito dall'applicazione client in caso di invio di una richiesta SOAP. Per una sessione implicita, il protocollo negoziato viene utilizzato solo fino al completamento della richiesta SOAP.  
  
 Le funzionalità del protocollo non devono essere negoziate in modo esplicito. Ovvero, un'applicazione client non deve includere come parte di un elemento **ProtocolCapabilities** la richiesta SOAP. Se una richiesta SOAP non include un **ProtocolCapabilities** elemento, il [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza risponde utilizzando lo stesso formato della richiesta SOAP.  
  
## Vedere anche  
 [La gestione delle connessioni e sessioni &#40; XMLA &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Intestazioni &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  

