---
title: DATEPART (Transact-SQL) | Microsoft Docs
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
- DATEPART_TSQL
- DATEPART
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- date and time [SQL Server], DATEPART
- dateparts [SQL Server]
- functions [SQL Server], time
- functions [SQL Server], date and time
- time [SQL Server], functions
- dateparts [SQL Server], datepart
- comparing dates times [SQL Server]
- DATEPART function [SQL Server]
- dates [SQL Server], dateparts
ms.assetid: 15f1a5bc-4c0c-4c48-848d-8ec03473e6c1
caps.latest.revision: 57
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: eee173d268af8e18343c286bda29384b2a327860
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="datepart-transact-sql"></a>DATEPART (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Restituisce un intero che rappresenta il valore *datepart* indicato della *data* specificata.
  
Per una panoramica di tutti i tipi di dati e delle funzioni di data e ora [!INCLUDE[tsql](../../includes/tsql-md.md)], vedere [Funzioni e tipi di dati di data e ora &#40;Transact-SQL&#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
DATEPART ( datepart , date )  
```  
  
## <a name="arguments"></a>Argomenti  
*datepart*  
Parte di *data* (un valore di data o ora) per la quale verrà restituito un **intero**. Nella tabella seguente sono elencati tutti gli argomenti *datepart* validi. Variabili definite dall'utente equivalenti non sono valide.
  
|*datepart*|Abbreviazioni|  
|---|---|
|**year**|**yy**, **yyyy**|  
|**quarter**|**qq**, **q**|  
|**month**|**mm**, **m**|  
|**dayofyear**|**dy**, **y**|  
|**day**|**dd**, **d**|  
|**week**|**wk**, **ww**|  
|**weekday**|**dw**|  
|**hour**|**hh**|  
|**minute**|**mi, n**|  
|**second**|**ss**, **s**|  
|**millisecond**|**ms**|  
|**microsecond**|**mcs**|  
|**nanosecond**|**ns**|  
|**TZoffset**|**tz**|  
|**ISO_WEEK**|**isowk**, **isoww**|  
  
*data*  
Espressione che può essere risolta in un valore **time**, **date**, **smalldatetime**, **datetime**, **datetime2** o **datetimeoffset**. *date* può essere costituito da un'espressione, un'espressione di colonna, una variabile definita dall'utente o un valore letterale stringa.  
Per evitare ambiguità, esprimere gli anni nel formato a quattro cifre. Per altre informazioni sugli anni a due cifre, vedere [Configurare l'opzione di configurazione del server Cambio data per anno a due cifre](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md).
  
## <a name="return-type"></a>Tipo restituito  
 **int**  
  
## <a name="return-value"></a>Valore restituito  
Ogni elemento *datepart* e le relative abbreviazioni restituiscono lo stesso valore.
  
Il valore restituito dipende dalla lingua impostata tramite [SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md) e in [Configurare l'opzione di configurazione del server default language](../../database-engine/configure-windows/configure-the-default-language-server-configuration-option.md) dell'account di accesso. Se *date* è un valore letterale stringa per alcuni formati, il valore restituito dipende dal formato specificato usando [SET DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md). SET DATEFORMAT non influisce sul valore restituito quando la data è un'espressione della colonna di un tipo di dati ora e data.
  
Nella tabella seguente sono elencati tutti gli argomenti *datepart* con i corrispondenti valori restituiti per l'istruzione `SELECT DATEPART(datepart,'2007-10-30 12:15:32.1234567 +05:10')`. Il tipo di dati dell'argomento *date* è **datetimeoffset(7)**. Il valore restituito usando **nanosecond***datepart* ha una scala di 9 (.123456700) e le ultime due posizioni sono sempre 00.
  
|*datepart*|Valore restituito|  
|---|---|
|**year, yyyy, yy**|2007|  
|**quarter, qq, q**|4|  
|**month, mm, m**|10|  
|**dayofyear, dy, y**|303|  
|**day, dd, d**|30|  
|**week, wk, ww**|45|  
|**weekday, dw**|1|  
|**hour, hh**|12|  
|**minute, n**|15|  
|**second, ss, s**|32|  
|**millisecond, ms**|123|  
|**microsecond, mcs**|123456|  
|**nanosecond, ns**|123456700|  
|**TZoffset, tz**|310|  
  
## <a name="week-and-weekday-datepart-arguments"></a>Argomenti datepart per settimana e giorno feriale
Quando *datepart* è **week** (**wk**, **ww**) o **weekday** (**dw**), il valore restituito dipende dal valore impostato usando [SET DATEFIRST](../../t-sql/statements/set-datefirst-transact-sql.md).
  
Il 1° gennaio di qualsiasi anno definisce il numero iniziale per **week***datepart*, ad esempio DATEPART (** wk**, '1 gen, *xxx*x') = 1, dove *xxxx* è qualsiasi anno.
  
Nella tabella seguente è elencato il valore restituito per **week** e **weekday***datepart* per '2007-04-21 ' per ogni argomento SET DATEFIRST. Il 1° gennaio è un lunedì nell'anno 2007. Il 21 aprile dell'anno 2007 è sabato. SET DATEFIRST 7, domenica è l'impostazione predefinita per gli Stati Uniti. Regno Unito,
  
|SET DATEFIRST<br /><br /> argomento|week<br /><br /> restituito|giorno feriale<br /><br /> restituito|  
|---|---|---|
|1|16|6|  
|2|17|5|  
|3|17|4|  
|4|17|3|  
|5|17|2|  
|6|17|1|  
|7|16|7|  
  
## <a name="year-month-and-day-datepart-arguments"></a>Argomenti datepart per anno, mese e giorno  
I valori restituiti per DATEPART (**year**, *date*), DATEPART (**month**, *date*) e DATEPART(**day**, *date*) corrispondono a quelli restituiti rispettivamente dalle funzioni [YEAR](../../t-sql/functions/year-transact-sql.md), [MONTH](../../t-sql/functions/month-transact-sql.md) e [DAY](../../t-sql/functions/day-transact-sql.md).
  
## <a name="isoweek-datepart"></a>datepart ISO_WEEK  
ISO 8601 include il sistema settimana-relativo alla data ISO, un sistema di numerazione per settimane. Ogni settimana è associata all'anno che inizia con un giovedì. Ad esempio, la settimana 1 del 2004 (2004W01) è iniziata lunedì 29 dicembre 2003 ed è terminata domenica 4 gennaio 2004. In un anno è possibile avere al massimo 52 o 53 settimane. Questo stile di numerazione viene in genere utilizzato nei paesi europei, raramente viene usato altrove.
  
Il sistema di numerazione nei diversi paesi potrebbe non essere conforme allo standard ISO. Ci sono almeno sei possibilità come mostra la tabella seguente
  
|Primo giorno della settimana|Prima settimana dell'anno|Settimane assegnate due volte|Utilizzato da/in|  
|---|---|---|---|
|Domenica|1 gennaio,<br /><br /> Primo sabato,<br /><br /> 1-7 giorni dell'anno|Sì|United States|  
|Lunedì|1 gennaio,<br /><br /> Prima domenica,<br /><br /> 1-7 giorni dell'anno|Sì|La maggior parte di Europa e Regno Unito|  
|Lunedì|4 gennaio,<br /><br /> Primo giovedì,<br /><br /> 4-7 giorni dell'anno|no|ISO 8601, Norvegia e Svezia|  
|Lunedì|7 gennaio,<br /><br /> Primo lunedì,<br /><br /> 7 giorni dell'anno|no||  
|Mercoledì|1 gennaio,<br /><br /> Primo martedì,<br /><br /> 1-7 giorni dell'anno|Sì||  
|Sabato|1 gennaio,<br /><br /> Primo venerdì,<br /><br /> 1-7 giorni dell'anno|Sì||  
  
## <a name="tzoffset"></a>TZoffset  
**TZoffset** (**tz**) viene restituito come numero di minuti (firmato). Nell'istruzione seguente è restituita una differenza di fuso orario di 310 minuti.
  
```sql
SELECT DATEPART (TZoffset, '2007-05-10  00:00:01.1234567 +05:10');  
```  
Il valore TZoffset viene reso come segue:
- Per datetimeoffset e datetime2, TZoffset restituisce la differenza di orario in minuti, in cui l'offset per datetime2 è sempre 0 minuti.
- Per i tipi di dati che possono essere convertiti in modo implicito in datetimeoffset o datetime2, fatta eccezione per gli altri tipi dati data/ora, restituisce la differenza di orario in minuti.
- I parametri di tutti gli altri tipi generano un errore.
  
  
## <a name="smalldatetime-date-argument"></a>Argomento date smalldatetime  
Quando *date* è [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md), i secondi vengono restituiti come 00.
  
## <a name="default-returned-for-a-datepart-that-is-not-in-a-date-argument"></a>Valore predefinito restituito per un datepart non incluso nell'argomento date  
Se per il tipo di dati dell'argomento *date* non viene specificato *datepart*, il valore predefinito per *datepart* verrà restituito solo se è stato specificato un valore letterale per *date*.
  
Ad esempio, l'anno-mese-giorno predefinito per qualsiasi tipo di dati **date** è 1900-01-01. L'istruzione seguente include gli argomenti datepart per *datepart*, un argomento time per *date* e restituisce `1900, 1, 1, 1, 2`.
  
```sql
SELECT DATEPART(year, '12:10:30.123')  
    ,DATEPART(month, '12:10:30.123')  
    ,DATEPART(day, '12:10:30.123')  
    ,DATEPART(dayofyear, '12:10:30.123')  
    ,DATEPART(weekday, '12:10:30.123');  
```  
  
Se *date* viene specificato come variabile o colonna di tabella e per il tipo di dati della variabile o della colonna *datepart* non viene specificato, verrà restituito l'errore 9810. L'esempio di codice riportato di seguito ha esito negativo perché la parte di data anno non è valida per il tipo di dati **time** dichiarato per la variabile *@t*.
  
```sql
DECLARE @t time = '12:10:30.123';   
SELECT DATEPART(year, @t);  
```  
  
## <a name="fractional-seconds"></a>Secondi frazionari
Secondi frazionari vengono restituiti come indicato nelle istruzioni seguenti:
  
```sql
SELECT DATEPART(millisecond, '00:00:01.1234567'); -- Returns 123  
SELECT DATEPART(microsecond, '00:00:01.1234567'); -- Returns 123456  
SELECT DATEPART(nanosecond,  '00:00:01.1234567'); -- Returns 123456700  
```  
  
## <a name="remarks"></a>Remarks  
È possibile utilizzare DATEPART in un elenco di selezione e nelle clausole WHERE, HAVING, GROUP BY e ORDER BY.
  
In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], DATEPART consente di eseguire in modo implicito il cast di valori letterali stringa in un tipo **datetime2**. Pertanto, DATEPART non supporta il formato AGM se la data viene passata come stringa. Per usare il formato AGM è necessario eseguire il cast della stringa in modo esplicito in un tipo **datetime** o **smalldatetime**.
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente viene restituito il valore dell'anno di base. L'anno di base è utile per i calcoli relativi alla data. Nell'esempio seguente, la data viene specificata sotto forma di numero. Si noti che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interpreta il valore 0 come 1 gennaio 1900.
  
```sql
SELECT DATEPART(year, 0), DATEPART(month, 0), DATEPART(day, 0);  
-- Returns: 1900    1    1 */  
```  
  
Nell'esempio seguente viene restituita la parte relativa al giorno della data `12/20/1974`.
  
```sql
-- Uses AdventureWorks  
  
SELECT TOP(1) DATEPART (day,'12/20/1974') FROM dbo.DimCustomer;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
--------
20
```  
  
Nell'esempio seguente viene restituita la parte relativa all'anno della data `12/20/1974`.
  
```sql
-- Uses AdventureWorks  
  
SELECT TOP(1) DATEPART (year,'12/20/1974') FROM dbo.DimCustomer;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
--------
1974
```  
  
## <a name="see-also"></a>Vedere anche
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  
