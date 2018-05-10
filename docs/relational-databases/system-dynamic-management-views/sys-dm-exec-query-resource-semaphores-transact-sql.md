---
title: Sys.dm exec_query_resource_semaphores (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_query_resource_semaphores_TSQL
- dm_exec_query_resource_semaphores_TSQL
- sys.dm_exec_query_resource_semaphores
- dm_exec_query_resource_semaphores
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_resource_semaphores dynamic management view
ms.assetid: e43a2aa9-dd52-4c89-911e-1a7d05f7ffbb
caps.latest.revision: 30
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 8d3c488a3c1338bc499153db0d9692870352cfe2
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmexecqueryresourcesemaphores-transact-sql"></a>sys.dm_exec_query_resource_semaphores (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Vengono restituite le informazioni sullo stato del semaforo per le risorse query corrente in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. **DM exec_query_resource_semaphores** fornisce lo stato della memoria generali di esecuzione di query e consente di determinare se il sistema può accedere a memoria insufficiente. Questa visualizzazione si integra con informazioni sulla memoria ottenute da [Sys.dm os_memory_clerks](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md) per fornire un quadro completo dello stato di memoria server. **DM exec_query_resource_semaphores** restituisce una riga per il semaforo di risorsa normale e un'altra riga per il semaforo di risorsa per query di dimensioni ridotte. Esistono due requisiti per una query di dimensioni ridotte di semaforo:  
  
-   La concessione di memoria richiesta deve essere inferiore a 5 MB  
  
-   Il costo della query deve essere inferiore a 3 unità di costo  
  
> [!NOTE]  
>  Per chiamare questo metodo dal [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilizzare il nome **sys.dm_pdw_nodes_exec_query_resource_semaphores**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**resource_semaphore_id**|**smallint**|ID non univoco del semaforo di risorsa. È uguale a 0 per il semaforo di risorsa normale e a 1 per il semaforo di risorsa per query di dimensioni ridotte.|  
|**target_memory_kb**|**bigint**|Destinazione di utilizzo della concessione di memoria, espressa in kilobyte.|  
|**max_target_memory_kb**|**bigint**|Destinazione potenziale massima, espressa in kilobyte. È NULL per il semaforo di risorsa per query di dimensioni ridotte.|  
|**total_memory_kb**|**bigint**|Memoria utilizzata dal semaforo di risorsa, espressa in kilobyte. Se il sistema è eccessivo della memoria o se minima della memoria viene concessa frequentemente, questo valore può essere maggiore di **target_memory_kb** o **max_target_memory_kb** valori. La memoria totale è la somma della memoria disponibile e della memoria concessa.|  
|**available_memory_kb**|**bigint**|Memoria disponibile per una nuova concessione, espressa in kilobyte.|  
|**granted_memory_kb**|**bigint**|Memoria totale concessa, espressa in kilobyte.|  
|**used_memory_kb**|**bigint**|Parte fisica della memoria concessa, espressa in kilobyte.|  
|**grantee_count**|**int**|Numero di query attive a cui è stata concessa la memoria richiesta.|  
|**waiter_count**|**int**|Numero di query in attesa che venga concessa la memoria richiesta.|  
|**timeout_error_count**|**bigint**|Numero complessivo di errori di timeout dall'avvio del server. È NULL per il semaforo di risorsa per query di dimensioni ridotte.|  
|**forced_grant_count**|**bigint**|Numero complessivo di concessioni di memoria minima dall'avvio del server. È NULL per il semaforo di risorsa per query di dimensioni ridotte.|  
|**pool_id**|**int**|ID del pool di risorse a cui appartiene il semaforo di risorsa.|  
|**pdw_node_id**|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L'identificatore per il nodo che utilizza questo tipo di distribuzione.|  
  
## <a name="permissions"></a>Autorizzazioni  

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], richiede `VIEW SERVER STATE` autorizzazione.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], richiede il `VIEW DATABASE STATE` autorizzazione per il database.   
  
## <a name="remarks"></a>Osservazioni  
 Le query che utilizzano viste a gestione dinamica che includono clausole ORDER BY o funzioni di aggregazione potrebbero aumentare l'utilizzo della memoria, contribuendo di conseguenza a causare il problema che dovrebbero risolvere.  
  
 Utilizzare **Sys.dm exec_query_resource_semaphores** per la risoluzione dei problemi, ma non includerla nelle applicazioni che utilizzeranno versioni future di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 La funzionalità Resource Governor consente a un amministratore di database di distribuire risorse del server fra un massimo di 64 pool di risorse. In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] e versioni successive, ogni pool si comporta come una piccola istanza indipendente del server e richiede 2 semafori.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica relative all'esecuzione &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_exec_query_memory_grants &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql.md)  
  
  


