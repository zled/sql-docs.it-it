---
title: Date, Time e Timestamp letterali | Documenti Microsoft
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
helpviewer_keywords: escape sequences [ODBC], literals
ms.assetid: 2b42a52a-6353-494c-a179-3a7533cd729f
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8aa042321602332ea016b88c69332dd67a256044
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="date-time-and-timestamp-literals"></a>Date, Time e Timestamp letterali
La sequenza di escape per i valori letterali data, ora e timestamp  
  
 **{***-tipo* **'** *valore* **'}**   
  
 dove *-tipo di valore letterale* è uno dei valori elencati nella tabella seguente.  
  
|*tipo di valore letterale*|Significato|Formato di *valore*|  
|---------------------|-------------|-----------------------|  
|**d**|Data|*aaaa*-*mm*-*gg*|  
|**t**|Ora *|*hh*:*mm*:*ss*[1]|  
|**Servizi terminal**|Timestamp|*aaaa*-*mm*-*gg* *hh*:*mm*:*ss* [. *f...* ] [1]|  
  
 [1] il numero di cifre a destra del separatore decimale in un intervallo di tempo o timestamp letterale contenente un componente di secondi dipende la precisione dei secondi, come contenuto nel campo SQL_DESC_PRECISION descrittore. (Per ulteriori informazioni, vedere [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).)  
  
 Per ulteriori informazioni sulla data, ora e timestamp sequenze di escape, vedere [Date, Time e Timestamp sequenze di Escape](../../../odbc/reference/appendixes/date-time-and-timestamp-escape-sequences.md) nella grammatica SQL di appendice c:.  
  
 Ad esempio, entrambe le istruzioni SQL seguenti aggiornare open data di ordine di vendita 1023 nella tabella Orders. La prima istruzione utilizza la sintassi della sequenza di escape. La seconda istruzione utilizza la sintassi nativa Rdb Oracle per la colonna di data e non è interoperativa.  
  
```  
UPDATE Orders SET OpenDate={d '1995-01-15'} WHERE OrderID=1023  
UPDATE Orders SET OpenDate='15-Jan-1995' WHERE OrderID=1023  
```  
  
 La sequenza di escape per una data, ora o timestamp letterale può essere inserita in una variabile di tipo carattere associata a una data, ora o parametro di tipo timestamp. Ad esempio, il codice seguente utilizza un parametro di data associato a una variabile di tipo carattere per aggiornare la data dell'ordine di vendita 1023 nella tabella Orders aperta:  
  
```  
SQLCHAR      OpenDate[56]; // The size of a date literal is 55.  
SQLINTEGER   OpenDateLenOrInd = SQL_NTS;  
  
// Bind the parameter.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_TYPE_DATE, 0, 0,  
                  OpenDate, sizeof(OpenDate), &OpenDateLenOrInd);  
  
// Place the date in the OpenDate variable. In addition to the escape  
// sequence shown, it would also be possible to use either of the  
// strings "{d '1995-01-15'}" and "15-Jan-1995", although the latter  
// is data source-specific.  
strcpy_s( (char*) OpenDate, _countof(OpenDate), "{d '1995-01-15'}");  
  
// Execute the statement.  
SQLExecDirect(hstmt, "UPDATE Orders SET OpenDate=? WHERE OrderID = 1023", SQL_NTS);  
```  
  
 Tuttavia, è in genere più efficiente per associare il parametro direttamente a una struttura di data:  
  
```  
SQL_DATE_STRUCT   OpenDate;  
SQLINTEGER        OpenDateInd = 0;  
  
// Bind the parameter.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_TYPE_DATE, SQL_TYPE_DATE, 0, 0,  
                  &OpenDate, 0, &OpenDateLen);  
  
// Place the date in the dsOpenDate structure.  
OpenDate.year = 1995;  
OpenDate.month = 1;  
OpenDate.day = 15;  
  
// Execute the statement.  
SQLExecDirect(hstmt, "UPDATE Employee SET OpenDate=? WHERE OrderID = 1023", SQL_NTS);  
```  
  
 Per determinare se un driver supporta le sequenze di escape ODBC per data, ora o valori letterali timestamp, un'applicazione chiama **SQLGetTypeInfo**. Se l'origine dati supporta un tipo di dati data, ora o timestamp, deve supportare anche la sequenza di escape corrispondente.  
  
 Origini dati possono supportare anche i valori letterali datetime definiti nella specifica ANSI SQL-92, che sono diverse dalle sequenze di escape ODBC per data, ora o valori letterali di timestamp. Per determinare se un'origine dati supporta i valori letterali ANSI, un'applicazione chiama **SQLGetInfo** con l'opzione SQL_ANSI_SQL_DATETIME_LITERALS.  
  
 Per determinare se un driver supporta le sequenze di escape ODBC per i valori letterali di intervallo, un'applicazione chiama **SQLGetTypeInfo**. Se l'origine dati supporta un tipo di dati di intervallo datetime, deve supportare anche la sequenza di escape corrispondente.  
  
 Origini dati possono supportare anche i valori letterali datetime definiti nella specifica ANSI SQL-92, diversi da sequenze di escape ODBC per i valori letterali intervallo datetime. Per determinare se un'origine dati supporta i valori letterali ANSI, un'applicazione chiama **SQLGetInfo** con l'opzione SQL_ANSI_SQL_DATETIME_LITERALS.
