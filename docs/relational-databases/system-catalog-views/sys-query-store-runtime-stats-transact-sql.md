---
title: query_store_runtime_stats (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/29/2016
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
- SYS.QUERY_STORE_RUNTIME_STATS_TSQL
- QUERY_STORE_RUNTIME_STATS_TSQL
- SYS.QUERY_STORE_RUNTIME_STATS
- QUERY_STORE_RUNTIME_STATS
dev_langs:
- TSQL
helpviewer_keywords:
- query_store_runtime_stats catalog view
- sys.query_store_runtime_stats catalog view
ms.assetid: ccf7a57c-314b-450c-bd34-70749a02784a
caps.latest.revision: 18
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 59e280a58f0b220ea7bff6f530833f16ba69dfe3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sysquerystoreruntimestats-transact-sql"></a>query_store_runtime_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Contiene informazioni sulle informazioni sulle statistiche di esecuzione di runtime per la query.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**runtime_stats_id**|**bigint**|Identificatore della riga che rappresenta le statistiche di esecuzione di runtime per il **plan_id**, **execution_type** e **runtime_stats_interval_id**. È univoco solo per gli intervalli delle statistiche di runtime precedenti. Per l'intervallo attualmente attivo potrebbe essere più righe che rappresenta le statistiche di runtime per il piano a cui fa riferimento **plan_id**, con il tipo di esecuzione rappresentato da **execution_type**. In genere, una riga rappresenta le statistiche di runtime vengono scaricate su disco, mentre altri (s) rappresentano lo stato in memoria. Di conseguenza, per ottenere lo stato effettivo per ogni intervallo occorre metrica di aggregazione, raggruppamento per **plan_id**, **execution_type** e **runtime_stats_interval_id**. |  
|**plan_id**|**bigint**|Chiave esterna. Unisce in join alla [Sys. query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md).|  
|**runtime_stats_interval_id**|**bigint**|Chiave esterna. Unisce in join alla [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md).|  
|**execution_type**|**tinyint**|Determina l'esecuzione di query di tipo:<br /><br /> 0 – esecuzione normale (completata)<br /><br /> 3-client ha avviato interrotto l'esecuzione<br /><br /> 4 - eccezione interrotto l'esecuzione|  
|**execution_type_desc**|**nvarchar(128)**|Descrizione testuale del campo di tipo di esecuzione:<br /><br /> 0-normale<br /><br /> 3 – interrotta<br /><br /> 4 - eccezione|  
|**first_execution_time**|**datetimeoffset**|Tempo di esecuzione prima del piano di query entro l'intervallo di aggregazione.|  
|**last_execution_time**|**datetimeoffset**|Ora dell'ultima esecuzione della query prevede entro l'intervallo di aggregazione.|  
|**count_executions**|**bigint**|Numero totale di esecuzioni del piano di query entro l'intervallo di aggregazione.|  
|**avg_duration**|**float**|La durata del piano di query entro l'intervallo di aggregazione (espresso in microsecondi).|  
|**last_duration**|**bigint**|Durata ultima per la query pianificare entro l'intervallo di aggregazione (espresso in microsecondi).|  
|**min_duration**|**bigint**|Durata minima per il piano di query entro l'intervallo di aggregazione (espresso in microsecondi).|  
|**max_duration**|**bigint**|Durata massima per il piano di query entro l'intervallo di aggregazione (espresso in microsecondi).|  
|**stdev_duration**|**float**|Deviazione standard di durata del piano di query entro l'intervallo di aggregazione (espresso in microsecondi).|  
|**avg_cpu_time**|**float**|Tempo medio di CPU per il piano di query entro l'intervallo di aggregazione (espresso in microsecondi).|  
|**last_cpu_time**|**bigint**|Ultimo tempo di CPU per la query pianificare entro l'intervallo di aggregazione (espresso in microsecondi).|  
|**min_cpu_time**|**bigint**|Tempo minimo di CPU per il piano di query entro l'intervallo di aggregazione (espresso in microsecondi).|  
|**max_cpu_time**|**bigint**|Tempo massimo della CPU per il piano di query entro l'intervallo di aggregazione (espresso in microsecondi).|  
|**stdev_cpu_time**|**float**|Deviazione standard di tempo della CPU per il piano di query entro l'intervallo di aggregazione (espresso in microsecondi).|  
|**avg_logical_io_reads**|**float**|Numero medio dei / o logiche legge del piano di query entro l'intervallo di aggregazione. (espressa in numero di pagine da 8KB lettura).|  
|**last_logical_io_reads**|**bigint**|Ultimo numero dei / o logiche legge del piano di query entro l'intervallo di aggregazione. (espressa in numero di pagine da 8KB lettura).|  
|**min_logical_io_reads**|**bigint**|Numero minimo dei / o logiche legge del piano di query entro l'intervallo di aggregazione. (espressa in numero di pagine da 8KB lettura).|  
|**max_logical_io_reads**|**bigint**|Numero massimo dei / o logiche legge del piano di query entro l'intervallo di aggregazione. (espressa in numero di pagine da 8KB lettura). |  
|**stdev_logical_io_reads**|**float**|Numero dei / o logiche legge la deviazione standard per il piano di query entro l'intervallo di aggregazione. (espressa in numero di pagine da 8KB lettura).|  
|**avg_logical_io_writes**|**float**|Numero medio dei / o logiche scrive per il piano di query entro l'intervallo di aggregazione.|  
|**last_logical_io_writes**|**bigint**|Ultimo numero dei / o logiche scrive per il piano di query entro l'intervallo di aggregazione.|  
|**min_logical_io_writes**|**bigint**|Numero minimo dei / o logiche scrive per il piano di query entro l'intervallo di aggregazione.|  
|**max_logical_io_writes**|**bigint**|Numero massimo dei / o logiche scrive per il piano di query entro l'intervallo di aggregazione.|  
|**stdev_logical_io_writes**|**float**|Numero dei / o logiche scrive la deviazione standard per il piano di query entro l'intervallo di aggregazione.|  
|**avg_physical_io_reads**|**float**|Numero medio dei / o fisico legge del piano di query entro l'intervallo di aggregazione (espressa in numero di pagine da 8KB lettura).|  
|**last_physical_io_reads**|**bigint**|Ultimo numero dei / o fisico Letture del piano di query entro l'intervallo di aggregazione (espressa in numero di pagine da 8KB lettura).|  
|**min_physical_io_reads**|**bigint**|Numero minimo dei / o fisico legge del piano di query entro l'intervallo di aggregazione (espressa in numero di pagine da 8KB lettura).|  
|**max_physical_io_reads**|**bigint**|Numero massimo dei / o fisico legge del piano di query entro l'intervallo di aggregazione (espressa in numero di pagine da 8KB lettura).|  
|**stdev_physical_io_reads**|**float**|Numero dei / o fisico legge la deviazione standard per il piano di query entro l'intervallo di aggregazione (espressa in numero di pagine da 8KB lettura).|  
|**avg_clr_time**|**float**|Tempo medio di CLR per il piano di query entro l'intervallo di aggregazione (espresso in microsecondi).|  
|**last_clr_time**|**bigint**|Ultima ora CLR per la query pianificare entro l'intervallo di aggregazione (espresso in microsecondi).|  
|**min_clr_time**|**bigint**|Tempo minimo di CLR per il piano di query entro l'intervallo di aggregazione (espresso in microsecondi).|  
|**max_clr_time**|**bigint**|Tempo massimo di CLR per il piano di query entro l'intervallo di aggregazione (espresso in microsecondi).|  
|**stdev_clr_time**|**float**|Deviazione standard di Common Language Runtime ora per il piano di query entro l'intervallo di aggregazione (espresso in microsecondi).|  
|**avg_dop**|**float**|Media DOP (grado di parallelismo) per il piano di query entro l'intervallo di aggregazione.|  
|**last_dop**|**bigint**|Ultimi DOP (grado di parallelismo) per il piano di query entro l'intervallo di aggregazione.|  
|**min_dop**|**bigint**|Minimo DOP (grado di parallelismo) per il piano di query entro l'intervallo di aggregazione.|  
|**max_dop**|**bigint**|Massimo grado di Parallelismo (grado di parallelismo) per il piano di query entro l'intervallo di aggregazione.|  
|**stdev_dop**|**float**|Deviazione standard DOP (grado di parallelismo) per il piano di query entro l'intervallo di aggregazione.|  
|**avg_query_max_used_memory**|**float**|Media concessione di memoria (indicato come il numero di pagine da 8 KB) per il piano di query entro l'intervallo di aggregazione. Sempre 0 per le query che utilizzano in modo nativo compilati procedure di ottimizzazione per la memoria.|  
|**last_query_max_used_memory**|**bigint**|Ultimo concessione di memoria (indicato come il numero di pagine da 8 KB) per il piano di query entro l'intervallo di aggregazione. Sempre 0 per le query che utilizzano in modo nativo compilati procedure di ottimizzazione per la memoria.|  
|**min_query_max_used_memory**|**bigint**|Minima concessione di memoria (indicato come il numero di pagine da 8 KB) per il piano di query entro l'intervallo di aggregazione. Sempre 0 per le query che utilizzano in modo nativo compilati procedure di ottimizzazione per la memoria.|  
|**max_query_max_used_memory**|**bigint**|Massima concessione di memoria (indicato come il numero di pagine da 8 KB) per il piano di query entro l'intervallo di aggregazione. Sempre 0 per le query che utilizzano in modo nativo compilati procedure di ottimizzazione per la memoria.|  
|**stdev_query_max_used_memory**|**float**|Deviazione standard (indicata come il numero di pagine da 8 KB) concessione di memoria per il piano di query entro l'intervallo di aggregazione. Sempre 0 per le query che utilizzano in modo nativo compilati procedure di ottimizzazione per la memoria.|  
|**avg_rowcount**|**float**|Numero medio di righe restituite per il piano di query entro l'intervallo di aggregazione.|  
|**last_rowcount**|**bigint**|Numero di righe restituite durante l'ultima esecuzione del piano di query entro l'intervallo di aggregazione.|  
|**min_rowcount**|**bigint**|Numero minimo di righe restituite per la query pianificazione entro l'intervallo di aggregazione.|  
|**max_rowcount**|**bigint**|Numero massimo di righe restituite per la query pianificazione entro l'intervallo di aggregazione.|  
|**stdev_rowcount**|**float**|Numero di righe restituite di deviazione standard per il piano di query entro l'intervallo di aggregazione.|
|**avg_log_bytes_used**|**float**|Numero medio di byte nel log del database utilizzato dal piano di query, entro l'intervallo di aggregazione. Si applica **solo al Database SQL di Azure**.|    
|**last_log_bytes_used**|**bigint**|Numero di byte nel log del database utilizzato durante l'ultima esecuzione del piano di query, entro l'intervallo di aggregazione. Si applica **solo al Database SQL di Azure**.|  
|**min_log_bytes_used**|**bigint**|Numero minimo di byte nel log del database utilizzato dal piano di query, entro l'intervallo di aggregazione.  Si applica **solo al Database SQL di Azure**.|  
|**max_log_bytes_used**|**bigint**|Numero massimo di byte nel log del database utilizzato dal piano di query, entro l'intervallo di aggregazione.  Si applica **solo al Database SQL di Azure**.| 
|**stdev_log_bytes_used**|**float**|Deviazione standard del numero di byte nel log del database utilizzato da un piano di query, entro l'intervallo di aggregazione.  Si applica **solo al Database SQL di Azure**.|
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede il **VIEW DATABASE STATE** autorizzazione.  
  
## <a name="see-also"></a>Vedere anche  
 [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys.query_context_settings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [sys.query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)   
 [sys.query_store_query &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)   
 [sys.query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)  
 [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [Monitoraggio delle prestazioni tramite Archivio query](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Stored procedure di archivio query &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  
  
  
