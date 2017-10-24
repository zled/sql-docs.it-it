---
title: Funzione UPPER-case (XQuery) | Documenti Microsoft
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
- upper-case
- upper-case Function (XQuery)
ms.assetid: 5bd01ad2-7adf-48fb-bf42-41e200419d37
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 18643d9c41fd78cc8f01ec4e5dcb607b73a5bf0a
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="functions-on-string-values---upper-case"></a>Funzioni su valori stringa - lettere maiuscole
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Questa funzione converte ogni carattere di *$arg* equivalente maiuscolo. La modalità di conversione dei caratteri nell'equivalente maiuscolo viene specificata dalla conversione binaria di maiuscole e minuscole di Microsoft Windows per i punti di codice Unicode. Questo standard è diverso dal mapping per lo standard dei punti di codice Unicode.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
fn:upper-case($arg as xs:string?) as xs:string  
```  
  
## <a name="arguments"></a>Argomenti  
  
|||  
|-|-|  
|Nome|Definizione|  
|*$arg*|Valore della stringa da convertire in lettere maiuscole.|  
  
## <a name="remarks"></a>Osservazioni  
 Se il valore di *$arg* è vuoto, viene restituita una stringa di lunghezza zero.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-changing-a-string-to-upper-case"></a>A. Conversione di una stringa in lettere maiuscole  
 L'esempio seguente modifica la stringa di input ' abcDEF! @4' in lettere maiuscole.  
  
```  
DECLARE @x xml = N'abcDEF!@4';  
SELECT @x.value('fn:upper-case(/text()[1])', 'nvarchar(10)');  
```  
  
### <a name="b-search-for-a-specific-character-string"></a>B. Ricerca di una stringa di caratteri specifica  
 In questo esempio viene illustrato come utilizzare la funzione upper-case per eseguire un ricerca senza distinzione tra maiuscole e minuscole.  
  
```  
USE AdventureWorks  
GO  
--WITH XMLNAMESPACES clause specifies the namespace prefix  
--to use.   
WITH XMLNAMESPACES ('http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd)  
--The XQuery contains() function is used to determine whether  
--any of the text nodes below the <Summary> element contain  
--the word 'frame'. The upper-case() function is used to make  
--the search case-insensitive.  
  
SELECT ProductModelID, CatalogDescription.query('  
      <Prod>  
         { /pd:ProductDescription/@ProductModelID }  
         { /pd:ProductDescription/pd:Summary }  
      </Prod>  
 ') as Result  
FROM Production.ProductModel  
where CatalogDescription.exist('  
/pd:ProductDescription/pd:Summary//text()[  
          contains(upper-case(.), "FRAME")]')  = 1  
```  
  
 [!INCLUDE[ssResult](../includes/ssresult-md.md)]  
  
 `ProductModelID Result`  
  
 `-------------- ---------`  
  
 `19     <Prod ProductModelID="19">`  
  
 `<pd:Summary xmlns:pd="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">`  
  
 `<p1:p xmlns:p1="http://www.w3.org/1999/xhtml">Our top-of-the-line competition mountain bike.`  
  
 `Performance-enhancing options include the innovative HL Frame,`  
  
 `super-smooth front suspension, and traction for all terrain.`  
  
 `</p1:p>`  
  
 `</pd:Summary>`  
  
 `</Prod>`  
  
 `25     <Prod ProductModelID="25">`  
  
 `<pd:Summary xmlns:pd="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">`  
  
 `<p1:p xmlns:p1="http://www.w3.org/1999/xhtml">This bike is ridden by race winners. Developed with the`  
  
 `Adventure Works Cycles professional race team, it has a extremely light`  
  
 `heat-treated aluminum frame, and steering that allows precision control.`  
  
 `</p1:p>`  
  
 `</pd:Summary>`  
  
 `</Prod>`  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni XQuery per il tipo di dati XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  

