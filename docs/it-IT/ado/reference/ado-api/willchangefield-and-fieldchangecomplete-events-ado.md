---
title: Eventi WillChangeField e FieldChangeComplete (ADO) | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FieldChangeComplete
- Recordset::WillChangeField
- Recordset::FieldChangeComplete
- WillChangeField
helpviewer_keywords:
- WillChangeField event [ADO]
- fieldchangecomplete event [ADO]
ms.assetid: 3e49fb89-c45b-4d39-823e-3cc887c59b37
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0114851f666589df614cbec9ba279ccfa0313189
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="willchangefield-and-fieldchangecomplete-events-ado"></a>Eventi WillChangeField e FieldChangeComplete (ADO)
Il **WillChangeField** eventi viene chiamato prima che un'operazione in sospeso cambia il valore di uno o più [campo](../../../ado/reference/ado-api/field-object.md) gli oggetti di [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md). Il **FieldChangeComplete** eventi viene chiamato dopo il valore di uno o più **campo** oggetti è stato modificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
WillChangeField cFields, Fields, adStatus, pRecordset  
FieldChangeComplete cFields, Fields, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Parametri  
 *cFields*  
 Oggetto **lungo** che indica il numero di **campo** oggetti *campi*.  
  
 *Fields*  
 Per **WillChangeField**, *campi* parametro è una matrice di **varianti** contenente **campo** oggetti con i valori originali. Per **FieldChangeComplete**, *campi* parametro è una matrice di **varianti** contenente **campo** oggetti con i valori modificati .  
  
 *pError*  
 Un [errore](../../../ado/reference/ado-api/error-object.md) oggetto. Viene descritto l'errore che si è verificato se il valore di *adStatus* è **adStatusErrorsOccurred**; in caso contrario non è impostata.  
  
 *adStatus*  
 Un [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) valore di stato.  
  
 Quando **WillChangeField** viene chiamato, questo parametro è impostato su **adStatusOK** se l'operazione che ha causato l'evento ha esito positivo. È impostato su **adStatusCantDeny** se questo evento non è possibile richiedere l'annullamento dell'operazione in sospeso.  
  
 Quando **FieldChangeComplete** viene chiamato, questo parametro è impostato su **adStatusOK** se l'operazione che ha causato l'evento ha esito positivo o a **adStatusErrorsOccurred** se operazione non riuscita.  
  
 Prima di **WillChangeField** restituisce un valore, impostare questo parametro su **adStatusCancel** per richiedere l'annullamento dell'operazione in sospeso.  
  
 Prima di **FieldChangeComplete** restituisce un valore, impostare questo parametro su **adStatusUnwantedEvent** per impedire notifiche successive.  
  
 *pRecordset*  
 Oggetto **Recordset** oggetto. Il **Recordset** per cui si è verificato l'evento.  
  
## <a name="remarks"></a>Osservazioni  
 A **WillChangeField** o **FieldChangeComplete** evento può verificarsi quando si imposta la [valore](../../../ado/reference/ado-api/value-property-ado.md) proprietà e la chiamata di [aggiornamento](../../../ado/reference/ado-api/update-method.md) (metodo) con i parametri di matrice campo e valore.  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di modello di eventi ADO (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Riepilogo dei gestori eventi ADO](../../../ado/guide/data/ado-event-handler-summary.md)
