---
title: query () (metodo) (tipo di dati xml) | Documenti Microsoft
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|xml
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- query method
- query() method
ms.assetid: f48f6f7b-219f-463a-bf36-bc10f21afaeb
caps.latest.revision: "28"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 4ec43116cf548df0a6f3541ab882635331f1b395
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="query-method-xml-data-type"></a>Metodo query() con tipo di dati XML
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Specifica un'espressione XQuery un'istanza di **xml** tipo di dati. Il risultato è di **xml** tipo. Il metodo restituisce un'istanza XML non tipizzata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
query ('XQuery')  
```  
  
## <a name="arguments"></a>Argomenti  
 XQuery  
 Stringa costituita da un'espressione XQuery che esegue query su nodi XML, ad esempio elementi o attributi, in un'istanza XML.  
  
## <a name="examples"></a>Esempi  
 In questa sezione vengono forniti esempi dell'utilizzo del metodo query () del **xml** tipo di dati.  
  
### <a name="a-using-the-query-method-against-an-xml-type-variable"></a>A. Utilizzo del metodo query() in una variabile di tipo XML  
 Nell'esempio seguente viene dichiarata una variabile  **@myDoc**  di **xml** digitare e assegna un'istanza XML a esso. Il **query ()** metodo viene quindi utilizzato per specificare un'espressione XQuery sul documento.  
  
 La query recupera l'elemento figlio <`Features`> dell'elemento <`ProductDescription`>:  
  
```  
declare @myDoc xml  
set @myDoc = '<Root>  
<ProductDescription ProductID="1" ProductName="Road Bike">  
<Features>  
  <Warranty>1 year parts and labor</Warranty>  
  <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>  
</Features>  
</ProductDescription>  
</Root>'  
SELECT @myDoc.query('/Root/ProductDescription/Features')  
```  
  
 Risultato:  
  
```  
<Features>  
  <Warranty>1 year parts and labor</Warranty>  
  <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>  
</Features>        
```  
  
### <a name="b-using-the-query-method-against-an-xml-type-column"></a>B. Utilizzo del metodo query() in una colonna di tipo XML  
 Nell'esempio seguente, il **query ()** metodo viene utilizzato per specificare un'espressione XQuery di **CatalogDescription** colonna di **xml** digitare il  **AdventureWorks** database:  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
<Product ProductModelID="{ /PD:ProductDescription[1]/@ProductModelID }" />  
') as Result  
FROM Production.ProductModel  
where CatalogDescription.exist('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
declare namespace wm="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain";  
     /PD:ProductDescription/PD:Features/wm:Warranty ') = 1  
```  
  
 Dalla query precedente si noti quanto segue:  
  
-   La colonna CatalogDescription è una classe tipizzata **xml** colonna. Pertanto, è disponibile il relativo schema associato. Nel [prologo XQuery](../../xquery/modules-and-prologs-xquery-prolog.md), **dello spazio dei nomi** parola chiave viene utilizzata per definire il prefisso che verrà utilizzato successivamente nel corpo della query.  
  
-   Il **query ()** metodo costruisce codice XML, un <`Product`> elemento che dispone di un **ProductModelID** attributo, in cui il **ProductModelID** è il valore di attributo recuperati dal database. Per ulteriori informazioni sulla costruzione di strutture XML, vedere [costruzione di strutture XML &#40; XQuery &#41; ](../../xquery/xml-construction-xquery.md).  
  
-   Il [metodo exist () (tipo di dati XML)](../../t-sql/xml/exist-method-xml-data-type.md) nella clausola WHERE viene utilizzata per trovare solo le righe che contiene il <`Warranty`> elemento nello schema XML. Nuovamente, il **dello spazio dei nomi** parola chiave viene utilizzata per definire due prefissi di spazio dei nomi.  
  
 Risultato parziale:  
  
```  
<Product ProductModelID="19"/>   
<Product ProductModelID="23"/>   
...  
```  
  
 Si noti che i metodi query() ed exist() dichiarano entrambi il prefisso PD. In tali casi, è possibile utilizzare WITH XMLNAMESPACES per definire innanzitutto i prefissi e utilizzarli nella query.  
  
```  
WITH XMLNAMESPACES (  
   'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS PD,  
   'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS wm)  
SELECT CatalogDescription.query('  
<Product ProductModelID="{ /PD:ProductDescription[1]/@ProductModelID }" />  
') as Result  
FROM Production.ProductModel  
where CatalogDescription.exist('  
     /PD:ProductDescription/PD:Features/wm:Warranty ') = 1  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiungere spazi dei nomi alle query con WITH XMLNAMESPACES](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [Confronto dati XML tipizzati con dati XML non tipizzati](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Creare istanze di dati XML](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [metodi con tipo di dati XML](../../t-sql/xml/xml-data-type-methods.md)   
 [Linguaggio di manipolazione dei dati XML &#40; Linguaggio XML DML &#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
