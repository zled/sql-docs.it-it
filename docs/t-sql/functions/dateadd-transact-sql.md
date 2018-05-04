---
title: DATEADD (Transact-SQL) | Microsoft Docs
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
- DATEADD
- DATEADD_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- add interval to date or time [SQL Server]
- subtract interval from date or time [SQL Server]
- functions [SQL Server], time
- functions [SQL Server], date and time
- time [SQL Server], functions
- dates [SQL Server], intervals
- date and time [SQL Server], DATEADD
- DATEADD function [SQL Server]
ms.assetid: 89c5ae32-89c6-47e1-979e-15d97908b9f1
caps.latest.revision: 71
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: dd7dd81f8e12b0c14048fd8ab550e7edfd780cf5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="dateadd-transact-sql"></a>DATEADD (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Restituisce il valore *date* specificato con l'intervallo di valori *number* specificato (interi con segno) aggiunto a un valore *datepart* specificato del valore *date* stesso.
  
Per una panoramica di tutti i tipi di dati e delle funzioni di data e ora [!INCLUDE[tsql](../../includes/tsql-md.md)], vedere [Funzioni e tipi di dati di data e ora &#40;Transact-SQL&#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
DATEADD (datepart , number , date )  
```  
  
## <a name="arguments"></a>Argomenti  
*datepart*  
È la parte dell'elemento *date* a cui viene aggiunto un **numero***intero*. Nella tabella seguente sono elencati tutti gli argomenti *datepart* validi. Variabili definite dall'utente equivalenti non sono valide.
  
|*datepart*|Abbreviazioni|  
|---|---|
|**year**|**yy**, **yyyy**|  
|**quarter**|**qq**, **q**|  
|**month**|**mm**, **m**|  
|**dayofyear**|**dy**, **y**|  
|**day**|**dd**, **d**|  
|**week**|**wk**, **ww**|  
|**weekday**|**dw**, **w**|  
|**hour**|**hh**|  
|**minute**|**mi**, **n**|  
|**second**|**ss**, **s**|  
|**millisecond**|**ms**|  
|**microsecond**|**mcs**|  
|**nanosecond**|**ns**|  
  
*number*  
Espressione che può essere risolta in un tipo [int](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md) aggiunto a un elemento *datepart* di *date*. Le variabili definite dall'utente sono valide.  
Se un valore viene specificato mediante una frazione decimale, la frazione viene troncata e non arrotondata.
  
*data*  
Espressione che può essere risolta in un valore **time**, **date**, **smalldatetime**, **datetime**, **datetime2** o **datetimeoffset**. *date* può essere costituito da un'espressione, un'espressione di colonna, una variabile definita dall'utente o un valore letterale stringa. Se l'espressione è un valore letterale stringa, deve essere risolta in un tipo **datetime**. Per evitare ambiguità, esprimere gli anni nel formato a quattro cifre. Per altre informazioni sugli anni a due cifre, vedere [Configurare l'opzione di configurazione del server Cambio data per anno a due cifre](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md).
  
## <a name="return-types"></a>Tipi restituiti
Il tipo di dati restituiti è rappresentato dal tipo di dati dell'argomento *date*, ad eccezione dei valori letterali stringa.
Il tipo di dati restituiti per un valore letterale stringa è **datetime**. Se la scala dei secondi del valore letterale stringa ha più di tre posizioni (.nnn) o contiene la parte relativa alla differenza di fuso orario, viene generato un errore.
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="datepart-argument"></a>Argomento datepart  
**dayofyear**, **day**, e **weekday** restituiscono lo stesso valore.
  
Ogni elemento *datepart* e le relative abbreviazioni restituiscono lo stesso valore.
  
Se *datepart* è **month**, il mese del valore *date* ha più giorni del mese restituito e il giorno del valore *date* non esiste nel mese restituito, viene restituito l'ultimo giorno del mese restituito. Ad esempio, settembre ha 30 giorni. Pertanto, le due istruzioni seguenti restituiscono 2006-09-30 00:00:00.000:
  
```sql
SELECT DATEADD(month, 1, '20060830');
SELECT DATEADD(month, 1, '20060831');
```
  
## <a name="number-argument"></a>Argomento number  
Un argomento *number* non può superare l'intervallo del tipo **int**. Nelle istruzioni seguenti l'argomento per il parametro *number* supera l'intervallo di **int** di una unità. Viene restituito il messaggio di errore seguente: "`Msg 8115, Level 16, State 2, Line 1. Arithmetic overflow error converting expression to data type int."`
  
```sql
SELECT DATEADD(year,2147483648, '20060731');  
SELECT DATEADD(year,-2147483649, '20060731');  
```  
  
## <a name="date-argument"></a>Argomento date  
Non è possibile incrementare un argomento per il parametro *date* a un valore al di fuori dell'intervallo consentito per il tipo di dati corrispondente. Nelle istruzioni seguenti il valore *number* aggiunto al valore *date* supera l'intervallo del tipo di dati *date*. Viene restituito il messaggio di errore seguente: "`Msg 517, Level 16, State 1, Line 1 Adding a value to a 'datetime' column caused overflow`".
  
```sql
SELECT DATEADD(year,2147483647, '20060731');  
SELECT DATEADD(year,-2147483647, '20060731');  
```  
  
## <a name="return-values-for-a-smalldatetime-date-and-a-second-or-fractional-seconds-datepart"></a>Valori restituiti per una data smalldatetime e un valore datepart in secondi o secondi frazionari  
La seconda parte di un valore [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md) è sempre 00. Se *date* è **smalldatetime**, si applica quanto segue:
-   Se *datepart* è **second** e *number* è compreso tra -30 e +29, non viene eseguita alcuna aggiunta.  
-   Se *datepart* è **second** e *number* è minore di -30 o maggiore di +29, l'aggiunta viene eseguita iniziando da un minuto.  
-   Se *datepart* è **millisecond** e *number* è compreso tra -30001 e +29998, non viene eseguita alcuna aggiunta.  
-   Se *datepart* è **millisecond** e *number* è minore di -30001 o maggiore di +29998, l'aggiunta viene eseguita iniziando da un minuto.  
  
## <a name="remarks"></a>Remarks  
È possibile usare DATEADD nelle clausole SELECT \<list>, WHERE, HAVING, GROUP BY e ORDER BY.
  
## <a name="fractional-seconds-precision"></a>Precisione in secondi frazionari
L'aggiunta di un valore *datepart* di **microsecond** o **nanosecond** per i tipi di dati *date* **smalldatetime**, **date**, e **datetime** non è consentita.
  
I millisecondi hanno una scala di 3 (.123), i microsecondi hanno una scala di 6 (.123456) e i nanosecondi hanno una scala di 9 (.123456789). I tipi di dati **time**, **datetime2** e **datetimeoffset** hanno una scala massima pari a 7 (0,1234567). Se *datepart* è **nanosecond**, *number* deve essere 100 prima che i secondi frazionari di *date* aumentino. Un valore di *number* compreso tra 1 e 49 viene arrotondato per difetto a 0 e un valore number da 50 a 99 viene arrotondato per eccesso a 100.
  
Le istruzioni seguenti aggiungono un valore *datepart* di **millisecond**, **microsecond** o **nanosecond**.
  
```sql
DECLARE @datetime2 datetime2 = '2007-01-01 13:10:10.1111111';  
SELECT '1 millisecond', DATEADD(millisecond,1,@datetime2)  
UNION ALL  
SELECT '2 milliseconds', DATEADD(millisecond,2,@datetime2)  
UNION ALL  
SELECT '1 microsecond', DATEADD(microsecond,1,@datetime2)  
UNION ALL  
SELECT '2 microseconds', DATEADD(microsecond,2,@datetime2)  
UNION ALL  
SELECT '49 nanoseconds', DATEADD(nanosecond,49,@datetime2)  
UNION ALL  
SELECT '50 nanoseconds', DATEADD(nanosecond,50,@datetime2)  
UNION ALL  
SELECT '150 nanoseconds', DATEADD(nanosecond,150,@datetime2);  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
1 millisecond     2007-01-01 13:10:10.1121111  
2 milliseconds    2007-01-01 13:10:10.1131111  
1 microsecond     2007-01-01 13:10:10.1111121  
2 microseconds    2007-01-01 13:10:10.1111131  
49 nanoseconds    2007-01-01 13:10:10.1111111  
50 nanoseconds    2007-01-01 13:10:10.1111112  
150 nanoseconds   2007-01-01 13:10:10.1111113  
```  
  
## <a name="time-zone-offset"></a>Differenza di fuso orario
L'aggiunta non è consentita per la differenza di fuso orario.
  
## <a name="examples"></a>Esempi  

### <a name="a-incrementing-datepart-by-an-interval-of-1"></a>A. Incremento di un datepart a intervalli di una unità  
Ognuna delle istruzioni seguenti incrementa il valore *datepart* a intervalli di una unità.
  
```sql
DECLARE @datetime2 datetime2 = '2007-01-01 13:10:10.1111111';  
SELECT 'year', DATEADD(year,1,@datetime2)  
UNION ALL  
SELECT 'quarter',DATEADD(quarter,1,@datetime2)  
UNION ALL  
SELECT 'month',DATEADD(month,1,@datetime2)  
UNION ALL  
SELECT 'dayofyear',DATEADD(dayofyear,1,@datetime2)  
UNION ALL  
SELECT 'day',DATEADD(day,1,@datetime2)  
UNION ALL  
SELECT 'week',DATEADD(week,1,@datetime2)  
UNION ALL  
SELECT 'weekday',DATEADD(weekday,1,@datetime2)  
UNION ALL  
SELECT 'hour',DATEADD(hour,1,@datetime2)  
UNION ALL  
SELECT 'minute',DATEADD(minute,1,@datetime2)  
UNION ALL  
SELECT 'second',DATEADD(second,1,@datetime2)  
UNION ALL  
SELECT 'millisecond',DATEADD(millisecond,1,@datetime2)  
UNION ALL  
SELECT 'microsecond',DATEADD(microsecond,1,@datetime2)  
UNION ALL  
SELECT 'nanosecond',DATEADD(nanosecond,1,@datetime2);  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Year         2008-01-01 13:10:10.1111111  
quarter      2007-04-01 13:10:10.1111111  
month        2007-02-01 13:10:10.1111111  
dayofyear    2007-01-02 13:10:10.1111111  
day          2007-01-02 13:10:10.1111111  
week         2007-01-08 13:10:10.1111111  
weekday      2007-01-02 13:10:10.1111111  
hour         2007-01-01 14:10:10.1111111  
minute       2007-01-01 13:11:10.1111111  
second       2007-01-01 13:10:11.1111111  
millisecond  2007-01-01 13:10:10.1121111  
microsecond  2007-01-01 13:10:10.1111121  
nanosecond   2007-01-01 13:10:10.1111111  
```  
  
### <a name="b-incrementing-more-than-one-level-of-datepart-in-one-statement"></a>B. Incremento di più livelli di datepart in un'unica istruzione  
Ognuna delle istruzioni seguenti incrementa *datepart* di un valore *number* abbastanza grande da incrementare anche l'argomento *datepart* di livello immediatamente più alto di *date*.
  
```sql
DECLARE @datetime2 datetime2;  
SET @datetime2 = '2007-01-01 01:01:01.1111111';  
--Statement                                 Result     
-------------------------------------------------------------------   
SELECT DATEADD(quarter,4,@datetime2);     --2008-01-01 01:01:01.110  
SELECT DATEADD(month,13,@datetime2);      --2008-02-01 01:01:01.110  
SELECT DATEADD(dayofyear,365,@datetime2); --2008-01-01 01:01:01.110  
SELECT DATEADD(day,365,@datetime2);       --2008-01-01 01:01:01.110  
SELECT DATEADD(week,5,@datetime2);        --2007-02-05 01:01:01.110  
SELECT DATEADD(weekday,31,@datetime2);    --2007-02-01 01:01:01.110  
SELECT DATEADD(hour,23,@datetime2);       --2007-01-02 00:01:01.110  
SELECT DATEADD(minute,59,@datetime2);     --2007-01-01 02:00:01.110  
SELECT DATEADD(second,59,@datetime2);     --2007-01-01 01:02:00.110  
SELECT DATEADD(millisecond,1,@datetime2); --2007-01-01 01:01:01.110  
```  
  
### <a name="c-using-expressions-as-arguments-for-the-number-and-date-parameters"></a>C. Utilizzo di espressioni come argomenti per i parametri number e date  
Negli esempi seguenti vengono usati tipi diversi di espressioni come argomenti per i parametri *number* e *date*. Gli esempi usano il database AdventureWorks.
  
#### <a name="specifying-a-column-as-date"></a>Indicazione di una colonna come data  
Nell'esempio seguente vengono aggiunti `2` giorni a ogni valore nella colonna `OrderDate` per derivare una nuova colonna denominata `PromisedShipDate`.
  
```sql
SELECT SalesOrderID  
    ,OrderDate   
    ,DATEADD(day,2,OrderDate) AS PromisedShipDate  
FROM Sales.SalesOrderHeader;  
```  
  
Set di risultati parziale:
  
```sql
SalesOrderID OrderDate               PromisedShipDate  
------------ ----------------------- -----------------------  
43659        2005-07-01 00:00:00.000 2005-07-03 00:00:00.000  
43660        2005-07-01 00:00:00.000 2005-07-03 00:00:00.000  
43661        2005-07-01 00:00:00.000 2005-07-03 00:00:00.000  
...  
43702        2005-07-02 00:00:00.000 2005-07-04 00:00:00.000  
43703        2005-07-02 00:00:00.000 2005-07-04 00:00:00.000  
43704        2005-07-02 00:00:00.000 2005-07-04 00:00:00.000  
43705        2005-07-02 00:00:00.000 2005-07-04 00:00:00.000  
43706        2005-07-03 00:00:00.000 2005-07-05 00:00:00.000  
...  
43711        2005-07-04 00:00:00.000 2005-07-06 00:00:00.000  
43712        2005-07-04 00:00:00.000 2005-07-06 00:00:00.000  
...  
43740        2005-07-11 00:00:00.000 2005-07-13 00:00:00.000  
43741        2005-07-12 00:00:00.000 2005-07-14 00:00:00.000  
  
```  
  
#### <a name="specifying-user-defined-variables-as-number-and-date"></a>Indicazione di variabili definite dall'utente come argomenti number e date  
Nell'esempio seguente vengono specificate variabili definite dall'utente come argomenti per i parametri *number* e *date*.
  
```sql
DECLARE @days int = 365,   
        @datetime datetime = '2000-01-01 01:01:01.111'; /* 2000 was a leap year */;  
SELECT DATEADD(day, @days, @datetime);  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
-----------------------  
2000-12-31 01:01:01.110  
  
(1 row(s) affected)  
```  
  
#### <a name="specifying-scalar-system-function-as-date"></a>Indicazione di una funzione di sistema scalare come valore date  
Nell'esempio seguente viene specificata la funzione `SYSDATETIME` per *date*.
  
```sql
SELECT DATEADD(month, 1, SYSDATETIME());  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
---------------------------  
2013-02-06 14:29:59.6727944  
  
(1 row(s) affected)  
```  
  
#### <a name="specifying-scalar-subqueries-and-scalar-functions-as-number-and-date"></a>Indicazione di sottoquery scalari e funzioni scalari come valori number e date  
Nell'esempio seguente vengono usate sottoquery scalari, `MAX(ModifiedDate)`, come argomenti per *number* e *date*. `(SELECT TOP 1 BusinessEntityID FROM Person.Person)` è un argomento fittizio che serve per far in modo che il parametro number illustri come selezionare un argomento *number* da un elenco di valori.
  
```sql
SELECT DATEADD(month,(SELECT TOP 1 BusinessEntityID FROM Person.Person),  
    (SELECT MAX(ModifiedDate) FROM Person.Person));  
```  
  
#### <a name="specifying-numeric-expressions-and-scalar-system-functions-as-number-and-date"></a>Indicazione di espressioni numeriche e funzioni di sistema scalari come valori number e date  
Nell'esempio seguente viene usata un'espressione numerica (-`(10/2))`, [operatori unari](../../mdx/unary-operators.md) (`-`), un [operatore aritmetico](../../mdx/arithmetic-operators.md) (`/`) e funzioni di sistema scalari (`SYSDATETIME`) come argomenti per *number* e *date*.
  
```sql
SELECT DATEADD(month,-(10/2), SYSDATETIME());  
```  
  
#### <a name="specifying-ranking-functions-as-number"></a>Indicazione di funzioni di rango come argomenti number  
Nell'esempio seguente viene usata una funzione di rango come argomento per *number*.
  
```sql
SELECT p.FirstName, p.LastName  
    ,DATEADD(day,ROW_NUMBER() OVER (ORDER BY  
        a.PostalCode),SYSDATETIME()) AS 'Row Number'  
FROM Sales.SalesPerson AS s   
    INNER JOIN Person.Person AS p   
        ON s.BusinessEntityID = p.BusinessEntityID  
    INNER JOIN Person.Address AS a   
        ON a.AddressID = p.BusinessEntityID  
WHERE TerritoryID IS NOT NULL   
    AND SalesYTD <> 0;  
```  
  
#### <a name="specifying-an-aggregate-window-function-as-number"></a>Indicazione di una funzione finestra di aggregazione come argomento number  
Nell'esempio seguente viene usata una funzione finestra di aggregazione come argomento per un parametro *number*.
  
```sql
SELECT SalesOrderID, ProductID, OrderQty  
    ,DATEADD(day,SUM(OrderQty)   
        OVER(PARTITION BY SalesOrderID),SYSDATETIME()) AS 'Total'  
FROM Sales.SalesOrderDetail   
WHERE SalesOrderID IN(43659,43664);  
GO  
```  
  
  
## <a name="see-also"></a>Vedere anche
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  

