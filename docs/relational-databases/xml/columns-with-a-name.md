---
title: Colonne provviste di un nome | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [SQL Server], columns with
ms.assetid: c994e089-4cfc-4e9b-b7fc-e74f6014b51a
caps.latest.revision: 8
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: b4b9a8774565dd0e31caf940cf3e8254b0987205
ms.openlocfilehash: 3a2651e6e67cceb648049f99ab9588a44b7f3fb0
ms.contentlocale: it-it
ms.lasthandoff: 11/08/2017

---
# <a name="columns-with-a-name"></a>Colonne provviste di un nome
  Di seguito vengono illustrate le condizioni specifiche in cui viene eseguito il mapping tra le colonne del set di righe provviste di nome e il codice XML risultante, con distinzione tra maiuscole e minuscole:  
  
-   Il nome di colonna inizia con un simbolo di chiocciola (@)  
  
-   Il nome di colonna non inizia con un simbolo di chiocciola (@)  
  
-   Il nome di colonna non inizia con un simbolo di chiocciola (@) e contiene una barra (/)  
  
-   Più colonne condividono lo stesso prefisso.  
  
-   Una colonna ha un nome diverso.  
  
## <a name="column-name-starts-with-an-at-sign-"></a>Il nome di colonna inizia con un simbolo di chiocciola (@)  
 Se il nome di colonna inizia con un simbolo di chiocciola (@) e non contiene una barra (/), un attributo del `row` viene creato l'elemento con il valore della colonna corrispondente. Ad esempio, la query seguente restituisce un set di righe a due colonne (@PmId, Name). Nel codice XML risultante, un **PmId** viene aggiunto un attributo corrispondente `row` elemento e un valore di ProductModelID viene assegnato a esso.  
  
```  
  
SELECT ProductModelID as "@PmId",  
       Name  
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH   
go  
  
```  
  
 Risultato:  
  
```  
<row PmId="7">  
  <Name>HL Touring Frame</Name>  
</row>  
```  
  
 Si noti che gli attributi devono precedere qualsiasi altro tipo di nodo presente nello stesso livello, ad esempio nodi di elemento e di testo. La query seguente restituirà un errore:  
  
```  
SELECT Name,  
       ProductModelID as "@PmId"  
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH   
go  
```  
  
## <a name="column-name-does-not-start-with-an-at-sign-"></a>Il nome di colonna non inizia con un simbolo di chiocciola (@)  
 Se il nome della colonna non inizia con un simbolo di chiocciola (@), non è uno dei test di nodo XPath e non contiene una barra (/), un elemento XML che è un sottoelemento dell'elemento riga, `row` per impostazione predefinita, viene creato.  
  
 La query seguente specifica il nome della colonna, il risultato. Pertanto, un `result` elemento figlio viene aggiunto per il `row` elemento.  
  
```  
SELECT 2+2 as result  
for xml PATH  
```  
  
 Risultato:  
  
```  
<row>  
  <result>4</result>  
</row>  
```  
  
 La query seguente specifica il nome della colonna, ManuWorkCenterInformation, per il codice XML restituito dall'espressione XQuery specificata sulla colonna Instructions di tipo **xml**. Pertanto, un `ManuWorkCenterInformation` elemento viene aggiunto come elemento figlio di `row` elemento.  
  
```  
SELECT   
       ProductModelID,  
       Name,  
       Instructions.query('declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
                /MI:root/MI:Location   
              ') as ManuWorkCenterInformation  
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH   
go  
```  
  
 Risultato:  
  
```  
<row>  
  <ProductModelID>7</ProductModelID>  
  <Name>HL Touring Frame</Name>  
  <ManuWorkCenterInformation>  
    <MI:Location ...LocationID="10" ...></MI:Location>  
    <MI:Location ...LocationID="20" ...></MI:Location>  
     ...  
  </ManuWorkCenterInformation>  
</row>  
```  
  
## <a name="column-name-does-not-start-with-an-at-sign--and-contains-a-slash-mark-"></a>Il nome di colonna non inizia con un simbolo di chiocciola (@) e contiene una barra (/)  
 Se il nome di colonna non inizia con un simbolo di chiocciola (@), ma contiene una barra (/), il nome della colonna indica una gerarchia XML. Ad esempio, se il nome della colonna è "Name1/Name2/Name3.../Name***n*** ", ogni Name***i*** rappresenta un nome di elemento nidificato nell'elemento di riga corrente (per i=1) o che si trova sotto l'elemento il cui nome è Name***i-1***. Se Name***n*** inizia con il simbolo @, viene eseguito il mapping a un attributo dell'elemento Name***n-1*** .  
  
 Ad esempio, la query seguente restituisce l'ID e il nome di un dipendente rappresentati come un elemento complesso EmpName che contiene nome, secondo nome e cognome.  
  
```  
SELECT EmployeeID "@EmpID",   
       FirstName  "EmpName/First",   
       MiddleName "EmpName/Middle",   
       LastName   "EmpName/Last"  
FROM   HumanResources.Employee E, Person.Contact C  
WHERE  E.EmployeeID = C.ContactID  
AND    E.EmployeeID=1  
FOR XML PATH  
```  
  
 I nomi di colonna vengono usati come un percorso nella creazione del codice XML in modalità PATH. Il nome della colonna che contiene i valori ID dipendente inizia con '\@'. Pertanto, un attributo, **EmpID**, viene aggiunto per il `row` elemento. I nomi di tutte le altre colonne contengono una barra ("/"), che indica la gerarchia. Il codice XML risultante avrà il `EmpName` figlio sotto il `row` elemento e `EmpName` figlio avrà `First`, `Middle` e `Last` gli elementi figlio.  
  
```  
<row EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
 Il valore del secondo nome del dipendente è Null e, per impostazione predefinita, il valore Null corrisponde all'assenza dell'elemento o attributo. Se si desidera la generazione di elementi per i valori NULL, è possibile specificare la direttiva ELEMENTS con XSINIL, come illustrato in questa query.  
  
```  
SELECT EmployeeID "@EmpID",   
       FirstName  "EmpName/First",   
       MiddleName "EmpName/Middle",   
       LastName   "EmpName/Last"  
FROM   HumanResources.Employee E, Person.Contact C  
WHERE  E.EmployeeID = C.ContactID  
AND    E.EmployeeID=1  
FOR XML PATH, ELEMENTS XSINIL  
```  
  
 Risultato:  
  
```  
<row xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"   
      EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Middle xsi:nil="true" />  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
 Per impostazione predefinita, la modalità PATH genera XML incentrato sugli elementi. Specificare la direttiva ELEMENTS in una query in modalità PATH pertanto non produce effetti. Come illustrato nell'esempio precedente tuttavia, la direttiva ELEMENTS risulta utile con XSINIL per la generazione di elementi per i valori Null.  
  
 Oltre all'ID e al nome, la query seguente recupera l'indirizzo di un dipendente. Come per il percorso nei nomi di colonna per le colonne degli indirizzi, un `Address` elemento figlio viene aggiunto per il `row` elemento e i dettagli relativi agli indirizzi vengono aggiunti come elementi figlio del `Address` elemento.  
  
```  
SELECT EmployeeID   "@EmpID",   
       FirstName    "EmpName/First",   
       MiddleName   "EmpName/Middle",   
       LastName     "EmpName/Last",  
       AddressLine1 "Address/AddrLine1",  
       AddressLine2 "Address/AddrLIne2",  
       City         "Address/City"  
FROM   HumanResources.Employee E, Person.Contact C, Person.Address A  
WHERE  E.EmployeeID = C.ContactID  
AND    E.AddressID = A.AddressID  
AND    E.EmployeeID=1  
FOR XML PATH  
```  
  
 Risultato:  
  
```  
<row EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Last>Achong</Last>  
  </EmpName>  
  <Address>  
    <AddrLine1>7726 Driftwood Drive</AddrLine1>  
    <City>Monroe</City>  
  </Address>  
</row>  
```  
  
## <a name="several-columns-share-the-same-path-prefix"></a>Più colonne condividono lo stesso prefisso di percorso  
 Se più colonne successive condividono lo stesso prefisso di percorso, vengono raggruppate sotto lo stesso nome. Se vengono utilizzati prefissi degli spazi dei nomi diversi, anche se associati allo stesso spazio dei nomi, un percorso viene considerato diverso. Nella query precedente, le colonne FirstName, MiddleName e LastName condividono lo stesso prefisso EmpName. Pertanto, vengono aggiunti come elementi figlio del `EmpName` elemento. Ciò avviene anche quando si crea il `Address` elemento nell'esempio precedente.  
  
## <a name="one-column-has-a-different-name"></a>Una colonna ha un nome diverso  
 Se è presente una colonna con un nome diverso, interromperà il raggruppamento, come illustrato nella query modificata seguente. La query interrompe il raggruppamento di FirstName, MiddleName e LastName, come specificato nella query precedente, aggiungendo colonne di indirizzi fra le colonne FirstName e MiddleName.  
  
```  
SELECT EmployeeID "@EmpID",   
       FirstName "EmpName/First",   
       AddressLine1 "Address/AddrLine1",  
       AddressLine2 "Address/AddrLIne2",  
       City "Address/City",  
       MiddleName "EmpName/Middle",   
       LastName "EmpName/Last"  
FROM   HumanResources.EmployeeAddress E, Person.Contact C, Person.Address A  
WHERE  E.EmployeeID = C.ContactID  
AND    E.AddressID = A.AddressID  
AND    E.EmployeeID=1  
FOR XML PATH  
```  
  
 Di conseguenza, la query crea due `EmpName` elementi. Il primo `EmpName` elemento ha il `FirstName` elemento figlio e il secondo `EmpName` elemento ha il `MiddleName` e `LastName` gli elementi figlio.  
  
 Risultato:  
  
```  
<row EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
  </EmpName>  
  <Address>  
    <AddrLine1>7726 Driftwood Drive</AddrLine1>  
    <City>Monroe</City>  
  </Address>  
  <EmpName>  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzare la modalità PATH con FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  

