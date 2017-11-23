---
title: Conversione di dati da SQL a tipi di dati C | Documenti Microsoft
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
- data conversions from SQL to C types [ODBC]
- data conversions from SQL to C types [ODBC], about converting
- data types [ODBC], C data types
- data types [ODBC], converting data
- data types [ODBC], SQL data types
- SQL data types [ODBC], converting to C types
- converting data from SQL to c types [ODBC]
- converting data from SQL to c types [ODBC], about converting
- C data types [ODBC], converting from SQL types
ms.assetid: 029727f6-d3f0-499a-911c-bcaf9714e43b
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0fef5a663ecbb3ec1f162dcf453691f04183d732
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="converting-data-from-sql-to-c-data-types"></a>Conversione di dati da SQL a tipi di dati C
Quando un'applicazione chiama **SQLFetch**, **SQLFetchScroll**, o **SQLGetData**, il driver recupera i dati dall'origine dati. Se necessario, ne converte i dati dal tipo di dati in cui il driver è stato recuperato al tipo di dati specificato per il *TargetType* argomento **SQLBindCol** o **SQLGetData.** Infine, archivia i dati nella posizione a cui fa riferimento il *TargetValuePtr* argomento **SQLBindCol** o **SQLGetData** (e il campo SQL_DESC_DATA_PTR del ARD).  
  
 La tabella seguente illustra le conversioni supportate da ODBC SQL nei tipi di dati per tipi di dati C ODBC. Un cerchio pieno indica la conversione del valore predefinito per un tipo di dati SQL (tipo di dati C a cui i dati verranno convertiti quando il valore di *TargetType* è SQL_C_DEFAULT). Un cerchio vuoto indica una conversione supportata.  
  
 Per un'applicazione ODBC 3*x* applicazione che utilizza un ODBC 2. *x* driver, la conversione da dati specifici del driver tipi potrebbero non essere supportati.  
  
 Il formato dei dati convertiti non è interessato dalla configurazione dell'impostazione di paese Windows®.  
  
 Le tabelle riportate nelle sezioni seguenti descrivono come il driver o l'origine di dati converte i dati recuperati dall'origine dati; per supportare le conversioni a tutti i tipi di dati C ODBC dai tipi di dati SQL ODBC che supportano sono necessari i driver. Per un determinato tipo di dati SQL ODBC, la prima colonna della tabella sono elencati i valori di input validi del *TargetType* argomento **SQLBindCol** e **SQLGetData**. La seconda colonna sono elencati i risultati di un test, utilizzando spesso il *BufferLength* argomento specificato **SQLBindCol** o **SQLGetData**, che il driver esegue in determinare se può convertire i dati. Per ogni risultato, le colonne il terza e quarta elencano i valori inseriti nel buffer specificato per il *TargetValuePtr* e *StrLen_or_IndPtr* gli argomenti specificati nella **SQLBindCol** o **SQLGetData** dopo che il driver ha tentato di convertire i dati. (Il *StrLen_or_IndPtr* argomento corrisponde al campo SQL_DESC_OCTET_LENGTH_PTR del ARD.) L'ultima colonna elenca il valore SQLSTATE restituito per ogni risultato da **SQLFetch**, **SQLFetchScroll**, o **SQLGetData**.  
  
 Se il *TargetType* argomento **SQLBindCol** o **SQLGetData** contiene un identificatore per un tipo di dati C ODBC non illustrato nella tabella per un determinato tipo di dati SQL ODBC,  **SQLFetch**, **SQLFetchScroll**, o **SQLGetData** restituisce SQLSTATE 07006 (violazione dell'attributo del tipo di dati). Se il *TargetType* argomento contiene un identificatore che specifica una conversione da un tipo di dati specifici del driver SQL a un tipo di dati ODBC C e questa conversione non è supportata dal driver, **SQLFetch**, **SQLFetchScroll**, o **SQLGetData** restituisce SQLSTATE HYC00 (funzionalità facoltativa non implementata).  
  
 Anche se non è visualizzata nelle tabelle, il driver restituisce SQL_NULL_DATA nel buffer specificato per il *StrLen_or_IndPtr* argomento quando il valore di dati SQL è NULL. Per una spiegazione dell'utilizzo di *StrLen_or_IndPtr* quando vengono effettuate più chiamate a recuperare i dati, vedere il [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)descrizione della funzione. Quando i dati SQL vengono convertiti in dati di tipo carattere C, il numero di caratteri restituiti in \* *StrLen_or_IndPtr* non include il byte di terminazione null. Se *TargetValuePtr* è un puntatore null, **SQLGetData** restituisce SQLSTATE HY009 (utilizzo non valido del puntatore null), in **SQLBindCol**, questa operazione Annulla la colonna.  
  
 Nelle tabelle vengono utilizzate i termini e le convenzioni seguenti:  
  
-   **Lunghezza in byte dei dati** è il numero di byte di dati C disponibili da restituire **TargetValuePtr*, i dati verranno troncati prima che venga restituito all'applicazione o meno. Per i dati stringa, non include lo spazio per il carattere di terminazione null.  
  
-   **Lunghezza in byte di caratteri** è il numero totale di byte necessari per visualizzare i dati in formato carattere. Si tratta come definito per ogni tipo di dati C nella sezione [visualizzare dimensioni](../../../odbc/reference/appendixes/display-size.md), ad eccezione del fatto che lunghezza in byte di caratteri è espresso in byte, mentre le dimensioni di visualizzazione sono espresso in caratteri.  
  
-   Le parole *corsivo* rappresentano gli argomenti di funzione o gli elementi della grammatica SQL. Per la sintassi di elementi di sintassi, vedere [grammatica SQL di appendice c:](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Da SQL a C: carattere](../../../odbc/reference/appendixes/sql-to-c-character.md)  
  
-   [Da SQL a C: dati numerici](../../../odbc/reference/appendixes/sql-to-c-numeric.md)  
  
-   [Da SQL a C: bit](../../../odbc/reference/appendixes/sql-to-c-bit.md)  
  
-   [Da SQL a C: dati binari](../../../odbc/reference/appendixes/sql-to-c-binary.md)  
  
-   [Da SQL a C: data](../../../odbc/reference/appendixes/sql-to-c-date.md)  
  
-   [Da SQL a C: GUID](../../../odbc/reference/appendixes/sql-to-c-guid.md)  
  
-   [Da SQL a C: ora](../../../odbc/reference/appendixes/sql-to-c-time.md)  
  
-   [Da SQL a C: timestamp](../../../odbc/reference/appendixes/sql-to-c-timestamp.md)  
  
-   [Da SQL a C: intervalli anno-mese](../../../odbc/reference/appendixes/sql-to-c-year-month-intervals.md)  
  
-   [Da SQL a C: intervalli di tempo](../../../odbc/reference/appendixes/sql-to-c-day-time-intervals.md)  
  
-   [Esempi di conversione di dati da SQL a C](../../../odbc/reference/appendixes/sql-to-c-data-conversion-examples.md)
