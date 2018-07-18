---
title: Elemento ProtocolCapabilities (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 85ddeb22fac03e5ae7f66521ac3ca8a46e210fe7
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38021196"
---
# <a name="protocolcapabilities-element-xmla"></a>Elemento ProtocolCapabilities (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Utilizza l'intestazione SOAP in un messaggio di richiesta SOAP per identificare le funzionalità del protocollo tra un'istanza di Analysis Services e un'applicazione client.  
  
 **Namespace** `http://schemas.microsoft.com/analysisservices/2003/engine`  
  
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
  
## <a name="element-characteristics"></a>Caratteristiche di elementi  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Elementi-relazioni  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|[Funzionalità](../../../analysis-services/xmla/xml-elements-properties/capability-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Il **ProtocolCapabilities** elemento consente alle applicazioni client di negoziare funzionalità del protocollo, ad esempio XML binario o supporto della compressione, con un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza in qualsiasi momento. La negoziazione del protocollo comporta i passaggi seguenti:  
  
1.  L'applicazione client identifica la funzionalità del protocollo inviando una richiesta SOAP che include come parte dell'elemento **ProtocolCapabilities** l'intestazione SOAP.  
  
2.  L'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] riceve ed elabora la richiesta SOAP.  
  
3.  Se il [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza ha la stessa funzionalità del protocollo richiesto, l'istanza invia una risposta SOAP che include lo stesso **ProtocolCapabilities** inviato nella richiesta SOAP e il protocollo è stato negoziato correttamente. In caso contrario le funzionalità del protocollo non vengono negoziate correttamente e l'istanza restituisce un errore SOAP.  
  
 Dopo aver negoziato correttamente le funzionalità del protocollo, quanto tempo l'applicazione client e il [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] utilizzano istanza un particolare protocollo dipende se la sessione sia esplicita o implicita:  
  
-   Una sessione esplicita è quello che viene creato utilizzando il [BeginSession](../../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md) elemento dell'intestazione. Per una sessione esplicita viene utilizzato il protocollo negoziato, finché l'applicazione client non invia un elemento **ProtocolCapabilities** nuovo o la sessione termina.  
  
-   Una sessione implicita viene creata da un'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] e non viene specificata in modo esplicito dall'applicazione client in caso di invio di una richiesta SOAP. Per una sessione implicita, il protocollo negoziato viene utilizzato solo fino al completamento della richiesta SOAP.  
  
 Le funzionalità del protocollo non devono essere negoziate in modo esplicito. Ovvero, un'applicazione client non deve includere come parte di un elemento **ProtocolCapabilities** la richiesta SOAP. Se una richiesta SOAP non include un' **ProtocolCapabilities** elemento, il [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza risponde utilizzando lo stesso formato della richiesta SOAP.  
  
## <a name="see-also"></a>Vedere anche
 [Gestione di connessioni e sessioni &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Le intestazioni &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  
