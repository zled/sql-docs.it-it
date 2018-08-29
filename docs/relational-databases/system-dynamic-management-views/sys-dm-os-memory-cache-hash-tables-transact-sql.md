---
title: sys.dm_os_memory_cache_hash_tables (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_os_memory_cache_hash_tables_TSQL
- sys.dm_os_memory_cache_hash_tables
- dm_os_memory_cache_hash_tables
- dm_os_memory_cache_hash_tables_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_cache_hash_tables dynamic management view
ms.assetid: 68b94f35-8f80-4d2b-bcde-7a21934219af
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e23a0c8575199f081acd311a516b5335143a4e78
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43090460"
---
# <a name="sysdmosmemorycachehashtables-transact-sql"></a>sys.dm_os_memory_cache_hash_tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce una riga per ogni cache attiva nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Per chiamare questo elemento dal [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] oppure [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], usare il nome **sys.dm_pdw_nodes_os_memory_cache_hash_tables**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**cache_address**|**varbinary(8)**|Indirizzo (chiave primaria) della voce nella cache. Non ammette i valori Null.|  
|**name**|**nvarchar(256)**|Nome della cache. Non ammette i valori Null.|  
|**type**|**nvarchar(60)**|Tipo di cache. Non ammette i valori Null.|  
|**table_level**|**int**|Numero di tabella hash. Una cache specifica può avere più tabelle hash corrispondenti a funzioni hash diverse. Non ammette i valori Null.|  
|**buckets_count**|**int**|Numero di bucket nella tabella hash. Non ammette i valori Null.|  
|**buckets_in_use_count**|**int**|Numero di bucket in uso. Non ammette i valori Null.|  
|**buckets_min_length**|**int**|Numero minimo di voci nella cache in un bucket. Non ammette i valori Null.|  
|**buckets_max_length**|**int**|Numero massimo di voci nella cache in un bucket. Non ammette i valori Null.|  
|**buckets_avg_length**|**int**|Numero medio di voci nella cache in ogni bucket. Non ammette i valori Null.|  
|**buckets_max_length_ever**|**int**|Numero massimo di voci nella cache in un hash bucket per la tabella hash corrente dall'avvio del server. Non ammette i valori Null.|  
|**hits_count**|**bigint**|Numero di riscontri nella cache. Non ammette i valori Null.|  
|**misses_count**|**bigint**|Numero di mancati riscontri nella cache. Non ammette i valori Null.|  
|**buckets_avg_scan_hit_length**|**int**|Numero medio di voci controllate in un bucket prima che venga individuato un elemento ricercato. Non ammette i valori Null.|  
|**buckets_avg_scan_miss_length**|**int**|Numero medio di voci controllate in un bucket prima che la ricerca venga conclusa con esito negativo. Non ammette i valori Null.|  
|**pdw_node_id**|**int**|L'identificatore per il nodo in questa distribuzione.<br /><br /> **Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]|  
  
## <a name="permissions"></a>Permissions 

Sul [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], è necessario `VIEW SERVER STATE` autorizzazione.   
Sul [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], è necessario il `VIEW DATABASE STATE` autorizzazione nel database.   

## <a name="see-also"></a>Vedere anche  
 
  [Viste a gestione dinamica relative al sistema di operativo SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


