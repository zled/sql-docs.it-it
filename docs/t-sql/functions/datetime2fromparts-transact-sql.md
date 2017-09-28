---
title: DATETIME2FROMPARTS (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATETIME2FROMPARTS_TSQL
- DATETIME2FROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- DATETIME2FROMPARTS function
ms.assetid: 632b757d-d2d1-43a5-b870-792a779ae204
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c4ad800c684bcf69a52828969ca816a135901280
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="datetime2fromparts-transact-sql"></a>DATETIME2FROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Restituisce un **datetime2** valore per la data e ora specificate e con precisione specificata.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
DATETIME2FROMPARTS ( year, month, day, hour, minute, seconds, fractions, precision )  
```  
  
## <a name="arguments"></a>Argomenti  
*anno*  
Espressione intera che specifica un anno.
  
*mese*  
Espressione intera che specifica un mese.
  
*giorno*  
Espressione intera che specifica un giorno.
  
 *ora*  
Espressione intera che specifica le ore.
  
*minuto* espressione Integer che specifica i minuti.
  
*secondi*  
Espressione intera che specifica i secondi.
  
*frazioni*  
Espressione intera che specifica le frazioni.
  
*precisione*  
Valore letterale integer che specifica la precisione del **datetime2** valore da restituire.
  
## <a name="return-types"></a>Tipi restituiti
**datetime2 (** *precisione* **)**
  
## <a name="remarks"></a>Osservazioni  
**DATETIME2FROMPARTS** restituisce un oggetto completamente inizializzato **datetime2** valore. Se gli argomenti non sono validi, viene generato un errore. Se gli argomenti obbligatori sono Null, viene restituito un valore Null. Tuttavia, se il *precisione* argomento è null, allora viene generato un errore.
  
Il *frazioni* argomento varia a seconda di *precisione* argomento. Ad esempio, se *precisione* è 7, quindi ogni frazione rappresenta 100 nanosecondi, mentre se *precisione* è 3, quindi ogni frazione rappresenta un millisecondo. Se il valore di *precisione* è zero, il valore di *frazioni* deve inoltre essere uguale a zero; in caso contrario, viene generato un errore.
  
Questa funzione può essere eseguita in modalità remota in server con [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e versioni successive, ma non in server con versioni precedenti a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
  
## <a name="examples"></a>Esempi  
  
### <a name="a-simple-example-without-fractions-of-a-second"></a>A. Esempio semplice senza frazioni di un secondo  
  
```sql
SELECT DATETIME2FROMPARTS ( 2010, 12, 31, 23, 59, 59, 0, 0 ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
---------------------------  
2010-12-31 23:59:59.0000000  
  
(1 row(s) affected)  
```  
  
### <a name="b-example-with-fractions-of-a-second"></a>B. Esempio con frazioni di un secondo  
Nell'esempio seguente viene illustrato l'utilizzo del *frazioni* e *precisione* parametri:
  
1.  Quando *frazioni* ha un valore pari a 5 e *precisione* ha un valore pari a 1, quindi il valore di *frazioni* rappresenta 5/10 di secondo.  
  
2.  Quando *frazioni* ha un valore pari a 50 e *precisione* ha un valore pari a 2, quindi il valore di *frazioni* rappresenta 50/100 di secondo.  
  
3.  Quando *frazioni* ha un valore pari a 500 e *precisione* ha un valore pari a 3, quindi il valore di *frazioni* rappresenta 500/1000 di un secondo.  
  
```sql
SELECT DATETIME2FROMPARTS ( 2011, 8, 15, 14, 23, 44, 5, 1 );  
SELECT DATETIME2FROMPARTS ( 2011, 8, 15, 14, 23, 44, 50, 2 );  
SELECT DATETIME2FROMPARTS ( 2011, 8, 15, 14, 23, 44, 500, 3 );  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
----------------------  
2011-08-15 14:23:44.5  
  
(1 row(s) affected)  
  
----------------------  
2011-08-15 14:23:44.50  
  
(1 row(s) affected)  
  
----------------------  
2011-08-15 14:23:44.500  
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-simple-example-without-fractions-of-a-second"></a>C. Esempio semplice senza frazioni di un secondo  
  
```sql
SELECT DATETIME2FROMPARTS ( 2010, 12, 31, 23, 59, 59, 0, 0 ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
---------------------------  
2010-12-31 23:59:59.0000000  
  
(1 row(s) affected)  
```  
  
### <a name="d-example-with-fractions-of-a-second"></a>D. Esempio con frazioni di un secondo  
Nell'esempio seguente viene illustrato l'utilizzo del *frazioni* e *precisione* parametri:
1.  Quando *frazioni* ha un valore pari a 5 e *precisione* ha un valore pari a 1, quindi il valore di *frazioni* rappresenta 5/10 di secondo.  
1.   Quando *frazioni* ha un valore pari a 50 e *precisione* ha un valore pari a 2, quindi il valore di *frazioni* rappresenta 50/100 di secondo.  
1.   Quando *frazioni* ha un valore pari a 500 e *precisione* ha un valore pari a 3, quindi il valore di *frazioni* rappresenta 500/1000 di un secondo.  
  
```sql
SELECT DATETIME2FROMPARTS ( 2011, 8, 15, 14, 23, 44, 5, 1 );  
SELECT DATETIME2FROMPARTS ( 2011, 8, 15, 14, 23, 44, 50, 2 );  
SELECT DATETIME2FROMPARTS ( 2011, 8, 15, 14, 23, 44, 500, 3 );  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
----------------------  
2011-08-15 14:23:44.5  
  
(1 row(s) affected)  
  
----------------------  
2011-08-15 14:23:44.50  
  
(1 row(s) affected)  
  
----------------------  
2011-08-15 14:23:44.500  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vedere anche
[datetime2 &#40;Transact-SQL&#41;](../../t-sql/data-types/datetime2-transact-sql.md)
  
  


