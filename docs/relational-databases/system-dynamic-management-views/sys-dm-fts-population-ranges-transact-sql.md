---
title: Sys.dm fts_population_ranges (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_fts_population_ranges
- sys.dm_fts_population_ranges_TSQL
- dm_fts_population_ranges_TSQL
- dm_fts_population_ranges
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_population_ranges dynamic management view
ms.assetid: 58d8564b-9c43-4965-a31c-2893890334ef
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 434dcf58b6c88ea473a6c8de02cb232c6563ac82
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2018
ms.locfileid: "34467217"
---
# <a name="sysdmftspopulationranges-transact-sql"></a>sys.dm_fts_population_ranges (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce informazioni sugli intervalli specifici correlati a un popolamento dell'indice full-text in corso.  
   
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**memory_address**|**varbinary(8)**|Indirizzo dei buffer di memoria allocati per l'attività correlata all'intervallo secondario corrente del popolamento di un indice full-text.|  
|**parent_memory_address**|**varbinary(8)**|Indirizzo dei buffer di memoria che rappresentano l'oggetto padre di tutti gli intervalli di popolamento correlati a un indice full-text.|  
|**is_retry**|**bit**|Se il valore è 1, questo intervallo secondario è responsabile del nuovo tentativo di esecuzione di righe in cui si sono verificati errori.|  
|**session_id**|**smallint**|ID della sessione che elabora l'attività.|  
|**processed_row_count**|**int**|Numero di righe elaborate dall'intervallo. Lo stato viene mantenuto e calcolato ogni 5 minuti, anziché con il commit di ogni batch.|  
|**error_count**|**int**|Numero di righe in cui l'intervallo ha rilevato errori. Lo stato viene mantenuto e calcolato ogni 5 minuti, anziché con il commit di ogni batch.|  
  
## <a name="permissions"></a>Autorizzazioni  

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], richiede `VIEW SERVER STATE` autorizzazione.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], richiede il `VIEW DATABASE STATE` autorizzazione per il database.   
 
## <a name="physical-joins"></a>Join fisici  
 ![Join significativi di questa vista a gestione dinamica](../../relational-databases/system-dynamic-management-views/media/join-dm-fts-population-ranges-1.gif "join significativi di questa vista a gestione dinamica")  
  
## <a name="relationship-cardinalities"></a>Cardinalità delle relazioni  
  
|From|Per|Relazione|  
|----------|--------|------------------|  
|dm_fts_population_ranges.parent_memory_address|dm_fts_index_population.memory_address|Molti-a-uno|  
  
## <a name="see-also"></a>Vedere anche  
  [Funzioni e viste a gestione dinamica ricerca semantica e ricerca full-Text &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)  
  
  

