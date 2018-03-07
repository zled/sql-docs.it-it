---
title: RAGGRUPPAMENTO (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GROUPING
- GROUPING_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- null values [SQL Server], GROUPING function
- grouping columns
- ROLLUP operator
- GROUP BY clause, GROUPING function
- GROUPING function
- CUBE operator
ms.assetid: 4efa3868-1fc4-4626-8fb1-e863cc03e422
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: cb9c9e7f4e5fe4a82c6f7a451614fde82e730e08
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="grouping-transact-sql"></a>GROUPING (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Indica se un'espressione della colonna specificata in un elenco GROUP BY è aggregata. GROUPING restituisce 1 per le espressioni aggregate o 0 per le espressioni non aggregate nel set di risultati. RAGGRUPPAMENTO può essere utilizzato solo in SELECT \<selezionare > elencare, HAVING e ORDER BY clausole quando GROUP BY è specificato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
GROUPING ( <column_expression> )  
```  
  
## <a name="arguments"></a>Argomenti  
 \<column_expression >  
 È una colonna o un'espressione che contiene una colonna in un [GROUP BY](../../t-sql/queries/select-group-by-transact-sql.md) clausola.  
  
## <a name="return-types"></a>Tipi restituiti  
 **tinyint**  
  
## <a name="remarks"></a>Osservazioni  
 GROUPING viene utilizzato per distinguere i valori Null restituiti da ROLLUP, CUBE o GROUPING SETS dai valori Null standard. Il risultato NULL restituito da un'operazione ROLLUP, CUBE o GROUPING SETS rappresenta un utilizzo particolare dei valori NULL. Funge infatti da segnaposto di colonna nel set di risultati e corrisponde a "tutti".  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono raggruppati gli importi di `SalesQuota` e aggregati gli importi di `SaleYTD` nel database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. La funzione `GROUPING` viene applicata alla colonna `SalesQuota`.  
  
```  
SELECT SalesQuota, SUM(SalesYTD) 'TotalSalesYTD', GROUPING(SalesQuota) AS 'Grouping'  
FROM Sales.SalesPerson  
GROUP BY SalesQuota WITH ROLLUP;  
GO  
```  
  
 Il set di risultati include due valori Null per `SalesQuota`. Il primo valore `NULL` rappresenta il gruppo di valori Null che derivano dalla colonna della tabella, il secondo valore `NULL` è incluso nella riga di riepilogo aggiunta dall'operazione ROLLUP. La riga di riepilogo Mostra il `TotalSalesYTD` quantità per tutti i `SalesQuota` gruppi ed è indicato da `1` nel `Grouping` colonna.  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 SalesQuota     TotalSalesYTD       Grouping  
------------   -----------------   --------  
NULL           1533087.5999          0  
250000.00      33461260.59           0  
300000.00      9299677.9445          0  
NULL           44294026.1344         1  

(4 row(s) affected)
```  
  
## <a name="see-also"></a>Vedere anche  
 [GROUPING_ID &#40; Transact-SQL &#41;](../../t-sql/functions/grouping-id-transact-sql.md)   
 [Clausola GROUP BY &#40; Transact-SQL &#41;](../../t-sql/queries/select-group-by-transact-sql.md)  
  
  
