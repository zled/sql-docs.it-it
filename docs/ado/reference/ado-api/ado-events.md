---
title: Gli eventi ADO | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- events [ADO]
- ADO, events
ms.assetid: 0ded5ad9-8f83-4224-95af-38512783b972
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1573eaca943c1bb018e279f5360f72480610a5d1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="ado-events"></a>Eventi ADO
|||  
|-|-|  
|[BeginTransComplete](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|Chiamato dopo il **BeginTrans** operazione.|  
|[CommitTransComplete](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|Chiamato dopo il **CommitTrans** operazione.|  
|[ConnectComplete](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|Chiamata eseguita dopo l'avvio di una connessione.|  
|[Disconnetti](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|Chiamato dopo la fine di una connessione.|  
|[EndOfRecordset](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|Chiamata eseguita quando viene eseguito un tentativo di spostare in una riga oltre la fine del **Recordset**.|  
|[ExecuteComplete](../../../ado/reference/ado-api/executecomplete-event-ado.md)|Chiamata eseguita dopo un comando ha terminato l'esecuzione.|  
|[FetchComplete](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|Chiamato dopo che sono stati recuperati tutti i record di un'operazione di lunga durata asincrona nel **Recordset**.|  
|[FetchProgress](../../../ado/reference/ado-api/fetchprogress-event-ado.md)|Viene chiamato periodicamente durante un'operazione asincrona di lunga durata per segnalare il numero di righe attualmente recuperato nel **Recordset**.|  
|[FieldChangeComplete](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|Chiamato dopo il valore di uno o più **campo** oggetti è stato modificato.|  
|[InfoMessage](../../../ado/reference/ado-api/infomessage-event-ado.md)|Chiamato ogni volta che viene generato un avviso durante un **ConnectionEvent** operazione.|  
|[MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|Chiamato dopo la posizione corrente all'interno di **Recordset** le modifiche.|  
|[RecordChangeComplete](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|Chiamato dopo la modifica di uno o più record.|  
|[RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|Chiamato dopo il **Recordset** è stato modificato.|  
|[RollbackTransComplete](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|Chiamato dopo il **RollbackTrans** operazione.|  
|[WillChangeField](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|Chiamato prima che un'operazione in sospeso modifichi il valore di uno o più **campo** gli oggetti di **Recordset**.|  
|[WillChangeRecord](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|Chiamato prima di uno o più record (righe) **Recordset** modificare.|  
|[WillChangeRecordset](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|Chiamato prima che un'operazione in sospeso modifichi il **Recordset**.|  
|[WillConnect](../../../ado/reference/ado-api/willconnect-event-ado.md)|Chiamato prima dell'avvio di una connessione.|  
|[WillExecute](../../../ado/reference/ado-api/willexecute-event-ado.md)|Chiamata eseguita subito prima esegue la connessione di un comando in sospeso e offre all'utente la possibilità di esaminare e modificare i parametri di esecuzione in sospeso.|  
|[WillMove](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|Il **WillMove** eventi viene chiamato *prima* modifica di un'operazione in sospeso nella posizione corrente di **Recordset**.|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ADO](../../../ado/reference/ado-api/ado-api-reference.md)   
 [Raccolte di ADO](../../../ado/reference/ado-api/ado-collections.md)   
 [Proprietà dinamiche ADO](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [Costanti enumerate ADO](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [Appendice b: errori di ADO](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [Gestione degli eventi ADO](../../../ado/guide/data/handling-ado-events.md)   
 [Metodi ADO](../../../ado/reference/ado-api/ado-methods.md)   
 [Modello a oggetti ADO](../../../ado/reference/ado-api/ado-object-model.md)   
 [Le interfacce e gli oggetti ADO](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [Proprietà ADO](../../../ado/reference/ado-api/ado-properties.md)
