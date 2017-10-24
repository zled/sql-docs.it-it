---
title: DICHIARARE @local_variable (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DECLARE
- DECLARE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- table-valued parameters
- variables [SQL Server], declaring
- DECLARE statement
- declaring variables
ms.assetid: d1635ebb-f751-4de1-8bbc-cae161f90821
caps.latest.revision: 76
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 70decceb0fb5bc34f5ac7a32c64ca80cb0977de2
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="declare-localvariable-transact-sql"></a>DICHIARARE @local_variable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Le variabili vengono dichiarate nel corpo di un batch o di una routine tramite l'istruzione DECLARE e i relativi valori vengono assegnati tramite un'istruzione SET o SELECT. È possibile dichiarare variabili di cursore con questa istruzione e utilizzarle insieme ad altre istruzioni correlate ai cursori. Dopo la dichiarazione, tutte le variabili vengono inizializzate con valore NULL, a meno che non venga fornito un valore nella dichiarazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
DECLARE   
{   
    { @local_variable [AS] data_type  | [ = value ] }  
  | { @cursor_variable_name CURSOR }  
} [,...n]   
| { @table_variable_name [AS] <table_type_definition> }   
  
<table_type_definition> ::=   
     TABLE ( { <column_definition> | <table_constraint> } [ ,... ] )   
  
<column_definition> ::=   
     column_name { scalar_data_type | AS computed_column_expression }  
     [ COLLATE collation_name ]   
     [ [ DEFAULT constant_expression ] | IDENTITY [ (seed ,increment ) ] ]   
     [ ROWGUIDCOL ]   
     [ <column_constraint> ]   
  
<column_constraint> ::=   
     { [ NULL | NOT NULL ]   
     | [ PRIMARY KEY | UNIQUE ]   
     | CHECK ( logical_expression )   
     | WITH ( <index_option > )  
     }   
  
<table_constraint> ::=   
     { { PRIMARY KEY | UNIQUE } ( column_name [ ,... ] )   
     | CHECK ( search_condition )   
     }   
  
<index_option> ::=  
See CREATE TABLE for index option syntax.  
  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DECLARE   
{{ @local_variable [AS] data_type } [ =value [ COLLATE <collation_name> ] ] } [,...n]  
  
```  
  
## <a name="arguments"></a>Argomenti  
@*local_variable*  
 Nome di una variabile. I nomi di variabile devono iniziare con un simbolo di chiocciola (@). Nomi delle variabili locali devono essere conformi alle regole per [identificatori](../../relational-databases/databases/database-identifiers.md).  
  
*data_type*  
 Qualsiasi tipo di tabella di sistema, CLR (Common Language Runtime) definito dall'utente o tipo di dati alias. Non può essere una variabile di **testo**, **ntext**, o **immagine** tipo di dati.  
  
 Per ulteriori informazioni sui tipi di dati di sistema, vedere [tipi di dati &#40; Transact-SQL &#41; ](../../t-sql/data-types/data-types-transact-sql.md). Per ulteriori informazioni sui tipi CLR definiti dall'utente o tipi di dati alias, vedere [CREATE TYPE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-type-transact-sql.md).  
  
 =*valore*  
 Assegna un valore alla variabile inline. Il valore può essere una costante o un'espressione, ma deve corrispondere al tipo di dichiarazione di variabile o deve supportare la conversione implicita in tale tipo. Per altre informazioni, vedere [Espressioni &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md).  
  
@*cursor_variable_name*  
 Nome di una variabile di cursore. I nomi delle variabili di cursore devono iniziare con un simbolo di chiocciola (@) e devono essere conformi alle regole per gli identificatori.  
  
CURSOR  
 Specifica che si tratta di una variabile di cursore locale.  
  
@*table_variable_name*  
 È il nome di una variabile di tipo **tabella**. I nomi delle variabili devono iniziare con un simbolo di chiocciola (@) e devono essere conformi alle regole per gli identificatori.  
  
<table_type_definition>  
Definisce il **tabella** tipo di dati. La dichiarazione di tabella include definizioni di colonna, nomi, tipi di dati e vincoli. Gli unici tipi di vincolo consentiti sono PRIMARY KEY, UNIQUE, NULL e CHECK. Non è possibile utilizzare un tipo di dati alias come tipo di dati scalare di una colonna se al tipo è associata una regola o una definizione di valore predefinito.
  
\<table_type_definiton > è un subset di informazioni utilizzate per definire una tabella nell'istruzione CREATE TABLE. Queste informazioni includono elementi e definizioni essenziali. Per altre informazioni, vedere [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md).  
  
 *n*  
 Segnaposto che indica che è possibile specificare più variabili e assegnare i relativi valori. Quando si dichiara **tabella** variabili, il **tabella** variabile deve essere l'unica variabile dichiarata nell'istruzione DECLARE.  
  
 *column_name*  
 Nome della colonna della tabella.  
  
 *scalar_data_type*  
 Specifica che il tipo di dati della colonna è scalare.  
  
 *computed_column_expression*  
 Espressione che determina il valore di una colonna calcolata. Il valore viene calcolato in base a un'espressione che utilizza altre colonne della stessa tabella. Ad esempio, una colonna calcolata può avere la definizione **costo** AS **prezzo \* qty**. L'espressione può essere un nome di colonna non calcolata, una costante, una funzione predefinita, una variabile o una qualsiasi combinazione di questi elementi uniti da uno o più operatori. Non può invece essere una sottoquery o una funzione definita dall'utente. Non può inoltre fare riferimento a un tipo CLR definito dall'utente.  
  
 [COLLATE *collation_name*]  
 Specifica le regole di confronto per la colonna. *collation_name* può essere un nome di regole di confronto Windows o un nome di regole di confronto SQL ed è applicabile solo alle colonne di **char**, **varchar**, **testo** , **nchar**, **nvarchar**, e **ntext** tipi di dati. Se viene omesso, alla colonna vengono assegnate le regole di confronto del tipo di dati definito dall'utente, se il tipo di dati della colonna è definito dall'utente, oppure le regole di confronto del database corrente.  
  
 Per ulteriori informazioni sui nomi delle regole di confronto Windows e SQL, vedere [COLLATE &#40; Transact-SQL &#41; ](~/t-sql/statements/collations.md).  
  
 DEFAULT  
 Specifica il valore assegnato alla colonna quando non viene specificato un valore in modo esplicito durante un inserimento. Le definizioni DEFAULT possono essere applicate a tutte le colonne ad eccezione di quelli definiti come **timestamp** o quelli con la proprietà IDENTITY. Le definizioni DEFAULT vengono rimosse quando la tabella viene eliminata. Come valore predefinito è possibile utilizzare solo una costante, ad esempio una stringa di caratteri, una funzione di sistema, ad esempio SYSTEM_USER(), oppure NULL. Per garantire la compatibilità con le versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è possibile assegnare un nome di vincolo a una definizione DEFAULT.  
  
 *constant_expression*  
 Costante, valore NULL o funzione di sistema utilizzata come valore predefinito della colonna.  
  
 IDENTITY  
 Indica che la nuova colonna è una colonna Identity. Quando si aggiunge una nuova riga alla tabella, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assegna un valore univoco e incrementale alla colonna. Le colonne Identity vengono comunemente utilizzate in combinazione con vincoli PRIMARY KEY per fungere da identificatore di riga univoco per la tabella. La proprietà IDENTITY può essere assegnata a **tinyint**, **smallint**, **int**, **decimal(p,0)**, o **numeric(p,0)** colonne. Ogni tabella può includere una sola colonna Identity. Non è consentito associare valori predefiniti e vincoli DEFAULT alle colonne Identity. È necessario specificare sia il valore di inizializzazione che l'incremento oppure è possibile omettere entrambi questi valori. In questo secondo caso, il valore predefinito è (1,1).  
  
 *valore di inizializzazione*  
 Valore di inizializzazione utilizzato per la prima riga caricata nella tabella.  
  
 *incremento*  
 Valore incrementale aggiunto al valore Identity della riga caricata in precedenza.  
  
 ROWGUIDCOL  
 Specifica che la nuova colonna funge da identificatore di riga univoco globale. Un solo **uniqueidentifier** colonna per ogni tabella può essere definita come colonna ROWGUIDCOL. La proprietà ROWGUIDCOL può essere assegnata solo a un **uniqueidentifier** colonna.  
  
 NULL | NOT NULL  
 Indica se il valore Null è ammesso nella variabile. Il valore predefinito è NULL.  
  
 PRIMARY KEY  
 Vincolo che impone l'integrità di entità per una o più colonne specificate tramite un indice univoco. È possibile creare un solo vincolo PRIMARY KEY per ogni tabella.  
  
 UNIQUE  
 Vincolo che impone l'integrità di entità per una o più colonne specificate tramite un indice univoco. Una tabella può includere più vincoli UNIQUE.  
  
 CHECK  
 Vincolo che impone l'integrità di dominio tramite la limitazione dei valori che è possibile inserire in una o più colonne.  
  
 *Logical_Expression*  
 Espressione logica che restituisce TRUE o FALSE.  
  
## <a name="remarks"></a>Osservazioni  
 Le variabili spesso vengono utilizzate in un batch o una procedura come contatori per istruzioni WHILE e LOOP oppure per un blocco IF...ELSE.  
  
 Le variabili possono essere utilizzate solo nelle espressioni e non in sostituzione di parole chiave o nomi di oggetto. Per creare istruzioni SQL dinamiche, utilizzare EXECUTE.  
  
 L'ambito di una variabile locale è il batch in cui viene dichiarata.  
 
 Una variabile di tabella non è necessariamente residenti in memoria. Eccessivo della memoria, le pagine appartengono a una variabile di tabella possono essere inserite in tempdb.
  
 Nelle seguenti istruzioni è possibile fare riferimento come origine a una variabile di cursore a cui è assegnato un cursore:  
  
-   Istruzione CLOSE.  
  
-   Istruzione DEALLOCATE.  
  
-   Istruzione FETCH.  
  
-   Istruzione OPEN.  
  
-   Istruzione DELETE o UPDATE posizionata.  
  
-   Istruzione SET CURSOR con variabile (nella parte destra).  
  
 Se la variabile di cursore a cui viene fatto riferimento in queste istruzioni esiste ma non le è stato assegnato un cursore, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene generato un errore. Se la variabile di cursore a cui viene fatto riferimento non esiste, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene restituito lo stesso errore generato per le variabili non dichiarate di altro tipo.  
  
 Una variabile di cursore:  
  
-   Può essere la destinazione di un tipo di cursore o di un'altra variabile di cursore. Per ulteriori informazioni, vedere [impostare @local_variable &#40; Transact-SQL &#41; ](../../t-sql/language-elements/set-local-variable-transact-sql.md).  
  
-   Può essere specificata come destinazione di un parametro di cursore di output in un'istruzione EXECUTE se alla variabile di cursore non è attualmente assegnato un cursore.  
  
-   Deve essere considerata come puntatore al cursore.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-declare"></a>A. Utilizzo di DECLARE  
 Nell'esempio seguente viene utilizzata una variabile locale denominata `@find` per recuperare le informazioni sul contatto per tutti i cognomi che iniziano con `Man`.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @find varchar(30);   
/* Also allowed:   
DECLARE @find varchar(30) = 'Man%';   
*/  
SET @find = 'Man%';   
SELECT p.LastName, p.FirstName, ph.PhoneNumber  
FROM Person.Person AS p   
JOIN Person.PersonPhone AS ph ON p.BusinessEntityID = ph.BusinessEntityID  
WHERE LastName LIKE @find;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
LastName            FirstName               Phone
------------------- ----------------------- -------------------------
Manchepalli         Ajay                    1 (11) 500 555-0174
Manek               Parul                   1 (11) 500 555-0146
Manzanares          Tomas                   1 (11) 500 555-0178
  
(3 row(s) affected)
```  
  
### <a name="b-using-declare-with-two-variables"></a>B. Utilizzo di DECLARE con due variabili  
 Nell'esempio seguente vengono recuperati i nomi dei rappresentanti di [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] che svolgono la propria attività nel Nord America e per cui l'ammontare delle vendite annue è pari almeno a $ 2.000.000.  
  
```  
USE AdventureWorks2012;  
GO  
SET NOCOUNT ON;  
GO  
DECLARE @Group nvarchar(50), @Sales money;  
SET @Group = N'North America';  
SET @Sales = 2000000;  
SET NOCOUNT OFF;  
SELECT FirstName, LastName, SalesYTD  
FROM Sales.vSalesPerson  
WHERE TerritoryGroup = @Group and SalesYTD >= @Sales;  
```  
  
### <a name="c-declaring-a-variable-of-type-table"></a>C. Dichiarazione di una variabile di tipo table  
 Nell'esempio seguente viene creata una variabile di tipo `table` in cui vengono archiviati i valori specificati nella clausola OUTPUT dell'istruzione UPDATE. Questa variabile è seguita da due istruzioni `SELECT` che restituiscono i valori in `@MyTableVar` e i risultati dell'operazione di aggiornamento nella tabella `Employee`. Si noti che i risultati nel `INSERTED.ModifiedDate` colonna sono diversi dai valori di `ModifiedDate` colonna il `Employee` tabella. Questo perché nella tabella `AFTER UPDATE` è stato definito il trigger `ModifiedDate`, che aggiorna il valore di `Employee` in base alla data corrente. Le colonne restituite da `OUTPUT`, tuttavia, riflettono i dati prima dell'attivazione dei trigger. Per ulteriori informazioni, vedere [clausola OUTPUT &#40; Transact-SQL &#41; ](../../t-sql/queries/output-clause-transact-sql.md).  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @MyTableVar table(  
    EmpID int NOT NULL,  
    OldVacationHours int,  
    NewVacationHours int,  
    ModifiedDate datetime);  
UPDATE TOP (10) HumanResources.Employee  
SET VacationHours = VacationHours * 1.25   
OUTPUT INSERTED.BusinessEntityID,  
       DELETED.VacationHours,  
       INSERTED.VacationHours,  
       INSERTED.ModifiedDate  
INTO @MyTableVar;  
--Display the result set of the table variable.  
SELECT EmpID, OldVacationHours, NewVacationHours, ModifiedDate  
FROM @MyTableVar;  
GO  
--Display the result set of the table.  
--Note that ModifiedDate reflects the value generated by an  
--AFTER UPDATE trigger.  
SELECT TOP (10) BusinessEntityID, VacationHours, ModifiedDate  
FROM HumanResources.Employee;  
GO  
```  
  
### <a name="d-declaring-a-variable-of-user-defined-table-type"></a>D. Dichiarazione di una variabile di tipo di tabella definito dall'utente  
 Nell'esempio seguente viene creato un parametro con valori di tabella o una variabile di tabella denominata `@LocationTVP`. A tale scopo è necessario un tipo di tabella definito dall'utente corrispondente denominato `LocationTableType`. Per ulteriori informazioni su come creare un tipo di tabella definito dall'utente, vedere [CREATE TYPE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-type-transact-sql.md). Per ulteriori informazioni sui parametri con valori di tabella, vedere [utilizzare parametri &#40; motore di Database &#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md).  
  
```  
DECLARE @LocationTVP   
AS LocationTableType;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-using-declare"></a>E. Utilizzo di DECLARE  
 Nell'esempio seguente viene utilizzata una variabile locale denominata `@find` per recuperare le informazioni sul contatto per tutti i cognomi che iniziano con `Walt`.  
  
```  
-- Uses AdventureWorks  
  
DECLARE @find varchar(30);  
/* Also allowed:   
DECLARE @find varchar(30) = 'Man%';  
*/  
SET @find = 'Walt%';  
  
SELECT LastName, FirstName, Phone  
FROM DimEmployee   
WHERE LastName LIKE @find;  
```  
  
### <a name="f-using-declare-with-two-variables"></a>F. Utilizzo di DECLARE con due variabili  
 L'esempio seguente recupera le variabili viene utilizzato per specificare i nomi e cognomi dei dipendenti nel `DimEmployee` tabella.  
  
```  
-- Uses AdventureWorks  
  
DECLARE @lastName varchar(30), @firstName varchar(30);  
  
SET @lastName = 'Walt%';  
SET @firstName = 'Bryan';  
  
SELECT LastName, FirstName, Phone  
FROM DimEmployee   
WHERE LastName LIKE @lastName AND FirstName LIKE @firstName;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [Funzioni predefinite &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [tabella &#40; Transact-SQL &#41;](../../t-sql/data-types/table-transact-sql.md)   
 [Confrontare dati XML tipizzati con dati XML non tipizzati](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)  
  
  





