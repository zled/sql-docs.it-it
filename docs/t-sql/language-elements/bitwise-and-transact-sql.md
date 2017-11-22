---
title: '&amp;(AND bit per bit) (Transact-SQL) | Documenti Microsoft'
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
- bitwise
- '&'
- '&_TSQL'
dev_langs: TSQL
helpviewer_keywords:
- AND, bitwise AND
- '& (bitwise AND)'
- bitwise AND (&)
ms.assetid: 20275755-4fa7-47b1-a9be-ac85606d63b0
caps.latest.revision: "42"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: d249ca1552197a5fb7e53540c40e70c864d134bb
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="amp-bitwise-and-transact-sql"></a>&amp;(AND bit per bit) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Esegue un'operazione con AND logico bit per bit tra due valori integer.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
expression & expression  
```  
  
## <a name="arguments"></a>Argomenti  
 *espressione*  
 È qualsiasi [espressione](../../t-sql/language-elements/expressions-transact-sql.md) di uno qualsiasi dei tipi di dati di categoria di tipi di dati integer, o **bit**, o **binario** o **varbinary** dati tipi. *espressione* viene considerato come un numero binario per l'operazione bit per bit.  
  
> [!NOTE]  
>  In un'operazione bit per bit, solo uno *espressione* può essere del **binario** o **varbinary** tipo di dati.  
  
## <a name="result-types"></a>Tipi restituiti  
 **int** se i valori di input sono **int**.  
  
 **smallint** se i valori di input sono **smallint**.  
  
 **tinyint** se i valori di input sono **tinyint** o **bit**.  
  
## <a name="remarks"></a>Osservazioni  
 Il  **&**  operatore bit per bit esegue un'operazione con AND logico bit per bit tra due espressioni, considerando tutti i corrispondenti bit entrambe le espressioni. I bit del risultato vengono impostati su 1 se, e solo se, il valore del bit in fase di risoluzione di entrambe le espressioni di input è uguale a 1. In caso contrario, il bit del risultato viene impostato su 0.  
  
 Se le espressioni sinistra e destra sono tipi di dati integer diverso (ad esempio, sinistra *espressione* è **smallint** e destra *espressione* è  **int**), l'argomento del tipo di dati più piccolo viene convertito nel tipo di dati più grande. In questo caso, il **smallint***espressione* viene convertito in un **int**.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata una tabella utilizzando il **int** digitare per archiviare i valori e inserisce i due valori in una riga di dati.  
  
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
  
 La query esegue l'operazione con AND bit per bit tra le colonne `a_int_value` e `b_int_value`.  
  
```  
SELECT a_int_value & b_int_value  
FROM bitwise;  
GO  
```  
  
 Set di risultati:  
  
```  
-----------   
10            
  
(1 row(s) affected)  
```  
  
 La rappresentazione binaria di 170 (`a_int_value` o `A`) è `0000 0000 1010 1010`. La rappresentazione binaria di 75 (`b_int_value` o `B`) è `0000 0000 0100 1011`. L'esecuzione dell'operazione con AND bit per bit su questi valori genera il risultato binario `0000 0000 0000 1010`, corrispondente al valore decimale 10.  
  
```  
(A & B)  
0000 0000 1010 1010  
0000 0000 0100 1011  
-------------------  
0000 0000 0000 1010  
```  
  
  
## <a name="see-also"></a>Vedere anche  
 [Espressioni &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Operatori &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Operatori bit per bit &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-operators-transact-sql.md)   
 [& = &#40; Assegnazione AND bit per bit &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-and-equals-transact-sql.md)   
 [Composta operatori &#40; Transact-SQL &#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  


