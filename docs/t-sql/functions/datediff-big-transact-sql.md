---
title: DATEDIFF_BIG (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
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
ms.openlocfilehash: 39e6b56b64f6a9aafa259be99e86bb66cf75f3d1
ms.sourcegitcommit: b52b5d972b1a180e575dccfc4abce49af1a6b230
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2018
ms.locfileid: "35250044"
---
# <a name="datediffbig-transact-sql"></a>DATEDIFF_BIG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Questa funzione restituisce il numero (sotto forma di valore big integer con segno) di limiti di *datepart* specificati sovrapposti tra gli elementi *startdate* ed *enddate* indicati.
  
Vedere [Funzioni e tipi di dati di data e ora &#40;Transact-SQL&#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md) per una panoramica di tutti i tipi di dati e delle funzioni di data e ora di [!INCLUDE[tsql](../../includes/tsql-md.md)].
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
  
DATEDIFF_BIG ( datepart , startdate , enddate )  
```  
  
## <a name="arguments"></a>Argomenti  
*datepart*  
Parte di *startdate* ed *enddate* che specifica il tipo di limite superato. `DATEDIFF_BIG` non accetta equivalenti di variabili definite dall'utente. Questa tabella elenca tutti gli argomenti validi per *datepart*.

> [!NOTE]
> `DATEDIFF_BIG` non accetta equivalenti di variabili definite dall'utente come argomenti di *datepart*.
  
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
Espressione che può risolversi in uno dei valori seguenti:

+ **data**
+ **datetime**
+ **datetimeoffset**
+ **datetime2** 
+ **smalldatetime**
+ **time**

Per *date*, `DATEDIFF_BIG` accetta un'espressione di colonna, un'espressione, un valore letterale stringa o una variabile definita dall'utente. Un valore stringa deve risolversi in un elemento **datetime**. Per evitare problemi di ambiguità, esprimere gli anni nel formato a quattro cifre. `DATEDIFF_BIG` sottrae *enddate* da *startdate*. Per evitare ambiguità, esprimere gli anni nel formato a quattro cifre. Per informazioni sugli anni a due cifre, vedere [Configurare l'opzione di configurazione del server Cambio data per anno a due cifre](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md).
  
*enddate*  
Vedere *startdate*.
  
## <a name="return-type"></a>Tipo restituito  

**bigint** con segno  
  
## <a name="return-value"></a>Valore restituito  
Restituisce il numero (valore bigint con segno) dei limiti di datepart specificati sovrapposti tra i valori startdate ed enddate indicati.
-   Ogni *datepart* specifico e le rispettive abbreviazioni di tali *datepart* restituiscono lo stesso valore.  
  
Per un valore restituito esterno all'intervallo per **bigint** (da -9.223.372.036.854.775.808 a +9.223.372.036.854.775.807), `DATEDIFF_BIG` restituisce un errore. Per **millisecond**, la differenza massima tra *startdate* e *enddate* è 24 giorni, 20 ore, 31 minuti e 23,647 secondi. Per **second**, la differenza massima è 68 anni.
  
Se sia a *startdate* che a *enddate* è stato assegnato solo un valore orario e *datepart* non è un *datepart* orario, `DATEDIFF_BIG` restituisce 0.
  
Per calcolare il valore restituito, `DATEDIFF_BIG` non usa un componente differenza di fuso orario *startdate* o *enddate*.
  
Per un valore **smalldatetime** usato per *startdate* o *enddate*, nel valore restituito `DATEDIFF_BIG` imposta sempre i secondi e i millisecondi su 0, perché [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md) garantisce la precisione solo a livello di minuti.
  
Se a una variabile di tipo data viene assegnato solo il valore dell'ora, `DATEDIFF_BIG` imposta il valore della parte mancante della data sul valore predefinito: 1900-01-01. Se a una variabile di tipo ora o data viene assegnato solo il valore della data, `DATEDIFF_BIG` imposta il valore della parte mancante dell'ora sul valore predefinito: 00:00:00. Se *startdate* ed *enddate* hanno rispettivamente solo la parte relativa all'ora o solo la parte relativa alla data, `DATEDIFF_BIG` imposta le parti mancanti sui rispettivi valori predefiniti.
  
Se i valori *startdate* ed *enddate* sono di tipi data diversi e uno di questi comprende un numero maggiore di parti di ora o offre una precisione in secondi frazionari maggiore, `DATEDIFF_BIG` imposta le parti mancanti dell'altro valore su 0.
  
## <a name="datepart-boundaries"></a>Limiti di datepart
Le istruzioni seguenti hanno gli stessi valori *startdate* ed *enddate*. Queste date sono adiacenti e differiscono di 0,0000001 secondi. La differenza tra *startdate* e *enddate* in ogni istruzione oltrepassa un limite di calendario o di ora del rispettivo valore *datepart*. Ciascuna istruzione restituisce 1. Se *startdate* ed *enddate* hanno valori di anno diversi ma gli stessi valori di settimana di calendario, `DATEDIFF_BIG` restituisce 0 per il parametro di *datepart*  **week**.

```sql
SELECT DATEDIFF_BIG(year,        '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(quarter,     '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(month,       '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(dayofyear,   '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(day,         '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(week,        '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(hour,        '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(minute,      '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(second,      '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(millisecond, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
```
  
## <a name="remarks"></a>Remarks  
Usare `DATEDIFF_BIG` nelle clausole SELECT <list>, WHERE, HAVING, GROUP BY e ORDER BY.
  
`DATEDIFF_BIG` consente di eseguire in modo implicito il cast di valori letterali stringa come tipo di dati **datetime2**. `DATEDIFF_BIG`, pertanto, non supporta il formato AGM se la data viene passata come stringa. Per usare il formato AGM è necessario eseguire il cast della stringa in modo esplicito in un tipo **datetime** o **smalldatetime**.
  
SET DATEFIRST non influisce su `DATEDIFF_BIG`. `DATEDIFF_BIG` usa sempre la domenica come primo giorno della settimana, per garantire che la funzione operi in modo deterministico.
  
## <a name="examples"></a>Esempi 
  
### <a name="specifying-columns-for-startdate-and-enddate"></a>Specifica di colonne per startdate ed enddate  
Questo esempio, che usa tipi diversi di espressioni come argomenti per i parametri *startdate* ed *enddate*, calcola il numero di limiti di giorno sovrapposti tra le date di due colonne di una tabella.
  
```sql
CREATE TABLE dbo.Duration  
    (startDate datetime2, endDate datetime2);  
    
INSERT INTO dbo.Duration(startDate,endDate)  
    VALUES('2007-05-06 12:10:09', '2007-05-07 12:10:09');  
    
SELECT DATEDIFF_BIG(day, startDate, endDate) AS 'Duration'  
    FROM dbo.Duration;  
-- Returns: 1  
```  

Per esempi più strettamente correlati, vedere [DATEDIFF &#40;Transact-SQL&#41;](../../t-sql/functions/datediff-transact-sql.md).
  
## <a name="see-also"></a>Vedere anche
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[DATEDIFF &#40;Transact-SQL&#41;](../../t-sql/functions/datediff-transact-sql.md)
  
  
