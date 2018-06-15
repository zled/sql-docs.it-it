---
title: Tipi di dati SQL | Documenti Microsoft
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
- SQL data types [ODBC]
- SQL data types [ODBC], about SQL data types
- data types [ODBC], SQL data types
ms.assetid: 1b22f985-f5e4-4779-87eb-e43329a442b1
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ba122ccbc873603b434a8541fe44aee10a5104e0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32914186"
---
# <a name="sql-data-types"></a>Tipi di dati SQL
Ogni sistema DBMS definisce i proprio tipi SQL. Ogni driver ODBC espone solo i tipi di dati SQL che definisce il sistema DBMS associato. Informazioni sulle modalità di mapping di un driver SQL DBMS tipi per gli identificatori di tipo definite da ODBC SQL e come un driver esegue il mapping di tipi SQL DBMS per i proprio identificatori di tipo specifici del driver SQL viene restituito tramite una chiamata a **SQLGetTypeInfo**. Un driver restituisce inoltre i tipi di dati SQL quando si descrivono i tipi di dati di colonne e parametri mediante chiamate a **SQLColAttribute**, **SQLColumns**, **SQLDescribeCol**, **SQLDescribeParam**, **SQLProcedureColumns**, e **SQLSpecialColumns**.  
  
> [!NOTE]  
>  I tipi di dati SQL sono contenuti nei campi SQL_DESC_ CONCISE_TYPE SQL_DESC_TYPE e SQL_DESC_DATETIME_INTERVAL_CODE dei descrittori di implementazione. Caratteristiche dei tipi di dati SQL sono contenute nei campi SQL_DESC_PRECISION, SQL_DESC_SCALE, SQL_DESC_LENGTH e SQL_DESC_OCTET_LENGTH dei descrittori di implementazione. Per ulteriori informazioni, vedere [gli identificatori di tipo di dati e i descrittori](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md) più avanti in questa appendice.  
  
 Un determinato driver e l'origine dati non supportano necessariamente tutti i tipi di dati SQL che sono definiti in questa appendice. Supporto di un driver per i tipi di dati SQL dipende dal livello di SQL-92 compatibile con il driver. Per determinare il livello di grammatica SQL-92 supportata dal driver, un'applicazione chiama **SQLGetInfo** con il tipo di informazioni SQL_SQL_CONFORMANCE. Tipi di dati SQL aggiuntivi, specifiche del driver potrebbe supportano inoltre un driver e i dati di origine specificato. Per determinare un driver di tipi di dati che supporta, un'applicazione chiama **SQLGetTypeInfo**. Per informazioni sui tipi di dati specifici del driver SQL, vedere la documentazione del driver. Per informazioni sui tipi di dati in un'origine dati specifica, vedere la documentazione per l'origine dati.  
  
> [!IMPORTANT]  
>  Le tabelle in questa appendice sono solo linee guida e Mostra in genere utilizzato nomi, intervalli e i limiti dei tipi di dati SQL. Una determinata origine dati potrebbe supportare solo alcuni dei tipi di dati elencati e le caratteristiche dei tipi di dati supportati possono differire da quelli elencati.  
  
 Nella tabella seguente sono elencati gli identificatori dei tipi SQL validi per tutti i tipi di dati SQL. La tabella include anche il nome e la descrizione del tipo di dati corrispondente da SQL-92 (se presente).  
  
|Identificatore di tipo SQL [1]|Dati SQL tipico<br /><br /> tipo [2]|Descrizione del tipo tipico|  
|------------------------------|------------------------------------|------------------------------|  
|SQL_CHAR|CHAR (*n*)|Stringa di lunghezza fissa di caratteri *n*.|  
|SQL_VARCHAR|VARCHAR (*n*)|Stringa di caratteri a lunghezza variabile con una lunghezza massima della stringa *n*.|  
|SQL_LONGVARCHAR|LONG VARCHAR|Dati di tipo carattere di lunghezza variabile. Lunghezza massima è dipende dall'origine dati. [9]|  
|SQL_WCHAR|WCHAR (*n*)|Stringa di caratteri Unicode di lunghezza fissa *n*|  
|SQL_WVARCHAR|VARWCHAR (*n*)|Stringa di caratteri a lunghezza variabile Unicode con una lunghezza massima della stringa *n*|  
|SQL_WLONGVARCHAR|LONGWVARCHAR|Dati di tipo carattere a lunghezza variabile Unicode. Lunghezza massima è dipende dall'origine dati|  
|SQL_DECIMAL|DECIMAL (*p*,*s*)|Firmato, a valore numerico esatto con una precisione di almeno *p* e la scala *s.* (La precisione massima è definito dal driver). (1 < = *p* < = 15; *s* <= *p*). [ 4]|  
|SQL_NUMERIC|NUMERICO (*p*,*s*)|Firmato, a valore numerico esatto con una precisione *p* e scala *s* (1 < = *p* < = 15; *s* <= *p*). [ 4]|  
|SQL_SMALLINT|SMALLINT|Valore numerico esatto con precisione 5 e scala 0 (firmato: da – 32.768 < = *n* < = 32.767, senza segno: 0 < = *n* < = 65.535) [3].|  
_INTEGER|INTEGER|Valore numerico esatto con 10 precisione e scala 0 (firmato: – 2 [31] < = *n* < = 2 [31] – 1, non firmato: 0 < = *n* < = 2 [32] – 1) [3].|  
|SQL_REAL|REAL|Valore con segno, numerico approssimativo con una precisione binaria 24 (zero o valore assoluto 10 [–38] per 10[38]).|  
|SQL_FLOAT|FLOAT (*p*)|Valore con segno, numerico approssimativo con una precisione binaria di almeno *p*. (La precisione massima è definito dal driver). [5]|  
|SQL_DOUBLE|DOUBLE PRECISION|Valore con segno, numerico approssimativo con una precisione binaria 53 (zero o valore assoluto 10 [–308] per 10[308]).|  
|SQL_BIT|BIT|Singolo bit di dati binari. [8]|  
|SQL_TINYINT|TINYINT|Valore numerico esatto con 3 precisione e scala 0 (firmato: da – 128 < = *n* < = 127, senza segno: 0 < = *n* < = 255) [3].|  
_BIGINT|bigint|Valore esatto di valori numerici con precisione 19 (se firmato) o 20 (se senza segno) e scala 0 (firmato: – 2 [63] < = *n* < = 2 [63] – 1, non firmato: 0 < = *n* < = 2 [64] – 1) [3], [9].|  
|SQL_BINARY|BINARIO (*n*)|Dati binari a lunghezza fissa *n*. [ 9]|  
|SQL_VARBINARY|VARBINARY (*n*)|Dati binari a lunghezza variabile di lunghezza massima *n*. Il valore massimo è impostato dall'utente. [9]|  
|SQL_LONGVARBINARY|LONG VARBINARY|Dati binari a lunghezza variabile. Lunghezza massima è dipende dall'origine dati. [9]|  
|TIPO SQL_TYPE_DATE [6]|DATE|Anno, mese e giorno campi, conforme alle regole del calendario gregoriano. (Vedere [vincoli del calendario gregoriano](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md), più avanti in questa appendice.)|  
|SQL_TYPE_TIME [6]|TEMPO (*p*)|Ora, minuto e secondo campi, con i valori validi per ore di valori validi da 00 a 23, da 00 a 59 minuti e i valori validi per i secondi di 00 a 61. Precisione *p* indica la precisione dei secondi.|  
|SQL_TYPE_TIMESTAMP [6]|TIMESTAMP (*p*)|Anno, mese, giorno, ora, minuti e i campi di secondo, con i valori validi, come definito per i tipi di dati data e ora.|  
_TYPE_UTCDATETIME|UTCDATETIME|Anno, mese, giorno, ora, minuto, secondo, utchour e utcminute campi. I campi utchour e utcminute contengono precisione di 1/10 microsecondi.|  
|SQL_TYPE_UTCTIME|UTCTIME|Campi ora, minuto, secondo, utchour e utcminute. I campi utchour e utcminute contengono precisione di 1/10 microsecondo...|  
|SQL_INTERVAL_MONTH [7]|INTERVALLO mese (*p*)|Numero di mesi tra due date; *p* è l'intervallo di precisione iniziale.|  
|SQL_INTERVAL_YEAR [7]|ANNO di intervallo (*p*)|Numero di anni tra due date; *p* è l'intervallo di precisione iniziale.|  
|SQL_INTERVAL_YEAR_TO_MONTH [7]|ANNO di intervallo (*p*) al mese|Numero di anni e mesi tra due date; *p* è l'intervallo di precisione iniziale.|  
|SQL_INTERVAL_DAY [7]|INTERVALLO giorno (*p*)|Numero di giorni tra due date; *p* è l'intervallo di precisione iniziale.|  
|SQL_INTERVAL_HOUR [7]|ORA di intervallo (*p*)|Numero di ore tra due data/ora; *p* è l'intervallo di precisione iniziale.|  
|SQL_INTERVAL_MINUTE [7]|MINUTI di intervallo (*p*)|Numero di minuti tra due data/ora; *p* è l'intervallo di precisione iniziale.|  
|SQL_INTERVAL_SECOND [7]|INTERVALLO di secondo (*p*,*q*)|Numero di secondi tra due data/ora; *p* è l'intervallo di precisione iniziale e *q* è la precisione dei secondi di intervallo.|  
_INTERVAL_DAY_TO_HOUR [7]|INTERVALLO giorno (*p*) all'ora|Numero di giorni/ore tra due data/ora; *p* è l'intervallo di precisione iniziale.|  
|SQL_INTERVAL_DAY_TO_MINUTE [7]|INTERVALLO giorno (*p*) al minuto|Numero di giorni/ore o minuti tra due data/ora; *p* è l'intervallo di precisione iniziale.|  
|SQL_INTERVAL_DAY_TO_SECOND [7]|INTERVALLO giorno (*p*) al secondo (*q*)|Numero di giorni/ore/minuti/secondi tra due data/ora; *p* è l'intervallo di precisione iniziale e *q* è la precisione dei secondi di intervallo.|  
|SQL_INTERVAL_HOUR_TO_MINUTE [7]|ORA di intervallo (*p*) al minuto|Numero di ore o minuti tra due data/ora; *p* è l'intervallo di precisione iniziale.|  
|SQL_INTERVAL_HOUR_TO_SECOND [7]|ORA di intervallo (*p*) al secondo (*q*)|Numero di minuti/ore/secondi tra due data/ora; *p* è l'intervallo di precisione iniziale e *q* è la precisione dei secondi di intervallo.|  
_INTERVAL_MINUTE_TO_SECOND [7]|MINUTI di intervallo (*p*) al secondo (*q*)|Numero di minuti/secondi tra due data/ora; *p* è l'intervallo di precisione iniziale e *q* è la precisione dei secondi di intervallo.|  
|SQL_GUID|GUID|GUID di lunghezza fissa.|  
  
 [1]. questo è il valore restituito nella colonna DATA_TYPE da una chiamata a **SQLGetTypeInfo**.  
  
 [2]. questo è il valore restituito nella colonna nome e la creazione di parametri da una chiamata a **SQLGetTypeInfo**. La colonna nome restituisce la designazione, ad esempio, CHAR, mentre la colonna creare PARAMS restituisce un elenco delimitato da virgole dei parametri di creazione, ad esempio precisione, scala e lunghezza.  
  
 [3] è un'applicazione utilizza **SQLGetTypeInfo** o **SQLColAttribute** per determinare se un particolare tipo di dati o una colonna specifica in un set di risultati è senza segno.  
  
 [4] tipi di dati SQL_DECIMAL e SQL_NUMERIC differiscono solo per la precisione. La precisione di un numero decimale (*p*,*s*) è una precisione decimale definito dall'implementazione che è non minore di *p*, mentre la precisione di un valore numerico (*p* ,*s*) è esattamente uguale alla *p*.  
  
 [5] a seconda dell'implementazione, può essere la precisione di SQL_FLOAT 24 o 53: se è 24, il tipo di dati SQL_FLOAT è identico SQL_REAL; Se è 53, il tipo di dati SQL_FLOAT è identico SQL_DOUBLE.  
  
 [6] in ODBC 3*x*, i tipi di dati SQL date, time e timestamp sono SQL_TYPE_DATE, SQL_TYPE_TIME e SQL_TYPE_TIMESTAMP, rispettivamente; in ODBC 2. *x*, i tipi di dati sono SQL_DATE, SQL_TIME e SQL_TIMESTAMP.  
  
 [7] per ulteriori informazioni sui tipi di dati di intervallo SQL, vedere il [i tipi di dati di intervallo](../../../odbc/reference/appendixes/interval-data-types.md) sezione più avanti in questa appendice.  
  
 [8] il tipo di dati SQL_BIT ha caratteristiche diverse rispetto al tipo BIT in SQL-92.  
  
 [9] questo tipo di dati non dispone di alcun tipo di dati corrispondente in SQL-92.  
  
 Questa sezione vengono fornite nell'esempio seguente.  
  
-   [Esempio di set di risultati SQLGetTypeInfo](../../../odbc/reference/appendixes/example-sqlgettypeinfo-result-set.md)
