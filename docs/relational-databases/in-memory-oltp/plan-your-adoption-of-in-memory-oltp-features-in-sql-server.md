---
title: "Pianificare l'adozione delle funzionalità OLTP in memoria in SQL Server | Microsoft Docs"
ms.custom: 
ms.date: 05/08/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 041b428f-781d-4628-9f34-4d697894e61e
caps.latest.revision: 4
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 0bcdf5c7eec91bccabc4b7b54f6121bec4d6c7f2
ms.openlocfilehash: bf29cd596c9b52ecf88fc715a580253de5477271
ms.contentlocale: it-it
ms.lasthandoff: 07/31/2017

---
# <a name="plan-your-adoption-of-in-memory-oltp-features-in-sql-server"></a>Pianificare l'adozione delle funzionalità OLTP in memoria in SQL Server
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]


In questo articolo vengono descritte i modi in cui l'adozione delle funzionalità In-Memory influisce su altri aspetti del sistema aziendale.



## <a name="a-adoption-of-in-memory-oltp-features"></a>A. Adozione delle funzionalità OLTP in memoria


Le sottosezioni seguenti illustrano i fattori da tenere in considerazione quando si intende adottare e implementare le funzionalità In-Memory. Molte altre informazioni esplicative sono disponibili in:

- [Usare OLTP in memoria per migliorare le prestazioni dell'applicazione in un database SQL di Azure](https://azure.microsoft.com/documentation/articles/sql-database-in-memory-oltp-migration/)



### <a name="a1-prerequisites"></a>A.1 Prerequisiti

Uno dei prerequisiti per l'uso di funzionalità In-Memory può implicare l'edizione o il livello di servizio del prodotto SQL. Per questo e altri prerequisiti, vedere:

- [Requisiti per l'utilizzo di tabelle con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/requirements-for-using-memory-optimized-tables.md)
    - [Edizioni e componenti di SQL Server 2016](../../sql-server/editions-and-components-of-sql-server-2016.md)
    - [Suggerimenti sul livello dei prezzi di database SQL](https://azure.microsoft.com/documentation/articles/sql-database-service-tier-advisor/)


### <a name="a2-forecast-the-amount-of-active-memory"></a>A.2 Prevedere la quantità di memoria attiva

Il sistema dispone di sufficiente memoria attiva per supportare una nuova tabella con ottimizzazione per la memoria?

#### <a name="microsoft-sql-server"></a>Microsoft SQL Server

Una tabella con ottimizzazione per la memoria che contiene 200 GB di dati richiede più di 200 GB di memoria attiva dedicata al suo supporto. Prima di implementare una tabella con ottimizzazione per la memoria che contiene una grande quantità di dati, si deve prevedere la quantità di memoria aggiuntiva attiva che è necessario aggiungere al computer server. Per linee guida sulla stima, vedere:

- [Stimare i requisiti di memoria delle tabelle con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md)

#### <a name="azure-sql-database"></a>Database SQL di Azure

Per un database ospitato nel servizio cloud del database SQL di Azure, il livello di servizio scelto influisce sulla quantità di memoria attiva che il database può usare. È consigliabile monitorare l'utilizzo della memoria del database tramite un avviso. Per informazioni dettagliate, vedere:

- Esaminare i limiti di archiviazione di OLTP in memoria per il [piano tariffario](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-service-tiers#single-database-service-tiers-and-performance-levels)
- [Monitorare l'archiviazione di OLTP in memoria](https://azure.microsoft.com/documentation/articles/sql-database-in-memory-oltp-monitoring/)

#### <a name="memory-optimized-table-variables"></a>Variabili di tabella con ottimizzazione per la memoria

È preferibile usare una variabile di tabella dichiarata con ottimizzazione per la memoria piuttosto che una #TempTable tradizionale che risiede nel database **tempdb** . Tali variabili di tabella possono garantire miglioramenti significativi delle prestazioni senza usare grandi quantità di memoria attiva.

### <a name="a3-table-must-be-offline-to-convert-to-memory-optimized"></a>A.3 La tabella deve essere offline per la conversione in tabella con ottimizzazione per la memoria

Parte della funzionalità di ALTER TABLE è disponibile per le tabelle con ottimizzazione per la memoria. Ma non è possibile eseguire un'istruzione ALTER TABLE per convertire una tabella basata su disco in una tabella con ottimizzazione per la memoria. È invece necessario usare una serie di passaggi più manuali. Di seguito vengono elencati vari modi in cui è possibile convertire la tabella basata su disco in tabella con ottimizzazione per la memoria.

#### <a name="manual-scripting"></a>Esecuzione manuale di script

Un modo per convertire la tabella basata su disco in una tabella con ottimizzazione per la memoria consiste nel codificare manualmente i passaggi necessari di Transact-SQL.


1. Sospendere l'attività dell'applicazione.

2. Eseguire un backup completo.

3. Rinominare la tabella basata su disco.

4. Eseguire un'istruzione CREATE TABLE per creare la nuova tabella con ottimizzazione per la memoria.

5. Aggiungere dati nella tabella con ottimizzazione per la memoria dalla tabella basata su disco con un clausola sub-SELECT.

6. Eliminare la tabella basata su disco.

7. Eseguire un altro backup completo.

8. Riprendere l'attività dell'applicazione.


#### <a name="memory-optimization-advisor"></a>Ottimizzazione guidata per la memoria

Lo strumento Ottimizzazione guidata per la memoria può generare uno script per supportare l'implementazione della conversione di una tabella basata su disco in una tabella con ottimizzazione per la memoria. Lo strumento è disponibile nell'installazione di SQL Server Data Tools (SSDT).

- [Ottimizzazione guidata per la memoria](../../relational-databases/in-memory-oltp/memory-optimization-advisor.md)
- [Scaricare SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx)


#### <a name="dacpac-file"></a>file DACPAC

È possibile aggiornare il database sul posto tramite un file con estensione DACPAC gestito da SSDT. In SSDT è possibile specificare le modifiche allo schema codificato nel file con estensione DACPAC.

Si usano file con estensione DACPAC nel contesto di un progetto di Visual Studio di tipo *Database*.

- [Applicazioni livello dati](../../relational-databases/data-tier-applications/data-tier-applications.md) e file con estensione DACPAC



### <a name="a4-guidance-for-whether-in-memory-oltp-features-are-right-for-your-application"></a>A.4 Linee guida per verificare se le funzionalità di OLTP in memoria sono adatte all'applicazione

Per le linee guida per verificare se le funzionalità di OLTP in memoria possono migliorare le prestazioni di un'applicazione specifica, vedere:

- [OLTP in memoria (ottimizzazione per la memoria)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)



## <a name="b-unsupported-features"></a>B. Funzionalità non supportate

Le funzionalità non supportate in alcuni scenari di OLTP in memoria sono descritte in:

- [Funzionalità di SQL Server non supportate per OLTP in memoria](../../relational-databases/in-memory-oltp/unsupported-sql-server-features-for-in-memory-oltp.md)


Le sottosezioni seguenti illustrano alcune delle più importanti funzionalità non supportate.


### <a name="b1-snapshot-of-a-database"></a>B.1 SNAPSHOT di un database

Dopo la prima creazione di un modulo o tabella con ottimizzazione per la memoria in un database specifico, non è più possibile eseguire [snapshot](../../relational-databases/databases/database-snapshots-sql-server.md) del database. Il motivo specifico è che:

- Il primo elemento con ottimizzazione per la memoria rende impossibile l'eliminazione dell'ultimo file dal filegroup con ottimizzazione per le memoria e
- nessun database che ha un file nel filegroup con ottimizzazione per la memoria può supportare uno snapshot.

In genere uno snapshot può essere utile per le iterazioni di test rapidi.


### <a name="b2-cross-database-queries"></a>B.2 Query tra database

Le tabelle con ottimizzazione per la memoria non supportano transazioni [tra database](../../relational-databases/in-memory-oltp/cross-database-queries.md) . Non è possibile accedere a un altro database dalla stessa transazione o dalla stessa query che accede anche a una tabella con ottimizzazione per la memoria.

Le variabili di tabella non sono transazionali. Di conseguenza, le [variabili di tabella con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/faster-temp-table-and-table-variable-by-using-memory-optimization.md) non possono essere usate nelle query tra database.


### <a name="b3-readpast-table-hint"></a>B.3 Hint di tabella READPAST

Nessuna query può applicare l' [hint di tabella](../../t-sql/queries/hints-transact-sql-table.md) READPAST alle tabelle con ottimizzazione per la memoria.

L'hint READPAST è utile in scenari con più sessioni che accedono e modificano lo stesso set di piccole dimensioni di righe, ad esempio nell'elaborazione di una coda.


### <a name="b4-rowversion-sequence"></a>B.4 RowVersion, Sequenza

- Nessuna colonna può essere contrassegnata per [RowVersion](../../t-sql/data-types/rowversion-transact-sql.md) in una tabella con ottimizzazione per la memoria.


- Un oggetto [SEQUENCE](../../t-sql/statements/create-sequence-transact-sql.md) non può essere usato con un vincolo in una tabella ottimizzata per la memoria. Ad esempio, non è possibile creare un vincolo DEFAULT con una clausola NEXT VALUE FOR. Gli oggetti SEQUENCE possono essere usati con le istruzioni INSERT e UPDATE.


## <a name="c-administrative-maintenance"></a>C. Manutenzione amministrativa


In questa sezione vengono descritte le differenze nell'amministrazione di un database in cui vengono usate tabelle con ottimizzazione per la memoria.


### <a name="c1-identity-seed-reset-increment--1"></a>C.1 Reimpostazione del valore di inizializzazione Identity, incremento > 1

Per reinizializzare una colonna IDENTITY, non è possibile usare[DBCC CHECKIDENT](../../t-sql/database-console-commands/dbcc-checkident-transact-sql.md)in una tabella con ottimizzazione per la memoria.

Il valore di incremento è limitato a 1 per una colonna IDENTITY in una tabella con ottimizzazione per la memoria.


### <a name="c2-dbcc-checkdb-cannot-validate-memory-optimized-tables"></a>C.2 DBCC CHECKDB non può validare tabelle con ottimizzazione per la memoria

Il comando [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) non produce alcun risultato quando si esegue in una tabella con ottimizzazione per la memoria. I passaggi seguenti rappresentano una soluzione alternativa:


1. [Eseguire un backup del log delle transazioni](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md).

2. Eseguire il backup dei file del filegroup con ottimizzazione per la memoria in un dispositivo NULL. Il processo di backup richiama una convalida mediante checksum.

    Se viene rilevato un errore, procedere con i passaggi successivi.

3. Copiare i dati dalle tabelle con ottimizzazione per la memoria in tabelle basate su disco, per l'archiviazione temporanea.

4. Ripristinare i file del filegroup con ottimizzazione per la memoria.

5. Inserire nelle tabelle con ottimizzazione per la memoria i dati temporaneamente archiviati nelle tabelle basate su disco.

6. Eliminare le tabelle basate su disco che includevano temporaneamente i dati.



## <a name="d-performance"></a>D. restazioni

In questa sezione vengono descritte situazioni in cui le prestazioni delle tabelle con ottimizzazione per la memoria non raggiungono la loro completa potenzialità.


### <a name="d1-index-considerations"></a>D.1 Considerazioni sugli indici

Tutti gli indici in una tabella con ottimizzazione per la memoria vengono creati e gestiti dalle istruzioni CREATE TABLE e ALTER TABLE relative alla tabella. Non è possibile usare come destinazione una tabella con ottimizzazione per la memoria tramite un'istruzione CREATE INDEX.

L'indice non cluster ad albero B tradizionale è spesso una scelta ragionevole e semplice quando si implementa una tabella con ottimizzazione per la memoria. In un secondo momento, dopo aver verificato le prestazioni dell'applicazione, è possibile sostituirlo con un altro tipo di indice.

Nel contesto di una tabella con ottimizzazione per la memoria è necessario considerare due tipi speciali di indici: gli indici hash e gli indici columnstore.

Per una panoramica degli indici in tabelle con ottimizzazione per la memoria, vedere:

- [Indici per tabelle con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md)


#### <a name="hash-indexes"></a>Indici hash

Gli indici hash possono rappresentare il formato più veloce per l'accesso a una riga specifica con il valore della chiave primaria preciso tramite l'operatore '**=**'.

- Gli operatori non precisi, ad esempio '**! =**','**>**', o '**BETWEEN**' potrebbero influenzare le prestazioni se usati con un indice hash.

- Un indice hash potrebbe non essere la scelta migliore se la velocità di duplicazione del valore chiave diventa troppo elevata.

- Per evitare lunghe catene all'interno di singoli bucket, non sottostimare la quantità di *bucket* necessari all'indice hash, . Per informazioni dettagliate, vedere:
    - [Hash Indexes for Memory-Optimized Tables (Indici hash per tabelle con ottimizzazione per la memoria)](../../relational-databases/in-memory-oltp/hash-indexes-for-memory-optimized-tables.md)


#### <a name="nonclustered-columnstore-indexes"></a>Indici columnstore non cluster

Le tabelle con ottimizzazione per la memoria offrono un'elevata velocità effettiva con dati transazionali aziendali tipici denominata *elaborazione delle transazioni online* o *OLTP (Online Transaction Processing)*. Gli indici columnstore offrono elevata velocità effettiva con aggregazioni e processi denominata *Analisi*. In passato, l'approccio migliore disponibile per soddisfare le esigenze di analisi e OLTP era quello di separare le tabelle con elevato movimento di dati e con un certo livello di duplicazione dei dati. Oggi è disponibile una **soluzione ibrida** più semplice, ovvero la creazione di un indice columnstore in una tabella con ottimizzazione per la memoria.


- Un [indice columnstore](../../relational-databases/indexes/columnstore-indexes-overview.md) può essere compilato in una tabella basata su disco, anche come indice cluster. Ma in una tabella con ottimizzazione per la memoria, un indice columnstore non può essere raggruppato in cluster.


- Le colonne LOB (Large Object, Oggetti di grandi dimensioni) o colonne all'esterno di righe in una tabella con ottimizzazione per la memoria impediscono la creazione di un indice columnstore nella tabella.


- Nessuna istruzione ALTER TABLE può essere eseguita in una tabella con ottimizzazione per la memoria se è presente un indice columnstore nella tabella.
    - A partire da agosto 2016, Microsoft ha intrapreso un progetto a breve termine per migliorare le prestazioni nel ricreare l'indice columnstore.



### <a name="d2-lob-and-off-row-columns"></a>D.2 Colonne LOB e colonne all'esterno di righe

Le colonne LOB sono di tipi specifici, ad esempio varchar (**max**). Un paio di colonne LOB in una tabella con ottimizzazione per la memoria probabilmente non influenza le prestazioni in maniera significativa. Evitare comunque la presenza di colonne LOB non necessarie. Lo stesso consiglio si applica alle colonne all'esterno di righe. Non definire una colonna come nvarchar(3072) se varchar(512) è sufficiente.


Altre informazioni sulle colonne all'esterno di righe e colonne LOB sono disponibili in:

- [Dimensioni di tabelle e righe per le tabelle con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/table-and-row-size-in-memory-optimized-tables.md)
- [Tipi di dati supportati per OLTP In memoria](../../relational-databases/in-memory-oltp/supported-data-types-for-in-memory-oltp.md)



## <a name="e-limitations-of-native-procs"></a>E. Limiti delle procedure native


Alcuni elementi specifici di Transact-SQL non sono supportati in stored procedure compilate in modo nativo.

Per considerazioni da tener presente quando si migra uno script Transact-SQL in una procedura nativa, vedere:

- [Problemi di migrazione relativi alle stored procedure compilate in modo nativo](../../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)


### <a name="e1-no-case-in-a-native-proc"></a>E.1 Espressioni CASE in una procedura nativa

L'espressione CASE in Transact-SQL non può essere usata all'interno di una procedura nativa. È possibile implementare una soluzione alternativa:

- [Implementazione di un'espressione CASE in una stored procedure compilata in modo nativo](../../relational-databases/in-memory-oltp/implementing-a-case-expression-in-a-natively-compiled-stored-procedure.md)


### <a name="e2-no-merge-in-a-native-proc"></a>E.2 Istruzione MERGE in una procedura nativa


L' [istruzione MERGE](../../t-sql/statements/merge-transact-sql.md) di Transact-SQL presenta analogie con ciò che viene spesso definito funzionalità *Upsert* . Una procedura nativa non può usare l'istruzione MERGE. Tuttavia, è possibile ottenere la stessa funzionalità di MERGE usando una combinazione di istruzioni SELECT, UPDATE e INSERT. Un codice di esempio si trova in:

- [Implementazione di una funzionalità MERGE in una stored procedure compilata in modo nativo](../../relational-databases/in-memory-oltp/implementing-merge-functionality-in-a-natively-compiled-stored-procedure.md)



### <a name="e3-no-joins-in-update-or-delete-statements-in-a-native-proc"></a>E.3 Creazione di join in istruzioni UPDATE o DELETE in una procedura nativa

Le istruzioni Transact-SQL in una procedura nativa possono accedere solo a tabelle con ottimizzazione per la memoria. Nelle istruzioni UPDATE e DELETE, è possibile creare un join di tutte le tabelle. I tentativi eseguiti in una procedura nativa danno esisti negativi e visualizzano un messaggio di errore, ad esempio Msg 12319, che indica quanto segue:

- Impossibile usare una clausola FROM in un'istruzione UPDATE.
- Impossibile specificare un'origine tabella in un'istruzione DELETE.

Nessun tipo di sottoquery offre una soluzione alternativa. Tuttavia, è possibile usare una variabile di tabella con ottimizzazione per la memoria per ottenere la creazione di un join su più istruzioni. Di seguito è possibile vedere due esempi di codice:

- Come si può osservare, non è possibile eseguire istruzioni DELETE, JOIN, ecc. in una procedura nativa.
- Set di soluzioni alternative con le istruzioni Transact-SQL per eliminare un join.


*Scenario:* la tabella TabProjectEmployee ha una chiave univoca di due colonne: ProjectId ed EmployeeId. Ogni riga indica l'assegnazione di un dipendente a un progetto attivo. Quando un dipendente lascia l'azienda, è necessario eliminarlo dalla tabella TabProjectEmployee.


#### <a name="invalid-t-sql-deletejoin"></a>DELETE...JOIN di Transact-SQL non valido


Una procedura nativa non può avere un'istruzione DELETE...JOIN come illustrato di seguito.


```tsql
DELETE pe
    FROM
             TabProjectEmployee   AS pe
        JOIN TabEmployee          AS e

            ON pe.EmployeeId = e.EmployeeId
    WHERE
            e.EmployeeStatus = 'Left-the-Company'
;
```


#### <a name="valid-work-around-manual-deletejoin"></a>Una soluzione alternativa valida consiste nell'eliminare manualmente il join.

Di seguito viene illustrato l'esempio di codice alternativo, in due parti:

1. L'istruzione CREATE TYPE viene eseguita una sola volta, alcuni giorni prima che il tipo venga usato per la prima volta da qualsiasi variabile di tabella esistente.

2. Il processo aziendale usa il tipo creato. Inizia con la dichiarazione di una variabile di tabella del tipo di tabella creato.


```tsql

CREATE TYPE dbo.type_TableVar_EmployeeId
    AS TABLE  
    (
        EmployeeId   bigint   NOT NULL
    );
```


Successivamente, usa il tipo di tabella creato.


```tsql
DECLARE @MyTableVarMo  dbo.type_TableVar_EmployeeId  

INSERT INTO @MyTableVarMo (EmployeeId)
    SELECT
            e.EmployeeId
        FROM
                 TabProjectEmployee  AS pe
            JOIN TabEmployee         AS e  ON e.EmployeeId = pe.EmployeeId
        WHERE
            e.EmployeeStatus = 'Left-the-Company'
;

DECLARE @EmployeeId   bigint;

WHILE (1=1)
BEGIN
    SET @EmployeeId = NULL;

    SELECT TOP 1 @EmployeeId = v.EmployeeId
        FROM @MyTableVarMo  AS v;

    IF (NULL = @Employeed) BREAK;
    
    DELETE TabProjectEmployee
        WHERE EmployeeId = @EmployeeId;

    DELETE @MyTableVarMo
        WHERE EmployeeId = @EmployeeId;
END;
```


### <a name="e4-query-plan-limitations-for-native-procs"></a>E.4 Limiti del piano di query per procedure native


Alcuni tipi di piani di query non sono disponibili per le procedure native. Molti dettagli su questo argomento vengono illustrati in:

- [Guida all'elaborazione delle query per le tabelle con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/a-guide-to-query-processing-for-memory-optimized-tables.md)


#### <a name="no-parallel-processing-in-a-native-proc"></a>Elaborazione parallela in una procedura nativa

L'elaborazione parallela non può far parte di nessun piano di query per una procedura nativa. Le procedure native sono sempre a thread singolo.


#### <a name="join-types"></a>Tipi di join


Hash join e merge join non possono far parte di nessun piano di query per una procedura nativa. Vengono usati join annidati dei cicli.


#### <a name="no-hash-aggregation"></a>Aggregazione di hash

Quando il piano di query per una procedura nativa richiede una fase di aggregazione, è disponibile solo l'aggregazione di flusso. L'aggregazione di hash non è supportata in un piano di query per un procedura nativa.

- L'aggregazione di hash è più efficace quando è necessario aggregare dati da un numero elevato di righe.



## <a name="f-application-design-transactions-and-retry-logic"></a>F. Progettazione di applicazioni: transazioni e logica ripetizione tentativi

Una transazione che coinvolge una tabella con ottimizzazione per la memoria può diventare dipendente di un'altra transazione che coinvolge la stessa tabella. Se il numero di transazioni dipendenti raggiunge o supera il valore massimo consentito, tutte le transazioni dipendenti avranno esito negativo.

In SQL Server 2016:

- Il valore massimo consentito è di 8 transazioni dipendenti. 8 è anche il limite di transazioni di cui una determinata transazione può essere dipendente.
- Il numero del messaggio di errore è 41839. (In SQL Server 2014 il numero del messaggio di errore è 41301).


È possibile rendere gli script Transact-SQL più affidabili per evitare possibili errori di transazione aggiungendo la *logica ripetizione tentativi* agli script. La logica ripetizione tentativi è più utile quando le chiamate UPDATE e DELETE sono frequenti oppure se viene fatto riferimento alla tabella con ottimizzazione per la memoria da una chiave esterna in un'altra tabella. Per informazioni dettagliate, vedere:

- [Transactions with Memory-Optimized Tables](../../relational-databases/in-memory-oltp/transactions-with-memory-optimized-tables.md)
- [Limiti di dipendenza delle transazioni nelle tabelle con ottimizzazione per la memoria: errore 41839](https://blogs.msdn.microsoft.com/sqlcat/2016/07/11/transaction-dependency-limits-with-memory-optimized-tables-error-41839/)



## <a name="related-links"></a>Collegamenti correlati

- [OLTP in memoria (ottimizzazione per la memoria)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)



