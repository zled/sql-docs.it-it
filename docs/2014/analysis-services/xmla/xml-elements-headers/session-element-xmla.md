---
title: Elemento Session (XMLA) | Documenti Microsoft
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
- Session Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.session
- http://schemas.microsoft.com/analysisservices/2003/engine#Session
- urn:schemas-microsoft-com:xml-analysis#Session
helpviewer_keywords:
- Session element
ms.assetid: 884ed090-968e-41d3-97e5-6d12787467da
caps.latest.revision: 15
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 4be4778be16da0271e2f46643a165864d679e8ff
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069255"
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
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|None|  
  
## <a name="attributes"></a>Attributi  
  
|attribute|Description|  
|---------------|-----------------|  
|SessionId|L'attributo `String` obbligatorio che identifica la sessione da utilizzare. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] utilizza un identificatore univoco globale (GUID) per identificare una sessione.|  
  
## <a name="remarks"></a>Remarks  
 L'elemento dell'intestazione `Session` identifica una sessione esistente avviata in modo esplicito nell'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. L'elemento `Session` fa parte dell'intestazione SOAP nei tipi di messaggi seguenti:  
  
-   Una risposta SOAP che contiene un [BeginSession](session-element-xmla.md) dell'elemento intestazione SOAP.  
  
-   Una richiesta SOAP per identificare la sessione in cui eseguire la [Discover](../xml-elements-methods-discover.md) oppure [Execute](../xml-elements-methods-execute.md) metodo.  
  
 Un identificatore di sessione non garantisce che una sessione rimanga valida. La sessione specificata nell'elemento `Session` può scadere. Una sessione può ad esempio scadere in caso di timeout oppure se la connessione associata alla sessione viene disconnessa. Se la sessione scade e non è più valida, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] termina la sessione ed esegue il rollback di qualsiasi transazione in corso. Tutti i messaggi SOAP inviati con un identificatore di sessione non più valido hanno esito negativo e viene generato un errore SOAP che indica che non è possibile trovare la sessione specificata.  
  
 Se un elemento `Session` non viene inviato come parte di una richiesta SOAP, l'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] avvia in modo implicito una sessione per la durata della chiamata al metodo `Discover` o `Execute`, quindi termina la sessione dopo che la chiamata al metodo è stata completata.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento EndSession &#40;XMLA&#41;](endsession-element-xmla.md)   
 [Gestione di connessioni e sessioni di &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Le intestazioni &#40;XMLA&#41;](xml-elements-headers.md)  
  
  