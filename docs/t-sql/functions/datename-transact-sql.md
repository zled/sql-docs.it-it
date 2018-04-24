---
title: DATENAME (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: a8803278c567f01888b7b530885e82e4543c966a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="datename-transact-sql"></a>DATENAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Restituisce una stringa di caratteri che rappresenta il valore *datepart* indicato del valore *date* specificato.
  
Per una panoramica di tutti i tipi di dati e delle funzioni di data e ora [!INCLUDE[tsql](../../includes/tsql-md.md)], vedere [Funzioni e tipi di dati di data e ora &#40;Transact-SQL&#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
DATENAME ( datepart , date )  
```  
  
## <a name="arguments"></a>Argomenti  
*datepart*  
Parte dell'argomento *date* da restituire. Nella tabella seguente sono elencati tutti gli argomenti *datepart* validi. Variabili definite dall'utente equivalenti non sono valide.
  
|*datepart*|Abbreviazioni|  
|---|---|
|**year**|**yy, yyyy**|  
|**quarter**|**qq, q**|  
|**month**|**mm, m**|  
|**dayofyear**|**dy, y**|  
|**day**|**dd, d**|  
|**week**|**wk, ww**|  
|**weekday**|**dw, w**|  
|**hour**|**hh**|  
|**minute**|**mi, n**|  
|**second**|**ss, s**|  
|**millisecond**|**ms**|  
|**microsecond**|**mcs**|  
|**nanosecond**|**ns**|  
|**TZoffset**|**tz**|  
|**ISO_WEEK**|**ISOWK, ISOWW**|  
  
*data*  
Espressione che può essere risolta in un valore **time**, **date**, **smalldatetime**, **datetime**, **datetime2** o **datetimeoffset**. *date* può essere costituito da un'espressione, un'espressione di colonna, una variabile definita dall'utente o un valore letterale stringa.  
Per evitare ambiguità, esprimere gli anni nel formato a quattro cifre. Per altre informazioni sugli anni a due cifre, vedere [Configurare l'opzione di configurazione del server Cambio data per anno a due cifre](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md).
  
## <a name="return-type"></a>Tipo restituito  
**nvarchar**
  
## <a name="return-value"></a>Valore restituito  
  
-   Ogni elemento *datepart* e le relative abbreviazioni restituiscono lo stesso valore.  
  
Il valore restituito dipende dalla lingua impostata tramite [SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md) e in [Configurare l'opzione di configurazione del server default language](../../database-engine/configure-windows/configure-the-default-language-server-configuration-option.md) dell'account di accesso. Il valore restituito dipende da [SET DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md) se *date* è un valore letterale stringa di alcuni formati. SET DATEFORMAT non influisce sul valore restituito quando la data è un'espressione della colonna di un tipo di dati ora e data.
  
Quando il parametro *date* ha un argomento del tipo di dati **date**, il valore restituito dipende dall'impostazione specificata tramite [SET DATEFIRST](../../t-sql/statements/set-datefirst-transact-sql.md).
  
## <a name="tzoffset-datepart-argument"></a>Argomento datepart TZoffset  
Se l'argomento *datepart* è **TZoffset** (**tz**) e l'argomento *date* non prevede una differenza di fuso orario, viene restituito il valore 0.
  
## <a name="smalldatetime-date-argument"></a>Argomento date smalldatetime  
Quando *date* è [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md), i secondi vengono restituiti come 00.
  
## <a name="default-returned-for-a-datepart-that-is-not-in-the-date-argument"></a>Valore predefinito restituito per un argomento datepart non incluso nell'argomento date  
Se per il tipo di dati dell'argomento *date* non viene specificato *datepart*, il valore predefinito per *datepart* verrà restituito solo se è stato specificato un valore letterale per *date*.
  
Ad esempio, l'anno-mese-giorno predefinito per qualsiasi tipo di dati **date** è 1900-01-01. L'istruzione seguente include gli argomenti datepart per *datepart*, un argomento time per *date* e restituisce `1900, January, 1, 1, Monday`.
  
```sql
SELECT DATENAME(year, '12:10:30.123')  
    ,DATENAME(month, '12:10:30.123')  
    ,DATENAME(day, '12:10:30.123')  
    ,DATENAME(dayofyear, '12:10:30.123')  
    ,DATENAME(weekday, '12:10:30.123');  
```  
  
Se *date* viene specificato come variabile o colonna di tabella e per il tipo di dati della variabile o della colonna *datepart* non viene specificato, verrà restituito l'errore 9810. L'esempio di codice riportato di seguito ha esito negativo perché la parte di data anno non è valida per il tipo di dati **time** dichiarato per la variabile *@t*.
  
```sql
DECLARE @t time = '12:10:30.123';   
SELECT DATENAME(year, @t);  
```  
  
## <a name="remarks"></a>Remarks  
È possibile utilizzare DATENAME nell'elenco di selezione e nelle clausole WHERE, HAVING, GROUP BY e ORDER BY.
  
In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] DATENAME consente di eseguire in modo implicito il cast di valori letterali stringa in un tipo **datetime2**. Pertanto, DATENAME non supporta il formato AGM se la data viene passata come stringa. Per usare il formato AGM è necessario eseguire il cast della stringa in modo esplicito in un tipo **datetime** o **smalldatetime**.
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente vengono restituite le parti della data specificata.
  
`SELECT DATENAME(datepart,'2007-10-30 12:15:32.1234567 +05:10');`
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
|*datepart*|Valore restituito|  
|---|---|
|**year, yyyy, yy**|2007|  
|**quarter, qq, q**|4|  
|**month, mm, m**|Ottobre|  
|**dayofyear, dy, y**|303|  
|**day, dd, d**|30|  
|**week, wk, ww**|44|  
|**weekday, dw**|Martedì|  
|**hour, hh**|12|  
|**minute, n**|15|  
|**second, ss, s**|32|  
|**millisecond, ms**|123|  
|**microsecond, mcs**|123456|  
|**nanosecond, ns**|123456700|  
|**TZoffset, tz**|310|  
|**ISO_WEEK, ISOWK, ISOWW**|44|  
  
[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]

Nell'esempio seguente vengono restituite le parti della data specificata.
  
```sql
SELECT DATENAME(datepart,'2007-10-30 12:15:32.1234567 +05:10');  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
|*datepart*|Valore restituito|  
|---|---|
|**year, yyyy, yy**|2007|  
|**quarter, qq, q**|4|  
|**month, mm, m**|Ottobre|  
|**dayofyear, dy, y**|303|  
|**day, dd, d**|30|  
|**week, wk, ww**|44|  
|**weekday, dw**|Martedì|  
|**hour, hh**|12|  
|**minute, n**|15|  
|**second, ss, s**|32|  
|**millisecond, ms**|123|  
|**microsecond, mcs**|123456|  
|**nanosecond, ns**|123456700|  
|**TZoffset, tz**|310|  
|**ISO_WEEK, ISOWK, ISOWW**|44|  
  
## <a name="see-also"></a>Vedere anche
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  

