---
title: 'SQL per c: anno-mese intervalli | Documenti Microsoft'
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- converting data from SQL to c types [ODBC], about converting
- data conversions from SQL to C types [ODBC], year-month intervals
- intervals [ODBC], converting
- year-month intervals [ODBC]
ms.assetid: 1233634b-8214-420f-b872-3b2630105ba4
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4acd46374597b19849abfaa7cb547c8b6af23bd9
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="sql-to-c-year-month-intervals"></a>SQL a intervalli di anno-mese c:
Gli identificatori per i tipi di dati SQL ODBC intervallo anno-mese sono:  
  
 SQL_INTERVAL_YEAR  
  
 SQL_INTERVAL_MONTH  
  
 SQL_INTERVAL_YEAR_TO_MONTH  
  
 Nella tabella seguente viene illustrato ODBC C a tipi di dati per il mese e anno-intervallo di dati SQL può essere convertito. Per una spiegazione delle colonne e delle condizioni nella tabella, vedere [la conversione di dati da SQL a tipi di dati C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Identificatore di tipo C|Test|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_INTERVAL_MONTH [a]<br /><br /> SQL_C_INTERVAL_YEAR [a]<br /><br /> SQL_C_INTERVAL_YEAR_TO_MONTH [a]|Parte finale di campi non verranno troncati<br /><br /> Parte finale di campi troncato<br /><br /> Precisione della destinazione iniziale non è sufficientemente grande da contenere i dati dall'origine|data<br /><br /> Dati troncati<br /><br /> Non definito|Lunghezza in byte dei dati<br /><br /> Lunghezza in byte dei dati<br /><br /> Non definito|n/d<br /><br /> 01S07<br /><br /> 22015|  
|SQL_C_STINYINT [b]<br /><br /> SQL_C_UTINYINT [b]<br /><br /> SQL_C_USHORT [b]<br /><br /> SQL_C_SHORT [b]<br /><br /> SQL_C_SLONG [b]<br /><br /> SQL_C_ULONG [b]<br /><br /> SQL_C_NUMERIC [b]<br /><br /> SQL_C_BIGINT [b]|Precisione di intervallo era un singolo campo e i dati è stati convertiti senza troncamento<br /><br /> Precisione di intervallo era un singolo campo e l'intero troncato<br /><br /> Precisione intervallo non è un singolo campo|data<br /><br /> Dati troncati<br /><br /> Non definito|Dimensioni del tipo di dati C<br /><br /> Lunghezza in byte dei dati<br /><br /> Dimensioni del tipo di dati C|n/d<br /><br /> 22003<br /><br /> 22015|  
_C_BINARY|Lunghezza in byte dei dati < = *BufferLength*<br /><br /> Lunghezza in byte dei dati > *BufferLength*|data<br /><br /> Non definito|Lunghezza in byte dei dati<br /><br /> Non definito|n/d<br /><br /> 22003|  
|SQL_C_CHAR|Lunghezza in byte di caratteri < *BufferLength*<br /><br /> Numero di cifre intero (in contrapposizione frazionari) < *BufferLength*<br /><br /> Numero di cifre intero (in contrapposizione frazionari) > = *BufferLength*|data<br /><br /> Dati troncati<br /><br /> Non definito|Dimensioni del tipo di dati C<br /><br /> Dimensioni del tipo di dati C<br /><br /> Non definito|n/d<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|Lunghezza in caratteri < *BufferLength*<br /><br /> Numero di cifre intero (in contrapposizione frazionari) < *BufferLength*<br /><br /> Numero di cifre intero (in contrapposizione frazionari) > = *BufferLength*|data<br /><br /> Dati troncati<br /><br /> Non definito|Dimensioni del tipo di dati C<br /><br /> Dimensioni del tipo di dati C<br /><br /> Non definito|n/d<br /><br /> 01004<br /><br /> 22003|  
  
 [a] intervallo di anno-mese di un tipo SQL può essere convertito in qualsiasi tipo di intervallo C anno-mese.  
  
 [b] se la precisione di intervallo è un singolo campo (un mese o anno), l'intervallo di tipo SQL può essere convertito in qualsiasi numerico esatto (SQL_C_STINYINT, SQL_C_UTINYINT, SQL_C_USHORT, SQL_C_SHORT, SQL_C_SLONG, SQL_C_ULONG o SQL_C_NUMERIC).  
  
 La conversione del valore predefinito di un intervallo di tipo SQL è il tipo di dati di intervallo C corrispondente. L'applicazione quindi associa la colonna o parametro (o imposta il campo SQL_DESC_DATA_PTR il record appropriato del ARD) in modo che punti alla struttura SQL_INTERVAL_STRUCT inizializzata (o passa un puntatore alla struttura di SQL _ INTERVAL_STRUCT come il *TargetValuePtr* argomento in una chiamata a **SQLGetData**).
