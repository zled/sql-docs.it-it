---
title: DATETIMEOFFSETFROMPARTS (Transact-SQL) | Documenti Microsoft
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
- DATETIMEOFFSETFROMPARTS_TSQL
- DATETIMEOFFSETFROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- DATETIMEOFFSETFROMPARTS function
ms.assetid: 463da1f4-b4b6-45a3-9a95-ea1f99575542
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: fe203e646f1ec0cb9732ff63ba8ee0dbe38c899a
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="datetimeoffsetfromparts-transact-sql"></a>DATETIMEOFFSETFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Restituisce un **datetimeoffset** valore per la data e ora specificate e con l'offset specificati e la precisione.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
DATETIMEOFFSETFROMPARTS ( year, month, day, hour, minute, seconds, fractions, hour_offset, minute_offset, precision )  
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
  
*minuto*  
Espressione intera che specifica i minuti.
  
*secondi*  
Espressione intera che specifica i secondi.
  
*frazioni*  
Espressione intera che specifica le frazioni.
  
*hour_offset*  
Espressione intera che specifica la parte di ora della differenza di fuso orario.
  
*minute_offset*  
Espressione intera che specifica la parte di minuto della differenza di fuso orario.
  
*precisione*  
Valore letterale integer che specifica la precisione del **datetimeoffset** valore da restituire.
  
## <a name="return-types"></a>Tipi restituiti
**DateTimeOffset (** *precisione* **)**
  
## <a name="remarks"></a>Osservazioni  
**DATETIMEOFFSETFROMPARTS** restituisce un oggetto completamente inizializzato **datetimeoffset** tipo di dati. Gli argomenti dell'offset vengono utilizzati per rappresentare la differenza di fuso orario. Se tali argomenti vengono omessi, si presuppone che la differenza di fuso orario sia 00.00, ovvero che non sia presente. Se invece vengono specificati, entrambi gli argomenti devono essere presenti e avere segno positivo o negativo. Se *minute_offset* viene specificato senza *hour_offset*, viene generato un errore. Se altri argomenti non sono validi, viene generato un errore. Se gli argomenti obbligatori sono Null, viene restituito un valore Null. Tuttavia, se il *precisione* argomento è null, allora viene generato un errore.
  
Il *frazioni* argomento varia a seconda di *precisione* argomento. Ad esempio, se *precisione* è 7, quindi ogni frazione rappresenta 100 nanosecondi, mentre se *precisione* è 3, quindi ogni frazione rappresenta un millisecondo. Se il valore di *precisione* è zero, il valore di *frazioni* deve inoltre essere uguale a zero; in caso contrario, viene generato un errore.
  
Questa funzione può essere eseguita in modalità remota in server con [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e versioni successive, ma non in server con versioni precedenti a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
  
## <a name="examples"></a>Esempi  
  
### <a name="a-simple-example-without-fractions-of-a-second"></a>A. Esempio semplice senza frazioni di un secondo  
  
```sql
SELECT DATETIMEOFFSETFROMPARTS ( 2010, 12, 31, 14, 23, 23, 0, 12, 0, 7 ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
-------------------------------------------  
2010-12-07 00:00:00.0000000 +00:00  
  
(1 row(s) affected)  
```  
  
### <a name="b-example-with-fractions-of-a-second"></a>B. Esempio con frazioni di un secondo  
Nell'esempio seguente viene illustrato l'utilizzo del *frazioni* e *precisione* parametri:
1.   Quando *frazioni* ha un valore pari a 5 e *precisione* ha un valore pari a 1, quindi il valore di *frazioni* rappresenta 5/10 di secondo.  
1.   Quando *frazioni* ha un valore pari a 50 e *precisione* ha un valore pari a 2, quindi il valore di *frazioni* rappresenta 50/100 di secondo.  
1.   Quando *frazioni* ha un valore pari a 500 e *precisione* ha un valore pari a 3, quindi il valore di *frazioni* rappresenta 500/1000 di un secondo.  
  
```sql
SELECT DATETIMEOFFSETFROMPARTS ( 2011, 8, 15, 14, 30, 00, 5, 12, 30, 1 );  
SELECT DATETIMEOFFSETFROMPARTS ( 2011, 8, 15, 14, 30, 00, 50, 12, 30, 2 );  
SELECT DATETIMEOFFSETFROMPARTS ( 2011, 8, 15, 14, 30, 00, 500, 12, 30, 3 );  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
----------------------------------  
2011-08-15 14:30:00.5 +12:30  
  
(1 row(s) affected)  
  
----------------------------------  
2011-08-15 14:30:00.50 +12:30  
  
(1 row(s) affected)  
  
----------------------------------  
2011-08-15 14:30:00.500 +12:30  
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-simple-example-without-fractions-of-a-second"></a>C. Esempio semplice senza frazioni di un secondo  
  
```sql
SELECT DATETIMEOFFSETFROMPARTS ( 2010, 12, 31, 14, 23, 23, 0, 12, 0, 7 ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
-------------------------------------------  
2010-12-07 00:00:00.0000000 +00:00  
  
(1 row(s) affected)  
```  
  
### <a name="d-example-with-fractions-of-a-second"></a>D. Esempio con frazioni di un secondo  
Nell'esempio seguente viene illustrato l'utilizzo del *frazioni* e *precisione* parametri:
1.  Quando *frazioni* ha un valore pari a 5 e *precisione* ha un valore pari a 1, quindi il valore di *frazioni* rappresenta 5/10 di secondo.  
1.   Quando *frazioni* ha un valore pari a 50 e *precisione* ha un valore pari a 2, quindi il valore di *frazioni* rappresenta 50/100 di secondo.  
1.   Quando *frazioni* ha un valore pari a 500 e *precisione* ha un valore pari a 3, quindi il valore di *frazioni* rappresenta 500/1000 di un secondo.  
  
```sql
SELECT DATETIMEOFFSETFROMPARTS ( 2011, 8, 15, 14, 30, 00, 5, 12, 30, 1 );  
SELECT DATETIMEOFFSETFROMPARTS ( 2011, 8, 15, 14, 30, 00, 50, 12, 30, 2 );  
SELECT DATETIMEOFFSETFROMPARTS ( 2011, 8, 15, 14, 30, 00, 500, 12, 30, 3 );  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
----------------------------------  
2011-08-15 14:30:00.5 +12:30  
  
(1 row(s) affected)  
  
----------------------------------  
2011-08-15 14:30:00.50 +12:30  
  
(1 row(s) affected)  
  
----------------------------------  
2011-08-15 14:30:00.500 +12:30  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vedere anche
[datetimeoffset &#40;Transact-SQL&#41;](../../t-sql/data-types/datetimeoffset-transact-sql.md)  
[FUSO orario &AMP; #40; Transact-SQL &#41;](../../t-sql/queries/at-time-zone-transact-sql.md)
  
  



