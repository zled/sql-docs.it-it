---
title: Colonne con il nome di un test di nodo XPath | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: xml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [SQL Server], columns with
- XPath node test
ms.assetid: b48adccd-3b6b-486a-b326-20f57170186f
caps.latest.revision: "10"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1e6ecd60de9116169ca3014338a629abf258a39f
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="columns-with-the-name-of-an-xpath-node-test"></a>Colonne con il nome di un test di nodo XPath
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)] Se il nome della colonna è uno dei test di nodo XPath, il mapping del contenuto viene eseguito come illustrato nella tabella seguente. Quando il nome della colonna è un test di nodo XPath, il mapping viene eseguito tra il contenuto e il nodo corrispondente. Se il tipo SQL della colonna è **xml**, viene generato un errore.  
  
|Nome colonna|Comportamento|  
|-----------------|--------------|  
|text()|Per una colonna con nome text(), il valore stringa contenuto nella colonna viene aggiunto come nodo di testo.|  
|comment()|Per una colonna con nome comment(), il valore stringa contenuto nella colonna viene aggiunto come commento XML.|  
|node()|Per una colonna con nome node(), il risultato è lo stesso di quando il nome della colonna è un carattere jolly (*).|  
|processing-instruction(name)|Per una colonna il cui nome corrisponde a quello di un'istruzione di elaborazione, il valore stringa contenuto nella colonna viene aggiunto come valore PI per il nome di destinazione dell'istruzione di elaborazione.|  
  
 Nella query seguente viene illustrato l'utilizzo dei test di nodo come nomi di colonna. I nodi di testo e i commenti vengono aggiunti nel codice XML risultante.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT E.BusinessEntityID "@EmpID",   
        'Example of using node tests such as text(), comment(), processing-instruction()'                as "comment()",  
        'Some PI'                   as "processing-instruction(PI)",  
        'Employee name and address data' as "text()",  
        'middle name is optional'        as "EmpName/text()",  
        FirstName                        as "EmpName/First",   
        MiddleName                       as "EmpName/Middle",   
        LastName                         as "EmpName/Last",  
        AddressLine1                     as "Address/AddrLine1",  
        AddressLine2                     as "Address/AddrLIne2",  
        City                             as "Address/City"  
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P   
    ON P.BusinessEntityID = E.BusinessEntityID  
INNER JOIN Person.BusinessEntityAddress AS BAE  
    ON BAE.BusinessEntityID = E.BusinessEntityID  
INNER JOIN Person.Address AS A  
    ON BAE.AddressID = A.AddressID  
WHERE  E.BusinessEntityID=1  
FOR XML PATH;  
```  
  
 Risultato:  
  
 `<row EmpID="1">`  
  
 `<!--Example of using node tests such as text(), comment(), processing-instruction() -->`  
  
 `<?PI Some PI?>`  
  
 `Employee name and address data`  
  
 `<EmpName>middle name is optional`  
  
 `<First>Ken</First>`  
  
 `<Last>Sánchez</Last>`  
  
 `</EmpName>`  
  
 `<Address>`  
  
 `<AddrLine1>4350 Minute Dr.</AddrLine1>`  
  
 `<City>Minneapolis</City>`  
  
 `</Address>`  
  
 `</row>`  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzare la modalità PATH con FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  
