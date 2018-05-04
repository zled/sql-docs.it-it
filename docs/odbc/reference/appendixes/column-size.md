---
title: Dimensioni della colonna | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], column size
- size of data types [ODBC]
- SQL data types [ODBC], column characteristics
- column size of data types [ODBC]
ms.assetid: 541b83ab-b16d-4714-bcb2-3c3daa9a963b
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1ce38cfd836aa9328838096763ba9191c4a9ec30
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="column-size"></a>Dimensioni di colonna
Le dimensioni di colonna (o parametro) dei tipi di dati numerici sono definita come il numero massimo di cifre utilizzate dal tipo di dati della colonna o parametro o la precisione dei dati. Per i tipi di carattere, si tratta della lunghezza in caratteri dei dati. per i tipi di dati binari, dimensioni della colonna sono definita come la lunghezza in byte dei dati. Per l'ora, timestamp e tutti i tipi di dati di intervallo, questo è il numero di caratteri nella rappresentazione di caratteri dei dati. La dimensione della colonna definita per ogni tipo di dati SQL conciso è illustrata nella tabella seguente.  
  
|Identificatore di tipo SQL|Dimensioni di colonna|  
|-------------------------|-----------------|  
|Tutti i tipi di carattere [a], [b].|Le dimensioni di colonna massima o definita in caratteri della colonna o parametro (come contenuto nel campo descrittore SQL_DESC_LENGTH). Ad esempio, la dimensione della colonna di una colonna carattere a byte singolo definita come char (10) è 10.|  
|SQL_DECIMAL SQL_NUMERIC|Il numero definito di cifre. Ad esempio, la precisione di una colonna definita come NUMERIC(10,3) è 10.|  
|SQL_BIT [c]|1|  
|SQL_TINYINT [c]|3|  
|SQL_SMALLINT [c]|5|  
|SQL_INTEGER [c]|10|  
|SQL_BIGINT [c]|19 (se signed) o 20 (se senza segno)|  
|SQL_REAL [c]|7|  
|SQL_FLOAT [c]|15|  
|SQL_DOUBLE [c]|15|  
|Tutti i tipi binari [a], [b].|La lunghezza massima o definita in byte della colonna o del parametro. Ad esempio, la lunghezza di una colonna definita come Binary (10) è 10.|  
|Tipo SQL_TYPE_DATE [c]|10 (il numero di caratteri di *aaaa-mm-gg* formato).|  
|SQL_TYPE_TIME [c]|8 (il numero di caratteri di *hh-mm-ss* formato), o 9 + *s* (il numero di caratteri nel *hh: mm:* formato [. fff], in cui *s*è la precisione dei secondi).|  
|SQL_TYPE_TIMESTAMP|16 (il numero di caratteri di *aaaa-mm-gg hh.mm* formato)<br /><br /> 19 (il numero di caratteri di *aaaa-mm-gg* *hh: mm:* formato)<br /><br /> o<br /><br /> 20 + *s* (il numero di caratteri di *aaaa-mm-gg hh: mm:* formato [. fff], dove *s* è la precisione dei secondi).|  
|SQL_INTERVAL_SECOND|Dove *p* è l'intervallo di precisione iniziale e *s* è la precisione dei secondi, *p* (se *s*= 0) o *p* + *s*+ 1 (se *s*> 0). [ d]|  
|SQL_INTERVAL_DAY_TO_SECOND|Dove *p* è l'intervallo di precisione iniziale e *s* è la precisione dei secondi 9 +*p* (se *s*= 0) o 10 +*p* + *s* (se *s*> 0). [ d]|  
|SQL_INTERVAL_HOUR_TO_SECOND|Dove *p* è l'intervallo di precisione iniziale e *s* è la precisione dei secondi 6 +*p* (se *s*= 0) o 7 +*p* + *s* (se *s*> 0). [ d]|  
|SQL_INTERVAL_MINUTE_TO_SECOND|Dove *p* è l'intervallo di precisione iniziale e *s* è la precisione dei secondi 3 +*p* (se *s*= 0) o 4 +*p* + *s* (se *s*> 0). [ d]|  
|SQL_INTERVAL_YEAR SQL_INTERVAL_MONTH SQL_INTERVAL_DAY SQL_INTERVAL_HOUR SQL_INTERVAL_MINUTE|*p*, dove *p* è l'intervallo di precisione iniziale. [ 1!d]|  
|SQL_INTERVAL_YEAR_TO_MONTH SQL_INTERVAL_DAY_TO_HOUR|3 +*p*, dove *p* è l'intervallo di precisione iniziale. [ d]|  
|SQL_INTERVAL_DAY_TO_MINUTE|6 +*p*, dove *p* è l'intervallo di precisione iniziale. [ d]|  
|SQL_INTERVAL_HOUR_TO_MINUTE|3 +*p*, dove *p* è l'intervallo di precisione iniziale. [ d]|  
|SQL_GUID|36 (il numero di caratteri di *aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee* formato)|  
  
 [a] per 1.0 ODBC un'applicazione che chiama **SQLSetParam** in un driver ODBC 2.0 e per un'applicazione che chiama ODBC 2.0 **SQLBindParameter** in un driver ODBC 1.0, quando \*  *StrLen_or_IndPtr* è SQL_DATA_AT_EXEC per un tipo SQL_LONGVARCHAR o SQL_LONGVARBINARY, *ColumnSize* deve essere impostato per la lunghezza totale dei dati da inviare, non la precisione come definito in questa tabella.  
  
 [b] se il driver non è possibile determinare la lunghezza di colonna o parametro per un tipo di variabile, restituisce SQL_NO_TOTAL.  
  
 [c] di *ColumnSize* argomento di **SQLBindParameter** viene ignorata per questo tipo di dati.  
  
 [d] per le regole generali sulla lunghezza della colonna nei tipi di dati di intervallo, vedere [lunghezza del tipo di dati intervallo](../../../odbc/reference/appendixes/interval-data-type-length.md), più indietro in questa appendice.  
  
 I valori restituiti per le dimensioni della colonna (o parametro) non corrispondono ai valori nel campo del descrittore. I valori possono provenire da di SQL_DESC_PRECISION o il campo SQL_DESC_LENGTH, a seconda del tipo di dati, come illustrato nella tabella seguente.  
  
|Tipo SQL|Campo di descrizione corrispondente<br /><br /> dimensioni di colonna o parametro|  
|--------------|--------------------------------------------------------------------|  
|Tutti i tipi carattere e binario|LENGTH|  
|Tutti i tipi numerici|PRECISION|  
|Tutti i tipi datetime e interval|LENGTH|  
|SQL_BIT|LENGTH|
