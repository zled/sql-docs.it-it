---
title: Elemento Session (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 02b4c93919e6354a59aad9b42a4f6dc8373c880f
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34577503"
---
# <a name="session-element-xmla"></a>Elemento Session (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Utilizza l'intestazione SOAP in un messaggio di richiesta SOAP per identificare una sessione esplicita esistente in un'istanza di Analysis Services.  
  
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
|SessionId|Richiesto **stringa** attributo che identifica la sessione da utilizzare. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] utilizza un identificatore univoco globale (GUID) per identificare una sessione.|  
  
## <a name="remarks"></a>Remarks  
 Il **sessione** elemento intestazione identifica una sessione esistente avviata in modo esplicito nel [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza. Il **sessione** elemento fa parte dell'intestazione SOAP in tipi di messaggi seguenti:  
  
-   Una risposta SOAP che contiene un [BeginSession](../../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md) elemento dell'intestazione SOAP.  
  
-   Una richiesta SOAP per identificare la sessione in cui eseguire il [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) o [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) metodo.  
  
 Un identificatore di sessione non garantisce che una sessione rimanga valida. La sessione specificata nel **sessione** elemento può scadere. Una sessione può ad esempio scadere in caso di timeout oppure se la connessione associata alla sessione viene disconnessa. Se la sessione scade e non è più valida, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] termina la sessione ed esegue il rollback di qualsiasi transazione in corso. Tutti i messaggi SOAP inviati con un identificatore di sessione non più valido hanno esito negativo e viene generato un errore SOAP che indica che non è possibile trovare la sessione specificata.  
  
 Se un **sessione** elemento non viene inviato come parte di una richiesta SOAP, il [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza inizia in modo implicito una sessione per la durata del **Discover** o **Execute** chiamata al metodo e quindi termina la sessione una volta completata la chiamata al metodo.  
  
## <a name="see-also"></a>Vedere anche
 [Elemento EndSession &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-headers/endsession-element-xmla.md)   
 [Gestione di connessioni e sessioni di &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Le intestazioni &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  
