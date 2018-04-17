---
title: sys.dm_repl_tranhash (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
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
- sys.dm_repl_tranhash
- sys.dm_repl_tranhash_TSQL
- dm_repl_tranhash_TSQL
- dm_repl_tranhash
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_repl_tranhash dynamic management view
ms.assetid: 0cc52338-e805-4ed4-9835-b19bbf72448e
caps.latest.revision: 13
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0672044659b85992166f35ffb60be0c5a46dc339
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmrepltranhash-transact-sql"></a>sys.dm_repl_tranhash (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sulle transazioni replicate in una pubblicazione transazionale.  
  
|column_name|data_type|description|  
|------------------|----------------|-----------------|  
|**bucket**|**bigint**|Numero di bucket nella tabella hash.|  
|**hashed_trans**|**bigint**|Numero di transazioni replicate nel batch corrente di cui è stato eseguito il commit.|  
|**completed_trans**|**bigint**|Numero di transazioni finora completate.|  
|**compensated_trans**|**bigint**|Numero di transazioni contenenti rollback parziali.|  
|**first_begin_lsn**|**nvarchar(64)**|Numero di sequenza del file di log (LSN) iniziale meno recente nel batch corrente.|  
|**last_commit_lsn**|**nvarchar(64)**|Ultimo LSN di commit nel batch corrente.|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW DATABASE STATE nel database di pubblicazione per chiamare **dm_repl_tranhash**.  
  
## <a name="remarks"></a>Osservazioni  
 Vengono restituite informazioni solo per gli oggetti di database replicati caricati nella cache dell'articolo di replica.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Viste a gestione dinamica relative alle repliche &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/replication-related-dynamic-management-views-transact-sql.md)  
  
  
