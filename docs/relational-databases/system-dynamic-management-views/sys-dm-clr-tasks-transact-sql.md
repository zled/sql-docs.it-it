---
title: sys.dm_clr_tasks (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_clr_tasks
- sys.dm_clr_tasks_TSQL
- dm_clr_tasks
- dm_clr_tasks_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_clr_tasks dynamic management view
ms.assetid: 462b9061-09fa-4858-9707-03d6cc19c769
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2a3c99ffd172c97c5738ed2dd19bc8b07f303470
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmclrtasks-transact-sql"></a>sys.dm_clr_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce una riga per tutte le attività CLR (Common Language Runtime) in esecuzione. Un batch [!INCLUDE[tsql](../../includes/tsql-md.md)] contenente un riferimento a una routine CLR crea un'attività distinta per l'esecuzione di tutto il codice gestito nel batch. La stessa attività CLR viene utilizzata da più istruzioni nel batch che richiedono l'esecuzione del codice gestito. L'attività CLR è responsabile del mantenimento di oggetti e stato relativi all'esecuzione del codice gestito, nonché delle transizioni tra l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e CLR.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**task_address**|**varbinary(8)**|Indirizzo dell'attività CLR.|  
|**sos_task_address**|**varbinary(8)**|Indirizzo dell'attività batch [!INCLUDE[tsql](../../includes/tsql-md.md)] sottostante.|  
|**appdomain_address**|**varbinary(8)**|Indirizzo del dominio applicazione in cui è in esecuzione l'attività.|  
|**state**|**nvarchar(128)**|Stato corrente dell'attività.|  
|**abort_state**|**nvarchar(128)**|Stato corrente dell'interruzione se l'attività è stata annullata. Durante l'interruzione delle attività si possono verificare più stati.|  
|**type**|**nvarchar(128)**|Tipo di attività.|  
|**affinity_count**|**int**|Affinità dell'attività.|  
|**forced_yield_count**|**int**|Numero di volte che l'attività è obbligata a restituire il controllo.|  
  
## <a name="permissions"></a>Autorizzazioni  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è necessaria l'autorizzazione VIEW SERVER STATE nel server.  
  
 In [!INCLUDE[ssSDS](../../includes/sssds-md.md)] livelli Premium richiede l'autorizzazione VIEW DATABASE STATE nel database. In [!INCLUDE[ssSDS](../../includes/sssds-md.md)] livelli Standard e Basic richiede il [!INCLUDE[ssSDS](../../includes/sssds-md.md)] account amministratore.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Common Language Runtime relative viste a gestione dinamica &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/common-language-runtime-related-dynamic-management-views-transact-sql.md)  
  
  

