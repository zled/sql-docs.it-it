---
title: DATETIMEOFFSETFROMPARTS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 5549f258e758cc91a228d5fee707120b57963d46
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33053130"
---
# <a name="datetimeoffsetfromparts-transact-sql"></a>DATETIMEOFFSETFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Restituisce un valore **datetimeoffset** per la data e l'ora specificata e con gli offset e la precisione indicati.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
DATETIMEOFFSETFROMPARTS ( year, month, day, hour, minute, seconds, fractions, hour_offset, minute_offset, precision )  
```  
  
## <a name="arguments"></a>Argomenti  
*year*  
Espressione intera che specifica un anno.
  
*month*  
Espressione intera che specifica un mese.
  
*day*  
Espressione intera che specifica un giorno.
  
*hour*  
Espressione intera che specifica le ore.
  
*minute*  
Espressione intera che specifica i minuti.
  
*secondi*  
Espressione intera che specifica i secondi.
  
*fractions*  
Espressione intera che specifica le frazioni.
  
*hour_offset*  
Espressione intera che specifica la parte di ora della differenza di fuso orario.
  
*minute_offset*  
Espressione intera che specifica la parte di minuto della differenza di fuso orario.
  
*precisione*  
Valore letterale intero che specifica la precisione del valore **datetimeoffset** da restituire.
  
## <a name="return-types"></a>Tipi restituiti
**datetimeoffset(** *precision* **)**
  
## <a name="remarks"></a>Remarks  
**DATETIMEOFFSETFROMPARTS** restituisce un tipo di dati **datetimeoffset** completamente inizializzato. Gli argomenti dell'offset vengono utilizzati per rappresentare la differenza di fuso orario. Se tali argomenti vengono omessi, si presuppone che la differenza di fuso orario sia 00.00, ovvero che non sia presente. Se invece vengono specificati, entrambi gli argomenti devono essere presenti e avere segno positivo o negativo. Se *minute_offset* viene specificato senza *hour_offset*, viene generato un errore. Se altri argomenti non sono validi, viene generato un errore. Se gli argomenti obbligatori sono Null, viene restituito un valore Null. Se tuttavia l'argomento *precision* è Null viene generato un errore.
  
L'argomento *fractions* dipende dall'argomento *precision*. Se ad esempio *precision* è 7, ogni frazione rappresenta 100 nanosecondi, mentre se *precision* è 3 ogni frazione rappresenta un millisecondo. Se il valore di *precision* è zero, anche il valore di *fractions* deve essere zero. In caso contrario, viene generato un errore.
  
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
L'esempio seguente illustra l'uso dei parametri *fractions* e *precision*:
1.   Se *fractions* ha valore 5 e *precision* ha valore 1, il valore di *fractions* corrisponde a 5/10 di secondo.  
1.   Se *fractions* ha valore 50 e *precision* ha valore 2, il valore di *fractions* corrisponde a 50/100 di secondo.  
1.   Se *fractions* ha valore 500 e *precision* ha valore 3, il valore di *fractions* corrisponde a 500/1000 di secondo.  
  
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
[AT TIME ZONE &#40;Transact-SQL&#41;](../../t-sql/queries/at-time-zone-transact-sql.md)
  
  


