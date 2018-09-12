---
title: Supporto del tipo di dati xml in FOR XML| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- user-defined functions [SQL Server], XML
- xml data type [SQL Server], FOR XML clause
ms.assetid: 365de07d-694c-4c8b-b671-8825be27f87c
caps.latest.revision: 24
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 62e2583de85ca20944b4e86c321ca661d98d2825
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "43890137"
---
# <a name="for-xml-support-for-the-xml-data-type"></a>Supporto del tipo di dati xml in FOR XML
  Se una query FOR XML specifica una colonna di `xml` tipo nella clausola SELECT, i valori delle colonne vengono eseguito il mapping come elementi nel codice XML risultante, indipendentemente dal fatto che si specifica la direttiva ELEMENTS. Le dichiarazioni XML nella colonna di tipo `xml` non sono serializzate.  
  
 Ad esempio, la query seguente recupera le informazioni di contatto cliente, ad esempio il `BusinessEntityID`, `FirstName`, e `LastName` le colonne e i numeri di telefono dal `AdditionalContactInfo` colonna di `xml` tipo.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT BusinessEntityID, FirstName, LastName, AdditionalContactInfo.query('  
declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
 //act:telephoneNumber/act:number  
') AS PhoneNumber  
FROM Person.Person  
WHERE AdditionalContactInfo.query('  
declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
 //act:telephoneNumber/act:number  
')IS NOT NULL  
FOR XML AUTO, TYPE;  
```  
  
 Poiché la query non specifica la direttiva ELEMENTS, i valori della colonna vengono restituiti come attributi, ad eccezione delle informazioni aggiuntive sui contatti recuperate dal `xml` colonna di tipo. che vengono restituite come elementi.  
  
 Risultato parziale:  
  
 `<Person.Person BusinessEntityID="291" FirstName="Gustavo" LastName="Achong">`  
  
 `<PhoneNumber>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">425-555-1112</act:number>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">425-555-1111</act:number>`  
  
 `</PhoneNumber>`  
  
 `</Person.Person>`  
  
 `<Person.Person BusinessEntityID="293" FirstName="Catherine" LastName="Abel">`  
  
 `<PhoneNumber>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">206-555-2222</act:number>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">206-555-1234</act:number>`  
  
 `</PhoneNumber>`  
  
```  
</Person.Person>  
...  
```  
  
 Se si specifica un alias di colonna per la colonna XML generata da XQuery, tale alias consente di aggiungere un elemento wrapper intorno al codice XML generato da XQuery. Ad esempio, la query seguente specifica `MorePhoneNumbers` come alias di colonna:  
  
```  
SELECT BusinessEntityID, FirstName, LastName, AdditionalContactInfo.query('  
declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
 //act:telephoneNumber/act:number  
') AS PhoneNumber  
FROM Person.Person  
WHERE AdditionalContactInfo.query('  
declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
 //act:telephoneNumber/act:number  
')IS NOT NULL  
FOR XML AUTO, TYPE;  
```  
  
 Il codice XML restituito da XQuery viene inserito nell'elemento <`MorePhoneNumbers`>, come illustrato nel risultato parziale seguente:  
  
 `<Person.Person BusinessEntityID="291" FirstName="Gustavo" LastName="Achong">`  
  
 `<MorePhoneNumbers>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">425-555-1112</act:number>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">425-555-1111</act:number>`  
  
 `</MorePhoneNumbers>`  
  
 `</Person.Person>`  
  
 `<Person.Person BusinessEntityID="293" FirstName="Catherine" LastName="Abel">`  
  
 `<MorePhoneNumbers>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">206-555-2222</act:number>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">206-555-1234</act:number>`  
  
 `</MorePhoneNumbers>`  
  
```  
</Person.Person>  
...  
```  
  
 Se si specifica la direttiva ELEMENTS nella query, BusinessEntityID, LastName e FirstName verranno restituiti come elementi nel codice XML risultante.  
  
 L'esempio seguente illustra che la logica di elaborazione di FOR XML non vengono serializzate le dichiarazioni XML contenute nei dati XML da un `xml` colonna di tipo:  
  
```  
create table t(i int, x xml)  
go  
insert into t values(1, '<?xml version="1.0" encoding="UTF-8" ?>  
                             <Root SomeID="10" />')  
select i, x  
from   t  
for xml auto;  
```  
  
 Di seguito è riportato il risultato. Nel risultato la dichiarazione XML <`?xml version="1.0" encoding="UTF-8" ?`> non è serializzata.  
  
```  
<root>  
  <t i="1">  
    <x>  
      <Root SomeID="10" />  
    </x>  
  </t>  
</root>  
```  
  
## <a name="returning-xml-from-a-user-defined-function"></a>Restituzione di codice XML da una funzione definita dall'utente  
 Le query FOR XML consentono di restituire codice XML da una funzione definita dall'utente che restituisce quanto segue:  
  
-   Una tabella con una singola colonna di tipo `xml`.  
  
-   Un'istanza di `xml` tipo  
  
 Ad esempio, la funzione definita dall'utente seguente restituisce una tabella con una singola colonna di `xm`tipo l:  
  
```  
USE AdventureWorks2012;  
GO  
CREATE FUNCTION dbo.MyUDF (@ProudctModelID int)  
RETURNS @T TABLE  
  (  
     ProductDescription xml  
  )  
AS  
BEGIN  
  INSERT @T  
     SELECT CatalogDescription.query('  
declare namespace PD="http://www.adventure-works.com/schemas/products/description";  
                    //PD:ProductDescription  ')  
     FROM Production.ProductModel  
     WHERE ProductModelID = @ProudctModelID  
  RETURN  
END;  
```  
  
 È possibile eseguire la funzione definita dall'utente ed eseguire una query sulla tabella restituita dalla funzione. In questo esempio, il codice XML restituito da una query sulla tabella viene assegnato a un `xml` variabile di tipo.  
  
```  
declare @x xml;  
set @x = (SELECT * FROM MyUDF(19));  
select @x;  
```  
  
 Di seguito è riportato un altro esempio di una funzione definita dall'utente, che restituisce un'istanza del tipo `xml`. Nell'esempio la funzione definita dall'utente restituisce un'istanza di tipo XML perché è specificato lo spazio dei nomi dello schema.  
  
```  
DROP FUNCTION dbo.MyUDF;  
GO  
CREATE FUNCTION MyUDF (@ProductModelID int)   
RETURNS xml ([Production].[ProductDescriptionSchemaCollection])  
AS  
BEGIN  
  declare @x xml  
  set @x =   ( SELECT CatalogDescription  
          FROM Production.ProductModel  
          WHERE ProductModelID = @ProductModelID )  
  return @x  
END;  
```  
  
 Il codice XML restituito dalla funzione definita dall'utente può quindi essere assegnato a una variabile di tipo `xml`, come illustrato nell'esempio seguente:  
  
```  
declare @x xml;  
SELECT @x= dbo.MyUDF4 (19) ;  
select @x;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto di FOR XML per vari tipi di dati di SQL Server](for-xml-support-for-various-sql-server-data-types.md)  
  
  
