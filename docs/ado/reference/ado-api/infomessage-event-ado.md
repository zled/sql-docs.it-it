---
title: Evento InfoMessage (ADO) | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Connection::InfoMessage
- InfoMessage
helpviewer_keywords:
- InfoMessage event [ADO]
ms.assetid: 468c87dd-e3bc-4084-9941-94d10743d4e9
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7f1e479b4dfb5b9cb557030e03afeac3f6278720
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="infomessage-event-ado"></a>Evento InfoMessage (ADO)
Il **InfoMessage** eventi viene chiamato ogni volta che viene generato un avviso durante un **ConnectionEvent** operazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
InfoMessage pError, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Parametri  
 *pError*  
 Un [errore](../../../ado/reference/ado-api/error-object.md) oggetto. Questo parametro contiene gli eventuali errori restituiti. Se vengono restituiti più errori, enumerare le **errori** insieme per individuarli.  
  
 *adStatus*  
 Un [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) valore di stato. Se viene generato un avviso, *adStatus* è impostato su **adStatusOK** e *pError* contiene l'avviso.  
  
 Prima di questo evento restituisce, impostare questo parametro su **adStatusUnwantedEvent** per impedire notifiche successive.  
  
 *pConnection*  
 Oggetto [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto. La connessione per il quale si è verificato l'avviso. Ad esempio, gli avvisi possono verificarsi quando si apre un **connessione** oggetto o l'esecuzione di un [comando](../../../ado/reference/ado-api/command-object-ado.md) su un **connessione**.  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di modello di eventi ADO (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Riepilogo dei gestori di eventi ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Oggetto di connessione (ADO.NET)](../../../ado/reference/ado-api/connection-object-ado.md)
