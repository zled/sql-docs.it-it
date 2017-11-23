---
title: "Determinazione delle funzionalità supportate | Documenti Microsoft"
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
- editing data [ADO], Supports method
- Supports method [ADO]
ms.assetid: 65090cba-6d46-4775-8d61-f6838e7752a6
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b16206a305ea9751b180fddccec5e36ba0945b5a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="determining-what-is-supported"></a>Determinazione delle funzionalità supportate
Il **supporta** metodo viene utilizzato per determinare se un oggetto **Recordset** oggetto supporta un determinato tipo di funzionalità. Contiene la sintassi seguente:  
  
```  
  
boolean = recordset.Supports(CursorOptions )  
```  
  
## <a name="remarks"></a>Osservazioni  
 Il **supporta** metodo restituisce un valore booleano che indica se il provider supporta tutte le funzionalità identificate dall'argomento CursorOptions. È possibile utilizzare il **supporta** metodo per determinare i tipi di funzionalità un **Recordset** supporta dell'oggetto. Se il **Recordset** oggetto supporta le funzionalità la cui costanti corrispondenti sono *CursorOptions*, **supporta** restituisce **True**. In caso contrario, restituisce **False**.  
  
 Utilizzando il **supporta** (metodo), è possibile cercare la capacità del **Recordset** oggetto per aggiungere nuovi record, utilizzare i segnalibri, utilizzare il **trovare** metodo, utilizzare lo scorrimento, utilizzare il  **Indice** , proprietà ed eseguire gli aggiornamenti in batch. Per un elenco completo delle costanti e i relativi significati, vedere [CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md).  
  
 Sebbene il **supporta** metodo può restituire **True** per una determinata funzionalità non garantisce che il provider può rendere la funzionalità disponibile in tutte le circostanze. Il **supporta** metodo restituisce semplicemente se il provider supporta la funzionalità specificata, presupponendo che vengano soddisfatte determinate condizioni. Ad esempio, il **supporta** metodo può indicare che un **Recordset** oggetto supporta gli aggiornamenti, anche se il cursore è basato su un join tra più tabelle, alcune colonne di cui non sono aggiornabili.
