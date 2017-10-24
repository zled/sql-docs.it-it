---
title: TRY_CONVERT (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TRY_CONVERT_TSQL
- TRY_CONVERT
dev_langs:
- TSQL
helpviewer_keywords:
- TRY_CONVERT function
ms.assetid: 3e6e7825-6482-4cb2-a8c2-9abc99e265a6
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0cb3854ae349b17dcdb0b0528c6415fd41b1e072
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="tryconvert-transact-sql"></a>TRY_CONVERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Restituisce un cast del valore nel tipo di dati specificato se il cast ha esito positivo. In caso contrario, restituisce Null.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
TRY_CONVERT ( data_type [ ( length ) ], expression [, style ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *data_type [(lunghezza)]*  
 Tipo di dati in cui eseguire il cast *espressione*.  
  
 *espressione*  
 Valore di cui eseguire il cast.  
  
 *stile*  
 Espressione integer che specifica il modo in **TRY_CONVERT** funzione consiste nel tradurre *espressione*.  
  
 *stile* accetta gli stessi valori di *stile* parametro del **CONVERTIRE** (funzione). Per altre informazioni, vedere [CAST and CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md).  
  
 L'intervallo di valori accettabili è determinato dal valore di *data_type*. Se *stile* è null, **TRY_CONVERT** restituisce null.  
  
## <a name="return-types"></a>Tipi restituiti  
 Restituisce un cast del valore nel tipo di dati specificato se il cast ha esito positivo. In caso contrario, restituisce Null.  
  
## <a name="remarks"></a>Osservazioni  
 **TRY_CONVERT** accetta il valore passato e tenta di convertirlo in oggetto *data_type*. Se il cast ha esito positivo, **TRY_CONVERT** restituisce il valore specificato *data_type*; se si verifica un errore, viene restituito null. Tuttavia se si richiede una conversione in modo esplicito non valido, quindi **TRY_CONVERT** genera un errore.  
  
 **TRY_CONVERT** è una parola chiave riservata nel livello di compatibilità 110 e versioni successive.  
  
 Questa funzione può essere eseguita in modalità remota in server con versione [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] e successive, ma non in server con versioni precedenti a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-tryconvert-returns-null"></a>A. TRY_CONVERT restituisce Null  
 Nell'esempio seguente viene dimostrato che TRY_CONVERT restituisce Null quando il cast non riesce.  
  
```tsql  
SELECT   
    CASE WHEN TRY_CONVERT(float, 'test') IS NULL   
    THEN 'Cast failed'  
    ELSE 'Cast succeeded'  
END AS Result;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
------------  
Cast failed  
  
(1 row(s) affected)  
```  
  
 Nell'esempio seguente viene dimostrato che l'espressione deve essere nel formato previsto.  
  
```tsql  
SET DATEFORMAT dmy;  
SELECT TRY_CONVERT(datetime2, '12/31/2010') AS Result;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
----------------------  
NULL  
  
(1 row(s) affected)  
```  
  
### <a name="b-tryconvert-fails-with-an-error"></a>B. TRY_CONVERT restituisce un errore  
 Nell'esempio seguente viene dimostrato che TRY_CONVERT restituisce un errore quando il cast non è consentito in modo esplicito.  
  
```tsql  
SELECT TRY_CONVERT(xml, 4) AS Result;  
GO  
```  
  
 Il risultato di questa istruzione è un errore perché il cast di un tipo di dati Integer non può essere eseguito nel tipo di dati xml.  
  
```  
Explicit conversion from data type int to xml is not allowed.  
```  
  
### <a name="c-tryconvert-succeeds"></a>C. TRY_CONVERT ha esito positivo  
 In questo esempio viene dimostrato che l'espressione deve essere nel formato previsto.  
  
```  
SET DATEFORMAT mdy;  
SELECT TRY_CONVERT(datetime2, '12/31/2010') AS Result;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
----------------------------------  
2010-12-31 00:00:00.0000000  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  

