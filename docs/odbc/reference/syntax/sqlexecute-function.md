---
title: Funzione SQLExecute | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLExecute
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLExecute
helpviewer_keywords:
- SQLExecute function [ODBC]
ms.assetid: 9286a01d-cde2-4b90-af94-9fd7f8da48bf
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e7a64d4e3cf265b8a53fc975b33e908bb2eb9248
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32922981"
---
# <a name="sqlexecute-function"></a>Funzione SQLExecute
**Conformità**  
 Introdotta: versione ODBC standard 1.0 conformità: 92 ISO  
  
 **Riepilogo**  
 **SQLExecute** esegue un'istruzione preparata, utilizzando i valori correnti delle variabili di marcatore di parametro in presenza di altri eventuali marcatori di parametro nell'istruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLExecute(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>Argomenti  
 *StatementHandle*  
 [Input] Handle di istruzione.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_STILL_EXECUTING, SQL_ERROR, SQL_NO_DATA, SQL_INVALID_HANDLE o SQL_PARAM_DATA_AVAILABLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLExecute** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato può essere ottenuto chiamando **SQLGetDiagRec** con un *HandleType* di Impostato su SQL_HANDLE_STMT e *gestire* di *StatementHandle*. Nella tabella seguente sono elencati i valori SQLSTATE comunemente restituiti da **SQLExecute** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01001|Conflitto dell'operazione del cursore|L'istruzione preparata associata la *StatementHandle* indipendente un posizionato istruzioni update o delete e senza righe o più di una riga sono stati aggiornati o eliminati. (Per ulteriori informazioni sugli aggiornamenti per più di una riga, vedere la descrizione del SQL_ATTR_SIMULATE_CURSOR *attributo* in **SQLSetStmtAttr**.)<br /><br /> (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01003|Valore NULL eliminato nella funzione sui set|L'istruzione preparata associata *StatementHandle* è contenuta una funzione set (ad esempio **AVG**, **MAX**, **MIN**e così via), ma non il **conteggio** set (funzione) e l'argomento NULL i valori sono stati eliminati prima è stata applicata la funzione. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01004|Stringa di dati corretto troncato|Stringa o dati binari restituiti per un parametro di output ha restituito il troncamento di un carattere non vuoto o dati binari non NULL. Se si trattasse di un valore stringa, è stato troncato a destra. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01006|Privilegio non revocato.|L'istruzione preparata associata la *StatementHandle* è stato un **revocare** istruzione e l'utente non conteneva il privilegio specificato. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01007|Privilegio non concesso.|L'istruzione preparata associata la *StatementHandle* è stato un **GRANT** istruzione e l'utente non è stato possibile concedere il privilegio specificato.|  
|01S02|Valore di opzione modificato|Un attributo di istruzione specificata non è valido a causa di condizioni di lavoro di implementazione, in modo temporaneamente con cui sostituire un valore analogo. (**SQLGetStmtAttr** può essere chiamato per determinare il valore di sostituzione temporaneamente.) Il valore di sostituzione è valido per il *StatementHandle* fino a quando il cursore è chiuso, a quel punto l'attributo di istruzione viene ripristinato il valore precedente. Gli attributi di istruzione che può essere modificato: SQL_ATTR_CONCURRENCY SQL_ATTR_CURSOR_TYPE, SQL_ATTR_KEYSET_SIZE, SQL_ATTR_MAX_LENGTH, SQL_ATTR_MAX_ROWS, SQL_ATTR_QUERY_TIMEOUT e SQL_ATTR_SIMULATE_CURSOR. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01S07|Troncamento frazionario.|I dati restituiti per un input/output o parametro di output sono stato troncato in modo che la parte frazionaria di un tipo di dati numerici sono stata troncata o la parte frazionaria del componente di un tipo di dati di ora, timestamp o intervallo di tempo è stata troncata.<br /><br /> (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|07002|Campo COUNT non corretto|Il numero di parametri specificati in **SQLBindParameter** è inferiore al numero di parametri nell'istruzione SQL nel \* *StatementText*.<br /><br /> **SQLBindParameter** è stato chiamato con *ParameterValuePtr* impostato su un puntatore null *StrLen_or_IndPtr* non è impostata su SQL_NULL_DATA o SQL_DATA_AT_EXEC, e *InputOutputType*  non è impostata su SQL_PARAM_OUTPUT, in modo che il numero di parametri specificato in **SQLBindParameter** era maggiore del numero di parametri nell'istruzione SQL contenuti in **StatementText* .|  
|07006|Violazione dell'attributo del tipo di dati|Il valore di dati identificato dal *ValueType* argomento **SQLBindParameter** per non è possibile convertire il parametro associato al tipo di dati identificato dal *ParameterType*argomento **SQLBindParameter**.<br /><br /> Il valore di dati restituito per un parametro di associazione come SQL_PARAM_INPUT_OUTPUT o SQL_PARAM_OUTPUT Impossibile convertire nel tipo di dati identificato dal *ValueType* argomento **SQLBindParameter**.<br /><br /> (Se non è stato convertire i valori dei dati per una o più righe ma una o più righe sono state restituite correttamente, Microsoft questa funzione restituisce SQL_SUCCESS_WITH_INFO.)|  
|07007|Violazione di valore di parametro con restrizioni|Il tipo di parametro SQL_PARAM_INPUT_OUTPUT_STREAM viene utilizzato solo per un parametro che invia e riceve i dati in parti. Un buffer di input associato non è consentito per questo tipo di parametro.<br /><br /> Questo errore si verifica quando il tipo di parametro è SQL_PARAM_INPUT_OUTPUT e quando il \* *StrLen_or_IndPtr* specificato in **SQLBindParameter** non è uguale a SQL_NULL_DATA, SQL_DEFAULT_ PARAM SQL_LEN_DATA_AT_EXEC(len) o SQL_DATA_AT_EXEC.|  
|07S01|Utilizzo non valido del parametro predefinito|Impostare un valore di parametro con **SQLBindParameter**stato SQL_DEFAULT_PARAM e il parametro corrispondente non è un parametro per una chiamata di procedura canonica ODBC.|  
|08S01|Errore del collegamento di comunicazione|Collegamento di comunicazione tra il driver e l'origine dati a cui era connesso il driver non è stato possibile prima dell'elaborazione della funzione è stata completata.|  
|21S02|Il grado della tabella derivata non corrisponde all'elenco di colonne|L'istruzione preparata associata la *StatementHandle* contenuti un **CREATE VIEW** istruzione e l'elenco di colonna non qualificati (il numero di colonne specificato per la visualizzazione nel  *Identificatore della colonna* argomenti dell'istruzione SQL) contenuti più nomi rispetto al numero di colonne della tabella derivata definito dal *specifica di query* argomento dell'istruzione SQL.|  
|22001|Stringa di dati, troncamento a destra|Il troncamento di byte, non vuoto (carattere) o non null caratteri (binari) ha restituito l'assegnazione di un carattere o un valore binario a una colonna.|  
|22002|Variabile indicatore necessaria ma non fornito|Dati NULL è stati associati a un parametro di output il cui *StrLen_or_IndPtr* impostazione **SQLBindParameter** era un puntatore null.|  
|22003|Valore numerico non compreso nell'intervallo|L'istruzione preparata associata la *StatementHandle* contenuti di un parametro numerico associato e il valore del parametro ha causato la parte intera (in contrapposizione frazionari) del numero da troncare quando assegnato alla proprietà associata colonna di tabella.<br /><br /> Restituisce un valore numerico (come valore numerico o stringa) per uno o più parametri di input/output o di output avrebbe causato la parte intera (in contrapposizione frazionari) del numero da troncare.|  
|22007|Formato di datetime non valido|L'istruzione preparata associata la *StatementHandle* conteneva un'istruzione SQL contenente una data, ora o la struttura di timestamp come un parametro di associazione e il parametro è, rispettivamente una data non valida, il tempo, o timestamp.<br /><br /> Un parametro di input/output o di output è stato associato a una data, ora o struttura di timestamp C, e un valore nel parametro restituito è, rispettivamente, una data non valida, il tempo o timestamp. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|22008|Overflow del campo DateTime|L'istruzione preparata associata la *StatementHandle* indipendente di un'istruzione SQL contenente un'espressione datetime che, quando calcolata, dà come risultato una data, ora o timestamp struttura che non è valida.<br /><br /> Un'espressione datetime calcolata per un input/output o parametro di output ha restituito una data, ora o struttura di timestamp C che non è valido.|  
|22012|Divisione per zero|L'istruzione preparata associata la *StatementHandle* contenuto in un'espressione aritmetica che ha causato la divisione per zero.<br /><br /> Un'espressione aritmetica calcolato per un input/output o un parametro di output ha comportato la divisione per zero.|  
|22015|Overflow del campo intervallo|*\*StatementText* contiene un parametro numerico o intervallo esatto che, quando convertito in un intervallo di tipo di dati SQL, ha causato una perdita di cifre significative.<br /><br /> *\*StatementText* contiene un parametro di intervallo con più di un campo che, quando convertito in un tipo di dati numerici in una colonna, non era alcuna rappresentazione nel tipo di dati numerici.<br /><br /> *\*StatementText* contiene dati di parametro che è stati assegnati a un intervallo di tipo SQL, e si è verificato alcuna rappresentazione del valore di tipo C nell'intervallo di tipo SQL.<br /><br /> Assegnazione di un parametro di input/output o di output che è stato un numerico esatto o l'intervallo di tipo SQL a un tipo di intervallo C ha causato una perdita di cifre significative.<br /><br /> Quando un parametro di input/output o di output è stato assegnato a una struttura di intervallo C, si è verificato alcun rappresentazione dei dati nella struttura di dati di intervallo.|  
|22018|Valore di carattere non valido per la specifica del cast|*\*StatementText* includeva un tipo C che sia un numerico esatto o approssimativo, un valore datetime o un tipo di dati di intervallo; il tipo SQL della colonna è un tipo di dati character; e il valore nella colonna non è un valore letterale valido del tipo C associato.<br /><br /> Quando è stato restituito un parametro di input/output o di output, il tipo SQL è un numerico esatto o approssimativo, un valore datetime o un tipo di dati di intervallo. il tipo C è SQL_C_CHAR; il valore nella colonna non ha un valore letterale valido del tipo SQL associato.|  
|22019|Carattere di escape non valido|L'istruzione preparata associata *StatementHandle* contenuti un **come** predicato con un **ESCAPE** nel **dove** clausola, e la lunghezza dei seguenti caratteri escape **ESCAPE** non è uguale a 1.|  
|22025|Sequenza di escape non valido|L'istruzione preparata associata *StatementHandle* contenuti "**come** *valore di schema* **ESCAPE** *escape carattere*"nel **dove** clausola e il carattere che segue il carattere di escape nel valore del modello non corrisponde a uno di"%"o"_".|  
|23000|Violazione del vincolo di integrità|L'istruzione preparata associata la *StatementHandle* contenuti di un parametro. Il valore del parametro è NULL per una colonna definita come NOT NULL nella colonna della tabella associati, è stato fornito un valore duplicato per una colonna vincolata per contenere solo valori univoci o un altro vincolo di integrità è stato violato.|  
|24000|Stato del cursore non valido|Un cursore è posizionato in corrispondenza di *StatementHandle* da **SQLFetch** o **SQLFetchScroll**. Questo errore viene restituito da Gestione Driver se **SQLFetch** o **SQLFetchScroll** non è stato restituito SQL_NO_DATA e viene restituito dal driver se **SQLFetch** o **SQLFetchScroll** ha restituito SQL_NO_DATA.<br /><br /> Un cursore è stato aperto nel *StatementHandle*.<br /><br /> L'istruzione preparata associata la *StatementHandle* contenuti di un aggiornamento posizionato o delete statemen, t e il cursore è posizionato prima dell'inizio del set di risultati o dopo la fine del set di risultati.|  
|40001|Errore di serializzazione.|La transazione viene annullata a causa di un deadlock delle risorse con un'altra transazione.|  
|40003|Completamento delle istruzioni sconosciuto|Impossibile stabilire la connessione associata durante l'esecuzione di questa funzione e non è possibile determinare lo stato della transazione.|  
|42000|Sintassi o violazione di accesso|L'utente non dispone dell'autorizzazione per eseguire l'istruzione preparata associato il *StatementHandle*.|  
|44000|Violazione della clausola WITH CHECK OPTION|L'istruzione preparata associata *StatementHandle* contenuti un **inserire** istruzione eseguita su una tabella visualizzata o una tabella derivata dalla tabella visualizzata che è stata creata specificando **WITH CHECK OPTION**, in modo che uno o più righe interessate dal **inserire** istruzione non saranno presente nella tabella visualizzata.<br /><br /> L'istruzione preparata associata la *StatementHandle* contenuti un **aggiornamento** istruzione eseguita su una tabella visualizzata o una tabella derivata dalla tabella visualizzata che è stata creata specificando **WITH CHECK OPTION**, in modo che uno o più righe interessate dal **aggiornamento** istruzione non saranno presente nella tabella visualizzata.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel  *\*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver è stato in grado di allocare la memoria necessaria per supportare l'esecuzione o il completamento della funzione.|  
|HY008|Operazione annullata|L'elaborazione asincrona è stata abilitata per il *StatementHandle*. La funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle*. Quindi la funzione è stata chiamata nuovamente sul *StatementHandle*.<br /><br /> La funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle* da un thread diverso in un applicazioni multithread.|  
|HY010|Errore nella sequenza (funzione)|(DM) a cui è stata chiamata per l'handle di connessione associata a una funzione in modo asincrono in esecuzione il *StatementHandle*. Questa funzione asincrona era ancora in esecuzione quando il **SQLExecute** funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** è stato chiamato per il *StatementHandle* e restituito SQL_PARAM_DATA_ È DISPONIBILE. Questa funzione è stata chiamata prima che i dati sono stati recuperati per tutti i parametri con flusso.<br /><br /> (DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione (non è presente uno) di *StatementHandle* ed era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos** è stato chiamato per il  *StatementHandle* e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima che sono stati inviati dati per tutti i parametri data-at-execution o colonne.<br /><br /> (DM) il *StatementHandle* non è stato preparato.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY090|Lunghezza di stringa o di buffer non valida|Impostare un valore di parametro con **SQLBindParameter**era un puntatore null e il valore di lunghezza del parametro non è 0, SQL_NULL_DATA, SQL_DATA_AT_EXEC, SQL_DEFAULT_PARAM, o minore o uguale a SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> Impostare un valore di parametro con **SQLBindParameter**, non è un puntatore null; è stato il tipo di dati C SQL_C_BINARY o SQL_C_CHAR; e il valore di lunghezza del parametro era minore di 0 ma non SQL_NTS, SQL_NULL_DATA, SQL_DEFAULT_PARAM o SQL_DATA_ AT_EXEC, o minore o uguale a SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> Un valore di lunghezza del parametro associato da **SQLBindParameter** era impostato su SQL_DATA_AT_EXEC; il tipo SQL era SQL_LONGVARCHAR, SQL_LONGVARBINARY, o un tipo di dati specifici dell'origine dati di tipo long; e le informazioni di SQL_NEED_LONG_DATA_LEN digitare **SQLGetInfo** è "Y".|  
|HY105|Tipo di parametro non valido|Il valore specificato per l'argomento *InputOutputType* in **SQLBindParameter** sia SQL_PARAM_OUTPUT e il parametro è un parametro di input.|  
|HY109|Posizione del cursore non valido|L'istruzione preparata è un'istruzione delete o un aggiornamento posizionato, e il cursore era posizionato (da **SQLSetPos** o **SQLFetchScroll**) su una riga che era stata eliminata o non può essere recuperata.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Funzionalità facoltativa non implementata.|La combinazione delle impostazioni correnti degli attributi di istruzione SQL_ATTR_CONCURRENCY e SQL_ATTR_CURSOR_TYPE non era supportata dall'origine dati o driver.<br /><br /> L'attributo di istruzione SQL_ATTR_USE_BOOKMARKS è stato impostato su SQL_UB_VARIABLE e l'attributo SQL_ATTR_CURSOR_TYPE di istruzione è stato impostato su un tipo di cursore per i quali il driver non supporta i segnalibri.|  
|HYT00|Timeout|Il periodo di timeout della query è scaduto prima che l'origine dati ha restituito il set di risultati. Il periodo di timeout viene impostato tramite **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|Il driver (DM) associato il *StatementHandle* non supporta la funzione.|  
|IM017|Polling è disabilitato in modalità di notifica asincrona|Ogni volta che viene utilizzato il modello di notifica, il polling è disabilitato.|  
|IM018|**SQLCompleteAsync** non è stato chiamato per completare l'operazione asincrona precedente su questo handle.|Se la chiamata di funzione precedente dell'handle restituisce SQL_STILL_EXECUTING e se è abilitata la modalità di notifica, **SQLCompleteAsync** deve essere chiamato per l'handle per eseguire la post-elaborazione e completare l'operazione.|  
  
 **SQLExecute** può restituire qualsiasi SQLSTATE che può essere restituiti da **SQLPrepare**, in base a quando l'origine dati restituisce l'istruzione SQL associata all'istruzione.  
  
## <a name="comments"></a>Commenti  
 **SQLExecute** esegue un'istruzione preparata **SQLPrepare**. Dopo l'applicazione elabora o Elimina i risultati di una chiamata a **SQLExecute**, l'applicazione può chiamare **SQLExecute** con nuovi valori dei parametri. Per ulteriori informazioni sull'esecuzione preparata, vedere [esecuzione preparata](../../../odbc/reference/develop-app/prepared-execution-odbc.md).  
  
 Per eseguire un **selezionare** istruzione più volte, l'applicazione deve chiamare **SQLCloseCursor** prima di rieseguire il **selezionare** istruzione.  
  
 Se l'origine dati è in modalità di commit manuale (che richiedono può avviare le transazioni esplicite) e non è già stata avviata una transazione, il driver avvia una transazione prima di inviare l'istruzione SQL. Per ulteriori informazioni, vedere [transazioni](../../../odbc/reference/develop-app/transactions-odbc.md).  
  
 Se un'applicazione utilizza **SQLPrepare** per preparare e **SQLExecute** per inviare un **COMMIT** o **ROLLBACK** istruzione, non sarà interoperabilità tra prodotti DBMS. Per eseguire il commit o rollback della transazione, chiamare **SQLEndTran**.  
  
 Se **SQLExecute** riscontrino un parametro data-at-execution, verrà restituito SQL_NEED_DATA. L'applicazione invia i dati utilizzando **SQLParamData** e **SQLPutData**. Vedere [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md), [SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md), [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md), e [l'invio di dati Long](../../../odbc/reference/develop-app/sending-long-data.md).  
  
 Se **SQLExecute** esegue un aggiornamento con ricerca, inserimento o istruzione delete che non influiscono su tutte le righe nell'origine dati, la chiamata a **SQLExecute** restituisce SQL_NO_DATA.  
  
 Se il valore dell'attributo di istruzione SQL_ATTR_PARAMSET_SIZE è maggiore di 1 e l'istruzione SQL contiene almeno un marcatore di parametro, **SQLExecute** esegue l'istruzione SQL una volta per ogni set di valori di parametro nelle matrici a cui fa riferimento il  *\*ParameterValuePtr* argomento nelle chiamate a **SQLBindParameter**. Per ulteriori informazioni, vedere [matrici di valori di parametro](../../../odbc/reference/develop-app/arrays-of-parameter-values.md).  
  
 Se sono abilitati i segnalibri e viene eseguita una query che non supportano i segnalibri, il driver deve tentare di assegnare l'ambiente in modo che supporti i segnalibri modifica un valore di attributo e restituendo un valore SQLSTATE 01S02 (valore di opzione modificato). Se l'attributo non può essere modificato, il driver dovrebbe restituire SQLSTATE HY024 (valore di attributo non valido).  
  
> [!NOTE]  
>  Quando si utilizza il pool di connessioni, un'applicazione non deve eseguire istruzioni SQL che modificano il database o il contesto del database, ad esempio il **utilizzare** *database* istruzione in SQL Server, che modifica il catalogo utilizzato da un'origine dati.  
  
## <a name="code-example"></a>Esempio di codice  
 Vedere [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md), [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md), [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md), e [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Associazione di un buffer a una colonna in un set di risultati|[Funzione SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|L'elaborazione di istruzione di annullamento|[Funzione SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Chiusura del cursore|[Funzione SQLCloseCursor](../../../odbc/reference/syntax/sqlclosecursor-function.md)|  
|Esecuzione di un'operazione di commit o rollback|[Funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|Esecuzione di un'istruzione SQL|[Funzione SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Recupero di più righe di dati|[Funzione SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Recupero di un blocco di dati o di scorrimento di un risultato impostato|[Funzione SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Liberare un handle di istruzione|[Funzione SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|Restituzione di un nome di cursore|[Funzione SQLGetCursorName](../../../odbc/reference/syntax/sqlgetcursorname-function.md)|  
|Il recupero o parte di una colonna di dati|[Funzione SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|Restituisce il parametro successivo per l'invio di dati|[Funzione SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md)|  
|Preparazione di un'istruzione per l'esecuzione|[Funzione SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|L'invio di dati del parametro in fase di esecuzione|[Funzione SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|  
|Impostazione di un nome di cursore|[Funzione SQLSetCursorName](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
|L'impostazione di un attributo di istruzione|[Funzione SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
