---
title: EventReasonEnum | Documenti Microsoft
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
- EventReasonEnum
helpviewer_keywords:
- EventReasonEnum enumeration [ADO]
ms.assetid: 7d4a5496-ec2d-4936-b36a-7049a82be4b4
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 176b9c1eaa54b7990ea44b0438c710e5ab4c7798
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="eventreasonenum"></a>EventReasonEnum
Specifica il motivo che ha causato un evento si verifichi.  
  
|Costante|Value|Description|  
|--------------|-----------|-----------------|  
|**adRsnAddNew**|1|Un'operazione di aggiunta di un nuovo record.|  
|**adRsnClose**|9|Un'operazione ha chiuso il **Recordset**.|  
|**adRsnDelete**|2|Un'operazione ha eliminato un record.|  
|**adRsnFirstChange**|11|Un'operazione effettuata la prima modifica a un record.|  
|**adRsnMove**|10|Un'operazione di spostata il puntatore del record all'interno di **Recordset**.|  
|**adRsnMoveFirst**|12|Un'operazione ha spostato il puntatore del record del primo record di **Recordset**.|  
|**adRsnMoveLast**|15|Un'operazione ha spostato il puntatore del record dell'ultimo record di **Recordset**.|  
|**adRsnMoveNext**|13|Un'operazione ha spostato il puntatore del record sul record successivo nel **Recordset**.|  
|**adRsnMovePrevious**|14|Un'operazione ha spostato il puntatore del record per record precedente il **Recordset**.|  
|**adRsnRequery**|7|Un'operazione rieseguita la [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).|  
|**adRsnResynch**|8|Un'operazione completa la risincronizzazione di **Recordset** con il database.|  
|**adRsnUndoAddNew**|5|Un'operazione ha annullato l'aggiunta di un nuovo record.|  
|**adRsnUndoDelete**|6|Un'operazione ha annullato l'eliminazione di un record.|  
|**adRsnUndoUpdate**|4|Un'operazione ha annullato l'aggiornamento di un record.|  
|**adRsnUpdate**|3|Un'operazione ha aggiornato un record esistente.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Package: **com.ms.wfc.data**  
  
|Costante|  
|--------------|  
|AdoEnums.EventReason.ADDNEW|  
|AdoEnums.EventReason.CLOSE|  
|AdoEnums.EventReason.DELETE|  
|AdoEnums.EventReason.FIRSTCHANGE|  
|AdoEnums.EventReason.MOVE|  
|AdoEnums.EventReason.MOVEFIRST|  
|AdoEnums.EventReason.MOVELAST|  
|AdoEnums.EventReason.MOVENEXT|  
|AdoEnums.EventReason.MOVEPREVIOUS|  
|AdoEnums.EventReason.REQUERY|  
|AdoEnums.EventReason.RESYNCH|  
|AdoEnums.EventReason.UNDOADDNEW|  
|AdoEnums.EventReason.UNDODELETE|  
|AdoEnums.EventReason.UNDOUPDATE|  
|AdoEnums.EventReason.UPDATE|  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Eventi WillChangeRecord e RecordChangeComplete (ADO)](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|[Eventi WillChangeRecordset e RecordsetChangeComplete (ADO)](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|  
|[Eventi WillMove e MoveComplete (ADO)](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)||
