---
title: CREARE l'indice COLUMNSTORE (Transact-SQL) | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_COLUMNSTORE_INDEX_TSQL
- COLUMNSTORE INDEX
- COLUMNSTORE_INDEX_TSQL
- CREATE CLUSTERED COLUMNSTORE INDEX
- COLUMNSTORE_TSQL
- CREATE NONCLUSTERED COLUMNSTORE INDEX
- CREATE_NONCLUSTERED_COLUMNSTORE_INDEX_TSQL
- CREATE COLUMNSTORE INDEX
- CREATE_CLUSTERED_COLUMNSTORE_INDEX_TSQL
- COLUMNSTORE
dev_langs:
- TSQL
helpviewer_keywords:
- index creation [SQL Server], columnstore indexes
- columnstore index, creating
- CREATE COLUMNSTORE INDEX statement
- CREATE INDEX statement
ms.assetid: 7e1793b3-5383-4e3d-8cef-027c0c8cb5b1
caps.latest.revision: 76
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: a4e3b602b026d359c7eac492fc44480d4b1a18a9
ms.contentlocale: it-it
ms.lasthandoff: 09/21/2017

---

# <a name="create-columnstore-index-transact-sql"></a>CREATE COLUMNSTORE INDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Convertire una tabella rowstore in un indice columnstore cluster o creare un indice columnstore non cluster. Utilizzare un indice columnstore per un'esecuzione efficiente analitica operativa in tempo reale in un carico di lavoro OLTP o per migliorare le prestazioni di query e la compressione dei dati per i carichi di lavoro di data warehousing.  
  
> [!NOTE]  
>  A partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], è possibile creare la tabella come indice columnstore cluster.   Non è più necessario creare prima una tabella rowstore e quindi convertirla in un indice columnstore cluster.  
  
Ignora agli esempi:  
-   [Esempi per la conversione di una tabella rowstore a columnstore](../../t-sql/statements/create-columnstore-index-transact-sql.md#convert)  
-   [Esempi per gli indici columnstore non cluster](../../t-sql/statements/create-columnstore-index-transact-sql.md#nonclustered)  
  
Passare a scenari:  
-   [Indici ColumnStore per analitica operativa in tempo reale](/sql-docs/docs/relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics)  
-   [Indici ColumnStore per il data warehouse](/sql-docs/docs/relational-databases/indexes/columnstore-indexes-data-warehouse)  
  
Ulteriori informazioni:  
-   [Guida agli indici ColumnStore](/sql-docs/docs/relational-databases/indexes/columnstore-indexes-overview)  
-   [Riepilogo delle funzionalità degli indici ColumnStore](/sql-docs/docs/relational-databases/indexes/columnstore-indexes-what-s-new)  
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
-- Create a clustered columnstore index on disk-based table.  
CREATE CLUSTERED COLUMNSTORE INDEX index_name  
    ON [database_name. [schema_name ] . | schema_name . ] table_name  
    [ WITH ( < with_option> [ ,...n ] ) ]  
    [ ON <on_option> ]  
[ ; ]  
  
--Create a non-clustered columnstore index on a disk-based table.  
CREATE [NONCLUSTERED]  COLUMNSTORE INDEX index_name   
    ON [database_name. [schema_name ] . | schema_name . ] table_name   
        ( column  [ ,...n ] )  
    [ WHERE <filter_expression> [ AND <filter_expression> ] ]
    [ WITH ( < with_option> [ ,...n ] ) ]  
    [ ON <on_option> ]   
[ ; ]  
  
<with_option> ::=  
      DROP_EXISTING = { ON | OFF } -- default is OFF  
    | MAXDOP = max_degree_of_parallelism 
    | ONLINE = { ON | OFF } 
    | COMPRESSION_DELAY  = { 0 | delay [ Minutes ] }  
    | DATA_COMPRESSION = { COLUMNSTORE | COLUMNSTORE_ARCHIVE }  
      [ ON PARTITIONS ( { partition_number_expression | range } [ ,...n ] ) ]  
  
<on_option>::=  
      partition_scheme_name ( column_name )   
    | filegroup_name   
    | "default"   
  
<filter_expression> ::=  
      column_name IN ( constant [ ,...n ]  
    | column_name { IS | IS NOT | = | <> | != | > | >= | !> | < | <= | !< } constant  
  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
CREATE CLUSTERED COLUMNSTORE INDEX index_name   
    ON [ database_name . [ schema_name ] . | schema_name . ] table_name  
    [ WITH ( DROP_EXISTING = { ON | OFF } ) ] --default is OFF  
[;]  
```  
  
## <a name="arguments"></a>Argomenti  
CREATE CLUSTERED COLUMNSTORE INDEX  
Creare un indice columnstore cluster in cui tutti i dati vengono compressi e archiviati dalla colonna. L'indice include tutte le colonne della tabella e archivia l'intera tabella. Se la tabella esistente è un heap o indice cluster, la tabella viene convertita in un indice columnstore cluster. Se la tabella è già archiviata come indice columnstore cluster, l'indice esistente viene eliminato e ricompilato.  
  
*index_name*  
Specifica il nome per il nuovo indice.  
  
Se la tabella dispone già di un indice columnstore cluster, è possibile specificare lo stesso nome di indice esistente oppure è possibile utilizzare l'opzione DROP_EXISTING per specificare un nuovo nome.  
  
ON [*database_name*. [*schema_name* ]. | *schema_name* . ] *table_name*  
   Specifica il nome composto da una, due o tre parti della tabella da archiviare come indice columnstore cluster. Se la tabella è un heap o indice cluster della tabella viene convertito da rowstore a columnstore. Se la tabella è già un columnstore, questa istruzione consente di ricompilare l'indice columnstore cluster.  
  
con  
DROP_EXISTING = [OFF] | ON  
   DROP_EXISTING = ON specifica per eliminare l'indice columnstore cluster esistente, quindi creare un nuovo indice columnstore.  

   Il valore predefinito, DROP_EXISTING = OFF prevede che il nome dell'indice è lo stesso nome esistente. Si verifica un errore è il nome dell'indice specificato esiste già.  
  
MAXDOP = *max_degree_of_parallelism*  
   Esegue l'override della configurazione del server del massimo grado di parallelismo per la durata dell'operazione di indice. Utilizzare MAXDOP per limitare il numero di processori utilizzati durante l'esecuzione di un piano parallelo. Il valore massimo è 64 processori.  
  
   *max_degree_of_parallelism* i possibili valori sono:  
   - 1 - Disattiva la generazione di piani paralleli.  
   - \>1 - limita il numero massimo di processori utilizzati in un'operazione parallela sugli indici per il numero specificato o meno in base al carico di lavoro di sistema corrente. Ad esempio, se MAXDOP = 4, il numero di processori utilizzati è minore o uguale a 4.  
   - 0 (valore predefinito) - Usa il numero effettivo di processori o un numero inferiore in base al carico di lavoro corrente del sistema.  
  
   Per ulteriori informazioni, vedere [il max degree of parallelism opzione di configurazione Server Configurare](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md), e [configurare operazioni parallele sugli indici](../../relational-databases/indexes/configure-parallel-index-operations.md).  
 
COMPRESSION_DELAY = **0** | *ritardo* [minuti]  
   Si applica a: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].

   Per una tabella basata su disco, *ritardo* specifica il numero minimo di minuti un rowgroup delta in stato di chiusura deve rimanere in rowgroup delta prima che SQL Server può ridurre in rowgroup compressi. Poiché le tabelle basate su disco non tenere traccia delle insert e update volte su singole righe, SQL Server si applica il ritardo in rowgroup delta nello stato CLOSED.  
   Il valore predefinito è 0 minuti.  
   Per indicazioni su quando usare COMPRESSION_DELAY, vedere [Introduzione a Columnstore per analitica operativa in tempo reale](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md).  
  
DATA_COMPRESSION = COLUMNSTORE | COLUMNSTORE_ARCHIVE  
   Si applica a: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
Specifica l'opzione di compressione dei dati per la tabella, il numero di partizione o l'intervallo di partizioni specificato. Sono disponibili le opzioni seguenti:   
COLUMNSTORE  
   COLUMNSTORE è il valore predefinito e specifica questa opzione per comprimere con la maggior parte dei compressione columnstore ad alte prestazioni. Si tratta in genere.  
  
COLUMNSTORE_ARCHIVE  
   COLUMNSTORE_ARCHIVE ulteriormente comprime la tabella o la partizione a una dimensione inferiore. Utilizzare questa opzione per le situazioni, ad esempio archiviazione che richiedono dimensioni di archiviazione inferiori ed è possibile concedere più tempo per l'archiviazione e il recupero.  
  
   Per ulteriori informazioni sulla compressione, vedere [la compressione dei dati](../../relational-databases/data-compression/data-compression.md).  

ON  
   Con le opzioni ON è possibile specificare le opzioni per l'archiviazione dei dati, ad esempio uno schema di partizione, un filegroup specifico o il filegroup predefinito. Se l'opzione ON non è specificato, l'indice utilizza le impostazioni di partizione o filegroup di impostazioni della tabella esistente.  
  
   *partition_scheme_name* **(** *column_name* **)**  
   Specifica lo schema di partizione per la tabella. Lo schema di partizione deve essere già presente nel database. Per creare lo schema di partizione, vedere [CREATE PARTITION SCHEME](../../t-sql/statements/create-partition-scheme-transact-sql.md).  
 
   *column_name* specifica la colonna in base alla quale viene partizionato un indice partizionato. Questa colonna deve corrispondere al tipo di dati, lunghezza e precisione dell'argomento della partizione di funzione che *partition_scheme_name* utilizza.  

   *filegroup_name*  
   Specifica il filegroup per l'archiviazione dell'indice columnstore cluster. Se non viene specificato alcun percorso e la tabella non è partizionata, l'indice usano lo stesso filegroup della tabella o vista sottostante. Il filegroup deve essere già esistente.  

   **"**predefinito**"**  
   Per creare l'indice nel filegroup predefinito, usare "default" o [default].  
  
   Se si specifica "default", l'opzione QUOTED_IDENTIFIER deve essere impostata su ON per la sessione corrente. QUOTED_IDENTIFIER è ON per impostazione predefinita. Per altre informazioni, vedere [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md).  
  
CREARE L'INDICE COLUMNSTORE [CLUSTER]  
Creare un indice columnstore non cluster in memoria in una tabella rowstore archiviati come un heap o indice cluster. L'indice può avere una condizione filtrata e non è necessario includere tutte le colonne della tabella sottostante. L'indice columnstore richiede spazio sufficiente per archiviare una copia dei dati. È aggiornabile e viene aggiornato con la tabella sottostante viene modificata. L'indice columnstore non cluster in un indice cluster consente analitica in tempo reale.  
  
*index_name*  
   Specifica il nome dell'indice. *index_name* deve essere univoco all'interno della tabella, ma non deve essere univoco all'interno del database. I nomi di indice devono rispettare le regole di [identificatori](../../relational-databases/databases/database-identifiers.md).  
  
 **(** *colonna* [ **,**... *n* ] **)**  
    Specifica le colonne da archiviare. Un indice columnstore non cluster è limitato a 1024 colonne.  
   Ogni colonna deve essere di un tipo di dati supportato per gli indici columnstore. Vedere [limitazioni e restrizioni](../../t-sql/statements/create-columnstore-index-transact-sql.md#LimitRest) per un elenco di tipi di dati supportati.  

ON [*database_name*. [*schema_name* ]. | *schema_name* . ] *table_name*  
   Specifica di una, due o nome in tre parti della tabella che contiene l'indice.  

CON DROP_EXISTING = [OFF] | ON  
   DROP_EXISTING = ON, l'indice esistente viene eliminato e ricompilato. Il nome di indice specificato deve corrispondere a quello dell'indice esistente, mentre la definizione dell'indice può essere modificata. È possibile, ad esempio, specificare colonne diverse oppure opzioni dell'indice.
  
   DROP_EXISTING = OFF, viene visualizzato un errore se il nome dell'indice specificato esiste già. Il tipo di indice non può essere modificato tramite l'opzione DROP_EXISTING. Per quanto riguarda la sintassi compatibile con le versioni precedenti, WITH DROP_EXISTING equivale a WITH DROP_EXISTING = ON.  

MAXDOP = *max_degree_of_parallelism*  
   Esegue l'override di [il max degree of parallelism opzione di configurazione Server Configurare](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md) opzione di configurazione per la durata dell'operazione sull'indice. Utilizzare MAXDOP per limitare il numero di processori utilizzati durante l'esecuzione di un piano parallelo. Il valore massimo è 64 processori.  
  
   *max_degree_of_parallelism* i possibili valori sono:  
   - 1 - Disattiva la generazione di piani paralleli.  
   - \>1 - limita il numero massimo di processori utilizzati in un'operazione parallela sugli indici per il numero specificato o meno in base al carico di lavoro di sistema corrente. Ad esempio, se MAXDOP = 4, il numero di processori utilizzati è minore o uguale a 4.  
   - 0 (valore predefinito) - Usa il numero effettivo di processori o un numero inferiore in base al carico di lavoro corrente del sistema.  
  
   Per altre informazioni, vedere [Configurazione di operazioni parallele sugli indici](../../relational-databases/indexes/configure-parallel-index-operations.md).  
  
> [!NOTE]  
>  Operazioni parallele sugli indici non sono disponibili in ogni edizione di [!INCLUDE[msC](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per un elenco delle funzionalità supportate dalle edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Edizioni e funzionalità supportate per SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
ONLINE = [ON | OFF]   
   Si applica a: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)], negli indici columnstore non cluster solo.
ON specifica che l'indice columnstore non cluster rimane online e disponibile mentre la nuova copia dell'indice in corso di compilazione.

   OFF specifica che l'indice non è disponibile per l'utilizzo durante la nuova copia in corso di compilazione. Poiché si tratta di un indice non cluster, solo la tabella di base rimanga, che solo l'indice columnstore non cluster non viene utilizzato per rispondere alle query fino al completamento del nuovo indice. 

COMPRESSION_DELAY = **0** | \<ritardo > [minuti]  
   Si applica a: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
   Specifica un limite inferiore per quanto tempo una riga deve rimanere in rowgroup delta prima che sia idoneo per la migrazione a gruppo di righe compresso. Un cliente può ad esempio, che se una riga è stata modificata per 120 minuti, renderlo idoneo per la compressione in formato di archiviazione. Per l'indice columnstore nelle tabelle basate su disco, è non tengono traccia il tempo quando una riga inserita o aggiornata, è possibile usare il delta rowgroup chiuso tempo come proxy per la riga invece. La durata predefinita è 0 minuti. Una riga viene eseguita la migrazione al formato di archiviazione dopo che sono stati accumulati 1 milione di righe nel rowgroup delta e perché è stato contrassegnato come chiuso.  
  
DATA_COMPRESSION  
   Specifica l'opzione di compressione dei dati per la tabella, il numero di partizione o l'intervallo di partizioni specificato. Sono disponibili le opzioni seguenti:  
COLUMNSTORE  
   Si applica a: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Si applica solo agli indici columnstore, inclusi gli indici columnstore cluster e quelli non cluster. COLUMNSTORE è il valore predefinito e specifica questa opzione per comprimere con la maggior parte dei compressione columnstore ad alte prestazioni. Si tratta in genere.  
  
COLUMNSTORE_ARCHIVE  
   Si applica a: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
Si applica solo agli indici columnstore, inclusi gli indici columnstore cluster e quelli non cluster. COLUMNSTORE_ARCHIVE ulteriormente comprime la tabella o la partizione a una dimensione inferiore. Può essere utilizzata per l'archiviazione o in altre situazioni in cui sono richieste dimensioni di archiviazione inferiori ed è possibile concedere più tempo per l'archiviazione e il recupero.  
  
 Per ulteriori informazioni sulla compressione, vedere [la compressione dei dati](../../relational-databases/data-compression/data-compression.md).  
  
DOVE \<filter_expression > [AND \<filter_expression >] si applica a: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
  
   Chiamata di un predicato del filtro, consente di specificare le righe da includere nell'indice. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Crea statistiche filtrate sulle righe di dati nell'indice filtrato.  
  
   Il predicato del filtro utilizza una logica di confronto semplice. I confronti in cui vengono utilizzati valori letterali NULL non sono consentiti con gli operatori di confronto. In alternativa, utilizzare gli operatori IS NULL e IS NOT NULL.  
  
   Di seguito sono riportati alcuni esempi di predicati di filtro per la tabella `Production.BillOfMaterials`:  
   `WHERE StartDate > '20000101' AND EndDate <= '20000630'`    
   `WHERE ComponentID IN (533, 324, 753)`  
   `WHERE StartDate IN ('20000404', '20000905') AND EndDate IS NOT NULL`  
   
   Per linee guida per gli indici filtrati, vedere [Create Filtered Indexes](../../relational-databases/indexes/create-filtered-indexes.md).  
  
ON  
   Queste opzioni consentono di specificare il filegroup in cui viene creato l'indice.  
  
*partition_scheme_name* **(** *column_name* **)**  
   Specifica lo schema di partizione che definisce i filegroup in cui viene eseguito il mapping delle partizioni di un indice partizionato. Lo schema di partizione deve esistere all'interno del database eseguendo [CREATE PARTITION SCHEME](../../t-sql/statements/create-partition-scheme-transact-sql.md). 
   *column_name* specifica la colonna in base alla quale viene partizionato un indice partizionato. Questa colonna deve corrispondere al tipo di dati, lunghezza e precisione dell'argomento della partizione di funzione che *partition_scheme_name* utilizza. *column_name* non è limitato alle colonne nella definizione dell'indice. Quando si partiziona un indice columnstore, la colonna di partizionamento viene aggiunta dal [!INCLUDE[ssDE](../../includes/ssde-md.md)] come colonna dell'indice, se non è già stata specificata.  
   Se *partition_scheme_name* o *filegroup* non è specificato e la tabella è partizionata, l'indice viene posizionato nello stesso schema di partizione, utilizzando la stessa colonna di partizionamento della tabella sottostante.  
   Un indice columnstore su una tabella partizionata deve essere allineato con il partizionamento.  
   Per ulteriori informazioni sul partizionamento degli indici, vedere [tabelle e indici partizionati](../../relational-databases/partitions/partitioned-tables-and-indexes.md).  

*filegroup_name*  
   Specifica il nome di un filegroup in cui creare l'indice. Se *filegroup_name* non è specificato e la tabella non è partizionata, l'indice Usa lo stesso filegroup della tabella sottostante. Il filegroup deve essere già esistente.  
 
**"**predefinito**"**  
Crea l'indice specificato nel filegroup predefinito.  
  
In questo contesto il termine default non rappresenta una parola chiave, È un identificatore per il filegroup predefinito e deve essere delimitato, ad esempio ON **"**predefinito**"** oppure ON **[**predefinito**]**. Se si specifica "default", l'opzione QUOTED_IDENTIFIER deve essere impostata su ON per la sessione corrente. Si tratta dell'impostazione predefinita. Per altre informazioni, vedere [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md).  
  
##  <a name="Permissions"></a> Autorizzazioni  
 È necessario disporre dell'autorizzazione ALTER per la tabella.  
  
##  <a name="GenRemarks"></a>Osservazioni generali  
 In una tabella temporanea, è possibile creare un indice columnstore. Quando si elimina la tabella o termina la sessione, viene eliminato anche l'indice.  
 
## <a name="filtered-indexes"></a>Indici filtrati  
Un indice filtrato è un indice non cluster ottimizzato, adatto per le query tramite cui viene selezionata una piccola percentuale di righe da una tabella. Utilizza un predicato del filtro per indicizzare una parte dei dati di una tabella. Un indice filtrato progettato correttamente consente di migliorare le prestazioni di esecuzione delle query e di ridurre i costi di archiviazione e di manutenzione.  
  
### <a name="required-set-options-for-filtered-indexes"></a>Opzioni SET necessarie per gli indici filtrati  
Le opzioni SET nella colonna Valore obbligatorio sono richieste ogni volta che si verifica una qualsiasi delle condizioni seguenti:  
- Viene creato un indice filtrato.  
- I dati di un indice filtrato vengono modificati tramite un'operazione INSERT, UPDATE, DELETE o MERGE.  
- L'indice filtrato venga utilizzato da query optimizer per generare il piano di query.  
  
    |Opzioni SET|Valore obbligatorio|Valore server predefinito|Default<br /><br /> OLE DB e ODBC predefinito|Default<br /><br /> DB-Library predefinito|  
    |-----------------|--------------------|--------------------------|---------------------------------------|-----------------------------------|  
    |ANSI_NULLS|ON|ON|ON|OFF|  
    |ANSI_PADDING|ON|ON|ON|OFF|  
    |ANSI_WARNINGS*|ON|ON|ON|OFF|  
    |ARITHABORT|ON|ON|OFF|OFF|  
    |CONCAT_NULL_YIELDS_NULL|ON|ON|ON|OFF|  
    |NUMERIC_ROUNDABORT|OFF|OFF|OFF|OFF|  
    |QUOTED_IDENTIFIER|ON|ON|ON|OFF|   
  
     *Quando il livello di compatibilità del database è impostato su 90 o su un valore maggiore, l'impostazione di ANSI_WARNINGS su ON comporta anche l'impostazione implicita di ARITHABORT su ON. Se il livello di compatibilità del database è impostato su 80 o su un valore inferiore, l'opzione ARITHABORT deve essere impostata su ON in modo esplicito.  
  
 Se le opzioni SET non sono corrette, possono verificarsi le condizioni seguenti:  
  
-   L'indice filtrato non viene creato.  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)] genera un errore ed esegue il rollback delle istruzioni INSERT, UPDATE, DELETE o MERGE tramite le quali vengono modificati i dati dell'indice.  
  
-   Query Optimizer non considera l'indice nel piano di esecuzione per le istruzioni Transact-SQL.  
  
 Per ulteriori informazioni sugli indici filtrati, vedere [Create Filtered Indexes](../../relational-databases/indexes/create-filtered-indexes.md). 
  
##  <a name="LimitRest"></a> Limitazioni e restrizioni  

**Ogni colonna in un indice columnstore deve essere uno dei seguenti tipi di dati di business comuni:** 
-   DateTimeOffset [( * n * )]  
-   datetime2 [( * n * )]  
-   datetime  
-   smalldatetime  
-   data  
-   tempo [( * n * )]  
-   float [( * n * )]  
-   reale [( * n * )]  
-   decimale [( *precisione* [ *, scala* ] **)** ]
-   numerico [( *precisione* [ *, scala* ] **)** ]    
-   money  
-   smallmoney  
-   bigint  
-   int  
-   smallint  
-   tinyint  
-   bit  
-   nvarchar [( * n * )] 
-   nvarchar (max) (si applica a [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] e Database SQL di Azure a premium tariffario, solo gli indici columnstore cluster)   
-   nchar [( * n * )]  
-   varchar [( * n * )]  
-   varchar (max) (si applica a [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] e Database SQL di Azure a premium tariffario, solo gli indici columnstore cluster)
-   Char [( * n * )]  
-   varbinary [( * n * )] 
-   varbinary (max) (si applica a [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] e Database SQL di Azure a premium tariffario, solo gli indici columnstore cluster)
-   binario [( * n * )]  
-   uniqueidentifier (si applica a [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] e versioni successive)
  
Se la tabella sottostante contiene una colonna di un tipo di dati che non è supportata per gli indici columnstore, è necessario omettere la colonna dall'indice columnstore non cluster.  
  
**Le colonne che utilizzano uno qualsiasi dei seguenti tipi di dati non possono essere inclusa in un indice columnstore:**
-   ntext, testo e immagine  
-   nvarchar (max), varchar (max) e varbinary (max) (si applica a [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] e le versioni precedenti e gli indici columnstore non cluster) 
-   rowversion (e timestamp)  
-   sql_variant  
-   Tipi CLR (tipi spaziali e hierarchyid)  
-   xml  
-   uniqueidentifier (si applica a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)])  

**Indici columnstore non cluster:**
-   Non può includere più di 1024 colonne.  
-   Una tabella con un indice columnstore non cluster può presentare vincoli univoci, vincoli di chiave primaria o vincoli di chiave esterna, ma i vincoli non possono essere inclusi nell'indice columnstore non cluster.  
-   Non può essere creato in una vista o in una vista indicizzata.  
-   Non può includere una colonna di tipo sparse.  
-   Non può essere modificato utilizzando il **ALTER INDEX** istruzione. Per modificare l'indice non cluster, è invece necessario eliminare e ricreare l'indice columnstore. È possibile utilizzare **ALTER INDEX** per disabilitare e ricompilare un indice columnstore.  
-   Non è possibile creare tramite il **INCLUDE** (parola chiave).  
-   Non può includere il **ASC** o **DESC** parole chiave per l'ordinamento dell'indice. Gli indici columnstore vengono ordinati in base agli algoritmi di compressione. L'ordinamento comporta molti dei vantaggi a livello di prestazioni.  
-   Non può includere colonne LOB (large object) di tipo nvarchar (max), varchar (max) e varbinary (max) in indici ColumnStore non cluster. Solo gli indici columnstore cluster supportano tipi LOB, a partire da [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] versione e il Database di SQL Azure configurata a livello di prezzo premium. Si noti che le versioni precedenti non supportano i tipi LOB negli indici cluster e columnstore.


 **Gli indici ColumnStore non possono essere combinati con le funzionalità seguenti:**  
-   Colonne calcolate. A partire da SQL Server 2017, un indice columnstore cluster può contenere una colonna calcolata non persistente. Tuttavia, in SQL Server 2017, gli indici columnstore cluster non possono contenere colonne calcolate persistenti e non è possibile gli indici non cluster creati per le colonne calcolate. 
-   La compressione di pagina e di riga, e **vardecimal** il formato di archiviazione (un indice columnstore è già compresso in un formato diverso).  
-   Replica  
-   Filestream

È possibile utilizzare i cursori o trigger in una tabella con un indice columnstore cluster. Questa restrizione non si applica agli indici columnstore non cluster; è possibile utilizzare i cursori e il trigger in una tabella con un indice columnstore non cluster.

**Limitazioni specifiche di SQL Server 2014**  
Queste limitazioni si applicano solo a SQL Server 2014. In questa versione è stata introdotta gli indici columnstore cluster aggiornabili. Indici columnstore non cluster sono stati ancora di sola lettura.  

-   Rilevamento delle modifiche. Non è possibile utilizzare rilevamento con indici columnstore non cluster (NCCI) perché sono di sola lettura. Funziona per gli indici columnstore cluster (CCI).  
-   Acquisizione dei dati delle modifiche. Non è possibile utilizzare change data capture per indice columnstore non cluster (NCCI) perché sono di sola lettura. Funziona per gli indici columnstore cluster (CCI).  
-   Secondario leggibile. È possibile accedere a un indice cluster columnstore cluster (CCI) da un database secondario leggibile di un gruppo di disponibilità AlwaysOn OnReadable.  È possibile accedere a un indice columnstore non cluster (NCCI) da un database secondario leggibile.  
-   Multiple Active Result Sets (MARS). SQL Server 2014 utilizza MARS per le connessioni di sola lettura alle tabelle con un indice columnstore.    Tuttavia, SQL Server 2014 non supporta MARS per le operazioni simultanee dei dati manipulation language (DML) in una tabella con un indice columnstore. In questo caso, SQL Server termina le connessioni e interrompe le transazioni.  
  
 Per informazioni sulle prestazioni e limitazioni degli indici columnstore, vedere [panoramica degli indici Columnstore](../../relational-databases/indexes/columnstore-indexes-overview.md).
  
##  <a name="Metadata"></a> Metadati  
 Tutte le colonne di un indice columnstore vengono archiviate nei metadati come colonne incluse. L'indice columnstore non contiene colonne chiave. Nelle seguenti viste di sistema sono fornite informazioni sugli indici columnstore.  
  
-   [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)  
-   [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
-   [sys.partitions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)  
-   [sys.column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-segments-transact-sql.md)  
-   [sys.column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md)  
-   [sys.column_store_row_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql.md)  

##  <a name="convert"></a>Esempi per la conversione di una tabella rowstore a columnstore  
  
### <a name="a-convert-a-heap-to-a-clustered-columnstore-index"></a>A. Convertire un heap in un indice columnstore cluster  
 In questo esempio viene creata una tabella come heap, che viene poi convertita in un indice columnstore cluster denominato cci_Simple. In questo modo viene modificata l'archiviazione dell'intera tabella da rowstore a columnstore.  
  
```  
CREATE TABLE SimpleTable(  
    ProductKey [int] NOT NULL,   
    OrderDateKey [int] NOT NULL,   
    DueDateKey [int] NOT NULL,   
    ShipDateKey [int] NOT NULL);  
GO  
CREATE CLUSTERED COLUMNSTORE INDEX cci_Simple ON SimpleTable;  
GO  
```  
  
### <a name="b-convert-a-clustered-index-to-a-clustered-columnstore-index-with-the-same-name"></a>B. Convertire un indice cluster in un indice columnstore cluster con lo stesso nome.  
 In questo esempio viene creato una tabella con un indice cluster, quindi viene illustrata la sintassi della conversione dell'indice cluster in un indice columnstore cluster. In questo modo viene modificata l'archiviazione dell'intera tabella da rowstore a columnstore.  
  
```  
CREATE TABLE SimpleTable (  
    ProductKey [int] NOT NULL,   
    OrderDateKey [int] NOT NULL,   
    DueDateKey [int] NOT NULL,   
    ShipDateKey [int] NOT NULL);  
GO  
CREATE CLUSTERED INDEX cl_simple ON SimpleTable (ProductKey);  
GO  
CREATE CLUSTERED COLUMNSTORE INDEX cl_simple ON SimpleTable  
WITH (DROP_EXISTING = ON);  
GO  
```  
  
### <a name="c-handle-nonclustered-indexes-when-converting-a-rowstore-table-to-a-columnstore-index"></a>C. Gestire gli indici non cluster durante la conversione di una tabella rowstore in un indice columnstore.  
 In questo esempio viene illustrato come gestire gli indici non cluster durante la conversione di una tabella rowstore in un indice columnstore. In realtà, a partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] alcuna azione speciale non è obbligatorio. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] definisce automaticamente e consente di ricompilare gli indici non cluster nel nuovo indice columnstore cluster.  
  
 Se si desidera eliminare gli indici non cluster, utilizzare l'istruzione DROP INDEX prima di creare l'indice columnstore. L'opzione DROP_EXISTING Elimina solo l'indice cluster che esegue la conversione. Non elimina gli indici non cluster.  
  
 In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] e [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], non è stato possibile creare un indice non cluster in un indice columnstore. Questo esempio mostra come nelle versioni precedenti è necessario eliminare gli indici non cluster prima di creare l'indice columnstore.  
  
```  
  
--Create the table for use with this example.  
CREATE TABLE SimpleTable (  
    ProductKey [int] NOT NULL,   
    OrderDateKey [int] NOT NULL,   
    DueDateKey [int] NOT NULL,   
    ShipDateKey [int] NOT NULL);  
GO  
  
--Create two nonclustered indexes for use with this example  
CREATE INDEX nc1_simple ON SimpleTable (OrderDateKey);  
CREATE INDEX nc2_simple ON SimpleTable (DueDateKey);   
GO  
  
--SQL Server 2012 and SQL Server 2014: you need to drop the nonclustered indexes  
--in order to create the columnstore index.   
  
DROP INDEX SimpleTable.nc1_simple;  
DROP INDEX SimpleTable.nc2_simple;  
  
--Convert the rowstore table to a columnstore index.  
CREATE CLUSTERED COLUMNSTORE INDEX cci_simple ON SimpleTable;   
GO  
  
```  
  
### <a name="d-convert-a-large-fact-table-from-rowstore-to-columnstore"></a>D. Convertire una tabella dei fatti di grandi dimensioni da rowstore a columnstore  
 In questo esempio viene illustrato come convertire una tabella dei fatti di grandi dimensioni da una tabella rowstore in una tabella columnstore.  
  
 Per convertire una tabella rowstore in una tabella columnstore.  
  
1.  Innanzitutto, creare una tabella di piccole dimensioni da usare nell'esempio.  
  
    ```  
    --Create a rowstore table with a clustered index and a non-clustered index.  
    CREATE TABLE MyFactTable (  
        ProductKey [int] NOT NULL,  
        OrderDateKey [int] NOT NULL,  
         DueDateKey [int] NOT NULL,  
         ShipDateKey [int] NOT NULL )  
    )  
    WITH (  
        CLUSTERED INDEX ( ProductKey )  
    );  
  
    --Add a non-clustered index.  
    CREATE INDEX my_index ON MyFactTable ( ProductKey, OrderDateKey );  
    ```  
  
2.  Eliminare tutti gli indici non cluster della tabella rowstore.  
  
    ```  
    --Drop all non-clustered indexes  
    DROP INDEX my_index ON MyFactTable;  
    ```  
  
3.  Eliminare l'indice cluster.  
  
    -   Eseguire questa operazione solo se si desidera specificare un nuovo nome per l'indice quando viene convertito in un indice columnstore cluster. Se non viene eliminato l'indice cluster, il nuovo indice columnstore cluster ha lo stesso nome.  
  
        > [!NOTE]  
        >  Il nome dell'indice è più facile da ricordare se si usano il proprio nome. Tutti gli indici cluster rowstore utilizzano il nome predefinito ' ClusteredIndex_\<GUID >'.  
  
    ```  
    --Process for dropping a clustered index.  
    --First, look up the name of the clustered rowstore index.  
    --Clustered rowstore indexes always use the DEFAULT name ‘ClusteredIndex_<GUID>’.  
    SELECT i.name   
    FROM sys.indexes i   
    JOIN sys.tables t  
    ON ( i.type_desc = 'CLUSTERED' ) WHERE t.name = 'MyFactTable';  
  
    --Drop the clustered rowstore index.  
    DROP INDEX ClusteredIndex_d473567f7ea04d7aafcac5364c241e09 ON MyDimTable;  
    ```  
  
4.  Convertire la tabella rowstore in una tabella columnstore con un indice columnstore cluster.  
  
    ```  
    --Option 1: Convert to columnstore and name the new clustered columnstore index MyCCI.  
    CREATE CLUSTERED COLUMNSTORE INDEX MyCCI ON MyFactTable;  
  
    --Option 2: Convert to columnstore and use the rowstore clustered   
    --index name for the columnstore clustered index name.  
    --First, look up the name of the clustered rowstore index.  
    SELECT i.name   
    FROM sys.indexes i  
    JOIN sys.tables t   
    ON ( i.type_desc = 'CLUSTERED' )  
    WHERE t.name = 'MyFactTable';  
  
    --Second, create the clustered columnstore index and   
    --Replace ClusteredIndex_d473567f7ea04d7aafcac5364c241e09  
    --with the name of your clustered index.  
    CREATE CLUSTERED COLUMNSTORE INDEX   
    ClusteredIndex_d473567f7ea04d7aafcac5364c241e09  
     ON MyFactTable  
    WITH DROP_EXISTING = ON;  
    ```  
  
### <a name="e-convert-a-columnstore-table-to-a-rowstore-table-with-a-clustered-index"></a>E. Convertire una tabella columnstore in una tabella rowstore con un indice cluster  
 Per convertire una tabella columnstore in una tabella rowstore con un indice cluster, usare l'istruzione CREATE INDEX con l'opzione DROP_EXISTING.  
  
```  
CREATE CLUSTERED INDEX ci_MyTable   
ON MyFactTable  
WITH ( DROP EXISTING = ON );  
```  
  
### <a name="f-convert-a-columnstore-table-to-a-rowstore-heap"></a>F. Convertire una tabella columnstore in un heap rowstore  
 Per convertire una tabella rowstore in un heap rowstore, eliminare l'indice columnstore cluster.  
  
```  
DROP INDEX MyCCI   
ON MyFactTable;  
```  
  

### <a name="g-defragment-by-rebuilding-the-entire-clustered-columnstore-index"></a>G. Deframmentare ricompilando l'intero indice columnstore cluster  
   Si applica a: SQL Server 2014  
  
 Sono disponibili due modi per ricompilare l'indice columnstore cluster per intero. È possibile usare CREATE CLUSTERED COLUMNSTORE INDEX, o [ALTER INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-index-transact-sql.md) e l'opzione REBUILD. Entrambi i metodi raggiungono gli stessi risultati.  
  
> [!NOTE]  
>  A partire da SQL Server 2016, usare ALTER INDEX REORGANIZE invece di ricompilare con i metodi descritti in questo esempio.  
  
```  
--Determine the Clustered Columnstore Index name of MyDimTable.  
SELECT i.object_id, i.name, t.object_id, t.name   
FROM sys.indexes i   
JOIN sys.tables t  
ON (i.type_desc = 'CLUSTERED COLUMNSTORE')  
WHERE t.name = 'RowstoreDimTable';  
  
--Rebuild the entire index by using CREATE CLUSTERED INDEX.  
CREATE CLUSTERED COLUMNSTORE INDEX my_CCI   
ON MyFactTable  
WITH ( DROP_EXISTING = ON );  
  
--Rebuild the entire index by using ALTER INDEX and the REBUILD option.  
ALTER INDEX my_CCI  
ON MyFactTable  
REBUILD PARTITION = ALL  
WITH ( DROP_EXISTING = ON );  
  
```  
  
##  <a name="nonclustered"></a>Esempi per gli indici columnstore non cluster  
  
### <a name="a-create-a-columnstore-index-as-a-secondary-index-on-a-rowstore-table"></a>A. Creare un indice columnstore come indice secondario in una tabella rowstore  
 In questo esempio viene creato un indice columnstore non cluster in una tabella rowstore. Un solo indice columnstore può essere creato in questa situazione. L'indice columnstore richiede memoria aggiuntiva in quanto contiene una copia dei dati nella tabella rowstore. In questo esempio viene creata una tabella semplice e un indice cluster, quindi viene illustrata la sintassi della creazione di un indice columnstore non cluster.  
  
```  
CREATE TABLE SimpleTable  
(ProductKey [int] NOT NULL,   
OrderDateKey [int] NOT NULL,   
DueDateKey [int] NOT NULL,   
ShipDateKey [int] NOT NULL);  
GO  
CREATE CLUSTERED INDEX cl_simple ON SimpleTable (ProductKey);  
GO  
CREATE NONCLUSTERED COLUMNSTORE INDEX csindx_simple  
ON SimpleTable  
(OrderDateKey, DueDateKey, ShipDateKey);  
GO  
```  
  
### <a name="b-create-a-simple-nonclustered-columnstore-index-using-all-options"></a>B. Creare un indice columnstore non cluster semplice tramite tutte le opzioni  
 Nell'esempio seguente viene illustrata la sintassi della creazione di un indice columnstore non cluster usando tutte le opzioni.  
  
```  
CREATE NONCLUSTERED COLUMNSTORE INDEX csindx_simple  
ON SimpleTable  
(OrderDateKey, DueDateKey, ShipDateKey)  
WITH (DROP_EXISTING =  ON,   
    MAXDOP = 2)  
ON "default"  
GO  
```  
  
 Per un esempio più complesso l'utilizzo di tabelle partizionate, vedere [panoramica degli indici Columnstore](../../relational-databases/indexes/columnstore-indexes-overview.md).  
  
### <a name="c-create-a-nonclustered-columnstore-index-with-a-filtered-predicate"></a>C. Creare un indice columnstore non cluster con un predicato filtrato  
 Nell'esempio seguente viene creato un indice columnstore non cluster filtrato nella tabella Production. billofmaterials il [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database. Il predicato del filtro può includere colonne che non sono colonne chiave nell'indice filtrato. Il predicato in questo esempio consente di selezionare solo le righe in cui EndDate non ha un valore NULL.  
  
```  
IF EXISTS (SELECT name FROM sys.indexes  
    WHERE name = N'FIBillOfMaterialsWithEndDate'   
    AND object_id = OBJECT_ID(N'Production.BillOfMaterials'))  
DROP INDEX FIBillOfMaterialsWithEndDate  
    ON Production.BillOfMaterials;  
GO  
CREATE NONCLUSTERED COLUMNSTORE INDEX "FIBillOfMaterialsWithEndDate"  
    ON Production.BillOfMaterials (ComponentID, StartDate)  
    WHERE EndDate IS NOT NULL;  
  
```  
  
###  <a name="ncDML"></a> D. Modificare i dati in un indice columnstore non cluster  
   Si applica a: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].
  
 Dopo aver creato un indice columnstore non cluster in una tabella, non è possibile modificare i dati direttamente nella tabella. Una query con INSERT, UPDATE, DELETE o MERGE non riesce e restituisce un messaggio di errore. Per aggiungere o modificare i dati nella tabella, è possibile effettuare una delle operazioni seguenti:  
  
-   Disabilitare o eliminare l'indice columnstore. È possibile aggiornare i dati nella tabella. Se si disabilita l'indice columnstore, è possibile ricompilare l'indice columnstore al termine dell'aggiornamento dei dati. Ad esempio,  
  
    ```  
    ALTER INDEX mycolumnstoreindex ON mytable DISABLE;  
    -- update mytable --  
    ALTER INDEX mycolumnstoreindex on mytable REBUILD  
    ```  
  
-   Caricare i dati in una tabella di gestione temporanea che non dispone di un indice columnstore. Compilare un indice columnstore nella tabella di gestione temporanea. Passare la tabella di gestione temporanea in una partizione vuota della tabella principale.  
  
-   Passare una partizione della tabella con l'indice columnstore in una tabella di gestione temporanea vuota. Se è presente un indice columnstore nella tabella di gestione temporanea, disabilitare l'indice columnstore. Eseguire gli aggiornamenti. Compilare o ricompilare l'indice columnstore. Passare la tabella di gestione temporanea nuovamente nella partizione (ora vuota) della tabella principale.  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-change-a-clustered-index-to-a-clustered-columnstore-index"></a>A. Modificare un indice cluster in un indice columnstore cluster  
 Utilizzando l'istruzione CREATE CLUSTERED COLUMNSTORE INDEX con DROP_EXISTING = ON, è possibile:  
  
-   Modificare un indice cluster in un indice columnstore cluster.  
  
-   Ricompilare un indice columnstore cluster.  
  
 In questo esempio viene creata la tabella xDimProduct come una tabella rowstore con un indice cluster e quindi creare indice COLUMNSTORE cluster viene utilizzato per modificare la tabella da una tabella rowstore in una tabella columnstore.  
  
```  
-- Uses AdventureWorks  
  
IF EXISTS (SELECT name FROM sys.tables  
    WHERE name = N'xDimProduct'  
    AND object_id = OBJECT_ID (N'xDimProduct'))  
DROP TABLE xDimProduct;  
  
--Create a distributed table with a clustered index.  
CREATE TABLE xDimProduct (ProductKey, ProductAlternateKey, ProductSubcategoryKey)  
WITH ( DISTRIBUTION = HASH(ProductKey),  
    CLUSTERED INDEX (ProductKey) )  
AS SELECT ProductKey, ProductAlternateKey, ProductSubcategoryKey FROM DimProduct;  
  
--Change the existing clustered index   
--to a clustered columnstore index with the same name.  
--Look up the name of the index before running this statement.  
CREATE CLUSTERED COLUMNSTORE INDEX <index_name>   
ON xdimProduct   
WITH ( DROP_EXISTING = ON );  
```  
  
### <a name="b-rebuild-a-clustered-columnstore-index"></a>B. Ricompilare un indice columnstore cluster  
 Compilazione dell'esempio precedente, questo esempio Usa CREATE CLUSTERED COLUMNSTORE INDEX per ricompilare l'indice columnstore cluster esistente denominato cci_xDimProduct.  
  
```  
--Rebuild the existing clustered columnstore index.  
CREATE CLUSTERED COLUMNSTORE INDEX cci_xDimProduct   
ON xdimProduct   
WITH ( DROP_EXISTING = ON );  
```  
  
### <a name="c-change-the-name-of-a-clustered-columnstore-index"></a>C. Modificare il nome di un indice columnstore cluster  
 Per modificare il nome di un indice columnstore cluster, eliminare l'indice columnstore cluster esistente e quindi ricreare l'indice con un nuovo nome.  
  
 È consigliabile solo esegue questa operazione con una tabella o una tabella vuota. Richiede molto tempo per eliminare un indice columnstore cluster di grandi dimensioni e ricompilare con un nome diverso.  
  
 Utilizzando l'indice columnstore cluster cci_xDimProduct dell'esempio precedente, in questo esempio viene eliminato l'indice columnstore cluster cci_xDimProduct e quindi ricrea l'indice columnstore cluster con il nome di mycci_xDimProduct.  
  
```  
--For illustration purposes, drop the clustered columnstore index.   
--The table continues to be distributed, but changes to a heap.  
DROP INDEX cci_xdimProduct ON xDimProduct;  
  
--Create a clustered index with a new name, mycci_xDimProduct.  
CREATE CLUSTERED COLUMNSTORE INDEX mycci_xDimProduct  
ON xdimProduct  
WITH ( DROP_EXISTING = OFF );  
```  
  
### <a name="d-convert-a-columnstore-table-to-a-rowstore-table-with-a-clustered-index"></a>D. Convertire una tabella columnstore in una tabella rowstore con un indice cluster  
 Potrebbe esserci un problema per cui si desidera eliminare un indice columnstore cluster e creare un indice cluster. Questo archivia la tabella nel formato rowstore. In questo esempio converte una tabella columnstore in una tabella rowstore con un indice cluster con lo stesso nome. Nessuno dei dati vengono perso. Tutti i dati vengono inseriti nella tabella rowstore e le colonne elencate più colonne chiave nell'indice cluster.  
  
```  
--Drop the clustered columnstore index and create a clustered rowstore index.   
--All of the columns are stored in the rowstore clustered index.   
--The columns listed are the included columns in the index.  
CREATE CLUSTERED INDEX cci_xDimProduct    
ON xdimProduct (ProductKey, ProductAlternateKey, ProductSubcategoryKey, WeightUnitMeasureCode)  
WITH ( DROP_EXISTING = ON);  
  
```  
  
### <a name="e-convert-a-columnstore-table-back-to-a-rowstore-heap"></a>E. Convertire una tabella columnstore nuovamente in un heap rowstore  
 Utilizzare [DROP INDEX (SQL Server PDW)](http://msdn.microsoft.com/en-us/f59cab43-9f40-41b4-bfdb-d90e80e9bf32) per eliminare l'indice columnstore cluster e convertire la tabella in un heap rowstore. Nell'esempio seguente la tabella cci_xDimProduct in un heap rowstore. La tabella continua a essere distribuita, ma viene archiviata come heap.  
  
```  
--Drop the clustered columnstore index. The table continues to be distributed, but changes to a heap.  
DROP INDEX cci_xdimProduct ON xdimProduct;  
```  


