---
title: ALTER FUNCTION (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, pdw, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_FUNCTION_TSQL
- ALTER FUNCTION
dev_langs: TSQL
helpviewer_keywords:
- ALTER FUNCTION statement
- modifying functions
- functions [SQL Server], modifying
ms.assetid: 89f066ee-05ac-4439-ab04-d8c3d5911179
caps.latest.revision: "62"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 4b1008715d9cfd3e48945d0651f454253bc4e4bc
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="alter-function-transact-sql"></a>ALTER FUNCTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-pdw-md.md)]

  Modifica una funzione [!INCLUDE[tsql](../../includes/tsql-md.md)] o CLR esistente, creata in precedenza tramite l'istruzione CREATE FUNCTION, senza modificare le autorizzazioni o alterare eventuali trigger, stored procedure o funzioni dipendenti.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Transact-SQL Scalar Function Syntax    
ALTER FUNCTION [ schema_name. ] function_name   
( [ { @parameter_name [ AS ][ type_schema_name. ] parameter_data_type   
    [ = default ] }   
    [ ,...n ]  
  ]  
)  
RETURNS return_data_type  
    [ WITH <function_option> [ ,...n ] ]  
    [ AS ]  
    BEGIN   
        function_body   
        RETURN scalar_expression  
    END  
[ ; ]
```  

```
-- Transact-SQL Inline Table-Valued Function Syntax
ALTER FUNCTION [ schema_name. ] function_name   
( [ { @parameter_name [ AS ] [ type_schema_name. ] parameter_data_type   
    [ = default ] }   
    [ ,...n ]  
  ]  
)  
RETURNS TABLE  
    [ WITH <function_option> [ ,...n ] ]  
    [ AS ]  
    RETURN [ ( ] select_stmt [ ) ]  
[ ; ]  
```
  
```
-- Transact-SQL Multistatement Table-valued Function Syntax
ALTER FUNCTION [ schema_name. ] function_name   
( [ { @parameter_name [ AS ] [ type_schema_name. ] parameter_data_type   
    [ = default ] }   
    [ ,...n ]  
  ]  
)  
RETURNS @return_variable TABLE <table_type_definition>  
    [ WITH <function_option> [ ,...n ] ]  
    [ AS ]  
    BEGIN   
        function_body   
        RETURN  
    END  
[ ; ]  
```

```  
-- Transact-SQL Function Clauses   
<function_option>::=   
{  
    [ ENCRYPTION ]  
  | [ SCHEMABINDING ]  
  | [ RETURNS NULL ON NULL INPUT | CALLED ON NULL INPUT ]  
  | [ EXECUTE_AS_Clause ]  
} 

<table_type_definition>:: =   
( { <column_definition> <column_constraint>   
  | <computed_column_definition> }   
    [ <table_constraint> ] [ ,...n ]  
)   
<column_definition>::=  
{  
    { column_name data_type }  
    [ [ DEFAULT constant_expression ]   
      [ COLLATE collation_name ] | [ ROWGUIDCOL ]  
    ]  
    | [ IDENTITY [ (seed , increment ) ] ]  
    [ <column_constraint> [ ...n ] ]   
}  

<column_constraint>::=   
{  
    [ NULL | NOT NULL ]   
    { PRIMARY KEY | UNIQUE }  
      [ CLUSTERED | NONCLUSTERED ]   
        [ WITH FILLFACTOR = fillfactor   
        | WITH ( < index_option > [ , ...n ] )  
      [ ON { filegroup | "default" } ]  
  | [ CHECK ( logical_expression ) ] [ ,...n ]  
}  
  
<computed_column_definition>::=  
column_name AS computed_column_expression   
  
<table_constraint>::=  
{   
    { PRIMARY KEY | UNIQUE }  
      [ CLUSTERED | NONCLUSTERED ]   
      ( column_name [ ASC | DESC ] [ ,...n ] )  
        [ WITH FILLFACTOR = fillfactor   
        | WITH ( <index_option> [ , ...n ] )  
  | [ CHECK ( logical_expression ) ] [ ,...n ]  
}  
  
<index_option>::=  
{   
    PAD_INDEX = { ON | OFF }   
  | FILLFACTOR = fillfactor   
  | IGNORE_DUP_KEY = { ON | OFF }  
  | STATISTICS_NORECOMPUTE = { ON | OFF }   
  | ALLOW_ROW_LOCKS = { ON | OFF }  
  | ALLOW_PAGE_LOCKS ={ ON | OFF }   
}  
```
  
```
-- CLR Scalar and Table-Valued Function Syntax
ALTER FUNCTION [ schema_name. ] function_name   
( { @parameter_name [AS] [ type_schema_name. ] parameter_data_type   
    [ = default ] }   
    [ ,...n ]  
)  
RETURNS { return_data_type | TABLE <clr_table_type_definition> }  
    [ WITH <clr_function_option> [ ,...n ] ]  
    [ AS ] EXTERNAL NAME <method_specifier>  
[ ; ]  
```
  
```
-- CLR Function Clauses
<method_specifier>::=  
    assembly_name.class_name.method_name  
 
  
<clr_function_option>::=  
}  
    [ RETURNS NULL ON NULL INPUT | CALLED ON NULL INPUT ]  
  | [ EXECUTE_AS_Clause ]  
}  
  
<clr_table_type_definition>::=   
( { column_name data_type } [ ,...n ] )  
  
```  
  
```  
-- Syntax for In-Memory OLTP: Natively compiled, scalar user-defined function  
ALTER FUNCTION [ schema_name. ] function_name    
 ( [ { @parameter_name [ AS ][ type_schema_name. ] parameter_data_type   
    [ NULL | NOT NULL ] [ = default ] }   
    [ ,...n ]   
  ]   
)   
RETURNS return_data_type  
    [ WITH <function_option> [ ,...n ] ]   
    [ AS ]   
    BEGIN ATOMIC WITH (set_option [ ,... n ])  
        function_body   
        RETURN scalar_expression  
    END  
    
<function_option>::=   
{ |  NATIVE_COMPILATION   
  |  SCHEMABINDING   
  | [ EXECUTE_AS_Clause ]   
  | [ RETURNS NULL ON NULL INPUT | CALLED ON NULL INPUT ]   
}  
```   
  
## <a name="arguments"></a>Argomenti  
 *schema_name*  
 Nome dello schema a cui appartiene la funzione definita dall'utente.  
  
 *nome_funzione*  
 Funzione definita dall'utente che si desidera modificare.  
  
> [!NOTE]  
>  È necessario apporre le parentesi dopo il nome della funzione anche se non viene specificato alcun parametro.  
  
 **@***parameter_name*  
 Parametro della funzione definita dall'utente. È possibile dichiarare uno o più parametri.  
  
 Una funzione può avere al massimo 2.100 parametri. Il valore di ciascun parametro dichiarato deve essere specificato dall'utente quando viene eseguita la funzione, a meno che non venga definito un valore predefinito per tale parametro.  
  
 Specificare un nome di parametro con un simbolo di chiocciola (**@**) come primo carattere. Il nome del parametro deve essere conforme alle regole per [identificatori](../../relational-databases/databases/database-identifiers.md). I parametri sono locali rispetto alla funzione. È pertanto possibile utilizzare gli stessi nomi di parametro in altre funzioni. I parametri possono rappresentare solo costanti, non nomi di tabella, di colonna o di altri oggetti di database.  
  
> [!NOTE]  
>  ANSI_WARNINGS non viene applicata quando vengono trasmessi parametri in una stored procedure o in una funzione definita dall'utente oppure in caso di dichiarazione e impostazione delle variabili in un'istruzione batch. Ad esempio, se una variabile viene definita come **char (3)**e quindi impostato su un valore maggiore di tre caratteri, i dati vengono troncati alla dimensione definita e l'inserimento o aggiornamento istruzione ha esito positivo.  
  
 [ *type_schema_name.* ] *parameter_data_type*  
 Tipo di dati del parametro e, facoltativamente, lo schema a cui appartiene. Per [!INCLUDE[tsql](../../includes/tsql-md.md)] sono consentite funzioni, tutti i tipi di dati, inclusi i tipi CLR definiti dall'utente, ad eccezione di **timestamp** tipo di dati. Per le funzioni CLR sono consentiti tutti i tipi di dati, inclusi i tipi CLR definiti dall'utente, eccetto **testo**, **ntext**, **immagine**, e **timestamp** tipi di dati. I tipi non scalari **cursore** e **tabella** non può essere specificato come un tipo di dati di parametro nelle [!INCLUDE[tsql](../../includes/tsql-md.md)] o funzioni CLR.  
  
 Se *type_schema_name* non viene specificato, il [!INCLUDE[ssDEversion2005](../../includes/ssdeversion2005-md.md)] Cerca il *parameter_data_type* nell'ordine seguente:  
  
-   Schema contenente i nomi dei tipi di dati di sistema di SQL Server.  
  
-   Schema predefinito dell'utente corrente nel database corrente.  
  
-   Schema **dbo** nel database corrente.  
  
 [  **=**  *predefinito* ]  
 Valore predefinito del parametro. Se un *predefinito* valore è definito, la funzione può essere eseguita senza specificare un valore per tale parametro.  
  
> [!NOTE]  
>  Valori predefiniti dei parametri può essere specificato per le funzioni CLR, ad eccezione di **varchar (max)** e **varbinary (max)** tipi di dati.  
  
 Se a un parametro della funzione è associato un valore predefinito, quando si richiama la funzione per ottenere il valore predefinito è necessario specificare la parola chiave "default". Questo comportamento risulta diverso dall'utilizzo di parametri con valore predefinito nelle stored procedure in cui l'omissione del parametro implica l'utilizzo del valore predefinito.  
  
 *return_data_type*  
 Valore restituito di una funzione scalare definita dall'utente. Per [!INCLUDE[tsql](../../includes/tsql-md.md)] sono consentite funzioni, tutti i tipi di dati, inclusi i tipi CLR definiti dall'utente, ad eccezione di **timestamp** tipo di dati. Per le funzioni CLR sono consentiti tutti i tipi di dati, inclusi i tipi CLR definiti dall'utente, eccetto **testo**, **ntext**, **immagine**, e **timestamp** tipi di dati. I tipi non scalari **cursore** e **tabella** non può essere specificato come un tipo di dati restituito nelle [!INCLUDE[tsql](../../includes/tsql-md.md)] o funzioni CLR.  
  
 *function_body*  
 Specifica che una serie di istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)], che nel loro complesso non producono alcun effetto collaterale, ad esempio la modifica di una tabella, definisce il valore della funzione. *function_body* viene utilizzata solo in funzioni scalari e funzioni a istruzioni multiple con valori di tabella.  
  
 Nelle funzioni scalari, *function_body* è una serie di [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzioni che in combinazione restituiscono un valore scalare.  
  
 Nelle funzioni con valori di tabella con istruzioni multiple, *function_body* è una serie di [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzioni che popolano una tabella restituiscono variabile.  
  
 *scalar_expression*  
 Specifica che la funzione scalare restituisce un valore scalare.  
  
 TABLE  
 Specifica che il valore restituito della funzione con valori di tabella è una tabella. Solo costanti e  **@**  *local_variables* possono essere passati alle funzioni con valori di tabella.  
  
 Nelle funzioni inline con valori di tabella, il valore restituito TABLE viene definito tramite una sola istruzione SELECT. Alle funzioni inline non sono associate variabili restituite.  
  
 Nelle funzioni con valori di tabella con istruzioni multiple,  **@**  *return_variable* è una variabile TABLE utilizzata per archiviare e l'accumulo delle righe devono essere restituite come valore della funzione. **@***return_variable* può essere specificata solo per [!INCLUDE[tsql](../../includes/tsql-md.md)] le funzioni e non per le funzioni CLR.  
  
 *Select-istruzione*  
 Istruzione SELECT che definisce il valore restituito di una funzione inline con valori di tabella.  
  
 NOME esterno \<method_specifier >*assembly_name.class_name*. *nome_metodo*  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica il metodo di un assembly da associare alla funzione. *nome_assembly* deve corrispondere a un assembly esistente in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nel database corrente con visibilità attivata. *CLASS_NAME* deve essere un valore valido [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] identificatore e deve esistere come classe nell'assembly. Se la classe dispone di un nome completo dello spazio dei nomi che utilizza un punto (**.**) per separare le varie parti dello spazio dei nomi, il nome della classe deve essere delimitato da parentesi quadre (**[]**) o virgolette (**""**). *nome_metodo* deve essere un valore valido [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] identificatore e deve esistere come metodo statico nella classe specificata.  
  
> [!NOTE]  
>  Per impostazione predefinita, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non può eseguire il codice CLR. È possibile creare, modificare e rilasciare gli oggetti di database che fanno riferimento a moduli CLR; Tuttavia, non è possibile eseguire questi riferimenti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] finché non si abilita il [opzione clr enabled](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md). Per abilitare l'opzione, usare [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
> [!NOTE]  
>  Questa opzione non è disponibile in un database indipendente.  
  
 *\<*table_type_definition*>***(** { \<column_definition > \<column_constraint > | \<computed_column_definition >} [ \<table_constraint >] [ **,**... *n* ]**)**  
 Definisce il tipo di dati della tabella per una funzione [!INCLUDE[tsql](../../includes/tsql-md.md)]. La dichiarazione di tabella include definizioni di colonna, nonché vincoli di colonna o tabella.  
  
\<clr_table_type_definition > **(** { *column_name**data_type* } [ **,**...  *n*  ] **)** **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] ([anteprima in alcune aree](http://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)).  
  
 Definisce i tipi di dati della tabella per una funzione CLR. La dichiarazione di tabella include solo nomi di colonna e tipi di dati.  
  
 NULL | NON È NULL  
 Supportato solo per le funzioni compilate in modo nativo e scalari definite dall'utente. Per ulteriori informazioni, vedere [funzioni scalari definite dall'utente per OLTP In memoria](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md).  
  
 NATIVE_COMPILATION  
 Indica se una funzione definita dall'utente è compilata in modo nativo. Questo argomento è obbligatorio per le funzioni compilate in modo nativo e scalari definite dall'utente.  
  
 L'argomento with NATIVE_COMPILATION è obbligatorio quando si modifica la funzione e può essere utilizzato solo, se la funzione è stata creata con l'argomento with NATIVE_COMPILATION.  
  
 BEGIN ATOMIC CON  
 Supportata solo per compilate in modo nativo, le funzioni scalari definite dall'utente ed sono necessaria. Per altre informazioni, vedere [Atomic Blocks](../../relational-databases/in-memory-oltp/atomic-blocks-in-native-procedures.md).  
  
 SCHEMABINDING  
 L'argomento SCHEMABINDING è obbligatorio per le funzioni compilate in modo nativo e scalari definite dall'utente.  
  
 **\<function_option >:: = e \<clr_function_option >:: =**  
  
 Specifica che la funzione avrà una o più opzioni seguenti.  
  
 ENCRYPTION  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Indica che nel [!INCLUDE[ssDE](../../includes/ssde-md.md)] vengono crittografate le colonne della vista del catalogo contenenti il testo dell'istruzione ALTER FUNCTION. Tramite il parametro ENCRYPTION è possibile evitare la pubblicazione della funzione come parte della replica di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Non è possibile specificare l'opzione ENCRYPTION per le funzioni CLR.  
  
 SCHEMABINDING  
 Specifica che la funzione è associata agli oggetti di database a cui fa riferimento. Questa condizione impedisce la modifica della funzione se altri oggetti associati allo schema vi fanno riferimento.  
  
 L'associazione della funzione agli oggetti cui fa riferimento viene rimossa solo quando viene eseguita una delle azioni seguenti:  
  
-   La funzione viene eliminata.  
  
-   La funzione viene modificata tramite l'istruzione ALTER senza specificare l'opzione SCHEMABINDING.  
  
Per un elenco di condizioni che devono essere soddisfatte prima di una funzione può essere associata a schema, vedere [CREATE FUNCTION &#40; Transact-SQL &#41; ](../../t-sql/statements/create-function-transact-sql.md).  
  
 RETURNS NULL ON NULL INPUT | CALLED ON NULL INPUT  
 Specifica il **OnNULLCall** attributo di una funzione a valori scalari. Se omesso, viene utilizzata l'opzione CALLED ON NULL INPUT per impostazione predefinita. Ciò significa che viene eseguito il corpo della funzione anche se come argomento viene passato NULL.  
  
 Se in una funzione CLR si specifica l'opzione RETURNS NULL ON NULL INPUT, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce NULL se uno qualsiasi degli argomenti ricevuti è NULL senza effettivamente richiamare il corpo della funzione. Se il metodo specificato nel \<method_specifier > esiste già un attributo personalizzato che indica RETURNS NULL ON NULL INPUT, ma l'istruzione ALTER FUNCTION indica CALLED ON NULL INPUT, l'istruzione ALTER FUNCTION ha la precedenza. Il **OnNULLCall** attributo non può essere specificato per le funzioni con valori di tabella CLR.  
  
 Clausola EXECUTE AS  
 Specifica il contesto di sicurezza nel quale viene eseguita la funzione definita dall'utente. Sarà pertanto possibile controllare l'account utente usato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per convalidare le autorizzazioni per qualsiasi oggetto di database a cui la funzione fa riferimento.  
  
> [!NOTE]  
>  Non è possibile specificare la clausola EXECUTE AS per le funzioni inline definite dall'utente.  
  
 Per altre informazioni, vedere [Clausola EXECUTE AS &#40;Transact-SQL&#41;](../../t-sql/statements/execute-as-clause-transact-sql.md).  
  
**\<column_definition >:: =**
  
 Definisce il tipo di dati della tabella. La dichiarazione di tabella include definizioni di colonna e vincoli. Per le funzioni CLR solo *column_name* e *data_type* può essere specificato.  
  
 *column_name*  
 Nome di una colonna della tabella. I nomi delle colonne devono essere conformi alle regole per gli identificatori e devono essere univoci nella tabella. *column_name* può contenere da 1 a 128 caratteri.  
  
 *data_type*  
 Specifica il tipo di dati della colonna. Per [!INCLUDE[tsql](../../includes/tsql-md.md)] sono consentite funzioni, tutti i tipi di dati, inclusi i tipi CLR definiti dall'utente, ad eccezione di **timestamp**. Per le funzioni CLR sono consentiti tutti i tipi di dati, inclusi i tipi CLR definiti dall'utente, eccetto **testo**, **ntext**, **immagine**, **char**, **varchar**, **varchar (max)**, e **timestamp**. Il tipo non scalare **cursore** non può essere specificato come un tipo di dati di colonna nelle [!INCLUDE[tsql](../../includes/tsql-md.md)] o funzioni CLR.  
  
 PREDEFINITO *constant_expression*  
 Specifica il valore assegnato alla colonna quando non viene specificato un valore in modo esplicito durante un inserimento. *constant_expression* è una costante, NULL o un valore di funzione di sistema. Le definizioni dell'opzione DEFAULT possono essere applicate a qualsiasi colonna eccetto quelle che includono la proprietà IDENTITY. Non è possibile specificare l'opzione DEFAULT per le funzioni CLR con valori di tabella.  
  
 COLLATE *collation_name*  
 Specifica le regole di confronto per la colonna. Se viene omesso, alla colonna vengono assegnate le regole di confronto predefinite del database. È possibile usare nomi di regole di confronto di Windows o SQL. Per un elenco di ulteriori informazioni, vedere [windows_collation_name &#40; Transact-SQL &#41; ](../../t-sql/statements/windows-collation-name-transact-sql.md) e [SQL nome regole di confronto del Server &#40; Transact-SQL &#41; ](../../t-sql/statements/sql-server-collation-name-transact-sql.md).  
  
 La clausola COLLATE consente di modificare le regole di confronto solo delle colonne di **char**, **varchar**, **nchar**, e **nvarchar** tipi di dati.  
  
 Non è possibile specificare l'opzione COLLATE per le funzioni CLR con valori di tabella.  
  
 ROWGUIDCOL  
 Specifica che la nuova colonna funge da identificatore di riga univoco globale. Un solo **uniqueidentifier** colonna per ogni tabella può essere definita come colonna ROWGUIDCOL. La proprietà ROWGUIDCOL può essere assegnata solo a un **uniqueidentifier** colonna.  
  
 La proprietà ROWGUIDCOL non impone l'univocità dei valori archiviati nella colonna e non genera automaticamente valori per le nuove righe inserite nella tabella. Per generare valori univoci per ogni colonna, utilizzare la funzione NEWID nelle istruzioni INSERT. È possibile specificare un valore predefinito. Non è tuttavia possibile specificare l'opzione NEWID come valore predefinito.  
  
 IDENTITY  
 Indica che la nuova colonna è una colonna Identity. Quando si aggiunge una nuova riga alla tabella, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assegna alla colonna un valore univoco e incrementale. Le colonne Identity vengono comunemente utilizzate in combinazione con vincoli PRIMARY KEY e svolgono la funzione di identificatore di riga univoco per la tabella. La proprietà IDENTITY può essere assegnata a **tinyint**, **smallint**, **int**, **bigint**, **decimal(p,0)**, o **numeric(p,0)** colonne. Ogni tabella può includere una sola colonna Identity. Non è consentito associare valori predefiniti e vincoli DEFAULT alle colonne Identity. È necessario specificare sia il *valore di inizializzazione* e *incremento* o nessuno. In questo secondo caso, il valore predefinito è (1,1).  
  
 Non è possibile specificare l'opzione IDENTITY per le funzioni CLR con valori di tabella.  
  
 *valore di inizializzazione*  
 Valore intero da assegnare alla prima riga della tabella.  
  
 *incremento*  
 Valore intero per aggiungere il *valore di inizializzazione* valore per le righe successive nella tabella.  
  
**\<column_constraint >:: = e \< table_constraint >:: =**
  
 Definisce il vincolo per una colonna o tabella specificata. Per le funzioni CLR l'unico tipo di vincolo consentito è NULL. I vincoli denominati non sono consentiti.  
  
 NULL | NOT NULL  
 Determina se i valori Null sono supportati nella colonna. L'opzione NULL non è esattamente un vincolo, ma può essere specificata allo stesso modo di NOT NULL. Non è possibile specificare l'opzione NOT NULL per le funzioni CLR con valori di tabella.  
  
 PRIMARY KEY  
 Vincolo che impone l'integrità di entità per una colonna specificata tramite un indice univoco. Nelle funzioni definite dall'utente con valori di tabella, il vincolo PRIMARY KEY può essere creato solo su una colonna per tabella. Non è possibile specificare il vincolo PRIMARY KEY per le funzioni CLR con valori di tabella.  
  
 UNIQUE  
 Vincolo che impone l'integrità di entità per una o più colonne specificate tramite un indice univoco. Una tabella può includere più vincoli UNIQUE. Non è possibile specificare il vincolo UNIQUE per le funzioni CLR con valori di tabella.  
  
 CLUSTERED | NONCLUSTERED  
 Definisce la creazione di un indice cluster o non cluster per il vincolo PRIMARY KEY o UNIQUE. I vincoli PRIMARY KEY utilizzano l'opzione CLUSTERED, mentre i vincoli UNIQUE utilizzano l'opzione NONCLUSTERED.  
  
 L'opzione CLUSTERED può essere specificata solo per un vincolo. Se per un vincolo UNIQUE si specifica CLUSTERED e viene specificato anche un vincolo PRIMARY KEY, quest'ultimo utilizza l'opzione NONCLUSTERED.  
  
 Non è possibile specificare le opzioni CLUSTERED e NON CLUSTERED per le funzioni CLR con valori di tabella.  
  
 CHECK  
 Vincolo che impone l'integrità di dominio tramite la limitazione dei valori che è possibile inserire in una o più colonne. Non è possibile specificare i vincoli CHECK per le funzioni CLR con valori di tabella.  
  
 *Logical_Expression*  
 Espressione logica che restituisce TRUE o FALSE.  
  
 **\<computed_column_definition >:: =**  
  
 Specifica una colonna calcolata. Per ulteriori informazioni sulle colonne calcolate, vedere [CREATE TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-table-transact-sql.md).  
  
 *column_name*  
 Nome della colonna calcolata.  
  
 *computed_column_expression*  
 Espressione che definisce il valore di una colonna calcolata.  
  
 **\<index_option >:: =**  
  
 Specifica le opzioni per l'indice PRIMARY KEY o UNIQUE. Per ulteriori informazioni sulle opzioni di indice, vedere [CREATE INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/create-index-transact-sql.md).  
  
 PAD_INDEX = { ON | OFF }  
 Specifica il riempimento dell'indice. Il valore predefinito è OFF.  
  
 Fattore di riempimento = *fattore di riempimento*  
 Specifica una percentuale indicante il livello di riempimento del livello foglia di ogni pagina di indice applicato dal [!INCLUDE[ssDE](../../includes/ssde-md.md)] durante la creazione o la modifica dell'indice. *fattore di riempimento* deve essere un valore intero compreso tra 1 e 100. Il valore predefinito è 0.  
  
 IGNORE_DUP_KEY = { ON | OFF }  
 Specifica l'errore restituito quando un'operazione di inserimento tenta di inserire valori di chiave duplicati in un indice univoco. L'opzione IGNORE_DUP_KEY viene applicata solo alle operazioni di inserimento eseguite dopo la creazione o la ricompilazione dell'indice. Il valore predefinito è OFF.  
  
 STATISTICS_NORECOMPUTE = { ON | OFF }  
 Specifica se le statistiche di distribuzione vengono ricalcolate. Il valore predefinito è OFF.  
  
 ALLOW_ROW_LOCKS = { ON | OFF }  
 Specifica se sono consentiti blocchi di riga. Il valore predefinito è ON.  
  
 ALLOW_PAGE_LOCKS = { ON | OFF }  
 Specifica se sono consentiti blocchi a livello di pagina. Il valore predefinito è ON.  
  
## <a name="remarks"></a>Osservazioni  
 L'istruzione ALTER FUNCTION non può essere usata per trasformare una funzione a valori scalari in una funzione con valori di tabella e viceversa, né per convertire una funzione inline in una funzione a più istruzioni e viceversa. Non può inoltre essere usata per convertire una funzione [!INCLUDE[tsql](../../includes/tsql-md.md)] in una funzione CLR e viceversa.  
  
 Le seguenti istruzioni di Service Broker non possono essere inclusa nella definizione di un [!INCLUDE[tsql](../../includes/tsql-md.md)] funzione definita dall'utente:  
  
-   BEGIN DIALOG CONVERSATION  
-   END CONVERSATION  
-   GET CONVERSATION GROUP  
-   MOVE CONVERSATION  
-   RECEIVE  
-   SEND  
  
## <a name="permissions"></a>Permissions  
 È necessario disporre dell'autorizzazione ALTER per la funzione o lo schema. Se per la funzione viene specificato un tipo definito dall'utente, è necessario disporre dell'autorizzazione EXECUTE per tale tipo.  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-function-transact-sql.md)   
 [DROP FUNCTION &#40; Transact-SQL &#41;](../../t-sql/statements/drop-function-transact-sql.md)   
 [Apportare modifiche allo schema nei database di pubblicazione](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
