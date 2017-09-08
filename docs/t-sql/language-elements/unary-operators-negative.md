---
title: '- (Negativo) (Transact-SQL) | Documenti Microsoft'
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
- negative
dev_langs:
- TSQL
helpviewer_keywords:
- '- (negative)'
- negative operator (-)
- negative values
ms.assetid: d6c14d14-d379-403b-82db-c197ad58c896
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 47a9eb729127e53dc3ee72fe5353ad536c56d922
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="unary-operators---negative"></a>Operatori unari - negativo
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce il valore negativo del valore di un'espressione numerica (operatore unario). Gli operatori unari eseguono un'operazione in una sola espressione di un tipo di dati della categoria numerici.   
  
|Operatore|Significato|  
|--------------|-------------|  
|[+ (positivo)](../../t-sql/language-elements/unary-operators-positive.md)|Valore numerico positivo.|  
|[- (negativo)](../../t-sql/language-elements/unary-operators-negative.md)|Valore numerico negativo.|  
|[~ (NOT bit per bit)](../../t-sql/language-elements/bitwise-not-transact-sql.md)|Restituisce il complemento a uno del numero.|  
  
 Gli operatori + (positivo) e - (negativo) possono essere utilizzati in qualsiasi espressione di un tipo di dati della categoria numerici. L'operatore ~ (NOT bit per bit) può essere utilizzato solo in espressioni di un tipo di dati della categoria integer. 
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
- numeric_expression  
```  
  
## <a name="arguments"></a>Argomenti  
 *numeric_expression*  
 È qualsiasi [espressione](../../t-sql/language-elements/expressions-transact-sql.md) uno qualsiasi dei tipi di dati di categoria di tipi di dati numerici, tranne la data e ora categoria.  
  
## <a name="result-types"></a>Tipi restituiti  
 Restituisce il tipo di dati di *numeric_expression*, ad eccezione del fatto che un unsigned **tinyint** espressioni in un **smallint** risultato.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-setting-a-variable-to-a-negative-value"></a>A. Impostazione di una variabile su un valore negativo  
 Nell'esempio seguente viene impostata una variabile su un valore negativo.  
  
```  
USE tempdb;  
GO  
DECLARE @MyNumber decimal(10,2);  
SET @MyNumber = -123.45;  
SELECT @MyNumber AS NegativeValue;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
NegativeValue  
---------------------------------------  
-123.45  
  
(1 row(s) affected)  
  
```  
  
### <a name="b-changing-a-variable-to-a-negative-value"></a>B. Modifica di una variabile su un valore negativo  
 Nell'esempio seguente viene modificata una variabile su un valore negativo.  
  
```  
USE tempdb;  
GO  
DECLARE @Num1 int;  
SET @Num1 = 5;  
SELECT @Num1 AS VariableValue, -@Num1 AS NegativeValue;  
GO  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
VariableValue NegativeValue  
------------- -------------  
5             -5  
  
(1 row(s) affected)  
  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-returning-the-negative-of-a-positive-constant"></a>C. Restituisce il valore negativo di una costante positiva  
 L'esempio seguente restituisce il valore negativo di una costante positiva.  
  
```  
USE ssawPDW;  
  
SELECT TOP (1) - 17 FROM DimEmployee;  
```  
  
 Valori di codice restituiti  
  
```  
-17  
```  
  
### <a name="d-returning-the-positive-of-a-negative-constant"></a>D. Restituisce il segno positivo di una costante negativa  
 L'esempio seguente restituisce il segno positivo di una costante negativa.  
  
```  
USE ssawPDW;  
  
SELECT TOP (1) – ( - 17) FROM DimEmployee;  
```  
  
 Valori di codice restituiti  
  
```  
17  
```  
  
### <a name="e-returning-the-negative-of-a-column"></a>E. Restituisce il corrispondente negativo di una colonna  
 L'esempio seguente restituisce il corrispondente negativo del `BaseRate` valore per ogni dipendente nel `dimEmployee` tabella.  
  
```  
USE ssawPDW;  
  
SELECT - BaseRate FROM DimEmployee;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Espressioni &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Operatori &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)  
  
  


