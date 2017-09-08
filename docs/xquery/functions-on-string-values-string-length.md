---
title: Funzione String-length (XQuery) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- string-length function
- fn:string-length function
ms.assetid: 7cd69c8b-cf2c-478c-b9a3-e0e14e1aa8aa
caps.latest.revision: 46
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2c46d7c2f2e0b4f88ca8b87a3943c2df14cc543a
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="functions-on-string-values---string-length"></a>Funzioni su valori stringa - stringa di lunghezza
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Restituisce la lunghezza della stringa in caratteri.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
fn:string-length() as xs:integer  
fn:string-length($arg as xs:string?) as xs:integer  
```  
  
## <a name="arguments"></a>Argomenti  
 *$arg*  
 Stringa di origine di cui calcolare la lunghezza.  
  
## <a name="remarks"></a>Osservazioni  
 Se il valore di *$arg* è una sequenza vuota, un **xs: integer** viene restituito il valore 0.  
  
 Il comportamento delle coppie di surrogati nelle funzioni XQuery dipende dal livello di compatibilità del database. Se il livello di compatibilità è 110 o maggiore, ogni coppia di surrogati viene conteggiata come singolo carattere. Per i livelli di compatibilità inferiori, ogni coppia viene conteggiata come due caratteri. Per ulteriori informazioni, vedere [del livello di compatibilità di ALTER DATABASE &#40; Transact-SQL &#41; ](../t-sql/statements/alter-database-transact-sql-compatibility-level.md) e [Collation and Unicode Support](../relational-databases/collations/collation-and-unicode-support.md).  
  
 Se nel valore è contenuto un carattere Unicode a 4 byte rappresentato da due caratteri surrogati, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] consentirà di calcolare i caratteri surrogati singolarmente.  
  
 Il **string-length()** senza un parametro può essere utilizzato solo all'interno di un predicato. Ad esempio, la query seguente restituisce l'elemento <`ROOT`>:  
  
```  
DECLARE @x xml;  
SET @x='<ROOT>Hello</ROOT>';  
SELECT @x.query('/ROOT[string-length()=5]');  
```  
  
## <a name="supplementary-characters-surrogate-pairs"></a>Caratteri supplementari (coppie di surrogati)  
 Il comportamento delle coppie di surrogati nelle funzioni XQuery dipende dal livello di compatibilità del database e, in alcuni casi, dall'URI dello spazio dei nomi predefinito per le funzioni. Per ulteriori informazioni, vedere la sezione "XQuery funzioni riconoscono i surrogati" nell'argomento [modifiche di rilievo alle funzionalità del motore di Database in SQL Server 2016](../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md). Vedere anche [del livello di compatibilità di ALTER DATABASE &#40; Transact-SQL &#41; ](../t-sql/statements/alter-database-transact-sql-compatibility-level.md) e [Collation and Unicode Support](../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="examples"></a>Esempi  
 In questo argomento vengono forniti esempi di XQuery sulle istanze XML archiviate in diverse **xml** colonne di tipo nel database AdventureWorks.  
  
### <a name="a-using-the-string-length-xquery-function-to-retrieve-products-with-long-summary-descriptions"></a>A. Utilizzo della funzione XQuery string-length() per il recupero di prodotti con descrizioni di riepilogo lunghe  
 Per i prodotti con descrizioni di riepilogo di lunghezza superiore a 50 caratteri, la query seguente recupera l'ID prodotto, la lunghezza della descrizione di riepilogo e il riepilogo stesso, ovvero l'elemento <`Summary`>.  
  
```  
WITH XMLNAMESPACES ('http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' as pd)  
SELECT CatalogDescription.query('  
      <Prod ProductID= "{ /pd:ProductDescription[1]/@ProductModelID }" >  
       <LongSummary SummaryLength =   
           "{string-length(string( (/pd:ProductDescription/pd:Summary)[1] )) }" >  
           { string( (/pd:ProductDescription/pd:Summary)[1] ) }  
       </LongSummary>  
      </Prod>  
 ') as Result  
FROM Production.ProductModel  
WHERE CatalogDescription.value('string-length( string( (/pd:ProductDescription/pd:Summary)[1]))', 'decimal') > 200;  
```  
  
 Dalla query precedente si noti quanto segue:  
  
-   La condizione nella clausola WHERE recupera solo le righe in cui la descrizione di riepilogo archiviata nel documento XML supera i 200 caratteri di lunghezza. Usa il [metodo Value () (tipo di dati XML)](../t-sql/xml/value-method-xml-data-type.md).  
  
-   La clausola SELECT costruisce il codice XML desiderato. Usa il [metodo query () (tipo di dati XML)](../t-sql/xml/query-method-xml-data-type.md) per costruire il codice XML e specificare l'espressione XQuery necessaria per recuperare i dati dal documento XML.  
  
 Risultato parziale:  
  
```  
Result  
-------------------  
<Prod ProductID="19">  
      <LongSummary SummaryLength="214">Our top-of-the-line competition   
             mountain bike. Performance-enhancing options include the  
             innovative HL Frame, super-smooth front suspension, and   
             traction for all terrain.  
      </LongSummary>  
</Prod>  
...  
```  
  
### <a name="b-using-the-string-length-xquery-function-to-retrieve-products-whose-warranty-descriptions-are-short"></a>B. Utilizzo della funzione XQuery string-length() per il recupero di prodotti con descrizioni della garanzia brevi  
 Per i prodotti con descrizioni della garanzia di lunghezza inferiore a 20 caratteri, la query seguente consente di recuperare il codice XML che include ID prodotto, lunghezza, descrizione della garanzia ed elemento <`Warranty`>.  
  
 La garanzia è una delle caratteristiche del prodotto. Un elemento figlio <`Warranty`> facoltativo segue dopo l'elemento <`Features`>.  
  
```  
WITH XMLNAMESPACES (  
'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd,  
'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS wm)  
  
SELECT CatalogDescription.query('  
      for   $ProdDesc in /pd:ProductDescription,  
            $pf in $ProdDesc/pd:Features/wm:Warranty  
      where string-length( string(($pf/wm:Description)[1]) ) < 20  
      return   
          <Prod >  
             { $ProdDesc/@ProductModelID }  
             <ShortFeature FeatureDescLength =   
                             "{string-length( string(($pf/wm:Description)[1]) ) }" >  
                 { $pf }  
             </ShortFeature>  
          </Prod>  
     ') as Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist('/pd:ProductDescription')=1;  
```  
  
 Dalla query precedente si noti quanto segue:  
  
-   **pD** e **wm** sono i prefissi dello spazio dei nomi utilizzati in questa query. Identificano gli stessi spazi dei nomi utilizzati nel documento su cui viene eseguita la query.  
  
-   L'espressione XQuery specifica un ciclo FOR nidificato. Il ciclo FOR esterno è necessario perché si desidera recuperare il **ProductModelID** gli attributi di <`ProductDescription`> elemento. Il ciclo FOR interno è necessario, poiché si desiderano solo i prodotti con descrizioni della caratteristica di garanzia di lunghezza inferiore a 20 caratteri.  
  
 Risultato parziale:  
  
```  
Result  
-------------------------  
<Prod ProductModelID="19">  
  <ShortFeature FeatureDescLength="15">  
    <wm:Warranty   
       xmlns:wm="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
      <wm:WarrantyPeriod>3 years</wm:WarrantyPeriod>  
      <wm:Description>parts and labor</wm:Description>  
    </wm:Warranty>  
   </ShortFeature>  
</Prod>  
...  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni XQuery per il tipo di dati XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
