---
title: tabella (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- table data type [SQL Server]
- table variables [SQL Server]
ms.assetid: 1ef0b60e-a64c-4e97-847b-67930e3973ef
caps.latest.revision: 48
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b22ecfa04f949af77df974abc3359b7bc5144a82
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="table-transact-sql"></a>table (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Tipo di dati speciale che può essere utilizzato per archiviare un set di risultati per l'elaborazione in un secondo momento. **tabella** viene utilizzato principalmente per l'archiviazione temporanea di un set di righe restituite come set di risultati di una funzione con valori di tabella. Funzioni e variabili possono essere dichiarate come tipo di **tabella**. **tabella** variabili possono essere utilizzate in funzioni, stored procedure e batch. Per dichiarare le variabili di tipo **tabella**, utilizzare [DECLARE @local_variable ](../../t-sql/language-elements/declare-local-variable-transact-sql.md).
  

**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] alla [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
table_type_definition ::=   
    TABLE ( { <column_definition> | <table_constraint> } [ ,...n ] )   
  
<column_definition> ::=   
    column_name scalar_data_type   
    [ COLLATE <collation_definition> ]   
    [ [ DEFAULT constant_expression ] | IDENTITY [ ( seed , increment ) ] ]   
    [ ROWGUIDCOL ]   
    [ column_constraint ] [ ...n ]   
  
 <column_constraint> ::=   
    { [ NULL | NOT NULL ]   
    | [ PRIMARY KEY | UNIQUE ]   
    | CHECK ( logical_expression )   
    }   
  
<table_constraint> ::=   
     { { PRIMARY KEY | UNIQUE } ( column_name [ ,...n ] )  
     | CHECK ( logical_expression )   
     }   
```  
  
## <a name="arguments"></a>Argomenti  
*table_type_definition*  
Stesso subset di informazioni utilizzate per definire una tabella nell'istruzione CREATE TABLE. La dichiarazione di tabella include definizioni di colonna, nomi, tipi di dati e vincoli. Gli unici tipi di vincoli consentiti sono PRIMARY KEY, UNIQUE KEY e NULL.  
Per ulteriori informazioni sulla sintassi, vedere [CREATE TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-table-transact-sql.md), [CREATE FUNCTION &#40; Transact-SQL &#41; ](../../t-sql/statements/create-function-transact-sql.md), e [DECLARE @local_variable &#40; Transact-SQL &#41; ](../../t-sql/language-elements/declare-local-variable-transact-sql.md).
  
*collation_definition*  
Regole di confronto della colonna che è costituita da un [!INCLUDE[msCoName](../../includes/msconame-md.md)] impostazioni locali di Windows e uno stile di confronto, impostazioni locali di Windows e la notazione binaria o una [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] delle regole di confronto. Se *collation_definition* non viene specificato, la colonna eredita le regole di confronto del database corrente. Se invece viene specificata come tipo CLR (Common Language Runtime) definito dall'utente, la colonna eredita le regole di confronto del tipo definito dall'utente.
  
## <a name="remarks"></a>Osservazioni  
**tabella** fare riferimento alle variabili in base al nome nella clausola FROM di un batch, come illustrato nell'esempio seguente:
  
```sql
SELECT Employee_ID, Department_ID FROM @MyTableVar;  
```  
  
All'esterno di una clausola FROM, **tabella** devono fare riferimento alle variabili utilizzando un alias, come illustrato nell'esempio seguente:
  
```sql
SELECT EmployeeID, DepartmentID   
FROM @MyTableVar m  
JOIN Employee on (m.EmployeeID =Employee.EmployeeID AND  
   m.DepartmentID = Employee.DepartmentID);  
```  
  
**tabella** variabili offrono i vantaggi seguenti per le query su scala ridotta contenenti piani di query che non cambiano e quando i problemi di ricompilazione sono dominanti:
-   Oggetto **tabella** variabile si comporta come una variabile locale. Queste variabili hanno un ambito ben definito, corrispondente alla funzione, alla stored procedure o al batch in cui sono dichiarate.  
     All'interno dell'ambito, un **tabella** variabile può essere utilizzata come una normale tabella. in tutti i casi in cui è possibile utilizzare una tabella o espressione di tabella in istruzioni SELECT, INSERT, UPDATE e DELETE. Tuttavia, **tabella** non può essere utilizzato nell'istruzione seguente:  
  
```sql
SELECT select_list INTO table_variable;
```
  
**tabella** variabili vengono pulite automaticamente alla fine della funzione, stored procedure o batch in cui sono definiti.
  
-   **tabella** le variabili utilizzate nelle stored procedure causano un numero di ricompilazioni delle stored procedure rispetto a quando le tabelle temporanee vengono utilizzate quando vi sono scelte basate sui costi che influiscono sulle prestazioni.  
-   Le transazioni che implica **tabella** variabili ultimo solo per la durata di un aggiornamento sul **tabella** variabile. Pertanto, **tabella** variabili richiedono meno risorse di registrazione e il blocco.  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni
**Tabella** variabili non dispone di statistiche di distribuzione, non attiva ricompilazioni. Pertanto, in molti casi, l'utilità di ottimizzazione compila un piano di query supponendo che la variabile di tabella non contenga righe. Per questo motivo, è necessario prestare attenzione in caso di utilizzo di una variabile di tabella se si prevede un numero elevato di righe (maggiore di 100). In tal caso, le tabelle temporanee potrebbero rappresentare una soluzione migliore. In alternativa, per le query che uniscono in join la variabile di tabella con altre tabelle, utilizzare l'hint RECOMPILE, che impedirà all'ottimizzatore di utilizzare la cardinalità corretta per la variabile di tabella.
  
**tabella** variabili non sono supportate nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] modello di ragionamento basato sui costi dell'utilità di ottimizzazione. È pertanto consigliabile non utilizzarle quando sono necessarie scelte basate sui costi per ottenere un piano di query efficiente. È preferibile utilizzare le tabelle temporanee quando sono necessarie scelte basate sui costi, ad esempio query con join, decisioni di parallelismo e scelte di selezione degli indici.
  
Query che modificano **tabella** variabili non generano piani di esecuzione di query parallele. Può influire sulle prestazioni quando grandi **tabella** , variabili o **tabella** le variabili di query complesse, vengono modificati. In questi casi, valutare l'utilizzo di tabelle temporanee in alternativa. Per altre informazioni, vedere [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md). Le query che leggono **tabella** variabili senza modificarle possono ancora essere parallelizzate.
  
È possibile creare indici in modo esplicito su **tabella** variabili e le statistiche non vengono mantenuti in **tabella** variabili. In alcuni casi, è possibile ottenere un miglioramento delle prestazioni utilizzando tabelle temporanee, che supportano indici e statistiche. Per ulteriori informazioni sulle tabelle temporanee, vedere [CREATE TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-table-transact-sql.md).
  
Vincoli CHECK, i valori predefiniti e le colonne calcolate nel **tabella** dichiarazione di tipo non è possibile chiamare funzioni definite dall'utente.
  
Operazione di assegnazione tra **tabella** variabili non è supportata.
  
Poiché **tabella** variabili hanno un ambito limitato e non fanno parte del database persistente, non sono influenzati dal rollback di transazioni.
  
Le variabili di tabella non possono essere modificate dopo la creazione.
  
## <a name="examples"></a>Esempi  
  
### <a name="a-declaring-a-variable-of-type-table"></a>A. Dichiarazione di una variabile di tipo table  
Nell'esempio seguente viene creata una variabile di tipo `table` in cui vengono archiviati i valori specificati nella clausola OUTPUT dell'istruzione UPDATE. Questa variabile è seguita da due istruzioni `SELECT` che restituiscono i valori in `@MyTableVar` e i risultati dell'operazione di aggiornamento nella tabella `Employee`. Si noti che i risultati nel `INSERTED.ModifiedDate` colonna sono diversi dai valori di `ModifiedDate` colonna il `Employee` tabella. Questo perché nella tabella `AFTER UPDATE` è stato definito il trigger `ModifiedDate`, che aggiorna il valore di `Employee` in base alla data corrente. Le colonne restituite da `OUTPUT`, tuttavia, riflettono i dati prima dell'attivazione dei trigger. Per ulteriori informazioni, vedere [clausola OUTPUT &#40; Transact-SQL &#41; ](../../t-sql/queries/output-clause-transact-sql.md).
  
```sql
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
  
### <a name="b-creating-an-inline-table-valued-function"></a>B. Creazione di una funzione inline con valori di tabella  
Nell'esempio seguente viene restituita una funzione inline con valori di tabella. Vengono restituite tre colonne `ProductID`, `Name` e l'aggregazione dei totali year-to-date per negozio come `YTD Total` per ogni prodotto venduto al Negozio.
  
```sql
USE AdventureWorks2012;  
GO  
IF OBJECT_ID (N'Sales.ufn_SalesByStore', N'IF') IS NOT NULL  
    DROP FUNCTION Sales.ufn_SalesByStore;  
GO  
CREATE FUNCTION Sales.ufn_SalesByStore (@storeid int)  
RETURNS TABLE  
AS  
RETURN   
(  
    SELECT P.ProductID, P.Name, SUM(SD.LineTotal) AS 'Total'  
    FROM Production.Product AS P   
    JOIN Sales.SalesOrderDetail AS SD ON SD.ProductID = P.ProductID  
    JOIN Sales.SalesOrderHeader AS SH ON SH.SalesOrderID = SD.SalesOrderID  
    JOIN Sales.Customer AS C ON SH.CustomerID = C.CustomerID  
    WHERE C.StoreID = @storeid  
    GROUP BY P.ProductID, P.Name  
);  
GO  
```  
  
Per richiamare la funzione, eseguire la query seguente.
  
```sql
SELECT * FROM Sales.ufn_SalesByStore (602);  
```  
  
## <a name="see-also"></a>Vedere anche
[COLLATE &#40; Transact-SQL &#41;](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9)  
[CREATE FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-function-transact-sql.md)  
[Funzioni definite dall'utente](../../relational-databases/user-defined-functions/user-defined-functions.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[Utilizzare i valori di tabella parametri &#40; motore di Database &#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md)  
[Hint di query &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-query.md)
  
  

