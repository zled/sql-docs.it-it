---
title: 'SQL: Column (funzione) (XQuery) | Documenti Microsoft'
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- sql:column function
- sql:column() function
ms.assetid: e8f67bdf-b489-49a9-9d0f-2069c1750467
caps.latest.revision: 38
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: abb8cf32f67af58fdb54e6605c844c6245fc545d
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="xquery-extension-functions---sqlcolumn"></a>Funzioni di estensione XQuery - SQL: Column
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Come descritto nell'argomento [associazione dati relazionali all'interno di codice XML](../t-sql/xml/binding-relational-data-inside-xml-data.md), è possibile utilizzare il **sql:column(()** funzione quando si utilizza [metodi con tipo di dati XML](../t-sql/xml/xml-data-type-methods.md) per esporre un valore relazionale in XQuery.  
  
 Ad esempio, il [metodo query () (tipo di dati XML)](../t-sql/xml/query-method-xml-data-type.md) viene utilizzato per specificare una query su un'istanza XML archiviata in una variabile o colonna di **xml** tipo. Talvolta, potrebbe inoltre essere necessario che la query utilizzi valori di un'altra colonna non XML per unire i dati relazionali e XML. A tale scopo, utilizzare il **SQL: Column** (funzione).  
  
 Verrà eseguito il mapping tra il valore SQL e un valore XQuery corrispondente e il relativo tipo sarà un tipo di base XQuery equivalente al tipo SQL corrispondente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sql:column("columnName")  
```  
  
## <a name="remarks"></a>Osservazioni  
 Si noti che il riferimento a una colonna specificata nella **SQL: Column** funzione all'interno di un'espressione XQuery fa riferimento a una colonna nella riga che viene elaborata.  
  
 In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], può fare riferimento solo una **xml** istanza nel contesto dell'espressione dell'origine di un XML DML insert-istruzione; in caso contrario, è possibile fare riferimento alle colonne di tipo **xml** o un tipo CLR tipo definito dall'utente.  
  
 Il **SQL: Column** funzione non è supportata nelle operazioni di JOIN. Al suo posto, è possibile utilizzare l'operazione APPLY.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-sqlcolumn-to-retrieve-the-relational-value-inside-xml"></a>A. Utilizzo della funzione sql:column() per recuperare il valore relazionale nell'istanza XML  
 Nell'esempio seguente relativo alla costruzione di un'istanza XML viene illustrato il recupero di valori da una colonna relazionale non XML per associare dati XML e relazionali.  
  
 La query costruisce un'istanza XML con il formato seguente:  
  
```  
<Product ProductID="771" ProductName="Mountain-100 Silver, 38" ProductPrice="3399.99" ProductModelID="19"   
  ProductModelName="Mountain 100" />  
```  
  
 Nell'istanza XML costruita si noti quanto segue:  
  
-   Il **ProductID**, **ProductName**, e **ProductPrice** vengono ottenuti i valori di attributo di **prodotto** tabella.  
  
-   Il **ProductModelID** valore dell'attributo verrà recuperato il **ProductModel** tabella.  
  
-   Per rendere più interessante la query di **ProductModelName** valore dell'attributo viene ottenuto dal **CatalogDescription** colonna di **tipo xml**. Poiché le informazioni XML del catalogo prodotti non vengono archiviate per tutti i modelli di prodotto, l'istruzione `if` viene utilizzata per recuperare il valore solo se esiste.  
  
    ```  
    SELECT P.ProductID, CatalogDescription.query('  
    declare namespace pd="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
           <Product   
               ProductID=       "{ sql:column("P.ProductID") }"  
               ProductName=     "{ sql:column("P.Name") }"  
               ProductPrice=    "{ sql:column("P.ListPrice") }"  
               ProductModelID= "{ sql:column("PM.ProductModelID") }" >  
               { if (not(empty(/pd:ProductDescription))) then  
                 attribute ProductModelName { /pd:ProductDescription[1]/@ProductModelName }  
                else   
                   ()  
    }  
            </Product>  
    ') as Result  
    FROM Production.ProductModel PM, Production.Product P  
    WHERE PM.ProductModelID = P.ProductModelID  
    AND   CatalogDescription is not NULL  
    ORDER By PM.ProductModelID  
    ```  
  
 Dalla query precedente si noti quanto segue:  
  
-   Poiché i valori vengono recuperati da due tabelle diverse, la clausola FROM specifica due tabelle. La condizione della clausola WHERE filtra il risultato e recupera solo i prodotti con modelli che includono descrizioni del catalogo.  
  
-   Il **dello spazio dei nomi** parola chiave nel [prologo XQuery](../xquery/modules-and-prologs-xquery-prolog.md) definisce il prefisso dello spazio dei nomi XML, "pd" utilizzato nel corpo della query. Si noti che gli alias di tabella "P" e "PM" vengono definiti nella clausola FROM della query stessa.  
  
-   Il **SQL: Column** funzione viene utilizzata per visualizzare i valori non XML nell'istanza XML.  
  
 Risultato parziale:  
  
```  
ProductID               Result  
-----------------------------------------------------------------  
771         <Product ProductID="771"                   ProductName="Mountain-100 Silver, 38"   
                  ProductPrice="3399.99" ProductModelID="19"   
                  ProductModelName="Mountain 100" />  
...  
```  
  
 La query seguente costruisce un'istanza XML che contiene informazioni specifiche del prodotto, inclusi i valori degli attributi ProductID, ProductName, ProductPrice e, se disponibile, ProductModelName per tutti i prodotti appartenenti al modello di prodotto specifico ProductModelID=19. Il codice XML viene quindi assegnato al @x variabile di **xml** tipo.  
  
```  
declare @x xml  
SELECT @x = CatalogDescription.query('  
declare namespace pd="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
       <Product   
           ProductID=       "{ sql:column("P.ProductID") }"  
           ProductName=     "{ sql:column("P.Name") }"  
           ProductPrice=    "{ sql:column("P.ListPrice") }"  
           ProductModelID= "{ sql:column("PM.ProductModelID") }" >  
           { if (not(empty(/pd:ProductDescription))) then  
             attribute ProductModelName { /pd:ProductDescription[1]/@ProductModelName }  
            else   
               ()  
}  
        </Product>  
')   
FROM Production.ProductModel PM, Production.Product P  
WHERE PM.ProductModelID = P.ProductModelID  
And P.ProductModelID = 19  
select @x  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni per le estensioni XQuery SQL Server](http://msdn.microsoft.com/library/4bc5d499-5fec-4c3f-b11e-5ab5ef9d8f97)   
 [Confronto dati XML tipizzati con dati XML non tipizzati](../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Dati XML &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [Creare istanze di dati XML](../relational-databases/xml/create-instances-of-xml-data.md)   
 [metodi con tipo di dati XML](../t-sql/xml/xml-data-type-methods.md)   
 [Linguaggio di manipolazione dei dati XML &#40; Linguaggio XML DML &#41;](../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
