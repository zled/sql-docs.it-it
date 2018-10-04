---
title: Sys.dm_fts_population_ranges (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
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
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ad5734a13224df89c034087863cbd39af0b919d3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47763689"
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
  
## <a name="permissions"></a>Permissions  

Sul [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], è necessario `VIEW SERVER STATE` autorizzazione.   
Sul [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], è necessario il `VIEW DATABASE STATE` autorizzazione nel database.   
 
## <a name="physical-joins"></a>Join fisici  
 ![Join significativi di questa vista a gestione dinamica](../../relational-databases/system-dynamic-management-views/media/join-dm-fts-population-ranges-1.gif "join significativi di questa vista a gestione dinamica")  
  
## <a name="relationship-cardinalities"></a>Cardinalità delle relazioni  
  
|From|Per|Relazione|  
|----------|--------|------------------|  
|dm_fts_population_ranges.parent_memory_address|dm_fts_index_population.memory_address|Molti-a-uno|  
  
## <a name="see-also"></a>Vedere anche  
  [Funzioni e viste a gestione dinamica la ricerca semantica e ricerca full-Text &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)  
  
  

