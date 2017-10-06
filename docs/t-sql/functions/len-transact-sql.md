---
title: LEN (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 09/03/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- LEN
- LEN_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- LEN function
- characters [SQL Server], number of
- number of characters
ms.assetid: fa20fee4-884d-4301-891a-c03e901345ae
caps.latest.revision: 47
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 532b996c23a8f9746a52434d78783da2a24d1add
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="len-transact-sql"></a>LEN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce il numero di caratteri dell'espressione stringa specificata, esclusi gli spazi vuoti finali.  
  
> [!NOTE]  
>  Per restituire il numero di byte utilizzati per rappresentare un'espressione, utilizzare il [DATALENGTH](../../t-sql/functions/datalength-transact-sql.md) (funzione).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
LEN ( string_expression )  
```  
  
## <a name="arguments"></a>Argomenti  
 *string_expression*  
 È la stringa [espressione](../../t-sql/language-elements/expressions-transact-sql.md) da valutare. *string_expression* può essere una costante, variabile o colonna di tipo carattere o binario.  
  
## <a name="return-types"></a>Tipi restituiti  
 **bigint** se *espressione* è il **varchar (max)**, **nvarchar (max)** o **varbinary (max)** tipi di dati. in caso contrario, **int**.  
  
 Se si utilizzano le regole di confronto SC, il valore intero restituito considererà le coppie di surrogati UTF-16 come un singolo carattere. Per altre informazioni, vedere [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="remarks"></a>Osservazioni  
 LEN esclude gli spazi vuoti finali. Se questo è un problema, provare a usare il [DATALENGTH &#40; Transact-SQL &#41; ](../../t-sql/functions/datalength-transact-sql.md) funzione tagli la stringa. Se l'elaborazione di una stringa unicode, DATALENGTH restituirà due volte il numero di caratteri. Nell'esempio seguente viene illustrato LEN e DATALENGTH con uno spazio finale.  
  
```  
DECLARE @v1 varchar(40),  
    @v2 nvarchar(40);  
SELECT   
@v1 = 'Test of 22 characters ',   
@v2 = 'Test of 22 characters ';  
SELECT LEN(@v1) AS [varchar LEN] , DATALENGTH(@v1) AS [varchar DATALENGTH];  
SELECT LEN(@v2) AS [nvarchar LEN], DATALENGTH(@v2) AS [nvarchar DATALENGTH];  
  
```  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono selezionati il numero di caratteri e i dati in `FirstName` per le persone residenti in `Australia`. In questo esempio viene utilizzato il database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
SELECT LEN(FirstName) AS Length, FirstName, LastName   
FROM Sales.vIndividualCustomer  
WHERE CountryRegionName = 'Australia';  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 L'esempio seguente restituisce il numero di caratteri nella colonna `FirstName` e i nomi e cognomi dei dipendenti nella `Australia`.  
  
```  
-- Uses AdventureWorks  
  
SELECT DISTINCT LEN(FirstName) AS FNameLength, FirstName, LastName   
FROM dbo.DimEmployee AS e  
INNER JOIN dbo.DimGeography AS g   
    ON e.SalesTerritoryKey = g.SalesTerritoryKey   
WHERE EnglishCountryRegionName = 'Australia';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
FNameLength  FirstName  LastName  
-----------  ---------  ---------------  
4            Lynn       Tsoflias
```  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Funzioni stringa &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)   
 [DATALENGTH &#40; Transact-SQL &#41;](../../t-sql/functions/datalength-transact-sql.md)   
 [SINISTRA &#40; Transact-SQL &#41;](../../t-sql/functions/left-transact-sql.md)   
 [DESTRA &#40; Transact-SQL &#41;](../../t-sql/functions/right-transact-sql.md)  
  
  



