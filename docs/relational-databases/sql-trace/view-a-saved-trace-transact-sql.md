---
title: Visualizzare una traccia salvata (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- traces [SQL Server], viewing
- displaying traces
- viewing traces
ms.assetid: 3a95a816-aa89-4d5f-858c-968a9cb3ee87
caps.latest.revision: "22"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 297d8e0725f30e97bf7c393559a04e62b0d3af21
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="view-a-saved-trace-transact-sql"></a>Visualizzare una traccia salvata (Transact-SQL)
  In questo argomento viene illustrato l'utilizzo delle funzioni predefinite per visualizzare una traccia salvata.  
  
### <a name="to-view-a-specific-trace"></a>Per visualizzare una traccia specifica  
  
1.  Eseguire **fn_trace_getinfo** specificando l'ID della traccia su cui si vuole ottenere informazioni. Questa funzione restituisce una tabella in cui sono indicate la traccia, la proprietà della traccia e le informazioni sulla proprietà.  
  
     Richiamare la funzione nel modo seguente:  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getinfo(trace_id)  
    ```  
  
### <a name="to-view-all-existing-traces"></a>Per visualizzare tutte le tracce esistenti  
  
1.  Eseguire **fn_trace_getinfo** specificando `0` o `default`. Questa funzione restituisce una tabella in cui sono indicate tutte le tracce, le relative proprietà e le informazioni su tali proprietà.  
  
     Di seguito è illustrato come richiamare la funzione:  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getinfo(default)  
    ```  
  
## <a name="net-framework-security"></a>Sicurezza di .NET Framework  
 Per eseguire la funzione predefinita **fn_trace_getinfo**, è necessaria l'autorizzazione seguente:  
  
 ALTER TRACE nel server.  
  
## <a name="see-also"></a>Vedere anche  
 [sys.fn_trace_getinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md)   
 [Visualizzare e analizzare le tracce con SQL Server Profiler](../../tools/sql-server-profiler/view-and-analyze-traces-with-sql-server-profiler.md)  
  
  
