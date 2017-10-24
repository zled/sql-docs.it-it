---
title: Cancel (metodo) (ADO) | Documenti Microsoft
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
- Recordset20::Cancel
- _Record::Cancel
- _Connection::Cancel
- Command25::Cancel
- _Stream::Cancel
helpviewer_keywords:
- Cancel method [ADO]
ms.assetid: e0db4e15-6787-41e2-8f13-9e9b524d620a
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ba15f12006b31fa8ce0f67fd14ef7c6afb46863b
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="cancel-method-ado"></a>Cancel (metodo) (ADO)
Annulla l'esecuzione di una chiamata al metodo asincrono in sospeso.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.Cancel  
```  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **Annulla** metodo per terminare l'esecuzione di una chiamata al metodo asincrono:, ovvero richiamato un metodo con il **adAsyncConnect**, **adAsyncExecute**, o **adAsyncFetch** opzione.  
  
 La tabella seguente mostra quali attività è terminata quando si utilizza il **Annulla** metodo su un particolare tipo di oggetto.  
  
|Se *oggetto* è un|L'ultima chiamata asincrona a questo metodo viene terminata|  
|----------------------|-------------------------------------------------------------|  
|[Command](../../../ado/reference/ado-api/command-object-ado.md)|[Eseguire](../../../ado/reference/ado-api/execute-method-ado-command.md)|  
|[Connessione](../../../ado/reference/ado-api/connection-object-ado.md)|[Eseguire](../../../ado/reference/ado-api/execute-method-ado-connection.md) o [aperto](../../../ado/reference/ado-api/open-method-ado-connection.md)|  
|[Record](../../../ado/reference/ado-api/record-object-ado.md)|[CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md), [DeleteRecord](../../../ado/reference/ado-api/deleterecord-method-ado.md), [MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md), o [aperto](../../../ado/reference/ado-api/open-method-ado-record.md)|  
|[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)|[Aprire](../../../ado/reference/ado-api/open-method-ado-recordset.md)|  
|[Flusso](../../../ado/reference/ado-api/stream-object-ado.md)|[Aprire](../../../ado/reference/ado-api/open-method-ado-stream.md)|  
  
## <a name="applies-to"></a>Si applica a  
  
||||  
|-|-|-|  
|[Oggetto Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Oggetto di connessione (ADO.NET)](../../../ado/reference/ado-api/connection-object-ado.md)|[Oggetto di record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|  
|[Oggetto Recordset ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[Oggetto di flusso (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)||  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio del metodo Cancel (VB)](../../../ado/reference/ado-api/cancel-method-example-vb.md)   
 [Esempio del metodo Cancel (VBScript)](../../../ado/reference/rds-api/cancel-method-example-vbscript.md)   
 [Esempio del metodo Cancel (VC + +)](../../../ado/reference/ado-api/cancel-method-example-vc.md)   
 [Metodo Cancel (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [Metodo CancelBatch (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [Metodo CancelUpdate (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [Metodo CancelUpdate (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Eseguire il metodo (comando ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md)   
 [Execute (metodo) (connessione ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md)   
 [Open (metodo) (connessione ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open (metodo) (Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)

