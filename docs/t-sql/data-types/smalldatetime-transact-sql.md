---
title: smalldatetime (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- smalldatetime_TSQL
- smalldatetime
dev_langs:
- TSQL
helpviewer_keywords:
- time [SQL Server], data types
- smalldatetime data type [SQL Server]
- dates [SQL Server], data types
- date and time [SQL Server], smalldatetime
- data types [SQL Server], date and time
ms.assetid: 68b74610-d54c-4c8e-b4b2-7e3747546ee0
caps.latest.revision: 50
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 07012d85a54292fa763a7b291d1b7318b6969ca4
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="smalldatetime-transact-sql"></a>smalldatetime (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Definisce una data combinata con un'ora del giorno. L'ora si basa su un formato di 24 ore, con secondi sempre a zero (: 00) e senza secondi frazionari.
  
> [!NOTE]  
>  Utilizzare il **ora**, **data**, **datetime2** e **datetimeoffset** tipi di dati per un nuovo lavoro. Questi tipi sono conformi allo standard SQL. e offrono una migliore portabilità. **tempo**, **datetime2** e **datetimeoffset** offrono una maggiore precisione dei secondi. **DateTimeOffset** fornisce supporto del fuso orario per le applicazioni distribuite globalmente.  
  
## <a name="smalldatetime-description"></a>descrizione di smalldatetime
  
|||  
|-|-|  
|Sintassi|**smalldatetime**|  
|Utilizzo|DICHIARARE @MySmalldatetime **smalldatetime**<br /><br /> Crea tabella Table1 (Column1 **smalldatetime** )|  
|Formati predefiniti dei valori letterali stringa<br /><br /> (utilizzato per client legacy)|Non applicabile|  
|Intervallo di date|da 01-01-1900 a 06-06-2079<br /><br /> Da 1 gennaio 1900 a 6 giugno 2079|  
|Intervallo di ore|Da 00:00:00 a 23:59:59<br /><br /> 2007-05-09 23:59:59 verrà arrotondato a<br /><br /> 2007-05-10 00:00:00|  
|Intervalli di elementi|AAAA rappresenta un numero di quattro cifre, compreso tra 1900 e 2079, indicante l'anno.<br /><br /> MM rappresenta un numero di due cifre compreso tra 01 e 12 indicante un mese dell'anno specificato.<br /><br /> GG rappresenta un numero di due cifre compreso tra 01 e 31, a seconda del mese, indicante il giorno del mese specificato.<br /><br /> hh rappresenta un numero di due cifre compreso tra 00 e 23 indicante l'ora.<br /><br /> mm rappresenta un numero di due cifre compreso tra 00 e 59 indicante i minuti.<br /><br /> ss rappresenta un numero di due cifre compreso tra 00 e 59 indicante i secondi. I valori minori o uguali a 29,998 secondi vengono arrotondati al minuto per difetto. I valori maggiori o uguali a 29,999 secondi vengono arrotondati al minuto per eccesso.|  
|Lunghezza in caratteri|Massimo 19 posizioni|  
|Dimensioni dello spazio di archiviazione|4 byte, fissa.|  
|Accuratezza|Un minuto|  
|Valore predefinito|1900-01-01 00:00:00|  
|Calendario|Gregoriano<br /><br /> Non è incluso l'intervallo completo di anni.|  
|Precisione in secondi frazionari definita dall'utente|No|  
|Considerazione e conservazione delle differenze di fuso orario|No|  
|Considerazione dell'ora legale|No|  
  
## <a name="ansi-and-iso-8601-compliance"></a>Conformità agli standard ANSI e ISO 8601  
**smalldatetime** non ANSI o ISO 8601 conforme.
  
## <a name="converting-date-and-time-data"></a>La conversione dei dati di data e ora
Nella conversione di tipi di dati relativi alla data e all'ora, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono rifiutati tutti i valori non riconosciuti come date o orari. Per informazioni sull'utilizzo delle funzioni CAST e CONVERT con dati di data e ora, vedere [CAST e CONVERT &#40; Transact-SQL &#41; ](../../t-sql/functions/cast-and-convert-transact-sql.md).
  
### <a name="converting-smalldatetime-to-other-date-and-time-types"></a>Conversione smalldatetime in altri tipi di data e ora
In questa sezione viene descritto cosa accade quando un **smalldatetime** tipo di dati viene convertito in altri tipi di dati data e ora.
  
Nel caso di conversione **data**, l'anno, mese e giorno vengono copiati. Nel codice seguente vengono illustrati i risultati della conversione di un valore `smalldatetime` in un valore `date`.
  
```sql
DECLARE @smalldatetime smalldatetime = '1955-12-13 12:43:10';  
DECLARE @date date = @smalldatetime  
  
SELECT @smalldatetime AS '@smalldatetime', @date AS 'date';  
  
--Result  
--@smalldatetime          date  
------------------------- ----------  
--1955-12-13 12:43:00     1955-12-13  
--  
--(1 row(s) affected)  
```  
  
Quando la conversione viene eseguita a **Time (n)**, le ore, minuti e secondi vengono copiati. I secondi frazionari sono impostati su 0. Nel codice seguente vengono illustrati i risultati della conversione di un valore `smalldatetime` in un valore `time(4)`.
  
```sql
DECLARE @smalldatetime smalldatetime = '1955-12-13 12:43:10';  
DECLARE @time time(4) = @smalldatetime;  
  
SELECT @smalldatetime AS '@smalldatetime', @time AS 'time';  
  
--Result  
--@smalldatetime          time  
------------------------- -------------  
--1955-12-13 12:43:00     12:43:00.0000  
--  
--(1 row(s) affected)  
```  
  
Quando la conversione viene eseguita a **datetime**, **smalldatetime** valore viene copiato il **datetime** valore. I secondi frazionari sono impostati su 0. Nel codice seguente vengono illustrati i risultati della conversione di un valore `smalldatetime` in un valore `datetime`.
  
```sql
DECLARE @smalldatetime smalldatetime = '1955-12-13 12:43:10';  
DECLARE @datetime datetime = @smalldatetime;  
  
SELECT @smalldatetime AS '@smalldatetime', @datetime AS 'datetime';  
  
--Result  
--@smalldatetime          datetime  
------------------------- -----------------------  
--1955-12-13 12:43:00     1955-12-13 12:43:00.000  
--  
--(1 row(s) affected)  
```  
  
Nel caso di conversione **DateTimeOffset (n)**, **smalldatetime** valore viene copiato il **DateTimeOffset (n)** valore. I secondi frazionari vengono impostati su 0, mentre la differenza di fuso orario viene impostata su +00:0. Nel codice seguente vengono illustrati i risultati della conversione di un valore `smalldatetime` in un valore `datetimeoffset(4)`.
  
```sql
DECLARE @smalldatetime smalldatetime = '1955-12-13 12:43:10';  
DECLARE @datetimeoffset datetimeoffset(4) = @smalldatetime;  
  
SELECT @smalldatetime AS '@smalldatetime', @datetimeoffset AS 'datetimeoffset(4)';  
  
--Result  
--@smalldatetime          datetimeoffset(4)  
------------------------- ------------------------------  
--1955-12-13 12:43:00     1955-12-13 12:43:00.0000 +00:0  
--  
--(1 row(s) affected)  
```  
  
Per la conversione a **datetime2**, **smalldatetime** valore viene copiato il **datetime2** valore. I secondi frazionari sono impostati su 0. Nel codice seguente vengono illustrati i risultati della conversione di un valore `smalldatetime` in un valore `datetime2(4)`.
  
```sql
DECLARE @smalldatetime smalldatetime = '1955-12-13 12:43:10';  
DECLARE @datetime2 datetime2(4) = @smalldatetime;  
  
SELECT @smalldatetime AS '@smalldatetime', @datetime2 AS ' datetime2(4)';  
  
--Result  
--@smalldatetime           datetime2(4)  
------------------------- ------------------------  
--1955-12-13 12:43:00     1955-12-13 12:43:00.0000  
--  
--(1 row(s) affected)  
```  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-casting-string-literals-with-seconds-to-smalldatetime"></a>A. Cast di valori letterali stringa con secondi a smalldatetime  
Nell'esempio seguente viene confrontata la conversione dei secondi nei valori letterali stringa in `smalldatetime`.
  
```sql
SELECT   
     CAST('2007-05-08 12:35:29'     AS smalldatetime)  
    ,CAST('2007-05-08 12:35:30'     AS smalldatetime)  
    ,CAST('2007-05-08 12:59:59.998' AS smalldatetime);  
```  
  
|Input|Output|  
|---|---|
|2007-05-08 12:35:29|2007-05-08 12:35:00|  
|2007-05-08 12:35:30|2007-05-08 12:36:00|  
|2007-05-08 12:59:59.998|2007-05-08 13:00:00|  
  
### <a name="b-comparing-date-and-time-data-types"></a>B. Confronto dei tipi di dati di data e ora  
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
  
  

