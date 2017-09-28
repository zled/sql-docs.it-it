---
title: TIMEFROMPARTS (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TIMEFROMPARTS_TSQL
- TIMEFROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- TIMEFROMPARTS function
ms.assetid: 786c65a1-2b3f-4e4b-82b6-4940d62f3801
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 43e6b8f2d234e0b2dd11299c56f1c6b9d0e06518
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="timefromparts-transact-sql"></a>TIMEFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Restituisce un **ora** valore per il tempo specificato e con precisione specificata.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
TIMEFROMPARTS ( hour, minute, seconds, fractions, precision )  
```  
  
## <a name="arguments"></a>Argomenti  
 *ora*  
 Espressione intera che specifica le ore.  
  
 *minuto*  
 Espressione intera che specifica i minuti.  
  
 *secondi*  
 Espressione intera che specifica i secondi.  
  
 *frazioni*  
 Espressione intera che specifica le frazioni.  
  
 *precisione*  
 Valore letterale integer che specifica la precisione del **ora** valore da restituire.  
  
## <a name="return-types"></a>Tipi restituiti  
 **tempo (** *precisione* **)**  
  
## <a name="remarks"></a>Osservazioni  
 TIMEROMPARTS restituisce un valore relativo all'ora completamente inizializzato. Se gli argomenti non sono validi, viene generato un errore. Se un parametro è Null, viene restituito Null. Tuttavia, se il *precisione* argomento è null, allora viene generato un errore.  
  
 Il *frazioni* argomento varia a seconda di *precisione* argomento. Ad esempio, se *precisione* è 7, quindi ogni frazione rappresenta 100 nanosecondi, mentre se *precisione* è 3, quindi ogni frazione rappresenta un millisecondo. Se il valore di *precisione* è zero, il valore di *frazioni* deve inoltre essere uguale a zero; in caso contrario, viene generato un errore.  
  
 Questa funzione può essere eseguita in modalità remota in server [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] e versioni successive, ma non in server con versioni precedenti a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-simple-example-without-fractions-of-a-second"></a>A. Esempio semplice senza frazioni di un secondo  
  
```  
SELECT TIMEFROMPARTS ( 23, 59, 59, 0, 0 ) AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
--------------------  
23:59:59.0000000  
  
(1 row(s) affected)  
```  
  
### <a name="b-example-with-fractions-of-a-second"></a>B. Esempio con frazioni di un secondo  
 Nell'esempio seguente viene illustrato l'utilizzo del *frazioni* e *precisione* parametri:  
  
1.  Quando *frazioni* ha un valore pari a 5 e *precisione* ha un valore pari a 1, quindi il valore di *frazioni* rappresenta 5/10 di secondo.  
  
2.  Quando *frazioni* ha un valore pari a 50 e *precisione* ha un valore pari a 2, quindi il valore di *frazioni* rappresenta 50/100 di secondo.  
  
3.  Quando *frazioni* ha un valore pari a 500 e *precisione* ha un valore pari a 3, quindi il valore di *frazioni* rappresenta 500/1000 di un secondo.  
  
```tsql  
SELECT TIMEFROMPARTS ( 14, 23, 44, 5, 1 );  
SELECT TIMEFROMPARTS ( 14, 23, 44, 50, 2 );  
SELECT TIMEFROMPARTS ( 14, 23, 44, 500, 3 );  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------------  
14:23:44.5  
  
(1 row(s) affected)  
  
----------------  
14:23:44.50  
  
(1 row(s) affected)  
  
----------------  
14:23:44.500  
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-simple-example-without-fractions-of-a-second"></a>C. Esempio semplice senza frazioni di un secondo  
  
```  
SELECT TIMEFROMPARTS ( 23, 59, 59, 0, 0 ) AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
--------------------  
23:59:59.0000000  
  
(1 row(s) affected)  
```  
  
### <a name="d-example-with-fractions-of-a-second"></a>D. Esempio con frazioni di un secondo  
 Nell'esempio seguente viene illustrato l'utilizzo del *frazioni* e *precisione* parametri:  
  
1.  Quando *frazioni* ha un valore pari a 5 e *precisione* ha un valore pari a 1, quindi il valore di *frazioni* rappresenta 5/10 di secondo.  
  
2.  Quando *frazioni* ha un valore pari a 50 e *precisione* ha un valore pari a 2, quindi il valore di *frazioni* rappresenta 50/100 di secondo.  
  
3.  Quando *frazioni* ha un valore pari a 500 e *precisione* ha un valore pari a 3, quindi il valore di *frazioni* rappresenta 500/1000 di un secondo.  
  
```tsql  
SELECT TIMEFROMPARTS ( 14, 23, 44, 5, 1 );  
SELECT TIMEFROMPARTS ( 14, 23, 44, 50, 2 );  
SELECT TIMEFROMPARTS ( 14, 23, 44, 500, 3 );  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------------  
14:23:44.5  
  
(1 row(s) affected)  
  
----------------  
14:23:44.50  
  
(1 row(s) affected)  
  
----------------  
14:23:44.500  
  
(1 row(s) affected)  
```  
  
  


