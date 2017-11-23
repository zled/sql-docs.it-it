---
title: Funzione Contains (XQuery) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
dev_langs: XML
helpviewer_keywords:
- contains function (XQuery)
- fn:contains function
ms.assetid: 2c88c015-04fc-429b-84b2-835596a28b65
caps.latest.revision: "42"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2939d3e2cda2ee691f1f9563d71c8a69e850e93b
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="functions-on-string-values---contains"></a>Funzioni su valori stringa - contiene
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Restituisce un valore di tipo xs: Boolean indicante se il valore di *$arg1* contiene un valore stringa specificato da *$arg2*.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
fn:contains ($arg1 as xs:string?, $arg2 as xs:string?) as xs:boolean?  
```  
  
## <a name="arguments"></a>Argomenti  
 *$arg1*  
 Valore stringa da testare.  
  
 *$arg2*  
 Sottostringa da cercare.  
  
## <a name="remarks"></a>Osservazioni  
 Se il valore di *$arg2* è una stringa di lunghezza zero, la funzione restituisce **True**. Se il valore di *$arg1* è una stringa di lunghezza zero e il valore di *$arg2* non è una stringa di lunghezza zero, la funzione restituisce **False**.  
  
 Se il valore di *$arg1* o *$arg2* è una sequenza vuota, l'argomento viene trattato come stringa di lunghezza zero.  
  
 La funzione contains() utilizza le regole di confronto dei punti di codice Unicode predefinite di XQuery per il confronto delle stringhe.  
  
 Il valore di sottostringa specificato per *$arg2* deve essere minore o uguale a 4000 caratteri. Se il valore specificato è maggiore di 4000 caratteri, si verifica una condizione di errore dinamico e la funzione Contains () restituisce una sequenza vuota anziché un valore booleano **True** o **False**. In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] non vengono generati errori dinamici nelle espressioni XQuery.  
  
 Per ottenere i confronti tra maiuscole e minuscole, il [maiuscole](../xquery/functions-on-string-values-upper-case.md) o Lower funzioni possono essere utilizzate.  
  
## <a name="supplementary-characters-surrogate-pairs"></a>Caratteri supplementari (coppie di surrogati)  
 Il comportamento delle coppie di surrogati nelle funzioni XQuery dipende dal livello di compatibilità del database e, in alcuni casi, dall'URI dello spazio dei nomi predefinito per le funzioni. Per ulteriori informazioni, vedere la sezione "XQuery funzioni riconoscono i surrogati" nell'argomento [modifiche di rilievo alle funzionalità del motore di Database in SQL Server 2016](../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md). Vedere anche [del livello di compatibilità di ALTER DATABASE &#40; Transact-SQL &#41; ](../t-sql/statements/alter-database-transact-sql-compatibility-level.md) e [Collation and Unicode Support](../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="examples"></a>Esempi  
 In questo argomento vengono forniti esempi di XQuery sulle istanze XML archiviate in diverse colonne di tipo xml nel database AdventureWorks.  
  
### <a name="a-using-the-contains-xquery-function-to-search-for-a-specific-character-string"></a>A. Utilizzo della funzione XQuery contains() per cercare una stringa di caratteri specifica  
 La query seguente trova i prodotti per i quali la descrizione di riepilogo contiene la parola Aerodynamic. La query restituisce il valore ProductID e l'elemento <`Summary`> relativi a tali prodotti.  
  
```  
--The product model description document uses  
--namespaces. The WHERE clause uses the exit()  
--method of the xml data type. Inside the exit method,  
--the XQuery contains()function is used to  
--determine whether the <Summary> text contains the word  
--Aerodynamic.   
  
USE AdventureWorks  
GO  
WITH XMLNAMESPACES ('http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd)  
SELECT ProductModelID, CatalogDescription.query('  
      <Prod>  
         { /pd:ProductDescription/@ProductModelID }  
         { /pd:ProductDescription/pd:Summary }  
      </Prod>  
 ') as Result  
FROM Production.ProductModel  
where CatalogDescription.exist('  
   /pd:ProductDescription/pd:Summary//text()  
    [contains(., "Aerodynamic")]') = 1  
```  
  
 Risultati  
  
 `ProductModelID Result`  
  
 `-------------- ---------`  
  
 `28     <Prod ProductModelID="28">`  
  
 `<pd:Summary xmlns:pd=`  
  
 `"http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">`  
  
 `<p1:p xmlns:p1="http://www.w3.org/1999/xhtml">`  
  
 `A TRUE multi-sport bike that offers streamlined riding and`  
  
 `a revolutionary design. Aerodynamic design lets you ride with`  
  
 `the pros, and the gearing will conquer hilly roads.</p1:p>`  
  
 `</pd:Summary>`  
  
 `</Prod>`  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni XQuery per il tipo di dati XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
