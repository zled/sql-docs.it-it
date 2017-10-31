---
title: ROW_NUMBER (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 09/11/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ROW_NUMBER
- ROW_NUMBER_TSQL
- ROW_NUMBER()_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ROW_NUMBER function
- row numbers [SQL Server]
- sequential row numbers [SQL Server]
ms.assetid: 82fa9016-77db-4b42-b4c8-df6095b81906
caps.latest.revision: 50
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 820acddf7de1282501caf2fcaa43dbc757b98b7a
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="rownumber-transact-sql"></a>ROW_NUMBER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Impostare l'output di un risultato di numeri. In particolare, restituisce il numero sequenziale di una riga all'interno di una partizione di un set di risultati, a partire da 1 per la prima riga in ogni partizione. 
  
`ROW_NUMBER`e `RANK` sono simili. `ROW_NUMBER`tutti i numeri di righe in sequenza (ad esempio 1, 2, 3, 4, 5). `RANK`fornisce lo stesso valore numerico per i valori equivalenti (ad esempio 1, 2, 2, 4, 5).   
  
> [!NOTE]
> `ROW_NUMBER`un tipo di valore viene calcolato quando viene eseguita la query. Per rendere persistenti i numeri in una tabella, vedere [proprietà IDENTITY](../../t-sql/statements/create-table-transact-sql-identity-property.md) e [sequenza](../../t-sql/statements/create-sequence-transact-sql.md). 
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
 
  
## <a name="syntax"></a>Sintassi  
  
```  
ROW_NUMBER ( )   
    OVER ( [ PARTITION BY value_expression , ... [ n ] ] order_by_clause )  
```  
  
## <a name="arguments"></a>Argomenti  
 PARTITION BY *value_expression*  
 Divide il set di risultati generato dal [FROM](../../t-sql/queries/from-transact-sql.md) clausola in partizioni alle quali viene applicata la funzione ROW_NUMBER. *value_expression* specifica la colonna in base al quale viene partizionato il set di risultati. Se `PARTITION BY` viene omesso, la funzione tratta tutte le righe del risultato della query impostare come un singolo gruppo. Per ulteriori informazioni, vedere [la clausola OVER &#40; Transact-SQL &#41; ](../../t-sql/queries/select-over-clause-transact-sql.md).  
  
 *order_by_clause*  
 Il `ORDER BY` clausola determina la sequenza in cui le righe vengono assegnate univoco `ROW_NUMBER` all'interno di una partizione specificata. Questo argomento è obbligatorio. Per ulteriori informazioni, vedere [la clausola OVER &#40; Transact-SQL &#41; ](../../t-sql/queries/select-over-clause-transact-sql.md).  
  
## <a name="return-types"></a>Tipi restituiti  
 **bigint**  
  
## <a name="general-remarks"></a>Osservazioni generali  
 Non c'è garanzia che le righe restituite da una query utilizzando `ROW_NUMBER()` verranno ordinati esattamente a ogni esecuzione a meno che non vengono soddisfatte le condizioni seguenti.  
  
1.  Univocità dei valori della colonna partizionata.  
  
2.  I valori del `ORDER BY` colonne siano univoche.  
  
3.  Combinazioni di valori della colonna di partizione e `ORDER BY` colonne siano univoche.  
  
 `ROW_NUMBER()`non è deterministico. Per altre informazioni, vedere [Funzioni deterministiche e non deterministiche](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-simple-examples"></a>A. Esempi semplici 

La query seguente restituisce le tabelle di quattro sistema in ordine alfabetico.

```t-sql
SELECT 
  name, recovery_model_desc
FROM sys.databases 
WHERE database_id < 5
ORDER BY name ASC;
```

 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
   
|name    |recovery_model_desc |  
|-----------  |------------ |  
|master |SIMPLE |
|model |FULL |
|msdb |SIMPLE |
|tempdb |SIMPLE |

Per aggiungere una colonna di numeri di riga davanti a ogni riga, aggiungere una colonna con il `ROW_NUMBER` funzione, in questo caso denominato `Row#`. È necessario spostare il `ORDER BY` clausola fino al `OVER` clausola.

```t-sql
SELECT 
  ROW_NUMBER() OVER(ORDER BY name ASC) AS Row#,
  name, recovery_model_desc
FROM sys.databases 
WHERE database_id < 5;
```

 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
   
|Riga # |name    |recovery_model_desc |  
|------- |-----------  |------------ |  
|1 |master |SIMPLE |
|2 |model |FULL |
|3 |msdb |SIMPLE |
|4 |tempdb |SIMPLE |

Aggiunta di un `PARTITION BY` clausola nel `recovery_model_desc` colonna, verrà riavviato la numerazione quando il `recovery_model_desc` modificato il valore. 
 
```t-sql
SELECT 
  ROW_NUMBER() OVER(PARTITION BY recovery_model_desc ORDER BY name ASC) 
    AS Row#,
  name, recovery_model_desc
FROM sys.databases WHERE database_id < 5;
```  

 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
   
|Riga # |name    |recovery_model_desc |  
|------- |-----------  |------------ |  
|1 |model |FULL |
|1 |master |SIMPLE |
|2 |msdb |SIMPLE |
|3 |tempdb |SIMPLE |


### <a name="b-returning-the-row-number-for-salespeople"></a>B. Restituzione del numero di riga per i venditori  
 Nell'esempio seguente viene calcolato un numero di riga per i venditori in [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] in base alla classificazione delle vendite dall'inizio dell'anno alla data corrente.  
  
```t-sql  
USE AdventureWorks2012;   
GO  
SELECT ROW_NUMBER() OVER(ORDER BY SalesYTD DESC) AS Row,   
    FirstName, LastName, ROUND(SalesYTD,2,1) AS "Sales YTD"   
FROM Sales.vSalesPerson  
WHERE TerritoryName IS NOT NULL AND SalesYTD <> 0;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
  
Row FirstName    LastName               SalesYTD  
--- -----------  ---------------------- -----------------  
1   Linda        Mitchell               4251368.54  
2   Jae          Pak                    4116871.22  
3   Michael      Blythe                 3763178.17  
4   Jillian      Carson                 3189418.36  
5   Ranjit       Varkey Chudukatil      3121616.32  
6   José         Saraiva                2604540.71  
7   Shu          Ito                    2458535.61  
8   Tsvi         Reiter                 2315185.61  
9   Rachel       Valdez                 1827066.71  
10  Tete         Mensa-Annan            1576562.19  
11  David        Campbell               1573012.93  
12  Garrett      Vargas                 1453719.46  
13  Lynn         Tsoflias               1421810.92  
14  Pamela       Ansman-Wolfe           1352577.13  
```  
  
### <a name="c-returning-a-subset-of-rows"></a>C. Restituzione di un subset di righe  
 Nell'esempio seguente vengono calcolati solo i numeri di riga per tutte le righe nella tabella `SalesOrderHeader` nell'ordine di `OrderDate` e vengono restituite le righe da `50` a `60` incluse.  
  
```t-sql  
USE AdventureWorks2012;  
GO  
WITH OrderedOrders AS  
(  
    SELECT SalesOrderID, OrderDate,  
    ROW_NUMBER() OVER (ORDER BY OrderDate) AS RowNumber  
    FROM Sales.SalesOrderHeader   
)   
SELECT SalesOrderID, OrderDate, RowNumber    
FROM OrderedOrders   
WHERE RowNumber BETWEEN 50 AND 60;  
```  
  
### <a name="d-using-rownumber-with-partition"></a>D. Utilizzo di ROW_NUMBER() con PARTITION  
 Nell'esempio seguente viene utilizzato l'argomento `PARTITION BY` per suddividere il set di risultati della query in base alla colonna `TerritoryName`. La clausola `ORDER BY` specificata nella clausola `OVER` ordina le righe in ogni partizione in base alla colonna `SalesYTD`. La clausola `ORDER BY` nell'istruzione `SELECT` ordina l'intero set di risultati della query in base al valore di `TerritoryName`.  
  
```t-sql  
USE AdventureWorks2012;  
GO  
SELECT FirstName, LastName, TerritoryName, ROUND(SalesYTD,2,1) AS SalesYTD,  
ROW_NUMBER() OVER(PARTITION BY TerritoryName ORDER BY SalesYTD DESC) 
  AS Row  
FROM Sales.vSalesPerson  
WHERE TerritoryName IS NOT NULL AND SalesYTD <> 0  
ORDER BY TerritoryName;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
  
FirstName  LastName             TerritoryName        SalesYTD      Row  
---------  -------------------- ------------------   ------------  ---  
Lynn       Tsoflias             Australia            1421810.92    1  
José       Saraiva              Canada               2604540.71    1  
Garrett    Vargas               Canada               1453719.46    2  
Jillian    Carson               Central              3189418.36    1  
Ranjit     Varkey Chudukatil    France               3121616.32    1  
Rachel     Valdez               Germany              1827066.71    1  
Michael    Blythe               Northeast            3763178.17    1  
Tete       Mensa-Annan          Northwest            1576562.19    1  
David      Campbell             Northwest            1573012.93    2  
Pamela     Ansman-Wolfe         Northwest            1352577.13    3  
Tsvi       Reiter               Southeast            2315185.61    1  
Linda      Mitchell             Southwest            4251368.54    1  
Shu        Ito                  Southwest            2458535.61    2  
Jae        Pak                  United Kingdom       4116871.22    1  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-returning-the-row-number-for-salespeople"></a>E. Restituzione del numero di riga per i venditori  
 Nell'esempio seguente viene restituito il `ROW_NUMBER` per i venditori in base alle rispettive quote di vendite assegnata.  
  
```t-sql  
-- Uses AdventureWorks  
  
SELECT ROW_NUMBER() OVER(ORDER BY SUM(SalesAmountQuota) DESC) 
    AS RowNumber,  
    FirstName, LastName,   
    CONVERT(varchar(13), SUM(SalesAmountQuota),1) AS SalesQuota   
FROM dbo.DimEmployee AS e  
INNER JOIN dbo.FactSalesQuota AS sq  
    ON e.EmployeeKey = sq.EmployeeKey  
WHERE e.SalesPersonFlag = 1  
GROUP BY LastName, FirstName;  
```  
  
 Set di risultati parziale:  

```  

RowNumber  FirstName  LastName            SalesQuota  
---------  ---------  ------------------  -------------  
1          Jillian    Carson              12,198,000.00  
2          Linda      Mitchell            11,786,000.00  
3          Michael    Blythe              11,162,000.00  
4          Jae        Pak                 10,514,000.00  
```

### <a name="f-using-rownumber-with-partition"></a>F. Utilizzo di ROW_NUMBER() con PARTITION  
 Nell'esempio seguente viene illustrato l'utilizzo della funzione `ROW_NUMBER` con l'argomento `PARTITION BY`. In questo modo il `ROW_NUMBER` funzione per numerare le righe in ogni partizione.  
  
```t-sql  
-- Uses AdventureWorks  
  
SELECT ROW_NUMBER() OVER(PARTITION BY SalesTerritoryKey 
        ORDER BY SUM(SalesAmountQuota) DESC) AS RowNumber,  
    LastName, SalesTerritoryKey AS Territory,  
    CONVERT(varchar(13), SUM(SalesAmountQuota),1) AS SalesQuota   
FROM dbo.DimEmployee AS e  
INNER JOIN dbo.FactSalesQuota AS sq  
    ON e.EmployeeKey = sq.EmployeeKey  
WHERE e.SalesPersonFlag = 1  
GROUP BY LastName, FirstName, SalesTerritoryKey;  
```  
  
 Set di risultati parziale:  
 
```  
 
RowNumber  LastName            Territory  SalesQuota  
---------  ------------------  ---------  -------------  
1          Campbell            1           4,025,000.00  
2          Ansman-Wolfe        1           3,551,000.00  
3          Mensa-Annan         1           2,275,000.00  
1          Blythe              2          11,162,000.00  
1          Carson              3          12,198,000.00  
1          Mitchell            4          11,786,000.00  
2          Ito                 4           7,804,000.00  
```
  
## <a name="see-also"></a>Vedere anche  
 [Numero di dimensioni &#40; Transact-SQL &#41;](../../t-sql/functions/rank-transact-sql.md)   
 [DENSE_RANK &#40; Transact-SQL &#41;](../../t-sql/functions/dense-rank-transact-sql.md)   
 [NTILE &#40; Transact-SQL &#41;](../../t-sql/functions/ntile-transact-sql.md)  
  
  



