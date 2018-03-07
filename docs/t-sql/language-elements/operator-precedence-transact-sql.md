---
title: Precedenza degli operatori (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- operators [Transact-SQL], precedence
- operator precedence [Transact-SQL]
- order of operator execution [Transact-SQL]
- precedence [SQL Server], operators
ms.assetid: f04d2439-6fff-4e4c-801f-cc62faef510a
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c9de4447c5918edbc33ec67c783272f724883e81
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="operator-precedence-transact-sql"></a>Precedenza degli operatori (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Quando in un'espressione complessa vengono utilizzati più operatori, la sequenza di esecuzione delle operazioni è determinata dalla precedenza degli operatori. L'ordine di esecuzione può modificare in modo significativo il valore restituito.  
  
 Nella tabella seguente sono indicati i livelli di precedenza degli operatori. Un operatore con livello di precedenza più alto viene valutato prima di un operatore con livello di precedenza più basso.  
  
|Level|Operatori|  
|-----------|---------------|  
|1|~ (NOT bit per bit)|  
|2|* (Moltiplicazione), / (divisione), % (modulo)|  
|3|+ (Positivo), - (negativo) + (addizione), (+ concatenazione)-(sottrazione), & (AND bit per bit), ^ (OR bit per bit esclusivo), &#124; (OR bit per bit)|  
|4|=, >, \<, > =, < =, <>,! =,! >,! < (operatori di confronto)|  
|5|NOT|  
|6|AND|  
|7|ALL, ANY, BETWEEN, IN, LIKE, OR, SOME|  
|8|= (assegnazione)|  
  
 Se due operatori di un'espressione hanno lo stesso livello di precedenza, vengono valutati da sinistra verso destra in base alla posizione nell'espressione. Nell'espressione utilizzata nell'istruzione `SET` seguente, ad esempio, l'operatore di sottrazione viene valutato prima dell'operatore di addizione.  
  
```  
DECLARE @MyNumber int;  
SET @MyNumber = 4 - 2 + 27;  
-- Evaluates to 2 + 27 which yields an expression result of 29.  
SELECT @MyNumber;  
```  
  
 Per ignorare l'ordine di precedenza predefinito degli operatori in un'espressione, è possibile utilizzare le parentesi. Tutti gli operatori racchiusi tra parentesi vengono valutati per primi in modo da ottenere un singolo valore, che verrà quindi utilizzato dagli operatori all'esterno delle parentesi.  
  
 Nell'espressione utilizzata nell'istruzione `SET` seguente, ad esempio, l'operatore di moltiplicazione ha un livello di precedenza più alto rispetto all'operatore di addizione e viene pertanto valutato per primo. Il risultato dell'espressione è `13`.  
  
```  
DECLARE @MyNumber int;  
SET @MyNumber = 2 * 4 + 5;  
-- Evaluates to 8 + 5 which yields an expression result of 13.  
SELECT @MyNumber;  
```  
  
 Nell'espressione utilizzata nell'istruzione `SET` seguente le parentesi fanno sì che venga eseguita per prima l'addizione. Il risultato dell'espressione è `18`.  
  
```  
DECLARE @MyNumber int;  
SET @MyNumber = 2 * (4 + 5);  
-- Evaluates to 2 * 9 which yields an expression result of 18.  
SELECT @MyNumber;  
```  
  
 Se in un'espressione vengono utilizzate parentesi nidificate, viene valutata per prima l'espressione più interna. Nell'esempio seguente con parentesi nidificate, l'espressione `5 - 3` corrisponde al set di parentesi più interno della struttura nidificata. Questa espressione restituisce il valore `2`. L'operatore di addizione (`+`) somma quindi questo risultato a `4`. Il valore restituito da questa operazione è `6`. Infine, il valore `6` viene moltiplicato per `2` e il risultato dell'espressione `12`.  
  
```  
DECLARE @MyNumber int;  
SET @MyNumber = 2 * (4 + (5 - 3) );  
-- Evaluates to 2 * (4 + 2) which then evaluates to 2 * 6, and   
-- yields an expression result of 12.  
SELECT @MyNumber;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Operatori logici &#40; Transact-SQL &#41;](../../t-sql/language-elements/logical-operators-transact-sql.md)   
 [Operators &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Funzioni predefinite &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)  
  
  
