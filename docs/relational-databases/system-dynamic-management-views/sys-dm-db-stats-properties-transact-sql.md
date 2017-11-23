---
title: Sys.dm db_stats_properties (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/05/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_db_stats_properties_TSQL
- sys.dm_db_stats_properties
- dm_db_stats_properties_TSQL
- dm_db_stats_properties
dev_langs: TSQL
helpviewer_keywords: sys.dm_db_stats_properties
ms.assetid: 8a54889d-e263-4881-9fcb-b1db410a9453
caps.latest.revision: "13"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: e2a1ebc3301372b490de9ec631c3cdb0743f264b
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmdbstatsproperties-transact-sql"></a>sys.dm_db_stats_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Vengono restituite le proprietà di statistiche per l'oggetto di database specificato (tabella o vista indicizzata) nel database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] corrente. Per le tabelle partizionate, vedere simile [sys.dm_db_incremental_stats_properties](../../relational-databases/system-dynamic-management-views/sys-dm-db-incremental-stats-properties-transact-sql.md). 
 
## <a name="syntax"></a>Sintassi  
  
```  
sys.dm_db_stats_properties (object_id, stats_id)  
```  
  
## <a name="arguments"></a>Argomenti  
 *object_id*  
 ID dell'oggetto nel database corrente per il quale sono richieste le proprietà di una delle relative statistiche. *object_id* è di tipo **int**.  
  
 *stats_id*  
 ID delle statistiche per l'oggetto *object_id*specificato. L'ID delle statistiche può essere ottenuto dalla DMV [sys.stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md) . *stats_id* è di tipo **int**.  
  
## <a name="table-returned"></a>Tabella restituita  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|object_id|**int**|ID dell'oggetto (tabella o vista indicizzata) per cui restituire le proprietà dell'oggetto statistiche.|  
|stats_id|**int**|ID dell'oggetto statistiche. Univoco all'interno della tabella o della vista indicizzata. Per altre informazioni, vedere [sys.stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md).|  
|last_updated|**datetime2**|Data e ora dell'ultimo aggiornamento dell'oggetto statistiche.|  
|rows|**bigint**|Numero totale di righe della tabella o della vista indicizzata al momento dell'ultimo aggiornamento delle statistiche. Se le statistiche vengono filtrate o corrispondono a un indice filtrato, il numero di righe potrebbe essere inferiore al numero di righe della tabella.|  
|rows_sampled|**bigint**|Numero totale di righe campionate per i calcoli statistici.|  
|passaggi|**int**|Numero di intervalli nell'istogramma. Per altre informazioni, vedere [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md).|  
|unfiltered_rows|**bigint**|Numero totale di righe nella tabella prima dell'applicazione dell'espressione di filtro (per statistiche filtrate). Se le statistiche non vengono filtrate, unfiltered_rows corrisponde al valore restituito nella colonna rows.|  
|modification_counter|**bigint**|Numero totale di modifiche per la colonna iniziale delle statistiche, la colonna in cui viene compilato l'istogramma, dall'ultimo aggiornamento delle statistiche.<br /><br /> Le tabelle con ottimizzazione per la memoria: avvio [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] e [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] questa colonna contiene: numero totale di modifiche per la tabella poiché sono state aggiornate le statistiche temporali ultimo o il database è stato riavviato.|  
|persisted_sample_percent|**float**|Persistente la percentuale di campionamento utilizzata per gli aggiornamenti delle statistiche che non specificano in modo esplicito una percentuale di campionamento. Se il valore è zero, verrà impostata alcuna percentuale di esempio persistente per la statistica.<br /><br /> **Si applica a:** [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 CU4|  
  
## <a name="remarks"></a>Osservazioni  
 **Sys.dm db_stats_properties** restituisce un set di righe vuoto in presenza delle condizioni seguenti:  
  
-   **object_id** o **stats_id** è NULL.  
  
-   L'oggetto specificato non viene trovato oppure non corrisponde a una tabella o a una vista indicizzata.  
  
-   L'ID delle statistiche specificato non corrisponde alle statistiche esistenti per l'ID oggetto specificato.  
  
-   L'utente corrente non dispone delle autorizzazioni per visualizzare l'oggetto statistiche.  
  
 Questo comportamento consente l'utilizzo sicuro di **Sys.dm db_stats_properties** quando tra applicato alle righe nelle viste, ad esempio **Sys. Objects** e **Sys. Stats**.  
  
## <a name="permissions"></a>Permissions  
 L'utente deve avere autorizzazioni di selezione per le colonne delle statistiche o essere proprietario della tabella o membro del ruolo predefinito del server `sysadmin`, del ruolo predefinito del database `db_owner` o del ruolo predefinito del database `db_ddladmin`.  
  
## <a name="examples"></a>Esempi  

### <a name="a-simple-example"></a>A. Esempio semplice
Nell'esempio seguente restituisce le statistiche per il `Person.Person` tabella nel database AdventureWorks.

```
SELECT * FROM sys.dm_db_stats_properties (object_id('Person.Person'), 1);
``` 
  
### <a name="b-returning-all-statistics-properties-for-a-table"></a>B. Restituzione di tutte le proprietà di statistiche per una tabella  
 Nell'esempio seguente vengono restituite le proprietà di tutte le statistiche esistenti per la tabella TEST.  
  
```  
SELECT sp.stats_id, name, filter_definition, last_updated, rows, rows_sampled, steps, unfiltered_rows, modification_counter   
FROM sys.stats AS stat   
CROSS APPLY sys.dm_db_stats_properties(stat.object_id, stat.stats_id) AS sp  
WHERE stat.object_id = object_id('TEST');  
```  
  
### <a name="c-returning-statistics-properties-for-frequently-modified-objects"></a>C. Restituzione delle proprietà di statistiche per oggetti modificati di frequente  
 Nell'esempio seguente vengono restituite tutte le tabelle, le viste indicizzate e le statistiche nel database corrente per cui la colonna iniziale è stata modificata più di 1000 volte dall'ultimo aggiornamento delle statistiche.  
  
```  
SELECT obj.name, obj.object_id, stat.name, stat.stats_id, last_updated, modification_counter  
FROM sys.objects AS obj   
INNER JOIN sys.stats AS stat ON stat.object_id = obj.object_id  
CROSS APPLY sys.dm_db_stats_properties(stat.object_id, stat.stats_id) AS sp  
WHERE modification_counter > 1000;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [sys.stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)   
 [Funzioni e viste a gestione dinamica relative agli oggetti &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/object-related-dynamic-management-views-and-functions-transact-sql.md)   
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
 [Sys.dm_db_incremental_stats_properties (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-incremental-stats-properties-transact-sql.md)  
 [Sys.dm_db_stats_histogram (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md) 
  

