---
title: "Formattare automaticamente l&quot;output JSON con la modalità AUTO (SQL Server) | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FOR JSON AUTO
ms.assetid: 178a2a4e-e0f6-49b9-9895-396956d3c7d9
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 3a04977311f1f04171caa1de0d15373d0b3cdf15
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="format-json-output-automatically-with-auto-mode-sql-server"></a>Formattare automaticamente l'output JSON con la modalità AUTO (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Per formattare l'output della clausola **FOR JSON** automaticamente in base alla struttura dell'istruzione **SELECT**, specificare l'opzione **AUTO**.  
  
Con l'opzione **AUTO** , il formato dell'output JSON viene determinato automaticamente in base all'ordine delle colonne nell'elenco SELECT e delle relative tabelle di origine. Non è possibile modificare questo formato.
 
 L'alternativa consiste nell'usare l'opzione **PATH** per mantenere il controllo sull'output.
 -   Per altre informazioni sull'opzione **PATH**, vedere [Formattare l'output JSON annidato con la modalità PATH](../../relational-databases/json/format-nested-json-output-with-path-mode-sql-server.md).
 -   Per una panoramica di entrambe le opzioni, vedere [Formattare i risultati delle query in formato JSON con FOR JSON](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md).
  
 Una query che usa l'opzione **FOR JSON AUTO** deve avere una clausola **FROM** .  
  
 Di seguito sono riportati alcuni esempi della clausola **FOR JSON** con l'opzione **AUTO** .  
  
## <a name="examples"></a>Esempi  
 **Query 1**  
  
I risultati della clausola FOR JSON AUTO sono simili a quelli di FOR JSON PATH quando si usa una sola tabella nella query. In questo caso, FOR JSON AUTO non crea oggetti annidati. L'unica differenza è che FOR JSON AUTO genera come output alias separati da punti (come `Info.MiddleName` nell'esempio seguente) come chiavi con punti e non come oggetti annidati.  
  
```tsql  
SELECT TOP 5   
       BusinessEntityID As Id,  
       FirstName, LastName,  
       Title As 'Info.Title',  
       MiddleName As 'Info.MiddleName'  
   FROM Person.Person  
   FOR JSON AUTO  
```  
  
 **Risultato 1**  
  
```json  
[{
    "Id": 1,
    "FirstName": "Ken",
    "LastName": "Sánchez",
    "Info.MiddleName": "J"
}, {
    "Id": 2,
    "FirstName": "Terri",
    "LastName": "Duffy",
    "Info.MiddleName": "Lee"
}, {
    "Id": 3,
    "FirstName": "Roberto",
    "LastName": "Tamburello"
}, {
    "Id": 4,
    "FirstName": "Rob",
    "LastName": "Walters"
}, {
    "Id": 5,
    "FirstName": "Gail",
    "LastName": "Erickson",
    "Info.Title": "Ms.",
    "Info.MiddleName": "A"
}]
```  
  
 **Query 2**  
  
 Quando si uniscono più tabelle, le colonne della prima tabella vengono generate come proprietà dell'oggetto radice. Le colonne della seconda tabella vengono generate come proprietà di un oggetto annidato. Il nome della tabella o l'alias della seconda tabella (ad esempio `D` nell'esempio seguente) viene usato come nome della matrice annidata.  
  
```tsql  
SELECT TOP 2 SalesOrderNumber,  
        OrderDate,  
        UnitPrice,  
        OrderQty  
FROM Sales.SalesOrderHeader H  
   INNER JOIN Sales.SalesOrderDetail D  
     ON H.SalesOrderID = D.SalesOrderID  
FOR JSON AUTO   
```  
  
 **Risultato 2**  
  
```json  
[{
    "SalesOrderNumber": "SO43659",
    "OrderDate": "2011-05-31T00:00:00",
    "D": [{
        "UnitPrice": 24.99,
        "OrderQty": 1
    }]
}, {
    "SalesOrderNumber": "SO43659",
    "D": [{
        "UnitPrice": 34.40
    }, {
        "UnitPrice": 134.24,
        "OrderQty": 5
    }]
}]
```  
 
 **Query 3**  
 Invece di usare FOR JSON AUTO è possibile annidare una sottoquery FOR JSON PATH nell'istruzione SELECT, come illustrato nell'esempio seguente. Questo esempio genera lo stesso risultato dell'esempio precedente.  
  
```tsql  
SELECT TOP 2  
    SalesOrderNumber,  
    OrderDate,  
    (SELECT UnitPrice, OrderQty  
      FROM Sales.SalesOrderDetail AS D  
      WHERE H.SalesOrderID = D.SalesOrderID  
     FOR JSON PATH) AS D  
FROM Sales.SalesOrderHeader AS H  
FOR JSON PATH  
```  
  
 **Risultato 3**  
  
```json  
[{
    "SalesOrderNumber": "SO43659",
    "OrderDate": "2011-05-31T00:00:00",
    "D": [{
        "UnitPrice": 24.99,
        "OrderQty": 1
    }]
}, {
    "SalesOrderNumber": "SO4390",
    "D": [{
        "UnitPrice": 24.99
    }]
}]
```  
  
## <a name="see-also"></a>Vedere anche  
 [Clausola FOR &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)  
  
  

