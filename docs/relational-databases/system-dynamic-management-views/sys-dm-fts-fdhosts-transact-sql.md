---
title: Sys.dm fts_fdhosts (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/29/2017
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
- dm_fts_fdhosts
- dm_fts_fdhosts_TSQL
- sys.dm_fts_fdhosts
- sys.dm_fts_fdhosts_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sys.dm_fts_fdhosts dynamic management view
- troubleshooting [SQL Server], full-text search
ms.assetid: d42a6334-4362-4361-83da-f8324fe55ec7
caps.latest.revision: "13"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fef59b93c9f9c5694fe0b7ecd8404eeaffcaf380
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmftsfdhosts-transact-sql"></a>sys.dm_fts_fdhosts (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce informazioni sull'attività corrente dell'host o degli host del daemon di filtri nell'istanza del server.  
  
 
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**fdhost_id**|**int**|ID dell'host del daemon di filtri.|  
|**fdhost_name**|**nvarchar(120)**|Nome dell'host del daemon di filtri.|  
|**fdhost_process_id**|**int**|ID del processo Windows dell'host del daemon di filtri.|  
|**fdhost_type**|**nvarchar(120)**|Tipo di documento elaborato dall'host del daemon di filtri, ad esempio:<br /><br /> A thread singolo<br /><br /> Multi-thread<br /><br /> Documento di grandi dimensioni|  
|**max_thread**|**int**|Numero massimo di thread nell'host del daemon di filtri.|  
|**batch_count**|**int**|Numero di batch in elaborazione nell'host del daemon di filtri.|  
  
## <a name="permissions"></a>Permissions  
In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], richiede `VIEW SERVER STATE` autorizzazione.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli Premium, è necessario il `VIEW DATABASE STATE` autorizzazione per il database. In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli Standard e Basic, è necessario il **amministratore del Server** o **amministratore di Azure Active Directory** account.  

## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituito il nome dell'host del daemon di filtri e il numero massimo di thread relativi. Viene inoltre monitorato il numero di batch attualmente in esecuzione nel daemon di filtri. Queste informazioni possono essere utilizzate nella diagnosi delle prestazioni.  
  
```  
SELECT fdhost_name, batch_count, max_thread FROM sys.dm_fts_fdhosts;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Ricerca full-Text e funzioni e viste a gestione dinamica della ricerca semantica &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [Ricerca full-text](../../relational-databases/search/full-text-search.md)  
  
  
