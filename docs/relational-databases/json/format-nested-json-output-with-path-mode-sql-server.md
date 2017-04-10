---
title: "Formattare l&#39;output JSON annidato con la modalit&#224; PATH (SQL Server) | Microsoft Docs"
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
ms.assetid: 032761b0-6358-42e4-b05c-dbfd663ac881
caps.latest.revision: 19
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 16
---
# Formattare l&#39;output JSON annidato con la modalit&#224; PATH (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Per mantenere il controllo completo sul formato dell'output JSON, specificare l'opzione **PATH** con la clausola **FOR JSON**.  
  
 La modalità **PATH** consente di creare oggetti wrapper e annidare proprietà complesse. I risultati vengono formattati sotto forma di matrice di oggetti JSON.  
  
 Di seguito sono riportati alcuni esempi della clausola **FOR JSON** con l'opzione **PATH** . Per formattare risultati annidati, usare nomi di colonna separati da punti oppure query annidate, come illustrato negli esempi seguenti. Per impostazione predefinita, i valori null non sono inclusi nell'output.  
  
## Esempio: nomi di colonna separati da punti  
 La query seguente formatta le prime cinque righe dalla tabella AdventureWorks Person come JSON.  
  
 **Query**  
  
```tsql  
SELECT TOP 5   
      BusinessEntityID As Id,  
      FirstName, LastName,  
      Title As 'Info.Title',  
      MiddleName As 'Info.MiddleName'  
  FROM Person.Person  
  FOR JSON PATH  
```  
  
 **Risultato**  
  
```json  
[  
    {"Id":1,"FirstName":"Ken","LastName":"Sánchez","Info":{"MiddleName":"J"}},  
    {"Id":2,"FirstName":"Terri","LastName":"Duffy","Info":{"MiddleName":"Lee"}},  
    {"Id":3,"FirstName":"Roberto","LastName":"Tamburello"},  
    {"Id":4,"FirstName":"Rob","LastName":"Walters"},  
    {"Id":5,"FirstName":"Gail","LastName":"Erickson","Info":{"Title":"Ms.","MiddleName":"A"}}  
]  
```  
  
 La clausola FOR JSON PATH usa l'alias o il nome di colonna per determinare il nome chiave nell'output JSON. Se alcuni alias contengono punti, la clausola FOR JSON PATH crea oggetti annidati. Si noti che nell'output non vengono generate celle con valori NULL.  
  
## Esempio: più tabelle  
 Se nella query si fa riferimento a più tabelle, i risultati vengono rappresentati come elenco semplice, quindi la clausola FOR JSON PATH annida ogni colonna tramite l'alias corrispondente. La query seguente crea un oggetto JSON per ogni coppia (OrderHeader,OrderDetails) unita in join nella query:  
  
 **Query**  
  
```tsql  
SELECT TOP 2 SalesOrderNumber AS 'Order.Number',  
       OrderDate AS 'Order.Date',  
       UnitPrice AS 'Product.Price',  
       OrderQty AS 'Product.Quantity'  
FROM Sales.SalesOrderHeader H  
  INNER JOIN Sales.SalesOrderDetail D  
    ON H.SalesOrderID = D.SalesOrderID  
FOR JSON PATH  
```  
  
 **Risultato**  
  
```json  
[  
  {  
    "Order":{  
        "Number":"SO43659",  
        "Date":"2011-05-31T00:00:00"  
      },  
    "Product":{  
         "Price":2024.9940,  
         "Quantity":1  
     }  
  },  
  {  
    "Order":{ "Number":"SO43659“ },  
    "Product":{"Price":2024.9940}  
  }  
]  
```  
  
## Vedere anche  
 [Clausola FOR &#40;Transact-SQL&#41;](../Topic/FOR%20Clause%20\(Transact-SQL\).md)  
  
  