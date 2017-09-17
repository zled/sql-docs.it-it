---
title: Evento WillConnect (ADO) | Documenti Microsoft
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
- WillConnect
- Connection::WillConnect
helpviewer_keywords:
- WillConnect event [ADO]
ms.assetid: da561d58-eb58-446c-a4fd-1838c76073c0
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fa5a610913124e1e21a228622cd7eb7a088be9df
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="willconnect-event-ado"></a>Evento WillConnect (ADO)
Il **WillConnect** eventi vengano chiamato prima dell'avvio di una connessione.  
  
 **Si applica a:** [oggetto di connessione (ADO.NET)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
WillConnect ConnectionString, UserID, Password, Options, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Parametri  
 *ConnectionString*  
 Oggetto **stringa** che contiene informazioni di connessione per la connessione in sospeso.  
  
 *ID utente*  
 Oggetto **stringa** che contiene un nome utente per la connessione in sospeso.  
  
 *Password*  
 Oggetto **stringa** che contiene una password per la connessione in sospeso.  
  
 *Opzioni*  
 Oggetto **lungo** valore che indica la modalità con cui il provider deve valutare il *ConnectionString*. L'unica possibilità è **adAsyncOpen**.  
  
 *adStatus*  
 Un [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) valore di stato.  
  
 Quando questo evento viene chiamato, questo parametro è impostato su **adStatusOK** per impostazione predefinita. È impostato su **adStatusCantDeny** se l'evento non è possibile richiedere l'annullamento dell'operazione in sospeso.  
  
 Prima di questo evento restituisce, impostare questo parametro su **adStatusUnwantedEvent** per impedire notifiche successive. Impostare questo parametro su **adStatusCancel** per richiedere l'operazione di connessione che ha causato l'annullamento di questa notifica.  
  
 *pConnection*  
 Il [connessione](../../../ado/reference/ado-api/connection-object-ado.md) dell'oggetto per cui si applica questa notifica dell'evento. Modifiche ai parametri del **connessione** dal **WillConnect** gestore dell'evento non avrà alcun effetto **connessione**.  
  
## <a name="remarks"></a>Osservazioni  
 Quando **WillConnect** viene chiamato, il *ConnectionString*, *UserID*, *Password*, e *opzioni* i parametri sono impostati sui valori definiti dall'operazione che ha causato l'evento (la connessione in sospeso) e può essere modificato prima della restituzione dell'evento. **WillConnect** può restituire una richiesta di annullamento che la connessione in sospeso.  
  
 Quando questo evento viene annullato, **ConnectComplete** verrà chiamato con il relativo *adStatus* parametro impostato su **adStatusErrorsOccurred**.  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di modello di eventi ADO (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Riepilogo dei gestori di eventi ADO](../../../ado/guide/data/ado-event-handler-summary.md)
