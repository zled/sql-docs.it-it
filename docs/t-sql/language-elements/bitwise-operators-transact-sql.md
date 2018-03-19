---
title: Operatori bit per bit (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 09/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
- operators [Transact-SQL], bitwise
- bitwise operators
- bit manipulations
ms.assetid: 2b994cf5-2daa-438a-b8c7-4bd8d451ac8d
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: b0706080c0a878987fab8d2cc5f0c1677f43309b
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="bitwise-operators-transact-sql"></a>Operatori bit per bit (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gli operatori bit per bit eseguono manipolazioni di bit tra due espressioni di uno dei tipi di dati della categoria integer.  
  Gli operatori bit per bit convertono due valori Integer in bit binari ed eseguono l'operazione AND, OR o NOT su ogni bit, producendo un risultato. Quindi il risultato viene convertito in un valore Integer.  
  
  Ad esempio il valore Integer 170 viene convertito nel valore binario 1010 1010.
il valore Integer 75 viene convertito nel valore binario 0100 1011.

|operatore|elaborazione bit per bit|
|---- |---- |
|AND <br> Se i bit in qualsiasi posizione sono entrambi 1, il risultato è 1. |1010 1010 = 170 <br>0100 1011 = 75 <br>-----------------  <br> 0000 1010 = 10 |
|o <br> Se uno dei due bit in qualsiasi posizione è 1, il risultato è 1. |1010 1010 = 170 <br>0100 1011 = 75 <br>-----------------  <br> 1110 1011 = 235|
|NOT  <br> Inverte il valore bit in ogni posizione di bit. |1010 1010 = 170 <br>----------------- <br>  0101 0101 = 85 |
  
Vedere gli argomenti seguenti:   
* [& &#40;AND bit per bit&#41;](../../t-sql/language-elements/bitwise-and-transact-sql.md)  
* [&= &#40;Assegnazione AND bit per bit&#41;](../../t-sql/language-elements/bitwise-and-equals-transact-sql.md)   
* [&#124; &#40;OR bit per bit&#41;](../../t-sql/language-elements/bitwise-or-transact-sql.md)  
* [&#124;= &#40;Assegnazione OR bit per bit&#41;](../../t-sql/language-elements/bitwise-or-equals-transact-sql.md)   
* [^ &#40;OR esclusivo bit per bit&#41;](../../t-sql/language-elements/bitwise-exclusive-or-transact-sql.md)  
* [^= &#40;Assegnazione OR esclusivo bit per bit&#41;](../../t-sql/language-elements/bitwise-exclusive-or-equals-transact-sql.md)  
* [~ &#40;NOT bit per bit&#41;](../../t-sql/language-elements/bitwise-not-transact-sql.md)  
  
 Il tipo di dati degli operandi per gli operatori bit per bit può essere uno dei tipi di dati delle categorie Integer o stringa binaria (tranne il tipo **image**). Non è tuttavia consentito che entrambi gli operandi siano di un tipo della categoria stringa binaria. Nella tabella seguente vengono descritti i tipi di dati supportati per gli operandi.  
  
|Operando sinistro|Operando destro|  
|------------------|-------------------|  
|[binary](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)|**int**, **smallint** o **tinyint**|  
|[bit](../../t-sql/data-types/bit-transact-sql.md)|**int**, **smallint**, **tinyint** o **bit**|  
|[int](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|**int**, **smallint**, **tinyint**, **binary** o **varbinary**|  
|[smallint](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|**int**, **smallint**, **tinyint**, **binary** o **varbinary**|  
|[tinyint](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|**int**, **smallint**, **tinyint**, **binary** o **varbinary**|  
|[varbinary](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)|**int**, **smallint** o **tinyint**|  
  
## <a name="see-also"></a>Vedere anche  
 [Operatori &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Operatori composti &#40;Transact-SQL&#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)   
  
