---
title: "Determinazione della modalità di modifica | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editing data [ADO], edit mode
- ADO, editing data
ms.assetid: 4c7e010d-08cd-4e22-9b32-23c36f02f88c
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d3ffee8b910c5e13754c461671a00380d348f3f9
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="determining-edit-mode"></a>Determinazione della modalità di modifica
ADO gestisce un buffer di modifica associato al record corrente. Il **EditMode** proprietà indica se sono state apportate modifiche a questo buffer o se è stato creato un nuovo record. Utilizzare **EditMode** per determinare lo stato di modifica del record corrente. È possibile verificare le modifiche in sospeso se è stato interrotto un processo di modifica e determinare se è necessario utilizzare il **aggiornamento** o **CancelUpdate** metodo.  
  
 **EditMode** restituisce uno del **EditModeEnum** costanti, sono elencate nella tabella seguente.  
  
|Costante|Description|  
|--------------|-----------------|  
|**adEditNone**|Indica che nessuna operazione di modifica è in corso.|  
|**adEditInProgress**|Indica che i dati del record corrente sono stati modificati ma non salvati.|  
|**adEditAdd**|Indica che il **AddNew** metodo è stato chiamato e il record corrente nel buffer di copia è un nuovo record che non è stato salvato nel database.|  
|**adEditDelete**|Indica che il record corrente è stato eliminato.|  
  
 **EditMode** può restituire un valore valido solo se è disponibile un record corrente. **EditMode** restituirà un errore se **BOF** o **EOF** è **True** o se è stato eliminato il record corrente.
