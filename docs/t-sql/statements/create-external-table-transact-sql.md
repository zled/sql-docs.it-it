---
title: CREATE EXTERNAL TABLE (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 11/27/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_EXTERNAL_TABLE
- CREATE EXTERNAL TABLE
- PolyBase, T-SQL
dev_langs:
- TSQL
helpviewer_keywords:
- External
- External, table create
- PolyBase, external table
ms.assetid: 6a6fd8fe-73f5-4639-9908-2279031abdec
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: e9ee131e1c4bb09ae19c90d84b78a7d6fc662ae8
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="create-external-table-transact-sql"></a>CREATE EXTERNAL TABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Crea una tabella esterna PolyBase che fa riferimento a dati archiviati in un cluster Hadoop o archiviazione blob di Azure. Può anche essere utilizzato per creare una tabella esterna per [query di Database elastico](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-overview/).  
  
 Utilizzare una tabella esterna per:  
  
-   Eseguire query sui dati di archiviazione blob Hadoop o Azure con [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzioni.  
  
-   Importare e archiviare i dati da Hadoop o Azure nell'archivio blob nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.  
  
-   Creare una tabella esterna per l'utilizzo con un Database elastico  
     query.  
     
- Importare e archiviare i dati dall'archivio Azure Data Lake in Azure SQL Data Warehouse
  
 Vedere anche [Crea origine dati esterna &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-data-source-transact-sql.md) e [DROP EXTERNAL TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/drop-external-table-transact-sql.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  

```  
-- Syntax for SQL Server 
  
-- Create a new external table  
CREATE EXTERNAL TABLE [ database_name . [ schema_name ] . | schema_name. ] table_name   
    ( <column_definition> [ ,...n ] )  
    WITH (   
        LOCATION = 'folder_or_filepath',  
        DATA_SOURCE = external_data_source_name,  
        FILE_FORMAT = external_file_format_name  
        [ , <reject_options> [ ,...n ] ]  
    )  
[;]  
  
<reject_options> ::=  
{  
    | REJECT_TYPE = value | percentage  
    | REJECT_VALUE = reject_value  
    | REJECT_SAMPLE_VALUE = reject_sample_value  
  
}  
  
-- Create a table for use with Elastic Database query  
CREATE EXTERNAL TABLE [ database_name . [ schema_name ] . | schema_name. ] table_name   
    ( <column_definition> [ ,...n ] )  
    WITH ( <sharded_external_table_options> )  
[;]  
  
<sharded_external_table_options> ::=  
        DATA_SOURCE = external_data_source_name,   
        SCHEMA_NAME = N'nonescaped_schema_name',  
        OBJECT_NAME = N'nonescaped_object_name',  
        [DISTRIBUTION  = SHARDED(sharding_column_name) | REPLICATED | ROUND_ROBIN]]  
    )  
[;]  
```  

```  
-- Syntax for Azure SQL Database
  
-- Create a table for use with Elastic Database query  
CREATE EXTERNAL TABLE [ database_name . [ schema_name ] . | schema_name. ] table_name   
    ( <column_definition> [ ,...n ] )  
    WITH ( <sharded_external_table_options> )  
[;]  
  
<sharded_external_table_options> ::=  
        DATA_SOURCE = external_data_source_name,   
        SCHEMA_NAME = N'nonescaped_schema_name',  
        OBJECT_NAME = N'nonescaped_object_name',  
        [DISTRIBUTION  = SHARDED(sharding_column_name) | REPLICATED | ROUND_ROBIN]]  
    )  
[;]  
```  


```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
-- Create a new external table in SQL Server PDW  
CREATE EXTERNAL TABLE [ database_name . [ schema_name ] . | schema_name. ] table_name   
    ( <column_definition> [ ,...n ] )  
    WITH (   
        LOCATION = 'hdfs_folder_or_filepath',  
        DATA_SOURCE = external_data_source_name,  
        FILE_FORMAT = external_file_format_name  
        [ , <reject_options> [ ,...n ] ]  
    )  
[;]  
  
<reject_options> ::=  
{  
    | REJECT_TYPE = value | percentage  
    | REJECT_VALUE = reject_value  
    | REJECT_SAMPLE_VALUE = reject_sample_value  
  
}  
```  
  
## <a name="arguments"></a>Argomenti  
 *database_name* . [schema_name]. | schema_name. ] *table_name*  
 Uno a tre - nome parte della tabella da creare. Per una tabella esterna, solo i metadati della tabella vengono archiviati in SQL insieme statistiche di base relative a file e o della cartella a cui fa riferimento nell'archiviazione blob di Hadoop o Azure. I dati effettivi non viene spostati o archiviati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 \<column_definition > [,...  *n*  ] CREATE EXTERNAL TABLE consente una o più definizioni di colonna. CREATE EXTERNAL TABLE e CREATE TABLE è possibile utilizzare la stessa sintassi per la definizione di una colonna. Un'eccezione, è possibile utilizzare il vincolo predefinito nelle tabelle esterne. Per informazioni dettagliate sulle definizioni di colonna e i relativi tipi di dati, vedere [CREATE TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-table-transact-sql.md) e [crea una tabella nel Database SQL di Azure](http://msdn.microsoft.com/library/d53c529a-1d5f-417f-9a77-64ccc6eddca1).  
  
 Le definizioni di colonna, inclusi i tipi di dati e il numero di colonne devono corrispondere ai dati in file esterni. Se è presente una mancata corrispondenza, quando si eseguono query i dati effettivi verranno rifiutate le righe di file.  
  
 Per le tabelle esterne che fanno riferimento a origini dati esterne, è necessario eseguire le definizioni di colonna e digitare il mapping allo schema esatto del file esterno. Quando si definiscono i tipi di dati che fanno riferimento a dati archiviati in Hadoop/Hive, usare i seguenti mapping tra tipi di dati SQL e Hive e il cast del tipo in un tipo di dati SQL quando si seleziona da esso. Se non specificato diversamente, i tipi includono tutte le versioni di Hive.

> [!NOTE]  
>  SQL Server non supporta l'Hive _infinito_ valore dei dati in alcuna conversione. PolyBase avrà esito negativo con un errore di conversione di tipo di dati.


|Tipo di dati SQL|Tipo di dati .NET|Tipo di dati hive|Tipo di dati Hadoop/Java|Commenti|  
|-------------------|--------------------|--------------------|----------------------------|--------------|  
|tinyint|Byte|tinyint|ByteWritable|Per i numeri senza segno.|  
|smallint|Int16|smallint|ShortWritable||  
|int|Int32|int|IntWritable||  
|bigint|Int64|bigint|LongWritable||  
|bit|Boolean|boolean|BooleanWritable||  
|float|Double|double|DoubleWritable||  
|real|Single|float|FloatWritable||  
|money|Decimal|double|DoubleWritable||  
|smallmoney|Decimal|double|DoubleWritable||  
|NCHAR|String<br /><br /> Char]|string|text||  
|nvarchar|String<br /><br /> Char]|string|Text||  
|char|String<br /><br /> Char]|string|Text||  
|varchar|String<br /><br /> Char]|string|Text||  
|BINARY|Byte[]|BINARY|BytesWritable|Si applica all'Hive 0,8 e versioni successive.|  
|varbinary|Byte[]|BINARY|BytesWritable|Si applica all'Hive 0,8 e versioni successive.|  
|data|DateTime|TIMESTAMP|TimestampWritable||  
|smalldatetime|DateTime|TIMESTAMP|TimestampWritable||  
|datetime2|DateTime|TIMESTAMP|TimestampWritable||  
|datetime|DateTime|TIMESTAMP|TimestampWritable||  
|time|TimeSpan|TIMESTAMP|TimestampWritable||  
|Decimal|Decimal|Decimal|BigDecimalWritable|Si applica a Hive0.11 e versioni successive.|  
  
 PERCORSO = '*folder_or_filepath*'  
 Specifica la cartella o il percorso del file e il nome di file per i dati effettivi nell'archiviazione blob di Hadoop o Azure. Il percorso inizia dalla cartella radice. la cartella radice è il percorso di dati specificato nell'origine dati esterna.  
  
 Se si specifica una posizione per essere una cartella, una query di PolyBase che consente di selezionare la tabella esterna recupererà i file dalla cartella e tutte le relative sottocartelle. Come Hadoop, PolyBase non restituisce le cartelle nascoste. Non restituisce anche i file per cui il nome del file inizia con un carattere di sottolineatura (_) o un punto (.).  
  
 In questo esempio, se percorso = 'webdata /', una query di PolyBase restituirà le righe da MyData e mydata2.txt.  Non restituirà mydata3.txt perché è una sottocartella di una cartella nascosta. Non restituirà _hidden.txt perché è un file nascosto.  
  
 ![Dati ricorsivi per tabelle esterne](../../t-sql/statements/media/aps-polybase-folder-traversal.png "dati ricorsivi per tabelle esterne")  
  
 Per modificare l'impostazione predefinita e lettura solo nella cartella radice, impostare l'attributo \<polybase.recursive.traversal > su 'false' nel file di configurazione core-Site.Xml. Questo file si trova in `<SqlBinRoot>\Polybase\Hadoop\Conf with SqlBinRoot the bin root of SQl Server`. Ad esempio, `C:\\Program Files\\Microsoft SQL Server\\MSSQL13.XD14\\MSSQL\\Binn`.  
  
 DATA_SOURCE = *external_data_source_name*  
 Specifica il nome dell'origine dati esterna che contiene il percorso dei dati esterni. Questo percorso è l'archiviazione blob di Hadoop o Azure. Per creare un'origine dati esterna, utilizzare [CREATE EXTERNAL DATA SOURCE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-data-source-transact-sql.md).  
  
 FILE_FORMAT = *external_file_format_name*  
 Specifica il nome dell'oggetto formato di file esterno che archivia il metodo di compressione e tipo di file per i dati esterni. Per creare un formato di file esterno, usare [CREATE EXTERNAL FILE FORMAT &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-file-format-transact-sql.md).  
  
 Rifiutare opzioni  
 È possibile specificare i parametri di rifiuto che determinano come gestire PolyBase *dirty* Registra Recupera dall'origine dati esterna. Un record di dati viene considerato "dirty" se è il numero di colonne o i tipi di dati effettivi non corrispondono le definizioni delle colonne della tabella esterna.  
  
 Quando non si specifica o modificare i valori di rifiuto, PolyBase utilizza valori predefiniti. Queste informazioni sui parametri di rifiuto sono archiviate come metadati aggiuntivi quando si crea una tabella esterna con l'istruzione CREATE EXTERNAL TABLE.   Quando un'istruzione SELECT futuri o selezionare INTO SELECT seleziona dati dalla tabella esterna, PolyBase utilizzerà le opzioni di rifiuti per determinare il numero o la percentuale di righe che può essere rifiutata prima che la query effettiva non riesca. tramite tabelle annidate. La query restituirà risultati (parziali) fino a quando non viene superata la soglia di rifiuti; quindi, si verifica un errore con il messaggio di errore appropriato.  
  
 REJECT_TYPE = **valore** | percentuale  
 Chiarisce se l'opzione REJECT_VALUE è specificata come valore letterale o percentuale.  
  
 Valore  
 REJECT_VALUE è un valore letterale, non una percentuale. La query di PolyBase non riuscirà quando supera il numero di righe rifiutate *reject_value*.  
  
 Ad esempio, se REJECT_VALUE = 5 e REJECT_TYPE = valore, la query SELECT avrà esito negativo dopo il rifiuto di 5 righe di PolyBase.  
  
 Percentuale  
 REJECT_VALUE è una percentuale, non un valore letterale. Una query di PolyBase avrà esito negativo quando il *percentuale* di righe con errori supera *reject_value*. La percentuale di righe con errori viene calcolata a intervalli.  
  
 REJECT_VALUE = *reject_value*  
 Specifica il valore o la percentuale di righe che può essere rifiutata prima che la query ha esito negativo.  
  
 Per REJECT_TYPE = value, *reject_value* deve essere un numero intero compreso tra 0 e 2.147.483.647.  
  
 Per REJECT_TYPE = percentuale, *reject_value* deve essere un valore float compreso tra 0 e 100.  
  
 REJECT_SAMPLE_VALUE = *reject_sample_value*  
 Questo attributo è obbligatorio quando si specifica REJECT_TYPE = percentuale. Determina il numero di righe per tentare di recuperare prima la PolyBase ricalcoli la percentuale di righe rifiutate.  
  
 Il *reject_sample_value* parametro deve essere un numero intero compreso tra 0 e 2.147.483.647.  
  
 Ad esempio, se REJECT_SAMPLE_VALUE = 1000, PolyBase verrà calcolata la percentuale di righe con errori dopo che ha tentato di importare 1000 righe dal file di dati esterno. Se la percentuale di righe con errori è inferiore a *reject_value*, PolyBase tenteranno di recuperare un altro 1000 righe. Continua a ricalcolare la percentuale di righe con esito negativo dopo il tentativo di importare ogni 1000 righe di aggiuntive.  
  
> [!NOTE]  
>  Poiché PolyBase calcola la percentuale di righe con esito negativo a intervalli, la percentuale effettiva di righe può superare *reject_value*.  
  
 Esempio:  
  
 Questo esempio viene illustrato come le tre opzioni di rifiuto interagiscono tra loro. Ad esempio, se REJECT_TYPE = percentuale, REJECT_VALUE = 30 e REJECT_SAMPLE_VALUE = 100, potrebbe verificarsi il seguente scenario:  
  
-   PolyBase tenta di recuperare le prime 100 righe; 25 avranno esito negativo e 75 esito positivo.  
  
-   Percentuale di righe con errori viene calcolato come 25%, che è minore del valore di rifiuto pari al 30%. Di conseguenza, PolyBase continuerà il recupero dei dati dall'origine dati esterna.  
  
-   PolyBase tenta di caricare le righe successive 100; Questa volta 25 esito positivo e 75 esito negativo.  
  
-   Percentuale di righe con errori viene ricalcolato al 50%. La percentuale di righe con errori ha superato il valore di rifiuto di 30%.  
  
-   La query di PolyBase non riesce con righe rifiutate di 50% dopo un tentativo di restituire le prime 200 righe. Si noti che le righe corrispondenti sono state restituite prima della query di PolyBase rileva che è stata superata la soglia di rifiuto.  
  
 Opzioni tabella esterna partizionate  
 Specifica l'origine dati esterna (un'origine dati non SQL Server) e un metodo di distribuzione per il [query di Database elastico](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-overview/).  
  
 DATA_SOURCE  
 Un'origine dati esterna, ad esempio i dati archiviati in un File System di Hadoop, archiviazione blob di Azure, o un [gestore mappe partizioni](https://azure.microsoft.com/documentation/articles/sql-database-elastic-scale-shard-map-management/).  
  
 SCHEMA_NAME  
 La clausola SCHEMA_NAME offre la possibilità di eseguire il mapping di definizione di tabella esterna in una tabella in un altro schema nel database remoto. Consente di evitare ambiguità tra gli schemi che esistono in entrambi i database locali e remoti.  
  
 OBJECT_NAME  
 La clausola OBJECT_NAME offre la possibilità di associare la definizione della tabella esterna a una tabella con un nome diverso al database remoto. Consente di evitare ambiguità tra i nomi degli oggetti presenti in entrambi i database locali e remoti.  
  
 DISTRIBUZIONE  
 Facoltativa. Questo è solo necessario solo per i database di tipo SHARD_MAP_MANAGER. Controlla se una tabella viene considerata come una tabella partizionata o una tabella replicata. Con **SHARDED** (*nome di colonna*) le tabelle, i dati da tabelle diverse non si sovrappongano. **REPLICATI** specifica tabelle dispongano degli stessi dati in ogni partizione. **ROUND_ROBIN** indica che un metodo specifico dell'applicazione viene utilizzato per distribuire i dati.  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede le autorizzazioni utente:  
  
-   **CREATE TABLE**  
  
-   **MODIFICA QUALSIASI SCHEMA**  
  
-   **MODIFICARE QUALSIASI ORIGINE DATI ESTERNA**  
  
-   **MODIFICARE QUALSIASI FORMATO DI FILE ESTERNI**  

-   **CONTROLLO DATABASE**
  
 Si noti che l'account di accesso che crea l'origine dati esterna devono avere l'autorizzazione di lettura e scrittura all'origine dati esterna, che si trova nell'archiviazione blob di Hadoop o Azure.  


 > [!IMPORTANT]  

>  L'autorizzazione ALTER ANY EXTERNAL DATA SOURCE concede a qualsiasi entità la possibilità di creare e modificare qualsiasi oggetto di origine dati esterna e di conseguenza, concede inoltre la possibilità di accedere a tutte le credenziali con ambito database nel database. Questa autorizzazione deve essere considerata privilegi elevati e pertanto devono essere concesse solo a entità attendibili nel sistema.

## <a name="error-handling"></a>Gestione degli errori  
 Durante l'esecuzione dell'istruzione CREATE EXTERNAL TABLE, PolyBase tenta di connettersi all'origine dati esterna. Se il tentativo di connessione non riesce, l'istruzione avrà esito negativo e non verrà creata la tabella esterna. Può richiedere un minuto o più errori perché PolyBase Ritenta la connessione prima che alla fine della query del comando.  
  
## <a name="general-remarks"></a>Osservazioni generali  
 Negli scenari di query ad hoc, ad esempio selezionare dalla tabella esterna, PolyBase archivia le righe recuperate dall'origine dati esterna in una tabella temporanea. Dopo il completamento della query, PolyBase rimuove ed elimina la tabella temporanea. Nessun dato permanente è archiviato in tabelle SQL.  
  
 Al contrario, nello scenario di importazione, ad esempio selezionare in dalla tabella esterna, PolyBase archivia le righe recuperate dall'origine dati esterna come permanente dei dati nella tabella SQL. La nuova tabella viene creata durante l'esecuzione di query quando Polybase recupera dati esterni.  
  
 PolyBase può inserire alcuni del calcolo delle query in Hadoop per migliorare le prestazioni delle query. Viene eseguita la distribuzione del predicato. A tale scopo, specificare l'opzione del percorso Gestione risorse di Hadoop in [CREATE EXTERNAL DATA SOURCE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-data-source-transact-sql.md).  
  
 È possibile creare numerose tabelle esterne che fanno riferimento a origini dati esterne uguale o diverso.  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
 Nella versione CTP2, la funzionalità di esportazione è supportata, ad esempio, in modo permanente l'archiviazione di dati SQL nell'origine dati esterna. Questa funzionalità sarà disponibile in CTP3.  
  
 Poiché i dati per una tabella esterna risiedono disattivare il dispositivo, non è sotto il controllo di PolyBase e può essere modificata o rimossa in qualsiasi momento da un processo esterno. Per questo motivo, uery risultati rispetto a una tabella esterna non sono garantiti per essere deterministiche. La stessa query può restituire risultati diversi ogni volta che viene eseguito su una tabella esterna. Analogamente, con una query può non riuscire se i dati esterni viene rimosso o spostati.  
  
 È possibile creare più tabelle esterne che ogni riferimento a origini dati esterne diverse. Tuttavia, se si eseguono contemporaneamente query rispetto a diverse origini dati di Hadoop, ogni origine di Hadoop deve utilizzare la stessa impostazione di configurazione server di 'hadoop connectivity'. Ad esempio, è possibile eseguire contemporaneamente una query su un cluster Cloudera Hadoop e un cluster Hortonworks Hadoop poiché questi utilizzare diverse impostazioni di configurazione. Per le impostazioni di configurazione e combinazioni supportate, vedere [configurazione della connettività di PolyBase &#40; Transact-SQL &#41; ](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md).  
  
 Solo queste istruzioni Data Definition Language (DDL) sono consentite nelle tabelle esterne:  
  
-   CREATE TABLE e DROP TABLE  
  
-   STATISTICHE CREATE e DROP STATISTICS  
Nota: Creare e rilasciare le statistiche nelle tabelle esterne non sono supportate in Database SQL di Azure. 
  
-   CREATE VIEW e DROP VIEW  
  
 Costrutti e operazioni non supportate:  
  
-   Il vincolo predefinito per le colonne di tabella esterna  
  
-   Data Manipulation Language (DML) operazioni delete, insert e update  
  
 Limitazioni delle query:  
  
 PolyBase può utilizzare un massimo di file k 33 per ogni cartella durante l'esecuzione di query di PolyBase simultanee 32. Il numero massimo specificato include i file e le sottocartelle in ogni cartella HDFS. Se il livello di concorrenza è minore di 32, un utente può eseguire le query PolyBase sulle cartelle in HDFS che includono più di 33 file k. È consigliabile mantenere brevi i percorsi di file esterno e Usa non più di 30 file k per ogni cartella HDFS. Quando vengono fatto riferimento troppi file, potrebbe verificarsi un'eccezione di Java Virtual Machine (JVM) di memoria insufficiente.  

Legati alla larghezza della tabella: PolyBase in SQL Server 2016 ha un limite di larghezza di riga di 32KB, in base alla dimensione massima di una singola riga valida dalla definizione della tabella. Se la somma dello schema di colonne è maggiore di 32KB, PolyBase non sarà in grado di eseguire query sui dati. 

In SQL Data Warehouse, questa limitazione è stata aumentata a 1MB.


## <a name="locking"></a>Utilizzo di blocchi  
 Condiviso blocco sull'oggetto SCHEMARESOLUTION.  
  
## <a name="security"></a>Sicurezza  
 I file di dati per una tabella esterna viene archiviato nell'archiviazione blob di Hadoop o Azure. Questi file di dati vengono creati e gestiti dai propri processi. È responsabilità dell'utente per gestire la sicurezza dei dati esterni.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-create-an-external-table-with-data-in-text-delimited-format"></a>A. Creare una tabella esterna con i dati in formato testo delimitato.  
 Questo esempio mostra tutti i passaggi necessari per creare una tabella esterna che contiene i dati formattati nei file di testo delimitato. Definisce un'origine dati esterna *mydatasource* e un formato di file esterno *myfileformat*. Questi oggetti a livello di database vengono quindi fatto riferimento nell'istruzione CREATE EXTERNAL TABLE. Per ulteriori informazioni, vedere [CREATE EXTERNAL DATA SOURCE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-data-source-transact-sql.md) e [il formato di FILE esterno CREATE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-file-format-transact-sql.md).  
  
```  
  
CREATE EXTERNAL DATA SOURCE mydatasource  
WITH (  
    TYPE = HADOOP,  
    LOCATION = 'hdfs://xxx.xxx.xxx.xxx:8020'  
)  
  
CREATE EXTERNAL FILE FORMAT myfileformat  
WITH (  
    FORMAT_TYPE = DELIMITEDTEXT,   
    FORMAT_OPTIONS (FIELD_TERMINATOR ='|')  
);  
  
CREATE EXTERNAL TABLE ClickStream (   
    url varchar(50),  
    event_date date,  
    user_IP varchar(50)  
)  
WITH (  
        LOCATION='/webdata/employee.tbl',  
        DATA_SOURCE = mydatasource,  
        FILE_FORMAT = myfileformat  
    )  
;  
  
```  
  
### <a name="b-create-an-external-table-with-data-in-rcfile-format"></a>B. I dati in formato RCFile, creare una tabella esterna.  
 Questo esempio mostra tutti i passaggi necessari per creare una tabella esterna che contiene i dati formattati come RCFiles. Definisce un'origine dati esterna *mydatasource_rc* e un formato di file esterno *myfileformat_rc*. Questi oggetti a livello di database vengono quindi fatto riferimento nell'istruzione CREATE EXTERNAL TABLE. Per ulteriori informazioni, vedere [CREATE EXTERNAL DATA SOURCE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-data-source-transact-sql.md) e [il formato di FILE esterno CREATE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-file-format-transact-sql.md).  
  
```  
  
CREATE EXTERNAL DATA SOURCE mydatasource_rc  
WITH (  
    TYPE = HADOOP,  
    LOCATION = 'hdfs://xxx.xxx.xxx.xxx:8020'  
)  
  
CREATE EXTERNAL FILE FORMAT myfileformat_rc  
WITH (  
    FORMAT_TYPE = RCFILE,  
    SERDE_METHOD = 'org.apache.hadoop.hive.serde2.columnar.LazyBinaryColumnarSerDe'  
)  
;  
  
CREATE EXTERNAL TABLE ClickStream_rc (   
    url varchar(50),  
    event_date date,  
    user_ip varchar(50)  
)  
WITH (  
        LOCATION='/webdata/employee_rc.tbl',  
        DATA_SOURCE = mydatasource_rc,  
        FILE_FORMAT = myfileformat_rc  
    )  
;  
  
```  
  
### <a name="c-create-an-external-table-with-data-in-orc-format"></a>C. Creare una tabella esterna con dati in formato ORC.  
 Questo esempio mostra tutti i passaggi necessari per creare una tabella esterna che contiene i dati formattati come file ORC. Definisce un mydatasource_orc di origine dati esterna e un myfileformat_orc di formato di file esterno. Questi oggetti a livello di database vengono quindi fatto riferimento nell'istruzione CREATE EXTERNAL TABLE. Per ulteriori informazioni, vedere [CREATE EXTERNAL DATA SOURCE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-data-source-transact-sql.md) e [il formato di FILE esterno CREATE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-file-format-transact-sql.md).  
  
```  
  
CREATE EXTERNAL DATA SOURCE mydatasource_orc  
WITH (  
    TYPE = HADOOP,  
    LOCATION = 'hdfs://xxx.xxx.xxx.xxx:8020'  
)  
  
CREATE EXTERNAL FILE FORMAT myfileformat_orc  
WITH (  
    FORMAT = ORC,  
    COMPRESSION = 'org.apache.hadoop.io.compress.SnappyCodec'  
)  
;  
  
CREATE EXTERNAL TABLE ClickStream_orc (   
    url varchar(50),  
    event_date date,  
    user_ip varchar(50)  
)  
WITH (  
        LOCATION='/webdata/',  
        DATA_SOURCE = mydatasource_orc,  
        FILE_FORMAT = myfileformat_orc  
    )  
;  
  
```  
  
### <a name="d-querying-hadoop-data"></a>D. Eseguire query sui dati di Hadoop  
 Clickstream è una tabella esterna che si connette al file di testo delimitato employee.tbl in un cluster Hadoop. La query seguente aspetto simile a una query su una tabella standard. Tuttavia, questa query recupera i dati da Hadoop e quindi calcola il verrà generato.  
  
```  
SELECT TOP 10 (url) FROM ClickStream WHERE user_ip = 'xxx.xxx.xxx.xxx'  
;  
```  
  
### <a name="e-join-hadoop-data-with-sql-data"></a>E. Unire i dati di Hadoop con i dati SQL  
 Questa query è riconosciuto come un JOIN di standard in due tabelle SQL. La differenza è che PolyBase recupera i dati Clickstream da Hadoop e quindi si unisce in join alla tabella UrlDescription. Una tabella è una tabella esterna e l'altro è una tabella SQL standard.  
  
```  
SELECT url.description  
FROM ClickStream cs  
JOIN UrlDescription url ON cs.url = url.name  
WHERE cs.url = 'msdn.microsoft.com'  
;  
```  
  
### <a name="f-import-data-from-hadoop-into-a-sql-table"></a>F. Importare dati da Hadoop in una tabella SQL  
 Questo esempio viene creata una nuova tabella ms_user SQL che archivia in modo permanente il risultato di un join tra la tabella SQL standard *utente* e la tabella esterna *ClickStream*.  
  
```  
SELECT DISTINCT user.FirstName, user.LastName  
INTO ms_user  
FROM user INNER JOIN (  
    SELECT * FROM ClickStream WHERE cs.url = 'www.microsoft.com'  
    ) AS ms_user  
ON user.user_ip = ms.user_ip  
;  
  
```  
  
### <a name="g-create-an-external-table-for-a-sharded-data-source"></a>G. Creare una tabella esterna per un'origine dati partizionati  
 In questo esempio riesegue il mapping di una DMV remota a una tabella esterna utilizzando le clausole nome_schema e nome_oggetto.  
  
```  
CREATE EXTERNAL TABLE [dbo].[all_dm_exec_requests]([session_id] smallint NOT NULL,  
  [request_id] int NOT NULL,  
  [start_time] datetime NOT NULL,   
  [status] nvarchar(30) NOT NULL,  
  [command] nvarchar(32) NOT NULL,  
  [sql_handle] varbinary(64),  
  [statement_start_offset] int,  
  [statement_end_offset] int,  
  [cpu_time] int NOT NULL)  
WITH  
(  
  DATA_SOURCE = MyExtSrc,  
  SCHEMA_NAME = 'sys',  
  OBJECT_NAME = 'dm_exec_requests',  
  DISTRIBUTION=ROUND_ROBIN  
);   
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="h-importing-data-from-adls-into-azure-includessdwincludesssdw-mdmd"></a>H. Importazione di dati da ADLS in Azure[!INCLUDE[ssDW](../../includes/ssdw-md.md)]  
 
  
```  

-- These values come from your Azure Active Directory Application used to authenticate to ADLS
CREATE DATABASE SCOPED CREDENTIAL ADLUser 
WITH IDENTITY = '<clientID>@\<OAuth2.0TokenEndPoint>',
SECRET = '<KEY>' ;


CREATE EXTERNAL DATA SOURCE AzureDataLakeStore
WITH (TYPE = HADOOP,
      LOCATION = 'adl://pbasetr.azuredatalakestore.net'
)



CREATE EXTERNAL FILE FORMAT TextFileFormat 
WITH ( FORMATTYPE = DELIMITEDTEXT 
     , FORMATOPTIONS ( FIELDTERMINATOR = '|' 
                     , STRINGDELIMITER = '' 
                     , DATEFORMAT = 'yyyy-MM-dd HH:mm:ss.fff' 
                     , USETYPE_DEFAULT = FALSE 
                     ) 
    )


CREATE EXTERNAL TABLE [dbo].[DimProductexternal] 
( [ProductKey] [int] NOT NULL, 
  [ProductLabel] nvarchar NULL, 
  [ProductName] nvarchar NULL ) 
WITH ( LOCATION='/DimProduct/' , 
       DATA_SOURCE = AzureDataLakeStore , 
       FILE_FORMAT = TextFileFormat , 
       REJECT_TYPE = VALUE ,
       REJECT_VALUE = 0 ) ;


CREATE TABLE [dbo].[DimProduct] 
WITH (DISTRIBUTION = HASH([ProductKey] ) ) 
AS SELECT * FROM 
[dbo].[DimProduct_external] ; 
     
```  
  
### <a name="i-join-external-tables"></a>I. Join di tabelle esterne  
  
```  
SELECT url.description  
FROM ClickStream cs  
JOIN UrlDescription url ON cs.url = url.name  
WHERE cs.url = 'msdn.microsoft.com'  
;  
```  
  
### <a name="j-join-hdfs-data-with-pdw-data"></a>J. Unire i dati HDFS con i dati PDW  
  
```  
SELECT cs.user_ip FROM ClickStream cs  
JOIN User u ON cs.user_ip = u.user_ip  
WHERE cs.url = 'www.microsoft.com'  
;  
  
```  
  
### <a name="k-import-row-data-from-hdfs-into-a-distributed-pdw-table"></a>K. Importare i dati delle righe da HDFS in una tabella PDW distribuita  
  
```  
CREATE TABLE ClickStream_PDW  
WITH ( DISTRIBUTION = HASH (url) )  
AS SELECT url, event_date, user_ip FROM ClickStream  
;  
```  
  
### <a name="l-import-row-data-from-hdfs-into-a-replicated-pdw-table"></a>L. Importare i dati delle righe da HDFS in una tabella replicata di PDW  
  
```  
CREATE TABLE ClickStream_PDW  
WITH ( DISTRIBUTION = REPLICATE )  
AS SELECT url, event_date, user_ip   
FROM ClickStream  
;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Esempi di Query di metadati comuni (SQL Server PDW)](http://msdn.microsoft.com/en-us/733fc99b-b9f6-4a29-b085-a1bd4f09f2ed)   
 [CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)   
 [CREATE EXTERNAL FILE FORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-file-format-transact-sql.md)   
 [CREATE EXTERNAL TABLE AS SELECT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-as-select-transact-sql.md)   
 [CREATE TABLE AS SELECT &#40; Azure SQL Data Warehouse &#41;](../../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md)  
  
  



