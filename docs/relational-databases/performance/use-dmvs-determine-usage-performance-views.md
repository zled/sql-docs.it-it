---
title: Usare DMV per determinare le statistiche di utilizzo e le prestazioni delle viste
description: Usare DMV per determinare le statistiche di utilizzo e le prestazioni delle viste
manager: craigg
author: MashaMSFT
ms.author: mathoma
ms.date: 09/27/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.openlocfilehash: 1ac9c72ecee9beee66ea190b3acf233a0e4bc753
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47618409"
---
# <a name="use-dmvs-to-determine-usage-statistics-and-performance-of-views"></a>Usare DMV per determinare le statistiche di utilizzo e le prestazioni delle viste

Questo articolo illustra la metodologia e gli script usati per ottenere informazioni sulle **prestazioni delle query che usano viste** in un oggetto di database. La finalità di questi script è fornire indicatori dell'uso e delle prestazioni delle varie viste disponibili all'interno di un database. 

## <a name="sysdmexecqueryoptimizerinfo"></a>Sys.dm_exec_query_optimizer_info

La vista DMV [sys.dm_exec_query_optimizer_info](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-optimizer-info-transact-sql) espone le statistiche sulle ottimizzazioni eseguite da Query Optimizer di SQL Server. Questi valori sono cumulativi e la registrazione inizia all'avvio di SQL Server.  

L'espressione di tabella comune (CTE, common_table_expression) seguente usa questa DMV per fornire informazioni sul carico di lavoro, ad esempio la percentuale di query che fanno riferimento a una vista. I risultati restituiti da questa query non indicano un problema di prestazioni da soli, ma possono esporre problemi sottostanti in combinazione con i reclami degli utenti per query lente. 


```SQL
WITH CTE_QO AS
(
  SELECT
    occurrence
  FROM
    sys.dm_exec_query_optimizer_info
  WHERE
    ([counter] = 'optimizations')
),
QOInfo AS
(
  SELECT
    [counter]
    ,[%] = CAST((occurrence * 100.00)/(SELECT occurrence FROM CTE_QO) AS DECIMAL(5, 2))
  FROM
    sys.dm_exec_query_optimizer_info
  WHERE
    [counter] IN ('optimizations'
                  ,'trivial plan'
                  ,'no plan'
                  ,'search 0'
                  ,'search 1'
                  ,'search 2'
                  ,'timeout'
                  ,'memory limit exceeded'
                  ,'insert stmt'
                  ,'delete stmt'
                  ,'update stmt'
                  ,'merge stmt'
                  ,'contains subquery'
                  ,'view reference'
                  ,'remote query'
                  ,'dynamic cursor request'
                  ,'fast forward cursor request'
             )
)
SELECT
  [optimizations] AS [optimizations %]
  ,[trivial plan] AS [trivial plan %]
  ,[no plan] AS [no plan %]
  ,[search 0] AS [search 0 %]
  ,[search 1] AS [search 1 %]
  ,[search 2] AS [search 2 %]
  ,[timeout] AS [timeout %]
  ,[memory limit exceeded] AS [memory limit exceeded %]
  ,[insert stmt] AS [insert stmt %]
  ,[delete stmt] AS [delete stmt]
  ,[update stmt] AS [update stmt]
  ,[merge stmt] AS [merge stmt]
  ,[contains subquery] AS [contains subquery %]
  ,[view reference] AS [view reference %]
  ,[remote query] AS [remote query %]
  ,[dynamic cursor request] AS [dynamic cursor request %]
  ,[fast forward cursor request] AS [fast forward cursor request %]
FROM
  QOInfo
PIVOT (MAX([%]) FOR [counter] 
  IN ([optimizations]
      ,[trivial plan]
      ,[no plan]
      ,[search 0]
      ,[search 1]
      ,[search 2]
      ,[timeout]
      ,[memory limit exceeded]
      ,[insert stmt]
      ,[delete stmt]
      ,[update stmt]
      ,[merge stmt]
      ,[contains subquery]
      ,[view reference]
      ,[remote query]
      ,[dynamic cursor request]
      ,[fast forward cursor request])) AS p;
GO
```
Combinare i risultati di questa query con i risultati della vista di sistema [sys.views](https://docs.microsoft.com/sql/relational-databases/system-catalog-views/sys-views-transact-sql) per identificare le statistiche sulle query, il testo delle query e il piano di esecuzione memorizzato nella cache. 

## <a name="sysviews"></a>Sys.views

L'espressione CTE seguente fornisce informazioni sul numero di esecuzioni, il tempo totale di esecuzione e le pagine lette dalla memoria. I risultati possono essere usati per identificare le query potenziali candidate per l'ottimizzazione. 
  
  >[!NOTE]
  > I risultati di questa query possono variare a seconda della versione di SQL Server.  


```SQL
WITH CTE_VW_STATS AS
(
  SELECT
    SCHEMA_NAME(vw.schema_id) AS schemaname
    ,vw.name AS viewname
    ,vw.object_id AS viewid
  FROM
    sys.views AS vw
  WHERE
    (vw.is_ms_shipped = 0)
  INTERSECT
  SELECT
    SCHEMA_NAME(o.schema_id) AS schemaname
    ,o.Name AS name
    ,st.objectid AS viewid
  FROM
    sys.dm_exec_cached_plans cp
  CROSS APPLY
    sys.dm_exec_sql_text(cp.plan_handle) st
  INNER JOIN
    sys.objects o ON st.[objectid] = o.[object_id]
  WHERE
    st.dbid = DB_ID()
)
SELECT
  vw.schemaname
  ,vw.viewname
  ,vw.viewid
  ,DB_NAME(t.databaseid) AS databasename
  ,t.databaseid
  ,t.*
FROM
  CTE_VW_STATS AS vw
CROSS APPLY
  (
    SELECT
      st.dbid AS databaseid
      ,st.text
      ,qp.query_plan
      ,qs.*
    FROM
      sys.dm_exec_query_stats AS qs
    CROSS APPLY
      sys.dm_exec_sql_text(qs.plan_handle) AS st
    CROSS APPLY
      sys.dm_exec_query_plan(qs.plan_handle) AS qp
    WHERE
      (CHARINDEX(vw.schemaname, st.text, 1) > 0)
      AND (st.dbid = DB_ID())
  ) AS t;
GO
```

## <a name="sysdmvexeccachedplans"></a>Sys.dmv_exec_cached_plans

La query finale offre informazioni sulle viste inutilizzate usando la DMV [sys.dmv_exec_cached_plans](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql). Tuttavia, la cache dei piani di esecuzione è dinamica e i risultati possono variare. Di conseguenza, usare questa query nel tempo per determinare se una vista viene effettivamente usata. 


```SQL
SELECT
  SCHEMA_NAME(vw.schema_id) AS schemaname
  ,vw.name AS name
  ,vw.object_id AS viewid
FROM
  sys.views AS vw
WHERE
  (vw.is_ms_shipped = 0)
EXCEPT
SELECT
  SCHEMA_NAME(o.schema_id) AS schemaname
  ,o.name AS name
  ,st.objectid AS viewid
FROM
  sys.dm_exec_cached_plans cp
CROSS APPLY
  sys.dm_exec_sql_text(cp.plan_handle) st
INNER JOIN
  sys.objects o ON st.[objectid] = o.[object_id]
WHERE
  st.dbid = DB_ID();
GO
```

## <a name="related-external-resources"></a>Risorse esterne correlate

- [DMVs for Performance Tuning (Video - SQL Saturday Pordenone)](https://www.youtube.com/watch?v=9FQaFwpt3-k) (DMV per l'ottimizzazione delle prestazioni - Video da SQL Saturday Pordenone)
- [DMVs for Performance Tuning (Video - SQL Saturday Pordenone)](http://www.sqlsaturday.com/589/Sessions/Details.aspx?sid=57409) (DMV per l'ottimizzazione delle prestazioni - Diapositive e demo da SQL Saturday Pordenone)
- [SQL Server Tuning in pillole (video da SQL Saturday Parma)](https://vimeo.com/200980883)
- [SQL Server Tuning in pillole (diapositive e demo da SQL Saturday Parma)](http://www.sqlsaturday.com/566/Sessions/Details.aspx?sid=53988)
- [Performance Tuning With SQL Server Dynamic Management Views](https://www.red-gate.com/library/performance-tuning-with-sql-server-dynamic-management-views) (Ottimizzazione delle prestazioni con le viste a gestione dinamica di SQL Server)
- [The Most Prominent Wait Types of your SQL Server 2016](https://channel9.msdn.com/Blogs/MVP-Data-Platform/The-Most-Prominent-Wait-Types-of-your-SQL-Server-2016) (I tipi di attesa più importanti di SQL Server 2016)
