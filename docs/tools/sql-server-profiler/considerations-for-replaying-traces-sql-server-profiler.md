---
title: Considerazioni relative alla riproduzione di tracce (SQL Server Profiler) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: sql-server-profiler
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 73fa339f-b71a-4be4-97ca-d4ae84c8b90b
caps.latest.revision: "21"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d325c5cd4988764134e4d76dd728a00981e1bc07
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="considerations-for-replaying-traces-sql-server-profiler"></a>Considerazioni relative alla riproduzione di tracce (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)][!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] non è possibile riprodurre i tipi di tracce seguenti:  
  
-   Tracce contenenti replica transazionale e altre attività del log delle transazioni. Questi eventi verranno ignorati. Gli altri tipi di replica non contrassegnano il log delle transazioni e pertanto non subiscono alcun effetto.  
  
-   Tracce contenenti operazioni che coinvolgono identificatori univoci globali (GUID). Questi eventi verranno ignorati.  
  
-   Tracce contenenti operazioni su colonne **text**, **ntext**e **image** che coinvolgono l'utilità **bcp** , istruzioni BULK INSERT, READTEXT, WRITETEXT e UPDATETEXT e operazioni full-text. Questi eventi verranno ignorati.  
  
-   Tracce contenenti operazioni di associazione della sessione, ovvero le stored procedure di sistema **sp_getbindtoken** e **sp_bindsession** . Questi eventi verranno ignorati.  
  
> [!NOTE]  
>  Se non si usa il modello di riproduzione preconfigurato (**TSQL_Replay**) e non si acquisiscono tutti i dati necessari, la traccia non verrà riprodotta in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] . Per altre informazioni, vedere [Requisiti per la riproduzione](../../tools/sql-server-profiler/replay-requirements.md).  
  
 Per informazioni sulle autorizzazioni necessarie per riprodurre una traccia, vedere [Autorizzazioni necessarie per l'esecuzione di SQL Server Profiler](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Utilità bcp](../../tools/bcp-utility.md)   
 [SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md)   
 [sp_getbindtoken &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-getbindtoken-transact-sql.md)   
 [sp_bindsession &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-bindsession-transact-sql.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md)   
 [READTEXT &#40; Transact-SQL &#41;](../../t-sql/queries/readtext-transact-sql.md)   
 [WRITETEXT &#40; Transact-SQL &#41;](../../t-sql/queries/writetext-transact-sql.md)   
 [UPDATETEXT &#40; Transact-SQL &#41;](../../t-sql/queries/updatetext-transact-sql.md)  
  
  
