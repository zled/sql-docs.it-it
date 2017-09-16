---
title: Struttura di intervallo C | Documenti Microsoft
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
- data types [ODBC], interval data types
- interval data type [ODBC], structure
- C data types [ODBC], interval
ms.assetid: 52b42b56-50aa-4ce6-8d79-0963c7a71437
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 146e16608f0f2f790bf49a84de2ef4610df33d0f
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="c-interval-structure"></a>Struttura di intervallo C
Ognuno dei tipi di dati di intervallo C elencati nel [tipi di dati C](../../../odbc/reference/appendixes/c-data-types.md) sezione Usa la stessa struttura per contenere i dati di intervallo. Quando **SQLFetch**, **SQLFetchScroll**, o **SQLGetData** viene chiamato, il driver restituisce i dati nella struttura SQL_INTERVAL_STRUCT, utilizza il valore specificato per il applicazione per i tipi di dati C (nella chiamata a **SQLBindCol**, **SQLGetData**, o **SQLBindParameter**) per interpretare il contenuto di SQL_INTERVAL_STRUCT e consente di popolare il *interval_type* campo struttura con il *enum* valore corrispondente al tipo di C. Si noti che i driver non leggono il *interval_type* campo per determinare il tipo dell'intervallo; cui recuperare il valore del campo SQL_DESC_CONCISE_TYPE descrittore. Quando la struttura viene utilizzata per i dati di parametro, il driver utilizza il valore specificato dall'applicazione nel campo SQL_DESC_CONCISE_TYPE di APD per interpretare il contenuto di SQL_INTERVAL_STRUCT, anche se l'applicazione imposta il valore della * interval_type* campo su un valore diverso.  
  
 Questa struttura viene definita come segue:  
  
```  
typedef struct tagSQL_INTERVAL_STRUCT  
{  
   SQLINTERVAL interval_type;   
   SQLSMALLINT interval_sign;  
   union {  
         SQL_YEAR_MONTH_STRUCT   year_month;  
         SQL_DAY_SECOND_STRUCT   day_second;  
         } intval;  
} SQL_INTERVAL_STRUCT;  
typedef enum   
{  
   SQL_IS_YEAR = 1,  
   SQL_IS_MONTH = 2,  
   SQL_IS_DAY = 3,  
   SQL_IS_HOUR = 4,  
   SQL_IS_MINUTE = 5,  
   SQL_IS_SECOND = 6,  
   SQL_IS_YEAR_TO_MONTH = 7,  
   SQL_IS_DAY_TO_HOUR = 8,  
   SQL_IS_DAY_TO_MINUTE = 9,  
   SQL_IS_DAY_TO_SECOND = 10,  
   SQL_IS_HOUR_TO_MINUTE = 11,  
   SQL_IS_HOUR_TO_SECOND = 12,  
   SQL_IS_MINUTE_TO_SECOND = 13  
} SQLINTERVAL;  
  
typedef struct tagSQL_YEAR_MONTH  
{  
   SQLUINTEGER year;  
   SQLUINTEGER month;   
} SQL_YEAR_MONTH_STRUCT;  
  
typedef struct tagSQL_DAY_SECOND  
{  
   SQLUINTEGER day;  
   SQLUINTEGER hour;  
   SQLUINTEGER minute;  
   SQLUINTEGER second;  
   SQLUINTEGER fraction;  
} SQL_DAY_SECOND_STRUCT;  
```  
  
 Il *interval_type* campo del SQL_INTERVAL_STRUCT indica all'applicazione struttura viene mantenuto nell'unione e anche i membri della struttura sono rilevanti. Il *interval_sign* campo contiene il valore SQL_FALSE se l'intervallo iniziale di campo non è firmato; in caso di SQL_TRUE, il campo iniziale è negativo. Il valore nel campo di uno stesso è sempre senza segno, indipendentemente dal valore di *interval_sign*. Il *interval_sign* campo agisce come un bit di segno.
