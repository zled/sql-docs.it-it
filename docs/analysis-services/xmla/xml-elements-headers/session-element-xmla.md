---
title: Elemento Session (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Session Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.session
- http://schemas.microsoft.com/analysisservices/2003/engine#Session
- urn:schemas-microsoft-com:xml-analysis#Session
helpviewer_keywords:
- Session element
ms.assetid: 884ed090-968e-41d3-97e5-6d12787467da
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: aa1f136ee02b73ab792dae7ee7730a3917dace66
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="session-element-xmla"></a>Elemento Session (XMLA)
  Utilizza l'intestazione SOAP in un messaggio di richiesta SOAP per identificare una sessione esplicita esistente in un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 **Namespace** urn:schemas-microsoft-com:xml-analysis  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
   <soap:Header>  
      ...  
      <Session  
         xmlns="urn:schemas-microsoft-com:xml-analysis"  
         SessionId="string" />  
      ...  
   </soap:Header>  
   <soap:Body>  
      ...  
   </soap:Body>  
</soap:Envelope>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|Nessuno|  
|Elementi figlio|Nessuno|  
  
## <a name="attributes"></a>Attributi  
  
|Attribute|Description|  
|---------------|-----------------|  
|SessionId|Richiesto **stringa** attributo che identifica la sessione da utilizzare. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] utilizza un identificatore univoco globale (GUID) per identificare una sessione.|  
  
## <a name="remarks"></a>Osservazioni  
 Il **sessione** elemento intestazione identifica una sessione esistente avviata in modo esplicito nel [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza. Il **sessione** elemento fa parte dell'intestazione SOAP in tipi di messaggi seguenti:  
  
-   Una risposta SOAP che contiene un [BeginSession](../../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md) elemento dell'intestazione SOAP.  
  
-   Una richiesta SOAP per identificare la sessione in cui eseguire il [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) o [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) metodo.  
  
 Un identificatore di sessione non garantisce che una sessione rimanga valida. La sessione specificata nel **sessione** elemento può scadere. Una sessione può ad esempio scadere in caso di timeout oppure se la connessione associata alla sessione viene disconnessa. Se la sessione scade e non è più valida, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] termina la sessione ed esegue il rollback di qualsiasi transazione in corso. Tutti i messaggi SOAP inviati con un identificatore di sessione non più valido hanno esito negativo e viene generato un errore SOAP che indica che non è possibile trovare la sessione specificata.  
  
 Se un **sessione** elemento non viene inviato come parte di una richiesta SOAP, il [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza inizia in modo implicito una sessione per la durata del **Discover** o **Execute** chiamata al metodo e quindi termina la sessione una volta completata la chiamata al metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento EndSession &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-headers/endsession-element-xmla.md)   
 [La gestione delle connessioni e sessioni &#40; XMLA &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Intestazioni &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  

