---
title: sys.dm_pdw_dms_workers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 0a284d18-3c46-4ffa-bcc9-689e660ee8b4
caps.latest.revision: 7
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 8559d26dc9bed6628fcd5df1a97e30cc553a17bf
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmpdwdmsworkers-transact-sql"></a>sys.dm_pdw_dms_workers (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contiene informazioni su tutti i ruoli worker procedura DMS.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Query che fanno parte di thread di lavoro DMS.<br /><br /> request_id step_index e dms_step_index formano la chiave per la visualizzazione.|Vedere request_id in [sys.dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|Passaggio di di che thread di lavoro DMS fa parte una query.<br /><br /> request_id step_index e dms_step_index formano la chiave per la visualizzazione.|Vedere step_index in [sys.dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|dms_step_index|**int**|Passaggio nel piano di DMS che il thread di lavoro è in esecuzione.<br /><br /> request_id step_index e dms_step_index formano la chiave per la visualizzazione.||  
|pdw_node_id|**int**|Nodo in cui è in esecuzione il processo di lavoro.|Vedere node_id in [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|distribution_id|**Int**|Distribuzione che esegue il processo di lavoro, se presente.|Vedere distribution_id in [sys.pdw_distributions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-distributions-transact-sql.md).|  
|Tipo|**nvarchar(32)**|Tipo di thread di lavoro DMS che rappresenta questa voce.|'DIRECT_CONVERTER', 'DIRECT_READER', 'FILE_READER', 'HASH_CONVERTER', 'HASH_READER', 'ROUNDROBIN_CONVERTER', 'EXPORT_READER', 'EXTERNAL_READER', 'EXTERNAL_WRITER', 'PARALLEL_COPY_READER', 'REJECT_WRITER', 'WRITER'|  
|status|**nvarchar(32)**|Stato del processo di lavoro DMS.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|bytes_per_sec|**bigint**|Velocità effettiva di lettura o scrittura nell'ultimo secondo.|Maggiore o uguale a 0. NULL se la query è stata annullata o non è riuscita prima di eseguire il processo di lavoro.|  
|bytes_processed|**bigint**|Numero totale di byte elaborati dal thread di lavoro.|Maggiore o uguale a 0. NULL se la query è stata annullata o non è riuscita prima di eseguire il processo di lavoro.|  
|rows_processed|**bigint**|Numero di righe lette o scritte per il thread di lavoro.|Maggiore o uguale a 0. NULL se la query è stata annullata o non è riuscita prima di eseguire il processo di lavoro.|  
|start_time|**datetime**|Ora di inizio dell'esecuzione del thread di lavoro.|Maggiore o uguale all'ora di inizio del passaggio della query di questo processo di lavoro a cui appartiene. Vedere [sys.dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|end_time|**datetime**|Ora in cui esecuzione è terminata, non è riuscita o annullata.|NULL per i lavori in corso o in coda. In caso contrario, maggiore di start_time.|  
|total_elapsed_time|**int**|Tempo totale impiegato per l'esecuzione, in millisecondi.|Maggiore o uguale a 0.<br /><br /> Tempo totale trascorso dal sistema avviare o riavviare. Se total_elapsed_time supera il valore massimo per un numero intero (24.8 giorni, in millisecondi), errore di materializzazione scadenza comporterà un overflow.<br /><br /> Il valore massimo in millisecondi è equivalente a 24.8 giorni.|  
|cpu_time|**bigint**|Tempo di CPU utilizzato dal thread di lavoro, in millisecondi.|Maggiore o uguale a 0.|  
|query_time|**int**|Periodo di tempo prima SQL avvia la restituzione delle righe per il thread, in millisecondi.|Maggiore o uguale a 0.|  
|buffers_available|**int**|Numero di buffer non utilizzati.| NULL se la query è stata annullata o non è riuscita prima di eseguire il processo di lavoro.|  
|sql_spid|**int**|Id di sessione nell'esecuzione del lavoro per il thread di lavoro DMS l'istanza di SQL Server.||  
|dms_cpid|**int**|ID del thread effettivo in esecuzione.||  
|error_id|**nvarchar(36)**|Identificatore univoco dell'errore che si è verificato durante l'esecuzione del thread di lavoro, se presente.|Vedere in error_id [sys.dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|source_info|**nvarchar(4000)**|Per un lettore, specifica le tabelle di origine e le colonne.||  
|destination_info|**nvarchar(4000)**|Per un writer, specifica tabelle di destinazione.||  
  
 Per informazioni sulle righe massimi mantenuto da questa vista, vedere [i valori massimi vista di sistema](http://msdn.microsoft.com/en-us/5243f018-2713-45e3-9b61-39b2a57401b9).  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e Parallel Data Warehouse, viste a gestione dinamica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
