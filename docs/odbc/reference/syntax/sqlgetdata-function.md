---
title: Funzione SQLGetData | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLGetData
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLGetData
helpviewer_keywords: SQLGetData function [ODBC]
ms.assetid: e3c1356a-5db7-4186-85fd-8b74633317e8
caps.latest.revision: "46"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 0a23ddb9ee932b67bddd35edfcc9d64228b36f18
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sqlgetdata-function"></a>Funzione SQLGetData
**Conformità**  
 Introdotta: versione ODBC standard 1.0 conformità: 92 ISO  
  
 **Riepilogo**  
 **SQLGetData** recupera dati per una singola colonna nel set di risultati o per un singolo parametro dopo **SQLParamData** restituisce SQL_PARAM_DATA_AVAILABLE. Può essere chiamato più volte per recuperare i dati a lunghezza variabile in parti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLGetData(  
      SQLHSTMT       StatementHandle,  
      SQLUSMALLINT   Col_or_Param_Num,  
      SQLSMALLINT    TargetType,  
      SQLPOINTER     TargetValuePtr,  
      SQLLEN         BufferLength,  
      SQLLEN *       StrLen_or_IndPtr);  
```  
  
## <a name="arguments"></a>Argomenti  
 *StatementHandle*  
 [Input] Handle di istruzione.  
  
 *Col_or_Param_Num*  
 [Input] Per il recupero di dati della colonna, è il numero di colonna per cui restituire i dati. Colonne del set di risultati sono numerate in ordine crescente di colonna a partire da 1. La colonna del segnalibro è il numero di colonna 0; può essere specificato solo se sono abilitati i segnalibri.  
  
 Per il recupero dei dati del parametro, è il numero ordinale del parametro, che inizia da 1.  
  
 *TargetType*  
 [Input] L'identificatore del tipo del tipo di dati C il **TargetValuePtr* buffer. Per un elenco di tipi di dati C validi e di identificatori di tipo, vedere il [tipi di dati C](../../../odbc/reference/appendixes/c-data-types.md) sezione Appendice d: tipo di dati.  
  
 Se *TargetType* è SQL_ARD_TYPE, il driver utilizza l'identificatore del tipo specificato nel campo SQL_DESC_CONCISE_TYPE del ARD. Se *TargetType* è SQL_APD_TYPE, **SQLGetData** verrà utilizzato il tipo di dati C stesso che è stato specificato in **SQLBindParameter**. In caso contrario, il tipo di dati C specificato **SQLGetData** esegue l'override nel tipo di dati C specificato **SQLBindParameter**. Se è SQL_C_DEFAULT, il driver consente di selezionare il tipo di dati C predefinito in base al tipo di dati SQL dell'origine.  
  
 È inoltre possibile specificare un tipo di dati C esteso. Per ulteriori informazioni, vedere [tipi di dati C in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
 *TargetValuePtr*  
 [Output] Puntatore al buffer in cui restituire i dati.  
  
 *TargetValuePtr* non può essere NULL.  
  
 *BufferLength*  
 [Input] Lunghezza di **TargetValuePtr* buffer in byte.  
  
 Il driver utilizza *BufferLength* per evitare di scrivere oltre la fine del \* *TargetValuePtr* buffer durante la restituzione di dati a lunghezza variabile, ad esempio carattere o dati binari. Si noti che il driver viene considerato il carattere di terminazione null per la restituzione di dati carattere \* *TargetValuePtr*. **TargetValuePtr* deve pertanto contenere spazio per il carattere di terminazione null, o il driver verrà troncare i dati.  
  
 Quando il driver restituisce dati a lunghezza fissa, ad esempio un numero intero o una struttura di data, il driver ignora *BufferLength* e presuppone che il buffer sia sufficientemente grande da contenere i dati. È pertanto importante per l'applicazione allocare un buffer sufficiente per i dati a lunghezza fissa o il driver scriverà oltre la fine del buffer.  
  
 **SQLGetData** restituisce SQLSTATE HY090 (stringa di lunghezza o non valida del buffer) quando *BufferLength* è minore di 0 ma non quando *BufferLength* è 0.  
  
 *StrLen_or_IndPtr*  
 [Output] Puntatore al buffer in cui restituire il valore di lunghezza o indicatore. Se questo è un puntatore null, viene restituito alcun valore di lunghezza o indicatore. Restituisce un errore quando i dati recuperati sono NULL.  
  
 **SQLGetData** può restituire i valori seguenti nel buffer di lunghezza/indicatore:  
  
-   La lunghezza dei dati da restituire  
  
-   SQL_NO_TOTAL  
  
-   SQL_NULL_DATA  
  
 Per ulteriori informazioni, vedere [tramite valori di lunghezza/indicatore](../../../odbc/reference/develop-app/using-length-and-indicator-values.md) e "Commenti" in questo argomento.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_STILL_EXECUTING, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLGetData** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato può essere ottenuto chiamando **SQLGetDiagRec** con un *HandleType* di Impostato su SQL_HANDLE_STMT e *gestire* di *StatementHandle*. Nella tabella seguente sono elencati i valori SQLSTATE comunemente restituiti da **SQLGetData** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01004|Stringa di dati corretto troncato|Non tutti i dati per la colonna specificata, *Col_or_Param_Num*, è stato possibile recuperare in una singola chiamata alla funzione. SQL_NO_TOTAL o la lunghezza dei dati rimanenti nella colonna specificata prima della chiamata corrente a **SQLGetData** viene restituito in \* *StrLen_or_IndPtr*. (Funzione restituisce SQL_SUCCESS_WITH_INFO).<br /><br /> Per ulteriori informazioni sull'utilizzo di più chiamate a **SQLGetData** per una singola colonna, vedere "Commenti".|  
|01S07|Troncamento frazionario.|I dati restituiti per una o più colonne è stati troncati. Per i tipi di dati numerici, la parte frazionaria del numero è stata troncata. Per ora, timestamp e tipi di dati di intervallo contenente un componente di ora, la parte frazionaria del tempo è stata troncata.<br /><br /> (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|07006|Violazione dell'attributo del tipo di dati|Il valore di dati di una colonna nel set di risultati non può essere convertito nel tipo di dati C specificato dall'argomento *TargetType*.|  
|07009|Indice del descrittore non valido|Il valore specificato per l'argomento *Col_or_Param_Num* era 0 e l'attributo di istruzione SQL_ATTR_USE_BOOKMARKS è stato impostato su SQL_UB_OFF.<br /><br /> Il valore specificato per l'argomento *Col_or_Param_Num* è maggiore del numero di colonne nel set di risultati.<br /><br /> Il *Col_or_Param_Num* valore non è uguale al numero ordinale del parametro che è disponibile.<br /><br /> (DM) è stata associata la colonna specificata. Questa descrizione non è valida per i driver che restituiscono la maschera di bit SQL_GD_BOUND per l'opzione SQL_GETDATA_EXTENSIONS in **SQLGetInfo**.<br /><br /> (DM) il numero della colonna specificata è minore o uguale al numero della colonna associata più alto. Questa descrizione non è valida per i driver che restituiscono la maschera di bit SQL_GD_ANY_COLUMN per l'opzione SQL_GETDATA_EXTENSIONS in **SQLGetInfo**.<br /><br /> (DM) l'applicazione è già chiamato **SQLGetData** per la riga corrente; il numero della colonna specificata nella chiamata corrente è minore del numero della colonna specificata nella chiamata precedente; e il driver non restituisce lo SQL _ Maschera di bit GD_ANY_ORDER per l'opzione SQL_GETDATA_EXTENSIONS in **SQLGetInfo**.<br /><br /> (DM) il *TargetType* argomento era SQL_ARD_TYPE e *Col_or_Param_Num* record del descrittore di ARD non è riuscita la verifica coerenza.<br /><br /> (DM) il *TargetType* argomento sia SQL_ARD_TYPE e il valore nel campo SQL_DESC_COUNT del ARD è inferiore a quello di *Col_or_Param_Num* argomento.|  
|08S01|Errore del collegamento di comunicazione|Collegamento di comunicazione tra il driver e l'origine dati a cui era connesso il driver non è stato possibile prima dell'elaborazione della funzione è stata completata.|  
|22002|Variabile indicatore necessaria ma non fornito|*StrLen_or_IndPtr* era un puntatore null e dati NULL è stati recuperati.|  
|22003|Valore numerico non compreso nell'intervallo|Restituire il valore numerico (come valore numerico o stringa) per la colonna avrebbe causato la parte intera (in contrapposizione frazionari) del numero da troncare.<br /><br /> Per ulteriori informazioni, vedere [appendice d: i tipi di dati](../../../odbc/reference/appendixes/appendix-d-data-types.md).|  
|22007|Formato di datetime non valido|Colonna di tipo carattere nel set di risultati è stata associata a una data, ora o struttura di timestamp C e il valore nella colonna è una data non valida, il tempo o timestamp, rispettivamente. Per ulteriori informazioni, vedere [appendice d: i tipi di dati](../../../odbc/reference/appendixes/appendix-d-data-types.md).|  
|22012|Divisione per zero|È stato restituito un valore da un'espressione aritmetica che ha comportato la divisione per zero.|  
|22015|Overflow del campo intervallo|L'assegnazione da un numerico esatto o l'intervallo di tipo SQL a un tipo di intervallo C ha causato una perdita di cifre significative nel campo iniziale.<br /><br /> Per la restituzione di dati a un tipo di intervallo C, si è verificato alcun rappresentazione del valore di tipo SQL nel tipo di intervallo C.|  
|22018|Valore di carattere non valido per la specifica del cast|Una colonna di tipo carattere nel set di risultati restituita da un buffer di caratteri C e la colonna contiene un carattere che non ha ricevuto alcuna rappresentazione nel set di caratteri del buffer.<br /><br /> Il tipo C è stato un numerico esatto o approssimativo, un valore datetime o un tipo di dati di intervallo. il tipo SQL della colonna è un tipo di dati character; il valore nella colonna non ha un valore letterale valido del tipo C associato.|  
|24000|Stato del cursore non valido|(DM) a cui è stata chiamata senza prima chiamare la funzione **SQLFetch** o **SQLFetchScroll** per posizionare il cursore sulla riga di dati necessari.<br /><br /> (DM) il *StatementHandle* è stato eseguito, ma è stato associato alcun set di risultati di *StatementHandle*.<br /><br /> Un cursore è stato aperto nel *StatementHandle* e **SQLFetch** o **SQLFetchScroll** fosse stata chiamata, ma è stato posizionato il cursore prima dell'inizio del set di risultati o dopo il fine del set di risultati.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel *MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver è stato in grado di allocare la memoria necessaria per supportare l'esecuzione o il completamento della funzione.|  
|HY003|Tipo di programma non compreso nell'intervallo|(DM) l'argomento *TargetType* non è un tipo di dati valido, SQL_C_DEFAULT, SQL_ARD_TYPE (in caso di recupero di dati della colonna) o SQL_APD_TYPE (in caso di recupero di dati di parametro).<br /><br /> (DM) l'argomento *Col_or_Param_Num* è 0 e l'argomento *TargetType* non SQL_C_BOOKMARK per un segnalibro a lunghezza fissa o SQL_C_VARBOOKMARK per un segnalibro a lunghezza variabile.|  
|HY008|Operazione annullata|L'elaborazione asincrona è stata abilitata per il *StatementHandle*. La funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle*, e quindi è stata chiamata la funzione nuovo di *StatementHandle*.<br /><br /> La funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle* da un thread diverso in un applicazioni multithread e quindi la funzione è stata chiamata nuovamente sul *StatementHandle*.|  
|HY009|Utilizzo non valido del puntatore null|(DM) l'argomento *TargetValuePtr* era un puntatore null.|  
|HY010|Errore nella sequenza (funzione)|(DM) specificato *StatementHandle* non è stato eseguito. La funzione è stata chiamata senza chiamare prima il metodo **SQLExecDirect**, **SQLExecute** o una funzione di catalogo.<br /><br /> (DM) a cui è stata chiamata per l'handle di connessione associata a una funzione in modo asincrono in esecuzione il *StatementHandle*. Questa funzione asincrona era ancora in esecuzione quando il **SQLGetData** funzione è stata chiamata.<br /><br /> (DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione (non è presente uno) di *StatementHandle* ed era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos** è stato chiamato per il  *StatementHandle* e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima che sono stati inviati dati per tutti i parametri data-at-execution o colonne.<br /><br /> (DM) il *StatementHandle* è stato eseguito, ma è stato associato alcun set di risultati di *StatementHandle*.<br /><br /> Una chiamata a **SQLExeceute**, **SQLExecDirect**, o **SQLMoreResults** restituito SQL_PARAM_DATA_AVAILABLE, ma **SQLGetData** è stato chiamato , invece di **SQLParamData**.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY090|Lunghezza di stringa o di buffer non valida|(DM) il valore specificato per l'argomento *BufferLength* era minore di 0.<br /><br /> Il valore specificato per l'argomento *BufferLength* è inferiore a 4, il *Col_or_Param_Num* argomento è stato impostato su 0 e il driver non è un'API ODBC 2*x* driver.|  
|HY109|Posizione del cursore non valido|Il cursore era posizionato (da **SQLSetPos**, **SQLFetch**, **SQLFetchScroll**, o **SQLBulkOperations**) su una riga che è stata eliminata o potrebbe non essere recuperati.<br /><br /> Il cursore sia un cursore forward-only e le dimensioni del set di righe sono maggiore di uno.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Funzionalità facoltativa non implementata.|L'origine dati o driver non supporta l'utilizzo di **SQLGetData** con più righe in **SQLFetchScroll**. Questa descrizione non è valida per i driver che restituiscono la maschera di bit SQL_GD_BLOCK per l'opzione SQL_GETDATA_EXTENSIONS in **SQLGetInfo**.<br /><br /> L'origine dati o driver non supporta la conversione specificata dalla combinazione del *TargetType* argomento e il tipo di dati SQL della colonna corrispondente. Questo errore si applica solo quando il tipo di dati SQL della colonna è stato eseguito il mapping a un tipo di dati specifici del driver SQL.<br /><br /> Il driver supporta solo 2 di ODBC*x*e l'argomento *TargetType* è uno dei seguenti:<br /><br /> SQL_C_NUMERIC SQL_C_SBIGINT SQL_C_UBIGINT<br /><br /> uno dei tipi di dati di intervallo C sono elencati nella [tipi di dati C](../../../odbc/reference/appendixes/c-data-types.md) appendice d: tipo di dati.<br /><br /> Il driver supporta solo versioni ODBC prima 3.50 e l'argomento *TargetType* stato SQL_C_GUID.|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|(DM) il driver corrispondente il *StatementHandle* non supporta la funzione.|  
|IM017|Polling è disabilitato in modalità di notifica asincrona|Ogni volta che viene utilizzato il modello di notifica, il polling è disabilitato.|  
|IM018|**SQLCompleteAsync** non è stato chiamato per completare l'operazione asincrona precedente su questo handle.|Se la chiamata di funzione precedente dell'handle restituisce SQL_STILL_EXECUTING e se è abilitata la modalità di notifica, **SQLCompleteAsync** deve essere chiamato per l'handle per eseguire la post-elaborazione e completare l'operazione.|  
  
## <a name="comments"></a>Commenti  
 **SQLGetData** restituisce i dati in una colonna specificata. **SQLGetData** può essere chiamato solo dopo che una o più righe sono state recuperate dal set di risultati tramite **SQLFetch**, **SQLFetchScroll**, o **SQLExtendedFetch** . Se i dati a lunghezza variabile sono troppo grandi per essere restituiti in una singola chiamata a **SQLGetData** (a causa di una limitazione nell'applicazione), **SQLGetData** possibile recuperarla in parti. È possibile associare alcune colonne in una riga e una chiamata **SQLGetData** ad altri utenti, anche se si tratta soggetti ad alcune restrizioni. Per ulteriori informazioni, vedere [recupero di dati Long](../../../odbc/reference/develop-app/getting-long-data.md).  
  
 Per informazioni sull'utilizzo **SQLGetData** con i parametri di flusso di output, vedere [il recupero dei parametri di Output tramite SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
## <a name="using-sqlgetdata"></a>Mediante SQLGetData  
 Se il driver non supporta le estensioni per **SQLGetData**, la funzione può restituire solo i dati per le colonne non associate con un numero maggiore di quello dell'ultima colonna associata. Inoltre, all'interno di una riga di dati, il valore della proprietà di *Col_or_Param_Num* argomento in ogni chiamata a **SQLGetData** deve essere maggiore o uguale al valore di *Col_or_Param_Num*nella chiamata precedente; ovvero, è necessario recuperare i dati in ordine di numero di colonna crescente. Infine, se è supportata alcuna estensione, **SQLGetData** non può essere chiamato se le dimensioni del set di righe sono maggiore di 1.  
  
 I driver non sono sempre rispettato uno qualsiasi di queste restrizioni. Per determinare le limitazioni vengono ridotti i un driver, un'applicazione chiama **SQLGetInfo** con le opzioni SQL_GETDATA_EXTENSIONS seguenti:  
  
-   SQL_GD_OUTPUT_PARAMS = **SQLGetData** può essere chiamato per restituire i valori di parametro di output. Per ulteriori informazioni, vedere [il recupero dei parametri di Output tramite SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
-   SQL_GD_ANY_COLUMN. Se questa opzione viene restituita, **SQLGetData** può essere chiamato per qualsiasi colonna non associata, inclusi quelli prima che l'ultima colonna associata.  
  
-   SQL_GD_ANY_ORDER. Se questa opzione viene restituita, **SQLGetData** può essere chiamato per le colonne non associate in qualsiasi ordine.  
  
-   SQL_GD_BLOCK. Se questa opzione viene restituita dalla **SQLGetInfo** per il InfoType SQL_GETDATA_EXTENSIONS, il driver supporta le chiamate a **SQLGetData** quando le dimensioni del set di righe sono maggiore di 1 e l'applicazione può chiamare **SQLSetPos** con l'opzione SQL_POSITION per posizionare il cursore sulla riga corretta prima di chiamare **SQLGetData.**  
  
-   SQL_GD_BOUND. Se questa opzione viene restituita, **SQLGetData** può essere chiamato per le colonne associate, nonché le colonne non associate.  
  
 Esistono due eccezioni a queste restrizioni e possibilità di un driver a essi. Prima di tutto, **SQLGetData** non dovrebbe mai essere chiamato per un cursore forward-only quando le dimensioni del set di righe sono maggiore di 1. In secondo luogo, se un driver supporta i segnalibri, deve sempre supportare la possibilità di chiamare **SQLGetData** per la colonna 0, anche se non consente alle applicazioni di chiamare **SQLGetData** per le altre colonne prima dell'ultimo colonna associata. (Quando un'applicazione sta utilizzando un'API ODBC 2*x* driver, **SQLGetData** restituirà correttamente un segnalibro quando viene chiamato con *Col_or_Param_Num* uguale a 0 dopo una chiamata a **SQLFetch**perché **SQLFetch** viene eseguito il mapping da ODBC 3*x* gestione Driver per **SQLExtendedFetch** con un  *FetchOrientation* di SQL_FETCH_NEXT, e **SQLGetData** con un *Col_or_Param_Num* 0 è stato eseguito il mapping da ODBC 3*x* gestione Driver per **SQLGetStmtOption** con un *fOption* di SQL_GET_BOOKMARK.)  
  
 **SQLGetData** non può essere utilizzato per recuperare il segnalibro per una riga appena inserita chiamando **SQLBulkOperations** con l'opzione SQL_ADD, perché il cursore non è posizionato sulla riga. Un'applicazione può recuperare il segnalibro per tale riga, associare la colonna 0 prima di chiamare **SQLBulkOperations** con SQL_ADD, nel qual caso **SQLBulkOperations** restituisce il segnalibro nel buffer associato. **SQLFetchScroll** può quindi essere chiamato con SQL_FETCH_BOOKMARK per riposizionare il cursore sulla riga.  
  
 Se il *TargetType* argomento è un tipo di dati di intervallo, la precisione iniziale intervallo predefinita (2) e la precisione dei secondi di intervallo predefinito (6), di cui i campi SQL_DESC_DATETIME_INTERVAL_PRECISION e SQL_DESC_PRECISION di ARD, vengono utilizzati rispettivamente per i dati. Se il *TargetType* argomento è un tipo di dati SQL_C_NUMERIC, la precisione predefinita (definito dal driver) e valore predefinito di scala (0), come set di campi di SQL_DESC_PRECISION e SQL_DESC_SCALE il ARD, vengono utilizzato per i dati. Se qualsiasi precisione predefinita o la scala non è appropriata, l'applicazione deve impostare in modo esplicito il campo di descrizione appropriato da una chiamata a **SQLSetDescField** o **SQLSetDescRec**. È possibile impostare il campo SQL_DESC_CONCISE_TYPE SQL_C_NUMERIC e chiamare **SQLGetData** con un *TargetType* argomento di SQL_ARD_TYPE, che verranno ripristinati i valori di precisione e scala campi di descrizione da utilizzare.  
  
> [!NOTE]  
>  In ODBC 2*x*, set di applicazioni *TargetType* SQL_C_DATE, SQL_C_TIME o SQL_C_TIMESTAMP per indicare che \* *TargetValuePtr* è una data, ora, o struttura di timestamp. In ODBC 3*x*, set di applicazioni *TargetType* SQL_C_TYPE_DATE, SQL_C_TYPE_TIME o SQL_C_TYPE_TIMESTAMP. Gestione Driver rende mapping appropriato se necessario, in base alla versione dell'applicazione e il driver.  
  
## <a name="retrieving-variable-length-data-in-parts"></a>Il recupero dei dati a lunghezza variabile in parti  
 **SQLGetData** può essere utilizzato per recuperare dati da una colonna che contiene i dati a lunghezza variabile in parti, ovvero, se l'identificatore del tipo di dati SQL della colonna è SQL_CHAR, SQL_VARCHAR, SQL_LONGVARCHAR, SQL_WCHAR, SQL_WVARCHAR, SQL _ WLONGVARCHAR SQL_BINARY, SQL_VARBINARY, SQL_LONGVARBINARY o un identificatore specifico del driver per un tipo a lunghezza variabile.  
  
 Per recuperare dati da una colonna in parti, l'applicazione chiama **SQLGetData** più volte in successione per la stessa colonna. Per ogni chiamata, **SQLGetData** restituisce la parte successiva dei dati. È compito dell'applicazione per riunire le parti, prestando attenzione a rimuovere il carattere di terminazione null da parti intermediate di dati di tipo carattere. Se sono presenti ulteriori dati per restituire o non è stata allocata buffer insufficiente per il carattere di terminazione, **SQLGetData** restituisce SQL_SUCCESS_WITH_INFO e SQLSTATE 01004 (dati troncati). Quando viene restituita l'ultima parte dei dati, **SQLGetData** restituisce SQL_SUCCESS. SQL_NO_TOTAL né zero può essere restituito nell'ultima chiamata valido per recuperare dati da una colonna, perché l'applicazione non sarà necessario in alcun modo di conoscere la quantità di dati nel buffer dell'applicazione è valido. Se **SQLGetData** viene chiamato in seguito, viene restituito SQL_NO_DATA. Per ulteriori informazioni, vedere la sezione successiva, "Recupero dei dati con SQLGetData".  
  
 I segnalibri a lunghezza variabile possono essere restituiti in parti di **SQLGetData**. Come con altri dati, una chiamata a **SQLGetData** per restituire i segnalibri di lunghezza variabile in parti restituirà SQLSTATE 01004 (dati String, troncati a destra) e SQL_SUCCESS_WITH_INFO quando sono presenti ulteriori dati da restituire. Ciò avviene minuscole diversa da un segnalibro a lunghezza variabile verrà troncato mediante una chiamata a **SQLFetch** o **SQLFetchScroll**, che restituisce SQL_ERROR e SQLSTATE 22001 (dati String, troncati a destra).  
  
 **SQLGetData** non può essere utilizzata per restituire dati a lunghezza fissa in parti. Se **SQLGetData** viene chiamato più volte in una riga per una colonna contenente i dati a lunghezza fissa, viene restituito SQL_NO_DATA per tutte le chiamate dopo la prima.  
  
## <a name="retrieving-streamed-output-parameters"></a>Il recupero dei parametri di flusso di Output  
 Se un driver supporta i parametri di flusso di output, un'applicazione può chiamare **SQLGetData** con un piccolo numero di volte per recuperare un valore di parametro di grandi dimensioni del buffer. Per ulteriori informazioni sul parametro di flusso di output, vedere [il recupero dei parametri di Output tramite SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
## <a name="retrieving-data-with-sqlgetdata"></a>Recupero dei dati con SQLGetData  
 Per restituire i dati per la colonna specificata, **SQLGetData** esegue la sequenza di passaggi seguente:  
  
1.  Se è già resa tutti i dati per la colonna non restituisce SQL_NO_DATA.  
  
2.  Set \* *StrLen_or_IndPtr* su SQL_NULL_DATA se i dati sono NULL. Se i dati sono NULL e *StrLen_or_IndPtr* era un puntatore null, **SQLGetData** restituisce SQLSTATE 22002 (variabile indicatore necessaria ma non specificato).  
  
     Se i dati per la colonna non sono NULL, **SQLGetData** procede al passaggio 3.  
  
3.  Se l'attributo di istruzione SQL_ATTR_MAX_LENGTH è impostato su un valore diverso da zero, se la colonna contiene dati carattere o binario e **SQLGetData** non è stato precedentemente chiamato per la colonna, i dati vengono troncati a SQL_ATTR_MAX_LENGTH byte.  
  
    > [!NOTE]  
    >  L'attributo di istruzione SQL_ATTR_MAX_LENGTH è progettato per ridurre il traffico di rete. Viene in genere implementato dall'origine dati, che tronca i dati prima di restituirlo attraverso la rete. Driver e origini dati non è necessario lo supporta. Pertanto, per garantire che i dati vengono troncati a una determinata dimensione, deve allocare un buffer di dimensione e specificare le dimensioni in un'applicazione di *BufferLength* argomento.  
  
4.  Converte i dati nel tipo specificato in *TargetType*. I dati ha la precisione predefinita e la scala per tale tipo di dati. Se *TargetType* è SQL_ARD_TYPE, i dati di tipo nel campo SQL_DESC_CONCISE_TYPE del ARD viene utilizzato. Se *TargetType* è SQL_ARD_TYPE, i dati ha precisione e scala nel SQL_DESC_DATETIME_INTERVAL_PRECISION, SQL_DESC_PRECISION, e digitare il SQL_DESC_CONCISE campi SQL_DESC_SCALE del ARD, a seconda dei dati Campo Type. Se qualsiasi precisione predefinita o la scala non è appropriata, l'applicazione deve impostare in modo esplicito il campo di descrizione appropriato da una chiamata a **SQLSetDescField** o **SQLSetDescRec**.  
  
5.  Se i dati è stati convertiti in un tipo di dati a lunghezza variabile, ad esempio carattere o binario, **SQLGetData** controlla se supera la lunghezza dei dati *BufferLength*. Se supera la lunghezza dei dati di carattere (incluso il carattere di terminazione null) *BufferLength*, **SQLGetData** tronca i dati da *BufferLength* minore della lunghezza di un carattere di terminazione null. Quindi null termina i dati. Se la lunghezza dei dati binari supera la lunghezza del buffer di dati, **SQLGetData** tronca a *BufferLength* byte.  
  
     Se il buffer di dati fornito è troppo piccolo per contenere il carattere di terminazione null, **SQLGetData** restituisce SQL_SUCCESS_WITH_INFO e SQLSTATE 01004.  
  
     **SQLGetData** mai tronca i dati convertiti in dati a lunghezza fissa tipi; sempre, si presuppone che la lunghezza di **TargetValuePtr* è la dimensione del tipo di dati.  
  
6.  Inserisce i dati convertiti (e probabilmente troncati) in \* *TargetValuePtr*. Si noti che **SQLGetData** non possono restituire dati da una riga.  
  
7.  Inserisce la lunghezza dei dati in \* *StrLen_or_IndPtr*. Se *StrLen_or_IndPtr* era un puntatore null, **SQLGetData** non restituisce la lunghezza.  
  
    -   Per dati carattere o binario, questa è la lunghezza dei dati dopo la conversione e prima di troncamento a causa di *BufferLength*. Se il driver non è possibile determinare la lunghezza dei dati dopo la conversione, come accade a volte con dati di tipo long, restituisce SQL_SUCCESS_WITH_INFO e imposta la lunghezza SQL_NO_TOTAL. (L'ultima chiamata a **SQLGetData** devono restituire sempre la lunghezza dei dati, non zero o SQL_NO_TOTAL.) Se i dati sono stati troncati a causa dell'istruzione SQL_ATTR_MAX_LENGTH attributo, il valore di questo attributo, anziché la lunghezza effettiva, viene inserito nella \* *StrLen_or_IndPtr*. Questo avviene perché l'attributo è progettato per troncare i dati nel server prima della conversione, in modo il driver non è in grado di determinare quali la lunghezza effettiva è. Quando **SQLGetData** viene chiamato più volte in successione per la stessa colonna, si tratta della lunghezza dei dati disponibili all'inizio della chiamata corrente; ovvero, la lunghezza diminuisce con ogni chiamata successiva.  
  
    -   Per tutti gli altri tipi di dati, si tratta della lunghezza dei dati dopo la conversione. che è la dimensione del tipo a cui è stati convertiti i dati.  
  
8.  Se i dati vengono troncati senza perdita di significato durante la conversione (ad esempio, il numero reale 1,234 viene troncato quando convertito all'intero 1) o perché *BufferLength* è troppo piccolo (ad esempio, la stringa "abcdef" viene inserita in un buffer a 4 byte), **SQLGetData** restituisce SQLSTATE 01004 (dati troncati) e SQL_SUCCESS_WITH_INFO. Se i dati vengono troncati senza perdita di significato a causa dell'attributo di istruzione, SQL_ATTR_MAX_LENGTH **SQLGetData** restituisce SQL_SUCCESS e non restituisce SQLSTATE 01004 (dati troncati).  
  
 Il contenuto del buffer di dati associati (se **SQLGetData** viene chiamato su una colonna associata) e il buffer di lunghezza/indicatore sono indefiniti se **SQLGetData** non restituisce SQL_SUCCESS o SQL_SUCCESS_WITH_INFO.  
  
 Le chiamate successive a **SQLGetData** recupererà i dati dall'ultima colonna richiesto; offset precedente diventano non valide. Ad esempio, quando viene eseguita la sequenza seguente:  
  
```  
SQLGetData(icol=n), SQLGetData(icol=m), SQLGetData(icol=n)  
```  
  
 la seconda chiamata a SQLGetData(icol=n) recupera i dati dall'inizio della colonna n. Qualsiasi offset nei dati a causa di precedenti chiamate a **SQLGetData** per la colonna non è più valida.  
  
## <a name="descriptors-and-sqlgetdata"></a>Descrittori e SQLGetData  
 **SQLGetData** non interagisce direttamente con tutti i campi di descrizione.  
  
 Se *TargetType* è SQL_ARD_TYPE, i dati di tipo nel campo SQL_DESC_CONCISE_TYPE del ARD viene utilizzato. Se *TargetType* è SQL_ARD_TYPE o SQL_C_DEFAULT, i dati ha precisione e scala nel SQL_DESC_DATETIME_INTERVAL_PRECISION, SQL_DESC_PRECISION, e i campi SQL_DESC_SCALE del ARD, a seconda dei dati tipo nel campo SQL_DESC_CONCISE_TYPE.  
  
## <a name="code-example"></a>Esempio di codice  
 Nell'esempio seguente, un'applicazione esegue un **selezionare** istruzione per restituire un set di risultati del cliente ID, nomi e numeri ordinati per nome, ID e il numero di telefono del cellulare. Per ogni riga di dati, viene chiamata **SQLFetch** per posizionare il cursore alla riga successiva. Chiama **SQLGetData** per recuperare i dati recuperati; il buffer dei dati e il numero di byte restituito specificato nella chiamata a **SQLGetData**. Infine, viene stampato un nome, ID e il numero di telefono di ogni dipendente.  
  
```  
#define NAME_LEN 50  
#define PHONE_LEN 50  
  
SQLCHAR      szName[NAME_LEN], szPhone[PHONE_LEN];  
SQLINTEGER   sCustID, cbName, cbAge, cbBirthday;  
SQLRETURN    retcode;  
SQLHSTMT     hstmt;  
  
retcode = SQLExecDirect(hstmt,  
   "SELECT CUSTID, NAME, PHONE FROM CUSTOMERS ORDER BY 2, 1, 3",  
   SQL_NTS);  
  
if (retcode == SQL_SUCCESS) {  
   while (TRUE) {  
      retcode = SQLFetch(hstmt);  
      if (retcode == SQL_ERROR || retcode == SQL_SUCCESS_WITH_INFO) {  
         show_error();  
      }  
      if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO){  
  
         /* Get data for columns 1, 2, and 3 */  
  
         SQLGetData(hstmt, 1, SQL_C_ULONG, &sCustID, 0, &cbCustID);  
         SQLGetData(hstmt, 2, SQL_C_CHAR, szName, NAME_LEN, &cbName);  
         SQLGetData(hstmt, 3, SQL_C_CHAR, szPhone, PHONE_LEN,  
            &cbPhone);  
  
         /* Print the row of data */  
  
         fprintf(out, "%-5d %-*s %*s", sCustID, NAME_LEN-1, szName,   
            PHONE_LEN-1, szPhone);  
      } else {  
         break;  
      }  
   }  
}  
```  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Assegnazione di archiviazione per una colonna in un set di risultati|[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Esecuzione di operazioni bulk che non riguardano la posizione del cursore blocco|[SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|L'elaborazione di istruzione di annullamento|[SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Esecuzione di un'istruzione SQL|[SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|L'esecuzione di un'istruzione SQL preparata|[SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Recupero di un blocco di dati o di scorrimento di un risultato impostato|[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Recupero di una singola riga di dati o un blocco di dati in una direzione forward-only|[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|L'invio di dati del parametro in fase di esecuzione|[SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|  
|Posizionando il cursore, l'aggiornamento dei dati del set di righe o l'aggiornamento o eliminazione di dati nel set di righe|[SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Recupero di parametri di output tramite SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)
