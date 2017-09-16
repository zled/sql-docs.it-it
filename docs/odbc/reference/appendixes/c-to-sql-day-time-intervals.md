---
title: 'C a SQL: gli intervalli di tempo di giorno | Documenti Microsoft'
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- day-time intervals [ODBC]
- data conversions from C to SQL types [ODBC], day-time intervals
- converting data from c to SQL types [ODBC], day-time intervals
- intervals [ODBC], converting
ms.assetid: f9ee1ddb-dec7-4f78-b6e2-5ba34e7d6f59
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 61c271a9de10bbc43db116f576b0c34589f899f3
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="c-to-sql-day-time-intervals"></a>C a SQL: gli intervalli di tempo di giorno
Gli identificatori per i tipi di dati di intervallo di tempo di giorno ODBC C sono:  
  
 SQL_C_INTERVAL_DAY  
  
 SQL_C_INTERVAL_HOUR  
  
 SQL_C_INTERVAL_MINUTE  
  
 SQL_C_INTERVAL_SECOND  
  
 SQL_C_INTERVAL_DAY_TO_HOUR  
  
 SQL_C_INTERVAL_DAY_TO_MINUTE  
  
 SQL_C_INTERVAL_DAY_TO_SECOND  
  
 SQL_C_INTERVAL_HOUR_TO_MINUTE  
  
 SQL_C_INTERVAL_HOUR_TO_SECOND  
  
 SQL_C_INTERVAL_MINUTE_TO_SECOND  
  
 Nella tabella seguente viene illustrato SQL ODBC dei tipi di dati a cui l'intervallo di dati C può essere convertito. Per una spiegazione delle colonne e delle condizioni nella tabella, vedere [la conversione di dati da C a tipi di dati SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Identificatore di tipo SQL|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR, [a]<br /><br /> SQL_VARCHAR, [a]<br /><br /> SQL_LONGVARCHAR [a]|Lunghezza in byte di colonna > = lunghezza in byte di caratteri<br /><br /> Lunghezza in byte colonna < caratteri di lunghezza in byte [a]<br /><br /> Valore di dati non è un intervallo valido di valore letterale|n/d<br /><br /> 22001<br /><br /> 22015|  
|SQL_WCHAR [a]<br /><br /> SQL_WVARCHAR [a]<br /><br /> SQL_WLONGVARCHAR [a]|Lunghezza in caratteri colonna > = lunghezza in caratteri di dati<br /><br /> Lunghezza in caratteri colonna < caratteri di lunghezza dei dati [a]<br /><br /> Valore di dati non è un intervallo valido di valore letterale|n/d<br /><br /> 22001<br /><br /> 22015|  
|SQL_TINYINT [b]<br /><br /> SQL_SMALLINT [b] SQL_INTEGER [b]<br /><br /> SQL_BIGINT [b] SQL_NUMERIC [b]<br /><br /> SQL_DECIMAL [b]|Conversione di un intervallo di un solo campo non ha restituito il troncamento di cifre intere<br /><br /> La conversione ha causato un troncamento di cifre intere|n/d<br /><br /> 22003|  
|SQL_INTERVAL_DAY<br /><br /> SQL_INTERVAL_HOUR<br /><br /> SQL_INTERVAL_MINUTE<br /><br /> SQL_INTERVAL_SECOND<br /><br /> SQL_INTERVAL_DAY_TO_HOUR<br /><br /> SQL_INTERVAL_DAY_TO_MINUTE<br /><br /> SQL_INTERVAL_DAY_TO_SECOND<br /><br /> SQL_INTERVAL_HOUR_TO_MINUTE<br /><br /> SQL_INTERVAL_HOUR_TO_SECOND<br /><br /> SQL_INTERVAL_MINUTE_TO_SECOND|Valore di dati è stato convertito senza troncamento dei campi<br /><br /> Uno o più campi di valore di dati sono stati troncati durante la conversione|n/d<br /><br /> 22015|  
  
 tipi di dati intervallo [a] tutti C possono essere convertito in un tipo di dati carattere.  
  
 [b] se il campo di tipo nella struttura di intervallo è tale che l'intervallo di un singolo campo (SQL_DAY, SQL_HOUR, SQL_MINUTE o SQL_SECOND), l'intervallo di tipo C può essere convertito in qualsiasi numerico esatto (SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT SQL_DECIMAL o SQL_NUMERIC).  
  
 La conversione del valore predefinito di un tipo di intervallo C è l'intervallo di giorni dal tipo SQL corrispondente.  
  
 Il driver ignora il valore di lunghezza/indicatore quando la conversione dei dati dal tipo di dati di intervallo C e si presuppone che le dimensioni del buffer di dati sono la dimensione del tipo di dati di intervallo C. Viene passato il valore di lunghezza/indicatore di *StrLen_or_Ind* argomento **SQLPutData** e nel buffer specificato con il *StrLen_or_IndPtr* argomento **SQLBindParameter**. Il buffer dei dati è specificato con il *DataPtr* argomento in **SQLPutData** e *ParameterValuePtr* argomento **SQLBindParameter**.  
  
 Nell'esempio seguente viene illustrato come inviare dati di intervallo C archiviati nella struttura SQL_INTERVAL_STRUCT in una colonna di database. La struttura di intervallo contiene un intervallo di DAY_TO_SECOND. verrà archiviata in una colonna di database di tipo SQL_INTERVAL_DAY_TO_MINUTE.  
  
```  
SQL_INTERVAL_STRUCT is;  
SQLINTEGER cbValue;  
  
// Initialize the interval struct to contain the DAY_TO_SECOND  
// interval "154 days, 22 hours, 44 minutes, and 10 seconds"  
is.intval.day_second.day      = 154;  
is.intval.day_second.hour     = 22;  
is.intval.day_second.minute   = 44;  
is.intval.day_second.second   = 10;  
is.interval_sign              = SQL_FALSE;  
  
// Bind the dynamic parameter  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_INTERVAL_DAY_TO_SECOND,  
                  SQL_INTERVAL_DAY_TO_MINUTE, 0, 0, &is,  
                  sizeof(SQL_INTERVAL_STRUCT), &cbValue);  
  
// Execute an insert statement; "interval_column" is a column  
// whose data type is SQL_INTERVAL_DAY_TO_MINUTE.  
SQLExecDirect(hstmt,"INSERT INTO table(interval_column) VALUES (?)",SQL_NTS);  
```
