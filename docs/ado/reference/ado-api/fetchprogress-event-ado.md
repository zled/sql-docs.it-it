---
title: Evento FetchProgress (ADO) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- FetchProgress
- Recordset::FetchProgress
helpviewer_keywords:
- FetchProgress event [ADO]
ms.assetid: 301716fd-81fc-40eb-8a04-221ef7ab410e
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 606e91ca69d981cf4c1396109f0114ce0244dc3b
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="fetchprogress-event-ado"></a>Evento FetchProgress (ADO)
Il **FetchProgress**eventi viene chiamato periodicamente durante un'operazione asincrona di lunga durata per segnalare il numero di righe attualmente recuperato nel [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
FetchProgress Progress, MaxProgress, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Parametri  
 *Stato*  
 Oggetto **lungo** valore che indica il numero di record che attualmente sono state recuperate dall'operazione di recupero.  
  
 *MaxProgress*  
 Oggetto **lungo** previsto valore che indica il numero massimo di record da recuperare.  
  
 *adStatus*  
 Un [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) valore di stato.  
  
 *pRecordset*  
 Oggetto **Recordset** oggetto che rappresenta l'oggetto per il quale vengono recuperati i record.  
  
## <a name="remarks"></a>Osservazioni  
 Quando si utilizza **FetchProgress** con un elemento figlio **Recordset**, tenere presente che il *lo stato di avanzamento* e *MaxProgress* derivano i valori dei parametri sottostante [servizio cursore](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) set di righe. I valori restituiti rappresentano il numero totale di record nel set di righe sottostanti, non solo il numero di record nel capitolo corrente.  
  
> [!NOTE]
>  Per utilizzare **FetchProgress** con Microsoft Visual Basic, Visual Basic 6.0 o versione successiva è obbligatorio.  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di modello di eventi ADO (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Riepilogo dei gestori di eventi ADO](../../../ado/guide/data/ado-event-handler-summary.md)

