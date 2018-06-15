---
title: Evento WillExecute (ADO) | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- WillExecute
- Connection::WillExecute
helpviewer_keywords:
- WillExecute event [ADO]
ms.assetid: dd755e46-f589-48a3-93a9-51ff998d44b5
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d0fd9c97018c5c15710067298a88b4996c5a699f
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35282880"
---
# <a name="willexecute-event-ado"></a>Evento WillExecute (ADO)
Il **WillExecute** eventi viene chiamato prima dell'esecuzione di un comando in sospeso su una connessione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
WillExecute Source, CursorType, LockType, Options, adStatus, pCommand, pRecordset, pConnection  
```  
  
#### <a name="parameters"></a>Parametri  
 *Origine*  
 Oggetto **stringa** che contiene un comando SQL o un nome della stored procedure.  
  
 *CursorType*  
 Oggetto [CursorTypeEnum](../../../ado/reference/ado-api/cursortypeenum.md) che contiene il tipo di cursore per il **Recordset** che verrà aperto. Con questo parametro, è possibile modificare il cursore in qualsiasi tipo durante un **Recordset**[Open (metodo) (Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md) operazione. *CursorType* per qualsiasi altra operazione verrà ignorata.  
  
 *LockType*  
 Oggetto [LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md) che contiene il tipo di blocco per il **Recordset** che verrà aperto. Con questo parametro, è possibile modificare il blocco a qualsiasi tipo durante un **RecordsetOpen** operazione. *LockType* per qualsiasi altra operazione verrà ignorata.  
  
 *Opzioni*  
 Oggetto **lungo** valore che indica le opzioni che possono essere utilizzate per eseguire il comando o aprire il **Recordset**.  
  
 *adStatus*  
 Un [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) valore di stato che può essere **adStatusCantDeny** o **adStatusOK** quando viene chiamato questo evento. Se è **adStatusCantDeny**, questo evento potrebbe non richiedere l'annullamento dell'operazione in sospeso.  
  
 *pCommand*  
 Il [comando ADO (Object)](../../../ado/reference/ado-api/command-object-ado.md) dell'oggetto per cui si applica questa notifica dell'evento.  
  
 *pRecordset*  
 Il [Recordset ADO (Object)](../../../ado/reference/ado-api/recordset-object-ado.md) dell'oggetto per cui si applica questa notifica dell'evento.  
  
 *pConnection*  
 Il [connessione ADO (Object)](../../../ado/reference/ado-api/connection-object-ado.md) dell'oggetto per cui si applica questa notifica dell'evento.  
  
## <a name="remarks"></a>Remarks  
 Oggetto **WillExecute** evento può verificarsi a causa di una connessione.  [Execute (metodo) (connessione ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md), [metodo Execute (comando ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md), o [Open (metodo) (Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md) metodo il *pConnection* deve parametro contengono sempre un riferimento valido a un **connessione** oggetto. Se l'evento è dovuto al **Connection**, *pRecordset* e *pCommand* sono impostati su **nulla**. Se l'evento è dovuto al **Open**, *pRecordset* parametro farà riferimento il **Recordset** oggetto e *pCommand* parametro è impostato su **nulla**. Se l'evento è dovuto al **Command. Execute**, *pCommand* parametro farà riferimento il **comando** oggetto e *pRecordset* parametro è impostato su **nulla**.  
  
 **WillExecute** consente di esaminare e modificare i parametri di esecuzione in sospeso. Questo evento può restituire una richiesta di annullamento che il comando in sospeso.  
  
> [!NOTE]
>  Se l'origine originale per un **comando** è un flusso specificato dal [proprietà CommandStream (ADO)](../../../ado/reference/ado-api/commandstream-property-ado.md) proprietà, l'assegnazione di una nuova stringa per il **WillExecute * * * origine* l'origine della modifica parametro di **comando**. Il **CommandStream** proprietà verrà cancellata e [proprietà CommandText (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md) proprietà verrà aggiornata con la nuova origine. Il flusso originale specificato dal parametro **CommandStream** verrà rilasciato e non è accessibile.  
  
 Se il sottolinguaggio della nuova stringa di origine è diverso dall'impostazione originale del [proprietà Dialect](../../../ado/reference/ado-api/dialect-property.md) proprietà (che corrisponde alla **CommandStream**), il sottolinguaggio corretto deve essere specificato impostando il **sottolinguaggio** proprietà dell'oggetto comando a cui fa riferimento *pCommand*.  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di modello di eventi ADO (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Riepilogo dei gestori di eventi ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Oggetto Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
