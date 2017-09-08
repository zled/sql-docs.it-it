---
title: CREATE TABLE AS SELECT (Azure SQL Data Warehouse) | Documenti Microsoft
ms.custom: 
ms.date: 10/07/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.service: sql-data-warehouse
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d1e08f88-64ef-4001-8a66-372249df2533
caps.latest.revision: 40
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2f95f9bc6975593f2536848e2bb3a2b346eca538
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="create-table-as-select-azure-sql-data-warehouse"></a>CREATE TABLE AS SELECT (Azure SQL Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

Crea tabella AS selezionare (un'istruzione CTAS) è uno dei più importanti funzionalità di T-SQL disponibili. È un'operazione completamente parallelizzata che crea una nuova tabella in base all'output di un'istruzione SELECT. Un'istruzione CTAS è il modo più semplice e rapido per creare una copia di una tabella.   
 
 Ad esempio, utilizzare un'istruzione CTAS per:  
  
-   Ricreare una tabella con una colonna di distribuzione hash diverso.
-   Ricreare una tabella come replicati.   
-   Creare un indice columnstore per solo alcune delle colonne nella tabella.  
-   Eseguire una query o importare dati esterni.  

> [!NOTE]  
> Poiché un'istruzione CTAS aggiunge le funzionalità di creazione di una tabella, in questo argomento tenta di non ripetere l'argomento di CREATE TABLE. In alternativa, descrive le differenze tra le istruzioni CREATE TABLE e di un'istruzione CTAS. Per i dettagli di CREATE TABLE, vedere [CREATE TABLE (Azure SQL Data Warehouse)](https://msdn.microsoft.com/library/mt203953/) istruzione. 
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
<a name="syntax-bk"></a>

## <a name="syntax"></a>Sintassi   

```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  

CREATE TABLE [ database_name . [ schema_name ] . | schema_name. ] table_name   
    [ ( column_name [ ,...n ] ) ]  
    WITH ( 
      <distribution_option> -- required
      [ , <table_option> [ ,...n ] ]    
    )  
    AS <select_statement>   
[;]  

<distribution_option> ::=
    { 
        DISTRIBUTION = HASH ( distribution_column_name ) 
      | DISTRIBUTION = ROUND_ROBIN 
      | DISTRIBUTION = REPLICATE
    }   

<table_option> ::= 
    {   
        CLUSTERED COLUMNSTORE INDEX --default for SQL Data Warehouse 
      | HEAP --default for Parallel Data Warehouse   
      | CLUSTERED INDEX ( { index_column_name [ ASC | DESC ] } [ ,...n ] ) --default is ASC 
    }  
    | PARTITION ( partition_column_name RANGE [ LEFT | RIGHT ] --default is LEFT  
        FOR VALUES ( [ boundary_value [,...n] ] ) ) 
  
<select_statement> ::=  
    [ WITH <common_table_expression> [ ,...n ] ]  
    SELECT select_criteria  

```  

<a name="arguments-bk"></a>
  
## <a name="arguments"></a>Argomenti  
Per informazioni dettagliate, vedere il [sezione argomenti](https://msdn.microsoft.com/library/mt203953/#Arguments) in CREATE TABLE.  

<a name="column-options-bk"></a>

### <a name="column-options"></a>Opzioni colonne
`column_name` [ ,...`n` ]   
 I nomi di colonna non consentono il [Opzioni colonne](https://msdn.microsoft.com/library/mt203953/#ColumnOptions) citate in CREATE TABLE.  In alternativa, è possibile fornire un elenco facoltativo di uno o più nomi di colonna per la nuova tabella. Le colonne nella nuova tabella utilizzerà i nomi specificati. Quando si specificano nomi di colonna, il numero di colonne nell'elenco di colonne deve corrispondere al numero di colonne nei risultati della selezione. Se non si specificano nomi di colonna, la nuova tabella di destinazione utilizzerà i nomi delle colonne di risultati dell'istruzione select. 
  
 È possibile specificare altre opzioni di colonna, ad esempio tipi di dati, le regole di confronto o null. Ognuno di questi attributi è derivato dai risultati del `SELECT` istruzione. Tuttavia, è possibile utilizzare l'istruzione SELECT per modificare gli attributi. Per un esempio, vedere [un'istruzione CTAS utilizzare per modificare gli attributi di colonna](#ctas-change-column-attributes-bk).   

<a name="table-distribution-options-bk"></a>

### <a name="table-distribution-options"></a>Opzioni di distribuzione di tabella

`DISTRIBUTION` = `HASH`( *distribution_column_name* ) | ROUND_ROBIN | LA REPLICA      
L'istruzione di un'istruzione CTAS richiede un'opzione di distribuzione e non dispone di valori predefiniti. Ciò è diverso da CREATE TABLE, che ha valori predefiniti. 

Per ulteriori informazioni e per comprendere come scegliere la colonna migliore di distribuzione, vedere il [tabella Opzioni di distribuzione](https://msdn.microsoft.com/library/mt203953/#TableDistributionOptions) sezione in CREATE TABLE. 

<a name="table-partition-options-bk"></a>

### <a name="table-partition-options"></a>Opzioni di partizione di tabella
L'istruzione di un'istruzione CTAS crea una tabella non partizionata per impostazione predefinita, anche se la tabella di origine è partizionata. Per creare una tabella partizionata con l'istruzione di un'istruzione CTAS, è necessario specificare l'opzione di partizione. 

Per informazioni dettagliate, vedere il [tabella Opzioni partizioni](https://msdn.microsoft.com/library/mt203953/#TablePartitionOptions) sezione in CREATE TABLE.

<a name="select-options-bk"></a>

### <a name="select-options"></a>Selezionare le opzioni
L'istruzione select è la differenza fondamentale tra un'istruzione CTAS e CREATE TABLE.  

 `WITH`*common_table_expression*  
 Indica un set di risultati denominato temporaneo, noto come espressione di tabella comune (CTE). Per ulteriori informazioni, vedere [con common_table_expression &#40; Transact-SQL &#41; ](../../t-sql/queries/with-common-table-expression-transact-sql.md).  
  
 `SELECT`*select_criteria*  
 Consente di popolare la nuova tabella con i risultati da un'istruzione SELECT. *select_criteria* è il corpo dell'istruzione SELECT che determina i dati da copiare nella nuova tabella. Per informazioni sulle istruzioni SELECT, vedere [SELECT &#40; Transact-SQL &#41; ](../../t-sql/queries/select-transact-sql.md).  
  
<a name="permissions-bk"></a>  
  
## <a name="permissions"></a>Permissions  
Richiede un'istruzione CTAS `SELECT` tutti gli oggetti a cui fa riferimento l'autorizzazione per la *select_criteria*.

Le autorizzazioni creare una tabella, vedere [autorizzazioni](https://msdn.microsoft.com/library/mt203953/#Permissions) in CREATE TABLE. 
  
<a name="general-remarks-bk"></a>
  
## <a name="general-remarks"></a>Osservazioni generali
Per informazioni dettagliate, vedere [osservazioni generali](https://msdn.microsoft.com/library/mt203953/#GeneralRemarks) in CREATE TABLE.

<a name="limitations-bk"></a>

## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
Azure SQL Data Warehouse esegue non è ancora supporto automatico crea o Aggiorna statistiche automatiche.  Per ottenere prestazioni ottimali da query, è importante creare statistiche per tutte le colonne di tutte le tabelle dopo avere eseguito un'istruzione CTAS e dopo le modifiche sostanziali vengono eseguiti nei dati. Per altre informazioni, vedere [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md).

[SET ROWCOUNT &#40; Transact-SQL &#41; ](../../t-sql/statements/set-rowcount-transact-sql.md) non ha alcun effetto in un'istruzione CTAS. Per ottenere un comportamento simile, utilizzare [torna all'inizio &#40; Transact-SQL &#41; ](../../t-sql/queries/top-transact-sql.md).  
 
Per informazioni dettagliate, vedere [limitazioni e restrizioni](https://msdn.microsoft.com/library/mt203953/#LimitationsRestrictions) in CREATE TABLE.

<a name="locking-behavior-bk"></a>
  
## <a name="locking-behavior"></a>Comportamento di blocco  
 Per informazioni dettagliate, vedere [il comportamento di blocco](https://msdn.microsoft.com/library/mt203953/#LockingBehavior) in CREATE TABLE.
 
<a name="performance-bk"></a>
 
 ## <a name="performance"></a>Prestazioni 

Per una tabella hash distribuita, è possibile utilizzare un'istruzione CTAS per scegliere una colonna di distribuzione diverso per ottenere prestazioni migliori di join e aggregazioni. Se si sceglie che una colonna di distribuzione diverso non è l'obiettivo, si avrà le migliori prestazioni di un'istruzione CTAS se si specifica la stessa colonna di distribuzione perché questo modo si evita nuovamente la distribuzione delle righe. 

Se si utilizza un'istruzione CTAS per creare una tabella e le prestazioni non costituiscono un fattore, è possibile specificare `ROUND_ROBIN` per evitare di dover decidere in una colonna di distribuzione.

Per evitare lo spostamento dei dati nelle query successive, è possibile specificare `REPLICATE` al costo di archiviazione maggiore per il caricamento di una copia completa della tabella in ogni nodo di calcolo.  


<a name="examples-copy-table-bk"></a>

## <a name="examples-for-copying-a-table"></a>Esempi per la copia di una tabella

<a name="ctas-copy-table-bk"></a>

### <a name="a-use-ctas-to-copy-a-table"></a>A. Utilizzare un'istruzione CTAS per copiare una tabella 
Si applica a: Azure SQL Data Warehouse e Parallel Data Warehouse

Forse una delle più comuni utilizzi di `CTAS` sta creando una copia di una tabella in modo che sia possibile modificare l'istruzione DDL. Se ad esempio originariamente creata la tabella come `ROUND_ROBIN` e si desidera modificarlo in una tabella in una colonna, `CTAS` è come cambiare la colonna di distribuzione. `CTAS`consente inoltre di modificare i tipi di partizionamento, l'indicizzazione o di colonna.

Si supponga che per creare questa tabella utilizzando il tipo di distribuzione predefinito di `ROUND_ROBIN` distribuiti dal momento cui è stata specificata alcuna colonna di distribuzione di `CREATE TABLE`.

```sql
CREATE TABLE FactInternetSales
(
    ProductKey int NOT NULL,
    OrderDateKey int NOT NULL,
    DueDateKey int NOT NULL,
    ShipDateKey int NOT NULL,
    CustomerKey int NOT NULL,
    PromotionKey int NOT NULL,
    CurrencyKey int NOT NULL,
    SalesTerritoryKey int NOT NULL,
    SalesOrderNumber nvarchar(20) NOT NULL,
    SalesOrderLineNumber tinyint NOT NULL,
    RevisionNumber tinyint NOT NULL,
    OrderQuantity smallint NOT NULL,
    UnitPrice money NOT NULL,
    ExtendedAmount money NOT NULL,
    UnitPriceDiscountPct float NOT NULL,
    DiscountAmount float NOT NULL,
    ProductStandardCost money NOT NULL,
    TotalProductCost money NOT NULL,
    SalesAmount money NOT NULL,
    TaxAmt money NOT NULL,
    Freight money NOT NULL,
    CarrierTrackingNumber nvarchar(25),
    CustomerPONumber nvarchar(25)
);
```

Ora si desidera creare una nuova copia di questa tabella con un indice columnstore cluster in modo che è possibile sfruttare le prestazioni delle tabelle columnstore cluster. Anche per distribuire la tabella nella ProductKey poiché si sono prevedendo join su questa colonna si desidera evitare lo spostamento dei dati durante l'unione in ProductKey join. Inoltre si desidera infine aggiungere partizionamento in OrderDateKey in modo che è possibile eliminare rapidamente dati precedenti l'eliminazione di partizioni precedenti. Di seguito è riportata l'istruzione di un'istruzione CTAS che copiava la vecchia tabella in una nuova tabella.

```sql
CREATE TABLE FactInternetSales_new
WITH
(
    CLUSTERED COLUMNSTORE INDEX,
    DISTRIBUTION = HASH(ProductKey),
    PARTITION
    (
        OrderDateKey RANGE RIGHT FOR VALUES
        (
        20000101,20010101,20020101,20030101,20040101,20050101,20060101,20070101,20080101,20090101,
        20100101,20110101,20120101,20130101,20140101,20150101,20160101,20170101,20180101,20190101,
        20200101,20210101,20220101,20230101,20240101,20250101,20260101,20270101,20280101,20290101
        )
    )
)
AS SELECT * FROM FactInternetSales;
```

Infine è possibile rinominare le tabelle per scambiare nella nuova tabella e quindi eliminare la tabella precedente.

```sql
RENAME OBJECT FactInternetSales TO FactInternetSales_old;
RENAME OBJECT FactInternetSales_new TO FactInternetSales;

DROP TABLE FactInternetSales_old;
```

<a name="examples-column-bk"></a>

## <a name="examples-for-column-options"></a>Esempi di Opzioni colonne

<a name="ctas-change-column-attributes-bk"></a>

### <a name="b-use-ctas-to-change-column-attributes"></a>B. Utilizzare un'istruzione CTAS per modificare gli attributi di colonna 
Si applica a: Azure SQL Data Warehouse e Parallel Data Warehouse

In questo esempio viene utilizzata un'istruzione CTAS per modificare i tipi di dati, ammissione di valori null e regole di confronto per più colonne nella tabella DimCustomer2.  
  
```  
-- Original table 
CREATE TABLE [dbo].[DimCustomer2] (  
    [CustomerKey] int NOT NULL,  
    [GeographyKey] int NULL,  
    [CustomerAlternateKey] nvarchar(15) COLLATE SQL_Latin1_General_CP1_CI_AS NOT NULL  
)  
WITH (CLUSTERED COLUMNSTORE INDEX, DISTRIBUTION = HASH([CustomerKey]));  
  
-- CTAS example to change data types, nullability, and column collations  
CREATE TABLE test  
WITH (HEAP, DISTRIBUTION = ROUND_ROBIN)  
AS  
SELECT  
    CustomerKey AS CustomerKeyNoChange,  
    CustomerKey*1 AS CustomerKeyChangeNullable,  
    CAST(CustomerKey AS DECIMAL(10,2)) AS CustomerKeyChangeDataTypeNullable,  
    ISNULL(CAST(CustomerKey AS DECIMAL(10,2)),0) AS CustomerKeyChangeDataTypeNotNullable,  
    GeographyKey AS GeographyKeyNoChange,  
    ISNULL(GeographyKey,0) AS GeographyKeyChangeNotNullable,  
    CustomerAlternateKey AS CustomerAlternateKeyNoChange,  
    CASE WHEN CustomerAlternateKey = CustomerAlternateKey 
        THEN CustomerAlternateKey END AS CustomerAlternateKeyNullable,  
    CustomerAlternateKey COLLATE Latin1_General_CS_AS_KS_WS AS CustomerAlternateKeyChangeCollation  
FROM [dbo].[DimCustomer2]  
  
-- Resulting table 
CREATE TABLE [dbo].[test] (
    [CustomerKeyNoChange] int NOT NULL, 
    [CustomerKeyChangeNullable] int NULL, 
    [CustomerKeyChangeDataTypeNullable] decimal(10, 2) NULL, 
    [CustomerKeyChangeDataTypeNotNullable] decimal(10, 2) NOT NULL, 
    [GeographyKeyNoChange] int NULL, 
    [GeographyKeyChangeNotNullable] int NOT NULL, 
    [CustomerAlternateKeyNoChange] nvarchar(15) COLLATE SQL_Latin1_General_CP1_CI_AS NOT NULL, 
    [CustomerAlternateKeyNullable] nvarchar(15) COLLATE SQL_Latin1_General_CP1_CI_AS NULL, 
    [CustomerAlternateKeyChangeCollation] nvarchar(15) COLLATE Latin1_General_CS_AS_KS_WS NOT NULL
)
WITH (DISTRIBUTION = ROUND_ROBIN);
```
 
Come passaggio finale, è possibile utilizzare [RIDENOMINAZIONE &#40; Transact-SQL &#41; ](../../t-sql/statements/rename-transact-sql.md) per passare i nomi di tabella. In questo modo DimCustomer2 può essere la nuova tabella.

```
RENAME OBJECT DimCustomer2 TO DimCustomer2_old;
RENAME OBJECT test TO DimCustomer2;

DROP TABLE DimCustomer2_old;
```

<a name="examples-table-distribution-bk"></a>

## <a name="examples-for-table-distribution"></a>Esempi per la distribuzione di tabella

<a name="ctas-change-distribution-method-bk"></a>

### <a name="c-use-ctas-to-change-the-distribution-method-for-a-table"></a>C. Utilizzare un'istruzione CTAS per modificare il metodo di distribuzione per una tabella
Si applica a: Azure SQL Data Warehouse e Parallel Data Warehouse

Questo semplice esempio viene illustrato come modificare il metodo di distribuzione per una tabella. Per visualizzare il meccanismo di come eseguire questa operazione, diventa una tabella hash distribuita round robin e diventa quindi la tabella round-robin hash distribuita. La tabella finale corrisponde alla tabella originale. 

Nella maggior parte dei casi non è necessario modificare una tabella hash distribuita a una tabella round-robin. Più spesso, potrebbe essere necessario modificare una tabella di round robin per una tabella di hash distribuita. Ad esempio, si potrebbe caricare inizialmente una nuova tabella come round robin e quindi spostarlo in seguito a una tabella hash distribuita per ottenere migliori prestazioni di join.

In questo esempio viene utilizzato il database di esempio AdventureWorksDW. Per caricare la versione di SQL Data Warehouse, vedere [caricare i dati di esempio in SQL Data Warehouse](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-load-sample-databases/)
 
```
-- DimSalesTerritory is hash-distributed.
-- Copy it to a round-robin table.
CREATE TABLE [dbo].[myTable]   
WITH   
  (   
    CLUSTERED COLUMNSTORE INDEX,  
    DISTRIBUTION = ROUND_ROBIN  
  )  
AS SELECT * FROM [dbo].[DimSalesTerritory]; 

-- Switch table names

RENAME OBJECT [dbo].[DimSalesTerritory] to [DimSalesTerritory_old];
RENAME OBJECT [dbo].[myTable] TO [DimSalesTerritory];

DROP TABLE [dbo].[DimSalesTerritory_old];

```  
Successivamente, modificarlo in una tabella di hash distribuita.

```
-- You just made DimSalesTerritory a round-robin table.
-- Change it back to the original hash-distributed table. 
CREATE TABLE [dbo].[myTable]   
WITH   
  (   
    CLUSTERED COLUMNSTORE INDEX,  
    DISTRIBUTION = HASH(SalesTerritoryKey) 
  )  
AS SELECT * FROM [dbo].[DimSalesTerritory]; 

-- Switch table names

RENAME OBJECT [dbo].[DimSalesTerritory] to [DimSalesTerritory_old];
RENAME OBJECT [dbo].[myTable] TO [DimSalesTerritory];

DROP TABLE [dbo].[DimSalesTerritory_old];
```
 
<a name="ctas-change-to-replicated-bk"></a>

### <a name="d-use-ctas-to-convert-a-table-to-a-replicated-table"></a>D. Utilizzare un'istruzione CTAS per convertire una tabella in una tabella replicata  
Si applica a: Azure SQL Data Warehouse e Parallel Data Warehouse 

Questo esempio viene applicato per la conversione di tabelle algoritmo round-robin o hash distribuita in una tabella replicata. Questo particolare esempio accetta il metodo di modificare il distribuzione tipo ulteriormente passaggio precedente.  DimSalesTerritory è una dimensione ed è probabile che una tabella più piccola, è possibile ricreare la tabella come replicati per evitare lo spostamento dei dati quando si uniscono ad altre tabelle. 

```
-- DimSalesTerritory is hash-distributed.
-- Copy it to a replicated table.
CREATE TABLE [dbo].[myTable]   
WITH   
  (   
    CLUSTERED COLUMNSTORE INDEX,  
    DISTRIBUTION = REPLICATE 
  )  
AS SELECT * FROM [dbo].[DimSalesTerritory]; 

-- Switch table names

RENAME OBJECT [dbo].[DimSalesTerritory] to [DimSalesTerritory_old];
RENAME OBJECT [dbo].[myTable] TO [DimSalesTerritory];

DROP TABLE [dbo].[DimSalesTerritory_old];
```
 
### <a name="e-use-ctas-to-create-a-table-with-fewer-columns"></a>E. Utilizzare un'istruzione CTAS per creare una tabella con un numero di colonne
Si applica a: Azure SQL Data Warehouse e Parallel Data Warehouse 

Nell'esempio seguente viene creata una tabella di distribuita round-robin denominata `myTable (c, ln)`. La nuova tabella ha solo due colonne. Utilizza gli alias di colonna nell'istruzione SELECT per i nomi delle colonne.  
  
```  
CREATE TABLE myTable  
WITH   
  (   
    CLUSTERED COLUMNSTORE INDEX,  
    DISTRIBUTION = ROUND_ROBIN  
  )  
AS SELECT CustomerKey AS c, LastName AS ln  
    FROM dimCustomer;  
  
```  

<a name="examples-query-hints-bk"></a>

## <a name="examples-for-query-hints"></a>Esempi per gli hint di query

<a name="ctas-query-hint-bk"></a>

### <a name="f-use-a-query-hint-with-create-table-as-select-ctas"></a>F. Utilizzare un Hint per la Query con CREATE TABLE AS selezionare (un'istruzione CTAS)  
Si applica a: Azure SQL Data Warehouse e Parallel Data Warehouse
  
Questa query Mostra la sintassi di base per l'utilizzo di un hint di join della query con l'istruzione di un'istruzione CTAS. Dopo che la query viene inviata, [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] si applica la strategia di join hash quando genera il piano di query per ogni distribuzione. Per ulteriori informazioni sull'hint per la query hash join, vedere [clausola OPTION &#40; Transact-SQL &#41; ](../../t-sql/queries/option-clause-transact-sql.md).  
  
```  
CREATE TABLE dbo.FactInternetSalesNew  
WITH   
  (   
    CLUSTERED COLUMNSTORE INDEX,  
    DISTRIBUTION = ROUND_ROBIN   
  )  
AS SELECT T1.* FROM dbo.FactInternetSales T1 JOIN dbo.DimCustomer T2  
ON ( T1.CustomerKey = T2.CustomerKey )  
OPTION ( HASH JOIN );  
```  

<a name="examples-external-tables"></a>

## <a name="examples-for-external-tables"></a>Esempi per le tabelle esterne

<a name="ctas-azure-blob-storage-bk"></a>

### <a name="g-use-ctas-to-import-data-from-azure-blob-storage"></a>G. Utilizzare un'istruzione CTAS per importare dati da archiviazione Blob di Azure  
Si applica a: Azure SQL Data Warehouse e Parallel Data Warehouse  

Per importare dati da una tabella esterna, usare CREATE TABLE AS SELECT per selezionare la tabella esterna. La sintassi per selezionare i dati da una tabella esterna in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] è uguale alla sintassi per la selezione di dati da una normale tabella.  
  
 L'esempio seguente definisce una tabella esterna ai dati in un account di archiviazione blob di Azure. Utilizza quindi CREATE TABLE AS SELECT per selezionare la tabella esterna. Questa importazione dei dati da file di testo delimitato da archiviazione blob di Azure e archivia i dati in un nuovo [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] tabella.  
  
```  
--Use your own processes to create the text-delimited files on Azure blob storage.  
--Create the external table called ClickStream.  
CREATE EXTERNAL TABLE ClickStreamExt (   
    url varchar(50),  
    event_date date,  
    user_IP varchar(50)  
)  
WITH (  
    LOCATION='/logs/clickstream/2015/',  
    DATA_SOURCE = MyAzureStorage,  
    FILE_FORMAT = TextFileFormat)  
;  
  
--Use CREATE TABLE AS SELECT to import the Azure blob storage data into a new   
--SQL Data Warehouse table called ClickStreamData  
CREATE TABLE ClickStreamData   
WITH  
  (  
    CLUSTERED COLUMNSTORE INDEX,  
    DISTRIBUTION = HASH (user_IP)  
  )  
AS SELECT * FROM ClickStreamExt  
;  
```  

<a name="ctas-import-Hadoop-bk"></a>
  
### <a name="h-use-ctas-to-import-hadoop-data-from-an-external-table"></a>H. Utilizzare un'istruzione CTAS per importare i dati di Hadoop da una tabella esterna  
Si applica a:[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
Per importare dati da una tabella esterna, usare CREATE TABLE AS SELECT per selezionare la tabella esterna. La sintassi per selezionare i dati da una tabella esterna in [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] è uguale alla sintassi per la selezione di dati da una normale tabella.  
  
 L'esempio seguente definisce una tabella esterna in un cluster Hadoop. Utilizza quindi CREATE TABLE AS SELECT per selezionare la tabella esterna. Questo Importa i dati dai file di testo delimitato di Hadoop e archivia i dati in un nuovo [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] tabella.  
  
```  
-- Create the external table called ClickStream.  
CREATE EXTERNAL TABLE ClickStreamExt (   
    url varchar(50),  
    event_date date,  
    user_IP varchar(50)  
)  
WITH (  
    LOCATION = 'hdfs://MyHadoop:5000/tpch1GB/employee.tbl',  
    FORMAT_OPTIONS ( FIELD_TERMINATOR = '|')  
)  
;  
  
-- Use your own processes to create the Hadoop text-delimited files 
-- on the Hadoop Cluster.  
  
-- Use CREATE TABLE AS SELECT to import the Hadoop data into a new 
-- table called ClickStreamPDW  
CREATE TABLE ClickStreamPDW   
WITH  
  (  
    CLUSTERED COLUMNSTORE INDEX,  
    DISTRIBUTION = HASH (user_IP)  
  )  
AS SELECT * FROM ClickStreamExt  
;   
```  
 
<a name="examples-workarounds-bk"></a>
 
## <a name="examples-using-ctas-to-replace-sql-server-code"></a>Esempi di utilizzo di un'istruzione CTAS per sostituire il codice di SQL Server

Utilizzare un'istruzione CTAS sopperire ad alcune funzionalità non supportate. Oltre a essere in grado di eseguire il codice nel data warehouse, riscrivere il codice esistente per l'utilizzo di un'istruzione CTAS in genere migliorerà le prestazioni. Questo è il risultato della progettazione completamente parallelizzato. 

> [!NOTE]
> Riflettere "un'istruzione CTAS prima". Se si ritiene che sia possibile risolvere un problema di mediante `CTAS` che viene in genere il modo migliore per affrontare, anche se si siano scrivendo più dati, di conseguenza.
>

<a name="ctas-replace-select-into-bk"></a>

### <a name="i-use-ctas-instead-of-selectinto"></a>I. Utilizzare un'istruzione CTAS anziché SELECT... IN  
Si applica a: Azure SQL Data Warehouse e Parallel Data Warehouse

Codice di SQL Server utilizza in genere SELECT... INTO per popolare una tabella con i risultati di un'istruzione SELECT. Questo è un esempio di un Server SQL SELECT... UN'istruzione.

```sql
SELECT *
INTO    #tmp_fct
FROM    [dbo].[FactInternetSales]
```

Questa sintassi non è supportata in SQL Data Warehouse e Parallel Data Warehouse. In questo esempio viene illustrato come riscrivere l'istruzione SELECT precedente... UN'istruzione come un'istruzione di un'istruzione CTAS. È possibile scegliere una delle opzioni di distribuzione descritte la sintassi di un'istruzione CTAS. In questo esempio viene utilizzato il metodo di distribuzione ROUND_ROBIN.

```sql
CREATE TABLE #tmp_fct
WITH
(
    DISTRIBUTION = ROUND_ROBIN
)
AS
SELECT  *
FROM    [dbo].[FactInternetSales]
;
```

<a name="ctas-replace-implicit-joins-bk"></a>

### <a name="j-use-ctas-and-implicit-joins-to-replace-ansi-joins-in-the-from-clause-of-an-update-statement"></a>J. Utilizzare un'istruzione CTAS e join implicito per sostituire i join ANSI nel `FROM` clausola di un `UPDATE` istruzione  
Si applica a: Azure SQL Data Warehouse e Parallel Data Warehouse  

È possibile che si dispone di un aggiornamento complesso che unisce in join più di due tabelle utilizzando la sintassi join ANSI per eseguire l'aggiornamento o eliminazione.

Si supponga che era necessario aggiornare la tabella:

```sql
CREATE TABLE [dbo].[AnnualCategorySales]
(   [EnglishProductCategoryName]    NVARCHAR(50)    NOT NULL
,   [CalendarYear]                  SMALLINT        NOT NULL
,   [TotalSalesAmount]              MONEY           NOT NULL
)
WITH
(
    DISTRIBUTION = ROUND_ROBIN
)
;
```

La query originale potrebbe siano presenti simile al seguente:

```sql
UPDATE  acs
SET     [TotalSalesAmount] = [fis].[TotalSalesAmount]
FROM    [dbo].[AnnualCategorySales]     AS acs
JOIN    (
        SELECT  [EnglishProductCategoryName]
        ,       [CalendarYear]
        ,       SUM([SalesAmount])              AS [TotalSalesAmount]
        FROM    [dbo].[FactInternetSales]       AS s
        JOIN    [dbo].[DimDate]                 AS d    ON s.[OrderDateKey]             = d.[DateKey]
        JOIN    [dbo].[DimProduct]              AS p    ON s.[ProductKey]               = p.[ProductKey]
        JOIN    [dbo].[DimProductSubCategory]   AS u    ON p.[ProductSubcategoryKey]    = u.[ProductSubcategoryKey]
        JOIN    [dbo].[DimProductCategory]      AS c    ON u.[ProductCategoryKey]       = c.[ProductCategoryKey]
        WHERE   [CalendarYear] = 2004
        GROUP BY
                [EnglishProductCategoryName]
        ,       [CalendarYear]
        ) AS fis
ON  [acs].[EnglishProductCategoryName]  = [fis].[EnglishProductCategoryName]
AND [acs].[CalendarYear]                = [fis].[CalendarYear]
;
```

Poiché SQL Data Warehouse non supporta ANSI unisce nel `FROM` clausola di un `UPDATE` istruzione, non è possibile utilizzare questo codice di SQL Server su senza modificarla leggermente.

È possibile utilizzare una combinazione di un `CTAS` e un join implicito per sostituire questo codice:

```sql
-- Create an interim table
CREATE TABLE CTAS_acs
WITH (DISTRIBUTION = ROUND_ROBIN)
AS
SELECT  ISNULL(CAST([EnglishProductCategoryName] AS NVARCHAR(50)),0)    AS [EnglishProductCategoryName]
,       ISNULL(CAST([CalendarYear] AS SMALLINT),0)                      AS [CalendarYear]
,       ISNULL(CAST(SUM([SalesAmount]) AS MONEY),0)                     AS [TotalSalesAmount]
FROM    [dbo].[FactInternetSales]       AS s
JOIN    [dbo].[DimDate]                 AS d    ON s.[OrderDateKey]             = d.[DateKey]
JOIN    [dbo].[DimProduct]              AS p    ON s.[ProductKey]               = p.[ProductKey]
JOIN    [dbo].[DimProductSubCategory]   AS u    ON p.[ProductSubcategoryKey]    = u.[ProductSubcategoryKey]
JOIN    [dbo].[DimProductCategory]      AS c    ON u.[ProductCategoryKey]       = c.[ProductCategoryKey]
WHERE   [CalendarYear] = 2004
GROUP BY
        [EnglishProductCategoryName]
,       [CalendarYear]
;

-- Use an implicit join to perform the update
UPDATE  AnnualCategorySales
SET     AnnualCategorySales.TotalSalesAmount = CTAS_ACS.TotalSalesAmount
FROM    CTAS_acs
WHERE   CTAS_acs.[EnglishProductCategoryName] = AnnualCategorySales.[EnglishProductCategoryName]
AND     CTAS_acs.[CalendarYear]               = AnnualCategorySales.[CalendarYear]
;

--Drop the interim table
DROP TABLE CTAS_acs
;
```

<a name="ctas-replace-ansi-joins-bk"></a>

### <a name="k-use-ctas-to-specify-which-data-to-keep-instead-of-using-ansi-joins-in-the-from-clause-of-a-delete-statement"></a>K. Utilizzare un'istruzione CTAS per specificare i dati da mantenere anziché ANSI join nella clausola FROM di un'istruzione DELETE  
Si applica a: Azure SQL Data Warehouse e Parallel Data Warehouse  

In alcuni casi l'approccio migliore per l'eliminazione dei dati consiste nell'utilizzare `CTAS`. Anziché l'eliminazione dei dati è sufficiente selezionare i dati di cui che si desidera mantenere. Questo particolarmente vero per `DELETE` le istruzioni che utilizzano ansi sintassi join poiché SQL Data Warehouse non supporta ANSI unisce nel `FROM` clausola di un `DELETE` istruzione.

Un esempio di un'istruzione DELETE convertito è riportato di seguito:

```sql
CREATE TABLE dbo.DimProduct_upsert
WITH
(   Distribution=HASH(ProductKey)
,   CLUSTERED INDEX (ProductKey)
)
AS -- Select Data you wish to keep
SELECT     p.ProductKey
,          p.EnglishProductName
,          p.Color
FROM       dbo.DimProduct p
RIGHT JOIN dbo.stg_DimProduct s
ON         p.ProductKey = s.ProductKey
;

RENAME OBJECT dbo.DimProduct        TO DimProduct_old;
RENAME OBJECT dbo.DimProduct_upsert TO DimProduct;
```

<a name="ctas-simplify-merge-bk"></a>

### <a name="l-use-ctas-to-simplify-merge-statements"></a>L. Utilizzare un'istruzione CTAS per semplificare le istruzioni merge  
Si applica a: Azure SQL Data Warehouse e Parallel Data Warehouse  

Le istruzioni merge possono essere sostituite, almeno in parte, utilizzando `CTAS`. È possibile consolidare il `INSERT` e `UPDATE` in una singola istruzione. Qualsiasi record eliminato dovranno essere chiuso in una seconda istruzione.

Un esempio di un `UPSERT` è riportato di seguito:

```sql
CREATE TABLE dbo.[DimProduct_upsert]
WITH
(   DISTRIBUTION = HASH([ProductKey])
,   CLUSTERED INDEX ([ProductKey])
)
AS
-- New rows and new versions of rows
SELECT      s.[ProductKey]
,           s.[EnglishProductName]
,           s.[Color]
FROM      dbo.[stg_DimProduct] AS s
UNION ALL  
-- Keep rows that are not being touched
SELECT      p.[ProductKey]
,           p.[EnglishProductName]
,           p.[Color]
FROM      dbo.[DimProduct] AS p
WHERE NOT EXISTS
(   SELECT  *
    FROM    [dbo].[stg_DimProduct] s
    WHERE   s.[ProductKey] = p.[ProductKey]
)
;

RENAME OBJECT dbo.[DimProduct]          TO [DimProduct_old];
RENAME OBJECT dbo.[DimpProduct_upsert]  TO [DimProduct];

```

<a name="ctas-data-type-and-nullability-bk"></a>

### <a name="m-explicitly-state-data-type-and-nullability-of-output"></a>M. In modo esplicito il tipo di dati dello stato e supporto di valori null dell'output  
Si applica a: Azure SQL Data Warehouse e Parallel Data Warehouse  

Durante la migrazione del codice di SQL Server a SQL Data Warehouse, è possibile che eseguire in questo tipo di modello di codifica:

```sql
DECLARE @d decimal(7,2) = 85.455
,       @f float(24)    = 85.455

CREATE TABLE result
(result DECIMAL(7,2) NOT NULL
)
WITH (DISTRIBUTION = ROUND_ROBIN)

INSERT INTO result
SELECT @d*@f
;
```

Si pensi istintivamente è necessario eseguire la migrazione di questo codice per una istruzione CTAS e sarebbe corretta. Tuttavia, è un problema di nascosto.

Il codice seguente non produce lo stesso risultato:

```sql
DECLARE @d decimal(7,2) = 85.455
,       @f float(24)    = 85.455
;

CREATE TABLE ctas_r
WITH (DISTRIBUTION = ROUND_ROBIN)
AS
SELECT @d*@f as result
;
```

Si noti che la colonna "risultato" estende i valori dei dati di tipo e il supporto di valori null dell'espressione. Questo può causare lievi variazioni nei valori se non si è attenzione.

Provare quanto segue come esempio:

```sql
SELECT result,result*@d
from result
;

SELECT result,result*@d
from ctas_r
;
```

Il valore archiviato per il risultato è diverso. Il valore persistente nella colonna dei risultati viene utilizzato in altre espressioni l'errore diventa ancora più significativo.

![CREATE TABLE AS SELECT risultati](../../t-sql/statements/media/create-table-as-select-results.png)

Ciò è particolarmente importante per le migrazioni di dati. Anche se la seconda query è probabilmente più precisa è un problema. I dati saranno diversi rispetto al sistema di origine e che comporta problemi di integrità della migrazione. Questo è uno dei rari casi in cui la risposta "errore" non è effettivamente quello corretto.

Il motivo che è possibile notare questo disparità tra i due risultati è down cast dei tipi impliciti. Nel primo esempio la tabella definisce la definizione di colonna. Quando viene inserita la riga si verifica una conversione implicita del tipo. Nel secondo esempio non è alcuna conversione implicita del tipo, come l'espressione definisce il tipo di dati della colonna. Si noti inoltre che la colonna nel secondo esempio è stata definita come una colonna che ammette valori null, mentre nel primo esempio ha non. Quando è stata creata la tabella in valori null prima colonna esempio è stata definita in modo esplicito. Nel secondo esempio che è stato appena uscito all'espressione e per impostazione predefinita questo comporta una definizione di NULL.  

Per risolvere questi problemi è necessario impostare esplicitamente la conversione del tipo e l'ammissione di valori null nel `SELECT` parte il `CTAS` istruzione. È possibile impostare queste proprietà nella parte create nella tabella.

Nell'esempio seguente viene illustrato come correggere il codice:

```sql
DECLARE @d decimal(7,2) = 85.455
,       @f float(24)    = 85.455

CREATE TABLE ctas_r
WITH (DISTRIBUTION = ROUND_ROBIN)
AS
SELECT ISNULL(CAST(@d*@f AS DECIMAL(7,2)),0) as result
```

Si noti quanto segue:
- CAST o CONVERT sarebbe stato possibile utilizzare
- ISNULL viene utilizzato per forzare l'ammissione di valori null non COALESCE
- ISNULL è la funzione più esterna
- La seconda parte di ISNULL è una costante, ovvero 0

> [!NOTE]
> Per il supporto di valori null da impostare in modo corretto, è importante utilizzare `ISNULL` e non `COALESCE`. `COALESCE`non è una funzione deterministica e pertanto il risultato dell'espressione sarà sempre ammette valori null. `ISNULL`è diverso. È deterministica. Pertanto quando la seconda parte di `ISNULL` funzione è una costante o un valore letterale, il valore risultante sarà non NULL.

Questo suggerimento non è utile solo per garantire l'integrità dei calcoli. È anche importante per il cambio partizione della tabella. Si supponga di che disporre di questa tabella definita come i fatti:

```sql
CREATE TABLE [dbo].[Sales]
(
    [date]      INT     NOT NULL
,   [product]   INT     NOT NULL
,   [store]     INT     NOT NULL
,   [quantity]  INT     NOT NULL
,   [price]     MONEY   NOT NULL
,   [amount]    MONEY   NOT NULL
)
WITH
(   DISTRIBUTION = HASH([product])
,   PARTITION   (   [date] RANGE RIGHT FOR VALUES
                    (20000101,20010101,20020101
                    ,20030101,20040101,20050101
                    )
                )
)
;
```

Tuttavia, il campo del valore è un'espressione calcolata non è parte dell'origine dati.

Per creare il set di dati partizionati, che è consigliabile eseguire questa operazione:

```sql
CREATE TABLE [dbo].[Sales_in]
WITH    
(   DISTRIBUTION = HASH([product])
,   PARTITION   (   [date] RANGE RIGHT FOR VALUES
                    (20000101,20010101
                    )
                )
)
AS
SELECT
    [date]    
,   [product]
,   [store]
,   [quantity]
,   [price]   
,   [quantity]*[price]  AS [amount]
FROM [stg].[source]
OPTION (LABEL = 'CTAS : Partition IN table : Create')
;
```

La query verrebbe eseguita ottimale. Il problema viene fornito quando si tenta di eseguire il cambio di partizione. Le definizioni di tabella non corrispondono. Per le definizioni di tabella in modo che corrispondano di un'istruzione CTAS deve essere modificata.

```sql
CREATE TABLE [dbo].[Sales_in]
WITH    
(   DISTRIBUTION = HASH([product])
,   PARTITION   (   [date] RANGE RIGHT FOR VALUES
                    (20000101,20010101
                    )
                )
)
AS
SELECT
    [date]    
,   [product]
,   [store]
,   [quantity]
,   [price]   
,   ISNULL(CAST([quantity]*[price] AS MONEY),0) AS [amount]
FROM [stg].[source]
OPTION (LABEL = 'CTAS : Partition IN table : Create');
```

È possibile vedere pertanto che la coerenza del tipo e la gestione di proprietà di supporto di valori null in una istruzione CTAS è buona norma migliore engineering. Consente di preservare l'integrità nei calcoli e garantisce inoltre che il cambio della partizione è possibile.
 
## <a name="see-also"></a>Vedere anche  
 [CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)   
 [CREATE EXTERNAL FILE FORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-file-format-transact-sql.md)   
 [CREATE EXTERNAL TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-transact-sql.md)   
 [CREATE EXTERNAL TABLE AS SELECT &#40; Transact-SQL &#41;](../../t-sql/statements/create-external-table-as-select-transact-sql.md)   
 [CREARE una tabella &#40; Azure SQL Data Warehouse &#41; ](../../t-sql/statements/create-table-azure-sql-data-warehouse.md) [DROP TABLE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-table-transact-sql.md)   
 [DROP EXTERNAL TABLE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-external-table-transact-sql.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [ALTER EXTERNAL TABLE &#40; Transact-SQL &#41;](http://msdn.microsoft.com/library/4ae1b23c-67f6-41d0-b614-7a8de914d145)  
  
  



