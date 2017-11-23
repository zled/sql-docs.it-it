---
title: Sys.dm os_memory_pools (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/13/2017
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
- sys.dm_os_memory_pools_TSQL
- dm_os_memory_pools
- dm_os_memory_pools_TSQL
- sys.dm_os_memory_pools
dev_langs: TSQL
helpviewer_keywords: sys.dm_os_memory_pools dynamic management view
ms.assetid: 1ef053f3-c6f3-456e-82b6-26e4bd630d46
caps.latest.revision: "25"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9e0e649688167c772defa308172f3b8a633ab6b7
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmosmemorypools-transact-sql"></a>sys.dm_os_memory_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce una riga per ogni archivio di oggetti nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. È possibile utilizzare questa vista per monitorare l'utilizzo della memoria cache e per identificare l'errato funzionamento della memorizzazione nella cache.  
  
> [!NOTE]  
>  Per chiamare questo metodo dal [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilizzare il nome **sys.dm_pdw_nodes_os_memory_pools**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**memory_pool_address**|**varbinary (8)**|Indirizzo di memoria della voce che rappresenta il pool di memoria. Non ammette i valori Null.|  
|**pool_id**|**int**|ID di un pool specifico all'interno di un set di pool. Non ammette i valori Null.|  
|**tipo**|**nvarchar(60)**|Tipo di pool di oggetti. Non ammette i valori Null. Per ulteriori informazioni, vedere [Sys.dm os_memory_clerks &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md).|  
|**name**|**nvarchar(256)**|Nome assegnato dal sistema dell'oggetto memoria. Non ammette i valori Null.|  
|**max_free_entries_count**|**bigint**|Numero massimo di voci libere che un pool può avere. Non ammette i valori Null.|  
|**free_entries_count**|**bigint**|Numero di voci libere incluse nel pool. Non ammette i valori Null.|  
|**removed_in_all_rounds_count**|**bigint**|Numero di voci rimosse dal pool dall'avvio dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Non ammette i valori Null.|  
|**pdw_node_id**|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L'identificatore per il nodo che utilizza questo tipo di distribuzione.|  
  
## <a name="permissions"></a>Permissions  
In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], richiede `VIEW SERVER STATE` autorizzazione.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli Premium, è necessario il `VIEW DATABASE STATE` autorizzazione per il database. In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli Standard e Basic, è necessario il **amministratore del Server** o **amministratore di Azure Active Directory** account.  
  
## <a name="remarks"></a>Osservazioni  
 I componenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] talvolta utilizzano una struttura comune di pool per memorizzare nella cache tipi di dati omogenei e senza informazioni sullo stato. La struttura di pool è più semplice della struttura di cache. Tutte le voci nei pool sono considerate uguali. Internamente i pool sono clerk di memoria e possono essere utilizzati nelle stesse posizioni in cui vengono utilizzati i clerk di memoria.  
  
## <a name="see-also"></a>Vedere anche  
 
  [Relative al sistema operativo SQL Server viste a gestione dinamica &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


