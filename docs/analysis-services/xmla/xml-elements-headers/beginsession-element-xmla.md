---
title: Elemento BeginSession (XMLA) | Documenti Microsoft
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
- BeginSession Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#BeginSession
- urn:schemas-microsoft-com:xml-analysis#BeginSession
- microsoft.xml.analysis.beginsession
helpviewer_keywords:
- BeginSession element
ms.assetid: 49873a97-58d7-42a9-ab7f-e045e2856737
caps.latest.revision: 16
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b3ebacd7677aecf7c953d966e3001cbe8f8f7691
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="beginsession-element-xmla"></a>Elemento BeginSession (XMLA)
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
 [Elemento EndSession &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-headers/endsession-element-xmla.md)   
 [Elemento Session &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-headers/session-element-xmla.md)   
 [La gestione delle connessioni e sessioni &#40; XMLA &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Intestazioni &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  
