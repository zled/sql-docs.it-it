---
title: Parametri di evento | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Error parameter [ADO]
- Object parameter [ADO]
- Status parameter [ADO]
- events [ADO], parameters
- Reason parameter [ADO]
- event parameters [ADO]
ms.assetid: bd5c5afa-d301-4899-acda-40f98a6afa4d
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9ae7ee638c8489795df8894be23ef80e63b26f07
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="event-parameters"></a>Parametri di evento
Ogni gestore di evento include un parametro di stato che controlla il gestore dell'evento. Per gli eventi Complete, questo parametro viene utilizzato anche per indicare l'esito positivo o negativo dell'operazione che ha generato l'evento. Gli eventi più completi hanno anche un parametro di errore per fornire informazioni su eventuali errori che potrebbero essersi verificati e uno o più parametri di oggetti che fanno riferimento a oggetti ADO utilizzati per eseguire l'operazione. Ad esempio, il [ExecuteComplete](../../../ado/reference/ado-api/executecomplete-event-ado.md) evento include i parametri di oggetto per il **comando**, **Recordset**, e **connessione** oggetti associato all'evento. Nell'esempio seguente di Microsoft® Visual Basic®, è possibile visualizzare il pCommand, pRecordset e pConnection oggetti che rappresentano il **comando**, **Recordset**, e **connessione** gli oggetti utilizzati per il **Execute** metodo.  
  
```  
Private Sub connEvent_ExecuteComplete(ByVal RecordsAffected As Long, _  
     ByVal pError As ADODB.Error, _  
     adStatus As ADODB.EventStatusEnum, _  
     ByVal pCommand As ADODB.Command, _  
     ByVal pRecordset As ADODB.Recordset, _  
     ByVal pConnection As ADODB.Connection)  
```  
  
 Fatta eccezione per il **errore** dell'oggetto, gli stessi parametri vengono passati agli eventi Will. Questo consente di esaminare tutti gli oggetti che verranno utilizzati durante l'operazione in sospeso e determinare se l'operazione deve essere portato a termine.  
  
 Alcuni gestori di eventi presentano un *motivo* parametro, che fornisce informazioni aggiuntive sui motivi per cui si è verificato l'evento. Ad esempio, il **WillMove** e **MoveComplete** gli eventi possono verificarsi a causa di uno qualsiasi dei metodi di navigazione (**MoveNext**, **MovePrevious**e così via) chiamato oppure come risultato di ripetizione di una query.  
  
## <a name="status-parameter"></a>Parametro di stato  
 Quando la routine del gestore eventi viene chiamata, il *stato* parametro è impostato su uno dei valori seguenti.  
  
|Valore|Description|  
|-----------|-----------------|  
|**adStatusOK**|Passato a sia sarà gli eventi e Complete. Questo valore indica che l'operazione che ha causato l'evento è stata completata.|  
|**adStatusErrorsOccurred**|Passato solo agli eventi Complete. Questo valore indica che l'operazione che ha causato l'evento ha avuto esito negativo o un evento verrà annullata l'operazione. Controllare il *errore* parametro per maggiori dettagli.|  
|**adStatusCantDeny**|Passato verrà solo agli eventi. Questo valore indica che l'operazione non può essere annullata dall'evento Will. Deve essere eseguita.|  
  
 Se si determina nell'evento Will che l'operazione deve continuare, lasciare il *stato* parametro invariato. Fino a quando il parametro di stato in ingresso non è stato impostato su **adStatusCantDeny**, tuttavia, è possibile annullare l'operazione in sospeso modificando *stato* a **adStatusCancel**. Quando si esegue questa operazione, l'evento completo associato all'operazione è relativo *stato* parametro impostato su **adStatusErrorsOccurred**. Il **errore** oggetto passato per l'evento di completamento, conterrà il valore **adErrOperationCancelled**.  
  
 Se non si desidera elaborare un evento, è possibile impostare *stato* a **adStatusUnwantedEvent** e l'applicazione non riceverà più notifiche di quell ' evento. Tuttavia, tenere presente che alcuni eventi possono essere generati per più di un motivo. In tal caso, è necessario specificare **adStatusUnwantedEvent** per ciascun motivo possibili. Ad esempio, per interrompere la ricezione di notifiche in sospeso **RecordChange** eventi, è necessario impostare il *stato* parametro **adStatusUnwantedEvent** per  **adRsnAddNew**, **adRsnDelete**, **adRsnUpdate**, **adRsnUndoUpdate**, **adRsnUndoAddNew**, **adRsnUndoDelete**, e **adRsnFirstChange** che si verificano.  
  
|Valore|Description|  
|-----------|-----------------|  
|**adStatusUnwantedEvent**|Questo gestore eventi viene visualizzato alcun ulteriori notifiche della richiesta.|  
|**adStatusCancel**|Richiedere l'annullamento dell'operazione che sta per verificarsi.|  
  
## <a name="error-parameter"></a>Errore parametro  
 Il *errore* parametro è un riferimento a un oggetto ADO [errore](../../../ado/reference/ado-api/error-object.md) oggetto. Quando il *stato* parametro è impostato su **adStatusErrorsOccurred**, **errore** oggetto contiene i dettagli sulla causa dell'errore dell'operazione. Se l'evento verrà associata a un evento di completamento ha annullato l'operazione impostando il *stato* parametro **adStatusCancel**, l'oggetto errore viene sempre impostata su  **adErrOperationCancelled**.  
  
## <a name="object-parameter"></a>Parametro dell'oggetto  
 Ogni evento riceve uno o più oggetti che rappresentano gli oggetti coinvolti nell'operazione. Ad esempio, il **ExecuteComplete** evento riceve un **comando** oggetto, un **Recordset** , oggetto e un **connessione** oggetto.  
  
## <a name="reason-parameter"></a>Parametro Reason  
 Il *motivo* parametro *adReason*, fornisce informazioni aggiuntive sui motivi per cui si è verificato l'evento. Gli eventi con un *adReason* parametro può essere chiamato più volte, anche per la stessa operazione per un motivo diverso ogni volta. Ad esempio, il **WillChangeRecord** gestore eventi viene chiamato per le operazioni che stanno per eseguire o annullare l'inserimento, eliminazione o la modifica di un record. Se si desidera elaborare un evento solo quando si verifica per un motivo specifico, è possibile utilizzare il *adReason* parametro per filtrare le occorrenze che non si è interessati in. Ad esempio, se si desidera elaborare gli eventi di modifica di record solo quando si verificano perché è stato aggiunto un record, è possibile utilizzare il seguente.  
  
```  
' BeginEventExampleVB01  
Private Sub rsTest_WillChangeRecord(ByVal adReason As ADODB.EventReasonEnum, ByVal cRecords As Long, adStatus As ADODB.EventStatusEnum, ByVal pRecordset As ADODB.Recordset)  
   If adReason = adRsnAddNew Then  
       ' Process event  
       '...  
   Else  
       ' Cancel event notification for all  
       ' other possible adReason values.  
       adStatus = adStatusUnwantedEvent  
   End If  
End Sub  
' EndEventExampleVB01  
```  
  
 In questo caso, la notifica può verificarsi per ognuno degli altri motivi. Tuttavia, si verificherà una sola volta per ciascun motivo. Dopo la notifica una sola volta per ciascun motivo, si riceverà la notifica solo per l'aggiunta di un nuovo record.  
  
 Al contrario, è necessario impostare *adStatus* a **adStatusUnwantedEvent** solo una volta per richiedere che un gestore eventi senza un **adReason** evento ricevente stop di parametro notifiche.  
  
## <a name="see-also"></a>Vedere anche  
 [Riepilogo dei gestori di eventi ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Creazione di istanze di ADO evento dal linguaggio](../../../ado/guide/data/ado-event-instantiation-by-language.md)   
 [Dell'interazione tra i gestori eventi](../../../ado/guide/data/how-event-handlers-work-together.md)   
 [Tipi di eventi](../../../ado/guide/data/types-of-events.md)

