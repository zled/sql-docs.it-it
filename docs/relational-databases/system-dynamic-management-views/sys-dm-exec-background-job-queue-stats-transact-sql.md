---
title: sys.dm_exec_background_job_queue_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
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
- dm_exec_background_job_queue_stats
- sys.dm_exec_background_job_queue_stats
- dm_exec_background_job_queue_stats_TSQL
- sys.dm_exec_background_job_queue_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_background_job_queue_stats dynamic management view
ms.assetid: 27f62ab5-46c4-417e-814d-8d6437034d1c
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 5e87278fe60b5314cb84066863acd134212f1887
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmexecbackgroundjobqueuestats-transact-sql"></a>sys.dm_exec_background_job_queue_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce una riga in cui sono visualizzate le statistiche di aggregazione per ogni processo di Query Processor sottomesso per l'esecuzione asincrona (in background).  
  
> [!NOTE]  
>  Per chiamare questo metodo dal [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilizzare il nome **sys.dm_pdw_nodes_exec_background_job_queue_stats**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**queue_max_len**|**int**|Lunghezza massima della coda.|  
|**enqueued_count**|**int**|Numero di richieste inviate correttamente alla coda.|  
|**started_count**|**int**|Numero di richieste di cui è stata avviata l'esecuzione.|  
|**ended_count**|**int**|Numero di richieste elaborate con esito positivo o con esito negativo.|  
|**failed_lock_count**|**int**|Numero di richieste non riuscite a causa di una contesta di blocchi o a causa di deadlock.|  
|**failed_other_count**|**int**|Numero di richieste non riuscite a causa di altri motivi.|  
|**failed_giveup_count**|**int**|Numero di richieste non riuscite perché è stato raggiunto il limite di tentativi.|  
|**enqueue_failed_full_count**|**int**|Numero di tentativi di accodamento non riusciti a causa della coda piena.|  
|**enqueue_failed_duplicate_count**|**int**|Numero di tentativi di accodamento duplicati.|  
|**elapsed_avg_ms**|**int**|Tempo medio trascorso della richiesta in millisecondi.|  
|**elapsed_max_ms**|**int**|Tempo trascorso della richiesta più lunga in millisecondi.|  
|**pdw_node_id**|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L'identificatore per il nodo che utilizza questo tipo di distribuzione.|  
  
## <a name="remarks"></a>Osservazioni  
 In questa vista vengono restituite solo le informazioni relative ai processi asincroni di aggiornamento delle statistiche. Per ulteriori informazioni su aggiornamenti asincroni delle statistiche, vedere [statistiche](../../relational-databases/statistics/statistics.md).  
  
## <a name="permissions"></a>Autorizzazioni

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], richiede `VIEW SERVER STATE` autorizzazione.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], richiede il `VIEW DATABASE STATE` autorizzazione per il database.   

## <a name="examples"></a>Esempi  
  
### <a name="a-determining-the-percentage-of-failed-background-jobs"></a>A. Individuazione della percentuale di processi in background non riusciti  
 Nell'esempio seguente viene restituita la percentuale di processi in background non riusciti per tutte le query eseguite.  
  
```  
SELECT   
        CASE ended_count WHEN 0   
                THEN 'No jobs ended'   
                ELSE CAST((failed_lock_count + failed_giveup_count + failed_other_count) / CAST(ended_count AS float) * 100 AS varchar(20))   
        END AS [Percent Failed]  
FROM sys.dm_exec_background_job_queue_stats;  
GO  
```  
  
### <a name="b-determining-the-percentage-of-failed-enqueue-attempts"></a>B. Individuazione della percentuale di tentativi di accodamento non riusciti  
 Nell'esempio seguente viene restituita la percentuale di tentativi di accodamento non riusciti per tutte le query eseguite.  
  
```  
SELECT   
        CASE enqueued_count WHEN 0   
                THEN 'No jobs posted'   
                ELSE CAST((enqueue_failed_full_count + enqueue_failed_duplicate_count) / CAST(enqueued_count AS float) * 100 AS varchar(20))   
        END AS [Percent Enqueue Failed]  
FROM sys.dm_exec_background_job_queue_stats;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Funzioni e viste a gestione dinamica relative all'esecuzione &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


