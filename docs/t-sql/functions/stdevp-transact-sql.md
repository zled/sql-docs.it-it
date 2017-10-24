---
title: STDEVP (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STDEVP
- STDEVP_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STDEVP function [Transact-SQL]
- expressions [SQL Server], statistical standard deviation
- statistical standard deviation
ms.assetid: 29f2a906-d084-4464-abc3-4b275ed19442
caps.latest.revision: 45
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: abda0ca087c75f67e295e4ce493834f13b37e5f3
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="stdevp-transact-sql"></a>STDEVP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce la deviazione statistica standard relativa al popolamento di tutti i valori dell'espressione specificata.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
STDEVP ( [ ALL | DISTINCT ] expression )   
   OVER ( [ partition_by_clause ] order_by_clause )    
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
-- Aggregate Function Syntax   
STDEVP ( [ ALL | DISTINCT ] expression )  
  
-- Analytic Function Syntax   
STDEVP (expression) OVER ( [ partition_by_clause ] order_by_clause)  
```  
  
## <a name="arguments"></a>Argomenti  
 **ALL**  
 Applica la funzione a tutti i valori. Il valore predefinito è ALL.  
  
 DISTINCT  
 Consente di considerare ogni valore univoco.  
  
 *espressione*  
 È un valore numerico [espressione](../../t-sql/language-elements/expressions-transact-sql.md). Non è possibile utilizzare funzioni di aggregazione e sottoquery. *espressione* è un'espressione della categoria di tipi di dati numerici o numerici approssimativi esatti, fatta eccezione per il **bit** tipo di dati.  
  
 SU **(** [ *partition_by_clause* ] *order_by_clause***)**  
 *partition_by_clause* suddivide il set di risultati generato dalla clausola FROM in partizioni a cui viene applicata la funzione. Se non specificato, la funzione tratta tutte le righe del set di risultati della query come un unico gruppo. *order_by_clause* determina l'ordine logico in cui viene eseguita l'operazione. *order_by_clause* è obbligatorio. Per ulteriori informazioni, vedere [la clausola OVER &#40; Transact-SQL &#41; ](../../t-sql/queries/select-over-clause-transact-sql.md).  
  
## <a name="return-types"></a>Tipi restituiti  
 **float**  
  
## <a name="remarks"></a>Osservazioni  
 Se la funzione STDEVP viene utilizzata per tutti gli elementi di un'istruzione SELECT, ogni valore del set di risultati viene incluso nel calcolo. STDEVP può essere utilizzata solo con colonne numeriche. I valori Null vengono ignorati.  
  
 STDEVP è una funzione deterministica quando viene utilizzata senza le clausole ORDER BY e OVER. Non è deterministica quando viene specificata con le clausole ORDER BY e OVER. Per altre informazioni, vedere [Funzioni deterministiche e non deterministiche](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-stdevp"></a>R: utilizzare la funzione DEV  
 Nell'esempio seguente viene restituita la deviazione standard per il popolamento per tutti i valori dei premi di produttività nella tabella `SalesPerson` del database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
SELECT STDEVP(Bonus)  
FROM Sales.SalesPerson;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-using-stdevp"></a>B: tramite STDEVP  
 Nell'esempio seguente viene restituito il `STDEVP` dei valori di quota di vendita nella tabella `dbo.FactSalesQuota`. La prima colonna contiene la deviazione standard di tutti i valori distinct e la seconda colonna contiene la deviazione standard di tutti i valori compresi i valori duplicati.  
  
```  
-- Uses AdventureWorks  
  
SELECT STDEVP(DISTINCT SalesAmountQuota)AS Distinct_Values, STDEVP(SalesAmountQuota) AS All_Values  
FROM dbo.FactSalesQuota;SELECT STDEVP(DISTINCT Quantity)AS Distinct_Values, STDEVP(Quantity) AS All_Values  
FROM ProductInventory;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
Distinct_Values   All_Values  
----------------  ----------------  
397676.79         397226.44
```  
  
### <a name="c-using-stdevp-with-over"></a>C. Con STDEVP OVER  
 Nell'esempio seguente viene restituito il `STDEVP` dei valori di quota di vendite per ogni trimestre dell'anno di calendario. Si noti che `ORDER BY` nella clausola `OVER` ordina `STDEVP` e che `ORDER BY` dell'istruzione `SELECT` ordina il set di risultati.  
  
```  
-- Uses AdventureWorks  
  
SELECT CalendarYear AS Year, CalendarQuarter AS Quarter, SalesAmountQuota AS SalesQuota,  
       STDEVP(SalesAmountQuota) OVER (ORDER BY CalendarYear, CalendarQuarter) AS StdDeviation  
FROM dbo.FactSalesQuota  
WHERE EmployeeKey = 272 AND CalendarYear = 2002  
ORDER BY CalendarQuarter;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
Year  Quarter  SalesQuota              StdDeviation  
----  -------  ----------------------  -------------------  
2002  1         91000.0000             0.00  
2002  2        140000.0000             24500.00  
2002  3         70000.0000             29329.55  
2002  4        154000.0000             34426.55
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di aggregazione &#40; Transact-SQL &#41;](../../t-sql/functions/aggregate-functions-transact-sql.md)   
 [IN una clausola &#40; Transact-SQL &#41;](../../t-sql/queries/select-over-clause-transact-sql.md)  
  
  


