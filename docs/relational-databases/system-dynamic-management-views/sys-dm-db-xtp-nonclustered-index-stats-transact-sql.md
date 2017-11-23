---
title: Sys.dm db_xtp_nonclustered_index_stats (Transact-SQL) | Documenti Microsoft
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
- dm_db_xtp_nonclustered_index_stats_TSQL
- dm_db_xtp_nonclustered_index_stats
- sys.dm_db_xtp_nonclustered_index_stats_TSQL
- sys.dm_db_xtp_nonclustered_index_stats
dev_langs: TSQL
helpviewer_keywords: sys.dm_db_xtp_nonclustered_index_stats
ms.assetid: d55ba31c-296c-419b-9c4b-c126e0a3d156
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ffaf0f200c33a5a2ed35a138bfc6da663b9b002e
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmdbxtpnonclusteredindexstats-transact-sql"></a>sys.dm_db_xtp_nonclustered_index_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  sys.dm_db_xtp_nonclustered_index_stats include statistiche sulle operazioni sugli indici non cluster nelle tabelle ottimizzate per la memoria. sys.dm_db_xtp_nonclustered_index_stats contiene una riga per ogni indice non cluster in una tabella ottimizzata per la memoria nel database corrente.  
  
 Le statistiche riflesse in sys.dm_db_xtp_nonclustered_index_stats vengono raccolte quando la struttura dell'indice in memoria viene creata. Le strutture degli indici in memoria vengono ricreate al riavvio del database.  
  
 Utilizzare sys.dm_db_xtp_nonclustered_index_stats per comprendere e monitorare l'attività dell'indice durante le operazioni DML e quando un database viene portato online. Quando un database con una tabella ottimizzata per la memoria viene riavviato, l'indice viene compilato inserendo una riga per volta in memoria. Il conteggio delle divisioni di pagina, dei merge e del consolidamento può aiutare a capire il lavoro svolto per la compilazione dell'indice quando un database viene portato online. Inoltre, è possibile anche osservare i conteggi prima e dopo una serie di operazioni DML.  
  
 Numerosi tentativi sono indicativi di problemi di concorrenza; contattare il supporto [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
 Per ulteriori informazioni sugli indici con ottimizzazione per la memoria, non cluster, vedere [panoramica dei meccanismi interni OLTP In memoria SQL Server](http://t.co/T6zToWc6y6), pagina 17.  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|object_id|**int**|ID dell'oggetto.|  
|xtp_object_id|**bigint**|ID della tabella con ottimizzazione per la memoria.|  
|index_id|**int**|ID dell'indice.|  
|delta_pages|**bigint**|Numero totale di pagine delta per questo indice nell'albero.|  
|internal_pages|**bigint**|Per uso interno. Numero totale di pagine interne per questo indice nell'albero.|  
|leaf_pages|**bigint**|Numero totale di pagine foglia per questo indice nell'albero.|  
|outstanding_retired_nodes|**bigint**|Per uso interno. Numero totale di nodi per questo indice nelle strutture interne.|  
|page_update_count|**bigint**|Numero cumulativo di operazioni di aggiornamento di una pagina nell'indice.|  
|page_update_retry_count|**bigint**|Numero cumulativo di tentativi di un'operazione di aggiornamento di una pagina nell'indice.|  
|page_consolidation_count|**bigint**|Numero cumulativo di consolidamenti di pagine nell'indice.|  
|page_consolidation_retry_count|**bigint**|Numero cumulativo di tentativi di operazioni di consolidamento di pagine.|  
|page_split_count|**bigint**|Numero cumulativo di operazioni di divisione pagina nell'indice.|  
|page_split_retry_count|**bigint**|Numero cumulativo di tentativi di operazioni di divisione pagina.|  
|key_split_count|**bigint**|Numero cumulativo di divisione chiave nell'indice.|  
|key_split_retry_count|**bigint**|Numero cumulativo di tentativi di operazioni di divisione chiave.|  
|page_merge_count|**bigint**|Numero cumulativo di operazioni di unione di pagine nell'indice.|  
|page_merge_retry_count|**bigint**|Numero cumulativo di tentativi di operazioni di unione di pagine.|  
|key_merge_count|**bigint**|Numero cumulativo di operazioni di unione di chiavi nell'indice.|  
|key_merge_retry_count|**bigint**|Numero cumulativo di tentativi di operazioni di unione di chiavi.|  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione VIEW DATABASE STATE per il database corrente.  
  
## <a name="see-also"></a>Vedere anche  
 [Viste a gestione dinamica tabella con ottimizzazione per la memoria &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  