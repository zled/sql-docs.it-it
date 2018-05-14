---
title: Elemento BeginSession (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: aace4a6f0f8bfbf1cf41853224b98b0dd09fa26a
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="beginsession-element-xmla"></a>Elemento BeginSession (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Utilizza un'intestazione SOAP in un messaggio di richiesta SOAP per avviare una nuova sessione in un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 **Namespace** urn:schemas-microsoft-com:xml-analysis  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
   <soap:Header>  
      ...  
      <BeginSession  
         xmlns="urn:schemas-microsoft-com:xml-analysis" />  
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
  
## <a name="remarks"></a>Osservazioni  
 Il **BeginSession** elemento intestazione fa parte di una richiesta SOAP inviata a un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza e, in modo esplicito, consente di avviare una nuova sessione nell'istanza. L'intestazione SOAP restituita dalla risposta SOAP contiene un [sessione](../../../analysis-services/xmla/xml-elements-headers/session-element-xmla.md) elemento che identifica la nuova sessione. Questo nuovo ID di sessione verrà archiviato e inviato nelle richieste SOAP successive utilizzando il **sessione** elemento intestazione.  
  
 Se il **BeginSession** elemento intestazione non viene inviato, una sessione non è stata avviata in modo esplicito. Se una sessione non viene avviata in modo esplicito, non sarà possibile gestire le transazioni nella sessione. In altre parole, è possibile utilizzare il seguente codice XML per i comandi Analysis (XMLA): [BeginTransaction](../../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md), [CommitTransaction](../../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md), e [RollbackTransaction](../../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md). Tutti i metodi e i comandi XMLA eseguiti in una sessione avviata in modo implicito vengono considerati transazioni atomiche.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento EndSession & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-headers/endsession-element-xmla.md)   
 [Elemento Session & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-headers/session-element-xmla.md)   
 [La gestione delle connessioni e sessioni & #40; XMLA & #41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Intestazioni & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  
