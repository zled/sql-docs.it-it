---
title: sys.pdw_loader_backup_run_details (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 04fc004f-ee15-4d7a-be08-78357aa99b55
caps.latest.revision: 9
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 82523cd453a2c4352121655c98a57e0ee4cb173b
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33180419"
---
# <a name="syspdwloaderbackuprundetails-transact-sql"></a>sys.pdw_loader_backup_run_details (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contiene informazioni dettagliate, oltre a informazioni in altre [sys.pdw_loader_backup_runs &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-loader-backup-runs-transact-sql.md), sul backup in corso e completate e operazioni di ripristino in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] e in corso completate e backup, ripristino e le operazioni di caricamento in [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Le informazioni vengono mantenute tra un riavvio di sistema e l'altro.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|run_id|**int**|Identificatore univoco per un determinato backup o ripristino eseguire.<br /><br /> run_id e pdw_node_id formano la chiave per la visualizzazione.||  
|pdw_node_id|**int**|Identificatore univoco di un nodo di dispositivo per cui questo record contiene dettagli.<br /><br /> run_id e pdw_node_id formano la chiave per la visualizzazione.|Vedere node_id in [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|status|**nvarchar (16)**|Lo stato corrente dell'esecuzione.|'ANNULLATO', 'COMPLETATO', 'NON RIUSCITO', 'QUEUED', 'IN ESECUZIONE'|  
|start_time|**datetime**|Ora di inizio dell'operazione in questo nodo particolare.||  
|end_time|**datetime**|Ora in cui è terminato l'operazione in questo nodo particolare, se presente.||  
|total_elapsed_time|**int**|Tempo totale che l'operazione è in esecuzione su questo nodo particolare.|Se total_elapsed_time supera il valore massimo per un numero intero (24.8 giorni, in millisecondi), errore di materializzazione scadenza comporterà un overflow.<br /><br /> Il valore massimo in millisecondi è equivalente a 24.8 giorni.|  
|stato di avanzamento|**int**|Stato di avanzamento dell'operazione espressa come percentuale.|da 0 a 100|  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e viste del catalogo Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
