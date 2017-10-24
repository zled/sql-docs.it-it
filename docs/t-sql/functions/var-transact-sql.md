---
title: VAR (Transact-SQL) | Documenti Microsoft
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
- VAR
- VAR_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- statistical variances
- expressions [SQL Server], statistical variance
- VAR function [Transact-SQL]
ms.assetid: 71dfc339-16c8-42f9-8555-ad45400f7f9b
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 677b8eae4863b18d5e94e8c7f577d13ebfe01031
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="var-transact-sql"></a>VAR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce lo scostamento statistico di tutti i valori dell'espressione specificata. Può essere seguita dal [clausola OVER](../../t-sql/queries/select-over-clause-transact-sql.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
VAR ( [ ALL | DISTINCT ] expression )   
   OVER ( [ partition_by_clause ] order_by_clause )    
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
-- Aggregate Function Syntax   
VAR ( [ ALL | DISTINCT ] expression )  
  
-- Analytic Function Syntax  
VAR (expression) OVER ( [ partition_by_clause ] order_by_clause)  
```  
  
## <a name="arguments"></a>Argomenti  
 **ALL**  
 Applica la funzione a tutti i valori. Il valore predefinito è ALL.  
  
 DISTINCT  
 Consente di considerare ogni valore univoco.  
  
 *espressione*  
 È un [espressione](../../t-sql/language-elements/expressions-transact-sql.md) di uno, categoria del tipo di dati numerici o numerici approssimativi, ad eccezione del **bit** tipo di dati. Non è possibile utilizzare funzioni di aggregazione e sottoquery.  
  
 SU **(** [ *partition_by_clause* ] *order_by_clause***)**  
 *partition_by_clause* suddivide il set di risultati generato dalla clausola FROM in partizioni a cui viene applicata la funzione. Se non specificato, la funzione tratta tutte le righe del set di risultati della query come un unico gruppo. *order_by_clause* determina l'ordine logico in cui viene eseguita l'operazione. *order_by_clause* è obbligatorio. Per ulteriori informazioni, vedere [la clausola OVER &#40; Transact-SQL &#41; ](../../t-sql/queries/select-over-clause-transact-sql.md).  
  
## <a name="return-types"></a>Tipi restituiti  
 **float**  
  
## <a name="remarks"></a>Osservazioni  
 Se la funzione VAR viene applicata a tutte le voci di un'istruzione SELECT, ogni valore nel set di risultati viene incluso nel calcolo. VAR può essere utilizzata solo con colonne numeriche. I valori Null vengono ignorati.  
  
 VAR è una funzione deterministica quando viene utilizzata senza le clausole ORDER BY e OVER. Non è deterministica quando viene specificata con le clausole ORDER BY e OVER. Per altre informazioni, vedere [Funzioni deterministiche e non deterministiche](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-var"></a>R: utilizzando VAR  
 Nell'esempio seguente viene restituita la varianza per tutti i valori relativi ai premi di produttività nella tabella `SalesPerson` del database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
SELECT VAR(Bonus)  
FROM Sales.SalesPerson;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-using-var"></a>B: utilizzando VAR  
 L'esempio seguente restituisce la varianza statistica dei valori di quota di vendita nella tabella `dbo.FactSalesQuota`. La prima colonna contiene la varianza di tutti i valori distinct e la seconda colonna contiene la varianza di tutti i valori compresi i valori duplicati.  
  
```  
-- Uses AdventureWorks  
  
SELECT VAR(DISTINCT SalesAmountQuota)AS Distinct_Values, VAR(SalesAmountQuota) AS All_Values  
FROM dbo.FactSalesQuota;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
Distinct_Values   All_Values
----------------  ----------------
159180469909.18   158762853821.10
 ```  
  
### <a name="c-using-var-with-over"></a>C. Con VAR OVER  
 L'esempio seguente restituisce la varianza statistica dei valori di quota di vendite per ogni trimestre dell'anno di calendario. Si noti che la clausola ORDER BY nella clausola OVER Ordina la varianza statistica e la clausola ORDER BY dell'istruzione SELECT Ordina il set di risultati.  
  
```  
-- Uses AdventureWorks  
  
SELECT CalendarYear AS Year, CalendarQuarter AS Quarter, SalesAmountQuota AS SalesQuota,  
       VAR(SalesAmountQuota) OVER (ORDER BY CalendarYear, CalendarQuarter) AS Variance  
FROM dbo.FactSalesQuota  
WHERE EmployeeKey = 272 AND CalendarYear = 2002  
ORDER BY CalendarQuarter;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
Year  Quarter  SalesQuota              Variance
----  -------  ----------------------  -------------------
2002  1         91000.0000             null
2002  2        140000.0000             1200500000.00
2002  3         70000.0000             1290333333.33
2002  4        154000.0000             1580250000.00
 ```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di aggregazione &#40; Transact-SQL &#41;](../../t-sql/functions/aggregate-functions-transact-sql.md)   
 [IN una clausola &#40; Transact-SQL &#41;](../../t-sql/queries/select-over-clause-transact-sql.md)  
  
  


