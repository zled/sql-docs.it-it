---
title: Sys.dm os_memory_cache_counters (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_os_memory_cache_counters_TSQL
- dm_os_memory_cache_counters_TSQL
- sys.dm_os_memory_cache_counters
- dm_os_memory_cache_counters
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_cache_counters dynamic management view
ms.assetid: ca7bd036-d661-4c17-b00a-e1a975bd8932
caps.latest.revision: 36
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d16da7e5bbc38b7017da1f94741d4c4955e3485d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmosmemorycachecounters-transact-sql"></a>sys.dm_os_memory_cache_counters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Viene restituito uno snapshot dello stato di una cache in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. **Sys.dm_os_memory_cache_counters** fornisce informazioni di run-time sulle voci di cache allocate, e il loro utilizzo sull'origine di memoria per le voci della cache.  
  
> **Nota:** per chiamare questo metodo dal [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] oppure [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], usare il nome **sys.dm_pdw_nodes_os_memory_cache_counters**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**cache_address**|**varbinary(8)**|Indica l'indirizzo (chiave primaria) dei contatori associati a una cache specifica. Non ammette i valori Null.|  
|**name**|**nvarchar(256)**|Specifica il nome della cache. Non ammette i valori Null.|  
|**type**|**nvarchar(60)**|Indica il tipo di cache associato a questa voce. Non ammette i valori Null.|  
|**single_pages_kb**|**bigint**|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Quantità, in kilobyte, della memoria a pagina singola allocata. Corrisponde alla quantità di memoria allocata tramite l'allocatore di pagine singole. Si riferisce alla pagine di 8 KB prelevate direttamente dal pool di buffer per questa cache. Non ammette i valori Null.|  
|**pages_kb**|**bigint**|**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Specifica la quantità di memoria, in kilobyte, allocata nella cache. Non ammette i valori Null.|  
|**multi_pages_kb**|**bigint**|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Quantità, in kilobyte, della memoria a più pagine allocata. Corrisponde alla quantità di memoria allocata tramite l'allocatore di pagine multiple del nodo di memoria. Questa memoria viene allocata all'esterno del pool di buffer e utilizza l'allocatore virtuale dei nodi di memoria. Non ammette i valori Null.|  
|**pages_in_use_kb**|**bigint**|**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Specifica la quantità di memoria, in kilobyte, allocata e in uso nella cache. Ammette i valori Null.  I valori per gli oggetti di tipo `USERSTORE_<*>` non vengono rilevati.  Viene riportato NULL.|  
|**single_pages_in_use_kb**|**bigint**|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Quantità, in kilobyte, della memoria a pagina singola utilizzata. Ammette i valori Null. Queste informazioni non vengono rilevate per gli oggetti di tipo USERSTORE_\<* > e i valori saranno NULL.|  
|**multi_pages_in_use_kb**|**bigint**|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Quantità, in kilobyte, della memoria a più pagine utilizzata. Ammette valori Null. Queste informazioni non vengono rilevate per gli oggetti di tipo USERSTORE_\<* >, e questi valori saranno NULL.|  
|**entries_count**|**bigint**|Indica il numero di voci nella cache. Non ammette i valori Null.|  
|**entries_in_use_count**|**bigint**|Indica il numero di voci della cache utilizzate. Non ammette i valori Null.|  
|**pdw_node_id**|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L'identificatore per il nodo che utilizza questo tipo di distribuzione.|  
  
## <a name="permissions"></a>Autorizzazioni 

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], richiede `VIEW SERVER STATE` autorizzazione.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], richiede il `VIEW DATABASE STATE` autorizzazione per il database.   

## <a name="see-also"></a>Vedere anche  
  [Viste a gestione dinamica relative al sistema di operativo SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


