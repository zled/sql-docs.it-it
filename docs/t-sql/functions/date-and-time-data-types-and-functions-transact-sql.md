---
title: Data e ora i tipi e funzioni (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 09/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- dates [SQL Server]
- date and time [SQL Server], all data types and functions
- date and time [SQL Server]
- functions [SQL Server], time
- functions [SQL Server], date and time
- time [SQL Server], functions
ms.assetid: 83e378a2-6e89-4c80-bc4f-644958d9e0a9
caps.latest.revision: "79"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 05ce8f3240590e1be28722ded5a526ad2dd2d6df
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="date-and-time-data-types-and-functions-transact-sql"></a>Funzioni e tipi di dati di data e ora (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

Le sezioni seguenti in questo argomento forniscono una panoramica di tutti i tipi di dati e funzioni di data e ora [!INCLUDE[tsql](../../includes/tsql-md.md)].
-   [Data e ora i tipi di dati](#DateandTimeDataTypes)  
-   [Funzioni data e ora](#DateandTimeFunctions)  
    -   [Funzione che valori Get sistema data e ora](#GetSystemDateandTimeValues)  
    -   [Funzioni che ottengono una data e ora parti](#GetDateandTimeParts)  
    -   [Funzioni che ottengono valori data e ora dalle parti relative](#fromParts)  
    -   [Funzioni che ottengono una data e differenza di ora](#GetDateandTimeDifference)  
    -   [Funzioni che modificano data e ora di valori](#ModifyDateandTimeValues)  
    -   [Funzioni che impostano oppure ottengono funzioni di formato sessione](#SetorGetSessionFormatFunctions)  
    -   [Funzioni che convalidano data e ora di valori](#ValidateDateandTimeValues)  
-   [Argomenti correlati ora e data](#DateandTimeRelatedTopics)  
  
##  <a name="DateandTimeDataTypes"></a>Tipi di dati data e ora
Il [!INCLUDE[tsql](../../includes/tsql-md.md)] tipi di dati data e ora sono elencati nella tabella seguente:
  
|Tipo di dati|Formato|Intervallo|Accuratezza|Dimensioni dello spazio di archiviazione (in byte)|Precisione in secondi frazionari definita dall'utente|Differenza di fuso orario|  
|---|---|---|---|---|---|---|
|[time](../../t-sql/data-types/time-transact-sql.md)|hh:mm:ss[.nnnnnnn]|da 00.00.00.0000000 a 23.59.59.9999999|100 nanosecondi|da 3 a 5|Sì|No|  
|[data](../../t-sql/data-types/date-transact-sql.md)|YYYY-MM-DD|Da 01-01-0001 a 31-12-9999|1 giorno|3|No|No|  
|[smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md)|AAAAA-MM-GG hh.mm.ss|da 01-01-1900 a 06-06-2079|1 minuto|4|No|No|  
|[datetime](../../t-sql/data-types/datetime-transact-sql.md)|AAAA-MM-GG hh:mm:ss[.nnn]|da 01-01-1753 a 31-12-9999|0,00333 secondi|8|No|No|  
|[datetime2](../../t-sql/data-types/datetime2-transact-sql.md)|AAAA-MM-GG hh:mm:ss[.nnnnnnn]|da 01-01-0001 00.00.00.0000000 a 31-12-9999 23.59.59.9999999|100 nanosecondi|da 6 a 8|Sì|No|  
|[datetimeoffset](../../t-sql/data-types/datetimeoffset-transact-sql.md)|AAAA-MM-gg hh.mm.ss [. nnnnnnn] [+ &#124;-] hh: mm|da 0001-01-01 00:00:00.0000000 a 9999-12-31 23:59:59.9999999 (in UTC)|100 nanosecondi|da 8 a 10|Sì|Sì|  
  
> [!NOTE]  
>  Il [!INCLUDE[tsql](../../includes/tsql-md.md)] [rowversion](../../t-sql/data-types/rowversion-transact-sql.md) tipo di dati non è un tipo di dati date o time. **timestamp** è un sinonimo deprecato per **rowversion**.  
  
##  <a name="DateandTimeFunctions"></a>Funzioni data e ora  
Le funzioni di data e ora [!INCLUDE[tsql](../../includes/tsql-md.md)] sono elencate nelle seguenti tabelle. Per ulteriori informazioni sulle funzioni deterministiche, vedere [funzioni deterministiche e non](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).
  
###  <a name="GetSystemDateandTimeValues"></a>Funzioni che ottengono valori data e ora di sistema 
Tutti i valori di data e ora derivano dal sistema operativo del computer in cui è in esecuzione l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
#### <a name="higher-precision-system-date-and-time-functions"></a>Funzioni di data e ora di sistema con precisione superiore  
[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]Ottiene i valori di data e ora tramite l'API di Windows GetSystemTimeAsFileTime(). L'accuratezza dipende dall'hardware e dalla versione di Windows del computer in cui è in esecuzione l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La precisione di tale API è fissata sul valore di 100 nanosecondi. L'accuratezza può essere determinato tramite l'API di Windows GetSystemTimeAdjustment().
  
|Funzione|Sintassi|Valore restituito|Tipo di dati restituito|Determinismo|  
|---|---|---|---|---|
|[SYSDATETIME](../../t-sql/functions/sysdatetime-transact-sql.md)|SYSDATETIME ()|Restituisce un **datetime2 (7)** valore che contiene la data e ora del computer in cui l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in esecuzione. La differenza di fuso orario non è inclusa.|**datetime2(7)**|Non deterministica|  
|[SYSDATETIMEOFFSET](../../t-sql/functions/sysdatetimeoffset-transact-sql.md)|SYSDATETIMEOFFSET ( )|Restituisce un **datetimeoffset(7)** valore che contiene la data e ora del computer in cui l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in esecuzione. La differenza di fuso orario è inclusa.|**DateTimeOffset(7)**|Non deterministica|  
|[SYSUTCDATETIME](../../t-sql/functions/sysutcdatetime-transact-sql.md)|SYSUTCDATETIME ( )|Restituisce un **datetime2 (7)** valore che contiene la data e ora del computer in cui l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in esecuzione. La data e l'ora viene restituito come ora UTC (Coordinated Universal Time).|**datetime2(7)**|Non deterministica|  
  
#### <a name="lower-precision--system-date-and-time-functions"></a>Funzioni di data e ora di sistema con precisione inferiore
  
|Funzione|Sintassi|Valore restituito|Tipo di dati restituito|Determinismo|  
|---|---|---|---|---|
|[CURRENT_TIMESTAMP](../../t-sql/functions/current-timestamp-transact-sql.md)|CURRENT_TIMESTAMP|Restituisce un **datetime** valore che contiene la data e ora del computer in cui l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in esecuzione. La differenza di fuso orario non è inclusa.|**datetime**|Non deterministica|  
|[GETDATE](../../t-sql/functions/getdate-transact-sql.md)|GETDATE ( )|Restituisce un **datetime** valore che contiene la data e ora del computer in cui l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in esecuzione. La differenza di fuso orario non è inclusa.|**datetime**|Non deterministica|  
|[GETUTCDATE](../../t-sql/functions/getutcdate-transact-sql.md)|GETUTCDATE ( )|Restituisce un **datetime** valore che contiene la data e ora del computer in cui l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in esecuzione. La data e l'ora viene restituito come ora UTC (Coordinated Universal Time).|**datetime**|Non deterministica|  
  
###  <a name="GetDateandTimeParts"></a>Funzioni che ottengono parti della data e ora
  
|Funzione|Sintassi|Valore restituito|Tipo di dati restituito|Determinismo|  
|--------------|------------|------------------|----------------------|-----------------|  
|[DATENAME](../../t-sql/functions/datename-transact-sql.md)|DATENAME ( *datepart* , *data* )|Restituisce una stringa di caratteri che rappresenta il valore *datepart* della data specificata.|**nvarchar**|Non deterministica|  
|[DATEPART](../../t-sql/functions/datepart-transact-sql.md)|DATEPART ( *datepart* , *data* )|Restituisce un intero che rappresenta l'oggetto specificato *datepart* dell'oggetto specificato *data*.|**int**|Non deterministica|  
|[DAY](../../t-sql/functions/day-transact-sql.md)|GIORNO ( *data* )|Restituisce un intero che rappresenta la parte del giorno dell'oggetto specificato *data*.|**int**|Deterministico|  
|[MONTH](../../t-sql/functions/month-transact-sql.md)|MESE ( *data* )|Restituisce un intero che rappresenta la parte del mese di un oggetto specificato *data*.|**int**|Deterministico|  
|[YEAR](../../t-sql/functions/year-transact-sql.md)|ANNO ( *data* )|Restituisce un intero che rappresenta la parte di un determinato anno *data*.|**int**|Deterministico|  
  
###  <a name="fromParts"></a>Funzioni che ottengono valori data e ora dalle parti relative
  
|Funzione|Sintassi|Valore restituito|Tipo di dati restituito|Determinismo|  
|---|---|---|---|---|
|[DATEFROMPARTS](../../t-sql/functions/datefromparts-transact-sql.md)|DATEFROMPARTS ( *anno*, *mese*, *giorno* )|Restituisce un **data** valore per l'anno, mese e giorno.|**data**|Deterministico|  
|[DATETIME2FROMPARTS](../../t-sql/functions/datetime2fromparts-transact-sql.md)|DATETIME2FROMPARTS ( *anno*, *mese*, *giorno*, *ora*, *minuto*, *secondi* , *frazioni*, *precisione*)|Restituisce un **datetime2** valore per la data e ora specificate e con precisione specificata.|**datetime2 (** *precisione* **)**|Deterministico|  
|[DATETIMEFROMPARTS](../../t-sql/functions/datetimefromparts-transact-sql.md)|DATETIMEFROMPARTS ( *anno*, *mese*, *giorno*, *ora*, *minuto*, *secondi* , *millisecondi*)|Restituisce un **datetime** valore per la data e ora specificate.|**datetime**|Deterministico|  
|[DATETIMEOFFSETFROMPARTS](../../t-sql/functions/datetimeoffsetfromparts-transact-sql.md)|DATETIMEOFFSETFROMPARTS ( *anno*, *mese*, *giorno*, *ora*, *minuto*,  *secondi*, *frazioni*, *hour_offset*, *minute_offset*, *precisione*)|Restituisce un **datetimeoffset** valore per la data e ora specificate e con l'offset specificati e la precisione.|**DateTime (** *precisione* **)**|Deterministico|  
|[SMALLDATETIMEFROMPARTS](../../t-sql/functions/smalldatetimefromparts-transact-sql.md)|SMALLDATETIMEFROMPARTS ( *anno*, *mese*, *giorno*, *ora*, *minuto* )|Restituisce un **smalldatetime** valore per la data e ora specificate.|**smalldatetime**|Deterministico|  
|[TIMEFROMPARTS](../../t-sql/functions/timefromparts-transact-sql.md)|TIMEFROMPARTS ( *ora*, *minuto*, *secondi*, *frazioni*, *precisione* )|Restituisce un **ora** valore per il tempo specificato e con precisione specificata.|**tempo (** *precisione* **)**|Deterministico|  
  
###  <a name="GetDateandTimeDifference"></a>Funzioni che ottengono la differenza di data e ora
  
|Funzione|Sintassi|Valore restituito|Tipo di dati restituito|Determinismo|  
|---|---|---|---|---|
|[DATEDIFF](../../t-sql/functions/datediff-transact-sql.md)|DATEDIFF ( *datepart* , *startdate* , *enddate* )|Restituisce il numero di data o ora *datepart* limiti si sovrappongono tra due date specificate.|**int**|Deterministico|  
|[DATEDIFF_BIG](../../t-sql/functions/datediff-big-transact-sql.md)|DATEDIFF_BIG ( *datepart* , *startdate* , *enddate* )|Restituisce il numero di data o ora *datepart* limiti si sovrappongono tra due date specificate.|**bigint**|Deterministico|  
  
###  <a name="ModifyDateandTimeValues"></a>Funzioni che modificano i valori di data e ora
  
|Funzione|Sintassi|Valore restituito|Tipo di dati restituito|Determinismo|  
|---|---|---|---|---|
|[DATEADD](../../t-sql/functions/dateadd-transact-sql.md)|DATEADD (*datepart* , *numero* , *data* )|Restituisce un nuovo **datetime** valore tramite l'aggiunta di un intervallo specificato *datepart* dell'oggetto specificato *data*.|Il tipo di dati di *data* argomento|Deterministico|  
|[EOMONTH](../../t-sql/functions/eomonth-transact-sql.md)|EOMONTH ( *start_date* [, *month_to_add* ])|Restituisce l'ultimo giorno del mese che contiene la data specificata, con un offset facoltativo.|Tipo restituito è il tipo di *start_date* o **data**.|Deterministico|  
|[SWITCHOFFSET](../../t-sql/functions/switchoffset-transact-sql.md)|OPZIONE*OFFSET* (*DATETIMEOFFSET* , *fuso orario*)|OPZIONE*OFFSET* cambia il fuso orario di un valore DATETIMEOFFSET e mantiene il valore UTC.|**DateTimeOffset** con la precisione frazionaria di *DATETIMEOFFSET*|Deterministico|  
|[TODATETIMEOFFSET](../../t-sql/functions/todatetimeoffset-transact-sql.md)|TODATETIMEOFFSET (*espressione* , *fuso orario*)|TODATETIMEOFFSET trasforma il valore datetime2 in un valore datetimeoffset. Il valore datetime2 viene interpretato come ora locale in base al valore time_zone specificato.|**DateTimeOffset** con la precisione frazionaria di *datetime* argomento|Deterministico|  
  
###  <a name="SetorGetSessionFormatFunctions"></a>Funzioni che ottiene o imposta il formato sessione
  
|Funzione|Sintassi|Valore restituito|Tipo di dati restituito|Determinismo|  
|---|---|---|---|---|
|[@@DATEFIRST](../../t-sql/functions/datefirst-transact-sql.md)|@@DATEFIRST  |Restituisce il valore corrente, per la sessione, di SET DATEFIRST.|**tinyint**|Non deterministica|  
|[SET DATEFIRST](../../t-sql/statements/set-datefirst-transact-sql.md)|SET DATEFIRST { *numero* &#124;  **@**  *number_var* }|Imposta il primo giorno della settimana su un numero compreso tra 1 e 7.|Non applicabile|Non applicabile|  
|[SET DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md)|SET DATEFORMAT { *formato* &#124;  **@**  *format_var* }|Imposta l'ordine delle parti della data (mese/giorno/anno) per l'immissione di **datetime** o **smalldatetime** dati.|Non applicabile|Non applicabile|  
|[@@LANGUAGE](../../t-sql/functions/language-transact-sql.md)|@@LANGUAGE  |Restituisce il nome della lingua correntemente in uso. @@LANGUAGE non è una funzione di data o ora. Comunque, l'impostazione della lingua può influire sull'output di funzioni di data.|Non applicabile|Non applicabile|  
|[IMPOSTAZIONE DELLA LINGUA](../../t-sql/statements/set-language-transact-sql.md)|SET LANGUAGE {[N] **'***language***'** &#124;  **@**  *language_var* }|Imposta la lingua per la sessione e i messaggi di sistema. SET LANGUAGE non è una data o una funzione dell'ora. Comunque, l'impostazione della lingua influisce sull'output di funzioni di data.|Non applicabile|Non applicabile|  
|[sp_helplanguage](../../relational-databases/system-stored-procedures/sp-helplanguage-transact-sql.md)|**sp_helplanguage** [[  **@language =** ] **'***language***'** ]|Restituisce informazioni su formati della data di tutte le lingue supportate. **sp_helplanguage** non è una data o ora stored procedure. Comunque, l'impostazione della lingua influisce sull'output di funzioni di data.|Non applicabile|Non applicabile|  
  
###  <a name="ValidateDateandTimeValues"></a>Funzioni che convalidano i valori di data e ora
  
|Funzione|Sintassi|Valore restituito|Tipo di dati restituito|Determinismo|  
|---|---|---|---|---|
|[ISDATE](../../t-sql/functions/isdate-transact-sql.md)|ISDATE ( *espressione* )|Determina se un **datetime** o **smalldatetime** espressione di input è una data valida o un valore di ora.|**int**|La funzione ISDATE è deterministica solo se utilizzata con la funzione CONVERT, quando viene specificato il parametro di stile della funzione CONVERT e se lo stile è diverso da 0, 100, 9 o 109.|  
  
##  <a name="DateandTimeRelatedTopics"></a>Argomenti data e ora 
  
|Argomento|Description|  
|-----------|-----------------|  
|[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)|Fornisce informazioni sulla conversione di valori della data e ora in e da valori letterali stringa e altri formati della data e ora.|  
|[Scrittura di istruzioni Transact-SQL internazionali](../../relational-databases/collations/write-international-transact-sql-statements.md)|Vengono fornite linee guida per la portabilità di database e applicazioni di database che utilizzano [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzioni da una lingua a altra o che supporta più lingue.|  
|[Funzioni scalari ODBC &#40; Transact-SQL &#41;](../../t-sql/functions/odbc-scalar-functions-transact-sql.md)|Vengono fornite informazioni sulle funzioni scalari ODBC che può essere usato in [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzioni. Ciò include le funzioni di data e ora ODBC.|  
|[FUSO orario &AMP;#40; Transact-SQL &#41;](../../t-sql/queries/at-time-zone-transact-sql.md)|Fornisce la conversione di fuso orario.|  
  
## <a name="see-also"></a>Vedere anche
[Funzioni](../../t-sql/functions/functions.md)  
[Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)
  
  
