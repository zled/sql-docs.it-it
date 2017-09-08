---
title: DateTimeOffset (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/23/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- datetimeoffset_TSQL
- datetimeoffset
dev_langs:
- TSQL
helpviewer_keywords:
- time [SQL Server], data types
- date and time [SQL Server], datetimeoffset
- datetimeoffset data type [SQL Server]
- dates [SQL Server], data types
- data types [SQL Server], date and time
- time zones [SQL Server]
ms.assetid: a0455b71-ca25-476e-a7a8-0770f1860bb7
caps.latest.revision: 41
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9a6c143380711d1af39a6c11f311e9ce3caf87c7
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="datetimeoffset-transact-sql"></a>datetimeoffset (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Definisce una data in combinazione con un'ora del giorno con considerazione del fuso orario ed espressa nel formato 24 ore.
  
## <a name="datetimeoffset-description"></a>descrizione di DateTimeOffset
  
|Proprietà|Valore|  
|---|---|
|Sintassi|**DateTimeOffset** [(*precisione frazionaria dei secondi*)]|  
|Utilizzo|DICHIARARE @MyDatetimeoffset **datetimeoffset(7)**<br /><br /> CREARE una tabella Table1 (Column1 **datetimeoffset(7)** )|  
|Formati predefiniti per i valori letterali stringa (utilizzati per il client legacy)|AAAA-MM-gg hh.mm.ss [. nnnnnnn] [{+ &#124;-} hh: mm]<br /><br /> Per ulteriori informazioni, vedere la sezione seguente relativa alla compatibilità con le versioni precedenti per i client legacy.|  
|Intervallo di date|Da 01-01-0001 a 31-12-9999<br /><br /> 1 gennaio 1 CE e il 31 dicembre 9999 CE|  
|Intervallo di ore|00:00:00 e 23.59.59.9999999 (i secondi frazionari non sono supportati in Informatica)|  
|Intervallo di differenze di fuso orario|-14:00 a + 14:00 (differenza di fuso orario viene ignorata in Informatica)|  
|Intervalli di elementi|AAAA rappresenta un numero di quattro cifre compreso tra 0001 e 9999 indicante l'anno.<br /><br /> MM rappresenta un numero di due cifre compreso tra 01 e 12 indicante un mese dell'anno specificato.<br /><br /> GG rappresenta un numero di due cifre compreso tra 01 e 31, a seconda del mese, indicante il giorno del mese specificato.<br /><br /> hh rappresenta un numero di due cifre compreso tra 00 e 23 indicante l'ora.<br /><br /> mm rappresenta un numero di due cifre compreso tra 00 e 59 indicante i minuti.<br /><br /> ss rappresenta un numero di due cifre compreso tra 00 e 59 indicante i secondi.<br /><br /> n* rappresenta un numero composto da un numero di cifre da 0 a 7 e compreso tra 0 e 9999999, indicante i secondi frazionari. I secondi frazionari non sono supportati in Informatica.<br /><br /> hh rappresenta un numero di due cifre compreso tra -14 e +14. Differenza di fuso orario viene ignorata in Informatica.<br /><br /> mm rappresenta un numero di due cifre compreso tra 00 e 59. Differenza di fuso orario viene ignorata in Informatica.|  
|Lunghezza in caratteri|minimo di 26 posizioni (AAAA-MM-gg hh: mm: {+ &#124;-} hh: mm) a un massimo di 34 (AAAA-MM-GG. di nnnnnnn {+ &#124;-} hh: mm)|  
|Precisione, scala|Vedere la tabella riportata di seguito.|  
|Dimensioni dello spazio di archiviazione|10 byte, fissa è l'impostazione predefinita con l'impostazione predefinita di 100 ns di precisione in secondi frazionari.|  
|Accuratezza|100 nanosecondi|  
|Valore predefinito|1900-01-01 00:00:00 00:00|  
|Calendario|Gregoriano|  
|Precisione in secondi frazionari definita dall'utente|Sì|  
|Considerazione e conservazione delle differenze di fuso orario|Sì|  
|Considerazione dell'ora legale|No|  
  
|Scala specificata|Risultato (precisione, scala)|Lunghezza della colonna (byte)|Precisione in secondi frazionari|  
|---|---|---|---|
|**datetimeoffset**|(34,7)|10|7|  
|**DateTimeOffset(0)**|(26,0)|8|0-2|  
|**DateTimeOffset(1)**|(28,1)|8|0-2|  
|**DateTimeOffset(2)**|(29,2)|8|0-2|  
|**DateTimeOffset(3)**|(30,3)|9|3-4|  
|**DateTimeOffset(4)**|(31,4)|9|3-4|  
|**DateTimeOffset(5)**|(32,5)|10|5-7|  
|**DateTimeOffset(6)**|(33,6)|10|5-7|  
|**DateTimeOffset(7)**|(34,7)|10|5-7|  
  
## <a name="supported-string-literal-formats-for-datetimeoffset"></a>Formati di letterale stringa supportati per datetimeoffset
La tabella seguente elenca i ISO 8601 stringa letterale formati supportati per **datetimeoffset**. Per informazioni sui formati alfabetico, numerici, senza separatori e tempi per le parti di data e ora di **datetimeoffset**, vedere [data &#40; Transact-SQL &#41; ](../../t-sql/data-types/date-transact-sql.md) e [ora &#40; Transact-SQL &#41; ](../../t-sql/data-types/time-transact-sql.md).
  
|ISO 8601|Description|  
|---|---|
|AAAA-MM-ggTHH [. nnnnnnn] [{+ &#124;-} hh: mm]|Su questi due formati non influiscono le impostazioni locali delle sessioni SET LANGUAGE e SET DATEFORMAT. Non sono consentiti spazi tra il **datetimeoffset** e **datetime** parti.|  
|AAAA-MM-GGThh:mm:ss[.nnnnnnn]Z (UTC)|Questo formato per la definizione ISO indica il **datetime** parte deve essere espresso in Coordinated Universal Time (UTC). Ad esempio, 1999-12-12 12:30:30.12345 -07: 00 deve essere rappresentata come 1999-12-12 19:30:30.12345Z.|  
  
## <a name="time-zone-offset"></a>Differenza di fuso orario
Una differenza di fuso orario specifica la differenza di fuso dall'ora UTC per un **ora** o **datetime** valore. La differenza di fuso orario può essere rappresentata nel formato [+|-] hh:mm:
-   hh è un numero di due cifre, compreso tra 00 e 14, che rappresenta il numero di ore della differenza di fuso orario.  
-   mm è un numero di due cifre, compreso tra 00 e 59, che rappresenta il numero di minuti aggiuntivi della differenza di fuso orario.  
-   \+(più) o -(meno) è il segno obbligatorio per una differenza di fuso orario. Indica se la differenza di fuso orario viene aggiunta o sottratta dall'ora UTC per ottenere l'ora locale. L'intervallo valido della differenza di fuso orario è da -14:00 a +14:00.  
  
L'intervallo di differenza di fuso orario segue lo standard XML W3C per la definizione di schemi XSD, leggermente diverso dalla definizione standard di SQL 2003, da 12:59 a +14:00.
  
Il parametro di tipo facoltativo *precisione frazionaria dei secondi* specifica il numero di cifre per la parte frazionaria dei secondi. Questo valore può essere un numero intero con un numero di cifre compreso tra 0 e 7 (100 nanosecondi). Il valore predefinito *precisione frazionaria dei secondi* è 100 NS (sette cifre per la parte frazionaria dei secondi).
  
I dati sono archiviati nel database ed elaborati, confrontati, ordinati e indicizzati nel server come in UTC. La differenza di fuso orario viene mantenuta nel database per il recupero.
  
Differenza di fuso orario specificato verrà considerata ora legale (DST) e regolata per un dato **datetime** che rientra nel periodo di ora legale.
  
Per **datetimeoffset** digitare, UTC e locali (per la differenza di fuso orario persistente o convertita) **datetime** valore verrà convalidato durante le operazioni di assegnazione, convert, aritmetica, update o insert. Il rilevamento di UTC o locale (per la differenza di fuso orario persistente o convertita) non valido **datetime** valore genererà un errore di valore non valido. Ad esempio, 9999-12-31 10:10:00 è valido in UTC ma causa overflow nell'ora locale per la differenza di fuso orario +13:50.
  
Per convertire una data in un oggetto corrispondente **datetimeoffset** valore in una destinazione fuso orario, vedere [AT TIME ZONE &#40; Transact-SQL &#41; ](../../t-sql/queries/at-time-zone-transact-sql.md).
  
## <a name="ansi-and-iso-8601-compliance"></a>Conformità ANSI e ISO 8601  
Le sezioni ANSI e ISO 8601 conformità del [data](../../t-sql/data-types/date-transact-sql.md) e [ora](../../t-sql/data-types/time-transact-sql.md) argomenti si applicano a **datetimeoffset**.
  
## <a name="backward-compatibility-for-down-level-clients"></a>Compatibilità con le versioni precedenti per i client legacy
Alcuni client legacy non supportano il **ora**, **data**, **datetime2** e **datetimeoffset** tipi di dati. Nella tabella seguente viene illustrato il mapping del tipo tra un'istanza di livello principale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e i client legacy.
  
|Tipo di dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|Formato predefiniti dei valori letterali stringa passati al client legacy|ODBC delle versioni precedenti|OLEDB delle versioni precedenti|JDBC delle versioni precedenti|SQLCLIENT delle versioni precedenti|  
|---|---|---|---|---|---|
|**time**|hh:mm:ss[.nnnnnnn]|SQL_WVARCHAR o SQL_VARCHAR|DBTYPE_WSTR o DBTYPE_STR|Java.sql.String|Stringa o SqString|  
|**data**|YYYY-MM-DD|SQL_WVARCHAR o SQL_VARCHAR|DBTYPE_WSTR o DBTYPE_STR|Java.sql.String|Stringa o SqString|  
|**datetime2**|AAAA-MM-GG hh:mm:ss[.nnnnnnn]|SQL_WVARCHAR o SQL_VARCHAR|DBTYPE_WSTR o DBTYPE_STR|Java.sql.String|Stringa o SqString|  
|**datetimeoffset**|AAAA-MM-gg hh.mm.ss [. nnnnnnn] [+ &#124;-] hh: mm|SQL_WVARCHAR o SQL_VARCHAR|DBTYPE_WSTR o DBTYPE_STR|Java.sql.String|Stringa o SqString|  
  
## <a name="converting-date-and-time-data"></a>La conversione dei dati di data e ora
Nella conversione di tipi di dati relativi alla data e all'ora, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono rifiutati tutti i valori non riconosciuti come date o orari. Per informazioni sull'utilizzo delle funzioni CAST e CONVERT con dati di data e ora, vedere [CAST e CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
Durante la conversione in **data**, l'anno, mese e giorno vengono copiati. Nel codice seguente vengono illustrati i risultati della conversione di un valore `datetimeoffset(4)` in un valore `date`.  
  
```sql
DECLARE @datetimeoffset datetimeoffset(4) = '12-10-25 12:32:10 +01:00';  
DECLARE @date date= @datetimeoffset;  
  
SELECT @datetimeoffset AS '@datetimeoffset ', @date AS 'date';  
  
--Result  
--@datetimeoffset                date  
-------------------------------- ----------  
--2025-12-10 12:32:10.0000 +01:0 2025-12-10  
--  
--(1 row(s) affected)  
  
```  
  
Se la conversione a **Time (n)**, i nostri, minuti, secondi e secondi frazionari vengono copiati. Il valore del fuso orario viene troncato. Quando la precisione del **DateTimeOffset (n)** è maggiore della precisione del valore di **Time (n)** valore, il valore viene arrotondato per eccesso. Nel codice seguente vengono illustrati i risultati della conversione di un valore `datetimeoffset(4)` in un valore `time(3)`.
  
```sql
DECLARE @datetimeoffset datetimeoffset(4) = '12-10-25 12:32:10.1237 +01:0';  
DECLARE @time time(3) = @datetimeoffset;  
  
SELECT @datetimeoffset AS '@datetimeoffset ', @time AS 'time';  
  
--Result  
--@datetimeoffset                time  
-------------------------------- ------------  
-- 2025-12-10 12:32:10.1237 +01:00    12:32:10.124  
  
--  
--(1 row(s) affected)  
  
```  
  
Durante la conversione in**datetime**, i valori di data e ora vengono copiati e il fuso orario viene troncato. Quando la precisione frazionaria di **DateTimeOffset (n)** valore è maggiore di tre cifre, il valore viene troncato. Nel codice seguente vengono illustrati i risultati della conversione di un valore `datetimeoffset(4)` in un valore `datetime`.
  
```sql
DECLARE @datetimeoffset datetimeoffset(4) = '12-10-25 12:32:10.1237 +01:0';  
DECLARE @datetime datetime = @datetimeoffset;  
  
SELECT @datetimeoffset AS '@datetimeoffset ', @datetime AS 'datetime';  
  
--Result  
--@datetimeoffset                datetime  
-------------------------------- -----------------------  
--2025-12-10 12:32:10.1237 +01:0 2025-12-10 12:32:10.123  
--  
--(1 row(s) affected)  
```  
  
Per le conversioni in **smalldatetime**, le date e ore vengono copiate. i minuti vengono arrotondati rispetto al valore dei secondi e i secondi vengono impostati su 0. Nel codice seguente vengono illustrati i risultati della conversione di un valore `datetimeoffset(3)` in un valore `smalldatetime`.  
  
```sql
DECLARE @datetimeoffset datetimeoffset(3) = '1912-10-25 12:24:32 +10:0';  
DECLARE @smalldatetime smalldatetime = @datetimeoffset;  
  
SELECT @datetimeoffset AS '@datetimeoffset', @smalldatetime AS '@smalldatetime';  
  
--Result  
--@datetimeoffset                @smalldatetime  
-------------------------------- -----------------------  
--1912-10-25 12:24:32.000 +10:00 1912-10-25 12:25:00  
--  
--(1 row(s) affected)  
```  
  
Se la conversione a **datetime2**, data e ora vengono copiati il **datetime2** valore e il fuso orario viene troncato. Quando la precisione del **datetime2** è maggiore della precisione del valore di **DateTimeOffset (n)** valore, i secondi frazionari vengono troncati. Nel codice seguente vengono illustrati i risultati della conversione di un valore `datetimeoffset(4)` in un valore `datetime2(3)`.
  
```sql
DECLARE @datetimeoffset datetimeoffset(4) = '1912-10-25 12:24:32.1277 +10:0';  
DECLARE @datetime2 datetime2(3)=@datetimeoffset;  
  
SELECT @datetimeoffset AS '@datetimeoffset', @datetime2 AS '@datetime2';  
  
--Result  
@datetimeoffset                    @datetime2  
---------------------------------- ----------------------  
1912-10-25 12:24:32.1277 +10:00    1912-10-25 12:24:32.12  
  
--(1 row(s) affected)  
```  
  
### <a name="converting-datetimeoffset-data-type-to-other-date-and-time-types"></a>Conversione di tipi di tempo e il tipo di dati datetimeoffset in altri data
La tabella seguente descrive ciò che accade quando un **datetimeoffset** tipo di dati viene convertito in altri tipi di dati data e ora.
  
### <a name="converting-string-literals-to-datetimeoffset"></a>Conversione di valori letterali stringa a datetimeoffset
Le conversioni da valori letterali stringa a tipi di data e ora sono consentite se tutte le parti delle stringhe hanno formati validi. In caso contrario, viene generato un errore di runtime. Le conversioni implicite o esplicite che non specificano uno stile, dai tipi di data e ora ai valori letterali stringa, saranno nel formato predefinito della sessione corrente. Nella tabella seguente vengono illustrate le regole per la conversione di una stringa letterale per il **datetimeoffset** tipo di dati.
  
|Valore letterale stringa di input|**DateTimeOffset (n)**|  
|---|---|
|ODBC DATE|Vengono eseguito il mapping di valori letterali stringa ODBC per la **datetime** tipo di dati. Qualsiasi operazione di assegnazione dai valori letterali di ODBC DATETIME in **datetimeoffset** tipi provocheranno una conversione implicita tra **datetime** e questo tipo in base a quanto definito dalle regole di conversione.|  
|ODBC TIME|Vedere la regola relativa a ODBC DATE.|  
|ODBC DATETIME|Vedere la regola relativa a ODBC DATE.|  
|Solo DATE|Il valore predefinito per la parte di TIME è 00:00:00. Il valore predefinito di TIMEZONE è +00:00:00.|  
|solo TIME|Il valore predefinito per la parte di DATE è 1900-1-1. Il valore predefinito di TIMEZONE è +00:00.|  
|solo TIMEZONE|Vengono forniti i valori predefiniti.|  
|DATE + TIME|Il valore predefinito di TIMEZONE è +00:00:00.|  
|DATE + TIMEZONE|Non consentiti|  
|TIME + TIMEZONE|Il valore predefinito per la parte di DATE è 1900-1-1.|  
|DATE + TIME + TIMEZONE|Semplice|  
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente vengono confrontati i risultati dell'esecuzione del cast di una stringa a ciascun **data** e **ora** tipo di dati.
  
```sql
SELECT   
     CAST('2007-05-08 12:35:29. 1234567 +12:15' AS time(7)) AS 'time'   
    ,CAST('2007-05-08 12:35:29. 1234567 +12:15' AS date) AS 'date'   
    ,CAST('2007-05-08 12:35:29.123' AS smalldatetime) AS   
        'smalldatetime'   
    ,CAST('2007-05-08 12:35:29.123' AS datetime) AS 'datetime'   
    ,CAST('2007-05-08 12:35:29.1234567+12:15' AS datetime2(7)) AS   
        'datetime2'  
    ,CAST('2007-05-08 12:35:29.1234567 +12:15' AS datetimeoffset(7)) AS   
        'datetimeoffset'  
    ,CAST('2007-05-08 12:35:29.1234567+12:15' AS datetimeoffset(7)) AS  
        'datetimeoffset IS08601';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
|Tipo di dati|Output|  
|---|---|
|**Time**|12:35:29. 1234567|  
|**Data**|2007-05-08|  
|**Smalldatetime**|2007-05-08 12:35:00|  
|**DateTime**|2007-05-08 12:35:29.123|  
|**datetime2**|2007-05-08 12:35:29. 1234567|  
|**DateTimeOffset**|2007-05-08 12:35:29.1234567 +12:15|  
  
## <a name="see-also"></a>Vedere anche
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[FUSO orario &AMP; #40; Transact-SQL &#41;](../../t-sql/queries/at-time-zone-transact-sql.md)
  
  

