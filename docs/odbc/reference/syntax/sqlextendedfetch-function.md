---
title: Funzione SQLExtendedFetch. | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLExtendedFetch
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLExtendedFetch
helpviewer_keywords:
- SQLExtendedFetch function [ODBC]
ms.assetid: 940b5cf7-581c-4ede-8533-c67d5e9ef488
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 08611c1a798f9c25ae57d518e46d94193239ca1f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sqlextendedfetch-function"></a>Funzione SQLExtendedFetch.
**Conformità**  
 Introdotta: versione ODBC standard 1.0 conformità: deprecato  
  
 **Riepilogo**  
 **SQLExtendedFetch** recupera il set specificato di righe di dati dal set di risultati e restituisce i dati per tutte le colonne associate. Set di righe può essere specificata in una posizione assoluta o relativa o dal segnalibro.  
  
> [!NOTE]  
>  In ODBC 3*x*, **SQLExtendedFetch** è stata sostituita da **SQLFetchScroll**. ODBC 3*x* applicazioni non devono chiamare **SQLExtendedFetch**; invece di chiamare **SQLFetchScroll**. Esegue il mapping di gestione Driver **SQLFetchScroll** a **SQLExtendedFetch** quando si lavora con un ODBC 2*x* driver. ODBC 3*x* driver devono supportare **SQLExtendedFetch** se desiderano utilizzare ODBC 2*x* applicazioni che lo chiamano. Per ulteriori informazioni, vedere "Commenti" e [cursori a blocchi, i cursori scorrevoli e compatibilità con le versioni precedenti](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) nell'appendice g: Driver le linee guida per la compatibilità con le versioni precedenti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLExtendedFetch(  
      SQLHSTMT         StatementHandle,  
      SQLUSMALLINT     FetchOrientation,  
      SQLLEN           FetchOffset,  
      SQLULEN *        RowCountPtr,  
      SQLUSMALLINT *   RowStatusArray);  
```  
  
## <a name="arguments"></a>Argomenti  
 *StatementHandle*  
 [Input] Handle di istruzione.  
  
 *FetchOrientation*  
 [Input] Tipo di recupero. Queste sono le stesse *FetchOrientation* in **SQLFetchScroll**.  
  
 *FetchOffset*  
 [Input] Numero della riga da recuperare. Queste sono le stesse *FetchOffset* in **SQLFetchScroll**, con un'eccezione. Quando *FetchOrientation* è impostato su SQL_FETCH_BOOKMARK, *FetchOffset* è un segnalibro a lunghezza fissa, non un offset da un segnalibro. In altre parole, **SQLExtendedFetch** recupera il segnalibro da questo argomento, non l'attributo di istruzione SQL_ATTR_FETCH_BOOKMARK_PTR. Non supporta segnalibri a lunghezza variabile e non supporta il recupero di un set di righe a un offset specifico (diverso da 0) da un segnalibro.  
  
 *RowCountPtr*  
 [Output] Puntatore a un buffer in cui restituire il numero di righe effettivamente recuperate. Questo buffer viene utilizzato nello stesso modo del buffer specificato dall'attributo SQL_ATTR_ROWS_FETCHED_PTR istruzione. Questo buffer viene utilizzato solo **SQLExtendedFetch**. Non è usato da **SQLFetch** o **SQLFetchScroll**.  
  
 *RowStatusArray*  
 [Output] Puntatore a una matrice in cui restituire lo stato di ogni riga. Questa matrice viene utilizzata in modo che l'array specificato dall'attributo di istruzione vengono impostati SQL_ATTR_ROW_STATUS_PTR.  
  
 Tuttavia, l'indirizzo di questa matrice non è archiviato nel campo SQL_DESC_STATUS_ARRAY_PTR nell'implementazione. Inoltre, la matrice viene utilizzata solo da **SQLExtendedFetch** e da **SQLBulkOperations** con un *operazione* di SQL_ADD o **SQLSetPos**quando viene chiamato dopo **SQLExtendedFetch**. Non è usato da **SQLFetch** o **SQLFetchScroll**, e non è usato da **SQLBulkOperations** o **SQLSetPos** quando vengono chiamati dopo **SQLFetch** o **SQLFetchScroll**. Non è inoltre utilizzata quando **SQLBulkOperations** con un *operazione* di SQL_ADD viene chiamato prima di chiamare qualsiasi funzione di recupero. In altre parole, si utilizza solo nello stato istruzione S7. Non è utilizzato negli Stati istruzione S5 o S6. Per ulteriori informazioni, vedere [istruzione transizioni](../../../odbc/reference/appendixes/statement-transitions.md) in tabelle di transizione dello stato di appendice b: ODBC.  
  
 Le applicazioni devono fornire un puntatore valido nel *RowStatusArray* argomento; in caso contrario, il comportamento di **SQLExtendedFetch** e il comportamento di chiamate a **SQLBulkOperations**o **SQLSetPos** dopo che un cursore è stato posizionato da **SQLExtendedFetch** non sono definiti.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_STILL_EXECUTING, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLExtendedFetch** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato può essere ottenuto chiamando **SQLError**. Nella tabella seguente sono elencati i valori SQLSTATE comunemente restituiti da **SQLExtendedFetch** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato. Se si verifica un errore in una singola colonna, **SQLGetDiagField** può essere chiamato con un *DiagIdentifier* di SQL_DIAG_COLUMN_NUMBER per determinare la colonna a cui si è verificato l'errore; e  **SQLGetDiagField** può essere chiamato con un *DiagIdentifier* di SQL_DIAG_ROW_NUMBER per determinare la riga che contiene tale colonna.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01004|Stringa di dati corretto troncato|Stringa o dati binari restituiti per una colonna ha restituito il troncamento di un carattere non vuoto o dati binari non NULL. Se si trattasse di un valore stringa, è stato troncato a destra. Se si trattasse di un valore numerico, la parte frazionaria del numero è stata troncata.  (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01S01|Errore alla riga|Si è verificato un errore durante il recupero di una o più righe. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01S06|Tentativo di recupero eseguito prima che il set di risultati restituito il primo set di righe|Il set di righe richiesto sovrapposta l'inizio del set di risultati quando la posizione corrente è oltre la prima riga e di *FetchOrientation* stato SQL_PRIOR o *FetchOrientation* stato SQL_RELATIVE con un negativo *FetchOffset* il cui valore assoluto è minore o uguale al SQL_ROWSET_SIZE corrente. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01S07|Troncamento frazionario.|I dati restituiti per una colonna è stati troncati. Per i tipi di dati numerici, la parte frazionaria del numero è stata troncata. Per ora, timestamp e tipi di dati di intervallo contenente un componente di ora, la parte frazionaria del tempo è stata troncata.<br /><br /> (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|07006|Violazione dell'attributo del tipo di dati|Non è possibile convertire un valore di dati per il tipo di dati C specificato da *TargetType* in **SQLBindCol**.|  
|07009|Indice del descrittore non valido|Colonna 0 è stato associato al **SQLBindCol**, e l'attributo di istruzione SQL_ATTR_USE_BOOKMARKS era impostato su SQL_UB_OFF.|  
|08S01|Errore del collegamento di comunicazione|Collegamento di comunicazione tra il driver e l'origine dati a cui era connesso il driver non è stato possibile prima dell'elaborazione della funzione è stata completata.|  
|22002|Variabile indicatore necessaria ma non fornito|NULL è stata recuperati i dati in una colonna il cui *StrLen_or_IndPtr* impostazione **SQLBindCol** era un puntatore null.<br /><br /> (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|22003|Valore numerico non compreso nell'intervallo|Restituire il valore numerico (come valore numerico o stringa) per una o più colonne avrebbe causato la parte intera (in contrapposizione frazionari) del numero da troncare.<br /><br /> (Funzione restituisce SQL_SUCCESS_WITH_INFO).<br /><br /> Per ulteriori informazioni, vedere [linee guida per l'intervallo e tipi di dati numerici](../../../odbc/reference/appendixes/guidelines-for-interval-and-numeric-data-types.md) appendice d: tipo di dati.|  
|22007|Formato di datetime non valido|Una colonna di tipo carattere nel set di risultati è stata associata a una data, ora o struttura di timestamp C, e un valore nella colonna è, rispettivamente, una data non valida, il tempo o timestamp.<br /><br /> (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|22012|Divisione per zero|Da un'espressione aritmetica ha restituito un valore, ciò ha provocato la divisione per zero.<br /><br /> (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|22015|Overflow del campo intervallo|L'assegnazione da un numerico esatto o l'intervallo di tipo SQL a un tipo di intervallo C ha causato una perdita di cifre significative nel campo iniziale.<br /><br /> Durante il recupero di dati a un tipo di intervallo C, si è verificato alcun rappresentazione del valore di tipo SQL nel tipo di intervallo C.<br /><br /> (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|22018|Valore di carattere non valido per la specifica del cast|Il tipo C è stato un numerico esatto o approssimativo, un valore datetime o un tipo di dati di intervallo. il tipo SQL della colonna è un tipo di dati character; il valore nella colonna non ha un valore letterale valido del tipo C associato.<br /><br /> (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|24000|Stato del cursore non valido|Il *StatementHandle* è stato eseguito, ma è stato associato alcun set di risultati di *StatementHandle*.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLError** nel  *\*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver è stato in grado di allocare la memoria necessaria per supportare l'esecuzione o il completamento della funzione.|  
|HY008|Operazione annullata|L'elaborazione asincrona è stata abilitata per il *StatementHandle*. La funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle*, e quindi è stata chiamata la funzione nuovo di *StatementHandle*.<br /><br /> La funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle* da un thread diverso in un applicazioni multithread.|  
|HY010|Errore nella sequenza (funzione)|(DM) a cui è stata chiamata per l'handle di connessione associata a una funzione in modo asincrono in esecuzione il *StatementHandle*. Questa funzione asincrona era ancora in esecuzione quando il **SQLExtendedFetch** funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** è stato chiamato per il *StatementHandle* e restituito SQL_PARAM_DATA_ È DISPONIBILE. Questa funzione è stata chiamata prima che i dati sono stati recuperati per tutti i parametri con flusso.<br /><br /> (DM) specificato *StatementHandle* non è stato eseguito. La funzione è stata chiamata senza chiamare prima il metodo **SQLExecDirect**, **SQLExecute**, o una funzione di catalogo.<br /><br /> (DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione (non è presente uno) di *StatementHandle* ed era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos** è stato chiamato per il  *StatementHandle* e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima che sono stati inviati dati per tutti i parametri data-at-execution o colonne.<br /><br /> (DM) **SQLExtendedFetch** è stato chiamato per il *StatementHandle* dopo **SQLFetch** o **SQLFetchScroll** è stato chiamato e prima  **SQLFreeStmt** è stato chiamato con l'opzione di SQL_CLOSE.<br /><br /> (DM) **SQLBulkOperations** è stato chiamato per un'istruzione prima **SQLFetch**, **SQLFetchScroll**, o **SQLExtendedFetch** è stato chiamato e quindi **SQLExtendedFetch** è stato chiamato prima di **SQLFreeStmt** è stato chiamato con l'opzione di SQL_CLOSE.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY106|Tipo non compreso nell'intervallo di recupero|(DM) il valore specificato per l'argomento *FetchOrientation* non è valido. (Vedere "Commenti".)<br /><br /> L'argomento *FetchOrientation* è stato impostato su SQL_FETCH_BOOKMARK, e l'attributo di istruzione SQL_ATTR_USE_BOOKMARKS era impostato su SQL_UB_OFF.<br /><br /> Il valore dell'opzione di istruzione SQL_CURSOR_TYPE era SQL_CURSOR_FORWARD_ONLY e il valore dell'argomento *FetchOrientation* non SQL_FETCH_NEXT.<br /><br /> L'argomento *FetchOrientation* stato SQL_FETCH_RESUME.|  
|HY107|Valore di riga non compreso nell'intervallo|Il valore specificato con l'opzione dell'istruzione SQL_CURSOR_TYPE SQL_CURSOR_KEYSET_DRIVEN, ma non ha il valore specificato con l'attributo di istruzione SQL_KEYSET_SIZE maggiore di 0 e minore del valore specificato con l'attributo di istruzione SQL_ROWSET_SIZE .|  
|HY111|Valore del segnalibro non valido|L'argomento *FetchOrientation* è stato impostato su SQL_FETCH_BOOKMARK e il segnalibro specificato nella *FetchOffset* argomento non valido.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Funzionalità facoltativa non implementata.|Origine dati o driver non supporta il tipo di recupero specificato.<br /><br /> L'origine dati o driver non supporta la conversione specificata dalla combinazione del *TargetType* in **SQLBindCol** e il tipo di dati SQL della colonna corrispondente. Questo errore si applica solo quando il tipo di dati SQL della colonna è stato eseguito il mapping a un tipo di dati specifici del driver SQL.|  
|HYT00|Timeout|Il periodo di timeout della query è scaduto prima che l'origine dati ha restituito il set di risultati. Il periodo di timeout viene impostato tramite **SQLSetStmtOption**, SQL_QUERY_TIMEOUT.|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|Il driver (DM) associato il *StatementHandle* non supporta la funzione.|  
  
## <a name="comments"></a>Commenti  
 Il comportamento di **SQLExtendedFetch** è identico a quello di **SQLFetchScroll**, con le eccezioni seguenti:  
  
-   **SQLExtendedFetch** e **SQLFetchScroll** usare diversi metodi per restituire il numero di righe recuperate. **SQLExtendedFetch** restituisce il numero di righe recuperate nel  *\*RowCountPtr*; **SQLFetchScroll** restituisce il numero di righe recuperate direttamente al buffer a cui puntato SQL_ATTR_ROWS_FETCHED_PTR. Per ulteriori informazioni, vedere il *RowCountPtr* argomento.  
  
-   **SQLExtendedFetch** e **SQLFetchScroll** restituiscono lo stato di ogni riga in array diversi. Per ulteriori informazioni, vedere il *RowStatusArray* argomento.  
  
-   **SQLExtendedFetch** e **SQLFetchScroll** usare diversi metodi per recuperare il segnalibro quando *FetchOrientation* è impostato su SQL_FETCH_BOOKMARK. **SQLExtendedFetch** non supporta i segnalibri a lunghezza variabile o un set di righe recupero in corrispondenza di un offset diverso da 0 da un segnalibro. Per ulteriori informazioni, vedere il *FetchOffset* argomento.  
  
-   **SQLExtendedFetch** e **SQLFetchScroll** utilizza formati diversi set di righe. **SQLExtendedFetch** utilizza il valore dell'attributo di istruzione SQL_ROWSET_SIZE, e **SQLFetchScroll** utilizza il valore dell'attributo di istruzione SQL_ATTR_ROW_ARRAY_SIZE.  
  
-   **SQLExtendedFetch** ha una semantica di gestione degli errori leggermente diverso **SQLFetchScroll**. Per ulteriori informazioni, vedere "Gestione degli errori" nella sezione "Osservazioni" di [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md).  
  
-   **SQLExtendedFetch** non supporta gli offset di associazione (l'attributo dell'istruzione SQL_ATTR_ROW_BIND_OFFSET_PTR).  
  
-   Le chiamate a **SQLExtendedFetch** ReadContentAsBinHex con chiamate a **SQLFetch** o **SQLFetchScroll**e se **SQLBulkOperations** viene chiamato prima di chiamare qualsiasi funzione di recupero, **SQLExtendedFetch** non può essere chiamato finché il cursore viene chiuso e riaperto. Vale a dire **SQLExtendedFetch** può essere chiamato solo in stato di istruzione S7. Per ulteriori informazioni, vedere [istruzione transizioni](../../../odbc/reference/appendixes/statement-transitions.md) in tabelle di transizione dello stato di appendice b: ODBC.  
  
 Quando un'applicazione chiama **SQLFetchScroll** quando si utilizza un ODBC 2*x* driver, Driver Manager esegue il mapping di questa chiamata a **SQLExtendedFetch**. Per ulteriori informazioni, vedere "SQLFetchScroll e ODBC 2*x* driver" in [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md).  
  
 In ODBC 2*x*, **SQLExtendedFetch** è stato chiamato per recuperare più righe e **SQLFetch** è stata chiamata per recuperare una singola riga. In ODBC 3*x*, d'altra parte, **SQLFetch** può essere chiamato per recuperare più righe.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Associazione di un buffer a una colonna in un set di risultati|[Funzione SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Esecuzione delle operazioni bulk insert, update o le operazioni di eliminazione|[Funzione SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|L'elaborazione di istruzione di annullamento|[Funzione SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Restituzione di informazioni su una colonna in un set di risultati|[Funzione SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|Esecuzione di un'istruzione SQL|[Funzione SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|L'esecuzione di un'istruzione SQL preparata|[Funzione SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Restituzione del numero di risultati le colonne del set|[Funzione SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|Posizionando il cursore, l'aggiornamento dei dati del set di righe o l'aggiornamento o eliminazione di dati nel set di risultati|[Funzione SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
|L'impostazione di un attributo di istruzione|[Funzione SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
