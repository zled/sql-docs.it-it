---
title: IN (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/29/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IN_TSQL
- IN
dev_langs:
- TSQL
helpviewer_keywords:
- values [SQL Server], matching
- NOT IN keyword
- 8623 (Database Engine error)
- matching values in subquery or list [SQL Server]
- IN keyword
- 8632 (Database Engine error)
ms.assetid: 4419de73-96b1-4dfe-8500-f4507915db04
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 70b186107966791e29ccb76ea9c310724b76e3b6
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="in-transact-sql"></a>IN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Determina se il valore specificato corrisponde a un valore in una sottoquery o in un elenco.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
test_expression [ NOT ] IN   
    ( subquery | expression [ ,...n ]  
    )   
```  
  
## <a name="arguments"></a>Argomenti  
 *test_expression*  
 È qualsiasi [espressione](../../t-sql/language-elements/expressions-transact-sql.md).  
  
 *sottoquery*  
 Sottoquery che include un set di risultati di una colonna. Questa colonna deve avere gli stessi dati di tipo come *test_expression*.  
  
 *espressione*[ **,**... *n* ]  
 Elenco di espressioni in cui individuare una corrispondenza. Tutte le espressioni devono essere dello stesso tipo *test_expression*.  
  
## <a name="result-types"></a>Tipi restituiti  
 **Boolean**  
  
## <a name="result-value"></a>Valore restituito  
 Se il valore di *test_expression* è uguale a qualsiasi valore restituito da *sottoquery* o è uguale a qualsiasi *espressione* dall'elenco delimitato da virgole, il valore di risultato è TRUE. in caso contrario, il valore del risultato è FALSE.  
  
 Utilizzo di NOT IN Nega la *sottoquery* valore o *espressione*.  
  
> [!CAUTION]  
>  Qualsiasi valore null restituito da *sottoquery* o *espressione* che vengono confrontati con *test_expression* utilizzando IN o NOT IN restituisce UNKNOWN. L'utilizzo di valori Null insieme a IN o NOT IN può generare risultati imprevisti.  
  
## <a name="remarks"></a>Osservazioni  
 Inclusi in modo esplicito un numero molto elevato di valori (molte migliaia di valori separati da virgole) all'interno delle parentesi, in una clausola IN grado di utilizzare le risorse e restituiti errori 8623 o 8632. Per risolvere questo problema, archiviare gli elementi nell'elenco in una tabella e utilizzare una sottoquery SELECT all'interno di una clausola IN.  
  
 Errore 8623:  
  
 `The query processor ran out of internal resources and could not produce a query plan. This is a rare event and only expected for extremely complex queries or queries that reference a very large number of tables or partitions. Please simplify the query. If you believe you have received this message in error, contact Customer Support Services for more information.`  
  
 Errore 8632:  
  
 `Internal error: An expression services limit has been reached. Please look for potentially complex expressions in your query, and try to simplify them.`  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-comparing-or-and-in"></a>A. Confronto di OR e IN  
 Nell'esempio seguente viene selezionato un elenco di nomi dei dipendenti con il titolo di Design Engineer, Tool Designer o Marketing Assistant.  
  
```  
-- Uses AdventureWorks  
  
SELECT p.FirstName, p.LastName, e.JobTitle  
FROM Person.Person AS p  
JOIN HumanResources.Employee AS e  
    ON p.BusinessEntityID = e.BusinessEntityID  
WHERE e.JobTitle = 'Design Engineer'   
   OR e.JobTitle = 'Tool Designer'   
   OR e.JobTitle = 'Marketing Assistant';  
GO  
```  
  
 Gli stessi risultati vengono tuttavia recuperati tramite IN.  
  
```  
-- Uses AdventureWorks  
  
SELECT p.FirstName, p.LastName, e.JobTitle  
FROM Person.Person AS p  
JOIN HumanResources.Employee AS e  
    ON p.BusinessEntityID = e.BusinessEntityID  
WHERE e.JobTitle IN ('Design Engineer', 'Tool Designer', 'Marketing Assistant');  
GO  
```  
  
 Set di risultati per entrambe le query.  
  
```  
FirstName   LastName      Title  
---------   ---------   ---------------------  
Sharon      Salavaria   Design Engineer                                     
Gail        Erickson    Design Engineer                                     
Jossef      Goldberg    Design Engineer                                     
Janice      Galvin      Tool Designer                                       
Thierry     D'Hers      Tool Designer                                       
Wanida      Benshoof    Marketing Assistant                                 
Kevin       Brown       Marketing Assistant                                 
Mary        Dempsey     Marketing Assistant                                 
  
(8 row(s) affected)  
```  
  
### <a name="b-using-in-with-a-subquery"></a>B. Utilizzo di IN con una sottoquery  
 Nell'esempio seguente consente di trovare tutti gli ID per i venditori nel `SalesPerson` tabella per i dipendenti che dispongono di una quota di vendite uguale a €250.000 per l'anno e quindi seleziona il `Employee` tabella i nomi di tutti i dipendenti in cui `EmployeeID` che corrispondono il risultante dal `SELECT` sottoquery.  
  
```  
-- Uses AdventureWorks  
  
SELECT p.FirstName, p.LastName  
FROM Person.Person AS p  
    JOIN Sales.SalesPerson AS sp  
    ON p.BusinessEntityID = sp.BusinessEntityID  
WHERE p.BusinessEntityID IN  
   (SELECT BusinessEntityID  
   FROM Sales.SalesPerson  
   WHERE SalesQuota > 250000);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
FirstName   LastName                                             
---------   --------   
Tsvi         Reiter                                              
Michael      Blythe                                              
Tete         Mensa-Annan                                         
  
(3 row(s) affected)  
```  
  
### <a name="c-using-not-in-with-a-subquery"></a>C. Utilizzo di NOT IN con una sottoquery  
 Nell'esempio seguente vengono recuperati tutti i venditori la cui quota di vendita è inferiore o uguale a €250.000. `NOT IN` restituisce i venditori che non corrispondono agli elementi nell'elenco dei valori.  
  
```  
-- Uses AdventureWorks  
  
SELECT p.FirstName, p.LastName  
FROM Person.Person AS p  
    JOIN Sales.SalesPerson AS sp  
    ON p.BusinessEntityID = sp.BusinessEntityID  
WHERE p.BusinessEntityID NOT IN  
   (SELECT BusinessEntityID  
   FROM Sales.SalesPerson  
   WHERE SalesQuota > 250000);  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-using-in-and-not-in"></a>D. Utilizzo IN e non IN  
 Nell'esempio seguente consente di trovare tutte le voci di `FactInternetSales` tabella che corrispondono `SalesReasonKey` valori il `DimSalesReason` tabella.  
  
```  
-- Uses AdventureWorks  
  
SELECT * FROM FactInternetSalesReason   
WHERE SalesReasonKey   
IN (SELECT SalesReasonKey FROM DimSalesReason);   
```  
  
 Nell'esempio seguente consente di trovare tutte le voci la `FactInternetSalesReason` tabella che non corrispondono `SalesReasonKey` i valori di `DimSalesReason` tabella.  
  
```  
-- Uses AdventureWorks  
  
SELECT * FROM FactInternetSalesReason   
WHERE SalesReasonKey   
NOT IN (SELECT SalesReasonKey FROM DimSalesReason);  
```  
  
### <a name="e-using-in-with-an-expression-list"></a>E. Utilizzo con un elenco di espressioni  
 Nell'esempio seguente consente di trovare tutti gli ID per i venditori nel `DimEmployee` dipendenti che dispongono di un primo nome che è una tabella `Mike` o `Michael`.  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName  
FROM DimEmployee  
WHERE FirstName IN ('Mike', 'Michael');  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CASE &#40; Transact-SQL &#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [Espressioni &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Funzioni predefinite &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [Operatori &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [IN &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)   
 [Tutti i &#40; Transact-SQL &#41;](../../t-sql/language-elements/all-transact-sql.md)   
 [ALCUNI &#124; I &#40; Transact-SQL &#41;](../../t-sql/language-elements/some-any-transact-sql.md)  
  
  




