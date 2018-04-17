---
title: sys.query_store_wait_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 04/21/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.query_store_wait_stats
- query_store_wait_stats
dev_langs:
- TSQL
helpviewer_keywords:
- query_store_wait_stats catalog view
- sys.query_store_wait_stats catalog view
ms.assetid: ccf7a57c-314b-450c-bd34-70749a02784a
caps.latest.revision: 18
author: AndrejsAnt
ms.author: AndrejsAnt
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2017 || = sqlallproducts-allversions
ms.openlocfilehash: cd60e0132c29fdfa2461112aa1220d149c9ad2db
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sysquerystorewaitstats-transact-sql"></a>sys.query_store_wait_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  Contiene informazioni sulle informazioni attesa per la query.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**wait_stats_id**|**bigint**|Identificatore della riga che rappresenta le statistiche di attesa per il valore plan_id, runtime_stats_interval_id, execution_type e wait_category. È univoco solo per gli intervalli delle statistiche di runtime precedenti. Per l'intervallo attualmente attivo può essere più righe che rappresenta le statistiche di attesa per il piano a cui fa riferimento plan_id, con il tipo di esecuzione rappresentato da execution_type e categoria di attesa rappresentato da wait_category. In genere, una riga rappresenta le statistiche di attesa che vengono scaricate su disco, mentre altri (s) rappresentano lo stato in memoria. Di conseguenza, per ottenere lo stato effettivo per ogni intervallo occorre metrica di aggregazione, raggruppamento plan_id, runtime_stats_interval_id, execution_type e wait_category. |  
|**plan_id**|**bigint**|Chiave esterna. Unisce in join alla [Sys. query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md).|  
|**runtime_stats_interval_id**|**bigint**|Chiave esterna. Unisce in join alla [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md).|  
|**wait_category**|**tinyint**|Tipi di attesa sono suddivisi in categorie utilizzando la tabella seguente e quindi il tempo di attesa verrà aggregato queste categorie di attesa. Per le varie categorie di attesa è necessario un'analisi di completamento diversa per risolvere il problema. Per i tipi di attesa della stessa categoria la risoluzione dei problemi è invece molto simile. Specificando la query interessata come prima nelle attese, si indica la parte mancante necessaria a completare le analisi in modo corretto.|
|**wait_category_desc**|**nvarchar(128)**|Per la descrizione testuale del campo categoria attesa, vedere la tabella seguente.|
|**execution_type**|**tinyint**|Determina l'esecuzione di query di tipo:<br /><br /> 0 – esecuzione normale (completata)<br /><br /> 3-client ha avviato interrotto l'esecuzione<br /><br /> 4 - eccezione interrotto l'esecuzione|  
|**execution_type_desc**|**nvarchar(128)**|Descrizione testuale del campo di tipo di esecuzione:<br /><br /> 0-normale<br /><br /> 3 – interrotta<br /><br /> 4 - eccezione|  
|**total_query_wait_time_ms**|**bigint**|CPU totale tempo di attesa per il piano di query entro l'intervallo di aggregazione e categoria (espresso in millisecondi) di attesa.|
|**avg_query_wait_time_ms**|**float**|Media durata dell'attesa per il piano di query per ogni esecuzione all'interno della categoria di attesa e di intervallo di aggregazione (espresso in millisecondi).|
|**last_query_wait_time_ms**|**bigint**|Ultima durata dell'attesa per il piano di query entro l'intervallo di aggregazione e categoria (espresso in millisecondi) di attesa.|
|**min_query_wait_time_ms**|**bigint**|CPU minima di tempo di attesa per il piano di query entro l'intervallo di aggregazione e categoria (espresso in millisecondi) di attesa.|
|**max_query_wait_time_ms**|**bigint**|Numero massimo di CPU, tempo di attesa per il piano di query entro l'intervallo di aggregazione e categoria (espresso in millisecondi) di attesa.|
|**stdev_query_wait_time_ms**|**float**|Query wait deviazione standard di durata del piano di query entro l'intervallo di aggregazione e categoria (espresso in millisecondi) di attesa.|

 ## <a name="wait-categories-mapping-table"></a>Tabella di mapping di categorie di attesa  
  *"%" viene utilizzato come carattere jolly*
  
|Valore integer|Categoria di attesa|Tipi di attesa includono nella categoria|  
|-----------------|---------------|-----------------|  
|**0**|**Unknown**|Unknown |  
|**1**|**CPU**|SOS_SCHEDULER_YIELD|
|**2**|**Thread di lavoro**|THREADPOOL|
|**3**|**blocco**|LCK_M_%|
|**4**|**Latch**|LATCH_%|
|**5**|**Latch del buffer**|PAGELATCH_%|
|**6**|**Buffer dei / o**|PAGEIOLATCH_%|
|**7**|**Compilazione***|RESOURCE_SEMAPHORE_QUERY_COMPILE|
|**8**|**CLR SQL**|CLR%, SQLCLR%|
|**9**|**Il mirroring**|% DBMIRROR|
|**10**|**Transazione**|XACT%, DTC%, TRAN_MARKLATCH_%, MSQL_XACT_%, TRANSACTION_MUTEX|
|**11**|**Inattività**|% SLEEP_, LAZYWRITER_SLEEP, SQLTRACE_BUFFER_FLUSH, SQLTRACE_INCREMENTAL_FLUSH_SLEEP, SQLTRACE_WAIT_ENTRIES, FT_IFTS_SCHEDULER_IDLE_WAIT, XE_DISPATCHER_WAIT, REQUEST_FOR_DEADLOCK_SEARCH, LOGMGR_QUEUE, ONDEMAND_TASK_QUEUE, CHECKPOINT_ CODA, XE_TIMER_EVENT|
|**12**|**Preemptive**|% PREEMPTIVE_|
|**13**|**Service Broker**|% BROKER_ **(ma non BROKER_RECEIVE_WAITFOR)**|
|**14**|**Log di TRAN i/o**|LOGMGR, LOGBUFFER, LOGMGR_RESERVE_APPEND, LOGMGR_FLUSH, LOGMGR_PMM_LOG, CHKPT, WRITELOGF|
|**15**|**IO di rete**|ASYNC_NETWORK_IO, NET_WAITFOR_PACKET, PROXY_NETWORK_IO, EXTERNAL_SCRIPT_NETWORK_IOF|
|**16**|**Parallelism**|CXPACKET, EXCHANGE|
|**17**|**Memoria**|RESOURCE_SEMAPHORE, CMEMTHREAD, CMEMPARTITIONED, EE_PMOLOCK, MEMORY_ALLOCATION_EXT, RESERVED_MEMORY_ALLOCATION_EXT, MEMORY_GRANT_UPDATE|
|**18**|**Attesa utente**|WAITFOR, WAIT_FOR_RESULTS, BROKER_RECEIVE_WAITFOR|
|**19**|**Traccia**|TRACEWRITE, SQLTRACE_LOCK, SQLTRACE_FILE_BUFFER, SQLTRACE_FILE_WRITE_IO_COMPLETION, SQLTRACE_FILE_READ_IO_COMPLETION, SQLTRACE_PENDING_BUFFER_WRITERS, SQLTRACE_SHUTDOWN, QUERY_TRACEOUT, TRACE_EVTNOTIFF|
|**20**|**Ricerca full-Text**|FT_RESTART_CRAWL, FULLTEXT GATHERER, MSSEARCH, FT_METADATA_MUTEX, FT_IFTSHC_MUTEX, FT_IFTSISM_MUTEX, FT_IFTS_RWLOCK, FT_COMPROWSET_RWLOCK, FT_MASTER_MERGE, FT_PROPERTYLIST_CACHE, FT_MASTER_MERGE_COORDINATOR, PWAIT_RESOURCE_SEMAPHORE_FT_PARALLEL_QUERY_SYNC|
|**21**|**Altri IO disco**|ASYNC_IO_COMPLETION, IO_COMPLETION, BACKUPIO, WRITE_COMPLETION, IO_QUEUE_LIMIT, IO_RETRY|
|**22**|**Replica**|SE_REPL_ %, % REPL_, HADR_ % **(ma non HADR_THROTTLE_LOG_RATE_GOVERNOR)**, PWAIT_HADR_ %, REPLICA_WRITES, FCB_REPLICA_WRITE, FCB_REPLICA_READ, PWAIT_HADRSIM|
|**23**|**Rate Governor di log**|LOG_RATE_GOVERNOR, POOL_LOG_RATE_GOVERNOR, HADR_THROTTLE_LOG_RATE_GOVERNOR, INSTANCE_LOG_RATE_GOVERNOR|

***Compilazione** categoria attesa non è attualmente supportato. 

  
## <a name="permissions"></a>Autorizzazioni  
 Richiede il **VIEW DATABASE STATE** autorizzazione.  
  
## <a name="see-also"></a>Vedere anche  
 [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys.query_context_settings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [sys.query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)   
 [sys.query_store_query &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)   
 [sys.query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [Monitoraggio delle prestazioni tramite Archivio query](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Stored procedure di archivio query &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  
  
  
