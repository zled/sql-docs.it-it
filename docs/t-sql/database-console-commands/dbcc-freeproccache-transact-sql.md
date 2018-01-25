---
title: DBCC FREEPROCCACHE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 10/13/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FREEPROCCACHE_TSQL
- FREEPROCCACHE
- DBCC_FREEPROCCACHE_TSQL
- DBCC FREEPROCCACHE
dev_langs: TSQL
helpviewer_keywords:
- freeing procedure cache
- removing procedure cache elements
- deleting procedure cache elements
- DBCC FREEPROCCACHE statement
- procedure cache [SQL Server]
- clearing procedure cache
ms.assetid: 0e09d210-6f23-4129-aedb-3d56b2980683
caps.latest.revision: "61"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Active
ms.openlocfilehash: b5fd65fa2a764d87d2c5481a7c20560551ca3311
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="dbcc-freeproccache-transact-sql"></a>DBCC FREEPROCCACHE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

Rimuove tutti gli elementi dalla cache dei piani, rimuove un piano specifico dalla cache dei piani specificando un handle di piani o un handle SQL oppure rimuove tutte le voci della cache associate a un pool di risorse specificato.

>[!NOTE]
>DBCC FREEPROCCACHE non comporta la cancellazione delle statistiche di esecuzione delle stored procedure compilate in modo nativo. La cache delle procedure non contiene informazioni sulle stored procedure compilate in modo nativo. Tutte le statistiche di esecuzione raccolte dalle esecuzioni delle procedure verranno visualizzati nelle viste a gestione dinamica delle statistiche di esecuzione: [Sys.dm exec_procedure_stats &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md) e [Sys.dm exec_query_plan &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md).  
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
Sintassi per SQL Server:

```sql
DBCC FREEPROCCACHE [ ( { plan_handle | sql_handle | pool_name } ) ] [ WITH NO_INFOMSGS ]  
```  

Sintassi per Azure SQL Data Warehouse e Parallel Data Warehouse:
  
```sql
DBCC FREEPROCCACHE [ ( COMPUTE | ALL ) ] 
     [ WITH NO_INFOMSGS ]   
[;]  
```  
  
## <a name="arguments"></a>Argomenti  
 ({ *plan_handle* | *sql_handle* | *pool_name* })  
*plan_handle* identifica in modo univoco un piano di query per un batch che ha eseguito il cui piano risiede nella cache dei piani. *plan_handle* è **varbinary(64)** e può essere ottenuto dagli oggetti a gestione dinamica seguenti:  
 -   [sys.dm_exec_cached_plans](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
 -   [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
 -   [sys.dm_exec_query_memory_grants](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql.md)  
 -   [sys.dm_exec_query_stats](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  

*valore di sql_handle* è l'handle SQL del batch da cancellare. *valore di sql_handle* è **varbinary(64)** e può essere ottenuto dagli oggetti a gestione dinamica seguenti:  
 -   [sys.dm_exec_query_stats](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
 -   [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
 -   [sys.dm_exec_cursors](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cursors-transact-sql.md)  
 -   [sys.dm_exec_xml_handles](../../relational-databases/system-dynamic-management-views/sys-dm-exec-xml-handles-transact-sql.md)  
 -   [sys.dm_exec_query_memory_grants](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql.md)  

*pool_name* è il nome di un pool di risorse di Resource Governor. *pool_name* è **sysname** e può essere ottenuto eseguendo una query di [Sys.dm resource_governor_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md) vista a gestione dinamica.  
 Per associare un pool di risorse di un gruppo di carico di lavoro di Resource Governor, eseguire una query di [Sys.dm resource_governor_workload_groups](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql.md) vista a gestione dinamica. Per informazioni sul gruppo di carico di lavoro per una sessione, eseguire una query di [Sys.dm exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md) vista a gestione dinamica.  

  
 WITH NO_INFOMSGS  
 Disattiva tutti i messaggi informativi.  
  
 COMPUTE  
 Cancellare la cache dei piani di query da ogni nodo di calcolo. Si tratta del valore predefinito.  
  
 ALL  
 Cancellare la cache dei piani di query da ogni nodo di calcolo e dal nodo di controllo.  

> [!NOTE]
> A partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], `ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE` per cancellare la cache delle procedure (piano) per il database nell'ambito.

## <a name="remarks"></a>Osservazioni  
Usare DBCC FREEPROCCACHE per cancellare con cautela la cache dei piani. Cancellare la cache fa sì che tutti i piani da rimuovere ed esecuzioni verranno compilato un nuovo piano di query in ingresso (piano) di procedura anziché riutilizzare qualsiasi piano precedentemente memorizzata nella cache. 

Questo può causare una riduzione improvvisa e temporanea delle prestazioni delle query come il numero di nuove compilazioni aumenta. Il log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contiene il messaggio informativo seguente per ogni archivio cache cancellato nella cache dei piani: "[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ha rilevato %d occorrenza/e di scaricamento dell'archivio cache '%s' (parte della cache dei piani) a causa di operazioni 'DBCC FREEPROCCACHE' o 'DBCC FREESYSTEMCACHE'". Questo messaggio viene registrato ogni cinque minuti per tutta la durata dello scaricamento della cache.

La cache delle procedure viene cancellata anche con le seguenti operazioni di riconfigurazione:
-   access check cache bucket count  
-   access check cache quota  
-   clr enabled  
-   cost threshold for parallelism  
-   cross db ownership chaining  
-   index create memory  
-   max degree of parallelism  
-   max server memory  
-   max text repl size  
-   max worker threads  
-   min memory per query  
-   min server memory  
-   query governor cost limit  
-   query wait  
-   remote query timeout  
-   user options  
  
## <a name="result-sets"></a>Set di risultati  
Quando non è specificata la clausola WITH NO_INFOMSGS, DBCC FREEPROCCACHE restituisce: "esecuzione DBCC completata. Se sono stati visualizzati messaggi di errore DBCC, rivolgersi all'amministratore di sistema".
  
## <a name="permissions"></a>Autorizzazioni  
Si applica a: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)] 
- È necessario disporre dell'autorizzazione ALTER SERVER STATE per il server.  

Si applica a:[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]
- Richiede l'appartenenza al ruolo predefinito del server del database DB_OWNER.  

## <a name="general-remarks-for-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Osservazioni generali per [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
Possono eseguire contemporaneamente più comandi DBCC FREEPROCCACHE.
In [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], cancellare la cache dei piani può causare un peggioramento temporaneo delle prestazioni delle query come un nuovo piano di compilazione di query in ingresso, anziché riutilizzare qualsiasi memorizzata nella cache di piano. 

DBCC FREEPROCCACHE (calcolo) fa sì che solo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di ricompilazione delle query quando vengono eseguiti sui nodi di calcolo. Ciò non causa [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] per ricompilare il piano di query parallelo che viene generato sul nodo del controllo.
DBCC FREEPROCCACHE può essere annullato durante l'esecuzione.
  
## <a name="limitations-and-restrictions-for-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Limitazioni e restrizioni per [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
Impossibile eseguire DBCC FREEPROCCACHE all'interno di una transazione.
DBCC FREEPROCCAHCE non è supportato in un'istruzione di descrizione.
  
## <a name="metadata-for-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>I metadati per [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
Una nuova riga viene aggiunto alla vista di sistema sys.pdw_exec_requests durante l'esecuzione di DBCC FREEPROCCACHE.

## <a name="examples-includessnoversionincludesssnoversion-mdmd"></a>Esempi:[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
### <a name="a-clearing-a-query-plan-from-the-plan-cache"></a>A. Cancellazione di un piano di query dalla cache dei piani  
Nell'esempio seguente viene indicato come cancellare un piano di query dalla cache dei piani specificando l'handle del piano di query. Per verificare che la query di esempio si trovi nella cache dei piani, la query viene prima eseguita. Il `sys.dm_exec_cached_plans` e `sys.dm_exec_sql_text` vengono eseguite query sulle viste a gestione dinamica per restituire l'handle del piano per la query. 

Il valore dell'handle di piani dal set di risultati viene quindi inserito nell'istruzione `DBCC FREEPROCACHE` per rimuovere solo quel piano dalla cache dei piani.
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT * FROM Person.Address;  
GO  
SELECT plan_handle, st.text  
FROM sys.dm_exec_cached_plans   
CROSS APPLY sys.dm_exec_sql_text(plan_handle) AS st  
WHERE text LIKE N'SELECT * FROM Person.Address%';  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]

```
plan_handle                                         text  
--------------------------------------------------  -----------------------------  
0x060006001ECA270EC0215D05000000000000000000000000  SELECT * FROM Person.Address;  
  
(1 row(s) affected)
 ```
 
```sql  
-- Remove the specific plan from the cache.  
DBCC FREEPROCCACHE (0x060006001ECA270EC0215D05000000000000000000000000);  
GO  
```  
  
### <a name="b-clearing-all-plans-from-the-plan-cache"></a>B. Cancellazione di tutti i piani dalla cache dei piani  
Nell'esempio seguente vengono cancellati tutti gli elementi dalla cache dei piani. WITH `NO_INFOMSGS` clausola è specificata per evitare che venga visualizzato il messaggio informativo.
  
```sql  
DBCC FREEPROCCACHE WITH NO_INFOMSGS;  
```  
  
### <a name="c-clearing-all-cache-entries-associated-with-a-resource-pool"></a>C. Cancellazione di tutte le voci di cache associate a un pool di risorse  
Nell'esempio seguente vengono cancellate tutte le voci di cache associate a un pool di risorse specificato. Il `sys.dm_resource_governor_resource_pools` prima una query sulla vista per ottenere il valore per *pool_name*.
  
```sql  
SELECT * FROM sys.dm_resource_governor_resource_pools;  
GO  
DBCC FREEPROCCACHE ('default');  
GO  
```  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-dbcc-freeproccache-basic-syntax-examples"></a>D. Esempi di sintassi di base DBCC FREEPROCCACHE  
Nell'esempio seguente rimuove i nodi di calcolo di tutte le cache esistente del piano di query. Sebbene il contesto è impostato su UserDbSales, calcolo nodo query piano cache per tutti i database verranno verrà rimosso. La clausola WITH NO_INFOMSGS impedisce che i messaggi informativi visualizzati nei risultati.  
  
```sql
USE UserDbSales;  
DBCC FREEPROCCACHE (COMPUTE) WITH NO_INFOMSGS;
```  
  
 Nell'esempio seguente ha gli stessi risultati dell'esempio precedente, ad eccezione del fatto che i messaggi informativi verranno visualizzati nei risultati.  
  
```sql
USE UserDbSales;  
DBCC FREEPROCCACHE (COMPUTE);  
```  
  
Quando vengono richiesti i messaggi informativi e l'esecuzione ha esito positivo, i risultati della query avrà una riga per ogni nodo di calcolo.
  
### <a name="e-granting-permission-to-run-dbcc-freeproccache"></a>E. Concessione dell'autorizzazione per l'esecuzione di DBCC FREEPROCCACHE  
Nell'esempio seguente fornisce l'account di accesso autorizzazione David per l'esecuzione di DBCC FREEPROCCACHE.  
  
```sql
GRANT ALTER SERVER STATE TO David; 
GO
```  
  
## <a name="see-also"></a>Vedere anche  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[Resource Governor](../../relational-databases/resource-governor/resource-governor.md)  
[ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)
  
  
