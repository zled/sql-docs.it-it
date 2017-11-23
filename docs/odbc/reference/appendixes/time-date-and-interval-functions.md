---
title: Funzioni di intervallo, ora e data | Documenti Microsoft
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
- functions [ODBC], time functions
- functions [ODBC], date functions
- interval functions [ODBC]
- functions [ODBC], interval functions
- time functions [ODBC]
- date functions [ODBC]
ms.assetid: bdf054a0-7aba-4e99-a34a-799917376fd5
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 64af89226e917b05c28f0c85500281fa84bc676c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="time-date-and-interval-functions"></a>Funzioni di data, ora e intervallo
La tabella seguente elenca le funzioni di data e ora che sono inclusi nel set di funzioni scalari ODBC. Un'applicazione può determinare quali funzioni di data e ora sono supportate da un driver chiamando **SQLGetInfo** con un *tipo di informazioni* di SQL_TIMEDATE_FUNCTIONS.  
  
 Gli argomenti indicati come *timestamp_exp* può essere il nome di una colonna, il risultato di un'altra funzione scalare, o un *ODBC-tempo-escape*, *ODBC-Data-escape*, o *-Escape timestamp ODBC*, in cui il tipo di dati sottostante potrebbe essere rappresentato come SQL_CHAR, SQL_VARCHAR, SQL_TYPE_TIME, SQL_TYPE_DATE o SQL_TYPE_TIMESTAMP.  
  
 Gli argomenti indicati come *date_exp* può essere il nome di una colonna, il risultato di un'altra funzione scalare, o un *ODBC-Data-escape* o *-escape timestamp ODBC*, dove il tipo di dati sottostante potrebbe essere rappresentato come SQL_CHAR, SQL_VARCHAR, SQL_TYPE_DATE o SQL_TYPE_TIMESTAMP.  
  
 Gli argomenti indicati come *time_exp* può essere il nome di una colonna, il risultato di un'altra funzione scalare, o un *ODBC-tempo-escape* o *-escape timestamp ODBC*, dove il tipo di dati sottostante potrebbe essere rappresentato come SQL_CHAR, SQL_VARCHAR, SQL_TYPE_TIME e SQL_TYPE_TIMESTAMP.  
  
 CURRENT_TIMESTAMP, CURRENT_DATE e CURRENT_TIME timedate funzioni scalari in ODBC 3.0 per la compatibilità con SQL-92 sono state aggiunte.  
  
|Funzione|Description|  
|--------------|-----------------|  
|**() CURRENT_DATE** (ODBC 3.0)|Restituisce la data corrente.|  
|**CURRENT_TIME [(** *precisione temporale* **)]** (ODBC 3.0)|Restituisce l'ora locale corrente. Il *precisione temporale* argomento determina la precisione dei secondi del valore restituito.|  
|**CURRENT_TIMESTAMP**<br /> **[(** *timestamp precisione* **)]** (ODBC 3.0)|Restituisce la data locale corrente e l'ora locale come un valore di timestamp. Il *timestamp precisione* argomento determina la precisione dei secondi del timestamp restituito.|  
|**() CURDATE** (ODBC 1.0)|Restituisce la data corrente.|  
|**() CURTIME** (ODBC 1.0)|Restituisce l'ora locale corrente.|  
|**DAYNAME (** *date_exp* **)** (ODBC 2.0)|Restituisce una stringa di caratteri contenente il nome di specifici dell'origine dati del giorno (ad esempio, Sunday a Saturday o da Sun. a Sat per un'origine dati che utilizza l'inglese o da lunedì a domenica per un'origine dati che utilizza l'italiano) per la parte del giorno *date_exp*.|  
|**DAYOFMONTH (** *date_exp* **)** (ODBC 1.0)|Restituisce il giorno del mese in base al campo del mese in *date_exp* come valore intero compreso nell'intervallo da 1 a 31.|  
|**DAYOFWEEK (** *date_exp* **)** (ODBC 1.0)|Restituisce il giorno della settimana in base al campo della settimana in *date_exp* come valore intero compreso nell'intervallo 1-7, dove 1 corrisponde a domenica.|  
|**DAYOFYEAR (** *date_exp* **)** (ODBC 1.0)|Restituisce il giorno dell'anno in base al campo year nella *date_exp* come valore intero compreso nell'intervallo da 1 a 366.|  
|**ESTRARRE (** *Estrai campo FROM* *origine estrazione* **)** (ODBC 3.0)|Restituisce il *Estrai campo* parte il *origine estrazione*. Il *origine estrazione* argomento è un'espressione datetime o intervallo. Il *Estrai campo* argomento può essere una delle parole chiave seguenti:<br /><br /> ANNO MESE GIORNO ORA MINUTO SECONDO<br /><br /> La precisione del valore restituito è definito dall'implementazione. La scala è 0 se non è specificato in secondo luogo, nel qual caso la scala non è la precisione dei secondi frazionari di minore di *origine estrazione* campo.|  
|**ORA (** *time_exp* **)** (ODBC 1.0)|Restituisce l'ora in base al campo dell'ora in *time_exp* come valore intero compreso nell'intervallo 0-23.|  
|**MINUTO (** *time_exp* **)** (ODBC 1.0)|Restituisce i minuti in base al campo relativo ai minuti in *time_exp* come valore intero compreso nell'intervallo 0-59.|  
|**MESE (** *date_exp* **)** (ODBC 1.0)|Restituisce il mese in base al campo del mese in *date_exp* come valore intero compreso nell'intervallo da 1 a 12.|  
|**MONTHNAME (** *date_exp* **)** (ODBC 2.0)|Restituisce una stringa di caratteri contenente il nome del mese (ad esempio, da gennaio a dicembre o Jan a DEC per un'origine dati che utilizza l'inglese o da gennaio a dicembre per un'origine dati che utilizza l'italiano) specifici dell'origine di dati per la parte del mese *date_exp*.|  
|**ORA ()** (ODBC 1.0)|Restituisce una data e ora come valore timestamp corrente.|  
|**TRIMESTRE (** *date_exp* **)** (ODBC 1.0)|Restituisce il trimestre *date_exp* come valore intero compreso nell'intervallo 1-4, dove 1 rappresenta il 1 ° gennaio al 31 marzo.|  
|**SECONDO (** *time_exp* **)** (ODBC 1.0)|Restituisce i secondi in base al secondo campo *time_exp* come valore intero compreso nell'intervallo 0-59.|
|**TIMESTAMPADD (** *intervallo*, *integer_exp*, *timestamp_exp* **)** (ODBC 2.0)|Restituisce il timestamp calcolato aggiungendo *integer_exp* intervalli di tipo *intervallo* a *timestamp_exp*. I valori validi di *intervallo* sono le parole chiave seguenti:<br /><br /> SQL_TSI_FRAC_SECOND<br /><br /> SQL_TSI_SECOND<br /><br /> SQL_TSI_MINUTE<br /><br /> SQL_TSI_HOUR<br /><br /> SQL_TSI_DAY<br /><br /> SQL_TSI_WEEK<br /><br /> SQL_TSI_MONTH<br /><br /> SQL_TSI_QUARTER<br /><br /> SQL_TSI_YEAR<br /><br /> frazioni di secondo in cui sono espressi in miliardesimi di secondo. Ad esempio, l'istruzione SQL seguente restituisce il nome di ogni dipendente e la data di ricorrenza annuale dell'anno:<br /><br /> `SELECT NAME, {fn  TIMESTAMPADD(SQL_TSI_YEAR, 1, HIRE_DATE)} FROM  EMPLOYEES`<br /><br /> Se *timestamp_exp* è un valore di ora e *intervallo* specifica i giorni, settimane, mesi, trimestri o anni, la parte relativa alla data di *timestamp_exp* è impostata sulla data corrente prima di il calcolo del timestamp risulta.<br /><br /> Se *timestamp_exp* è un valore di data e *intervallo* specifica frazionari secondi, secondi, minuti o ore, la porzione dell'ora *timestamp_exp* è impostato su 0 prima il calcolo del timestamp risulta.<br /><br /> Un'applicazione determina quali intervalli di un'origine dati supporta chiamando **SQLGetInfo** con l'opzione SQL_TIMEDATE_ADD_INTERVALS.|  
|**TIMESTAMPDIFF (** *intervallo*, *timestamp_exp1*, *timestamp_exp2* **)** (ODBC 2.0)|Restituisce il numero intero di intervalli di tipo *intervallo* mediante il quale *timestamp_exp2* è maggiore di *timestamp_exp1*. I valori validi di *intervallo* sono le parole chiave seguenti:<br /><br /> SQL_TSI_FRAC_SECOND<br /><br /> SQL_TSI_SECOND<br /><br /> SQL_TSI_MINUTE<br /><br /> SQL_TSI_HOUR<br /><br /> SQL_TSI_DAY<br /><br /> SQL_TSI_WEEK<br /><br /> SQL_TSI_MONTH<br /><br /> SQL_TSI_QUARTER<br /><br /> SQL_TSI_YEAR<br /><br /> frazioni di secondo in cui sono espressi in miliardesimi di secondo. Ad esempio, l'istruzione SQL seguente restituisce il nome di ogni dipendente e il numero di anni che egli usato:<br /><br /> `SELECT NAME, {fn  TIMESTAMPDIFF(SQL_TSI_YEAR, {fn CURDATE()}, HIRE_DATE)} FROM EMPLOYEES`<br /><br /> Se due espressioni di timestamp è un valore di ora e *intervallo* giorni, settimane, mesi, trimestri o anni, la parte relativa alla data di tale timestamp viene impostata sulla data corrente prima di calcolare la differenza tra i timestamp.<br /><br /> Se due espressioni di timestamp è un valore di data e *intervallo* specifica frazionari secondi, secondi, minuti o ore, la porzione dell'ora di tale timestamp è impostata su 0 prima di calcolare la differenza tra i timestamp.<br /><br /> Un'applicazione determina quali intervalli di un'origine dati supporta chiamando **SQLGetInfo** con l'opzione SQL_TIMEDATE_DIFF_INTERVALS.|  
|**SETTIMANA (** *date_exp* **)** (ODBC 1.0)|Restituisce la settimana dell'anno in base al campo della settimana in *date_exp* come valore intero compreso nell'intervallo da 1 a 53.|  
|**ANNO (** *date_exp* **)** (ODBC 1.0)|Restituisce l'anno in base al campo year nella *date_exp* come valore integer. L'intervallo è dipende dall'origine dati.|
