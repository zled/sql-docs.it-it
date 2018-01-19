---
title: Operatori bit per bit (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 09/07/2017
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
- operators [Transact-SQL], bitwise
- bitwise operators
- bit manipulations
ms.assetid: 2b994cf5-2daa-438a-b8c7-4bd8d451ac8d
caps.latest.revision: "29"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 17ef615ab6b82cb9407871fcf8ee7a312ce22613
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="bitwise-operators-transact-sql"></a>Operatori bit per bit (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gli operatori bit per bit eseguono manipolazioni di bit tra due espressioni di uno dei tipi di dati della categoria integer.  
  Operatori bit per bit convertire due valori integer a bit binari, eseguire l'operazione con AND, OR o non un'operazione su ogni bit, produce un risultato. Converte quindi il risultato in un intero.  
  
  Ad esempio, l'intero 170 converte 1010 1010 binario.
Converte l'intero 75 0100 1011 binario.

|operatore|matematiche bit per bit|
|---- |---- |
|AND <br> Se il bit in qualsiasi posizione sono entrambi pari a 1, il risultato è 1. |1010 1010 = 170 <br>0100 1011 =  75 <br>-----------------  <br> 0000 1010 =  10 |
|OPPURE <br> Se un bit in qualsiasi posizione è 1, il risultato è 1. |1010 1010 = 170 <br>0100 1011 =  75 <br>-----------------  <br> 1110 1011 = 235|
|NOT  <br> Inverte il valore di bit in ogni posizione di bit. |1010 1010 = 170 <br>----------------- <br>  0101 0101 =   85 |
  
Vedere gli argomenti seguenti:   
* [& &#40; AND bit per bit &#41;](../../t-sql/language-elements/bitwise-and-transact-sql.md)  
* [& = &#40; Assegnazione AND bit per bit &#41;](../../t-sql/language-elements/bitwise-and-equals-transact-sql.md)   
* [&#124; &#40; OR bit per bit &#41;](../../t-sql/language-elements/bitwise-or-transact-sql.md)  
* [&#124; = &#40; OR bit per bit assegnazione &#41;](../../t-sql/language-elements/bitwise-or-equals-transact-sql.md)   
* [^ &#40; Bit per bit esclusivo &#41;](../../t-sql/language-elements/bitwise-exclusive-or-transact-sql.md)  
* [^ = &#40; Bit per bit esclusivo assegnazione &#41;](../../t-sql/language-elements/bitwise-exclusive-or-equals-transact-sql.md)  
* [~ &#40; NOT bit per bit &#41;](../../t-sql/language-elements/bitwise-not-transact-sql.md)  
  
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
 [Operators &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Composta operatori &#40; Transact-SQL &#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)   
  
