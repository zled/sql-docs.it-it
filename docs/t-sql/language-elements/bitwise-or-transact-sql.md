---
title: '| (OR bit per bit) (Transact-SQL) | Documenti Microsoft'
ms.custom: 
ms.date: 01/10/2017
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
- '|'
- '|_TSQL'
- Bitwise OR
- bitwise
- OR
dev_langs: TSQL
helpviewer_keywords:
- OR operator
- bitwise OR (|)
- '| (bitwise OR operator)'
ms.assetid: 86a3b87f-9688-4eaf-a552-29f1b01d880a
caps.latest.revision: "43"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: bb22a18a1d61857afbbc17cc82f444d6551083be
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="-bitwise-or-transact-sql"></a>| (OR bit per bit) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Esegue un'operazione con OR logico bit per bit tra i due valori interi specificati convertiti in espressioni binarie in istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```   
expression | expression  
```  
  
## <a name="arguments"></a>Argomenti  
 *espressione*  
 È qualsiasi [espressione](../../t-sql/language-elements/expressions-transact-sql.md) della categoria di tipi di dati integer, o **bit**, **binario**, o **varbinary** tipi di dati. *espressione* viene considerato come un numero binario per l'operazione bit per bit.  
  
> [!NOTE]  
>  Un solo *espressione* può essere del **binario** o **varbinary** il tipo di dati in un'operazione bit per bit.  
  
## <a name="result-types"></a>Tipi restituiti  
 Restituisce un **int** se i valori di input sono **int**, **smallint** se i valori di input sono **smallint**, o un **tinyint** se i valori di input sono **tinyint**.  
  
## <a name="remarks"></a>Osservazioni  
 L'operatore | esegue un'operazione con OR logico bit per bit tra due espressioni, considerando tutti i bit corrispondenti in entrambe le espressioni. I bit nel risultato sono impostati su 1 se il valore di uno o di entrambi i bit (per il bit in fase di risoluzione) delle espressioni di input è uguale a 1. Se nessuno dei bit è uguale a 1, il bit del risultato è impostato su 0.  
  
 Se le espressioni sinistra e destra sono tipi di dati integer diverso (ad esempio, sinistra *espressione* è **smallint** e destra *espressione* è  **int**), l'argomento del tipo di dati più piccolo viene convertito nel tipo di dati più grande. In questo esempio, il **smallint * * * espressione* viene convertito in un **int**.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata una tabella con **int** tipi per mostrare i valori originali di dati e lo inserisce nella tabella in un'unica riga.  
  
```sql  
CREATE TABLE bitwise  
(   
 a_int_value int NOT NULL,  
b_int_value int NOT NULL  
);  
GO  
INSERT bitwise VALUES (170, 75);  
GO  
```  
  
 La query seguente esegue l'operatore OR bit per bit di **a_int_value** e **b_int_value** colonne.  
  
```  
SELECT a_int_value | b_int_value  
FROM bitwise;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
-----------   
235           
  
(1 row(s) affected)  
```  
  
 La rappresentazione binaria di 170 (**a_int_value** o `A`riportato di seguito) è `0000 0000 1010 1010`. La rappresentazione binaria di 75 (**b_int_value** o `B`riportato di seguito) è `0000 0000 0100 1011`. L'operazione con OR logico bit per bit eseguita su questi due valori restituisce il risultato binario `0000 0000 1110 1011`, ovvero 235 decimale.  
  
```  
(A | B)  
0000 0000 1010 1010  
0000 0000 0100 1011  
-------------------  
0000 0000 1110 1011  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Operators &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Operatori bit per bit &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-operators-transact-sql.md)   
 [&#124;= &#40;Bitwise OR Assignment&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/bitwise-or-equals-transact-sql.md)   
 [Composta operatori &#40; Transact-SQL &#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  


