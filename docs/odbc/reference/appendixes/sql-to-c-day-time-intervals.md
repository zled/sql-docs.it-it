---
title: 'SQL a intervalli di giorno-Time c: | Documenti Microsoft'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- converting data from SQL to C types [ODBC], day-time intervals
- day-time intervals [ODBC]
- data conversions from SQL to C types [ODBC], day-time intervals
- intervals [ODBC], converting
ms.assetid: 8ea84d69-2292-4128-89a0-f184f68abb98
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9df3ee4fdd01d5296e547bb445f3e4e47cee3561
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sql-to-c-day-time-intervals"></a>SQL a intervalli di giorno-Time c:
Gli identificatori per i tipi di dati SQL ODBC intervallo di tempo di giorno sono:  
  
 SQL_INTERVAL_DAY  
  
 SQL_INTERVAL_DAY_TO_MINUTE  
  
 SQL_INTERVAL_HOUR  
  
 SQL_INTERVAL_DAY_TO_SECOND  
  
 SQL_INTERVAL_MINUTE  
  
 SQL_INTERVAL_HOUR_TO_MINUTE  
  
 SQL_INTERVAL_SECOND  
  
 SQL_INTERVAL_HOUR_TO_SECOND  
  
 SQL_INTERVAL_DAY_TO_HOUR  
  
 SQL_INTERVAL_MINUTE_TO_SECOND  
  
 Nella tabella seguente viene illustrato come ODBC C i tipi di dati a cui può essere convertito giorno-intervallo di dati SQL. Per una spiegazione delle colonne e delle condizioni nella tabella, vedere [la conversione di dati da SQL a tipi di dati C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Identificatore di tipo C|Test|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|Tutti i tipi di intervallo C diurno|Parte finale di campi non verranno troncati<br /><br /> Parte finale di campi troncato<br /><br /> Precisione della destinazione iniziale non è sufficientemente grande da contenere i dati dall'origine|data<br /><br /> Dati troncati<br /><br /> Non definito|Lunghezza dei dati<br /><br /> Lunghezza dei dati<br /><br /> Non definito|n/d<br /><br /> 01S07<br /><br /> 22015|  
|SQL_C_STINYINT [b] SQL_C_UTINYINT [b] SQL_C_USHORT [b] SQL_C_SHORT [b] SQL_C_SLONG [b] SQL_C_ULONG [b] SQL_C_NUMERIC [b] SQL_C_BIGINT [b]|Precisione di intervallo era un singolo campo e i dati è stati convertiti senza troncamento<br /><br /> Precisione intervallo è un singolo campo e troncato frazionaria<br /><br /> Precisione di intervallo era un singolo campo e l'intero troncato<br /><br /> Precisione intervallo non è un singolo campo|data<br /><br /> Dati troncati<br /><br /> Dati troncati<br /><br /> Non definito|Dimensioni del tipo di dati C<br /><br /> Lunghezza dei dati<br /><br /> Lunghezza dei dati<br /><br /> Dimensioni del tipo di dati C|n/d<br /><br /> 01S07<br /><br /> 22003<br /><br /> 07006|  
|SQL_C_BINARY|Lunghezza in byte dei dati < = *BufferLength*<br /><br /> Lunghezza in byte dei dati > *BufferLength*|data<br /><br /> Non definito|Lunghezza dei dati<br /><br /> Non definito|n/d<br /><br /> 22003|  
|SQL_C_CHAR|Lunghezza in byte di caratteri < *BufferLength*<br /><br /> Numero di cifre intero (in contrapposizione a frazionari) < *BufferLength*<br /><br /> Numero di cifre (in contrapposizione a frazionari) intero > = *BufferLength*|data<br /><br /> Dati troncati<br /><br /> Non definito|Dimensioni del tipo di dati C<br /><br /> Dimensioni del tipo di dati C<br /><br /> Non definito|n/d<br /><br /> 01004<br /><br /> 22003|  
_C_WCHAR|Lunghezza in caratteri < *BufferLength*<br /><br /> Numero di cifre intero (in contrapposizione a frazionari) < *BufferLength*<br /><br /> Numero di cifre (in contrapposizione a frazionari) intero > = *BufferLength*|data<br /><br /> Dati troncati<br /><br /> Non definito|Dimensioni del tipo di dati C<br /><br /> Dimensioni del tipo di dati C<br /><br /> Non definito|n/d<br /><br /> 01004<br /><br /> 22003|  
  
 [a] A giorno-intervallo di tipo SQL può essere convertito in qualsiasi tipo di intervallo giorno-time C.  
  
 [b] se la precisione di intervallo è un singolo campo (un giorno, ora, minuto o secondo), l'intervallo di tipo SQL può essere convertito in qualsiasi numerico esatto (SQL_C_STINYINT, SQL_C_UTINYINT, SQL_C_USHORT, SQL_C_SHORT, SQL_C_SLONG, SQL_C_ULONG o SQL_C_NUMERIC).  
  
 La conversione del valore predefinito di un intervallo di tipo SQL è il tipo di dati di intervallo C corrispondente. L'applicazione quindi associa la colonna o parametro (o imposta il campo SQL_DESC_DATA_PTR il record appropriato del ARD) in modo che punti alla struttura SQL_INTERVAL_STRUCT inizializzata (o passa un puntatore alla struttura di SQL _ INTERVAL_STRUCT come il *TargetValuePtr* argomento in una chiamata a **SQLGetData**).  
  
 Nell'esempio seguente viene illustrato come trasferire i dati da una colonna di tipo SQL_INTERVAL_DAY_TO_MINUTE nella struttura SQL_INTERVAL_STRUCT in modo che viene restituita come un intervallo DAY_TO_HOUR.  
  
```  
SQL_INTERVAL_STRUCT is;  
SQLINTEGER    cbValue;  
SQLUINTEGER   days, hours;  
  
// Execute a select statement; "interval_column" is a column  
// whose data type is SQL_INTERVAL_DAY_TO_MINUTE.  
SQLExecDirect(hstmt, "SELECT interval_column FROM table", SQL_NTS);  
  
// Bind  
SQLBindCol(hstmt, 1, SQL_C_INTERVAL_DAY_TO_MINUTE, &is, sizeof(SQL_INTERVAL_STRUCT), &cbValue);  
  
// Fetch  
SQLFetch(hstmt);  
  
// Process data  
days = is.intval.day_second.day;  
hours = is.intval.day_second.hour;  
```
