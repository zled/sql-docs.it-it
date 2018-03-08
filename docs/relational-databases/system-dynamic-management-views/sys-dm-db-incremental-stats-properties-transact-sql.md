---
title: sys.dm_db_incremental_stats_properties (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 12/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server 2014
f1_keywords:
- sys.dm_db_incremental_stats_properties
- sys.dm_db_incremental_stats_properties_TSQL
- dm_db_incremental_stats_properties
- dm_db_incremental_stats_properties_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_incremental_stats_properties
ms.assetid: aa0db893-34d1-419c-b008-224852e71307
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6187179f6599404dac86f92403cba507eb5e5fcc
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmdbincrementalstatsproperties-transact-sql"></a>sys.dm_db_incremental_stats_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Restituisce le proprietà di statistiche incrementali per l'oggetto di database specificato (tabella) nel database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] corrente. L'uso di `sys.dm_db_incremental_stats_properties` (che contiene un numero di partizione) è simile a `sys.dm_db_stats_properties` usato per le statistiche non incrementali. 
  
  Questa funzione è stata introdotta in [!INCLUDE[ssSQL14_md](../../includes/sssql14-md.md)] Service Pack 2 e [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] Service Pack 1.
  
## <a name="syntax"></a>Sintassi  
  
```  
sys.dm_db_incremental_stats_properties (object_id, stats_id)  
```  
  
## <a name="arguments"></a>Argomenti  
 *object_id*  
 ID dell'oggetto nel database corrente per il quale sono richieste le proprietà di una delle relative statistiche incrementali. *object_id* è di tipo **int**.  
  
 *stats_id*  
 ID delle statistiche per l'oggetto *object_id*specificato. L'ID delle statistiche può essere ottenuto dalla DMV [sys.stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md) . *stats_id* è di tipo **int**.  
  
## <a name="table-returned"></a>Tabella restituita  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|object_id|**int**|ID dell'oggetto (tabella) per cui restituire le proprietà dell'oggetto statistiche.|  
|stats_id|**int**|ID dell'oggetto statistiche. Il valore è univoco all'interno della tabella. Per altre informazioni, vedere [sys.stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md).|
|partition_number|**int**|Numero di partizione che contiene la parte della tabella.|  
|last_updated|**datetime2**|Data e ora dell'ultimo aggiornamento dell'oggetto statistiche. Per ulteriori informazioni, vedere il [osservazioni](#Remarks) sezione in questa pagina.|  
|rows|**bigint**|Numero totale di righe della tabella al momento dell'ultimo aggiornamento delle statistiche. Se le statistiche vengono filtrate o corrispondono a un indice filtrato, il numero di righe potrebbe essere inferiore al numero di righe della tabella.|  
|rows_sampled|**bigint**|Numero totale di righe campionate per i calcoli statistici.|  
|passaggi|**int**|Numero di intervalli nell'istogramma. Per altre informazioni, vedere [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md).|  
|unfiltered_rows|**bigint**|Numero totale di righe nella tabella prima dell'applicazione dell'espressione di filtro (per statistiche filtrate). Se le statistiche non vengono filtrate, unfiltered_rows corrisponde al valore restituito nella colonna rows.|  
|modification_counter|**bigint**|Numero totale di modifiche per la colonna iniziale delle statistiche, la colonna in cui viene compilato l'istogramma, dall'ultimo aggiornamento delle statistiche.<br /><br /> Questa colonna non contiene informazioni per le tabelle ottimizzate per la memoria.|  
  
## <a name="Remarks"></a> Osservazioni  
 `sys.dm_db_incremental_stats_properties` restituisce un set di righe vuoto in base a una delle condizioni seguenti:  
  
-   `object_id` o `stats_id` è NULL.   
-   L'oggetto specificato non viene trovato oppure non corrisponde a una tabella con statistiche incrementali.  
-   L'ID delle statistiche specificato non corrisponde alle statistiche esistenti per l'ID oggetto specificato.  
-   L'utente corrente non dispone delle autorizzazioni per visualizzare l'oggetto statistiche.
 
 Questo comportamento consente l'utilizzo sicuro di `sys.dm_db_incremental_stats_properties` in caso di applicazione incrociata in viste quali `sys.objects` e `sys.stats`. Questo metodo può restituire le proprietà per le statistiche che corrispondono a ogni partizione. Per visualizzare le proprietà per le statistiche unite combinate in tutte le partizioni, usare sys.dm_db_stats_properties. 

Data di aggiornamento delle statistiche viene archiviato nel [oggetto blob statistiche](../../relational-databases/statistics/statistics.md#DefinitionQOStatistics) insieme il [istogramma](../../relational-databases/statistics/statistics.md#histogram) e [vettore di densità](../../relational-databases/statistics/statistics.md#density), non nei metadati. Quando viene letto alcun dato per generare i dati delle statistiche, non viene creato il blob di statistiche, la data non è disponibile e *last_updated* colonna è NULL. Questo vale per le statistiche filtrate per cui il predicato non restituisce alcuna riga, o per le nuove tabelle vuote.

## <a name="permissions"></a>Autorizzazioni  
 L'utente deve avere autorizzazioni di selezione per le colonne delle statistiche o essere proprietario della tabella o membro del ruolo predefinito del server `sysadmin`, del ruolo predefinito del database `db_owner` o del ruolo predefinito del database `db_ddladmin`.  
  
## <a name="examples"></a>Esempi  

### <a name="a-simple-example"></a>A. Esempio semplice
L'esempio seguente restituisce le statistiche per la tabella `PartitionTable` descritta nell'argomento [Creare tabelle e indici partizionati](../../relational-databases/partitions/create-partitioned-tables-and-indexes.md).

```sql
SELECT * FROM sys.dm_db_incremental_stats_properties (object_id('PartitionTable'), 1);
``` 

Per altre informazioni sull'utilizzo, vedere  [sys.dm_db_stats_properties](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-properties-transact-sql.md).
  
## <a name="see-also"></a>Vedere anche  
 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [sys.stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)   
 [Funzioni e viste a gestione dinamica relative agli oggetti &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/object-related-dynamic-management-views-and-functions-transact-sql.md)   
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
 [sys.dm_db_stats_properties](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-properties-transact-sql.md)   
 [sys.dm_db_stats_histogram (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md) 
