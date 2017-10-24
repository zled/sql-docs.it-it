---
title: substring-funzione (XQuery) | Documenti Microsoft
ms.custom: 
ms.date: 03/09/2017
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
- substring function [XQuery]
- fn:substring function
ms.assetid: 2b3b8651-de51-46dc-af82-c86c45eac871
caps.latest.revision: 42
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2fbe33b349def61c3b093079554db626b56f2f09
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="functions-on-string-values---substring"></a>Funzioni su valori stringa: substring
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Restituisce parte del valore di *$sourceString*, iniziando in corrispondenza della posizione indicata dal valore di *$startingLoc,* e continua per il numero di caratteri indicato dal valore di *$ lunghezza*.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
fn:substring($sourceString as xs:string?,  
                          $startingLoc  as as xs:decimal?) as xs:string?  
  
fn:substring($sourceString as xs:string?,  
                          $startingLoc as xs:decimal?,  
                          $length as xs:decimal?) as xs:string?  
```  
  
## <a name="arguments"></a>Argomenti  
 *$sourceString*  
 Stringa di origine.  
  
 *$startingLoc*  
 Punto della stringa di origine corrispondente al punto iniziale della sottostringa. Se il valore è negativo o è uguale a 0, vengono restituiti solo i caratteri nelle posizioni maggiori di zero. Se è maggiore della lunghezza del *$sourceString*, viene restituita la stringa di lunghezza zero.  
  
 *$length*  
 Numero di caratteri da recuperare (facoltativo). Se non specificato, restituisce tutti i caratteri dalla posizione specificata *$startingLoc* fino alla fine della stringa.  
  
## <a name="remarks"></a>Osservazioni  
 La versione della funzione con tre argomenti restituisce i caratteri di `$sourceString` il cui operatore di posizione `$p` è soggetto alla regola seguente:  
  
 `fn:round($startingLoc) <= $p < fn:round($startingLoc) + fn:round($length)`  
  
 Il valore di *$length* può essere maggiore del numero di caratteri nel valore di *$sourceString* successivi alla posizione iniziale. In questo caso, la sottostringa restituisce i caratteri fino alla fine della *$sourceString*.  
  
 Il primo carattere di una stringa si trova nella posizione 1.  
  
 Se il valore di *$sourceString* è una sequenza vuota, viene gestita come stringa di lunghezza zero. In caso contrario, se il valore *$startingLoc* o *$length* è una sequenza vuota, viene restituita la sequenza vuota.  
  
## <a name="supplementary-characters-surrogate-pairs"></a>Caratteri supplementari (coppie di surrogati)  
 Il comportamento delle coppie di surrogati nelle funzioni XQuery dipende dal livello di compatibilità del database e, in alcuni casi, dall'URI dello spazio dei nomi predefinito per le funzioni. Per ulteriori informazioni, vedere la sezione "XQuery funzioni riconoscono i surrogati" nell'argomento [modifiche di rilievo alle funzionalità del motore di Database in SQL Server 2016](../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md). Vedere anche [del livello di compatibilità di ALTER DATABASE &#40; Transact-SQL &#41; ](../t-sql/statements/alter-database-transact-sql-compatibility-level.md) e [Collation and Unicode Support](../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="implementation-limitations"></a>Limitazioni di implementazione  
 SQL Server richiede il *$startingLoc* e *$length parametri* siano di tipo xs anziché xs: double di.  
  
 SQL Server consente *$startingLoc* e *$length* di una sequenza vuota, perché la sequenza vuota è un possibile valore risultante di errori dinamici viene eseguito il mapping a ().  
  
## <a name="examples"></a>Esempi  
 In questo argomento vengono forniti esempi di XQuery sulle istanze XML archiviate in diverse **xml** colonne di tipo di [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.  
  
### <a name="a-using-the-substring-xquery-function-to-retrieve-partial-summary-product-model-descriptions"></a>A. Utilizzo della funzione XQuery substring() per recuperare le descrizioni parziali del modello del prodotto disponibili nell'elemento Summary  
 La query recupera i primi 50 caratteri del testo della descrizione del modello del prodotto, ovvero l'elemento <`Summary`> nel documento.  
  
```  
WITH XMLNAMESPACES ('http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd)  
SELECT ProductModelID, CatalogDescription.query('  
    <Prod>{ substring(string((/pd:ProductDescription/pd:Summary)[1]), 1, 50) }</Prod>  
 ') as Result  
FROM Production.ProductModel  
where CatalogDescription.exist('/pd:ProductDescription')  = 1;  
```  
  
 Dalla query precedente si noti quanto segue:  
  
-   Il **String ()** funzione restituisce il valore della stringa di <`Summary`> elemento. L'utilizzo di questa funzione è determinato dal fatto che l'elemento <`Summary`> contiene sia il testo che i sottoelementi (elementi di formattazione html) e che tali elementi verranno ignorati, mentre verrà recuperato tutto il testo.  
  
-   Il **substring** funzione recupera i primi 50 caratteri del valore di stringa recuperati tramite il **String ()**.  
  
 Risultato parziale:  
  
```  
ProductModelID Result  
-------------- ----------------------------------------------------  
19      <Prod>Our top-of-the-line competition mountain bike.</Prod>   
23      <Prod>Suitable for any type of riding, on or off-roa</Prod>  
...  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni XQuery per il tipo di dati XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  

