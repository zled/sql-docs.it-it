---
title: Sys.dm exec_query_memory_grants (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_exec_query_memory_grants_TSQL
- sys.dm_exec_query_memory_grants
- sys.dm_exec_query_memory_grants_TSQL
- dm_exec_query_memory_grants
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_memory_grants dynamic management view
ms.assetid: 2c417747-2edd-4e0d-8a9c-e5f445985c1a
caps.latest.revision: 36
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 1147bf6ebd4683a51bb2fed95cdddb2370cc843d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmexecquerymemorygrants-transact-sql"></a>sys.dm_exec_query_memory_grants (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce informazioni su tutte le query che hanno richiesto e sono in attesa di una concessione di memoria o è stato assegnato una concessione di memoria. Le query che non richiedono una concessione di memoria non verranno visualizzati in questa vista. Ad esempio, ordinare in modo che le operazioni di join hash concessioni di memoria per l'esecuzione di query, mentre le query senza un **ORDER BY** clausola non avrà una memoria concedere.  
  
 In [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], le viste a gestione dinamica non possono esporre le informazioni che influenzerebbero l'indipendenza del database o le informazioni sugli altri database a cui l'utente dispone di accesso. Per evitare di esporre queste informazioni, ogni riga che contiene dati che non appartengono al tenant connesso viene esclusa tramite filtro. Inoltre, i valori nelle colonne **scheduler_id**, **wait_order**, **pool_id**, **group_id** vengono filtrati; il valore della colonna è impostato su NULL.  
  
> [!NOTE]  
>  Per chiamare questo metodo dal [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilizzare il nome **sys.dm_pdw_nodes_exec_query_memory_grants**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**session_id**|**smallint**|ID (SPID) della sessione nella quale viene eseguita la query.|  
|**request_id**|**int**|ID della richiesta. Valore univoco nel contesto della sessione.|  
|**scheduler_id**|**int**|ID dell'utilità di pianificazione che sta pianificando la query.|  
|**grado di parallelismo**|**smallint**|Grado di parallelismo della query.|  
|**request_time**|**datetime**|Data e ora in cui la query ha richiesto la concessione di memoria.|  
|**grant_time**|**datetime**|Data e ora in cui la memoria è stata concessa alla query. È NULL se la memoria non è stata ancora concessa.|  
|**requested_memory_kb**|**bigint**|Quantità totale di memoria richiesta, espressa in kilobyte.|  
|**granted_memory_kb**|**bigint**|Quantità totale di memoria effettivamente concessa, espressa in kilobyte. Può essere NULL se la memoria non è stata ancora concessa. Per una situazione tipica questo valore deve essere identico **requested_memory_kb**. In caso di creazione di indici, il server può concedere ulteriore memoria su richiesta in aggiunta alla memoria concessa inizialmente.|  
|**required_memory_kb**|**bigint**|Quantità minima di memoria necessaria per l'esecuzione della query, espressa in kilobyte. **requested_memory_kb** è uguale o maggiore di questa quantità.|  
|**used_memory_kb**|**bigint**|Memoria fisica attualmente in uso, espressa in kilobyte.|  
|**max_used_memory_kb**|**bigint**|Memoria fisica massima utilizzata fino a questo momento, espressa in kilobyte.|  
|**query_cost**|**float**|Costo stimato della query.|  
|**timeout_sec**|**int**|Timeout in secondi prima che la query rinunci alla richiesta di concessione di memoria.|  
|**resource_semaphore_id**|**smallint**|ID non univoco del semaforo di risorsa su cui la query è in attesa.<br /><br /> **Nota:** tale ID è univoco nelle versioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] precedenti a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]. La modifica può influire sulla risoluzione dei problemi relativi all'esecuzione di query. Per ulteriori informazioni, vedere la sezione "Osservazioni" di seguito in questo argomento.|  
|**queue_id**|**smallint**|ID della coda nella quale la query sta attendendo la concessione di memoria. È NULL se la memoria è già stata concessa.|  
|**wait_order**|**int**|Ordine sequenziale delle query in attesa della **queue_id**. Questo valore può variare in caso di timeout o di concessione di memoria ad altre query. È NULL se la memoria è già stata concessa.|  
|**is_next_candidate**|**bit**|Candidato alla concessione di memoria successiva.<br /><br /> 1 = Sì<br /><br /> 0 = No<br /><br /> NULL = Memoria già concessa|  
|**wait_time_ms**|**bigint**|Periodo di attesa espresso in millisecondi. È NULL se la memoria è già stata concessa.|  
|**plan_handle**|**varbinary(64)**|Identificatore del piano di query. Utilizzare **Sys.dm exec_query_plan** per estrarre il piano XML effettivo.|  
|**sql_handle**|**varbinary(64)**|Identificatore del testo [!INCLUDE[tsql](../../includes/tsql-md.md)] della query. Utilizzare **Sys.dm exec_sql_text** per ottenere l'effettivo [!INCLUDE[tsql](../../includes/tsql-md.md)] testo.|  
|**group_id**|**int**|ID per il gruppo del carico di lavoro nel quale viene eseguita la query.|  
|**pool_id**|**int**|ID del pool di risorse a cui appartiene il gruppo del carico di lavoro.|  
|**is_small**|**tinyint**|Se il valore è 1, questa concessione utilizza il semaforo piccolo di risorsa. Se il valore è 0, viene utilizzato un semaforo normale.|  
|**ideal_memory_kb**|**bigint**|Dimensioni, in kilobyte (KB), della concessione di memoria per inserire tutto nella memoria fisica. Si basa su una stima della cardinalità.|  
|**pdw_node_id**|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L'identificatore per il nodo che utilizza questo tipo di distribuzione.|  
  
## <a name="permissions"></a>Autorizzazioni  

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], richiede `VIEW SERVER STATE` autorizzazione.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], richiede il `VIEW DATABASE STATE` autorizzazione per il database.   
   
## <a name="remarks"></a>Osservazioni  
 Di seguito è illustrato un tipico scenario di debug per il timeout delle query:  
  
-   Controllare sistema memoria lo stato complessivo utilizzando [Sys.dm os_memory_clerks](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md), [Sys.dm os_sys_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)e diversi contatori di prestazioni.  
  
-   Verificare la presenza di prenotazioni di memoria dell'esecuzione di query in **Sys.dm os_memory_clerks** in `type = 'MEMORYCLERK_SQLQERESERVATIONS'`.  
  
-   Verificare le query in attesa di concessione di memoria utilizzando **Sys.dm exec_query_memory_grants**.  
  
    ```  
    --Find all queries waiting in the memory queue  
    SELECT * FROM sys.dm_exec_query_memory_grants where grant_time is null  
    ```  
  
-   Eseguire la ricerca della cache per le query con concessioni di memoria utilizzando[exec_cached_plans &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md) e [exec_query_plan &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)  
  
    ```  
    -- retrieve every query plan from the plan cache  
    USE master;  
    GO  
    SELECT * FROM sys.dm_exec_cached_plans cp CROSS APPLY sys.dm_exec_query_plan(cp.plan_handle);  
    GO  
  
    ```  
  
-   Esaminare in maggiore dettaglio le query a elevato utilizzo di memoria che utilizzano [Sys.dm exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).  
  
    ```  
    --Find top 5 queries by average CPU time  
    SELECT TOP 5 total_worker_time/execution_count AS [Avg CPU Time],  
    Plan_handle, query_plan   
    FROM sys.dm_exec_query_stats AS qs  
    CROSS APPLY sys.dm_exec_query_plan(qs.plan_handle)  
    ORDER BY total_worker_time/execution_count DESC;  
    GO  
  
    ```  
  
-   Se si sospetta la presenza di una query runaway, esaminare lo Showplan di [Sys.dm exec_query_plan](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md) e testo del batch di [Sys.dm exec_sql_text](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md).  
  
 Le query che utilizzano viste a gestione dinamica con incluse clausole ORDER BY o funzioni di aggregazione potrebbero aumentare l'utilizzo della memoria, contribuendo di conseguenza a causare il problema che dovrebbero risolvere.  
  
 La funzionalità Resource Governor consente a un amministratore di database di distribuire risorse del server fra un massimo di 64 pool di risorse. A partire da [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], ogni pool si comporta come una piccola indipendenti istanza del server e richiede 2 semafori. Il numero di righe restituite da **Sys.dm exec_query_resource_semaphores** può essere fino a 20 volte superiore alle righe restituite in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [sys.dm_exec_query_resource_semaphores &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-resource-semaphores-transact-sql.md)   
 [Funzioni e viste a gestione dinamica relative all'esecuzione &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


