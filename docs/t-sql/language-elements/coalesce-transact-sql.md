---
title: COALESCE (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/30/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COALESCE
- COALESCE_TSQL
dev_langs: TSQL
helpviewer_keywords:
- expressions [SQL Server], nonnull
- COALESCE function
- first nonnull expressions [SQL Server]
- nonnull expressions
ms.assetid: fafc0dba-f8a8-4aad-9b7f-908e34b74d88
caps.latest.revision: "52"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: b2d67040ae1f55e94baf03eb45929459fc39a84a
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="coalesce-transact-sql"></a>COALESCE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Valuta gli argomenti nell'ordine e restituisce il valore corrente della prima espressione che inizialmente non restituisce `NULL`. Ad esempio, `SELECT COALESCE(NULL, NULL, 'third_value', 'fourth_value');` restituisce il terzo valore perché il terzo valore è il primo valore che non sia null. 
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
COALESCE ( expression [ ,...n ] )   
```  
  
## <a name="arguments"></a>Argomenti  
 *espressione*  
 È un [espressione](../../t-sql/language-elements/expressions-transact-sql.md) di qualsiasi tipo.  
  
## <a name="return-types"></a>Tipi restituiti  
 Restituisce il tipo di dati di *espressione* le priorità di tipo di dati. Se tutte le espressioni non ammettono valori Null, il risultato non ammetterà valori Null.  
  
## <a name="remarks"></a>Osservazioni  
 Se tutti gli argomenti sono `NULL`, `COALESCE` restituisce `NULL`. Almeno uno dei valori null deve essere un oggetto tipizzato `NULL`.  
  
## <a name="comparing-coalesce-and-case"></a>Confronto tra COALESCE e CASE  
 Il `COALESCE` espressione è una sintassi abbreviata per la `CASE` espressione.  Ovvero, il codice `COALESCE`(*expression1*,*... n*) viene quindi riscritto da query optimizer il seguente `CASE` espressione:  
  
 ```sql  
 CASE  
 WHEN (expression1 IS NOT NULL) THEN expression1  
 WHEN (expression2 IS NOT NULL) THEN expression2  
 ...  
 ELSE expressionN  
 END  
 ```  
  
 Ciò significa che i valori di input (*expression1*, *expression2*, *expressionN*e così via) vengono valutati più volte. Inoltre, in conformità con lo standard SQL, un'espressione di valori che contiene una sottoquery è considerata non deterministica e la sottoquery viene valutata due volte. In entrambi i casi, è possibile che tra la prima valutazione e quelle successive i risultati siano diversi.  
  
 Ad esempio, quando viene eseguito il codice `COALESCE((subquery), 1)`, la sottoquery viene valutata due volte. Di conseguenza, è possibile che si ottengano risultati differenti a seconda del livello di isolamento della query. Ad esempio, il codice può restituire `NULL` sotto il `READ COMMITTED` livello di isolamento in un ambiente multiutente. Per garantire risultati stabili vengono restituiti, utilizzare il `SNAPSHOT ISOLATION` livello di isolamento o la sostituzione `COALESCE` con il `ISNULL` (funzione). In alternativa, è possibile riscrivere la query per eseguire il push della sottoquery in un sub-SELECT come illustrato nell'esempio seguente:  
  
```sql  
SELECT CASE WHEN x IS NOT NULL THEN x ELSE 1 END  
from  
(  
SELECT (SELECT Nullable FROM Demo WHERE SomeCol = 1) AS x  
) AS T;  
  
```  
  
## <a name="comparing-coalesce-and-isnull"></a>Confronto tra COALESCE e ISNULL  
 Il `ISNULL` funzione e `COALESCE` espressione presentano uno scopo simile, ma può funzionare in modo diverso.  
  
1.  Poiché `ISNULL` è una funzione, viene valutata una sola volta.  Come descritto in precedenza, i valori di input per il `COALESCE` espressione può essere valutata più volte.  
  
2.  La determinazione dei tipi di dati dell'espressione risultante è differente. `ISNULL`utilizza il tipo di dati del primo parametro, `COALESCE` segue il `CASE` regole di espressione e restituisce il tipo di dati del valore con la precedenza più alta.  
  
3.  Il supporto di valori null dell'espressione di risultato è diverso per `ISNULL` e `COALESCE`. Il `ISNULL` il valore restituito è sempre considerato non ammette valori null (supponendo che il valore restituito è uno non nullable) mentre `COALESCE` con parametri non null è considerato `NULL`. Pertanto, le espressioni `ISNULL(NULL, 1)` e `COALESCE(NULL, 1)`, sebbene equivalenti, hanno valori di supporto di valori null. Una differenza in questo modo se si utilizzano queste espressioni nelle colonne calcolate, creazione di vincoli di chiave o rendendo deterministico il valore restituito di una funzione definita dall'utente scalare in modo che possa essere indicizzato come mostrato nell'esempio seguente:  
  
    ```sql  
    USE tempdb;  
    GO  
    -- This statement fails because the PRIMARY KEY cannot accept NULL values  
    -- and the nullability of the COALESCE expression for col2   
    -- evaluates to NULL.  
    CREATE TABLE #Demo   
    (   
    col1 integer NULL,   
    col2 AS COALESCE(col1, 0) PRIMARY KEY,   
    col3 AS ISNULL(col1, 0)   
    );   
  
    -- This statement succeeds because the nullability of the   
    -- ISNULL function evaluates AS NOT NULL.  
  
    CREATE TABLE #Demo   
    (   
    col1 integer NULL,   
    col2 AS COALESCE(col1, 0),   
    col3 AS ISNULL(col1, 0) PRIMARY KEY   
    );  
    ```  
  
4.  Le convalide per `ISNULL` e `COALESCE` anche sono diversi. Ad esempio, un `NULL` valore per `ISNULL` viene convertito in **int** mentre per `COALESCE`, è necessario fornire un tipo di dati.  
  
5.  `ISNULL`accetta solo due parametri, mentre `COALESCE` accetta un numero variabile di parametri.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-running-a-simple-example"></a>A. Esecuzione di un esempio semplice  
 Nell'esempio seguente viene illustrato il modo in cui `COALESCE` seleziona i dati dalla prima colonna in cui è presente un valore non Null. In questo esempio viene utilizzato il database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```sql  
SELECT Name, Class, Color, ProductNumber,  
COALESCE(Class, Color, ProductNumber) AS FirstNotNull  
FROM Production.Product;  
```  
  
### <a name="b-running-a-complex-example"></a>B. Esecuzione di un esempio complesso  
 Nell'esempio seguente viene illustrata una tabella `wages` che include tre colonne con informazioni sulla retribuzione annua dei dipendenti, ovvero retribuzione oraria, stipendio e commissione. Un dipendente tuttavia riceve un solo tipo di paga. Per determinare l'importo totale pagato a tutti i dipendenti, utilizzare la funzione `COALESCE` per ottenere solo i valori non Null delle colonne `hourly_wage`, `salary` e `commission`.  
  
```sql  
SET NOCOUNT ON;  
GO  
USE tempdb;  
IF OBJECT_ID('dbo.wages') IS NOT NULL  
    DROP TABLE wages;  
GO  
CREATE TABLE dbo.wages  
(  
    emp_id        tinyint   identity,  
    hourly_wage   decimal   NULL,  
    salary        decimal   NULL,  
    commission    decimal   NULL,  
    num_sales     tinyint   NULL  
);  
GO  
INSERT dbo.wages (hourly_wage, salary, commission, num_sales)  
VALUES  
    (10.00, NULL, NULL, NULL),  
    (20.00, NULL, NULL, NULL),  
    (30.00, NULL, NULL, NULL),  
    (40.00, NULL, NULL, NULL),  
    (NULL, 10000.00, NULL, NULL),  
    (NULL, 20000.00, NULL, NULL),  
    (NULL, 30000.00, NULL, NULL),  
    (NULL, 40000.00, NULL, NULL),  
    (NULL, NULL, 15000, 3),  
    (NULL, NULL, 25000, 2),  
    (NULL, NULL, 20000, 6),  
    (NULL, NULL, 14000, 4);  
GO  
SET NOCOUNT OFF;  
GO  
SELECT CAST(COALESCE(hourly_wage * 40 * 52,   
   salary,   
   commission * num_sales) AS money) AS 'Total Salary'   
FROM dbo.wages  
ORDER BY 'Total Salary';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```   
 Total Salary  
 ------------  
 10000.00  
 20000.00  
 20800.00  
 30000.00  
 40000.00  
 41600.00  
 45000.00  
 50000.00  
 56000.00  
 62400.00  
 83200.00  
 120000.00  
  
 (12 row(s) affected)
 ```  
  
### <a name="c-simple-example"></a>C: esempio  
 Nell'esempio seguente viene illustrato come `COALESCE` seleziona i dati dalla prima colonna che contiene un valore non null. Si supponga che per questo esempio che il `Products` tabella contiene dati:  
  
 ```  
 Name         Color      ProductNumber  
 ------------ ---------- -------------  
 Socks, Mens  NULL       PN1278  
 Socks, Mens  Blue       PN1965  
 NULL         White      PN9876
 ```  
  
 È quindi possibile eseguire la seguente query di unione:  
  
```sql  
SELECT Name, Color, ProductNumber, COALESCE(Color, ProductNumber) AS FirstNotNull   
FROM Products ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```  
 Name         Color      ProductNumber  FirstNotNull  
 ------------ ---------- -------------  ------------  
 Socks, Mens  NULL       PN1278         PN1278  
 Socks, Mens  Blue       PN1965         Blue  
 NULL         White      PN9876         White
 ```  
  
 Si noti che nella prima riga, il `FirstNotNull` valore `PN1278`, non `Socks, Mens`. In questo modo il `Name` colonna non è stata specificata come parametro per `COALESCE` nell'esempio.  
  
### <a name="d-complex-example"></a>Unità d: esempio complesso  
 L'esempio seguente usa `COALESCE` per confrontare i valori in tre colonne e restituire solo il valore non null trovato nelle colonne.  
  
```sql  
CREATE TABLE dbo.wages  
(  
    emp_id        tinyint   NULL,  
    hourly_wage   decimal   NULL,  
    salary        decimal   NULL,  
    commission    decimal   NULL,  
    num_sales     tinyint   NULL  
);  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (1, 10.00, NULL, NULL, NULL);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (2, 20.00, NULL, NULL, NULL);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (3, 30.00, NULL, NULL, NULL);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (4, 40.00, NULL, NULL, NULL);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (5, NULL, 10000.00, NULL, NULL);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (6, NULL, 20000.00, NULL, NULL);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (7, NULL, 30000.00, NULL, NULL);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (8, NULL, 40000.00, NULL, NULL);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (9, NULL, NULL, 15000, 3);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (10,NULL, NULL, 25000, 2);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (11, NULL, NULL, 20000, 6);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (12, NULL, NULL, 14000, 4);  
  
SELECT CAST(COALESCE(hourly_wage * 40 * 52,   
   salary,   
   commission * num_sales) AS decimal(10,2)) AS TotalSalary   
FROM dbo.wages  
ORDER BY TotalSalary;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 Total Salary  
 ------------  
 10000.00  
 20000.00  
 20800.00  
 30000.00  
 40000.00  
 41600.00  
 45000.00  
 50000.00  
 56000.00  
 62400.00  
 83200.00  
 120000.00
 ```  
  
## <a name="see-also"></a>Vedere anche  
 [ISNULL &#40;Transact-SQL&#41;](../../t-sql/functions/isnull-transact-sql.md)   
 [CASE &#40;Transact-SQL&#41;](../../t-sql/language-elements/case-transact-sql.md)  
  
  
