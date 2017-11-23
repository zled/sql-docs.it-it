---
title: ROUND (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ROUND_TSQL
- ROUND
dev_langs: TSQL
helpviewer_keywords:
- rounding expressions
- ROUND function [Transact-SQL]
ms.assetid: 23921ed6-dd6a-4c9e-8c32-91c0d44fe4b7
caps.latest.revision: "40"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: e9cb05c7f0b00f93f2602e114de2b502b8be0213
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="round-transact-sql"></a>ROUND (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce un valore numerico arrotondato alla lunghezza o alla precisione specificata.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
ROUND ( numeric_expression , length [ ,function ] )  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
ROUND (numeric_expression , length )  
```  
  
## <a name="arguments"></a>Argomenti  
 *numeric_expression*  
 È un [espressione](../../t-sql/language-elements/expressions-transact-sql.md) di uno, categoria del tipo di dati numerici o numerici approssimativi, ad eccezione del **bit** tipo di dati.  
  
 *length*  
 La precisione a cui *numeric_expression* da arrotondare. *lunghezza* deve essere un'espressione di tipo **tinyint**, **smallint**, o **int**. Quando *lunghezza* è un numero positivo, *numeric_expression* viene arrotondato al numero di posizioni decimali specificato da *lunghezza*. Quando *lunghezza* è un numero negativo, *numeric_expression* viene arrotondato a sinistra del separatore decimale, come specificato da *lunghezza*.  
  
 *function*  
 Tipo di operazione da eseguire. *funzione* deve essere **tinyint**, **smallint**, o **int**. Quando *funzione* viene omesso oppure è un valore pari a 0 (impostazione predefinita), *numeric_expression* viene arrotondato. Quando un valore diverso da è specificato 0, *numeric_expression* viene troncato.  
  
## <a name="return-types"></a>Tipi restituiti  
 Restituisce i tipi di dati seguenti:  
  
|Risultato dell'espressione|Tipo restituito|  
|-----------------------|-----------------|  
|**tinyint**|**int**|  
|**smallint**|**int**|  
|**int**|**int**|  
|**bigint**|**bigint**|  
|**decimale** e **numerico** categoria (p, s)|**Decimal (p, s)**|  
|**Money** e **smallmoney** categoria|**money**|  
|**float** e **reale** categoria|**float**|  
  
## <a name="remarks"></a>Osservazioni  
 La funzione ROUND restituisce sempre un valore. Se *lunghezza* è negativo e maggiore del numero di cifre prima del separatore decimale, la funzione ROUND restituisce 0.  
  
|Esempio|Risultato|  
|-------------|------------|  
|ROUND (748.58 ASSUME, -4)|0|  
  
 Funzione ROUND restituisce arrotondato *numeric_expression*, indipendentemente dal tipo di dati, quando *lunghezza* è un numero negativo.  
  
|Esempi|Risultato|  
|--------------|------------|  
|ROUND (748.58 ASSUME, -1)|750.00|  
|ROUND (748.58 ASSUME, -2)|700.00|  
|ROUND(748.58, -3)|Genera un overflow aritmetico, perché 748.58 assume il valore decimal(5,2), tramite il quale non può essere restituito 1000.00.|  
|Per un arrotondamento fino a 4 cifre, modificare il tipo di dati di input. Esempio:<br /><br /> `SELECT ROUND(CAST (748.58 AS decimal (6,2)),-3);`|1000.00|  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-round-and-estimates"></a>A. Utilizzo della funzione ROUND e delle stime  
 In questo esempio vengono utilizzate due espressioni per illustrare che con la funzione `ROUND` l'ultima cifra è sempre una stima.  
  
```  
SELECT ROUND(123.9994, 3), ROUND(123.9995, 3);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------- -----------  
123.9990    124.0000      
```  
  
### <a name="b-using-round-and-rounding-approximations"></a>B. Utilizzo della funzione ROUND e delle approssimazioni di arrotondamento  
 Nell'esempio seguente vengono illustrati l'arrotondamento e l'approssimazione.  
  
```  
SELECT ROUND(123.4545, 2), ROUND(123.45, -2);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  

 ```
--------  ----------
123.45    100.00
```
  
### <a name="c-using-round-to-truncate"></a>C. Utilizzo della funzione ROUND per ottenere un troncamento  
 Nell'esempio seguente vengono utilizzate due istruzioni `SELECT` per illustrare la differenza tra l'arrotondamento e il troncamento. La prima istruzione arrotonda il risultato, la seconda lo tronca.  
  
```  
SELECT ROUND(150.75, 0);  
GO  
SELECT ROUND(150.75, 0, 1);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--------  
151.00  
  
(1 row(s) affected)  
  
--------  
150.00  
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-using-round-and-estimates"></a>D. Utilizzo della funzione ROUND e delle stime  
 In questo esempio vengono utilizzate due espressioni per illustrare che con la funzione `ROUND` l'ultima cifra è sempre una stima.  
  
```  
SELECT ROUND(123.994999, 3), ROUND(123.995444, 3);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  

 ```
--------  ---------
123.995000    123.995444
```
  
## <a name="see-also"></a>Vedere anche  
 [CEILING &#40; Transact-SQL &#41;](../../t-sql/functions/ceiling-transact-sql.md)   
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Espressioni &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [FLOOR &#40; Transact-SQL &#41;](../../t-sql/functions/floor-transact-sql.md)   
 [Funzioni matematiche &#40; Transact-SQL &#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)  
  
  

