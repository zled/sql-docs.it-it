---
title: REVERSE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- REVERSE_TSQL
- REVERSE
dev_langs:
- TSQL
helpviewer_keywords:
- expressions [SQL Server], reverse
- REVERSE function
- reverse character expressions
ms.assetid: 555d8877-7cc7-4955-ae2c-6215aca313b7
caps.latest.revision: 46
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8696a2cff3589b9b756e2ddd9cc1160b465b70d8
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="reverse-transact-sql"></a>REVERSE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce un valore stringa in ordine inverso.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
REVERSE ( string_expression )  
```  
  
## <a name="arguments"></a>Argomenti  
 *string_expression*  
 *string_expression* è un [espressione](../../t-sql/language-elements/expressions-transact-sql.md) di un tipo di dati string o binary. *string_expression* può essere una costante, variabile o colonna di tipo carattere o binario.  
  
## <a name="return-types"></a>Tipi restituiti  
 **varchar** o **nvarchar**  
  
## <a name="remarks"></a>Osservazioni  
 *string_expression* deve essere di un tipo di dati che è implicitamente convertibile in **varchar**. In caso contrario, utilizzare [CAST](../../t-sql/functions/cast-and-convert-transact-sql.md) per convertire esplicitamente *string_expression*.  
  
## <a name="supplementary-characters-surrogate-pairs"></a>Caratteri supplementari (coppie di surrogati)  
 Quando si utilizzano le regole di confronto SC, la funzione REVERSE non invertirà l'ordine di due metà di una coppia di surrogati.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituiti tutti i nomi dei contatti con i caratteri in ordine inverso. In questo esempio viene utilizzato il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
SELECT FirstName, REVERSE(FirstName) AS Reverse  
FROM Person.Person  
WHERE BusinessEntityID < 5  
ORDER BY FirstName;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `FirstName      Reverse`  
  
 `-------------- --------------`  
  
 `Ken            neK`  
  
 `Rob            boR`  
  
 `Roberto        otreboR`  
  
 `Terri          irreT`  
  
 `(4 row(s) affected)`  
  
 Nell'esempio seguente vengono restituiti i caratteri in una variabile in ordine inverso.  
  
```  
DECLARE @myvar varchar(10);  
SET @myvar = 'sdrawkcaB';  
SELECT REVERSE(@myvar) AS Reversed ;  
GO  
```  
  
 Nell'esempio seguente viene eseguita una conversione implicita da un **int** del tipo di dati in **varchar** tipo di dati e quindi inverte il risultato.  
  
```  
SELECT REVERSE(1234) AS Reversed ;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 L'esempio seguente restituisce i nomi di tutti i database e i nomi con i caratteri invertito.  
  
```  
SELECT name, REVERSE(name) FROM sys.databases;  
GO  
```  
  
 Nell'esempio seguente vengono restituiti i caratteri in una variabile in ordine inverso.  
  
```  
DECLARE @myvar varchar(10);  
SET @myvar = 'sdrawkcaB';  
SELECT REVERSE(@myvar) AS Reversed ;  
GO  
```  
  
 Nell'esempio seguente viene eseguita una conversione implicita da un **int** del tipo di dati in **varchar** tipo di dati e quindi inverte il risultato.  
  
```  
SELECT REVERSE(1234) AS Reversed ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CAST e CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Funzioni stringa &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  
  


