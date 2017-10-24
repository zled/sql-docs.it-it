---
title: DBCC SHOW_STATISTICS (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SHOW_STATISTICS_TSQL
- DBCC SHOW_STATISTICS
- SHOW_STATISTICS
- DBCC_SHOW_STATISTICS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- query optimization statistics [SQL Server], densities
- histograms [SQL Server]
- statistical information [SQL Server], viewing statistics objects
- current distribution statistics
- query optimization statistics [SQL Server], histograms
- DBCC SHOW_STATISTICS statement
- distribution statistics
- statistical information [SQL Server], densities
- statistics objects
- statistical information [SQL Server], histograms
- query optimization statistics [SQL Server], viewing statistics objects
- statistical information [SQL Server], distribution
- densities [SQL Server]
- displaying distribution statistics
ms.assetid: 12be2923-7289-4150-b497-f17e76a50b2e
caps.latest.revision: 75
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: 38abfb552f1bb969c132d5086ca007d36541a76c
ms.contentlocale: it-it
ms.lasthandoff: 10/17/2017

---
# <a name="dbcc-showstatistics-transact-sql"></a>DBCC SHOW_STATISTICS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

DBCC SHOW_STATISTICS consente di visualizzare le statistiche relative all'ottimizzazione delle query correnti per una tabella o una vista indicizzata. L'utilizzo delle statistiche consente a Query Optimizer di stimare la cardinalità o il numero di righe nel risultato di una query e di creare un piano di query di qualità elevata. Query Optimizer potrebbe ad esempio utilizzare le stime relative alla cardinalità per scegliere l'operatore Index Seek anziché l'operatore Index Scan nel piano di query, evitando un'operazione di analisi dell'indice che utilizza un numero elevato di risorse e migliorando di conseguenza le prestazioni delle query.
  
Query Optimizer archivia le statistiche relative a una tabella oppure a una vista indicizzata in un oggetto statistiche. Per una tabella, l'oggetto statistiche viene creato in un indice oppure in un elenco di colonne della tabella. L'oggetto statistiche è costituito da un'intestazione con metadati relativi alle statistiche, un istogramma con la distribuzione dei valori nella prima colonna chiave dell'oggetto stesso e un vettore di densità per misurare la correlazione tra colonne. Nel [!INCLUDE[ssDE](../../includes/ssde-md.md)] è possibile calcolare le stime relative alla cardinalità con qualsiasi dato contenuto nell'oggetto statistiche.
  
DBCC SHOW_STATISTICS consente di visualizzare l'intestazione, l'istogramma e il vettore di densità in base ai dati archiviati nell'oggetto statistiche. La sintassi consente inoltre di specificare una tabella o una vista indicizzata con un nome di colonna, un nome di statistiche o un nome di indice di destinazione. In questo argomento vengono descritte le modalità di visualizzazione delle statistiche e di interpretazione dei risultati visualizzati.
  
Per altre informazioni, vedere [Statistics](../../relational-databases/statistics/statistics.md).
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```
-- Syntax for SQL Server and Azure SQL Database  
  
DBCC SHOW_STATISTICS ( table_or_indexed_view_name , target )   
[ WITH [ NO_INFOMSGS ] < option > [ , n ] ]  
< option > :: =  
    STAT_HEADER | DENSITY_VECTOR | HISTOGRAM | STATS_STREAM  
```  
  
```
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  

DBCC SHOW_STATISTICS ( table_name , target )   
    [ WITH {STAT_HEADER | DENSITY_VECTOR | HISTOGRAM } [ ,...n ] ]  
[;]  
```  
  
## <a name="arguments"></a>Argomenti  
 *table_or_indexed_view_name*  
 Nome della tabella o della vista indicizzata per la quale visualizzare le informazioni statistiche.  
  
 *table_name*  
 Nome della tabella che contiene le statistiche per la visualizzazione. La tabella non può essere una tabella esterna.  
  
 *destinazione*  
 Nome dell'indice, delle statistiche o della colonna per cui visualizzare le informazioni statistiche. *destinazione* è racchiuso tra parentesi quadre, singolo offerte, le virgolette doppie o senza virgolette. Se *destinazione* è un nome di un indice esistente o le statistiche in una tabella o vista indicizzata, le relative informazioni statistiche viene restituita. Se *destinazione* è il nome di una colonna esistente e statistiche create automaticamente in questa colonna non è disponibile, vengono restituite informazioni su tale statistiche create automaticamente. Se per una colonna specificata in target non sono presenti statistiche create automaticamente, viene restituito il messaggio di errore 2767.  
 In [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], *destinazione* non può essere un nome di colonna.  
  
 NO_INFOMSGS  
 Evita la visualizzazione di tutti i messaggi informativi con livello di gravità compreso tra 0 e 10.  
  
 STAT_HEADER | DENSITY_VECTOR | ISTOGRAMMA | STATS_STREAM [ **,**  *n*  ]  
 Specificando una o più opzioni tra quelle disponibili è possibile limitare i set di risultati restituiti dall'istruzione all'opzione o alle opzioni specificate. Se non si specifica alcuna opzione, vengono restituite tutte le informazioni statistiche.  
  
 STATS_STREAM è [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="result-sets"></a>Set di risultati  
Nella tabella seguente vengono descritte le colonne restituite nel set di risultati quando si specifica l'opzione STAT_HEADER.
  
|Nome colonna|Description|  
|-----------------|-----------------|  
|Nome|Nome dell'oggetto statistiche.|  
|Updated|Data e ora dell'ultimo aggiornamento delle statistiche. Il [STATS_DATE](../../t-sql/functions/stats-date-transact-sql.md) funzione è un modo alternativo per recuperare queste informazioni.|  
|Righe|Numero totale di righe della tabella o della vista indicizzata al momento dell'ultimo aggiornamento delle statistiche. Se le statistiche vengono filtrate o corrispondono a un indice filtrato, il numero di righe potrebbe essere inferiore al numero di righe della tabella. Per ulteriori informazioni, vedere[statistiche](../../relational-databases/statistics/statistics.md).|  
|Rows Sampled|Numero totale di righe campionate per i calcoli statistici. Se Rows Sampled < Rows, l'istogramma e i risultati relativi alla densità visualizzati vengono stimati in base alle righe campionate.|  
|Passaggi|Numero di intervalli nell'istogramma. Ogni intervallo comprende un insieme di valori di colonna seguiti da un valore di colonna pari al limite superiore. Gli intervalli dell'istogramma vengono definiti nella prima colonna chiave delle statistiche. Il numero massimo di intervalli è 200.|  
|Density|Valore calcolato come 1/ *valori distinct* per tutti i valori nella prima colonna chiave dell'oggetto statistiche, ad eccezione dei valori limite dell'istogramma. Tale valore Density non viene utilizzato da Query Optimizer e viene visualizzato per compatibilità con le versioni precedenti a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].|  
|Average Key Length|Numero medio di byte per valore per tutte le colonne chiave nell'oggetto statistiche.|  
|String Index|Il valore Yes indica che l'oggetto statistiche contiene statistiche di riepilogo delle stringhe per migliorare le stime relative alla cardinalità per i predicati della query che utilizzano l'operatore LIKE, ad esempio `WHERE ProductName LIKE '%Bike'`. Stringa di statistiche di riepilogo vengono archiviate separatamente dall'istogramma e vengono create nella prima colonna chiave dell'oggetto statistiche quando è di tipo **char**, **varchar**, **nchar**, **nvarchar**, **varchar (max)**, **nvarchar (max)**, **testo**, o **ntext.**.|  
|Espressione filtro|Predicato per il subset di righe della tabella incluso nell'oggetto statistiche. NULL = statistiche non filtrate. Per ulteriori informazioni sui predicati filtrati, vedere [Create Filtered Indexes](../../relational-databases/indexes/create-filtered-indexes.md). Per ulteriori informazioni sulle statistiche filtrate, vedere [statistiche](../../relational-databases/statistics/statistics.md).|  
|Unfiltered Rows|Numero totale di righe nella tabella prima dell'applicazione dell'espressione di filtro. Se l'espressione di filtro è NULL, Unfiltered Rows è uguale a Rows.|  
|Percentuale di esempio persistenti|Persistente la percentuale di campionamento utilizzata per gli aggiornamenti delle statistiche che non specificano in modo esplicito una percentuale di campionamento. Se il valore è zero, verrà impostata alcuna percentuale di esempio persistente per la statistica.<br /><br /> **Si applica a:** [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 CU4| 
  
Nella tabella seguente vengono descritte le colonne restituite nel set di risultati quando si specifica l'opzione DENSITY_VECTOR.
  
|Nome colonna|Description|  
|-----------------|-----------------|  
|All Density|Il valore Density viene calcolato come 1/ *valori distinct*. Nei risultati la densità viene visualizzata per ogni prefisso di colonna dell'oggetto statistiche, una riga per ogni densità. Un valore distinct è un elenco distinto dei valori delle colonne per riga e per prefisso di colonna. Se l'oggetto statistiche contiene, ad esempio, le colonne chiave (A, B, C), i risultati restituiscono la densità degli elenchi di valori distinct in ognuno di tali prefissi di colonna, ovvero (A), (A, B) e (A, B, C). Utilizzando il prefisso (A, B, C), ciascuno di questi elenchi è un elenco di valori distinct, ovvero (3, 5, 6), (4, 4, 6), (4, 5, 6), (4, 5, 7). Utilizzando il prefisso (A, B) agli stessi valori di colonna sono associati gli elenchi di valori distinct (3, 5), (4, 4) e (4, 5).|  
|Average Length|Lunghezza media, in byte, per archiviare un elenco di valori di colonna per il prefisso di colonna. Se per ogni valore presente nell'elenco (3, 5, 6), ad esempio, sono necessari 4 byte, la lunghezza media è di 12 byte.|  
|Colonne|Nomi delle colonne nel prefisso per cui sono visualizzati i valori di All Density e Average Length.|  
  
Nella tabella seguente vengono descritte le colonne restituite nel set di risultati quando si specifica l'opzione HISTOGRAM.
  
|Nome colonna|Description|  
|---|---|
|RANGE_HI_KEY|Valore di colonna pari al limite superiore per un intervallo dell'istogramma. Il valore di colonna viene denominato anche valore chiave.|  
|RANGE_ROWS|Numero stimato di righe il cui valore di colonna è compreso in un intervallo dell'istogramma, escluso il limite superiore.|  
|EQ_ROWS|Numero stimato di righe il cui valore di colonna è uguale al limite superiore dell'intervallo dell'istogramma.|  
|DISTINCT_RANGE_ROWS|Numero stimato di righe con un valore distinct di colonna compreso in un intervallo dell'istogramma, escluso il limite superiore.|  
|AVG_RANGE_ROWS|Numero medio di righe con valori di colonna duplicati compresi in un intervallo dell'istogramma, escluso il limite superiore (RANGE_ROWS / DISTINCT_RANGE_ROWS per DISTINCT_RANGE_ROWS > 0).| 
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="histogram"></a>Istogramma  
Un istogramma misura la frequenza di occorrenza per ogni valore distinct in un set di dati. Query Optimizer calcola un istogramma nei valori di colonna nella prima colonna chiave dell'oggetto statistiche, selezionando i valori di colonna tramite il campionamento statistico delle righe o un'analisi completa di tutte le righe della tabella o della vista. Se l'istogramma viene creato da un set campionato di righe, i totali archiviati per numero di righe e numero di valori distinct sono stime e non è necessario che siano numeri interi.
  
Per creare l'istogramma, Query Optimizer ordina i valori di colonna, calcola il numero di valori che corrispondono a ogni valore distinct di colonna, quindi aggrega i valori di colonna in un massimo di 200 intervalli contigui dell'istogramma. Ogni intervallo comprende un insieme di valori di colonna seguiti da un valore di colonna pari al limite superiore. Nell'insieme sono inclusi tutti i possibili valori di colonna compresi tra i valori limite, esclusi questi ultimi. Il minore tra i valori di colonna ordinati costituisce il limite superiore per il primo intervallo dell'istogramma.
  
Nel diagramma seguente viene illustrato un istogramma con sei intervalli. L'area a sinistra del primo valore limite superiore è il primo intervallo.
  
![](../../relational-databases/system-dynamic-management-views/media/a0ce6714-01f4-4943-a083-8cbd2d6f617a.gif "a0ce6714-01f4-4943-a083-8cbd2d6f617a")
  
Per ogni intervallo dell'istogramma:
-   La riga in grassetto rappresenta il valore limite superiore (RANGE_HI_KEY) e il relativo numero di occorrenze (EQ_ROWS).  
-   L'area a tinta unita a sinistra di RANGE_HI_KEY rappresenta l'insieme di valori di colonna e il numero medio di occorrenze di ciascun valore (AVG_RANGE_ROWS) di colonna. Il valore AVG_RANGE_ROWS per il primo intervallo dell'istogramma è sempre 0.  
-   Le linee punteggiate rappresentano i valori campionati utilizzati per stimare il numero complessivo dei valori distinct nell'insieme (DISTINCT_RANGE_ROWS) e il numero complessivo dei valori nell'insieme (RANGE_ROWS). Query Optimizer utilizza RANGE_ROWS e DISTINCT_RANGE_ROWS per calcolare AVG_RANGE_ROWS e non archivia i valori campionati.  
  
Query Optimizer definisce gli intervalli dell'istogramma in base al relativo significato statistico e utilizza un algoritmo per il calcolo della differenza massima per ridurre al minimo il numero di intervalli nell'istogramma, aumentando contemporaneamente la differenza tra i valori limite. Il numero massimo di intervalli è 200. Il numero di intervalli dell'istogramma può essere minore del numero di valori distinct, anche per le colonne con un numero di punti limite inferiore a 200. A una colonna con 100 valori distinct, ad esempio, può essere associato un istogramma con un numero di punti limite inferiore a 100.
  
## <a name="density-vector"></a>Vettore di densità  
Per ottimizzare le stime relative alla cardinalità per query che restituiscono più colonne della stessa tabella o vista indicizzata, Query Optimizer utilizza le densità. Il vettore di densità contiene una densità per ogni prefisso di colonna nell'oggetto statistiche. Se in un oggetto statistiche, ad esempio, sono presenti le colonne chiave CustomerId, ItemId e Price, la densità viene calcolata su ciascuno dei prefissi di colonna seguenti.
  
|Prefisso di colonna|Densità calcolata su|  
|---|---|
|(CustomerId)|Righe con valori corrispondenti per CustomerId|  
|(CustomerId, ItemId)|Righe con valori corrispondenti per CustomerId e ItemId|  
|(CustomerId, ItemId, Price)|Righe con valori corrispondenti per CustomerId, ItemId e Price|  
  
## <a name="restrictions"></a>Restrizioni  
 DBCC SHOW_STATISTICS non fornisce statistiche per gli indici spaziali o columnstore ottimizzati in memoria xVelocity.  
  
## <a name="permissions-for-includessnoversionincludesssnoversion-mdmd-and-includesssdsincludessssds-mdmd"></a>Le autorizzazioni per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e[!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
Per visualizzare l'oggetto statistiche, l'utente deve essere proprietaria della tabella o l'utente deve essere un membro del `sysadmin` ruolo predefinito del server, il `db_owner` ruolo predefinito del database, o `db_ddladmin` ruolo predefinito del database.
  
Tramite SQL Server 2012 SP1 vengono modificate le restrizioni alle autorizzazioni e gli utenti che dispongono dell'autorizzazione SELECT possono utilizzare questo comando. Affinché le autorizzazioni SELECT siano sufficienti per eseguire il comando, sono richiesti i requisiti seguenti:
-   Gli utenti devono disporre delle autorizzazioni su tutte le colonne nell'oggetto statistiche  
-   Gli utenti devono disporre dell'autorizzazione su tutte le colonne in una condizione di filtro, se esistente  
-   La tabella non può avere un criterio di sicurezza a livello di riga.  
  
Per disabilitare questo comportamento, utilizzare il traceflag 9485.
  
## <a name="permissions-for-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Le autorizzazioni per [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
DBCC SHOW_STATISTICS richiede l'autorizzazione SELECT sulla tabella o l'appartenenza a uno dei valori seguenti:
-   ruolo predefinito del server sysadmin  
-   ruolo predefinito del database db_owner  
-   ruolo predefinito del database db_ddladmin  
  
## <a name="limitations-and-restrictions-for-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Limitazioni e restrizioni per [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
DBCC SHOW_STATISTICS Mostra le statistiche archiviate nello scheletro di database a livello di nodo di controllo. Non vengono visualizzati le statistiche vengono create automaticamente da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sui nodi di calcolo.
  
DBCC SHOW_STATISTICS non è supportata nelle tabelle esterne.
  
## <a name="examples-includessnoversionincludesssnoversion-mdmd-and-includesssdsincludessssds-mdmd"></a>Esempi: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e[!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
### <a name="a-returning-all-statistics-information"></a>A. Restituzione di tutte le informazioni statistiche  
L'esempio seguente visualizza tutte le informazioni statistiche per il `AK_Address_rowguid` indice del `Person.Address` tabella il [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.
  
```t-sql
DBCC SHOW_STATISTICS ("Person.Address", AK_Address_rowguid);  
GO  
```  
  
### <a name="b-specifying-the-histogram-option"></a>B. Specifica dell'opzione HISTOGRAM  
Consente di limitare le informazioni statistiche visualizzate per Customer_LastName ai dati dell'istogramma.
  
```t-sql
DBCC SHOW_STATISTICS ("dbo.DimCustomer",Customer_LastName) WITH HISTOGRAM;  
GO  
```  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="c-display-the-contents-of-one-statistics-object"></a>C. Visualizzare il contenuto dell'oggetto uno statistiche  
 Nell'esempio seguente visualizza il contenuto delle statistiche Customer_LastName per la tabella DimCustomer.  
  
```t-sql
-- Uses AdventureWorks  
--First, create a statistics object  
CREATE STATISTICS Customer_LastName   
ON AdventureWorksPDW2012.dbo.DimCustomer (LastName);  
GO  
DBCC SHOW_STATISTICS ("dbo.DimCustomer",Customer_LastName);  
GO  
```  
  
I risultati mostrano l'intestazione, il vettore di densità e parte dell'istogramma.
  
![Risultati di DBCC SHOW_STATISTICS](../../t-sql/database-console-commands/media/aps-sql-dbccshow-statistics.JPG "risultati di DBCC SHOW_STATISTICS")
  
## <a name="see-also"></a>Vedere anche  
[Statistiche](../../relational-databases/statistics/statistics.md)  
[CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)  
[CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md)  
[DROP STATISTICS &#40; Transact-SQL &#41;](../../t-sql/statements/drop-statistics-transact-sql.md)  
[sp_autostats &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-autostats-transact-sql.md)  
[sp_createstats &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-createstats-transact-sql.md)  
[STATS_DATE &#40; Transact-SQL &#41;](../../t-sql/functions/stats-date-transact-sql.md)  
[UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)  
[Sys.dm db_stats_properties (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-properties-transact-sql.md)  
[Sys.dm_db_stats_histogram (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md)   

