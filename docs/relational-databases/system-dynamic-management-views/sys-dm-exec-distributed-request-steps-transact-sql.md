---
title: sys.dm_exec_distributed_request_steps (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SYS.DM_EXEC_DISTRIBUTED_REQUEST_STEPS_TSQL
- DM_EXEC_DISTRIBUTED_REQUEST_STEPS_TSQL
- DM_EXEC_DISTRIBUTED_REQUEST_STEPS
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- dm_exec_distributed_request_steps
- sys.dm_exec_distributed_request_steps management view
ms.assetid: 1954541d-b716-4e03-8fcc-7022f428e01d
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 348b78de034f252f5ea9561df53dc69c267d8257
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmexecdistributedrequeststeps-transact-sql"></a>sys.dm_exec_distributed_request_steps (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Contiene informazioni su tutti i passaggi che compongono una query o una richiesta di PolyBase. Contiene una riga per ogni passaggio della query.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|**int**|valore di execution_id e step_index costituiscono la chiave per la visualizzazione. Id numerico univoco associato alla richiesta.|Vedere ID in [Sys.dm exec_requests &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|step_index|**int**|La posizione di questo passaggio della sequenza di passaggi che costituiscono la richiesta.|0 (n-1) per una richiesta con passaggi n.|  
|operation_type|**nvarchar(128)**|Tipo di operazione rappresentato da questo passaggio.|'MoveOperation','OnOperation','RandomIDOperation','RemoteOperation','ReturnOperation','ShuffleMoveOperation','TempTablePropertiesOperation','DropDiagnosticsNotifyOperation', ‘HadoopShuffleOperation', ‘HadoopBroadCastOperation', ‘HadoopRoundRobinOperation'|  
|distribution_type|**nvarchar(32)**|In cui è in esecuzione il passaggio.|‘AllComputeNodes','AllDistributions','ComputeNode','Distribution','AllNodes','SubsetNodes','SubsetDistributions','Unspecified'.|  
|location_type|**nvarchar(32)**|In cui è in esecuzione il passaggio.|'Compute', 'Testa' o 'DMS'. Tutti i passaggi di spostamento di dati mostrano 'DMS'.|  
|status|**nvarchar(32)**|Stato del passaggio|'Sospeso', 'Running', 'Completato', 'Non riuscita', 'UndoFailed', 'PendingCancel', 'annullato', 'Annullate', 'Interrotta'|  
|error_id|**nvarchar(36)**|Id univoco dell'errore associato con questo passaggio, se presente|Id di vedere [sys.dm_exec_compute_node_errors &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-node-errors-transact-sql.md), NULL se si è verificato alcun errore.|  
|start_time|**datetime**|Ora di inizio esecuzione il passaggio|Minore o uguale all'ora corrente e maggiori o uguali a end_compile_time della query a cui appartiene questo passaggio.|  
|end_time|**datetime**|Ora in cui questo passaggio ha completato l'esecuzione, è stato annullato o non è riuscito.|Minore o uguale all'ora corrente e maggiore o uguale a start_time, impostato su NULL per i passaggi attualmente in esecuzione o in coda.|  
|total_elapsed_time|**int**|Quantità totale di tempo, che il passaggio della query è stato in esecuzione, in millisecondi|Compreso tra 0 e la differenza tra start_time ed end_time. 0 per i passaggi in coda.|  
|row_count|**bigint**|Numero totale di righe modificate o restituita da questa richiesta|0 per i passaggi che non modificare o restituire dati, numero di righe interessate in caso contrario. Impostare su -1 per i passaggi DMS.|  
|comando|nvarchar(4000)|Contiene il testo completo del comando di questo passaggio.|Qualsiasi stringa di richiesta valido per un passaggio. Troncata se supera i 4000 caratteri.|  
  
## <a name="see-also"></a>Vedere anche  
 [PolyBase, risoluzione dei problemi con viste a gestione dinamica](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Viste a gestione dinamica &#40; correlati al database Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
