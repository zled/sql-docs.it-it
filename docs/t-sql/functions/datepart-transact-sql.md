---
title: DATEPART (Transact-SQL) | Documenti Microsoft
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
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 05547f2dd50d7f130438d6a07b6952b8c29ec816
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="datepart-transact-sql"></a>DATEPART (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Restituisce un intero che rappresenta l'oggetto specificato *datepart* dell'oggetto specificato *data*.
  
Per una panoramica di tutti i [!INCLUDE[tsql](../../includes/tsql-md.md)] tipi di dati data e ora e funzioni, vedere [data e ora i tipi di dati e funzioni &#40; Transact-SQL &#41; ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
DATEPART ( datepart , date )  
```  
  
## <a name="arguments"></a>Argomenti  
*parte di una data*  
È la parte di *data* (valore di data o ora) per il quale un **intero** verranno restituiti. La tabella seguente elenca tutti validi *datepart* argomenti. Variabili definite dall'utente equivalenti non sono valide.
  
|*parte di una data*|Abbreviazioni|  
|---|---|
|**anno**|**aa**, **aaaa**|  
|**trimestre**|**q**, **q**|  
|**mese**|**mm**, **m**|  
|**DayOfYear**|**dy**, **y**|  
|**giorno**|**gg**, **d**|  
|**settimana**|**wk**, **ww**|  
|**giorno della settimana**|**data warehouse**|  
|**ora**|**hh**|  
|**minuto**|**mi, n**|  
|**secondo**|**ss**, **s**|  
|**millisecondi**|**MS**|  
|**microsecondi**|**MCS**|  
|**nanosecondi**|**NS**|  
|**TZoffset**|**fuso orario**|  
|**ISO_WEEK**|**isowk**, **isoww**|  
  
*data*  
È un'espressione che può essere risolta in un **ora**, **data**, **smalldatetime**, **datetime**, **datetime2**, o **datetimeoffset** valore. *Data* può essere un'espressione, l'espressione di colonna, variabile definita dall'utente o stringa letterale.  
Per evitare ambiguità, esprimere gli anni nel formato a quattro cifre. Per informazioni sull'anno a due cifre, vedere [configurare l'anno a due cifre cutoff Server Configuration Option](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md).
  
## <a name="return-type"></a>Tipo restituito  
 **int**  
  
## <a name="return-value"></a>Valore restituito  
Ogni *datepart* e relative abbreviazioni restituiscono lo stesso valore.
  
Il valore restituito dipende dalla lingua impostata tramite [SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md) e dal [configurare l'opzione di configurazione Server default language](../../database-engine/configure-windows/configure-the-default-language-server-configuration-option.md) dell'account di accesso. Se *data* è una stringa letterale per alcuni formati, il valore restituito dipende dal formato specificato tramite [SET DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md). SET DATEFORMAT non influisce sul valore restituito quando la data è un'espressione della colonna di un tipo di dati ora e data.
  
Nella tabella seguente sono elencati tutti *datepart* argomenti con corrispondenti valori restituiscono per l'istruzione `SELECT DATEPART(datepart,'2007-10-30 12:15:32.1234567 +05:10')`. Il tipo di dati di *data* argomento **datetimeoffset(7)**. Il **nanosecondi***datepart* restituire valore ha una scala di 9 (. 123456700) e le ultime due posizioni sono sempre 00.
  
|*parte di una data*|Valore restituito|  
|---|---|
|**anno, gg, AA**|2007|  
|**trimestre, q, q**|4|  
|**mese, mm, m**|10|  
|**DayOfYear, dy, y**|303|  
|**giorno, gg, d**|30|  
|**settimana, wk, ss**|45|  
|**giorno della settimana, data warehouse**|1|  
|**ora, hh**|12|  
|**minuto, n**|15|  
|**in secondo luogo, ss, s**|32|  
|**millisecondo ms**|123|  
|**microsecondi, mcs**|123456|  
|**nanosecondi, ns**|123456700|  
|**TZoffset, fuso orario**|310|  
  
## <a name="week-and-weekday-datepart-arguments"></a>Argomenti datepart settimana e giorno della settimana
Quando *datepart* è **settimana** (**wk**, **ww**) o **giorno della settimana** (**dw**), il valore restituito dipende dal valore impostato utilizzando [SET DATEFIRST](../../t-sql/statements/set-datefirst-transact-sql.md).
  
1 ° gennaio di qualsiasi anno definisce il numero iniziale per il **settimana***datepart*, ad esempio: DATEPART (**wk**, ' 1 gen, *xxx*x') = 1, dove *xxxx* è qualsiasi anno.
  
Nella tabella seguente sono elencati il valore restituito per **settimana** e **giorno della settimana***datepart* per ' 2007-04-21' per ogni argomento SET DATEFIRST. Il 1° gennaio è un lunedì nell'anno 2007. Il 21 aprile dell'anno 2007 è sabato. SET DATEFIRST 7, domenica è l'impostazione predefinita per gli Stati Uniti. Regno Unito,
  
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
I valori restituiti per DATEPART (**anno**, *data*), DATEPART (**mese**, *data*) e DATEPART (**giorno** , *data*) sono uguali a quelli restituiti dalle funzioni [anno](../../t-sql/functions/year-transact-sql.md), [mese](../../t-sql/functions/month-transact-sql.md), e [giorno](../../t-sql/functions/day-transact-sql.md), f rispettivamente.
  
## <a name="isoweek-datepart"></a>datepart ISO_WEEK  
ISO 8601 include il sistema settimana-relativo alla data ISO, un sistema di numerazione per settimane. Ogni settimana è associata all'anno che inizia con un giovedì. Ad esempio, la settimana 1 del 2004 (2004W01) è iniziata lunedì 29 dicembre 2003 ed è terminata domenica 4 gennaio 2004. In un anno è possibile avere al massimo 52 o 53 settimane. Questo stile di numerazione viene in genere utilizzato nei paesi europei, raramente viene usato altrove.
  
Il sistema di numerazione nei diversi paesi potrebbe non essere conforme allo standard ISO. Ci sono almeno sei possibilità come mostra la tabella seguente
  
|Primo giorno della settimana|Prima settimana dell'anno|Settimane assegnate due volte|Utilizzato da/in|  
|---|---|---|---|
|Domenica|1 gennaio,<br /><br /> Primo sabato,<br /><br /> 1-7 giorni dell'anno|Sì|United States|  
|Lunedì|1 gennaio,<br /><br /> Prima domenica,<br /><br /> 1-7 giorni dell'anno|Sì|La maggior parte di Europa e Regno Unito|  
|Lunedì|4 gennaio,<br /><br /> Primo giovedì,<br /><br /> 4-7 giorni dell'anno|No|ISO 8601, Norvegia e Svezia|  
|Lunedì|7 gennaio,<br /><br /> Primo lunedì,<br /><br /> 7 giorni dell'anno|No||  
|Mercoledì|1 gennaio,<br /><br /> Primo martedì,<br /><br /> 1-7 giorni dell'anno|Sì||  
|Sabato|1 gennaio,<br /><br /> Primo venerdì,<br /><br /> 1-7 giorni dell'anno|Sì||  
  
## <a name="tzoffset"></a>TZoffset  
Il **TZoffset** (**tz**) viene restituito come numero di minuti (firmato). Nell'istruzione seguente è restituita una differenza di fuso orario di 310 minuti.
  
```sql
SELECT DATEPART (TZoffset, '2007-05-10  00:00:01.1234567 +05:10');  
```  
Il valore TZoffset viene eseguito come segue:
- Per datetime2 e datetimeoffset TZoffset restituisce la differenza di orario in minuti, in cui l'offset per datetime2 è sempre 0 minuti.
- Per i tipi di dati che possono essere convertiti in modo implicito in datetimeoffset o datetime2, fatta eccezione per gli altri tipi dati Data/ora, restituisce la differenza di orario in minuti.
- Parametri di tutti gli altri tipi generano un errore.
  
  
## <a name="smalldatetime-date-argument"></a>Argomento date smalldatetime  
Quando *data* è [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md), secondi vengono restituiti come 00.
  
## <a name="default-returned-for-a-datepart-that-is-not-in-a-date-argument"></a>Valore predefinito restituito per un datepart non incluso nell'argomento date  
Se il tipo di dati di *data* dell'argomento non è specificato *datepart*, il valore predefinito per tale *datepart* verrà restituito solo quando viene specificato un valore letterale per *data*.
  
Ad esempio, il valore predefinito anno-mese-giorno per qualsiasi **data** tipo di dati è 1900-01-01. L'istruzione seguente include gli argomenti DatePart per *datepart*, un argomento time per *data*e restituisce `1900, 1, 1, 1, 2`.
  
```sql
SELECT DATEPART(year, '12:10:30.123')  
    ,DATEPART(month, '12:10:30.123')  
    ,DATEPART(day, '12:10:30.123')  
    ,DATEPART(dayofyear, '12:10:30.123')  
    ,DATEPART(weekday, '12:10:30.123');  
```  
  
Se *data* viene specificato come una variabile o colonna di tabella e i dati di tipo per tale variabile o una colonna non dispone specificato *datepart*, viene restituito l'errore 9810. Nell'esempio di codice ha esito negativo di esempio perché la parte di data anno non è valido per il **ora** tipo dati dichiarato per la variabile  *@t* .
  
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
  
## <a name="remarks"></a>Osservazioni  
È possibile utilizzare DATEPART in un elenco di selezione e nelle clausole WHERE, HAVING, GROUP BY e ORDER BY.
  
In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], DATEPART esegue in modo implicito il cast di valori letterali stringa come un **datetime2** tipo. Pertanto, DATEPART non supporta il formato AGM se la data viene passata come stringa. È necessario eseguire il cast esplicito la stringa da un **datetime** o **smalldatetime** tipo da utilizzare il formato AGM.
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente viene restituito il valore dell'anno di base. L'anno di base è utile per i calcoli relativi alla data. Nell'esempio seguente, la data viene specificata sotto forma di numero. Si noti che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interpreta il valore 0 come 1 gennaio 1900.
  
```sql
SELECT DATEPART(year, 0), DATEPART(month, 0), DATEPART(day, 0);  
-- Returns: 1900    1    1 */  
```  
  
L'esempio seguente restituisce la parte del giorno della data `12/20/1974`.
  
```sql
-- Uses AdventureWorks  
  
SELECT TOP(1) DATEPART (day,'12/20/1974') FROM dbo.DimCustomer;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
`--------`
  
 `20`  
  
L'esempio seguente restituisce la parte dell'anno della data `12/20/1974`.
  
```sql
-- Uses AdventureWorks  
  
SELECT TOP(1) DATEPART (year,'12/20/1974') FROM dbo.DimCustomer;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
`--------`
  
 `1974`  
  
## <a name="see-also"></a>Vedere anche
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  

