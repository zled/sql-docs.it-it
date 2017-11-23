---
title: Conversione di dati c ai tipi di dati SQL | Documenti Microsoft
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
- converting data from c to SQL types [ODBC], about converting
- converting data from c to SQL types [ODBC]
- data conversions from C to SQL types [ODBC], about converting
- data types [ODBC], C data types
- data types [ODBC], converting data
- SQL data types [ODBC], converting from C types
- data types [ODBC], SQL data types
- data conversions from C to SQL types [ODBC]
- C data types [ODBC], converting to SQL types
ms.assetid: ee0afe78-b58f-4d34-ad9b-616bb23653bd
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9d3f3edee7f90920ad1d3ff68ccf3057a248b3b6
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="converting-data-from-c-to-sql-data-types"></a>Conversione di dati c ai tipi di dati SQL
Quando un'applicazione chiama **SQLExecute** o **SQLExecDirect**, il driver recupera i dati per tutti i parametri associati con **SQLBindParameter** da posizioni di archiviazione in l'applicazione. Quando un'applicazione chiama **SQLSetPos**, il driver recupera i dati per un aggiornamento o l'operazione di aggiunta di colonne associate a **SQLBindCol**. Per i parametri data-at-execution, l'applicazione invia i dati del parametro con **SQLPutData**. Se necessario, il driver converte i dati dal tipo di dati specificato per il *ValueType* argomento in **SQLBindParameter** al tipo di dati specificato dal *ParameterType*argomento **SQLBindParameter**e quindi invia i dati all'origine dati.  
  
 La tabella seguente illustra le conversioni supportate da ODBC C i tipi di dati per i tipi di dati SQL ODBC. Un cerchio pieno indica la conversione del valore predefinito per un tipo di dati SQL (tipo di dati C da cui verranno convertiti i dati quando il valore di *ValueType* o il campo di descrizione SQL_DESC_CONCISE_TYPE è SQL_C_DEFAULT). Un cerchio vuoto indica una conversione supportata.  
  
 Il formato dei dati convertiti non è interessato dalla configurazione dell'impostazione di paese Windows®.  
  
 ![Conversioni supportate: ODBC C a tipi di dati SQL](../../../odbc/reference/appendixes/media/apd1b.gif "apd1b")  
  
 Le tabelle riportate nelle sezioni seguenti descrivono come il driver o l'origine dati converte i dati inviati a origine dati. per supportare le conversioni da tutti i tipi di dati C ODBC per i tipi di dati SQL ODBC che supportano sono necessari i driver. Per un determinato tipo di dati ODBC C, la prima colonna della tabella sono elencati i valori di input validi del *ParameterType* argomento **SQLBindParameter**. La seconda colonna sono elencati i risultati di un test che esegue il driver per determinare se può convertire i dati. La terza colonna indica il valore SQLSTATE restituito per ogni risultato da **SQLExecDirect**, **SQLExecute**, **SQLBulkOperations**, **SQLSetPos**, o **SQLPutData**. Dati viene inviati all'origine dati solo se viene restituito SQL_SUCCESS.  
  
 Se il *ParameterType* argomento **SQLBindParameter** contiene l'identificatore di un tipo di dati ODBC SQL che non viene visualizzato nella tabella per un determinato tipo di dati C, **SQLBindParameter**restituisce SQLSTATE 07006 (violazione dell'attributo del tipo di dati). Se il *ParameterType* argomento contiene un identificatore specifico del driver e il driver non supporta la conversione dal tipo di dati ODBC C specifico di tale tipo di dati specifici del driver SQL **SQLBindParameter** restituisce SQLSTATE HYC00 (funzionalità facoltativa non implementata).  
  
 Se il *ParameterValuePtr* e *StrLen_or_IndPtr* gli argomenti specificati nella **SQLBindParameter** sono entrambi puntatori null, che restituisce SQLSTATE HY009 (non valido utilizzo del puntatore null). Anche se non è visualizzata nelle tabelle, un'applicazione imposta il valore del buffer di lunghezza/indicatore a cui fa riferimento il *StrLen_or_IndPtr* argomento di **SQLBindParameter** oppure il valore della  *StrLen_or_IndPtr* argomento di **SQLPutData** su SQL_NULL_DATA per specificare un valore di dati SQL NULL. (Il *StrLen_or_IndPtr* argomento corrisponde al campo SQL_DESC_OCTET_LENGTH_PTR di APD.) L'applicazione imposta questi valori per SQL_NTS per specificare che il valore in \* *ParameterValuePtr* in **SQLBindParameter** o \* *DataPtr*in **SQLPutData** (a cui punta il campo SQL_DESC_DATA_PTR di APD) è una stringa con terminazione null.  
  
 Nelle tabelle vengono utilizzati i seguenti termini:  
  
-   **Lunghezza in byte dei dati** : numero di byte di dati SQL disponibili per l'invio all'origine dati, i dati verranno troncati prima che venga inviato all'origine dati o meno. Per i dati stringa, questo non include lo spazio per il carattere di terminazione null.  
  
-   **Lunghezza in byte colonna** : numero di byte necessari per archiviare i dati nell'origine dati.  
  
-   **Lunghezza in byte di caratteri** , ovvero il numero massimo di byte necessari per visualizzare i dati in formato carattere. Si tratta come definito per ogni tipo di dati SQL in [visualizzare dimensioni](../../../odbc/reference/appendixes/display-size.md), ma è di lunghezza in byte di caratteri in byte, mentre le dimensioni di visualizzazione in caratteri.  
  
-   **Numero di cifre** : numero di caratteri utilizzato per rappresentare un numero, incluso il segno meno, il separatore decimale e l'esponente (se necessario).  
  
-   **Parole in**   
     ***corsivo*** , gli elementi della grammatica SQL. Per la sintassi di elementi di sintassi, vedere [grammatica SQL di appendice c:](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Da C a SQL: carattere](../../../odbc/reference/appendixes/c-to-sql-character.md)  
  
-   [Da C a SQL: dati numerici](../../../odbc/reference/appendixes/c-to-sql-numeric.md)  
  
-   [Da C a SQL: bit](../../../odbc/reference/appendixes/c-to-sql-bit.md)  
  
-   [Da C a SQL: dati binari](../../../odbc/reference/appendixes/c-to-sql-binary.md)  
  
-   [Da C a SQL: data](../../../odbc/reference/appendixes/c-to-sql-date.md)  
  
-   [Da C a SQL: GUID](../../../odbc/reference/appendixes/c-to-sql-guid.md)  
  
-   [Da C a SQL: ora](../../../odbc/reference/appendixes/c-to-sql-time.md)  
  
-   [Da C a SQL: timestamp](../../../odbc/reference/appendixes/c-to-sql-timestamp.md)  
  
-   [Da C a SQL: intervalli anno-mese](../../../odbc/reference/appendixes/c-to-sql-year-month-intervals.md)  
  
-   [Da C a SQL: intervalli di tempo](../../../odbc/reference/appendixes/c-to-sql-day-time-intervals.md)  
  
-   [Esempi di conversione di dati da C a SQL](../../../odbc/reference/appendixes/c-to-sql-data-conversion-examples.md)
