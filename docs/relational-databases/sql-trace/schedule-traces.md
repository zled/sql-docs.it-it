---
title: "Pianificare tracce | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "filtri [SQL Server], eventi"
  - "tracce [SQL Server]"
  - "tracce [SQL Server], arresto"
  - "eventi [SQL Server], filtri"
  - "pianificazione di tracce [SQL Server]"
  - "tracce [SQL Server], pianificazione"
  - "arresto di tracce"
ms.assetid: 620b79db-924b-4502-8af3-39efcfca245d
caps.latest.revision: 24
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 24
---
# Pianificare tracce
  Esistono due modi per pianificare le tracce in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. È possibile effettuare le operazioni seguenti:  
  
-   Abilitare una data e un'ora di arresto della traccia  
  
-   Utilizzare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent per pianificare una traccia.  
  
## Specifica di una data e un'ora di arresto  
 È possibile specificare una data e un'ora di arresto della traccia se si utilizzano le stored procedure di [!INCLUDE[tsql](../../includes/tsql-md.md)] o [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. L'impostazione della data e dell'ora di arresto deve essere eseguita durante la configurazione originale della traccia.  
  
## Pianificazione di tracce tramite SQL Server Agent  
 Il metodo migliore per pianificare le tracce consiste nell'avviare la traccia tramite [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent e quindi specificare una data e un'ora di arresto per la traccia tramite la stored procedure [!INCLUDE[tsql](../../includes/tsql-md.md)]**sp_trace_setstatus** o [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
 **Per impostare un filtro basato sulla data e sull'ora di fine per una traccia**  
  
 [Filtrare gli eventi in base all'ora di fine &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-based-on-the-event-end-time-sql-server-profiler.md)  
  
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)  
  
## Vedere anche  
 [Automatizzazione delle attività amministrative &#40;SQL Server Agent&#41;](../../ssms/agent/automated-administration-tasks-sql-server-agent.md)  
  
  