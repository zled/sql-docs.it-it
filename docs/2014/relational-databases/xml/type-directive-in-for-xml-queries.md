---
title: Direttiva TYPE in query FOR XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FOR XML clause, TYPE directive
- TYPE directive
ms.assetid: a3df6c30-1f25-45dc-b5a9-bd0e41921293
caps.latest.revision: 40
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 3e5a3ffe184513bce9f331f5d905a0587897e64a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169177"
---
# <a name="type-directive-in-for-xml-queries"></a>Direttiva TYPE in query FOR XML
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporto per la [xml &#40;Transact-SQL&#41; ](/sql/t-sql/xml/xml-transact-sql) consente di richiedere facoltativamente che il risultato di una query FOR XML venga restituito come `xml` tipo di dati specificando la direttiva TYPE. In questo modo è possibile elaborare il risultato di una query FOR XML sul server. Ad esempio, è possibile specificare un'espressione XQuery, assegnare il risultato a un `xml` variabile di tipo, o scrivere [query FOR XML annidate](use-nested-for-xml-queries.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Restituisce i dati dell'istanza al client come risultato di diversi costrutti server del tipo di dati XML, ad esempio query FOR XML che utilizzano la direttiva TYPE o in cui il `xml` tipo di dati viene utilizzato per restituire i valori dei dati di istanza XML da colonne di tabella SQL e di output parametri. Nel codice delle applicazioni client, il provider ADO.NET richiede che le informazioni sui tipi di dati XML vengano inviate dal server in codifica binaria. Se tuttavia si utilizza FOR XML senza la direttiva TYPE, i dati XML vengono restituiti come tipo stringa. In tutti i casi, il provider client sarà sempre in grado di gestire entrambe i formati di XML. La clausola FOR XML di livello principale senza la direttiva TYPE non può essere utilizzata con i cursori.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato l'utilizzo della direttiva TYPE con le query FOR XML.  
  
### <a name="retrieving-for-xml-query-results-as-xml-type"></a>Recupero dei risultati di una query FOR XML come tipo xml  
 La query seguente recupera le informazioni di contatto del cliente dalla tabella `Contacts` . Poiché in `TYPE` è specificata la direttiva `FOR XML`, il risultato viene restituito come tipo `xml`.  
  
```  
USE AdventureWorks2012;  
Go  
SELECT BusinessEntityID, FirstName, LastName  
FROM Person.Person  
ORDER BY BusinessEntityID  
FOR XML AUTO, TYPE;  
```  
  
 Risultato parziale:  
  
 `<Person.Person BusinessEntityID="1" FirstName="Ken" LastName="Sánchez"/>`  
  
 `<Person.Person BusinessEntityID="2" FirstName="Terri" LastName="Duffy"/>`  
  
 `...`  
  
### <a name="assigning-for-xml-query-results-to-an-xml-type-variable"></a>Assegnazione dei risultati di una query FOR XML a una variabile di tipo xml  
 Nell'esempio seguente, un risultato FOR XML viene assegnato a un `xml` variabile di tipo, `@x`. La query recupera le informazioni di contatto, ad esempio il `BusinessEntityID`, `FirstName`, `LastName`e ulteriore i numeri di telefono dal `AdditionalContactInfo` colonna di `xml``TYPE`. Poiché la clausola `FOR XML` specifica la direttiva `TYPE`, il codice XML viene restituito come tipo `xml` e assegnato a una variabile.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @x xml;  
SET @x = (  
   SELECT BusinessEntityID,   
          FirstName,   
          LastName,   
          AdditionalContactInfo.query('  
declare namespace aci="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
              //act:telephoneNumber/act:number') as MorePhoneNumbers  
   FROM Person.Person  
   FOR XML AUTO, TYPE);  
SELECT @x;  
GO  
```  
  
### <a name="querying-results-of-a-for-xml-query"></a>Esecuzione di una query sui risultati di una query FOR XML  
 La query FOR XML restituisce codice XML. Pertanto, è possibile applicare `xml` digitare i metodi, ad esempio `query()` e `value()`, al risultato XML restituito dalle query FOR XML.  
  
 Nella query seguente, il `query()` metodo per il `xml` tipo di dati viene utilizzato per eseguire query sul risultato del `FOR XML` query. Per altre informazioni, vedere [Metodo query&#40;&#41; con &#40;tipo di dati XML&#41;](/sql/t-sql/xml/query-method-xml-data-type).  
  
```  
USE AdventureWorks2012;  
GO  
SELECT (SELECT BusinessEntityID, FirstName, LastName, AdditionalContactInfo.query('  
DECLARE namespace aci="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
DECLARE namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
 //act:telephoneNumber/act:number  
') AS PhoneNumbers  
FROM Person.Person  
FOR XML AUTO, TYPE).query('/Person.Person[1]');  
```  
  
 Interna `SELECT … FOR XML` query restituisce un `xml` tipo di risultato a cui esterna `SELECT` si applica il `query()` metodo per il `xml` tipo. Si noti la direttiva `TYPE` specificata.  
  
 Risultato:  
  
 `<Person.Person BusinessEntityID="1" FirstName="Ken" LastName="Sánchez">`  
  
 `<PhoneNumbers>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">111-111-1111</act:number>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">112-111-1111</act:number>`  
  
 `</PhoneNumbers>`  
  
 `</Person.Person>`  
  
 Nella query seguente il metodo `value()` con il tipo di dati `xml` viene utilizzato per recuperare un valore dal risultato XML restituito dalla query `SELECT…FOR XML`. Per altre informazioni, vedere [Metodo value&#40;&#41; &#40;tipo di dati XML&#41;](/sql/t-sql/xml/value-method-xml-data-type).  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @FirstPhoneFromAdditionalContactInfo varchar(40);  
SELECT @FirstPhoneFromAdditionalContactInfo =   
 ( SELECT BusinessEntityID, FirstName, LastName, AdditionalContactInfo.query('  
declare namespace aci="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
   //act:telephoneNumber/act:number  
   ') AS PhoneNumbers  
   FROM Person.Person Contact  
   FOR XML AUTO, TYPE).value('  
declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
  /Contact[@BusinessEntityID="1"][1]/PhoneNumbers[1]/act:number[1]', 'varchar(40)'  
 )  
SELECT @FirstPhoneFromAdditionalContactInfo;  
```  
  
 L'espressione di percorso XQuery nel metodo `value()` recupera il primo numero di telefono di un cliente il cui `BusinessEntityID` è `1`.  
  
> [!NOTE]  
>  Se la direttiva TYPE non è specificata, il risultato della query FOR XML viene restituito come tipo `nvarchar(max)`.  
  
### <a name="using-for-xml-query-results-in-insert-update-and-delete-transact-sql-dml"></a>Utilizzo dei risultati di query FOR XML in istruzioni INSERT, UPDATE e DELETE (DML Transact-SQL)  
 Nell'esempio seguente viene illustrato l'utilizzo delle query FOR XML nelle istruzioni DML (Data Manipulation Language). Nell'esempio, il `FOR XML` restituisce un'istanza di `xml` tipo. L'istruzione `INSERT` inserisce il codice XML in una tabella.  
  
```  
CREATE TABLE T1(intCol int, XmlCol xml);  
GO  
INSERT INTO T1   
VALUES(1, '<Root><ProductDescription ProductModelID="1" /></Root>');  
GO  
  
CREATE TABLE T2(XmlCol xml)  
GO  
INSERT INTO T2(XmlCol)   
SELECT (SELECT XmlCol.query('/Root')   
        FROM T1   
        FOR XML AUTO,TYPE);   
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [FOR XML &#40;SQL Server&#41;](../xml/for-xml-sql-server.md)  
  
  
