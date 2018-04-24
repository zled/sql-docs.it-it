---
title: DATEDIFF_BIG (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 173daacfd95ec63789dde878e960d5a8b820a27c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="datediffbig-transact-sql"></a>DATEDIFF_BIG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Restituisce il conteggio (intero lungo con segno) dei limiti *datepart* specificati incrociati con i valori di *startdate* e *enddate* specificati.
  
Per una panoramica di tutti i tipi di dati e delle funzioni di data e ora [!INCLUDE[tsql](../../includes/tsql-md.md)], vedere [Funzioni e tipi di dati di data e ora &#40;Transact-SQL&#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
  
DATEDIFF_BIG ( datepart , startdate , enddate )  
```  
  
## <a name="arguments"></a>Argomenti  
*datepart*  
Parte di *startdate* e *enddate* che specifica il tipo di limite superato. Nella tabella seguente sono elencati tutti gli argomenti *datepart* validi. Variabili definite dall'utente equivalenti non sono valide.
  
|*datepart*|Abbreviazioni|  
|---|---|
|**year**|**yy, yyyy**|  
|**quarter**|**qq, q**|  
|**month**|**mm, m**|  
|**dayofyear**|**dy, y**|  
|**day**|**dd, d**|  
|**week**|**wk, ww**|  
|**hour**|**hh**|  
|**minute**|**mi, n**|  
|**second**|**ss, s**|  
|**millisecond**|**ms**|  
|**microsecond**|**mcs**|  
|**nanosecond**|**ns**|  
  
*startdate*  
Espressione che può essere risolta in un valore **time**, **date**, **smalldatetime**, **datetime**, **datetime2** o **datetimeoffset**. *date* può essere costituito da un'espressione, un'espressione di colonna, una variabile definita dall'utente o un valore letterale stringa. *startdate* viene sottratto da *enddate*.  
Per evitare ambiguità, esprimere gli anni nel formato a quattro cifre. Per altre informazioni sugli anni a due cifre, vedere [Configurare l'opzione di configurazione del server Cambio data per anno a due cifre](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md).
  
*enddate*  
Vedere *startdate*.
  
## <a name="return-type"></a>Tipo restituito  
 Firmato   
        **bigint**  
  
## <a name="return-value"></a>Valore restituito  
Restituisce il conteggio (intero lungo con segno) dei limiti datepart specificati incrociati con i valori di startdate e enddate specificati.
-   Ogni elemento *datepart* e le relative abbreviazioni restituiscono lo stesso valore.  
  
Se il valore restituito non è compreso nell'intervallo per **bigint** (da -9.223.372.036.854.775.808 a 9.223.372.036.854.775.807), viene restituito un errore. Per **millisecond**, la differenza massima tra *startdate* e *enddate* è 24 giorni, 20 ore, 31 minuti e 23,647 secondi. Per **second**, la differenza massima è 68 anni.
  
Se sia a *startdate* che a *enddate* è stato assegnato solo un valore orario e *datepart* non è un oggetto *datepart* orario, viene restituito 0.
  
Per calcolare il valore restituito non viene usato un componente di differenza di fuso orario di *startdate* o *endate*.
  
Dal momento che [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md) garantisce la precisione solo a livello di minuti, quando viene usato un valore **smalldatetime** per *startdate* o *enddate*, i secondi e i millisecondi vengono sempre impostati su 0 nel valore restituito.
  
Se a una variabile di tipo data viene assegnato solo un valore di tipo ora, il valore della parte mancante della data viene impostato sul valore predefinito: 1900-01-01. Se a una variabile di tipo ora viene assegnato solo un valore di tipo data, il valore della parte mancante dell'ora viene impostato sul valore predefinito: 00.00.00. Se *startdate* o *enddate* hanno solo rispettivamente la parte dell'ora e la parte della data, le parti mancanti vengono impostate sui valori predefiniti.
  
Se i valori *startdate* e *enddate* sono di tipi data diversi e uno di questi comprende un numero maggiore di parti di ora o offre una precisione in secondi frazionari maggiore, le parti mancanti dell'altro valore vengono impostate su 0.
  
## <a name="datepart-boundaries"></a>Limiti di datepart
Le istruzioni seguenti comprendono gli stessi valori *startdate* e *endate*. Queste date sono adiacenti e differiscono di 0,0000001 secondi. La differenza tra *startdate* e *endate* in ogni istruzione oltrepassa un limite di calendario o di ora del rispettivo valore *datepart*. Ciascuna istruzione restituisce 1. Se per questo esempio vengono usati anni diversi e se *startdate* e *endate* fanno parte della stessa settimana di calendario, il valore restituito per **week** è 0.

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
  
## <a name="remarks"></a>Remarks  
L'elemento DATEDIFF può essere usato in un elenco SELECT e nelle clausole WHERE, HAVING, GROUP BY e ORDER BY.
  
DATEDIFF_BIG consente di eseguire in modo implicito il cast di valori letterali stringa come tipo di dati **datetime2**. Pertanto, DATEDIFF_BIG non supporta il formato AGM se la data viene passata come stringa. Per usare il formato AGM è necessario eseguire il cast della stringa in modo esplicito in un tipo **datetime** o **smalldatetime**.
  
La specifica di SET DATEFIRST non influisce su DATEDIFFF_BIG. In DATEDIFFF_BIG viene usata sempre la domenica come primo giorno della settimana per garantire che la funzione sia deterministica.
  
## <a name="examples"></a>Esempi  
Negli esempi seguenti vengono usati tipi diversi di espressioni come argomenti per i parametri *startdate* e *enddate*.
  
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
  
Per molti altri esempi, vedere gli esempi strettamente correlati in [DATEDIFF &#40;Transact-SQL&#41;](../../t-sql/functions/datediff-transact-sql.md).
  
## <a name="see-also"></a>Vedere anche
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[DATEDIFF &#40;Transact-SQL&#41;](../../t-sql/functions/datediff-transact-sql.md)
  
  
