---
title: sys.pdw_loader_backup_run_details (Transact-SQL) | Microsoft Docs
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
ms.assetid: 04fc004f-ee15-4d7a-be08-78357aa99b55
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 02b934db7152723e66aab5818751cb748d2e2a87
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="syspdwloaderbackuprundetails-transact-sql"></a>sys.pdw_loader_backup_run_details (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contiene inoltre informazioni dettagliate, oltre le informazioni contenute in [sys.pdw_loader_backup_runs &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-pdw-loader-backup-runs-transact-sql.md), sul backup in corso e completate e operazioni di ripristino in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] e sul backup in corso e completate e, in operazioni di caricamento [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Le informazioni persiste tra i riavvii del sistema.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|run_id|**int**|Identificatore univoco per un determinato backup o ripristino eseguire.<br /><br /> run_id e pdw_node_id formano la chiave per la visualizzazione.||  
|pdw_node_id|**int**|Identificatore univoco di un nodo di dispositivo per cui questo record contiene dettagli.<br /><br /> run_id e pdw_node_id formano la chiave per la visualizzazione.|Vedere node_id in [sys.dm_pdw_nodes &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|status|**nvarchar(16)**|Lo stato corrente dell'esecuzione.|'ANNULLATO', 'COMPLETATO', 'NON RIUSCITO', 'QUEUED', 'IN ESECUZIONE'|  
|start_time|**datetime**|Ora di inizio dell'operazione in questo nodo particolare.||  
|end_time|**datetime**|Ora in cui è terminato l'operazione in questo nodo particolare, se presente.||  
|total_elapsed_time|**int**|Tempo totale che l'operazione è in esecuzione su questo nodo particolare.|Se total_elapsed_time supera il valore massimo per un numero intero (24.8 giorni, in millisecondi), errore di materializzazione scadenza comporterà un overflow.<br /><br /> Il valore massimo in millisecondi è equivalente a 24.8 giorni.|  
|stato di avanzamento|**int**|Stato di avanzamento dell'operazione espressa come percentuale.|da 0 a 100|  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e viste del catalogo Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
