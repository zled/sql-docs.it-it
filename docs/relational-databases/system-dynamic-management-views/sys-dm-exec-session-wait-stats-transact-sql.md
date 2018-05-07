---
title: Sys.dm exec_session_wait_stats (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 04/24/2018
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_session_wait_stats
- sys.dm_exec_session_wait_stats_tsql
- dm_exec_session_wait_stats
- dm_exec_session_wait_stats_tsql
helpviewer_keywords:
- sys.dm_exec_session_wait_stats
ms.assetid: df84842a-71eb-4fda-b448-5953cf9985dc
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ef6c58f615df530924440c747a10c08ca6cdd13e
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmexecsessionwaitstats-transact-sql"></a>sys.dm_exec_session_wait_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Restituisce informazioni su tutte le attese rilevate dai thread eseguiti per ogni sessione. È possibile utilizzare questa visualizzazione per diagnosticare problemi di prestazioni con la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sessione e anche con query e batch specifici.  Questa vista restituisce sessione le stesse informazioni vengono aggregate per il [DM os_wait_stats &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md) ma fornisce il **session_id** nonché numero.  
  
**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|session_id|**smallint**|L'id della sessione.|  
|wait_type|**nvarchar(60)**|Nome del tipo di attesa. Per altre informazioni, vedere [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md).|  
|waiting_tasks_count|**bigint**|Numero di attese del tipo specificato. Questo contatore viene incrementato all'inizio di ogni attesa.|  
|wait_time_ms|**bigint**|Tempo di attesa totale, espresso in millisecondi, per il tipo di attesa specifico. Il tempo comprende signal_wait_time_ms.|  
|max_wait_time_ms|**bigint**|Tempo di attesa massimo per il tipo di attesa specifico.|  
|signal_wait_time_ms|**bigint**|Differenza tra il momento in cui è stato rilevato il thread in attesa e quello in cui è stata avviata l'esecuzione del thread.|  
  
## <a name="remarks"></a>Osservazioni  
 Questa DMV Reimposta le informazioni per una sessione quando viene aperta la sessione oppure quando la sessione viene reimpostata (se il pool di connessioni),  
  
 Per informazioni sui tipi di attesa, vedere [DM os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 Se l'utente ha **VIEW SERVER STATE** autorizzazione nel server, l'utente vedrà le sessioni in esecuzione tutti nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; in caso contrario, l'utente vedrà solo la sessione corrente.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Viste a gestione dinamica relative al sistema di operativo SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)  
 
