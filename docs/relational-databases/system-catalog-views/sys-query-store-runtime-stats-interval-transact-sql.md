---
title: Sys.query_store_runtime_stats_interval (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- QUERY_STORE_RUNTIME_STATS_INTERVAL
- SYS.QUERY_STORE_RUNTIME_STATS_INTERVAL
- QUERY_STORE_RUNTIME_STATS_INTERVAL_TSQL
- SYS.QUERY_STORE_RUNTIME_STATS_INTERVAL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.query_store_runtime_stats_interval catalog view
- query_store_runtime_stats_interval catalog view
ms.assetid: 2be83785-0569-41a3-88c8-59bfa0932e6e
caps.latest.revision: 9
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 4357eaf9abe519cc3238acddedc6fc8168db5fa5
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33180077"
---
# <a name="sysquerystoreruntimestatsinterval-transact-sql"></a>Sys.query_store_runtime_stats_interval (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Contiene informazioni sull'ora di inizio e fine di ogni intervallo su cui runtime raccolto informazioni statistiche di esecuzione per una query.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**runtime_stats_interval_id**|**bigint**|Chiave primaria.|  
|**start_time**|**datetimeoffset**|Ora di inizio dell'intervallo.|  
|**end_time**|**datetimeoffset**|Ora di fine dell'intervallo.|  
|**Commento**|**nvarchar(32)**|Sempre NULL.|  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede il **VIEW DATABASE STATE** autorizzazione.  
  
## <a name="see-also"></a>Vedere anche  
 [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys.query_context_settings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [sys.query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)   
 [sys.query_store_query &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)   
 [sys.query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys.query_store_runtime_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md)   
 [sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)  
 [Monitoraggio delle prestazioni tramite Archivio query](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Stored procedure di archivio query &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  
  
  
