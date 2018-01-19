---
title: UNION (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- UNION
- UNION_TSQL
dev_langs: TSQL
helpviewer_keywords:
- UNION queries
- combining query results
- UNION operator [SQL Server]
ms.assetid: 607c296f-8a6a-49bc-975a-b8d0c0914df7
caps.latest.revision: "34"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 329048d4a4f520612ce62bcf6764fa438bcbbe15
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="set-operators---union-transact-sql"></a>Set - operatori UNION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Combina i risultati di due o più query in un singolo set di risultati che include tutte le righe delle query combinate. L'operazione UNION è diversa dall'utilizzo di join che combinano le colonne di due tabelle.  
  
 Di seguito sono riportate le regole di base per la combinazione dei set di risultati di due query tramite l'istruzione UNION:  
  
-   Tutte le query devono includere lo stesso numero di colonne nello stesso ordine.  
  
-   I tipi di dati devono essere compatibili.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
    { <query_specification> | ( <query_expression> ) }   
  UNION [ ALL ]   
  <query_specification | ( <query_expression> )   
 [ UNION [ ALL ] <query_specification> | ( <query_expression> )   
    [ ...n ] ]   
```  
  
## <a name="arguments"></a>Argomenti  
\<query_specification > | ( \<query_expression >) è una specifica di query o espressione di query che restituisce i dati da combinare con i dati da un'altra query specifica o espressione di query. Le definizioni delle colonne di un'operazione UNION non devono essere necessariamente identiche. È necessario tuttavia che siano compatibili tramite una conversione implicita. Se sono diversi tipi di dati, il tipo di dati risultante viene determinato in base alle regole per [precedenza dei tipi di dati](../../t-sql/data-types/data-type-precedence-transact-sql.md). Se i tipi sono gli stessi ma la precisione, la scala o la lunghezza è diversa, il risultato viene determinato in base alle stesse regole previste per la combinazione di espressioni. Per altre informazioni, vedere [Precisione, scala e lunghezza &#40;Transact-SQL&#41;](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
 Colonne di **xml** tipo di dati deve essere equivalente. Tutte le colonne devono essere tipizzate in un XML Schema oppure senza tipo. In caso di colonne tipizzate, esse devono essere tipizzate nella stessa raccolta di XML Schema.  
  
 UNION  
 Specifica che più set di risultati devono essere combinati e restituiti come singolo set di risultati.  
  
 ALL  
 Incorpora tutte le righe nei risultati, compresi i duplicati. Se viene omesso, le righe duplicate vengono rimosse.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-a-simple-union"></a>A. Utilizzo di un semplice operatore UNION  
 Nell'esempio seguente il set di risultati include il contenuto delle colonne `ProductModelID` e `Name` di entrambe le tabelle `ProductModel` e `Gloves`.  
  
```  
-- Uses AdventureWorks  
  
IF OBJECT_ID ('dbo.Gloves', 'U') IS NOT NULL  
DROP TABLE dbo.Gloves;  
GO  
-- Create Gloves table.  
SELECT ProductModelID, Name  
INTO dbo.Gloves  
FROM Production.ProductModel  
WHERE ProductModelID IN (3, 4);  
GO  
  
-- Here is the simple union.  
-- Uses AdventureWorks  
  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID NOT IN (3, 4)  
UNION  
SELECT ProductModelID, Name  
FROM dbo.Gloves  
ORDER BY Name;  
GO  
```  
  
### <a name="b-using-select-into-with-union"></a>B. Utilizzo di SELECT INTO con UNION  
 Nell'esempio seguente la clausola `INTO` nella seconda istruzione `SELECT` specifica che la tabella `ProductResults` contiene il set di risultati finale ottenuto con l'unione delle colonne designate delle tabelle `ProductModel` e `Gloves`. Si noti che la tabella `Gloves` viene creata nella prima istruzione `SELECT`.  
  
```  
-- Uses AdventureWorks  
  
IF OBJECT_ID ('dbo.ProductResults', 'U') IS NOT NULL  
DROP TABLE dbo.ProductResults;  
GO  
IF OBJECT_ID ('dbo.Gloves', 'U') IS NOT NULL  
DROP TABLE dbo.Gloves;  
GO  
-- Create Gloves table.  
SELECT ProductModelID, Name  
INTO dbo.Gloves  
FROM Production.ProductModel  
WHERE ProductModelID IN (3, 4);  
GO  
  
-- Uses AdventureWorks  
  
SELECT ProductModelID, Name  
INTO dbo.ProductResults  
FROM Production.ProductModel  
WHERE ProductModelID NOT IN (3, 4)  
UNION  
SELECT ProductModelID, Name  
FROM dbo.Gloves;  
GO  
  
SELECT ProductModelID, Name   
FROM dbo.ProductResults;  
  
```  
  
### <a name="c-using-union-of-two-select-statements-with-order-by"></a>C. Utilizzo dell'operatore UNION in due istruzioni SELECT con la clausola ORDER BY  
 L'ordine di alcuni parametri utilizzati con la clausola UNION è importante. Nell'esempio seguente vengono illustrati l'utilizzo errato e quello corretto di `UNION` in due istruzioni `SELECT` in cui una colonna deve essere rinominata nell'output.  
  
```  
-- Uses AdventureWorks  
  
IF OBJECT_ID ('dbo.Gloves', 'U') IS NOT NULL  
DROP TABLE dbo.Gloves;  
GO  
-- Create Gloves table.  
SELECT ProductModelID, Name  
INTO dbo.Gloves  
FROM Production.ProductModel  
WHERE ProductModelID IN (3, 4);  
GO  
  
/* INCORRECT */  
-- Uses AdventureWorks  
  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID NOT IN (3, 4)  
ORDER BY Name  
UNION  
SELECT ProductModelID, Name  
FROM dbo.Gloves;  
GO  
  
/* CORRECT */  
-- Uses AdventureWorks  
  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID NOT IN (3, 4)  
UNION  
SELECT ProductModelID, Name  
FROM dbo.Gloves  
ORDER BY Name;  
GO  
  
```  
  
### <a name="d-using-union-of-three-select-statements-to-show-the-effects-of-all-and-parentheses"></a>D. Utilizzo dell'operatore UNION in tre istruzioni SELECT per illustrare gli effetti dell'opzione ALL e delle parentesi  
 Negli esempi seguenti viene utilizzato l'operatore `UNION` per combinare i risultati di tre tabelle contenenti 5 righe di dati identiche. Nel primo esempio viene utilizzato `UNION ALL` per mostrare i record duplicati e vengono restituite tutte le 15 righe. Nel secondo esempio l'operatore `UNION` viene utilizzato senza l'opzione `ALL` per eliminare le righe duplicate dai risultati combinati delle tre istruzioni `SELECT` e vengono restituite 5 righe.  
  
 Nel terzo esempio viene utilizzata l'opzione `ALL` con il primo operatore `UNION` e il secondo operatore `UNION`, che non utilizza l'opzione `ALL`, viene racchiuso tra parentesi. Il secondo operatore `UNION` viene elaborato per primo in quanto è racchiuso tra parentesi e restituisce 5 righe in quanto l'opzione `ALL` è stata omessa e i duplicati vengono rimossi. Queste 5 righe vengono combinate con i risultati della prima istruzione `SELECT` mediante le parole chiave `UNION ALL`. I duplicati tra i due set di 5 righe non vengono rimossi. Il risultato finale include 10 righe.  
  
```  
-- Uses AdventureWorks  
  
IF OBJECT_ID ('dbo.EmployeeOne', 'U') IS NOT NULL  
DROP TABLE dbo.EmployeeOne;  
GO  
IF OBJECT_ID ('dbo.EmployeeTwo', 'U') IS NOT NULL  
DROP TABLE dbo.EmployeeTwo;  
GO  
IF OBJECT_ID ('dbo.EmployeeThree', 'U') IS NOT NULL  
DROP TABLE dbo.EmployeeThree;  
GO  
  
SELECT pp.LastName, pp.FirstName, e.JobTitle   
INTO dbo.EmployeeOne  
FROM Person.Person AS pp JOIN HumanResources.Employee AS e  
ON e.BusinessEntityID = pp.BusinessEntityID  
WHERE LastName = 'Johnson';  
GO  
SELECT pp.LastName, pp.FirstName, e.JobTitle   
INTO dbo.EmployeeTwo  
FROM Person.Person AS pp JOIN HumanResources.Employee AS e  
ON e.BusinessEntityID = pp.BusinessEntityID  
WHERE LastName = 'Johnson';  
GO  
SELECT pp.LastName, pp.FirstName, e.JobTitle   
INTO dbo.EmployeeThree  
FROM Person.Person AS pp JOIN HumanResources.Employee AS e  
ON e.BusinessEntityID = pp.BusinessEntityID  
WHERE LastName = 'Johnson';  
GO  
-- Union ALL  
SELECT LastName, FirstName, JobTitle  
FROM dbo.EmployeeOne  
UNION ALL  
SELECT LastName, FirstName ,JobTitle  
FROM dbo.EmployeeTwo  
UNION ALL  
SELECT LastName, FirstName,JobTitle   
FROM dbo.EmployeeThree;  
GO  
  
SELECT LastName, FirstName,JobTitle  
FROM dbo.EmployeeOne  
UNION   
SELECT LastName, FirstName, JobTitle   
FROM dbo.EmployeeTwo  
UNION   
SELECT LastName, FirstName, JobTitle   
FROM dbo.EmployeeThree;  
GO  
  
SELECT LastName, FirstName,JobTitle   
FROM dbo.EmployeeOne  
UNION ALL  
(  
SELECT LastName, FirstName, JobTitle   
FROM dbo.EmployeeTwo  
UNION  
SELECT LastName, FirstName, JobTitle   
FROM dbo.EmployeeThree  
);  
GO  
  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-using-a-simple-union"></a>E. Utilizzo di un semplice operatore UNION  
 Nell'esempio seguente, il set di risultati include il contenuto del `CustomerKey` colonne di entrambe le `FactInternetSales` e `DimCustomer` tabelle. Poiché non viene utilizzata la parola chiave ALL, i duplicati vengono escluse dai risultati.  
  
```  
-- Uses AdventureWorks  
  
SELECT CustomerKey   
FROM FactInternetSales    
UNION   
SELECT CustomerKey   
FROM DimCustomer   
ORDER BY CustomerKey;  
```  
  
### <a name="f-using-union-of-two-select-statements-with-order-by"></a>F. Utilizzo dell'operatore UNION in due istruzioni SELECT con la clausola ORDER BY  
 Quando un'istruzione SELECT in un'istruzione UNION include una clausola ORDER BY, tale clausola deve essere inserito dopo tutte le istruzioni SELECT. Nell'esempio seguente viene illustrato come utilizzare errato e quello corretto `UNION` in due `SELECT` istruzioni in cui una colonna viene ordinata con ORDER BY.  
  
```  
-- Uses AdventureWorks  
  
-- INCORRECT  
SELECT CustomerKey   
FROM FactInternetSales    
ORDER BY CustomerKey  
UNION   
SELECT CustomerKey   
FROM DimCustomer  
ORDER BY CustomerKey;  
  
-- CORRECT   
USE AdventureWorksPDW2012;  
  
SELECT CustomerKey   
FROM FactInternetSales    
UNION   
SELECT CustomerKey   
FROM DimCustomer   
ORDER BY CustomerKey;  
```  
  
### <a name="g-using-union-of-two-select-statements-with-where-and-order-by"></a>G. Tramite l'unione di due istruzioni SELECT con WHERE e ORDER BY  
 Nell'esempio seguente viene illustrato come utilizzare errato e quello corretto `UNION` in due `SELECT` istruzioni where WHERE e ORDER BY sono necessari.  
  
```  
-- Uses AdventureWorks  
  
-- INCORRECT   
SELECT CustomerKey   
FROM FactInternetSales   
WHERE CustomerKey >= 11000  
ORDER BY CustomerKey   
UNION   
SELECT CustomerKey   
FROM DimCustomer   
ORDER BY CustomerKey;  
  
-- CORRECT  
USE AdventureWorksPDW2012;  
  
SELECT CustomerKey   
FROM FactInternetSales   
WHERE CustomerKey >= 11000  
UNION   
SELECT CustomerKey   
FROM DimCustomer   
ORDER BY CustomerKey;  
```  
  
### <a name="h-using-union-of-three-select-statements-to-show-effects-of-all-and-parentheses"></a>H. Utilizzo di unione di tre istruzioni SELECT per illustrare effetti dell'opzione ALL e delle parentesi  
 L'esempio seguente usa `UNION` per combinare i risultati di **della stessa tabella** per illustrare gli effetti dell'opzione ALL e delle parentesi quando si utilizza `UNION`.  
  
 Il primo esempio Usa `UNION ALL` per mostrare duplicati record e restituisce ogni riga nella tabella di origine tre volte. Il secondo esempio Usa `UNION` senza `ALL` per eliminare le righe duplicate dai risultati combinati delle tre `SELECT` istruzioni e restituisce solo le righe non duplicate dalla tabella di origine.  
  
 Il terzo esempio viene utilizzato `ALL` con il primo `UNION` parentesi che racchiudono il secondo e `UNION` che non utilizza `ALL`. Il secondo `UNION` viene elaborata per prima perché è racchiuso tra parentesi. Restituisce solo le righe non duplicate dalla tabella perché la `ALL` opzione non viene utilizzato e vengono eliminati i duplicati. Queste righe vengono combinate con i risultati del primo `SELECT` utilizzando il `UNION ALL` parole chiave. Ciò non rimuove i duplicati tra i due set.  
  
```  
-- Uses AdventureWorks  
  
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
UNION ALL   
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
UNION ALL   
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer;  
  
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
UNION   
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
UNION   
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer;  
  
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
UNION ALL  
(  
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
UNION   
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [Selezionare esempi &#40; Transact-SQL &#41;](../../t-sql/queries/select-examples-transact-sql.md)  
  
  

