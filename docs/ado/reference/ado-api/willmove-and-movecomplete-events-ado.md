---
title: WillMove e MoveComplete eventi (ADO) | Documenti Microsoft
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
f1_keywords:
- Recordset::MoveComplete
- WillMove
- MoveComplete
- Recordset::WillMove
helpviewer_keywords:
- MoveComplete event [ADO]
- WillMove event [ADO]
ms.assetid: 1a3d1042-4f30-4526-a0c7-853c242496db
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b4cf136ccd49b461578f7a34941465a54c4e4183
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="willmove-and-movecomplete-events-ado"></a>WillMove e MoveComplete eventi (ADO)
Il **WillMove** eventi viene chiamato prima che un'operazione in sospeso modifichi la posizione corrente nella [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md). Il **MoveComplete** eventi viene chiamato dopo la posizione corrente all'interno di **Recordset** le modifiche.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
WillMove adReason, adStatus, pRecordset  
MoveComplete adReason, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Parametri  
 *adReason*  
 Un [EventReasonEnum](../../../ado/reference/ado-api/eventreasonenum.md) valore che specifica il motivo di questo evento. Il valore può essere **adRsnMoveFirst**, **adRsnMoveLast**, **adRsnMoveNext**, **adRsnMovePrevious**, **adRsnMove** , o **adRsnRequery**.  
  
 *pError*  
 Un [errore](../../../ado/reference/ado-api/error-object.md) oggetto. Viene descritto l'errore che si è verificato se il valore di *adStatus* è **adStatusErrorsOccurred**; in caso contrario il parametro non è stato impostato.  
  
 *adStatus*  
 Un [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) valore di stato.  
  
 Quando **WillMove** viene chiamato, questo parametro è impostato su **adStatusOK** se l'operazione che ha causato l'evento ha esito positivo. È impostato su **adStatusCantDeny** se questo evento non è possibile richiedere l'annullamento dell'operazione in sospeso.  
  
 Quando **MoveComplete** viene chiamato, questo parametro è impostato su **adStatusOK** se l'operazione che ha causato l'evento ha esito positivo o a **adStatusErrorsOccurred** se la operazione non riuscita.  
  
 Prima di **WillMove** restituisce un valore, impostare questo parametro su **adStatusCancel** per richiedere l'annullamento dell'operazione in sospeso oppure impostare questo parametro su **adStatusUnwantedEvent** Per impedire notifiche successive.  
  
 Prima di **MoveComplete** restituisce un valore, impostare questo parametro su **adStatusUnwantedEvent** per impedire notifiche successive.  
  
 *pRecordset*  
 Oggetto [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto. Il **Recordset** per cui si è verificato l'evento.  
  
## <a name="remarks"></a>Osservazioni  
 Oggetto **WillMove** o **MoveComplete** evento può verificarsi a causa dei seguenti **Recordset** operations: [aprire](../../../ado/reference/ado-api/open-method-ado-recordset.md), [spostare](../../../ado/reference/ado-api/move-method-ado.md), [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MoveLast](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md), e [Requery](../../../ado/reference/ado-api/requery-method.md). Questi eventi possono verificarsi a causa delle proprietà seguenti: [filtro](../../../ado/reference/ado-api/filter-property.md), [indice](../../../ado/reference/ado-api/index-property.md), [segnalibro](../../../ado/reference/ado-api/bookmark-property-ado.md), [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)e [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md). Questi eventi si verificano anche se un elemento figlio **Recordset** è **Recordset** eventi connessi e il padre **Recordset** viene spostato.  
  
 È necessario impostare il *adStatus* parametro **adStatusUnwantedEvent** per ogni possibile *adReason* valore interrompere completamente la notifica degli eventi per qualsiasi evento che include un *adReason* parametro.  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di modello di eventi ADO (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Riepilogo dei gestori di eventi ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
