---
title: CREARE una tabella (Azure SQL Data Warehouse) | Documenti Microsoft
ms.custom: 
ms.date: 07/14/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: 
ms.service: sql-data-warehouse
ms.component: t-sql|statements
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: ea21c73c-40e8-4c54-83d4-46ca36b2cf73
caps.latest.revision: "59"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 42b3f397fa93b2134594e10476138d5d30e0015f
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="create-table-azure-sql-data-warehouse"></a>CREARE una tabella (Azure SQL Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Crea una nuova tabella in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
 
Per comprendere le tabelle e sul loro utilizzo, vedere [nelle tabelle SQL Data Warehouse](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-tables-overview/).

Nota: Alle discussioni su SQL Data Warehouse in questo articolo si applicano a SQL Data Warehouse sia Parallel Data Warehouse se non diversamente specificato. 
 
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

<a name="Syntax"></a>   
## <a name="syntax"></a>Sintassi  
  
```  
-- Create a new table. 
CREATE TABLE [ database_name . [ schema_name ] . | schema_name. ] table_name   
    ( 
      { column_name <data_type>  [ <column_options> ] } [ ,...n ]   
    )  
    [ WITH [ <table_option> [ ,...n ] ) ]  
[;]  
   
<column_options> ::=
    [ COLLATE Windows_collation_name ]  
    [ NULL | NOT NULL ] -- default is NULL  
    [ [ CONSTRAINT constraint_name ] DEFAULT constant_expression  ]
  
<table_option> ::= 
    {   
        CLUSTERED COLUMNSTORE INDEX --default for SQL Data Warehouse 
      | HEAP --default for Parallel Data Warehouse   
      | CLUSTERED INDEX ( { index_column_name [ ASC | DESC ] } [ ,...n ] ) -- default is ASC 
    }  
    { 
        DISTRIBUTION = HASH ( distribution_column_name ) 
      | DISTRIBUTION = ROUND_ROBIN -- default for SQL Data Warehouse
      | DISTRIBUTION = REPLICATE -- default for Parallel Data Warehouse
    }   
    | PARTITION ( partition_column_name RANGE [ LEFT | RIGHT ] -- default is LEFT  
        FOR VALUES ( [ boundary_value [,...n] ] ) )  
  
<data type> ::=   
      datetimeoffset [ ( n ) ]  
    | datetime2 [ ( n ) ]  
    | datetime  
    | smalldatetime  
    | date  
    | time [ ( n ) ]  
    | float [ ( n ) ]  
    | real [ ( n ) ]  
    | decimal [ ( precision [ , scale ] ) ]   
    | numeric [ ( precision [ , scale ] ) ]   
    | money  
    | smallmoney  
    | bigint  
    | int   
    | smallint  
    | tinyint  
    | bit  
    | nvarchar [ ( n | max ) ]  -- max applies only to SQL Data Warehouse 
    | nchar [ ( n ) ]  
    | varchar [ ( n | max )  ] -- max applies only to SQL Data Warehouse  
    | char [ ( n ) ]  
    | varbinary [ ( n | max ) ] -- max applies only to SQL Data Warehouse  
    | binary [ ( n ) ]  
    | uniqueidentifier  
```  

<a name="Arguments"></a>   
## <a name="arguments"></a>Argomenti  
 *database_name*  
 Il nome del database che conterrà la nuova tabella. Il valore predefinito è il database attuale.  
  
 *schema_name*  
 Schema della tabella. Specifica di *schema* è facoltativo. Se vuoto, verrà utilizzato lo schema predefinito.  
  
 *table_name*  
 Il nome della nuova tabella. Per creare una tabella temporanea locale, anteporre al nome di tabella con #.  Per una spiegazione e informazioni aggiuntive su tabelle temporanee, vedere [tabelle temporanee in Azure SQL Data Warehouse](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-tables-temporary/). 
 
 *column_name*  
 Il nome di una colonna di tabella.
   
### <a name="ColumnOptions"></a>Opzioni colonne

 `COLLATE`*Windows_collation_name*  
 Specifica le regole di confronto per l'espressione. Le regole di confronto deve essere una delle regole di confronto di Windows supportate da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per un elenco di regole di confronto di Windows supportata da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [windows_collation_name (Transact-SQL)](http://msdn.microsoft.com/library/ms188046\(v=sql11\)/).  
  
 `NULL` | `NOT NULL`  
 Specifica se `NULL` sono consentiti valori nella colonna. Il valore predefinito è `NULL`.  
  
 [ `CONSTRAINT` *constraint_name* ] `DEFAULT` *constant_expression*  
 Specifica il valore predefinito della colonna.  
  
 | Argomento | Spiegazione |
 | -------- | ----------- |
 | *constraint_name* | Nome facoltativo per il vincolo. Il nome del vincolo è univoco all'interno del database. Il nome può essere riutilizzato in altri database. |
 | *constant_expression* | Il valore predefinito per la colonna. L'espressione deve essere un valore letterale o una costante. Ad esempio, queste espressioni costanti sono consentite: `'CA'`, `4`. Questi non sono consentiti: `2+3`, `CURRENT_TIMESTAMP`. |
  

### <a name="TableOptions"></a>Opzioni della struttura di tabella
Per indicazioni sulla scelta del tipo di tabella, vedere [l'indicizzazione di tabelle in Azure SQL Data Warehouse](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-tables-index/).
  
 `CLUSTERED COLUMNSTORE INDEX`  
Archiviare la tabella come indice columnstore cluster. L'indice columnstore cluster viene applicata a tutti i dati della tabella. Questo è il valore predefinito per [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].   
 
 `HEAP`   
  Archiviare la tabella come heap. Questo è il valore predefinito per [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
 `CLUSTERED INDEX`( *index_column_name* [,... *n* ] )  
 Archiviare la tabella come indice cluster con una o più colonne chiave. Questo archivia i dati di riga. Utilizzare *index_column_name* per specificare il nome di uno o più colonne chiave nell'indice.  Per ulteriori informazioni, vedere le tabelle Rowstore nella sezione Osservazioni generali.
 
 `LOCATION = USER_DB`   
 Questa opzione è deprecata. Sintatticamente viene accettata, ma non è più richiesto e non influisce sul comportamento.   
  
### <a name="TableDistributionOptions"></a>Opzioni di distribuzione di tabella
Per comprendere come scegliere il migliore metodo di distribuzione e usare tabelle distribuite, vedere [la distribuzione di tabelle in Azure SQL Data Warehouse](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-tables-distribute/).

`DISTRIBUTION = HASH`( *distribution_column_name* )   
Assegna ogni riga a una distribuzione mediante l'hashing il valore archiviato *distribution_column_name*. L'algoritmo è deterministica, ovvero che l'hashing viene sempre eseguito sullo stesso valore per la stessa distribuzione.  La colonna di distribuzione deve essere definita come NOT NULL, poiché tutte le righe verranno NULL è possibile assegnare la stessa distribuzione.

`DISTRIBUTION = ROUND_ROBIN`   
Distribuisce le righe in modo uniforme tra tutte le distribuzioni in uno schema round-robin. Questo è il valore predefinito per [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].

`DISTRIBUTION = REPLICATE`    
Archivia una copia della tabella in ogni nodo di calcolo. Per [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] la tabella è archiviata nei database di distribuzione in ogni nodo di calcolo. Per [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], la tabella è archiviata in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] filegroup che si estende il nodo di calcolo. Questo è il valore predefinito per [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].
  
### <a name="TablePartitionOptions"></a>Opzioni di partizione di tabella
Per informazioni sull'utilizzo di partizioni di tabella, vedere [partizionamento delle tabelle in SQL Data Warehouse](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-tables-partition/).

 `PARTITION`( *partition_column_name* `RANGE` [ `LEFT`  |  `RIGHT` ] `FOR VALUES` ([ *boundary_value* [,... *n*] ] ))   
Crea una o più partizioni di tabella. Questi sono intervalli orizzontali di tabelle che consentono di eseguire operazioni su subset di righe, indipendentemente dal fatto che la tabella viene archiviata come un heap, un indice cluster o un indice columnstore cluster. A differenza della colonna di distribuzione, le partizioni della tabella non determina la distribuzione in cui ogni riga viene archiviato. Al contrario, le partizioni della tabella determinano come le righe vengono raggruppate e archiviate all'interno di ogni distribuzione.  
 
| Argomento | Spiegazione |
| -------- | ----------- |
|*partition_column_name*| Specifica la colonna che [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] verrà utilizzato per suddividere le righe. Questa colonna può essere qualsiasi tipo di dati. [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]Ordina i valori della colonna di partizione in ordine crescente. L'ordinamento basso verso l'alto va da `LEFT` a `RIGHT` allo scopo del `RANGE` specifica. |  
| `RANGE LEFT` | Specifica che il valore limite appartiene alla partizione a sinistra (i valori più bassi). Il valore predefinito è LEFT. |
| `RANGE RIGHT` | Specifica che il valore limite appartiene alla partizione a destra (valori più elevati). | 
| `FOR VALUES`( *boundary_value* [,... *n*] ) | Specifica i valori limite per la partizione. *boundary_value* è un'espressione costante. Non può essere NULL. Deve corrispondere o essere convertibile in modo implicito nel tipo di dati di *partition_column_name*. Non può essere troncato durante la conversione implicita in modo che le dimensioni e la scala del valore non corrisponde al tipo di dati di *partition_column_name*<br></br><br></br>Se si specifica il `PARTITION` clausola, ma non si specifica un valore limite, [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] verrà creata una tabella partizionata con un'unica partizione. Se applicabile, è una suddivisione la tabella in due partizioni in un secondo momento.<br></br><br></br>Se si specifica un valore limite, la tabella risultante dispone di due partizioni. uno per i valori inferiori al valore limite e uno per i valori superiori al valore limite. Si noti che se si sposta una partizione in una tabella non partizionata, la tabella non partizionata riceverà i dati, ma non avrà i limiti delle partizioni nei relativi metadati.| 
 
 Vedere [creare una tabella partizionata](#PartitionedTable) nella sezione esempi.

### <a name="DataTypes"></a>Tipi di dati
[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]supporta l'uso più comune di tipi di dati. Di seguito è un elenco di tipi di dati supportati con i relativi dettagli e i byte di archiviazione. Per comprendere meglio i tipi di dati e sul loro utilizzo, vedere [ tipi di dati per le tabelle in SQL Data Warehouse](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-tables-data-types).

Per una tabella delle conversioni di tipi di dati, vedere la sezione conversioni implicite di [CAST e CONVERT (Transact-SQL)](http://msdn.microsoft.com/library/ms187928/).

`datetimeoffset` [ ( *n* ) ]  
 Il valore predefinito per  *n*  è 7.  
  
 `datetime2` [ ( *n* ) ]  
Uguale a `datetime`, ad eccezione del fatto che è possibile specificare il numero di secondi frazionari. Il valore predefinito per  *n*  è `7`.  
  
|*n*valore|Precisione|Scala|  
|--:|--:|-:|  
|`0`|19|0|  
|`1`|21|1|  
|`2`|22|2|  
|`3`|23|3|  
|`4`|24|4|  
|`5`|25|5|  
|`6`|26|6|  
|`7`|27|7|  
  
 `datetime`  
 Archivia data e ora del giorno con 19 e 23 caratteri in base al calendario gregoriano. La data può contenere anno, mese e giorno. L'ora contiene l'ora, minuti e secondi. In alternativa, è possibile visualizzare tre cifre per i secondi frazionari. Le dimensioni di archiviazione sono di 8 byte.  
  
 `smalldatetime`  
 Contiene una data e un'ora. Dimensioni di archiviazione sono 4 byte.  
  
 `date`  
 Archivia una data utilizzando un massimo di 10 caratteri per anno, mese e giorno in base al calendario gregoriano. Le dimensioni di archiviazione sono 3 byte. Data viene archiviata come un numero intero.  
  
 `time` [ ( *n* ) ]  
 Il valore predefinito per  *n*  è `7`.  
  
 `float` [ ( *n* ) ]  
 Tipo di dati numerici approssimati per l'utilizzo con dati numerici a virgola mobile. Dati a virgola mobile sono approssimativo, il che significa che non tutti i valori di vari tipi di dati possono essere rappresentati esattamente. *n*Specifica il numero di bit utilizzati per archiviare la mantissa del `float` in notazione scientifica. Pertanto,  *n*  determina la precisione e dimensioni di archiviazione. Se  *n*  è specificato, deve essere un valore compreso tra `1` e `53`. Il valore predefinito di  *n*  è `53`.  
  
| *n*valore | Precisione | Dimensioni dello spazio di archiviazione |  
| --------: | --------: | -----------: |  
| 1-24   | 7 cifre  | 4 byte      |  
| 25-53  | 15 cifre | 8 byte      |  
  
 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]considera  *n*  come uno dei due valori possibili. Se `1` <=   *n*   <=  `24`,  *n*  viene trattato come `24`. Se `25`  <=   *n*   <=  `53`,  *n*  viene trattato come `53`.  
  
 Il [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] `float` tipo di dati conforme allo standard ISO per tutti i valori di  *n*  da `1` tramite `53`. Il sinonimo di precisione doppia è `float(53)`.  
  
 `real` [ ( *n* ) ]  
 La definizione di reale è analogo a float. Il sinonimo di ISO per `real` è `float(24)`.  
  
 `decimal`[( *precisione* [ *, scala* ])] | `numeric` [( *precisione* [ *, scala* ])]  
 Archivia i numeri di precisione e scala fissato.  
  
 *precisione*  
 Numero massimo totale di cifre decimali che è possibile archiviare, sia a destra che a sinistra del separatore decimale. La precisione deve essere un valore da `1` e la precisione massima di `38`. La precisione predefinita è `18`.  
  
 *scala*  
 Numero massimo di cifre decimali che è possibile archiviare a destra del separatore decimale. *Scala* deve essere un valore da `0` tramite *precisione*. È possibile specificare solo *scala* se *precisione* specificato. La dimensione predefinita è `0`; pertanto, `0`  <=  *scala* <= *precisione*. Le dimensioni massime di archiviazione variano a seconda della precisione.  
  
| Precisione | Byte per l'archiviazione  |  
| ---------: |-------------: |  
|  1-9       |             5 |  
| 10-19      |             9 |  
| 20-28      |            13 |  
| 29-38      |            17 |  
  
 `money` | `smallmoney`  
 Tipi di dati che rappresentano i valori di valuta.  
  
| Tipo di dati | Byte per l'archiviazione |  
| --------- | ------------: |  
| `money`|8|  
| `smallmoney` |4|  
  
 `bigint` | `int` | `smallint` | `tinyint`  
 Tipi di dati numerici esatti che utilizzano dati integer. Lo spazio di archiviazione viene visualizzato nella tabella seguente.  
  
| Tipo di dati | Byte per l'archiviazione |  
| --------- | ------------: |  
| `bigint`|8|  
| `int` |4|  
| `smallint` |2|  
| `tinyint` |1|  
  
 `bit`  
 Tipo di dati integer che può accettare il valore di `1`, `0`, o ' NULL. [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]Ottimizza l'archiviazione di colonne di tipo bit. Se sono presenti un massimo di 8 colonne di tipo bit in una tabella, le colonne vengono archiviate come 1 byte. Se sono presenti colonne di 9 a 16 bit, le colonne vengono archiviate come 2 byte e così via.  
  
 `nvarchar`[(  *n*   |  `max` )]- `max` si applica solo a [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
 Dati Unicode di tipo carattere a lunghezza variabile. *n*può essere un valore compreso tra 1 e 4000. Tramite `max` viene indicato che la capacità di memorizzazione massima è di 2^31-1 byte (2 GB). Dimensioni di archiviazione in byte sono due volte il numero di caratteri immessi + 2 byte. La lunghezza dei dati immessi può essere uguale a 0 caratteri.  
  
 `nchar` [ ( *n* ) ]  
 Dati di tipo carattere Unicode a lunghezza fissa con lunghezza  *n*  caratteri. *n*deve essere un valore da `1` tramite `4000`. Le dimensioni di archiviazione sono pari al doppio  *n*  byte.  
  
 `varchar`[(  *n*    |  `max` )]- `max` si applica solo a [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].   
 Dati di tipo carattere non Unicode a lunghezza variabile con lunghezza  *n*  byte. *n*deve essere un valore da `1` a `8000`. `max`indica che le dimensioni massime di archiviazione sono 2 ^ 31-1 byte (2 GB). Le dimensioni di archiviazione sono la lunghezza effettiva dei dati immessi + 2 byte.  
  
 `char` [ ( *n* ) ]  
 Dati di tipo carattere non Unicode a lunghezza fissa con lunghezza  *n*  byte. *n*deve essere un valore da `1` a `8000`. Le dimensioni di archiviazione sono  *n*  byte. Il valore predefinito per  *n*  è `1`.  
  
 `varbinary`[(  *n*    |  `max` )]- `max` si applica solo a [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
 Dati binary a lunghezza variabile. *n*può essere un valore da `1` a `8000`. Tramite `max` viene indicato che la capacità di memorizzazione massima è di 2^31-1 byte (2 GB). Le dimensioni di archiviazione sono pari all'effettiva lunghezza dei dati immessi + 2 byte. Il valore predefinito per  *n*  è 7.  
  
 `binary` [ ( *n* ) ]  
 Dati binari a lunghezza fissa con lunghezza  *n*  byte. *n*può essere un valore da `1` a `8000`. Le dimensioni di archiviazione sono  *n*  byte. Il valore predefinito per  *n*  è `7`.  
  
 `uniqueidentifier`  
 GUID a 16 byte.  
   
<a name="Permissions"></a>  
## <a name="permissions"></a>Permissions  
 Creazione di una tabella richiede l'autorizzazione di `db_ddladmin` ruolo predefinito del database, o:
 - `CREATE TABLE`autorizzazione per il database
 - `ALTER SCHEMA`autorizzazione per lo schema che conterrà la tabella. 

Creazione di una tabella partizionata richiede l'autorizzazione di `db_ddladmin` ruolo predefinito del database, o

- `ALTER ANY DATASPACE`autorizzazione
  
 L'account di accesso che crea una tabella temporanea locale riceve `CONTROL`, `INSERT`, `SELECT`, e `UPDATE` autorizzazioni per la tabella.  
 
<a name="GeneralRemarks"></a>  
## <a name="general-remarks"></a>Osservazioni generali  
 
Per i limiti minimi e massimi, vedere [limiti della capacità di SQL Data Warehouse](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-service-capacity-limits/). 
 
### <a name="determining-the-number-of-table-partitions"></a>Determinazione del numero di partizioni della tabella
Ogni tabella definita dall'utente è suddivisa in più tabelle più piccole che vengono archiviate in posizioni diverse distribuzioni di chiamata. [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]utilizza le distribuzioni di 60. In [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], il numero di distribuzioni dipende dal numero di nodi di calcolo.
 
Ogni distribuzione contiene tutte le partizioni di tabella. Ad esempio, se sono presenti 60 distribuzioni e quattro le partizioni della tabella, esisterà 320 partizioni. Se la tabella è un indice columnstore cluster, saranno presenti un solo indice columnstore per ogni partizione, ovvero che si disporrà di 320 indici columnstore.

È consigliabile l'utilizzo di un minor numero di partizioni di tabella per verificare ogni indice columnstore ha un numero di righe sufficiente per poter sfruttare i vantaggi degli indici columnstore. Per ulteriori informazioni, vedere [partizionamento delle tabelle in SQL Data Warehouse](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-tables-partition/) e [l'indicizzazione di tabelle in SQL Data Warehouse](https://azure.microsoft.com/en-us/documentation/articles/sql-data-warehouse-tables-index/)  

  
 ### <a name="rowstore-table-heap-or-clustered-index"></a>Tabella Rowstore (indice heap o cluster)  
 Una tabella rowstore è una tabella archiviata in ordine di riga per riga. È un heap o indice cluster. [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]Crea tutte le tabelle rowstore con compressione di pagina. non è configurabile dall'utente.   
 
 ### <a name="columnstore-table-columnstore-index"></a>Tabella ColumnStore (indice columnstore)
Una tabella columnstore è una tabella archiviata in ordine di colonna per colonna. L'indice columnstore è la tecnologia che gestisce i dati archiviati in una tabella columnstore.  L'indice columnstore cluster non influisce sulla modalità di distribuzione dati; influisce su come i dati vengono archiviati all'interno di ogni distribuzione.

Per modificare una tabella rowstore in una tabella columnstore, eliminare tutti gli indici esistenti dalla tabella e creare un indice columnstore cluster. Per un esempio, vedere [CREATE COLUMNSTORE INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/create-columnstore-index-transact-sql.md).

Per altre informazioni, vedere gli articoli seguenti:
- [Riepilogo delle funzioni con controllo delle versioni di indici ColumnStore](https://msdn.microsoft.com/library/dn934994/)
- [L'indicizzazione di tabelle in SQL Data Warehouse](https://azure.microsoft.com/en-us/documentation/articles/sql-data-warehouse-tables-index/)
- [Guida agli indici columnstore](~/relational-databases/indexes/columnstore-indexes-overview.md) 
 
<a name="LimitationsRestrictions"></a>  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
 È possibile definire un vincolo predefinito su una colonna di distribuzione.  
  
 ### <a name="partitions"></a>Partizioni
 Quando l'utilizzo di partizioni, la colonna di partizione non può contenere regole di confronto solo Unicode. Ad esempio, l'istruzione seguente ha esito negativo.  
  
 `CREATE TABLE t1 ( c1 varchar(20) COLLATE Divehi_90_CI_AS_KS_WS) WITH (PARTITION (c1 RANGE FOR VALUES (N'')))`  
 
 Se *boundary_value* è un valore letterale che deve essere convertito in modo implicito nel tipo di dati in *partition_column_name*, si verificherà una discrepanza. Il valore letterale viene visualizzato tramite il [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] viste di sistema, ma il valore convertito viene utilizzato per [!INCLUDE[tsql](../../includes/tsql-md.md)] operazioni. 
 
  
 ### <a name="temporary-tables"></a>Tabelle temporanee
 Le tabelle temporanee globali che iniziano con # # non sono supportati.  
  
 Tabelle temporanee locali contengono le seguenti limitazioni e restrizioni:  
  
-   Sono visibili solo alla sessione corrente. [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]Rilascia automaticamente alla fine della sessione. Per eliminare explicitlt, utilizzare l'istruzione DROP TABLE.   
-   Non è possibile rinominare. 
-   Non possono avere partizioni o viste.  
-   Impossibile modificare le relative autorizzazioni. `GRANT`, `DENY`, e `REVOKE` non è possibile utilizzare le istruzioni con le tabelle temporanee locali.   
-   I comandi della console del database vengono bloccati per le tabelle temporanee.   
-   Se più di una tabella temporanea locale viene utilizzata all'interno di un batch, ognuna deve avere un nome univoco. Se l'esecuzione del batch stesso e la creazione della tabella temporanea locale stesso, più sessioni [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] aggiunge internamente un suffisso numerico al nome della tabella temporanea locale per gestire un nome univoco per ogni tabella temporanea locale.  
    
<a name="LockingBehavior"></a>   
## <a name="locking-behavior"></a>Comportamento di blocco  
 Accetta un blocco esclusivo sulla tabella. Acquisisce un blocco condiviso per gli oggetti DATABASE, schemi e SCHEMARESOLUTION.  
 

<a name="ExamplesColumn"></a>   
## <a name="examples-for-columns"></a>Esempi per le colonne

### <a name="ColumnCollation"></a> A. Specificare le regole di confronto colonna 
 Nell'esempio seguente, la tabella `MyTable` viene creato con due regole di confronto colonna diversa. Per impostazione predefinita, la colonna, `mycolumn1`, dispone di regole di confronto predefinite Latin1_General_100_CI_AS_KS_WS. La colonna, `mycolumn2` ha Frisian_100_CS_AS le regole di confronto.  
  
```  
CREATE TABLE MyTable   
  (  
    mycolumnnn1 nvarchar,  
    mycolumn2 nvarchar COLLATE Frisian_100_CS_AS )  
WITH ( CLUSTERED COLUMNSTORE INDEX )  
;  
  
```  
  
### <a name="DefaultConstraint"></a> B. Specificare un vincolo predefinito per una colonna  
 Nell'esempio seguente viene illustrata la sintassi per specificare un valore predefinito per una colonna. La colonna colA ha un vincolo predefinito denominato constraint_colA e un valore predefinito pari a 0.  
  
```  
  
CREATE TABLE MyTable   
  (  
    colA int CONSTRAINT constraint_colA DEFAULT 0,  
    colB nvarchar COLLATE Frisian_100_CS_AS   
  )  
WITH ( CLUSTERED COLUMNSTORE INDEX )  
;  
```  

<a name="ExamplesTemporaryTables"></a> 
## <a name="examples-for-temporary-tables"></a>Esempi per le tabelle temporanee

### <a name="TemporaryTable"></a> C. Creare una tabella temporanea locale  
 Di seguito crea una tabella temporanea locale denominata #myTable. La tabella è specificata con un nome composto da 3 parti. Il nome di tabella temporanea inizia con un simbolo #.   
  
```  
CREATE TABLE AdventureWorks.dbo.#myTable   
  (  
   id int NOT NULL,  
   lastName varchar(20),  
   zipCode varchar(6)  
  )  
WITH  
  (   
    DISTRIBUTION = HASH (id),  
    CLUSTERED COLUMNSTORE INDEX   
  )  
;  
```

<a name="ExTableStructure"></a>  
## <a name="examples-for-table-structure"></a>Esempi per la struttura della tabella

### <a name="ClusteredColumnstoreIndex"></a> D. Creare una tabella con un indice columnstore cluster  
 Nell'esempio seguente crea una tabella distribuita con un indice columnstore cluster. Ogni distribuzione verrà archiviati come columnstore.  
  
 L'indice columnstore cluster non influisce sulla modalità di distribuzione dei dati; dati sempre viene distribuiti per riga. L'indice columnstore cluster influisce sul modo in cui sono archiviati i dati all'interno di ogni distribuzione.  
  
```  
  
CREATE TABLE MyTable   
  (  
    colA int CONSTRAINT constraint_colA DEFAULT 0,  
    colB nvarchar COLLATE Frisian_100_CS_AS   
  )  
WITH   
  (   
    DISTRIBUTION = HASH ( colB ),  
    CLUSTERED COLUMNSTORE INDEX   
  )  
;  
```  
 
<a name="ExTableDistribution"></a> 
## <a name="examples-for-table-distribution"></a>Esempi per la distribuzione di tabella

### <a name="RoundRobin"></a> E. Creare una tabella ROUND_ROBIN  
 L'esempio seguente crea una tabella ROUND_ROBIN con tre colonne e senza partizioni. I dati vengono distribuiti tra tutte le distribuzioni. La tabella viene creata con un indice COLUMNSTORE cluster, che consente una migliore compressione dati e delle prestazioni rispetto a un indice heap o rowstore cluster.  
  
```  
CREATE TABLE myTable   
  (  
    id int NOT NULL,  
    lastName varchar(20),  
    zipCode varchar(6)  
  )  
WITH ( CLUSTERED COLUMNSTORE INDEX );  
```  
  
### <a name="HashDistributed"></a> F. Creare una tabella hash distribuita  
 Nell'esempio seguente crea la tabella stessa dell'esempio precedente. Tuttavia, per questa tabella, vengono distribuite le righe (nel `id` colonna) invece di distribuire in modo casuale come una tabella ROUND_ROBIN. La tabella viene creata con un indice COLUMNSTORE cluster, che consente una migliore compressione dati e delle prestazioni rispetto a un indice heap o rowstore cluster.  
  
```  
CREATE TABLE myTable   
  (  
    id int NOT NULL,  
    lastName varchar(20),  
    zipCode varchar(6)  
  )  
WITH  
  (   
    DISTRIBUTION = HASH (id),   
    CLUSTERED COLUMNSTORE INDEX  
  );  
```  
  
### <a name="Replicated"></a>G. Creare una tabella replicata  
 L'esempio seguente crea una tabella replicata simile agli esempi precedenti. Le tabelle replicate vengono copiate in modo completo per ogni nodo di calcolo. Con questa copia in ogni nodo di calcolo, lo spostamento dei dati verrà ridotte per le query. In questo esempio viene creato con un indice cluster, che offre una migliore compressione dei dati a un heap e non può contenere un numero di righe sufficiente per ottenere buoni risultati con indice COLUMNSTORE cluster.  
  
```  
CREATE TABLE myTable   
  (  
    id int NOT NULL,  
    lastName varchar(20),  
    zipCode varchar(6)  
  )  
WITH  
  (   
    DISTRIBUTION = REPLICATE,   
    CLUSTERED INDEX (lastName)  
  );  
```  

<a name="ExTablePartitions"></a> 
## <a name="examples-for-table-partitions"></a>Esempi per le partizioni di tabella

###  <a name="PartitionedTable"></a>H. Creare una tabella partizionata  
 L'esempio seguente crea la tabella stessa, come illustrato nell'esempio A, con l'aggiunta di partizionamento RANGE LEFT nel `id` colonna. Specifica i valori di limite di quattro partizioni, dando luogo a cinque partizioni.  
  
```  
CREATE TABLE myTable   
  (  
    id int NOT NULL,  
    lastName varchar(20),  
    zipCode int)  
WITH   
  (   
  
    PARTITION ( id RANGE LEFT FOR VALUES (10, 20, 30, 40 )),  
    CLUSTERED COLUMNSTORE INDEX      
  )  
;  
```  
  
 In questo esempio, i dati verranno ordinati in partizioni seguenti:  
  
-   Partizione 1: colonna < = 10   
-   Partizione 2:10 < col < = 20   
-   Partizione 3:20 < col < = 30   
-   Partizione 4:30 < col < = 40   
-   Partizione 5:40 < col  
  
 Se questa stessa tabella è stata partizionata RANGE RIGHT, invece di RANGE LEFT (impostazione predefinita), i dati verranno ordinati in partizioni seguenti:  
  
-   La partizione 1: col < 10  
-   Partizione 2:10 < = col < 20   
-   Partizione 3:20 < = col < 30    
-   Partizione 4:30 < = col < 40   
-   Partizione 5:40 < = col  
  
### <a name="OnePartition"></a>I. Creare una tabella partizionata con una partizione  
 L'esempio seguente crea una tabella partizionata con un'unica partizione. Non specifica alcun valore di limite, dando luogo a una partizione.  
  
```  
CREATE TABLE myTable (  
    id int NOT NULL,  
    lastName varchar(20),  
    zipCode int)  
WITH   
    (   
      PARTITION ( id RANGE LEFT FOR VALUES ( )),  
      CLUSTERED COLUMNSTORE INDEX  
    )  
;  
```  
  
### <a name="DatePartition"></a>J. Creare una tabella con il partizionamento di data  
 L'esempio seguente crea una nuova tabella denominata `myTable`, con il partizionamento in un `date` colonna. Per i valori limite, con date e RANGE RIGHT, inserisce un mese di dati in ogni partizione.  
  
```  
CREATE TABLE myTable (  
    l_orderkey      bigint,       
    l_partkey       bigint,                                             
    l_suppkey       bigint,                                           
    l_linenumber    bigint,        
    l_quantity      decimal(15,2),  
    l_extendedprice decimal(15,2),  
    l_discount      decimal(15,2),  
    l_tax           decimal(15,2),  
    l_returnflag    char(1),  
    l_linestatus    char(1),  
    l_shipdate      date,  
    l_commitdate    date,  
    l_receiptdate   date,  
    l_shipinstruct  char(25),  
    l_shipmode      char(10),  
    l_comment       varchar(44))  
WITH   
  (   
    DISTRIBUTION = HASH (l_orderkey),  
    CLUSTERED COLUMNSTORE INDEX,  
    PARTITION ( l_shipdate  RANGE RIGHT FOR VALUES   
      (  
        '1992-01-01','1992-02-01','1992-03-01','1992-04-01','1992-05-01',
        '1992-06-01','1992-07-01','1992-08-01','1992-09-01','1992-10-01',
        '1992-11-01','1992-12-01','1993-01-01','1993-02-01','1993-03-01',
        '1993-04-01','1993-05-01','1993-06-01','1993-07-01','1993-08-01',
        '1993-09-01','1993-10-01','1993-11-01','1993-12-01','1994-01-01',
        '1994-02-01','1994-03-01','1994-04-01','1994-05-01','1994-06-01',
        '1994-07-01','1994-08-01','1994-09-01','1994-10-01','1994-11-01',
        '1994-12-01'  
      ))
  );  
```  
  
<a name="SeeAlso"></a>    
## <a name="see-also"></a>Vedere anche 
 
 [CREATE TABLE AS SELECT &#40; Azure SQL Data Warehouse &#41;](../../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md)   
 [DROP TABLE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-table-transact-sql.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
  
  
