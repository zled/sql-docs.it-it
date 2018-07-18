---
title: Eventi WillChangeRecordset e RecordsetChangeComplete (ADO) | Documenti Microsoft
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
- Recordset::RecordsetChangeComplete
- RecordsetChangeComplete
- Recordset::WillChangeRecordset
- WillChangeRecordset
helpviewer_keywords:
- RecordsetChangeComplete event [ADO]
- WillChangeRecordset event [ADO]
ms.assetid: d5d44659-e0d9-46d9-a297-99c43555082f
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 63962d0ce3c8c4a5bf5aa0274a4084a9f8d84a5f
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35282800"
---
# <a name="willchangerecordset-and-recordsetchangecomplete-events-ado"></a>Eventi WillChangeRecordset e RecordsetChangeComplete (ADO)
Il **WillChangeRecordset** eventi viene chiamato prima che un'operazione in sospeso modifichi il [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md). Il **RecordsetChangeComplete** eventi viene chiamato dopo il **Recordset** è stato modificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
WillChangeRecordset adReason, adStatus, pRecordset  
RecordsetChangeComplete adReason, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Parametri  
 *adReason*  
 Un [EventReasonEnum](../../../ado/reference/ado-api/eventreasonenum.md) valore che specifica il motivo di questo evento. Il valore può essere **adRsnRequery**, **adRsnResynch**, **adRsnClose**, **o adRsnOpen**.  
  
 *adStatus*  
 Un [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) valore di stato.  
  
 Quando **WillChangeRecordset** viene chiamato, questo parametro è impostato su **adStatusOK** se l'operazione che ha causato l'evento ha esito positivo. È impostato su **adStatusCantDeny** se questo evento non è possibile richiedere l'annullamento dell'operazione in sospeso.  
  
 Quando **RecordsetChangeComplete** viene chiamato, questo parametro è impostato su **adStatusOK** se è stata completata l'operazione che ha causato l'evento **adStatusErrorsOccurred** se operazione non riuscita, o **adStatusCancel** se l'operazione associata a accettate in precedenza **WillChangeRecordset** evento è stato annullato.  
  
 Prima di **WillChangeRecordset** restituisce un valore, impostare questo parametro su **adStatusCancel** per richiedere l'annullamento dell'operazione in sospeso oppure impostare questo parametro su adStatusUnwantedEvent per impedire successive notifiche.  
  
 Prima di **WillChangeRecordset** o **RecordsetChangeComplete** restituisce un valore, impostare questo parametro su **adStatusUnwantedEvent** per impedire notifiche successive.  
  
 *pError*  
 Un [errore](../../../ado/reference/ado-api/error-object.md) oggetto. Viene descritto l'errore che si è verificato se il valore di *adStatus* è **adStatusErrorsOccurred**; in caso contrario non è impostata.  
  
 *pRecordset*  
 Oggetto **Recordset** oggetto. Il **Recordset** per cui si è verificato l'evento.  
  
## <a name="remarks"></a>Remarks  
 A **WillChangeRecordset** o **RecordsetChangeComplete** evento può verificarsi perché il **Recordset** [Requery](../../../ado/reference/ado-api/requery-method.md) o [Aprire](../../../ado/reference/ado-api/open-method-ado-recordset.md) metodi.  
  
 Se il provider non supporta i segnalibri, un **RecordsetChange viene generata** notifica degli eventi si verifica ogni volta che le nuove righe vengono recuperate dal provider. Dipende dalla frequenza dell'evento di **RecordsetCacheSize** proprietà.  
  
 È necessario impostare il **adStatus** parametro **adStatusUnwantedEvent** per ogni possibile **adReason** valore arresti completamente la notifica degli eventi per qualsiasi evento che include un **adReason** parametro.  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di modello di eventi ADO (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Riepilogo dei gestori eventi ADO](../../../ado/guide/data/ado-event-handler-summary.md)
