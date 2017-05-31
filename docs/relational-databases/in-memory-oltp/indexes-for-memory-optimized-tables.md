---
title: Indici per tabelle con ottimizzazione per la memoria | Microsoft Docs
ms.custom:
- MSDN content
- MSDN - SQL DB
ms.date: 10/24/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.service: sql-database
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eecc5821-152b-4ed5-888f-7c0e6beffed9
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f55708bc9eaf8e94cf33ead19cf62cbc319e8e63
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="indexes-for-memory-optimized-tables"></a>Indici per tabelle con ottimizzazione per la memoria
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  
Questo articolo descrive i tipi di indice disponibili per una tabella con ottimizzazione per la memoria. Questo articolo:  
  
- Fornisce brevi esempi di codice per illustrare la sintassi Transact-SQL.  
- Descrive la differenza tra gli indici con ottimizzazione per la memoria e i tradizionali indici basati su disco.  
- Spiega in quali circostanze ciascun tipo di indice con ottimizzazione per la memoria rappresenta la scelta ottimale.  
  
  
Gli indici*hash* sono descritti in dettaglio in un [articolo strettamente correlato](../../relational-databases/in-memory-oltp/hash-indexes-for-memory-optimized-tables.md).  
  
  
Gli indici*columnstore* sono illustrati in [un altro articolo](~/relational-databases/indexes/columnstore-indexes-overview.md).  
  
  
## <a name="a-syntax-for-memory-optimized-indexes"></a>A. Sintassi per gli indici con ottimizzazione per la memoria  
  
Ogni istruzione CREATE TABLE per una tabella con ottimizzazione per la memoria deve includere tra 1 e 8 clausole per dichiarare gli indici. Il tipo di indice deve essere uno dei seguenti:  
  
- Indice hash.  
- Indice non cluster (struttura interna predefinita di un albero B).  
  
  
Per essere dichiarata con DURABILITY = SCHEMA_AND_DATA predefinita, la tabella con ottimizzazione per la memoria deve contenere una chiave primaria. La clausola PRIMARY KEY NONCLUSTERED nell'istruzione CREATE TABLE seguente soddisfa due requisiti:  
  
- Fornisce un indice per soddisfare il requisito minimo di un indice nell'istruzione CREATE TABLE.  
- Fornisce la chiave primaria è necessaria per la clausola SCHEMA_AND_DATA.  
  
  
  
    CREATE TABLE SupportEvent  
    (  
        SupportEventId   int NOT NULL  
            PRIMARY KEY NONCLUSTERED,  
        ...  
    )  
        WITH (  
            MEMORY_OPTIMIZED = ON,  
            DURABILITY = SCHEMA_AND_DATA);  
  
  
  
### <a name="a1-code-sample-for-syntax"></a>A.1 Esempio di codice per la sintassi  
  
Questa sottosezione contiene un blocco di codice Transact-SQL che mostra la sintassi per creare vari indici in una tabella con ottimizzazione per la memoria. Il codice dimostra quanto segue:  
  
  
1. Creare una tabella con ottimizzazione per la memoria.  
2. Usare le istruzioni ALTER TABLE per aggiungere due indici.  
3. Usare INSERT per inserire alcune righe di dati.  
  
  
  
    DROP TABLE IF EXISTS SupportEvent;  
    go  
  
    CREATE TABLE SupportEvent  
    (  
      SupportEventId   int               not null   identity(1,1)  
        PRIMARY KEY NONCLUSTERED,  
  
      StartDateTime        datetime2     not null,  
      CustomerName         nvarchar(16)  not null,  
      SupportEngineerName  nvarchar(16)      null,  
      Priority             int               null,  
      Description          nvarchar(64)      null  
    )  
      WITH (  
        MEMORY_OPTIMIZED = ON,  
        DURABILITY = SCHEMA_AND_DATA);  
    go  
      
        --------------------  
      
    ALTER TABLE SupportEvent  
      ADD CONSTRAINT constraintUnique_SDT_CN  
        UNIQUE NONCLUSTERED (StartDateTime DESC, CustomerName);  
    go  
  
    ALTER TABLE SupportEvent  
      ADD INDEX idx_hash_SupportEngineerName  
        HASH (SupportEngineerName) WITH (BUCKET_COUNT = 64);  -- Nonunique.  
    go  
      
        --------------------  
      
    INSERT INTO SupportEvent  
        (StartDateTime, CustomerName, SupportEngineerName, Priority, Description)  
      VALUES  
        ('2016-02-25 13:40:41:123', 'Abby', 'Zeke', 2, 'Display problem.'     ),  
        ('2016-02-25 13:40:41:323', 'Ben' , null  , 1, 'Cannot find help.'    ),  
        ('2016-02-25 13:40:41:523', 'Carl', 'Liz' , 2, 'Button is gray.'      ),  
        ('2016-02-25 13:40:41:723', 'Dave', 'Zeke', 2, 'Cannot unhide column.');  
    go  
  
  
  
## <a name="b-nature-of-memory-optimized-indexes"></a>B. Natura degli indici con ottimizzazione per la memoria.  
  
In una tabella con ottimizzazione per la memoria, ogni indice è anche ottimizzato per la memoria. Le differenze tra un indice in un indice con ottimizzazione per la memoria e un indice tradizionale in una tabella basata su disco sono molte.  
  
Ogni indice con ottimizzazione per la memoria esiste solo nella memoria attiva. L'indice non viene rappresentato sul disco.  
  
- Quando il database torna online, gli indici con ottimizzazione per la memoria vengono ricompilati.  
  
  
Quando un'istruzione SQL UPDATE modifica i dati in una tabella con ottimizzazione per la memoria, le modifiche corrispondenti agli indici non vengono scritte nel log.  
  
  
Le voci in un indice con ottimizzazione per la memoria contengono un indirizzo di memoria diretto alla riga nella tabella.  
  
- Al contrario, le voci in un indice tradizionale ad albero B su disco includono un valore di chiave che il sistema deve usare per trovare l'indirizzo di memoria per la riga della tabella associata.  
  
  
Gli indici con ottimizzazione per la memoria non hanno pagine fisse come gli indici basati su disco.  
  
- Non presentano il tipo tradizionale di frammentazione all'interno di una pagina e non usano quindi il fattore di riempimento.  
  
## <a name="c-duplicate-index-key-values"></a>C. Valori duplicati delle chiavi di indice

I valori duplicati delle chiavi di indice possono influire sulle prestazioni delle operazioni su tabelle con ottimizzazione per la memoria. Un numero elevato di duplicati (ad esempio, 100+) rende inefficienti le attività di gestione di un indice perché la maggior parte delle operazioni di indice deve attraversare catene di duplicati. L'impatto può essere notato nelle operazioni INSERT, UPDATE e DELETE sulle tabelle con ottimizzazione per la memoria. Questo problema è più evidente nel caso di indici hash, sia per il costo inferiore per ogni operazione per gli indici hash sia per l'interferenza di catene di duplicati di grandi dimensioni con la catena di collisioni hash. Per ridurre la duplicazione di un indice, usare un indice non cluster e aggiungere colonne aggiuntive, ad esempio dalla chiave primaria, alla fine della chiave di indice per ridurre il numero di duplicati.

Si consideri, ad esempio, una tabella clienti con una chiave primaria impostata su CustomerId e un indice sulla colonna CustomerCategoryID. In genere in una determinata categoria si trovano molti clienti e quindi esistono molti valori duplicati per una determinata chiave di indice sulla colonna CustomerCategoryID. In questo scenario, è consigliabile usare un indice non cluster (CustomerCategoryID, CustomerId). L'indice può essere usato per le query che usano un predicato che interessa il valore CustomerCategoryID e non contiene la duplicazione evitando inefficienze nella manutenzione di indici.

La query seguente mostra il numero medio di valori di chiave di indice duplicati per l'indice in `CustomerCategoryID` nella tabella `Sales.Customers`, all'interno del database di esempio [WideWorldImporters](https://msdn.microsoft.com/library/mt734199(v=sql.1).aspx).

```Transact-SQL
    SELECT AVG(row_count) FROM
       (SELECT COUNT(*) AS row_count 
        FROM Sales.Customers
        GROUP BY CustomerCategoryID) a
```

Per valutare il numero medio di duplicati di chiave di indice per la tabella e l'indice in uso, sostituire `Sales.Customers` con il nome della tabella e `CustomerCategoryID` con l'elenco delle colonne di chiave di indice.

## <a name="d-comparing-when-to-use-each-index-type"></a>D. Confronto tra le situazioni in cui usare ogni tipo di indice  
  
  
La scelta del tipo di indice ottimale dipende dalla natura query.  

Quando si implementano tabelle con ottimizzazione per la memoria in un'applicazione esistente, la raccomandazione generale consiste nell'iniziare con gli indici non cluster, poiché le relative funzionalità sono più simili alle funzionalità degli indici non cluster e cluster tradizionali sulle tabelle basate su disco. 
  
  
### <a name="d1-strengths-of-nonclustered-indexes"></a>D.1 Punti di forza degli indici non cluster  
  
  
Un indice non cluster è da preferirsi a un indice hash quando:  
  
- Le query hanno una clausola ORDER BY nella colonna indicizzata.  
- Query in cui viene verificata solo la colonna o le colonne iniziali di un indice a più colonne.  
- Le query verificano la colonna indicizzata usando una clausola WHERE con:  
  - Una disuguaglianza: *WHERE StatusCode != 'Done'*  
  - Un intervallo di valori: *WHERE Quantity >= 100*  
  
  
Un indice non cluster è da preferirsi a un indice hash in tutte le istruzioni SELECT seguenti:  
  
  
  
    SELECT col2 FROM TableA  
        WHERE StartDate > DateAdd(day, -7, GetUtcDate());  
      
    SELECT col3 FROM TableB  
        WHERE ActivityCode != 5;  
      
    SELECT StartDate, LastName  
        FROM TableC  
        ORDER BY StartDate;  
      
    SELECT IndexKeyColumn2  
        FROM TableD  
        WHERE IndexKeyColumn1 = 42;  
  
  
  
### <a name="d2-strengths-of-hash-indexes"></a>D.2 Punti di forza degli indici hash  
  
  
Un [indice hash](../../relational-databases/in-memory-oltp/hash-indexes-for-memory-optimized-tables.md) è da preferirsi a un indice non cluster quando:  
  
- Le query verificano le colonne indicizzate usando una clausola WHERE con un'uguaglianza esatta su tutte le colonne delle chiavi di indice, come nell'esempio seguente:  
  
  
  
    SELECT col9 FROM TableZ  
        WHERE Z_Id = 2174;  
  
  
  
### <a name="d3-summary-table-to-compare-index-strengths"></a>D.3 Tabella riepilogativa dei punti di forza degli indici a confronto  
  
  
Nella tabella seguente sono elencate tutte le operazioni supportate dai vari tipi di indice.  
  
  
| Operazione | Con ottimizzazione per la memoria, <br/> hash | Con ottimizzazione per la memoria, <br/> non cluster | Basato su disco, <br/> (non) cluster |  
| :-------- | :--------------------------- | :----------------------------------- | :------------------------------------ |  
| Index Scan, recupera tutte le righe della tabella. | Sì | Sì | Sì |  
| Index Seek su predicati di uguaglianza (=). | Sì <br/> (chiave completa necessaria) | Sì  | Sì |  
| Index Seek su predicati di disuguaglianza e di intervallo <br/> (>, <, \<=, >=, BETWEEN). | No <br/> (risultati in un'analisi di indice) | Sì | Sì |  
| Recupero di righe con un ordinamento corrispondente alla definizione dell'indice. | No | Sì | Sì |  
| Recupero di righe con un ordinamento inverso rispetto alla definizione dell'indice. | No | No | Sì |  
  
  
Nella tabella, Sì significa che l'indice può soddisfare la richiesta in modo appropriato e No significa che non può.  


  
  
\<!--   
Indexes_for_Memory-Optimized_Tables.md , which is....  
CAPS guid: {eecc5821-152b-4ed5-888f-7c0e6beffed9}  
mt670614.aspx  
  
Application-Level%20Partitioning.xml , {162d1392-39d2-4436-a4d9-ee5c47864c5a}  
  
/Image/hekaton_tables_23d.png , fbc511a0-304c-42f7-807d-d59f3193748f  
  
  
Replaces dn511012.aspx , which is....  
CAPS guid: {86805eeb-6972-45d8-8369-16ededc535c7}  
  
GeneMi  ,  2016-05-05  Thursday  17:25pm  (Hash content moved to new child article, e922cc3a-3d6e-453b-8d32-f4b176e98488.)  
-->  
  
  
  



