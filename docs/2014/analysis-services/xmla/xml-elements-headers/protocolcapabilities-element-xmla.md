---
title: Elemento ProtocolCapabilities (XMLA) | Microsoft Docs
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
- ProtocolCapabilities Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.protocolcapabilities
- http://schemas.microsoft.com/analysisservices/2003/engine#ProtocolCapabilities
- urn:schemas-microsoft-com:xml-analysis#ProtocolCapabilities
helpviewer_keywords:
- ProtocolCapabilities element
ms.assetid: f923896a-3f32-46a3-9543-388c30b3465d
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c4183d90d07a54cf009daec59ca29ca802f2bf67
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37295431"
---
# <a name="protocolcapabilities-element-xmla"></a>Elemento ProtocolCapabilities (XMLA)
  Utilizza l'intestazione SOAP in un messaggio di richiesta SOAP per identificare le funzionalità del protocollo tra un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] e un'applicazione client.  
  
 **Namespace** http://schemas.microsoft.com/analysisservices/2003/engine  
  
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
|Elementi figlio|[Funzionalità](../xml-elements-properties/capability-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 L'elemento `ProtocolCapabilities` consente alle applicazioni client di negoziare funzionalità del protocollo, ad esempio XML binario o supporto della compressione, con un'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] in qualsiasi momento. La negoziazione del protocollo comporta i passaggi seguenti:  
  
1.  L'applicazione client identifica la funzionalità del protocollo inviando una richiesta SOAP che include il `ProtocolCapabilities` elemento come parte dell'intestazione SOAP.  
  
2.  L'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] riceve ed elabora la richiesta SOAP.  
  
3.  Se l'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ha la stessa funzionalità del protocollo richiesto, l'istanza invia una risposta SOAP che include lo stesso elemento `ProtocolCapabilities` inviato nella richiesta SOAP e il protocollo viene negoziato correttamente. In caso contrario le funzionalità del protocollo non vengono negoziate correttamente e l'istanza restituisce un errore SOAP.  
  
 Dopo aver negoziato correttamente le funzionalità del protocollo, quanto tempo l'applicazione client e il [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] utilizzano istanza un particolare protocollo dipende se la sessione sia esplicita o implicita:  
  
-   Una sessione esplicita è quello che viene creato utilizzando il [BeginSession](session-element-xmla.md) elemento dell'intestazione. Per una sessione esplicita, viene utilizzato il protocollo negoziato, finché l'applicazione client invia un nuovo `ProtocolCapabilities` elemento o la sessione termina.  
  
-   Una sessione implicita viene creata da un'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] e non viene specificata in modo esplicito dall'applicazione client in caso di invio di una richiesta SOAP. Per una sessione implicita, il protocollo negoziato viene utilizzato solo fino al completamento della richiesta SOAP.  
  
 Le funzionalità del protocollo non devono essere negoziate in modo esplicito. Vale a dire, un'applicazione client non deve includere un `ProtocolCapabilities` elemento come parte della richiesta SOAP. Se una richiesta SOAP non include un elemento `ProtocolCapabilities`, l'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] risponde utilizzando lo stesso formato della richiesta SOAP.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione di connessioni e sessioni &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Le intestazioni &#40;XMLA&#41;](xml-elements-headers.md)  
  
  
