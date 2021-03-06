---
title: Guida sull'architettura di elaborazione delle query | Microsoft Docs
ms.custom: ''
ms.date: 06/06/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- guide, query processing architecture
- query processing architecture guide
- row mode execution
- batch mode execution
ms.assetid: 44fadbee-b5fe-40c0-af8a-11a1eecf6cb5
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: d85ac4addb2b1ec0e709a4e0fd72f0ca0be46f86
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51701479"
---
# <a name="query-processing-architecture-guide"></a>Guida sull'architettura di elaborazione delle query
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Il [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] consente di elaborare le query su diverse architetture di archiviazione dei dati, come tabelle locali, tabelle partizionate e tabelle distribuite su più server. Negli argomenti seguenti viene descritta l'elaborazione delle query e l'ottimizzazione del riutilizzo delle query in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tramite la memorizzazione nella cache dei piani di esecuzione.

## <a name="execution-modes"></a>Modalità di esecuzione
Il [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] può elaborare istruzioni SQL usando due modalità di elaborazione distinte:
- Esecuzione in modalità riga
- Esecuzione in modalità batch

### <a name="row-mode-execution"></a>Esecuzione in modalità riga
L'*esecuzione in modalità riga* è un metodo di elaborazione delle query utilizzato con le tabelle RDMBS tradizionali in cui i dati vengono archiviati in formato riga. Quando una query viene eseguita e accede ai dati in tabelle rowstore, gli operatori dell'albero di esecuzione e gli operatori figlio leggono ogni riga necessaria in tutte le colonne specificate nello schema della tabella. Da ogni riga letta, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] recupera le colonne richieste per il set di risultati, come indicato dall'istruzione SELECT, dal predicato di JOIN o dal predicato di filtro.

> [!NOTE]
> L'esecuzione in modalità riga è molto efficiente per gli scenari OLTP, ma può rivelarsi meno efficiente nell'analisi di grandi quantità di dati, ad esempio in scenari che coinvolgono data warehouse.

### <a name="batch-mode-execution"></a>Esecuzione in modalità batch  
L'*esecuzione in modalità batch* è un metodo di elaborazione delle query con cui le query elaborano più righe contemporaneamente. Ogni colonna all'interno di un batch viene archiviata come vettore in un'area separata della memoria, pertanto l'elaborazione in modalità batch è basata su vettore. L'elaborazione in modalità batch usa inoltre algoritmi ottimizzati per le CPU multicore e la maggiore velocità effettiva di memoria dell'hardware moderno.      

L'esecuzione in modalità batch è strettamente integrata nel formato di archiviazione columnstore, per il quale è ottimizzata. L'elaborazione in modalità batch funziona sui dati compressi, quando disponibili, ed elimina gli [operatori di scambio](../relational-databases/showplan-logical-and-physical-operators-reference.md#exchange) utilizzati dall'esecuzione in modalità riga. Ne derivano un migliore parallelismo e prestazioni più veloci.    

Quando una query viene eseguita in modalità batch e accede ai dati negli indici columnstore, gli operatori dell'albero di esecuzione e gli operatori figlio leggono più righe insieme in segmenti di colonna. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] legge solo le colonne necessarie per il risultato, come indicato dall'istruzione SELECT, dal predicato di JOIN o dal predicato di filtro.    
Per altre informazioni sugli indici columnstore, vedere [Architettura degli indici columnstore](../relational-databases/sql-server-index-design-guide.md#columnstore_index).  

> [!NOTE]
> L'esecuzione in modalità batch è molto efficiente negli scenari che coinvolgono data warehouse in cui vengono lette e aggregate grandi quantità di dati.

## <a name="sql-statement-processing"></a>Elaborazione di istruzioni SQL
L'elaborazione di una singola istruzione [!INCLUDE[tsql](../includes/tsql-md.md)] rappresenta la modalità più semplice di esecuzione delle istruzioni SQL in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Per illustrare il processo di base, viene usata la procedura di elaborazione di una singola istruzione `SELECT` che fa riferimento esclusivamente a tabelle di base locali, non a viste o tabelle remote.

### <a name="logical-operator-precedence"></a>Ordine di precedenza degli operatori logici

Se in un'istruzione vengono usati più operatori logici, viene valutato prima `NOT`, quindi `AND` e infine `OR`. Gli operatori aritmetici (e bit per bit) vengono valutati prima degli operatori logici. Per altre informazioni, vedere [Precedenza degli operatori](../t-sql/language-elements/operator-precedence-transact-sql.md).

Nell'esempio seguente la condizione per il colore riguarda il modello di prodotto 21 e non il modello di prodotto 20, perché `AND` ha la priorità rispetto a `OR`.

```sql
SELECT ProductID, ProductModelID
FROM Production.Product
WHERE ProductModelID = 20 OR ProductModelID = 21
  AND Color = 'Red';
GO
```

È possibile modificare il significato della query aggiungendo le parentesi in modo da imporre la priorità dell'operatore `OR` nell'ordine di valutazione. La query seguente trova solo i prodotti di colore rosso dei modelli 20 e 21.

```sql
SELECT ProductID, ProductModelID
FROM Production.Product
WHERE (ProductModelID = 20 OR ProductModelID = 21)
  AND Color = 'Red';
GO
```

L'uso delle parentesi, anche quando non è obbligatorio, può contribuire a rendere le query più leggibili e a ridurre il rischio di errori dovuti all'ordine di precedenza degli operatori. Non ha inoltre alcun effetto negativo rilevante sulle prestazioni. L'esempio seguente risulta più leggibile rispetto a quello precedente, anche se sintatticamente i due esempi sono identici.

```sql
SELECT ProductID, ProductModelID
FROM Production.Product
WHERE ProductModelID = 20 OR (ProductModelID = 21
  AND Color = 'Red');
GO
```

### <a name="optimizing-select-statements"></a>Ottimizzazione delle istruzioni SELECT

Un'istruzione `SELECT` non definisce esattamente la procedura che il server di database deve eseguire per recuperare i dati richiesti. Il server di database deve pertanto analizzare l'istruzione per determinare il metodo più efficace per l'estrazione dei dati. Tale procedura, denominata ottimizzazione dell'istruzione `SELECT` , viene eseguita dal componente Query Optimizer. I dati di input per Query Optimizer sono costituiti dalla query, dallo schema del database (definizioni di tabella e indice) e dalle statistiche del database. L'output di Query Optimizer è un piano di esecuzione della query, talvolta definito piano di query o semplicemente piano. La descrizione dettagliata del contenuto di un piano di query è riportata più avanti in questo argomento.

I dati di input e di output di Query Optimizer durante l'ottimizzazione di una singola istruzione `SELECT` sono illustrati nel diagramma seguente:

![query_processor_io](../relational-databases/media/query-processor-io.gif)

Un'istruzione `SELECT` definisce soltanto gli elementi seguenti:  
* Il formato del set di risultati. Questo elemento viene nella maggior parte dei casi specificato nell'elenco di selezione. Altre clausole, ad esempio `ORDER BY` e `GROUP BY` , possono tuttavia influire sul formato finale del set di risultati.
* Le tabelle che contengono i dati di origine. La modalità è specificata nella clausola `FROM` .
* La relazione logica tra le tabelle ai fini dell'istruzione `SELECT` . Questo elemento viene definito nelle specifiche di join, incluse nella clausola `WHERE` oppure in una clausola `ON` che segue una clausola `FROM`.
* Condizioni che le righe delle tabelle di origine devono soddisfare per essere incluse nel risultato dell'istruzione `SELECT` . Queste condizioni vengono specificate nelle clausole `WHERE` ed `HAVING` .

Il piano di esecuzione di una query è costituito dalla definizione degli elementi seguenti: 

* La sequenza di accesso alle tabelle di origine.  
  In genere il server di database può utilizzare molte sequenze diverse per accedere alle tabelle di base e quindi compilare il set di risultati. Ad esempio, se l'istruzione `SELECT` fa riferimento a tre tabelle, il server di database può accedere innanzitutto a `TableA`, usare i dati di `TableA` per estrarre le righe corrispondenti da `TableB`, quindi usare i dati di `TableB` per estrarre i dati da `TableC`. Di seguito vengono indicate le altre sequenze di accesso alle tabelle utilizzabili dal server di database:  
  `TableC`, `TableB`, `TableA`o  
  `TableB`, `TableA`, `TableC`o  
  `TableB`, `TableC`, `TableA`o  
  `TableC`, `TableA`, `TableB`  

* I metodi utilizzati per estrarre i dati da ogni tabella.  
  Per accedere ai dati di ogni tabella sono in genere disponibili metodi diversi. Se sono necessarie solo alcune righe con valori di chiave specifici, il server di database può utilizzare un indice. Se sono necessarie tutte le righe della tabella, il server di database può ignorare gli indici ed eseguire un'analisi di tabella. Se sono necessarie tutte le righe di una tabella, ma l'indice contiene colonne chiave incluse in una clausola `ORDER BY`, è consigliabile eseguire l'analisi dell'indice anziché della tabella per evitare che il set di risultati venga ordinato separatamente. Se una tabella è di dimensioni molto ridotte, l'analisi della tabella può rappresentare il metodo più efficiente per quasi tutti gli accessi alla tabella.

Il processo di scelta di un piano di esecuzione è denominato ottimizzazione. Query Optimizer è uno dei principali componenti di un sistema di database SQL. L'overhead generato dall'utilizzo di Query Optimizer per l'analisi della query e la scelta di un piano è ampiamente compensato dall'efficienza del piano di esecuzione scelto. Si supponga, ad esempio, che il progetto di costruzione di una casa venga assegnato a due imprese edili diverse. Se un'impresa dedica alcuni giorni alla pianificazione della costruzione della casa e l'altra impresa inizia immediatamente la costruzione senza alcuna pianificazione, è molto probabile che l'impresa che ha pianificato il progetto termini la costruzione per prima.

Query Optimizer di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] è un'utilità di ottimizzazione basata sui costi. A ogni piano di esecuzione possibile corrisponde un costo in termini di quantità di risorse del computer utilizzate. Query Optimizer analizza i piani possibili e sceglie il piano con il costo stimato minore. Per alcune istruzioni `SELECT` complesse i piani di esecuzione possibili sono migliaia. In questi casi, Query Optimizer non analizza tutte le combinazioni possibili, ma utilizza algoritmi complessi per individuare rapidamente un piano di esecuzione il cui costo si avvicini il più possibile al costo minimo teorico.

Query Optimizer di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] non sceglie esclusivamente il piano di esecuzione con il costo minore in termini di risorse, ma individua il piano che restituisce più rapidamente i risultati all'utente con un costo ragionevole in termini di risorse. Ad esempio, l'esecuzione parallela di una query in genere utilizza una quantità di risorse maggiore rispetto all'esecuzione seriale, ma consente di completare la query più rapidamente. Query Optimizer di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] userà un piano di esecuzione parallela per restituire i risultati, a condizione che tale piano non aumenti il carico sul server.

Per la stima dei costi in termini di risorse relativi ai diversi metodi di estrazione delle informazioni da una tabella o da un indice, Query Optimizer di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] si basa sulle le statistiche di distribuzione. Le statistiche di distribuzione vengono registrate per le colonne e gli indici e contengono informazioni sulla densità <sup>1</sup> dei dati sottostanti. Queste informazioni sono usate per indicare la selettività dei valori in un indice o in una colonna. Ad esempio, in una tabella che rappresenta automobili, molte automobili vengono prodotte dallo stesso costruttore, ma a ciascuna è assegnato un numero di identificazione univoco. Un indice basato sul numero di identificazione del veicolo è più selettivo rispetto all'indice basato sul produttore, perché il numero di identificazione del veicolo ha una densità minore rispetto al produttore. Se le statistiche dell'indice non sono aggiornate, è possibile che Query Optimizer non scelga la soluzione migliore per lo stato corrente della tabella. Per altre informazioni sulle densità, vedere [Statistiche](../relational-databases/statistics/statistics.md#density). 

<sup>1</sup> La densità definisce la distribuzione di valori univoci esistenti nei dati, o il numero medio di valori duplicati per una determinata colonna. Man mano che la densità diminuisce, aumenta la selettività di un valore.

Query Optimizer di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] è un componente importante perché consente al server di database di adattarsi in modo dinamico alle condizioni variabili del database senza fare ricorso all'intervento di un programmatore o di un amministratore di database. In questo modo i programmatori possono concentrarsi sulla descrizione del risultato finale della query. A ogni esecuzione dell'istruzione, Query Optimizer di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] compila un piano di esecuzione efficace per lo stato corrente del database.

### <a name="processing-a-select-statement"></a>Elaborazione di un'istruzione SELECT

Di seguito viene illustrata la procedura di base necessaria per elaborare una singola istruzione SELECT in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]: 

1. Il parser esegue l'analisi dell'istruzione `SELECT` e la suddivide in unità logiche, quali parole chiave, espressioni, operatori e identificatori.
2. Viene compilato un albero della query, talvolta denominata sequenza logica, che descrive i passaggi logici necessari per convertire i dati di origine nel formato necessario per il set di risultati.
3. Query Optimizer analizza le diverse modalità di accesso alle tabelle di origine e seleziona le serie di passaggi che restituiscono i risultati con maggior rapidità e con minor impiego di risorse. L'albero della query viene aggiornato in modo da registrare la serie esatta di passaggi. La versione finale ottimizzata dell'albero della query è denominato piano di esecuzione.
4. Il motore relazionale avvia l'esecuzione del piano di esecuzione. Man mano che vengono elaborati i passaggi che richiedono i dati delle tabelle di base, il motore relazionale richiede al motore di archiviazione di passare i dati dei set di righe richiesti dal motore relazionale stesso.
5. Il motore relazionale elabora i dati restituiti dal motore di archiviazione nel formato definito per il set di risultati e restituisce il set di risultati al client.

### <a name="processing-other-statements"></a>Elaborazione di altre istruzioni

La procedura di base descritta per l'elaborazione di un'istruzione `SELECT` è valida anche per altre istruzioni SQL, ad esempio `INSERT`, `UPDATE`e `DELETE`. Entrambe le istruzioni`UPDATE` e `DELETE` devono definire il set di righe da modificare o eliminare. usando un processo di identificazione delle righe corrispondente a quello che consente di identificare le righe di origine che formano il set di risultati di un'istruzione `SELECT` . Le istruzioni `UPDATE` e `INSERT` possono includere istruzioni SELECT incorporate che forniscono i valori dei dati da aggiornare o da inserire.

Anche le istruzioni DDL (Data Definition Language), ad esempio `CREATE PROCEDURE` o `ALTER TABLE`, vengono risolte in una serie di operazioni relazionali eseguite nelle tabelle del catalogo di sistema e in alcuni casi, ad esempio con `ALTER TABLE ADD COLUMN`, nelle tabelle di dati.

### <a name="worktables"></a>Tabelle di lavoro

È possibile che il motore relazionale debba compilare una tabella di lavoro per eseguire un'operazione logica specificata in un'istruzione SQL. Le tabelle di lavoro sono tabelle interne utilizzate per inserirvi i risultati intermedi. Le tabelle di lavoro vengono generate per alcune query `GROUP BY`, `ORDER BY`o `UNION` . Se, ad esempio, una clausola `ORDER BY` fa riferimento a colonne non coperte da indici, può essere necessario generare una tabella di lavoro per disporre il set di risultati nell'ordine richiesto. Le tabelle di lavoro vengono a volte utilizzate anche come spool per conservare temporaneamente il risultato dell'esecuzione di un piano della query. Le tabelle di lavoro vengono compilate in tempdb e vengono eliminate automaticamente quando non sono più necessarie.

### <a name="view-resolution"></a>Risoluzione delle viste

In Query Processor di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] le viste indicizzate e non indicizzate vengono gestite in modi diversi: 

* Le righe di una vista indicizzata vengono archiviate nel database con lo stesso formato di una tabella. Se Query Optimizer decide di utilizzare una vista indicizzata in un piano di query, la vista indicizzata verrà gestita come una tabella di base.
* Viene archiviata solo la definizione di una vista indicizzata e non le righe della vista. Query Optimizer incorpora la logica della definizione della vista nel piano di esecuzione compilato per l'istruzione SQL che fa riferimento alla vista non indicizzata. 

La logica usata da Query Optimizer di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] per decidere quando usare una vista indicizzata è analoga alla logica usare per decidere quando usare un indice per una tabella. Se i dati della vista indicizzata coprono tutta o parte dell'istruzione SQL e Query Optimizer identifica un indice della vista come percorso di accesso più economico, tale indice verrà scelto indipendentemente dal fatto che nella query venga fatto o meno riferimento alla vista in questione.

Se un'istruzione SQL fa riferimento a una vista non indicizzata, il parser e Query Optimizer analizzano le origini dell'istruzione SQL e della vista e le risolvono in un singolo piano di esecuzione. Il piano di esecuzione è lo stesso per l'istruzione SQL e per la vista.

Si consideri, ad esempio, la vista seguente:

```sql
USE AdventureWorks2014;
GO
CREATE VIEW EmployeeName AS
SELECT h.BusinessEntityID, p.LastName, p.FirstName
FROM HumanResources.Employee AS h 
JOIN Person.Person AS p
ON h.BusinessEntityID = p.BusinessEntityID;
GO
```

In base a questa vista le due istruzioni SQL seguenti eseguono le stesse operazioni sulle tabelle di base e producono gli stessi risultati:

```sql
/* SELECT referencing the EmployeeName view. */
SELECT LastName AS EmployeeLastName, SalesOrderID, OrderDate
FROM AdventureWorks2014.Sales.SalesOrderHeader AS soh
JOIN AdventureWorks2014.dbo.EmployeeName AS EmpN
ON (soh.SalesPersonID = EmpN.BusinessEntityID)
WHERE OrderDate > '20020531';

/* SELECT referencing the Person and Employee tables directly. */
SELECT LastName AS EmployeeLastName, SalesOrderID, OrderDate
FROM AdventureWorks2014.HumanResources.Employee AS e 
JOIN AdventureWorks2014.Sales.SalesOrderHeader AS soh
ON soh.SalesPersonID = e.BusinessEntityID
JOIN AdventureWorks2014.Person.Person AS p
ON e.BusinessEntityID =p.BusinessEntityID
WHERE OrderDate > '20020531';
```

La funzionalità Showplan di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Studio indica che il motore relazionale compila lo stesso piano di esecuzione per entrambe le istruzioni `SELECT`.

### <a name="using-hints-with-views"></a>Utilizzo di hint con le viste

Gli hint inseriti nelle viste di una query possono entrare in conflitto con altri hint individuati quando la vista viene espansa in modo da accedere alle relative tabelle di base. In questo caso, la query restituisce un errore. Si consideri, ad esempio, la vista seguente nella cui definizione è contenuto un hint di tabella:

```sql
USE AdventureWorks2014;
GO
CREATE VIEW Person.AddrState WITH SCHEMABINDING AS
SELECT a.AddressID, a.AddressLine1, 
    s.StateProvinceCode, s.CountryRegionCode
FROM Person.Address a WITH (NOLOCK), Person.StateProvince s
WHERE a.StateProvinceID = s.StateProvinceID;
```

Si supponga a questo punto di immettere la query seguente:

```sql
SELECT AddressID, AddressLine1, StateProvinceCode, CountryRegionCode
FROM Person.AddrState WITH (SERIALIZABLE)
WHERE StateProvinceCode = 'WA';
```

La query ha esito negativo perché l'hint `SERIALIZABLE` applicato nella vista `Person.AddrState` della query viene propagato a entrambe le tabelle `Person.Address` e `Person.StateProvince` quando la vista viene espansa. L'espansione della vista consente anche di rilevare l'hint `NOLOCK` nella tabella `Person.Address`. Gli hint `SERIALIZABLE` e `NOLOCK` sono in conflitto tra loro, pertanto la query risultante non è corretta. 

Gli hint delle tabelle `PAGLOCK`, `NOLOCK`, `ROWLOCK`, `TABLOCK`o `TABLOCKX` sono in conflitto tra loro, così come gli hint delle tabelle `HOLDLOCK`, `NOLOCK`, `READCOMMITTED`, `REPEATABLEREAD`e `SERIALIZABLE` .

Gli hint possono propagarsi in più livelli di viste nidificate. Si supponga, ad esempio, una query che applica l'hint `HOLDLOCK` in una vista `v1`. Espandendo `v1` , si noterà che la definizione di tale vista include la vista `v2` , `v2`la cui definizione include a `NOLOCK` sua volta un hint in una delle tabelle di base. Questa tabella eredita anche l'hint `HOLDLOCK` dalla query sulla vista `v1`. Gli hint `NOLOCK` e `HOLDLOCK` sono in conflitto tra loro, pertanto la query ha esito negativo.

Quando si usa l'hint `FORCE ORDER` in una query che contiene una vista, l'ordine di join delle tabelle all'interno della vista dipende dalla posizione della vista nel costrutto ordinato. La query seguente, ad esempio, consente di selezionare da tre tabelle e una vista:

```sql
SELECT * FROM Table1, Table2, View1, Table3
WHERE Table1.Col1 = Table2.Col1 
    AND Table2.Col1 = View1.Col1
    AND View1.Col2 = Table3.Col2;
OPTION (FORCE ORDER);
```

La vista `View1` viene definita come illustrato di seguito:

```sql
CREATE VIEW View1 AS
SELECT Colx, Coly FROM TableA, TableB
WHERE TableA.ColZ = TableB.Colz;
```

L'ordine di join nel piano di query sarà quindi `Table1`, `Table2`, `TableA`, `TableB`, `Table3`.

### <a name="resolving-indexes-on-views"></a>Risoluzione di indici nelle viste

Come per qualsiasi indice, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sceglie di usare una vista indicizzata nel piano della query solo se Query Optimizer determina che tale operazione è vantaggiosa.

Le viste indicizzate possono essere create con qualsiasi versione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. In alcune edizioni di alcune versioni di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], Query Optimizer considera automaticamente la vista indicizzata. In alcune edizioni di alcune versioni di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], per usare una vista indicizzata è necessario usare l'hint della tabella `NOEXPAND`. Per i dettagli, vedere la documentazione relativa alla versione specifica.

In Query Optimizer di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] viene usata una vista indicizzata quando vengono soddisfatte le condizioni seguenti: 

* Le opzioni relative alla sessione indicate di seguito sono impostate su `ON`: 
  * `ANSI_NULLS`
  * `ANSI_PADDING`
  * `ANSI_WARNINGS`
  * `ARITHABORT`
  * `CONCAT_NULL_YIELDS_NULL`
  * `QUOTED_IDENTIFIER` 
  * L'opzione di sessione `NUMERIC_ROUNDABORT` è impostata su OFF.
* In Query Optimizer viene trovata una corrispondenza tra le colonne dell'indice della vista e gli elementi della query, tra cui: 
  * Predicati relativi a condizioni di ricerca nella clausola WHERE
  * Operazioni di join
  * Funzioni di aggregazione
  * Clausole`GROUP BY` 
  * Riferimenti alla tabella
* Il costo stimato necessario per l'utilizzo dell'indice è inferiore a quello di qualsiasi altro meccanismo di accesso considerato in Query Optimizer. 
* Ogni tabella a cui si fa riferimento nella query, direttamente oppure espandendo una vista per accedere alle tabelle sottostanti, corrispondente a un riferimento alla tabella nella vista indicizzata, deve disporre dello stesso set di hint ad essa applicato nella query.

> [!NOTE] 
> Gli hint `READCOMMITTED` e `READCOMMITTEDLOCK` sono sempre considerati diversi in questo contesto, indipendentemente dal livello corrente di isolamento delle transazioni.
 
Ad eccezione dei requisiti relativi alle opzioni `SET` e agli hint di tabella, si tratta delle stesse regole usate da Query Optimizer per determinare se l'indice di una tabella copre una query. Per utilizzare una vista indicizzata, non è necessario specificare nient'altro nella query.

Non è necessario che una query faccia riferimento in modo esplicito a una vista indicizzata nella clausola `FROM` affinché Query Optimizer usi la vista indicizzata. Se la query include riferimenti alle colonne delle tabelle di base incluse anche nella vista indicizzata e tramite Query Optimizer viene determinato che l'utilizzo della vista indicizzata è il meccanismo di accesso più economico, in Query Optimizer viene scelta la vista indicizzata con modalità analoghe a quelle utilizzate per scegliere gli indici delle tabelle di base a cui non viene fatto riferimento diretto in una query. Query Optimizer potrebbe scegliere la vista anche se include colonne a cui non fa riferimento la query, a condizione che la vista stessa rappresenti la soluzione più economica ai fini della copertura di una o più colonne specificate nella query.

Query Optimizer elabora le viste indicizzate a cui fa riferimento la clausola `FROM` come viste standard. Tramite Query Optimizer la definizione della vista viene espansa nella query all'inizio del processo di ottimizzazione. Viene quindi eseguita la ricerca della corrispondenza nella vista indicizzata. La vista indicizzata potrebbe essere usata nel piano di esecuzione finale selezionato da Query Optimizer oppure il piano può ottenere dalla vista i dati necessari accedendo alle tabelle di base a cui fa riferimento la vista. Tramite Query Optimizer viene scelta l'alternativa con il costo inferiore.

#### <a name="using-hints-with-indexed-views"></a>Utilizzo di hint con viste indicizzate

È possibile impedire l'uso delle viste indicizzate da parte di una query usando l'hint per la query `EXPAND VIEWS` oppure è possibile usare l'hint di tabella `NOEXPAND` per fare in modo che venga impiegato un indice per una vista indicizzata specificata nella clausola `FROM` di una query. È tuttavia consigliabile lasciar determinare in modo dinamico a Query Optimizer i metodi di accesso migliori da utilizzare per ogni query. Limitare l'uso degli hint `EXPAND` e `NOEXPAND` a casi specifici per i quali si è verificato che in tal modo è possibile ottenere un miglioramento significativo delle prestazioni.

L'opzione `EXPAND VIEWS` specifica che in Query Optimizer non verranno usati indici delle viste per l'intera query. 

Se per una vista viene specificata l'opzione `NOEXPAND` , tramite Query Optimizer viene valuta l'opportunità di usare gli indici definiti per la vista. Se l'opzione`NOEXPAND` viene specificata con la clausola `INDEX()` facoltativa, Query Optimizer userà gli indici specificati. L'opzione`NOEXPAND` può essere specificata solo per le viste indicizzate e non è supportata per quelle non indicizzate.

Quando non viene specificata né l'opzione `NOEXPAND` né `EXPAND VIEWS` in una query contenente una vista, la vista viene espansa per accedere alle tabelle sottostanti. Se la query che compone la vista contiene hint di tabella, tali hint vengono propagati alle tabelle sottostanti. Per altre informazioni su questo processo, vedere Risoluzione delle viste. Se i set di hint presenti nelle tabelle sottostanti della vista sono identici tra loro, la query può essere utilizzata per la ricerca della corrispondenza con una vista indicizzata. La maggior parte delle volte questi hint corrispondono tra loro in quanto vengono ereditati direttamente dalla vista. Se. tuttavia, la query fa riferimento a tabelle anziché a viste e gli hint applicati direttamente a tali tabelle non sono identici, la query non può essere utilizzata per la ricerca della corrispondenza con una vista indicizzata. Se gli hint `INDEX`, `PAGLOCK`, `ROWLOCK`, `TABLOCKX`, `UPDLOCK`o `XLOCK` vengono applicati a tabelle a cui fa riferimento la query dopo l'espansione della vista, la query non può essere usata per la ricerca della corrispondenza con una vista indicizzata.

Se un hint di tabella nel formato `INDEX (index_val[ ,...n] )` fa riferimento a una vista in una query e non viene specificato anche l'hint `NOEXPAND` , l'hint per l'indice viene ignorato. Per specificare l'uso di un determinato indice, usare `NOEXPAND`. 

In genere, quando Query Optimizer trova una corrispondenza tra una vista indicizzata e una query, eventuali hint specificati nelle tabelle o nelle viste nella query vengono applicati direttamente alla vista indicizzata. Se tramite Query Optimizer viene scelto di non utilizzare una vista indicizzata, eventuali hint vengono propagati direttamente alle tabelle a cui viene fatto riferimento nella vista. Per altre informazioni, vedere Risoluzione delle viste. Questa propagazione non riguarda gli hint di join, che vengono applicati solo nella relativa posizione originale nella query. Gli hint di join non vengono presi in considerazione da Query Optimizer durante la ricerca della corrispondenza tra query e viste indicizzate. Se in un piano della query viene utilizzata una vista indicizzata che corrisponde a una parte di una query contenente un hint di join, tale hint non viene utilizzato nel piano.

Nelle definizioni delle viste indicizzate non sono consentiti hint. Nella modalità di compatibilità 80 e superiore, in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] vengono ignorati gli hint contenuti nelle definizioni delle viste indicizzate quando ne viene eseguita la manutenzione oppure quando vengono eseguite query in cui sono utilizzate viste indicizzate. Sebbene l'utilizzo di hint nelle definizioni delle viste indicizzate non comporti la generazione di un errore di sintassi nella modalità di compatibilità 80, gli hint vengono ignorati.

### <a name="resolving-distributed-partitioned-views"></a>Risoluzione di viste partizionate distribuite

Query Processor di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ottimizza le prestazioni delle viste partizionate distribuite. Per le prestazioni delle viste partizionate distribuite, l'aspetto più importante è rappresentato dalla necessità di ridurre al minimo la quantità di dati trasferiti tra server membri.

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] compila piani dinamici e intelligenti che consentono di usare le query distribuite in modo efficiente ai fini dell'accesso ai dati da tabelle membro remote: 

* Query Processor usa prima di tutto OLE DB per recuperare le definizioni del vincolo CHECK da ogni tabella membro. In questo modo, può eseguire il mapping della distribuzione dei valori di chiave in tutte le tabelle membro.
* The Query Processor compares the key ranges specified in an SQL statement `WHERE` di un'istruzione SQL con la mappa in cui viene indicata la distribuzione delle righe nelle tabelle membro. Compila quindi un piano di esecuzione delle query che utilizza le query distribuite per recuperare solo le righe remote necessarie per completare l'istruzione SQL. Il piano di esecuzione viene compilato in modo che tutti gli accessi alle tabelle membro remote vengano rimandati al momento in cui vengono richieste le informazioni, indipendentemente dal fatto che si tratti di dati o metadati.

Si consideri, ad esempio, un sistema in cui la tabella Customers è partizionata tra Server1 (`CustomerID` da 1 a 3299999), Server2 (`CustomerID` da 3300000 a 6599999) e Server3 (`CustomerID` da 6600000 a 9999999).

Si consideri quindi il piano di esecuzione compilato per la query eseguita in Server1:

```sql
SELECT *
FROM CompanyData.dbo.Customers
WHERE CustomerID BETWEEN 3200000 AND 3400000;
```

Il piano di esecuzione di questa query estrae dalla tabella membro locale le righe con valori di chiave `CustomerID` compresi tra 3200000 e 3299999 e quindi esegue una query distribuita per recuperare da Server2 le righe con valori di chiave compresi tra 3300000 e 3400000.

Query Processor di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] può inoltre compilare una logica dinamica nei piani di esecuzione delle query per istruzioni SQL in cui i valori di chiave non sono noti al momento della compilazione del piano. Si consideri, ad esempio, la stored procedure seguente:

```sql
CREATE PROCEDURE GetCustomer @CustomerIDParameter INT
AS
SELECT *
FROM CompanyData.dbo.Customers
WHERE CustomerID = @CustomerIDParameter;
```

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] non è in grado di determinare in anticipo quale valore della chiave verrà restituito dal parametro `@CustomerIDParameter` a ogni esecuzione della procedura. Pertanto, nemmeno Query Processor può prevedere a quale tabella membro si accederà. Per gestire questa situazione, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] compila un piano di esecuzione che include una logica condizionale (ovvero filtri dinamici) in grado di determinare in base al valore del parametro di input a quale tabella membro si accederà. Se la stored procedure `GetCustomer` viene eseguita in Server1, la logica del piano di esecuzione può essere rappresentata nel modo seguente:

```sql
IF @CustomerIDParameter BETWEEN 1 and 3299999
   Retrieve row from local table CustomerData.dbo.Customer_33
ELSE IF @CustomerIDParameter BETWEEN 3300000 and 6599999
   Retrieve row from linked table Server2.CustomerData.dbo.Customer_66
ELSE IF @CustomerIDParameter BETWEEN 6600000 and 9999999
   Retrieve row from linked table Server3.CustomerData.dbo.Customer_99
```

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] compila a volte questi tipi di piani di esecuzione dinamici anche per query senza parametri. Query Optimizer può parametrizzare una query in modo che il piano di esecuzione possa essere riutilizzato. Se Query Optimizer esegue la parametrizzazione di una query che fa riferimento a una vista partizionata, non potrà più basarsi sul presupposto che le righe necessarie verranno recuperate da una tabella di base specificata e dovrà utilizzare filtri dinamici nel piano di esecuzione.

## <a name="stored-procedure-and-trigger-execution"></a>Esecuzione di stored procedure e trigger

In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] viene archiviata solo l'origine di stored procedure e trigger. Se una stored procedure o un trigger viene eseguito per la prima volta, l'origine viene compilata in un piano di esecuzione. Se la stored procedure o il trigger viene eseguito nuovamente prima che il piano di esecuzione venga rimosso dalla memoria, il motore relazionale rileva e riutilizza il piano esistente. Se il piano è stato rimosso dalla memoria, viene creato un nuovo piano. Questo processo è simile al processo seguito da [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] per tutte le istruzioni SQL. Il vantaggio principale delle prestazioni di stored procedure e trigger in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] rispetto ai batch di istruzioni SQL dinamiche è che le istruzioni SQL sono sempre uguali. pertanto, il motore relazionale mette agevolmente in corrispondenza con tutti i piani di esecuzione esistenti. I piani di stored procedure e trigger sono quindi facilmente riutilizzabili.

Il piano di esecuzione delle stored procedure e dei trigger viene eseguito indipendentemente dal piano di esecuzione del batch che chiama la stored procedure o che attiva il trigger. In tal modo viene garantito un maggiore riutilizzo dei piani di esecuzione delle stored procedure e dei trigger.

## <a name="execution-plan-caching-and-reuse"></a>Memorizzazione nella cache e riutilizzo del piano di esecuzione

In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] è presente un pool di memoria utilizzato per archiviare sia i piani di esecuzione che i buffer dei dati. La percentuale del pool allocata ai piani di esecuzione o ai buffer dei dati varia dinamicamente in base allo stato del sistema. La parte del pool di memoria usata per archiviare i piani di esecuzione è denominata cache dei piani.

I piani di esecuzione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] includono i componenti principali seguenti: 

* Piano di esecuzione della query: la parte centrale del piano di esecuzione è una struttura di dati rientrante di sola lettura che può essere usata da un numero qualsiasi di utenti. Questo elemento è detto piano della query. Nel piano della query non viene archiviato alcun contesto utente. In memoria non vi sono mai più di una o due copie del piano della query: una copia per tutte le esecuzioni seriali e una per tutte le esecuzioni parallele. La copia parallela copre tutte le esecuzioni parallele, indipendentemente dal loro grado di parallelismo. 
* Contesto di esecuzione: ogni utente che esegue la query dispone di una struttura di dati contenente i dati specifici per l'esecuzione, ad esempio i valori dei parametri. Questa struttura di dati è denominata contesto di esecuzione. Le strutture di dati del contesto di esecuzione vengono riutilizzate. Se un utente esegue una query e una delle strutture non è in uso, questa viene reinizializzata con il contesto del nuovo utente. 

![execution_context](../relational-databases/media/execution-context.gif)

Quando in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] viene eseguita un'istruzione SQL, il motore relazionale esegue prima di tutto una ricerca nella cache dei piani per verificare se è presente un piano di esecuzione esistente per la stessa istruzione SQL. L'eventuale piano esistente trovato viene riutilizzato in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], evitando così l'overhead associato alla ricompilazione dell'istruzione SQL. Se non esiste già un piano di esecuzione, in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] viene generato un nuovo piano per la query.

In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] è disponibile un algoritmo efficiente per l'individuazione di piani di esecuzione esistenti per una specifica istruzione SQL. Nella maggior parte dei sistemi, le risorse minime utilizzate da questa analisi sono inferiori a quelle risparmiate riutilizzando i piani esistenti anziché compilando ogni istruzione SQL.

Per gli algoritmi che consentono di trovare la corrispondenza tra le nuove istruzioni SQL e i piani di esecuzione esistenti inutilizzati nella cache è necessario che i riferimenti agli oggetti siano completi. Per la prima delle istruzioni `SELECT` seguenti, ad esempio, non viene trovata la corrispondenza con un piano esistente, come avviene invece per la seconda:

```sql
SELECT * FROM Person;

SELECT * FROM Person.Person;
```

### <a name="removing-execution-plans-from-the-plan-cache"></a>Rimozione di piani di esecuzione dalla cache dei piani

I piani di esecuzione rimangono nella cache dei piani fino a quando è disponibile memoria sufficiente per archiviarli. In caso di un numero eccessivo di richieste di memoria, il [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] usa un approccio basato sui costi per determinare i piani di esecuzione da rimuovere dalla cache dei piani. Per prendere una decisione basata sui costi, il [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] incrementa e decrementa una variabile relativa al costo corrente per ogni piano di esecuzione in base ai fattori descritti di seguito.

Quando un processo utente inserisce un piano di esecuzione nella cache, il costo corrente viene impostato sul costo di compilazione della query originale. Per i piani di esecuzione ad hoc, il processo utente imposta il costo corrente su zero. Quindi, ogni volta che un processo utente fa riferimento a un piano di esecuzione, il costo corrente viene reimpostato sul costo di compilazione originale. Per i piani di esecuzione ad hoc, il processo utente aumenta il costo corrente. Per tutti i piani, il valore massimo per il costo corrente corrisponde al costo di compilazione originale.

In caso di un numero eccessivo di richieste di memoria, il [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] risponde rimuovendo i piani di esecuzione dalla cache dei piani. Per determinare i piani da rimuovere, il [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] esamina ripetutamente lo stato di ogni piano di esecuzione e rimuove i piani quando il relativo costo corrente è pari a zero. Un piano di esecuzione con un costo corrente pari a zero non viene rimosso automaticamente in caso di un numero eccessivo di richieste di memoria, ma viene rimosso solo nel momento in cui il [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] esamina il piano e il costo corrente è pari a zero. Durante l'analisi di un piano di esecuzione attualmente non utilizzato da una query, il [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] decrementa il costo corrente fino a raggiungere il valore zero.

Il [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] esamina ripetutamente i piani di esecuzione fino a quando non ne viene rimosso un numero sufficiente per soddisfare i requisiti di memoria. In caso di un numero eccessivo di richieste di memoria, è possibile che il costo di un piano di esecuzione venga incrementato e decrementato più di una volta. Quando il numero di richieste diminuisce, il [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] arresta la riduzione del costo corrente dei piani di esecuzione non usati e tutti i piani di esecuzione rimangono nella cache dei piani anche se il costo relativo è pari zero.

Il [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] usa il monitoraggio risorse e i thread di lavoro dell'utente per liberare memoria dalla cache dei piani in risposta a un numero eccessivo di richieste di memoria. Il monitoraggio risorse e i thread di lavoro dell'utente possono esaminare i piani in esecuzione simultanea per ridurre il costo corrente per ogni piano di esecuzione non usato. Il monitoraggio risorse rimuove i piani di esecuzione dalla cache dei piani quando è presente un numero eccessivo di richieste di memoria globale e libera memoria per applicare i criteri per la memoria di sistema, la memoria processi, la memoria del pool di risorse e la dimensione massima per tutte le cache. 

Le dimensioni massime di tutte le cache sono rappresentate da una funzione relativa alle dimensioni del pool di buffer e non possono superare la memoria massima del server. Per altre informazioni sulla configurazione della memoria massima del server, vedere l'impostazione `max server memory` in `sp_configure`. 

In caso di un numero eccessivo di richieste di memoria cache, i thread di lavoro dell'utente rimuovono i piani di esecuzione dalla cache dei piani e applicano i criteri per le dimensioni massime e per il numero massimo di voci della singola cache. 

L'esempio seguente indica quali piani di esecuzione vengono rimossi dalla cache dei piani:

* A un piano di esecuzione viene fatto riferimento di frequente in modo che il costo non sia mai pari a zero. Il piano viene mantenuto nella cache dei piani e non viene rimosso a meno che non vi sia un numero eccessivo di richieste di memoria e il costo corrente non sia pari a zero.
* Viene inserito un piano di esecuzione ad hoc, cui non viene fatto nuovamente riferimento prima che sia presente un numero massimo di richieste di memoria. Dato che i piani ad hoc vengono inizializzati con un costo corrente pari a zero, quando il [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] esamina il piano di esecuzione, individuerà il costo corrente pari a zero e rimuoverà il piano dalla cache dei piani. Il piano di esecuzione ad hoc viene mantenuto nella cache dei piani con un costo corrente pari a zero in assenza di un numero eccessivo di richieste di memoria.

Per rimuovere manualmente un singolo piano o tutti i piani dalla cache, usare [DBCC FREEPROCCACHE](../t-sql/database-console-commands/dbcc-freeproccache-transact-sql.md).

### <a name="recompiling-execution-plans"></a>Ricompilazione dei piani di esecuzione

Alcune modifiche in un database possono provocare un piano di esecuzione inefficiente o non valido, in base al nuovo stato del database. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] rileva le modifiche che rendono un piano di esecuzione non valido e contrassegna il piano come tale. Per la successiva connessione che esegue la query, pertanto, è necessaria la ricompilazione di un nuovo piano. Le condizioni che invalidano un piano includono le seguenti: 

* Modifiche apportate a una tabella o a una vista a cui fa riferimento la query (`ALTER TABLE` e `ALTER VIEW`).
* Modifiche apportate a una singola procedura, che elimina dalla cache tutti i piani relativi a questa procedura (`ALTER PROCEDURE`).
* Modifiche agli indici utilizzati dal piano di esecuzione.
* Aggiornamenti ai dati statistici usati dal piano di esecuzione, generati in modo esplicito da un'istruzione, ad esempio `UPDATE STATISTICS`, o automaticamente.
* Eliminazione di un indice utilizzato dal piano di esecuzione.
* Chiamata esplicita a `sp_recompile`.
* Grande quantità di modifiche alle chiavi, generate dalle istruzioni `INSERT` o `DELETE` eseguite da altri utenti che modificano una tabella a cui fa riferimento la query.
* Nel caso di tabelle con trigger, aumento significativo del numero di righe della tabella inserite o eliminate.
* Esecuzione di una stored procedure usando l'opzione `WITH RECOMPILE` .

La maggior parte delle ricompilazioni è necessaria per garantire la correttezza dell'istruzione o per ottenere piani di esecuzione della query potenzialmente più veloci.

In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2000 ogni volta che un'istruzione di un batch provoca la ricompilazione, viene ricompilato l'intero batch, indipendentemente dal fatto che sia stato inviato tramite una stored procedure, un trigger, un batch ad hoc o un'istruzione preparata. A partire da [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], viene ricompilata solo l'istruzione all'interno del batch che ha provocato la ricompilazione. A causa di questa differenza, i conteggi delle ricompilazioni in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2000 e versioni successive non possono essere confrontati. In [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] e versioni successive sono inoltre presenti più tipi di ricompilazioni, in quanto il set di caratteristiche è più ampio.

La ricompilazione a livello di istruzione consente di migliorare le prestazioni in quanto, nella maggior parte dei casi, le ricompilazioni e gli svantaggi associati, in termini di blocchi e tempo della CPU, sono dovuti a un piccolo numero di istruzioni. Questi svantaggi possono pertanto venire evitati per le altre istruzioni nel batch che non devono essere ricompilate.

L'evento esteso (XEvent) `sql_statement_recompile` indica le ricompilazioni a livello di istruzione. Questo XEvent viene generato quando qualsiasi tipo di batch richiede una ricompilazione a livello di istruzione, inclusi trigger, stored procedure, batch ad hoc e query. I batch possono essere inviati tramite varie interfacce, inclusi sp_executesql, SQL dinamico, metodi Prepare e metodi Execute.
La colonna `recompile_cause` dell'XEvent `sql_statement_recompile` contiene un codice integer che indica il motivo della ricompilazione. La tabella seguente include i motivi possibili:

|||
|----|----|  
|Schema modificato|Statistiche modificate|  
|Compilazione posticipata|Opzione SET modificata|  
|Tabella temporanea modificata|Set di righe remoto modificato|  
|Autorizzazione`FOR BROWSE` modificata|Ambiente di notifica query modificato|  
|Vista partizionata modificata|Opzioni cursore modificate|  
|`OPTION (RECOMPILE)` richiesta.|Piano con parametri scaricato|  
|Piano che influisce sulla versione del database modificato|Criteri di uso forzato del piano dell'archivio query modificati|  
|Uso forzato del piano dell'archivio query non riuscito|Piano mancante nell'archivio query|

> [!NOTE]
> Nelle versioni di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in cui non sono disponibili xEvent, è possibile usare l'evento di traccia [SP:Recompile](../relational-databases/event-classes/sp-recompile-event-class.md) di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Profiler per lo stesso scopo, ovvero segnalare le ricompilazioni a livello di istruzione.
> Anche l'evento di traccia [SQL:StmtRecompile](../relational-databases/event-classes/sql-stmtrecompile-event-class.md) segnala le ricompilazioni a livello di istruzione e questo evento di traccia può essere usato anche per tenere traccia delle ricompilazioni ed eseguirne il debug. Mentre SP:Recompile viene generato solo per stored procedure e trigger, SQL:StmtRecompile viene generato per stored procedure, trigger, batch ad hoc, batch eseguiti tramite `sp_executesql`sp_executesql, query preparate e SQL dinamico.
> La colonna *EventSubClass* di SP:Recompile e SQL:StmtRecompile contiene un codice integer che indica il motivo della ricompilazione. I codici sono descritti [qui](../relational-databases/event-classes/sql-stmtrecompile-event-class.md).

> [!NOTE]
> Quando l'opzione di database `AUTO_UPDATE_STATISTICS` è impostata su `ON`, le query vengono ricompilate quando sono indirizzate a tabelle o viste indicizzate le cui statistiche sono state aggiornate o le cui cardinalità sono state modificate in modo significativo dall'ultima esecuzione. Questo comportamento si applica alle tabelle standard definite dall'utente, alle tabelle temporanee e alle tabelle inserite ed eliminate, create dai trigger DML. Se le prestazioni delle query sono influenzate da un numero eccessivo di ricompilazioni, è possibile modificare l'impostazione su `OFF`. Quando l'opzione `AUTO_UPDATE_STATISTICS` del database è impostata su `OFF`, non vengono eseguite ricompilazioni in base alle statistiche o alle modifiche delle cardinalità, ad eccezione delle tabelle inserite ed eliminate create dai trigger DML `INSTEAD OF`. Poiché tali tabelle vengono create in tempdb, la ricompilazione delle query che vi accedono dipende dall'impostazione di `AUTO_UPDATE_STATISTICS` in tempdb. Si noti che in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2000, la ricompilazione delle query continua in base alle modifiche delle cardinalità delle tabelle inerite ed eliminate del trigger DML, anche quando l'impostazione è `OFF`.

### <a name="PlanReuse"></a> Parametri e riutilizzo del piano di esecuzione

L'utilizzo dei parametri, inclusi i marcatori di parametro nelle applicazioni ADO, OLE DB e ODBC, può comportare un maggiore riutilizzo dei piani di esecuzione. 

> [!WARNING] 
> L'uso di parametri o marcatori di parametro per includere i valori digitati dagli utenti offre una protezione maggiore rispetto alla concatenazione dei valori in una stringa eseguita usando un metodo API di accesso ai dati, l'istruzione `EXECUTE` o la stored procedure `sp_executesql` .
 
L'unica differenza tra le due istruzioni `SELECT` seguenti è rappresentata dai valori confrontati nella clausola `WHERE` :

```sql
SELECT * 
FROM AdventureWorks2014.Production.Product 
WHERE ProductSubcategoryID = 1;
```

```sql
SELECT * 
FROM AdventureWorks2014.Production.Product 
WHERE ProductSubcategoryID = 4;
```

L'unica differenza tra i piani di esecuzione delle due query è rappresentata dal valore archiviato per il confronto con la colonna `ProductSubcategoryID` . L'obiettivo principale di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] consiste nel riconoscere sempre che le istruzioni generano essenzialmente lo stesso piano e nel riutilizzare i piani, anche se [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] a volte non riesce a eseguire questo rilevamento per istruzioni SQL complesse.

La separazione delle costanti dall'istruzione SQL tramite i parametri consente al motore relazionale di riconoscere i piani duplicati. È possibile utilizzare i parametri come indicato di seguito: 

* In Transact-SQL, usare `sp_executesql`: 

   ```sql
   DECLARE @MyIntParm INT
   SET @MyIntParm = 1
   EXEC sp_executesql
     N'SELECT * 
     FROM AdventureWorks2014.Production.Product 
     WHERE ProductSubcategoryID = @Parm',
     N'@Parm INT',
     @MyIntParm
   ```

   Questo metodo è particolarmente adatto per gli script Transact-SQL, le stored procedure o i trigger che generano istruzioni SQL in modo dinamico. 

* ADO, OLE DB e ODBC utilizzano i marcatori di parametro. I marcatori di parametro sono punti interrogativi (?) che sostituiscono una costante in un'istruzione SQL e sono associati a una variabile di programma. In un'applicazione ODBC, ad esempio, verrebbero eseguite le operazioni seguenti: 

   * Usare `SQLBindParameter` per associare una variabile integer al primo marcatore di parametro di un'istruzione SQL.
   * Inserire il valore intero nella variabile.
   * Eseguire l'istruzione specificando il marcatore di parametro (?): 

   ```
   SQLExecDirect(hstmt, 
     "SELECT * 
     FROM AdventureWorks2014.Production.Product 
     WHERE ProductSubcategoryID = ?",
     SQL_NTS);
   ```

   Il provider OLE DB di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client e il driver ODBC di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client inclusi in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] usano `sp_executesql` per inviare istruzioni a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] quando nelle applicazioni vengono usati marcatori di parametro. 

* Progettare stored procedure, che utilizzano parametri per schema.

Se non si compilano parametri in modo esplicito nella progettazione dell'applicazione, è anche possibile basarsi su [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Query Optimizer per parametrizzare automaticamente query specifiche usando il funzionamento predefinito di parametrizzazione semplice. In alternativa, è possibile forzare Query Optimizer affinché esegua la parametrizzazione di tutte le query nel database impostando l'opzione `PARAMETERIZATION` dell'istruzione `ALTER DATABASE` su `FORCED`.

Quando viene attivata la parametrizzazione forzata, la parametrizzazione semplice può essere comunque eseguita. La query seguente, ad esempio, non può essere parametrizzata in base alle regole di parametrizzazione forzata:

```sql
SELECT * FROM Person.Address
WHERE AddressID = 1 + 2;
```

La query può tuttavia essere parametrizzata in base alle regole di parametrizzazione semplice. Quando un tentativo di parametrizzazione forzata ha esito negativo, viene successivamente tentata la parametrizzazione semplice.

### <a name="SimpleParam"></a> Parametrizzazione semplice

In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] l'uso di parametri o di marcatori di parametro nelle istruzioni di Transact-SQL consente di aumentare la capacità del motore relazionale di trovare una corrispondenza tra le nuove istruzioni SQL e i piani di esecuzione esistenti compilati in precedenza.

> [!WARNING] 
> L'uso di parametri o marcatori di parametro per includere i valori digitati dagli utenti offre una protezione maggiore rispetto alla concatenazione dei valori in una stringa eseguita usando un metodo API di accesso ai dati, l'istruzione `EXECUTE` o la stored procedure `sp_executesql` .

Se un'istruzione SQL viene eseguita senza parametri, in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] l'istruzione viene parametrizzata a livello interno per aumentare la possibilità di trovare una corrispondenza con un piano di esecuzione esistente. Questo processo viene definito parametrizzazione semplice. In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2000 il processo è definito parametrizzazione automatica.

Si consideri l'istruzione seguente:

```sql
SELECT * FROM AdventureWorks2014.Production.Product 
WHERE ProductSubcategoryID = 1;
```

Il valore 1 alla fine dell'istruzione può essere specificato come parametro. Tramite il motore relazionale compilato il piano di esecuzione per questo batch come se fosse stato specificato un parametro al posto del valore 1. Grazie a questa semplice parametrizzazione, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] riconosce che le due istruzioni seguenti generano essenzialmente lo stesso piano di esecuzione e il primo piano viene riutilizzato per la seconda istruzione:

```sql
SELECT * FROM AdventureWorks2014.Production.Product 
WHERE ProductSubcategoryID = 1;
```
```sql
SELECT * FROM AdventureWorks2014.Production.Product 
WHERE ProductSubcategoryID = 4;
```

Durante l'elaborazione di istruzioni SQL complesse, è possibile che il motore relazionale incontri difficoltà nel determinare le espressioni che è possibile parametrizzare. Per aumentare la capacità del motore relazionale di associare le istruzioni SQL complesse ai piani di esecuzione esistenti e inutilizzati, è necessario specificare in modo esplicito i parametri tramite sp_executesql o i marcatori di parametro. 

> [!NOTE]
> Quando vengono usati gli operatori aritmetici +, -, \*, / o % per eseguire una conversione implicita o esplicita di valori costanti int, smallint, tinyint o bigint in tipi di dati float, real, decimal o numeric, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] applica regole specifiche per calcolare il tipo e la precisione dei risultati dell'espressione. Queste regole, tuttavia, variano in base al fatto che la query includa o meno parametri. Espressioni simili nelle query possono pertanto in alcuni casi generare risultati diversi.

In base al comportamento predefinito della parametrizzazione semplice, in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] viene parametrizzato un numero relativamente piccolo di query. È tuttavia possibile fare in modo che tutte le query in un database vengano parametrizzate, rispettando determinate limitazioni, impostando l'opzione `PARAMETERIZATION` del comando `ALTER DATABASE` su `FORCED`. In questo modo, è possibile migliorare le prestazioni dei database in cui viene eseguito un numero elevato di query simultanee riducendo la frequenza di compilazione delle query.

In alternativa, è possibile specificare la parametrizzazione di una singola query e di tutte le altre con sintassi equivalente ma che differiscono solo per i valori dei parametri. 

### <a name="ForcedParam"></a> Parametrizzazione forzata

È possibile ignorare il comportamento predefinito di parametrizzazione semplice di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] specificando la parametrizzazione di tutte le istruzioni `SELECT`, `INSERT`, `UPDATE` e `DELETE` di un database in base a limiti specifici. La parametrizzazione forzata viene attivata impostando l'opzione `PARAMETERIZATION` su `FORCED` nell'istruzione `ALTER DATABASE` . La parametrizzazione forzata può offrire un miglioramento delle prestazioni di alcuni database riducendo la frequenza delle operazioni di compilazione e ricompilazione delle query. I database che possono essere soggetti a un miglioramento delle prestazione grazie alla parametrizzazione forzata sono in genere quelli che ricevono volumi elevati di query simultanee da origini quali le applicazioni POS.

Quando l'opzione `PARAMETERIZATION` è impostata su `FORCED`, qualsiasi valore letterale visualizzato in un'istruzione `SELECT`, `INSERT`, `UPDATE`o `DELETE` , inviato in qualsiasi forma, viene convertito in un parametro durante la compilazione delle query. Le eccezioni consistono in valori letterali presenti nei costrutti di query seguenti: 

* Istruzioni`INSERT...EXECUTE` .
* Istruzioni all'interno del corpo di stored procedure, trigger o funzioni definite dall'utente. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] riutilizza già piani di query per tali routine.
* Istruzioni preparate già parametrizzate nell'applicazione sul lato client.
* Istruzioni contenenti chiamate al metodo XQuery, in cui il metodo appare in un contesto in cui i relativi argomenti verrebbero in genere parametrizzati, ad esempio una clausola `WHERE` . Se il metodo appare in un contesto in cui i relativi argomenti non verrebbero parametrizzati, il resto dell'istruzione viene parametrizzato.
* Istruzioni all'interno di un cursore Transact-SQL. Le istruzioni`SELECT` all'interno dei cursori API vengono parametrizzate.
* Costrutti di query deprecati.
* Qualsiasi istruzione che viene eseguita nel contesto di `ANSI_PADDING` o `ANSI_NULLS` impostata su `OFF`.
* Istruzioni contenenti oltre 2.097 valori letterali idonei per la parametrizzazione.
* Istruzioni che fanno riferimento a variabili, ad esempio `WHERE T.col2 >= @bb`.
* Istruzioni contenenti l'hint per la query `RECOMPILE` .
* Istruzioni contenenti una clausola `COMPUTE` .
* Istruzioni contenenti una clausola `WHERE CURRENT OF` .

Le clausole di query seguenti sono inoltre senza parametri. Si noti che in questi casi soltanto le clausole sono senza parametri. Altre clausole all'interno della stessa query potrebbero essere idonee per la parametrizzazione forzata.

* <select_list> di qualsiasi istruzione `SELECT`. Ciò include elenchi `SELECT` delle sottoquery ed elenchi `SELECT` all'interno delle istruzioni `INSERT`.
* Istruzioni `SELECT` delle sottoquery incluse in un'istruzione `IF` .
* Clausole `TOP`, `TABLESAMPLE`, `HAVING`, `GROUP BY`, `ORDER BY`, `OUTPUT...INTO`o `FOR XM`L di una query.
* Argomenti, diretti o sottoespressioni, a `OPENROWSET`, `OPENQUERY`, `OPENDATASOURCE`, `OPENXML`o qualsiasi operatore `FULLTEXT` .
* Argomenti pattern ed escape_character di una clausola `LIKE` .
* Argomento style di una clausola `CONVERT` .
* Costante integer all'interno di una clausola `IDENTITY` .
* Costanti specificate utilizzando la sintassi delle estensioni ODBC.
* Espressioni per le quali è possibile eseguire l'elaborazione delle costanti in fase di compilazione che rappresentano argomenti degli operatori +, -, \*, / e %. Quando viene valutata l'idoneità per la parametrizzazione forzata, in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] un'espressione viene considerata come idonea per l'elaborazione delle costanti in fase di compilazione quando si verificano le condizioni seguenti:  
  * Nell'espressione non è inclusa alcuna colonna, variabile o subquery.  
  * L'espressione contiene una clausola `CASE` .  
* Argomenti delle clausole degli hint per le query. Sono inclusi l'argomento `number_of_rows` dell'hint per la query `FAST` , l'argomento `number_of_processors` dell'hint per la query `MAXDOP` e l'argomento del numero dell'hint della query `MAXRECURSION` .

La parametrizzazione viene eseguita a livello di singole istruzioni Transact-SQL. In altri termini, vengono parametrizzate le singole istruzioni presenti in un batch. In seguito alla compilazione, una query con parametri viene eseguita nel contesto del batch in cui è stata inviata originariamente. Se un piano di esecuzione per una query viene memorizzato nella cache, è possibile determinare se è stata eseguita la parametrizzazione della query facendo riferimento alla colonna sql della vista a gestione dinamica sys.syscacheobjects. Se è stata eseguita la parametrizzazione di una query, i nomi e i tipi di dati dei parametri precedono il testo del batch inviato nella colonna, ad esempio \@1 tinyint.

> [!NOTE]
> I nomi dei parametri sono arbitrari. Gli utenti o le applicazioni non devono basarsi su un ordine di denominazione specifico. È inoltre possibile che nomi dei parametri, scelta dei valori letterali con parametri e spaziatura nel testo con parametri cambino tra le versioni di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e gli aggiornamenti dei Service Pack.

#### <a name="data-types-of-parameters"></a>Tipi di dati dei parametri

Quando in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] vengono parametrizzati valori letterali, i parametri vengono convertiti nei tipi di dati seguenti:

* I valori letterali interi le cui dimensioni altrimenti si adatterebbero al tipo di dati int vengono parametrizzati in int. I valori letterali interi di dimensioni maggiori inclusi in predicati che comportano qualsiasi operatore di confronto, come <, \<=, =, !=, >, >=, , !\<, !>, <>, `ALL`, `ANY`, `SOME`, `BETWEEN` e `IN`, vengono parametrizzati in numeric(38,0). I valori letterali di dimensioni maggiori non inclusi in predicati che comportano operatori di confronto vengono parametrizzati in numeric, la cui precisione è tale da supportarne le dimensioni e il cui valore di scala è 0.
* I valori letterali numerici a virgola fissa inclusi in predicati che comportano operatori di confronto vengono parametrizzati in numeric con precisione 38 e valore di scala tale da supportarne le dimensioni. I valori letterali numerici a virgola fissa non inclusi in predicati che comportano operatori di confronto vengono parametrizzati in numeric con precisione e valore di scala tali da supportarne le dimensioni.
* I valori letterali numerici a virgola mobile vengono parametrizzati in float(53).
* I valori letterali stringa vengono parametrizzati in varchar(8000) se il valore letterale non supera gli 8000 caratteri e in varchar(max) se è maggiore di 8000 caratteri.
* I valori letterali stringa vengono parametrizzati in nvarchar(4000) se il valore letterale non supera i 4000 caratteri e in nvarchar(max) se è maggiore di 4000 caratteri.
* I valori letterali binari vengono parametrizzati in varbinary(8000) se il valore letterale non supera gli 8000 byte. Se il valore letterale è maggiore di 8000 byte, viene convertito in varbinary(max).
* I valori letterali di tipo money vengono parametrizzati in money.

#### <a name="ForcedParamGuide"></a> Linee guida per l'utilizzo della parametrizzazione forzata

Quando si desidera impostare l'opzione `PARAMETERIZATION` su FORCED, considerare gli aspetti seguenti:

* Tramite la parametrizzazione forzata, in pratica, le costanti letterali incluse in una query vengono modificate in parametri durante la compilazione di una query. È pertanto possibile che in Query Optimizer vengano scelti piani non ottimali per le query. In particolare, è meno probabile che Query Optimizer associ la query a una vista indicizzata o a un indice in una colonna calcolata. Potrebbero inoltre essere scelti piani non ottimali per le query formulate nelle tabelle partizionate e nelle viste partizionate distribuite. Non utilizzare la parametrizzazione forzata negli ambienti basati in modo significativo su viste indicizzate e indici in colonne calcolate. In generale l'opzione `PARAMETERIZATION FORCED` deve essere usata solo da amministratori di database esperti dopo avere determinato che le prestazioni non subiranno alcun impatto negativo.
* Le query distribuite che fanno riferimento a più di un database sono idonee per la parametrizzazione forzata a condizione che l'opzione `PARAMETERIZATION` sia impostata su `FORCED` nel database nel cui contesto viene eseguita la query.
* L'impostazione dell'opzione `PARAMETERIZATION` su `FORCED` consente di scaricare tutti i piani di query dalla cache dei piani del database, ad eccezione di quelli di cui è in corso la compilazione, la ricompilazione o l'esecuzione. I piani per le query di cui è in corso la compilazione o l'esecuzione durante la modifica dell'impostazione verranno parametrizzati alla successiva esecuzione della query.
* L'impostazione dell'opzione `PARAMETERIZATION` è un'operazione online che richiede che non vi sia alcun blocco esclusivo a livello del database.
* L'impostazione corrente dell'opzione `PARAMETERIZATION` viene mantenuta quando un database viene ricollegato o ripristinato.

È possibile ignorare il comportamento della parametrizzazione forzata specificando che su una singola query, e su qualsiasi altra query sintatticamente equivalente ma che differisca solo nei valori dei parametri, venga eseguita la parametrizzazione semplice. Viceversa è possibile specificare che la parametrizzazione forzata venga tentata solo su un set di query sintatticamente equivalenti, anche se disabilitata nel database. A tale scopo, vengono usate le[guide di piano](../relational-databases/performance/plan-guides.md) .

> [!NOTE]
> Quando l'opzione `PARAMETERIZATION` è impostata su `FORCED`, il report dei messaggi di errore potrebbe presentare differenze rispetto a quando l'opzione `PARAMETERIZATION` è impostata su `SIMPLE`: questa impostazione potrebbe comportare la segnalazione di più messaggi di errore nei casi in cui nella parametrizzazione semplice sarebbe stato segnalato un numero di messaggi di errore inferiore e i numeri di riga nei quali si sono verificati gli errori potrebbero non essere segnalati correttamente.

### <a name="preparing-sql-statements"></a>Preparazione delle istruzioni SQL

Il motore relazionale di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] offre supporto completo per la preparazione di istruzioni SQL prima della relativa esecuzione. Se in un'applicazione è necessario eseguire più volte un'istruzione SQL, è possibile utilizzare l'API di database per: 

* Preparare l'istruzione una sola volta. L'istruzione SQL viene compilata in un piano di esecuzione.
* Eseguire il piano di esecuzione precompilato ogni volta che è necessario eseguire l'istruzione. In questo modo, si evita di ricompilare l'istruzione SQL a ogni esecuzione dopo la prima volta.   
  La preparazione e l'esecuzione delle istruzioni è controllata dalle funzioni e dai metodi dell'API. Non è inclusa nel linguaggio Transact-SQL. Il modello di preparazione/esecuzione per l'esecuzione di istruzioni SQL è supportato dal Provider OLE DB Native Client di e [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e dal driver ODBC Native Client di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. A una richiesta di preparazione, il provider o il driver invia l'istruzione a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] con una richiesta di preparazione dell'istruzione. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] compila un piano di esecuzione e restituisce un handle del piano al provider o al driver. Alla richiesta di esecuzione, il provider o il driver invia al server una richiesta di esecuzione del piano associato all'handle. 

Le istruzioni preparate non possono essere utilizzate per creare oggetti temporanei in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Nelle istruzioni preparate, infatti, non è consentito fare riferimento a stored procedure di sistema che creano oggetti temporanei, ad esempio tabelle temporanee. Tali procedure devono essere eseguite in modo diretto.

L'utilizzo eccessivo del modello di preparazione/esecuzione può determinare un peggioramento delle prestazioni. Se un'istruzione viene eseguita una sola volta, è sufficiente l'esecuzione diretta, che richiede un solo ciclo di andata e ritorno in rete per il server. La preparazione e l'esecuzione di un'istruzione SQL che viene eseguita una sola volta richiedono un ciclo di andata e ritorno in rete aggiuntivo (uno per preparare l'istruzione e uno per eseguirla).

È possibile preparare un'istruzione in modo più efficiente utilizzando i marcatori di parametro. Si supponga, ad esempio, che a un'applicazione venga richiesto occasionalmente di recuperare informazioni sui prodotti dal database di esempio `AdventureWorks` . L'applicazione può eseguire questa operazione in due modi diversi. 

L'applicazione può innanzitutto eseguire una query distinta per ogni prodotto richiesto:

```sql
SELECT * FROM AdventureWorks2014.Production.Product
WHERE ProductID = 63;
```

Altrimenti, l'applicazione può eseguire le operazioni seguenti: 

1. Preparare un'istruzione contenente un marcatore di parametro (?):  
   ```sql
   SELECT * FROM AdventureWorks2014.Production.Product  
   WHERE ProductID = ?;
   ```
2. Associare una variabile di programma al marcatore di parametro.
3. A ogni richiesta di informazioni sul prodotto, inserire nella variabile associata il valore di chiave ed eseguire l'istruzione.

Il secondo metodo è più efficiente se l'istruzione viene eseguita più di tre volte.

In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], il modello di preparazione/esecuzione non presenta alcun vantaggio significativo per le prestazioni rispetto all'esecuzione diretta, a causa della modalità in cui [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] riutilizza i piani di esecuzione. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ha algoritmi efficienti per la corrispondenza di istruzioni SQL correnti con i piani di esecuzione generati per esecuzioni precedenti della stessa istruzione SQL. Se un'applicazione esegue più volte un'istruzione SQL con marcatori di parametro, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] riutilizzerà il piano di esecuzione della prima esecuzione per la seconda e le successive esecuzioni, a meno che il piano non venga rimosso dalla cache dei piani. Il modello di preparazione/esecuzione presenta comunque i vantaggi seguenti: 

* È più conveniente cercare un piano di esecuzione tramite un handle di identificazione che non utilizzare gli algoritmi per trovare una corrispondenza tra un'istruzione SQL e i piani di esecuzione esistenti.
* L'applicazione può controllare il momento della creazione del piano di esecuzione e del suo riutilizzo.
* Il modello di preparazione/esecuzione è utilizzabile con altri database, incluse le versioni precedenti di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

 
### <a name="ParamSniffing"></a> Analisi dei parametri
Il termine "analisi dei parametri" si riferisce a un processo in base al quale [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] individua i valori dei parametri correnti durante la compilazione o ricompilazione e li passa a Query Optimizer in modo che possano essere usati per generare piani di esecuzione di query potenzialmente più efficienti.

I valori dei parametri vengono individuati durante la compilazione o ricompilazione per i seguenti tipi di batch:

-  Stored procedure
-  Query inviate tramite sp_executesql 
-  Query preparate

> [!NOTE]
> Per le query che usano l'hint `RECOMPILE`, vengono individuati sia i valori dei parametri che i valori correnti delle variabili locali. I valori individuati (dei parametri e delle variabili locali) sono quelli esistenti nella posizione all'interno del batch prima dell'istruzione con l'hint `RECOMPILE`. In particolare, per i parametri, non vengono individuati i valori passati con la chiamata del batch.

## <a name="parallel-query-processing"></a>Elaborazione parallela di query

In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] è possibile eseguire query parallele, che consentono di ottimizzare l'esecuzione delle query e le operazioni sugli indici nei computer che dispongono di più microprocessori (CPU). La possibilità di eseguire una query o un'operazione sugli indici in parallelo in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] usando diversi thread di lavoro del sistema operativo assicura maggiore velocità ed efficienza.

Durante l'ottimizzazione delle query, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ricerca le query o le operazioni sugli indici che potrebbero trarre vantaggio dall'esecuzione parallela. Nel piano di esecuzione di tali query [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] inserisce operatori di scambio per preparare la query all'esecuzione parallela. Un operatore di scambio è un operatore del piano di esecuzione della query responsabile della gestione dei processi, della ridistribuzione dei dati e del controllo di flusso. L'operatore di scambio include gli operatori logici `Distribute Streams`, `Repartition Streams`e `Gather Streams` come sottotipi, ognuno dei quali può essere incluso nell'output Showplan del piano di esecuzione parallela di una query. 

Dopo l'inserimento degli operatori di scambio, si ottiene un piano di esecuzione parallela della query. Questo tipo di piano può usare più di un thread di lavoro. In un piano di esecuzione seriale, usato da una query non parallela, l'esecuzione è invece affidata a un solo thread di lavoro. Il numero effettivo di thread di lavoro usati da una query parallela viene determinato al momento dell'inizializzazione del piano di esecuzione della query e dipende dalla complessità del piano e dal grado di parallelismo. Il grado di parallelismo determina il numero massimo di CPU usate, ma non il numero di thread di lavoro usati. Il valore del grado di parallelismo viene impostato a livello del server e può essere modificato usando la stored procedure di sistema sp_configure. Questo valore può essere sostituito per singole istruzioni di query o di indice specificando l'hint per la query `MAXDOP` o l'opzione di indice `MAXDOP` . 

Quando una delle condizioni seguenti è vera, Query Optimizer di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] non usa un piano di esecuzione parallela per una query:

* Il costo dell'esecuzione seriale della query non è sufficientemente elevato da suggerire l'adozione di un piano alternativo di esecuzione parallela. 
* Un piano di esecuzione seriale è considerato più veloce di ogni possibile piano di esecuzione parallela per la query in esame.
* La query contiene operatori scalari o relazionali che non possono essere eseguiti in parallelo. Alcuni operatori possono richiedere l'esecuzione seriale di una sezione della query o dell'intero piano.

### <a name="DOP"></a> Grado di parallelismo

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] rileva automaticamente il grado di parallelismo ottimale per ogni istanza di esecuzione parallela di una query o di operazione DDL sull'indice, utilizzando i criteri seguenti: 

1. Esecuzione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in un computer con più microprocessori o CPU, ad esempio un computer SMP (Symmetric Multiprocessing).  
  Solo i computer con più CPU possono utilizzare le query parallele. 

2. Disponibilità di un numero sufficiente di thread di lavoro.  
  Per l'esecuzione di una query o di un'operazione su un indice è necessario un numero specifico di thread di lavoro. L'esecuzione di un piano parallelo richiede un numero di thread di lavoro maggiore rispetto all'esecuzione di un piano seriale e il numero di thread di lavoro necessari aumenta con il grado di parallelismo. Se non è possibile rispettare i requisiti di thread di lavoro del piano parallelo per un grado di parallelismo specifico, [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] riduce automaticamente il grado di parallelismo o ignora completamente il piano parallelo nel contesto del carico di lavoro specificato ed esegue il piano seriale (un solo thread di lavoro). 

3. Tipo di query o di operazione sull'indice eseguita.  
  Le operazioni di creazione o ricompilazione di un indice o di eliminazione di un indice cluster e le query che utilizzano molte risorse CPU sono candidate ideali per un piano parallelo. Esempi di operazioni di questo tipo sono i join di tabelle di grandi dimensioni, le aggregazioni di ampia portata e gli ordinamenti di set di risultati estesi. Nel caso di query semplici, spesso presenti nelle applicazioni di elaborazione delle transazioni, il coordinamento aggiuntivo necessario per eseguire una query in parallelo viene compensato dal potenziale miglioramento delle prestazioni. Per distinguere le query che possono trarre vantaggio dal parallelismo, [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] confronta il costo stimato per l'esecuzione della query o dell'operazione sull'indice con il valore [cost threshold for parallelism](../database-engine/configure-windows/configure-the-cost-threshold-for-parallelism-server-configuration-option.md). È possibile modificare il valore predefinito di 5 usando [sp_configure](../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) se da un test appropriato risulta che è preferibile usare un valore diverso per il carico di lavoro in esecuzione. 

4. Presenza di un numero sufficiente di righe da elaborare.  
  Se Query Optimizer determina che il numero di righe di un flusso è troppo basso, non introduce gli operatori di scambio per la distribuzione delle righe. Gli operatori vengono pertanto eseguiti in modo seriale, evitando così le situazioni in cui il costo di avvio, distribuzione e coordinamento supera i vantaggi ottenuti tramite l'esecuzione parallela dell'operatore.

5. Disponibilità di statistiche di distribuzione correnti.  
  Se il grado di parallelismo massimo non è disponibile, prima di annullare il piano parallelo vengono considerati i gradi inferiori.  
  Ad esempio, quando si crea un indice cluster in una vista, non è possibile valutare le statistiche di distribuzione perché l'indice cluster non esiste ancora. In questo caso, [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] non può fornire il grado di parallelismo massimo per l'operazione sull'indice. Alcuni operatori, ad esempio quelli relativi all'ordinamento e all'analisi, possono tuttavia trarre vantaggi dall'esecuzione parallela.

> [!NOTE]
> Le operazioni parallele sugli indici sono disponibili solo nelle edizioni Enterprise, Developer ed Evaluation di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].
 
Al momento dell'esecuzione, [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] determina se il carico di lavoro di sistema corrente e i dati di configurazione illustrati in precedenza consentono l'esecuzione parallela. Se l'esecuzione parallela è possibile, [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] determina il numero ottimale di thread di lavoro e suddivide l'esecuzione del piano parallelo tra tali thread di lavoro. Dal momento in cui viene avviata l'esecuzione parallela su più thread di lavoro di una query o di un'operazione sull'indice, viene usato lo stesso numero di thread di lavoro fino al completamento dell'operazione. [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] riesamina il numero ottimale di thread di lavoro ogni volta che viene recuperato un piano di esecuzione dalla cache dei piani. Ad esempio, l'esecuzione di una query può comportare l'uso di un piano seriale, un'esecuzione successiva della stessa query può richiedere un piano parallelo con tre thread di lavoro e una terza esecuzione può richiedere un piano parallelo con quattro thread di lavoro.

In un piano di esecuzione parallela della query, gli operatori insert, update e delete vengono eseguiti in modo seriale. La clausola WHERE di un'istruzione UPDATE o DELETE oppure la parte SELECT di un'istruzione INSERT possono tuttavia essere eseguite in parallelo. Le modifiche apportate ai dati verranno quindi applicate in modo seriale al database.

I cursori statici e gestiti da keyset possono essere popolati tramite piani di esecuzione parallela. La funzionalità dei cursori dinamici può invece essere implementata solo tramite l'esecuzione seriale. Query Optimizer genera sempre un piano di esecuzione seriale per le query che fanno parte di un cursore dinamico.

#### <a name="overriding-degrees-of-parallelism"></a>Sostituzione dei gradi di parallelismo

È possibile usare l'opzione di configurazione del server [max degree of parallelism](../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md) (MAXDOP) ([ALTER DATABASE SCOPED CONFIGURATION](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) in [!INCLUDE[ssSDS_md](../includes/sssds-md.md)]) per limitare il numero di processori da usare per l'esecuzione del piano parallelo. L'opzione Massimo grado di parallelismo può essere ignorata per le singole istruzioni delle query e delle operazioni sugli indici specificando l'hint per le query MAXDOP o l'opzione per gli indici MAXDOP. MAXDOP offre un maggiore controllo sulle singole query e operazioni sugli indici. Ad esempio, è possibile usare questa opzione per aumentare o diminuire il numero di processori dedicati a un'operazione sull'indice online. Ciò consente di bilanciare le risorse utilizzate per un'operazione sull'indice con quelle degli utenti simultanei. 

L'impostazione dell'opzione max degree of parallelism su 0 (impostazione predefinita) consente a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] di usare tutti i processori disponibili fino a un massimo di 64 nell'esecuzione di piani paralleli. Anche se [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] imposta una destinazione di runtime di 64 processori logici quando l'opzione MAXDOP è impostata su 0, è possibile impostare manualmente un valore diverso se necessario. L'impostazione di MAXDOP su 0 per query e indici consente a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] di usare tutti i processori disponibili fino a un massimo di 64 per le query o gli indici specificati nell'esecuzione di piani paralleli. MAXDOP non è un valore imposto per tutte le query parallele, ma piuttosto un valore target provvisorio per tutte le query idonee per il parallelismo. Ciò significa che se ci sono thread di lavoro sufficienti disponibili in fase di esecuzione, una query può essere eseguita con un grado di parallelismo minore rispetto all'opzione di configurazione del server MAXDOP.

Fare riferimento a questo [articolo del supporto tecnico Microsoft](https://support.microsoft.com/help/2806535/recommendations-and-guidelines-for-the-max-degree-of-parallelism-configuration-option-in-sql-server) per informazioni sulle procedure consigliate per la configurazione di MAXDOP.

### <a name="parallel-query-example"></a>Esempio di query parallela

Nella query seguente viene eseguito il conteggio del numero di ordini effettuati nel trimestre con inizio 1 aprile 2000. Per questi ordini, almeno uno degli articoli è stato ricevuto dal cliente successivamente alla data prevista. La query indica il numero totale di tali ordini raggruppati per priorità di ordine e disposti in ordine di priorità crescente. 

Nell'esempio seguente vengono utilizzati nomi di tabelle e colonne fittizi.

```sql
SELECT o_orderpriority, COUNT(*) AS Order_Count
FROM orders
WHERE o_orderdate >= '2000/04/01'
   AND o_orderdate < DATEADD (mm, 3, '2000/04/01')
   AND EXISTS
         (
          SELECT *
            FROM    lineitem
            WHERE l_orderkey = o_orderkey
               AND l_commitdate < l_receiptdate
         )
   GROUP BY o_orderpriority
   ORDER BY o_orderpriority
```

Si supponga che per le tabelle `lineitem` e `orders` vengano definiti gli indici seguenti:

```sql
CREATE INDEX l_order_dates_idx 
   ON lineitem
      (l_orderkey, l_receiptdate, l_commitdate, l_shipdate)

CREATE UNIQUE INDEX o_datkeyopr_idx
   ON ORDERS
      (o_orderdate, o_orderkey, o_custkey, o_orderpriority)
```

Di seguito viene riportato un possibile piano parallelo generato per la query indicata in precedenza:

```
|--Stream Aggregate(GROUP BY:([ORDERS].[o_orderpriority])
                  DEFINE:([Expr1005]=COUNT(*)))
    |--Parallelism(Gather Streams, ORDER BY:
                  ([ORDERS].[o_orderpriority] ASC))
         |--Stream Aggregate(GROUP BY:
                  ([ORDERS].[o_orderpriority])
                  DEFINE:([Expr1005]=Count(*)))
              |--Sort(ORDER BY:([ORDERS].[o_orderpriority] ASC))
                   |--Merge Join(Left Semi Join, MERGE:
                  ([ORDERS].[o_orderkey])=
                        ([LINEITEM].[l_orderkey]),
                  RESIDUAL:([ORDERS].[o_orderkey]=
                        [LINEITEM].[l_orderkey]))
                        |--Sort(ORDER BY:([ORDERS].[o_orderkey] ASC))
                        |    |--Parallelism(Repartition Streams,
                           PARTITION COLUMNS:
                           ([ORDERS].[o_orderkey]))
                        |         |--Index Seek(OBJECT:
                     ([tpcd1G].[dbo].[ORDERS].[O_DATKEYOPR_IDX]),
                     SEEK:([ORDERS].[o_orderdate] >=
                           Apr  1 2000 12:00AM AND
                           [ORDERS].[o_orderdate] <
                           Jul  1 2000 12:00AM) ORDERED)
                        |--Parallelism(Repartition Streams,
                     PARTITION COLUMNS:
                     ([LINEITEM].[l_orderkey]),
                     ORDER BY:([LINEITEM].[l_orderkey] ASC))
                             |--Filter(WHERE:
                           ([LINEITEM].[l_commitdate]<
                           [LINEITEM].[l_receiptdate]))
                                  |--Index Scan(OBJECT:
         ([tpcd1G].[dbo].[LINEITEM].[L_ORDER_DATES_IDX]), ORDERED)
```

Nella figura seguente è illustrato un piano di query eseguito con grado di parallelismo 4 e con un join a due tabelle.

![parallel_plan](../relational-databases/media/parallel-plan.gif)

Il piano parallelo contiene tre operatori di parallelismo. Sia l'operatore Index Seek dell'indice `o_datkey_ptr` che l'operatore Index Scan dell'indice `l_order_dates_idx` vengono eseguiti in parallelo. In questo modo vengono creati diversi flussi esclusivi. Ciò può essere determinato dagli operatori di parallelismo più vicini sopra gli operatori Index Scan e Index Seek, rispettivamente. Entrambi gli operatori eseguono la ripartizione del tipo di scambio, ovvero ridistribuiscono i dati tra i flussi creando nell'output lo stesso numero di flussi presenti nell'input. Questo numero di flussi equivale al grado di parallelismo.

L'operatore di parallelismo sopra l'operatore Index Scan `l_order_dates_idx` esegue la ripartizione dei flussi di input usando il valore di `L_ORDERKEY` come chiave. In questo modo, lo stesso valore di `L_ORDERKEY` viene incluso nello stesso flusso di output. Allo stesso tempo, i flussi di output mantengono l'ordine della colonna `L_ORDERKEY` per soddisfare il requisito di input dell'operatore Merge Join.

L'operatore di parallelismo sopra l'operatore Index Seek esegue la ripartizione dei flussi di input utilizzando il valore di `O_ORDERKEY`. Poiché l'input non viene ordinato nei valori della colonna `O_ORDERKEY` , che rappresenta la colonna di join dell'operatore `Merge Join` , l'operatore Sort tra gli operatori di parallelismo e Merge Join assicura che l'input venga ordinato per l'operatore `Merge Join` nelle colonne di join. Analogamente all'operatore Merge Join, l'operatore `Sort` viene eseguito in parallelo.

L'operatore di parallelismo superiore riunisce i risultati di numerosi flussi in un singolo flusso. Le aggregazioni parziali eseguite dall'operatore Stream Aggregate sottostante all'operatore di parallelismo vengono quindi riunite in un singolo valore `SUM` per ogni valore diverso di `O_ORDERPRIORITY` nell'operatore Stream Aggregate sopra l'operatore di parallelismo. Poiché include due segmenti di scambio con grado di parallelismo 4, questo piano usa otto thread di lavoro.

Per altre informazioni sugli operatori usati in questo esempio, vedere [Guida di riferimento a operatori Showplan logici e fisici](../relational-databases/showplan-logical-and-physical-operators-reference.md).

### <a name="parallel-index-operations"></a>Operazioni parallele sugli indici

I piani di query compilati ai fini della creazione o della ricompilazione di un indice, oppure dell'eliminazione di un indice cluster, consentono in computer con più microprocessori di eseguire operazioni parallele con più thread di lavoro.

> [!NOTE]
> Le operazioni parallele sugli indici sono disponibili solo nell'edizione Enterprise, a partire da [!INCLUDE[ssKatmai](../includes/ssKatmai-md.md)].
 
[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] usa gli stessi algoritmi utilizzati per altre query per determinare il grado di parallelismo, ovvero il numero totale di singoli thread lavoro da eseguire, per le operazioni sugli indici. Il grado massimo di parallelismo per un'operazione sugli indici dipende dal valore impostato per l'opzione di configurazione del server [Massimo grado di parallelismo](../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md) . È possibile ignorare il valore dell'opzione Massimo grado di parallelismo per singole operazioni sull'indice impostando l'opzione per gli indici MAXDOP nelle istruzioni CREATE INDEX, ALTER INDEX, DROP INDEX e ALTER TABLE.

Quando [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] compila un piano di esecuzione dell'indice, il numero di operazioni parallele viene impostato sul valore più basso tra i seguenti: 

* Il numero di microprocessori, o CPU, del computer.
* Il numero specificato per l'opzione di configurazione del server Massimo grado di parallelismo.
* Il numero di CPU che non hanno già superato una determinata soglia di carico di elaborazione per l'esecuzione dei thread di lavoro di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

Ad esempio, in un computer con 8 CPU in cui, tuttavia, l'opzione max degree of parallelism è impostata su 6, per un'operazione sugli indici verranno generati al massimo 6 thread di lavoro paralleli. Se 5 CPU del computer superano la soglia di carico di elaborazione per [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] al momento della compilazione del piano di esecuzione per l'indice, il piano userà solo 3 thread di lavoro paralleli.

Le fasi principali di un'operazione parallela sugli indici includono quanto segue: 

* Un thread di lavoro di coordinamento esegue rapidamente l'analisi casuale della tabella per produrre una stima della distribuzione delle chiavi dell'indice. Il thread di lavoro di coordinamento stabilisce i limiti delle chiavi in base ai quali verrà creato un numero di intervalli di chiavi equivalente al grado di operazioni parallele. Ogni intervallo di chiavi copre un numero di righe simile. Se ad esempio la tabella include 4 milioni di righe e il grado di parallelismo è 4, il thread di lavoro di coordinamento determinerà i valori di chiave che delimitano 4 set di righe che includono 1 milione di righe ciascuno. Se non è possibile stabilire un numero sufficiente di intervalli di chiavi per utilizzare tutte le CPU, il grado di parallelismo viene ridotto di conseguenza.  
* Il thread di lavoro di coordinamento recapita un numero di thread di lavoro pari al grado di operazioni parallele e attende che tali thread di lavoro completino le rispettive operazioni. Ogni thread di lavoro esegue l'analisi della tabella di base usando un filtro che recupera solo le righe con valori di chiave inclusi nell'intervallo assegnato al thread di lavoro. Ogni thread di lavoro compila una struttura di indice per le righe nel rispettivo intervallo di chiavi. Nel caso di indici partizionati ogni thread di lavoro compila un numero specifico di partizioni. Le partizioni non sono condivise tra i thread di lavoro.  
* Quando tutti i thread di lavoro paralleli sono stati completati, il thread di lavoro di coordinamento connette le sottounità dell'indice in un unico indice. Questa fase viene eseguita solo nelle operazioni sugli indici offline.

Singole istruzioni `CREATE TABLE` o `ALTER TABLE` possono avere più vincoli che richiedono la creazione di un indice. Le operazioni di creazione dell'indice vengono eseguite in serie, anche se in un computer con più CPU ogni singola operazione può essere eseguita in parallelo.

## <a name="distributed-query-architecture"></a>Architettura delle query distribuite

Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] supporta due metodi per fare riferimento a origini dati OLE DB eterogenee nelle istruzioni Transact-SQL:

* Nomi di server collegati  
  Per assegnare il nome di un server a un'origine dei dati OLE DB vengono usate le stored procedure di sistema `sp_addlinkedserver` e `sp_addlinkedsrvlogin` . Per fare riferimento agli oggetti di server collegati nelle istruzioni Transact-SQL, è possibile usare nomi in quattro parti. Ad esempio, se si definisce il nome del server collegato `DeptSQLSrvr` per un'altra istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], l'istruzione seguente fa riferimento a una tabella in tale server: 
  
  ```sql
  SELECT JobTitle, HireDate 
  FROM DeptSQLSrvr.AdventureWorks2014.HumanResources.Employee;
  ```

   È anche possibile specificare il nome del server collegato in un'istruzione `OPENQUERY` per aprire un set di righe dall'origine dei dati OLE DB. Successivamente, è possibile inserire i riferimenti a tale set di righe nelle istruzioni Transact-SQL in base alle stesse modalità usate per i riferimenti a una tabella. 

* Nomi di connettore ad hoc  
  Nel caso di un numero limitato di riferimenti a un'origine dei dati, nella funzione `OPENROWSET` o `OPENDATASOURCE` vengono specificate le informazioni necessarie per la connessione al server collegato. In seguito, sarà possibile fare riferimento a tale set di righe nelle istruzioni Transact-SQL in base alle stesse modalità usate per i riferimenti a una tabella: 
  
  ```sql
  SELECT *
  FROM OPENROWSET('Microsoft.Jet.OLEDB.4.0',
        'c:\MSOffice\Access\Samples\Northwind.mdb';'Admin';'';
        Employees);
  ```

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] utilizza OLE DB per la comunicazione tra il motore relazionale e il motore di archiviazione. Il motore relazionale suddivide ogni istruzione Transact-SQL in una serie di operazioni su set di righe OLE DB semplici, aperti dal motore di archiviazione nelle tabelle di base. Pertanto, il motore relazionale può aprire inoltre set di righe OLE DB semplici in qualsiasi origine dei dati OLE DB.  
![oledb_storage](../relational-databases/media/oledb-storage.gif)  
Il motore relazionale utilizza l'API OLE DB per aprire i set di righe nei server collegati, recuperare le righe e gestire le transazioni.

Per ogni origine dei dati OLE DB accessibile come server collegato, è necessario un provider OLE DB nel server che esegue [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. La serie di operazioni Transact-SQL che è possibile usare per un'origine dei dati OLE DB specifica dipende dalle funzionalità del provider OLE DB.

Per ogni istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], i membri del ruolo predefinito del server `sysadmin` possono abilitare o disabilitare l'uso di nomi di connettore ad hoc per un provider OLE DB tramite la proprietà `DisallowAdhocAccess` di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Quando l'accesso ad hoc è disabilitato, qualsiasi utente collegato a tale istanza può eseguire istruzioni SQL contenenti nomi di connettore ad hoc che fanno riferimento a qualsiasi origine dei dati in rete accessibile tramite tale provider OLE DB. Per controllare l'accesso alle origini dei dati, i membri del ruolo `sysadmin` possono disabilitare l'accesso ad hoc per i provider OLE DB corrispondenti, limitando in tal modo l'accesso da parte degli utenti alle sole origini dei dati a cui viene fatto riferimento dai nomi dei server collegati definiti dagli amministratori. Per impostazione predefinita, l'accesso ad hoc è abilitato per il provider OLE DB di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e disabilitato per tutti gli altri provider OLE DB.

Le query distribuite consentono agli utenti di accedere a un'altra origine dati (ad esempio file, origini dati non relazionali come Active Directory e così via) tramite il contesto di sicurezza dell'account di Microsoft Windows usato per l'esecuzione del servizio [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] rappresenta l'account di accesso appropriato nel caso degli account di accesso di Windows, ma non per gli account di accesso di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. In tal modo modo, è possibile che l'utente di una query distribuita acceda a un'altra origine dei dati per cui non dispone delle autorizzazioni necessarie, ma l'account utilizzato per l'esecuzione del servizio [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] dispone di tali autorizzazioni. Per definire gli account di accesso specifici autorizzati per l'accesso al server collegato corrispondente, usare la stored procedure `sp_addlinkedsrvlogin` . Poiché tale controllo non è disponibile per i nomi ad hoc, prestare attenzione quando si attiva l'accesso ad hoc in un provider OLE DB.

Quando possibile, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] esegue il push delle operazioni relazionali quali join, restrizioni, proiezioni, ordinamenti e operazioni su gruppi all'origine dati OLE DB. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] non analizza per impostazione predefinita la tabella di base in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e non esegue operazioni relazionali in autonomia. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] esegue query sul provider OLE DB per determinare il livello di grammatica SQL supportata e, in base a tali informazioni, esegue il push al provider del maggior numero possibile di operazioni relazionali. 

In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] è disponibile un meccanismo in base al quale il provider OLE DB restituisce statistiche che indicano la modalità di distribuzione dei valori di chiave all'interno dell'origine dati OLE DB. In questo modo, Query Optimizer di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] può analizzare in modo più approfondito lo schema dri dati nell'origine dati in base ai requisiti di ogni istruzione SQL, generando con maggiore efficienza piani di esecuzione ottimali. 

## <a name="query-processing-enhancements-on-partitioned-tables-and-indexes"></a>Miglioramenti apportati all'elaborazione di query su tabelle e indici partizionati

In [!INCLUDE[ssKatmai](../includes/ssKatmai-md.md)] sono state migliorate le prestazioni di elaborazione delle query su tabelle partizionate per molti piani paralleli, modificate le modalità di rappresentazione dei piani seriali e paralleli, nonché ottimizzate le informazioni relative al partizionamento fornite nei piani di esecuzione sia nella fase di compilazione che di esecuzione. In questo argomento vengono descritti i miglioramenti apportati, viene spiegato come interpretare i piani di esecuzione delle query relativi a tabelle e indici partizionati e vengono fornite le procedure consigliate per migliorare le prestazioni delle query su oggetti partizionati. 

> [!NOTE]
> Il partizionamento di indici e tabelle è supportato solo nelle edizioni Enterprise, Developer ed Evaluation di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

### <a name="new-partition-aware-seek-operation"></a>Nuova operazione di ricerca con riconoscimento delle partizioni

In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], la rappresentazione interna di una tabella partizionata viene modificata in modo che la tabella sia visibile all'elaboratore di query come indice multicolonna con `PartitionID` come colonna iniziale. `PartitionID` è una colonna calcolata nascosta usata internamente per rappresentare il valore `ID` della partizione che contiene una riga specifica. Ad esempio, si supponga che la tabella T, definita come `T(a, b, c)`, venga partizionata in base alla colonna A e includa un indice cluster nella colonna B. In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] questa tabella partizionata viene considerata internamente come una tabella non partizionata caratterizzata dallo schema `T(PartitionID, a, b, c)` e con un indice cluster sulla chiave composta `(PartitionID, b)`. In questo modo Query Optimizer è in grado di eseguire operazioni di ricerca basate su `PartitionID` su qualsiasi tabella o indice partizionato. 

L'eliminazione della partizione viene ora eseguita durante tale operazione di ricerca.

In addition, the Query Optimizer is extended so that a seek or scan operation with one condition can be done on `PartitionID` (come colonna iniziale logica) e su altre colonne chiave indice e quindi un'operazione di ricerca di secondo livello, con una condizione diversa, su una o più colonne aggiuntive, per ogni valore distinto che soddisfa la qualificazione per l'operazione di ricerca di primo livello. Questa operazione, denominata skip scan consente a Query Optimizer di eseguire un'operazione di ricerca o di analisi basata su un unica condizione per determinare le partizioni a cui eseguire l'accesso e un'operazione Index Scan di secondo livello all'interno di tale operatore per restituire le righe delle partizioni che soddisfano una condizione diversa. Si consideri ad esempio la query seguente.

```sql
SELECT * FROM T WHERE a < 10 and b = 2;
```

Per questo esempio si supponga che la tabella T, definita come `T(a, b, c)`, venga partizionata in base alla colonna A e includa un indice cluster nella colonna B. I limiti delle partizione per la tabella T sono definiti dalla funzione di partizione seguente:

```sql
CREATE PARTITION FUNCTION myRangePF1 (int) AS RANGE LEFT FOR VALUES (3, 7, 10);
```

Per risolvere la query, Query Processor esegue un'operazione di ricerca di primo livello per individuare tutte le partizioni contenenti righe che soddisfano la condizione `T.a < 10`. In tal modo vengono identificate le partizioni a cui effettuare l'accesso. All'interno di ciascuna partizione identificata, viene quindi eseguita una ricerca di secondo livello nell'indice cluster della colonna B per individuare le righe che soddisfano le condizioni `T.b = 2` e `T.a < 10`. 

Nell'illustrazione seguente è riportata una rappresentazione logica dell'operazione di "skip scan". Include la tabella `T` con i dati nelle colonne `a` e `b`. Le partizioni sono numerate da 1 a 4 e i limiti delle partizioni sono contraddistinti da righe verticali tratteggiate. In seguito a un'operazione di ricerca di primo livello eseguita sulle partizioni (non riportata nell'illustrazione) è stato determinato che le partizioni 1, 2 e 3 soddisfano la condizione di ricerca prevista dal partizionamento definito per la tabella e il predicato sulla colonna `a`, ovvero `T.a < 10`. Il percorso attraversato dalla parte di ricerca di secondo livello dell'operazione di skip scan è illustrata dalla linea curva. In pratica, l'operazione di skip scan cerca in ciascuna di queste partizioni le righe che soddisfano la condizione `b = 2`. Il costo totale dell'operazione di skip scan equivale a quello di tre operazioni Index Seek distinte.   

![skip_scan](../relational-databases/media/skip-scan.gif)

### <a name="displaying-partitioning-information-in-query-execution-plans"></a>Visualizzazione di informazioni sul partizionamento nei piani di esecuzione delle query

È possibile esaminare i piani di esecuzione delle query su tabelle e indici partizionati usando le istruzioni `SET` di Transact-SQL `SET SHOWPLAN_XML` o `SET STATISTICS XML` oppure l'output del piano di esecuzione grafico restituito in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Studio. È ad esempio possibile visualizzare il piano di esecuzione della fase di compilazione facendo clic su *Visualizza piano di esecuzione stimato* sulla barra degli strumenti dell'editor di query e il piano della fase di esecuzione facendo clic su *Includi piano di esecuzione effettivo*. 

Questi strumenti consentono di verificare le informazioni seguenti:

* Operazioni come `scans`, `seeks`, `inserts`, `updates`, `merges`e `deletes` che accedono alle tabelle partizionate o agli indici.
* Partizioni a cui viene effettuato l'accesso tramite la query. Ad esempio, il totale delle partizioni e gli intervalli relativi alle partizioni contigue a cui viene effettuato l'accesso sono disponibili nei piani di esecuzione della fase di esecuzione.
* Utilizzo dell'operazione di skip scan in un'operazione di ricerca o analisi per recuperare dati da una o più partizioni.

#### <a name="partition-information-enhancements"></a>Miglioramenti apportati alle informazioni sulle partizioni

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] fornisce informazioni migliorate sul partizionamento per i piani di esecuzione sia della fase di compilazione che della fase di esecuzione. I piani di esecuzione includono ora le informazioni seguenti:

* Un attributo `Partitioned` facoltativo per indicare che su una tabella partizionata viene eseguito un operatore, ad esempio `seek`, `scan`, `insert`, `update`, `merge`o `delete`.  
* Un elemento `SeekPredicateNew` nuovo con un sottoelemento `SeekKeys` che include `PartitionID` come colonna chiave di indice iniziale e condizioni di filtro che specificano ricerche di intervallo su `PartitionID`. La presenza di due sottoelementi `SeekKeys` indica che su `PartitionID` viene usata un'operazione di skip scan.   
* Informazioni di riepilogo che includono il totale delle partizioni a cui viene effettuato l'accesso. Queste informazioni sono disponibili solo nei piani della fase di esecuzione. 

Per illustrare la modalità di visualizzazione di queste informazioni nell'output del piano di esecuzione grafico e nell'output di Showplan XML, considerare la query seguente sulla tabella partizionata `fact_sales`. Questa query implica l'aggiornamento dei dati in due partizioni. 

```sql
UPDATE fact_sales
SET quantity = quantity * 2
WHERE date_id BETWEEN 20080802 AND 20080902;
```

Nella figura seguente sono illustrate le proprietà dell'operatore `Clustered Index Seek` nel piano di esecuzione della fase di compilazione per questa query. Per visualizzare la definizione della tabella `fact_sales` e la definizione della partizione, vedere la sezione "Esempio" in questo argomento.  

![clustered_index_seek](../relational-databases/media/clustered-index-seek.gif)

#### <a name="partitioned-attribute"></a>Attributo Partitioned

Quando su una tabella o un indice partizionato si esegue un operatore quale `Index Seek` , l'attributo `Partitioned` viene incluso sia nel piano della fase di compilazione che in quello della fase di esecuzione ed è impostato su `True` (1). L'attributo non viene visualizzato quando è impostato su `False` (0).

L'attributo `Partitioned` può essere visualizzato negli operatori fisici e logici seguenti:  
* `Table Scan`  
* `Index Scan`  
* `Index Seek`  
* `Insert`  
* `Update`  
* `Delete`  
* `Merge`  

Come illustrato nella figura precedente, questo attributo viene visualizzato nelle proprietà dell'operatore in cui è definito. Nell'output di Showplan XML, questo attributo è indicato come `Partitioned="1"` nel nodo `RelOp` dell'operatore nel quale è definito.

#### <a name="new-seek-predicate"></a>Nuovo predicato Seek

Nell'output di Showplan XML l'elemento `SeekPredicateNew` è visualizzato nell'operatore nel quale è definito. Può contenere fino a due occorrenze del sottoelemento `SeekKeys` . Il primo elemento `SeekKeys` specifica l'operazione di ricerca di primo livello a livello di ID della partizione dell'indice logico. Tale ricerca consente di determinare le partizioni a cui è necessario accedere per soddisfare le condizioni della query. Il secondo elemento `SeekKeys` specifica la parte della ricerca di secondo livello dell'operazione di skip scan che viene eseguita all'interno di ciascuna partizione identificata nella ricerca di primo livello. 

#### <a name="partition-summary-information"></a>Informazioni di riepilogo sulle partizioni

Nei piani di esecuzione della fase di esecuzione le informazioni di riepilogo sulle partizioni includono il totale delle partizioni e l'identità delle partizioni effettive a cui viene effettuato l'accesso. È possibile utilizzare queste informazioni per verificare che le partizioni a cui viene effettuato l'accesso tramite la query sono corrette e che tutte le altre partizioni non vengono considerate.

Vengono fornite le informazioni seguenti: `Actual Partition Count`e `Partitions Accessed`. 

`Actual Partition Count` corrisponde al numero totale di partizioni a cui si accede tramite la query.

Nell'output di Showplan XML`Partitions Accessed`corrisponde alle informazioni di riepilogo sulle partizioni che vengono visualizzate nel nuovo elemento `RuntimePartitionSummary` del nodo `RelOp` dell'operatore nel quale è definito. Nell'esempio seguente è illustrato il contenuto dell'elemento `RuntimePartitionSummary` , in cui è indicato che viene eseguito l'accesso a due partizioni totali, ovvero la 2 e la 3.
```
<RunTimePartitionSummary>

    <PartitionsAccessed PartitionCount="2" >

        <PartitionRange Start="2" End="3" />

    </PartitionsAccessed>

</RunTimePartitionSummary>
```

#### <a name="displaying-partition-information-by-using-other-showplan-methods"></a>Visualizzazione delle informazioni sulle partizioni utilizzando altri metodi di Showplan

I metodi `SHOWPLAN_ALL`, `SHOWPLAN_TEXT`e `STATISTICS PROFILE` di Showplan non restituiscono le informazioni sulle partizioni descritte in questo argomento, con un'unica eccezione illustrata di seguito. In quanto incluse nel predicato `SEEK` , le partizioni a cui eseguire l'accesso sono identificate da un predicato di intervallo nella colonna calcolata che rappresenta l'ID di partizione. L'esempio seguente mostra il predicato `SEEK` per un operatore `Clustered Index Seek` . Viene effettuato l'accesso alle partizioni 2 e 3 e l'operatore di ricerca applica il filtro sulle righe che soddisfano la condizione `date_id BETWEEN 20080802 AND 20080902`.
```
|--Clustered Index Seek(OBJECT:([db_sales_test].[dbo].[fact_sales].[ci]), 

        SEEK:([PtnId1000] >= (2) AND [PtnId1000] \<= (3) 

                AND [db_sales_test].[dbo].[fact_sales].[date_id] >= (20080802) 

                AND [db_sales_test].[dbo].[fact_sales].[date_id] <= (20080902)) 

                ORDERED FORWARD)
```

#### <a name="interpreting-execution-plans-for-partitioned-heaps"></a>Interpretazione dei piani di esecuzione per heap partizionati

Un heap partizionato viene considerato come un indice logico sull'ID di partizione. In un piano di esecuzione l'eliminazione di partizioni in un heap partizionato viene rappresentata come un operatore `Table Scan` con un predicato `SEEK` sull'ID di partizione. Nell'esempio seguente sono illustrate le informazioni di Showplan fornite:
```
|-- Table Scan (OBJECT: ([db].[dbo].[T]), SEEK: ([PtnId1001]=[Expr1011]) ORDERED FORWARD)
```

#### <a name="interpreting-execution-plans-for-collocated-joins"></a>Interpretazione dei piani di esecuzione per join collocati

La collocazione dei join può verificarsi quando due tabelle vengono partizionate utilizzando una funzione di partizionamento identica o equivalente e le colonne di partizionamento di entrambi lati del join sono specificate nella condizione di join della query. Query Optimizer può generare un piano in cui le partizioni di ogni tabella con ID di partizione uguali sono unite in join separatamente. I join collocati possono risultare più rapidi di quelli non collocati perché possono richiedere una minor quantità di memoria e tempi di elaborazione inferiori. Query Optimizer sceglie un piano non collocato o un piano collocato sulla base delle stime dei costi.

In un piano collocato il join `Nested Loops` legge una o più partizioni di tabelle o indici unite in join dal lato interno. I numeri all'interno degli operatori `Constant Scan` rappresentano i numeri della partizione. 

Quando per le tabelle o gli indici partizionati si generano piani paralleli per join collocati, viene visualizzato un operatore Parallelism tra gli operatori di join `Constant Scan` e `Nested Loops` . In questo caso, ognuno dei thread di lavoro sul lato esterno del join legge ed elabora una partizione diversa. 

Nella figura seguente viene illustrato un piano di query parallele per un join collocato.   
![colocated_join](../relational-databases/media/colocated-join.gif)


#### <a name="parallel-query-execution-strategy-for-partitioned-objects"></a>Strategia di esecuzione delle query parallele per oggetti partizionati

Query Processor utilizza una strategia di esecuzione parallela per query che eseguono la selezione da oggetti partizionati. Come parte della strategia di esecuzione, Query Processor determina le partizioni della tabella necessarie per eseguire la query e la proporzione di thread di lavoro da allocare a ogni partizione. Nella maggior parte dei casi, Query Processor alloca un numero di thread di lavoro uguale o quasi uguale a ogni partizione, quindi esegue la query in parallelo tra le partizioni. Nei paragrafi seguenti viene descritta più dettagliatamente l'allocazione dei thread di lavoro.  

![thread di lavoro1](../relational-databases/media/thread1.gif)

Se il numero di thread di lavoro è minore di quello delle partizioni, Query Processor assegna ogni thread di lavoro a una partizione diversa, lasciando inizialmente una o più partizioni senza un thread di lavoro assegnato. Quando termina l'esecuzione di un thread di lavoro in una partizione, Query Processor assegna tale thread alla partizione successiva finché non viene assegnato un singolo thread di lavoro a ogni partizione. Questo è l'unico caso in cui Query Processor rialloca i thread di lavoro ad altre partizioni.  
Mostra il thread di lavoro riassegnato al termine dell'esecuzione. Se il numero di thread di lavoro è uguale a quello delle partizioni, Query Processor assegna un thread di lavoro a ogni partizione. Quando un thread di lavoro termina, non viene riallocato ad altre partizioni.  

![thread di lavoro2](../relational-databases/media/thread2.gif)  

Se il numero di thread di lavoro è maggiore di quello delle partizioni, Query Processor alloca un numero uguale di thread di lavoro a ogni partizione. Se il numero di thread di lavoro non è un multiplo esatto del numero di partizioni, Query Processor alloca un thread di lavoro aggiuntivo ad alcune partizioni per usare tutti i thread di lavoro disponibili. Si noti che se la partizione è unica, tutti i thread di lavoro verranno assegnati a tale partizione. Nel diagramma seguente sono presenti quattro partizioni e 14 thread di lavoro. Ogni partizione dispone di 3 thread di lavoro assegnati e due partizioni dispongono di un thread di lavoro aggiuntivo, per un totale di 14 thread di lavoro assegnati. Quando un thread di lavoro termina, non viene riassegnato ad altre partizioni.  

![thread di lavoro3](../relational-databases/media/thread3.gif)  

Sebbene negli esempi precedenti venga suggerito un modo semplice per allocare i thread di lavoro, la strategia effettiva è più complessa e tiene conto di altre variabili che possono presentarsi durante l'esecuzione di query. Ad esempio, se la tabella è partizionata e dispone di un indice cluster nella colonna A e se in una query è presente la clausola del predicato `WHERE A IN (13, 17, 25)`, Query Processor allocherà uno o più thread di lavoro a ciascuno dei tre valori di ricerca (A=13, A=17 e A=25) anziché eseguire l'allocazione a ogni partizione della tabella. È necessario solo eseguire la query nelle partizioni che contengono questi valori e, se tutti i predicati SEEK si trovano nella stessa partizione della tabella, tutti i thread di lavoro verranno assegnati alla partizione specifica.

Per illustrare un altro esempio, si supponga che la tabella dispone di quattro partizioni nella colonna A con punti limite (10, 20, 30), un indice nella colonna B e che la query include una clausola `WHERE B IN (50, 100, 150)`del predicato. Dal momento che partizioni della tabella sono basate sui valori di A, i valori di B possono trovarsi in qualsiasi partizione della tabella. Di conseguenza Query Processor ricercherà ciascuno dei tre valori di B (50, 100, 150) in ognuna delle quattro partizioni della tabella e assegnerà proporzionatamente i thread di lavoro in modo da eseguire ciascuna delle 12 analisi della query in parallelo.

|Partizioni della tabella basate sulla colonna A |Ricerca della colonna B in ogni partizione della tabella |
|----|----|
|Partizione della tabella 1: A < 10   |B=50, B=100, B=150 |
|Partizione della tabella 2: A >= 10 AND A < 20   |B=50, B=100, B=150 |
|Partizione della tabella 3: A >= 20 AND A < 30   |B=50, B=100, B=150 |
|Partizione della tabella 4: A >= 30  |B=50, B=100, B=150 |

### <a name="best-practices"></a>Procedure consigliate

Per migliorare le prestazioni di query che accedono a una grande quantità di dati da tabelle e indici partizionati estesi, è opportuno adottare le procedure consigliate seguenti:

* Eseguire lo striping di ogni partizione tra molti dischi. Questo è particolarmente importante durante l'uso della rotazione dei dischi.
* Quando possibile, utilizzare un server con memoria principale sufficiente per contenere partizioni a cui viene effettuato l'accesso frequentemente o a tutte le partizioni in memoria per ridurre il costo delle operazioni di I/O.
* Se i dati oggetto della query non sono tutti contenuti in memoria, comprimere le tabelle e gli indici al fine di ridurre il costo delle operazioni di I/O.
* Utilizzare un server con processori veloci e il maggior numero possibile di core del processore per sfruttare a pieno la funzionalità di elaborazione di query parallele.
* Assicurarsi che per il server sia disponibile larghezza di banda sufficiente del controller I/O. 
* Creare un indice cluster in ogni tabella partizionata grande per sfruttare le ottimizzazioni dell'analisi dell'albero B.
* Quando si esegue il caricamento bulk di dati in tabelle partizionate, attenersi ai requisiti della procedura consigliata nel white paper [The Data Loading Performance Guide](https://msdn.microsoft.com/library/dd425070.aspx) (Guida alle prestazioni del caricamento dati).

### <a name="example"></a>Esempio

Nell'esempio seguente viene creato un database di test che contiene un'unica tabella con sette partizioni. Per l'esecuzione delle query in questo esempio utilizzare gli strumenti descritti in precedenza per visualizzare le informazioni sul partizionamento relative ai piani della fase di compilazione e della fase di esecuzione. 

> [!NOTE]
> In questo esempio nella tabella viene inserito più di un milione di righe. A seconda dell'hardware disponibile l'esecuzione di questo esempio può richiedere diversi minuti. Prima di eseguire questo esempio, verificare di disporre di almeno 1,5 GB di spazio libero su disco. 
 
```sql
USE master;
GO
IF DB_ID (N'db_sales_test') IS NOT NULL
    DROP DATABASE db_sales_test;
GO
CREATE DATABASE db_sales_test;
GO
USE db_sales_test;
GO
CREATE PARTITION FUNCTION [pf_range_fact](int) AS RANGE RIGHT FOR VALUES 
(20080801, 20080901, 20081001, 20081101, 20081201, 20090101);
GO
CREATE PARTITION SCHEME [ps_fact_sales] AS PARTITION [pf_range_fact] 
ALL TO ([PRIMARY]);
GO
CREATE TABLE fact_sales(date_id int, product_id int, store_id int, 
    quantity int, unit_price numeric(7,2), other_data char(1000))
ON ps_fact_sales(date_id);
GO
CREATE CLUSTERED INDEX ci ON fact_sales(date_id);
GO
PRINT 'Loading...';
SET NOCOUNT ON;
DECLARE @i int;
SET @i = 1;
WHILE (@i<1000000)
BEGIN
    INSERT INTO fact_sales VALUES(20080800 + (@i%30) + 1, @i%10000, @i%200, RAND() * 25, (@i%3) + 1, '');
    SET @i += 1;
END;
GO
DECLARE @i int;
SET @i = 1;
WHILE (@i<10000)
BEGIN
    INSERT INTO fact_sales VALUES(20080900 + (@i%30) + 1, @i%10000, @i%200, RAND() * 25, (@i%3) + 1, '');
    SET @i += 1;
END;
PRINT 'Done.';
GO
-- Two-partition query.
SET STATISTICS XML ON;
GO
SELECT date_id, SUM(quantity*unit_price) AS total_price
FROM fact_sales
WHERE date_id BETWEEN 20080802 AND 20080902
GROUP BY date_id ;
GO
SET STATISTICS XML OFF;
GO
-- Single-partition query.
SET STATISTICS XML ON;
GO
SELECT date_id, SUM(quantity*unit_price) AS total_price
FROM fact_sales
WHERE date_id BETWEEN 20080801 AND 20080831
GROUP BY date_id;
GO
SET STATISTICS XML OFF;
GO
```

##  <a name="Additional_Reading"></a> Ulteriori informazioni  
 [Guida di riferimento a operatori Showplan logici e fisici](../relational-databases/showplan-logical-and-physical-operators-reference.md)  
 [Eventi estesi](../relational-databases/extended-events/extended-events.md)  
 [Procedure consigliate per l'archivio query](../relational-databases/performance/best-practice-with-the-query-store.md)  
 [Stima della cardinalità](../relational-databases/performance/cardinality-estimation-sql-server.md)  
 [Elaborazione di query adattive](../relational-databases/performance/adaptive-query-processing.md)   
 [Ordine di precedenza degli operatori](../t-sql/language-elements/operator-precedence-transact-sql.md)
