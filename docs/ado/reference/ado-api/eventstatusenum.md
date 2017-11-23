---
title: EventStatusEnum | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: EventStatusEnum
helpviewer_keywords: EventStatusEnum enumeration [ADO]
ms.assetid: ebfd4cda-4017-4873-9d28-38b1c7db12a8
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: de4655072b5ce25b3fb35dbb8bc73b6334a9f6c6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="eventstatusenum"></a>EventStatusEnum
Specifica lo stato corrente dell'esecuzione di un evento.  
  
|Costante|Valore|Description|  
|--------------|-----------|-----------------|  
|**adStatusCancel**|4|Richiede l'annullamento dell'operazione che ha causato la generazione dell'evento.|  
|**adStatusCantDeny**|3|Indica che l'operazione non è possibile richiedere l'annullamento dell'operazione in sospeso.|  
|**adStatusErrorsOccurred**|2|Indica che l'operazione che ha causato l'evento non è riuscito a causa di uno o più errori.|  
|**adStatusOK**|1|Indica che l'operazione che ha causato l'evento è riuscita.|  
|**adStatusUnwantedEvent**|5|Impedisce notifiche successive prima il metodo di evento ha terminato l'esecuzione.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Pacchetto: **com.ms. wfc.**  
  
|Costante|  
|--------------|  
|AdoEnums.EventStatus.CANCEL|  
|AdoEnums.EventStatus.CANTDENY|  
|AdoEnums.EventStatus.ERRORSOCCURRED|  
|AdoEnums.EventStatus.OK|  
|AdoEnums.EventStatus.UNWANTEDEVENT|  
  
## <a name="applies-to"></a>Si applica a  
  
||||  
|-|-|-|  
|[BeginTransComplete, CommitTransComplete ed eventi RollbackTransComplete (ADO)](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|[Eventi ConnectComplete e Disconnect (ADO)](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|[Evento EndOfRecordset (ADO)](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|  
|[Evento ExecuteComplete (ADO)](../../../ado/reference/ado-api/executecomplete-event-ado.md)|[Evento FetchComplete (ADO)](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|[Evento InfoMessage (ADO)](../../../ado/reference/ado-api/infomessage-event-ado.md)|  
|[Eventi WillChangeField e FieldChangeComplete (ADO)](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|[Eventi WillChangeRecord e RecordChangeComplete (ADO)](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|[Eventi WillChangeRecordset e RecordsetChangeComplete (ADO)](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|  
|[Evento WillConnect (ADO)](../../../ado/reference/ado-api/willconnect-event-ado.md)|[Evento WillExecute (ADO)](../../../ado/reference/ado-api/willexecute-event-ado.md)|[Eventi WillMove e MoveComplete (ADO)](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|
