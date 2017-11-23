---
title: Funzione SQLDescribeCol | Documenti Microsoft
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
apiname: SQLDescribeCol
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLDescribeCol
helpviewer_keywords: SQLDescribeCol function [ODBC]
ms.assetid: eddef353-83f3-4a3c-8f24-f9ed888890a4
caps.latest.revision: "35"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 778b301cad67e6cfaf6205b65a67026ed109eae0
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="sqldescribecol-function"></a>Funzione SQLDescribeCol 
**Conformità**  
 Introdotta: versione ODBC standard 1.0 conformità: 92 ISO  
  
 **Riepilogo**  
 **SQLDescribeCol** restituisce il descrittore del risultato, il nome di colonna, tipo, dimensioni della colonna, cifre decimali e supporto di valori null, per una colonna nel risultato impostato. Queste informazioni sono anche disponibili nei campi di implementazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLDescribeCol(  
      SQLHSTMT       StatementHandle,  
      SQLUSMALLINT   ColumnNumber,  
      SQLCHAR *      ColumnName,  
      SQLSMALLINT    BufferLength,  
      SQLSMALLINT *  NameLengthPtr,  
      SQLSMALLINT *  DataTypePtr,  
      SQLULEN *      ColumnSizePtr,  
      SQLSMALLINT *  DecimalDigitsPtr,  
      SQLSMALLINT *  NullablePtr);  
```  
  
## <a name="arguments"></a>Argomenti  
 *StatementHandle*  
 [Input] Handle di istruzione.  
  
 *ColumnNumber*  
 [Input] Numero di colonna di dati del risultato, ordinati in sequenza in ordine crescente di colonna, a partire da 1. Il *ColumnNumber* argomento può inoltre essere impostato su 0 per descrivere la colonna del segnalibro.  
  
 *Nome colonna*  
 [Output] Puntatore a un buffer con terminazione null in cui restituire il nome della colonna. Questo valore viene letto dal campo SQL_DESC_NAME di implementazione. Se la colonna è senza nome o non è possibile determinare il nome della colonna, il driver restituisce una stringa vuota.  
  
 Se *ColumnName* è NULL, *NameLengthPtr* continuerà a restituire il numero totale di caratteri (escluso il carattere di terminazione null per i dati di tipo carattere) disponibile da restituire nel buffer a cui fa riferimento *ColumnName*.  
  
 *BufferLength*  
 [Input] Lunghezza di **ColumnName* buffer, in caratteri.  
  
 *NameLengthPtr*  
 [Output] Puntatore a un buffer in cui restituire il numero totale di caratteri (esclusa la terminazione null) disponibile per restituire \* *ColumnName*. Se il numero di caratteri disponibili da restituire è maggiore o uguale a *BufferLength*, il nome della colonna in \* *ColumnName* viene troncato a *BufferLength*meno la lunghezza di un carattere di terminazione null.  
  
 *DataTypePtr*  
 [Output] Puntatore a un buffer in cui restituire il tipo di dati SQL della colonna. Questo valore viene letto dal campo SQL_DESC_CONCISE_TYPE di implementazione. Questo sarà uno dei valori in [tipi di dati SQL](../../../odbc/reference/appendixes/sql-data-types.md), o un tipo di dati specifici del driver SQL. Se non è possibile determinare il tipo di dati, il driver restituisce SQL_UNKNOWN_TYPE.  
  
 In ODBC 3. *x*, viene restituito SQL_TYPE_DATE, SQL_TYPE_TIME e SQL_TYPE_TIMESTAMP in  *\*DataTypePtr* per data, ora o dati di tipo timestamp, rispettivamente; in ODBC 2. *x*, SQL_DATE, SQL_TIME o SQL_TIMESTAMP viene restituito. Gestione Driver esegue il mapping richiesto quando un ODBC 2. *x* applicazione funziona con un'applicazione ODBC 3. *x* driver o quando un'applicazione ODBC 3. *x* applicazione sta utilizzando un'API ODBC 2. *x* driver.  
  
 Quando *ColumnNumber* è uguale a 0 (per una colonna del segnalibro), viene restituito SQL_BINARY in  *\*DataTypePtr* per i segnalibri a lunghezza variabile. (SQL_INTEGER viene restituito se i segnalibri vengono utilizzati da un'applicazione ODBC 3. *x* applicazione che utilizza un ODBC 2. *x* driver o da un ODBC 2. *x* applicazione che utilizza un'applicazione ODBC 3. *x* driver.)  
  
 Per ulteriori informazioni su questi tipi di dati, vedere [tipi di dati SQL](../../../odbc/reference/appendixes/sql-data-types.md) appendice d: tipo di dati. Per informazioni sui tipi di dati specifici del driver SQL, vedere la documentazione del driver.  
  
 *ColumnSizePtr*  
 [Output] Puntatore a un buffer in cui si desidera restituire le dimensioni (in caratteri) della colonna nell'origine dati. Se non è possibile determinare le dimensioni della colonna, il driver restituisce 0. Per ulteriori informazioni sulle dimensioni di colonna, vedere [dimensioni di colonna, cifre decimali, trasferimento ottetto lunghezza e dimensioni di visualizzazione](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) appendice d: tipo di dati.  
  
 *DecimalDigitsPtr*  
 [Output] Puntatore a un buffer in cui restituire il numero di cifre decimali della colonna nell'origine dati. Se il numero di cifre decimali non può essere determinato o non è applicabile, il driver restituisce 0. Per ulteriori informazioni su cifre decimali, vedere [dimensioni di colonna, cifre decimali, trasferimento ottetto lunghezza e dimensioni di visualizzazione](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) appendice d: tipo di dati.  
  
 *NullablePtr*  
 [Output] Puntatore a un buffer in cui si desidera restituire un valore che indica se la colonna ammette valori NULL. Questo valore viene letto dal campo SQL_DESC_NULLABLE di implementazione. I possibili valori sono i seguenti:  
  
 SQL_NO_NULLS: La colonna non ammette valori NULL.  
  
 SQL_NULLABLE: La colonna ammette valori NULL.  
  
 SQL_NULLABLE_UNKNOWN: Il driver non è possibile determinare se la colonna ammette valori NULL.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLDescribeCol** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato può essere ottenuto chiamando **SQLGetDiagRec** con un *HandleType*impostato su SQL_HANDLE_STMT e *gestire* di *StatementHandle*. Nella tabella seguente sono elencati i valori SQLSTATE comunemente restituiti da **SQLDescribeCol** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01004|Stringa di dati corretto troncato|Il buffer \* *ColumnName* non sia abbastanza grande per restituire il nome della colonna intera, pertanto il nome della colonna è stato troncato. Viene restituita la lunghezza del nome della colonna non troncato **NameLengthPtr*. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|07005|Istruzione preparata non un *specifica di cursore.*|L'istruzione associata la *StatementHandle* non ha restituito un set di risultati. Si sono verificati non le colonne per descrivere.|  
|07009|Indice del descrittore non valido|(DM) il valore specificato per l'argomento *ColumnNumber* sia uguale a 0 e l'opzione dell'istruzione SQL_ATTR_USE_BOOKMARKS è SQL_UB_OFF.<br /><br /> Il valore specificato per l'argomento *ColumnNumber* è maggiore del numero di colonne nel set di risultati.|  
|08S01|Errore del collegamento di comunicazione|Collegamento di comunicazione tra il driver e l'origine dati a cui era connesso il driver non è stato possibile prima dell'elaborazione della funzione è stata completata.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel  *\*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione di memoria|Il driver è stato in grado di allocare la memoria necessaria per supportare l'esecuzione o il completamento della funzione.|  
|HY008|Operazione annullata|L'elaborazione asincrona è stata abilitata per il *StatementHandle*. La funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle*. Quindi la funzione è stata chiamata nuovamente sul *StatementHandle*.<br /><br /> La funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle* da un thread diverso in un applicazioni multithread.|  
|HY010|Errore nella sequenza (funzione)|(DM) a cui è stata chiamata per l'handle di connessione associata a una funzione in modo asincrono in esecuzione il *StatementHandle*. Questa funzione asincrona era ancora in esecuzione quando **SQLDescribeCol** è stato chiamato.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** è stato chiamato per il *StatementHandle* e restituito SQL_PARAM_DATA_ È DISPONIBILE. Questa funzione è stata chiamata prima che i dati sono stati recuperati per tutti i parametri con flusso.<br /><br /> (DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione (non è presente uno) di *StatementHandle* ed era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) a cui è stata chiamata prima di chiamare la funzione **SQLPrepare**, **SQLExecute**, o una funzione di catalogo nell'handle di istruzione.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos** è stato chiamato per il  *StatementHandle* e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima che sono stati inviati dati per tutti i parametri data-at-execution o colonne.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY090|Lunghezza di stringa o di buffer non valida|(DM) il valore specificato per l'argomento *BufferLength* era minore di 0.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|Il driver (DM) associato il *StatementHandle* non supporta la funzione.|  
|IM017|Polling è disabilitato in modalità di notifica asincrona|Ogni volta che viene utilizzato il modello di notifica, il polling è disabilitato.|  
|IM018|**SQLCompleteAsync** non è stato chiamato per completare l'operazione asincrona precedente su questo handle.|Se la chiamata di funzione precedente dell'handle restituisce SQL_STILL_EXECUTING e se è abilitata la modalità di notifica, **SQLCompleteAsync** deve essere chiamato per l'handle per eseguire la post-elaborazione e completare l'operazione.|  
  
 **SQLDescribeCol** può restituire qualsiasi SQLSTATE che può essere restituiti da **SQLPrepare** o **SQLExecute** quando viene chiamato dopo **SQLPrepare** e prima  **SQLExecute**, a seconda di quando l'origine dati restituisce l'istruzione SQL associata all'handle di istruzione.  
  
 Per motivi di prestazioni, un'applicazione non deve chiamare **SQLDescribeCol** prima di eseguire un'istruzione.  
  
## <a name="comments"></a>Commenti  
 Un'applicazione chiama in genere **SQLDescribeCol** dopo una chiamata a **SQLPrepare** e prima o dopo la chiamata a associata **SQLExecute**. Un'applicazione può anche chiamare **SQLDescribeCol** dopo una chiamata a **SQLExecDirect**. Per ulteriori informazioni, vedere [metadati dei Set di risultati](../../../odbc/reference/develop-app/result-set-metadata.md).  
  
 **SQLDescribeCol** recupera il nome della colonna, tipo e lunghezza generati da un **selezionare** istruzione. Se la colonna è un'espressione, **ColumnName* è una stringa vuota o un nome definito dal driver.  
  
> [!NOTE]  
>  ODBC supporta SQL_NULLABLE_UNKNOWN come estensione, anche se la specifica Open Group e gruppo di accesso SQL Call livello Interface viene specificata l'opzione per **SQLDescribeCol**.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Associazione di un buffer a una colonna in un set di risultati|[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|L'elaborazione di istruzione di annullamento|[SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Restituzione di informazioni su una colonna in un set di risultati|[SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|  
|Recupero di più righe di dati|[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Restituzione del numero di risultati le colonne del set|[SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|Preparazione di un'istruzione per l'esecuzione|[SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
