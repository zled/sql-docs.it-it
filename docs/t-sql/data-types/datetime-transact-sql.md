---
title: DateTime (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- datetime_TSQL
- datetime
dev_langs:
- TSQL
helpviewer_keywords:
- time [SQL Server], data types
- date and time [SQL Server], datetime
- dates [SQL Server], data types
- datetime data type [SQL Server]
- data types [SQL Server], date and time
ms.assetid: 9bd1cc5b-227b-4032-95d6-7581ddcc9924
caps.latest.revision: 64
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ae40eaacd6fd441ce0bdbadd3af02b7b189704a2
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="datetime-transact-sql"></a>datetime (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Definisce una data costituita dalla combinazione di un'ora del giorno e di secondi frazionari ed espressa nel formato 24 ore.
  
> [!NOTE]  
>  Utilizzare il **ora**, **data**, **datetime2** e **datetimeoffset** tipi di dati per un nuovo lavoro. Questi tipi sono conformi allo standard SQL. e offrono una migliore portabilità. **tempo**, **datetime2** e **datetimeoffset** offrono una maggiore precisione dei secondi. **DateTimeOffset** fornisce supporto del fuso orario per le applicazioni distribuite globalmente.  
  
## <a name="datetime-description"></a>Descrizione di datetime  
  
|Proprietà|Valore|  
|---|---|
|Sintassi|**datetime**|  
|Utilizzo|DICHIARARE @MyDatetime **datetime**<br /><br /> Crea tabella Table1 (Column1 **datetime** )|  
|Formati predefiniti dei valori letterali stringa<br /><br /> (utilizzato per client legacy)|Non applicabile|  
|Intervallo di date|Da 01.01.53 a 31.12.99|  
|Intervallo di ore|00:00:00 a 23:59:59.997|  
|Intervallo di differenze di fuso orario|Nessuno|  
|Intervalli di elementi|AAAA rappresenta un numero di quattro cifre compreso tra 1753 e 9999 indicante l'anno.<br /><br /> MM rappresenta un numero di due cifre compreso tra 01 e 12 indicante un mese dell'anno specificato.<br /><br /> GG rappresenta un numero di due cifre compreso tra 01 e 31, a seconda del mese, indicante il giorno del mese specificato.<br /><br /> hh rappresenta un numero di due cifre compreso tra 00 e 23 indicante l'ora.<br /><br /> mm rappresenta un numero di due cifre compreso tra 00 e 59 indicante i minuti.<br /><br /> ss rappresenta un numero di due cifre compreso tra 00 e 59 indicante i secondi.<br /><br /> n* rappresenta un numero composto da un numero di cifre da 0 a 3 e compreso tra 0 e 999, indicante i secondi frazionari.|  
|Lunghezza in caratteri|Da 19 posizioni minimo a 23 massimo|  
|Dimensioni dello spazio di archiviazione|8 byte|  
|Accuratezza|Arrotondato a incrementi di 0,000, 0,003 o 0,007 secondi|  
|Valore predefinito|1900-01-01 00:00:00|  
|Calendario|Gregoriano. Non è incluso l'intervallo completo di anni.|  
|Precisione in secondi frazionari definita dall'utente|No|  
|Considerazione e conservazione delle differenze di fuso orario|No|  
|Considerazione dell'ora legale|No|  
  
## <a name="supported-string-literal-formats-for-datetime"></a>Formati di valore letterale stringa supportati per datetime  
Le tabelle seguenti elencano i formati di valore letterale stringa supportati per **datetime**. Eccezione ODBC **datetime** valori letterali stringa sono le virgolette singole ('), ad esempio, 'string_literaL'. Se l'ambiente non è **us_english**, i valori letterali di stringa devono essere nel formato n' string_literaL'.
  
|Numeric|Description|  
|---|---|
|Formati di data:<br /><br /> [0]4/15/[19]96 -- (mga)<br /><br /> [0]4-15-[19]96 -- (mga)<br /><br /> [0]4.15.[19]96 -- (mga)<br /><br /> [0]4/[19]96/15 -- (mag)<br /><br /> 15/[0]4/[19]96 -- (gma)<br /><br /> 15/[19]96/[0]4 -- (gam)<br /><br /> [19]96/15/[0]4 -- (agm)<br /><br /> [19]96/[0]4/15 -- (amg)<br /><br /> Formati di ora:<br /><br /> 14:30<br /><br /> 14:30[:20:999]<br /><br /> 14:30[:20.9]<br /><br /> 4am<br /><br /> 4 PM|È possibile specificare i dati relativi alla data specificando il mese in formato numerico. Ad esempio, 5/20/97 rappresenta il ventesimo giorno di maggio 1997. Quando si utilizza il formato di data numerico, specificare il mese, il giorno e l'anno all'interno della stessa stringa utilizzando come separatori la barra (/), il segno meno (-) o il punto (.). Il formato corretto è il seguente:<br /><br /> *numero separatore numero separatore numero [time] [time]*<br /><br /> <br /><br /> Quando la lingua è impostata su **us_english**, l'ordine predefinito per la data è MGA. È possibile modificare l'ordine della data utilizzando il [SET DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md) istruzione.<br /><br /> L'impostazione dell'istruzione SET DATEFORMAT determina la modalità di interpretazione dei valori di data. Se l'ordine non corrisponde all'impostazione, i valori non vengono interpretati come date perché non compresi nell'intervallo valido oppure non vengono interpretati correttamente. La data 12/10/08 può ad esempio essere interpretata in sei modi diversi a seconda dell'impostazione di DATEFORMAT. Un anno in quattro parti è interpretato come anno.|  
  
|Espressione alfabetica|Description|  
|---|---|
|Apr[ile] [15][,] 1996<br /><br /> Apr[ile] 15[,] [19]96<br /><br /> Apr[ile] 1996 [15]<br /><br /> [15] Apr[ile][,] 1996<br /><br /> 15 Apr[ile][,][19]96<br /><br /> 15 [19]96 apr[ile]<br /><br /> [15] 1996 apr[ile]<br /><br /> 1996 APR[ILE] [15]<br /><br /> 1996 [15] APR[ILE]|È possibile specificare dati relativi alla data con il mese specificato con il nome completo. Ad esempio, aprile o l'abbreviazione del mese di aprile specificata nel linguaggio corrente. Le virgole sono facoltative e l'uso delle maiuscole è ignorato.<br /><br /> Di seguito vengono riportate alcune linee guida per l'utilizzo dei formati di data alfabetici:<br /><br /> 1) racchiudere i dati di data e ora tra virgolette singole ('). Per le lingue diverse dall'inglese, utilizzare N'<br /><br /> 2) i caratteri racchiusi tra parentesi quadre sono facoltativi.<br /><br /> 3) se si specificano solo le ultime due cifre dell'anno, i valori minori delle ultime due cifre del valore del [configurare l'anno a due cifre cutoff Server Configuration Option](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md) opzione di configurazione si trovano in stesso secolo dell'anno di cambio Data . I valori maggiori o uguali al valore di questa opzione vengono interpretati come appartenenti al secolo che precede l'anno di cambio data. Ad esempio, se **cambio data per anno a due cifre** è 2050 (impostazione predefinita), 25 è interpretato come 2025 mentre 50 è interpretato come 1950. Per evitare ambiguità, esprimere gli anni nel formato a quattro cifre.<br /><br /> 4) se il giorno è mancano, viene fornito il primo giorno del mese.<br /><br /> <br /><br /> Quando si specifica il mese in formato alfabetico, l'impostazione SET DATEFORMAT della sessione non viene applicata.|  
  
|ISO 8601|Description|  
|---|---|
|AAAA-MM-GGThh:mm:ss [.mmm]<br /><br /> AAAAMMGG[ hh:mm:ss[.mmm]]|Esempi:<br /><br /> 1) 2004-05-23T14:25:10<br /><br /> 2) 2004-05-23T14:25:10.487<br /><br /> <br /><br /> Per utilizzare il formato ISO 8601, è necessario specificare ogni elemento in tale formato, Ciò include anche il **T**, due punti (:) e il punto (.) che vengono visualizzati nel formato.<br /><br /> Le parentesi indicano che la frazione del componente dei secondi è facoltativa. Il componente dell'ora viene specificato nel formato 24 ore.<br /><br /> T indica l'inizio della parte del tempo di **datetime** valore.<br /><br /> Il vantaggio dell'utilizzo del formato ISO 8601 consiste nel fatto che è uno standard internazionale con specifiche chiare. Inoltre, questo formato non è interessato da SET DATEFORMAT o [SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md) impostazione.|  
  
|Senza separatori|Description|  
|---|---|
|AAAAMMGG hh:mm:ss[.mmm]||  
  
|ODBC|Description|  
|---|---|
|{ ts '1998-05-02 01:23:56.123' }<br /><br /> { d '1990-10-02' }<br /><br /> { t '13:33:41' }|L'API ODBC definisce sequenze di escape per la rappresentazione dei valori di data e ora, che in ODBC sono denominati dati timestamp. Il formato timestamp ODBC è anche supportato dalla definizione del linguaggio OLE DB (DBGUID-SQL) supportata dal [!INCLUDE[msCoName](../../includes/msconame-md.md)] provider OLE DB per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Nelle applicazioni che utilizzano API basate su ADO, OLE DB e ODBC è possibile utilizzare il formato timestamp ODBC per la rappresentazione di valori di data e ora.<br /><br /> Sequenze di escape del timestamp ODBC sono nel formato: { *seguenti:* '*constant_value*'}:<br /><br /> <br /><br /> - *seguenti:* specifica il tipo della sequenza di escape. Timestamp dispongono di tre *seguenti:* identificatori:<br />1) d = solo data<br />2) t = solo ora<br />3) ts = timestamp (ora + data)<br /><br /> <br /><br /> -'*constant_value*' è il valore della sequenza di escape. *constant_value* deve seguire questi formati per ogni *seguenti:*.<br />d: aaaa-mm-gg.<br />t: hh.mm.ss [. fff]<br />Servizi terminal: aaaa-mm-gg hh.mm.ss [. fff]|  
  
## <a name="rounding-of-datetime-fractional-second-precision"></a>Arrotondamento della precisione in secondi frazionari dei valori datetime  
**DateTime** i valori vengono arrotondati con incrementi di.000,.003 o.007 secondi, come illustrato nella tabella seguente.
  
|Valore specificato dall'utente|Valore archiviato dal sistema|  
|---|---|
|01/01/98 23:59:59.999|1998-01-02 00:00:00.000|  
|01/01/98 23:59:59.995<br /><br /> 01/01/98 23:59:59.996<br /><br /> 01/01/98 23:59:59.997<br /><br /> 01/01/98 23:59:59.998|1998-01-01 23:59:59.997|  
|01/01/98 23:59:59.992<br /><br /> 01/01/98 23:59:59.993<br /><br /> 01/01/98 23:59:59.994|1998-01-01 23:59:59.993|  
|01/01/98 23:59:59.990<br /><br /> 01/01/98 23:59:59.991|1998-01-01 23:59:59.990|  
  
## <a name="ansi-and-iso-8601-compliance"></a>Conformità agli standard ANSI e ISO 8601  
**DateTime** non ANSI o ISO 8601 conforme.
  
##  <a name="_datetime"></a>Conversione di data e ora  
Nella conversione di tipi di dati relativi alla data e all'ora, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono rifiutati tutti i valori non riconosciuti come date o orari. Per informazioni sull'utilizzo delle funzioni CAST e CONVERT con dati di data e ora, vedere [CAST e CONVERT &#40; Transact-SQL &#41; ](../../t-sql/functions/cast-and-convert-transact-sql.md).
  
### <a name="converting-other-date-and-time-types-to-the-datetime-data-type"></a>Conversione di altri tipi di data e ora per il tipo di dati datetime 
In questa sezione viene descritto cosa accade quando vengono convertiti in altri tipi di dati data e ora di **datetime** tipo di dati.  
  
Quando la conversione è da **data**, l'anno, mese e giorno vengono copiati. Il componente relativo all'ora viene impostato su 00:00:00.000. Nel codice seguente vengono illustrati i risultati della conversione di un valore `date` in un valore `datetime`.  
  
```sql
DECLARE @date date = '12-21-16';  
DECLARE @datetime datetime = @date;  
  
SELECT @datetime AS '@datetime', @date AS '@date';  
  
--Result  
--@datetime               @date  
------------------------- ----------  
--2016-12-21 00:00:00.000 2016-12-21  
```  
  
Quando la conversione è da **Time (n)**, viene copiato il componente di ora e il componente Data è impostato su ' 1900-01-01'. Quando la precisione frazionaria di **Time (n)** valore è maggiore di tre cifre, il valore verrà troncato in base. Nell'esempio seguente vengono illustrati i risultati della conversione di un valore `time(4)` in un valore `datetime`.  
  
```sql
DECLARE @time time(4) = '12:10:05.1237';  
DECLARE @datetime datetime = @time;  
  
SELECT @datetime AS '@datetime', @time AS '@time';  
  
--Result  
--@datetime               @time  
------------------------- -------------  
--1900-01-01 12:10:05.123 12:10:05.1237  
```  
  
Quando la conversione è da **smalldatetime**, ore e minuti vengono copiati. mentre i secondi e i secondi frazionari vengono impostati su 0. Nel codice seguente vengono illustrati i risultati della conversione di un valore `smalldatetime` in un valore `datetime`.  
  
```sql
DECLARE @smalldatetime smalldatetime = '12-01-16 12:32';  
DECLARE @datetime datetime = @smalldatetime;  
  
SELECT @datetime AS '@datetime', @smalldatetime AS '@smalldatetime';  
  
--Result  
--@datetime               @smalldatetime  
------------------------- -----------------------  
--2016-12-01 12:32:00.000 2016-12-01 12:32:00  
```  
  
Quando la conversione è da **DateTimeOffset (n)**, i componenti di data e ora vengono copiati. Il fuso orario viene troncato. Quando la precisione frazionaria di **DateTimeOffset (n)** valore è maggiore di tre cifre, il valore verrà troncato. Nell'esempio seguente vengono illustrati i risultati della conversione di un valore `datetimeoffset(4)` in un valore `datetime`.  
  
```sql
DECLARE @datetimeoffset datetimeoffset(4) = '1968-10-23 12:45:37.1234 +10:0';  
DECLARE @datetime datetime = @datetimeoffset;  
  
SELECT @datetime AS '@datetime', @datetimeoffset AS '@datetimeoffset';  
  
--Result  
--@datetime               @datetimeoffset  
------------------------- ------------------------------  
--1968-10-23 12:45:37.123 1968-10-23 12:45:37.1237 +01:0   
```  
  
Quando la conversione è da **datetime2**, data e ora vengono copiati. Quando la precisione frazionaria di **datetime2** valore è maggiore di tre cifre, il valore verrà troncato. Nell'esempio seguente vengono illustrati i risultati della conversione di un valore `datetime2(4)` in un valore `datetime`.  
  
```sql
DECLARE @datetime2 datetime2(4) = '1968-10-23 12:45:37.1237';  
DECLARE @datetime datetime = @datetime2;  
  
SELECT @datetime AS '@datetime', @datetime2 AS '@datetime2';  
  
--Result  
--@datetime               @datetime2  
------------------------- ------------------------  
--1968-10-23 12:45:37.123 1968-10-23 12:45:37.1237  
```  
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente vengono confrontati i risultati dell'esecuzione del cast di una stringa a ciascun **data** e **ora** tipo di dati.
  
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
|---|---|
|**time**|12:35:29. 1234567|  
|**data**|2007-05-08|  
|**smalldatetime**|2007-05-08 12:35:00|  
|**datetime**|2007-05-08 12:35:29.123|  
|**datetime2**|2007-05-08 12:35:29. 1234567|  
|**datetimeoffset**|2007-05-08 12:35:29.1234567 +12:15|  
  
## <a name="see-also"></a>Vedere anche
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  

