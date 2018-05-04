---
title: sys.dm_exec_procedure_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/10/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_procedure_stats_TSQL
- dm_exec_procedure_stats_TSQL
- dm_exec_procedure_stats
- sys.dm_exec_procedure_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_procedure_stats dynamic management view
ms.assetid: ab8ddde8-1cea-4b41-a7e4-697e6ddd785a
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d99985e40a0b8cb04500085852fd431d9f020007
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmexecprocedurestats-transact-sql"></a>sys.dm_exec_procedure_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce dati statistici aggregati sulle prestazioni delle stored procedure memorizzate nella cache. La vista restituisce una riga per ogni piano di stored procedure memorizzato nella cache e la durata della riga è uguale al periodo in cui la stored procedure rimane memorizzata nella cache. Quando una stored procedure viene rimossa dalla cache, la riga corrispondente viene elimina dalla vista. In quel momento, viene generato un evento di traccia di SQL di Performance Statistics simile a **Sys.dm exec_query_stats**.  
  
 In [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], le viste a gestione dinamica non possono esporre le informazioni che influenzerebbero l'indipendenza del database o le informazioni sugli altri database a cui l'utente dispone di accesso. Per evitare di esporre queste informazioni, ogni riga che contiene dati che non appartengono al tenant connesso viene esclusa tramite filtro.  
  
> [!NOTE]
> Una query iniziale di **Sys.dm exec_procedure_stats** potrebbe produrre risultati non accurati se è presente un carico di lavoro attualmente in esecuzione nel server. La riesecuzione della query può garantire risultati più accurati.  
  
> [!NOTE]
> Per chiamare questo metodo dal [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilizzare il nome **sys.dm_pdw_nodes_exec_procedure_stats**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|ID del database in cui è contenuta la stored procedure.|  
|**object_id**|**int**|Numero di identificazione dell'oggetto della stored procedure.|  
|**type**|**char(2)**|Tipo dell'oggetto:<br /><br /> P = stored procedure SQL<br /><br /> PC = stored procedure assembly (CLR)<br /><br /> X = stored procedure estesa|  
|**type_desc**|**nvarchar(60)**|Descrizione del tipo di oggetto:<br /><br /> SQL_STORED_PROCEDURE<br /><br /> CLR_STORED_PROCEDURE<br /><br /> EXTENDED_STORED_PROCEDURE|  
|**sql_handle**|**varbinary(64)**|Può essere utilizzato per correlare le query in **Sys.dm exec_query_stats** eseguite dall'interno della stored procedure.|  
|**plan_handle**|**varbinary(64)**|Identificatore del piano in memoria. Si tratta di un identificatore temporaneo, che rimane costante solo se il piano rimane nella cache. Questo valore può essere utilizzato con il **Sys.dm exec_cached_plans** vista a gestione dinamica.<br /><br /> È sempre 0x000 quando una stored procedure compilata in modo nativo esegue una query su una tabella ottimizzata per la memoria.|  
|**cached_time**|**datetime**|Ora in cui la stored procedure è stata aggiunta alla cache.|  
|**last_execution_time**|**datetime**|Ora dell'ultima esecuzione della stored procedure.|  
|**execution_count**|**bigint**|Il numero di volte in cui la stored procedure è stata eseguita a partire dall'ultima compilazione.|  
|**total_worker_time**|**bigint**|La quantità totale di tempo di CPU, espresso in microsecondi, utilizzato dalle esecuzioni della stored procedure a partire dalla relativa compilazione.<br /><br /> Per le stored procedure compilate in modo nativo, il valore di **total_worker_time** non può essere accurato se più esecuzioni richiedono meno di 1 millisecondo.|  
|**last_worker_time**|**bigint**|Tempo di CPU, in microsecondi, utilizzato durante l'ultima esecuzione della stored procedure. <sup>1</sup>|  
|**min_worker_time**|**bigint**|Tempo minimo di CPU, espresso in microsecondi, stored procedure utilizzato dalla durante una singola esecuzione. <sup>1</sup>|  
|**max_worker_time**|**bigint**|Il tempo massimo di CPU, espresso in microsecondi, stored procedure utilizzato dalla durante una singola esecuzione. <sup>1</sup>|  
|**total_physical_reads**|**bigint**|Numero totale di letture fisiche effettuate dalle esecuzioni della stored procedure dopo l'ultima compilazione.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**last_physical_reads**|**bigint**|Il numero di letture fisiche eseguite l'ora dell'ultima che esecuzione della stored procedure.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**min_physical_reads**|**bigint**|Il numero minimo di letture fisiche effettuate che questa stored procedure durante una singola esecuzione.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**max_physical_reads**|**bigint**|Il numero massimo di letture fisiche effettuate che questa stored procedure durante una singola esecuzione.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**total_logical_writes**|**bigint**|Numero totale di scritture logiche effettuate dalle esecuzioni della stored procedure dopo l'ultima compilazione.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**last_logical_writes**|**bigint**|Il numero di pagine del pool di buffer diventate dirty durante l'ultima volta che è stato eseguito il piano. Se una pagina è già dirty (modificata) le scritture non vengono conteggiate.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**min_logical_writes**|**bigint**|Il numero minimo di scritture logiche effettuate che questa stored procedure durante una singola esecuzione.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**max_logical_writes**|**bigint**|Il numero massimo di scritture logiche effettuate che questa stored procedure durante una singola esecuzione.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**total_logical_reads**|**bigint**|Numero totale di letture logiche effettuate dalle esecuzioni della stored procedure dopo l'ultima compilazione.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**last_logical_reads**|**bigint**|Il numero di letture logiche eseguite l'ora dell'ultima che esecuzione della stored procedure.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**min_logical_reads**|**bigint**|Il numero minimo di letture logiche effettuate che questa stored procedure durante una singola esecuzione.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**max_logical_reads**|**bigint**|Il numero massimo di letture logiche effettuate che questa stored procedure durante una singola esecuzione.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**total_elapsed_time**|**bigint**|Tempo trascorso totale, espresso in microsecondi, per le esecuzioni complete della stored procedure.|  
|**last_elapsed_time**|**bigint**|Il tempo trascorso, in microsecondi, per l'ultima esecuzione completata di questa stored procedure.|  
|**min_elapsed_time**|**bigint**|Tempo minimo trascorso, in microsecondi, per qualsiasi esecuzione completata della stored procedure.|  
|**max_elapsed_time**|**bigint**|Il tempo massimo trascorso, in microsecondi, per qualsiasi esecuzione completata della stored procedure.|  
|**total_spills**|**bigint**|Il numero totale di pagine distribuite tramite l'esecuzione di questa stored procedure dopo l'ultima compilazione.<br /><br /> **Si applica a**: a partire da [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**last_spills**|**bigint**|Il numero di pagine distribuite l'ora dell'ultima che esecuzione della stored procedure.<br /><br /> **Si applica a**: a partire da [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**min_spills**|**bigint**|Il numero minimo di pagine che questa stored procedure ha sempre distribuito durante una singola esecuzione.<br /><br /> **Si applica a**: a partire da [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**max_spills**|**bigint**|Il numero massimo di pagine che questa stored procedure ha sempre distribuito durante una singola esecuzione.<br /><br /> **Si applica a**: a partire da [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**pdw_node_id**|**int**|L'identificatore per il nodo che utilizza questo tipo di distribuzione.<br /><br />**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]|  
  
 <sup>1</sup> per le stored procedure compilate in modo nativo quando la raccolta delle statistiche è abilitata, tempo del processo viene raccolto in millisecondi. Se la query viene eseguita in meno di un millisecondo, il valore sarà 0.  
  
## <a name="permissions"></a>Autorizzazioni  

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], richiede `VIEW SERVER STATE` autorizzazione.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], richiede il `VIEW DATABASE STATE` autorizzazione per il database.   
   
## <a name="remarks"></a>Osservazioni  
 Le statistiche nella vista vengono aggiornate quando viene completata l'esecuzione della stored procedure.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituite informazioni sulle prime dieci stored procedure identificate in base al tempo medio trascorso.  
  
```sql  
SELECT TOP 10 d.object_id, d.database_id, OBJECT_NAME(object_id, database_id) 'proc name',   
    d.cached_time, d.last_execution_time, d.total_elapsed_time,  
    d.total_elapsed_time/d.execution_count AS [avg_elapsed_time],  
    d.last_elapsed_time, d.execution_count  
FROM sys.dm_exec_procedure_stats AS d  
ORDER BY [total_worker_time] DESC;  
```  
  
## <a name="see-also"></a>Vedere anche  
[Funzioni e viste a gestione dinamica relative all'esecuzione &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
[sys.dm_exec_sql_text &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)   
[sys.dm_exec_query_plan &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)    
[sys.dm_exec_query_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)    
[sys.dm_exec_trigger_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)    
[sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)    
  
  


