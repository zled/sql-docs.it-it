---
title: Indici hash per tabelle con ottimizzazione per la memoria | Microsoft Docs
ms.custom:
- MSDN content
- MSDN - SQL DB
ms.date: 06/12/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.service: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e922cc3a-3d6e-453b-8d32-f4b176e98488
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: b1acbcd97dfabfa5d23fa82e55d4eb01101233aa
ms.contentlocale: it-it
ms.lasthandoff: 07/31/2017

---
# <a name="hash-indexes-for-memory-optimized-tables"></a>Hash Indexes for Memory-Optimized Tables (Indici hash per tabelle con ottimizzazione per la memoria)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  
Questo articolo descrive il tipo di indice *hash* disponibile per una tabella con ottimizzazione per la memoria. Questo articolo:  
  
- Fornisce brevi esempi di codice per illustrare la sintassi Transact-SQL.  
- Illustra le nozioni fondamentali sugli indici hash.  
- Descrive [come stimare un numero di bucket appropriato](#configuring_bucket_count).  
- Descrive come progettare e gestire gli indici hash.  
  
  
#### <a name="prerequisite"></a>Prerequisiti  
  
Informazioni sul contesto importanti per la comprensione di questo articolo sono disponibili nell'articolo:  
  
- [Indici per tabelle con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md)  
  
  
  
## <a name="a-syntax-for-memory-optimized-indexes"></a>A. Sintassi per gli indici con ottimizzazione per la memoria  
  
  
### <a name="a1-code-sample-for-syntax"></a>A.1 Esempio di codice per la sintassi  
  
Questa sottosezione contiene un blocco di codice Transact-SQL che mostra le sintassi disponibili per creare un indice hash in una tabella con ottimizzazione per la memoria.  
  
- Nell'esempio viene illustrato che l'indice hash viene dichiarato all'interno dell'istruzione CREATE TABLE.  
  - È invece possibile dichiarare l'indice hash in un'istruzione [ALTER TABLE...ADD INDEX](#h3-b2-declaration-limitations) separata.  
  
  
  
    DROP TABLE IF EXISTS SupportEventHash;  
    go  
      
    CREATE TABLE SupportIncidentRating_Hash  
    (  
      SupportIncidentRatingId   int      not null   identity(1,1)  
        PRIMARY KEY NONCLUSTERED,  
      
      RatingLevel          int           not null,  
      
      SupportEngineerName  nvarchar(16)  not null,  
      Description          nvarchar(64)      null,  
      
      INDEX ix_hash_SupportEngineerName  
        HASH (SupportEngineerName) WITH (BUCKET_COUNT = 100000)  
    )  
      WITH (  
        MEMORY_OPTIMIZED = ON,  
        DURABILITY = SCHEMA_ONLY);  
    go  
  

Per determinare il corretto `BUCKET_COUNT` per i propri dati, vedere [Configurazione del numero di bucket dell'indice hash](#configuring_bucket_count). 
  
## <a name="b-hash-indexes"></a>B. Indici hash  
  
  
### <a name="b1-performance-basics"></a>B.1 Nozioni fondamentali sulle prestazioni  
  
Le prestazioni di un indice hash sono:  
  
- Eccellenti quando la clausola WHERE specifica un valore *esatto* per ogni colonna della chiave di indice hash.  
- Scarse quando la clausola WHERE cerca un *intervallo* di valori nella chiave di indice.  
- Scarse quando la clausola WHERE specifica un determinato valore per la prima colonna di una chiave di indice hash a due colonne, ma non specifica un valore per la *seconda* colonna della chiave.  
  
  
<a name="h3-b2-declaration-limitations"></a>  
  
### <a name="b2-declaration-limitations"></a>B.2 Limitazioni di dichiarazione  
  
Un indice hash può essere presente solo in una tabella con ottimizzazione per la memoria. Non può esistere in una tabella basata su disco.  
  
Un indice hash può essere dichiarato:  
  
- UNIQUE, oppure per impostazione predefinita Nonunique.  
- NONCLUSTERED, che è l'impostazione predefinita.   
  
  
Di seguito è riportato un esempio della sintassi per creare un indice hash al di fuori dell'istruzione CREATE TABLE:  
  
  
    ALTER TABLE MyTable_memop  
      ADD INDEX ix_hash_Column2 UNIQUE  
        HASH (Column2) WITH (BUCKET_COUNT = 64);  
  
  
  
### <a name="b3-buckets-and-hash-function"></a>B.3 Bucket e funzione hash  
  
Un indice hash ancora i propri valori di chiave in una matrice di *bucket* :  
  
- Ogni bucket è costituito da 8 byte, che vengono usati per archiviare l'indirizzo di memoria di un elenco di collegamenti delle voci della chiave.  
- Ogni voce rappresenta un valore per una chiave di indice, oltre all'indirizzo della riga corrispondente nella tabella con ottimizzazione per la memoria sottostante.  
  - Ogni voce punta alla voce successiva in un elenco di collegamenti di voci, tutte concatenate per il bucket corrente.  
  
  
L'algoritmo di hash tenta di distribuire tutti i valori di chiave univoci o distinct in modo uniforme tra i bucket, ma è difficile raggiungere l'uniformità totale. Allo stesso bucket vengono concatenate tutte le istanze di un qualsiasi valore di chiave specificato. Il bucket può anche contenere una combinazione di tutte le istanze di un valore chiave diverso.  
  
- Una combinazione di questo tipo è detta *collisione hash*. Le collisioni sono comuni ma non ottimali.  
- Un obiettivo realistico è che il 30% dei bucket contengano due valori di chiave diversi.  
  
  
È necessario dichiarare quanti bucket dovrà avere l'indice hash.  
  
- Minore è il rapporto tra bucket e righe di tabella o valori distinct, maggiore sarà la lunghezza dell'elenco di collegamenti bucket medio.  
- Gli elenchi di collegamenti brevi risultano più veloci rispetto agli elenchi di collegamenti lunghi.  
  
  
In SQL Server è disponibile una funzione hash usata per tutti gli indici hash.  
  
- La funzione hash è deterministica: dato lo stesso valore di chiave di input, restituisce lo stesso slot di bucket.  
- Con chiamate ripetute, gli output della funzione hash tendono a formare una distribuzione di Poisson o a campana, non una distribuzione lineare piana.  
  
  
Nell'immagine seguente è riepilogata l'interazione tra l'indice hash e i bucket.  
  
  
![hekaton_tables_23d](../../relational-databases/in-memory-oltp/media/hekaton-tables-23d.png "chiavi di indice, input nella funzione hash, l'output è l'indirizzo di un bucket di hash, che punta all'inizio della catena.")  
  
  
  
### <a name="b4-row-versions-and-garbage-collection"></a>B.4 Versioni delle righe e Garbage Collection  
  
  
In una tabella con ottimizzazione per la memoria, quando una riga è interessata da un'istruzione SQL UPDATE, la tabella crea una versione aggiornata della riga. Durante la transazione di aggiornamento, altre sessioni potrebbero riuscire a leggere la versione precedente della riga e quindi evitare il rallentamento delle prestazioni associato a un blocco di riga.  
  
L'indice hash potrebbe anche avere versioni diverse delle relative voci per includere l'aggiornamento.  
  
In seguito, quando le versioni precedenti non sono più necessarie, un thread di Garbage Collection (GC) attraversa i bucket e i relativi elenchi di collegamenti per eliminare le voci obsolete. Il thread GC offre prestazioni migliori se le catene degli elenchi di collegamenti sono brevi.   
  
<a name="configuring_bucket_count"></a>
  
## <a name="c-configuring-the-hash-index-bucket-count"></a>C. Configurazione del numero di bucket dell'indice hash  
  
Il numero di bucket dell'indice hash viene specificato al momento della creazione dell'indice e può essere modificato utilizzando la sintassi ALTER TABLE...ALTER INDEX REBUILD.  
  
Nella maggior parte dei casi, il numero di bucket dovrebbe essere in teoria impostato su un valore compreso tra una e due volte il numero di valori distinct della chiave di indice.   
Non è sempre possibile stimare quanti valori ha o potrebbe avere una particolare chiave di indice. Le prestazioni sono di norma ancora soddisfacenti se il valore **BUCKET_COUNT** è al massimo 10 volte superiore al numero effettivo di valori chiave e un valore superiore è in genere migliore di un valore inferiore.  
  
Un numero di bucket troppo *ridotto* presenta i seguenti svantaggi:  
  
- Più collisioni hash di valori di chiave distinct.  
  - Ogni valore distinct è costretto a condividere lo stesso bucket con un valore distinct diverso.  
  - La lunghezza media di catena per bucket aumenta.  
  - Più è lunga la catena di bucket, più lente saranno le ricerche di uguaglianza nell'indice.  
  
Un numero di bucket troppo *elevato* presenta i seguenti svantaggi:  
  
- Un numero di bucket troppo elevato può comportare la presenza di più bucket vuoti.  
  - I bucket vuoti influiscono sulle prestazioni delle analisi complete degli indici. Se le analisi vengono eseguite regolarmente, è consigliabile scegliere un numero di bucket simile al numero dei valori di chiave di indice distinct.  
  - I bucket vuoti utilizzano memoria, anche se ogni bucket utilizza solo 8 byte.  
    
  
> [!NOTE]
> L'aggiunta di ulteriori bucket non determina in alcun modo la riduzione del concatenamento di voci che condividono un valore duplicato. La frequenza di duplicazione dei valori viene usata per stabilire se un hash è del tipo di indice appropriato, non per calcolare il numero di bucket.  
  
  
  
### <a name="c1-practical-numbers"></a>C.1 Numeri pratici  
  
Anche se il valore **BUCKET_COUNT** è moderatamente inferiore o superiore all'intervallo preferito, è probabile che le prestazioni dell'indice hash siano tollerabili o accettabili. Non si verificano problemi.  
  
Assegnare all'indice hash un valore **BUCKET_COUNT** quasi uguale al numero di righe che si prevede di raggiungere nella tabella con ottimizzazione per la memoria.  
  
Se ad esempio la tabella espandibile contiene 2.000.000 righe, ma si prevede che crescerà di 10 volte, fino a 20.000.000 righe, iniziare con un numero di bucket 10 volte superiore al numero di righe nella tabella. In questo modo si avrà spazio sufficiente per un numero maggiore di righe.  
  
- In teoria, è consigliabile aumentare il numero di bucket quando la quantità di righe raggiunge il numero di bucket iniziale.  
- Anche se il numero di righe diventasse 5 volte superiore rispetto al numero di bucket, le prestazioni sarebbero ancora soddisfacenti in molte situazioni.  
  
Si supponga che un indice hash includa 10.000.000 valori di chiave distinct.  
  
- Un numero di bucket pari a 2.000.000 sarebbe il valore minimo accettabile. La riduzione del livello delle prestazioni potrebbe essere tollerabile.  
  
### <a name="c2-too-many-duplicate-values-in-the-index"></a>C.2 L'indice contiene troppi valori duplicati?  
  
Se i valori indicizzati di hash presentano un tasso elevato di duplicati, i bucket di hash avranno catene più lunghe.  
  
Si supponga di avere la stessa tabella SupportEvent del blocco di codice con sintassi T-SQL riportato sopra. Il codice T-SQL seguente dimostra come trovare e visualizzare il rapporto tra *tutti* i valori e i valori *univoci* :  
  
        -- Calculate ratio of:  Rows / Unique_Values.  
    DECLARE @allValues float(8) = 0.0, @uniqueVals float(8) = 0.0;  
      
    SELECT @allValues = Count(*) FROM SupportEvent;  
      
    SELECT @uniqueVals = Count(*) FROM  
      (SELECT DISTINCT SupportEngineerName  
         FROM SupportEvent) as d;  
      
        -- If (All / Unique) >= 10.0, use a nonclustered index, not a hash.   
    SELECT Cast((@allValues / @uniqueVals) as float) as [All_divby_Unique];  
    go  
  
- Un rapporto di 10:0 o superiore indica che un hash sarebbe un tipo di indice inadeguato. Considerare la possibilità di utilizzare in alternativa un indice non cluster.   
  
## <a name="d-troubleshooting-hash-index-bucket-count"></a>D. Risoluzione dei problemi relativi al numero di bucket dell'indice hash  
  
Questa sezione illustra come risolvere i problemi relativi al numero di bucket per l'indice hash.  
  
### <a name="d1-monitor-statistics-for-chains-and-empty-buckets"></a>D.1 Monitorare le statistiche per le catene e i bucket vuoti  
  
È possibile monitorare l'integrità statistica degli indici hash eseguendo l'istruzione T-SQL SELECT seguente. L'istruzione SELECT usa la vista di gestione dati (DMV) denominata **sys.dm_db_xtp_hash_index_stats**.  
  
  
```t-sql
  SELECT  
    QUOTENAME(SCHEMA_NAME(t.schema_id)) + N'.' + QUOTENAME(OBJECT_NAME(h.object_id)) as [table],   
    i.name                   as [index],   
    h.total_bucket_count,  
    h.empty_bucket_count,  
      
    FLOOR((  
      CAST(h.empty_bucket_count as float) /  
        h.total_bucket_count) * 100)  
                             as [empty_bucket_percent],  
    h.avg_chain_length,   
    h.max_chain_length  
  FROM  
         sys.dm_db_xtp_hash_index_stats  as h   
    JOIN sys.indexes                     as i  
            ON h.object_id = i.object_id  
           AND h.index_id  = i.index_id  
    JOIN sys.memory_optimized_tables_internal_attributes ia ON h.xtp_object_id=ia.xtp_object_id
    JOIN sys.tables t on h.object_id=t.object_id
  WHERE ia.type=1
  ORDER BY [table], [index];  
```
  
  
Confrontare i risultati dell'istruzione SELECT con le linee guida statistiche seguenti:  
  
- Bucket vuoti:  
  - 33% è un valore di destinazione valido, ma una percentuale più grande (anche 90%) è in genere accettabile.  
  - Quando il numero di bucket è pari al numero di valori di chiave distinct, circa il 33% dei bucket è vuoto.  
  - Un valore inferiore al 10% è troppo basso.  
- Catene all'interno dei bucket:  
  - Una lunghezza media della catena pari a 1 è ideale nel caso in cui non sono presenti valori duplicati delle chiavi di indice. Le lunghezze della catena fino a 10 sono in genere accettabili.  
  - Se la lunghezza media delle catene è maggiore di 10 e la percentuale di bucket vuoti è superiore al 10%, il numero di duplicati dei dati è tale per cui un indice hash potrebbe non essere il tipo più appropriato.  
  

  
### <a name="d2-demonstration-of-chains-and-empty-buckets"></a>D.2 Dimostrazione delle catene e dei bucket vuoti  
  
  
Il blocco di codice T-SQL seguente offre un modo semplice per testare un `SELECT * FROM sys.dm_db_xtp_hash_index_stats;`. Il blocco di codice viene completato in 1 minuto. Di seguito sono riportate le fasi del blocco di codice seguente:  
  
  
1. Crea una tabella con ottimizzazione per la memoria con alcuni indici hash.  
2. Popola la tabella con migliaia di righe.  
    A. Viene usato un operatore modulo per configurare il tasso di valori duplicati nella colonna StatusCode.  
    B. Il ciclo INSERT inserisce 262144 righe in circa 1 minuto.  
3. Con PRINT viene stampato un messaggio che chiede di eseguire l'istruzione SELECT precedente da **sys.dm_db_xtp_hash_index_stats**.  
  
  
```t-sql
    DROP TABLE IF EXISTS SalesOrder_Mem;  
    go  
      
      
    CREATE TABLE SalesOrder_Mem  
    (  
      SalesOrderId   uniqueidentifier  NOT NULL  DEFAULT newid(),  
      OrderSequence  int               NOT NULL,  
      OrderDate      datetime2(3)      NOT NULL,  
      StatusCode     tinyint           NOT NULL,  
      
      PRIMARY KEY NONCLUSTERED  
          HASH (SalesOrderId)  WITH (BUCKET_COUNT = 262144),  
      
      INDEX ix_OrderSequence  
          HASH (OrderSequence) WITH (BUCKET_COUNT = 20000),  
      
      INDEX ix_StatusCode  
          HASH (StatusCode)    WITH (BUCKET_COUNT = 8),  
      
      INDEX ix_OrderDate       NONCLUSTERED (OrderDate DESC)  
    )  
      WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
    go  
      
        --------------------  
      
    SET NoCount ON;  
      
      -- Same as PK bucket_count.  68 seconds to complete.  
    DECLARE @i int = 262144;  
      
    BEGIN TRANSACTION;  
      
    WHILE @i > 0  
    Begin  
      
      INSERT SalesOrder_Mem  
          (OrderSequence, OrderDate, StatusCode)  
        Values  
          (@i, GetUtcDate(), @i % 8);  -- Modulo technique.  
      
      SET @i -= 1;  
    End  
    COMMIT TRANSACTION;  
      
    PRINT 'Next, you should query:  sys.dm_db_xtp_hash_index_stats .';  
    go  
```  
  
  
Il ciclo INSERT precedente esegue queste operazioni:  
  
- Inserisce valori univoci per l'indice di chiave primaria e per IX_OrderSequence.  
- Inserisce un paio di centinaia di migliaia di righe che rappresentano solo 8 valori distinct per StatusCode. È quindi presente un tasso elevato di duplicazione di valori nell'indice ix_StatusCode.  
  
Per la risoluzione dei problemi quando il numero di bucket non è ottimale, esaminare il seguente output di SELECT da **sys.dm_db_xtp_hash_index_stats**. Per questi risultati abbiamo aggiunto `WHERE Object_Name(h.object_id) = 'SalesOrder_Mem'` all'istruzione SELECT copiata dalla sezione D.1.  
  
  
  
I risultati SELECT vengono visualizzati dopo il codice, artificialmente suddivisi in due tabelle di risultati più ristretti per una migliore visualizzazione.  
  
- Di seguito sono riportati i risultati per *bucket_count*.  
  
  
| IndexName | total_bucket_count | empty_bucket_count | EmptyBucketPercent |  
| :-------- | -----------------: | -----------------: | -----------------: |  
| ix_OrderSequence | 32768 | 13 | 0 |  
| ix_StatusCode | 8 | 4 | 50 |  
| PK_SalesOrd_B14003... | 262144 | 96525 | 36 |  
  
  
- Successivamente vengono riportati i risultati per *chain_length*.  
  
  
| IndexName | avg_chain_length | max_chain_length |  
| :-------- | ---------------: | ---------------: |  
| ix_OrderSequence | 8 | 26 |  
| ix_StatusCode | 65536 | 65536 |  
| PK_SalesOrd_B14003... | 1 | 8 |  
  
  
  
  
Interpretiamo la tabella dei risultati precedenti per i tre indici hash:  
  
*ix_StatusCode:*  
  
- Il 50% dei bucket è vuoto, una condizione positiva.  
- La lunghezza media della catena, però, è molto elevata (65536).  
  - Questo è indicativo di un tasso elevato di valori duplicati.  
  - Quindi, l'uso di un indice hash non è appropriato in questo caso. È più opportuno utilizzare in alternativa un indice non cluster.  
  
*ix_OrderSequence:*  
  
- Lo 0% dei bucket è vuoto, un valore troppo basso.  
- La lunghezza media della catena è 8, anche se tutti i valori dell'indice sono univoci.  
  - È quindi consigliabile aumentare il numero di bucket per avvicinare la lunghezza media della catena a 2 o 3.  
- Dato che la chiave di indice ha 262144 valori univoci, il numero di bucket deve essere pari ad almeno 262144.  
  - Se si prevede una crescita futura, il numero di bucket deve essere maggiore.  
  
*Indice di chiave primaria (PK_SalesOrd_...):*  
  
- Il 36% dei bucket è vuoto, una condizione positiva.  
- La lunghezza media della catena è pari a 1, un'altra condizione positiva. Non è necessario apportare alcuna modifica.  
  
  
### <a name="d3-balancing-the-trade-off"></a>D.3 Soluzione di compromesso  
  
I carichi di lavoro OLTP si focalizzano su singole righe. Le scansioni complete delle tabelle non fanno in genere parte del percorso critico per le prestazioni per i carichi di lavoro OLTP. Occorre quindi trovare un compromesso tra:  
  
- Quantità di memoria utilizzata e  
- Prestazioni dei test di uguaglianza e delle operazioni di inserimento.  
  
  
*Se l'utilizzo della memoria è l'aspetto più rilevante:*  
  
- Scegliere un numero di bucket simile al numero di record di chiave di indice.  
- Il numero di bucket non deve essere notevolmente inferiore al numero di valori di chiave di indice, in quanto ciò influisce sulla maggior parte delle operazioni DML nonché sul tempo necessario per il recupero del database dopo il riavvio del server.  
  
  
*Se le prestazioni dei test di uguaglianza sono l'aspetto più rilevante:*  
  
- Un numero di bucket superiore, due o tre volte maggiore rispetto al numero di valori di indice univoci, è appropriato. Un numero maggiore comporta:  
  - Maggiore rapidità di recupero quando si cerca uno specifico valore.  
  - Un utilizzo maggiore della memoria.  
  - Prolungamento del tempo necessario per l'analisi completa dell'indice hash.  
  
  
  
  
## <a name="e-strengths-of-hash-indexes"></a>E. Punti di forza degli indici hash  
  
  
Un indice hash è da preferirsi a un indice non cluster quando:  
  
- Le query verificano la colonna indicizzata usando una clausola WHERE con un'uguaglianza, come nell'esempio seguente:  
  
  
  
    SELECT col9 FROM TableZ  
        WHERE Z_Id = 2174;  
  
  
  
### <a name="e1-multi-column-hash-index-keys"></a>E.1 Chiavi di indice hash a più colonne  
  
  
L'indice a due colonne può essere un indice non cluster o un indice hash. Si supponga che le colonne di indice siano col1 e col2. Data la seguente istruzione SQL SELECT, solo l'indice non cluster potrebbe essere utile per Query Optimizer:  
  
  
    SELECT col1, col3  
        FROM MyTable_memop  
        WHERE col1 = 'dn';  
  
  
L'indice hash necessita della clausola WHERE per specificare un test di uguaglianza per ogni colonna della chiave. In caso contrario l'indice hash non è utile per Query Optimizer.  
  
Nessuno dei due tipi di indice è utile se la clausola WHERE specifica solo la seconda colonna della chiave di indice.  

