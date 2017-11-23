---
title: Sys.dm db_index_usage_stats (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_db_index_usage_stats_TSQL
- sys.dm_db_index_usage_stats
- sys.dm_db_index_usage_stats_TSQL
- dm_db_index_usage_stats
dev_langs: TSQL
helpviewer_keywords: sys.dm_db_index_usage_stats dynamic management view
ms.assetid: d06a001f-0f72-4679-bc2f-66fff7958b86
caps.latest.revision: "35"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 1bd4812468ea0c17458f2b32b653ebcbf161c1ab
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmdbindexusagestats-transact-sql"></a>sys.dm_db_index_usage_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce i conteggi di diversi tipi di operazioni relative agli indici e l'ora dell'ultima esecuzione di ogni tipo di operazione in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 In [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], le viste a gestione dinamica non possono esporre le informazioni che influenzerebbero l'indipendenza del database o le informazioni sugli altri database a cui l'utente dispone di accesso. Per evitare di esporre queste informazioni, ogni riga che contiene dati che non appartengono al tenant connesso viene esclusa tramite filtro.  
  
> [!NOTE]  
>  **Sys.dm db_index_usage_stats** non restituisce informazioni sugli indici con ottimizzazione per la memoria. Per informazioni sull'uso degli indici con ottimizzazione per la memoria, vedere [sys.dm_db_xtp_index_stats &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-index-stats-transact-sql.md).  
  
> [!NOTE]  
>  Per chiamare questo metodo dal [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilizzare il nome **sys.dm_pdw_nodes_db_index_usage_stats**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**smallint**|ID del database in cui è definita la tabella o la vista.|  
|**object_id**|**int**|ID della tabella o della vista in cui è definito l'indice.|  
|**index_id**|**int**|ID dell'indice.|  
|**user_seeks**|**bigint**|Numero di operazioni Seek dovute a query utente.|  
|**user_scans**|**bigint**|Numero di analisi dovute a query utente. Rappresenta le analisi che non utilizzano seek predicato.|  
|**user_lookups**|**bigint**|Numero di ricerche tramite segnalibro eseguite da query utente.|  
|**user_updates**|**bigint**|Numero di aggiornamenti dovuti a query utente. Ovvero inserimento, eliminazione e aggiornamenti che rappresenta numero di operazioni eseguite non le righe effettivamente interessate. Ad esempio, se si eliminano 1000 righe in un'unica istruzione, questo numero viene incrementato di 1|  
|**last_user_seek**|**datetime**|Ora dell'ultima operazione Seek utente.|  
|**last_user_scan**|**datetime**|Ora dell'ultima analisi utente.|  
|**last_user_lookup**|**datetime**|Ora dell'ultima ricerca utente.|  
|**last_user_update**|**datetime**|Ora dell'ultimo aggiornamento utente.|  
|**system_seeks**|**bigint**|Numero di operazioni Seek dovute a query di sistema.|  
|**system_scans**|**bigint**|Numero di analisi dovute a query di sistema.|  
|**system_lookups**|**bigint**|Numero di ricerche dovute a query di sistema.|  
|**system_updates**|**bigint**|Numero di aggiornamenti dovuti a query di sistema.|  
|**last_system_seek**|**datetime**|Ora dell'ultima operazione Seek di sistema.|  
|**last_system_scan**|**datetime**|Ora dell'ultima analisi di sistema.|  
|**last_system_lookup**|**datetime**|Ora dell'ultima ricerca di sistema.|  
|**last_system_update**|**datetime**|Ora dell'ultimo aggiornamento di sistema.|  
|pdw_node_id|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L'identificatore per il nodo che utilizza questo tipo di distribuzione.|  
  
## <a name="remarks"></a>Osservazioni  
 Ogni operazione Seek, analisi, ricerca o aggiornamento individuale sull'indice specificato, eseguita da una query, viene conteggiata come un utilizzo dell'indice e incrementa il contatore corrispondente in questa vista. Le informazioni vengono restituite sia per le operazioni causate dalle query eseguite dall'utente che per le operazioni causate dalle query generate internamente, ad esempio le analisi per la raccolta di statistiche.  
  
 Il **user_updates** contatore indica il livello di manutenzione nell'indice causato da inserimento, aggiornamento o operazioni delete in una tabella o vista sottostante. È possibile utilizzare questa vista per determinare gli indici scarsamente utilizzati dalle applicazioni. È anche possibile utilizzare la vista per determinare quali indici sono sottoposti a un overhead di manutenzione. Potrebbe essere opportuno rimuovere gli indici che comportano un overhead di manutenzione e che non sono utilizzati, o sono utilizzati solo raramente, per le query.  
  
 I contatori vengono inizializzati su un valore vuoto ad ogni avvio del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER). Inoltre, ogni volta che un database viene scollegato o arrestato (perché, ad esempio, AUTO_CLOSE è impostato su ON), tutte le righe associate al database vengono rimosse.  
  
 Quando viene utilizzato un indice, viene aggiunta una riga per **Sys.dm db_index_usage_stats** se una riga non esiste già per l'indice. All'aggiunta della riga, i contatori corrispondenti vengono inizialmente impostati su zero.  
  
 Durante l'aggiornamento a [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], o [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], vengono rimosse le voci in sys.dm db_index_usage_stats. A partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], le voci vengono mantenute come avveniva prima di [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].  
  
## <a name="permissions"></a>Permissions  
In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], richiede `VIEW SERVER STATE` autorizzazione.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli Premium, è necessario il `VIEW DATABASE STATE` autorizzazione per il database. In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli Standard e Basic, è necessario il **amministratore del Server** o **amministratore di Azure Active Directory** account.  
  
## <a name="see-also"></a>Vedere anche  

 [Indice relative funzioni e viste a gestione dinamica &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/index-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)   
 [Sys.dm db_index_operational_stats &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [Sys. Objects &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [Monitoraggio e ottimizzazione delle prestazioni](../../relational-databases/performance/monitor-and-tune-for-performance.md)  
  
  


