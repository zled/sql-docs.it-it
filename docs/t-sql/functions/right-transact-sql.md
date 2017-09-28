---
title: RIGHT (Transact-SQL) | Documenti Microsoft
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
- RIGHT_TSQL
- RIGHT
dev_langs:
- TSQL
helpviewer_keywords:
- rightmost character of expression
- RIGHT function
- character strings [SQL Server], RIGHT
ms.assetid: 43f1fe1f-aa18-47e3-ba20-e03e32254a6d
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 19dcdea078648b6ff41e08fcf82c9a4c705abe4c
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="right-transact-sql"></a>RIGHT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce la parte finale di una stringa di caratteri, di lunghezza pari al numero di caratteri specificato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
RIGHT ( character_expression , integer_expression )  
```  
  
## <a name="arguments"></a>Argomenti  
 *character_expression*  
 È un [espressione](../../t-sql/language-elements/expressions-transact-sql.md) di dati carattere o binario. *character_expression* può essere una costante, variabile o colonna. *character_expression* può essere qualsiasi tipo di dati, eccetto **testo** o **ntext**, che può essere convertito in modo implicito in **varchar** o  **nvarchar**. In caso contrario, utilizzare il [CAST](../../t-sql/functions/cast-and-convert-transact-sql.md) funzione per convertire esplicitamente *character_expression*.  
  
 *integer_expression*  
 È un numero intero positivo che specifica il numero di caratteri di *character_expression* verranno restituiti. Se *integer_expression* è negativo, viene restituito un errore. Se *integer_expression* è di tipo **bigint** e contiene un valore elevato, *character_expression* deve essere di un tipo di dati di grandi dimensioni, ad esempio **varchar(max)**.  
  
## <a name="return-types"></a>Tipi restituiti  
 Restituisce **varchar** quando *character_expression* è un tipo di dati carattere non Unicode.  
  
 Restituisce **nvarchar** quando *character_expression* è un tipo di dati carattere Unicode.  
  
## <a name="supplementary-characters-surrogate-pairs"></a>Caratteri supplementari (coppie di surrogati)  
 Quando si utilizzano le regole di confronto SC, la funzione RIGHT considera una coppia di surrogati UTF-16 come un singolo carattere. Per altre informazioni, vedere [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-right-with-a-column"></a>R: con una colonna di destra  
 Nell'esempio seguente vengono restituiti gli ultimi cinque caratteri del nome di ciascuna persona nel database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
SELECT RIGHT(FirstName, 5) AS 'First Name'  
FROM Person.Person  
WHERE BusinessEntityID < 5  
ORDER BY FirstName;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
First Name  
----------  
Ken  
Terri  
berto  
Rob  
  
(4 row(s) affected)  
  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-using-right-with-a-column"></a>B. Con una colonna di destra  
 L'esempio seguente restituisce gli ultimi cinque caratteri di ogni cognome nel `DimEmployee` tabella.  
  
```  
-- Uses AdventureWorks  
  
SELECT RIGHT(LastName, 5) AS Name  
FROM dbo.DimEmployee  
ORDER BY EmployeeKey;  
```  
  
 Set di risultati parziale:  
  
 `Name`  
  
 `-----`  
  
 `lbert`  
  
 `Brown`  
  
 `rello`  
  
 `lters`  
  
### <a name="c-using-right-with-a-character-string"></a>C. Utilizzo di RIGHT con una stringa di caratteri  
 L'esempio seguente usa `RIGHT` per restituire i primi due caratteri della stringa di caratteri `abcdefg`.  
  
```  
-- Uses AdventureWorks  
  
SELECT TOP(1) RIGHT('abcdefg',2) FROM dbo.DimProduct;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `-------`  
  
 `fg`  
  
## <a name="see-also"></a>Vedere anche  
 [CAST e CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Funzioni stringa &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  
  


