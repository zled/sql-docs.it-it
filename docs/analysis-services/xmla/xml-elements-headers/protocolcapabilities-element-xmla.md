---
title: Elemento ProtocolCapabilities (XMLA) | Documenti Microsoft
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
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34574783"
---
# <a name="protocolcapabilities-element-xmla"></a>Elemento ProtocolCapabilities (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Utilizza l'intestazione SOAP in un messaggio di richiesta SOAP per identificare le funzionalità del protocollo tra un'istanza di Analysis Services e un'applicazione client.  
  
 **spazio dei nomi** `http://schemas.microsoft.com/analysisservices/2003/engine`  
  
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
 [Gestione di connessioni e sessioni di &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Le intestazioni &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  
