---
title: query_store_query (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/29/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- QUERY_STORE_QUERY
- SYS.QUERY_STORE_QUERY_TSQL
- SYS.QUERY_STORE_QUERY
- QUERY_STORE_QUERY_TSQL
dev_langs: TSQL
helpviewer_keywords:
- query_store_query catalog view
- sys.query_store_query catalog view
ms.assetid: bdee149e-7556-4fc3-8242-925dd4b7b6ac
caps.latest.revision: "15"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ef06fab57c78c83e4c38993cf0acdaf60fcc0f39
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sysquerystorequery-transact-sql"></a>query_store_query (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Contiene informazioni sulle query e le statistiche di esecuzione di runtime aggregate complessivo associato.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**query_id**|**bigint**|Chiave primaria.|  
|**query_text_id**|**bigint**|Chiave esterna. Crea un join tra [query_store_query_text &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)|  
|**context_settings_id**|**bigint**|Chiave esterna. Crea un join tra [sys.query_context_settings &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md).|  
|**object_id**|**bigint**|ID dell'oggetto di database che fa parte di query (stored procedure, trigger, CLR definita dall'utente/aggregazione definita dall'utente, ecc.). 0 se non viene eseguita la query come parte di un oggetto di database (query ad hoc).|  
|**batch_sql_handle**|**varbinary(64)**|ID del batch di istruzione, la query fa parte di. Popolato solo se la query fa riferimento alle tabelle temporanee o variabili di tabella.|  
|**query_hash**|**Binary (8)**|Hash MD5 della singola query, in base a una struttura della query logica. Include l'hint di ottimizzazione.|  
|**is_internal_query**|**bit**|La query è stata generata internamente.|  
|**query_parameterization_type**|**tinyint**|Tipo di parametrizzazione automatica:<br /><br /> 0: nessuno<br /><br /> 1-utente<br /><br /> 2-semplice<br /><br /> 3 – forzato|  
|**query_parameterization_type_desc**|**nvarchar(60)**|Descrizione per il tipo di parametrizzazione.|  
|**initial_compile_start_time**|**datetimeoffset**|Compilare l'ora di inizio.|  
|**last_compile_start_time**|**datetimeoffset**|Compilare l'ora di inizio.|  
|**last_execution_time**|**datetimeoffset**|Ora dell'ultima esecuzione fa riferimento all'ultima ora di fine del piano di query /.|  
|**last_compile_batch_sql_handle**|**varbinary(64)**|Handle dell'ultimo batch SQL in cui query è stata utilizzata l'ora dell'ultima. Può essere fornito come input per [Sys.dm exec_sql_text &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md) per ottenere il testo completo del batch.|  
|**last_compile_batch_offset_start**|**bigint**|Informazioni che possono essere fornite a Sys.dm exec_sql_text insieme last_compile_batch_sql_handle.|  
|**last_compile_batch_offset_end**|**bigint**|Informazioni che possono essere fornite a Sys.dm exec_sql_text insieme last_compile_batch_sql_handle.|  
|**count_compiles**|**bigint**|Statistiche di compilazione.|  
|**avg_compile_duration**|**float**|Statistiche di compilazione in microsecondi.|  
|**last_compile_duration**|**bigint**|Statistiche di compilazione in microsecondi.|  
|**avg_bind_duration**|**float**|Statistiche di associazione in microsecondi.|  
|**last_bind_duration**|**bigint**|Statistiche di associazione.|  
|**avg_bind_cpu_time**|**float**|Statistiche di associazione.|  
|**last_bind_cpu_time**|**bigint**|Statistiche di associazione.|  
|**avg_optimize_duration**|**float**|Statistiche di ottimizzazione in microsecondi.|  
|**last_optimize_duration**|**bigint**|Statistiche di ottimizzazione.|  
|**avg_optimize_cpu_time**|**float**|Statistiche di ottimizzazione in microsecondi.|  
|**last_optimize_cpu_time**|**bigint**|Statistiche di ottimizzazione.|  
|**avg_compile_memory_kb**|**float**|Compilazione di statistiche di memoria.|  
|**last_compile_memory_kb**|**bigint**|Compilazione di statistiche di memoria.|  
|**max_compile_memory_kb**|**bigint**|Compilazione di statistiche di memoria.|  
|**is_clouddb_internal_query**|**bit**|Restituisce sempre 0 in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] locale.|  
  
## <a name="permissions"></a>Permissions  
 Richiede il **VIEW DATABASE STATE** autorizzazione.  
  
## <a name="see-also"></a>Vedere anche  
 [database_query_store_options &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [Sys.query_context_settings &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [Sys. query_store_plan &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)   
 [query_store_query_text &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)  
 [query_store_runtime_stats &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md)   
 [Sys.query_store_runtime_stats_interval &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [Monitoraggio delle prestazioni tramite Archivio query](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Stored procedure di Archivio query &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)   
 [sys.fn_stmt_sql_handle_from_sql_stmt &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-stmt-sql-handle-from-sql-stmt-transact-sql.md)  
  
  
