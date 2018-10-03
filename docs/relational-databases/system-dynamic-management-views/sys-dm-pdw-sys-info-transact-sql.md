---
title: sys.dm_pdw_sys_info (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 686976b4-2d5d-4d64-bf12-56eba1dc59b1
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: ad7311759e2ea38f5b9b375785b7f035d1dcdbfa
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47821519"
---
# <a name="sysdmpdwsysinfo-transact-sql"></a>sys.dm_pdw_sys_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Fornisce un set di contatori a livello di dispositivo che riflettono l'attività complessiva nell'appliance.  
  
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
 [SQL Data Warehouse e Parallel Data Warehouse viste a gestione dinamica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
