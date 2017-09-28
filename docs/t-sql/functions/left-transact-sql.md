---
title: A sinistra (Transact-SQL) | Documenti Microsoft
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
- LEFT
- LEFT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- character strings [SQL Server], LEFT
- characters [SQL Server], leftmost
- LEFT function
- leftmost character of expression
ms.assetid: 44a8c71b-63d8-458b-8b5d-99d570067c3c
caps.latest.revision: 48
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0b0ec58ed9e8bbaae6f4f4ae90834f415476b039
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="left-transact-sql"></a>LEFT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce la parte iniziale di una stringa di caratteri, di lunghezza pari al numero di caratteri specificato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
LEFT ( character_expression , integer_expression )  
```  
  
## <a name="arguments"></a>Argomenti  
 *character_expression*  
 È un [espressione](../../t-sql/language-elements/expressions-transact-sql.md) di dati carattere o binario. *character_expression* può essere una costante, variabile o colonna. *character_expression* può essere qualsiasi tipo di dati, eccetto **testo** o **ntext**, che può essere convertito in modo implicito in **varchar** o  **nvarchar**. In caso contrario, utilizzare il [CAST](../../t-sql/functions/cast-and-convert-transact-sql.md) funzione per convertire esplicitamente *character_expression*.  
  
 *integer_expression*  
 È un numero intero positivo che specifica il numero di caratteri del *character_expression* verranno restituiti. Se *integer_expression* è negativo, viene restituito un errore. Se *integer_expression* è di tipo **bigint** e contiene un valore elevato, *character_expression* deve essere di un tipo di dati di grandi dimensioni, ad esempio **varchar(max)**.  
  
 Il *integer_expression* parametro conta un carattere surrogato UTF-16 come un carattere.  
  
## <a name="return-types"></a>Tipi restituiti  
 Restituisce **varchar** quando *character_expression* è un tipo di dati carattere non Unicode.  
  
 Restituisce **nvarchar** quando *character_expression* è un tipo di dati carattere Unicode.  
  
## <a name="remarks"></a>Osservazioni  
 Quando si utilizzano regole di confronto SC, il *integer_expression* parametro conta una coppia di surrogati UTF-16 come un carattere. Per altre informazioni, vedere [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-left-with-a-column"></a>A. Utilizzo di LEFT con una colonna  
 Nell'esempio seguente vengono restituiti i primi cinque caratteri di ciascun nome di prodotto nella tabella `Product` del database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
SELECT LEFT(Name, 5)   
FROM Production.Product  
ORDER BY ProductID;  
GO  
```  
  
### <a name="b-using-left-with-a-character-string"></a>B. Utilizzo di LEFT con una stringa di caratteri  
 Nell'esempio seguente viene utilizzata la funzione `LEFT` per ottenere i primi due caratteri della stringa di caratteri `abcdefg`.  
  
```  
SELECT LEFT('abcdefg',2);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--   
ab   
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-left-with-a-column"></a>C. Utilizzo di LEFT con una colonna  
 Nell'esempio seguente vengono restituiti i primi cinque caratteri di ogni nome di prodotto.  
  
```  
-- Uses AdventureWorks  
  
SELECT LEFT(EnglishProductName, 5)   
FROM dbo.DimProduct  
ORDER BY ProductKey;  
```  
  
### <a name="d-using-left-with-a-character-string"></a>D. Utilizzo di LEFT con una stringa di caratteri  
 Nell'esempio seguente viene utilizzata la funzione `LEFT` per ottenere i primi due caratteri della stringa di caratteri `abcdefg`.  
  
```  
-- Uses AdventureWorks  
  
SELECT LEFT('abcdefg',2) FROM dbo.DimProduct;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--   
ab  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CAST e CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Funzioni stringa &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  
  


