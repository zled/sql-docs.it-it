---
title: sys.dm_pdw_request_steps (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/01/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.component: dmv's
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: cc563e88-0d34-436e-b914-b60d6ee0d50b
caps.latest.revision: 10
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: f5eba0cc108b18f4e093dbf6935230747910d2c3
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmpdwrequeststeps-transact-sql"></a>sys.dm_pdw_request_steps (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contiene informazioni su tutti i passaggi che costituiscono una determinata richiesta o una query nel [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Contiene una riga per ogni passaggio della query.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|request_id e step_index costituiscono la chiave per la visualizzazione.<br /><br /> Id numerico univoco associato alla richiesta.|Vedere request_id in [sys.dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|request_id e step_index costituiscono la chiave per la visualizzazione.<br /><br /> La posizione di questo passaggio della sequenza di passaggi che costituiscono la richiesta.|0 (n-1) per una richiesta con passaggi n.|  
|operation_type|**nvarchar(35)**|Tipo di operazione rappresentata da questo passaggio.|**Operazioni di piano di query DMS:** 'ReturnOperation', 'PartitionMoveOperation', 'MoveOperation', 'BroadcastMoveOperation', 'ShuffleMoveOperation', 'TrimMoveOperation', 'CopyOperation', 'DistributeReplicatedTableMoveOperation'<br /><br /> **Operazioni di piano di query SQL:** 'OnOperation', 'RemoteOperation'<br /><br /> **Altre operazioni del piano di query:** 'MetaDataCreateOperation', 'RandomIDOperation'<br /><br /> **Le operazioni esterne per le letture:** 'HadoopShuffleOperation', 'HadoopRoundRobinOperation', 'HadoopBroadcastOperation'<br /><br /> **Le operazioni esterne per MapReduce:** 'HadoopJobOperation', 'HdfsDeleteOperation'<br /><br /> **Le operazioni esterne per operazioni di scrittura:** 'ExternalExportDistributedOperation', 'ExternalExportReplicatedOperation', 'ExternalExportControlOperation'<br /><br /> Per ulteriori informazioni, vedere "Informazioni sui piani di Query" nel [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].|  
|distribution_type|**nvarchar(32)**|Tipo di distribuzione di che questo passaggio verrà sottoposta ad.|'AllNodes', 'AllDistributions', 'AllComputeNodes', 'ComputeNode', 'Distribution', 'SubsetNodes', 'SubsetDistributions', 'Unspecified'|  
|location_type|**nvarchar(32)**|In cui viene eseguito il passaggio.|'Compute', 'Control', 'DMS'|  
|status|**nvarchar(32)**|Stato di questo passaggio.|In sospeso, in esecuzione, completata, non è riuscita, UndoFailed, PendingCancel, annullato, il rollback, interrotto|  
|error_id|**nvarchar(36)**|Id univoco dell'errore associato con questo passaggio, se presente.|Vedere di error_id [sys.dm_pdw_errors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md). NULL se si è verificato alcun errore.|  
|start_time|**datetime**|Ora di inizio esecuzione il passaggio.|Minore o uguale all'ora corrente e maggiori o uguali a end_compile_time della query a cui appartiene questo passaggio. Per ulteriori informazioni sulle query, vedere [sys.dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|end_time|**datetime**|Ora in cui questo passaggio ha completato l'esecuzione, è stato annullato o non è riuscito.|Minore o uguale all'ora corrente e maggiore o uguale a start_time. Impostare su NULL per i passaggi attualmente in esecuzione o in coda.|  
|total_elapsed_time|**int**|Quantità totale di tempo che è stato eseguito il passaggio della query, in millisecondi.|Compreso tra 0 e la differenza tra start_time ed end_time. 0 per i passaggi in coda.<br /><br /> Se total_elapsed_time supera il valore massimo per un numero intero, total_elapsed_time continuerà a essere il valore massimo. Questa condizione genera l'avviso "è stato superato il valore massimo."<br /><br /> Il valore massimo in millisecondi è equivalente a 24.8 giorni.|  
|row_count|**bigint**|Numero totale di righe modificate o restituita da questa richiesta.|0 per i passaggi che non modificare o restituire dati. In caso contrario, numero di righe interessate.|  
|comando|**nvarchar(4000)**|Contiene il testo completo del comando di questo passaggio.|Qualsiasi stringa di richiesta valido per un passaggio. NULL se l'operazione è di tipo MetaDataCreateOperation. Troncata se supera i 4000 caratteri.|  
  
 Per informazioni sulle righe massimi mantenuto da questa vista, vedere la sezione valori massimi vista di sistema il "minimo e massimo dei valori" nel [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e Parallel Data Warehouse, viste a gestione dinamica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
