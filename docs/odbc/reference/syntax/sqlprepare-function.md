---
title: Funzione SQLPrepare | Documenti Microsoft
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
ms.topic: conceptual
apiname:
- SQLPrepare
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLPrepare
helpviewer_keywords:
- SQLPrepare function [ODBC]
ms.assetid: 332e1b4b-b0ed-4e7a-aa4d-4f35f4f4476b
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cb62fff2fccf0dbb87ac7ab15784a3d2441ede9c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlprepare-function"></a>Pagina relativa alla funzione SQLPrepare
**Conformità**  
 Introdotta: versione ODBC standard 1.0 conformità: 92 ISO  
  
 **Riepilogo**  
 **SQLPrepare** prepara una stringa SQL per l'esecuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLPrepare(  
     SQLHSTMT      StatementHandle,  
     SQLCHAR *     StatementText,  
     SQLINTEGER    TextLength);  
```  
  
## <a name="arguments"></a>Argomenti  
 *StatementHandle*  
 [Input] Handle di istruzione.  
  
 *StatementText*  
 [Input] Stringa di testo SQL.  
  
 *SetFocus per effettuare*  
 [Input] Lunghezza di **StatementText* in caratteri.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLPrepare** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato possono essere ottenuti chiamando **SQLGetDiagRec** con un *HandleType* di SQL _ HANDLE_STMT e *gestire* di *StatementHandle*. Nella tabella seguente sono elencati i valori SQLSTATE comunemente restituiti da **SQLPrepare** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01S02|Valore di opzione modificato|Un attributo di istruzione specificata non è valido a causa di condizioni di lavoro di implementazione, in modo temporaneamente con cui sostituire un valore analogo. (**SQLGetStmtAttr** può essere chiamato per determinare il valore di sostituzione temporaneamente.) Il valore di sostituzione è valido per il *StatementHandle* fino a quando il cursore è chiuso. Gli attributi di istruzione che può essere modificato: SQL_ATTR_CONCURRENCY SQL_ATTR_CURSOR_TYPE SQL_ATTR_KEYSET_SIZE SQL_ATTR_MAX_LENGTH SQL_ATTR_MAX_ROWS SQL_ATTR_QUERY_TIMEOUT SQL_ATTR_SIMULATE_CURSOR<br /><br /> (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|08S01|Errore del collegamento di comunicazione|Collegamento di comunicazione tra il driver e l'origine dati a cui era connesso il driver non è stato possibile prima dell'elaborazione della funzione è stata completata.|  
|21S01|Elenco di valori delle INSERT non corrisponde all'elenco di colonne|\**StatementText* contenuti un' **inserire** istruzione e il numero di valori da inserire non corrispondeva il grado della tabella derivata.|  
|21S02|Il grado della tabella derivata non corrisponde all'elenco di colonne|\**StatementText* contenuti un **CREATE VIEW** istruzione e il numero dei nomi specificato non è lo stesso grado della tabella derivata definito dalla specifica di query.|  
|22018|Valore di carattere non valido per la specifica del cast|**StatementText* conteneva un'istruzione SQL contenente un valore letterale o un parametro e il valore è incompatibile con il tipo di dati della colonna della tabella associata.|  
|22019|Carattere di escape non valido|L'argomento *StatementText* contenuti un **come** predicato con un **ESCAPE** nel **dove** clausola e la lunghezza del carattere di escape carattere che segue **ESCAPE** non è uguale a 1.|  
|22025|Sequenza di escape non valido|L'argomento *StatementText* contenuti "**come** *valore di schema* **ESCAPE** *caratterediescape*"nel **dove** clausola e il carattere che segue il carattere di escape nel valore del criterio era"%"né"_".|  
|24000|Stato del cursore non valido|(DM) un cursore è stato aperto nel *StatementHandle*, e **SQLFetch** o **SQLFetchScroll** fosse stata chiamata.<br /><br /> Un cursore è stato aperto nel *StatementHandle*, ma **SQLFetch** o **SQLFetchScroll** non è stato chiamato.|  
|34000|Nome di cursore non valido|\**StatementText* contenuti un posizionati **eliminare** o un oggetto posizionato **aggiornamento**, e il cursore fanno riferimento l'istruzione preparata non è stato aperto.|  
|3D000|Nome catalogo non valido|Il nome del catalogo specificato in *StatementText* non è valido.|  
|3F000|Nome dello schema non valido|Il nome dello schema specificato in *StatementText* non è valido.|  
|42000|Sintassi o violazione di accesso|\**StatementText* conteneva un'istruzione SQL che non è stato preparabile o essere contenuto un errore di sintassi.<br /><br /> **StatementText* conteneva un'istruzione per il quale l'utente non dispone dei privilegi necessari.|  
|42S01|Vista o tabella di base già esistente|\**StatementText* contenuti un **CREATE TABLE** o **CREATE VIEW** istruzione e il nome della tabella o vista nome specificato esiste già.|  
|42S02|Vista o tabella di base non trovata|\**StatementText* contenuti un **DROP TABLE** o un **DROP VIEW** istruzione e la vista nome non esiste o il nome di tabella specificata.<br /><br /> \**StatementText* contenuti un' **ALTER TABLE** istruzione e il nome della tabella specificato non esiste.<br /><br /> \**StatementText* contenuti un **CREATE VIEW** istruzione e un nome della tabella o vista nome definito per la specifica di query non esiste.<br /><br /> \**StatementText* contenuti un **CREATE INDEX** istruzione e il nome della tabella specificato non esiste.<br /><br /> \**StatementText* contenuti un **GRANT** o **revocare** istruzione e la vista nome non esiste o il nome di tabella specificata.<br /><br /> \**StatementText* contenuti un **selezionare** istruzione e una vista nome non esiste o il nome di tabella specificata.<br /><br /> \**StatementText* contenuti un **eliminare**, **inserire**, o **aggiornamento** istruzione e il nome della tabella specificato non esiste.<br /><br /> \**StatementText* contenuti un **CREATE TABLE** istruzione e una tabella specificata in un vincolo (riferimento a una tabella diversa da quella creata) non esiste.|  
|42S11|Indice già esistente.|\**StatementText* contenuti un **CREATE INDEX** istruzione e il nome dell'indice specificato esiste già.|  
|42S12|Indice non trovato|\**StatementText* contenuti un **DROP INDEX** istruzione e il nome dell'indice specificato non esiste.|  
|42S21|Esiste già una colonna|\**StatementText* contenuti un' **ALTER TABLE** istruzione e la colonna specificata nel **aggiungere** clausola non è univoca o identifica una colonna esistente nella tabella di base.|  
|42S22|Colonna non trovata|\**StatementText* contenuti un **CREATE INDEX** istruzione e uno o più della colonna dei nomi specificati nell'elenco delle colonne non esisteva.<br /><br /> \**StatementText* contenuti un **GRANT** o **revocare** istruzione e un nome di colonna specificato non esiste.<br /><br /> \**StatementText* contenuti un **selezionare**, **eliminare**, **inserire**, o **aggiornamento** istruzione e un nome di colonna specificato non esiste.<br /><br /> \**StatementText* contenuti un **CREATE TABLE** istruzione e una colonna specificata in un vincolo (riferimento a una tabella diversa da quella creata) non esiste.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel  *\*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver è stato in grado di allocare la memoria necessaria per supportare l'esecuzione o il completamento della funzione.|  
|HY008|Operazione annullata|L'elaborazione asincrona è stata abilitata per il *StatementHandle*. La funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle*, e quindi è stata chiamata la funzione nuovo di *StatementHandle*.<br /><br /> La funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle* da un thread diverso in un applicazioni multithread.|  
|HY009|Utilizzo non valido del puntatore null|(DM) *StatementText* era un puntatore null.|  
|HY010|Errore nella sequenza (funzione)|(DM) a cui è stata chiamata per l'handle di connessione associata a una funzione in modo asincrono in esecuzione il *StatementHandle*. Questa funzione asincrona era ancora in esecuzione quando il **SQLPrepare** funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** è stato chiamato per il *StatementHandle* e restituito SQL_PARAM_DATA_ È DISPONIBILE. Questa funzione è stata chiamata prima che i dati sono stati recuperati per tutti i parametri con flusso.<br /><br /> (DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione (non è presente uno) di *StatementHandle* ed era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos** è stato chiamato per il  *StatementHandle* e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima che sono stati inviati dati per tutti i parametri data-at-execution o colonne.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY090|Lunghezza di stringa o di buffer non valida|(DM) l'argomento *TextLength* è minore o uguale a 0, ma non è uguale a SQL_NTS.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Funzionalità facoltativa non implementata.|L'impostazione di concorrenza non è valido per il tipo di cursore definito.<br /><br /> L'attributo di istruzione SQL_ATTR_USE_BOOKMARKS è stato impostato su SQL_UB_VARIABLE e l'attributo SQL_ATTR_CURSOR_TYPE di istruzione è stato impostato su un tipo di cursore per i quali il driver non supporta i segnalibri.|  
|HYT00|Timeout|Il periodo di timeout è scaduto prima che l'origine dati ha restituito il set di risultati. Il periodo di timeout viene impostato tramite **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|Il driver (DM) associato il *StatementHandle* non supporta la funzione.|  
|IM017|Polling è disabilitato in modalità di notifica asincrona|Ogni volta che viene utilizzato il modello di notifica, il polling è disabilitato.|  
|IM018|**SQLCompleteAsync** non è stato chiamato per completare l'operazione asincrona precedente su questo handle.|Se la chiamata di funzione precedente dell'handle restituisce SQL_STILL_EXECUTING e se è abilitata la modalità di notifica, **SQLCompleteAsync** deve essere chiamato per l'handle per eseguire la post-elaborazione e completare l'operazione.|  
  
## <a name="comments"></a>Commenti  
 L'applicazione chiama **SQLPrepare** per inviare un'istruzione SQL per l'origine dati per la preparazione. Per ulteriori informazioni sull'esecuzione preparata, vedere [esecuzione preparata](../../../odbc/reference/develop-app/prepared-execution-odbc.md). L'applicazione può includere uno o più indicatori di parametro nell'istruzione SQL. Per includere un marcatore di parametro, l'applicazione incorpora un punto interrogativo (?) nella stringa SQL in una posizione appropriata. Per informazioni sui parametri, vedere [parametri dell'istruzione](../../../odbc/reference/develop-app/statement-parameters.md).  
  
> [!NOTE]  
>  Se un'applicazione utilizza **SQLPrepare** per preparare e **SQLExecute** per inviare un **COMMIT** o **ROLLBACK** istruzione, non sarà interoperabilità tra prodotti DBMS. Per eseguire il commit o rollback della transazione, chiamare **SQLEndTran**.  
  
 Il driver è possibile modificare l'istruzione per utilizzare il formato di SQL utilizzato dall'origine dati e quindi inviarlo all'origine dati per la preparazione. In particolare, il driver modifica le sequenze di escape utilizzate per definire la sintassi SQL per determinate funzionalità. (Per una descrizione di grammatica di istruzione SQL, vedere [sequenze di Escape ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md) e [grammatica SQL di appendice c:](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md).) Per il driver, un handle di istruzione è simile a un identificatore di istruzione nel codice SQL incorporato. Se l'origine dati supporta gli identificatori di istruzione, il driver può inviare un identificatore di istruzione e i valori dei parametri per l'origine dati.  
  
 Dopo un'istruzione preparata, l'applicazione utilizza l'handle di istruzione per fare riferimento all'istruzione nelle successive chiamate di funzione. L'istruzione preparata associato all'handle di istruzione può essere eseguita nuovamente chiamando **SQLExecute** fino a quando l'applicazione consente di liberare l'istruzione con una chiamata a **SQLFreeStmt** con l'opzione SQL_DROP o fino a quando non viene utilizzato l'handle di istruzione in una chiamata a **SQLPrepare**, **SQLExecDirect**, o una delle funzioni di catalogo (**SQLColumns**,  **SQLTables**e così via). Dopo l'applicazione prepara un'istruzione, può richiedere informazioni sul formato del set di risultati. Per alcune implementazioni, la chiamata **SQLDescribeCol** o **SQLDescribeParam** dopo **SQLPrepare** potrebbe non essere più efficienti chiamando la funzione dopo **SQLExecute** o **SQLExecDirect**.  
  
 Alcuni driver non è possibile restituire gli errori di sintassi o violazioni di accesso quando l'applicazione chiama **SQLPrepare**. Un driver può gestire gli errori di sintassi e violazioni di accesso, solo gli errori di sintassi o errori di sintassi né violazioni di accesso. Pertanto, un'applicazione deve essere in grado di gestire queste condizioni quando la chiamata successiva correlati, ad esempio funzioni **SQLNumResultCols**, **SQLDescribeCol**, **SQLColAttribute**, e **SQLExecute**.  
  
 A seconda delle funzionalità del driver e origine dati, informazioni sui parametri (ad esempio i tipi di dati) potrebbe essere effettuati quando viene preparata l'istruzione (se tutti i parametri sono stati associati) o quando viene eseguita (se tutti i parametri non sono stati associati). Per garantire la massima interoperabilità, un'applicazione deve annullare l'associazione di tutti i parametri applicati a un'istruzione SQL precedente prima di preparare una nuova istruzione SQL nella stessa istruzione. In questo modo gli errori a causa di precedenti informazioni sui parametri utilizzati per la nuova istruzione.  
  
> [!IMPORTANT]  
>  Commit di una transazione, in modo esplicito chiamando **SQLEndTran** o quando si lavora in modalità autocommit, può causare l'origine dati eliminare i piani di accesso per tutte le istruzioni in una connessione. Per ulteriori informazioni, vedere i tipi di informazioni SQL_CURSOR_COMMIT_BEHAVIOR e SQL_CURSOR_ROLLBACK_BEHAVIOR in [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) e [effettiva delle transazioni, cursori e delle istruzioni preparate](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md).  
  
## <a name="code-example"></a>Esempio di codice  
 Vedere [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md), [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md), e [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Allocare un handle di istruzione|[Funzione SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Associazione di un buffer a una colonna in un set di risultati|[Funzione SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Associazione di un buffer per un parametro|[Funzione SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|L'elaborazione di istruzione di annullamento|[Funzione SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Esecuzione di un'operazione di commit o rollback|[Funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|Esecuzione di un'istruzione SQL|[Funzione SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|L'esecuzione di un'istruzione SQL preparata|[Funzione SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Restituzione del numero di righe interessate da un'istruzione|[Funzione SQLRowCount](../../../odbc/reference/syntax/sqlrowcount-function.md)|  
|Impostazione di un nome di cursore|[Funzione SQLSetCursorName](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
