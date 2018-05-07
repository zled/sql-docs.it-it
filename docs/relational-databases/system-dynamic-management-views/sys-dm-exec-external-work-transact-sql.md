---
title: sys.dm_exec_external_work (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DM_EXEC_EXTERNAL_WORK
- DM_EXEC_EXTERNAL_WORK_TSQL
- SYS.DM_EXEC_EXTERNAL_WORK_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_external_work management view
- dm_exec_external_work management view
- PolyBase,views
- PolyBase
ms.assetid: 7597d97b-1fde-4135-ac35-4af12968f300
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d44d36f478e28518df525356c5fef3e4475bc0ff
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmexecexternalwork-transact-sql"></a>sys.dm_exec_external_work (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Restituisce informazioni sul carico di lavoro per ogni thread di lavoro, in ogni nodo di calcolo.  
  
 Eseguire una query sys.dm_exec_external_work per identificare il lavoro riattivato per comunicare con l'origine dati esterna (ad esempio Hadoop o esterni di SQL Server).  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|**nvarchar(32)**|Identificatore univoco per le query PolyBase associata.|Vedere *request_ID* in [DM exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|step_index|**int**|La richiesta di thread di lavoro è in esecuzione.|Vedere *step_index* in [DM exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|dms_step_index|**int**|Passaggio nel piano di DMS che il thread di lavoro è in esecuzione.|Vedere [sys.dm_exec_dms_workers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-dms-workers-transact-sql.md).|  
|compute_node_id|**int**|Il nodo, il processo di lavoro è in esecuzione.|Vedere [DM exec_compute_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md).|  
|Tipo|**nvarchar(60)**|Il tipo di lavoro esterno.|'File Split'|  
|work_id|**int**|ID della divisione effettiva.|Maggiore o uguale a 0.|  
|input_name|**nvarchar(4000)**|Nome dell'input da leggere|Nome del file quando si utilizza Hadoop.|  
|read_location|**bigint**|L'offset o leggere percorso.|Offset del file da leggere.|  
|bytes_processed|**bigint**|Numero totale di byte elaborati dal thread di lavoro.|Maggiore o uguale a 0.|  
|length|**bigint**|Lunghezza della divisione o blocco HDFS in caso di Hadoop|Definibile dall'utente. Il valore predefinito è 64M|  
|status|**nvarchar(32)**|Stato del processo di lavoro|In sospeso, l'elaborazione, operazione eseguita, non è riuscita, interrotto|  
|start_time|**datetime**|Inizio del lavoro||  
|end_time|**datetime**|Fine del lavoro||  
|total_elapsed_time|**int**|Tempo totale in millisecondi||  
  
## <a name="see-also"></a>Vedere anche  
 [PolyBase, risoluzione dei problemi con viste a gestione dinamica](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Viste a gestione dinamica relative ai database &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
