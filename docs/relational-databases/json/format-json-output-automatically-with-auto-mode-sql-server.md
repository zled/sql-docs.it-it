---
title: "Formattare automaticamente l&#39;output JSON con la modalit&#224; AUTO (SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FOR JSON AUTO"
ms.assetid: 178a2a4e-e0f6-49b9-9895-396956d3c7d9
caps.latest.revision: 17
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 15
---
# Formattare automaticamente l&#39;output JSON con la modalit&#224; AUTO (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Per formattare l'output JSON automaticamente in base alla struttura dell'istruzione **SELECT** , specificare l'opzione  **AUTO** con la clausola **FOR JSON** .  
  
 Con l'opzione **AUTO** , il formato dell'output JSON viene determinato automaticamente in base all'ordine delle colonne nell'elenco SELECT e delle relative tabelle di origine. Non è possibile modificare questo formato.  
  
 Una query che usa l'opzione **FOR JSON AUTO** deve avere una clausola **FROM** .  
  
 Di seguito sono riportati alcuni esempi della clausola **FOR JSON** con l'opzione **AUTO** .  
  
## Esempi  
 **Query 1**  
  
 I risultati della clausola FOR JSON AUTO sono simili a quelli di FOR JSON PATH se viene usata una sola tabella nella query. In questo caso, FOR JSON AUTO non crea oggetti nidificati. L'unica differenza è che gli alias separati da punti verranno generati come chiavi con punti. Di conseguenza, FOR JSON AUTO non userà gli alias di colonna per la formattazione.  
  
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
[  
      {"Id":1,"FirstName":"Ken","LastName":"Sánchez","Info.MiddleName":"J"},  
      {"Id":2,"FirstName":"Terri","LastName":"Duffy","Info.MiddleName":"Lee"},  
      {"Id":3,"FirstName":"Roberto","LastName":"Tamburello"},  
      {"Id":4,"FirstName":"Rob","LastName":"Walters"},  
      {"Id":5,"FirstName":"Gail","LastName":"Erickson","Info.Title":"Ms.","Info.MiddleName":"A"}  
]  
```  
  
 **Query 2**  
  
 Quando si uniscono più tabelle, le colonne della prima tabella vengono generate come proprietà dell'oggetto radice. Le colonne della seconda tabella vengono generate come proprietà di un oggetto annidato. Il nome della tabella o l'alias della seconda tabella viene usato come nome della matrice annidata.  
  
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
[  
  {  
       "SalesOrderNumber":"SO43659",  
        "OrderDate":"2011-05-31T00:00:00",  
        "D":[  
            {"UnitPrice":24.99, "OrderQty":1  }  
         ]  
  },  
  {  
       "SalesOrderNumber":"SO43659" ,  
       "D":[  
          { "UnitPrice":34.40  },  
          { "UnitPrice":134.24, "OrderQty":5 }  
        ]  
  }  
]  
  
```  
  
## Esempi - Generare un output JSON annidato  
 Anziché FOR JSON AUTO, è possibile scrivere query FOR JSON nidificate nella sezione SELECT della query principale con la clausola FOR JSON PATH, come illustrato negli esempi seguenti.  
  
 **Query 1**  
  
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
  
 **Risultato 1**  
  
```json  
[  
  {  
       "SalesOrderNumber":"SO43659",  
        "OrderDate":"2011-05-31T00:00:00",  
        "D":[  
            { "UnitPrice":24.99,  "OrderQty":1 }  
         ]  
  },  
  {  
       "SalesOrderNumber":"SO4390" ,  
       "D":[  
            { "UnitPrice":24.99 }  
        ]  
  }  
]  
  
```  
  
## Vedere anche  
 [Clausola FOR &#40;Transact-SQL&#41;](../Topic/FOR%20Clause%20\(Transact-SQL\).md)  
  
  