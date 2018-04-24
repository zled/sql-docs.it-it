---
title: DATEDIFF (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DATEDIFF_TSQL
- DATEDIFF
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- DATEDIFF function [SQL Server]
- time [SQL Server], crossed boundaries
- differences in date and time [SQL Server]
- counting crossed date time boundaries [SQL Server]
- date and time [SQL Server], DATEDIFF
- dates [SQL Server], crossed boundaries
- boundary differences date and time [SQL Server]
- functions [SQL Server], time
- functions [SQL Server], date and time
- interval dates [SQL Server]
- time [SQL Server], functions
- crossing date time boundaries [SQL Server]
- calculating dates times [SQL Server]
ms.assetid: eba979f2-1a8d-4cce-9d75-b74f9b519b37
caps.latest.revision: 52
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: be399382bedbcdd97c90db6bd83d70d01056ab59
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="datediff-transact-sql"></a>DATEDIFF (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Restituisce il conteggio (intero con segno) dei limiti *datepart* specificati superati con i valori di *startdate* e *enddate* specificati.
  
Per altre differenze, vedere [DATEDIFF_BIG &#40;Transact-SQL&#41;](../../t-sql/functions/datediff-big-transact-sql.md). Per una panoramica di tutti i tipi di dati e delle funzioni di data e ora [!INCLUDE[tsql](../../includes/tsql-md.md)], vedere [Funzioni e tipi di dati di data e ora &#40;Transact-SQL&#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
DATEDIFF ( datepart , startdate , enddate )  
```  
  
## <a name="arguments"></a>Argomenti  
*datepart*  
Parte di *startdate* e *enddate* che specifica il tipo di limite superato. Nella tabella seguente sono elencati tutti gli argomenti *datepart* validi. Variabili definite dall'utente equivalenti non sono valide.
  
|*datepart*|Abbreviazioni|  
|---|---|
|**year**|**yy, yyyy**|  
|**quarter**|**qq, q**|  
|**month**|**mm, m**|  
|**dayofyear**|**dy, y**|  
|**day**|**dd, d**|  
|**week**|**wk, ww**|  
|**hour**|**hh**|  
|**minute**|**mi, n**|  
|**second**|**ss, s**|  
|**millisecond**|**ms**|  
|**microsecond**|**mcs**|  
|**nanosecond**|**ns**|  
  
*startdate*  
Espressione che può essere risolta in un valore **time**, **date**, **smalldatetime**, **datetime**, **datetime2** o **datetimeoffset**. *date* può essere costituito da un'espressione, un'espressione di colonna, una variabile definita dall'utente o un valore letterale stringa. *startdate* viene sottratto da *enddate*.
  
Per evitare ambiguità, esprimere gli anni nel formato a quattro cifre. Per altre informazioni sugli anni a due cifre, vedere [Configurare l'opzione di configurazione del server Cambio data per anno a due cifre](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md).
  
*enddate*  
Vedere *startdate*.
  
## <a name="return-type"></a>Tipo restituito  
 **int**  
  
## <a name="return-value"></a>Valore restituito  
  
-   Ogni elemento *datepart* e le relative abbreviazioni restituiscono lo stesso valore.  
  
Se il valore restituito non è compreso nell'intervallo per **int** (da -2.147.483.648 a +2.147.483.647), viene restituito un errore. Per **millisecond**, la differenza massima tra *startdate* e *enddate* è 24 giorni, 20 ore, 31 minuti e 23,647 secondi. Per **second**, la differenza massima è 68 anni.
  
Se sia a *startdate* che a *enddate* è stato assegnato solo un valore orario e *datepart* non è un oggetto *datepart* orario, viene restituito 0.
  
Per calcolare il valore restituito non viene usato un componente di differenza di fuso orario di *startdate* o *enddate*.
  
Dal momento che [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md) garantisce la precisione solo a livello di minuti, quando viene usato un valore **smalldatetime** per *startdate* o *enddate*, i secondi e i millisecondi vengono sempre impostati su 0 nel valore restituito.
  
Se a una variabile di tipo data viene assegnato solo un valore di tipo ora, il valore della parte mancante della data viene impostato sul valore predefinito: 1900-01-01. Se a una variabile di tipo ora viene assegnato solo un valore di tipo data, il valore della parte mancante dell'ora viene impostato sul valore predefinito: 00.00.00. Se *startdate* o *enddate* hanno solo rispettivamente la parte dell'ora e la parte della data, le parti mancanti vengono impostate sui valori predefiniti.
  
Se i valori *startdate* e *enddate* sono di tipi data diversi e uno di questi comprende un numero maggiore di parti di ora o offre una precisione in secondi frazionari maggiore, le parti mancanti dell'altro valore vengono impostate su 0.
  
## <a name="datepart-boundaries"></a>Limiti di datepart  
Le istruzioni seguenti comprendono gli stessi valori *startdate* e *enddate*. Queste date sono adiacenti e differiscono di 0,0000001 secondi. La differenza tra *startdate* e *enddate* in ogni istruzione oltrepassa un limite di calendario o di ora del rispettivo valore *datepart*. Ciascuna istruzione restituisce 1. Se per questo esempio vengono usati anni diversi e se *startdate* e *enddate* fanno parte della stessa settimana di calendario, il valore restituito per **week** è 0.
  
```sql
SELECT DATEDIFF(year, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(quarter, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(month, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(dayofyear, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(day, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(week, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(hour, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(minute, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(second, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(millisecond, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
```
  
## <a name="remarks"></a>Remarks  
La funzione DATEDIFF può essere utilizzata in un elenco SELECT e nelle clausole WHERE, HAVING, GROUP BY e ORDER BY.
  
DATEDIFF consente di eseguire in modo implicito il cast di valori letterali stringa come tipo di dati **datetime2**. Pertanto, DATEDIFF non supporta il formato AGM se la data viene passata come stringa. Per usare il formato AGM è necessario eseguire il cast della stringa in modo esplicito in un tipo **datetime** o **smalldatetime**.
  
La specifica di SET DATEFIRST non influisce su DATEDIFF. In DATEDIFF viene utilizzata sempre la domenica come primo giorno della settimana per garantire che la funzione sia deterministica.
  
## <a name="examples"></a>Esempi  
Negli esempi seguenti vengono usati tipi diversi di espressioni come argomenti per i parametri *startdate* e *enddate*.
  
### <a name="a-specifying-columns-for-startdate-and-enddate"></a>A. Specifica di colonne per startdate ed enddate  
Nell'esempio seguente viene calcolato il numero di limiti di giorno che si sovrappongono tra le date di due colonne in una tabella.
  
```sql
CREATE TABLE dbo.Duration  
    (  
    startDate datetime2  
    ,endDate datetime2  
    );  
INSERT INTO dbo.Duration(startDate,endDate)  
    VALUES('2007-05-06 12:10:09','2007-05-07 12:10:09');  
SELECT DATEDIFF(day,startDate,endDate) AS 'Duration'  
FROM dbo.Duration;  
-- Returns: 1  
```  
  
### <a name="b-specifying-user-defined-variables-for-startdate-and-enddate"></a>B. Specifica di variabili definite dall'utente per startdate ed enddate  
Nell'esempio seguente vengono usate variabili definite dall'utente come argomenti per *startdate* e *enddate*.
  
```sql
DECLARE @startdate datetime2 = '2007-05-05 12:10:09.3312722';  
DECLARE @enddate datetime2 = '2007-05-04 12:10:09.3312722';   
SELECT DATEDIFF(day, @startdate, @enddate);  
```  
  
### <a name="c-specifying-scalar-system-functions-for-startdate-and-enddate"></a>C. Specifica di funzioni di sistema scalari per startdate ed enddate  
Nell'esempio seguente vengono usate funzioni di sistema scalari come argomenti per *startdate* e *enddate*.
  
```sql
SELECT DATEDIFF(millisecond, GETDATE(), SYSDATETIME());  
```  
  
### <a name="d-specifying-scalar-subqueries-and-scalar-functions-for-startdate-and-enddate"></a>D. Specifica di sottoquery scalari e di funzioni scalari per startdate ed enddate  
Nell'esempio seguente vengono usate sottoquery e funzioni scalari come argomenti per *startdate* e *enddate*.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT DATEDIFF(day,(SELECT MIN(OrderDate) FROM Sales.SalesOrderHeader),  
    (SELECT MAX(OrderDate) FROM Sales.SalesOrderHeader));  
```  
  
### <a name="e-specifying-constants-for-startdate-and-enddate"></a>E. Specifica di costanti per startdate ed enddate  
Nell'esempio seguente vengono usate costanti di tipo carattere come argomenti per *startdate* e *enddate*.
  
```sql
SELECT DATEDIFF(day, '2007-05-07 09:53:01.0376635'  
    , '2007-05-08 09:53:01.0376635');  
```  
  
### <a name="f-specifying-numeric-expressions-and-scalar-system-functions-for-enddate"></a>F. Specifica di espressioni numeriche e funzioni di sistema scalari per enddate  
Nell'esempio seguente vengono usate un'espressione numerica, `(GETDATE ()+ 1)`, e funzioni di sistema scalari, `GETDATE` e `SYSDATETIME`, come argomenti per *enddate*.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT DATEDIFF(day, '2007-05-07 09:53:01.0376635', GETDATE()+ 1)   
    AS NumberOfDays  
FROM Sales.SalesOrderHeader;  
GO  
USE AdventureWorks2012;  
GO  
SELECT DATEDIFF(day, '2007-05-07 09:53:01.0376635', DATEADD(day,1,SYSDATETIME())) AS NumberOfDays  
FROM Sales.SalesOrderHeader;  
GO  
```  
  
### <a name="g-specifying-ranking-functions-for-startdate"></a>G. Specifica di funzioni di rango per startdate  
Nell'esempio seguente viene usata una funzione di rango come argomento per *startdate*.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT p.FirstName, p.LastName  
    ,DATEDIFF(day,ROW_NUMBER() OVER (ORDER BY   
        a.PostalCode),SYSDATETIME()) AS 'Row Number'  
FROM Sales.SalesPerson s   
    INNER JOIN Person.Person p   
        ON s.BusinessEntityID = p.BusinessEntityID  
    INNER JOIN Person.Address a   
        ON a.AddressID = p.BusinessEntityID  
WHERE TerritoryID IS NOT NULL   
    AND SalesYTD <> 0;  
```  
  
### <a name="h-specifying-an-aggregate-window-function-for-startdate"></a>H. Specifica di una funzione finestra di aggregazione per startdate  
Nell'esempio seguente viene usata una funzione finestra di aggregazione come argomento per *startdate*.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT soh.SalesOrderID, sod.ProductID, sod.OrderQty,soh.OrderDate  
    ,DATEDIFF(day,MIN(soh.OrderDate)   
        OVER(PARTITION BY soh.SalesOrderID),SYSDATETIME() ) AS 'Total'  
FROM Sales.SalesOrderDetail sod  
    INNER JOIN Sales.SalesOrderHeader soh  
        ON sod.SalesOrderID = soh.SalesOrderID  
WHERE soh.SalesOrderID IN(43659,58918);  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
Negli esempi seguenti vengono usati tipi diversi di espressioni come argomenti per i parametri *startdate* e *enddate*.
  
### <a name="i-specifying-columns-for-startdate-and-enddate"></a>I. Specifica di colonne per startdate ed enddate  
Nell'esempio seguente viene calcolato il numero di limiti di giorno che si sovrappongono tra le date di due colonne in una tabella.
  
```sql
CREATE TABLE dbo.Duration (  
    startDate datetime2  
    ,endDate datetime2  
    );  
INSERT INTO dbo.Duration(startDate,endDate)  
    VALUES('2007-05-06 12:10:09','2007-05-07 12:10:09');  
SELECT TOP(1) DATEDIFF(day,startDate,endDate) AS Duration  
FROM dbo.Duration;  
-- Returns: 1  
```  
  
### <a name="j-specifying-scalar-subqueries-and-scalar-functions-for-startdate-and-enddate"></a>J. Specifica di sottoquery scalari e di funzioni scalari per startdate ed enddate  
Nell'esempio seguente vengono usate sottoquery e funzioni scalari come argomenti per *startdate* e *enddate*.
  
```sql
-- Uses AdventureWorks  
  
SELECT TOP(1) DATEDIFF(day,(SELECT MIN(HireDate) FROM dbo.DimEmployee),  
    (SELECT MAX(HireDate) FROM dbo.DimEmployee))   
FROM dbo.DimEmployee;  
  
```  
  
### <a name="k-specifying-constants-for-startdate-and-enddate"></a>K. Specifica di costanti per startdate ed enddate  
Nell'esempio seguente vengono usate costanti di tipo carattere come argomenti per *startdate* e *enddate*.
  
```sql
-- Uses AdventureWorks  
  
SELECT TOP(1) DATEDIFF(day, '2007-05-07 09:53:01.0376635'  
    , '2007-05-08 09:53:01.0376635') FROM DimCustomer;  
```  
  
### <a name="l-specifying-ranking-functions-for-startdate"></a>L. Specifica di funzioni di rango per startdate  
Nell'esempio seguente viene usata una funzione di rango come argomento per *startdate*.
  
```sql
-- Uses AdventureWorks  
  
SELECT FirstName, LastName  
,DATEDIFF(day,ROW_NUMBER() OVER (ORDER BY   
        DepartmentName),SYSDATETIME()) AS RowNumber  
FROM dbo.DimEmployee;  
```  
  
### <a name="m-specifying-an-aggregate-window-function-for-startdate"></a>M. Specifica di una funzione finestra di aggregazione per startdate  
Nell'esempio seguente viene usata una funzione finestra di aggregazione come argomento per *startdate*.
  
```sql
-- Uses AdventureWorks  
  
SELECT FirstName, LastName, DepartmentName  
    ,DATEDIFF(year,MAX(HireDate)  
             OVER (PARTITION BY DepartmentName),SYSDATETIME()) AS SomeValue  
FROM dbo.DimEmployee  
```  
  
## <a name="see-also"></a>Vedere anche
[DATEDIFF_BIG &#40;Transact-SQL&#41;](../../t-sql/functions/datediff-big-transact-sql.md)  
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  


