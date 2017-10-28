---
title: Creare tracce manuali usando stored procedure | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f6f47fa2-7c17-41d4-9f69-9be144d56832
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1ee7ef604dc518fb4765ca5bd944c7fe01500035
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="create-manual-traces-using-stored-procedures"></a>Creare tracce manuali utilizzando stored procedure
  In Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono disponibili stored procedure di sistema [!INCLUDE[tsql](../../includes/tsql-md.md)] per la creazione di tracce per un'istanza di [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. È possibile utilizzare tali stored procedure di sistema all'interno di applicazioni personalizzate per creare tracce in modo manuale anziché tramite [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Ciò consente di creare applicazioni personalizzate in grado di soddisfare esigenze aziendali specifiche.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 Nella tabella seguente sono elencate le stored procedure di sistema per la traccia di un'istanza di [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
|Stored procedure|Operazione eseguita|  
|----------------------|--------------------|  
|[sys.fn_trace_geteventinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql.md)|Restituisce informazioni sugli eventi inclusi in una traccia.|  
|[sys.fn_trace_getinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md)|Restituisce informazioni sulla traccia specificata o sulle tracce esistenti.|  
|[sp_trace_create &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)|Crea la definizione di una nuova traccia nello stato arrestato.|  
|[sp_trace_generateevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)|Crea un evento definito dall'utente.|  
|[sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)|Aggiunge una classe di evento o una colonna dati in una traccia oppure rimuove uno di questi elementi dalla traccia.|  
|[sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)|Avvia, arresta o chiude una traccia.|  
|[sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md)|Restituisce informazioni sui filtri applicati a una traccia.|  
|[sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)|Applica a una traccia un nuovo filtro o un filtro modificato.|  
  
 **Per definire una traccia personalizzata tramite stored procedure**  
  
1.  Tramite **sp_trace_setevent**specificare gli eventi da acquisire.  
  
2.  Specificare eventuali filtri per gli eventi. Per altre informazioni, vedere [Impostare un filtro di traccia &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/set-a-trace-filter-transact-sql.md).  
  
3.  Tramite **sp_trace_create** specificare la destinazione per i dati degli eventi acquisiti.  
  
 Per un esempio dell'uso di stored procedure relative alla traccia, vedere [Creare una traccia &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/create-a-trace-transact-sql.md).  
  
 **Per impostare i valori predefiniti per la definizione della traccia**  
  
 [SQL Server Profiler](../../tools/sql-server-profiler/set-trace-definition-defaults-sql-server-profiler.md)  
  
 **Per impostare i valori predefiniti per la visualizzazione della traccia**  
  
 [SQL Server Profiler](../../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md)  
  
 **Per creare una traccia**  
  
 [SQL Server Profiler](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
 [Transact-SQL](../../relational-databases/sql-trace/create-a-trace-transact-sql.md)  
  
 **Per aggiungere o rimuovere eventi da un modello di traccia**  
  
 [SQL Server Profiler](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
  
 [Transact-SQL](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  

