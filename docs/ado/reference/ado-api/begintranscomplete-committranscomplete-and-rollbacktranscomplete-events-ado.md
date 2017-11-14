---
title: Gli eventi di BeginTrans, CommitTrans e RollbackTrans (ADO) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- CommitTransComplete
- Connection::BeginTransComplete
- Connection::RollbackTransComplete
- Connection::CommitTransComplete
- RollbackTransComplete
- BeginTransComplete
helpviewer_keywords:
- CommitTransComplete event [ADO]
- RollbackTransComplete event [ADO]
- BeginTransComplete event [ADO]
ms.assetid: ec4e4b38-e9c6-4757-b2ef-4e468ae5f1d8
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 26062971810fcc46fdcd3ab95c8edc0701784860
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado"></a>BeginTransComplete, CommitTransComplete ed eventi RollbackTransComplete (ADO)
Questi eventi verranno chiamati dopo l'operazione associata sul [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto termina l'esecuzione.  
  
-   **BeginTransComplete** viene chiamato dopo il [BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) operazione.  
  
-   **CommitTransComplete** viene chiamato dopo il [CommitTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) operazione.  
  
-   **RollbackTransComplete** viene chiamato dopo il [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) operazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BeginTransComplete TransactionLevel, pError, adStatus, pConnection  
CommitTransComplete pError, adStatus, pConnection  
RollbackTransComplete pError, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Parametri  
 *TransactionLevel*  
 Oggetto **lungo** valore contenente il nuovo livello di transazione del **BeginTrans** che ha causato l'evento.  
  
 *pError*  
 Un [errore](../../../ado/reference/ado-api/error-object.md) oggetto. Viene descritto l'errore che si è verificato se il valore di EventStatusEnum è **adStatusErrorsOccurred**; in caso contrario non è impostata.  
  
 *adStatus*  
 Un [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) valore di stato. Quando uno di questi eventi viene chiamato, questo parametro è impostato su **adStatusOK** se l'operazione che ha causato l'evento ha esito positivo o a **adStatusErrorsOccurred** se l'operazione non riuscita.  
  
 Questi eventi possono impedire notifiche successive impostando questo parametro su **adStatusUnwantedEvent** prima della restituzione dell'evento.  
  
 *pConnection*  
 Il **connessione** dell'oggetto per cui si è verificato l'evento.  
  
## <a name="remarks"></a>Osservazioni  
 In Visual C++, più **connessioni** possono condividere lo stesso evento con metodo di gestione. Il metodo utilizza l'oggetto restituito **connessione** oggetto per determinare quale oggetto ha causato l'evento.  
  
 Se il [attributi](../../../ado/reference/ado-api/attributes-property-ado.md) è impostata su **adXactCommitRetaining** o **adXactAbortRetaining**, viene avviata una nuova transazione dopo il commit o il rollback di una transazione. Utilizzare il **BeginTransComplete** evento per ignorare tutti, ma il primo evento di inizio transazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di modello di eventi ADO (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [BeginTrans, CommitTrans e RollbackTrans metodi esempio (VB)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-example-vb.md)   
 [Riepilogo dei gestori di eventi ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [BeginTrans, CommitTrans e RollbackTrans metodi (ADO)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)

