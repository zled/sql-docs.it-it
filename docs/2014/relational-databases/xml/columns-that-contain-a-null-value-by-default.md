---
title: Colonne contenenti un valore NULL per impostazione predefinita | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- columns [XML in SQL Server], null default value
ms.assetid: 9381c07f-6887-4a62-9730-32661f9aa87c
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e4c975e898a7b7b57d69aa95b2e62175f8e95cdf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48223261"
---
# <a name="columns-that-contain-a-null-value-by-default"></a>Colonne contenenti un valore NULL per impostazione predefinita
  Per impostazione predefinita, la presenza di un valore Null in una colonna corrisponde all'assenza dell'attributo, nodo o elemento. Questo funzionamento predefinito può essere sovrascritto richiedendo un valore XML incentrato sugli elementi mediante la direttiva ELEMENTS e specificando XSINIL per richiedere l'aggiunta di elementi per i valori NULL, come illustrato nella query seguente:  
  
```  
SELECT EmployeeID as "@EmpID",   
       FirstName  as "EmpName/First",   
       MiddleName as "EmpName/Middle",   
       LastName   as "EmpName/Last"  
FROM   HumanResources.Employee E, Person.Contact C  
WHERE  E.EmployeeID = C.ContactID  
AND    E.EmployeeID=1  
FOR XML PATH, ELEMENTS XSINIL  
```  
  
 Il risultato è illustrato di seguito. Non specificando XSINIL, l'elemento <`Middle`> non sarà presente.  
  
```  
<row xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Middle xsi:nil="true" />  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzare la modalità PATH con FOR XML](use-path-mode-with-for-xml.md)  
  
  
