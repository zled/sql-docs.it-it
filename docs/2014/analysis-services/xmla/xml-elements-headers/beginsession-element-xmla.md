---
title: Elemento BeginSession (XMLA) | Documenti Microsoft
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
- BeginSession Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#BeginSession
- urn:schemas-microsoft-com:xml-analysis#BeginSession
- microsoft.xml.analysis.beginsession
helpviewer_keywords:
- BeginSession element
ms.assetid: 49873a97-58d7-42a9-ab7f-e045e2856737
caps.latest.revision: 16
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 2982709512433e5a6b87929f3a4efba4f77138b8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067665"
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
  
## <a name="remarks"></a>Remarks  
 L'elemento dell'intestazione `BeginSession` fa parte di una richiesta SOAP inviata a un'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] e avvia in modo esplicito una nuova sessione nell'istanza. L'intestazione SOAP restituita dalla risposta SOAP contiene un [sessione](session-element-xmla.md) elemento che identifica la nuova sessione. Questo identificatore della nuova sessione verrà archiviato e inviato nelle richieste SOAP successive utilizzando l'elemento dell'intestazione `Session`.  
  
 Se l'elemento dell'intestazione `BeginSession` non viene inviato, una sessione non verrà avviata in modo esplicito. Se una sessione non viene avviata in modo esplicito, non sarà possibile gestire le transazioni nella sessione. In altre parole, non è possibile utilizzare il seguente codice XML per i comandi Analysis (XMLA): [BeginTransaction](../xml-elements-commands/begintransaction-element-xmla.md), [CommitTransaction](../xml-elements-commands/committransaction-element-xmla.md), e [RollbackTransaction](../xml-elements-commands/rollbacktransaction-element-xmla.md). Tutti i metodi e i comandi XMLA eseguiti in una sessione avviata in modo implicito vengono considerati transazioni atomiche.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento EndSession &#40;XMLA&#41;](endsession-element-xmla.md)   
 [Elemento di sessione &#40;XMLA&#41;](session-element-xmla.md)   
 [Gestione di connessioni e sessioni di &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Le intestazioni &#40;XMLA&#41;](xml-elements-headers.md)  
  
  