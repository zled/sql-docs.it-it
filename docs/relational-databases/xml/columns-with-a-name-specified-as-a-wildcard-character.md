---
title: "Colonne con nome specificato come carattere jolly | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-xml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "nomi [SQL Server], colonne con nomi"
ms.assetid: d9551df1-5bb4-4c0b-880a-5bb049834884
caps.latest.revision: 10
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 10
---
# Colonne con nome specificato come carattere jolly
  Se il nome di colonna specificato è un carattere jolly (\*), il contenuto della colonna viene inserito come se non fosse stato specificato alcun nome di colonna. Se la colonna non è di tipo diverso da **xml**, il relativo contenuto viene inserito come nodo di testo, come illustrato nell'esempio seguente:  
  
```  
USE AdventureWorks2012;  
GO  
SELECT E.BusinessEntityID "@EmpID",   
       FirstName "*",   
       MiddleName "*",   
       LastName "*"  
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P  
    ON E.BusinessEntityID = P.BusinessEntityID  
WHERE E.BusinessEntityID=1  
FOR XML PATH;  
```  
  
 Risultato:  
  
 `<row EmpID="1">KenJSánchez</row>`  
  
 Se la colonna è di tipo **xml**, viene inserito l'albero XML corrispondente. Ad esempio, la query seguente specifica "*" come nome della colonna che contiene il codice XML restituito dall'espressione XQuery eseguita sulla colonna Instructions.  
  
```  
SELECT   
       ProductModelID,  
       Name,  
       Instructions.query('declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
                /MI:root/MI:Location   
              ') as "*"  
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH;   
GO  
```  
  
 Di seguito è riportato il risultato. Il codice XML restituito dalla XQuery viene inserito senza un elemento di wrapping.  
  
 `<row>`  
  
 `<ProductModelID>7</ProductModelID>`  
  
 `<Name>HL Touring Frame</Name>`  
  
 `<MI:Location LocationID="10">...</MI:Location>`  
  
 `<MI:Location LocationID="20">...</MI:Location>`  
  
 `...`  
  
 `</row>`  
  
## Vedere anche  
 [Utilizzare la modalità PATH con FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  