---
title: LOG10 (Transact-SQL) | Documenti Microsoft
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
- LOG10
- LOG10_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- float expressions
- LOG10 function
- base-10 logarithms
- logarithm of expression
ms.assetid: 1eb7fb34-1937-4a39-a936-f5c0c7c7e06f
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d8cc5b0ef6af319e55744a3ca373f0e6b11e230b
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="log10-transact-sql"></a>LOG10 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce il logaritmo in base 10 dell'oggetto specificato **float** espressione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
LOG10 ( float_expression )  
```  
  
## <a name="arguments"></a>Argomenti  
 *argomento float_expression*  
 È un [espressione](../../t-sql/language-elements/expressions-transact-sql.md) di tipo **float** o di un tipo che può essere convertito in modo implicito in **float**.  
  
## <a name="return-types"></a>Tipi restituiti  
 **float**  
  
## <a name="remarks"></a>Osservazioni  
 Le funzioni LOG10 e POWER sono inversamente correlate. Ad esempio, 10 ^ LOG10 (*n*) =  *n* .  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-calculating-the-base-10-logarithm-for-a-variable"></a>A. Calcolo del logaritmo in base 10 per una variabile.  
 Nell'esempio seguente viene calcolato il valore `LOG10` della variabile specificata.  
  
```  
DECLARE @var float;  
SET @var = 145.175643;  
SELECT 'The LOG10 of the variable is: ' + CONVERT(varchar,LOG10(@var));  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
The LOG10 of the variable is: 2.16189      
  
(1 row(s) affected)  
```  
  
### <a name="b-calculating-the-result-of-raising-a-base-10-logarithm-to-a-specified-power"></a>B. Calcolo del risultato dell'elevamento di un logaritmo in base 10 alla potenza specificata.  
 Nell'esempio seguente viene restituito il risultato dell'elevamento di un logaritmo in base 10 alla potenza specificata.  
  
```  
SELECT POWER (10, LOG10(5));   
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
-----------  
5  
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-calculating-the-base-10-logarithm-for-a-value"></a>C: calcolare il logaritmo in base 10 di un valore.  
 L'esempio seguente calcola il `LOG10` del valore specificato.  
  
```  
SELECT LOG10(145.175642);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `-------------------`  
  
 `2.16`  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni matematiche &#40; Transact-SQL &#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)   
 [POWER &#40; Transact-SQL &#41;](../../t-sql/functions/power-transact-sql.md)   
 [LOG &#40; Transact-SQL &#41;](../../t-sql/functions/log-transact-sql.md)  
  
  


