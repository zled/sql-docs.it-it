---
title: + = (Concatenazione di stringhe e assegnazione) (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 12/07/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- concatenate strings
- string concatenation
- += (concatenate operator)
ms.assetid: 4aaeaab7-9b2b-48e0-8487-04ed672ebcb1
caps.latest.revision: "15"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 6c1716e014de1c99e4b3560d55674f0d82797c03
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="-string-concatenation-assignment-transact-sql"></a>+ = (Assegnazione di concatenazione di stringhe) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Concatena due stringhe e imposta la stringa sul risultato dell'operazione. Ad esempio, se una variabile @x è uguale a 'Adventure', quindi @x + = 'Works' accetta il valore originale di @x, aggiunta di 'Works' per la stringa e imposta @x nuovo valore 'AdventureWorks'.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
expression += expression  
```  
  
## <a name="arguments"></a>Argomenti  
 *espressione*  
 È qualsiasi [espressione](../../t-sql/language-elements/expressions-transact-sql.md) di uno qualsiasi dei tipi di dati carattere.  
  
## <a name="result-types"></a>Tipi restituiti  
 Restituisce il tipo di dati definito per la variabile.  
  
## <a name="remarks"></a>Osservazioni  
 IMPOSTARE @v1 + = 'expression' equivale a SET @v1 = @v1 + ('expression'). Inoltre, impostare @v1 = @v2 + @v3 + @v4 equivale a SET @v1 = (@v2 + @v3) + @v4.  
  
 L'operatore += non può essere utilizzato senza una variabile. Il codice riportato di seguito comporta, ad esempio, la generazione di un errore:  
  
```  
SELECT 'Adventure' += 'Works'  
```  
  
## <a name="examples"></a>Esempi  
### <a name="a-concatenation-using--operator"></a>A. Concatenazione utilizzando l'operatore + =
 Nell'esempio seguente viene eseguita una concatenazione utilizzando l'operatore `+=`.  
  
```  
DECLARE @v1 varchar(40);  
SET @v1 = 'This is the original.';  
SET @v1 += ' More text.';  
PRINT @v1;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `This is the original. More text.`  
  
### <a name="b-order-of-evaluation-while-concatenating-using--operator"></a>B. Ordine di valutazione durante la concatenazione utilizzando l'operatore + =
Nell'esempio seguente consente di concatenare più stringhe per formare una stringa lunga e quindi tenta di calcolare la lunghezza della stringa finale. In questo esempio viene illustrato l'ordine e il troncamento delle regole di valutazione, quando si utilizza l'operatore di concatenazione. 

```
DECLARE @x varchar(4000) = replicate('x', 4000)
DECLARE @z varchar(8000) = replicate('z',8000)
DECLARE @y varchar(max);
 
SET @y = '';
SET @y += @x + @z;
SELECT LEN(@y) AS Y; -- 8000
 
SET @y = '';
SET @y = @y + @x + @z;
SELECT LEN(@y) AS Y; -- 12000
 
SET @y = '';
SET @y = @y +(@x + @z);
SELECT LEN(@y) AS Y; -- 8000
-- or
SET @y = '';
SET @y = @x + @z + @y;
SELECT LEN(@y) AS Y; -- 8000
GO
```
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 Y       
 ------- 
 8000 
  
 (1 row(s) affected) 
  
    
 Y       
 ------- 
 12000 
  
 (1 row(s) affected) 

 Y       
 ------- 
 8000 
  
 (1 row(s) affected) 
  
 Y       
 ------- 
 8000 
  
 (1 row(s) affected)
  ```   
   
## <a name="see-also"></a>Vedere anche  
 [Operatori &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [+ = &#40; Aggiungi assegnazione &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/add-equals-transact-sql.md)   
 [+ &#40; Concatenazione di stringhe &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/string-concatenation-transact-sql.md)  
  
  
