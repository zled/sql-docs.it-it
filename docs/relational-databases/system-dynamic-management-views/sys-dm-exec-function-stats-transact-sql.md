---
title: Sys.dm exec_function_stats (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- sys.dm_exec_function_stats
- sys.dm_exec_function_stats_tsql
- dm_exec_function_stats
- dm_exec_function_stats_tsql
helpviewer_keywords:
- sys.dm_exec_function_stats dynamic management view
ms.assetid: 4c3d6a02-08e4-414b-90be-36b89a0e5a3a
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: c85e25130214a6b12e630c186f275e75efd4b3d0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmexecfunctionstats-transact-sql"></a>sys.dm_exec_function_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Restituisce le statistiche sulle prestazioni per le funzioni memorizzati nella cache di aggregazione. La vista restituisce una riga per ogni piano funzione memorizzata nella cache e la durata della riga fino a quando la funzione rimane nella cache. Quando una funzione viene rimosso dalla cache, la riga corrispondente viene eliminata dalla vista. In quel momento, viene generato un evento di traccia di SQL di Performance Statistics simile a **Sys.dm exec_query_stats**. Restituisce informazioni sulle funzioni scalari, comprese le funzioni in memoria e le funzioni scalari CLR. Non restituisce informazioni sulle funzioni con valori di tabella.  
  
 In [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], le viste a gestione dinamica non possono esporre le informazioni che influenzerebbero l'indipendenza del database o le informazioni sugli altri database a cui l'utente dispone di accesso. Per evitare di esporre queste informazioni, ogni riga che contiene dati che non appartengono al tenant connesso viene esclusa tramite filtro.  
  
> [!NOTE]
> Una query iniziale di **Sys.dm exec_function_stats** potrebbe produrre risultati non accurati se è presente un carico di lavoro attualmente in esecuzione nel server. La riesecuzione della query può garantire risultati più accurati.  
  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|ID del database in cui risiede la funzione.|  
|**object_id**|**int**|Numero di identificazione di oggetto della funzione.|  
|**type**|**char(2)**|Tipo di oggetto: FN = funzioni a valori scalari|  
|**type_desc**|**nvarchar(60)**|Descrizione del tipo di oggetto: SQL_SCALAR_FUNCTION|  
|**sql_handle**|**varbinary(64)**|Può essere utilizzato per correlare le query in **Sys.dm exec_query_stats** che sono stati eseguiti dall'interno di questa funzione.|  
|**plan_handle**|**varbinary(64)**|Identificatore del piano in memoria. Si tratta di un identificatore temporaneo, che rimane costante solo se il piano rimane nella cache. Questo valore può essere utilizzato con il **Sys.dm exec_cached_plans** vista a gestione dinamica.<br /><br /> Sarà sempre 0x000 quando una tabella di query ottimizzato della memoria della funzione compilata in modo nativo.|  
|**cached_time**|**datetime**|Ora in cui la funzione è stato aggiunto alla cache.|  
|**last_execution_time**|**datetime**|Ultima volta in cui è stata eseguita la funzione.|  
|**execution_count**|**bigint**|Numero di volte che la funzione è stata eseguita a partire dall'ultima compilazione.|  
|**total_worker_time**|**bigint**|Quantità totale di tempo CPU, in microsecondi, utilizzato dalle esecuzioni della funzione dopo l'ultima compilazione.<br /><br /> Per le funzioni compilate in modo nativo, **total_worker_time** potrebbe non essere accurato se più esecuzioni richiedono meno di 1 millisecondo.|  
|**last_worker_time**|**bigint**|Tempo di CPU, espresso in microsecondi, utilizzato durante l'ultima volta che è stata eseguita la funzione. <sup>1</sup>|  
|**min_worker_time**|**bigint**|Tempo minimo di CPU, in microsecondi, questa funzione è utilizzato dal durante una singola esecuzione. <sup>1</sup>|  
|**max_worker_time**|**bigint**|Tempo di CPU massimo, in microsecondi, questa funzione è utilizzato dal durante una singola esecuzione. <sup>1</sup>|  
|**total_physical_reads**|**bigint**|Numero totale di letture fisiche effettuate dalle esecuzioni della funzione dopo l'ultima compilazione.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**last_physical_reads**|**bigint**|Numero di letture fisiche eseguite l'ultima volta che è stata eseguita la funzione.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**min_physical_reads**|**bigint**|Numero minimo di letture fisiche che questa funzione effettuate durante una singola esecuzione.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**max_physical_reads**|**bigint**|Numero massimo di letture fisiche che questa funzione effettuate durante una singola esecuzione.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**total_logical_writes**|**bigint**|Numero totale di scritture logiche effettuate dalle esecuzioni della funzione dopo l'ultima compilazione.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**last_logical_writes**|**bigint**|Numero del numero di pagine del pool di buffer diventate dirty durante l'ultima esecuzione del piano. Se una pagina è già dirty (modificata) le scritture non vengono conteggiate.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**min_logical_writes**|**bigint**|Numero minimo di scritture logiche che questa funzione effettuate durante una singola esecuzione.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**max_logical_writes**|**bigint**|Numero massimo di scritture logiche che questa funzione effettuate durante una singola esecuzione.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**total_logical_reads**|**bigint**|Numero totale di letture logiche effettuate dalle esecuzioni della funzione dopo l'ultima compilazione.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**last_logical_reads**|**bigint**|Numero di letture logiche eseguite l'ultima volta che è stata eseguita la funzione.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**min_logical_reads**|**bigint**|Numero minimo di letture logiche effettuate questa funzione durante una singola esecuzione.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**max_logical_reads**|**bigint**|Numero massimo di letture logiche effettuate questa funzione durante una singola esecuzione.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**total_elapsed_time**|**bigint**|Tempo totale trascorso, in microsecondi, per le esecuzioni completate di questa funzione.|  
|**last_elapsed_time**|**bigint**|Tempo trascorso, espresso in microsecondi, per l'ultima esecuzione completata di questa funzione.|  
|**min_elapsed_time**|**bigint**|Tempo minimo trascorso, in microsecondi, per qualsiasi esecuzione completata di questa funzione.|  
|**max_elapsed_time**|**bigint**|Tempo massimo trascorso, in microsecondi, per qualsiasi esecuzione completata di questa funzione.|  
  
## <a name="permissions"></a>Autorizzazioni  

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], richiede `VIEW SERVER STATE` autorizzazione.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], richiede il `VIEW DATABASE STATE` autorizzazione per il database.   
  
## <a name="examples"></a>Esempi  
 L'esempio seguente restituisce informazioni sulle funzioni prime dieci identificato dal tempo medio trascorso.  
  
```  
SELECT TOP 10 d.object_id, d.database_id, OBJECT_NAME(object_id, database_id) 'function name',   
    d.cached_time, d.last_execution_time, d.total_elapsed_time,  
    d.total_elapsed_time/d.execution_count AS [avg_elapsed_time],  
    d.last_elapsed_time, d.execution_count  
FROM sys.dm_exec_function_stats AS d  
ORDER BY [total_worker_time] DESC;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica relative all'esecuzione &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_exec_sql_text &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)   
 [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)   
 
 [sys.dm_exec_trigger_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)   
 [sys.dm_exec_procedure_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)  
  
  
