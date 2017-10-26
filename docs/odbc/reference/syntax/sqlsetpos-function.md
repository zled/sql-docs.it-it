---
title: Funzione SQLSetPos | Documenti Microsoft
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
- SQLSetPos
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetPos
helpviewer_keywords:
- SQLSetPos function [ODBC]
ms.assetid: 80190ee7-ae3b-45e5-92a9-693eb558f322
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6140625da489bcb573b3beb4ca2be0838805f8d5
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetpos-function"></a>Funzione SQLSetPos
**Conformità**  
 Introdotta: versione ODBC standard 1.0 conformità: ODBC  
  
 **Riepilogo**  
 **SQLSetPos** imposta la posizione del cursore in un set di righe e consente a un'applicazione per aggiornare i dati nel set di righe o aggiornare o eliminare dati nel set di risultati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLSetPos(  
      SQLHSTMT        StatementHandle,  
      SQLSETPOSIROW   RowNumber,  
      SQLUSMALLINT    Operation,  
      SQLUSMALLINT    LockType);  
```  
  
## <a name="arguments"></a>Argomenti  
 *StatementHandle*  
 [Input] Handle di istruzione.  
  
 *RowNumber*  
 [Input] Posizione della riga nel set di righe su cui eseguire l'operazione specificata con il *operazione* argomento. Se *RowNumber* è 0, l'operazione si applica a tutte le righe nel set di righe.  
  
 Per ulteriori informazioni, vedere "Commenti".  
  
 *Operazione*  
 [Input] Operazione da eseguire:  
  
 SQL_POSITION SQL_REFRESH SQL_UPDATE SQL_DELETE  
  
> [!NOTE]  
>  Il valore SQL_ADD per il *operazione* argomento è stato deprecato per ODBC 3*x*. ODBC 3. *x* driver necessario supportare SQL_ADD per compatibilità con le versioni precedenti. Questa funzionalità è stata sostituita da una chiamata a **SQLBulkOperations** con un *operazione* di SQL_ADD. Quando un'applicazione ODBC 3. *x* applicazione funziona con un'API ODBC 2.* x* driver, Driver Manager esegue il mapping di una chiamata a **SQLBulkOperations** con un *operazione* di SQL_ADD a **SQLSetPos** con un * Operazione* di SQL_ADD.  
  
 Per ulteriori informazioni, vedere "Commenti".  
  
 *Tipo di blocco*  
 [Input] Specifica la modalità di blocco di riga dopo aver eseguito l'operazione specificata nel *operazione* argomento.  
  
 SQL_LOCK_NO_CHANGE SQL_LOCK_EXCLUSIVE SQL_LOCK_UNLOCK  
  
 Per ulteriori informazioni, vedere "Commenti".  
  
 **Restituisce**  
  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_STILL_EXECUTING, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLSetPos** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato possono essere ottenuti chiamando **SQLGetDiagRec** con un *HandleType* di SQL _ HANDLE_STMT e *gestire* di *StatementHandle*. Nella tabella seguente sono elencati i valori SQLSTATE comunemente restituiti da **SQLSetPos** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
 Per tutti questi SQLSTATE restituiti SQL_SUCCESS_WITH_INFO o SQL_ERROR (eccetto SQLSTATE 01xxx), viene restituito SQL_SUCCESS_WITH_INFO, se si verifica un errore in uno o più, ma non tutte le righe di un'operazione su più righe e viene restituito SQL_ERROR se si verifica un errore in un riga singola operazione.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01001|Conflitto dell'operazione del cursore|Il *operazione* argomento è stato SQL_DELETE o SQL_UPDATE e nessuna riga o più righe eliminate o aggiornate. (Per ulteriori informazioni sugli aggiornamenti per più di una riga, vedere la descrizione del SQL_ATTR_SIMULATE_CURSOR *attributo* in **SQLSetStmtAttr**.) (Funzione restituisce SQL_SUCCESS_WITH_INFO).<br /><br /> Il *operazione* argomento è stato SQL_DELETE o SQL_UPDATE e l'operazione non riuscita a causa della concorrenza ottimistica. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01004|Troncamento a destra dei dati stringa|Il *operazione* argomento è stato SQL_REFRESH e stringa o dati binari restituiti per una o più colonne con un tipo di dati SQL_C_CHAR o SQL_C_BINARY ha comportato il troncamento di un carattere non vuoto o dati binari non NULL.|  
|01S01|Errore alla riga|Il *RowNumber* argomento è 0, e si è verificato un errore in uno o più righe durante l'esecuzione dell'operazione specificata con il *operazione* argomento.<br /><br /> (SQL_SUCCESS_WITH_INFO viene restituito se si verifica un errore in uno o più, ma non tutte le righe di un'operazione su più righe e viene restituito SQL_ERROR se si verifica un errore in un'operazione a riga singola).<br /><br /> (Questo SQLSTATE viene restituito solo quando **SQLSetPos** viene chiamato dopo **SQLExtendedFetch**, se il driver è un'API ODBC 2.* x* driver e la libreria di cursori non viene utilizzato.)|  
|01S07|Troncamento frazionario.|Il *operazione* argomento era SQL_REFRESH, il tipo di dati del buffer di applicazione non è stata SQL_C_CHAR o SQL_C_BINARY e i dati restituiti al buffer dell'applicazione per una o più colonne è stati troncati. Per i tipi di dati numerici, la parte frazionaria del numero è stata troncata. Per ora, timestamp e tipi di dati di intervallo contenente un componente di ora, la parte frazionaria del tempo è stata troncata.<br /><br /> (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|07006|Violazione dell'attributo del tipo di dati|Impossibile convertire il valore di dati di una colonna nel set di risultati per il tipo di dati specificato da *TargetType* nella chiamata a **SQLBindCol**.|  
|07009|Indice del descrittore non valido|L'argomento *operazione* era SQL_REFRESH o SQL_UPDATE e una colonna è stata associata con un numero di colonne maggiore del numero di colonne nel set di risultati.|  
|21S02|Il grado della tabella derivata non corrisponde all'elenco di colonne|L'argomento *operazione* stato SQL_UPDATE, e nessuna colonna aggiornabile perché tutte le colonne sono stati sia non associata di sola lettura, o il valore nel buffer di lunghezza/indicatore associato è stato SQL_COLUMN_IGNORE.|  
|22001|Stringa di dati, troncamento a destra|Il *operazione* argomento è stato SQL_UPDATE e l'assegnazione di un carattere o un valore binario a una colonna ha comportato il troncamento di non vuoto (per i caratteri) o non null (per i dati binari) caratteri o byte.|  
|22003|Valore numerico non compreso nell'intervallo|L'argomento *operazione* era SQL_UPDATE e l'assegnazione di un valore numerico a una colonna nel set di risultati ha causato la parte intera (in contrapposizione frazionari) del numero da troncare.<br /><br /> L'argomento *operazione* era SQL_REFRESH e restituire il valore numerico per uno o più colonne associate avrebbe causato una perdita di cifre significative.|  
|22007|Formato di datetime non valido|L'argomento *operazione* era SQL_UPDATE, e l'assegnazione di un valore date o timestamp a una colonna nel set di risultati ha causato l'anno, mese o campo giorno sia compreso nell'intervallo.<br /><br /> L'argomento *operazione* era SQL_REFRESH e restituire il valore di date o timestamp per una o più colonne associate avrebbe causato l'anno, mese o campo giorno sia compreso nell'intervallo.|  
|22008|Overflow del campo Data/ora|Il *operazione* argomento è stato SQL_UPDATE e le prestazioni di operazioni aritmetiche sui dati inviati a una colonna nel set di risultati datetime ha comportato un campo datetime (anno, mese, giorno, ora, minuto o secondo campo) dei risultati compreso nell'intervallo consentito di valori per il campo o non sono validi in base alle regole di naturale del calendario gregoriano per date e ore.<br /><br /> Il *operazione* argomento è stato SQL_REFRESH e le prestazioni di operazioni aritmetiche sui dati recuperati dal set di risultati datetime ha comportato un campo datetime (anno, mese, giorno, ora, minuto o secondo campo) dei risultati compreso nell'intervallo consentito di valori per il campo o non sono validi in base alle regole di naturale del calendario gregoriano per date e ore.|  
|22015|Overflow del campo intervallo|Il *operazione* argomento era SQL_UPDATE, e l'assegnazione di un numerico esatto o il tipo di intervallo C a un intervallo di tipo di dati SQL ha causato una perdita di cifre significative.<br /><br /> Il *operazione* argomento SQL_UPDATE, quando si assegna a un intervallo di tipo SQL, si è verificato alcuna rappresentazione del valore di tipo C nell'intervallo di tipo SQL.<br /><br /> Il *operazione* argomento è stato SQL_REFRESH e l'assegnazione da un numerico esatto o l'intervallo di tipo SQL a un tipo di intervallo C ha causato una perdita di cifre significative nel campo iniziale.<br /><br /> Il *operazione* argomento SQL _ Aggiorna, quando si assegna a un tipo di intervallo C, si è verificato alcun rappresentazione del valore di tipo SQL nel tipo di intervallo C.|  
|22018|Valore di carattere non valido per la specifica del cast|Il *operazione* argomento è stato SQL_REFRESH; il tipo C è stato un numerico esatto o approssimativo, un valore datetime o un tipo di dati di intervallo; il tipo SQL della colonna è un tipo di dati character; e il valore nella colonna non è un valore letterale valido del associazione di tipo C.<br /><br /> L'argomento *operazione* stato SQL_UPDATE; il tipo SQL è un numerico esatto o approssimativo, un valore datetime o un tipo di dati di intervallo; il tipo C è SQL_C_CHAR; e il valore nella colonna non è un valore letterale valido del tipo SQL associato.|  
|23000|Violazione del vincolo di integrità|L'argomento *operazione* era SQL_DELETE o SQL_UPDATE e violato un vincolo di integrità.|  
|24000|Stato del cursore non valido|Il *StatementHandle* è stato eseguito, ma è stato associato alcun set di risultati di *StatementHandle*.<br /><br /> (DM) un cursore è stato aperto nel *StatementHandle*, ma **SQLFetch** o **SQLFetchScroll** non è stato chiamato.<br /><br /> Un cursore è stato aperto nel *StatementHandle*, e **SQLFetch** o **SQLFetchScroll** fosse stata chiamata, ma è stato posizionato il cursore prima dell'inizio del set di risultati o dopo la fine del set di risultati.<br /><br /> L'argomento *operazione* era SQL_DELETE, SQL_REFRESH o SQL_UPDATE e il cursore è posizionato prima dell'inizio del set di risultati o dopo la fine del set di risultati.|  
|40001|Errore di serializzazione.|La transazione viene annullata a causa di un deadlock delle risorse con un'altra transazione.|  
|40003|Completamento delle istruzioni sconosciuto|Impossibile stabilire la connessione associata durante l'esecuzione di questa funzione e non è possibile determinare lo stato della transazione.|  
|42000|Sintassi o violazione di accesso|Il driver è stato in grado di bloccare la riga in base alle esigenze per eseguire l'operazione richiesta nell'argomento *operazione*.<br /><br /> Il driver è stato in grado di bloccare la riga come richiesto nell'argomento *LockType*.|  
|44000|Violazione della clausola WITH CHECK OPTION|Il *operazione* argomento era SQL_UPDATE e l'aggiornamento è stata eseguita su una tabella visualizzata o una tabella derivata dalla tabella visualizzata di cui è stata creata specificando **WITH CHECK OPTION**, in modo che una o più righe interessati l'aggiornamento non saranno presente nella tabella visualizzata.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel * \*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver è stato in grado di allocare la memoria necessaria per supportare l'esecuzione o il completamento della funzione.|  
|HY008|Operazione annullata|L'elaborazione asincrona è stata abilitata per il *StatementHandle*. La funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle*, e quindi è stata chiamata la funzione nuovo di *StatementHandle*.<br /><br /> La funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle* da un thread diverso in un applicazioni multithread.|  
|HY010|Errore nella sequenza (funzione)|(DM) a cui è stata chiamata per l'handle di connessione associata a una funzione in modo asincrono in esecuzione il *StatementHandle*. Questa funzione asincrona era ancora in esecuzione quando è stata chiamata la funzione SQLSetPos.<br /><br /> (DM) specificato *StatementHandle* non è stato eseguito. La funzione è stata chiamata senza chiamare prima il metodo **SQLExecDirect**, **SQLExecute**, o una funzione di catalogo.<br /><br /> (DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione (non è presente uno) di *StatementHandle* ed era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos** è stato chiamato per il * StatementHandle* e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima che sono stati inviati dati per tutti i parametri data-at-execution o colonne.<br /><br /> (DM) il driver non è un'API ODBC 2. *x* driver, e **SQLSetPos** è stato chiamato per un *StatementHandle* dopo **SQLFetch** è stato chiamato.|  
|HY011|Impossibile impostare l'attributo ora|(DM) il driver non è un'API ODBC 2. *x* driver; il SQL_ATTR_ROW_STATUS_PTR è stato impostato l'attributo di istruzione; quindi **SQLSetPos** è stato chiamato prima di **SQLFetch**, **SQLFetchScroll**, o **SQLExtendedFetch** è stato chiamato.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY090|Lunghezza di stringa o di buffer non valida|Il *operazione* argomento era SQL_UPDATE, un valore di dati è un puntatore null e il valore di lunghezza di colonna non è 0, SQL_DATA_AT_EXEC, SQL_COLUMN_IGNORE, SQL_NULL_DATA, o minore o uguale a SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> Il *operazione* argomento è stato SQL_UPDATE; un valore di dati non è un puntatore null; è stato il tipo di dati C SQL_C_BINARY o SQL_C_CHAR; e il valore di lunghezza di colonna è minore di 0 ma non uguale a SQL_DATA_AT_EXEC, SQL_COLUMN_IGNORE , SQL_NTS o SQL_NULL_DATA, o minore o uguale a SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> Il valore in un buffer di lunghezza/indicatore era SQL_DATA_AT_EXEC; il tipo SQL non SQL_LONGVARCHAR, SQL_LONGVARBINARY o un tipo di dati specifici dell'origine dati di tipo long; e il tipo di informazioni SQL_NEED_LONG_DATA_LEN in **SQLGetInfo** è "Y".|  
|HY092|Identificatore di attributo non valido|(DM) il valore specificato per il *operazione* argomento non valido.<br /><br /> (DM) il valore specificato per il *LockType* argomento non valido.<br /><br /> Il *operazione* argomento è stato SQL_UPDATE o SQL_DELETE e l'attributo di istruzione SQL_ATTR_CONCURRENCY stato SQL_ATTR_CONCUR_READ_ONLY.|  
|HY107|Valore di riga non compreso nell'intervallo|Il valore specificato per l'argomento *RowNumber* è maggiore del numero di righe nel set di righe.|  
|HY109|Posizione del cursore non valido|Il cursore associato di *StatementHandle* è stato definito come forward-only, pertanto non può essere posizionato il cursore all'interno del set di righe. Vedere la descrizione per l'attributo SQL_ATTR_CURSOR_TYPE in **SQLSetStmtAttr**.<br /><br /> Il *operazione* argomento è stato SQL_UPDATE, SQL_DELETE o SQL_REFRESH e identificate la riga di *RowNumber* argomento è stato eliminato o non era stata recuperata.<br /><br /> (DM) il *RowNumber* argomento è 0 e *operazione* argomento era SQL_POSITION.<br /><br /> **SQLSetPos** è stato chiamato dopo **SQLBulkOperations** è stato chiamato e prima **SQLFetchScroll** o **SQLFetch** è stato chiamato.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Funzionalità facoltativa non implementata.|L'origine dati o driver non supporta l'operazione richiesta nel *operazione* argomento o *LockType* argomento.|  
|HYT00|Timeout|Il periodo di timeout della query è scaduto prima che l'origine dati ha restituito il set di risultati. Il periodo di timeout viene impostato tramite **SQLSetStmtAttr** con un *attributo* di SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|Il driver (DM) associato il *StatementHandle* non supporta la funzione.|  
|IM017|Polling è disabilitato in modalità di notifica asincrona|Ogni volta che viene utilizzato il modello di notifica, il polling è disabilitato.|  
|IM018|**SQLCompleteAsync** non è stato chiamato per completare l'operazione asincrona precedente su questo handle.|Se la chiamata di funzione precedente dell'handle restituisce SQL_STILL_EXECUTING e se è abilitata la modalità di notifica, **SQLCompleteAsync** deve essere chiamato per l'handle per eseguire la post-elaborazione e completare l'operazione.|  
  
## <a name="comments"></a>Commenti  
  
> [!CAUTION]  
>  Per informazioni sull'istruzione gli Stati che **SQLSetPos** può essere chiamato in ed è necessario eseguire per la compatibilità con ODBC 2*x* applicazioni, vedere [cursori a blocchi, i cursori scorrevoli, e Compatibilità con le versioni precedenti](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md).  
  
## <a name="rownumber-argument"></a>Argomento RowNumber  
 Il *RowNumber* argomento specifica il numero della riga nel set di righe su cui eseguire l'operazione specificata il *operazione* argomento. Se *RowNumber* è 0, l'operazione si applica a tutte le righe nel set di righe. *RowNumber* deve essere un valore compreso tra 0 e il numero di righe nel set di righe.  
  
> [!NOTE]  
>  Nel linguaggio C, le matrici sono basate su 0 e *RowNumber* argomento è basato su 1. Ad esempio, per aggiornare la quinta riga del set di righe, un'applicazione modifica i buffer di set di righe in corrispondenza dell'indice di matrice 4 ma specifica un *RowNumber* pari a 5.  
  
 Tutte le operazioni di posizionare il cursore sulla riga specificata da *RowNumber*. Le operazioni seguenti richiedono una posizione del cursore:  
  
-   Aggiornamento posizionato e istruzioni delete.  
  
-   Le chiamate a **SQLGetData**.  
  
-   Le chiamate a **SQLSetPos** con le opzioni SQL_DELETE e SQL_REFRESH SQL_UPDATE.  
  
 Ad esempio, se *RowNumber* è 2 per una chiamata a **SQLSetPos** con un *operazione* di SQL_DELETE, il cursore viene posizionato nella seconda riga del set di righe e viene eliminata. La voce nell'implementazione riga stato matrice (a cui puntata l'attributo di istruzione vengono impostati SQL_ATTR_ROW_STATUS_PTR) per la seconda riga viene modificata in SQL_ROW_DELETED.  
  
 Un'applicazione può specificare una posizione del cursore quando si chiama **SQLSetPos**. In genere, viene chiamato **SQLSetPos** con l'operazione SQL_POSITION o SQL_REFRESH per posizionare il cursore prima di eseguire un posizionamento aggiornare o eliminare l'istruzione o la chiamata **SQLGetData**.  
  
## <a name="operation-argument"></a>Argomento dell'operazione  
 Il *operazione* argomento supporta le operazioni seguenti. Per determinare quali opzioni sono supportate da un'origine dati, un'applicazione chiama **SQLGetInfo** con SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 o SQL_STATIC_ Tipo di informazioni CURSOR_ATTRIBUTES1 (a seconda del tipo di cursore).  
  
|*Operazione*<br /><br /> argomento|Operazione|  
|------------------------------|---------------|  
|SQL_POSITION|Il driver posiziona il cursore sulla riga specificata da *RowNumber*.<br /><br /> Il contenuto della matrice di stato di riga a cui fa riferimento l'attributo di istruzione SQL_ATTR_ROW_OPERATION_PTR viene ignorato per il SQL_POSITION *operazione*.|  
|SQL_REFRESH|Il driver posiziona il cursore sulla riga specificata da *RowNumber* e aggiorna i dati nei buffer di set di righe per la riga. Per ulteriori informazioni su come il driver restituisce i dati nei buffer di set di righe, vedere le descrizioni di associazione per riga e colonna **SQLBindCol**.<br /><br /> **SQLSetPos** con un *operazione* di SQL_REFRESH Aggiorna lo stato e il contenuto delle righe nel set di righe recuperate corrente. Ciò include l'aggiornamento i segnalibri. Poiché i dati nei buffer di vengano aggiornati ma non refetched, l'appartenenza del set di righe è fissa. Questo comportamento è diverso dall'aggiornamento eseguita da una chiamata a **SQLFetchScroll** con un *FetchOrientation* di SQL_FETCH_RELATIVE e *RowNumber* uguale a 0, che recupera nuovamente il set di righe dal set di risultati in modo che è possibile visualizzare dati aggiunti e rimuovere i dati vengono eliminati se tali operazioni sono supportate dal driver e il cursore.<br /><br /> Un aggiornamento ha esito positivo con **SQLSetPos** non modificherà lo stato riga SQL_ROW_DELETED. Le righe eliminate nel set di righe continueranno a essere contrassegnato come eliminato finché l'operazione di recupero successiva. Le righe non verranno più visualizzato al successivo recupero se il cursore supporta la compressione (in cui una successiva **SQLFetch** o **SQLFetchScroll** non restituisce le righe eliminate).<br /><br /> Aggiunta di righe non vengono visualizzati quando un aggiornamento con **SQLSetPos** viene eseguita. Questo comportamento è diverso da **SQLFetchScroll** con un *FetchType* di SQL_FETCH_RELATIVE e *RowNumber* uguale a 0, che consente inoltre di aggiornare il set di righe corrente ma Mostra i record aggiunti o pack record eliminati se queste operazioni sono supportate dal cursore.<br /><br /> Un aggiornamento ha esito positivo con **SQLSetPos** verrà visualizzata l'indicazione dello stato di una riga di SQL_ROW_ADDED SQL_ROW_SUCCESS (se è presente la matrice di stato di riga).<br /><br /> Un aggiornamento ha esito positivo con **SQLSetPos** verrà visualizzata l'indicazione dello stato di una riga di SQL_ROW_UPDATED nuovo stato della riga (se è presente la matrice di stato di riga).<br /><br /> Se si verifica un errore un **SQLSetPos** operazione su una riga, lo stato di riga è impostato su SQL_ROW_ERROR (se è presente la matrice di stato di riga).<br /><br /> Per un cursore aperto con un attributo di istruzione SQL_ATTR_CONCURRENCY di SQL_CONCUR_ROWVER o SQL_CONCUR_VALUES, un aggiornamento con **SQLSetPos** potrebbe aggiornare i valori di concorrenza ottimistica utilizzati dall'origine dati per rilevare che il riga è stata modificata. In questo caso, le versioni di riga o i valori utilizzati per garantire una concorrenza dei cursori vengono aggiornati ogni volta che i buffer di set di righe vengono aggiornati dal server. Questo errore si verifica per ogni riga che viene aggiornato.<br /><br /> Il contenuto della matrice di stato di riga a cui fa riferimento l'attributo di istruzione SQL_ATTR_ROW_OPERATION_PTR viene ignorato per il SQL_REFRESH *operazione*.|  
|SQL_UPDATE|Il driver posiziona il cursore sulla riga specificata da *RowNumber* e aggiorna la riga di dati sottostante con i valori nei buffer di set di righe (il *TargetValuePtr* argomento ** SQLBindCol**). Recupera le lunghezze dei dati dai buffer di lunghezza/indicatore (il *StrLen_or_IndPtr* argomento **SQLBindCol**). Se la lunghezza di qualsiasi colonna SQL_COLUMN_IGNORE, la colonna non viene aggiornata. Dopo aver aggiornato la riga, il driver diventa l'elemento corrispondente della matrice di stato di riga SQL_ROW_UPDATED o SQL_ROW_SUCCESS_WITH_INFO (se è presente la matrice di stato di riga).<br /><br /> È definito dal driver che cos'è il comportamento se **SQLSetPos** con un *operazione* argomento di SQL_UPDATE viene chiamato su un cursore che include colonne duplicate. Il driver può restituire un valore SQLSTATE definito dal driver, aggiornare la prima colonna visualizzata nel set di risultati o eseguire altri comportamenti definito dal driver.<br /><br /> La matrice di operazione riga a cui fa riferimento l'attributo di istruzione SQL_ATTR_ROW_OPERATION_PTR può essere utilizzata per indicare che una riga nel set di righe corrente deve essere ignorata durante l'aggiornamento bulk. Per ulteriori informazioni, vedere "Matrici di stato e di operazione" più avanti in questo riferimento di funzione.|  
|SQL_DELETE|Il driver posiziona il cursore sulla riga specificata da *RowNumber* ed elimina la riga di dati sottostante. Modifica l'elemento corrispondente della matrice di stato di riga per SQL_ROW_DELETED. Dopo la riga è stata eliminata, le operazioni seguenti non sono valide per la riga: aggiornamento posizionato ed eliminare le istruzioni, le chiamate a **SQLGetData**e le chiamate a **SQLSetPos** con *operazione* impostato su un valore diverso da SQL_POSITION. Per i driver che supportano la compressione, la riga viene eliminata dalla posizione del cursore quando i nuovi dati vengono recuperati dall'origine dati.<br /><br /> Se la riga rimane visibile varia a seconda del tipo di cursore. Ad esempio, le righe eliminate sono visibili ai cursori statici e basati su keyset, ma non per i cursori dinamici.<br /><br /> La matrice di operazione riga a cui fa riferimento l'attributo di istruzione SQL_ATTR_ROW_OPERATION_PTR può essere utilizzata per indicare che una riga nel set di righe corrente deve essere ignorata durante un'operazione di eliminazione bulk. Per ulteriori informazioni, vedere "Matrici di stato e di operazione" più avanti in questo riferimento di funzione.|  
  
## <a name="locktype-argument"></a>Argomento LockType  
 Il *LockType* argomento fornisce un modo per le applicazioni controllare la concorrenza. Nella maggior parte dei casi, origini dati che supportano livelli di concorrenza e transazioni supporterà solo il valore SQL_LOCK_NO_CHANGE il *LockType* argomento. Il *LockType* argomento in genere viene utilizzato solo per il supporto basato su file.  
  
 Il *LockType* argomento specifica lo stato del blocco di riga dopo **SQLSetPos** è stata eseguita. Se il driver è in grado di bloccare la riga per eseguire l'operazione richiesta o per soddisfare il *LockType* argomento, viene restituito SQL_ERROR e SQLSTATE 42000 (sintassi o violazione di accesso).  
  
 Sebbene il *LockType* argomento è stato specificato per una singola istruzione, il blocco dà gli stessi privilegi a tutte le istruzioni per la connessione. In particolare, è possibile sbloccare un blocco che viene acquisito da un'unica istruzione in una connessione da un'istruzione diversa nella stessa connessione.  
  
 Una riga bloccata tramite **SQLSetPos** rimane bloccato fino a quando l'applicazione chiama **SQLSetPos** per la riga con *LockType* impostato su SQL_LOCK_UNLOCK, oppure fino a quando l'applicazione chiamate **SQLFreeHandle** per l'istruzione o **SQLFreeStmt** con l'opzione di SQL_CLOSE. Per un driver che supporta le transazioni, una riga bloccata tramite **SQLSetPos** viene sbloccata quando l'applicazione chiama **SQLEndTran** per eseguire il commit o rollback della transazione sulla connessione (se il cursore viene chiuso Quando viene eseguito il commit o rollback, come indicato dai tipi di informazioni SQL_CURSOR_COMMIT_BEHAVIOR e SQL_CURSOR_ROLLBACK_BEHAVIOR restituiti da una transazione **SQLGetInfo**).  
  
 Il *LockType* argomento supporta i seguenti tipi di blocchi. Per determinare quali blocchi sono supportati da un'origine dati, un'applicazione chiama **SQLGetInfo** con SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 o SQL_STATIC_ Tipo di informazioni CURSOR_ATTRIBUTES1 (a seconda del tipo di cursore).  
  
|*LockType* argomento|Tipo di blocco|  
|-------------------------|---------------|  
|SQL_LOCK_NO_CHANGE|Il driver o l'origine dati garantisce che la riga è lo stesso stato bloccato o sbloccato, in cui si trovava prima **SQLSetPos** è stato chiamato. Il valore di *LockType* consente di origini dati che non supportano il blocco a livello di riga esplicite per l'utilizzo di qualsiasi tipo di blocco è necessario per i livelli di isolamento di concorrenza e la transazione correnti.|  
|SQL_LOCK_EXCLUSIVE|L'origine dati o driver Blocca esclusivamente la riga. Un'istruzione su una connessione diversa o in un'altra applicazione non può essere utilizzata per acquisire i blocchi sulla riga.|  
|SQL_LOCK_UNLOCK|L'origine dati o driver Sblocca la riga.|  
  
 Se un driver supporta SQL_LOCK_EXCLUSIVE ma SQL_LOCK_UNLOCK, una riga bloccata rimarrà bloccata fino a quando non si verifica una delle chiamate di funzione descritte nel paragrafo precedente.  
  
 Se un driver supporta SQL_LOCK_EXCLUSIVE ma SQL_LOCK_UNLOCK, una riga bloccata rimarrà bloccata fino a quando l'applicazione chiama **SQLFreeHandle** per l'istruzione o **SQLFreeStmt** con l'opzione di SQL_CLOSE. Se il driver supporta le transazioni e chiude il cursore dopo il commit o il rollback della transazione, l'applicazione chiama **SQLEndTran**.  
  
 Per le operazioni update e delete in **SQLSetPos**, l'applicazione utilizza il *LockType* argomento come indicato di seguito:  
  
-   Per garantire che una riga non cambia dopo il recupero, un'applicazione chiama **SQLSetPos** con *operazione* impostato su SQL_REFRESH e *LockType* impostato su SQL_LOCK_ ESCLUSIVO.  
  
-   Se l'applicazione imposta *LockType* a SQL_LOCK_NO_CHANGE, il driver garantisce che un'operazione update o delete avrà esito positivo solo se l'applicazione specificata SQL_CONCUR_LOCK per l'attributo di istruzione SQL_ATTR_CONCURRENCY.  
  
-   Se l'applicazione specifica SQL_CONCUR_ROWVER o SQL_CONCUR_VALUES per l'attributo di istruzione SQL_ATTR_CONCURRENCY, il driver confronta le versioni delle righe o valori e rifiuta l'operazione, la riga è stato modificato dopo l'applicazione di recuperare la riga.  
  
-   Se l'applicazione specifica SQL_CONCUR_READ_ONLY per l'attributo di istruzione SQL_ATTR_CONCURRENCY, il driver rifiuta qualsiasi aggiornamento o eliminazione.  
  
 Per ulteriori informazioni sull'attributo di istruzione SQL_ATTR_CONCURRENCY, vedere [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md).  
  
## <a name="status-and-operation-arrays"></a>Lo stato e le matrici di operazione  
 Le matrici di stato e l'operazione seguente vengono utilizzate quando si chiama **SQLSetPos**:  
  
-   Matrice di stato di riga (come a cui fa riferimento il campo SQL_DESC_ARRAY_STATUS_PTR nell'implementazione e l'attributo di istruzione SQL_ATTR_ROW_STATUS_ARRAY) contiene i valori di stato per ogni riga di dati nel set di righe. Il driver imposta i valori di stato di questa matrice dopo una chiamata a **SQLFetch**, **SQLFetchScroll**, **SQLBulkOperations**, o **SQLSetPos** . Questa matrice viene fatto riferimento tramite l'attributo di istruzione vengono impostati SQL_ATTR_ROW_STATUS_PTR.  
  
-   Matrice di operazione di riga (come a cui fa riferimento il campo SQL_DESC_ARRAY_STATUS_PTR il ARD e l'attributo di istruzione SQL_ATTR_ROW_OPERATION_ARRAY) contiene un valore per ogni riga nel set di righe che indica se una chiamata a **SQLSetPos**per un'operazione di blocco verrà ignorata o eseguita. Ogni elemento nella matrice è impostato su SQL_ROW_PROCEED (impostazione predefinita) o SQL_ROW_IGNORE. Questa matrice viene fatto riferimento tramite l'attributo di istruzione SQL_ATTR_ROW_OPERATION_PTR.  
  
 Il numero di elementi nelle matrici di stato e l'operazione sia uguale al numero di righe nel set di righe (come definito dall'attributo di istruzione SQL_ATTR_ROW_ARRAY_SIZE).  
  
 Per informazioni sulla matrice di stato di riga, vedere [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md). Per informazioni sulla matrice di operazione di riga, vedere "Verrà ignorato una riga in un'operazione in blocco," più avanti in questa sezione.  
  
## <a name="using-sqlsetpos"></a>Utilizzando SQLSetPos  
 Prima di un'applicazione chiama **SQLSetPos**, è necessario eseguire la sequenza di passaggi seguente:  
  
1.  Se l'applicazione chiama **SQLSetPos** con *operazione* impostato su SQL_UPDATE, chiamata **SQLBindCol** (o **SQLSetDescRec**) per ogni colonna per specificare il tipo di dati e associare i buffer di dati e la lunghezza della colonna.  
  
2.  Se l'applicazione chiama **SQLSetPos** con *operazione* impostato su SQL_DELETE o SQL_UPDATE, chiamata **SQLColAttribute** per assicurarsi che le colonne per essere eliminata o aggiornata sono aggiornabili.  
  
3.  Chiamare **SQLExecDirect**, **SQLExecute**, o una funzione di catalogo per creare un set di risultati.  
  
4.  Chiamare **SQLFetch** o **SQLFetchScroll** per recuperare i dati.  
  
 Per ulteriori informazioni sull'utilizzo **SQLSetPos**, vedere [aggiornamento dei dati con SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md).  
  
## <a name="deleting-data-using-sqlsetpos"></a>Eliminazione di dati mediante SQLSetPos  
 Per eliminare i dati con **SQLSetPos**, un'applicazione chiama **SQLSetPos** con *RowNumber* impostato sul numero della riga da eliminare e *operazione*impostato su SQL_DELETE.  
  
 Dopo aver eliminati i dati, il driver modifica il valore della matrice di stato di riga di implementazione per la riga appropriata in SQL_ROW_DELETED (o SQL_ROW_ERROR).  
  
## <a name="updating-data-using-sqlsetpos"></a>Aggiornamento dei dati tramite SQLSetPos  
 Un'applicazione può passare il valore per una colonna nel buffer di dati associato o con uno o più chiamate a **SQLPutData**. Le colonne i cui dati vengono passati con **SQLPutData** sono note come *data-at-execution* *colonne*. Questi sono comunemente utilizzati per inviare i dati per le colonne SQL_LONGVARBINARY e SQL_LONGVARCHAR e possono essere combinati con altre colonne.  
  
#### <a name="to-update-data-with-sqlsetpos-an-application"></a>Per aggiornare i dati con SQLSetPos, un'applicazione:  
  
1.  I valori decimali nei buffer di dati e lunghezza/indicatore associato al **SQLBindCol**:  
  
    -   Per le colonne normale, viene visualizzato il nuovo valore della colonna nel * \*TargetValuePtr* buffer e la lunghezza di tale valore nel * \*StrLen_or_IndPtr* buffer. Se la riga non deve essere aggiornata, l'applicazione inserisce SQL_ROW_IGNORE nell'elemento di tale riga della matrice di operazione di riga.  
  
    -   Per le colonne data-at-execution, viene visualizzato un valore definito dall'applicazione, ad esempio il numero di colonna, nel * \*TargetValuePtr* buffer. Il valore può essere utilizzato in un secondo momento per identificare la colonna.  
  
         L'applicazione inserisce il risultato di SQL_LEN_DATA_AT_EXEC (*lunghezza*) (macro) nei **StrLen_or_IndPtr* buffer. Se il tipo di dati SQL della colonna è SQL_LONGVARBINARY, SQL_LONGVARCHAR o un tipo di dati specifici dell'origine dati di tipo long e il driver restituisce "Y" per il tipo di informazioni SQL_NEED_LONG_DATA_LEN in **SQLGetInfo**, *lunghezza * è il numero di byte di dati da inviare per il parametro; in caso contrario, deve essere un valore non negativo e viene ignorato.  
  
2.  Chiamate **SQLSetPos** con il *operazione* argomento impostato su SQL_UPDATE per aggiornare la riga di dati.  
  
    -   Se non sono presenti colonne data-at-execution, il processo è stato completato.  
  
    -   Se sono presenti colonne data-at-execution, la funzione restituisce SQL_NEED_DATA e procede al passaggio 3.  
  
3.  Chiamate **SQLParamData** per recuperare l'indirizzo del * \*TargetValuePtr* buffer per la prima colonna data-at-execution da elaborare. **SQLParamData** restituisce SQL_NEED_DATA. L'applicazione recupera il valore definito dall'applicazione di * \*TargetValuePtr* buffer.  
  
    > [!NOTE]  
    >  Anche se i parametri data-at-execution sono analoghi alle colonne data-at-execution, il valore restituito da **SQLParamData** è diverso per ognuno.  
  
    > [!NOTE]  
    >  I parametri data-at-execution sono parametri in un'istruzione SQL per il quale i dati verranno inviati con **SQLPutData** quando viene eseguita l'istruzione con **SQLExecDirect** o **SQLExecute**. Sono associate con **SQLBindParameter** o impostando i descrittori di **SQLSetDescRec**. Il valore restituito da **SQLParamData** è passato a un valore a 32 bit **SQLBindParameter** nel *ParameterValuePtr* argomento.  
  
    > [!NOTE]  
    >  Le colonne data-at-execution sono colonne in un set di righe per cui i dati verranno inviati con **SQLPutData** quando viene aggiornata una riga con **SQLSetPos**. Sono associate con **SQLBindCol**. Il valore restituito da **SQLParamData** è l'indirizzo della riga di **TargetValuePtr* buffer che viene elaborato.  
  
4.  Chiamate **SQLPutData** una o più volte per inviare i dati per la colonna. Più di una chiamata è necessario se tutti i valori dei dati non possono essere restituiti nel * \*TargetValuePtr* specificato nel buffer **SQLPutData**; più chiamate al metodo **SQLPutData** per la stessa colonna sono consentiti solo durante l'invio di dati di tipo carattere C a una colonna con un tipo di carattere, binary o dati specifici dell'origine dati o per l'invio di dati C binari a una colonna con un carattere, binario, o tipo di dati specifici dell'origine dati.  
  
5.  Chiamate **SQLParamData** per segnalare che tutti i dati è stato inviato per la colonna.  
  
    -   Se sono presenti altre colonne data-at-execution, **SQLParamData** restituisce SQL_NEED_DATA e l'indirizzo del *TargetValuePtr* buffer per la colonna data-at-execution successiva da elaborare. L'applicazione si ripete i passaggi 4 e 5.  
  
    -   Se sono presenti colonne data-at-execution non sono più presenti, il processo è stato completato. Se l'istruzione è stata eseguita correttamente, **SQLParamData** restituisce SQL_SUCCESS o SQL_SUCCESS_WITH_INFO; se l'esecuzione non riuscita, viene restituito SQL_ERROR. A questo punto, **SQLParamData** può restituire qualsiasi SQLSTATE che può essere restituiti da **SQLSetPos**.  
  
 Se i dati sono stati aggiornati, il driver modifica il valore della matrice di stato di riga di implementazione per la riga appropriata in SQL_ROW_UPDATED.  
  
 Se l'operazione viene annullata o si verifica un errore **SQLParamData** o **SQLPutData**, dopo **SQLSetPos** restituisce SQL_NEED_DATA e prima dell'invio di dati per tutti le colonne data-at-execution, l'applicazione può chiamare solo **SQLCancel**, **SQLGetDiagField**, **SQLGetDiagRec**, **SQLGetFunctions **, **SQLParamData**, o **SQLPutData** per l'istruzione o la connessione associata all'istruzione. Se per la connessione associata all'istruzione o l'istruzione chiama qualsiasi altra funzione, la funzione restituisce SQL_ERROR e SQLSTATE HY010 (funzione di errore nella sequenza).  
  
 Se l'applicazione chiama **SQLCancel** mentre il driver deve comunque i dati per le colonne data-at-execution, il driver Annulla l'operazione. L'applicazione può quindi chiamare **SQLSetPos** nuovamente l'annullamento non influisce sullo stato del cursore o la posizione corrente del cursore.  
  
 Quando l'elenco SELECT della specifica di query associata al cursore contiene più di un riferimento alla stessa colonna, se viene generato un errore o il driver ignora i riferimenti duplicati ed esegue le operazioni richieste è definito dal driver.  
  
## <a name="performing-bulk-operations"></a>Esecuzione di operazioni Bulk  
 Se il *RowNumber* argomento è 0, il driver esegue l'operazione specificata nel *operazione* argomento per ogni riga nel set di righe con un valore di SQL_ROW_PROCEED nel relativo campo nell'operazione di riga matrice a cui puntava attributo dell'istruzione SQL_ATTR_ROW_OPERATION_PTR. Si tratta di un valore valido di *RowNumber* argomento per un *operazione* argomento di SQL_DELETE, SQL_REFRESH, o SQL_UPDATE, ma non SQL_POSITION. **SQLSetPos** con un *operazione* di SQL_POSITION e *RowNumber* uguale a 0 restituirà HY109 SQLSTATE (posizione del cursore non valido).  
  
 Se si verifica un errore che riguardano l'intero set di righe, ad esempio HYT00 SQLSTATE (Timeout scaduto), il driver restituisce SQL_ERROR e i codici SQLSTATE appropriati. Il contenuto del buffer di set di righe non è definito e viene modificata la posizione del cursore.  
  
 Se si verifica un errore che si riferisce a una singola riga, il driver:  
  
-   Imposta l'elemento per la riga nella matrice di stato di riga a cui fa riferimento l'attributo di istruzione vengono impostati SQL_ATTR_ROW_STATUS_PTR a SQL_ROW_ERROR.  
  
-   Inserisce una o più SQLSTATE aggiuntive per l'errore nella coda di errore e imposta il campo SQL_DIAG_ROW_NUMBER nella struttura di dati di diagnostica.  
  
 Dopo avere elaborato l'errore o avviso, se il driver viene completata l'operazione per le righe rimanenti nel set di righe, viene restituito SQL_SUCCESS_WITH_INFO. Pertanto, per ogni riga che ha restituito un errore, la coda di errore contiene zero o più SQLSTATE aggiuntive. Se il driver arresta l'operazione dopo che è stato elaborato l'errore o avviso, viene restituito SQL_ERROR.  
  
 Se il driver restituisce tutti gli avvisi, ad esempio SQLSTATE 01004 (dati troncati), restituisce gli avvisi che si applicano per l'intero set di righe o alle righe sconosciute nel set di righe prima di restituire le informazioni sull'errore che si applica a colonne specifiche. Restituisce gli avvisi per le righe specifiche insieme a qualsiasi altra informazione di errore su tali righe.  
  
 Se *RowNumber* è uguale a 0 e *operazione* è SQL_UPDATE, SQL_REFRESH o SQL_DELETE, il numero di righe che **SQLSetPos** opera in a cui punta l'attributo Attributo di istruzione _FETCHED_PTR.  
  
 Se *RowNumber* è uguale a 0 e *operazione* è SQL_DELETE, SQL_REFRESH o SQL_UPDATE, la riga corrente al termine dell'operazione come la riga corrente prima dell'operazione.  
  
## <a name="ignoring-a-row-in-a-bulk-operation"></a>Verrà ignorata una riga in un'operazione Bulk  
 La matrice di operazione riga può essere utilizzata per indicare che una riga nel set di righe corrente deve essere ignorata durante un'operazione bulk usando **SQLSetPos**. Per indirizzare il driver per ignorare una o più righe durante un'operazione bulk, un'applicazione deve eseguire i passaggi seguenti:  
  
1.  Chiamare **SQLSetStmtAttr** per impostare l'attributo dell'istruzione in modo che punti a una matrice di SQLUSMALLINTs SQL_ATTR_ROW_OPERATION_PTR. Questo campo può essere impostato anche chiamando **SQLSetDescField** per impostare il campo di intestazione SQL_DESC_ARRAY_STATUS_PTR di ARD, il che richiede che un'applicazione ottiene l'handle di descrittore.  
  
2.  Impostare ogni elemento della matrice operazione riga a uno dei due valori:  
  
    -   SQL_ROW_IGNORE, per indicare che la riga esclusa per l'operazione bulk.  
  
    -   SQL_ROW_PROCEED, per indicare che la riga è incluso nell'operazione di blocco. Si tratta del valore predefinito.  
  
3.  Chiamare **SQLSetPos** per eseguire l'operazione bulk.  
  
 Le regole seguenti si applicano alla matrice operazione riga:  
  
-   SQL_ROW_IGNORE e SQL_ROW_PROCEED interessano solo le operazioni bulk utilizzando **SQLSetPos** con un *operazione* di SQL_DELETE o SQL_UPDATE. Non influiscono le chiamate a **SQLSetPos** con un *operazione* di SQL_REFRESH o SQL_POSITION.  
  
-   Il puntatore è impostato su null per impostazione predefinita.  
  
-   Se il puntatore è null, tutte le righe vengono aggiornate come se tutti gli elementi sono stati impostati su SQL_ROW_PROCEED.  
  
-   L'impostazione di un elemento a SQL_ROW_PROCEED non garantisce che l'operazione verrà eseguita in tale riga specifica. Ad esempio, se una determinata riga all'interno del set di righe con lo stato di SQL_ROW_ERROR, il driver potrebbe non essere in grado di aggiornare tale riga, indipendentemente dal fatto che l'applicazione specificata SQL_ROW_PROCEED. Un'applicazione deve controllare sempre la matrice di stato di riga per vedere se l'operazione ha avuto esito positivo.  
  
-   SQL_ROW_PROCEED è definito come 0 nel file di intestazione. Un'applicazione può inizializzare la matrice di operazione riga su 0 per elaborare tutte le righe.  
  
-   Se il numero di elementi "n" nella matrice di operazione di riga è impostato su SQL_ROW_IGNORE e **SQLSetPos** viene chiamata per eseguire un aggiornamento in blocco o l'ennesima riga del set di righe di rimane invariata dopo la chiamata a, l'operazione di eliminazione **SQLSetPos**.  
  
-   Un'applicazione deve impostare una colonna di sola lettura SQL_ROW_IGNORE.  
  
## <a name="ignoring-a-column-in-a-bulk-operation"></a>Ignorare una colonna in un'operazione Bulk  
 Per evitare un'elaborazione diagnostica generata dai tentativi aggiornamenti a uno o più colonne di sola lettura, un'applicazione può impostare il valore nel buffer di lunghezza/indicatore associato al SQL_COLUMN_IGNORE. Per ulteriori informazioni, vedere [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
## <a name="code-example"></a>Esempio di codice  
 Nell'esempio seguente, un'applicazione consente all'utente di selezionare la tabella ORDERS e aggiornare lo stato dell'ordine. Il cursore è basati su keyset con dimensioni di righe pari a 20 e utilizza il controllo della concorrenza ottimistica confrontare le versioni di riga. Dopo ogni set di righe vengono recuperati, l'applicazione Visualizza e consente all'utente di selezionare e aggiornare lo stato di un ordine. L'applicazione utilizza **SQLSetPos** per posizionare il cursore nella riga selezionata ed esegue un aggiornamento posizionato della riga. (La gestione degli errori viene omesso per maggiore chiarezza).  
  
```  
#define ROWS 20  
#define STATUS_LEN 6  
  
SQLCHAR        szStatus[ROWS][STATUS_LEN], szReply[3];  
SQLINTEGER     cbStatus[ROWS], cbOrderID;  
SQLUSMALLINT   rgfRowStatus[ROWS];  
SQLUINTEGER    sOrderID, crow = ROWS, irow;  
SQLHSTMT       hstmtS, hstmtU;  
  
SQLSetStmtAttr(hstmtS, SQL_ATTR_CONCURRENCY, (SQLPOINTER) SQL_CONCUR_ROWVER, 0);  
SQLSetStmtAttr(hstmtS, SQL_ATTR_CURSOR_TYPE, (SQLPOINTER) SQL_CURSOR_KEYSET_DRIVEN, 0);  
SQLSetStmtAttr(hstmtS, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER) ROWS, 0);  
SQLSetStmtAttr(hstmtS, SQL_ATTR_ROW_STATUS_PTR, (SQLPOINTER) rgfRowStatus, 0);  
SQLSetCursorName(hstmtS, "C1", SQL_NTS);  
SQLExecDirect(hstmtS, "SELECT ORDERID, STATUS FROM ORDERS ", SQL_NTS);  
  
SQLBindCol(hstmtS, 1, SQL_C_ULONG, &sOrderID, 0, &cbOrderID);  
SQLBindCol(hstmtS, 2, SQL_C_CHAR, szStatus, STATUS_LEN, &cbStatus);  
  
while ((retcode == SQLFetchScroll(hstmtS, SQL_FETCH_NEXT, 0)) != SQL_ERROR) {  
   if (retcode == SQL_NO_DATA_FOUND)  
      break;  
   for (irow = 0; irow < crow; irow++) {  
      if (rgfRowStatus[irow] != SQL_ROW_DELETED)  
         printf("%2d %5d %*s\n", irow+1, sOrderID, NAME_LEN-1, szStatus[irow]);  
   }  
   while (TRUE) {  
      printf("\nRow number to update?");  
      gets_s(szReply, 3);  
      irow = atoi(szReply);  
      if (irow > 0 && irow <= crow) {  
         printf("\nNew status?");  
         gets_s(szStatus[irow-1], (ROWS * STATUS_LEN));  
         SQLSetPos(hstmtS, irow, SQL_POSITION, SQL_LOCK_NO_CHANGE);  
         SQLPrepare(hstmtU,  
          "UPDATE ORDERS SET STATUS=? WHERE CURRENT OF C1", SQL_NTS);  
         SQLBindParameter(hstmtU, 1, SQL_PARAM_INPUT,  
            SQL_C_CHAR, SQL_CHAR,  
            STATUS_LEN, 0, szStatus[irow], 0, NULL);  
         SQLExecute(hstmtU);  
      } else if (irow == 0) {  
         break;  
      }  
   }  
}  
```  
  
 Per ulteriori esempi, vedere [istruzioni di eliminazione e aggiornamento posizionato](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md) e [l'aggiornamento di righe nel set di righe con SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md).  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Associazione di un buffer a una colonna in un set di risultati|[Funzione SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Esecuzione di operazioni bulk che non riguardano la posizione del cursore blocco|[Funzione SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|L'elaborazione di istruzione di annullamento|[Funzione SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Recupero di un blocco di dati o di scorrimento di un risultato impostato|[Funzione SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Recupero di un singolo campo di un descrittore|[Funzione SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Recupero di più campi di un descrittore|[Funzione SQLGetDescRec](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|L'impostazione di un singolo campo di un descrittore|[Funzione SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|Impostazione dei diversi campi di un descrittore|[Funzione SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
|L'impostazione di un attributo di istruzione|[Funzione SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)

