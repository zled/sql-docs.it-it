---
title: DATEDIFF_BIG (Transact-SQL) | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATEDIFF_BIG
- DATEDIFF_BIG_TSQL
helpviewer_keywords:
- DATEDIFF_BIG function [SQL Server]
- dates [SQL Server]. functions
- date and time [SQL Server], DATEDIFF_BIG
- functions [SQL Server], time
- functions [SQL Server], date and time
- time [SQL Server], functions
ms.assetid: 19ac1693-3cfa-400d-bf83-20a9cb46599a
caps.latest.revision: 7
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 80c1228faeaaa4012afc0fd27992a2f5cf389f6e
ms.openlocfilehash: 08f27953aac5fa36f1b38e243d8465f57458dafe
ms.contentlocale: it-it
ms.lasthandoff: 10/12/2017

---
# <a name="datediffbig-transact-sql"></a>DATEDIFF_BIG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Restituisce il conteggio (intero grande con segno) dell'oggetto specificato *datepart* limiti incrociati tra specificato *startdate* e *enddate*.
  
Per una panoramica di tutti i [!INCLUDE[tsql](../../includes/tsql-md.md)] tipi di dati data e ora e funzioni, vedere [data e ora i tipi di dati e funzioni &#40; Transact-SQL &#41; ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
  
DATEDIFF_BIG ( datepart , startdate , enddate )  
```  
  
## <a name="arguments"></a>Argomenti  
*parte di una data*  
È la parte di *startdate* e *enddate* che specifica il tipo di limite sovrapposto. La tabella seguente elenca tutti validi *datepart* argomenti. Variabili definite dall'utente equivalenti non sono valide.
  
|*parte di una data*|Abbreviazioni|  
|---|---|
|**anno**|**yy, yyyy**|  
|**trimestre**|**q, q**|  
|**mese**|**mm, m**|  
|**DayOfYear**|**dy, y**|  
|**giorno**|**GG, d**|  
|**settimana**|**wk, ww**|  
|**ora**|**hh**|  
|**minuto**|**mi, n**|  
|**secondo**|**ss, s**|  
|**millisecondi**|**MS**|  
|**microsecondi**|**MCS**|  
|**nanosecondi**|**NS**|  
  
*startdate*  
È un'espressione che può essere risolta in un **ora**, **data**, **smalldatetime**, **datetime**, **datetime2**, o **datetimeoffset** valore. *Data* può essere un'espressione, l'espressione di colonna, variabile definita dall'utente o stringa letterale. *StartDate* viene sottratto *enddate*.  
Per evitare ambiguità, esprimere gli anni nel formato a quattro cifre. Per informazioni sull'anno a due cifre, vedere [configurare l'anno a due cifre cutoff Server Configuration Option](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md).
  
*EndDate*  
Vedere *startdate*.
  
## <a name="return-type"></a>Tipo restituito  
 Firmato   
        **bigint**  
  
## <a name="return-value"></a>Valore restituito  
Restituisce il numero (bigint con segno) dei limiti di datepart specificato trascorsi tra la data di inizio e data di fine.
-   Ogni *datepart* e relative abbreviazioni restituiscono lo stesso valore.  
  
Se il valore restituito è compreso nell'intervallo per **bigint** (-9.223.372.036.854.775.808 a 9.223.372.036.854.775.807), viene restituito un errore. Per **millisecondo**, la differenza massima tra *startdate* e *enddate* è 24 giorni, 20 ore, 31 minuti e 23,647 secondi. Per **secondo**, la differenza massima è 68 anni.
  
Se *startdate* e *enddate* è assegnato un valore di ora e *datepart* non è un'ora *datepart*, viene restituito 0.
  
Componente di differenza di un fuso orario *startdate* o *endate* non viene utilizzato nel calcolo del valore restituito.
  
Poiché [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md) accurato solo al minuto, quando un **smalldatetime** valore viene utilizzato per *startdate* o *enddate*, secondi e i millisecondi vengono sempre impostati su 0 nel valore restituito.
  
Se a una variabile di tipo data viene assegnato solo un valore di tipo ora, il valore della parte mancante della data viene impostato sul valore predefinito: 1900-01-01. Se a una variabile di tipo ora viene assegnato solo un valore di tipo data, il valore della parte mancante dell'ora viene impostato sul valore predefinito: 00.00.00. Se il valore *startdate* o *enddate* avere solo una parte del tempo e l'altro solo una parte della data, ora mancano e parti della data sono impostate sui valori predefiniti.
  
Se *startdate* e *enddate* sono di tipi data diversi e due con altre parti di ora o la precisione frazionaria dei secondi rispetto a altra, le parti mancanti di altro sono impostate su 0.
  
## <a name="datepart-boundaries"></a>limiti di DatePart
Le istruzioni seguenti hanno lo stesso *startdate* e lo stesso *endate*. Queste date sono adiacenti e differiscono di 0,0000001 secondi. La differenza tra il *startdate* e *endate* in ogni istruzione attraversa un limite di calendario o di ora della relativa *datepart*. Ciascuna istruzione restituisce 1. Se per questo esempio vengono usati anni diversi e se entrambi *startdate* e *endate* sono nella stessa settimana di calendario, il valore restituito per **settimana** sarà 0.

```sql
SELECT DATEDIFF_BIG(year, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(quarter, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(month, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(dayofyear, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(day, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(week, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(hour, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(minute, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(second, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(millisecond, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
```
  
## <a name="remarks"></a>Osservazioni  
DATEDIFF_BIG può essere utilizzato nell'elenco di selezione, WHERE, HAVING, GROUP BY e ORDER clausole BY.
  
DATEDIFF_BIG esegue in modo implicito il cast di valori letterali stringa come un **datetime2** tipo. Ciò significa che DATEDIFF_BIG non supporta il formato AGM se la data viene passata come stringa. È necessario eseguire il cast esplicito la stringa da un **datetime** o **smalldatetime** tipo da utilizzare il formato AGM.
  
Specifica di SET DATEFIRST non influisce su DATEDIFF_BIG. DATEDIFF_BIG utilizza sempre la domenica come primo giorno della settimana per garantire che la funzione è deterministica.
  
## <a name="examples"></a>Esempi  
Gli esempi seguenti usano tipi diversi di espressioni come argomenti per il *startdate* e *enddate* parametri.
  
### <a name="specifying-columns-for-startdate-and-enddate"></a>Specifica di colonne per startdate ed enddate  
Nell'esempio seguente viene calcolato il numero di limiti di giorno che si sovrappongono tra le date di due colonne in una tabella.
  
```sql
CREATE TABLE dbo.Duration  
    (  
    startDate datetime2  
    ,endDate datetime2  
    );  
INSERT INTO dbo.Duration(startDate,endDate)  
    VALUES('2007-05-06 12:10:09','2007-05-07 12:10:09');  
SELECT DATEDIFF_BIG(day,startDate,endDate) AS 'Duration'  
FROM dbo.Duration;  
-- Returns: 1  
```  
  
Per molti altri esempi, vedere gli esempi strettamente correlati in [DATEDIFF &#40; Transact-SQL &#41; ](../../t-sql/functions/datediff-transact-sql.md).
  
## <a name="see-also"></a>Vedere anche
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[DATEDIFF &#40; Transact-SQL &#41;](../../t-sql/functions/datediff-transact-sql.md)
  
  

