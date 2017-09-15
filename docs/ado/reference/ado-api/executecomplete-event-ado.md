---
title: Evento ExecuteComplete (ADO) | Documenti Microsoft
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
- Connection::ExecuteComplete
- ExecuteComplete
helpviewer_keywords:
- ExecuteComplete event [ADO]
ms.assetid: 62470d42-e511-494c-bec4-ad4591734b7b
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e612e83e3c550c429b9ebcfe63c0641b61390b95
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="executecomplete-event-ado"></a>Evento ExecuteComplete (ADO)
Il **ExecuteComplete** eventi viene chiamato dopo che un comando ha terminato l'esecuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
ExecuteComplete RecordsAffected, pError, adStatus, pCommand, pRecordset, pConnection  
```  
  
#### <a name="parameters"></a>Parametri  
 *RecordsAffected*  
 Oggetto **lungo** valore che indica il numero di record interessati dal comando.  
  
 *pError*  
 Un [errore](../../../ado/reference/ado-api/error-object.md) oggetto. Viene descritto l'errore che si è verificato se il valore di **adStatus** è **adStatusErrorsOccurred**; in caso contrario non è impostata.  
  
 *adStatus*  
 Un [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) valore di stato. Quando questo evento viene chiamato, questo parametro è impostato su **adStatusOK** se l'operazione che ha causato l'evento ha esito positivo o a **adStatusErrorsOccurred** se l'operazione non riuscita.  
  
 Prima di questo evento restituisce, impostare questo parametro su **adStatusUnwantedEvent** per impedire notifiche successive.  
  
 *pCommand*  
 Il [comando](../../../ado/reference/ado-api/command-object-ado.md) oggetto su cui è stato eseguito. Contiene un **comando** anche quando la chiamata dell'oggetto **Connection** o **Open** senza creare esplicitamente un **comando** , in quali casi la **comando** oggetto viene creato internamente da ADO.  
  
 *pRecordset*  
 Oggetto [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto che rappresenta il risultato del comando eseguito. Questo **Recordset** può essere vuoto. Non distruggere mai questo oggetto Recordset all'interno di questo gestore eventi. Questa operazione comporterà una violazione di accesso quando ADO tenta di accedere a un oggetto che non esiste più.  
  
 *pConnection*  
 Oggetto [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto. La connessione su cui è stato eseguito l'operazione.  
  
## <a name="remarks"></a>Osservazioni  
 Un **ExecuteComplete** evento può verificarsi a causa di **connessione.** [Eseguire](../../../ado/reference/ado-api/execute-method-ado-connection.md), **comando.** [Eseguire](../../../ado/reference/ado-api/execute-method-ado-command.md), **Recordset.** [Aprire](../../../ado/reference/ado-api/open-method-ado-recordset.md), **Recordset.** [Requery](../../../ado/reference/ado-api/requery-method.md), o **Recordset.** [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md) metodi.  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di modello di eventi ADO (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Riepilogo dei gestori di eventi ADO](../../../ado/guide/data/ado-event-handler-summary.md)
