---
title: sys.dm_exec_query_parallel_workers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-non-specified
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
- dm_exec_query_parallel_workers_TSQL
- dm_exec_query_parallel_workers
- sys.dm_exec_query_parallel_workers_TSQL
- sys.dm_exec_query_parallel_workers
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_parallel_workers dynamic management view
ms.assetid: 1d72cef1-22d8-4ae0-91db-6694fe918c9f
caps.latest.revision: 1
author: pelopes
ms.author: pelopes
manager: ajayj
ms.workload: Inactive
ms.openlocfilehash: d320796103853ab4cf0724d1157e0d926ecdc1e0
ms.sourcegitcommit: 8b332c12850c283ae413e0b04b2b290ac2edb672
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/05/2018
---
# <a name="sysdmexecqueryparallelworkers-transact-sql"></a>sys.dm_exec_query_parallel_workers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Restituisce informazioni sulla disponibilità di lavoro per ogni nodo.  
  
|Nome|Tipo di dati|Description|  
|----------|---------------|-----------------|  
|**node_id**|**int**|ID del nodo NUMA.|  
|**scheduler_count**|**int**|Numero di utilità di pianificazione nel nodo.|  
|**max_worker_count**|**int**|Numero massimo di thread di lavoro per query parallele.|  
|**reserved_worker_count**|**int**|Numero di processi di lavoro riservati da query parallele, più il numero di lavori principali utilizzato da tutte le richieste.| 
|**free_worker_count**|**int**|Numero di processi di lavoro disponibili per le attività.<br /><br />**Nota:** tutte le richieste in ingresso utilizza almeno 1 thread di lavoro, viene sottratto il conteggio di lavoro disponibile.  È possibile che il numero di lavoro può essere un numero negativo su un server con carico elevato.| 
|**used_worker_count**|**int**|Numero di lavori utilizzati da query parallele.|  
  
## <a name="permissions"></a>Autorizzazioni  

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], richiede `VIEW SERVER STATE` autorizzazione.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], richiede il `VIEW DATABASE STATE` autorizzazione per il database.   
 
## <a name="examples"></a>Esempi  
  
### <a name="a-viewing-current-parallel-worker-availability"></a>A. Visualizzazione corrente della disponibilità di un lavoro parallelo  

```sql 
SELECT * FROM sys.dm_exec_query_parallel_workers;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Funzioni e viste a gestione dinamica relative all'esecuzione &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_os_workers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md)
