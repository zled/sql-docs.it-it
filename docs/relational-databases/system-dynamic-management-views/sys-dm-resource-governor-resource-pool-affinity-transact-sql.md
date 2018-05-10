---
title: Sys.dm_resource_governor_resource_pool_affinity (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_resource_pool_affinity_TSQL
- sys.dm_resource_governor_resource_pool_affinity
- dm_resource_governor_resource_pool_affinity
- dm_resource_governor_resource_pool_affinity_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dm_resource_governor_resource_pool_affinity
- sys.dm_resource_governor_resource_pool_affinity
ms.assetid: a197ec19-a2ba-44f5-a4f2-3eee33ebd77d
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 02b8ecfc4081c32d242c96980716134714bd238b
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmresourcegovernorresourcepoolaffinity-transact-sql"></a>sys.dm_resource_governor_resource_pool_affinity (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Consente di tenere traccia dell'affinità di pool di risorse.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
|Nome colonna|Tipo di dati|Description|  
|----------------|---------------|-----------------|  
|Pool_id|**int**|ID del pool di risorse. Non ammette i valori Null.|  
|Processor_group|**smallint**|ID del gruppo di processori logici Windows. Non ammette i valori Null.|  
|Scheduler_mask|**bigint**|Maschera binaria che rappresenta le utilità di pianificazione associate a questo pool. Non ammette i valori Null.|  
  
## <a name="remarks"></a>Osservazioni  
 I pool creati con un'affinità equivalente ad AUTO non saranno visualizzati in questa vista perché non presentano affinità. Per altre informazioni, vedere la [CREATE RESOURCE POOL &#40;Transact-SQL&#41; ](../../t-sql/statements/create-resource-pool-transact-sql.md) e [ALTER RESOURCE POOL &#40;Transact-SQL&#41; ](../../t-sql/statements/alter-resource-pool-transact-sql.md) istruzioni.  
  
## <a name="see-also"></a>Vedere anche  
 [sys.dm_resource_governor_external_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)  
  
  
