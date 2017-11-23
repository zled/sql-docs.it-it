---
title: "Sys.dm os_memory_brokers – (Transact-SQL) | Documenti Microsoft"
ms.custom: 
ms.date: 08/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_os_memory_brokers
- dm_os_memory_brokers_TSQL
- sys.dm_os_memory_brokers_TSQL
- dm_os_memory_brokers
dev_langs: TSQL
helpviewer_keywords: sys.dm_os_memory_brokers dynamic management view
ms.assetid: 48dd6ad9-0d36-4370-8a12-4921d0df4b86
caps.latest.revision: "20"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c2b1a1d13e4a15df92d79bf74d1358352a93266a
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmosmemorybrokers-transact-sql"></a>sys.dm_os_memory_brokers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le allocazioni interne a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzano il gestore della memoria di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Registrazione della differenza tra i contatori di memoria del processo da **Sys.dm os_process_memory** e i contatori interni possono indicare l'utilizzo di memoria da componenti esterni nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spazio di memoria.  
  
 I broker della memoria distribuiscono equamente le allocazioni di memoria tra i vari componenti all'interno di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], in base all'utilizzo corrente e previsto. I broker di memoria non eseguono allocazioni. Le registrano solo per calcolare la distribuzione.  
  
 Nella tabella seguente sono disponibili informazioni sui broker di memoria.  
  
> [!NOTE]  
>  Per chiamare questo metodo dal [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilizzare il nome **sys.dm_pdw_nodes_os_memory_brokers**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**pool_id**|**int**|ID del pool di risorse se associato a un pool di Resource Governor.|  
|**memory_broker_type**|**nvarchar(60)**|Tipo di broker di memoria. Esistono attualmente tre tipi di Broker di memoria in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], indicata di seguito, con le relative descrizioni.<br /><br /> **MEMORYBROKER_FOR_CACHE** : la memoria allocata per l'utilizzo da memorizzati nella cache gli oggetti.<br /><br /> **MEMORYBROKER_FOR_STEAL** : memoria prelevata dal pool di buffer. Tale memoria non è disponibile per il riutilizzo da parte di altri componenti fino a che non viene liberata dal proprietario corrente.<br /><br /> **MEMORYBROKER_FOR_RESERVE** : memoria riservata per utilizzi futuri da richieste attualmente in esecuzione.|  
|**allocations_kb**|**bigint**|Quantità di memoria, in kilobyte (KB), allocata a questo tipo di broker.|  
|**allocations_kb_per_sec**|**bigint**|Velocità delle allocazioni di memoria in kilobyte (KB) al secondo. Il valore può essere negativo per le deallocazioni di memoria.|  
|**predicted_allocations_kb**|**bigint**|Quantità stimata di memoria allocata dal broker. Si basa sul modello di utilizzo della memoria.|  
|**target_allocations_kb**|**bigint**|Quantità consigliata di memoria allocata, in kilobyte (KB) basata sulle impostazioni correnti e sul modello di utilizzo della memoria. Il broker deve crescere o diminuire fino a questo numero.|  
|**future_allocations_kb**|**bigint**|Numero previsto di allocazioni, in kilobyte (KB), che verranno effettuate nei prossimi secondi.|  
|**overall_limit_kb**|**bigint**|Quantità massima di memoria, in kilobyte (KB), allocabile dal broker.|  
|**last_notification**|**nvarchar(60)**|Indicazione sull'utilizzo della memoria basato sulle impostazioni correnti e sul modello di utilizzo. I valori validi sono i seguenti:<br /><br /> grow<br /><br /> shrink<br /><br /> stable|  
|**pdw_node_id**|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L'identificatore per il nodo che utilizza questo tipo di distribuzione.|  
  
## <a name="permissions"></a>Permissions  
In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], richiede `VIEW SERVER STATE` autorizzazione.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli Premium, è necessario il `VIEW DATABASE STATE` autorizzazione per il database. In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli Standard e Basic, è necessario il **amministratore del Server** o **amministratore di Azure Active Directory** account.  s  
  
## <a name="see-also"></a>Vedere anche  

  [Relative al sistema operativo SQL Server viste a gestione dinamica &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


