---
title: DATENAME (Transact-SQL) | Documenti Microsoft
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
- DATENAME_TSQL
- DATENAME
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- DATENAME function [SQL Server
- functions [SQL Server], time
- functions [SQL Server], date and time
- dateparts [SQL Server], datename
- date and time [SQL Server], DATENAME
- comparing dates times [SQL Server]
- dates [SQL Server], dateparts
ms.assetid: 11855b56-c554-495d-aad4-ba446990153b
caps.latest.revision: 59
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2d41bbf5a83f0dee8518ece6f074181b8412bad8
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="datename-transact-sql"></a>DATENAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Restituisce una stringa di caratteri che rappresenta il valore *datepart* dell'oggetto specificato *Data*
  
Per una panoramica di tutti i [!INCLUDE[tsql](../../includes/tsql-md.md)] tipi di dati data e ora e funzioni, vedere [data e ora i tipi di dati e funzioni &#40; Transact-SQL &#41; ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
DATENAME ( datepart , date )  
```  
  
## <a name="arguments"></a>Argomenti  
*parte di una data*  
È la parte di *data* da restituire. La tabella seguente elenca tutti validi *datepart* argomenti. Variabili definite dall'utente equivalenti non sono valide.
  
|*parte di una data*|Abbreviazioni|  
|---|---|
|**anno**|**yy, yyyy**|  
|**trimestre**|**q, q**|  
|**mese**|**mm, m**|  
|**DayOfYear**|**dy, y**|  
|**giorno**|**GG, d**|  
|**settimana**|**wk, ww**|  
|**giorno della settimana**|**data warehouse, w**|  
|**ora**|**hh**|  
|**minuto**|**mi, n**|  
|**secondo**|**ss, s**|  
|**millisecondi**|**MS**|  
|**microsecondi**|**MCS**|  
|**nanosecondi**|**NS**|  
|**TZoffset**|**fuso orario**|  
|**ISO_WEEK**|**ISOWK, ISOWW**|  
  
*data*  
È un'espressione che può essere risolta in un **ora**, **data**, **smalldatetime**, **datetime**, **datetime2**, o **datetimeoffset** valore. *Data* può essere un'espressione, l'espressione di colonna, variabile definita dall'utente o stringa letterale.  
Per evitare ambiguità, esprimere gli anni nel formato a quattro cifre. Per informazioni su anni a due cifre, vedere [configurare l'anno a due cifre cutoff Server Configuration Option](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md).
  
## <a name="return-type"></a>Tipo restituito  
**nvarchar**
  
## <a name="return-value"></a>Valore restituito  
  
-   Ogni *datepart* e relative abbreviazioni restituiscono lo stesso valore.  
  
Il valore restituito dipende dalla lingua impostata tramite [SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md) e dal [configurare l'opzione di configurazione Server default language](../../database-engine/configure-windows/configure-the-default-language-server-configuration-option.md) dell'account di accesso. Il valore restituito è dipendenti in [SET DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md) se *data* è una stringa letterale di alcuni formati. SET DATEFORMAT non influisce sul valore restituito quando la data è un'espressione della colonna di un tipo di dati ora e data.
  
Quando il *data* parametro ha un **data** argomento di tipo di dati, il valore restituito dipende dall'impostazione specificata tramite [SET DATEFIRST](../../t-sql/statements/set-datefirst-transact-sql.md).
  
## <a name="tzoffset-datepart-argument"></a>Argomento datepart TZoffset  
Se *datepart* argomento **TZoffset** (**tz**) e *data* argomento non dispone di alcuna differenza di fuso orario, viene restituito 0.
  
## <a name="smalldatetime-date-argument"></a>Argomento date smalldatetime  
Quando *data* è [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md), secondi vengono restituiti come 00.
  
## <a name="default-returned-for-a-datepart-that-is-not-in-the-date-argument"></a>Valore predefinito restituito per un argomento datepart non incluso nell'argomento date  
Se il tipo di dati di *data* dell'argomento non è specificato *datepart*, il valore predefinito per tale *datepart* verrà restituito solo quando viene specificato un valore letterale per *data*.
  
Ad esempio, il valore predefinito anno-mese-giorno per qualsiasi **data** tipo di dati è 1900-01-01. L'istruzione seguente include gli argomenti DatePart per *datepart*, un argomento time per *data*e restituisce `1900, January, 1, 1, Monday`.
  
```sql
SELECT DATENAME(year, '12:10:30.123')  
    ,DATENAME(month, '12:10:30.123')  
    ,DATENAME(day, '12:10:30.123')  
    ,DATENAME(dayofyear, '12:10:30.123')  
    ,DATENAME(weekday, '12:10:30.123');  
```  
  
Se *data* viene specificato come una variabile o colonna di tabella e i dati di tipo per tale variabile o una colonna non dispone specificato *datepart*, viene restituito l'errore 9810. Nell'esempio di codice ha esito negativo di esempio perché la parte di data anno non è valido per il **ora** tipo dati dichiarato per la variabile  *@t* .
  
```sql
DECLARE @t time = '12:10:30.123';   
SELECT DATENAME(year, @t);  
```  
  
## <a name="remarks"></a>Osservazioni  
È possibile utilizzare DATENAME nell'elenco di selezione e nelle clausole WHERE, HAVING, GROUP BY e ORDER BY.
  
In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], DATENAME esegue in modo implicito il cast di valori letterali stringa come un **datetime2** tipo. Pertanto, DATENAME non supporta il formato AGM se la data viene passata come stringa. È necessario eseguire il cast esplicito la stringa da un **datetime** o **smalldatetime** tipo da utilizzare il formato AGM.
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente vengono restituite le parti della data specificata.
  
`SELECT DATENAME(datepart,'2007-10-30 12:15:32.1234567 +05:10');`
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
|*parte di una data*|Valore restituito|  
|---|---|
|**anno, gg, AA**|2007|  
|**trimestre, q, q**|4|  
|**mese, mm, m**|Ottobre|  
|**DayOfYear, dy, y**|303|  
|**giorno, gg, d**|30|  
|**settimana, wk, ss**|44|  
|**giorno della settimana, data warehouse**|Martedì|  
|**ora, hh**|12|  
|**minuto, n**|15|  
|**in secondo luogo, ss, s**|32|  
|**millisecondo ms**|123|  
|**microsecondi, mcs**|123456|  
|**nanosecondi, ns**|123456700|  
|**TZoffset, fuso orario**|310|  
|**ISOWW ISO_WEEK, ISOWK,**|44|  
  
[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]

Nell'esempio seguente vengono restituite le parti della data specificata.
  
```sql
SELECT DATENAME(datepart,'2007-10-30 12:15:32.1234567 +05:10');  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
|*parte di una data*|Valore restituito|  
|---|---|
|**anno, gg, AA**|2007|  
|**trimestre, q, q**|4|  
|**mese, mm, m**|Ottobre|  
|**DayOfYear, dy, y**|303|  
|**giorno, gg, d**|30|  
|**settimana, wk, ss**|44|  
|**giorno della settimana, data warehouse**|Martedì|  
|**ora, hh**|12|  
|**minuto, n**|15|  
|**in secondo luogo, ss, s**|32|  
|**millisecondo ms**|123|  
|**microsecondi, mcs**|123456|  
|**nanosecondi, ns**|123456700|  
|**TZoffset, fuso orario**|310|  
|**ISOWW ISO_WEEK, ISOWK,**|44|  
  
## <a name="see-also"></a>Vedere anche
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  


