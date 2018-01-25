---
title: Le sottoquery (Azure SQL Data Warehouse, Parallel Data Warehouse) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e8ebd60-1936-48c9-b2b9-e099c8269fcf
caps.latest.revision: "7"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5b30ff820d9a9003a1832c8b4226adf20072fceb
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="subqueries-azure-sql-data-warehouse-parallel-data-warehouse"></a>Sottoquery (Azure SQL Data Warehouse, Parallel Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  In questo argomento vengono forniti alcuni esempi di utilizzo di sottoquery in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
 Per l'istruzione SELECT, vedere [SELECT &#40; Transact-SQL &#41;](../../t-sql/queries/select-transact-sql.md)  
  
## <a name="contents"></a>Sommario  
  
-   [Nozioni di base](#Basics)  
  
-   [Esempi: SQL Data Warehouse e Parallel Data Warehouse](#Examples)  
  
##  <a name="Basics"></a> Basics  
 Sottoquery  
 Una sottoquery è una query nidificata in un'istruzione SELECT, INSERT, UPDATE o DELETE o in un'altra sottoquery. Questo è l'acronimo di una query interna o un'istruzione select interna.  
  
 Query esterna  
 L'istruzione che contiene la sottoquery. Si tratta inoltre di un'istruzione select esterna.  
  
 Sottoquery correlata  
 Una sottoquery che fa riferimento a una tabella nella query esterna.  
  
##  <a name="Examples"></a>Esempi: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 In questa sezione vengono forniti esempi di sottoquery è supportato in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
### <a name="a-top-and-order-by-in-a-subquery"></a>A. TOP e ORDER BY in una sottoquery  
  
```  
SELECT * FROM tblA  
WHERE col1 IN  
    (SELECT TOP 100 col1 FROM tblB ORDER BY col1);  
  
```  
  
### <a name="b-having-clause-with-a-correlated-subquery"></a>B. HAVING (clausola) con una sottoquery correlata  
  
```  
SELECT dm.EmployeeKey, dm.FirstName, dm.LastName   
FROM DimEmployee AS dm   
GROUP BY dm.EmployeeKey, dm.FirstName, dm.LastName  
HAVING 5000 <=   
(SELECT sum(OrderQuantity)  
FROM FactResellerSales AS frs  
WHERE dm.EmployeeKey = frs.EmployeeKey)  
ORDER BY EmployeeKey;  
  
```  
  
### <a name="c-correlated-subqueries-with-analytics"></a>C. Sottoquery correlate con analitica  
  
```  
SELECT * FROM ReplA AS A   
WHERE A.ID IN   
    (SELECT sum(B.ID2) OVER() FROM ReplB AS B WHERE A.ID2 = B.ID);  
```  
  
### <a name="d-correlated-union-statements-in-a-subquery"></a>D. Istruzioni unione correlate in una sottoquery  
  
```  
SELECT * FROM RA   
WHERE EXISTS   
    (SELECT 1 FROM RB WHERE RB.b1 = RA.a1   
     UNION ALL SELECT 1 FROM RC);  
```  
  
### <a name="e-join-predicates-in-a-subquery"></a>E. I predicati di join in una sottoquery  
  
```  
SELECT * FROM RA INNER JOIN RB   
    ON RA.a1 = (SELECT COUNT(*) FROM RC);  
```  
  
### <a name="f-correlated-join-predicates-in-a-subquery"></a>F. Predicati di join correlati in una sottoquery  
  
```  
SELECT * FROM RA   
    WHERE RA.a2 IN   
    (SELECT 1 FROM RB INNER JOIN RC ON RA.a1=RB.b1+RC.c1);  
```  
  
### <a name="g-correlated-subselects-as-data-sources"></a>G. Sub-SELECT correlate come origini dati  
  
```  
SELECT * FROM RA   
    WHERE 3 = (SELECT COUNT(*)   
        FROM (SELECT b1 FROM RB WHERE RB.b1 = RA.a1) X);  
```  
  
### <a name="h-correlated-subqueries-in-the-data-values--used-with-aggregates"></a>H. Sottoquery correlate nei valori dei dati utilizzati con funzioni di aggregazione  
  
```  
SELECT Rb.b1, (SELECT RA.a1 FROM RA WHERE RB.b1 = RA.a1) FROM RB GROUP BY RB.b1;  
```  
  
### <a name="i-using-in-with-a-correlated-subquery"></a>I. Utilizzo con una sottoquery correlata  
 Nell'esempio seguente viene utilizzata la parola chiave `IN` in una sottoquery correlata o ripetuta. È una query che dipende dalla query esterna. La query interna viene eseguita ripetutamente, una volta per ogni riga che può essere selezionata dalla query esterna. Questa query recupera un'istanza del `EmployeeKey` oltre a nome e cognome di ogni dipendente per il quale il `OrderQuantity` nel `FactResellerSales` tabella è `5` e per cui i numeri di identificazione del dipendente corrispondano nel `DimEmployee` e `FactResellerSales` tabelle.  
  
```  
SELECT DISTINCT dm.EmployeeKey, dm.FirstName, dm.LastName   
FROM DimEmployee AS dm   
WHERE 5 IN   
    (SELECT OrderQuantity  
    FROM FactResellerSales AS frs  
    WHERE dm.EmployeeKey = frs.EmployeeKey)  
ORDER BY EmployeeKey;  
```  
  
### <a name="j-using-exists-versus-in-with-a-subquery"></a>J. L'utilizzo di EXISTS e con una sottoquery  
 Nell'esempio seguente vengono illustrate query semanticamente equivalenti per illustrare la differenza tra l'utilizzo di `EXISTS` (parola chiave) e `IN` (parola chiave). Entrambi sono esempi di sottoquery che recupera un'istanza di ogni nome di prodotto per i quali è la sottocategoria di prodotto `Road Bikes`. `ProductSubcategoryKey`corrispondente tra il `DimProduct` e `DimProductSubcategory` tabelle.  
  
```  
SELECT DISTINCT EnglishProductName  
FROM DimProduct AS dp   
WHERE EXISTS  
    (SELECT *  
     FROM DimProductSubcategory AS dps   
     WHERE dp.ProductSubcategoryKey = dps.ProductSubcategoryKey  
           AND dps.EnglishProductSubcategoryName = 'Road Bikes')  
ORDER BY EnglishProductName;  
```  
  
 Oppure  
  
```  
SELECT DISTINCT EnglishProductName  
FROM DimProduct AS dp   
WHERE dp.ProductSubcategoryKey IN  
    (SELECT ProductSubcategoryKey  
     FROM DimProductSubcategory   
     WHERE EnglishProductSubcategoryName = 'Road Bikes')  
ORDER BY EnglishProductName;  
```  
  
### <a name="k-using-multiple-correlated-subqueries"></a>K. Utilizzo di più sottoquery correlate  
 In questo esempio vengono utilizzate due sottoquery correlate per trovare i nomi dei dipendenti che hanno venduto un determinato prodotto.  
  
```  
SELECT DISTINCT LastName, FirstName, e.EmployeeKey  
FROM DimEmployee e JOIN FactResellerSales s ON e.EmployeeKey = s.EmployeeKey  
WHERE ProductKey IN  
(SELECT ProductKey FROM DimProduct WHERE ProductSubcategoryKey IN  
(SELECT ProductSubcategoryKey FROM DimProductSubcategory   
 WHERE EnglishProductSubcategoryName LIKE '%Bikes'))  
ORDER BY LastName  
;  
  
```  
  
  
