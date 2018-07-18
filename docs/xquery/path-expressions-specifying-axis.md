---
title: Definizione dell'asse in un passo dell'espressione di percorso | Documenti Microsoft
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: sql
ms.component: xquery
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- attribute axis [SQL Server]
- axis step [XQuery]
- descendant axis
- self axis
- path expressions [XQuery]
- child axis
- descendant-or-self axis
- parent axis
ms.assetid: c44fb843-0626-4496-bde0-52ca0bac0a9e
caps.latest.revision: 30
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 2acb1aa6b9eddd2cf30f97da0d594db56b94e456
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="path-expressions---specifying-axis"></a>Espressioni di percorso - definizione asse
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Ogni passo dell'asse in un'espressione di percorso include i componenti seguenti:  
  
-   Un asse  
  
-   Oggetto [test di nodo](../xquery/path-expressions-specifying-node-test.md)  
  
-   [Zero o più predicati (facoltativo)](../xquery/path-expressions-specifying-predicates.md)  
  
 Per altre informazioni, vedere [espressioni di percorso &#40;XQuery&#41;](../xquery/path-expressions-xquery.md).  
  
 L'implementazione di XQuery in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] supporta i passi dell'asse seguenti:  
  
|Asse|Description|  
|----------|-----------------|  
|**child**|Restituisce gli elementi figlio del nodo di contesto.|  
|**descendant**|Restituisce tutti i discendenti del nodo di contesto.|  
|**parent**|Restituisce l'elemento padre del nodo di contesto.|  
|**attribute**|Restituisce gli attributi del nodo di contesto.|  
|**self**|Restituisce il nodo di contesto stesso.|  
|**descendant-or-self**|Restituisce il nodo di contesto e tutti i relativi discendenti.|  
  
 Tutti questi assi, ad eccezione di **padre** asse, sono assi in avanti. Il **padre** asse è un asse inverso, poiché esegue una ricerca all'indietro nella gerarchia del documento. Ad esempio, l'espressione di percorso relativo `child::ProductDescription/child::Summary` include due passi, ognuno dei quali specifica un asse `child`. Il primo passo recupera i \<ProductDescription > gli elementi figlio del nodo di contesto. Per ogni \<ProductDescription > nodo elemento, il secondo passo recupera i \<riepilogo > nodi elemento figlio.  
  
 L'espressione di percorso relativo `child::root/child::Location/attribute::LocationID` include tre passi. I primi due passi specificano ognuno un asse `child`, mentre il terzo passo specifica l'asse `attribute`. Quando eseguite le istruzioni di produzione di documenti XML nel **Production. ProductModel** tabella, l'espressione restituisce il `LocationID` attributo del \<percorso > nodo elemento figlio del \<radice > elemento.  
  
## <a name="examples"></a>Esempi  
 Gli esempi di query in questo argomento vengono specificati sui **xml** colonne di tipo di **AdventureWorks** database.  
  
### <a name="a-specifying-a-child-axis"></a>A. Definizione di un asse child  
 Per un modello di prodotto specifico, la query seguente recupera il \<funzionalità > elemento figlio del nodo il \<ProductDescription > dalla descrizione del catalogo prodotti archiviata nel nodo di elemento di `Production.ProductModel` tabella.  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
  /child::PD:ProductDescription/child::PD:Features')  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 Dalla query precedente si noti quanto segue:  
  
-   Il `query()` metodo il **xml** tipo di dati specifica l'espressione di percorso.  
  
-   Entrambi i passi dell'espressione di percorso specificano un asse `child` e i nomi dei nodi, `ProductDescription` e `Features`, come test di nodo. Per informazioni sui test di nodo, vedere [specificando i Test di nodo in un passo dell'espressione di percorso](../xquery/path-expressions-specifying-node-test.md).  
  
### <a name="b-specifying-descendant-and-descendant-or-self-axes"></a>B. Definizione di assi descendant e descendant-or-self  
 Nell'esempio seguente vengono utilizzati assi descendant e descendant-or-self. La query in questo esempio viene eseguita su un **xml** variabile di tipo. L'istanza XML è semplificata per illustrare in modo chiaro la differenza nei risultati generati.  
  
```  
declare @x xml  
set @x='  
<a>  
 <b>text1  
   <c>text2  
     <d>text3</d>  
   </c>  
 </b>  
</a>'  
declare @y xml  
set @y = @x.query('  
  /child::a/child::b  
')  
select @y  
```  
  
 Nel risultato seguente, l'espressione restituisce il nodo elemento figlio `<b>` del nodo elemento `<a>`:  
  
```  
<b>text1  
   <c>text2  
     <d>text3</d>  
   </c>  
</b>  
```  
  
 Se in questa espressione si specifica un asse descendant per l'espressione di percorso,  
  
 `/child::a/child::b/descendant::*`, si richiedono tutti i discendenti del nodo elemento <`b`>.  
  
 L'asterisco (*) nel test di nodo rappresenta il nome del nodo come test di nodo. Pertanto, il tipo di nodo primario dell'asse descendant, il nodo elemento, determina i tipi di nodi restituiti. L'espressione restituisce quindi tutti i nodi elemento. I nodi di testo non vengono restituiti. Per ulteriori informazioni sul tipo di nodo primario e la relativa relazione con il test di nodo, vedere [specifica di Test di nodo in un passo dell'espressione di percorso](../xquery/path-expressions-specifying-node-test.md) argomento.  
  
 I nodi elemento <`c`> e <`d`> vengono restituiti come illustrato nel risultato seguente:  
  
```  
<c>text2  
     <d>text3</d>  
</c>  
<d>text3</d>  
```  
  
 Se si specifica un asse descendant-or-self anziché l'asse descendant, `/child::a/child::b/descendant-or-self::*` restituisce il nodo di contesto, l'elemento <`b`> e i relativi discendenti.  
  
 Risultato:  
  
```  
<b>text1  
   <c>text2  
     <d>text3</d>  
   </c>  
</b>  
  
<c>text2  
     <d>text3</d>  
</c>  
  
<d>text3</d>   
```  
  
 La seguente query di esempio sul **AdventureWorks** database recupera tutti i nodi elemento discendenti di <`Features`> figlio dell'elemento di <`ProductDescription`> elemento:  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
  /child::PD:ProductDescription/child::PD:Features/descendant::*  
')  
FROM  Production.ProductModel  
WHERE ProductModelID=19  
```  
  
### <a name="c-specifying-a-parent-axis"></a>C. Definizione di un asse parent  
 La query seguente restituisce l'elemento figlio <`Summary`> dell'elemento <`ProductDescription`> nel documento XML del catalogo prodotti archiviato nella tabella `Production.ProductModel`.  
  
 In questo esempio viene utilizzato l'asse parent per tornare all'elemento padre dell'elemento <`Feature`> e recuperare l'elemento figlio <`Summary`> dell'elemento <`ProductDescription`>.  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
  
/child::PD:ProductDescription/child::PD:Features/parent::PD:ProductDescription/child::PD:Summary  
')  
FROM   Production.ProductModel  
WHERE  ProductModelID=19  
  
```  
  
 In questo esempio di query, l'espressione di percorso utilizza l'asse `parent`. È possibile riscrivere l'espressione senza l'asse parent, come illustrato di seguito:  
  
```  
/child::PD:ProductDescription[child::PD:Features]/child::PD:Summary  
```  
  
 Un esempio più dettagliato dell'asse parent è il seguente.  
  
 Ogni descrizione del catalogo prodotti archiviati nel **CatalogDescription** colonna del **ProductModel** tabella include un `<ProductDescription>` elemento con la `ProductModelID` attributo e `<Features>`elemento figlio, come illustrato nel frammento seguente:  
  
```  
<ProductDescription ProductModelID="..." >  
  ...  
  <Features>  
    <Feature1>...</Feature1>  
    <Feature2>...</Feature2>  
   ...  
</ProductDescription>  
```  
  
 La query imposta la variabile iteratore `$f` nell'istruzione FLWOR per restituire gli elementi figli dell'elemento `<Features>`. Per altre informazioni, vedere [istruzione e iterazione FLWOR &#40;XQuery&#41;](../xquery/flwor-statement-and-iteration-xquery.md). Per ogni caratteristica, la clausola `return` costruisce un'istanza XML nel formato seguente:  
  
```  
<Feature ProductModelID="...">...</Feature>  
<Feature ProductModelID="...">...</Feature>  
```  
  
 Per aggiungere `ProductModelID` per ogni elemento `<Feature`>, viene specificato l'asse `parent`:  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
declare namespace wm="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain";  
  for $f in /child::PD:ProductDescription/child::PD:Features/child::*  
  return  
   <Feature  
     ProductModelID="{ ($f/parent::PD:Features/parent::PD:ProductDescription/attribute::ProductModelID)[1]}" >  
          { $f }  
   </Feature>  
')  
FROM  Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 Risultato parziale:  
  
```  
<Feature ProductModelID="19">  
  <wm:Warranty   
   xmlns:wm="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    <wm:WarrantyPeriod>3 years</wm:WarrantyPeriod>  
    <wm:Description>parts and labor</wm:Description>  
  </wm:Warranty>  
</Feature>  
<Feature ProductModelID="19">  
  <wm:Maintenance   
   xmlns:wm="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    <wm:NoOfYears>10 years</wm:NoOfYears>  
    <wm:Description>maintenance contract available through your dealer   
                  or any AdventureWorks retail store.</wm:Description>  
  </wm:Maintenance>  
</Feature>  
<Feature ProductModelID="19">  
  <p1:wheel   
   xmlns:p1="http://www.adventure-works.com/schemas/OtherFeatures">  
      High performance wheels.  
  </p1:wheel>  
</Feature>  
```  
  
 Si noti che il predicato `[1]` nell'espressione di percorso viene aggiunto per assicurare che venga restituito un valore singleton.  
  
  
