---
title: Funzione SQLMoreResults | Documenti Microsoft
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
- SQLMoreResults
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLMoreResults
helpviewer_keywords:
- SQLMoreResults function [ODBC]
ms.assetid: bf169ed5-4d55-412c-b184-12065a726e89
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 772bfd3d05d620840ea43c9f1313b4d94add10de
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlmoreresults-function"></a>Funzione SQLMoreResults
**Conformità**  
 Introdotta: versione ODBC standard 1.0 conformità: ODBC  
  
 **Riepilogo**  
 **SQLMoreResults** determina se sono disponibili in un'istruzione contenente altri risultati **selezionare**, **aggiornamento**, **inserire**, o  **ELIMINARE** istruzioni e, in caso affermativo, inizializza l'elaborazione per i risultati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLMoreResults(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>Argomenti  
 *StatementHandle*  
 [Input] Handle di istruzione.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_NO_DATA, SQL_ERROR, SQL_INVALID_HANDLE O SQL_PARAM_DATA_AVAILABLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLMoreResults** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato possono essere ottenuti chiamando **SQLGetDiagRec** con un *HandleType* di SQL _HANDLE_STMT e *gestire* di *StatementHandle*. Nella tabella seguente sono elencati i valori SQLSTATE comunemente restituiti da **SQLMoreResults** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01S02|Valore dell'opzione è stata modificata|Il valore di un attributo di istruzione sono cambiato, come il batch è stato elaborato. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|08S01|Errore del collegamento di comunicazione|Collegamento di comunicazione tra il driver e l'origine dati a cui era connesso il driver non è stato possibile prima dell'elaborazione della funzione è stata completata.|  
|40001|Errore di serializzazione.|La transazione viene annullata a causa di un deadlock delle risorse con un'altra transazione.|  
|40003|Completamento delle istruzioni sconosciuto|Impossibile stabilire la connessione associata durante l'esecuzione di questa funzione e non è possibile determinare lo stato della transazione.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel  *\*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver è stato in grado di allocare la memoria necessaria per supportare l'esecuzione o il completamento della funzione.|  
|HY008|Operazione annullata|L'elaborazione asincrona è stata abilitata per il *StatementHandle*. Il **SQLMoreResults** funzione e, prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle* . Il **SQLMoreResults** funzione è stata chiamata nuovamente sul *StatementHandle*.<br /><br /> Il **SQLMoreResults** funzione e, prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle*  da un thread diverso in un'applicazione multithread.|  
|HY010|Errore nella sequenza (funzione)|(DM) a cui è stata chiamata per l'handle di connessione associata a una funzione in modo asincrono in esecuzione il *StatementHandle*. Questa funzione asincrona era ancora in esecuzione quando il **SQLMoreResults** funzione è stata chiamata.<br /><br /> (DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione (non è presente uno) di *StatementHandle* ed era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos** è stato chiamato per il  *StatementHandle* e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima che sono stati inviati dati per tutti i parametri data-at-execution o colonne.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|Il driver (DM) associato il *StatementHandle* non supporta la funzione.|  
|IM017|Polling è disabilitato in modalità di notifica asincrona|Ogni volta che viene utilizzato il modello di notifica, il polling è disabilitato.|  
|IM018|**SQLCompleteAsync** non è stato chiamato per completare l'operazione asincrona precedente su questo handle.|Se la chiamata di funzione precedente dell'handle restituisce SQL_STILL_EXECUTING e se è abilitata la modalità di notifica, **SQLCompleteAsync** deve essere chiamato per l'handle per eseguire la post-elaborazione e completare l'operazione.|  
  
## <a name="comments"></a>Commenti  
 **Selezionare** istruzioni restituiscono set di risultati. **AGGIORNAMENTO**, **inserire**, e **eliminare** istruzioni restituiscono un conteggio delle righe interessate. Se una di queste istruzioni vengono eseguite in batch, inviato con le matrici di parametri (numerati in ordine di parametro, nell'ordine in cui appaiono nel batch crescente) o in procedure, possono restituire più set di risultati o conteggio delle righe. Per informazioni su batch di istruzioni e le matrici di parametri, vedere [batch di istruzioni SQL](../../../odbc/reference/develop-app/batches-of-sql-statements.md) e [matrici di valori di parametro](../../../odbc/reference/develop-app/arrays-of-parameter-values.md).  
  
 Dopo l'esecuzione del batch, l'applicazione viene posizionato sul primo set di risultati. L'applicazione può chiamare **SQLBindCol**, **SQLBulkOperations**, **SQLFetch**, **SQLGetData**, **SQLFetchScroll** , **SQLSetPos**e tutte le funzioni di metadati, nel set di risultati prima o i successivi, come se fossero solo un singolo set di risultati. Una volta eseguita con il primo set di risultati, l'applicazione chiama **SQLMoreResults** per spostare in set di risultati successivo. Se è disponibile, un altro set di risultati o conteggio **SQLMoreResults** restituisce SQL_SUCCESS e inizializza il set di risultati o conteggio per un'ulteriore elaborazione. Se tutte le istruzioni di generazione: conteggio righe viene visualizzato tra provocare: generazione di set di istruzioni, può essere eseguiti da una chiamata **SQLMoreResults**. Dopo la chiamata **SQLMoreResults** per **aggiornamento**, **inserire**, o **eliminare** istruzioni, un'applicazione può chiamare **SQLRowCount**.  
  
 Se si è verificato un set con le righe di risultati correnti **SQLMoreResults** elimina tale set di risultati e rende il successivo set di risultati o conteggio disponibili. Se sono stati elaborati tutti i risultati, **SQLMoreResults** restituisce SQL_NO_DATA. Per alcuni driver, i parametri di output e valori restituiti non sono disponibili fino a quando non sono stati elaborati tutti i set di risultati e i conteggi delle righe. Per tale driver, i parametri di output e restituire valori diventi disponibili quando **SQLMoreResults** restituisce SQL_NO_DATA.  
  
 Tutti i binding sono stati stabiliti per precedenti set di risultati ancora restano validi. Se le strutture di colonna sono diverse per il set di risultati, chiamare **SQLFetch** o **SQLFetchScroll** può comportare un errore o un troncamento. Per evitare questo problema, l'applicazione deve chiamare **SQLBindCol** riassociare come appropriato (o esplicitamente a tale scopo, impostare i campi di descrizione). In alternativa, l'applicazione può chiamare **SQLFreeStmt** con un *opzione* su SQL_UNBIND per separare tutti i buffer di colonna.  
  
 Possono modificare i valori degli attributi di istruzione, ad esempio tipo di cursore, concorrenza dei cursori, dimensione del keyset o la lunghezza massima, mentre l'applicazione passa da batch dalle chiamate a **SQLMoreResults**. In questo caso, **SQLMoreResults** restituirà SQL_SUCCESS_WITH_INFO e SQLSTATE 01S02 (valore dell'opzione modificata).  
  
 La chiamata **SQLCloseCursor**, o **SQLFreeStmt** con un *opzione* di SQL_CLOSE, Elimina tutti i set di risultati e i conteggi delle righe che non erano disponibili in seguito l'esecuzione di il batch. L'handle di istruzione restituisce lo stato allocato o preparato. La chiamata **SQLCancel** per annullare una funzione in modo asincrono in esecuzione quando un batch è stato eseguito e l'handle di istruzione è in esecuzione, cursore posizionato, o lo stato asincrono comporta set di tutti i risultati e conteggio delle righe generato dal batch vengano eliminati se la chiamata di annullamento ha avuto esito positivo. L'istruzione restituisce quindi nello stato prepared o allocato.  
  
 Se un batch di istruzioni o una stored procedure sono presenti altre istruzioni SQL con **selezionare**, **aggiornamento**, **inserire**, e **eliminare** istruzioni Queste istruzioni altri non influiscono **SQLMoreResults**.  
  
 Per ulteriori informazioni, vedere [più risultati](../../../odbc/reference/develop-app/multiple-results.md).  
  
 Se una ricerca di aggiornarla, inserisce o Elimina l'istruzione in un batch di istruzioni non influiscono su tutte le righe nell'origine dati, **SQLMoreResults** restituisce SQL_SUCCESS. Questo comportamento è diverso da quello di un aggiornamento con ricerca, inserire o eliminare l'istruzione che viene eseguita tramite **SQLExecDirect**, **SQLExecute**, o **SQLParamData**, che Se non si applica tutte le righe nell'origine dati non restituisce SQL_NO_DATA. Se un'applicazione chiama **SQLRowCount** per recuperare il conteggio delle righe dopo una chiamata a **SQLMoreResults** non interessa tutte le righe, **SQLRowCount** restituisce SQL_NO_DATA.  
  
 Per ulteriori informazioni sulla sequenza valida di funzioni di elaborazione dei risultati, vedere [tabelle di transizione dello stato di appendice b: ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Per ulteriori informazioni su SQL_PARAM_DATA_AVAILABLE e parametri di flusso di output, vedere [il recupero dei parametri di Output tramite SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
## <a name="availability-of-row-counts"></a>Disponibilità dei conteggi delle righe  
 Quando un batch contiene più istruzioni di creazione di conteggio righe consecutive, è possibile che questi conteggi delle righe vengono raggruppate nel conteggio di una sola riga. Ad esempio, se un batch ha cinque istruzioni insert, determinate origini dati sono in grado di restituire i conteggi di cinque righe singole. Alcune altre origini dati restituiscono solo un conteggio che rappresenta la somma dei conteggi delle righe singole cinque.  
  
 Quando un batch contiene una combinazione di set-generazione di risultati e istruzioni di generazione: numero di righe, i conteggi delle righe possono o potrebbe non essere disponibili a tutti. Il comportamento del driver per quanto riguarda la disponibilità di conteggio delle righe viene enumerato nel tipo di informazioni SQL_BATCH_ROW_COUNT disponibile tramite una chiamata a **SQLGetInfo**. Ad esempio, si supponga che il batch contiene un **selezionare**, seguito da due **inserire**s e un altro **selezionare**. Quindi possono verificarsi i casi seguenti:  
  
-   Il conteggio delle righe corrispondenti ai due **inserire** istruzioni non sono tutti disponibili. La prima chiamata a **SQLMoreResults** verrà posizionato nel set di risultati del secondo è **selezionare** istruzione.  
  
-   Il conteggio delle righe corrispondenti ai due **inserire** sono disponibili istruzioni singolarmente. (Una chiamata a **SQLGetInfo** non restituisce il bit SQL_BRC_ROLLED_UP per il tipo di informazioni SQL_BATCH_ROW_COUNT.) La prima chiamata a **SQLMoreResults** verrà è posizionato sul conteggio delle righe del primo **inserire**, e la seconda chiamata verrà posizionato sul conteggio delle righe del secondo **inserire**. La terza chiamata a **SQLMoreResults** verrà posizionato nel set di risultati del secondo è **selezionare** istruzione.  
  
-   Il conteggio delle righe corrispondenti ai due **inserisce** vengono raggruppate in un numero di singola riga che è disponibile. (Una chiamata a **SQLGetInfo** restituisce il SQL_BRC_ROLLED_UP bit per il tipo di informazioni SQL_BATCH_ROW_COUNT.) La prima chiamata a **SQLMoreResults** si verrà posizionato il conteggio delle righe di roll-up e la seconda chiamata a **SQLMoreResults** verrà posizionato nel set di risultati del secondo è **selezionare**.  
  
 Alcuni driver rendono i conteggi delle righe è disponibile solo per i batch esplicita e non per le stored procedure.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|L'elaborazione di istruzione di annullamento|[Funzione SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Recupero di un blocco di dati o di scorrimento di un risultato impostato|[Funzione SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Recupero di una singola riga o un blocco di dati in una direzione forward-only|[Funzione SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Il recupero o parte di una colonna di dati|[Funzione SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Il recupero dei parametri di Output tramite SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)

