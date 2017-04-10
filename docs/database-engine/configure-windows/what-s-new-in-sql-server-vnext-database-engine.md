---
title: "Novit&#224; di SQL Server vNext (motore di database) | Microsoft Docs"
ms.custom: ""
ms.date: "03/13/2017"
ms.prod: "sql-vnext"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 42f45b23-6509-45e8-8ee7-76a78f99a920
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 13
---
# Novit&#224; di SQL Server vNext (motore di database)
[!INCLUDE[tsql-appliesto-ssvNxt-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]

**Nota:** SQL Server vNext include anche le funzionalità introdotte nei Service Pack di SQL Server 2016. Per tali elementi, vedere [Novità del motore di database](../../database-engine/configure-windows/what-s-new-in-sql-server-2016-database-engine.md).

## <a name="sql-server-database-engine-ctp-13"></a>Motore di database di SQL Server (CTP 1.3)
- Sono state migliorate le prestazioni dei checkpoint indiretti.
- È stato aggiunto il supporto per i gruppi di disponibilità senza cluster.
- È stata aggiunta l'impostazione relativa ai gruppi di disponibilità che consente di definire il numero minimo di repliche necessarie per il commit.
- I gruppi di disponibilità sono ora supportati negli ambienti Windows e Linux per consentire le migrazioni e i test tra i diversi sistemi operativi.
- È stato aggiunto il supporto per i criteri di conservazione delle tabelle temporali.
- È stata introdotta la nuova vista a gestione dinamica SYS.DM_DB_STATS_HISTOGRAM.
- È stato aggiunto il supporto per la compilazione e la ricompilazione degli indici online columnstore non cluster.
- Sono state incluse cinque nuove viste a gestione dinamica per restituire informazioni sul processo Linux. Per altre informazioni, vedere [Viste a gestione dinamica del processo Linux](../../relational-databases/system-dynamic-management-views/linux-process-dynamic-management-views-transact-sql.md).   
- È stata aggiunta [sys.dm_db_stats_histogram (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md) per l'analisi delle statistiche.

## <a name="sql-server-database-engine-ctp-12"></a>Motore di database di SQL Server (CTP 1.2)

- L'ottimizzazione guidata di database (DTA) rilasciata con SQL Server Management Studio versione 16.4, per l'analisi di SQL Server 2016 e versioni successive, include alcune opzioni aggiuntive.    
   - Prestazioni migliorate. Per altre informazioni, vedere [Performance Improvements using Database Engine Tuning Advisor (DTA) recommendations](../../relational-databases/performance/performance-improvements-using-dta-recommendations.md) (Miglioramenti delle prestazioni mediante le indicazioni dell'ottimizzazione guidata di database).
   - Opzione `-fc` per abilitare le indicazioni relative agli indici columnstore. Per altre informazioni, vedere [Utilità dta](../../tools/dta/dta-utility.md) e [Columnstore index recommendations in Database Engine Tuning Advisor (DTA)](../../relational-databases/performance/columnstore-index-recommendations-in-database-engine-tuning-advisor-dta.md) (Indicazioni relative agli indici columnstore nell'ottimizzazione guidata di database).  
   - Opzione `-iq` per consentire all'ottimizzazione guidata di database di esaminare un carico di lavoro dell'archivio query. Per altre informazioni, vedere [Tuning Database Using Workload from Query Store](../../relational-databases/performance/tuning-database-using-workload-from-query-store.md) (Ottimizzazione del database tramite un carico di lavoro dell'archivio query).
   

## <a name="sql-server-database-engine-ctp-11"></a>Motore di database di SQL Server (CTP 1.1)

<a name="InMemoryBulletsCtp11"/>
- Per la funzionalità in memoria, di seguito sono elencati altri miglioramenti alle tabelle con ottimizzazione per la memoria e alle funzioni compilate in modo nativo e nelle [sezioni successive](#InMemory_CodeSamples) sono disponibili esempi di codice:
    - Supporto per le colonne calcolate in tabelle con ottimizzazione per la memoria, inclusi gli indici in colonne calcolate.
    - Supporto completo per le funzioni JSON in moduli compilati in modo nativo e in vincoli CHECK.
    - Operatore `CROSS APPLY` in moduli compilati in modo nativo.   
- Sono state aggiunte nuove funzioni per i valori stringa [CONCAT_WS](../../t-sql/functions/concat-ws-transact-sql.md), [TRANSLATE](../../t-sql/functions/translate-transact-sql.md) e [TRIM](../../t-sql/functions/trim-transact-sql.md).   
- La clausola `WITHIN GROUP` è ora supportata per la funzione [STRING_AGG](../../t-sql/functions/string-agg-transact-sql.md).
- Sono state aggiunte due nuove famiglie di regole di confronto per il giapponese (Japanese_Bushu_Kakusu_140 e Japanese_XJIS_140) ed è stata introdotta l'opzione per la distinzione tra selettori di variazione (_VSS) per l'uso nelle regole di confronto per il giapponese. Per altre informazioni dettagliate, vedere [Regole di confronto e supporto Unicode](../../relational-databases/collations/collation-and-unicode-support.md)   
- Nuove opzioni di accesso in blocco ([BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) e [OPENROWSET(BULK...)](../../t-sql/functions/openrowset-transact-sql.md)) consentono l'accesso ai dati direttamente da un file specificato con estensione csv e da file archiviati in Archiviazione BLOB di Azure tramite la nuova opzione `BLOB_STORAGE` di [EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md).


## <a name="sql-server-database-engine-ctp-10"></a>Motore di database di SQL Server (CTP 1.0)

- È stato aggiunto il database **COMPATIBILITY_LEVEL** 140.   I clienti che eseguono in questo livello otterranno le funzionalità più recenti del linguaggio e i comportamenti di Query Optimizer. Sono incluse le modifiche apportate a ogni versione non definitiva di Microsoft.
- Sono stati apportati miglioramenti alla modalità di calcolo delle soglie di aggiornamento delle statistiche incrementali. È richiesta la modalità di compatibilità&140;.
- È stato aggiunto [sys.dm_exec_query_statistics_xml](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-statistics-xml-transact-sql.md).
- Sono stati aggiunti molti miglioramenti delle prestazioni e del linguaggio alle tabelle in memoria:
    - `sp_spaceused` è ora supportato per le tabelle in memoria.
    - `sp_rename` è ora supportato per i moduli nativi.
    - Le istruzioni `CASE` sono ora supportate per i moduli nativi.
    - È stato rimosso il limite di 8 indici nelle tabelle in memoria.
    - `TOP (N) WITH TIES` è ora supportato nei moduli nativi.
    - `ALTER TABLE` per le tabelle in memoria è decisamente più veloce in alcuni casi.
    - Il rollforward delle transazioni delle tabelle in memoria viene ora eseguito in parallelo. In questo modo, viene ridotto il tempo per eseguire i failover o in alcuni casi viene riavviato.
    - I file del checkpoint in memoria possono ora essere archiviati in Archiviazione di Azure. Fornisce funzionalità equivalenti a MDF rispetto ai file LDF, che dispongono già di questa funzionalità.
- Gli indici Clustered Columnstore supportano ora le colonne LOB (nvarchar(max), varchar(max), varbinary(max)).
- È stata aggiunta la funzione di aggregazione [STRING_AGG](../../t-sql/functions/string-agg-transact-sql.md).  
- Nuove autorizzazioni: `DATABASE SCOPED CREDENTIAL` è ora una classe di autorizzazioni `CONTROL`, `ALTER`, `REFERENCES`, `TAKE OWNERSHIP` e `VIEW DEFINITION` a protezione diretta di supporto. `ADMINISTER DATABASE BULK OPERATIONS`, limitato al database SQL, è ora visibile in `sys.fn_builtin_permissions`.   
- Sono state aggiunte le viste a gestione dinamica [sys.dm_os_host_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md) per fornire informazioni sul sistema operativo per Windows e Linux.   
- I ruoli del database vengono creati con R Services per la gestione delle autorizzazioni associate ai pacchetti. Per altre informazioni, vedere [R Package management for SQL Server](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md) (Gestione dei pacchetti R per SQL Server).
 
<a name="InMemory_CodeSamples"/> 
## <a name="code-samples-for-new-in-memory-enhancements"></a>Esempi di codice per i nuovi miglioramenti in memoria

Le sottosezioni seguenti forniscono esempi di codice Transact-SQL che illustrano le nuove funzionalità in memoria elencate in una delle sezioni precedenti di questo articolo.

Fare clic [qui](#InMemoryBulletsCtp11) per visualizzare l'elenco puntato di CTP 1.1 relativo alle funzionalità in memoria.

#### <a name="computed-column-in-a-memory-optimized-table"></a>Colonna calcolata in una tabella con ottimizzazione della memoria

Questa istruzione CREATE TABLE illustra le funzionalità seguenti che sono state indicate nella sezione precedente relativa a CTP 1.1:

- Vincolo CHECK JSON su una colonna.
- Nuove colonne calcolate.
- Indice su una colonna calcolata.

```tsql
CREATE TABLE Product(
    ProductID  int            PRIMARY KEY NONCLUSTERED,
    Name       nvarchar(400)  NOT NULL,
    Price      float,

    Data      nvarchar(4000)  CONSTRAINT [Data contains JSON]  CHECK (ISJSON(Data)=1),

    MadeIn  AS CAST(JSON_VALUE(Data, '$.MadeIn')            as NVARCHAR(50)) PERSISTED,
    Cost    AS CAST(JSON_VALUE(Data, '$.ManufacturingCost') as float       ),

    INDEX [idx_Product_MadeIn] NONCLUSTERED (MadeIn)
)
        WITH (MEMORY_OPTIMIZED=ON);
```

#### <a name="cross-apply-and-json-functions"></a>CROSS APPLY e funzioni JSON

Questa istruzione CREATE PROCEDURE, per una stored procedure compilata in modo nativo, illustra le funzionalità seguenti che sono state indicate nella sezione precedente relativa a CTP 1.1:

- Operatore CROSS APPLY.
- Funzioni JSON.

```tsql
CREATE OR ALTER PROCEDURE ProductList()
    WITH SCHEMABINDING, NATIVE_COMPILATION
as begin
    atomic with (transaction isolation level = snapshot,  language = N'English')

    SELECT
            ProductID, Name, Price, Tags,
            Data,
            JSON_VALUE(Data,'$.MadeIn') AS MadeIn,
            value
        FROM Product
        CROSS APPLY OPENJSON(Data, '$.SalesReasons')
        FOR JSON PATH
end;
```
