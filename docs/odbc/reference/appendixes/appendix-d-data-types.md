---
title: 'Appendice d: i tipi di dati | Documenti Microsoft'
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
- C data types [ODBC], defined
- SQL data types [ODBC], defined
- data types [ODBC]
- data types [ODBC], about data types
ms.assetid: 981d49c3-3531-4543-aa75-5bd9e4f67000
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a543430479a33953e087fd50c91f7f2a307fc204
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="appendix-d-data-types"></a>Appendice d: i tipi di dati
ODBC definisce due set di tipi di dati: SQL tipi di dati e tipi di dati C. Tipi di dati SQL indicano il tipo di dati dei dati archiviati nell'origine dati. Tipi di dati C indicano il tipo di dati di dati memorizzati nel buffer dell'applicazione.  
  
 Per ogni sistema DBMS conforme allo standard SQL-92 sono definiti i tipi di dati SQL. Per ogni tipo di dati SQL specificata nello standard SQL-92, ODBC definisce un identificatore di tipo, ovvero un **#define** valore che viene passata come argomento nelle funzioni ODBC o restituito nei metadati di un set di risultati. SQL-92 solo tipi di dati non supportati da ODBC sono BIT (il tipo ODBC SQL_BIT ha caratteristiche diverse), BIT_VARYING, TIME_WITH_TIMEZONE, TIMESTAMP_WITH_TIMEZONE e NATIONAL_CHARACTER. I driver sono responsabili per il mapping dei tipi di dati specifici dell'origine SQL per gli identificatori di tipo di dati SQL ODBC e gli identificatori dei tipi dati specifici del driver SQL. Il tipo di dati SQL è specificato nel campo SQL_DESC_CONCISE_TYPE di un descrittore di implementazione.  
  
 ODBC definisce i tipi di dati C e i corrispondenti identificatori di tipo ODBC. Un'applicazione specifica il tipo di dati del buffer che riceverà i dati del set di risultati, passando l'identificatore di tipo C appropriato in C il *TargetType* argomento in una chiamata a **SQLBindCol** o ** SQLGetData**. Specifica il tipo C del buffer che contiene un parametro dell'istruzione, passando l'identificatore di tipo C appropriato nel *ValueType* argomento in una chiamata a **SQLBindParameter**. Il tipo di dati C è specificato nel campo SQL_DESC_CONCISE_TYPE di un descrittore di applicazione.  
  
> [!NOTE]  
>  Non sono disponibili tipi di dati C di specifiche del driver.  
  
 Ogni tipo di dati SQL corrisponde a un tipo di dati C ODBC. Prima di restituire dati dall'origine dati, il driver converte nel tipo di dati C specificato. Prima di inviare dati all'origine dati, il driver converte il tipo di dati C specificato.  
  
 Questa appendice contiene gli argomenti seguenti.  
  
-   [Utilizzando gli identificatori di tipo di dati](../../../odbc/reference/appendixes/using-data-type-identifiers.md)  
  
-   [Tipi di dati SQL](../../../odbc/reference/appendixes/sql-data-types.md)  
  
-   [Tipi di dati C](../../../odbc/reference/appendixes/c-data-types.md)  
  
-   [Gli identificatori di tipo di dati e i descrittori](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md)  
  
-   [Identificatori di pseudo-tipo](../../../odbc/reference/appendixes/pseudo-type-identifiers.md)  
  
-   [Trasferimento dei dati in forma binaria](../../../odbc/reference/appendixes/transferring-data-in-its-binary-form.md)  
  
-   [Linee guida per l'intervallo e tipi di dati numerici](../../../odbc/reference/appendixes/guidelines-for-interval-and-numeric-data-types.md)  
  
-   [Vincoli del calendario gregoriano](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md)  
  
-   [Dimensioni della colonna, cifre decimali, trasferimento ottetto lunghezza e dimensioni di visualizzazione](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)  
  
-   [Conversione di dati da SQL a tipi di dati C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)  
  
-   [Conversione di dati c ai tipi di dati SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)  
  
 Per una spiegazione dei tipi di dati ODBC, vedere [tipi di dati ODBC](../../../odbc/reference/develop-app/data-types-in-odbc.md). Per informazioni sui tipi di dati specifici del driver SQL, vedere la documentazione del driver.

