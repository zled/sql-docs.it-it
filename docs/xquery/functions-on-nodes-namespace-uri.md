---
title: Funzione namespace-uri (XQuery) | Documenti Microsoft
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
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- fn:namespace-uri function
- namespace-uri function
ms.assetid: 9b48d216-26c8-431d-9ab4-20ab187917f4
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d765c32fc0387a1aff755a59d454f9b5797eb297
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="functions-on-nodes---namespace-uri"></a>Funzioni sui nodi - namespace-uri
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce l'URI spazio dei nomi del QName specificato *$arg* come xs: String.  
  
## <a name="syntax"></a>Sintassi  
  
```  
fn:namespace-uri() as xs:string  
fn:namespace-uri($arg as node()?) as xs:string  
```  
  
## <a name="arguments"></a>Argomenti  
 *$arg*  
 Nome del nodo di cui verrà recuperata la parte relativa all'URI dello spazio dei nomi.  
  
## <a name="remarks"></a>Osservazioni  
  
-   Se l'argomento viene omesso, l'impostazione predefinita è il nodo di contesto.  
  
-   In SQL Server, **fn:namespace-uri()** senza un argomento può essere utilizzato solo nel contesto di un predicato dipendente dal contesto. In particolare, può essere utilizzata solo tra parentesi ([ ]).  
  
-   Se *$arg* è una sequenza vuota, viene restituita la stringa di lunghezza zero.  
  
-   Se *$arg* è un elemento o nodo di attributo il cui expanded-QName non è in uno spazio dei nomi, la funzione restituisce la stringa di lunghezza zero  
  
## <a name="examples"></a>Esempi  
 In questo argomento vengono forniti esempi di XQuery sulle istanze XML archiviate in diverse **xml** colonne di tipo nel database AdventureWorks.  
  
### <a name="a-retrieve-namespace-uri-of-a-specific-node"></a>A. Recupero dell'URI dello spazio dei nomi di un nodo specifico  
 La query seguente viene eseguita su un'istanza XML non tipizzata. L'espressione di query `namespace-uri(/ROOT[1])` recupera la parte relativa all'URI dello spazio dei nomi del nodo specificato.  
  
```  
set @x='<ROOT><a>111</a></ROOT>'  
SELECT @x.query('namespace-uri(/ROOT[1])')  
```  
  
 Poiché l'elemento QName specificato non contiene l'URI dello spazio dei nomi, ma solo il nome locale, il risultato è una stringa di lunghezza zero.  
  
 La query seguente viene eseguita Instructions di tipo **xml** colonna. L'espressione `namespace-uri(/AWMI:root[1]/AWMI:Location[1])` restituisce l'URI dello spazio dei nomi del primo elemento figlio <`Location`> dell'elemento <`root`>.  
  
```  
SELECT Instructions.query('  
declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
     namespace-uri(/AWMI:root[1]/AWMI:Location[1])') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Risultato:  
  
```  
http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions  
```  
  
### <a name="b-using-namespace-uri-without-argument-in-a-predicate"></a>B. Utilizzo di namespace-uri() senza argomento in un predicato  
 La query seguente viene specificata sulla colonna XML tipizzata CatalogDescription. L'espressione restituisce tutti i nodi elemento il cui URI dello spazio dei nomi è `http://www.adventure-works.com/schemas/OtherFeatures`. Spazio dei nomi -**URI ()** viene specificata senza un argomento di funzione e viene utilizzato il nodo di contesto.  
  
```  
SELECT CatalogDescription.query('  
declare namespace p1="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
   /p1:ProductDescription//*[namespace-uri() = "http://www.adventure-works.com/schemas/OtherFeatures"]  
') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 Risultato parziale:  
  
```  
<p1:wheel xmlns:p1="http://www.adventure-works.com/schemas/OtherFeatures">High performance wheels.</p1:wheel>  
<p2:saddle xmlns:p2="http://www.adventure-works.com/schemas/OtherFeatures">  
  <p3:i xmlns:p3="http://www.w3.org/1999/xhtml">Anatomic design</p3:i> and made from durable leather for a full-day of riding in comfort.</p2:saddle>  
…  
```  
  
 È possibile modificare l'URI dello spazio dei nomi nella query precedente in `http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain`. Verranno così restituiti tutti i nodi figlio dell'elemento <`ProductDescription`> in cui la parte dell'URI dello spazio dei nomi del QName esteso è `http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain`.  
  
### <a name="implementation-limitations"></a>Limitazioni di implementazione  
 Limitazioni:  
  
-   Il **namespace-uri()** funzione restituisce istanze di tipo xs: String anziché di xs: anyURI.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni sui nodi](http://msdn.microsoft.com/library/09a8affa-3341-4f50-aebc-fdf529e00c08)   
 [Funzione local-name &#40; XQuery &#41;](../xquery/functions-on-nodes-local-name.md)  
  
  
