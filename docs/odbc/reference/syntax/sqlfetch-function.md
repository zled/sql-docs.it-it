---
title: Funzione SQLFetch | Documenti Microsoft
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
- SQLFetch
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLFetch
helpviewer_keywords:
- SQLFetch function [ODBC]
ms.assetid: 6c6611d2-bc6a-4390-87c9-1c5dd9cfe07c
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 135ee130d56801c5da3abb47447a1372d29656a5
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlfetch-function"></a>SQLFetch-funzione
**Conformità**  
 Introdotta: versione ODBC standard 1.0 conformità: 92 ISO  
  
 **Riepilogo**  
 **SQLFetch** recupera il successivo set di righe di dati dal set di risultati e restituisce i dati per tutte le colonne associate.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLFetch(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>Argomenti  
 *StatementHandle*  
 [Input] Handle di istruzione.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_STILL_EXECUTING, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLFetch** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato può essere ottenuto chiamando [funzione SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md) con un *HandleType*impostato su SQL_HANDLE_STMT e *gestire* di *StatementHandle*. Nella tabella seguente sono elencati i valori SQLSTATE normalmente restituiti dal **SQLFetch** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato. Se si verifica un errore in una singola colonna, [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) può essere chiamato con un *DiagIdentifier* di SQL_DIAG_COLUMN_NUMBER per determinare la colonna a cui si è verificato l'errore; e ** SQLGetDiagField** può essere chiamato con un *DiagIdentifier* di SQL_DIAG_ROW_NUMBER per determinare la riga che contiene tale colonna.  
  
 Per tutti questi SQLSTATE restituiti SQL_SUCCESS_WITH_INFO o SQL_ERROR (eccetto SQLSTATE 01xxx), viene restituito SQL_SUCCESS_WITH_INFO, se si verifica un errore in uno o più, ma non tutte le righe di un'operazione su più righe e viene restituito SQL_ERROR se si verifica un errore in un riga singola operazione.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01004|Stringa di dati corretto troncato|Stringa o dati binari restituiti per una colonna ha restituito il troncamento di un carattere non vuoto o dati binari non NULL. Se si trattasse di un valore stringa, è stato troncato a destra.|  
|01S01|Errore alla riga|Si è verificato un errore durante il recupero di una o più righe.<br /><br /> (Se questa SQLSTATE viene restituito quando un'applicazione ODBC 3*x* applicazione sta utilizzando un'API ODBC 2*x* driver, può essere ignorato.)|  
|01S07|Troncamento frazionario.|I dati restituiti per una colonna è stati troncati. Per i tipi di dati numerici, la parte frazionaria del numero è stata troncata. Per ora, timestamp e tipi di dati di intervallo che contengono un componente di ora, la parte frazionaria del tempo è stata troncata.<br /><br /> (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|07006|Violazione dell'attributo del tipo di dati|Impossibile convertire il valore di dati di una colonna nel set di risultati per il tipo di dati specificato da *TargetType* in **SQLBindCol**.<br /><br /> Colonna 0 è stata associata a un tipo di dati di SQL_C_BOOKMARK e l'attributo di istruzione SQL_ATTR_USE_BOOKMARKS è stato impostato su SQL_UB_VARIABLE.<br /><br /> Colonna 0 è stata associata a un tipo di dati di SQL_C_VARBOOKMARK e non è stato impostato l'attributo di istruzione SQL_ATTR_USE_BOOKMARKS SQL_UB_VARIABLE.|  
|07009|Indice del descrittore non valido|Il driver non è un'API ODBC 2*x* driver che non supporta **SQLExtendedFetch**, e un numero di colonna specificato nell'associazione per una colonna è 0.<br /><br /> Colonna 0 è stato associato, e l'attributo di istruzione SQL_ATTR_USE_BOOKMARKS era impostato su SQL_UB_OFF.|  
|08S01|Errore del collegamento di comunicazione|Collegamento di comunicazione tra il driver e l'origine dati a cui era connesso il driver non è stato possibile prima dell'elaborazione della funzione è stata completata.|  
|22001|Stringa di dati corretto troncato|Un segnalibro a lunghezza variabile per una colonna restituito è stato troncato.|  
|22002|Variabile indicatore necessaria ma non fornito|NULL è stata recuperati i dati in una colonna il cui *StrLen_or_IndPtr* impostazione **SQLBindCol** (o l'impostazione SQL_DESC_INDICATOR_PTR **SQLSetDescField** o ** SQLSetDescRec**) è un puntatore null.|  
|22003|Valore numerico non compreso nell'intervallo|Restituisce il valore numerico come numerico o stringa per uno o più colonne associate avrebbe causato la parte intera (in contrapposizione frazionari) del numero da troncare.<br /><br /> Per ulteriori informazioni, vedere [la conversione di dati da SQL a tipi di dati C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) appendice d: tipo di dati.|  
|22007|Formato di datetime non valido|Una colonna di tipo carattere nel set di risultati è stata associata a una data, ora o struttura di timestamp C, e un valore nella colonna è, rispettivamente, una data non valida, il tempo o timestamp.|  
|22012|Divisione per zero|Da un'espressione aritmetica ha restituito un valore, ciò ha provocato la divisione per zero.|  
|22015|Overflow del campo intervallo|L'assegnazione da un numerico esatto o l'intervallo di tipo SQL a un tipo di intervallo C ha causato una perdita di cifre significative nel campo iniziale.<br /><br /> Durante il recupero di dati a un tipo di intervallo C, si è verificato alcun rappresentazione del valore di tipo SQL nel tipo di intervallo C.|  
|22018|Valore di carattere non valido per la specifica del cast|Una colonna di tipo carattere nel set di risultati è stata associata a un buffer di caratteri C e la colonna contiene un carattere che non ha ricevuto alcuna rappresentazione nel set di caratteri del buffer.<br /><br /> Il tipo C è stato un numerico esatto o approssimativo, un valore datetime o un tipo di dati di intervallo. il tipo SQL della colonna è un tipo di dati character; il valore nella colonna non ha un valore letterale valido del tipo C associato.|  
|24000|Stato del cursore non valido|Il *StatementHandle* era in uno stato eseguito ma è stato associato alcun set di risultati di *StatementHandle*.|  
|40001|Errore di serializzazione.|La transazione in cui è stato eseguito l'operazione di recupero è stata interrotta per impedire un deadlock.|  
|40003|Completamento delle istruzioni sconosciuto|Impossibile stabilire la connessione associata durante l'esecuzione di questa funzione e non è possibile determinare lo stato della transazione.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel * \*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver non è riuscito ad allocare memoria che è necessario per supportare l'esecuzione o il completamento della funzione.|  
|HY008|Operazione annullata|L'elaborazione asincrona è stata abilitata per il *StatementHandle*. Il **SQLFetch** funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle*. Il **SQLFetch** funzione è stata chiamata nuovamente sul *StatementHandle*.<br /><br /> O, **SQLFetch** funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle * da un thread diverso in un'applicazione multithread.|  
|HY010|Errore nella sequenza (funzione)|(DM) a cui è stata chiamata per l'handle di connessione associata a una funzione in modo asincrono in esecuzione il *StatementHandle*. Questa funzione asincrona era ancora in esecuzione quando il **SQLFetch** funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** è stato chiamato per il *StatementHandle* e restituito SQL_PARAM_DATA_ È DISPONIBILE. Questa funzione è stata chiamata prima che i dati sono stati recuperati per tutti i parametri con flusso.<br /><br /> (DM) specificato *StatementHandle* non è stato eseguito. La funzione è stata chiamata senza chiamare prima il metodo **SQLExecDirect**, **SQLExecute** o una funzione di catalogo.<br /><br /> (DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione (non è presente uno) di *StatementHandle* ed era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos** è stato chiamato per il * StatementHandle* e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima che sono stati inviati dati per tutti i parametri data-at-execution o colonne.<br /><br /> (DM) **SQLFetch** è stato chiamato per il *StatementHandle* dopo **SQLExtendedFetch** è stato chiamato e prima **SQLFreeStmt** con il SQL _ Opzione di chiusura è stato chiamato.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY090|Lunghezza di stringa o di buffer non valida|L'attributo di istruzione SQL_ATTR_USE_BOOKMARK è stato impostato su SQL_UB_VARIABLE e colonna 0 è stata associata a un buffer, la cui lunghezza non è uguale alla lunghezza massima per il segnalibro per questo set di risultati. (Questa lunghezza è disponibile nel campo SQL_DESC_OCTET_LENGTH di implementazione e può essere ottenuta chiamando **SQLDescribeCol**, **SQLColAttribute**, o **SQLGetDescField**.)|  
|HY107|Valore di riga non compreso nell'intervallo|Il valore specificato con l'attributo di istruzione SQL_ATTR_CURSOR_TYPE SQL_CURSOR_KEYSET_DRIVEN, ma non ha il valore specificato con l'attributo di istruzione SQL_ATTR_KEYSET_SIZE maggiore di 0 e minore del valore specificato con il SQL_ATTR_ROW_ARRAY_ Attributo di istruzione di dimensioni.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Funzionalità facoltativa non implementata.|L'origine dati o driver non supporta la conversione specificata dalla combinazione del *TargetType* in **SQLBindCol** e il tipo di dati SQL della colonna corrispondente.|  
|HYT00|Timeout|Il periodo di timeout della query è scaduto prima origine dati ha restituito il set di risultati richiesti. Il periodo di timeout viene impostato tramite la funzione SQLSetStmtAttr, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|Il driver (DM) associato il *StatementHandle* non supporta la funzione.|  
|IM017|Polling è disabilitato in modalità di notifica asincrona|Ogni volta che viene utilizzato il modello di notifica, il polling è disabilitato.|  
|IM018|**SQLCompleteAsync** non è stato chiamato per completare l'operazione asincrona precedente su questo handle.|Se la chiamata di funzione precedente dell'handle restituisce SQL_STILL_EXECUTING e se è abilitata la modalità di notifica, **SQLCompleteAsync** deve essere chiamato per l'handle per eseguire la post-elaborazione e completare l'operazione.|  
  
## <a name="comments"></a>Commenti  
 **SQLFetch** restituisce il successivo set di righe nel set di risultati. Può essere chiamato solo quando esiste un set di risultati: ovvero, dopo una chiamata che crea un set di risultati e prima del cursore sopra di set di risultati viene chiuso. Se tutte le colonne sono associate, restituisce i dati in tali colonne. Se l'applicazione non è specificato un puntatore a una matrice di stato di riga o di un buffer in cui restituire il numero di righe recuperate, **SQLFetch** anche restituisce queste informazioni. Le chiamate a **SQLFetch** può essere combinato con chiamate a **SQLFetchScroll** ma non può essere combinato con chiamate a **SQLExtendedFetch**. Per ulteriori informazioni, vedere [il recupero di una riga di dati](../../../odbc/reference/develop-app/fetching-a-row-of-data.md).  
  
 Se un'applicazione ODBC 3*x* applicazione funziona con un'API ODBC 2*x* esegue il mapping di driver, Driver Manager **SQLFetch** le chiamate a **SQLExtendedFetch** per un ODBC 2*x* driver che supporta **SQLExtendedFetch**. Se l'API ODBC 2*. x* driver non supporta **SQLExtendedFetch**, viene eseguito il mapping di gestione Driver **SQLFetch** le chiamate a **SQLFetch** in ODBC 2 *x* driver, che è possibile recuperare una sola riga.  
  
 Per ulteriori informazioni, vedere [cursori a blocchi, i cursori scorrevoli e compatibilità con le versioni precedenti](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) nell'appendice g: Driver le linee guida per la compatibilità con le versioni precedenti.  
  
## <a name="positioning-the-cursor"></a>Posizionando il cursore  
 Quando viene creato il set di risultati, il cursore viene posizionato prima dell'inizio del set di risultati. **SQLFetch** recupera il set di righe successivo. È equivalente alla chiamata al metodo **SQLFetchScroll** con *FetchOrientation* impostato su SQL_FETCH_NEXT. Per ulteriori informazioni sui cursori, vedere [cursori](../../../odbc/reference/develop-app/cursors.md) e [cursori a blocchi](../../../odbc/reference/develop-app/block-cursors.md).  
  
 L'attributo di istruzione SQL_ATTR_ROW_ARRAY_SIZE specifica il numero di righe nel set di righe. Se il set di righe recuperate da **SQLFetch** si sovrappone la fine del set di risultati, **SQLFetch** restituisce un set di righe parziale. Vale a dire se S + R-1 è maggiore di L, dove S è la riga iniziale del set di righe recuperate, R è la dimensione del set di righe e L è l'ultima riga nel set di risultati, quindi solo il primo L – S + 1 righe del set di righe sono validi. Le righe rimanenti sono vuote e lo stato del SQL_ROW_NOROW.  
  
 Dopo aver **SQLFetch** restituisce, la riga corrente è la prima riga del set di righe.  
  
 Le regole elencate nella tabella seguente vengono descritti il posizionamento del cursore dopo una chiamata a **SQLFetch**, in base alle condizioni elencate nella seconda tabella in questa sezione.  
  
|Condizione|Prima riga del nuovo set di righe|  
|---------------|-----------------------------|  
|Operazioni preliminari|1|  
|*CurrRowsetStart* \< =  *LastResultRow – RowsetSize*[1]|*CurrRowsetStart* + *RowsetSize*[2]|  
|*CurrRowsetStart* > *LastResultRow – RowsetSize*[1]|Dopo la fine|  
|Dopo la fine|Dopo la fine|  
  
 [1] se le dimensioni del set di righe viene modificata tra operazioni di recupero, è la dimensione del set di righe che è stata utilizzata con la precedente operazione di recupero.  
  
 [2] se le dimensioni del set di righe viene modificata tra operazioni di recupero, è la dimensione del set di righe che è stata utilizzata con la nuova operazione di recupero.  
  
|Notazione|Significato|  
|--------------|-------------|  
|Operazioni preliminari|Il cursore a blocchi viene posizionato prima dell'inizio del set di risultati. Se la prima riga del nuovo set di righe è precedente all'inizio del set di risultati, **SQLFetch** restituisce SQL_NO_DATA.|  
|Dopo la fine|Il cursore a blocchi viene posizionato dopo aver impostato la fine del risultato. Se è la prima riga del set di righe di nuovo dopo la fine del set di risultati, **SQLFetch** restituisce SQL_NO_DATA.|  
|*CurrRowsetStart*|Il numero della prima riga nel set di righe corrente.|  
|*LastResultRow*|Il numero dell'ultima riga nel set di risultati.|  
|*RowsetSize*|Le dimensioni del set di righe.|  
  
 Si supponga, ad esempio, un set di risultati ha 100 righe e le dimensioni del set di righe sono 5. Nella tabella seguente viene illustrato il codice restituito e di set di righe restituito da **SQLFetch** per le posizioni iniziale diverse.  
  
|Set di righe corrente|Codice restituito|Nuovo set di righe|numero di righe recuperate|  
|--------------------|-----------------|----------------|------------------------|  
|Operazioni preliminari|SQL_SUCCESS|da 1 a 5|5|  
|da 1 a 5|SQL_SUCCESS|da 6 a 10|5|  
|52 a 56|SQL_SUCCESS|57 a 61|5|  
|91 a 95|SQL_SUCCESS|96 a 100|5|  
|93-97|SQL_SUCCESS|98 e 100. Le righe 4 e 5 della matrice di stato di riga vengono impostate su SQL_ROW_NOROW.|3|  
|96 a 100|SQL_NO_DATA|nessuna.|0|  
|99 e 100.|SQL_NO_DATA|nessuna.|0|  
|Dopo la fine|SQL_NO_DATA|nessuna.|0|  
  
## <a name="returning-data-in-bound-columns"></a>Restituzione di dati in colonne associate  
 Come **SQLFetch** restituisce ogni riga, vengono inseriti i dati per ogni colonna associata nel buffer associato a tale colonna. Se nessuna colonna è associata, **SQLFetch** non restituisce dati ma spostarsi in avanti il cursore a blocchi. I dati possono ancora essere recuperati tramite **SQLGetData**. Se il cursore è di più righe (ovvero, l'oggetto SQL_ATTR_ROW_ARRAY_SIZE è maggiore di 1), **SQLGetData** può essere chiamato solo se viene restituito SQL_GD_BLOCK quando **SQLGetInfo** viene chiamato con un * InfoType* di SQL_GETDATA_EXTENSIONS. (Per ulteriori informazioni, vedere [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md).)  
  
 Per ogni colonna associata in una riga, **SQLFetch** esegue le operazioni seguenti:  
  
1.  Imposta il buffer di lunghezza/indicatore su SQL_NULL_DATA e passare alla colonna successiva, se i dati sono NULL. Se i dati sono NULL ed è stato associato alcun buffer di lunghezza/indicatore, **SQLFetch** restituisce SQLSTATE 22002 (variabile indicatore necessaria ma non è stato fornito) per la riga e consente di passare alla riga successiva. Per informazioni su come determinare l'indirizzo del buffer di lunghezza/indicatore, vedere "Buffer indirizzi" in [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
     Se i dati per la colonna non sono NULL, **SQLFetch** procede al passaggio 2.  
  
2.  Se l'attributo di istruzione SQL_ATTR_MAX_LENGTH è impostato su un valore diverso da zero e la colonna contiene dati carattere o binario, i dati vengono troncati a byte SQL_ATTR_MAX_LENGTH.  
  
    > [!NOTE]  
    >  L'attributo di istruzione SQL_ATTR_MAX_LENGTH è progettato per ridurre il traffico di rete. Viene in genere implementato dall'origine dati, che tronca i dati prima di restituirlo attraverso la rete. Driver e origini dati non è necessario lo supporta. Pertanto, per garantire che i dati vengono troncati a una determinata dimensione, deve allocare un buffer di dimensione e specificare le dimensioni in un'applicazione di *cbValueMax* argomento **SQLBindCol**.  
  
3.  Converte i dati nel tipo specificato da *TargetType* in **SQLBindCol**.  
  
4.  Se i dati è stati convertiti in un tipo di dati a lunghezza variabile, ad esempio carattere o binario, **SQLFetch** controlla se la lunghezza dei dati supera la lunghezza del buffer di dati. Se la lunghezza dei dati di carattere (incluso il carattere di terminazione null) supera la lunghezza del buffer di dati, **SQLFetch** tronca i dati per la lunghezza del buffer dei dati meno la lunghezza di un carattere di terminazione null. Quindi null termina i dati. Se la lunghezza dei dati binari supera la lunghezza del buffer di dati, **SQLFetch** troncato alla lunghezza del buffer di dati. La lunghezza del buffer di dati viene specificata con *BufferLength* in **SQLBindCol**.  
  
     **SQLFetch** mai tronca i dati convertiti in dati a lunghezza fissa tipi; sempre presuppone che la lunghezza del buffer di dati sia le dimensioni del tipo di dati.  
  
5.  Inserisce i dati convertiti (e probabilmente troncati) nel buffer di dati. Per informazioni su come determinare l'indirizzo del buffer di dati, vedere "Buffer indirizzi" in [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
6.  Inserisce la lunghezza dei dati nel buffer di lunghezza/indicatore. Se il puntatore di indicatori e il puntatore di lunghezza sono stati impostati entrambi su stesso buffer (come una chiamata a **SQLBindCol** does), la lunghezza viene scritto nel buffer di dati validi e SQL_NULL_DATA viene scritto nel buffer per i dati NULL. Se è stato associato alcun buffer di lunghezza/indicatore, **SQLFetch** non restituisce la lunghezza.  
  
    -   Per dati carattere o binario, questa è la lunghezza dei dati dopo la conversione e prima di troncamento a causa di buffer di dati troppo piccolo. Se il driver non è possibile determinare la lunghezza dei dati dopo la conversione, come accade a volte con dati di tipo long, imposta la lunghezza SQL_NO_TOTAL. Se i dati sono stati troncati a causa di attributo di istruzione SQL_ATTR_MAX_LENGTH, il valore di questo attributo viene inserito nel buffer di lunghezza/indicatore anziché la lunghezza effettiva. Questo avviene perché l'attributo è progettato per troncare i dati nel server prima della conversione, in modo che il driver non è in grado di determinare la lunghezza effettiva è.  
  
    -   Per tutti gli altri tipi di dati, si tratta della lunghezza dei dati dopo la conversione. che è la dimensione del tipo a cui è stati convertiti i dati.  
  
     Per informazioni su come determinare l'indirizzo del buffer di lunghezza/indicatore, vedere "Buffer indirizzi" in [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
7.  Se i dati vengono troncati durante la conversione senza perdita di cifre significative (ad esempio, il numero reale 1,234 viene troncato 1 quando convertito nell'intero), **SQLFetch** restituisce l'errore SQLSTATE 01S07 (troncamento frazionario) e SQL _ SUCCESS_WITH_INFO. Se i dati vengono troncati perché la lunghezza del buffer di dati è troppo piccola (ad esempio, la stringa "abcdef" è inserita in un buffer a 4 byte), **SQLFetch** restituisce SQLSTATE 01004 (dati troncati) e SQL_SUCCESS_WITH_INFO. Se i dati vengono troncati a causa dell'attributo di istruzione, SQL_ATTR_MAX_LENGTH **SQLFetch** restituisce SQL_SUCCESS e non restituisce alcun errore SQLSTATE 01S07 (troncamento frazionario) o SQLSTATE 01004 (dati troncati). Se i dati vengono troncati durante la conversione con una perdita di cifre significative (ad esempio, se un valore SQL_INTEGER maggiore di 100.000 sono stato convertito in un SQL_C_TINYINT), **SQLFetch** restituisce SQLSTATE 22003 (valore numerico non compreso nell'intervallo) e (se le dimensioni del set di righe sono 1) di SQL_ERROR o SQL_SUCCESS_WITH_INFO (se le dimensioni del set di righe sono maggiore di 1).  
  
 Il contenuto del buffer di dati associato e del buffer di lunghezza/indicatore è indefinito se **SQLFetch** o **SQLFetchScroll** non restituisce SQL_SUCCESS o SQL_SUCCESS_WITH_INFO.  
  
## <a name="row-status-array"></a>Matrice di stato di riga  
 La matrice di stato di riga viene utilizzata per restituire lo stato di ogni riga nel set di righe. L'indirizzo di questa matrice viene specificato con l'attributo di istruzione vengono impostati SQL_ATTR_ROW_STATUS_PTR. La matrice viene allocata dall'applicazione e deve disporre di tutti gli elementi definiti dall'attributo di istruzione SQL_ATTR_ROW_ARRAY_SIZE. Vengono impostati i valori **SQLFetch**, **SQLFetchScroll**, e **SQLBulkOperations** o **SQLSetPos** (tranne quando sono stati chiamati Dopo che è stato posizionato il cursore da **SQLExtendedFetch**). Se il valore dell'attributo di istruzione vengono impostati SQL_ATTR_ROW_STATUS_PTR è un puntatore null, queste funzioni non restituiscono lo stato di riga.  
  
 Il contenuto del buffer di matrice di stato di riga è indefinito se **SQLFetch** o **SQLFetchScroll** non restituisce SQL_SUCCESS o SQL_SUCCESS_WITH_INFO.  
  
 I valori seguenti vengono restituiti nella matrice di stato di riga.  
  
|Valore di matrice di stato di riga|Description|  
|----------------------------|-----------------|  
|SQL_ROW_SUCCESS|La riga è stata recuperata correttamente e non è stato modificato dopo l'ultimo recupero da questo set di risultati.|  
|SQL_ROW_SUCCESS_WITH_INFO|La riga è stata recuperata correttamente e non è stato modificato dopo l'ultimo recupero da questo set di risultati. Tuttavia, è stato restituito un avviso sulla riga.|  
|SQL_ROW_ERROR|Si è verificato un errore durante il recupero della riga.|  
|SQL_ROW_UPDATED [1], [2], [3] e|La riga è stata recuperata correttamente ed è stato modificato dopo l'ultimo recupero da questo set di risultati. Se la riga viene recuperata di nuovo da questo set di risultati o viene aggiornata da **SQLSetPos**, lo stato viene modificato al nuovo stato della riga.|  
|SQL_ROW_DELETED [3]|La riga è stata eliminata dopo l'ultimo recupero da questo set di risultati.|  
|SQL_ROW_ADDED [4]|La riga inserita da **SQLBulkOperations**. Se la riga viene recuperata di nuovo da questo set di risultati o viene aggiornata da **SQLSetPos**, lo stato è SQL_ROW_SUCCESS.|  
|SQL_ROW_NOROW|Il set di righe sovrapposti la fine del set di risultati ed è stata restituita alcuna riga che corrisponde a questo elemento della matrice di stato di riga.|  
  
 [1] per keyset, misti cursori dinamici, se un valore di chiave viene aggiornato, viene considerata la riga di dati sono stati eliminati e aggiunta una nuova riga.  
  
 [2] alcuni driver non è in grado di rilevare gli aggiornamenti ai dati e pertanto non può restituire questo valore. Per determinare se un driver è possibile rilevare gli aggiornamenti alle righe refetched, un'applicazione chiama **SQLGetInfo** con l'opzione SQL_ROW_UPDATES.  
  
 [3] **SQLFetch** può restituire questo valore solo quando è distinta con chiamate a **SQLFetchScroll**. In questo modo **SQLFetch** si sposta in avanti il set di risultati e quando viene utilizzato in modo esclusivo, non recupera di nuovo tutte le righe. Poiché non è refetched alcuna riga, **SQLFetch** non rileva le modifiche apportate alle righe recuperate in precedenza. Tuttavia, se **SQLFetchScroll** posiziona il cursore prima di qualsiasi precedentemente recuperate le righe e **SQLFetch** è utilizzato per recuperare le righe, **SQLFetch** può rilevare eventuali modifiche alle le righe.  
  
 [4] restituito da SQLBulkOperations solo. Non è impostato dal **SQLFetch** o **SQLFetchScroll**.  
  
### <a name="rows-fetched-buffer"></a>Buffer di recupero di righe  
 Le righe recuperate buffer viene utilizzato per restituire il numero di righe recuperate, incluse le righe per cui è stato restituito alcun dato perché si è verificato un errore quando essi sono stati recuperati. In altre parole, è il numero di righe per cui il valore della matrice di stato di riga non è SQL_ROW_NOROW. L'indirizzo di questo buffer viene specificata con l'attributo SQL_ATTR_ROWS_FETCHED_PTR dell'istruzione. Il buffer è allocato dall'applicazione. L'impostazione è **SQLFetch** e **SQLFetchScroll**. Se il valore dell'attributo SQL_ATTR_ROWS_FETCHED_PTR istruzione è un puntatore null, queste funzioni non restituiscono il numero di righe recuperate. Per determinare il numero della riga corrente nel set di risultati, un'applicazione può chiamare **SQLGetStmtAttr** con l'attributo SQL_ATTR_ROW_NUMBER.  
  
 Il contenuto del buffer di righe recuperate è indefinito se **SQLFetch** o **SQLFetchScroll** non restituisce SQL_SUCCESS o SQL_SUCCESS_WITH_INFO, tranne quando viene restituito SQL_NO_DATA, nel qual caso il nelle righe del buffer di recupero è impostato su 0.  
  
### <a name="error-handling"></a>Gestione degli errori  
 Errori e avvisi è possono applicare alle singole righe o per l'intera funzione. Per ulteriori informazioni sui record di diagnostica, vedere [diagnostica](../../../odbc/reference/develop-app/diagnostics.md) e [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md).  
  
#### <a name="errors-and-warnings-on-the-entire-function"></a>Errori e avvisi nell'intera funzione  
 Se l'errore si applica all'intera funzione, ad esempio HYT00 SQLSTATE (Timeout scaduto) o SQLSTATE 24000 (stato del cursore non valido), **SQLFetch** restituisce SQL_ERROR e SQLSTATE applicabile. Il contenuto del buffer di set di righe non è definito e la posizione del cursore non viene modificata.  
  
 Se un avviso si applica all'intera funzione **SQLFetch** restituisce SQL_SUCCESS_WITH_INFO e SQLSTATE l'applicabile. I record di stato per gli avvisi che si applicano all'intera funzione vengono restituiti prima i record di stato che si applicano alle singole righe.  
  
#### <a name="errors-and-warnings-in-individual-rows"></a>Errori e avvisi in singole righe  
 Se un errore (ad esempio SQLSTATE 22012 (divisione per zero)) o un avviso (ad esempio SQLSTATE 01004 (dati troncati)) si applica a una singola riga, **SQLFetch**esegue le operazioni seguenti:  
  
-   Imposta l'elemento corrispondente della matrice di stato di riga SQL_ROW_ERROR per errori o SQL_ROW_SUCCESS_WITH_INFO per gli avvisi.  
  
-   Aggiunge zero o più record di stato che contengono SQLSTATE per l'errore o avviso.  
  
-   Imposta i campi numero di riga e colonna record di stato. Se **SQLFetch** non può determinare un numero di riga o colonna, imposta tale numero SQL_ROW_NUMBER_UNKNOWN o SQL_COLUMN_NUMBER_UNKNOWN, rispettivamente. Se il record di stato non viene applicato a una determinata colonna, **SQLFetch** SQL_NO_COLUMN_NUMBER imposta il numero di colonna.  
  
 **SQLFetch** continua il recupero delle righe fino a quando non essere recuperati tutte le righe nel set di righe. Restituisce SQL_SUCCESS_WITH_INFO, a meno che non si verifica un errore in ogni riga del set di righe (escluse le righe con stato SQL_ROW_NOROW), nel qual caso viene restituito SQL_ERROR. In particolare, se le dimensioni del set di righe sono 1 e si verifica un errore in tale riga, **SQLFetch** restituisce SQL_ERROR.  
  
 **SQLFetch** restituisce i record di stato nell'ordine di numero di riga. Ovvero, restituisce tutti i record di stato per le righe sconosciute (se presente); Restituisce quindi tutti i record di stato per la prima riga (se presente) e quindi restituisce tutti i record di stato per la seconda riga (se presente) e così via. I record di stato per ogni riga vengono ordinati in base alle normali regole per l'ordinamento dei record di stato. Per ulteriori informazioni, vedere "Sequenza di record di stato" in [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md).  
  
### <a name="descriptors-and-sqlfetch"></a>Descrittori e SQLFetch  
 Le sezioni seguenti descrivono come **SQLFetch** interagisce con descrittori.  
  
#### <a name="argument-mappings"></a>Mapping di argomento  
 Il driver imposta tutti i campi di descrizione in base agli argomenti di **SQLFetch**.  
  
#### <a name="other-descriptor-fields"></a>Altri campi di descrizione  
 I seguenti campi di descrizione vengono utilizzati da **SQLFetch**.  
  
|Campo di descrizione|DESC.|Campo|Impostare tramite|  
|----------------------|-----------|--------------|-----------------|  
|SQL_DESC_ARRAY_SIZE|ARD|Intestazione|Attributo di istruzione SQL_ATTR_ROW_ARRAY_SIZE|  
|SQL_DESC_ARRAY_STATUS_PTR|IRD|Intestazione|Attributo di istruzione vengono impostati SQL_ATTR_ROW_STATUS_PTR|  
|SQL_DESC_BIND_OFFSET_PTR|ARD|Intestazione|Attributo di istruzione SQL_ATTR_ROW_BIND_OFFSET_PTR|  
|SQL_DESC_BIND_TYPE|ARD|Intestazione|Attributo di istruzione SQL_ATTR_ROW_BIND_TYPE|  
|SQL_DESC_COUNT|ARD|Intestazione|*ColumnNumber* argomento di **SQLBindCol**|  
|SQL_DESC_DATA_PTR|ARD|record|*TargetValuePtr* argomento di **SQLBindCol**|  
|SQL_DESC_INDICATOR_PTR|ARD|record|*StrLen_or_IndPtr* argomento **SQLBindCol**|  
|SQL_DESC_OCTET_LENGTH|ARD|record|*BufferLength* argomento **SQLBindCol**|  
|SQL_DESC_OCTET_LENGTH_PTR|ARD|record|*StrLen_or_IndPtr* argomento **SQLBindCol**|  
|SQL_DESC_ROWS_PROCESSED_PTR|IRD|Intestazione|Attributo di istruzione SQL_ATTR_ROWS_FETCHED_PTR|  
|SQL_DESC_TYPE|ARD|record|*TargetType* argomento **SQLBindCol**|  
  
 Tutti i campi di descrizione possono essere impostati anche tramite **SQLSetDescField**.  
  
#### <a name="separate-length-and-indicator-buffers"></a>Lunghezza separato e buffer di indicatore  
 Le applicazioni possono associare un singolo buffer o due buffer separato che può essere usato per contenere i valori di lunghezza e indicatore. Quando un'applicazione chiama **SQLBindCol**, il driver imposta i campi SQL_DESC_OCTET_LENGTH_PTR e SQL_DESC_INDICATOR_PTR del ARD per lo stesso indirizzo, viene passato il *StrLen_or_IndPtr* argomento. Quando un'applicazione chiama **SQLSetDescField** o **SQLSetDescRec**, è possibile impostare questi due campi a indirizzi diversi.  
  
 **SQLFetch** determina se l'applicazione è specificato separati i buffer di lunghezza e indicatore. In questo caso, quando i dati non sono NULL, **SQLFetch** il buffer di indicatore viene impostato su 0 e restituisce la lunghezza del buffer di lunghezza. Quando i dati sono NULL, **SQLFetch** imposta il buffer di indicatore su SQL_NULL_DATA e non modifica il buffer di lunghezza.  
  
### <a name="code-example"></a>Esempio di codice  
 Vedere [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md), [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md), [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md), e [SQLProcedures](../../../odbc/reference/syntax/sqlprocedures-function.md).  
  
### <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Associazione di un buffer a una colonna in un set di risultati|[Funzione SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|L'elaborazione di istruzione di annullamento|[Funzione SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Restituzione di informazioni su una colonna in un set di risultati|[Funzione SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|Esecuzione di un'istruzione SQL|[Funzione SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|L'esecuzione di un'istruzione SQL preparata|[Funzione SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Recupero di un blocco di dati o di scorrimento di un risultato impostato|[Funzione SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Chiudere il cursore sull'istruzione|[Funzione SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|Il recupero o parte di una colonna di dati|[Funzione SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|Restituzione del numero di risultati le colonne del set|[Funzione SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|Preparazione di un'istruzione per l'esecuzione|[Funzione SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)

