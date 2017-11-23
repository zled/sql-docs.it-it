---
title: Data (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- date_TSQL
- date
dev_langs: TSQL
helpviewer_keywords:
- data types [SQL Server], date
- date and time [SQL Server], date
- dates [SQL Server], data types
- date data type [SQL Server]
- data types [SQL Server], date and time
ms.assetid: c963e8b4-5a85-4bd0-9d48-3f8da8f6516b
caps.latest.revision: "44"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: bc3d838c81ea8d973cff90e2e57e4bfd8b443f69
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="date-transact-sql"></a>date (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Definisce una data in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
## <a name="date-description"></a>descrizione data
  
|Proprietà|Valore|  
|--------------|-----------|  
|Sintassi|**data**|  
|Utilizzo|DICHIARARE @MyDate **Data**<br /><br /> Crea tabella Table1 (Column1 **data** )|  
|Formato predefinito dei valori letterali stringa<br /><br /> (utilizzato per client legacy)|YYYY-MM-DD<br /><br /> Per ulteriori informazioni, vedere la sezione seguente relativa alla compatibilità con le versioni precedenti per i client legacy.|  
|Intervallo|0001-01-01 e 9999-12-31 (1582-10-15 a 9999-12-31 per Informatica)<br /><br /> 1 gennaio 1 CE e il 31 dicembre 9999 CE (15 ottobre 1582 CE e il 31 dicembre, 9999 CE per Informatica)|  
|Intervalli di elementi|AAAA rappresenta un numero di quattro cifre compreso tra 0001 e 9999 indicante l'anno. Per Informatica, aaaa è limitato all'intervallo 1582 a 9999.<br /><br /> MM rappresenta un numero di due cifre compreso tra 01 e 12 indicante un mese dell'anno specificato.<br /><br /> GG rappresenta un numero di due cifre compreso tra 01 e 31, a seconda del mese, indicante il giorno del mese specificato.|  
|Lunghezza in caratteri|10 posizioni|  
|Precisione, scala|10, 0|  
|Dimensioni dello spazio di archiviazione|3 byte, fissa|  
|Struttura di archiviazione|Valore intero di 1, 3 byte archivia la data.|  
|Accuratezza|Un giorno|  
|Valore predefinito|1900-01-01<br /><br /> Questo valore viene utilizzato per la parte relativa alla data per la conversione implicita da **ora** a **datetime2** o **datetimeoffset**.|  
|Calendario|Gregoriano|  
|Precisione in secondi frazionari definita dall'utente|No|  
|Considerazione e conservazione delle differenze di fuso orario|No|  
|Considerazione dell'ora legale|No|  
  
## <a name="supported-string-literal-formats-for-date"></a>Formati di valore letterale stringa è supportato per data
Le tabelle seguenti illustrano la stringa valida di formati di valore letterale per il **data** tipo di dati.
  
|Numeric|Description|  
|-------------|-----------------|  
|mdy<br /><br /> [m] m/gg/aa [Aa]<br /><br /> [m] m - dd-[Aa] AA<br /><br /> [m]m.dd. [Aa] AA<br /><br /> myd<br /><br /> mm / aa [Aa]<br /><br /> mm-[Aa] AA<br /><br /> [m] m [Aa] yy.dd<br /><br /> DMY<br /><br /> gg / [m] m / [Aa] AA<br /><br /> gg-[m] m-[Aa] AA<br /><br /> gg. [m] m [Aa] AA<br /><br /> dym<br /><br /> gg / aa [Aa] / [m] m<br /><br /> gg-[Aa] AA-[m] m<br /><br /> gg. [Aa] aa. [m] m<br /><br /> AMG<br /><br /> [Aa] AA / [m] m/aaaa<br /><br /> [Aa] AA-[m] m-gg.<br /><br /> [Aa] AA-[m] m-gg.|[m]m, gg e [aa]aa rappresentano il mese, il giorno e l'anno all'interno di una stringa in cui sono utilizzati come separatori la barra (/), il segno meno (-) o il punto (.).<br /><br /> Sono supportati solo anni a due cifre o a quattro cifre. Utilizzare sempre anni a quattro cifre quando possibile. Per specificare un numero intero compreso tra 0001 e 9999 che rappresenta l'anno di cambio data per l'interpretazione degli anni a due cifre come anni a quattro cifre, utilizzare il [configurare l'anno a due cifre cutoff Server Configuration Option](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md).<br /><br /> **Nota.** Per Informatica, aaaa è limitato all'intervallo 1582 a 9999.<br /><br /> Un anno a due cifre con valore minore o uguale alle ultime due cifre dell'anno di cambio data si trova nello stesso secolo dell'anno di cambio data. Un anno a due cifre con valore maggiore delle ultime due cifre dell'anno di cambio data si trova nel secolo precedente a quello dell'anno di cambio data. Ad esempio, se il valore dell'anno di cambio data è 2049 (impostazione predefinita), l'anno a due cifre 49 è interpretato come 2049 mentre l'anno a due cifre 50 è interpretato come 1950.<br /><br /> Il formato predefinito della data è determinato dall'impostazione della lingua corrente. È possibile modificare il formato di data utilizzando il [SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md) e [SET DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md) istruzioni.<br /><br /> Il **agm** formato non è supportato per **data**.|  
  
|Espressione alfabetica|Description|  
|------------------|-----------------|  
|mese [gg] [,] aaaa<br /><br /> mes gg [,] [Aa] AA<br /><br /> mese aaaa [gg]<br /><br /> [gg] mese [,] aaaa<br /><br /> gg mese [,] [Aa] AA<br /><br /> gg [Aa] AA mese<br /><br /> aaaa [gg] mese<br /><br /> aaaa mese [gg]<br /><br /> aaaa [gg] mese|**LUN** rappresenta il nome completo o l'abbreviazione del mese nella lingua corrente. Le virgole sono facoltative e l'uso delle maiuscole è ignorato.<br /><br /> Per evitare ambiguità, esprimere gli anni nel formato a quattro cifre.<br /><br /> Se manca il giorno, viene inserito il primo giorno del mese.|  
  
|ISO 8601|Descrizione|  
|--------------|----------------|  
|YYYY-MM-DD<br /><br /> YYYYMMDD|Uguale allo standard SQL. Si tratta dell'unico formato definito come standard internazionale.|  
  
|Senza separatori|Description|  
|-----------------|-----------------|  
|yymmdd [Aa]<br /><br /> aaaa [gg] [mm]|Il **data** dati possono essere specificati con quattro, sei o otto cifre. Una stringa a sei o otto cifre viene sempre interpretata come **AMG**. Il mese e il giorno devono sempre essere rappresentati da due cifre. Una stringa di quattro cifre viene interpretata come anno.|  
  
|ODBC|Description|  
|----------|-----------------|  
|{d 'aaaa-mm-gg'}|Specifico delle API ODBC|  
  
|Formato W3C XML|Description|  
|--------------------|-----------------|  
|aaaa-mm-ddTZD|Specificamente supportato per l'utilizzo di XML/SOAP.<br /><br /> TZD è l'identificatore del fuso orario (Z, + hh:mm o - hh:mm):<br /><br /> -hh: mm rappresenta la differenza di fuso orario. hh è un numero di due cifre, compreso tra 0 e 14, che rappresenta il numero di ore della differenza di fuso orario.<br />-MM è il numero di due cifre compreso tra 0 e 59, che rappresenta il numero di minuti aggiuntivi della differenza di fuso orario.<br />-+ (più) o -(meno), il segno obbligatorio della differenza di fuso orario. Indica che la differenza di fuso orario viene aggiunta o sottratta dall'ora UTC (Coordinated Universal Times) per ottenere l'ora locale. L'intervallo valido della differenza di fuso orario è da -14:00 a +14:00.|  
  
## <a name="ansi-and-iso-8601-compliance"></a>Conformità ANSI e ISO 8601  
**Data** è conforme alla definizione dello standard ANSI SQL per il calendario gregoriano: "NOTE 85 - Datetime, tipi di dati consentirà le date nel formato gregoriano da archiviare in date range 0001 – 01 – 01 CE tramite 9999 – 12 – 31 CE."
  
Il formato predefinito dei valori letterali stringa utilizzato per i client legacy è conforme al formato standard SQL, definito come AAAA-MM-GG. Questo formato è lo stesso della definizione ISO 8601 per DATE.
  
> [!NOTE]  
>  Per Informatica, l'intervallo è limitato a 1582-10-15 (15 ottobre 1582 CE) e 9999-12-31 (31 dicembre 9999 CE).  
  
## <a name="backward-compatibility-for-down-level-clients"></a>Compatibilità con le versioni precedenti per i client legacy
Alcuni client legacy non supportano il **ora**, **data**, **datetime2** e **datetimeoffset** tipi di dati. Nella tabella seguente viene illustrato il mapping del tipo tra un'istanza di livello principale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e i client legacy.
  
|Tipo di dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|Formato predefiniti dei valori letterali stringa passati al client legacy|ODBC delle versioni precedenti|OLEDB delle versioni precedenti|JDBC delle versioni precedenti|SQLCLIENT delle versioni precedenti|  
| --- | --- | --- | --- | --- | --- |
|**time**|hh:mm:ss[.nnnnnnn]|SQL_WVARCHAR o SQL_VARCHAR|DBTYPE_WSTR o DBTYPE_STR|Java.sql.String|Stringa o SqString|  
|**data**|YYYY-MM-DD|SQL_WVARCHAR o SQL_VARCHAR|DBTYPE_WSTR o DBTYPE_STR|Java.sql.String|Stringa o SqString|  
|**datetime2**|AAAA-MM-GG hh:mm:ss[.nnnnnnn]|SQL_WVARCHAR o SQL_VARCHAR|DBTYPE_WSTR o DBTYPE_STR|Java.sql.String|Stringa o SqString|  
|**datetimeoffset**|AAAA-MM-gg hh.mm.ss [. nnnnnnn] [+ &#124;-] hh: mm|SQL_WVARCHAR o SQL_VARCHAR|DBTYPE_WSTR o DBTYPE_STR|Java.sql.String|Stringa o SqString|  
  
## <a name="converting-date-and-time-data"></a>La conversione dei dati di data e ora
Nella conversione di tipi di dati relativi alla data e all'ora, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono rifiutati tutti i valori non riconosciuti come date o orari. Per informazioni sull'utilizzo delle funzioni CAST e CONVERT con dati di data e ora, vedere [CAST e CONVERT &#40; Transact-SQL &#41; ](../../t-sql/functions/cast-and-convert-transact-sql.md).
  
Quando la conversione viene eseguita a **Time (n)**, la conversione non riesce e viene generato il messaggio di errore 206: "conflitto del tipo di operando: date è incompatibile con time".
  
Se la conversione a **datetime**, la data viene copiata e il componente della fase è impostato su 00.00.00.000. Nel codice seguente vengono illustrati i risultati della conversione di un valore `date` in un valore `datetime`.  
  
```sql
DECLARE @date date= '12-10-25';  
DECLARE @datetime datetime= @date;  
  
SELECT @date AS '@date', @datetime AS '@datetime';  
  
--Result  
--@date      @datetime  
------------ -----------------------  
--2025-12-10 2025-12-10 00:00:00.000  
--  
--(1 row(s) affected)  
```  
  
Nel caso di conversione **smalldatetime**, quando il **data** valore è compreso nell'intervallo di un [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md), viene copiato il componente di data e l'ora viene impostato su 00:00:00. Quando il **data** valore è compreso nell'intervallo di un **smalldatetime** viene generato valore, il messaggio di errore 242: "la conversione di un **data** tipo di dati un  **smalldatetime** risultati al tipo di dati in un valore; out-of-range e **smalldatetime** è impostato su NULL. Nel codice seguente vengono illustrati i risultati della conversione di un valore `date` in un valore `smalldatetime`.
  
```sql
DECLARE @date date= '1912-10-25';  
DECLARE @smalldatetime smalldatetime = @date;  
  
SELECT @date AS '@date', @smalldatetime AS '@smalldatetime';  
  
--Result  
--@date      @smalldatetime  
------------ -----------------------  
--1912-10-25 1912-10-25 00:00:00  
--  
--(1 row(s) affected)  
```  
  
Quando la conversione viene eseguita a **DateTimeOffset (n)**, la data viene copiata e l'ora è impostata su 00: 00.0000000 + 00:00. Nel codice seguente vengono illustrati i risultati della conversione di un valore `date` in un valore `datetimeoffset(3)`.
  
```sql
DECLARE @date date = '1912-10-25';  
DECLARE @datetimeoffset datetimeoffset(3) = @date;  
  
SELECT @date AS '@date', @datetimeoffset AS '@datetimeoffset';  
  
--Result  
--@date      @datetimeoffset  
------------ ------------------------------  
--1912-10-25 1912-10-25 00:00:00.000 +00:00  
--  
--(1 row(s) affected)  
```  
  
Se la conversione a **datetime2**, viene copiato il componente di data e l'ora viene impostato su 00.00.00.00 indipendentemente dal valore di (n). Nel codice seguente vengono illustrati i risultati della conversione di un valore `date` in un valore `datetime2(3)`.
  
```sql
DECLARE @date date = '1912-10-25';  
DECLARE @datetime2 datetime2(3) = @date;  
  
SELECT @date AS '@date', @datetime2 AS '@datetime2(3)';  
  
--Result  
--@date      @datetime2(3)  
------------ -----------------------  
--1912-10-25 1912-10-25 00:00:00.00  
--  
--(1 row(s) affected)  
```  
  
### <a name="converting-date-to-other-date-and-time-types"></a>Conversione di date in altri tipi di data e ora
In questa sezione viene descritto cosa accade quando un **data** tipo di dati viene convertito in altri tipi di dati data e ora.
  
Quando la conversione viene eseguita a **Time (n)**, la conversione non riesce e viene generato il messaggio di errore 206: "conflitto del tipo di operando: date è incompatibile con time".
  
Se la conversione a **datetime**, data viene copiata. Nel codice seguente vengono illustrati i risultati della conversione di un valore `date` in un valore `datetime`.
  
```sql
DECLARE @date date= '12-10-25';  
DECLARE @datetime datetime= @date;  
  
SELECT @date AS '@date', @datetime AS '@datetime';  
  
--Result  
--@date      @datetime  
------------ -----------------------  
--2025-12-10 2025-12-10 00:00:00.000  
--  
--(1 row(s) affected)  
```  
  
Quando la conversione viene eseguita a **smalldatetime**, **data** valore è compreso nell'intervallo di un [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md), viene copiato il componente di data e l'ora viene impostato su 00.00.00.000. Quando il **data** valore è compreso nell'intervallo di un **smalldatetime** viene generato valore, il messaggio di errore 242: "la conversione di un tipo di dati date in un tipo di dati smalldatetime ha generato un valore di out-of-range."; e **smalldatetime** è impostato su NULL. Nel codice seguente vengono illustrati i risultati della conversione di un valore `date` in un valore `smalldatetime`.
  
```sql
DECLARE @date date= '1912-10-25';  
DECLARE @smalldatetime smalldatetime = @date;  
  
SELECT @date AS '@date', @smalldatetime AS '@smalldatetime';  
  
--Result  
--@date      @smalldatetime  
------------ -----------------------  
--1912-10-25 1912-10-25 00:00:00  
--  
--(1 row(s) affected)  
```  
  
Per la conversione in **DateTimeOffset (n)**data viene copiata e l'ora è impostata su 00: 00.0000000 + 00:00. Nel codice seguente vengono illustrati i risultati della conversione di un valore `date` in un valore `datetimeoffset(3)`.
  
```sql
DECLARE @date date = '1912-10-25';  
DECLARE @datetimeoffset datetimeoffset(3) = @date;  
  
SELECT @date AS '@date', @datetimeoffset AS '@datetimeoffset';  
  
--Result  
--@date      @datetimeoffset  
------------ ------------------------------  
--1912-10-25 1912-10-25 00:00:00.000 +00:00  
--  
--(1 row(s) affected)  
```  
  
Quando la conversione viene eseguita a **datetime2**, viene copiato il componente di data e l'ora viene impostato su 00: 00.000000. Nel codice seguente vengono illustrati i risultati della conversione di un valore `date` in un valore `datetime2(3)`.
  
```sql
DECLARE @date date = '1912-10-25'  
DECLARE @datetime2 datetime2(3) = @date;  
  
SELECT @date AS '@date', @datetime2 AS '@datetime2(3)';  
  
--Result  
--@date      @datetime2(3)  
------------ -----------------------  
--1912-10-25 1912-10-25 00:00:00.000  
--  
--(1 row(s) affected)  
```  
  
### <a name="converting-string-literals-to-date"></a>Conversione di valori letterali stringa in una data
Le conversioni da valori letterali stringa a tipi di data e ora sono consentite se tutte le parti delle stringhe hanno formati validi. In caso contrario, viene generato un errore di runtime. Le conversioni implicite o esplicite che non specificano uno stile, dai tipi di data e ora ai valori letterali stringa, saranno nel formato predefinito della sessione corrente. Nella tabella seguente vengono illustrate le regole per la conversione di una stringa letterale per il **data** tipo di dati.
  
|Valore letterale stringa di input|**data**|  
|---|---|
|ODBC DATE|Vengono eseguito il mapping di valori letterali stringa ODBC per la **datetime** tipo di dati. Qualsiasi operazione di assegnazione dai valori letterali di ODBC DATETIME in un **data** tipo provocheranno una conversione implicita tra **datetime** e questo tipo in base a quanto definito dalle regole di conversione.|  
|ODBC TIME|Vedere la regola relativa a ODBC DATE.|  
|ODBC DATETIME|Vedere la regola relativa a ODBC DATE.|  
|Solo DATE|Semplice|  
|solo TIME|Vengono forniti i valori predefiniti.|  
|solo TIMEZONE|Vengono forniti i valori predefiniti.|  
|DATE + TIME|Viene utilizzata la parte di DATE della stringa di input.|  
|DATE + TIMEZONE|Non consentiti.|  
|TIME + TIMEZONE|Vengono forniti i valori predefiniti.|  
|DATE + TIME + TIMEZONE|Verrà utilizzata la parte DATE di DATETIME locale.|  
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente vengono confrontati i risultati dell'esecuzione del cast di una stringa ai tipi di dati relativi a data e ora.
  
```sql
SELECT   
     CAST('2007-05-08 12:35:29. 1234567 +12:15' AS time(7)) AS 'time'   
    ,CAST('2007-05-08 12:35:29. 1234567 +12:15' AS date) AS 'date'   
    ,CAST('2007-05-08 12:35:29.123' AS smalldatetime) AS   
        'smalldatetime'   
    ,CAST('2007-05-08 12:35:29.123' AS datetime) AS 'datetime'   
    ,CAST('2007-05-08 12:35:29. 1234567 +12:15' AS datetime2(7)) AS   
        'datetime2'  
    ,CAST('2007-05-08 12:35:29.1234567 +12:15' AS datetimeoffset(7)) AS   
        'datetimeoffset';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
|Tipo di dati|Output|  
|---------------|------------|  
|**time**|12:35:29. 1234567|  
|**data**|2007-05-08|  
|**smalldatetime**|2007-05-08 12:35:00|  
|**datetime**|2007-05-08 12:35:29.123|  
|**datetime2**|2007-05-08 12:35:29. 1234567|  
|**datetimeoffset**|2007-05-08 12:35:29.1234567 +12:15|  
  
## <a name="see-also"></a>Vedere anche
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  
