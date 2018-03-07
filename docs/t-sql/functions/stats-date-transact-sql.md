---
title: STATS_DATE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 12/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STATS_DATE_TSQL
- STATS_DATE
dev_langs:
- TSQL
helpviewer_keywords:
- statistical information [SQL Server], last time updated
- STATS_DATE function
- query optimization statistics [SQL Server], last time updated
- last time statistics updated
- stats update date
ms.assetid: f9ec3101-1e41-489d-b519-496a0d6089fb
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: de308046d069b6efa6115cf1efae33af7c07128c
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2018
---
# <a name="statsdate-transact-sql"></a>STATS_DATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce la data dell'aggiornamento più recente delle statistiche per una tabella o vista indicizzata.  
  
 Per ulteriori informazioni sull'aggiornamento delle statistiche, vedere [statistiche](../../relational-databases/statistics/statistics.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
STATS_DATE ( object_id , stats_id )  
```  
  
## <a name="arguments"></a>Argomenti  
 *object_id*  
 ID della tabella o della vista indicizzata contenente le statistiche.  
  
 *stats_id*  
 ID dell'oggetto statistiche.  
  
## <a name="return-types"></a>Tipi restituiti  
 Restituisce **datetime** in caso di esito positivo. Restituisce **NULL** se non è stato creato un blob di statistiche.  
  
## <a name="remarks"></a>Osservazioni  
 È possibile utilizzare funzioni di sistema nell'elenco di selezione, nella clausola WHERE e in tutti i casi in cui è consentita un'espressione.  
 
 Data di aggiornamento delle statistiche viene archiviato nel [oggetto blob statistiche](../../relational-databases/statistics/statistics.md#DefinitionQOStatistics) insieme il [istogramma](../../relational-databases/statistics/statistics.md#histogram) e [vettore di densità](../../relational-databases/statistics/statistics.md#density), non nei metadati. Quando viene letto alcun dato per generare i dati delle statistiche, non viene creato il blob di statistiche e la data non è disponibile. Questo vale per le statistiche filtrate per cui il predicato non restituisce alcuna riga, o per le nuove tabelle vuote.
 
 Se le statistiche corrispondono a un indice, il *stats_id* valore nel [Sys. Stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md) vista del catalogo è identico il *index_id* valore il [Sys. Indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md) vista del catalogo.
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo predefinito del database db_owner o l'autorizzazione per la visualizzazione dei metadati per la tabella o la vista indicizzata.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-return-the-dates-of-the-most-recent-statistics-for-a-table"></a>A. Recupero delle date delle statistiche più recenti per una tabella  
 L'esempio seguente restituisce la data dell'aggiornamento più recente di ogni oggetto statistiche nella tabella `Person.Address`.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT name AS stats_name,   
    STATS_DATE(object_id, stats_id) AS statistics_update_date  
FROM sys.stats   
WHERE object_id = OBJECT_ID('Person.Address');  
GO  
```  
  
 Se le statistiche corrispondono a un indice, il *stats_id* valore nel [Sys. Stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md) vista del catalogo è identico il *index_id* valore il [Sys. Indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md) vista del catalogo e la query seguente restituisce gli stessi risultati della query precedente. Se le statistiche non corrispondono a un indice, vengono restituite nei risultati di sys.stats ma non in quelli di sys.indexes.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT name AS index_name,   
    STATS_DATE(object_id, index_id) AS statistics_update_date  
FROM sys.indexes   
WHERE object_id = OBJECT_ID('Person.Address');  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-learn-when-a-named-statistics-was-last-updated"></a>B. Informazioni statistiche denominata dell'ultimo aggiornamento  
 Nell'esempio seguente crea statistiche per la colonna LastName della tabella DimCustomer. Viene quindi eseguita una query per visualizzare la data delle statistiche. È possibile aggiornamenti delle statistiche e viene eseguito di nuovo la query per visualizzare la data di aggiornamento.  
  
```sql
--First, create a statistics object  
USE AdventureWorksPDW2012;  
GO  
CREATE STATISTICS Customer_LastName_Stats  
ON AdventureWorksPDW2012.dbo.DimCustomer (LastName)  
WITH SAMPLE 50 PERCENT;  
GO  
  
--Return the date when Customer_LastName_Stats was last updated  
USE AdventureWorksPDW2012;  
GO  
SELECT stats_id, name AS stats_name,   
    STATS_DATE(object_id, stats_id) AS statistics_date  
FROM sys.stats s  
WHERE s.object_id = OBJECT_ID('dbo.DimCustomer')  
    AND s.name = 'Customer_LastName_Stats';  
GO  
  
--Update Customer_LastName_Stats so it will have a different timestamp in the next query  
GO  
UPDATE STATISTICS dbo.dimCustomer (Customer_LastName_Stats);  
  
--Return the date when Customer_LastName_Stats was last updated.  
SELECT stats_id, name AS stats_name,   
    STATS_DATE(object_id, stats_id) AS statistics_date  
FROM sys.stats s  
WHERE s.object_id = OBJECT_ID('dbo.DimCustomer')  
    AND s.name = 'Customer_LastName_Stats';  
GO    
```  
  
### <a name="c-view-the-date-of-the-last-update-for-all-statistics-on-a-table"></a>C. Visualizza la data dell'ultimo aggiornamento per tutte le statistiche in una tabella  
 In questo esempio restituisce la data di quando ogni oggetto statistiche per la tabella DimCustomer dell'ultimo aggiornamento.  
  
```sql  
--Return the dates all statistics on the table were last updated.  
SELECT stats_id, name AS stats_name,   
    STATS_DATE(object_id, stats_id) AS statistics_date  
FROM sys.stats s  
WHERE s.object_id = OBJECT_ID('dbo.DimCustomer');  
GO  
```  
  
 Se le statistiche corrispondono a un indice, il *stats_id* valore nel [Sys. Stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md) vista del catalogo è identico il *index_id* valore il [Sys. Indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md) vista del catalogo e la query seguente restituisce gli stessi risultati della query precedente. Se le statistiche non corrispondono a un indice, vengono restituite nei risultati di sys.stats ma non in quelli di sys.indexes.  
  
```sql  
USE AdventureWorksPDW2012;  
GO  
SELECT name AS index_name,   
    STATS_DATE(object_id, index_id) AS statistics_update_date  
FROM sys.indexes   
WHERE object_id = OBJECT_ID('dbo.DimCustomer');  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)   
 [sp_autostats &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-autostats-transact-sql.md)   
 [Statistiche](../../relational-databases/statistics/statistics.md)    
 [sys.dm_db_stats_properties &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-properties-transact-sql.md)   
 [sys.stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)   
  
  

