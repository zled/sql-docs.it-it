---
title: Funzione SQLSetConnectAttr | Documenti Microsoft
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
apiname: SQLSetConnectAttr
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLSetConnectAttr
helpviewer_keywords: SQLSetConnectAttr function [ODBC]
ms.assetid: 97fc7445-5a66-4eb9-8e77-10990b5fd685
caps.latest.revision: "83"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: d239280ebe6eaaafaed44341354bec8a6d0b225e
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="sqlsetconnectattr-function"></a>Pagina relativa alla funzione SQLSetConnectAttr
**Conformità**  
 Introdotta: versione ODBC 3.0 aderenza: 92 ISO  
  
 **Riepilogo**  
 **La funzione SQLSetConnectAttr** imposta gli attributi che controllano gli aspetti di connessioni.  
  
> [!NOTE]  
>  Per ulteriori informazioni su cosa the Driver Manager esegue il mapping di questa funzione per quando un'applicazione ODBC 3*x* applicazione sta utilizzando un'API ODBC 2*x* driver, vedere [Mapping di funzioni di sostituzione per indietro Compatibilità delle applicazioni](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLSetConnectAttr(  
     SQLHDBC       ConnectionHandle,  
     SQLINTEGER    Attribute,  
     SQLPOINTER    ValuePtr,  
     SQLINTEGER    StringLength);  
```  
  
## <a name="arguments"></a>Argomenti  
 *ConnectionHandle*  
 [Input] Handle di connessione.  
  
 *Attribute*  
 [Input] Attributo da impostare, elencati in "Commenti".  
  
 *ValuePtr*  
 [Input] Puntatore al valore da associare a *attributo*. A seconda del valore di *attributo*, *ValuePtr* sarà un valore intero senza segno o farà riferimento a una stringa di caratteri con terminazione null. Si noti che il tipo di integrale del *attributo* argomento potrebbe non essere a lunghezza fissa, vedere la sezione commenti per i dettagli.  
  
 *StringLength*  
 [Input] Se *attributo* è un attributo basato su ODBC e *ValuePtr* punta a una stringa di caratteri o di un buffer binario, la lunghezza di questo argomento deve essere **ValuePtr*. Per i dati di stringa di caratteri, questo argomento deve contenere il numero di byte nella stringa.  
  
 Se *attributo* è un attributo basato su ODBC e *ValuePtr* è un numero intero, *StringLength* viene ignorato.  
  
 Se *attributo* è un attributo definito dal driver, l'applicazione indica la natura dell'attributo al Driver Manager impostando il *StringLength* argomento. *StringLength* può avere i valori seguenti:  
  
-   Se *ValuePtr* è un puntatore a una stringa di caratteri, quindi *StringLength* è la lunghezza della stringa o SQL_NTS.  
  
-   Se *ValuePtr* è un puntatore a un buffer binario, quindi viene visualizzato il risultato di SQL_LEN_BINARY_ATTR (*lunghezza*) (macro) in *StringLength*. In questo modo un valore negativo in *StringLength*.  
  
-   Se *ValuePtr* è un puntatore a un valore diverso da una stringa di caratteri o una stringa binaria, quindi *StringLength* deve avere il valore SQL_IS_POINTER.  
  
-   Se *ValuePtr* contiene un valore di lunghezza fissa, quindi *StringLength* è SQL_IS_INTEGER o SQL_IS_UINTEGER, come appropriato.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE o SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLSetConnectAttr** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato possono essere ottenuti chiamando **SQLGetDiagRec** con un *HandleType* di Impostato su SQL_HANDLE_DBC e *gestire* di *ConnectionHandle*. Nella tabella seguente sono elencati i valori SQLSTATE comunemente restituiti da **SQLSetConnectAttr** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
 Il driver può restituire SQL_SUCCESS_WITH_INFO per fornire informazioni sul risultato di un'opzione di configurazione.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01S02|Valore di opzione modificato|Il driver non supportava il valore specificato *ValuePtr* e sostituito con un valore analogo. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|08002|Nome della connessione in uso|Il *attributo* argomento era SQL_ATTR_ODBC_CURSORS, e il driver è stato già connesso all'origine dati.|  
|08003|Connessione non aperta|(DM) un *attributo* valore è stato specificato che necessaria una connessione aperta, ma la *ConnectionHandle* non è in stato connesso.|  
|08S01|Errore del collegamento di comunicazione|Collegamento di comunicazione tra il driver e l'origine dati a cui era connesso il driver non è stato possibile prima dell'elaborazione della funzione è stata completata.|  
|24000|Stato del cursore non valido|Il *attributo* argomento stato SQL_ATTR_CURRENT_CATALOG e un set di risultati è stato in sospeso.|  
|25000|Operazione non valida in una transazione locale|Una connessione è stato in una transazione locale durante il tentativo di eseguire l'inserimento di una connessione di transazioni distribuite (DTC) impostando l'attributo di connessione SQL_ATTR_ENLIST_IN_DTC.<br /><br /> Una connessione è già elencata in un DTC.<br /><br /> Una connessione è stata integrata in una connessione di transazione distribuita e una transazione locale avviata dall'impostazione SQL_ATTR_AUTOCOMMIT su SQL_AUTOCOMMIT_OFF.|  
|3D000|Nome catalogo non valido|Il *attributo* argomento è stato SQL_CURRENT_CATALOG e il nome del catalogo specificato non è valido.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel  *\*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver è stato in grado di allocare la memoria necessaria per supportare l'esecuzione o il completamento della funzione.|  
|HY008|Operazione annullata|L'elaborazione asincrona è stata abilitata per il *ConnectionHandle*. Il **SQLSetConnectAttr** funzione è stata chiamata e prima ha completato l'esecuzione, il [SQLCancelHandle funzione](../../../odbc/reference/syntax/sqlcancelhandle-function.md) è stato chiamato sul *ConnectionHandle*e quindi il **SQLSetConnectAttr** funzione è stata chiamata nuovamente sul *ConnectionHandle*.<br /><br /> O, **SQLSetConnectAttr** funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancelHandle** è stato chiamato sul *ConnectionHandle* da un thread diverso in un'applicazione multithread.|  
|HY009|Utilizzo non valido del puntatore null|Il *attributo* argomento identificato un attributo di connessione che hanno richiesto un valore stringa, e *ValuePtr* argomento è un puntatore null.|  
|HY010|Errore nella sequenza (funzione)|(DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione un *StatementHandle* associato il *ConnectionHandle* ed era ancora in esecuzione quando **SQLSetConnectAttr**è stato chiamato.<br /><br /> (DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione (non è presente uno) di *ConnectionHandle* ed era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** è stato chiamato per uno degli handle di istruzione associati il *ConnectionHandle* e SQL_PARAM_DATA_AVAILABLE restituito. Questa funzione è stata chiamata prima che i dati sono stati recuperati per tutti i parametri con flusso.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos** è stato chiamato per un *StatementHandle*  associato il *ConnectionHandle* e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima che sono stati inviati dati per tutti i parametri data-at-execution o colonne.<br /><br /> (DM) **SQLBrowseConnect** è stato chiamato per il *ConnectionHandle* e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima di **SQLBrowseConnect** restituito SQL_SUCCESS_WITH_INFO o SQL_SUCCESS.|  
|HY011|Impossibile impostare l'attributo ora|Il *attributo* argomento sia SQL_ATTR_TXN_ISOLATION e una transazione è aperta.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY024|Valore dell'attributo non valido|Ha specificato *attributo* valore, in cui è stato specificato un valore non valido *ValuePtr*. (The Driver Manager restituisce il valore SQLSTATE solo per la connessione e gli attributi di istruzione che accettano un set discreto di valori, ad esempio SQL_ATTR_ACCESS_MODE o SQL_ATTR_ASYNC_ENABLE. Per tutti gli altri connessione e gli attributi di istruzione, il driver deve verificare il valore specificato *ValuePtr*.)<br /><br /> Il *attributo* argomento è stato SQL_ATTR_TRACEFILE o SQL_ATTR_TRANSLATE_LIB, e *ValuePtr* è una stringa vuota.|  
|HY090|Lunghezza di stringa o di buffer non valida|*(DM) \*ValuePtr* è una stringa di caratteri e *StringLength* argomento è minore di 0 ma non è stato SQL_NTS.|  
|HY092|Identificatore di attributo/opzione non valida|(DM) il valore specificato per l'argomento *attributo* non valido per la versione di ODBC supportati dal driver.<br /><br /> (DM) il valore specificato per l'argomento *attributo* è un attributo di sola lettura.|  
|HY114|Driver non supporta l'esecuzione di funzione asincrona a livello di connessione|(DM) un'applicazione ha tentato di attivare l'esecuzione di funzione asincrona con SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE per un driver che non supporta le operazioni di connessione asincrona.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HY121|Libreria di cursori e pool compatibile con il Driver non possono essere abilitati contemporaneamente|Per ulteriori informazioni, vedere [Driver-Aware Connection Pooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md).|  
|HYC00|Funzionalità facoltativa non implementata.|Il valore specificato per l'argomento *attributo* è una connessione ODBC valida o attributo di istruzione per la versione di ODBC supportati dal driver, ma non è supportato dal driver.|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|Il driver (DM) associato il *ConnectionHandle* non supporta la funzione.|  
|IM009|Impossibile caricare la DLL di conversione|Il driver non è riuscito a caricare la DLL che è stato specificato per la connessione di traduzione. Questo errore può essere restituito solo quando *attributo* è SQL_ATTR_TRANSLATE_LIB.|  
|IM017|Polling è disabilitato in modalità di notifica asincrona|Ogni volta che viene utilizzato il modello di notifica, il polling è disabilitato.|  
|IM018|**SQLCompleteAsync** non è stato chiamato per completare l'operazione asincrona precedente su questo handle.|Se la chiamata di funzione precedente dell'handle restituisce SQL_STILL_EXECUTING e se è abilitata la modalità di notifica, **SQLCompleteAsync** deve essere chiamato per l'handle per eseguire la post-elaborazione e completare l'operazione.|  
|S1118|Driver non supporta la notifica asincrona|È stato impostato SQL_ATTR_ASYNC_DBC_EVENT (dopo che è stata effettuata la connessione) ma la notifica asincrona non è supportata dal driver.|  
  
 Quando *attributo* è un attributo di istruzione, **SQLSetConnectAttr** può restituire qualsiasi SQLSTATE restituiti da **SQLSetStmtAttr**.  
  
## <a name="comments"></a>Commenti  
 Per informazioni generali sugli attributi di connessione, vedere [gli attributi di connessione](../../../odbc/reference/develop-app/connection-attributes.md).  
  
 Vengono visualizzati gli attributi attualmente definiti e la versione di ODBC in cui sono state introdotte nella tabella più avanti in questa sezione; è previsto che verranno definiti più attributi per sfruttare i vantaggi di origini dati diverse. Un intervallo di attributi è riservato da ODBC. gli sviluppatori di driver è necessario riservare i valori per l'uso di specifici del driver da Open Group.  
  
> [!NOTE]  
>  La possibilità di impostare gli attributi di istruzione a livello di connessione chiamando **SQLSetConnectAttr** è stato deprecato in ODBC 3*x*. ODBC 3*x* applicazioni non devono mai impostata gli attributi di istruzione a livello di connessione. ODBC 3*x* gli attributi di istruzione non possono essere impostati a livello di connessione, fatta eccezione per gli attributi SQL_ATTR_METADATA_ID e SQL_ATTR_ASYNC_ENABLE, che sono entrambi gli attributi di connessione e gli attributi di istruzione e può essere impostare il livello di connessione o il livello di istruzione.  
>   
>  ODBC 3*x* driver necessitano supportano questa funzionalità solo se funzionano con ODBC 2*x* applicazione che imposta ODBC 2*x* opzioni dell'istruzione a livello di connessione. Per ulteriori informazioni, vedere [SQLSetConnectOption Mapping](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md) nell'appendice g: Driver le linee guida per la compatibilità con le versioni precedenti.  
  
 Un'applicazione può chiamare **SQLSetConnectAttr** in qualsiasi momento tra il momento in cui la connessione viene allocata e liberata. Tutti gli attributi di istruzione e connessione correttamente impostati dall'applicazione per la connessione mantenuta fino al **SQLFreeHandle** viene chiamato per la connessione. Ad esempio, se un'applicazione chiama **SQLSetConnectAttr** prima della connessione a un'origine dati, l'attributo persiste anche se **SQLSetConnectAttr** ha esito negativo nel driver quando l'applicazione si connette per la origine dati. Se un'applicazione imposta un attributo specifico del driver, l'attributo persiste anche se l'applicazione si connette a un driver diverso per la connessione.  
  
 Alcuni attributi di connessione possono essere impostate solo prima è stata stabilita una connessione; altri utenti può essere impostati solo dopo che è stata stabilita una connessione. Nella tabella seguente indica gli attributi di connessione che devono essere impostati prima o dopo che è stata stabilita una connessione. *Entrambi* indica che l'attributo può essere impostato prima o dopo la connessione.  
  
|Attribute|Impostare prima o dopo la connessione?|  
|---------------|-------------------------------------|  
|SQL_ATTR_ACCESS_MODE|[1]|  
|SQL_ATTR_ASYNC_DBC_EVENT|Prima o dopo|  
|SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE|[4]|  
|SQL_ATTR_ASYNC_DBC_PCALLBACK|Prima o dopo|  
|SQL_ATTR_ASYNC_DBC_PCONTEXT|Prima o dopo|  
|SQL_ATTR_ASYNC_ENABLE|[2]|  
|SQL_ATTR_AUTO_IPD|Prima o dopo|  
|SQL_ATTR_AUTOCOMMIT|[5]|  
|SQL_ATTR_CONNECTION_DEAD|After|  
|SQL_ATTR_CONNECTION_TIMEOUT|Prima o dopo|  
|SQL_ATTR_CURRENT_CATALOG|[1]|  
|SQL_ATTR_DBC_INFO_TOKEN|After|  
|SQL_ATTR_ENLIST_IN_DTC|After|  
|SQL_ATTR_LOGIN_TIMEOUT|Prima|  
|SQL_ATTR_METADATA_ID|Prima o dopo|  
|SQL_ATTR_ODBC_CURSORS|Prima|  
|SQL_ATTR_PACKET_SIZE|Prima|  
|SQL_ATTR_QUIET_MODE|Prima o dopo|  
|SQL_ATTR_TRACE|Prima o dopo|  
|SQL_ATTR_TRACEFILE|Prima o dopo|  
|SQL_ATTR_TRANSLATE_LIB|After|  
|SQL_ATTR_TRANSLATE_OPTION|After|  
|SQL_ATTR_TXN_ISOLATION|[3]|  
  
 [1] SQL_ATTR_ACCESS_MODE e SQL_ATTR_CURRENT_CATALOG può essere impostata prima o dopo la connessione, a seconda del driver. Tuttavia, applicazioni interoperative impostarle prima della connessione poiché alcuni driver non supporta la modifica di questi dopo la connessione.  
  
 [2] prima di un'istruzione attiva, è necessario impostare SQL_ATTR_ASYNC_ENABLE.  
  
 [3] SQL_ATTR_TXN_ISOLATION può essere impostata solo se non sono presenti transazioni aperte per la connessione. Alcuni attributi di connessione supportano la sostituzione di un valore simile, se l'origine dati non supporta il valore specificato \* *ValuePtr*. In questi casi, il driver restituisce SQL_SUCCESS_WITH_INFO e SQLSTATE 01S02 (valore di opzione modificato). Ad esempio, se *attributo* è SQL_ATTR_PACKET_SIZE e \* *ValuePtr* supera la dimensione massima del pacchetto, il driver sostituisce la dimensione massima. Per determinare il valore di sostituzione, un'applicazione chiama **SQLGetConnectAttr**.  
  
 [4] se SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE viene impostato prima che una connessione è aperta, gestione Driver imposterà l'attributo del driver quando viene caricato il driver durante una chiamata a **SQLBrowseConnect**, **SQLConnect**, o **SQLDriverConnect**. Prima di chiamare **SQLBrowseConnect**, **SQLConnect**, o **SQLDriverConnect**, gestione Driver non riconosce il driver a cui connettersi e non sa se il driver supporta le operazioni di connessione asincrona. Di conseguenza, gestione Driver restituisce sempre SQL_SUCCESS. Tuttavia, nel caso in cui il driver non supporta le operazioni di connessione asincrona, la chiamata a **SQLBrowseConnect**, **SQLConnect**, o **SQLDriverConnect** avrà esito negativo.  
  
 [5] quando SQL_ATTR_AUTOCOMMIT è impostata su FALSE, le applicazioni devono chiamare SQLEndTran(SQL_ROLLBACK) se qualsiasi API restituisce SQL_ERROR per garantire la coerenza transazionale.  
  
 Il formato delle informazioni di cui il \* *ValuePtr* buffer dipende specificato *attributo*. **La funzione SQLSetConnectAttr** accetterà informazioni sugli attributi in uno dei due formati: una stringa di caratteri con terminazione null o un valore intero. Il formato di ogni viene indicato nella descrizione dell'attributo. A cui puntate stringhe di caratteri di *ValuePtr* argomento di **SQLSetConnectAttr** avere una lunghezza di *StringLength* byte.  
  
 Il *StringLength* argomento viene ignorato se la lunghezza è definita dall'attributo, come accade per tutti gli attributi introdotte in ODBC 2*x* o versioni precedenti.  
  
|*Attribute*|*ValuePtr* contenuto|  
|-----------------|-------------------------|  
|SQL_ATTR_ACCESS_MODE (ODBC 1.0)|Un valore SQLUINTEGER. SQL_MODE_READ_ONLY viene utilizzato dal driver o origine dati come un indicatore che la connessione non è necessaria per supportare le istruzioni SQL che causano l'esecuzione degli aggiornamenti. Questa modalità può essere usata per ottimizzare le strategie di blocco, gestione delle transazioni o altre aree appropriato per l'origine dati o driver. Il driver non è necessaria per evitare tali istruzioni venga inviato all'origine dati. Il comportamento del driver e origine dati quando viene richiesto per elaborare istruzioni SQL che non sono in sola lettura durante una connessione di sola lettura è definito dall'implementazione. SQL_MODE_READ_WRITE è il valore predefinito.|  
|SQL_ATTR_ASYNC_DBC_EVENT (ODBC 3.8)|Valore SQLPOINTER che è un handle di evento.<br /><br /> Notifica del completamento di funzioni asincrone è abilitata per la chiamata **SQLSetConnectAttr** con l'attributo SQL_ATTR_ASYNC_STMT_EVENT e specificando l'handle dell'evento. **Nota:** il metodo di notifica non è supportato con libreria di cursori. Un'applicazione verrà visualizzato il messaggio di errore se tenta di abilitare la libreria di cursori tramite SQLSetConnectAttr, quando il metodo di notifica è abilitato.|  
|SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE (ODBC 3.8)|Valore SQLUINTEGER che abilita o disabilita l'esecuzione asincrona delle funzioni selezionate nell'handle di connessione. Per ulteriori informazioni, vedere [esecuzione asincrona (metodo di Polling)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md).<br /><br /> SQL_ASYNC_DBC_ENABLE_ON = Enable operazione asincrona per le funzioni correlate alla connessione specificate.<br /><br /> SQL_ASYNC_DBC_ENABLE_OFF = Disable (impostazione predefinita) operazione asincrona per le funzioni correlate alla connessione specificate.<br /><br /> Impostazione SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE è sempre sincrono (ovvero, non restituirà mai SQL_STILL_EXECUTING).<br /><br /> Esecuzione asincrona delle operazioni di istruzione sono abilitate con SQL_ATTR_ASYNC_ENABLE.|  
|SQL_ATTR_ASYNC_DBC_PCALLBACK (ODBC 3.8)|Valore SQLPOINTER che punta alla struttura di contesto.<br /><br /> Solo in Gestione Driver può chiamare un driver **SQLSetStmtAttr** funzione con questo attributo.|  
|SQL_ATTR_ASYNC_DBC_PCONTEXT (ODBC 3.8)|Valore SQLPOINTER che punta alla struttura di contesto.<br /><br /> Solo in Gestione Driver può chiamare un driver **SQLSetStmtAttr** funzione con questo attributo.|  
|SQL_ATTR_ASYNC_ENABLE (ODBC 3.0)|Un valore SQLULEN che specifica se una funzione denominata con un'istruzione sulla connessione specificata viene eseguita in modo asincrono:<br /><br /> SQL_ASYNC_ENABLE_OFF = disabilita il supporto di livello esecuzione asincrona connessione per le operazioni di istruzione (impostazione predefinita).<br /><br /> SQL_ASYNC_ENABLE_ON = abilitare il supporto di livello di esecuzione asincrona di connessione per le operazioni di istruzione.<br /><br /> Questo attributo può essere impostata se **SQLGetInfo** con le informazioni di SQL_ASYNC_MODE tipo restituisce SQL_AM_CONNECTION o SQL_AM_STATEMENT.|  
|SQL_ATTR_AUTO_IPD (ODBC 3.0)|Un valore di sola lettura SQLUINTEGER che specifica se il popolamento automatico del IPD dopo una chiamata a **SQLPrepare** è supportato:<br /><br /> SQL_TRUE = popolamento automatico del IPD dopo una chiamata a **SQLPrepare** è supportato dal driver.<br /><br /> SQL_FALSE = popolamento automatico del IPD dopo una chiamata a **SQLPrepare** non è supportata dal driver. I server che non supportano le istruzioni preparate non saranno in grado di popolare il IPD automaticamente.<br /><br /> Se SQL_TRUE viene restituito per l'attributo di connessione SQL_ATTR_AUTO_IPD, è possibile impostare l'attributo di istruzione SQL_ATTR_ENABLE_AUTO_IPD per attivare o disattivare la compilazione automatica del IPD. Se SQL_ATTR_AUTO_IPD è SQL_FALSE, SQL_ATTR_ENABLE_AUTO_IPD non può essere impostato su SQL_TRUE. Il valore predefinito di SQL_ATTR_ENABLE_AUTO_IPD è uguale al valore di SQL_ATTR_AUTO_IPD.<br /><br /> L'attributo di connessione può essere restituito da **SQLGetConnectAttr** ma non possono essere impostate da **SQLSetConnectAttr**.|  
|SQL_ATTR_AUTOCOMMIT (ODBC 1.0)|Un valore SQLUINTEGER che specifica se utilizzare la modalità autocommit o commit manuale:<br /><br /> SQL_AUTOCOMMIT_OFF = il driver utilizza modalità di commit manuale e l'applicazione deve esplicitamente eseguire il commit o il rollback delle transazioni con **SQLEndTran**.<br /><br /> SQL_AUTOCOMMIT_ON = il driver utilizza la modalità autocommit. Ogni istruzione viene eseguito il commit immediatamente dopo che viene eseguita. Impostazione predefinita. Transazioni aperte per la connessione vengono eseguito il commit quando SQL_ATTR_AUTOCOMMIT è impostata su SQL_AUTOCOMMIT_ON per passare dalla modalità di commit manuale alla modalità di autocommit.<br /><br /> Per ulteriori informazioni, vedere [modalità Commit](../../../odbc/reference/develop-app/commit-mode.md). **Importante:** alcune origini dati di eliminare i piani di accesso e chiudere i cursori per tutte le istruzioni in una connessione ogni volta che un'istruzione viene eseguito il commit; la modalità autocommit può causare questo risultato dopo l'esecuzione di ogni istruzione nonquery o quando il cursore è chiuso per una query. Per ulteriori informazioni, vedere i tipi di informazioni SQL_CURSOR_COMMIT_BEHAVIOR e SQL_CURSOR_ROLLBACK_BEHAVIOR in [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) e [effettiva delle transazioni, cursori e delle istruzioni preparate](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md). <br /><br /> Quando un batch viene eseguito in modalità autocommit, sono possibili due operazioni. L'intero batch può essere considerato come un'unità autocommitable oppure ogni istruzione in un batch viene considerato come un'unità autocommitable. Determinate origini dati possono supportare entrambi questi comportamenti e possono costituire un modo per la scelta di uno o l'altro. È definito dal driver se un batch viene considerato come un'unità di autocommitable o se ogni istruzione all'interno del batch è autocommitable.|  
|SQL_ATTR_CONNECTION_DEAD<br /><br /> (ODBC 3.5)|Valore SQLUINTEGER in sola lettura che indica lo stato della connessione. Se SQL_CD_TRUE, la connessione è stata persa. Se SQL_CD_FALSE, la connessione è ancora attiva.|  
|SQL_ATTR_CONNECTION_TIMEOUT (ODBC 3.0)|Un valore SQLUINTEGER corrispondente al numero di secondi di attesa per qualsiasi richiesta per la connessione per il completamento prima di restituire l'applicazione. Il driver deve restituire HYT00 SQLSTATE (Timeout scaduto) in qualsiasi momento che è possibile timeout in una situazione non è associata l'esecuzione di query o l'account di accesso.<br /><br /> Se *ValuePtr* è uguale a 0 (impostazione predefinita), non vi è alcun timeout.|  
|SQL_ATTR_CURRENT_CATALOG (ODBC 2.0)|Una stringa di caratteri contenente il nome del catalogo da utilizzare dall'origine dati. Ad esempio, in SQL Server, il catalogo è un database, pertanto il driver invia un **utilizzare** *database* istruzione per l'origine dati, in cui *database* è il database specificato \* *ValuePtr*. Per un driver a un solo livello, il catalogo potrebbe essere una directory, pertanto, il driver modifica la directory corrente alla directory specificata **ValuePtr*.|  
|SQL_ATTR_DBC_INFO_TOKEN (ODBC 3.8|Un valore SQLPOINTER utilizzato per impostare nuovamente il token di informazioni di connessione in DBC handle quando [SQLRateConnection](../../../odbc/reference/syntax/sqlrateconnection-function.md)del (\**pRating*) parametro non è uguale a 100.<br /><br /> SQL_ATTR_DBC_INFO_TOKEN è di sola. Non è possibile utilizzare **SQLGetConnectAttr** o **SQLGetConnectOption** per recuperare questo valore. Il Driver Manager **SQLSetConnectAttr** non accetterà SQL_ATTR_DBC_INFO_TOKEN, poiché un'applicazione non deve impostare questo attributo.<br /><br /> Se un driver restituisce SQL_ERROR dopo l'impostazione SQL_ATTR_DBC_INFO_TOKEN, la connessione appena ottenuta dal pool vengono liberata. Gestione Driver tenta quindi di ottenere un'altra connessione dal pool. Vedere [consapevolezza Pool di connessioni lo sviluppo di un Driver ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md) per ulteriori informazioni.|  
|SQL_ATTR_ENLIST_IN_DTC (ODBC 3.0)|Un valore SQLPOINTER che specifica se utilizzare il driver ODBC in transazioni distribuite coordinate da Servizi componenti Microsoft.<br /><br /> Passare un oggetto OLE DTC transaction che specifica la transazione per esportare in SQL Server o SQL_DTC_DONE per terminare l'associazione DTC della connessione.<br /><br /> Il client chiama il metodo di Microsoft Distributed Transaction Coordinator (MS DTC) OLE ITransactionDispenser:: BeginTransaction per iniziare una transazione MS DTC e creare un oggetto transazione MS DTC che rappresenta la transazione. L'applicazione chiama quindi la funzione SQLSetConnectAttr con l'opzione SQL_ATTR_ENLIST_IN_DTC per associare l'oggetto di transazione della connessione ODBC. Tutte le attività del database correlate verranno eseguite sotto la protezione della transazione MS DTC. L'applicazione chiama la funzione SQLSetConnectAttr con SQL_DTC_DONE per terminare l'associazione DTC della connessione. Per ulteriori informazioni, vedere la documentazione di MS DTC.|  
|SQL_ATTR_LOGIN_TIMEOUT (ODBC 1.0)|Un valore SQLUINTEGER corrispondente al numero di secondi di attesa per una richiesta di accesso per il completamento prima di restituire l'applicazione. Il valore predefinito è dipendente dal driver. Se *ValuePtr* è 0, il timeout è disabilitato e un tentativo di connessione attenderà un tempo illimitato.<br /><br /> Se il timeout specificato supera il timeout di accesso massimo nell'origine dati, il driver sostituisce il valore e restituisce SQLSTATE 01S02 (valore di opzione modificato).|  
|SQL_ATTR_METADATA_ID (ODBC 3.0)|Un valore SQLUINTEGER che determina come vengono trattati gli argomenti stringa di funzioni di catalogo.<br /><br /> Se SQL_TRUE, l'argomento di stringa delle funzioni di catalogo vengono considerati come identificatori. Nel caso non è significativo. Per le stringhe non delimitate, il driver rimuove gli spazi finali e viene ridotta la stringa in lettere maiuscole. Per le stringhe delimitate, il driver rimuove gli spazi iniziali o finali e accetta letteralmente qualunque sia l'intervallo tra i delimitatori. Se uno di questi argomenti è impostato su un puntatore null, la funzione restituisce SQL_ERROR e SQLSTATE HY009 (utilizzo non valido del puntatore null).<br /><br /> Se SQL_FALSE, gli argomenti stringa di funzioni di catalogo non vengono considerati come identificatori. Il case è significativo. Essi possono contenere un criterio di ricerca stringa oppure No, a seconda dell'argomento.<br /><br /> Il valore predefinito è SQL_FALSE.<br /><br /> Il *TableType* argomento di **SQLTables**, che accetta un elenco di valori, non è interessato da questo attributo.<br /><br /> SQL_ATTR_METADATA_ID può anche essere impostati a livello di istruzione. (È l'attributo di connessione solo che è anche un attributo di istruzione).<br /><br /> Per ulteriori informazioni, vedere [argomenti delle funzioni di catalogo in](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).|  
|SQL_ATTR_ODBC_CURSORS (ODBC 2.0)|Un valore SQLULEN che specifica la modalità di gestione Driver utilizza la libreria di cursori ODBC:<br /><br /> SQL_CUR_USE_IF_NEEDED = il Driver Manager utilizza la libreria di cursori ODBC solo se necessario. Se il driver supporta l'opzione SQL_FETCH_PRIOR in **SQLFetchScroll**, gestione Driver utilizza le funzionalità di scorrimento del driver. In caso contrario, utilizza la libreria di cursori ODBC.<br /><br /> SQL_CUR_USE_ODBC = il Driver Manager utilizza la libreria di cursori ODBC.<br /><br /> SQL_CUR_USE_DRIVER = il Driver Manager utilizza le funzionalità di scorrimento del driver. Si tratta dell'impostazione predefinita.<br /><br /> Per ulteriori informazioni sulla libreria di cursori ODBC, vedere [libreria di cursori ODBC appendice f:](../../../odbc/reference/appendixes/appendix-f-odbc-cursor-library.md). **Avviso:** la libreria di cursori verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.|  
|SQL_ATTR_PACKET_SIZE (ODBC 2.0)|Un valore SQLUINTEGER che specifica le dimensioni del pacchetto di rete in byte. **Nota:** molte origini dati non supportano questa opzione o solo restituito ma non impostare le dimensioni del pacchetto di rete. <br /><br /> Se la dimensione specificata supera la dimensione massima del pacchetto o è inferiore alla dimensione minima dei pacchetti, il driver sostituisce il valore e restituisce SQLSTATE 01S02 (valore di opzione modificato).<br /><br /> Se l'applicazione imposta dimensioni del pacchetto dopo che è già stata stabilita una connessione, il driver restituirà SQLSTATE HY011 (Impossibile impostare l'attributo ora).|  
|SQL_ATTR_QUIET_MODE (ODBC 2.0)|Un handle di finestra (HWND).<br /><br /> Se l'handle di finestra è un puntatore null, il driver non viene visualizzata alcuna finestra di dialogo.<br /><br /> Se l'handle di finestra non è un puntatore null, deve essere l'handle della finestra principale dell'applicazione. Impostazione predefinita. Il driver Usa questo handle per la visualizzazione di finestre di dialogo. **Nota:** l'attributo di connessione SQL_ATTR_QUIET_MODE non si applica alle finestre di dialogo visualizzate da **SQLDriverConnect**.|  
|SQL_ATTR_TRACE (ODBC 1.0)|Un valore SQLUINTEGER indicando se eseguire la traccia di gestione Driver:<br /><br /> SQL_OPT_TRACE_OFF = traccia off (impostazione predefinita)<br /><br /> SQL_OPT_TRACE_ON = traccia in<br /><br /> Quando la traccia è attiva, gestione Driver scrive ogni chiamata di funzione ODBC nel file di traccia. **Nota:** quando la traccia è attiva, gestione Driver può restituire IM013 SQLSTATE (errore del file di traccia) da qualsiasi funzione. <br /><br /> Un'applicazione specifica un file di traccia con l'opzione SQL_ATTR_TRACEFILE. Se il file esiste già, gestione Driver aggiunge il file. In caso contrario, viene creato il file. Se è stato specificato alcun file di traccia traccia è attiva, gestione Driver scrive il file SQL. LOG nella directory radice.<br /><br /> Un'applicazione può impostare la variabile **ODBCSharedTraceFlag** per abilitare la traccia in modo dinamico. Quindi è attivata per tutte le applicazioni ODBC attualmente in esecuzione. Se un'applicazione disattiva la traccia, è stato disattivato solo per tale applicazione.<br /><br /> Se il **traccia** (parola chiave) nelle informazioni di sistema è impostato su 1 quando un'applicazione chiama **SQLAllocHandle** con un *HandleType* impostato su SQL_HANDLE_ENV, la traccia è abilitata per tutti gestisce l'eccezione. È abilitato solo per l'applicazione che ha chiamato **SQLAllocHandle**.<br /><br /> La chiamata **SQLSetConnectAttr** con un *attributo* di SQL_ATTR_TRACE non richiede che il *ConnectionHandle* argomento sia valido e non restituisce SQL_ERROR se *ConnectionHandle* è NULL. Questo attributo si applica a tutte le connessioni.|  
|SQL_ATTR_TRACEFILE (ODBC 1.0)|Una stringa di caratteri con terminazione null contenente il nome del file di traccia.<br /><br /> Il valore predefinito dell'attributo SQL_ATTR_TRACEFILE è specificato con il **TraceFile** (parola chiave) nelle informazioni di sistema. Per ulteriori informazioni, vedere [sottochiave ODBC](../../../odbc/reference/install/odbc-subkey.md).<br /><br /> La chiamata **SQLSetConnectAttr** con un *attributo* di sql_attr TRACEFILE non richiede il *ConnectionHandle* argomento sia valido e non restituisce SQL_ERROR se *ConnectionHandle* non è valido. Questo attributo si applica a tutte le connessioni.|  
|SQL_ATTR_TRANSLATE_LIB (ODBC 1.0)|Una stringa di caratteri con terminazione null contenente il nome di una libreria che contiene le funzioni **SQLDriverToDataSource** e **SQLDataSourceToDriver** che consente di accedere il driver per eseguire attività, ad esempio conversione del set di caratteri. Questa opzione può essere specificato solo se il driver è connesso all'origine dati. L'impostazione di questo attributo verrà mantenuto tra le connessioni. Per ulteriori informazioni sulla conversione di dati, vedere [traduzione DLL](../../../odbc/reference/develop-app/translation-dlls.md) e [riferimento alle funzioni di conversione DLL](../../../odbc/reference/syntax/translation-dll-api-reference.md).|  
|SQL_ATTR_TRANSLATE_OPTION (ODBC 1.0)|Valore flag a 32 bit che viene passato alla DLL di conversione. Questo attributo può essere specificato solo se il driver è connesso all'origine dati. Per informazioni sulla conversione di dati, vedere [traduzione DLL](../../../odbc/reference/develop-app/translation-dlls.md).|  
|SQL_ATTR_TXN_ISOLATION (ODBC 1.0)|Una maschera a 32 bit che imposta il livello di isolamento per la connessione corrente. Un'applicazione deve chiamare **SQLEndTran** per eseguire il commit o il rollback di tutte le transazioni aperte in una connessione, prima di chiamare **SQLSetConnectAttr** con questa opzione.<br /><br /> I valori validi per *ValuePtr* può essere determinato chiamando **SQLGetInfo** con *InfoType* uguale a SQL_TXN_ISOLATION_OPTIONS.<br /><br /> Per una descrizione dei livelli di isolamento delle transazioni, vedere la descrizione del tipo di informazioni SQL_DEFAULT_TXN_ISOLATION nel [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) e [livelli di isolamento delle transazioni](../../../odbc/reference/develop-app/transaction-isolation-levels.md).|  
  
 [1] queste funzioni possono essere chiamate in modo asincrono, solo se il descrittore è un descrittore di implementazione, non è un descrittore di applicazione.  
  
## <a name="code-example"></a>Esempio di codice  
 Vedere [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Allocazione di un handle|[Funzione SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Restituisce l'impostazione di un attributo di connessione|[Funzione SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
