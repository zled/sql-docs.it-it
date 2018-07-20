---
title: MSmerge_identity_range_allocations (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSmerge_identity_range_allocations
- MSmerge_identity_range_allocations_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_identity_range_allocations system table
ms.assetid: 6362e35e-0ab3-4638-855b-1ce013f5fd6d
caps.latest.revision: 13
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: df286fcd67db26ac149bd56d3635425453d78405
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39102789"
---
# <a name="msmergeidentityrangeallocations-transact-sql"></a>MSmerge_identity_range_allocations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSmerge_identity_range_allocations** tabella viene utilizzata per tenere traccia della cronologia di identità assegnazioni di intervalli, sia i server di pubblicazione e sottoscrittori, per gli articoli pubblicati. Questa tabella è archiviata nel database di distribuzione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|ID del server di pubblicazione.|  
|**publisher_db**|**nvarchar(128)**|Nome del database di pubblicazione.|  
|**pubblicazione**|**nvarchar(128)**|Nome della pubblicazione.|  
|**article**|**nvarchar(128)**|Nome dell'articolo.|  
|**subscriber**|**nvarchar(128)**|Nome del Sottoscrittore.|  
|**subscriber_db**|**nvarchar(128)**|Nome del database di sottoscrizione.|  
|**is_pub_range**|**bit**|Indica se l'intervallo di valori Identity è assegnato a un server di pubblicazione.|  
|**ranges_allocated**|**tinyint**|Numero di intervalli di valori Identity assegnati.|  
|**range_begin**|**Numeric(38)**|Valore iniziale dell'intervallo.|  
|**range_end**|**Numeric(38)**|Valore finale dell'intervallo.|  
|**next_range_begin**|**Numeric(38)**|Valore iniziale dell'intervallo successivo da assegnare.|  
|**next_range_end**|**Numeric(38)**|Valore finale dell'intervallo successivo da assegnare.|  
|**max_used**|**Numeric(38)**|Valore Identity più alto utilizzato.|  
|**time_of_allocation**|**datetime**|Ora in cui è stata eseguita l'assegnazione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
