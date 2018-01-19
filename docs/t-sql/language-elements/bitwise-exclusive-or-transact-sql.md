---
title: ^ (OR bit per bit esclusivo) (Transact-SQL) | Documenti Microsoft
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
- ^_TSQL
- Bitwise Exclusive OR
- Exclusive
- ^
- bitwise
- OR
dev_langs: TSQL
helpviewer_keywords:
- ^ (bitwise exclusive OR operator)
- OR operator
- exclusive OR mathematical operations
- bitwise exclusive OR (^)
ms.assetid: f38f0ad4-46d0-40ea-9851-0f928fda5293
caps.latest.revision: "44"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 897e37f19765ac43c881f2646e0bf0cc91d3205a
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="-bitwise-exclusive-or-transact-sql"></a>^ (OR esclusivo bit per bit) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Esegue un'operazione con OR esclusivo bit per bit tra due valori integer.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
expression ^ expression  
```  
  
## <a name="arguments"></a>Argomenti  
 *espressione*  
 È qualsiasi [espressione](../../t-sql/language-elements/expressions-transact-sql.md) uno qualsiasi dei tipi di dati della categoria di tipi di dati integer, o **bit**, o **binario** o **varbinary** tipi di dati. *espressione* viene considerato come un numero binario per l'operazione bit per bit.  
  
> [!NOTE]  
>  Un solo *espressione* può essere del **binario** o **varbinary** il tipo di dati in un'operazione bit per bit.  
  
## <a name="result-types"></a>Tipi restituiti  
 **int** se i valori di input sono **int**.  
  
 **smallint** se i valori di input sono **smallint**.  
  
 **tinyint** se i valori di input sono **tinyint**.  
  
## <a name="remarks"></a>Osservazioni  
 Il  **^**  operatore bit per bit esegue un OR esclusivo logico bit per bit tra due espressioni, considerando tutti i corrispondenti bit entrambe le espressioni. I bit nel risultato sono impostati su 1 se il valore di un solo bit (per il bit in fase di risoluzione) nelle espressioni di input è uguale a 1. Se entrambi i bit hanno valore 0 o 1, il bit del risultato corrispondente verrà impostato su 0.  
  
 Se le espressioni sinistra e destra sono tipi di dati integer diverso (ad esempio, sinistra *espressione* è **smallint** e destra *espressione* è  **int**), l'argomento del tipo di dati più piccolo viene convertito nel tipo di dati più grande. In questo caso, il **smallint * * * espressione* viene convertito in un **int**.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata una tabella utilizzando il **int** digitare per archiviare i valori originali e inserisce i due valori in una riga di dati.  
  
```  
CREATE TABLE bitwise  
(   
a_int_value int NOT NULL,  
b_int_value int NOT NULL  
);  
GO  
INSERT bitwise VALUES (170, 75);  
GO  
```  
  
 La query seguente esegue l'operazione con OR esclusivo bit per bit sulle colonne `a_int_value` e `b_int_value`.  
  
```  
SELECT a_int_value ^ b_int_value  
FROM bitwise;  
GO  
```  
  
 Set di risultati:  
  
```  
-----------   
225           
  
(1 row(s) affected)  
```  
  
 La rappresentazione binaria di 170 (`a_int_value` o `A`) è `0000 0000 1010 1010`. La rappresentazione binaria di 75 (`b_int_value` o `B`) è `0000 0000 0100 1011`. L'esecuzione dell'operazione con OR esclusivo bit per bit su questi due valori genera il risultato binario `0000 0000 1110 0001`, che corrisponde al valore decimale 225.  
  
```  
(A ^ B)     
         0000 0000 1010 1010  
         0000 0000 0100 1011  
         -------------------  
         0000 0000 1110 0001  
```  
  

  
## <a name="see-also"></a>Vedere anche  
 [Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Operators &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Operatori bit per bit &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-operators-transact-sql.md)   
 [^ = &#40; Bit per bit esclusivo assegnazione &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-exclusive-or-equals-transact-sql.md)   
 [Composta operatori &#40; Transact-SQL &#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  


