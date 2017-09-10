---
title: Operatori bit per bit (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 09/07/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- operators [Transact-SQL], bitwise
- bitwise operators
- bit manipulations
ms.assetid: 2b994cf5-2daa-438a-b8c7-4bd8d451ac8d
caps.latest.revision: 29
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 05976158e43d7dfafaf02289462d1537f5beeb36
ms.openlocfilehash: 5d04924a82578040f801864bb68905feebc53e94
ms.contentlocale: it-it
ms.lasthandoff: 09/08/2017

---
# <a name="bitwise-operators-transact-sql"></a>Operatori bit per bit (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gli operatori bit per bit eseguono manipolazioni di bit tra due espressioni di uno dei tipi di dati della categoria integer.  
  Operatori bit per bit convertire due valori integer a bit binari, eseguire l'operazione con AND, OR o non un'operazione su ogni bit, produce un risultato. Converte quindi il risultato in un intero.  
  
  Ad esempio, l'intero 170 converte 1010 1010 binario.
Converte l'intero 75 0100 1011 binario.

|operatore|matematiche bit per bit|
|---- |---- |
|AND <br> Se il bit in qualsiasi posizione sono entrambi pari a 1, il risultato è 1. |1010 1010 = 170 <br>0100 1011 =  75 <br>-----------------  <br> 0000 1010 =  10 |
|o <br> Se un bit in qualsiasi posizione è 1, il risultato è 1. |1010 1010 = 170 <br>0100 1011 =  75 <br>-----------------  <br> 1110 1011 = 235|
|NOT  <br> Inverte il valore di bit in ogni posizione di bit. |1010 1010 = 170 <br>----------------- <br>  0101 0101 =   85 |
  
Vedere gli argomenti seguenti:   
* [& (AND bit per bit)](../../t-sql/language-elements/bitwise-and-transact-sql.md)  
* [& = (AND bit per bit uguale a)](../../t-sql/language-elements/bitwise-and-equals-transact-sql.md)   
* [&#124; (OR bit per bit)](../../t-sql/language-elements/bitwise-or-transact-sql.md)  
* [&#124; = (OR EQUALS bit)](../../t-sql/language-elements/bitwise-or-equals-transact-sql.md)   
* [^ (OR bit per bit esclusivo)](../../t-sql/language-elements/bitwise-exclusive-or-transact-sql.md)  
* [^ = (OR esclusivo è uguale a)](../../t-sql/language-elements/bitwise-exclusive-or-equals-transact-sql.md)  
* [~ (NOT bit per bit)](../../t-sql/language-elements/bitwise-not-transact-sql.md)  
  
 Gli operandi per gli operatori bit per bit possono essere uno qualsiasi dei tipi di dati di integer o categorie di tipi di dati stringa binaria (tranne che per il **immagine** tipo di dati), ad eccezione del fatto che entrambi gli operandi non possono essere uno dei tipi di dati della stringa binaria categoria di tipi di dati. Nella tabella seguente vengono descritti i tipi di dati supportati per gli operandi.  
  
|Operando sinistro|Operando destro|  
|------------------|-------------------|  
|[binary](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)|**int**, **smallint**, o **tinyint**|  
|[bit](../../t-sql/data-types/bit-transact-sql.md)|**int**, **smallint**, **tinyint**, o **bit**|  
|[int](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|**int**, **smallint**, **tinyint**, **binario**, o **varbinary**|  
|[smallint](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|**int**, **smallint**, **tinyint**, **binario**, o **varbinary**|  
|[tinyint](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|**int**, **smallint**, **tinyint**, **binario**, o **varbinary**|  
|[varbinary](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)|**int**, **smallint**, o **tinyint**|  
  
## <a name="see-also"></a>Vedere anche  
 [Operatori &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
  
  

