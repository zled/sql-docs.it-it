---
title: IN (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- WHERE_TSQL
- WHERE
dev_langs:
- TSQL
helpviewer_keywords:
- retrieving rows
- clauses [SQL Server], WHERE
- WHERE clause, about WHERE clause
- row retrieval [SQL Server], WHERE clause
- WHERE clause
ms.assetid: a8430421-7bce-4fab-a2d2-56c00a3c6fa4
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5835510f37f52d57d2c23918a30dde10e7496a5d
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="where-transact-sql"></a>WHERE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Specifica la condizione di ricerca che deve essere soddisfatta dalle righe restituite da una query.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
[ WHERE <search_condition> ]  
```  
  
## <a name="arguments"></a>Argomenti  
\<*search_condition* > definisce la condizione deve essere soddisfatta per le righe da restituire. Non sono previsti limiti per il numero di predicati che è possibile includere in una condizione di ricerca. Per ulteriori informazioni sulle condizioni di ricerca e predicati, vedere [condizione di ricerca &#40; Transact-SQL &#41; ](../../t-sql/queries/search-condition-transact-sql.md).  
  
## <a name="examples"></a>Esempi  
 Negli esempi seguenti viene illustrato come utilizzare alcune condizioni di ricerca comuni nella clausola `WHERE`.  
  
### <a name="a-finding-a-row-by-using-a-simple-equality"></a>A. Ricerca di una riga tramite una semplice uguaglianza  
  
```  
USE AdventureWorks2012  
GO  
SELECT ProductID, Name  
FROM Production.Product  
WHERE Name = 'Blade' ;  
GO  
```  
  
### <a name="b-finding-rows-that-contain-a-value-as-a-part-of-a-string"></a>B. Ricerca di righe che contengono un valore come parte di una stringa  
  
```  
SELECT ProductID, Name, Color  
FROM Production.Product  
WHERE Name LIKE ('%Frame%');  
GO  
```  
  
### <a name="c-finding-rows-by-using-a-comparison-operator"></a>C. Ricerca di righe tramite un operatore di confronto  
  
```  
SELECT ProductID, Name  
FROM Production.Product  
WHERE ProductID <= 12 ;  
GO  
```  
  
### <a name="d-finding-rows-that-meet-any-of-three-conditions"></a>D. Ricerca di righe che soddisfano una di tre condizioni  
  
```  
SELECT ProductID, Name  
FROM Production.Product  
WHERE ProductID = 2  
OR ProductID = 4   
OR Name = 'Spokes' ;  
GO  
```  
  
### <a name="e-finding-rows-that-must-meet-several-conditions"></a>E. Ricerca di righe che devono soddisfare diverse condizioni  
  
```  
SELECT ProductID, Name, Color  
FROM Production.Product  
WHERE Name LIKE ('%Frame%')  
AND Name LIKE ('HL%')  
AND Color = 'Red' ;  
GO  
```  
  
### <a name="f-finding-rows-that-are-in-a-list-of-values"></a>F. Ricerca di righe incluse in un elenco di valori  
  
```  
SELECT ProductID, Name, Color  
FROM Production.Product  
WHERE Name IN ('Blade', 'Crown Race', 'Spokes');  
GO  
```  
  
### <a name="g-finding-rows-that-have-a-value-between-two-values"></a>G. Ricerca di righe con un valore compreso tra due valori  
  
```  
SELECT ProductID, Name, Color  
FROM Production.Product  
WHERE ProductID BETWEEN 725 AND 734;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Negli esempi seguenti viene illustrato come utilizzare alcune condizioni di ricerca comuni nella clausola `WHERE`.  
  
### <a name="h-finding-a-row-by-using-a-simple-equality"></a>H. Ricerca di una riga tramite una semplice uguaglianza  
  
```  
-- Uses AdventureWorks  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE LastName = 'Smith' ;  
```  
  
### <a name="i-finding-rows-that-contain-a-value-as-part-of-a-string"></a>I. Ricerca di righe che contengono un valore come parte di una stringa  
  
```  
-- Uses AdventureWorks  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE LastName LIKE ('%Smi%');  
```  
  
### <a name="j-finding-rows-by-using-a-comparison-operator"></a>J. Ricerca di righe tramite un operatore di confronto  
  
```  
-- Uses AdventureWorks  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE EmployeeKey  <= 500;  
```  
  
### <a name="k-finding-rows-that-meet-any-of-three-conditions"></a>K. Ricerca di righe che soddisfano una di tre condizioni  
  
```  
-- Uses AdventureWorks  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE EmployeeKey = 1 OR EmployeeKey = 8 OR EmployeeKey = 12;  
```  
  
### <a name="l-finding-rows-that-must-meet-several-conditions"></a>L. Ricerca di righe che devono soddisfare diverse condizioni  
  
```  
-- Uses AdventureWorks  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE EmployeeKey <= 500 AND LastName LIKE '%Smi%' AND FirstName LIKE '%A%';  
```  
  
### <a name="m-finding-rows-that-are-in-a-list-of-values"></a>M. Ricerca di righe incluse in un elenco di valori  
  
```  
-- Uses AdventureWorks  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE LastName IN ('Smith', 'Godfrey', 'Johnson');  
```  
  
### <a name="n-finding-rows-that-have-a-value-between-two-values"></a>N. Ricerca di righe con un valore compreso tra due valori  
  
```  
-- Uses AdventureWorks  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE EmployeeKey Between 100 AND 200;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [Predicati &#40; Transact-SQL &#41;](~/t-sql/queries/predicates.md)   
 [Condizione di ricerca &#40; Transact-SQL &#41;](../../t-sql/queries/search-condition-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)   
 [MERGE &#40;Transact-SQL&#41;](../../t-sql/statements/merge-transact-sql.md)  
  
  



