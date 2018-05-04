---
title: Evento FetchComplete (ADO) | Documenti Microsoft
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
apitype: COM
f1_keywords:
- Recordset::ExecuteComplete
- ExecuteComplete
helpviewer_keywords:
- FetchComplete event [ADO]
ms.assetid: a28d3858-566c-468d-b070-d1de4339fbea
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 59c3adb6b0ad683b40dac2cf4547800bf7398067
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="fetchcomplete-event-ado"></a>Evento FetchComplete (ADO)
Il **FetchComplete** eventi viene chiamato dopo che sono stati recuperati tutti i record di un'operazione di lunga durata asincrona nel [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
FetchComplete pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Parametri  
 *pError*  
 Un [errore](../../../ado/reference/ado-api/error-object.md) oggetto. Viene descritto l'errore che si è verificato se il valore di **adStatus** è **adStatusErrorsOccurred**; in caso contrario non è impostata.  
  
 *adStatus*  
 Un [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) valore di stato. Quando questo evento viene chiamato, questo parametro è impostato su **adStatusOK** se l'operazione che ha causato l'evento ha esito positivo o a **adStatusErrorsOccurred** se l'operazione non riuscita.  
  
 Prima di questo evento restituisce, impostare questo parametro su **adStatusUnwantedEvent** per impedire notifiche successive.  
  
 *pRecordset*  
 Oggetto **Recordset** oggetto. L'oggetto per cui sono stati recuperati i record.  
  
## <a name="remarks"></a>Osservazioni  
 Per utilizzare **FetchComplete** con Microsoft Visual Basic, Visual Basic 6.0 o versione successiva è obbligatorio.  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di modello di eventi ADO (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Riepilogo dei gestori eventi ADO](../../../ado/guide/data/ado-event-handler-summary.md)
