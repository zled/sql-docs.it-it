---
title: Funzione position (XQuery) | Documenti Microsoft
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: xquery
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- position function
- fn:position function
ms.assetid: f1bab9e4-1715-4c06-9cb0-06c7e0c9c97f
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 00ac65b0e0468cb1b4985af92e29cdd0376ea250
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="context-functions---position-xquery"></a>Funzioni di contesto - posizione (XQuery)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce un valore integer che indica la posizione dell'elemento di contesto all'interno della sequenza di elementi corrente da elaborare.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
fn:position() as xs:integer  
```  
  
## <a name="remarks"></a>Osservazioni  
 In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], **fn:position()** può essere utilizzato solo nel contesto di un predicato dipendente dal contesto. In particolare, può essere utilizzata solo tra parentesi ([ ]). I confronti basati su tale funzione non riducono la cardinalità durante l'interferenza dei tipi statici.  
  
## <a name="examples"></a>Esempi  
 In questo argomento vengono forniti esempi di XQuery sulle istanze XML archiviate in diverse **xml** colonne di tipo di [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.  
  
### <a name="a-using-the-position-xquery-function-to-retrieve-the-first-two-product-features"></a>A. Utilizzo della funzione XQuery position() per recuperare le prime due caratteristiche del prodotto  
 La query seguente recupera le prime due caratteristiche, ovvero i primi due elementi figlio dell'elemento <`Features`>, dalla descrizione del catalogo prodotti. Se sono disponibili più caratteristiche, viene aggiunto un elemento <`there-is-more/`> al risultato.  
  
```  
SELECT CatalogDescription.query('  
     declare namespace pd="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     <Product>   
          { /pd:ProductDescription/@ProductModelID }  
          { /pd:ProductDescription/@ProductModelName }   
          {  
            for $f in /pd:ProductDescription/pd:Features/*[position()<=2]  
            return  
            $f   
          }  
          {  
            if (count(/pd:ProductDescription/pd:Features/*) > 2)  
            then <there-is-more/>  
            else ()  
          }   
     </Product>          
') as x  
FROM Production.ProductModel  
WHERE CatalogDescription is not null  
```  
  
 Dalla query precedente si noti quanto segue:  
  
-   Il **dello spazio dei nomi** parola chiave nel [prologo XQuery](../xquery/modules-and-prologs-xquery-prolog.md) definisce un prefisso dello spazio dei nomi utilizzato nel corpo della query.  
  
-   Il corpo della query costruisce codice XML con un \<prodotto > elemento con **ProductModelID** e **ProductModelName** attributi e le caratteristiche del prodotto restituite come elementi figlio.  
  
-   Il **Position** funzione viene utilizzata nel predicato per determinare la posizione del \<funzionalità > elemento figlio nel contesto. Viene restituita se si tratta della prima o della seconda caratteristica.  
  
-   L'istruzione IF aggiunge un \<non esiste-is-more / > elemento per il risultato se sono presenti più di due caratteristiche del catalogo prodotti.  
  
-   Poiché non tutte le descrizioni del catalogo dei modelli di prodotto vengono archiviate nella tabella, viene utilizzata la clausola WHERE per scartare le righe in cui CatalogDescriptions è NULL.  
  
 Risultato parziale:  
  
```  
<Product ProductModelID="19" ProductModelName="Mountain 100">  
  <p1:Warranty xmlns:p1="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    <p1:WarrantyPeriod>3 year</p1:WarrantyPeriod>  
    <p1:Description>parts and labor</p1:Description>  
  </p1:Warranty>  
  <p2:Maintenance xmlns:p2="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    <p2:NoOfYears>10</p2:NoOfYears>  
    <p2:Description>maintenance contact available through your dealer or  
                    any AdventureWorks retail store.</p2:Description>  
  </p2:Maintenance>  
  <there-is-more/>  
</Product>   
…  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni XQuery per il tipo di dati XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
