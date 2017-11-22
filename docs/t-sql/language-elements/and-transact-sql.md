---
title: E (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- AND_TSQL
- AND
dev_langs: TSQL
helpviewer_keywords:
- values [SQL Server], TRUE
- TRUE
- AND, about AND operators
- AND
- combining expressions
ms.assetid: b61d7f8d-5a51-49b7-91dd-f6190a5a0fb9
caps.latest.revision: "26"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 34014541d124b0226218012d907fd2f99e0b1610
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="and-transact-sql"></a>AND (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Combina due espressioni booleane e restituisce **TRUE** quando entrambe le espressioni sono **TRUE**. Quando più di un operatore logico viene utilizzato in un'istruzione di **AND** operatori vengono valutati per primi. È tuttavia possibile modificare l'ordine di valutazione tramite l'utilizzo delle parentesi.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
boolean_expression AND boolean_expression  
```  
  
## <a name="arguments"></a>Argomenti  
 *boolean_expression*  
 È qualsiasi [espressione](../../t-sql/language-elements/expressions-transact-sql.md) che restituisce un valore booleano: **TRUE**, **FALSE**, o **sconosciuto**.  
  
## <a name="result-types"></a>Tipi restituiti  
 **Boolean**  
  
## <a name="result-value"></a>Valore restituito  
 Restituisce TRUE quando entrambe le espressioni sono TRUE.  
  
## <a name="remarks"></a>Osservazioni  
 Nella tabella seguente vengono illustrati i risultati dei confronti eseguiti tra valori TRUE e FALSE tramite l'operatore AND.  
  
||TRUE|FALSE|UNKNOWN|  
|------|----------|-----------|-------------|  
|**TRUE**|TRUE|FALSE|UNKNOWN|  
|**FALSE**|FALSE|FALSE|FALSE|  
|**SCONOSCIUTO**|UNKNOWN|FALSE|UNKNOWN|  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-the-and-operator"></a>A. Utilizzo dell'operatore AND  
 Nell'esempio seguente vengono selezionate le informazioni sui dipendenti che dispongono sia del titolo di `Marketing Assistant` e di oltre `41` ore di ferie disponibili.  
  
```  
-- Uses AdventureWorks  
  
SELECT  BusinessEntityID, LoginID, JobTitle, VacationHours   
FROM HumanResources.Employee  
WHERE JobTitle = 'Marketing Assistant'  
AND VacationHours > 41 ;  
```  
  
### <a name="b-using-the-and-operator-in-an-if-statement"></a>B. Utilizzo dell'operatore AND in un'istruzione IF  
 Negli esempi seguenti viene mostrato come utilizzare AND in un'istruzione IF. Nella prima istruzione, sia `1 = 1` sia `2 = 2` sono true; pertanto il risultato è true. Nel secondo esempio, l'argomento `2 = 17` è false; pertanto il risultato è false.  
  
```  
IF 1 = 1 AND 2 = 2  
BEGIN  
   PRINT 'First Example is TRUE'  
END  
ELSE PRINT 'First Example is FALSE';  
GO  
  
IF 1 = 1 AND 2 = 17  
BEGIN  
   PRINT 'Second Example is TRUE'  
END  
ELSE PRINT 'Second Example is FALSE' ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni predefinite &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [Operatori &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [IN &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)  
  
  
