---
title: LAG (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 10/20/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- LAG_TSQL
- LAG
dev_langs:
- TSQL
helpviewer_keywords:
- LAG function
- analytic functions, LAG
ms.assetid: a9a90bdb-3f80-4c97-baca-b7407bcdc7f0
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 77598feb87f6766f6c24c454dace2c138315e69b
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="lag-transact-sql"></a>LAG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Accede ai dati da una riga precedente nello stesso set di risultati senza l'utilizzo di un self-join in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. LAG fornisce l'accesso a una riga situata a una distanza fisica specificata e precedente rispetto alla riga corrente. Utilizzare questa funzione analitica in un'istruzione SELECT per confrontare valori nella riga corrente con i valori in una riga precedente.  
  
 ![Icona di collegamento argomento](../../database-engine/configure-windows/media/topic-link.gif "icona Collegamento argomento") [convenzioni della sintassi Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
LAG (scalar_expression [,offset] [,default])  
    OVER ( [ partition_by_clause ] order_by_clause )  
```  
  
## <a name="arguments"></a>Argomenti  
 *scalar_expression*  
 Valore da restituire basato sull'offset specificato. Tale valore può essere un'espressione di ogni tipo che restituisce un singolo valore scalare. *scalar_expression* non può essere una funzione analitica.  
  
 *offset*  
 Numero di righe in posizioni precedenti rispetto alla riga corrente dalla quale ottenere un valore. Se non specificato, il valore predefinito è 1. *offset* può essere una colonna, una sottoquery o un'altra espressione che restituisce un numero intero positivo o può essere convertito in modo implicito in **bigint**. *offset* non può essere un valore negativo o una funzione analitica.  
  
 *impostazione predefinita*  
 Il valore da restituire quando *scalar_expression* in *offset* è NULL. Se non viene specificato un valore predefinito, viene restituito NULL. *predefinito* può essere una colonna, una sottoquery o un'altra espressione, ma non può essere una funzione analitica. *predefinito* deve essere di tipo compatibile con *scalar_expression*.  
  
 SU **(** [ *partition_by_clause* ] *order_by_clause***)**  
 *partition_by_clause* suddivide il set di risultati generato dalla clausola FROM in partizioni a cui viene applicata la funzione. Se non specificato, la funzione tratta tutte le righe del set di risultati della query come un unico gruppo. *order_by_clause* determina l'ordine dei dati prima che venga applicata la funzione. Se *partition_by_clause* viene specificata, determina l'ordine dei dati nella partizione. Il *order_by_clause* è obbligatorio. Per ulteriori informazioni, vedere [la clausola OVER &#40; Transact-SQL &#41; ](../../t-sql/queries/select-over-clause-transact-sql.md).  
  
## <a name="return-types"></a>Tipi restituiti  
 Il tipo di dati dell'oggetto specificato *scalar_expression*. Se viene restituito NULL *scalar_expression* ammette valori null o *predefinito* è impostato su NULL.  
  
## <a name="general-remarks"></a>Osservazioni generali  
 LAG è non deterministico. Per altre informazioni, vedere [Funzioni deterministiche e non deterministiche](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-compare-values-between-years"></a>A. Confronto di valori tra anni  
 Nell'esempio seguente viene utilizzata la funzione LAG per restituire la differenza nelle quote vendite per un dipendente specifico negli anni precedenti. Si noti che poiché non è presente alcun valore di ritardo disponibile per la prima riga, viene restituita l'impostazione predefinita zero (0).  
  
```  
USE AdventureWorks2012;  
GO  
SELECT BusinessEntityID, YEAR(QuotaDate) AS SalesYear, SalesQuota AS CurrentQuota,   
       LAG(SalesQuota, 1,0) OVER (ORDER BY YEAR(QuotaDate)) AS PreviousQuota  
FROM Sales.SalesPersonQuotaHistory  
WHERE BusinessEntityID = 275 and YEAR(QuotaDate) IN ('2005','2006');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
  
BusinessEntityID SalesYear   CurrentQuota          PreviousQuota  
---------------- ----------- --------------------- ---------------------  
275              2005        367000.00             0.00  
275              2005        556000.00             367000.00  
275              2006        502000.00             556000.00  
275              2006        550000.00             502000.00  
275              2006        1429000.00            550000.00  
275              2006        1324000.00            1429000.00  
  
```  
  
### <a name="b-compare-values-within-partitions"></a>B. Confronto di valori all'interno di partizioni  
 Nell'esempio seguente viene utilizzata la funzione LAG per confrontare le vendite dei dipendenti a partire dall'inizio dell'anno. La clausola PARTITION BY è specificata per dividere le righe nel set di risultati in base al territorio di vendita. La funzione LAG viene applicata a ogni singola partizione e il calcolo viene riavviato per ogni partizione. La clausola ORDER BY specificata nella clausola OVER ordina le righe in ogni partizione. La clausola ORDER BY nell'istruzione SELECT ordina le righe nell'intero set di risultati. Si noti che poiché non è presente alcun valore di ritardo per la prima riga di ogni partizione, viene restituita l'impostazione predefinita zero (0).  
  
```  
USE AdventureWorks2012;  
GO  
SELECT TerritoryName, BusinessEntityID, SalesYTD,   
       LAG (SalesYTD, 1, 0) OVER (PARTITION BY TerritoryName ORDER BY SalesYTD DESC) AS PrevRepSales  
FROM Sales.vSalesPerson  
WHERE TerritoryName IN (N'Northwest', N'Canada')   
ORDER BY TerritoryName;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
  
TerritoryName            BusinessEntityID SalesYTD              PrevRepSales  
-----------------------  ---------------- --------------------- ---------------------  
Canada                   282              2604540.7172          0.00  
Canada                   278              1453719.4653          2604540.7172  
Northwest                284              1576562.1966          0.00  
Northwest                283              1573012.9383          1576562.1966  
Northwest                280              1352577.1325          1573012.9383  
  
```  
  
### <a name="c-specifying-arbitrary-expressions"></a>C. Specifica di espressioni arbitrarie  
 Nell'esempio seguente viene illustrata la specifica di una varietà di espressioni arbitrarie nella sintassi della funzione LAG.  
  
```  
CREATE TABLE T (a int, b int, c int);   
GO  
INSERT INTO T VALUES (1, 1, -3), (2, 2, 4), (3, 1, NULL), (4, 3, 1), (5, 2, NULL), (6, 1, 5);   
  
SELECT b, c,   
    LAG(2*c, b*(SELECT MIN(b) FROM T), -c/2.0) OVER (ORDER BY a) AS i  
FROM T;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
b           c           i  
----------- ----------- -----------  
1           -3          1  
2           4           -2  
1           NULL        8  
3           1           -6  
2           NULL        NULL  
1           5           NULL  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-compare-values-between-quarters"></a>Unità d: confrontare valori tra trimestri  
 L'esempio seguente illustra la funzione LAG. La query utilizza la funzione LAG per restituire la differenza nelle quote vendite per un dipendente specifico negli trimestri di calendario precedente. Si noti che poiché non è presente alcun valore di ritardo disponibile per la prima riga, viene restituita l'impostazione predefinita zero (0).  
  
```  
-- Uses AdventureWorks  
  
SELECT CalendarYear, CalendarQuarter, SalesAmountQuota AS SalesQuota,  
       LAG(SalesAmountQuota,1,0) OVER (ORDER BY CalendarYear, CalendarQuarter) AS PrevQuota,  
       SalesAmountQuota - LAG(SalesAmountQuota,1,0) OVER (ORDER BY CalendarYear, CalendarQuarter) AS Diff  
FROM dbo.FactSalesQuota  
WHERE EmployeeKey = 272 AND CalendarYear IN (2001, 2002)  
ORDER BY CalendarYear, CalendarQuarter;   
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Year Quarter  SalesQuota  PrevQuota  Diff`  
  
 `---- -------  ----------  ---------  -------------`  
  
 `2001 3        28000.0000      0.0000   28000.0000`  
  
 `2001 4         7000.0000  28000.0000  -21000.0000`  
  
 `2001 1        91000.0000   7000.0000   84000.0000`  
  
 `2002 2       140000.0000  91000.0000   49000.0000`  
  
 `2002 3         7000.0000 140000.0000  -70000.0000`  
  
 `2002 4       154000.0000   7000.0000   84000.0000`  
  
## <a name="see-also"></a>Vedere anche  
 [LEAD &#40; Transact-SQL &#41;](../../t-sql/functions/lead-transact-sql.md)  
  
  



