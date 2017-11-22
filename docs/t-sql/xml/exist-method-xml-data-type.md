---
title: EXIST () (metodo) (tipo di dati xml) | Documenti Microsoft
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|xml
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- exist() method
- exist method
ms.assetid: a55b75e0-0a17-4787-a525-9b095410f7af
caps.latest.revision: "35"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: bcf939f68dd338e9672dfc4bc716b3d92ebda272
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="exist-method-xml-data-type"></a>Metodo exist() (tipo di dati xml)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce un **bit** che rappresenta una delle condizioni seguenti:  
  
-   1, che rappresenta True, se l'espressione XQuery di una query restituisce un risultato non vuoto, ovvero se restituisce almeno un nodo XML.  
  
-   0, che rappresenta False, se restituisce un risultato vuoto.  
  
-   NULL se il **xml** istanza del tipo di dati in cui è stata eseguita la query contiene un valore NULL.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
exist (XQuery)   
```  
  
## <a name="arguments"></a>Argomenti  
 XQuery  
 È un'espressione XQuery, un valore letterale stringa.  
  
## <a name="remarks"></a>Osservazioni  
  
> [!NOTE]  
>  Il **exist ()** metodo restituisce 1 per l'espressione XQuery che restituisce un risultato non vuoto. Se si specifica il **true ()** o **false ()** funziona all'interno di **exist ()** (metodo), il **exist ()** metodo restituirà 1, perché il funzioni **true ()** e **false ()** restituiscono booleani True e False, rispettivamente. ovvero un risultato non vuoto. Pertanto, **exist ()** restituirà 1 (True), come illustrato nell'esempio seguente:  
  
```  
declare @x xml;  
set @x='';  
select @x.exist('true()');   
```  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato come specificare il **exist ()** metodo.  
  
### <a name="example-specifying-the-exist-method-against-an-xml-type-variable"></a>Esempio: Specifica del metodo exist() su una variabile di tipo XML  
 Nell'esempio seguente, @x è un **xml** variabile di tipo (xml non tipizzato) e @f è una variabile di tipo integer che archivia il valore restituito dal **exist ()** metodo. Il **exist ()** metodo restituisce True (1) se il valore di data archiviato nell'istanza XML è `2002-01-01`.  
  
```  
declare @x xml;  
declare @f bit;  
set @x = '<root Somedate = "2002-01-01Z"/>';  
set @f = @x.exist('/root[(@Somedate cast as xs:date?) eq xs:date("2002-01-01Z")]');  
select @f;  
```  
  
 Nel confronto delle date nel **exist ()** (metodo), tenere presente quanto segue:  
  
-   Il codice `cast as xs:date?` viene utilizzato per il cast del valore di **xs: date** tipo per scopi di confronto.  
  
-   Il valore di  **@Somedate**  attributo non è tipizzato. Confrontare questo valore, viene eseguito in modo implicito il cast di tipo sul lato destro del confronto, il **xs: date** tipo.  
  
-   Invece di **sottoposto a cast come xs:date()**, è possibile utilizzare il **xs:date()** funzione del costruttore. Per ulteriori informazioni, vedere [funzioni costruttore &#40; XQuery &#41; ](../../xquery/constructor-functions-xquery.md).  
  
 L'esempio seguente è simile al precedente, ma contiene un elemento <`Somedate`>.  
  
```  
DECLARE @x xml;  
DECLARE @f bit;  
SET @x = '<Somedate>2002-01-01Z</Somedate>';  
SET @f = @x.exist('/Somedate[(text()[1] cast as xs:date ?) = xs:date("2002-01-01Z") ]')  
SELECT @f;  
```  
  
 Dalla query precedente si noti quanto segue:  
  
-   Il **Text ()** il metodo restituisce un nodo di testo che contiene il valore non tipizzato `2002-01-01`. (Il tipo XQuery è **xdt: untypedAtomic**.) È necessario eseguire il cast esplicito questo valore tipizzato da **x** a **xsd: date**, perché il cast implicito non è supportato in questo caso.  
  
### <a name="example-specifying-the-exist-method-against-a-typed-xml-variable"></a>Esempio: Specifica del metodo exist() su una variabile XML tipizzata  
 Nell'esempio seguente viene illustrato l'utilizzo del **exist ()** metodo su un **xml** variabile di tipo. Si tratta di una variabile XML tipizzata, poiché specifica il nome della raccolta di spazi dei nomi dello schema, `ManuInstructionsSchemaCollection`.  
  
 Nell'esempio, un documento viene innanzitutto assegnato a questa variabile di istruzioni di produzione e quindi la **exist ()** metodo viene utilizzato per trovare se il documento include un <`Location`> elemento il cui **LocationID**  valore dell'attributo è 50.  
  
 Il **exist ()** metodo specificato con il @x variabile restituisce 1 (True) se il documento include le istruzioni di produzione un <`Location`> elemento con `LocationID=50`. In caso contrario, il metodo restituisce 0 (False).  
  
```  
DECLARE @x xml (Production.ManuInstructionsSchemaCollection);  
SELECT @x=Instructions  
FROM Production.ProductModel  
WHERE ProductModelID=67;  
--SELECT @x  
DECLARE @f int;  
SET @f = @x.exist(' declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
    /AWMI:root/AWMI:Location[@LocationID=50]  
');  
SELECT @f;  
```  
  
### <a name="example-specifying-the-exist-method-against-an-xml-type-column"></a>Esempio: Specifica del metodo exist() su una colonna di tipo XML  
 La query seguente recupera gli ID dei modelli di prodotto le cui descrizioni di catalogo non includono le specifiche, ovvero l'elemento <`Specifications`>:  
  
```  
SELECT ProductModelID, CatalogDescription.query('  
declare namespace pd="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
    <Product   
        ProductModelID= "{ sql:column("ProductModelID") }"   
        />  
') AS Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist('  
    declare namespace  pd="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     /pd:ProductDescription[not(pd:Specifications)]'  
    ) = 1;  
```  
  
 Dalla query precedente si noti quanto segue:  
  
-   La clausola WHERE seleziona solo le righe di **ProductDescription** table che soddisfano la condizione specificata sul **CatalogDescription xml** colonna di tipo.  
  
-   Il **exist ()** metodo nella clausola WHERE restituisce 1 (True) se il codice XML non include alcun <`Specifications`> elemento. Si noti l'uso del [funzione NOT () (XQuery)](../../xquery/functions-on-boolean-values-not-function.md).  
  
-   Il [funzione SQL: Column (XQuery)](../../xquery/xquery-extension-functions-sql-column.md) funzione viene utilizzata per recuperare il valore da una colonna non XML.  
  
-   Questa query restituisce un set di righe vuoto.  
  
 La query specifica **query ()** e **exist ()** metodi del tipo di dati xml e entrambi i metodi dichiarano gli stessi spazi dei nomi nel prologo della query. In questo caso è possibile utilizzare WITH XMLNAMESPACES per dichiarare il prefisso e utilizzarlo nella query.  
  
```  
WITH XMLNAMESPACES ('http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd)  
SELECT ProductModelID, CatalogDescription.query('  
    <Product   
        ProductModelID= "{ sql:column("ProductModelID") }"   
        />  
') AS Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist('  
     /pd:ProductDescription[not(pd:Specifications)]'  
    ) = 1;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiungere spazi dei nomi alle query con WITH XMLNAMESPACES](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [Confronto dati XML tipizzati con dati XML non tipizzati](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Creare istanze di dati XML](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [metodi con tipo di dati XML](../../t-sql/xml/xml-data-type-methods.md)   
 [Linguaggio di manipolazione dei dati XML &#40; Linguaggio XML DML &#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
