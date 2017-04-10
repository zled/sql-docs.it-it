---
title: "Visualizzare una traccia salvata (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tracce [SQL Server], visualizzazione"
  - "visualizzazione di tracce"
  - "visualizzazione di tracce"
ms.assetid: 3a95a816-aa89-4d5f-858c-968a9cb3ee87
caps.latest.revision: 22
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 22
---
# Visualizzare una traccia salvata (Transact-SQL)
  In questo argomento viene illustrato l'utilizzo delle funzioni predefinite per visualizzare una traccia salvata.  
  
### Per visualizzare una traccia specifica  
  
1.  Eseguire **fn_trace_getinfo** specificando l'ID della traccia su cui si vuole ottenere informazioni. Questa funzione restituisce una tabella in cui sono indicate la traccia, la proprietà della traccia e le informazioni sulla proprietà.  
  
     Richiamare la funzione nel modo seguente:  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getinfo(trace_id)  
    ```  
  
### Per visualizzare tutte le tracce esistenti  
  
1.  Eseguire **fn_trace_getinfo** specificando `0` o `default`. Questa funzione restituisce una tabella in cui sono indicate tutte le tracce, le relative proprietà e le informazioni su tali proprietà.  
  
     Di seguito è illustrato come richiamare la funzione:  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getinfo(default)  
    ```  
  
## Sicurezza di .NET Framework  
 Per eseguire la funzione predefinita **fn_trace_getinfo**, è necessaria l'autorizzazione seguente:  
  
 ALTER TRACE nel server.  
  
## Vedere anche  
 [sys.fn_trace_getinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md)   
 [Visualizzare e analizzare le tracce con SQL Server Profiler](../../tools/sql-server-profiler/view-and-analyze-traces-with-sql-server-profiler.md)  
  
  