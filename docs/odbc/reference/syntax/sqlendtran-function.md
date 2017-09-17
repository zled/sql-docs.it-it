---
title: Funzione SQLEndTran | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLEndTran
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLEndTran
helpviewer_keywords:
- SQLEndTran function [ODBC]
ms.assetid: ff375ce1-eb50-4693-b1e6-70181a6dbf9f
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fcae4699f6effbc0e6605701560dad11acff5281
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlendtran-function"></a>SQLEndTran Function
**Conformità**  
 Introdotta: versione ODBC 3.0 aderenza: 92 ISO  
  
 **Riepilogo**  
 **SQLEndTran** richiede un'operazione di commit o rollback per tutte le operazioni attive in tutte le istruzioni associate a una connessione. **SQLEndTran** può inoltre richiedere che eseguire un'operazione di commit o rollback per tutte le connessioni associate a un ambiente.  
  
> [!NOTE]  
>  Per ulteriori informazioni su quali il Driver Manager esegue il mapping di questa funzione per quando un'applicazione ODBC 3. *x* applicazione sta utilizzando un'API ODBC 2.* x* driver, vedere [Mapping di funzioni di sostituzione per la compatibilità con le versioni precedenti di applicazioni](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLEndTran(  
     SQLSMALLINT   HandleType,  
     SQLHANDLE     Handle,  
     SQLSMALLINT   CompletionType);  
```  
  
## <a name="arguments"></a>Argomenti  
 *HandleType*  
 [Input] Identificatore del tipo di handle. Contiene un impostato su SQL_HANDLE_ENV (se *gestire* è un handle di ambiente) o impostato su SQL_HANDLE_DBC (se *gestire* è un handle di connessione).  
  
 *Handle*  
 [Input] L'handle, il tipo indicato dalla *HandleType*, che indica l'ambito della transazione. Per ulteriori informazioni, vedere "Commenti".  
  
 *CompletionType*  
 [Input] Uno dei due valori seguenti:  
  
 SQL_COMMIT SQL_ROLLBACK  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE o SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLEndTran** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato possono essere ottenuti chiamando **SQLGetDiagRec** con l'appropriato *HandleType*e *gestire*. Nella tabella seguente sono elencati i valori SQLSTATE comunemente restituiti da **SQLEndTran** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|08003|Connessione non aperta|(DM) il *HandleType* è stato impostato su SQL_HANDLE_DBC e *gestire* non è in stato connesso.|  
|08007|Errore di connessione durante la transazione|Il *HandleType* è stato impostato su SQL_HANDLE_DBC e la connessione è associato il *gestire* non riuscito durante l'esecuzione della funzione e non può essere determinato se la richiesta ** Eseguire il COMMIT** o **ROLLBACK** si è verificato prima dell'errore.|  
|25S01|Stato della transazione sconosciuto|Uno o più delle connessioni in *gestire* non è riuscito a completare la transazione con il risultato specificato e il risultato è sconosciuto.|  
|25S02|La transazione è ancora attiva|Il driver non è in grado di garantire che tutte le operazioni nella transazione globale è stato possibile completare in modo atomico e la transazione è ancora attiva.|  
|25S03|Viene eseguito il rollback della transazione|Il driver non è in grado di garantire che tutte le operazioni nella transazione globale è stato possibile completare in modo atomico e tutte le attività nella transazione attiva in *gestire* è stato eseguito il rollback.|  
|40001|Errore di serializzazione.|La transazione viene annullata a causa di un deadlock delle risorse con un'altra transazione.|  
|40002|Violazione del vincolo di integrità|Il *CompletionType* era SQL_COMMIT e il commit delle modifiche causato violazione del vincolo di integrità. Di conseguenza, la transazione viene annullata.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel * \*szMessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver è stato in grado di allocare la memoria necessaria per supportare l'esecuzione o il completamento della funzione.|  
|HY008|Operazione annullata|L'elaborazione asincrona è stata abilitata per il *ConnectionHandle*. La funzione è stata chiamata e prima di completare l'esecuzione di [SQLCancelHandle funzione](../../../odbc/reference/syntax/sqlcancelhandle-function.md) è stato chiamato sul *ConnectionHandle*. Quindi la funzione è stata chiamata nuovamente sul *ConnectionHandle*.<br /><br /> La funzione è stata chiamata e prima di completare l'esecuzione di **SQLCancelHandle** è stato chiamato sul *ConnectionHandle* da un thread diverso in un'applicazione multithread.|  
|HY010|Errore nella sequenza (funzione)|(DM) a cui è stata chiamata per un handle di istruzione associato a una funzione in modo asincrono in esecuzione il *ConnectionHandle* ed era ancora in esecuzione quando **SQLEndTran** è stato chiamato.<br /><br /> (DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione (non è presente uno) di *ConnectionHandle* ed era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos** è stato chiamato per un handle di istruzione associati il *ConnectionHandle* e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima che sono stati inviati dati per tutti i parametri data-at-execution o colonne.<br /><br /> (DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione (non è presente uno) di *gestire* con *HandleType* impostato su SQL_HANDLE_DBC ed era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** è stato chiamato per uno degli handle di istruzione associati *gestire* e SQL_PARAM_DATA_AVAILABLE restituito. Questa funzione è stata chiamata prima che i dati sono stati recuperati per tutti i parametri con flusso.|  
|HY012|Codice operativo della transazione non valido|(DM) il valore specificato per l'argomento *CompletionType* è stato né SQL_COMMIT o SQL_ROLLBACK.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY092|Identificatore di attributo/opzione non valida|(DM) il valore specificato per l'argomento *HandleType* è stato impostato su SQL_HANDLE_ENV né impostato su SQL_HANDLE_DBC.|  
|HY115|SQLEndTran non è consentita per un ambiente che contiene una connessione con abilitata l'esecuzione asincrona (funzione)|(DM) *HandleType* non può essere impostato su SQL_HANDLE_ENV se l'esecuzione asincrona delle funzioni di connessione è abilitata per una connessione nell'ambiente.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, fare riferimento alla sezione dei commenti di questo argomento.|  
|HYC00|Funzionalità facoltativa non implementata.|L'origine dati o driver non supporta il **ROLLBACK** operazione.|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|Il driver (DM) associato il *ConnectionHandle* non supporta la funzione.|  
|IM017|Polling è disabilitato in modalità di notifica asincrona|Ogni volta che viene utilizzato il modello di notifica, il polling è disabilitato.|  
|IM018|**SQLCompleteAsync** non è stato chiamato per completare l'operazione asincrona precedente su questo handle.|Se la chiamata di funzione precedente dell'handle restituisce SQL_STILL_EXECUTING e se è abilitata la modalità di notifica, **SQLCompleteAsync** deve essere chiamato per l'handle per eseguire la post-elaborazione e completare l'operazione.|  
  
## <a name="comments"></a>Commenti  
 Per un database ODBC 3. *x* driver, se *HandleType* è impostato su SQL_HANDLE_ENV e *gestire* è un handle di ambiente valido, quindi Driver Manager chiamerà **SQLEndTran**in tutti i driver associato all'ambiente. Il *gestire* argomento per la chiamata a un driver sarà l'handle di ambiente del driver. Per un database ODBC 2. *x* driver, se *HandleType* è impostato su SQL_HANDLE_ENV e *gestire* è un handle di ambiente valido e non esistono più connessioni in uno stato connesso in tale ambiente, quindi Driver Manager chiamerà **SQLTransact** nel driver una volta per ogni connessione in uno stato connesso in tale ambiente. Il *gestire* argomento in ogni chiamata sarà l'handle di connessione. In entrambi i casi, il driver tenterà di eseguire il commit o il rollback delle transazioni, a seconda del valore di *CompletionType*, in tutte le connessioni che sono in stato connesso in tale ambiente. Le connessioni che non sono attive non influenzano la transazione.  
  
> [!NOTE]  
>  **SQLEndTran** non può essere utilizzato per eseguire il commit o il rollback delle transazioni in un ambiente condiviso. SQLSTATE HY092 (identificatore di attributo/opzione non valida) verrà restituito se **SQLEndTran** viene chiamato con *gestire* impostata su entrambi l'handle di un ambiente condiviso o l'handle di una connessione su un oggetto condiviso ambiente.  
  
 Gestione Driver restituisce SQL_SUCCESS solo se riceve SQL_SUCCESS per ogni connessione. Se Gestione Driver riceve SQL_ERROR in una o più connessioni, l'applicazione restituisce SQL_ERROR, e le informazioni di diagnostica viene inserite nella struttura di dati di diagnostica dell'ambiente. Per determinare quale connessione o connessioni non riuscita durante l'operazione di commit o rollback, l'applicazione può chiamare **SQLGetDiagRec** per ogni connessione.  
  
> [!NOTE]  
>  Gestione Driver non simulare una transazione globale in tutte le connessioni e pertanto non vengono utilizzati i protocolli di commit in due fasi.  
  
 Se *CompletionType* è SQL_COMMIT, **SQLEndTran** genera una richiesta di commit di tutte le operazioni attive in qualsiasi istruzione associata a una connessione interessata. Se *CompletionType* è SQL_ROLLBACK, **SQLEndTran** emette una richiesta di rollback per tutte le operazioni attive in qualsiasi istruzione associata a una connessione interessata. Se nessuna transazione sono attiva, **SQLEndTran** restituisce SQL_SUCCESS senza alcun effetto su tutte le origini dati. Per ulteriori informazioni, vedere [Committing e rollback transazioni](../../../odbc/reference/develop-app/committing-and-rolling-back-transactions.md).  
  
 Se il driver è in modalità di commit manuale (chiamando **SQLSetConnectAttr** attributo set con il SQL_ATTR_AUTOCOMMIT su SQL_AUTOCOMMIT_OFF), una nuova transazione viene avviata in modo implicito quando un'istruzione SQL che può essere contenuta all'interno di un transazione viene eseguita sull'origine dati corrente. Per ulteriori informazioni, vedere [modalità Commit](../../../odbc/reference/develop-app/commit-mode.md).  
  
 Per determinare come le operazioni di transazione influenzano i cursori, un'applicazione chiama **SQLGetInfo** con le opzioni SQL_CURSOR_ROLLBACK_BEHAVIOR e SQL_CURSOR_COMMIT_BEHAVIOR. Per ulteriori informazioni, vedere i paragrafi seguenti e inoltre vedere [effettiva delle transazioni, cursori e delle istruzioni preparate](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md).  
  
 Se il valore SQL_CURSOR_ROLLBACK_BEHAVIOR o SQL_CURSOR_COMMIT_BEHAVIOR uguale SQL_CB_DELETE, **SQLEndTran** viene chiusa, Elimina tutti i cursori aperti in tutte le istruzioni associate alla connessione e Cancella tutti i risultati in sospeso. **SQLEndTran** lascia qualsiasi istruzione presente in uno stato (non preparato) allocato; l'applicazione, possono essere riutilizzate per le successive richieste SQL alternativa è possibile chiamare **SQLFreeStmt** o **SQLFreeHandle** con un *HandleType* impostato su SQL_HANDLE_STMT per deallocarle.  
  
 Se il valore SQL_CURSOR_ROLLBACK_BEHAVIOR o SQL_CURSOR_COMMIT_BEHAVIOR uguale SQL_CB_CLOSE, **SQLEndTran** chiude i cursori aperti vengono su tutte le istruzioni associate alla connessione. **SQLEndTran** lascia qualsiasi istruzione presente in uno stato preparato; l'applicazione può chiamare **SQLExecute** per un'istruzione associata alla connessione senza prima chiamare **SQLPrepare** .  
  
 Se il valore SQL_CURSOR_ROLLBACK_BEHAVIOR o SQL_CURSOR_COMMIT_BEHAVIOR uguale SQL_CB_PRESERVE, **SQLEndTran** non influisce sui cursori aperti associati alla connessione. I cursori rimangono in corrispondenza della riga a cui prima della chiamata a **SQLEndTran**.  
  
 Per i driver e le origini dati che supportano le transazioni, la chiamata **SQLEndTran** con SQL_COMMIT o SQL_ROLLBACK quando non è attiva alcuna transazione restituisce SQL_SUCCESS (che indica che non sono presenti operazioni per essere eseguito il commit o rollback) e non ha alcun effetto sull'origine dati.  
  
 Quando un driver in modalità autocommit, gestione Driver non chiama **SQLEndTran** nel driver. **SQLEndTran** sempre restituisce SQL_SUCCESS indipendentemente dal fatto che venga chiamato con un *CompletionType* di SQL_COMMIT o SQL_ROLLBACK.  
  
 Origini dati o i driver che non supportano le transazioni (**SQLGetInfo** *opzione* SQL_TXN_CAPABLE è SQL_TC_NONE) sono sempre in modo efficace in modalità autocommit e pertanto restituisce SQL_SUCCESS per sempre **SQLEndTran** o meno quando vengono chiamate con un *CompletionType* di SQL_COMMIT o SQL_ROLLBACK. Tali origini dati e il driver non effettivamente il rollback delle transazioni quando richiesto.  
  
## <a name="suspended-state"></a>Stato di sospensione  
 In Gestioni di Driver che sono stati rilasciati prima di Windows 7, una transazione è attiva se **SQLEndTran** restituito SQL_ERROR dal driver. Tuttavia, è possibile che la transazione era stato correttamente eseguito il commit nel server, ma il driver nel client non ha ricevuto notifica (ad esempio perché si è verificato un errore di rete). In tal modo la connessione in uno stato non valido. A partire da Windows 7, quando **SQLEndTran** restituisce SQL_ERROR, la connessione potrebbero essere in uno stato sospeso. In uno stato sospeso, è possibile chiamare le funzioni di sola lettura. Infine, l'applicazione deve chiamare **SQLDisconnect** su una connessione sospesa per rilasciare le risorse.  
  
 Se tutte le condizioni seguenti sono vere, la connessione verrà messe in uno stato sospeso:  
  
-   Il driver restituisce SQL_ERROR da **SQLEndTran**.  
  
-   Il driver è ODBC 3.8, o versione successiva.  
  
-   La versione dell'applicazione è 3.8 o successiva. o Annulla correttamente l'applicazione 2. x o 3. x ODBC ricompilata la **SQLEndTran** tramite **SQLCancelHandle**.  
  
-   Il driver non ha restituito uno dei due messaggi seguenti, che consentono di verificare che la transazione non è stata completata:  
  
    -   25S03: viene eseguito il rollback della transazione  
  
    -   40001: errore di serializzazione.  
  
    -   40002: vincolo di integrità  
  
    -   HYC00: Funzionalità facoltativa non implementata.  
  
 Se **SQLEndTran** è stato chiamato in un ambiente handle e una delle relative connessioni soddisfatte le condizioni precedenti, tutte le connessioni di connessione per lo stesso driver rimarrà in stato sospeso.  
  
 Dopo che un'applicazione chiama **SQLDisconnect** su una connessione sospesa, la connessione è utilizzabile per ristabilire la connessione a un'altra origine dati o la stessa origine dati.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Annullamento di una funzione in esecuzione in modo asincrono in un handle di connessione.|[Funzione SQLCancelHandle](../../../odbc/reference/syntax/sqlcancelhandle-function.md)|  
|Restituzione di informazioni su un'origine dati o il driver|[Funzione SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
|Liberare un handle|[Funzione SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|Liberare un handle di istruzione|[Funzione SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Esecuzione asincrona (metodo di Polling)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
