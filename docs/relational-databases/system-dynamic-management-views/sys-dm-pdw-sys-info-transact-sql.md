---
title: sys.dm_pdw_sys_info (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 686976b4-2d5d-4d64-bf12-56eba1dc59b1
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: e1fe45c9844346b96da561dc48786ffbed963d77
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmpdwsysinfo-transact-sql"></a>sys.dm_pdw_sys_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Fornisce un set di contatori a livello di dispositivo che riflettono l'attività complessiva nel dispositivo.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|total_sessions|**int**|Numero di sessioni attualmente nel sistema.|0 per max_active_sessions (vedere sotto).|  
|idle_sessions|**int**|Numero di sessioni attualmente inattive.||  
|active_requests|**int**|Numero di richieste attive in esecuzione.||  
|queued_requests|**int**|Numero di richieste attualmente in coda.||  
|active_loads|**int**|Numero di caricamenti attualmente in esecuzione nel sistema.||  
|queued_loads|**int**|Numero di caricamenti in coda in attesa di esecuzione.||  
|active_backups|**int**|Numero di backup attualmente in esecuzione.||  
|active_restores|**int**|Numero di ripristini backup attualmente in esecuzione.||  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e Parallel Data Warehouse, viste a gestione dinamica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
