---
title: CREARE il tipo (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 04/11/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sql13.swb.sysdatatype.properties.f1
- CREATE TYPE
- TYPE_TSQL
- TYPE
- CREATE_TYPE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- UDTs [SQL Server], creating
- CLR user-defined types [SQL Server]
- user-defined table types [SQL Server]
- user-defined types [SQL Server], creating
- CREATE TYPE statement
- alias data types [SQL Server], creating
- data types [SQL Server], creating
ms.assetid: 2202236b-e09f-40a1-bbc7-b8cff7488905
caps.latest.revision: 92
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4e7f411871d98fc6854b97478402567017d28222
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="create-type-transact-sql"></a>CREATE TYPE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Crea un tipo di dati alias o un tipo definito dall'utente (UDT) nel database corrente in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. L'implementazione di un tipo di dati alias è basata su un tipo di sistema nativo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Un tipo definito dall'utente viene implementato tramite una classe di un assembly nel [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] common language runtime (CLR). Per associare un tipo definito dall'utente alla relativa implementazione, l'assembly CLR che contiene l'implementazione del tipo deve essere prima registrata nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzando [CREATE ASSEMBLY](../../t-sql/statements/create-assembly-transact-sql.md).  
  
 Per impostazione predefinita, l'esecuzione di codice CLR è disattivata in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. È possibile creare, modificare e rilasciare gli oggetti di database che fanno riferimento a moduli di codice gestito, ma tali riferimenti non verranno eseguiti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , a meno che il [opzione clr enabled](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) abilitata utilizzando [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
 
> [!NOTE]  
>  Integrazione di CLR di .NET Framework in SQL Server viene illustrata in questo argomento. Integrazione con CLR non si applica ad Azure [!INCLUDE[ssSDS](../../includes/sssds-md.md)].
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Disk-Based Type Syntax  
CREATE TYPE [ schema_name. ] type_name  
{   
    FROM base_type   
    [ ( precision [ , scale ] ) ]  
    [ NULL | NOT NULL ]   
  | EXTERNAL NAME assembly_name [ .class_name ]   
  | AS TABLE ( { <column_definition> | <computed_column_definition> }  
        [ <table_constraint> ] [ ,...n ] )    
} [ ; ]  
  
<column_definition> ::=  
column_name <data_type>  
    [ COLLATE collation_name ]   
    [ NULL | NOT NULL ]  
    [   
        DEFAULT constant_expression ]   
      | [ IDENTITY [ ( seed ,increment ) ]   
    ]  
    [ ROWGUIDCOL ] [ <column_constraint> [ ...n ] ]   
  
<data type> ::=   
[ type_schema_name . ] type_name   
    [ ( precision [ , scale ] | max |   
                [ { CONTENT | DOCUMENT } ] xml_schema_collection ) ]   
  
<column_constraint> ::=   
{     { PRIMARY KEY | UNIQUE }   
        [ CLUSTERED | NONCLUSTERED ]   
        [   
            WITH ( <index_option> [ ,...n ] )   
        ]  
  | CHECK ( logical_expression )   
}   
  
<computed_column_definition> ::=  
  
column_name AS computed_column_expression   
[ PERSISTED [ NOT NULL ] ]  
[   
    { PRIMARY KEY | UNIQUE }  
        [ CLUSTERED | NONCLUSTERED ]  
        [   
            WITH ( <index_option> [ ,...n ] )  
        ]  
    | CHECK ( logical_expression )   
]   
  
<table_constraint> ::=  
{   
    { PRIMARY KEY | UNIQUE }   
        [ CLUSTERED | NONCLUSTERED ]   
    ( column [ ASC | DESC ] [ ,...n ] )   
        [   
    WITH ( <index_option> [ ,...n ] )   
        ]  
    | CHECK ( logical_expression )   
}   
  
<index_option> ::=  
{  
    IGNORE_DUP_KEY = { ON | OFF }  
}  
```  
  
```  
-- Memory-Optimized Table Type Syntax  
CREATE TYPE [schema_name. ] type_name  
AS TABLE ( { <column_definition> }  
    |  [ <table_constraint> ] [ ,... n ]    
    | [ <table_index> ] [ ,... n ]    } )
    [ WITH ( <table_option> [ ,... n ] ) ]  
 [ ; ]  
  
<column_definition> ::=  
column_name <data_type>  
    [ COLLATE collation_name ]   [ NULL | NOT NULL ]    [  
      [ IDENTITY [ (1 , 1) ]  
    ]  
    [ <column_constraint> [ ... n ] ]    [ <column_index> ]  
  
<data type> ::=  
 [type_schema_name . ] type_name [ (precision [ , scale ]) ]  
  
<column_constraint> ::=  
{ PRIMARY KEY {   NONCLUSTERED HASH WITH (BUCKET_COUNT = bucket_count) 
                | NONCLUSTERED } }  
  
< table_constraint > ::=  
{ PRIMARY KEY { NONCLUSTERED HASH (column [ ,... n ] ) 
                   WITH (BUCKET_COUNT = bucket_count) 
               | NONCLUSTERED  (column [ ASC | DESC ] [ ,... n ] )  } }  
  
<column_index> ::=  
  INDEX index_name  
{ { [ NONCLUSTERED ] HASH WITH (BUCKET_COUNT = bucket_count) 
     | NONCLUSTERED } }  
  
< table_index > ::=  
  INDEX constraint_name  
{ { [ NONCLUSTERED ] HASH (column [ ,... n ] ) WITH (BUCKET_COUNT = bucket_count) 
 |  [NONCLUSTERED]  (column [ ASC | DESC ] [ ,... n ] )} }  
  
<table_option> ::=  
{  
    [MEMORY_OPTIMIZED = {ON | OFF}]  
}  
```  
  
## <a name="arguments"></a>Argomenti  
 *schema_name*  
 Nome dello schema a cui appartiene il tipo di dati alias o il tipo definito dall'utente.  
  
 *TYPE_NAME*  
 Nome del tipo di dati alias o del tipo definito dall'utente. I nomi dei tipi devono essere conformi alle regole per [identificatori](../../relational-databases/databases/database-identifiers.md).  
  
 *base_type*  
 È il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] il tipo di dati su cui è basato il tipo di dati alias. *base_type* è **sysname**e non prevede alcun valore predefinito può essere uno dei valori seguenti:  
  
|||||  
|-|-|-|-|  
|**bigint**|**binario (**  *n*  **)**|**bit**|**Char (**  *n*  **)**|  
|**data**|**datetime**|**datetime2**|**datetimeoffset**|  
|**decimal**|**float**|**image**|**int**|  
|**money**|**nchar (**  *n*  **)**|**ntext**|**numeric**|  
|**nvarchar (**  *n*  &#124; **max)**|**real**|**smalldatetime**|**smallint**|  
|**smallmoney**|**sql_variant**|**text**|**time**|  
|**tinyint**|**uniqueidentifier**|**varbinary (**  *n*  &#124; **max)**|**varchar (**  *n*  &#124; **max)**|  
  
 *base_type* può anche essere di qualsiasi sinonimo di tipo di dati che esegue il mapping a uno di questi tipi di dati di sistema.  
  
 *precisione*  
 Per **decimale** o **numerico**, è un numero intero non negativo che indica il numero totale massimo di cifre decimali che è possibile archiviare, sia a sinistra e a destra del separatore decimale. Per ulteriori informazioni, vedere [decimal e numeric &#40; Transact-SQL &#41; ](../../t-sql/data-types/decimal-and-numeric-transact-sql.md).  
  
 *scala*  
 Per **decimale** o **numerico**è un numero intero non negativo che indica il numero massimo di cifre decimali che è possibile archiviare a destra del separatore decimale e deve essere minore o uguale alla precisione . Per ulteriori informazioni, vedere [decimal e numeric &#40; Transact-SQL &#41; ](../../t-sql/data-types/decimal-and-numeric-transact-sql.md).  
  
 **NULL** | NON È NULL  
 Specifica se il tipo supporta la memorizzazione di valori Null. Se omesso, l'impostazione predefinita è NULL.  
  
 *nome_assembly*  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assembly che fa riferimento all'implementazione del tipo definito dall'utente in common language runtime. *nome_assembly* deve corrispondere a un assembly esistente in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nel database corrente.  
  
> [!NOTE]  
>  EXTERNAL_NAME non è disponibile in un database indipendente.  
  
 **[.** *CLASS_NAME***]**   
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica la classe nell'assembly che implementa il tipo definito dall'utente. *CLASS_NAME* deve essere un identificatore valido e deve esistere come classe nell'assembly con visibilità dell'assembly. *CLASS_NAME* tra maiuscole e minuscole, indipendentemente dalle regole di confronto di database e deve corrispondere esattamente al nome di classe nell'assembly corrispondente. Il nome della classe può essere un nome completo dello spazio tra parentesi quadre (**[]**) se il linguaggio di programmazione utilizzato per scrivere la classe viene utilizzato il concetto degli spazi dei nomi, ad esempio c#. Se *class_name* non viene specificato, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si presuppone che sia identico *type_name*.  
  
 \<column_definition >  
 Definisce le colonne per un tipo di tabella definito dall'utente.  
  
 \<tipo di dati >  
 Definisce il tipo di dati in una colonna con un tipo di tabella definito dall'utente. Per ulteriori informazioni sui tipi di dati, vedere [tipi di dati &#40; Transact-SQL &#41; ](../../t-sql/data-types/data-types-transact-sql.md). Per ulteriori informazioni sulle tabelle, vedere [CREATE TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-table-transact-sql.md).  
  
 \<column_constraint >  
 Definisce i vincoli di colonna per un tipo di tabella definito dall'utente. I vincoli supportati includono PRIMARY KEY, UNIQUE e CHECK. Per ulteriori informazioni sulle tabelle, vedere [CREATE TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-table-transact-sql.md).  
  
 \<computed_column_definition >  
 Definisce un'espressione di colonna calcolata come una colonna in un tipo di tabella definito dall'utente. Per ulteriori informazioni sulle tabelle, vedere [CREATE TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-table-transact-sql.md).  
  
 \<table_constraint >  
 Definisce un vincolo di tabella per un tipo di tabella definito dall'utente. I vincoli supportati includono PRIMARY KEY, UNIQUE e CHECK.  
  
 \<index_option >  
 Specifica il tipo di risposta in caso di errori di valori di chiave duplicati in un'operazione di inserimento di più righe su un indice cluster o non cluster univoco. Per ulteriori informazioni sulle opzioni di indice, vedere [CREATE INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/create-index-transact-sql.md).  
  
 INDEX  
 È necessario specificare gli indici di tabella e di colonna come parte dell'istruzione CREATE TABLE. CREATE INDEX e DROP INDEX non sono supportati per le tabelle con ottimizzazione per la memoria.  
  
 MEMORY_OPTIMIZED  
 **Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Indica se il tipo di tabella è con ottimizzazione per la memoria. Questa opzione è disabilitata per impostazione predefinita; il tipo di tabella o la tabella non è con ottimizzazione per la memoria. I tipi di tabella con ottimizzazione per la memoria sono tabelle utente con ottimizzazione per la memoria, il cui schema è persistente su disco in modo analogo ad altre tabelle utente.  
  
 BUCKET_COUNT  
 **Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Indica il numero di bucket che deve essere creato nell'indice hash. Il valore massimo per BUCKET_COUNT in indici hash è 1.073.741.824. Per ulteriori informazioni sui numeri di bucket, vedere [indici per tabelle con ottimizzazione](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md). *valore di bucket_count* è un argomento obbligatorio.  
  
 HASH  
 **Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Indica che viene creato un indice HASH. Gli indici hash sono supportati solo nelle tabelle con ottimizzazione per la memoria.  
  
## <a name="remarks"></a>Osservazioni  
 La classe dell'assembly a cui fa riferimento in *nome_assembly*, e i relativi metodi devono soddisfare tutti i requisiti per l'implementazione di un tipo definito dall'utente in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per ulteriori informazioni su questi requisiti, vedere [tipi CLR definiti dall'utente](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md).  
  
 Ulteriori considerazioni:  
  
-   La classe può contenere metodi di overload, ma tali metodi possono essere chiamati solo da codice gestito e non da [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   Qualsiasi membro statico deve essere dichiarato come **const** o **readonly** se *nome_assembly* è SAFE o EXTERNAL_ACCESS.  
  
 Nell'ambito di un database può esistere un solo tipo definito dall'utente registrato per qualsiasi tipo specificato caricato in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da CLR. Se si crea un tipo definito dall'utente basato su un tipo CLR per cui esiste già un tipo definito dall'utente nel database, l'istruzione CREATE TYPE viene interrotta e viene generato un errore. Questa restrizione risulta necessaria per evitare ambiguità durante la risoluzione dei tipi SQL, nel caso su un tipo CLR possa essere eseguito il mapping a più di un tipo definito dall'utente.  
  
 Se qualsiasi metodo mutatore nel tipo restituito non *void*, l'istruzione CREATE TYPE non viene eseguito.  
  
 Per modificare un tipo definito dall'utente, è necessario eliminare il tipo tramite l'istruzione DROP TYPE e quindi ricrearlo.  
  
 A differenza dei tipi definiti dall'utente che vengono creati utilizzando **sp_addtype**, **pubblica** ruolo del database non viene concessa automaticamente l'autorizzazione REFERENCES per i tipi che vengono creati tramite CREATE TYPE. È necessario concedere l'autorizzazione separatamente.  
  
 Nei tipi di tabella definito dall'utente, i tipi definiti dall'utente che vengono utilizzati in strutturato *column_name* \<tipo dati > fanno parte di ambito dello schema del database in cui è definito il tipo di tabella. Per accedere ai tipi strutturati definiti dall'utente in un ambito diverso all'interno del database, usare nomi in due parti.  
  
 Nei tipi di tabella definiti dall'utente, la chiave primaria sulle colonne calcolate deve essere PERSISTED e NOT NULL.  
  
## <a name="memory-optimized-table-types"></a>Tipi di tabella con ottimizzazione per la memoria  
 A partire da [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], l'elaborazione dei dati in un tipo di tabella può essere eseguita nella memoria primaria e non su disco. Per altre informazioni, vedere [OLTP in memoria &#40;ottimizzazione in memoria&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md). Per esempi di codice che illustra come creare tipi di tabella con ottimizzazione per la memoria, vedere [la creazione di una tabella con ottimizzazione per la memoria e un'in modo nativo Stored Procedure compilata](../../relational-databases/in-memory-oltp/creating-a-memory-optimized-table-and-a-natively-compiled-stored-procedure.md).  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione CREATE TYPE nel database corrente e l'autorizzazione ALTER per *schema_name*. Se *schema_name* viene omesso, vengono applicate le regole predefinite per la risoluzione dei nomi per determinare lo schema dell'utente corrente. Se *nome_assembly* viene specificato, un utente deve disporre dell'autorizzazione REFERENCES su di esso o proprietari dell'assembly.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-creating-an-alias-type-based-on-the-varchar-data-type"></a>A. Creazione di un tipo alias basato sul tipo di dati varchar  
 Nell'esempio seguente viene creato un tipo alias basato sul tipo di dati di sistema `varchar`.  
  
```  
CREATE TYPE SSN  
FROM varchar(11) NOT NULL ;  
```  
  
### <a name="b-creating-a-user-defined-type"></a>B. Creazione di un tipo definito dall'utente  
 L'esempio seguente crea un tipo `Utf8String` che fa riferimento a classe `utf8string` nell'assembly `utf8string`. Prima di creare il tipo, l'assembly `utf8string` viene registrato nel database locale. Sostituire la parte binaria dell'istruzione CREATE ASSEMBLY con una descrizione valida.  
  
**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
CREATE ASSEMBLY utf8string  
AUTHORIZATION [dbi]   
FROM 0x4D... ;  
GO  
CREATE TYPE Utf8String   
EXTERNAL NAME utf8string.[Microsoft.Samples.SqlServer.utf8string] ;  
GO  
```  
  
### <a name="c-creating-a-user-defined-table-type"></a>C. Creazione di un tipo di tabella definito dall'utente  
 Nell'esempio seguente viene creato un tipo di tabella definito dall'utente con due colonne. Per ulteriori informazioni su come creare e utilizzare i parametri con valori di tabella, vedere [utilizzare parametri &#40; motore di Database &#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md).  
  
```  
CREATE TYPE LocationTableType AS TABLE   
    ( LocationName VARCHAR(50)  
    , CostRate INT );  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREAZIONE di ASSEMBLY &#40; Transact-SQL &#41;](../../t-sql/statements/create-assembly-transact-sql.md)   
 [TIPO di rilascio &#40; Transact-SQL &#41;](../../t-sql/statements/drop-type-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

