---
title: Sys.dm_db_xtp_index_stats (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/29/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_db_xtp_index_stats
- dm_db_xtp_index_stats
- sys.dm_db_xtp_index_stats_TSQL
- dm_db_xtp_index_stats_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_db_xtp_index_stats dynamic management view
ms.assetid: 8d0a50b8-2015-4576-930f-e3307dfc888e
caps.latest.revision: "25"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8803e51eab52a10e67e90dc6ddb06cfc7d737434
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmdbxtpindexstats-transact-sql"></a>sys.dm_db_xtp_index_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Contiene le statistiche raccolte dall'ultimo riavvio del database.  
  
 Per ulteriori informazioni, vedere [OLTP In memoria &#40; ottimizzazione per la memoria &#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md) e [linee guida per l'utilizzo di indici nelle tabelle con ottimizzazione](http://msdn.microsoft.com/library/16ef63a4-367a-46ac-917d-9eebc81ab29b).  

  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|object_id|**bigint**|ID dell'oggetto a cui appartiene l'indice.|  
|xtp_object_id|**bigint**|ID interno corrispondente alla versione corrente dell'oggetto.<br /><br /> Nota: Si applica a [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].|  
|index_id|**bigint**|ID dell'indice. index_id è un valore univoco solo nell'ambito dell'oggetto.|  
|scans_started|**bigint**|Numero di analisi degli indici OLTP in memoria eseguite. Ogni istruzione select, insert, update o delete richiede un'analisi dell'indice.|  
|scans_retries|**bigint**|Numero di analisi degli indici che è necessario ritentare.|  
|rows_returned|**bigint**|Numero cumulativo di righe restituite dopo la creazione della tabella o l'avvio di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|rows_touched|**bigint**|Numero cumulativo di righe cui è stato eseguito l'accesso dopo la creazione della tabella o l'avvio di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|rows_expiring|**bigint**|Solo per uso interno.|  
|rows_expired|**bigint**|Solo per uso interno.|  
|rows_expired_removed|**bigint**|Solo per uso interno.|  
|phantom_scans_started|**bigint**|Solo per uso interno.|  
|phatom_scans_retries|**bigint**|Solo per uso interno.|  
|phantom_rows_touched|**bigint**|Solo per uso interno.|  
|phantom_expiring_rows_encountered|**bigint**|Solo per uso interno.|  
|phantom_expired_rows_encountered|**bigint**|Solo per uso interno.|  
|phantom_expired_removed_rows_encountered|**bigint**|Solo per uso interno.|  
|phantom_expired_rows_removed|**bigint**|Solo per uso interno.|  
|object_address|**varbinary (8)**|Solo per uso interno.|  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione VIEW DATABASE STATE per il database corrente.  
  
## <a name="see-also"></a>Vedere anche  
 [Viste a gestione dinamica tabella con ottimizzazione per la memoria &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
