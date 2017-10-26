---
title: 'C a SQL: intervalli anno-mese | Documenti Microsoft'
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
- converting data from c to SQL types [ODBC], year-month intervals
- intervals [ODBC], converting
- year-month intervals [ODBC]
- data conversions from C to SQL types [ODBC], year-month intervals
ms.assetid: a0eb7b55-9db0-4375-9210-bddec4593880
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6a6b4e1992ea5f446203b125261f5572c2bd9db7
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="c-to-sql-year-month-intervals"></a>C a SQL: intervalli anno-mese
Gli identificatori per i tipi di dati ODBC C intervallo anno-mese sono:  
  
 SQL_C_INTERVAL_MONTH SQL_C_INTERVAL_YEAR SQL_C_INTERVAL_YEAR_TO_MONTH  
  
 Nella tabella seguente viene illustrato SQL ODBC dei tipi di dati per il mese dell'anno possono essere convertiti i dati di intervallo C. Per una spiegazione delle colonne e delle condizioni nella tabella, vedere [la conversione di dati da C a tipi di dati SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Identificatore di tipo SQL|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR, [a]<br /><br /> SQL_VARCHAR, [a]<br /><br /> SQL_LONGVARCHAR [a]|Lunghezza in byte di colonna > = lunghezza in byte di caratteri<br /><br /> Lunghezza in byte colonna < caratteri di lunghezza in byte [a]<br /><br /> Valore di dati non è un intervallo valido di valore letterale|n/d<br /><br /> 22001<br /><br /> 22015|  
|SQL_WCHAR [a]<br /><br /> SQL_WVARCHAR [a]<br /><br /> SQL_WLONGVARCHAR [a]|Lunghezza in caratteri colonna > = lunghezza in caratteri di dati<br /><br /> Lunghezza in caratteri colonna < caratteri di lunghezza dei dati [a]<br /><br /> Valore di dati non è un intervallo valido di valore letterale|n/d<br /><br /> 22001<br /><br /> 22015|  
|SQL_TINYINT [b]<br /><br /> SQL_SMALLINT [b]<br /><br /> SQL_INTEGER [b]<br /><br /> SQL_BIGINT [b]<br /><br /> SQL_NUMERIC [b]<br /><br /> SQL_DECIMAL [b]|Conversione di un intervallo di un solo campo non ha restituito il troncamento di cifre intere<br /><br /> La conversione ha causato un troncamento di cifre intere|n/d<br /><br /> 22003|  
|SQL_INTERVAL_MONTH<br /><br /> SQL_INTERVAL_YEAR<br /><br /> SQL_INTERVAL_YEAR_TO_MONTH|Valore di dati è stato convertito senza troncamento dei campi<br /><br /> Uno o più campi di valore di dati sono stati troncati durante la conversione|n/d<br /><br /> 22015|  
  
 tipi di dati intervallo [a] tutti C possono essere convertito in un tipo di dati carattere.  
  
 [b] se il campo di tipo nella struttura di intervallo è tale che l'intervallo di un singolo campo (SQL_YEAR o SQL_MONTH), il tipo di intervallo C può essere convertito in qualsiasi numerico esatto (SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_DECIMAL o SQL_NUMERIC).  
  
 La conversione del valore predefinito di un intervallo di tipo C è l'intervallo di anno-mese tipo SQL corrispondente.  
  
 Il driver ignora il valore di lunghezza/indicatore quando la conversione dei dati dal tipo di dati di intervallo C e si presuppone che le dimensioni del buffer di dati sono la dimensione del tipo di dati di intervallo C. Viene passato il valore di lunghezza/indicatore di *StrLen_or_Ind* argomento **SQLPutData** e nel buffer specificato con il *StrLen_or_IndPtr* argomento **SQLBindParameter**. Il buffer dei dati è specificato con il *DataPtr* argomento in **SQLPutData** e *ParameterValuePtr* argomento **SQLBindParameter**.

