---
title: Regole di conversione per dwloader del tipo di dati
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: 
ms.technology: mpp-data-warehouse
description: Questo argomento descrive i formati di dati di input e le conversioni implicite dei dati che dwloader che caricatore della riga di comando supporta quando carica i dati in PDW.
ms.date: 10/20/2016
ms.topic: article
ms.assetid: 79c48520-b08b-4b15-a943-a551cc90a2c4
caps.latest.revision: "30"
ms.openlocfilehash: 29cf43b7bb5ea38d821e62b03cc125fe5e0fc30c
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="data-type-conversion-rules-for-dwloader"></a>Regole di conversione per dwloader del tipo di dati
Questo argomento descrive i formati di dati di input e le conversioni implicite dei dati che [dwloader caricatore della riga di comando](dwloader.md) supporta al momento del caricamento dei dati in PDW. Le conversioni implicite dei dati si verificano quando i dati di input non corrisponde al tipo di dati nella tabella di destinazione di SQL Server PDW. Utilizzare queste informazioni quando il processo di caricamento per garantire che i dati di progettazione verrà caricato correttamente in SQL Server PDW.  
   
  
## <a name="InsertBinaryTypes"></a>Inserimento di valori letterali in tipi binari  
Nella tabella seguente definisce i tipi letterali accettati, formato e le regole di conversione per il caricamento di un valore letterale in una colonna di SQL Server PDW di tipo **binario** (*n*) o  **varbinary**(*n*).  
  
|Tipo di dati di input|Esempi di dati di input|Conversione in binary o varbinary tipo di dati|  
|-------------------|-----------------------|-----------------------------------------------|  
|Valore letterale binario|[0x] *hexidecimal_string*<br /><br />Esempio: 12Ef o 0x12Ef|Il prefisso 0x è facoltativo.<br /><br />La lunghezza di origine dati non può superare il numero di byte specificati per il tipo di dati.<br /><br />Se la lunghezza di origine dati è minore di dimensioni di **binario** del tipo di dati, i dati vengano applicato un riempimento a destra con zeri per raggiungere le dimensioni di tipo di dati.|  
  
## <a name="InsertDateTimeTypes"></a>Inserimento di valori letterali in tipi data e ora  
Valori letterali di data e ora vengono rappresentati tramite valori letterali stringa in formati specifici, racchiusi tra virgolette singole. Nelle tabelle seguenti definiscono i tipi di valore letterale consentiti, formato e le regole di conversione per il caricamento di una data o ora letterale in una colonna di tipo **datetime**, **smalldatetime**, **data**, **ora**, **datetimeoffset**, o **datetime2**. Le tabelle di definiscono il formato predefinito per il tipo di dati specificato. Altri formati che è possibile specificare sono definiti nella sezione [formati Datetime](#DateFormats). Valori letterali di data e ora non possono includere spazi iniziali o finali. **Data**, **smalldatetime**, e i valori null possono essere caricati in modalità a larghezza fissa.  
  
### <a name="datetime-data-type"></a>Tipi di dati datetime  
Nella tabella seguente definisce il formato predefinito e le regole per il caricamento di valori letterali in una colonna di tipo **datetime**. Una stringa vuota (") viene convertita il valore predefinito ' 12:00:00.000 1900-01-01'. Le stringhe che contengono solo spazi vuoti (' ') genera un errore.  
  
|Tipo di dati di input|Esempi di dati di input|Conversione di tipi di dati datetime|  
|-------------------|-----------------------|------------------------------------|  
|Valore letterale stringa nel **datetime** formato|'aaaa-MM-gg hh.mm.ss [. fff]'<br /><br />Esempio: ' 2007-05-08 12:35:29.123'|Cifre frazionarie mancante vengono impostate su 0 quando viene inserito il valore. Ad esempio, il valore letterale ' 2007-05-08 12:35 ' viene inserito come ' 2007-05-08 12:35:00.000'.|  
|Valore letterale stringa nel **smalldatetime** formato|"aaaa-MM-gg hh: mm"<br /><br />Esempio: ' 2007-05-08:35 12'|Quando il valore viene inserito, secondi e cifre frazionarie rimanenti vengono impostate su 0.|  
|Valore letterale stringa nel **data** formato|"yyyy-MM-dd"<br /><br />Esempio: ' 2007-05-08'|Valori di ora (ora, minuti, secondi e frazioni) sono impostati su 12:00:00.000 quando viene inserito il valore.|  
|Valore letterale stringa nel **datetime2** formato|"aaaa-MM-GG fffffff"<br /><br />Esempio: ' 2007-05-08 12:35:29.1234567'|I dati di origine non possono superare tre cifre frazionarie. Ad esempio, il valore letterale ' 2007-05-08 12:35:29.123' verrà inserito, ma il valore ' 2007-05-8 12:35:29.1234567' genera un errore.|  
  
### <a name="smalldatetime-data-type"></a>Tipo di dati smalldatetime  
Nella tabella seguente definisce il formato predefinito e le regole per il caricamento di valori letterali in una colonna di tipo **smalldatetime**. Una stringa vuota (") viene convertita il valore predefinito ' 1900-01-01 12:00". Le stringhe che contengono solo spazi vuoti (' ') genera un errore.  
  
|Tipo di dati di input|Esempi di dati di input|Conversione in tipo di dati smalldatetime|  
|-------------------|-----------------------|-----------------------------------------|  
|Valore letterale stringa nel **smalldatetime** formato|'aaaa-MM-gg hh: mm' o 'aaaa-MM-gg hh'<br /><br />Esempio: ' 2007-05-08 12:00 ' o ' 2007-05-08 12:00:15 '|I dati di origine devono contenere valori per anno, mese, data, ora e minuto. Secondi sono facoltativi e, se presente, devono essere impostati sul valore 00. Qualsiasi altro valore genera un errore.<br /><br />I secondi sono facoltativi. Durante il caricamento in una colonna di tipo smalldatetime, dwloader Arrotonda secondi e frazioni di secondo. Ad esempio, 1999-05-01 20:10:35.123 caricherà come 20:05-01 11.|  
|Valore letterale stringa nel **data** formato|"yyyy-MM-dd"<br /><br />Esempio: ' 2007-05-08'|I valori di ora (ora, minuti, secondi e frazioni) vengono impostati su 0 quando viene inserito il valore.|  
  
### <a name="date-data-type"></a>Tipo di dati date  
Nella tabella seguente definisce il formato predefinito e le regole per il caricamento di valori letterali in una colonna di tipo **data**. Una stringa vuota (") viene convertita il valore predefinito ' 1900-01-01'. Le stringhe che contengono solo spazi vuoti (' ') genera un errore.  
  
|Tipo di dati di input|Esempi di dati di input|Conversione a tipo di dati date|  
|-------------------|-----------------------|--------------------------------|  
|Valore letterale stringa nel **data** formato|"yyyy-MM-dd"<br /><br />Esempio: ' 2007-05-08'||  
  
### <a name="time-data-type"></a>Tipo di dati ora  
Nella tabella seguente definisce il formato predefinito e le regole per il caricamento di valori letterali in una colonna di tipo **tempo**. Una stringa vuota (") viene convertita il valore predefinito '00:00:00.0000'. Le stringhe che contengono solo spazi vuoti (' ') genera un errore.  
  
|Tipo di dati di input|Esempi di dati di input|Conversione in tipo di dati ora|  
|-------------------|-----------------------|--------------------------------|  
|Valore letterale stringa nel **ora** formato|"fffffff"<br /><br />Esempio: '12:35:29.1234567'|Se l'origine dati ha una precisione di minore o uguale (numero di cifre frazionarie) quella di **ora** del tipo di dati, i dati vengano applicato un riempimento a destra con zeri. Ad esempio, viene inserito un valore letterale '12:35:29.123' come '12:35:29.1230000'.|  
  
### <a name="datetimeoffset-data-type"></a>Tipo di dati DateTimeOffset  
Nella tabella seguente definisce il formato predefinito e le regole per il caricamento di valori letterali in una colonna di tipo **datetimeoffset** (*n*). Il formato predefinito è "yyyy-MM-GG fffffff {+ |-} hh: mm". Una stringa vuota (") viene convertita il valore predefinito ' 1900-01-01 12:00:00.0000000 + 00:00". Le stringhe che contengono solo spazi vuoti (' ') genera un errore. Il numero di cifre frazionarie dipende dalla definizione della colonna. Ad esempio, una colonna definita come **datetimeoffset** (2) avranno due cifre frazionarie.  
  
|Tipo di dati di input|Esempi di dati di input|Conversione in tipo di dati datetimeoffset|  
|-------------------|-----------------------|------------------------------------------|  
|Valore letterale stringa nel **datetime** formato|'aaaa-MM-gg hh.mm.ss [. fff]'<br /><br />Esempio: ' 2007-05-08 12:35:29.123'|Cifre frazionarie mancante e valori di offset sono impostati su 0 quando viene inserito il valore. Ad esempio, il valore letterale ' 2007-05-08 12:35:29.123' viene inserito come ' 2007-05-08 12:35:29.1230000 + 00:00 ".|  
|Valore letterale stringa nel **smalldatetime** formato|"aaaa-MM-gg hh: mm"<br /><br />Esempio: ' 2007-05-08:35 12'|Secondi, le cifre frazionarie rimanenti e i valori di offset vengono impostati su 0 quando viene inserito il valore.|  
|Valore letterale stringa nel **data** formato|"yyyy-MM-dd"<br /><br />Esempio: ' 2007-05-08'|I valori di ora (ora, minuti, secondi e frazioni) vengono impostati su 0 quando viene inserito il valore. Ad esempio, il valore letterale ' 2007-05-08' viene inserito come ' 2007-05-08 00.00.00.0000000 + 00:00 ".|  
|Valore letterale stringa nel **datetime2** formato|"aaaa-MM-GG fffffff"<br /><br />Esempio: ' 2007-05-08 12:35:29.1234567'|I dati di origine non possono superare il numero specificato di secondi frazionari nella colonna datetimeoffset. Se l'origine dati contiene un numero minore o uguale dei secondi frazionari, i dati verranno aggiunti a destra con zeri. Ad esempio, se il tipo di dati datetimeoffset (5), il valore letterale ' 2007-05-08 12:35:29.123 + 12:15 ' viene inserito come ' 12:35:29.12300 + 12:15 '.|  
|Valore letterale stringa nel **datetimeoffset** formato|"aaaa-MM-GG fffffff {+ &#124;;-} hh: mm"<br /><br />Esempio: ' 2007-05-08 12:35:29.1234567 + 12:15 '|I dati di origine non possono superare il numero specificato di secondi frazionari nella colonna datetimeoffset. Se l'origine dati contiene un numero minore o uguale dei secondi frazionari, i dati verranno aggiunti a destra con zeri. Ad esempio, se il tipo di dati datetimeoffset (5), il valore letterale ' 2007-05-08 12:35:29.123 + 12:15 ' viene inserito come ' 12:35:29.12300 + 12:15 '.|  
  
### <a name="datetime2-data-type"></a>Tipi di dati datetime2  
Nella tabella seguente definisce il formato predefinito e le regole per il caricamento di valori letterali in una colonna di tipo **datetime2** (*n*). Il formato predefinito è 'yyyy-MM-GG fffffff'. Una stringa vuota (") viene convertita il valore predefinito ' 1900-01-01-12:00:00". Le stringhe che contengono solo spazi vuoti (' ') genera un errore. Il numero di cifre frazionarie dipende dalla definizione della colonna. Ad esempio, una colonna definita come **datetime2** (2) avranno due cifre frazionarie.  
  
|Tipo di dati di input|Esempi di dati di input|Conversione al tipo di dati datetime2|  
|-------------------|-----------------------|-------------------------------------|  
|Valore letterale stringa nel **datetime** formato|'aaaa-MM-gg hh.mm.ss [. fff]'<br /><br />Esempio: ' 2007-05-08 12:35:29.123'|I secondi frazionari sono facoltativi e vengono impostati su 0 quando viene inserito il valore.|  
|Valore letterale stringa nel **smalldatetime** formato|"aaaa-MM-gg hh: mm"<br /><br />Esempio: ' 2007-05-08 12'|Secondi facoltativi e cifre frazionarie rimanenti vengono impostate su 0 quando viene inserito il valore.|  
|Valore letterale stringa nel **data** formato|"yyyy-MM-dd"<br /><br />Esempio: ' 2007-05-08'|I valori di ora (ora, minuti, secondi e frazioni) vengono impostati su 0 quando viene inserito il valore. Ad esempio, il valore letterale ' 2007-05-08' viene inserito come ' 2007-05-08 12:00:00.0000000'.|  
|Valore letterale stringa nel **datetime2** formato|'aaaa-MM-gg hh:mm:ss:fffffff'<br /><br />Esempio: ' 2007-05-08 12:35:29.1234567'|Se l'origine dati contiene i componenti di data e ora sono minore o uguale al valore specificato **datetime2**(*n*), i dati vengono inseriti; in caso contrario viene generato un errore.|  
  
### <a name="DateFormats"></a>Formati di data/ora  
Dwloader supporta i seguenti formati di dati per i dati di input che sta caricando in SQL Server PDW. Ulteriori dettagli sono elencati sotto la tabella.  
  
|DATETIME|smalldatetime|Data|datetime2|datetimeoffset|  
|------------|-----------------|--------|-------------|------------------|  
|[M [M]] M-[d] d-[Aa] aa hh.mm.ss [. fff]|[M [M]] M-[d] d-[Aa] aa hh: mm [: 00]|[M [M]] M-[d] d-[Aa] AA|[M [M]] M-[d] d-[Aa] aa hh.mm.ss [. fffffff]|[M [M]] M-[d] d-[Aa] aa hh.mm.ss [. fffffff] zzz|  
|[M [M]] M-[d] d-[Aa] aa hh.mm.ss [. fff] [Aa]|[M [M]] M-[d] d-[Aa] aa hh: mm [: 00] [Aa]||[M [M]] M-[d] d-[Aa] aa hh.mm.ss [. fffffff] [Aa]|[M [M]] M-[d] d-[Aa] aa hh.mm.ss [. fffffff] [Aa] zzz|  
|[M [M]] M-[Aa] AA-[d] d hh.mm.ss [. fff]|[M [M]] M-[Aa] AA-[d] d hh: mm [: 00]|[M [M]] M-[Aa] AA-[d] d|[M [M]] M-[Aa] AA-[d] d hh.mm.ss [. fffffff]|[M [M]] M-[Aa] AA-[d] d zzz hh.mm.ss [. fffffff]|  
|[M [M]] M-[Aa] AA-[d] d hh.mm.ss [. fff] [Aa]|[M [M]] M-[Aa] AA-[d] d hh: mm [: 00] [Aa]||[M [M]] M-[Aa] AA-[d] d hh.mm.ss [. fffffff] [Aa]|[M [M]] M-[Aa] AA-[d] [. fffffff] [Aa] hh: mm: d zzz|  
|[Aa] AA-[[M] M] M-[d] d hh.mm.ss [. fff]|[Aa] AA-[[M] M] M-[d] d hh: mm [: 00]|[Aa] AA-[[M] M] M-[d] d|[Aa] AA-[[M] M] M-[d] d hh.mm.ss [. fffffff]|[Aa] AA-[[M] M] M-[d] [. fffffff] hh: mm: d zzz|  
|[Aa] AA-[[M] M] M-[d] d hh.mm.ss [. fff] [Aa]|[Aa] AA-[[M] M] M-[d] d hh: mm [: 00] [Aa]||[Aa] AA-[[M] M] M-[d] d hh.mm.ss [. fffffff] [Aa]|[Aa] AA-[[M] M] M-[d] d hh.mm.ss [. fffffff] [Aa] zzz|  
|[Aa] AA-[d] d-[[M] M] M hh.mm.ss [. fff]|[Aa] AA-[d] d-[[M] M] M hh: mm [: 00]|[Aa] AA - d [d]-[[M] M] M|[Aa] AA-[d] d-[[M] M] M hh.mm.ss [. fffffff]|[Aa] AA-[d] d-[[M] M] M hh.mm.ss [. fffffff] zzz|  
|[Aa] AA-[d] d-[[M] M] M hh.mm.ss [. fff] [Aa]|[Aa] AA-[d] d-[[M] M] M hh: mm [: 00] [Aa]||[Aa] AA-[d] d-[[M] M] M hh.mm.ss [. fffffff] [Aa]|[Aa] AA-[d] d-[[M] M] M hh.mm.ss [. fffffff] [Aa] zzz|  
|[d] d-[[M] M] M-[Aa] aa hh.mm.ss [. fff]|[d] d-[[M] M] M-[Aa] aa hh: mm [: 00]|[d] d-[[M] M] M-[Aa] AA|[d] d-[[M] M] M-[Aa] aa hh.mm.ss [. fffffff]|[d] d-[[M] M] M-[Aa] aa hh.mm.ss [. fffffff] zzz|  
|[d] d-[[M] M] M-[Aa] aa hh.mm.ss [. fff] [Aa]|[d] d-[[M] M] M-[Aa] aa hh: mm [: 00] [Aa]||[d] d-[[M] M] M-[Aa] aa hh.mm.ss [. fffffff] [Aa]|[d] d-[[M] M] M-[Aa] aa hh.mm.ss [. fffffff] [Aa] zzz|  
|d [d]-[Aa] AA-[[M] M] M hh.mm.ss [. fff]|d [d]-[Aa] AA-[[M] M] M hh: mm [: 00]|d [d]-[Aa] AA-[[M] M] M|d [d]-[Aa] AA-[[M] M] M hh.mm.ss [. fffffff]|[d] d-[Aa] AA-[[M] M] M hh.mm.ss [. fffffff] zzz|  
|[d] d-[Aa] AA-[[M] M] M hh.mm.ss [. fff] [Aa]|[d] d-[Aa] AA-[[M] M] M hh: mm [: 00] [Aa]||[d] d-[Aa] AA-[[M] M] M hh.mm.ss [. fffffff] [Aa]|[d] d-[Aa] AA-[[M] M] M hh.mm.ss [. fffffff] [Aa] zzz|  
  
Dettagli:  
  
-   Per separare i valori di mese, giorno e anno, è possibile utilizzare '-', '/' o '. '. Per semplicità, la tabella utilizza solo il separatore ':'.  
  
-   Per specificare il mese come testo utilizzare tre o più caratteri. Verranno interpretati come un numero di mesi con caratteri di 1 o 2.  
  
-   Per separare i valori di ora, utilizzare i ': ' simbolo.  
  
-   Lettere racchiuso tra parentesi quadre sono facoltative.  
  
-   Designare le lettere "tt" [AM | PM | am | pm]. AM è l'impostazione predefinita. Se si specifica "tt", il valore dell'ora (hh) deve essere compreso nell'intervallo da 0 a 12.  
  
-   Le lettere 'zzz' designare l'offset del fuso orario per fuso orario corrente del sistema nel formato {+ |-} HH:ss].  
  
## <a name="InsertNumerictypes"></a>Inserimento di valori letterali in tipi numerici  
Nelle tabelle seguenti definiscono le regole di conversione e formato predefinito per il caricamento di un valore letterale in una colonna di SQL Server PDW che utilizza un tipo numerico.  
  
### <a name="bit-data-type"></a>Tipo di dati bit  
Nella tabella seguente definisce il formato predefinito e le regole per il caricamento di valori letterali in una colonna di tipo **bit**. Una stringa vuota (") o una stringa che contiene solo spazi vuoti (' ') viene convertito in 0.  
  
|Tipo di dati di input|Esempi di dati di input|Conversione in tipo di dati bit|  
|-------------------|-----------------------|-------------------------------|  
|Valore letterale stringa nel **intero** formato|'ffffffffff'<br /><br />Esempio: '1' o '321'|Un valore integer formattato come valore letterale stringa non può contenere un valore negativo. Ad esempio, il valore '-123' genera un errore.<br /><br />Un valore maggiore di 1 viene convertito in 1. Ad esempio, il valore "123" viene convertito in 1.|  
|Valore letterale stringa|'TRUE' o 'FALSE'<br /><br />Esempio: 'true'|Il valore 'TRUE' viene convertito in 1. il valore 'FALSE' viene convertita in 0.|  
|Valore letterale integer|fffffffn<br /><br />Esempio: 1 o 321|Un valore maggiore di 1 o minore di 0 viene convertito in 1. Ad esempio, i valori 123 e -123 sono convertiti in 1.|  
|Valore letterale decimale|fffnn.fffn<br /><br />Esempio: 1234.5678|Un valore maggiore di 1 o minore di 0 viene convertito in 1. Ad esempio, i valori 123,45 e -123.45 sono convertiti in 1.|  
  
### <a name="decimal-data-type"></a>Tipo di dati Decimal  
Nella tabella seguente definisce le regole per il caricamento di valori letterali in una colonna di tipo **decimale** (*p, s*). Regole di conversione di dati sono uguali a quelli di SQL Server. Per ulteriori informazioni, vedere [la conversione di tipi di dati (motore di Database)](http://go.microsoft.com/fwlink/?LinkId=202128) su MSDN.  
  
|Tipo di dati di input|Esempi di dati di input|  
|-------------------|-----------------------|  
|Valore letterale integer|321312313123|  
|Valore letterale decimale|123344.34455|  
  
### <a name="float-and-real-data-types"></a>Tipi di dati float e real  
Nella tabella seguente definisce le regole per il caricamento di valori letterali in una colonna di tipo **float** o **reale**. Regole di conversione di dati sono uguali a quelli di SQL Server. Per ulteriori informazioni, vedere [la conversione di tipi di dati (motore di Database)](../t-sql/data-types/data-type-conversion-database-engine.md) su MSDN.  
  
|Tipo di dati di input|Esempi di dati di input|  
|-------------------|-----------------------|  
|Valore letterale integer|321312313123|  
|Valore letterale decimale|123344.34455|  
|Valore letterale punto a virgola mobile|3.12323E + 14|  
  
### <a name="int-bigint-tinyint-smallint-data-types"></a>int, bigint, tinyint, smallint i tipi di dati  
Nella tabella seguente definisce le regole per il caricamento di valori letterali in una colonna di tipo **int**, **bigint**, **tinyint**, o **smallint**. L'origine dati non può superare l'intervallo consentito per il tipo di dati specificato. Ad esempio, l'intervallo per **tinyint** è 0 e 255 e l'intervallo per **int** è compreso tra -2.147.483.648 e 2.147.483.647.  
  
|Tipo di dati di input|Esempi di dati di input|Conversione di tipi di dati Integer|  
|-------------------|-----------------------|------------------------------------|  
|Valore letterale integer|321312313123||  
|Valore letterale decimale|123344.34455|I valori a destra del separatore decimale vengono troncati.|  
  
### <a name="money-and-smallmoney-data-types"></a>Tipi di dati Money e smallmoney  
Valori letterali Money vengono rappresentati sotto forma di stringa di numeri con separatore decimale facoltativo e un simbolo di valuta facoltativo come prefisso. L'origine dati non può superare l'intervallo consentito per il tipo di dati specificato. Ad esempio, l'intervallo per **smallmoney** è -214.748,3648 a 214.748,3647 e l'intervallo per **money** è -922.337.203.685.477,5808 e 922.337.203.685.477,5807. Nella tabella seguente definisce le regole per il caricamento di valori letterali in una colonna di tipo **money** o **smallmoney**.  
  
|Tipo di dati di input|Esempi di dati di input|Conversione di denaro o tipo di dati smallmoney|  
|-------------------|-----------------------|-----------------------------------------------|  
|Valore letterale integer|321312|Cifre mancano dopo il separatore decimale vengono impostato su 0 quando viene inserito il valore. Ad esempio, il valore letterale 12345 viene inserito come 12345.0000|  
|Valore letterale decimale|123344.34455|Se il numero di cifre dopo il separatore decimale superare 4, il valore viene arrotondato per eccesso al valore più vicino. Ad esempio, il valore 123344.34455 viene inserito come 123344.3446.|  
|Valore letterale Money|$123456.7890|Il simbolo di valuta non viene inserito con il valore.<br /><br />Se il numero di cifre dopo il separatore decimale superare 4, il valore viene arrotondato per eccesso al valore più vicino.|  
  
## <a name="InsertStringTypes"></a>Inserimento di valori letterali in tipi di stringa  
Nelle tabelle seguenti definiscono le regole di conversione e formato predefinito per il caricamento di un valore letterale in una colonna di SQL Server PDW che utilizza un tipo stringa.  
  
### <a name="char-varchar-nchar-and-nvarchar-data-types"></a>Tipi di dati char, varchar, nchar e nvarchar  
Nella tabella seguente definisce il formato predefinito e le regole per il caricamento di valori letterali in una colonna di tipo **char**, **varchar**, **nchar** e **nvarchar** . La lunghezza di origine dati non può superare le dimensioni specificate per il tipo di dati. Se la lunghezza di origine dati è minore di dimensioni di **char** o **nchar** del tipo di dati, i dati vengano applicato un riempimento a destra con spazi vuoti per raggiungere le dimensioni di tipo di dati.  
  
|Tipo di dati di input|Esempi di dati di input|Conversione di tipi di dati carattere|  
|---------------|-------------------|----------------------------------|  
|Valore letterale stringa|Formato: "stringa di caratteri'<br /><br />Esempio: 'abc'| ND |  
|Valore letterale stringa Unicode|Formato: Stringa N'character'<br /><br />Esempio: N'abc '| ND |  
|Valore letterale integer|Formato: ffffffffffn<br /><br />Esempio: 321312313123| ND |  
|Valore letterale decimale|Formato: ffffff.fffffff<br /><br />Esempio: 12344.34455| ND |  
|Valore letterale Money|Formato: $ffffff.fffnn<br /><br />Esempio: $123456.99|Il simbolo di valuta facoltativo non viene inserito con il valore. Per inserire il simbolo di valuta, inserire il valore come valore letterale stringa. Verrà trovata corrispondenza il formato del caricatore, considera ogni valore letterale come un valore letterale stringa.<br /><br />Virgola non è consentita.<br /><br />Se il numero di cifre dopo il separatore decimale sono superiori a 2, il valore viene arrotondato per eccesso al valore più vicino. Ad esempio, il valore 123.946789 viene inserito come 123.95.<br /><br />Quando si utilizza la funzione CONVERT per inserire valori letterali money, è consentito solo lo stile predefinito 0 (Nessun separatore delle migliaia e 2 cifre dopo il separatore decimale).|  
  
### <a name="general-remarks"></a>Osservazioni generali  
**dwloader** esegue le stesse conversioni implicite che SMP SQL Server vengono eseguite, ma non supporta tutte le conversioni implicite che supporta SMP SQL Server.  
 
<!-- MISSING LINKS 
## See Also  
[Grant Permissions to Load Data &#40;SQL Server PDW&#41;](../sqlpdw/grant-permissions-to-load-data-sql-server-pdw.md)  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  

-->
  
