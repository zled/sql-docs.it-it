---
title: sys.dm_os_dispatcher_pools (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_os_dispatcher_pools_TSQL
- dm_os_dispatcher_pools
- sys.dm_os_dispatcher_pools
- sys.dm_os_dispatcher_pools_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- extended events [SQL Server], views
- sys.dm_os_dispatcher_pools DMV
ms.assetid: b9edbc83-c6bc-4753-9bb5-a454cfe7d6bf
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 65f149f5fc1478fabaff8735c55f16fc8e32f421
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmosdispatcherpools-transact-sql"></a>sys.dm_os_dispatcher_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce le informazioni sui pool di dispatcher di sessione. I pool di dispatcher sono pool di thread utilizzati dai componenti del sistema per eseguire elaborazioni di fondo.  
  
> [!NOTE]  
>  Per chiamare questo metodo dal [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilizzare il nome **sys.dm_pdw_nodes_os_dispatcher_pools**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|dispatcher_pool_address|**varbinary(8)**|Indirizzo del pool di dispatcher. dispatcher_pool_address è univoco. Non ammette i valori Null.|  
|Tipo|**nvarchar(256)**|Tipo del pool di dispatcher. Non ammette i valori Null. Esistono due tipi di pool di dispatcher:<br /><br /> DISP_POOL_XE_ENGINE<br /><br /> DISP_POOL_XE_SESSION<br /><br /> Eseguire una query sulla DMV per un elenco completo|  
|name|**nvarchar(256)**|Nome del pool di dispatcher. Non ammette i valori Null.|  
|dispatcher_count|**int**|Numero di thread del dispatcher attivi. Non ammette i valori Null.|  
|dispatcher_ideal_count|**int**|Numero di thread del dispatcher che il pool di dispatcher può iniziare a utilizzare. Non ammette i valori Null.|  
|dispatcher_timeout_ms|**int**|Il tempo, espresso in millisecondi, durante il quale un dispatcher dovrà attendere per un nuovo lavoro prima di uscire. Non ammette i valori Null.|  
|dispatcher_waiting_count|**int**|Numero di thread del dispatcher non attivi. Non ammette i valori Null.|  
|queue_length|**int**|Numero di elementi di lavoro che aspettano di essere gestiti dal pool del dispatcher. Non ammette i valori Null.|  
|pdw_node_id|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L'identificatore per il nodo che utilizza questo tipo di distribuzione.|  
  
## <a name="permissions"></a>Autorizzazioni

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], richiede `VIEW SERVER STATE` autorizzazione.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], richiede il `VIEW DATABASE STATE` autorizzazione per il database.   

## <a name="see-also"></a>Vedere anche  
  
  


