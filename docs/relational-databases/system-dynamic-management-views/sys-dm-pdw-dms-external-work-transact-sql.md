---
title: sys.dm_pdw_dms_external_work (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 47345015-f861-451e-97c4-6e1cb81d1922
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: d980034474bc08e57044ecdcf555877b50a0c1f2
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmpdwdmsexternalwork-transact-sql"></a>sys.dm_pdw_dms_external_work (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] vista di sistema che contiene informazioni su tutti i passaggi del servizio lo spostamento dei dati (DMS) per le operazioni esterne.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Query che utilizza il thread di lavoro DMS.<br /><br /> request_id step_index e dms_step_index formano la chiave per la visualizzazione.|Uguale a request_id in [sys.dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|Passaggio di query che richiama il thread di lavoro DMS.<br /><br /> request_id step_index e dms_step_index formano la chiave per la visualizzazione.|Uguale a step_index in [sys.dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|dms_step_index|**int**|Passaggio corrente del piano DMS.<br /><br /> request_id step_index e dms_step_index formano la chiave per la visualizzazione.|Uguale a dms___step_index in [sys.dm_pdw_dms_workers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-dms-workers-transact-sql.md).|  
|pdw_node_id|**int**|Nodo che esegue il processo di lavoro DMS.|Uguale a node_id in [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|Tipo|**nvarchar(60)**|Tipo di operazione esterna di che questo nodo è in esecuzione.<br /><br /> FILE SPLIT è un'operazione in un file Hadoop esterno che è stata suddivisa in più cade più piccoli.|'SPLIT FILE'|  
|work_id|**int**|Il file separato ID.|Maggiore o uguale a 0.<br /><br /> Valore univoco per ogni nodo di calcolo.|  
|input_name|**nvarchar(60)**|Stringa del nome per l'input letto.|Per un file di Hadoop, questo è il nome del file Hadoop.|  
|read_location|**bigint**|Offset della posizione di lettura.||  
|estimated_bytes_processed|**bigint**|Numero di byte elaborati dal thread di lavoro.|Maggiore o uguale a 0.|  
|length|**bigint**|Numero di byte nel file di divisione.<br /><br /> Per Hadoop, questa è la dimensione del blocco di HDFS.|Definito dall'utente. Il valore predefinito è 64 MB.|  
|status|**nvarchar(32)**|Stato del processo di lavoro.|In sospeso, l'elaborazione, operazione eseguita, non è riuscita, interrotto|  
|start_time|**datetime**|Ora di inizio dell'esecuzione del thread di lavoro.|Maggiore o uguale all'ora di inizio del passaggio della query di questo processo di lavoro a cui appartiene. Vedere [sys.dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|end_time|**datetime**|Ora in cui esecuzione è terminata, non è riuscita o annullata.|NULL per i lavori in corso o in coda. In caso contrario, maggiore di start_time.|  
|total_elapsed_time|**int**|Tempo totale impiegato per l'esecuzione, in millisecondi.|Maggiore o uguale a 0.<br /><br /> Se total_elapsed_time supera il valore massimo per un numero intero, total_elapsed_time continuerà a essere il valore massimo. Questa condizione genera l'avviso "è stato superato il valore massimo."<br /><br /> Il valore massimo in millisecondi è equivalente a 24.8 giorni.|  
  
 Per informazioni sulle righe massimi mantenuto da questa vista, vedere [i valori massimi vista di sistema](http://msdn.microsoft.com/en-us/5243f018-2713-45e3-9b61-39b2a57401b9).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste di sistema &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)  
  
  
