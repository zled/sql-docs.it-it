---
title: sys.pdw_loader_backup_runs (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 2b72034c-6a11-46b9-a76c-7a88b2bea360
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2bc42a27de363d0c1f3e62a4b3f69b8b9fbb95de
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="syspdwloaderbackupruns-transact-sql"></a>sys.pdw_loader_backup_runs (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contiene informazioni sul backup in corso e completate e operazioni di ripristino in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]e sui backup in corso e completate e, in operazioni di caricamento [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Le informazioni persiste tra i riavvii del sistema.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|run_id|**int**|Identificatore univoco per un determinato backup, ripristino o esecuzione test di carico.<br /><br /> Chiave per la visualizzazione.||  
|name|**nvarchar(255)**|Null per il carico. Nome facoltativo per il backup o ripristino.||  
|submit_time|**datetime**|Ora che è stata inviata la richiesta.||  
|start_time|**datetime**|Ora di avvio dell'operazione.||  
|end_time|**datetime**|Ora l'operazione di completamento, non riuscita o annullata.||  
|total_elapsed_time|**int**|Tempo totale trascorso tra start_time e l'ora corrente, o tra start_time ed end_time processo completato, annullato o viene eseguito.|Se total_elapsed_time supera il valore massimo per un numero intero (24.8 giorni, in millisecondi), errore di materializzazione scadenza comporterà un overflow.<br /><br /> Il valore massimo in millisecondi è equivalente a 24.8 giorni.|  
|operation_type|**nvarchar(16)**|Il tipo di carico.|'BACKUP', 'CARICO', 'RESTORE'|  
|mode|**nvarchar(16)**|La modalità di all'interno del tipo di esecuzione.|Per operation_type = **BACKUP**<br />**BACKUP DIFFERENZIALE**<br />**FULL**<br /><br /> Per operation_type = **carico**<br />**AGGIUNGERE**<br />**RICARICA**<br />**UPSERT**<br /><br /> Per operation_type = **ripristino**<br />**DATABASE**<br />**HEADER_ONLY**|  
|database_name|**nvarchar(255)**|Nome del database che rappresenta il contesto di questa operazione||  
|table_name|**nvarchar(255)**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|Principal_id|**int**|ID dell'utente che richiede l'operazione.||  
|session_id|**nvarchar(32)**|ID della sessione dell'esecuzione dell'operazione.|Vedere session_id in [sys.dm_pdw_exec_sessions &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).|  
|request_id|**nvarchar(32)**|ID della richiesta di esecuzione dell'operazione. Per i caricamenti, questa è la richiesta corrente o l'ultima associata a questo carico...|Vedere request_id in [sys.dm_pdw_exec_requests &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|status|**nvarchar(16)**|Stato dell'esecuzione.|'ANNULLATO', 'COMPLETATO', 'NON RIUSCITO', 'QUEUED', 'IN ESECUZIONE'|  
|stato di avanzamento|**int**|Percentuale di completamento.|da 0 a 100|  
|comando|**nvarchar(4000)**|Testo completo del comando inviato dall'utente.|Verrà troncato se più di 4000 caratteri (da spazi).|  
|rows_processed|**bigint**|Numero di righe elaborate come parte di questa operazione.||  
|rows_rejected|**bigint**|Numero di righe rifiutate come parte di questa operazione.||  
|rows_inserted|**bigint**|Numero di righe inserite tra le tabelle di database come parte di questa operazione.||  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e viste del catalogo Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
