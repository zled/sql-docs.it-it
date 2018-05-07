---
title: sys.dm_pdw_sql_requests (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 44e19609-902c-46cf-acdf-19ea75011365
caps.latest.revision: 10
author: barbkess
ms.author: barbkess
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 8fb8dc47d288470bedb8692ab38d00b0d810a1f6
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmpdwsqlrequests-transact-sql"></a>sys.dm_pdw_sql_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contiene informazioni su tutte le distribuzioni di query di SQL Server come parte di un passaggio SQL nella query.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Identificatore univoco della query a cui appartiene questa distribuzione di query SQL.<br /><br /> request_id step_index e distribution_id formano la chiave per la visualizzazione.|Vedere request_id in [sys.dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|Indice del passaggio query di che questa distribuzione è parte.<br /><br /> request_id step_index e distribution_id formano la chiave per la visualizzazione.|Vedere step_index in [sys.dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|pdw_node_id|**int**|Identificatore univoco del nodo in cui viene eseguita la distribuzione di query.|Vedere node_id in [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|distribution_id|**int**|Identificatore univoco della distribuzione in cui viene eseguita la distribuzione di query.<br /><br /> request_id step_index e distribution_id formano la chiave per la visualizzazione.|Vedere distribution_id in [sys.pdw_distributions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-distributions-transact-sql.md). Impostare su -1 per le richieste eseguite nell'ambito del nodo, non l'ambito della distribuzione.|  
|status|**nvarchar(32)**|Stato corrente della distribuzione di query.|In sospeso, in esecuzione, non riusciti, annullato, completato, interrotto, CancelSubmitted|  
|error_id|**nvarchar(36)**|Identificatore univoco dell'errore associata a questa distribuzione delle query, se presente.|Vedere in error_id [sys.dm_pdw_errors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md). Se si è verificato alcun errore, impostato su NULL.|  
|start_time|**datetime**|Ora di query in cui distribuzione inizio esecuzione.|Minore o uguale all'ora corrente e maggiore o uguale a start_time dell'istruzione di query appartiene questa distribuzione delle query|  
|end_time|**datetime**|Ora in cui questa distribuzione di query ha completato l'esecuzione, è stata annullata o non è riuscita.|Maggiore o uguale all'ora di inizio o impostato su NULL se la distribuzione di query è in corso o in coda.|  
|total_elapsed_time|**int**|Rappresenta l'ora che di distribuzione delle query è in esecuzione, in millisecondi.|Maggiore o uguale a 0. Uguale a delta di start_time ed end_time che sono state completate, non è riuscita o annullata le distribuzioni di query.<br /><br /> Se total_elapsed_time supera il valore massimo per un numero intero, total_elapsed_time continuerà a essere il valore massimo. Questa condizione genera l'avviso "è stato superato il valore massimo."<br /><br /> Il valore massimo in millisecondi è equivalente a 24.8 giorni.|  
|row_count|**bigint**|Numero di righe modificate o lette dalla distribuzione delle query.|-1 per le operazioni che modificano o non restituire dati, ad esempio CREATE TABLE e DROP TABLE.|  
|spid|**int**|Id di sessione nell'istanza di SQL Server che esegue la distribuzione delle query.||  
|comando|**nvarchar(4000)**|Testo completo del comando per la distribuzione di query.|Qualsiasi stringa di query o una richiesta valida.|  
  
 Per informazioni sulle righe massimi mantenuto da questa vista, vedere la sezione valori massimi vista di sistema nel [valori minimo e massimo (SQL Server PDW)](http://msdn.microsoft.com/en-us/5243f018-2713-45e3-9b61-39b2a57401b9) argomento.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e Parallel Data Warehouse, viste a gestione dinamica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
