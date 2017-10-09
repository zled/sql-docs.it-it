---
title: CREARE una tabella (Transact-SQL) | Documenti Microsoft
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
- FILESTREAM_TSQL
- TABLE
- CREATE_TABLE_TSQL
- CREATE TABLE
- FILESTREAM
- TABLE_TSQL
- FILESTREAM_ON
- FILESTREAM_ON_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CHECK constraints
- global temporary tables [SQL Server]
- local temporary tables [SQL Server]
- size [SQL Server], tables
- UNIQUE constraints [SQL Server], creating
- constraints [SQL Server], columns
- maximum number of indexes per table
- number of tables per database
- number of indexes per table
- table creation [SQL Server], CREATE TABLE
- temporary tables [SQL Server], creating
- table size [SQL Server]
- nullability [SQL Server]
- partitioned tables [SQL Server], creating
- DEFAULT definition
- null values [SQL Server], columns
- number of rows per table
- maximum number of columns per table
- FOREIGN KEY constraints, creating
- PRIMARY KEY constraints
- number of bytes per row
- CREATE TABLE statement
- number of columns per table
- maximum number of bytes per row
ms.assetid: 1e068443-b9ea-486a-804f-ce7b6e048e8b
caps.latest.revision: 256
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0978041b1c2683f6af3f6c531ddc10edc6b9bcbf
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="create-table-transact-sql"></a>CREATE TABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Crea una nuova tabella in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
> [!NOTE]   
>  Per [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] sintassi, vedere [CREATE TABLE (Azure SQL Data Warehouse)](../../t-sql/statements/create-table-azure-sql-data-warehouse.md).
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
--Simple CREATE TABLE Syntax (common if not using options)  
CREATE TABLE   
    [ database_name . [ schema_name ] . | schema_name . ] table_name   
    ( { <column_definition> } [ ,...n ] )   
[ ; ]  
```  
  
## <a name="syntax"></a>Sintassi  
  
```  
--Disk-Based CREATE TABLE Syntax  
CREATE TABLE   
    [ database_name . [ schema_name ] . | schema_name . ] table_name   
    [ AS FileTable ]  
    ( {   <column_definition>   
        | <computed_column_definition>    
        | <column_set_definition>   
        | [ <table_constraint> ]   
        | [ <table_index> ] }  
          [ ,...n ]    
          [ PERIOD FOR SYSTEM_TIME ( system_start_time_column_name   
             , system_end_time_column_name ) ]  
      )  
    [ ON { partition_scheme_name ( partition_column_name )   
           | filegroup   
           | "default" } ]   
    [ TEXTIMAGE_ON { filegroup | "default" } ]   
    [ FILESTREAM_ON { partition_scheme_name   
           | filegroup   
           | "default" } ]  
    [ WITH ( <table_option> [ ,...n ] ) ]  
[ ; ]  
  
<column_definition> ::=  
column_name <data_type>  
    [ FILESTREAM ]  
    [ COLLATE collation_name ]   
    [ SPARSE ]  
    [ MASKED WITH ( FUNCTION = ' mask_function ') ]  
    [ CONSTRAINT constraint_name [ DEFAULT constant_expression ] ]   
    [ IDENTITY [ ( seed,increment ) ]  
    [ NOT FOR REPLICATION ]   
    [ GENERATED ALWAYS AS ROW { START | END } [ HIDDEN ] ]   
    [ NULL | NOT NULL ]  
    [ ROWGUIDCOL ]  
    [ ENCRYPTED WITH   
        ( COLUMN_ENCRYPTION_KEY = key_name ,  
          ENCRYPTION_TYPE = { DETERMINISTIC | RANDOMIZED } ,   
          ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256'  
        ) ]  
    [ <column_constraint> [ ...n ] ]   
    [ <column_index> ]  
  
<data type> ::=   
[ type_schema_name . ] type_name   
    [ ( precision [ , scale ] | max |   
        [ { CONTENT | DOCUMENT } ] xml_schema_collection ) ]   
  
<column_constraint> ::=   
[ CONSTRAINT constraint_name ]   
{     { PRIMARY KEY | UNIQUE }   
        [ CLUSTERED | NONCLUSTERED ]   
        [   
            WITH FILLFACTOR = fillfactor    
          | WITH ( < index_option > [ , ...n ] )   
        ]   
        [ ON { partition_scheme_name ( partition_column_name )   
            | filegroup | "default" } ]  
  
  | [ FOREIGN KEY ]   
        REFERENCES [ schema_name . ] referenced_table_name [ ( ref_column ) ]   
        [ ON DELETE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]   
        [ ON UPDATE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]   
        [ NOT FOR REPLICATION ]   
  
  | CHECK [ NOT FOR REPLICATION ] ( logical_expression )   
}   
  
<column_index> ::=   
 INDEX index_name [ CLUSTERED | NONCLUSTERED ]  
    [ WITH ( <index_option> [ ,... n ] ) ]  
    [ ON { partition_scheme_name (column_name )   
         | filegroup_name  
         | default   
         }  
    ]   
    [ FILESTREAM_ON { filestream_filegroup_name | partition_scheme_name | "NULL" } ]  
  
<computed_column_definition> ::=  
column_name AS computed_column_expression   
[ PERSISTED [ NOT NULL ] ]  
[   
    [ CONSTRAINT constraint_name ]  
    { PRIMARY KEY | UNIQUE }  
        [ CLUSTERED | NONCLUSTERED ]  
        [   
            WITH FILLFACTOR = fillfactor   
          | WITH ( <index_option> [ , ...n ] )  
        ]  
        [ ON { partition_scheme_name ( partition_column_name )   
        | filegroup | "default" } ]  
  
    | [ FOREIGN KEY ]   
        REFERENCES referenced_table_name [ ( ref_column ) ]   
        [ ON DELETE { NO ACTION | CASCADE } ]   
        [ ON UPDATE { NO ACTION } ]   
        [ NOT FOR REPLICATION ]   
  
    | CHECK [ NOT FOR REPLICATION ] ( logical_expression )   
]   
  
<column_set_definition> ::=  
column_set_name XML COLUMN_SET FOR ALL_SPARSE_COLUMNS  
  
< table_constraint > ::=  
[ CONSTRAINT constraint_name ]   
{   
    { PRIMARY KEY | UNIQUE }   
        [ CLUSTERED | NONCLUSTERED ]   
        (column [ ASC | DESC ] [ ,...n ] )   
        [   
            WITH FILLFACTOR = fillfactor   
           |WITH ( <index_option> [ , ...n ] )   
        ]  
        [ ON { partition_scheme_name (partition_column_name)  
            | filegroup | "default" } ]   
    | FOREIGN KEY   
        ( column [ ,...n ] )   
        REFERENCES referenced_table_name [ ( ref_column [ ,...n ] ) ]   
        [ ON DELETE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]   
        [ ON UPDATE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]   
        [ NOT FOR REPLICATION ]   
    | CHECK [ NOT FOR REPLICATION ] ( logical_expression )  
 

  
< table_index > ::=   
{  
    {  
      INDEX index_name [ CLUSTERED | NONCLUSTERED ]   
         (column_name [ ASC | DESC ] [ ,... n ] )   
    | INDEX index_name CLUSTERED COLUMNSTORE  
    | INDEX index_name [ NONCLUSTERED ] COLUMNSTORE (column_name [ ,... n ] )  
    }  
    [ WITH ( <index_option> [ ,... n ] ) ]   
    [ ON { partition_scheme_name (column_name )   
         | filegroup_name  
         | default   
         }  
    ]   
    [ FILESTREAM_ON { filestream_filegroup_name | partition_scheme_name | "NULL" } ]  
  
}   


<table_option> ::=  
{  
    [DATA_COMPRESSION = { NONE | ROW | PAGE }  
      [ ON PARTITIONS ( { <partition_number_expression> | <range> }   
      [ , ...n ] ) ]]  
    [ FILETABLE_DIRECTORY = <directory_name> ]   
    [ FILETABLE_COLLATE_FILENAME = { <collation_name> | database_default } ]  
    [ FILETABLE_PRIMARY_KEY_CONSTRAINT_NAME = <constraint_name> ]  
    [ FILETABLE_STREAMID_UNIQUE_CONSTRAINT_NAME = <constraint_name> ]  
    [ FILETABLE_FULLPATH_UNIQUE_CONSTRAINT_NAME = <constraint_name> ]  
    [ SYSTEM_VERSIONING = ON [ ( HISTORY_TABLE = schema_name . history_table_name  
        [, DATA_CONSISTENCY_CHECK = { ON | OFF } ] ) ] ]  
    [ REMOTE_DATA_ARCHIVE =   
      {   
          ON [ ( <table_stretch_options> [,...n] ) ]  
        | OFF ( MIGRATION_STATE = PAUSED )   
      }   
    ]  
}  
  
<table_stretch_options> ::=  
{  
     [ FILTER_PREDICATE = { null | table_predicate_function } , ]  
       MIGRATION_STATE = { OUTBOUND | INBOUND | PAUSED }  
 }  
  
<index_option> ::=  
{   
    PAD_INDEX = { ON | OFF }   
  | FILLFACTOR = fillfactor   
  | IGNORE_DUP_KEY = { ON | OFF }   
  | STATISTICS_NORECOMPUTE = { ON | OFF }   
  | ALLOW_ROW_LOCKS = { ON | OFF}   
  | ALLOW_PAGE_LOCKS ={ ON | OFF}   
  | COMPRESSION_DELAY= {0 | delay [Minutes]}  
  | DATA_COMPRESSION = { NONE | ROW | PAGE | COLUMNSTORE | COLUMNSTORE_ARCHIVE }  
       [ ON PARTITIONS ( { <partition_number_expression> | <range> }   
       [ , ...n ] ) ]  
}  
<range> ::=   
<partition_number_expression> TO <partition_number_expression>  
```  
  
```  
  
      --Memory optimized CREATE TABLE Syntax  
CREATE TABLE  
    [database_name . [schema_name ] . | schema_name . ] table_name  
    ( { <column_definition>  
    | [ <table_constraint> ] [ ,... n ]  
    | [ <table_index> ]  
      [ ,... n ] }   
      [ PERIOD FOR SYSTEM_TIME ( system_start_time_column_name   
        , system_end_time_column_name ) ]  
)  
    [ WITH ( <table_option> [ ,... n ] ) ]  
 [ ; ]  
  
<column_definition> ::=  
column_name <data_type>  
    [ COLLATE collation_name ]  
    [ GENERATED ALWAYS AS ROW { START | END } [ HIDDEN ] ]   
    [ NULL | NOT NULL ]  
[  
    [ CONSTRAINT constraint_name ] DEFAULT memory_optimized_constant_expression ]  
    | [ IDENTITY [ ( 1, 1 ) ]  
]  
    [ <column_constraint> ]  
    [ <column_index> ]  
  
<data type> ::=  
 [type_schema_name . ] type_name [ (precision [ , scale ]) ]  
  
<column_constraint> ::=  
 [ CONSTRAINT constraint_name ]  
{   
  { PRIMARY KEY | UNIQUE }    
      {   NONCLUSTERED   
        | NONCLUSTERED HASH WITH (BUCKET_COUNT = bucket_count)   
      }   
  | [ FOREIGN KEY ]   
        REFERENCES [ schema_name . ] referenced_table_name [ ( ref_column ) ]   
  | CHECK ( logical_expression )   
}  
  
< table_constraint > ::=  
 [ CONSTRAINT constraint_name ]  
{    
   { PRIMARY KEY | UNIQUE }  
     {   
       NONCLUSTERED (column [ ASC | DESC ] [ ,... n ])  
       | NONCLUSTERED HASH (column [ ,... n ] ) WITH ( BUCKET_COUNT = bucket_count )   
                    }   
    | FOREIGN KEY   
        ( column [ ,...n ] )   
        REFERENCES referenced_table_name [ ( ref_column [ ,...n ] ) ]   
    | CHECK ( logical_expression )   
}  
  
<column_index> ::=  
  INDEX index_name  
{ [ NONCLUSTERED ] | [ NONCLUSTERED ] HASH WITH (BUCKET_COUNT = bucket_count)  }  
  
<table_index> ::=  
  INDEX index_name  
{   [ NONCLUSTERED ] HASH (column [ ,... n ] ) WITH (BUCKET_COUNT = bucket_count)   
  | [ NONCLUSTERED ] (column [ ASC | DESC ] [ ,... n ] )   
      [ ON filegroup_name | default ]  
  | CLUSTERED COLUMNSTORE [WITH ( COMPRESSION_DELAY = {0 | delay [Minutes]})]  
      [ ON filegroup_name | default ]  
  
}  
  
<table_option> ::=  
{  
    MEMORY_OPTIMIZED = ON   
  | DURABILITY = {SCHEMA_ONLY | SCHEMA_AND_DATA}  
  | SYSTEM_VERSIONING = ON [ ( HISTORY_TABLE = schema_name . history_table_name  
        [, DATA_CONSISTENCY_CHECK = { ON | OFF } ] ) ]   
  
}  
```  
  
## <a name="arguments"></a>Argomenti  
 *database_name*  
 Nome del database in cui è viene creata la tabella. *database_name* deve specificare il nome di un database esistente. Se non specificato, *database_name* impostazioni predefinite per il database corrente. L'account di accesso per la connessione corrente deve essere associata a un ID utente esistente nel database specificato da *database_name*, e all'ID utente deve disporre delle autorizzazioni CREATE TABLE.  
  
 *schema_name*  
 Nome dello schema a cui appartiene la nuova tabella.  
  
 *table_name*  
 Nome della nuova tabella. I nomi di tabella devono seguire le regole per [identificatori](../../relational-databases/databases/database-identifiers.md). *TABLE_NAME* può contenere un massimo di 128 caratteri, ad eccezione dei nomi di tabella temporanea locale (i nomi preceduti da un solo simbolo di cancelletto (#)) che non può superare i 116 caratteri.  
  
 AS FileTable 
 
**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
 
 Consente di creare la nuova tabella come tabella FileTable. Non è necessario specificare le colonne, perché una tabella FileTable è associata a uno schema fisso. Per ulteriori informazioni su tabelle Filetable, vedere [FileTables &#40; SQL Server &#41; ](../../relational-databases/blob/filetables-sql-server.md).  
  
 *column_name*  
 *computed_column_expression*  
 Espressione che definisce il valore di una colonna calcolata. Una colonna calcolata è una colonna virtuale che non viene archiviata fisicamente nella tabella, a meno che non sia contrassegnata come PERSISTED. Questo tipo di colonna viene calcolata in base a un'espressione che utilizza altre colonne nella stessa tabella. Ad esempio, una colonna calcolata può avere la definizione: **costo** AS **prezzo** \* **qty**. L'espressione può essere un nome di colonna non calcolata, una costante, una funzione, una variabile e qualsiasi combinazione di questi elementi uniti da uno o più operatori. L'espressione non può essere una sottoquery o contenere tipi di dati alias.  
  
 È possibile usare le colonne calcolate in elenchi di selezione, clausole WHERE e ORDER BY o in qualsiasi altra posizione in cui è consentito l'utilizzo di espressioni regolari, con le eccezioni seguenti:  
  
-   Le colonne calcolate devono essere contrassegnate come PERSISTED per partecipare a un vincolo CHECK o FOREIGN KEY.  
  
-   È possibile usare una colonna calcolata come colonna chiave di un indice o come parte di un vincolo PRIMARY KEY o UNIQUE, a condizione che il valore della colonna sia definito da un'espressione deterministica e il tipo di dati del risultato sia supportato nelle colonne dell'indice.  
  
     Ad esempio, se la tabella include colonne di tipo integer **un** e **b**, la colonna calcolata **+ b** potrebbero essere indicizzati, ma non la colonna calcolata **+ DATEPART (dd, GETDATE**  non può essere indicizzata perché il valore potrebbe cambiare nelle chiamate successive.  
  
-   Non è possibile usare una colonna calcolata in un'istruzione INSERT o UPDATE.  
  
> [!NOTE]  
>  Ogni riga di una tabella può includere valori diversi per le colonne correlate a una colonna calcolata. È pertanto possibile che non sia disponibile lo stesso valore per ciascuna riga della colonna calcolata.  
  
 In base alle espressioni utilizzate, il supporto dei valori Null per le colonne calcolate viene determinato automaticamente da [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Si presuppone che il risultato della maggior parte delle espressioni ammetta valori Null anche se sono presenti solo colonne in cui tali valori non sono ammessi, perché anche i possibili underflow oppure overflow generano risultati NULL. Utilizzare la funzione COLUMNPROPERTY con la **AllowsNull** proprietà i valori null delle colonne calcolate in una tabella. Un'espressione che ammette valori null può essere convertita in uno di tali valori non specificando ISNULL con la *check_expression* costante, in cui la costante è un valore non null sostituito per qualsiasi risultato NULL. Per le colonne calcolate basate su espressioni di tipo CLR (Common Language Runtime) definito dall'utente è richiesta l'autorizzazione REFERENCES per il tipo.  
  
 PERSISTED  
 Specifica che [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] archivierà fisicamente i valori calcolati nella tabella e aggiornerà i valori in caso di aggiornamento di eventuali altre colonne da cui dipende la colonna calcolata. Quando si contrassegna una colonna calcolata come PERSISTED, è possibile creare un indice deterministico, ma non preciso, in una colonna calcolata. Per altre informazioni, vedere [Indici per le colonne calcolate](../../relational-databases/indexes/indexes-on-computed-columns.md). Le colonne calcolate utilizzate come colonne di partizionamento di una tabella partizionata devono essere contrassegnate con PERSISTED in modo esplicito. *computed_column_expression* deve essere deterministica se è specificato PERSISTED.  
  
 ON { *partition_scheme* | *filegroup* | **"**predefinito**"** }  

 Specifica lo schema di partizione o il filegroup in cui la tabella viene archiviata. Se *partition_scheme* viene specificato, la tabella deve essere una tabella partizionata con partizioni sono archiviate in un set di uno o più filegroup specificato in *partition_scheme*. Se *filegroup* viene specificato, la tabella è archiviata nel filegroup specificato. Il filegroup deve essere presente nel database. Se **"**predefinito**"** viene specificato, o se ON non è specificato, la tabella è archiviata nel filegroup predefinito. Il meccanismo di archiviazione di una tabella specificato in CREATE TABLE non può essere modificato in seguito.  
  
 ON {*partition_scheme* | *filegroup* | **"**predefinito**"**} può anche essere specificato in una chiave primaria o un vincolo UNIQUE. Questi vincoli comportano la creazione di indici. Se *filegroup* viene specificato, l'indice è archiviato nel filegroup specificato. Se **"**predefinito**"** viene specificato, o se ON non è specificato, l'indice viene archiviato nello stesso filegroup della tabella. Se il vincolo PRIMARY KEY o UNIQUE crea un indice cluster, le pagine di dati della tabella vengono archiviate nello stesso filegroup dell'indice. Se si specifica CLUSTERED o il vincolo in caso contrario viene creato un indice cluster e un *partition_scheme* viene specificato che è diverso dal *partition_scheme* o *filegroup* della definizione di tabella, o viceversa, verrà rispettata solo la definizione di vincolo e l'altro verrà ignorato.  
  
> [!NOTE]  
>  In questo contesto, default non è una parola chiave, È un identificatore per il filegroup predefinito e deve essere delimitato, ad esempio ON **"**predefinito**"** oppure ON **[**predefinito**]**. Se **"**predefinito**"** viene specificato, l'opzione QUOTED_IDENTIFIER deve essere impostata su ON per la sessione corrente. Si tratta dell'impostazione predefinita. Per altre informazioni, vedere [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md).  
  
> [!NOTE]  
>  Dopo avere creato una tabella partizionata, impostare l'opzione LOCK_ESCALATION per la tabella su AUTO. In questo modo è possibile migliorare la concorrenza consentendo ai blocchi di eseguire l'escalation a livello di partizione (HoBT) anziché di tabella. Per altre informazioni, vedere [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md).  
  
 TEXTIMAGE_ON { *filegroup*| **"**predefinito**"** }  
 Indica che il **testo**, **ntext**, **immagine**, **xml**, **varchar (max)**,  **nvarchar (max)**, **varbinary (max)**, e le colonne di tipo definito dall'utente CLR (inclusi geometry e geography) vengono archiviate nel filegroup specificato.  
  
 La parola chiave TEXTIMAGE_ON non è consentita se la tabella non include colonne con valori di grandi dimensioni. Non è possibile specificare TEXTIMAGE_ON se *partition_scheme* specificato. Se **"**predefinito**"** viene specificato, o se viene omessa in tutti, le colonne di valori di grandi dimensioni vengono archiviate nel filegroup predefinito. Il tipo di archiviazione per i dati di colonne con valori di grandi dimensioni specificato in CREATE TABLE non può essere modificato in seguito.  

> [!NOTE]  
> Varchar (max), nvarchar (max), varbinary (max), xml e valori UDT di grandi dimensioni vengono archiviate direttamente nella riga di dati, con un limite massimo di 8000 byte e purché il valore può corrispondere al record. Se il valore non rientra nel record, un puntatore viene ordinato in righe e il resto viene archiviato all'esterno della riga nello spazio di archiviazione LOB. 0 è il valore predefinito.
TEXTIMAGE_ON modifica solo la posizione di "spazio di archiviazione LOB", non si applica quando i dati sono archiviati nella riga. Utilizzare large value types out of row di sp_tableoption per archiviare l'intero valore LOB all'esterno delle righe. 


> [!NOTE]  
>  In questo contesto, default non è una parola chiave, È un identificatore per il filegroup predefinito e deve essere delimitato, ad esempio TEXTIMAGE_ON **"**predefinito**"** o TEXTIMAGE_ON **[**predefinito**]**. Se **"**predefinito**"** viene specificato, l'opzione QUOTED_IDENTIFIER deve essere impostata su ON per la sessione corrente. Si tratta dell'impostazione predefinita. Per altre informazioni, vedere [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md).  
  
 FILESTREAM_ON { *partition_scheme_name* | filegroup | **"**predefinito**"** } **si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. 
 
 Specifica il filegroup per i dati FILESTREAM.  
  
 Se la tabella è partizionata e contiene dati FILESTREAM, la clausola FILESTREAM_ON deve essere inclusa e deve specificare uno schema di partizione dei filegroup FILESTREAM che utilizzi la stessa funzione e le stesse colonne di partizione dello schema di partizione per la tabella. In caso contrario, verrà generato un errore.  
  
 Se la tabella non è partizionata, la colonna FILESTREAM non può essere partizionata. I dati FILESTREAM per la tabella devono essere archiviati in un singolo filegroup, specificato nella clausola FILESTREAM_ON.  
  
 Se la tabella non è partizionata e la clausola FILESTREAM_ON non è specificata, viene utilizzato il filegroup FILESTREAM per cui è impostata la proprietà DEFAULT. Se non è presente alcun filegroup FILESTREAM, viene generato un errore.  
  
-   Analogamente a ON e TEXTIMAGE_ON, il valore impostato utilizzando CREATE TABLE per FILESTREAM_ON non può essere modificato, ad eccezione dei casi seguenti:  
  
-   Oggetto [CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md) istruzione converte un heap in un indice cluster. In questo caso è possibile specificare un filegroup FILESTREAM diverso, uno schema di partizione o NULL.  
  
-   Oggetto [DROP INDEX](../../t-sql/statements/drop-index-transact-sql.md) istruzione converte un indice cluster in un heap. In questo caso, un filegroup FILESTREAM diverso, uno schema di partizione o **"**predefinito**"** può essere specificato.  
  
 Il filegroup nel `FILESTREAM_ON <filegroup>` clausola o ogni filegroup FILESTREAM denominato nello schema di partizione, è necessario un file definito per il filegroup. Questo file deve essere definito utilizzando un [CREATE DATABASE](../../t-sql/statements/create-database-sql-server-transact-sql.md) o [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md) istruzione; in caso contrario, viene generato un errore.  
  
 Per argomenti correlati a FILESTREAM, vedere [Binary Large Object &#40; BLOB &#41; Dati &#40; SQL Server &#41; ](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md).  
  
 [ *type_schema_name***.** ] *type_name*  
 Specifica il tipo di dati della colonna e lo schema a cui appartiene. Per le tabelle basate su disco, il tipo di dati può essere uno dei seguenti:  
  
-   Tipo di dati di sistema.  
  
-   Tipo di alias basato su un tipo di dati di sistema di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per consentirne l'utilizzo in una definizione di tabella, i tipi di dati alias vengono creati con l'istruzione CREATE TYPE. L'assegnazione NULL o NOT NULL per un tipo di dati alias può essere ignorata durante l'esecuzione dell'istruzione CREATE TABLE. Non è tuttavia possibile modificare l'impostazione della lunghezza. In un'istruzione CREATE TABLE non è possibile specificare la lunghezza per un tipo di dati alias.  
  
-   Tipo CLR definito dall'utente. I tipi CLR definiti dall'utente devono essere creati con l'istruzione CREATE TYPE prima di poterli usare in una definizione di tabella. Per creare una colonna con un tipo CLR definito dall'utente, è richiesta l'autorizzazione REFERENCES per il tipo.  
  
 Se *type_schema_name* non viene specificato, il [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] riferimenti *type_name* nell'ordine seguente:  
  
-   Tipo di dati di sistema di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Schema predefinito dell'utente corrente nel database corrente.  
  
-   Schema **dbo** nel database corrente.  
  
 Per le tabelle con ottimizzazione per la memoria, vedere [tipi di dati supportati per OLTP In memoria](../../relational-databases/in-memory-oltp/supported-data-types-for-in-memory-oltp.md) per un elenco di tipi di sistema supportati.  
  
 *precisione*  
 Precisione del tipo di dati specificato. Per ulteriori informazioni sui valori di precisione validi, vedere [precisione, scala e lunghezza](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
 *scala*  
 Scala per il tipo di dati specificato. Per ulteriori informazioni sui valori di scala validi, vedere [precisione, scala e lunghezza](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
 **Max**  
 Si applica solo al **varchar**, **nvarchar**, e **varbinary** tipi di dati per l'archiviazione di 2 ^ 31 byte di tipo carattere e dati binari e 2 ^ 30 byte di dati Unicode.  
  
 CONTENT  
 Specifica che ogni istanza di **xml** del tipo di dati *column_name* può contenere più elementi di livello superiore. Si applica solo al contenuto di **xml** dati digitare e può essere specificato solo se *xml_schema_collection* viene anche specificato. Se non specificato, CONTENT rappresenta il comportamento predefinito.  
  
 DOCUMENT  
 Specifica che ogni istanza di **xml** del tipo di dati *column_name* può contenere un solo elemento di primo livello. DOCUMENTO si applica solo al **xml** dati digitare e può essere specificato solo se *xml_schema_collection* viene anche specificato.  
  
 *xml_schema_collection*  
 Si applica solo al **xml** il tipo di dati per l'associazione con il tipo di una raccolta XML schema. Prima di digitare un **xml** colonna a uno schema, lo schema è necessario innanzitutto creare nel database utilizzando [CREATE XML SCHEMA COLLECTION](../../t-sql/statements/create-xml-schema-collection-transact-sql.md).  
  
 DEFAULT  
 Specifica il valore assegnato alla colonna quando non viene specificato un valore in modo esplicito durante un inserimento. Le definizioni DEFAULT possono essere applicate a tutte le colonne ad eccezione di quelli definiti come **timestamp**, o quelli con la proprietà IDENTITY. Se è specificato un valore predefinito per una colonna di tipo definito dall'utente, il tipo deve supportare una conversione implicita da *constant_expression* per il tipo definito dall'utente. Le definizioni DEFAULT vengono rimosse quando la tabella viene eliminata. È possibile usare come predefinito solo un valore costante, ad esempio una stringa di caratteri, una funzione scalare (una funzione di sistema, definita dall'utente o CLR) oppure un valore NULL. Per garantire la compatibilità con le versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è possibile assegnare un nome di vincolo a una definizione DEFAULT.  
  
 *constant_expression*  
 Costante, valore NULL o funzione di sistema utilizzata come valore predefinito della colonna.  
  
 *memory_optimized_constant_expression*  
 Costante, valore NULL o funzione di sistema utilizzata come valore predefinito della colonna. Deve essere supportata nelle stored procedure compilate in modo nativo. Per ulteriori informazioni sulle funzioni predefinite nelle stored procedure compilate in modo nativo, vedere [funzionalità supportate per moduli T-SQL compilati in modo nativo](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md).  
  
 IDENTITY  
 Indica che la nuova colonna è una colonna Identity. Quando si aggiunge una nuova riga alla tabella, [!INCLUDE[ssDE](../../includes/ssde-md.md)] assegna un valore univoco e incrementale alla colonna. Le colonne Identity vengono in genere utilizzate in combinazione con vincoli PRIMARY KEY come identificatori di riga univoci per la tabella. La proprietà IDENTITY può essere assegnata a **tinyint**, **smallint**, **int**, **bigint**, **decimal(p,0)**, o **numeric(p,0)** colonne. Ogni tabella può includere una sola colonna Identity. Non è consentito associare valori predefiniti e vincoli DEFAULT alle colonne Identity. È necessario specificare sia il valore di inizializzazione, sia l'incremento oppure nessuno dei due. In questo secondo caso, il valore predefinito è (1,1).  
  
 In una tabella con ottimizzazione per la memoria, l'unico valore consentito sia per *valore di inizializzazione* e *incremento* è 1. (1,1) è il valore predefinito per *valore di inizializzazione* e *incremento*.  
  
 *valore di inizializzazione*  
 Valore di inizializzazione utilizzato per la prima riga caricata nella tabella.  
  
 *incremento*  
 Valore incrementale aggiunto al valore Identity della riga caricata in precedenza.  
  
 NOT FOR REPLICATION  
 Nell'istruzione CREATE TABLE è possibile specificare la clausola NOT FOR REPLICATION per la proprietà IDENTITY, i vincoli FOREIGN KEY e i vincoli CHECK. Se si specifica questa clausola per la proprietà IDENTITY, i valori non vengono incrementati nelle colonne Identity per gli inserimenti eseguiti dagli agenti di replica. Se per un vincolo si specifica questa clausola, il vincolo non viene imposto quando gli agenti di replica eseguono le operazioni di inserimento, aggiornamento o eliminazione.  
  
 ATTRIBUTO GENERATED ALWAYS AS RIGA {START | TERMINARE} [NASCOSTO] [NON NULL]  
 **Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Specifica una colonna di tipo datetime2 specificato verrà utilizzata dal sistema per registrare l'ora di inizio per il quale un record è valido o l'ora di fine per il quale un record è valido. La colonna deve essere definita come NOT NULL. Se si tenta di specificarli come NULL, il sistema genererà un errore. Se non si specifica in modo esplicito non NULL per una colonna di periodo, il sistema sarà la colonna definita come NOT NULL per impostazione predefinita. Utilizzare questo argomento in combinazione con l'operazione PERIOD FOR SYSTEM_TIME e con SYSTEM_VERSIONING = ON argomenti per abilitare il controllo delle versioni di sistema in una tabella. Per altre informazioni, vedere [Temporal Tables](../../relational-databases/tables/temporal-tables.md).  
  
 È possibile contrassegnare una o entrambe le colonne del periodo con **HIDDEN** flag per nascondere in modo implicito le colonne in modo che **selezionare \* FROM**  *`<table>`*  non Restituisce un valore per tali colonne. Per impostazione predefinita, le colonne del periodo non vengono nascosti. Per poter essere usato, le colonne nascoste devono essere incluso in modo esplicito in tutte le query che fanno riferimento direttamente alla tabella temporale. Per modificare il **HIDDEN** attributo per una colonna di periodo esistente, **periodo** necessario eliminarlo e ricrearlo con un flag nascosto diversi.  
  
 `INDEX *index_name* [ CLUSTERED | NONCLUSTERED ] (*column_name* [ ASC | DESC ] [ ,... *n* ] )`  
     
**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].

Specifica per creare un indice nella tabella. Può trattarsi di un indice cluster o un indice non cluster. L'indice conterrà le colonne elencate e verrà ordinati i dati in ordine crescente o decrescente.  
  
 INDICE *index_name* COLUMNSTORE cluster  
   
  
**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].
  
 Specifica per archiviare l'intera tabella nel formato a colonne con un indice columnstore cluster. Questo include sempre tutte le colonne nella tabella. I dati non è ordinati in ordine alfabetico o numerico poiché le righe sono organizzate per ottenere i vantaggi di compressione di columnstore.  
  
 INDICE *index_name* COLUMNSTORE [NONCLUSTERED] (*column_name* [,... *n* ] )  
   
  
**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].
  
 Specifica per creare un indice columnstore non cluster nella tabella. La tabella sottostante può essere un heap rowstore o un indice cluster oppure può trattarsi di un indice columnstore cluster. In tutti i casi, la creazione di un indice columnstore non cluster in una tabella archivia una seconda copia dei dati per le colonne nell'indice.  
  
 L'indice columnstore non cluster archiviato e gestito come un indice columnstore cluster. Perché le colonne possono essere limitate ed esiste come un indice secondario in una tabella viene definito un indice columnstore non cluster.  
  
 ON *partition_scheme_name***(***column_name***)**  
 Specifica lo schema di partizione che definisce i filegroup a cui verrà eseguito il mapping delle partizioni di un indice partizionato. Lo schema di partizione deve esistere all'interno del database per l'esecuzione di una [CREATE PARTITION SCHEME](../../t-sql/statements/create-partition-scheme-transact-sql.md) o [ALTER PARTITION SCHEME](../../t-sql/statements/alter-partition-scheme-transact-sql.md). *column_name* specifica la colonna in base alla quale verrà partizionato un indice partizionato. Questa colonna deve corrispondere al tipo di dati, lunghezza e precisione dell'argomento della partizione di funzione che *partition_scheme_name* utilizza. *column_name* non è limitato alle colonne nella definizione dell'indice. È possibile specificare qualsiasi colonna nella tabella di base, tranne quando si partiziona un indice univoco, *column_name* devono essere scelte tra quelle utilizzate come chiave univoca. Questa restrizione consente a [!INCLUDE[ssDE](../../includes/ssde-md.md)] di verificare l'univocità dei valori di chiave all'interno di una singola partizione.  
  
> [!NOTE]  
>  Quando si partiziona un indice cluster non univoco, per impostazione predefinita [!INCLUDE[ssDE](../../includes/ssde-md.md)] aggiunge la colonna di partizionamento all'elenco delle chiavi di indice cluster, se non è già presente. Quando si partiziona un indice non cluster non univoco, [!INCLUDE[ssDE](../../includes/ssde-md.md)] aggiunge la colonna di partizionamento come colonna non chiave (inclusa) dell'indice, se non è già presente.  
  
 Se *partition_scheme_name* o *filegroup* non è specificato e la tabella è partizionata, l'indice viene posizionato nello stesso schema di partizione, utilizzando la stessa colonna di partizionamento della tabella sottostante.  
  
> [!NOTE]  
>  Non è possibile specificare uno schema di partizione per un indice XML. Se la tabella di base è partizionata, l'indice XML utilizzerà lo stesso schema di partizione della tabella.  
  
 Per ulteriori informazioni sul partizionamento degli indici, [tabelle e indici partizionati](../../relational-databases/partitions/partitioned-tables-and-indexes.md).  
  
 ON *filegroup_name*  
 Crea l'indice specificato nel filegroup specificato. Se non viene specificata una posizione e la tabella o la vista non è partizionata, l'indice utilizzerà lo stesso filegroup della tabella o della vista sottostante. Il filegroup deve essere già esistente.  
  
 ON **"**predefinito**"**  
 Crea l'indice specificato nel filegroup predefinito.  
  
 In questo contesto il termine default non rappresenta una parola chiave, È un identificatore per il filegroup predefinito e deve essere delimitato, ad esempio ON **"**predefinito**"** oppure ON **[**predefinito**]**. Se si specifica "default", l'opzione QUOTED_IDENTIFIER deve essere impostata su ON per la sessione corrente. Si tratta dell'impostazione predefinita. Per altre informazioni, vedere [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md).  
  
 [FILESTREAM_ON { *filestream_filegroup_name* | *partition_scheme_name* | "NULL"}]  
   
**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion.md)].

 Specifica la posizione dei dati FILESTREAM per la tabella quando viene creato un indice cluster. La clausola FILESTREAM_ON consente di spostare i dati FILESTREAM in uno schema di partizione o in un filegroup FILESTREAM diverso.  
  
 *filestream_filegroup_name* è il nome di un filegroup FILESTREAM. Il filegroup deve avere un file definito per il filegroup utilizzando un [CREATE DATABASE](../../t-sql/statements/create-database-sql-server-transact-sql.md) o [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md) istruzione; in caso contrario, viene generato un errore.  
  
 Se la tabella è partizionata, la clausola FILESTREAM_ON deve essere inclusa e deve specificare uno schema di partizione dei filegroup FILESTREAM che utilizzi la stessa funzione di partizione e le stesse colonne di partizione dello schema di partizione per la tabella. In caso contrario, viene generato un errore.  
  
 Se la tabella non è partizionata, la colonna FILESTREAM non può essere partizionata. I dati FILESTREAM per la tabella devono essere archiviati in un singolo filegroup specificato nella clausola FILESTREAM_ON.  
  
 È possibile specificare FILESTREAM_ON NULL in un'istruzione CREATE INDEX se si sta creando un indice cluster e se nella tabella non è contenuta alcuna colonna FILESTREAM.  
  
 Per altre informazioni, vedere [FILESTREAM &#40;SQL Server&#41;](../../relational-databases/blob/filestream-sql-server.md).  
  
 ROWGUIDCOL  
 Indica che la nuova colonna è una colonna GUID di riga. Un solo **uniqueidentifier** colonna per ogni tabella può essere definita come colonna ROWGUIDCOL. L'applicazione della proprietà ROWGUIDCOL consente di fare riferimento alla colonna utilizzando $ROWGUID. La proprietà ROWGUIDCOL può essere assegnata solo a un **uniqueidentifier** colonna. Le colonne con tipo di dati definito dall'utente non possono essere designate con ROWGUIDCOL.  
  
 La proprietà ROWGUIDCOL non impone l'univocità dei valori archiviati nella colonna e non genera automaticamente valori per le nuove righe inserite nella tabella. Per generare valori univoci per ogni colonna, utilizzare il [NEWID](../../t-sql/functions/newid-transact-sql.md) o [NEWSEQUENTIALID](../../t-sql/functions/newsequentialid-transact-sql.md) funzione su [inserire](../../t-sql/statements/insert-transact-sql.md) istruzioni o utilizzare queste funzioni come il valore predefinito per il colonna.  
  
 CRITTOGRAFATO CON  
 Specifica le colonne di crittografia utilizzando il [Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md) funzionalità.  
  
 COLUMN_ENCRYPTION_KEY = *key_name*  
 Specifica la chiave di crittografia di colonna. Per ulteriori informazioni, vedere [CREATE COLUMN ENCRYPTION KEY &#40; Transact-SQL &#41; ](../../t-sql/statements/create-column-encryption-key-transact-sql.md).  
  
 ENCRYPTION_TYPE = {DETERMINISTICA | CASUALE}  
 La**crittografia deterministica** usa un metodo che genera sempre lo stesso valore crittografato per qualsiasi valore di testo normale specificato. Uso della crittografia deterministica consente la ricerca utilizzando il confronto di uguaglianza, raggruppamento e join di tabelle con join di uguaglianza in base ai valori crittografati, ma può anche consentire agli utenti non autorizzati di indovinare le informazioni sui valori crittografati esaminando i criteri in la colonna crittografata. Unione di due tabelle sulle colonne crittografate in modo deterministico è possibile solo se entrambe le colonne vengono crittografate tramite la stessa chiave di crittografia di colonna. La crittografia deterministica deve usare regole di confronto a livello di colonna con un ordinamento binario2 per colonne di tipo carattere.  
  
 La**crittografia casuale** usa un metodo di crittografia dei dati meno prevedibile. La crittografia casuale è più sicura ma impedisce le ricerche di uguaglianza, raggruppamento e join su colonne crittografate. Le colonne con la crittografia casuale non possono essere indicizzate.  
  
 Per le colonne che saranno i parametri di ricerca o raggruppamento, ad esempio un numero di ID per enti pubblici, utilizzare la crittografia deterministica. Usare la crittografia casuale, per i dati, ad esempio un numero di carta di credito, che non è raggruppati con altri record o usati per il join di tabelle e che non viene cercato per perché utilizzare altre colonne (ad esempio un numero di transazioni) per trovare la riga che contiene crittografata colonna di interesse.  
  
 Le colonne devono essere di un tipo di dati validi.  
  
 ALGORITMO  
 Deve essere **'AEAD_AES_256_CBC_HMAC_SHA_256'**.  
  
 Per ulteriori informazioni, inclusi i vincoli di funzionalità, vedere [Always Encrypted &#40; motore di Database &#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md).  
  
 **Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 SPARSE  
 Indica che la colonna è di tipo sparse. L'archiviazione delle colonne di tipo sparse è ottimizzata per valori Null. Non è possibile designare le colonne di tipo sparse come NOT NULL. Per ulteriori restrizioni e ulteriori informazioni sulle colonne di tipo sparse, vedere [utilizzare le colonne di tipo Sparse](../../relational-databases/tables/use-sparse-columns.md).  
  
 MASCHERATI con (funzione = ' *mask_function* ')  
 **Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica una maschera dati dinamica. *mask_function* è il nome della funzione di maschera con i parametri appropriati. Sono disponibili seguenti le:  
  
-   default)  
  
-   email()  
  
-   partial()  
  
-   funzione DISTRIB  
  
 Per i parametri di funzione, vedere [maschera dati dinamica](../../relational-databases/security/dynamic-data-masking.md).  
  
 FILESTREAM  
   
**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion.md)].

 Valido solo per **varbinary (max)** colonne. Specifica l'archiviazione FILESTREAM per il **varbinary (max)** dati BLOB.  
  
 La tabella deve includere anche una colonna del **uniqueidentifier** tipo di dati che dispone dell'attributo ROWGUIDCOL. Questa colonna non deve consentire valori Null e deve avere un vincolo a colonna singola UNIQUE o PRIMARY KEY. Il valore GUID per la colonna deve essere specificato da un'applicazione al momento dell'inserimento dei dati o da un vincolo DEFAULT che utilizza la funzione NEWID ().  
  
 Non è possibile eliminare la colonna ROWGUIDCOL, né modificare i vincoli correlati quando per la tabella è stata definita una colonna FILESTREAM. La colonna ROWGUIDCOL può essere eliminata solo dopo l'eliminazione dell'ultima colonna FILESTREAM.  
  
 Quando l'attributo di archiviazione FILESTREAM viene specificato per una colonna, tutti i valori per quella colonna vengono archiviati in un contenitore di dati FILESTREAM nel file system.  
  
 COLLATE *collation_name*  
 Specifica le regole di confronto per la colonna. È possibile usare nomi di regole di confronto di Windows o SQL. *collation_name* è applicabile solo alle colonne di **char**, **varchar**, **testo**, **nchar**, **nvarchar**, e **ntext** tipi di dati. Se non specificato, alla colonna vengono assegnate le regole di confronto del tipo di dati definito dall'utente, se la colonna presenta questo tipo di dati, oppure le regole di confronto predefinite del database.  
  
 Per ulteriori informazioni sui nomi delle regole di confronto Windows e SQL, vedere [windows_collation_name](../../t-sql/statements/windows-collation-name-transact-sql.md) e [nome regole di confronto SQL](../../t-sql/statements/sql-server-collation-name-transact-sql.md).  
  
 Per ulteriori informazioni sulla clausola COLLATE, vedere [COLLATE &#40; Transact-SQL &#41; ](~/t-sql/statements/collations.md).  
  
 CONSTRAINT  
 Parola chiave facoltativa che indica l'inizio di una definizione di vincolo PRIMARY KEY, NOT NULL, UNIQUE, FOREIGN KEY o CHECK.  
  
 *constraint_name*  
 Nome di un vincolo. I nomi di vincolo devono essere univoci nell'ambito dello schema a cui appartiene la tabella.  
  
 NULL | NOT NULL  
 Indica se i valori NULL sono consentiti nella colonna. L'opzione NULL non è esattamente un vincolo, ma può essere specificata allo stesso modo di NOT NULL. È possibile specificare NOT NULL per le colonne calcolate solo se è specificato PERSISTED.  
  
 PRIMARY KEY  
 Vincolo che impone l'integrità di entità per una o più colonne specificate tramite un indice univoco. È possibile creare un solo vincolo PRIMARY KEY per ogni tabella.  
  
 UNIQUE  
 Vincolo che impone l'integrità di entità per una o più colonne specificate tramite un indice univoco. Una tabella può includere più vincoli UNIQUE.  
  
 CLUSTERED | NONCLUSTERED  
 Definisce la creazione di un indice cluster o non cluster per il vincolo PRIMARY KEY o UNIQUE. Il valore predefinito per i vincoli PRIMARY KEY è CLUSTERED, mentre per i vincoli UNIQUE è NONCLUSTERED.  
  
 In un'istruzione CREATE TABLE è possibile specificare CLUSTERED per un solo vincolo. Se si specifica CLUSTERED per un vincolo UNIQUE e si specifica anche un vincolo PRIMARY KEY, il valore predefinito di quest'ultimo è NONCLUSTERED.  
  
 Di seguito viene illustrato come usare NONCLUSTERED in una tabella basata su disco:  
  
```  
CREATE TABLE t1 ( c1 int, INDEX ix_1 NONCLUSTERED (c1))   
CREATE TABLE t2( c1 int INDEX ix_1 NONCLUSTERED (c1))   
CREATE TABLE t3( c1 int, c2 int INDEX ix_1 NONCLUSTERED)   
CREATE TABLE t4( c1 int, c2 int, INDEX ix_1 NONCLUSTERED (c1,c2))  
```  
  
 FOREIGN KEY REFERENCES  
 Vincolo che impone l'integrità referenziale dei dati di una o più colonne. È necessario che ogni valore delle colonne sia incluso nelle colonne di riferimento corrispondenti della tabella di riferimento. È possibile fare riferimento a vincoli FOREIGN KEY solo nelle colonne che nella tabella con riferimenti corrispondono a vincoli PRIMARY KEY o UNIQUE e nelle colonne a cui viene fatto riferimento in un indice univoco nella tabella di riferimento. È necessario contrassegnare come PERSISTED anche le chiavi esterne nelle colonne calcolate.  
  
 [ *schema_name***.**] *referenced_table_name*]  
 Nome della tabella a cui fa riferimento il vincolo FOREIGN KEY e dello schema a cui appartiene.  
  
 **(** *ref_column* [ **,**... *n* ] **)**  
 Colonna o elenco di colonne della tabella a cui fa riferimento il vincolo FOREIGN KEY.  
  
 ELIMINAZIONE { **ALCUNA AZIONE** | CASCADE | SET NULL | IMPOSTAZIONE DEL VALORE PREDEFINITO}  
 Specifica quale azione eseguire sulle righe nella tabella creata, se tali righe includono una relazione referenziale e se la riga a cui viene fatto riferimento viene eliminata dalla tabella padre. Il valore predefinito è NO ACTION.  
  
 NO ACTION  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] genera un errore e viene eseguito il rollback dell'azione di eliminazione della riga nella tabella padre.  
  
 CASCADE  
 Le righe corrispondenti vengono eliminate dalla tabella di riferimento se la riga viene eliminata dalla tabella padre.  
  
 SET NULL  
 Tutti i valori che compongono la chiave esterna vengono impostati su NULL se viene eliminata la riga corrispondente nella tabella padre. Per l'esecuzione di questo vincolo, è necessario che le colonne chiave esterna ammettano valori Null.  
  
 SET DEFAULT  
 Tutti i valori che compongono la chiave esterna vengono impostati sui rispettivi valori predefiniti se viene eliminata la riga corrispondente nella tabella padre. Per l'esecuzione di questo vincolo, è necessario che per tutte le colonne chiave esterna siano definiti valori predefiniti. Se una colonna ammette valori Null e non viene impostato un valore predefinito esplicito, NULL diventa il valore predefinito implicito della colonna.  
  
 Non specificare CASCADE se la tabella verrà inclusa in una pubblicazione di tipo merge che utilizza record logici. Per altre informazioni sui record logici, vedere [Raggruppare modifiche alle righe correlate con record logici](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
 Non è possibile specificare ON DELETE CASCADE se nella tabella è già presente un trigger INSTEAD OF per ON DELETE.  
  
 Ad esempio, nel [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, il **ProductVendor** tabella ha una relazione referenziale con la **fornitore** tabella. Il **ProductVendor** riferimenti di chiave esterna di **BusinessEntityID** chiave primaria.  
  
 Se viene eseguita un'istruzione DELETE in una riga di **fornitore** tabella e un'azione ON DELETE CASCADE viene specificata per **ProductVendor**, [!INCLUDE[ssDE](../../includes/ssde-md.md)] controlli per uno o più dipendenti le righe del **ProductVendor** tabella. Le eventuali righe dipendenti nella **ProductVendor** tabella vengono eliminate e anche la riga a cui fa riferimento il **fornitore** tabella.  
  
 Al contrario, se si specifica NO ACTION, il [!INCLUDE[ssDE](../../includes/ssde-md.md)] genera un errore ed eseguire il rollback dell'azione di eliminazione **fornitore** se esiste almeno una riga nel **ProductVendor** tabella cui fa riferimento.  
  
 AGGIORNAMENTO { **ALCUNA AZIONE** | CASCADE | SET NULL | IMPOSTAZIONE DEL VALORE PREDEFINITO}  
 Specifica l'azione eseguita nelle righe della tabella modificata se tali righe includono una relazione referenziale e la riga a cui viene fatto riferimento è stata aggiornata nella tabella padre. Il valore predefinito è NO ACTION.  
  
 NO ACTION  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] genera un errore e viene eseguito il rollback dell'azione di aggiornamento della riga nella tabella padre.  
  
 CASCADE  
 Le righe corrispondenti vengono aggiornate nella tabella di riferimento quando la riga viene aggiornata nella tabella padre.  
  
 SET NULL  
 Tutti i valori che costituiscono la chiave esterna vengono impostati su NULL quando viene aggiornata la riga corrispondente nella tabella padre. Per l'esecuzione di questo vincolo, è necessario che le colonne chiave esterna ammettano valori Null.  
  
 SET DEFAULT  
 Tutti i valori che costituiscono la chiave esterna vengono impostati sui rispettivi valori predefiniti quando viene aggiornata la riga corrispondente nella tabella padre. Per l'esecuzione di questo vincolo, è necessario che per tutte le colonne chiave esterna siano definiti valori predefiniti. Se una colonna ammette valori Null e non viene impostato un valore predefinito esplicito, NULL diventa il valore predefinito implicito della colonna.  
  
 Non specificare CASCADE se la tabella verrà inclusa in una pubblicazione di tipo merge che utilizza record logici. Per altre informazioni sui record logici, vedere [Raggruppare modifiche alle righe correlate con record logici](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
 Non è possibile specificare ON UPDATE CASCADE, SET NULL o SET DEFAULT se nella tabella che viene modificata esiste già un trigger INSTEAD OF per ON UPDATE.  
  
 Ad esempio, nel [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, il **ProductVendor** tabella ha una relazione referenziale con la **fornitore** tabella: **businessEntity** riferimenti di chiave esterna di **BusinessEntityID** chiave primaria.  
  
 Se viene eseguita un'istruzione UPDATE in una riga di **fornitore** tabella e un'azione ON UPDATE CASCADE viene specificata per **ProductVendor**, [!INCLUDE[ssDE](../../includes/ssde-md.md)] controlli per uno o più dipendenti le righe del **ProductVendor** tabella. Le eventuali righe dipendenti nella **ProductVendor** tabella vengono aggiornati e anche la riga a cui fa riferimento il **fornitore** tabella.  
  
 Al contrario, se si specifica NO ACTION, il [!INCLUDE[ssDE](../../includes/ssde-md.md)] genera un errore ed eseguire il rollback dell'azione di aggiornamento **fornitore** se esiste almeno una riga nel **ProductVendor** tabella cui fa riferimento.  
  
 CHECK  
 Vincolo che impone l'integrità di dominio tramite la limitazione dei valori che è possibile inserire in una o più colonne. È necessario contrassegnare come PERSISTED anche i vincoli CHECK nelle colonne calcolate.  
  
 *Logical_Expression*  
 Espressione logica che restituisce TRUE o FALSE. L'espressione non può includere tipi di dati alias.  
  
 *colonna*  
 Colonna o elenco di colonne, indicate tra parentesi, utilizzate nei vincoli di tabella per indicare le colonne specificate nella definizione del vincolo.  
  
 [ **ASC** | DESC]  
 Specifica l'ordinamento della colonna o delle colonne che fanno parte dei vincoli di tabella. Il valore predefinito è ASC.  
  
 *partition_scheme_name*  
 Nome dello schema di partizione che definisce i filegroup a cui verrà eseguito il mapping delle partizioni di una tabella partizionata. Lo schema di partizione deve essere presente nel database.  
  
 [ *partition_column_name***.** ]  
 Specifica la colonna in base alla quale verrà partizionata una tabella partizionata. La colonna deve corrispondere a quello specificato nella partizione di funzione che *partition_scheme_name* utilizza in termini di tipo di dati, lunghezza e precisione. Una colonna calcolata utilizzata in una funzione di partizione deve essere contrassegnata in modo esplicito come PERSISTED.  
  
> [!IMPORTANT]  
>  Si consiglia di specificare NOT NULL sulla colonna di partizionamento di tabelle partizionate oppure di tabelle non partizionate che rappresentano origini o destinazioni di operazioni ALTER TABLE...SWITCH. In questo modo, i vincoli CHECK su colonne di partizionamento non devono verificare la presenza di valori Null.  
  
 CON valore FILLFACTOR  **=**  *fattore di riempimento*  
 Specifica la percentuale di riempimento impostata da [!INCLUDE[ssDE](../../includes/ssde-md.md)] per ogni pagina di indice utilizzata per archiviare i dati dell'indice. Specificato dall'utente *fillfactor* valori possono essere compresi tra 1 e 100. Se non viene specificato alcun valore, il valore predefinito è 0. I valori 0 e 100 relativi al fattore di riempimento sono equivalenti.  
  
> [!IMPORTANT]  
>  Documentazione con FILLFACTOR = *fillfactor* come l'unica opzione di indice che si applica ai vincoli PRIMARY KEY o UNIQUE viene mantenuto per compatibilità con le versioni precedenti, ma non sarà più documentata in futuro in questo modo rilascia.  
  
 *nome_set_colonne* XML COLUMN_SET FOR ALL_SPARSE_COLUMNS.  
 Nome del set di colonne. Un set di colonne è una rappresentazione XML non tipizzata che combina tutte le colonne di tipo sparse di una tabella in un output strutturato. Per altre informazioni sui set di colonne, vedere [Utilizzare set di colonne](../../relational-databases/tables/use-column-sets.md).  
  
 PERIOD FOR SYSTEM_TIME (*system_start_time_column_name* , *system_end_time_column_name* )  
   
**Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].
  
 Specifica i nomi delle colonne che verrà utilizzata dal sistema per registrare il periodo di validità per il quale un record. Utilizzare questo argomento in combinazione con la generato sempre come riga {START | FINE} e con SYSTEM_VERSIONING = ON argomenti per abilitare il controllo delle versioni di sistema in una tabella. Per altre informazioni, vedere [Temporal Tables](../../relational-databases/tables/temporal-tables.md).  
  
 COMPRESSION_DELAY  
   
**Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].
  
 Per un con ottimizzazione della memoria, ritardo specifica il numero minimo di minuti che deve rimanere una riga nella tabella, invariata, prima che sia idoneo per la compressione in corrispondenza dell'indice columnstore. SQL Server consente di selezionare le righe specifiche da comprimere in base all'ultima ora di aggiornamento. Ad esempio, se le righe modificano frequentemente durante un periodo di due ore di tempo, è possibile impostare COMPRESSION_DELAY = 120 minuti per verificare gli aggiornamenti vengono completati prima che SQL Server consente di comprimere la riga.  
  
 Per una tabella basata su disco, ritardo specifica il numero minimo di minuti che un rowgroup delta in stato di chiusura deve rimanere in rowgroup delta prima di SQL Server può ridurre in rowgroup compressi. Poiché le tabelle basate su disco non tenere traccia delle insert e update volte su singole righe, SQL Server si applica il ritardo in rowgroup delta nello stato CLOSED.  
  
 Il valore predefinito è 0 minuti.  
  
 Per indicazioni su quando usare COMPRESSION_DELAY, vedere [Introduzione a Columnstore per analitica operativa in tempo reale](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)  
  
 \<table_option >:: = specifica uno o più opzioni di tabella.  
  
 DATA_COMPRESSION  
 Specifica l'opzione di compressione dei dati per la tabella, il numero di partizione o l'intervallo di partizioni specificato. Sono disponibili le opzioni seguenti:  
  
 NONE  
 La tabella o le partizioni specificate non vengono compresse.  
  
 ROW  
 La tabella o le partizioni specificate vengono compresse utilizzando la compressione di riga.  
  
 PAGE  
 La tabella o le partizioni specificate vengono compresse utilizzando la compressione di pagina.  
  
 COLUMNSTORE  
   
  
**Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].
  
 Si applica solo agli indici columnstore, inclusi gli indici columnstore cluster e quelli non cluster. COLUMNSTORE specifica questa opzione per comprimere con la maggior parte dei compressione columnstore ad alte prestazioni. Si tratta in genere.  
  
 COLUMNSTORE_ARCHIVE  
   
  
**Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Si applica solo agli indici columnstore, inclusi gli indici columnstore cluster e quelli non cluster. COLUMNSTORE_ARCHIVE comprimerà ulteriormente la tabella o la partizione a una dimensione inferiore. Può essere utilizzata per l'archiviazione o in altre situazioni in cui sono richieste dimensioni di archiviazione inferiori ed è possibile concedere più tempo per l'archiviazione e il recupero.  
  
 Per ulteriori informazioni sulla compressione, vedere [la compressione dei dati](../../relational-databases/data-compression/data-compression.md).  
  
 PARTIZIONI **(** { `<partition_number_expression>` | [ **,**... *n* ] **)**  
 Specifica le partizioni alle quali si applica l'impostazione DATA_COMPRESSION. Se la tabella non è partizionata, l'argomento ON PARTITIONS genererà un errore. Se la clausola ON PARTITIONS non viene specificata, l'opzione DATA_COMPRESSION verrà applicata a tutte le partizioni di una tabella partizionata.  
  
 *partition_number_expression* possono essere specificati nei modi seguenti:  
  
-   Specificare il numero di una partizione, ad esempio ON PARTITIONS (2).  
  
-   Fornire i numeri di partizione per più partizioni singole separati da virgole, ad esempio ON PARTITIONS (1, 5).  
  
-   Specificare sia intervalli, sia singole partizioni, ad esempio ON PARTITIONS (2, 4, 6 TO 8).  
  
 `<range>`possono essere specificati come numeri di partizione separati dalla parola TO, ad esempio: ON PARTITIONS (6 TO 8).  
  
 Per impostare tipi diversi di compressione dei dati per partizioni diverse, specificare più volte l'opzione DATA_COMPRESSION, ad esempio:  
  
```  
WITH   
(  
DATA_COMPRESSION = NONE ON PARTITIONS (1),   
DATA_COMPRESSION = ROW ON PARTITIONS (2, 4, 6 TO 8),   
DATA_COMPRESSION = PAGE ON PARTITIONS (3, 5)  
)  
```  
  
 \<index_option >:: =  
 Specifica una o più opzioni per l'indice. Per una descrizione completa di queste opzioni, vedere [CREATE INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/create-index-transact-sql.md).  
  
 PAD_INDEX = {ON | **OFF** }  
 Se l'opzione è impostata su ON, la percentuale di spazio disponibile specificata da FILLFACTOR viene applicata alle pagine di livello intermedio dell'indice. Se si specifica OFF o se non si specifica un valore FILLFACTOR, le pagine di livello intermedio vengono riempite quasi fino alla capacità massima, lasciando spazio sufficiente per almeno una riga delle dimensioni massime consentite per l'indice, considerando il set di chiavi nelle pagine intermedie. Il valore predefinito è OFF.  
  
 Fattore di riempimento  **=**  *fattore di riempimento*  
 Specifica una percentuale indicante il livello di riempimento del livello foglia di ogni pagina di indice applicato dal [!INCLUDE[ssDE](../../includes/ssde-md.md)] durante la creazione o la modifica dell'indice. *fattore di riempimento* deve essere un valore intero compreso tra 1 e 100. Il valore predefinito è 0. I valori 0 e 100 relativi al fattore di riempimento sono equivalenti.  
  
 IGNORE_DUP_KEY = {ON | **OFF** }  
 Specifica l'errore restituito quando un'operazione di inserimento tenta di inserire valori di chiave duplicati in un indice univoco. L'opzione IGNORE_DUP_KEY viene applicata solo alle operazioni di inserimento eseguite dopo la creazione o la ricompilazione dell'indice. L'opzione non ha alcun effetto quando si esegue [CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md), [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md), o [aggiornamento](../../t-sql/queries/update-transact-sql.md). Il valore predefinito è OFF.  
  
 ON  
 Viene visualizzato un messaggio di avviso quando i valori di chiave duplicati vengono inseriti in un indice univoco. Avranno esito negativo solo le righe che violano il vincolo di unicità.  
  
 OFF  
 Viene visualizzato un messaggio di errore quando i valori di chiave duplicati vengono inseriti in un indice univoco. Viene eseguito il rollback dell'intera operazione INSERT.  
  
 L'opzione IGNORE_DUP_KEY non può essere impostata su ON per gli indici creati in una vista, negli indici non univoci, negli indici XML, spaziali e filtrati.  
  
 Per visualizzare IGNORE_DUP_KEY, utilizzare [Sys. Indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).  
  
 Per quanto riguarda la sintassi compatibile con le versioni precedenti, WITH IGNORE_DUP_KEY equivale a WITH IGNORE_DUP_KEY = ON.  
  
 STATISTICS_NORECOMPUTE  **=**  {ON | **OFF** }  
 Se si specifica ON, le statistiche dell'indice non aggiornate non vengono ricalcolate automaticamente. Se si specifica OFF, viene abilitato l'aggiornamento automatico delle statistiche. Il valore predefinito è OFF.  
  
 ALLOW_ROW_LOCKS  **=**  { **ON** | OFF}  
 Se si specifica ON, sono consentiti blocchi di riga per l'accesso all'indice. Il [!INCLUDE[ssDE](../../includes/ssde-md.md)] determina quando utilizzare blocchi di riga. Se si specifica OFF, i blocchi a livello di riga non vengono utilizzati. Il valore predefinito è ON.  
  
 ALLOW_PAGE_LOCKS  **=**  { **ON** | OFF}  
 Se si specifica ON, sono consentiti blocchi di pagina per l'accesso all'indice. Il [!INCLUDE[ssDE](../../includes/ssde-md.md)] determina quando utilizzare blocchi a livello di pagina. Se si specifica OFF, i blocchi a livello di pagina non vengono utilizzati. Il valore predefinito è ON.  
  
 FILETABLE_DIRECTORY = *directory_name*  
   
  
**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
 Specifica un nome di directory FileTable compatibile con Windows. Questo nome deve essere univoco tra tutti i nomi di directory FileTable nel database. Il confronto di univocità non supporta la distinzione tra maiuscole e minuscole, indipendentemente dalle impostazioni delle regole di confronto. Se questo valore non è specificato, viene utilizzato il nome della tabella FileTable.  
  
 FILETABLE_COLLATE_FILENAME = { *collation_name* | database_default}  
   
  
**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
 Specifica il nome delle regole di confronto da applicare alla colonna **Name** della tabella FileTable. Nelle regole di confronto specificate non deve essere applicata la distinzione tra maiuscole e minuscole ai fini della conformità con la semantica di denominazione dei file di Windows. Se questo valore non è specificato, vengono utilizzate le regole di confronto predefinite del database. Se nelle regole di confronto predefinite del database viene applicata la distinzione tra maiuscole e minuscole, viene generato un errore e l'operazione CREATE TABLE non riesce.  
  
 *collation_name*  
 Nome delle regole di confronto senza distinzione tra maiuscole e minuscole.  
  
 database_default  
 Viene specificato che è necessario usare le regole di confronto predefinite per il database. Nelle regole di confronto non deve essere applicata la distinzione tra maiuscole e minuscole.  
  
 FILETABLE_PRIMARY_KEY_CONSTRAINT_NAME = *constraint_name*  
   
**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
 Viene specificato il nome da usare per il vincolo di chiave primaria che viene creato automaticamente nella tabella FileTable. Se questo valore non è specificato, tramite il sistema viene generato un nome per il vincolo.  
  
 FILETABLE_STREAMID_UNIQUE_CONSTRAINT_NAME = *constraint_name*  
   
  
**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
 Specifica il nome da utilizzare per il vincolo univoco che viene creato automaticamente sul **stream_id** colonna nella tabella FileTable. Se questo valore non è specificato, tramite il sistema viene generato un nome per il vincolo.  
  
 FILETABLE_FULLPATH_UNIQUE_CONSTRAINT_NAME = *constraint_name*  
   
  
**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
 Specifica il nome da utilizzare per il vincolo univoco che viene creato automaticamente sul **parent_path_locator** e **nome** colonne nella tabella FileTable. Se questo valore non è specificato, tramite il sistema viene generato un nome per il vincolo.  
  
 SYSTEM_VERSIONING  **=**  ON [(HISTORY_TABLE  **=**  *schema_name* .  *history_table_name* [, DATA_CONSISTENCY_CHECK  **=**  { **ON** | OFF}])]  
   
  
**Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].   
  
 Consente il controllo delle versioni di sistema della tabella se vengono soddisfatti i requisiti per i vincoli di chiave primaria, il tipo di dati e il vincolo di ammissione di valori null. Se il **HISTORY_TABLE** argomento non viene utilizzato il sistema genera una nuova tabella di cronologia corrispondente lo schema della tabella nello stesso filegroup della tabella corrente, creare un collegamento tra le due tabelle corrente e consente al sistema di registrare la cronologia di ogni record nella tabella corrente nella tabella di cronologia. Il nome di questa tabella di cronologia sarà `MSSQL_TemporalHistoryFor<primary_table_object_id>`. Per impostazione predefinita, la tabella di cronologia è **PAGE** compresso. Se l'argomento HISTORY_TABLE viene utilizzato per creare un collegamento a e utilizzare una tabella di cronologia esistente, viene creato il collegamento tra la tabella corrente e la tabella specificata. Se la tabella corrente è partizionata, la tabella di cronologia viene creata nel filegroup predefinito perché la configurazione del partizionamento non viene replicata automaticamente dalla tabella corrente nella tabella di cronologia. Se durante la creazione della tabella di cronologia viene specificato il nome di una tabella di cronologia, è necessario specificare il nome tabella e il nome schema. Quando si crea un collegamento a una tabella di cronologia esistente, è possibile scegliere di eseguire una verifica della coerenza dei dati. La coerenza dei dati garantisce che i record esistenti non si sovrappongano. L'impostazione predefinita prevede l'esecuzione della verifica della coerenza dei dati. Utilizzare questo argomento in combinazione con l'operazione PERIOD FOR SYSTEM_TIME e generato sempre AS riga {START | Argomenti di fine} per abilitare il controllo delle versioni di sistema in una tabella. Per altre informazioni, vedere [Temporal Tables](../../relational-databases/tables/temporal-tables.md).  
  
 REMOTE_DATA_ARCHIVE = {ON [( *table_stretch_options* [,... n])] | OFF (MIGRATION_STATE = IN PAUSA)}  
   
  
**Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Crea la nuova tabella con estensione Database abilitata o disabilitata. Per ulteriori informazioni, vedere [Stretch Database](../../sql-server/stretch-database/stretch-database.md).  
  
 **Abilitazione di estensione Database per una tabella**  
  
 Quando si abilita estensione per una tabella specificando `ON`, è possibile specificare facoltativamente `MIGRATION_STATE = OUTBOUND` per iniziare subito la migrazione dei dati o `MIGRATION_STATE = PAUSED` per posticipare la migrazione dei dati. Il valore predefinito è `MIGRATION_STATE = OUTBOUND`. Per ulteriori informazioni sull'abilitazione dell'estensione per una tabella, vedere [abilitare estensione Database per una tabella](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md).  
  
 **Prerequisiti**. Prima abilitare l'estensione per una tabella, è necessario abilitare l'estensione nel server e sul database. Per ulteriori informazioni, vedere [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md).  
  
 **Autorizzazioni**. Abilitazione dell'estensione per un database o una tabella richiede autorizzazioni db_owner. Abilitazione dell'estensione per una tabella richiede anche autorizzazioni ALTER sulla tabella.  
  
 [FILTER_PREDICATE = {null | *predicato* }]  
   
  
**Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Facoltativamente è possibile specificare un predicato del filtro per selezionare righe di cui eseguire la migrazione da una tabella che contiene i dati correnti e cronologici. Il predicato deve chiamare una funzione con valori di tabella inline deterministica. Per altre informazioni, vedere [abilitare estensione Database per una tabella](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md) e [selezionare righe di cui eseguire la migrazione tramite una funzione di filtro](../../sql-server/stretch-database/select-rows-to-migrate-by-using-a-filter-function-stretch-database.md). 
   
> [!IMPORTANT]  
>  Se si specifica un predicato del filtro inefficace, anche la migrazione dei dati risulterà inefficace. Stretch Database applica il predicato del filtro alla tabella usando l'operatore CROSS APPLY.  
  
 Se non si specifica un predicato del filtro, viene eseguita la migrazione dell'intera tabella.  
  
 Quando si specifica un predicato del filtro, è necessario specificare anche *MIGRATION_STATE*.  
  
 MIGRATION_STATE = {IN USCITA |  CONNESSIONI IN ENTRATA | IN PAUSA}  
   
  
**Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]e SQL Azure. 
  
-   Specificare `OUTBOUND` per migrare i dati da SQL Server in Azure.  
  
-   Specificare `INBOUND` copiare remoto per la tabella da Azure nuovamente i dati per SQL Server e per disabilitare l'estensione per la tabella. Per altre informazioni, vedere [Disabilitare Stretch Database e ripristinare i dati remoti](../../sql-server/stretch-database/disable-stretch-database-and-bring-back-remote-data.md).  
  
     Questa operazione comporta costi di trasferimento dati e non può essere annullata.  
  
-   Specificare `PAUSED` per sospendere o posticipare la migrazione dei dati. Per altre informazioni, vedere [sospendere e riprendere la migrazione dei dati &#40; Estensione Database &#41; ](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md).  
  
 MEMORY_OPTIMIZED  
   
  
**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 ON valore indica che la tabella è ottimizzata per la memoria. Le tabelle con ottimizzazione per la memoria sono parte della funzionalità di OLTP In memoria, viene utilizzata ottimizzare le prestazioni dell'elaborazione delle transazioni. Per iniziare a OLTP In memoria vedere [avvio rapido 1: tecnologie OLTP In memoria per più rapidamente le prestazioni di Transact-SQL](../../relational-databases/in-memory-oltp/survey-of-initial-areas-in-in-memory-oltp.md). Per informazioni più dettagliate sulle tabelle con ottimizzazione per la memoria vedere [Optimized tabelle](../../relational-databases/in-memory-oltp/memory-optimized-tables.md).  
  
 Il valore predefinito è impostata su OFF indica che la tabella è basata su disco.  
  
 DURABILITY  
   
  
**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].   
  
 Il valore di SCHEMA_AND_DATA indica che la tabella è durevole, vale a dire che le modifiche vengono rese persistenti su disco e valide anche dopo il riavvio o failover.  SCHEMA_AND_DATA è il valore predefinito.  
  
 Il valore di SCHEMA_ONLY indica che la tabella non è durevole. Lo schema della tabella è persistente ma alcuni aggiornamenti di dati non vengono mantenuti durante un riavvio o failover del database. DURABILITY = SCHEMA_ONLY è consentita solo con MEMORY_OPTIMIZED = ON.  
  
> [!WARNING]  
>  Quando viene creata una tabella con **DURABILITY = SCHEMA_ONLY**, e **READ_COMMITTED_SNAPSHOT** viene successivamente modificata usando **ALTER DATABASE**, nella tabella dati andranno perduti.  
  
 BUCKET_COUNT  
   
  
**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. 
  
 Indica il numero di bucket che deve essere creato nell'indice hash. Il valore massimo per BUCKET_COUNT in indici hash è 1.073.741.824. Per ulteriori informazioni sui numeri di bucket, vedere [indici per tabelle con ottimizzazione](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md).  
  
 Bucket_count è un argomento obbligatorio.  
  
 INDEX  
   
  
**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. 
  
Gli indici di colonna e di tabella possono essere specificati come parte dell'istruzione CREATE TABLE. Per informazioni sull'aggiunta e rimozione di indici nelle tabelle con ottimizzazione per la memoria, vedere: [modifica di tabelle](../../relational-databases/in-memory-oltp/altering-memory-optimized-tables.md)
  
 HASH  
   
  
**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. 
  
 Indica che viene creato un indice HASH.  
  
 Gli indici hash sono supportati solo nelle tabelle con ottimizzazione per la memoria.  
  
## <a name="remarks"></a>Osservazioni  
 Per informazioni sul numero di tabelle consentite, colonne, vincoli e indici, vedere [Maximum Capacity Specifications for SQL Server](../../sql-server/maximum-capacity-specifications-for-sql-server.md).  
  
 Lo spazio in tabelle e indici viene generalmente allocato con incrementi di un extent. Quando l'opzione SET MIXED_PAGE_ALLOCATION di ALTER DATABASE è impostato TRUE, o sempre prima di [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], quando viene creata una tabella o indice, vengono allocate pagine da extent misti fino a quando non dispone di pagine sufficiente per riempire un extent uniforme. In seguito, viene allocato un altro extent ogni volta che gli extent allocati risultano pieni. Per un report sulla quantità di spazio allocato e utilizzato da una tabella, eseguire **sp_spaceused**.  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] non prevede l'applicazione di un ordine particolare per l'impostazione dei valori DEFAULT, IDENTITY, ROWGUIDCOL o dei vincoli di colonna in una definizione di colonna.  
  
 Quando viene creata una tabella, l'opzione QUOTED IDENTIFIER viene sempre archiviata con l'impostazione ON nei metadati della tabella, anche se l'opzione viene impostata su OFF quando si crea la tabella.  
  
## <a name="temporary-tables"></a>Tabelle temporanee  
 È possibile creare tabelle temporanee locali e globali. Le tabelle temporanee locali sono visibili solo nella sessione corrente, mentre quelle globali sono visibili in tutte le sessioni. Non è possibile partizionare le tabelle temporanee.  
  
 Prefisso di nomi di tabella temporanea locale con solo simbolo di cancelletto (#*table_name*) e i nomi di tabella temporanea globale con un simbolo di cancelletto doppio del prefisso (# #*table_name*).  
  
 Istruzioni SQL fanno riferimento alla tabella temporanea utilizzando il valore specificato per *table_name* nell'istruzione CREATE TABLE, per esempio # # #:  
  
```  
CREATE TABLE #MyTempTable (cola INT PRIMARY KEY);  
  
INSERT INTO #MyTempTable VALUES (1);  
```  
  
 Se si creano più tabelle temporanee all'interno di una sola stored procedure o di un singolo batch, è necessario che i nomi delle tabelle siano diversi.  
  
 Se viene creata una tabella temporanea locale in una stored procedure o in un'applicazione che può essere eseguita contemporaneamente da più utenti, [!INCLUDE[ssDE](../../includes/ssde-md.md)] deve essere in grado di distinguere le tabelle create dai vari utenti. A tale scopo, [!INCLUDE[ssDE](../../includes/ssde-md.md)] aggiunge internamente un suffisso numerico a ogni nome di tabella temporanea locale. Il nome completo di una tabella temporanea archiviato nella **sysobjects** tabella **tempdb** è costituito il nome della tabella specificato nell'istruzione CREATE TABLE e il suffisso numerico generato dal sistema. Per consentire il suffisso *table_name* specificato per un nome temporaneo locale non può superare i 116 caratteri.  
  
 Le tabelle temporanee vengono eliminate automaticamente quando non sono più comprese nell'ambito, a meno di eliminarle in modo esplicito tramite l'istruzione DROP TABLE:  
  
-   Una tabella temporanea locale creata in una stored procedure viene eliminata automaticamente al termine della stored procedure. È possibile fare riferimento alla tabella da qualsiasi stored procedure nidificata eseguita dalla stored procedure con cui è stata creata la tabella. Non è invece possibile fare riferimento alla tabella dal processo che ha chiamato la stored procedure con cui è stata creata la tabella.  
  
-   Tutte le altre tabelle temporanee locali vengono eliminate automaticamente alla fine della sessione corrente.  
  
-   Le tabelle temporanee globali vengono eliminate automaticamente alla fine della sessione in cui è stata creata la tabella e quando tutte le altre attività non vi fanno più riferimento. L'associazione tra un'attività e una tabella viene mantenuta solo per la durata di una singola istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)]. Una tabella temporanea globale viene pertanto eliminata dopo il completamento dell'ultima istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] che fa attivamente riferimento alla tabella alla fine della sessione di creazione.  
  
 Una tabella temporanea locale creata all'interno di una stored procedure o in un trigger può avere lo stesso nome di una tabella temporanea creata prima della chiamata alla stored procedure o al trigger. Se tuttavia una query fa riferimento a una tabella temporanea e sono disponibili due tabelle temporanee con lo stesso nome, non è possibile stabilire in base a quale tabella verrà risolta la query. Anche le stored procedure nidificate possono creare tabelle temporanee con lo stesso nome di una tabella temporanea creata dalla stored procedure chiamante. In questo caso, tuttavia, per fare in modo che le modifiche vengano applicate alla tabella creata nella stored procedure nidificata, è necessario che la struttura della tabella e i nomi di colonna siano identici a quelli della tabella creata nella procedura chiamante, come illustrato nell'esempio seguente.  
  
```  
CREATE PROCEDURE dbo.Test2  
AS  
    CREATE TABLE #t(x INT PRIMARY KEY);  
    INSERT INTO #t VALUES (2);  
    SELECT Test2Col = x FROM #t;  
GO  
  
CREATE PROCEDURE dbo.Test1  
AS  
    CREATE TABLE #t(x INT PRIMARY KEY);  
    INSERT INTO #t VALUES (1);  
    SELECT Test1Col = x FROM #t;  
EXEC Test2;  
GO  
  
CREATE TABLE #t(x INT PRIMARY KEY);  
INSERT INTO #t VALUES (99);  
GO  
  
EXEC Test1;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 (1 row(s) affected) 
 Test1Col 
 ----------- 
 1 

 (1 row(s) affected) 
 Test2Col 
 ----------- 
 2 
 ```
  
 Quando si creano tabelle temporanee locali o globali, la sintassi dell'istruzione CREATE TABLE supporta le definizioni di vincolo, ad eccezione dei vincoli FOREIGN KEY. Se si specifica un vincolo FOREIGN KEY in una tabella temporanea, l'istruzione restituisce un messaggio di avviso per segnalare che il vincolo è stato ignorato. La tabella viene comunque creata senza i vincoli FOREIGN KEY. Non è possibile fare riferimento a tabelle temporanee nei vincoli FOREIGN KEY.  
  
 Se una tabella temporanea viene creata con un vincolo denominato e all'interno dell'ambito di una transazione definita dall'utente, solo un utente alla volta può eseguire l'istruzione che crea la tabella temporanea. Se ad esempio una stored procedure crea una tabella temporanea con un vincolo di chiave primaria denominato, la stored procedure non può essere eseguita simultaneamente dai più utenti.  


## <a name="database-scoped-global-temporary-tables-azure-sql-database"></a>Le tabelle temporanee globali (Database SQL di Azure) con ambito database

Le tabelle temporanee globali per SQL Server (avviata con # # nome della tabella) sono archiviate in tempdb e condivise tra le sessioni di tutti gli utenti nell'intera istanza di SQL Server. Per informazioni sui tipi di tabella SQL, vedere la sezione precedente nella creazione di tabelle.  

Database SQL di Azure supporta le tabelle temporanee globali sono inoltre archiviate in tempdb e il cui ambite al livello di database.  Ciò significa che le tabelle temporanee globali vengono condivisi per le sessioni di tutti gli utenti all'interno del database SQL di Azure stesso. Le sessioni utente dagli altri database di SQL Azure non è possibile accedere a tabelle temporanee globali.

Le tabelle temporanee globali per il database SQL di Azure seguono la stessa sintassi e semantica utilizzata da SQL Server per le tabelle temporanee.  Analogamente, stored procedure temporanee globali sono limitate anche al livello di database nel database di SQL Azure. Tabelle temporanee locali (avviate con il nome di tabella #) sono supportate anche per Database SQL di Azure e seguano la stessa sintassi e semantica utilizzata da SQL Server.  Vedere la sezione precedente relativa [tabelle temporanee](#temporary-tables).  

> [!IMPORTANT]
> Questa funzionalità è disponibile in anteprima pubblica e disponibile per il Database SQL di Azure.
>

### <a name="troubleshooting-global-temporary-tables-for-azure-sql-db"></a>Risoluzione dei problemi relativi a tabelle temporanee globali per il database SQL di Azure 

Per la risoluzione dei problemi di tempdb, vedere [spazio di risoluzione dei problemi di disco insufficiente in tempdb](https://technet.microsoft.com/library/ms176029%28v=sql.105%29.aspx?f=255&MSPPError=-2147217396). Per accedere le DMV di risoluzione dei problemi nel Database di SQL Azure, è necessario essere un amministratore del server.
  
### <a name="permissions"></a>Permissions  

 Qualsiasi utente può creare oggetti temporanei globali. Gli utenti possono accedere solo ai propri oggetti, a meno che non ottengano ulteriori autorizzazioni. .  
  
### <a name="examples"></a>Esempi 

- Sessione crea una tabella temporanea globale ##test nel Database SQL di Azure testdb1 e aggiunge la 1 riga

```tsql
CREATE TABLE ##test ( a int, b int);
INSERT INTO ##test values (1,1);

--Obtain object ID for temp table ##test 
SELECT OBJECT_ID('tempdb.dbo.##test') AS 'Object ID'; 

---Result
1253579504

---Obtain global temp table name for a given object ID 1253579504 in tempdb (2)
SELECT name FROM tempdb.sys.objects WHERE object_id = 1253579504

---Result
##test
```
- Sessione B si connette al Database SQL di Azure testdb1 e può accedere a tabella ##test creato da una sessione

```tsql
SELECT * FROM ##test
---Results
1,1
```

- Sessione C si connette a un altro database in Database SQL di Azure testdb2 e desidera accedere ##test creato in testdb1. Questa selezione non riesce a causa dell'ambito del database per le tabelle temporanee globali 

```tsql
SELECT * FROM ##test
---Results
Msg 208, Level 16, State 0, Line 1
Invalid object name '##test'
```

- Indirizzamento di oggetto di sistema nel Database SQL di Azure tempdb dal testdb1 di database utente corrente

```tsql
SELECT * FROM tempdb.sys.objects
SELECT * FROM tempdb.sys.columns
SELECT * FROM tempdb.sys.database_files
```



## <a name="partitioned-tables"></a>Tabelle partizionate  
 Prima di creare una tabella partizionata con CREATE TABLE, è necessario creare una funzione di partizione per specificare la modalità di partizionamento della tabella. Viene creata una funzione di partizione utilizzando [CREATE PARTITION FUNCTION](../../t-sql/statements/create-partition-function-transact-sql.md). In secondo luogo, è necessario creare uno schema di partizione per specificare i filegroup di destinazione delle partizioni indicate dalla funzione di partizione. Viene creato uno schema di partizione utilizzando [CREATE PARTITION SCHEME](../../t-sql/statements/create-partition-scheme-transact-sql.md). Per le tabelle partizionate non è possibile posizionare i vincoli PRIMARY KEY o UNIQUE in filegroup diversi. Per altre informazioni, vedere [Partitioned Tables and Indexes](../../relational-databases/partitions/partitioned-tables-and-indexes.md).  
  
## <a name="primary-key-constraints"></a>Vincoli PRIMARY KEY  
  
-   In una tabella è possibile includere un solo vincolo PRIMARY KEY.  
  
-   Se l'indice viene generato da un vincolo PRIMARY KEY, nella tabella sarà possibile creare non più di 999 indici non cluster e di 1 indice cluster.  
  
-   Nel caso in cui per un vincolo PRIMARY KEY non si specifichi CLUSTERED né NONCLUSTERED, verrà utilizzato automaticamente il valore CLUSTERED se per i vincoli UNIQUE non sono specificati indici cluster.  
  
-   Tutte le colonne specificate in un vincolo PRIMARY KEY devono essere definite come NOT NULL. Se non si specifica il supporto di valori Null, per tutte le colonne coinvolte in un vincolo PRIMARY KEY viene impostato NOT NULL.  
  
    > [!NOTE]  
    >  Per le tabelle con ottimizzazione per la memoria, la colonna chiave che ammettono valori null è consentita.  
  
-   Se si definisce una chiave primaria in una colonna di tipo CLR definito dall'utente, è necessario che l'implementazione del tipo supporti l'ordinamento binario. Per altre informazioni, vedere [Tipi CLR definiti dall'utente](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md).  
  
## <a name="unique-constraints"></a>Vincoli UNIQUE  
  
-   Se per un vincolo UNIQUE non si specifica CLUSTERED né NONCLUSTERED, il valore predefinito è NONCLUSTERED.  
  
-   Ogni vincolo UNIQUE genera un indice. Il numero di vincoli UNIQUE non deve generare un numero di indici della tabella maggiore di 999, in caso di indici non cluster, e di 1, in caso di indici cluster.  
  
-   Se si definisce un vincolo UNIQUE in una colonna di tipo CLR definito dall'utente, è necessario che l'implementazione del tipo supporti l'ordinamento binario o basato su operatore. Per altre informazioni, vedere [Tipi CLR definiti dall'utente](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md).  
  
## <a name="foreign-key-constraints"></a>Vincoli FOREIGN KEY  
  
-   I valori diversi da NULL immessi nella colonna di un vincolo FOREIGN KEY devono essere presenti nella colonna a cui viene fatto riferimento. In caso contrario, viene restituito un messaggio di errore di violazione della chiave esterna.  
  
-   I vincoli FOREIGN KEY vengono applicati alla colonna precedente, a meno che non vengano specificate colonne di origine.  
  
-   I vincoli FOREIGN KEY possono fare riferimento solo a tabelle di un singolo database nello stesso server. L'integrità referenziale tra database diversi deve essere implementata tramite trigger. Per altre informazioni, vedere [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md).  
  
-   I vincoli FOREIGN KEY possono fare riferimento a un'altra colonna nella stessa tabella. Questo tipo di vincolo viene definito autoreferenziale.  
  
-   La clausola REFERENCES di un vincolo FOREIGN KEY a livello di colonna può includere una sola colonna di riferimento. Il tipo di dati di tale colonna deve essere uguale al tipo di dati della colonna in cui viene definito il vincolo.  
  
-   La clausola REFERENCES di un vincolo FOREIGN KEY a livello di tabella deve includere lo stesso numero di colonne di riferimento di quelle presenti nell'elenco di colonne del vincolo. Il tipo di dati di ogni colonna di riferimento deve inoltre essere uguale a quello della colonna corrispondente nell'elenco di colonne.  
  
-   Non è possibile specificare CASCADE, SET NULL o SET DEFAULT se una colonna di tipo **timestamp** fa parte di chiave esterna o la chiave di cui si fa riferimento.  
  
-   È possibile combinare le azioni CASCADE, SET NULL, SET DEFAULT e NO ACTION in tabelle con relazioni referenziali reciproche. Se [!INCLUDE[ssDE](../../includes/ssde-md.md)] rileva l'azione NO ACTION, l'operazione viene arrestata e viene eseguito il rollback delle azioni CASCADE, SET NULL e SET DEFAULT correlate. Quando un'istruzione DELETE genera una combinazione di azioni CASCADE, SET NULL, SET DEFAULT e NO ACTION, tutte le azioni CASCADE, SET NULL e SET DEFAULT vengono applicate prima che il [!INCLUDE[ssDE](../../includes/ssde-md.md)] verifichi l'esistenza di azioni NO ACTION.  
  
-   Il [!INCLUDE[ssDE](../../includes/ssde-md.md)] non prevede un limite predefinito per il numero di vincoli FOREIGN KEY che possono essere inclusi in una tabella e che fanno riferimento ad altre tabelle o per il numero di vincoli FOREIGN KEY di proprietà di altre tabelle che fanno riferimento a una tabella specifica.  
  
     Il numero effettivo di vincoli FOREIGN KEY che è possibile usare, tuttavia, è limitato dalla configurazione hardware e dalla progettazione del database e dell'applicazione. È consigliabile evitare che una tabella contenga più di 253 vincoli FOREIGN KEY e che più di 253 vincoli FOREIGN KEY facciano riferimento alla tabella stessa. Il limite effettivo potrebbe variare a seconda dell'applicazione e della configurazione hardware. Nella progettazione di database e applicazioni è opportuno valutare i costi correlati all'applicazione dei vincoli FOREIGN KEY.  
  
-   I vincoli FOREIGN KEY non vengono applicati nelle tabelle temporanee.  
  
-   I vincoli FOREIGN KEY possono fare riferimento solo alle colonne di vincoli PRIMARY KEY o UNIQUE della tabella a cui si fa riferimento o alle colonne in un indice univoco di tale tabella.  
  
-   Se si definisce una chiave esterna su una colonna di tipo CLR definito dall'utente, è necessario che l'implementazione del tipo supporti l'ordinamento binario. Per altre informazioni, vedere [Tipi CLR definiti dall'utente](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md).  
  
-   Le colonne incluse in una relazione di chiave esterna devono essere definite con la stessa lunghezza e la stessa scala.  
  
## <a name="default-definitions"></a>Definizioni DEFAULT  
  
-   Una colonna può contenere una sola definizione DEFAULT.  
  
-   Una definizione DEFAULT può includere valori costanti, funzioni, funzioni senza parametri standard SQL o valori NULL. Nella tabella seguente sono illustrati le funzioni senza parametri e i valori predefiniti corrispondenti restituiti durante un'istruzione INSERT.  
  
    |Funzione senza parametri SQL-92|Valore restituito|  
    |------------------------------|--------------------|  
    |CURRENT_TIMESTAMP|Data e ora correnti.|  
    |CURRENT_USER|Nome dell'utente che esegue un inserimento.|  
    |SESSION_USER|Nome dell'utente che esegue un inserimento.|  
    |SYSTEM_USER|Nome dell'utente che esegue un inserimento.|  
    |Utente|Nome dell'utente che esegue un inserimento.|  
  
-   *constant_expression* predefinita definizione non può fare riferimento a un'altra colonna nella tabella o di altre tabelle, viste o stored procedure.  
  
-   Non è possibile creare definizioni DEFAULT in colonne con un **timestamp** tipo di dati o le colonne con una proprietà IDENTITY.  
  
-   Non è possibile creare definizioni DEFAULT per colonne con tipo di dati alias se tale tipo di dati è associato a un oggetto predefinito.  
  
## <a name="check-constraints"></a>Vincoli CHECK  
  
-   Una colonna può contenere un numero qualsiasi di vincoli CHECK e la condizione può includere più espressioni logiche unite tramite gli operatori AND e OR. Più vincoli CHECK per una colonna vengono convalidati nell'ordine di creazione.  
  
-   La condizione di ricerca deve restituire un'espressione booleana e non può fare riferimento a un'altra tabella.  
  
-   Un vincolo CHECK a livello di colonna può fare riferimento solo alla colonna vincolata, mentre un vincolo CHECK a livello di tabella può fare riferimento solo alle colonne della stessa tabella.  
  
     Le regole e i vincoli CHECK svolgono la stessa funzione di convalida dei dati durante l'esecuzione delle istruzioni INSERT e UPDATE.  
  
-   Quando per una o più colonne sono definiti una regola e uno o più vincoli CHECK, vengono valutate tutte le restrizioni.  
  
-   Impossibile definire vincoli CHECK su **testo**, **ntext**, o **immagine** colonne.  
  
## <a name="additional-constraint-information"></a>Informazioni aggiuntive sui vincoli  
  
-   L'istruzione DROP INDEX non consente di eliminare un indice creato per un vincolo. Per eliminare il vincolo, è necessario usare l'istruzione ALTER TABLE. Un indice creato per un vincolo specifico e da esso utilizzato può essere ricompilato tramite l'istruzione ALTER INDEX...REBUILD. Per altre informazioni, vedere [Riorganizzare e ricompilare gli indici](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).  
  
-   I nomi di vincolo devono seguire le regole per [identificatori](../../relational-databases/databases/database-identifiers.md), ad eccezione del fatto che il nome non può iniziare con un simbolo di cancelletto (#). Se *constraint_name* viene omesso, il vincolo viene assegnato un nome generato dal sistema. Il nome del vincolo viene indicato nei messaggi di errore relativi alle violazioni di vincolo.  
  
-   Quando in un'istruzione INSERT, UPDATE o DELETE viene violato un vincolo, l'istruzione viene interrotta. Con l'impostazione OFF per SET XACT_ABORT, tuttavia, la transazione continua a essere elaborata se l'istruzione fa parte di una transazione esplicita. Se l'impostazione di SET XACT_ABORT è ON, viene eseguito il rollback dell'intera transazione. È inoltre possibile utilizzare l'istruzione ROLLBACK TRANSACTION con la definizione di transazione controllando il @@ERROR funzione di sistema.  
  
-   Con ALLOW_ROW_LOCKS = ON e ALLOW_PAGE_LOCK = ON, sono consentiti blocchi a livello di riga, di pagina e di tabella per l'accesso all'indice. [!INCLUDE[ssDE](../../includes/ssde-md.md)] sceglie il blocco appropriato e può eseguire un'escalation del blocco da un blocco di riga o di pagina a un blocco di tabella. Se ALLOW_ROW_LOCKS = OFF e ALLOW_PAGE_LOCK = OFF, sono consentiti solo blocchi a livello di tabella per l'accesso all'indice.  
  
-   Se una tabella include vincoli FOREIGN KEY o CHECK e trigger, le condizioni di vincolo vengono valutate prima dell'esecuzione del trigger.  
  
 Per un report in una tabella e le relative colonne, utilizzare **sp_help** o **sp_helpconstraint**. Per rinominare una tabella, utilizzare **sp_rename**. Per un report sulle viste e stored procedure che dipendono da una tabella, utilizzare [Sys.dm sql_referenced_entities](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md) e [Sys.dm sql_referencing_entities](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md).  
  
## <a name="nullability-rules-within-a-table-definition"></a>Regole per il supporto di valori Null all'interno di una definizione di tabella  
 L'impostazione del supporto di valori Null per una colonna determina se la colonna ammette o meno valori Null (NULL) come dati. NULL non equivale né a zero né a uno spazio vuoto, ma indica che non è stata immessa alcuna voce oppure che è stato specificato un valore NULL esplicito e in genere implica che il valore è sconosciuto o non applicabile.  
  
 Quando si crea o si modifica una tabella con l'istruzione CREATE TABLE o ALTER TABLE, le impostazioni del database e della sessione influiscono ed eventualmente sono prioritarie sull'impostazione del supporto di valori Null per il tipo di dati in una definizione di colonna. È consigliabile definire sempre in modo esplicito una colonna come NULL o NOT NULL per le colonne non calcolate oppure, se si utilizza un tipo di dati definito dall'utente, consentire nella colonna l'utilizzo dell'impostazione predefinita relativa al supporto di valori Null per tale tipo di dati. Le colonne di tipo sparse devono consentire sempre valori Null.  
  
 Se non si specifica in modo esplicito il supporto di valori Null per una colonna, saranno valide le regole indicate nella tabella seguente.  
  
|Tipo di dati colonna|Rule|  
|----------------------|----------|  
|Tipo di dati alias|[!INCLUDE[ssDE](../../includes/ssde-md.md)] utilizza l'impostazione del supporto di valori Null specificata in fase di creazione del tipo di dati. Per determinare i valori null del tipo di dati predefiniti, utilizzare **sp_help**.|  
|Tipo CLR definito dall'utente|Il supporto dei valori Null viene stabilito in base alla definizione della colonna.|  
|Tipo di dati fornito dal sistema|Se il tipo di dati fornito dal sistema prevede una sola opzione, questa ha la precedenza. **timestamp** devono essere tipi di dati non NULL. Quando sono presenti impostazioni di sessione specificate su ON tramite SET:<br />**ANSI_NULL_DFLT_ON** = ON, viene assegnato il valore NULL.  <br />**ANSI_NULL_DFLT_OFF** = ON, non è assegnato il valore NULL.<br /><br /> Quando sono presenti impostazioni del database configurate tramite ALTER DATABASE:<br />**ANSI_NULL_DEFAULT_ON** = ON, viene assegnato il valore NULL.  <br />**ANSI_NULL_DEFAULT_OFF** = ON, non è assegnato il valore NULL.<br /><br /> Per visualizzare l'impostazione del database per ANSI_NULL_DEFAULT, usare il **Sys. Databases** vista del catalogo|  
  
 Quando per la sessione non è impostata alcuna opzione ANSI_NULL_DFLT e per il database è impostato il valore predefinito (ANSI_NULL_DEFAULT è OFF), viene assegnato il valore predefinito NOT NULL.  
  
 Nel caso di una colonna calcolata, l'impostazione del supporto di valori Null viene sempre determinata automaticamente dal [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Per scoprire il supporto di valori null di questo tipo di colonna, utilizzare la funzione COLUMNPROPERTY con la **AllowsNull** proprietà.  
  
> [!NOTE]  
>  Per il driver ODBC di SQL Server e il provider Microsoft OLE DB per SQL Server l'impostazione predefinita dell'opzione ANSI_NULL_DFLT_ON è ON. Gli utenti di ODBC e OLE DB possono configurare questa impostazione nelle origini dati ODBC oppure tramite le proprietà o gli attributi di connessione impostati dall'applicazione.  
  
## <a name="data-compression"></a>Compressione dei dati  
 Le tabelle di sistema non possono essere abilitate per la compressione. Se non specificato diversamente, quando si crea una tabella la compressione dei dati è impostata su NONE. Se si specifica un elenco di partizioni o una partizione non compresa nell'intervallo, verrà generato un errore. Per altre informazioni sulla compressione dei dati, vedere [Compressione dei dati](../../relational-databases/data-compression/data-compression.md).  
  
 Per valutare il modo in cui la modifica dello stato di compressione influirà su una tabella, un indice o una partizione, usare la stored procedure [sp_estimate_data_compression_savings](../../relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql.md) .  
  
## <a name="permissions"></a>Permissions  
 Sono richieste l'autorizzazione CREATE TABLE per il database e l'autorizzazione ALTER per lo schema in cui viene creata la tabella.  
  
 Se una colonna nell'istruzione CREATE TABLE è definita con un tipo CLR definito dall'utente, è necessario che l'utente sia il proprietario del tipo o disponga dell'autorizzazione REFERENCES.  
  
 Se a una colonna nell'istruzione CREATE TABLE è associata una raccolta di XML Schema, è necessario che l'utente sia il proprietario della raccolta di XML Schema o disponga dell'autorizzazione REFERENCES.  
  
 Qualsiasi utente può creare tabelle temporanee in tempdb.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-create-a-primary-key-constraint-on-a-column"></a>A. Creare un vincolo PRIMARY KEY in una colonna  
 Nell'esempio seguente viene illustrata la definizione di colonna per un vincolo PRIMARY KEY con un indice cluster nella colonna `EmployeeID` della tabella `Employee`. Poiché un nome di vincolo non viene specificato, ne viene fornito uno dal sistema.  
  
```  
CREATE TABLE dbo.Employee (EmployeeID int  
PRIMARY KEY CLUSTERED);  
```  
  
### <a name="b-using-foreign-key-constraints"></a>B. Utilizzo di vincoli FOREIGN KEY  
 Il vincolo FOREIGN KEY viene utilizzato per fare riferimento a un'altra tabella. Le chiavi esterne possono essere chiavi a colonna singola o a più colonne. Nell'esempio seguente viene illustrato un vincolo FOREIGN KEY a colonna singola nella tabella `SalesOrderHeader` che fa riferimento alla tabella `SalesPerson`. Per un vincolo FOREIGN KEY a colonna singola è sufficiente specificare solo la clausola REFERENCES.  
  
```  
SalesPersonID int NULL  
REFERENCES SalesPerson(SalesPersonID)  
```  
  
 È inoltre possibile usare la clausola FOREIGN KEY in modo esplicito per ridefinire l'attributo di colonna. Si noti che il nome della colonna non deve essere identico in entrambe le tabelle.  
  
```  
FOREIGN KEY (SalesPersonID) REFERENCES SalesPerson(SalesPersonID)  
```  
  
 I vincoli con chiavi a più colonne vengono creati come vincoli di tabella. La tabella `SpecialOfferProduct` del database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] include un vincolo PRIMARY KEY a più colonne. Nell'esempio seguente viene illustrato come fare riferimento a questa chiave da un'altra tabella. Il nome di vincolo esplicito è facoltativo.  
  
```  
CONSTRAINT FK_SpecialOfferProduct_SalesOrderDetail FOREIGN KEY  
 (ProductID, SpecialOfferID)  
REFERENCES SpecialOfferProduct (ProductID, SpecialOfferID)  
```  
  
### <a name="c-using-unique-constraints"></a>C. Utilizzo di vincoli UNIQUE  
 I vincoli UNIQUE vengono utilizzati per imporre l'univocità di colonne chiave non primaria. Nell'esempio seguente viene applicata una restrizione per specificare che la colonna `Name` della tabella `Product` deve essere univoca.  
  
```  
Name nvarchar(100) NOT NULL  
UNIQUE NONCLUSTERED  
```  
  
### <a name="d-using-default-definitions"></a>D. Utilizzo di definizioni DEFAULT  
 I valori predefiniti forniscono un valore (tramite le istruzioni INSERT e UPDATE) nel caso in cui non ne viene specificato alcuno. Il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] potrebbe, ad esempio, includere una tabella di ricerca con un elenco dei vari ruoli professionali che possono essere assegnati ai dipendenti della società. Nella colonna destinata alla descrizione di ogni ruolo professionale, si potrebbe usare una stringa di caratteri predefinita per fornire una descrizione nel caso in cui questa non venga immessa in modo esplicito.  
  
```  
DEFAULT 'New Position - title not formalized yet'  
```  
  
 Oltre alle costanti, le definizioni DEFAULT possono includere funzioni. Per ottenere la data corrente per una voce, è possibile usare l'esempio seguente:  
  
```  
DEFAULT (getdate())  
```  
  
 È inoltre possibile migliorare l'integrità dei dati tramite un'analisi di funzioni senza parametri. Per tenere traccia dell'utente che ha inserito una riga, usare la funzione senza parametri per USER. Non racchiudere le funzioni senza parametri tra parentesi.  
  
```  
DEFAULT USER  
```  
  
### <a name="e-using-check-constraints"></a>E. Utilizzo di vincoli CHECK  
 Nell'esempio seguente viene illustrata l'applicazione di una restrizione ai valori immessi nella colonna `CreditRating` della tabella `Vendor`. Al vincolo non viene assegnato un nome.  
  
```  
CHECK (CreditRating >= 1 and CreditRating <= 5)  
```  
  
 Nell'esempio seguente viene illustrato un vincolo denominato con una restrizione basata su modello per i dati di tipo carattere immessi in una colonna di una tabella.  
  
```  
CONSTRAINT CK_emp_id CHECK (emp_id LIKE   
'[A-Z][A-Z][A-Z][1-9][0-9][0-9][0-9][0-9][FM]'   
OR emp_id LIKE '[A-Z]-[A-Z][1-9][0-9][0-9][0-9][0-9][FM]')  
```  
  
 Nell'esempio seguente viene specificato che i valori devono essere inclusi in un elenco specifico o essere conformi a un modello specificato.  
  
```  
CHECK (emp_id IN ('1389', '0736', '0877', '1622', '1756')  
OR emp_id LIKE '99[0-9][0-9]')  
```  
  
### <a name="f-showing-the-complete-table-definition"></a>F. Visualizzazione della definizione completa della tabella  
 Nell'esempio seguente vengono illustrate le definizioni di tabella complete con tutte le definizioni dei vincoli per la tabella `PurchaseOrderDetail` creata nel database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Per l'esecuzione dell'esempio, lo schema della tabella viene modificato in `dbo`.  
  
```  
CREATE TABLE dbo.PurchaseOrderDetail  
(  
    PurchaseOrderID int NOT NULL  
        REFERENCES Purchasing.PurchaseOrderHeader(PurchaseOrderID),  
    LineNumber smallint NOT NULL,  
    ProductID int NULL   
        REFERENCES Production.Product(ProductID),  
    UnitPrice money NULL,  
    OrderQty smallint NULL,  
    ReceivedQty float NULL,  
    RejectedQty float NULL,  
    DueDate datetime NULL,  
    rowguid uniqueidentifier ROWGUIDCOL  NOT NULL  
        CONSTRAINT DF_PurchaseOrderDetail_rowguid DEFAULT (newid()),  
    ModifiedDate datetime NOT NULL   
        CONSTRAINT DF_PurchaseOrderDetail_ModifiedDate DEFAULT (getdate()),  
    LineTotal  AS ((UnitPrice*OrderQty)),  
    StockedQty  AS ((ReceivedQty-RejectedQty)),  
    CONSTRAINT PK_PurchaseOrderDetail_PurchaseOrderID_LineNumber  
               PRIMARY KEY CLUSTERED (PurchaseOrderID, LineNumber)  
               WITH (IGNORE_DUP_KEY = OFF)  
)   
ON PRIMARY;  
```  
  
### <a name="g-creating-a-table-with-an-xml-column-typed-to-an-xml-schema-collection"></a>G. Creazione di una tabella con una colonna xml tipizzata in una raccolta di XML Schema  
 Nell'esempio seguente viene creata una tabella con una colonna `xml` tipizzata nella raccolta di XML Schema `HRResumeSchemaCollection`. Il `DOCUMENT` (parola chiave) specifica che ogni istanza del `xml` del tipo di dati *column_name* può contenere un solo elemento di primo livello.  
  
```  
CREATE TABLE HumanResources.EmployeeResumes   
   (LName nvarchar(25), FName nvarchar(25),   
    Resume xml( DOCUMENT HumanResources.HRResumeSchemaCollection) );  
```  
  
### <a name="h-creating-a-partitioned-table"></a>H. Creazione di una tabella partizionata  
 Nell'esempio seguente viene creata una funzione di partizione per suddividere una tabella o indice in quattro partizioni. Viene quindi creato uno schema di partizione per specificare i filegroup in cui posizionare ognuna delle quattro partizioni. Infine viene creata una tabella che utilizza tale schema di partizione. Nell'esempio si presuppone che i filegroup esistano già nel database.  
  
```  
CREATE PARTITION FUNCTION myRangePF1 (int)  
    AS RANGE LEFT FOR VALUES (1, 100, 1000) ;  
GO  
  
CREATE PARTITION SCHEME myRangePS1  
    AS PARTITION myRangePF1  
    TO (test1fg, test2fg, test3fg, test4fg) ;  
GO  
  
CREATE TABLE PartitionTable (col1 int, col2 char(10))  
    ON myRangePS1 (col1) ;  
GO  
```  
  
 Sulla base dei valori della colonna `col1` di `PartitionTable`, le partizioni vengono assegnate nei modi seguenti.  
  
|Filegroup|test1fg|test2fg|test3fg|test4fg|  
|---------------|-------------|-------------|-------------|-------------|  
|**Partizione**|1|2|3|4|  
|**Valori**|col 1 \<= 1|> 1 col1 e col1 \<= 100|col1 > 100 AND col1 \<= 1000|col1 > 1000|  
  
### <a name="i-using-the-uniqueidentifier-data-type-in-a-column"></a>I. Utilizzo del tipo di dati uniqueidentifier in una colonna  
 Nell'esempio seguente viene creata una tabella con una colonna `uniqueidentifier`. Il vincolo PRIMARY KEY viene utilizzato per evitare che gli utenti inseriscano valori duplicati nella tabella, mentre la funzione `NEWSEQUENTIALID()` nel vincolo `DEFAULT` fornisce i valori per le nuove righe. La proprietà ROWGUIDCOL viene applicata alla colonna `uniqueidentifier` in modo che sia possibile farvi riferimento tramite la parola chiave $ROWGUID.  
  
```  
CREATE TABLE dbo.Globally_Unique_Data  
    (guid uniqueidentifier   
        CONSTRAINT Guid_Default DEFAULT   
        NEWSEQUENTIALID() ROWGUIDCOL,  
    Employee_Name varchar(60)  
    CONSTRAINT Guid_PK PRIMARY KEY (guid) );  
```  
  
### <a name="j-using-an-expression-for-a-computed-column"></a>J. Utilizzo di un'espressione per una colonna calcolata  
 Nell'esempio seguente viene illustrato l'utilizzo di un'espressione (`(low + high)/2`) per calcolare la colonna calcolata `myavg`.  
  
```  
CREATE TABLE dbo.mytable   
    ( low int, high int, myavg AS (low + high)/2 ) ;  
```  
  
### <a name="k-creating-a-computed-column-based-on-a-user-defined-type-column"></a>K. Creazione di una colonna calcolata basata su una colonna di tipo definito dall'utente  
 Nell'esempio seguente viene creata una tabella con una colonna di tipo definito dall'utente `utf8string` presupponendo che l'assembly del tipo e il tipo stesso siano già stati creati nel database corrente. Una seconda colonna viene definita in base `utf8string`e Usa metodo `ToString()` di **type(class)** `utf8string` per calcolare un valore per la colonna.  
  
```  
CREATE TABLE UDTypeTable   
    ( u utf8string, ustr AS u.ToString() PERSISTED ) ;  
```  
  
### <a name="l-using-the-username-function-for-a-computed-column"></a>L. Utilizzo della funzione USER_NAME per una colonna calcolata  
 Nell'esempio seguente viene utilizzata la funzione `USER_NAME()` nella colonna `myuser_name`.  
  
```  
CREATE TABLE dbo.mylogintable  
    ( date_in datetime, user_id int, myuser_name AS USER_NAME() ) ;  
```  
  
### <a name="m-creating-a-table-that-has-a-filestream-column"></a>M. Creazione di una tabella con una colonna FILESTREAM  
 Nell'esempio seguente viene creata una tabella con una colonna `FILESTREAM` `Photo`. Se in una tabella sono presenti una o più colonne `FILESTREAM`, tale tabella deve includere anche una colonna `ROWGUIDCOL`.  
  
```  
CREATE TABLE dbo.EmployeePhoto  
    (  
    EmployeeId int NOT NULL PRIMARY KEY,  
    ,Photo varbinary(max) FILESTREAM NULL  
    ,MyRowGuidColumn uniqueidentifier NOT NULL ROWGUIDCOL  
        UNIQUE DEFAULT NEWID()  
    );  
```  
  
### <a name="n-creating-a-table-that-uses-row-compression"></a>N. Creazione di una tabella che utilizza la compressione di riga  
 Nell'esempio seguente viene creata una tabella che utilizza la compressione di riga.  
  
```  
CREATE TABLE dbo.T1   
(c1 int, c2 nvarchar(200) )  
WITH (DATA_COMPRESSION = ROW);  
```  
  
 Per esempi sulla compressione dei dati aggiuntivi, vedere [la compressione dei dati](../../relational-databases/data-compression/data-compression.md).  
  
### <a name="o-creating-a-table-that-has-sparse-columns-and-a-column-set"></a>O. Creazione di una tabella con colonne di tipo sparse e un set di colonne  
 Negli esempi seguenti viene illustrato come creare una tabella con una colonna di tipo sparse e una tabella con due colonne di tipo sparse e un set di colonne. Negli esempi viene utilizzata la sintassi di base. Per esempi più complessi, vedere [utilizzare le colonne di tipo Sparse](../../relational-databases/tables/use-sparse-columns.md) e [usare set di colonne](../../relational-databases/tables/use-column-sets.md).  
  
 Nell'esempio viene creata una tabella con una colonna di tipo sparse.  
  
```  
CREATE TABLE dbo.T1  
    (c1 int PRIMARY KEY,  
    c2 varchar(50) SPARSE NULL ) ;  
```  
  
 In questo esempio viene creata una tabella con due colonne di tipo sparse e un set di colonne denominato `CSet`.  
  
```  
CREATE TABLE T1  
    (c1 int PRIMARY KEY,  
    c2 varchar(50) SPARSE NULL,  
    c3 int SPARSE NULL,  
    CSet XML COLUMN_SET FOR ALL_SPARSE_COLUMNS ) ;  
```  
  
### <a name="p-creating-a-system-versioned-disk-based-temporal-table"></a>P. Creazione di una tabella di temporale con controllo delle versioni del sistema basata su disco  
   
  
**Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].
  
 Gli esempi seguenti mostrano come creare una tabella temporale collegata a una nuova tabella di cronologia e come creare una tabella temporale collegata a una tabella di cronologia esistente. Si noti che la tabella temporale deve avere una chiave primaria definita per poter essere abilitato per la tabella deve essere abilitata per il controllo delle versioni di sistema. Per esempi che illustra come aggiungere o rimuovere il controllo delle versioni di sistema in una tabella esistente, vedere controllo delle versioni di sistema in [esempi](../../t-sql/statements/alter-table-transact-sql.md#Example_Top). Per casi di utilizzo, vedere [le tabelle temporali](../../relational-databases/tables/temporal-tables.md).  
  
 Questo esempio crea una nuova tabella temporale collegata a una nuova tabella di cronologia.  
  
```  
CREATE TABLE Department   
(  
    DepartmentNumber char(10) NOT NULL PRIMARY KEY CLUSTERED,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID int  NULL,   
    ParentDepartmentNumber char(10) NULL,   
    SysStartTime datetime2 GENERATED ALWAYS AS ROW START HIDDEN NOT NULL,   
    SysEndTime datetime2 GENERATED ALWAYS AS ROW END HIDDEN NOT NULL,     
    PERIOD FOR SYSTEM_TIME (SysStartTime,SysEndTime)     
)  
WITH (SYSTEM_VERSIONING = ON);  
```  
  
 Questo esempio crea una nuova tabella temporale collegata a una tabella di cronologia esistente.  
  
```  
  
--Existing table   
CREATE TABLE Department_History   
(  
    DepartmentNumber char(10) NOT NULL,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID int  NULL,   
    ParentDepartmentNumber char(10) NULL,   
    SysStartTime datetime2 NOT NULL,   
    SysEndTime datetime2 NOT NULL   
);  
--Temporal table  
CREATE TABLE Department   
(  
    DepartmentNumber char(10) NOT NULL PRIMARY KEY CLUSTERED,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID INT  NULL,   
    ParentDepartmentNumber char(10) NULL,   
    SysStartTime datetime2 GENERATED ALWAYS AS ROW START HIDDEN NOT NULL,   
    SysEndTime datetime2 GENERATED ALWAYS AS ROW END HIDDEN NOT NULL,     
    PERIOD FOR SYSTEM_TIME (SysStartTime,SysEndTime)    
)  
WITH   
    (SYSTEM_VERSIONING = ON   
        (HISTORY_TABLE = dbo.Department_History, DATA_CONSISTENCY_CHECK = ON )  
    );  
```  
  
### <a name="q-creating-a-system-versioned-memory-optimized-temporal-table"></a>Q. Creazione di una tabella di temporale con controllo delle versioni del sistema con ottimizzazione per la memoria  
   
  
**Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].
  
 Nell'esempio seguente viene illustrato come creare una controllo delle versioni di sistema con ottimizzazione per la memoria tabella temporale collegata a una nuova tabella di cronologia basata su disco.  
  
 Questo esempio crea una nuova tabella temporale collegata a una nuova tabella di cronologia.  
  
```  
CREATE SCHEMA History  
GO  
CREATE TABLE dbo.Department   
(  
    DepartmentNumber char(10) NOT NULL PRIMARY KEY CLUSTERED,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID int  NULL,   
    ParentDepartmentNumber char(10) NULL,   
    SysStartTime datetime2 GENERATED ALWAYS AS ROW START HIDDEN NOT NULL,   
    SysEndTime datetime2 GENERATED ALWAYS AS ROW END HIDDEN NOT NULL,     
    PERIOD FOR SYSTEM_TIME (SysStartTime,SysEndTime)     
)  
WITH   
    (  
        MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA,  
            SYSTEM_VERSIONING = ON ( HISTORY_TABLE = History.DepartmentHistory )   
    );  
```  
  
 Questo esempio crea una nuova tabella temporale collegata a una tabella di cronologia esistente.  
  
```  
  
--Existing table   
CREATE TABLE Department_History   
(  
    DepartmentNumber char(10) NOT NULL,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID int  NULL,   
    ParentDepartmentNumber char(10) NULL,   
    SysStartTime datetime2 NOT NULL,   
    SysEndTime datetime2 NOT NULL   
);  
--Temporal table  
CREATE TABLE Department   
(  
    DepartmentNumber char(10) NOT NULL PRIMARY KEY CLUSTERED,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID INT  NULL,   
    ParentDepartmentNumber char(10) NULL,   
    SysStartTime datetime2 GENERATED ALWAYS AS ROW START HIDDEN NOT NULL,   
    SysEndTime datetime2 GENERATED ALWAYS AS ROW END HIDDEN NOT NULL,     
    PERIOD FOR SYSTEM_TIME (SysStartTime,SysEndTime)    
)  
WITH   
    (SYSTEM_VERSIONING = ON   
        (HISTORY_TABLE = dbo.Department_History, DATA_CONSISTENCY_CHECK = ON )  
    );  
```  
  
### <a name="r-creating-a-table-with-encrypted-columns"></a>R. Creazione di una tabella con colonne crittografate  
 Nell'esempio seguente viene creata una tabella con due colonne crittografate. Per altre informazioni, vedere [Always Encrypted &#40;Motore di database&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md).  
  
```  
CREATE TABLE Customers (  
    CustName nvarchar(60)   
        ENCRYPTED WITH   
            (  
             COLUMN_ENCRYPTION_KEY = MyCEK,  
             ENCRYPTION_TYPE = RANDOMIZED,  
             ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256'  
            ),   
    SSN varchar(11) COLLATE  Latin1_General_BIN2  
        ENCRYPTED WITH   
            (  
             COLUMN_ENCRYPTION_KEY = MyCEK,  
             ENCRYPTION_TYPE = DETERMINISTIC ,  
             ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256'  
            ),   
    Age int NULL  
);  
```

### <a name="s-create-an-inline-filtered-index"></a>S. Creare un indice filtrato inline 
Crea una tabelle con un indice filtrato inline.
  
  ```
  CREATE TABLE t1 
 (
      c1 int,
      index IX1  (c1) WHERE c1 > 0   
 )
GO
 ```
 
  
## <a name="see-also"></a>Vedere anche  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [COLUMNPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/columnproperty-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [CREATE VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/create-view-transact-sql.md)   
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [DROP INDEX &#40; Transact-SQL &#41;](../../t-sql/statements/drop-index-transact-sql.md)   
 [sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md)   
 [sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md)   
 [DROP TABLE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-table-transact-sql.md)   
 [CREATE PARTITION FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-function-transact-sql.md)   
 [CREATE PARTITION SCHEME &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-scheme-transact-sql.md)   
 [CREATE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/create-type-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [sp_helpconstraint &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpconstraint-transact-sql.md)   
 [sp_rename &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)   
 [sp_spaceused &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)  
  
  



