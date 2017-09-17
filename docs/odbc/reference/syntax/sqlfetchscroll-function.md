---
title: Funzione SQLFetchScroll | Documenti Microsoft
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
- SQLFetchScroll
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLFetchScroll
helpviewer_keywords:
- SQLFetchScroll function [ODBC]
ms.assetid: c0243667-428c-4dda-ae91-3c307616a1ac
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 79224469fe1e6e4f0840eceb394b30cec63fcd2a
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlfetchscroll-function"></a>Funzione SQLFetchScroll
**Conformità**  
 Introdotta: versione ODBC 3.0 aderenza: 92 ISO  
  
 **Riepilogo**  
 **SQLFetchScroll** recupera il set specificato di righe di dati dal set di risultati e restituisce i dati per tutte le colonne associate. Set di righe può essere specificata in una posizione assoluta o relativa o dal segnalibro.  
  
 Quando si utilizza un driver ODBC 2. x, Driver Manager esegue il mapping di questa funzione per **SQLExtendedFetch**. Per ulteriori informazioni, vedere [Mapping di funzioni di sostituzione per la compatibilità con le versioni precedenti di applicazioni](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLFetchScroll(  
      SQLHSTMT      StatementHandle,  
      SQLSMALLINT   FetchOrientation,  
      SQLLEN        FetchOffset);  
```  
  
## <a name="arguments"></a>Argomenti  
 *StatementHandle*  
 [Input] Handle di istruzione.  
  
 *FetchOrientation*  
 [Input]  
  
 Tipo di recupero:  
  
 SQL_FETCH_NEXT  
  
 SQL_FETCH_PRIOR  
  
 SQL_FETCH_FIRST  
  
 SQL_FETCH_LAST  
  
 SQL_FETCH_ABSOLUTE  
  
 SQL_FETCH_RELATIVE  
  
 SQL_FETCH_BOOKMARK  
  
 Per ulteriori informazioni, vedere "Posizionamento del cursore" nella sezione "Commenti".  
  
 *FetchOffset*  
 [Input]  
  
 Numero della riga da recuperare. L'interpretazione di questo argomento dipende dal valore del *FetchOrientation* argomento. Per ulteriori informazioni, vedere "Posizionamento del cursore" nella sezione "Commenti".  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_STILL_EXECUTING, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLFetchScroll** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato può essere ottenuto chiamando **SQLGetDiagRec** con un HandleType su SQL_HANDLE_STMT e un Handle di StatementHandle. Nella tabella seguente sono elencati i valori SQLSTATE comunemente restituiti da **SQLFetchScroll** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato. Se si verifica un errore in una singola colonna, **SQLGetDiagField** può essere chiamato con un DiagIdentifier di SQL_DIAG_COLUMN_NUMBER per determinare la colonna a cui si è verificato l'errore; e **SQLGetDiagField** può essere chiamato con un DiagIdentifier di SQL_DIAG_ROW_NUMBER per determinare la riga che contiene tale colonna.  
  
 Per tutti questi SQLSTATE restituiti SQL_SUCCESS_WITH_INFO o SQL_ERROR (eccetto SQLSTATE 01xxx), viene restituito SQL_SUCCESS_WITH_INFO, se si verifica un errore in uno o più, ma non tutte le righe di un'operazione su più righe e viene restituito SQL_ERROR se si verifica un errore in un riga singola operazione.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01004|Stringa di dati corretto troncato|Stringa o dati binari restituiti per una colonna ha restituito il troncamento di un carattere non vuoto o dati binari non NULL. Se si trattasse di un valore stringa, è stato troncato a destra.|  
|01S01|Errore alla riga|Si è verificato un errore durante il recupero di una o più righe.<br /><br /> (Se questa SQLSTATE viene restituito quando un'applicazione ODBC 3*x* applicazione sta utilizzando un'API ODBC 2*x* driver, può essere ignorato.)|  
|01S06|Tentativo di recupero eseguito prima che il set di risultati restituito il primo set di righe|Il set di righe richiesto sovrapposte l'inizio del set di risultati quando FetchOrientation stato SQL_FETCH_PRIOR, la posizione corrente è oltre la prima riga e il numero della riga corrente è minore o uguale alla dimensione del set di righe.<br /><br /> Il set di righe richiesto sovrapposte l'inizio del set di risultati quando FetchOrientation sia SQL_FETCH_PRIOR, la posizione corrente è oltre la fine del set di risultati e le dimensioni del set di righe sono maggiore della dimensione del set di risultati.<br /><br /> Il set di righe richiesto sovrapposte l'inizio del set di risultati quando FetchOrientation sia SQL_FETCH_RELATIVE, FetchOffset è negativo e il valore assoluto di FetchOffset è minore o uguale alla dimensione del set di righe.<br /><br /> Il set di righe richiesto sovrapposta l'inizio del set di risultati quando FetchOrientation sia SQL_FETCH_ABSOLUTE, FetchOffset è negativo e il valore assoluto di FetchOffset è maggiore della dimensione del set di risultati, ma minore o uguale alla dimensione del set di righe.<br /><br /> (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01S07|Troncamento frazionario.|I dati restituiti per una colonna è stati troncati. Per i tipi di dati numerici, la parte frazionaria del numero è stata troncata. Per ora, timestamp e tipi di dati di intervallo contenente un componente di ora, la parte frazionaria del tempo è stata troncata.<br /><br /> (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|07006|Violazione dell'attributo del tipo di dati|Impossibile convertire il valore di dati di una colonna nel set di risultati per il tipo di dati specificato da *TargetType* in **SQLBindCol**.<br /><br /> Colonna 0 è stata associata a un tipo di dati di SQL_C_BOOKMARK e l'attributo di istruzione SQL_ATTR_USE_BOOKMARKS è stato impostato su SQL_UB_VARIABLE.<br /><br /> Colonna 0 è stata associata a un tipo di dati di SQL_C_VARBOOKMARK e non è stato impostato l'attributo di istruzione SQL_ATTR_USE_BOOKMARKS SQL_UB_VARIABLE.|  
|07009|Indice del descrittore non valido|Il driver non è un'API ODBC 2*x* driver che non supporta **SQLExtendedFetch**, e un numero di colonna specificato nell'associazione per una colonna è 0.<br /><br /> Colonna 0 è stato associato, e l'attributo di istruzione SQL_ATTR_USE_BOOKMARKS era impostato su SQL_UB_OFF.|  
|08S01|Errore del collegamento di comunicazione|Collegamento di comunicazione tra il driver e l'origine dati a cui era connesso il driver non è stato possibile prima dell'elaborazione della funzione è stata completata.|  
|22001|Stringa di dati corretto troncato|Un segnalibro a lunghezza variabile per una colonna restituito è stato troncato.|  
|22002|Variabile indicatore necessaria ma non fornito|NULL è stata recuperati i dati in una colonna il cui *StrLen_or_IndPtr* impostazione **SQLBindCol** (o l'impostazione SQL_DESC_INDICATOR_PTR **SQLSetDescField** o ** SQLSetDescRec**) è un puntatore null.|  
|22003|Valore numerico non compreso nell'intervallo|Restituire il valore numerico (come valore numerico o stringa) per uno o più colonne associate avrebbe causato la parte intera (in contrapposizione frazionari) del numero da troncare.<br /><br /> Per ulteriori informazioni, vedere [la conversione di dati da SQL a tipi di dati C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) in [appendice d: i tipi di dati](../../../odbc/reference/appendixes/appendix-d-data-types.md).|  
|22007|Formato di datetime non valido|Una colonna di tipo carattere nel set di risultati è stata associata a una data, ora o struttura di timestamp C, e un valore nella colonna è, rispettivamente, una data non valida, il tempo o timestamp.|  
|22012|Divisione per zero|Da un'espressione aritmetica ha restituito un valore, ciò ha provocato la divisione per zero.|  
|22015|Overflow del campo intervallo|L'assegnazione da un numerico esatto o l'intervallo di tipo SQL a un tipo di intervallo C ha causato una perdita di cifre significative nel campo iniziale.<br /><br /> Durante il recupero di dati a un tipo di intervallo C, si è verificato alcun rappresentazione del valore di tipo SQL nel tipo di intervallo C.|  
|22018|Valore di carattere non valido per la specifica del cast|Una colonna di tipo carattere nel set di risultati è stata associata a un buffer di caratteri C e la colonna contiene un carattere che non ha ricevuto alcuna rappresentazione nel set di caratteri del buffer.<br /><br /> Il tipo C è stato un numerico esatto o approssimativo, un valore datetime o un tipo di dati di intervallo. il tipo SQL della colonna è un tipo di dati character; il valore nella colonna non ha un valore letterale valido del tipo C associato.|  
|24000|Stato del cursore non valido|Il *StatementHandle* era in uno stato eseguito ma è stato associato alcun set di risultati di *StatementHandle*.|  
|40001|Errore di serializzazione.|La transazione in cui è stato eseguito l'operazione di recupero è stata interrotta per impedire un deadlock.|  
|40003|Completamento delle istruzioni sconosciuto|Impossibile stabilire la connessione associata durante l'esecuzione di questa funzione e non è possibile determinare lo stato della transazione.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel * \*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver è stato in grado di allocare la memoria necessaria per supportare l'esecuzione o il completamento della funzione.|  
|HY008|Operazione annullata|L'elaborazione asincrona è stata abilitata per il *StatementHandle*. La funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle*. Quindi la funzione è stata chiamata nuovamente sul *StatementHandle*.<br /><br /> La funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle* da un thread diverso in un applicazioni multithread.|  
|HY010|Errore nella sequenza (funzione)|(DM) a cui è stata chiamata per l'handle di connessione associata a una funzione in modo asincrono in esecuzione il *StatementHandle*. Questa funzione asincrona era ancora in esecuzione quando il **SQLFetchScroll** funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** è stato chiamato per il *StatementHandle* e restituito SQL_PARAM_DATA_ È DISPONIBILE. Questa funzione è stata chiamata prima che i dati sono stati recuperati per tutti i parametri con flusso.<br /><br /> (DM) specificato *StatementHandle* non è stato eseguito. La funzione è stata chiamata senza chiamare prima il metodo **SQLExecDirect**, **SQLExecute** o una funzione di catalogo.<br /><br /> (DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione (non è presente uno) di *StatementHandle* ed era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos** è stato chiamato per il * StatementHandle* e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima che sono stati inviati dati per tutti i parametri data-at-execution o colonne.<br /><br /> (DM) **SQLFetch** è stato chiamato per il *StatementHandle* dopo **SQLExtendedFetch** è stato chiamato e prima **SQLFreeStmt** con il SQL _ Opzione di chiusura è stato chiamato.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY090|Lunghezza di stringa o di buffer non valida|L'attributo di istruzione SQL_ATTR_USE_BOOKMARK è stato impostato su SQL_UB_VARIABLE e colonna 0 è stata associata a un buffer, la cui lunghezza non è uguale alla lunghezza massima per il segnalibro per questo set di risultati. (Questa lunghezza è disponibile nel campo SQL_DESC_OCTET_LENGTH di implementazione e può essere ottenuta chiamando **SQLDescribeCol**, **SQLColAttribute**, o **SQLGetDescField**.)|  
|HY106|Tipo non compreso nell'intervallo di recupero|DM) il valore specificato per l'argomento FetchOrientation non è valido.<br /><br /> (DM) FetchOrientation l'argomento è stato impostato su SQL_FETCH_BOOKMARK, e l'attributo di istruzione SQL_ATTR_USE_BOOKMARKS era impostato su SQL_UB_OFF.<br /><br /> Il valore dell'attributo di istruzione SQL_ATTR_CURSOR_TYPE era SQL_CURSOR_FORWARD_ONLY e il valore dell'argomento che non è FetchOrientation SQL_FETCH_NEXT.<br /><br /> Il valore dell'attributo di istruzione SQL_ATTR_CURSOR_SCROLLABLE è SQL_NONSCROLLABLE e il valore dell'argomento che non è FetchOrientation SQL_FETCH_NEXT.|  
|HY107|Valore di riga non compreso nell'intervallo|Il valore specificato con l'attributo di istruzione SQL_ATTR_CURSOR_TYPE SQL_CURSOR_KEYSET_DRIVEN, ma non ha il valore specificato con l'attributo di istruzione SQL_ATTR_KEYSET_SIZE maggiore di 0 e minore del valore specificato con il SQL_ATTR_ROW_ARRAY_ Attributo di istruzione di dimensioni.|  
|HY111|Valore del segnalibro non valido|L'argomento FetchOrientation era impostato su SQL_FETCH_BOOKMARK e segnalibro a cui fa riferimento il valore dell'attributo di istruzione SQL_ATTR_FETCH_BOOKMARK_PTR non è valido o è un puntatore null.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Funzionalità facoltativa non implementata.|L'origine dati o driver non supporta la conversione specificata dalla combinazione del *TargetType* in **SQLBindCol** e il tipo di dati SQL della colonna corrispondente.|  
|HYT00|Timeout|Il periodo di timeout della query è scaduto prima origine dati ha restituito il set di risultati richiesti. Il periodo di timeout viene impostato tramite la funzione SQLSetStmtAttr, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|Il driver (DM) associato il *StatementHandle* non supporta la funzione.|  
|IM017|Polling è disabilitato in modalità di notifica asincrona|Ogni volta che viene utilizzato il modello di notifica, il polling è disabilitato.|  
|IM018|**SQLCompleteAsync** non è stato chiamato per completare l'operazione asincrona precedente su questo handle.|Se la chiamata di funzione precedente dell'handle restituisce SQL_STILL_EXECUTING e se è abilitata la modalità di notifica, **SQLCompleteAsync** deve essere chiamato per l'handle per eseguire la post-elaborazione e completare l'operazione.|  
  
## <a name="comments"></a>Commenti  
 **SQLFetchScroll** restituisce un set di righe specificato dal set di risultati. Set di righe può essere specificata in base alla posizione assoluta o relativa o dal segnalibro. **SQLFetchScroll** può essere chiamato solo quando esiste un set di risultati, vale a dire, dopo una chiamata che crea un set di risultati e prima del cursore sopra di set di risultati viene chiuso. Se tutte le colonne sono associate, restituisce i dati in tali colonne. Se l'applicazione non è specificato un puntatore a una matrice di stato di riga o di un buffer in cui restituire il numero di righe recuperate, **SQLFetchScroll** restituisce anche le informazioni. Le chiamate a **SQLFetchScroll** può essere combinato con chiamate a **SQLFetch** ma non può essere combinato con chiamate a **SQLExtendedFetch**.  
  
 Per ulteriori informazioni, vedere [cursori a blocchi usando](../../../odbc/reference/develop-app/using-block-cursors.md) e [utilizzando i cursori scorrevoli](../../../odbc/reference/develop-app/using-scrollable-cursors.md).  
  
## <a name="positioning-the-cursor"></a>Posizionando il cursore  
 Quando viene creato il set di risultati, il cursore viene posizionato prima dell'inizio del set di risultati. **SQLFetchScroll** posiziona il cursore a blocchi in base ai valori del *FetchOrientation* e *FetchOffset* argomenti, come illustrato nella tabella seguente. Le regole precise per determinare l'inizio del nuovo set di righe vengono visualizzate nella sezione successiva.  
  
|FetchOrientation|Significato|  
|----------------------|-------------|  
|SQL_FETCH_NEXT|Restituisce il set di righe successivo. Ciò equivale a chiamare il metodo **SQLFetch**.<br /><br /> **SQLFetchScroll** ignora il valore di *FetchOffset*.|  
|SQL_FETCH_PRIOR|Restituisce il set di righe precedenti.<br /><br /> **SQLFetchScroll** ignora il valore di *FetchOffset*.|  
|SQL_FETCH_RELATIVE|Restituire il set di righe *FetchOffset* dall'inizio del set di righe corrente.|  
|SQL_FETCH_ABSOLUTE|Restituisce il set di righe a partire dalla riga *FetchOffset*.|  
|SQL_FETCH_FIRST|Restituisce il primo set di righe nel set di risultati.<br /><br /> **SQLFetchScroll** ignora il valore di *FetchOffset*.|  
|SQL_FETCH_LAST|Restituisce l'ultimo intero set di righe nel set di risultati.<br /><br /> **SQLFetchScroll** ignora il valore di *FetchOffset*.|  
|SQL_FETCH_BOOKMARK|Restituisce il set di righe FetchOffset righe dal segnalibro specificato dall'attributo di istruzione SQL_ATTR_FETCH_BOOKMARK_PTR.|  
  
 Driver non sono necessari per supportare tutti gli orientamenti di recupero; un'applicazione chiama **SQLGetInfo** con un tipo di informazioni di SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 o SQL_STATIC_CURSOR_ATTRIBUTES1 (a seconda del tipo di cursore) per determinare quali fetch gli orientamenti supportati dal driver. L'applicazione deve esaminare le maschere di bit SQL_CA1_NEXT, SQL_CA1_RELATIVE, SQL_CA1_ABSOLUTE e WQL_CA1_BOOKMARK in questi tipi di informazioni. Inoltre, se il cursore è forward-only e FetchOrientation non SQL_FETCH_NEXT, **SQLFetchScroll** restituisce SQLSTATE HY106 (tipo compreso nell'intervallo di recupero).  
  
 L'attributo di istruzione SQL_ATTR_ROW_ARRAY_SIZE specifica il numero di righe nel set di righe. Se il set di righe recuperate da **SQLFetchScroll** si sovrappone la fine del set di risultati, **SQLFetchScroll** restituisce un set di righe parziale. Vale a dire se S + R-1 è maggiore di L, dove S è la riga iniziale del set di righe recuperate, R è la dimensione del set di righe e L è l'ultima riga nel set di risultati, quindi solo il primo L – S + 1 righe del set di righe sono validi. Le righe rimanenti sono vuote e lo stato del SQL_ROW_NOROW.  
  
 Dopo aver **SQLFetchScroll** restituisce, la riga corrente è la prima riga del set di righe.  
  
## <a name="cursor-positioning-rules"></a>Le regole di posizionamento del cursore  
 Le sezioni seguenti descrivono le regole precise per ogni valore di FetchOrientation. Tali regole utilizzano la notazione seguente.  
  
|Notazione|Significato|  
|--------------|-------------|  
|*Operazioni preliminari*|Il cursore a blocchi viene posizionato prima dell'inizio del set di risultati. Se la prima riga del nuovo set di righe è precedente all'inizio del set di risultati, **SQLFetchScroll** restituisce SQL_NO_DATA.|  
|*Dopo la fine*|Il cursore a blocchi viene posizionato dopo aver impostato la fine del risultato. Se è la prima riga del set di righe di nuovo dopo la fine del set di risultati, **SQLFetchScroll** restituisce SQL_NO_DATA.|  
|*CurrRowsetStart*|Il numero della prima riga nel set di righe corrente.|  
|*LastResultRow*|Il numero dell'ultima riga nel set di risultati.|  
|*RowsetSize*|Le dimensioni del set di righe.|  
|*FetchOffset*|Il valore di *FetchOffset* argomento.|  
|*BookmarkRow*|La riga corrispondente al segnalibro specificato dall'attributo di istruzione SQL_ATTR_FETCH_BOOKMARK_PTR.|  
  
## <a name="sqlfetchnext"></a>SQL_FETCH_NEXT  
 Le regole seguenti si applicano.  
  
|Condizione|Prima riga del nuovo set di righe|  
|---------------|-----------------------------|  
|*Operazioni preliminari*|1|  
|*CurrRowsetStart + RowsetSize*[1] * \<= LastResultRow*|*CurrRowsetStart + RowsetSize*[1]|  
|*CurrRowsetStart + RowsetSize*[1]*> LastResultRow*|*Dopo la fine*|  
|*Dopo la fine*|*Dopo la fine*|  
  
 [1] se le dimensioni del set di righe sono stata modificata dopo la chiamata precedente al recupero di righe, è la dimensione del set di righe che è stata utilizzata con la chiamata precedente.  
  
## <a name="sqlfetchprior"></a>SQL_FETCH_PRIOR  
 Le regole seguenti si applicano.  
  
|Condizione|Prima riga del nuovo set di righe|  
|---------------|-----------------------------|  
|*Operazioni preliminari*|*Operazioni preliminari*|  
|*CurrRowsetStart = 1*|*Operazioni preliminari*|  
|*1 < CurrRowsetStart < = RowsetSize* <sup>[2].</sup>|*1* <sup>[1]</sup>|  
|*CurrRowsetStart > RowsetSize* <sup>[2]</sup>|*CurrRowsetStart – RowsetSize* <sup>[2]</sup>|  
|*Dopo la fine e LastResultRow < RowsetSize* <sup>[2]</sup>|*1* <sup>[1]</sup>|  
|*Dopo la fine LastResultRow e > = RowsetSize* <sup>[2]</sup>|*LastResultRow – RowsetSize + 1* <sup>[2].</sup>|  
  
 [1] **SQLFetchScroll** restituisce SQLSTATE 01S06 (tentativo di recupero prima che il set di risultati restituito il primo set di righe) e SQL_SUCCESS_WITH_INFO.  
  
 [2] se le dimensioni del set di righe sono stata modificata dopo la chiamata precedente al recupero di righe, questa è la nuova dimensione del set di righe.  
  
## <a name="sqlfetchrelative"></a>SQL_FETCH_RELATIVE  
 Le regole seguenti si applicano.  
  
|Condizione|Prima riga del nuovo set di righe|  
|---------------|-----------------------------|  
|*(Prima di avviare e FetchOffset > 0) O (dopo la fine e FetchOffset < 0)*|*--* <sup>[1]</sup>|  
|*BeforeStart e FetchOffset < = 0*|*Operazioni preliminari*|  
|*CurrRowsetStart = 1 e FetchOffset < 0*|*Operazioni preliminari*|  
|*CurrRowsetStart > 1 CurrRowsetStart AND + FetchOffset < 1 e &#124; FetchOffset &#124; > RowsetSize* <sup>[3]</sup>|*Operazioni preliminari*|  
|*CurrRowsetStart > 1 CurrRowsetStart AND + FetchOffset < 1 e &#124; FetchOffset &#124; < = RowsetSize* <sup>[3]</sup>|*1* <sup>[2]</sup>|  
|*1 < = CurrRowsetStart + FetchOffset \<= LastResultRow*|*CurrRowsetStart + FetchOffset*|  
|*CurrRowsetStart + FetchOffset > LastResultRow*|*Dopo la fine*|  
|*Dopo la fine FetchOffset e > = 0*|*Dopo la fine*|  
  
 [1] ***SQLFetchScroll*** restituisce il set di righe stesso come se fosse stato chiamato con FetchOrientation impostato su SQL_FETCH_ABSOLUTE. Per ulteriori informazioni, vedere la sezione "SQL_FETCH_ABSOLUTE".  
  
 [2] **SQLFetchScroll** restituisce SQLSTATE 01S06 (tentativo di recupero prima che il set di risultati restituito il primo set di righe) e SQL_SUCCESS_WITH_INFO.  
  
 [3] se le dimensioni del set di righe sono stata modificata dopo la chiamata precedente al recupero di righe, questa è la nuova dimensione del set di righe.  
  
## <a name="sqlfetchabsolute"></a>SQL_FETCH_ABSOLUTE  
 Le regole seguenti si applicano.  
  
|Condizione|Prima riga del nuovo set di righe|  
|---------------|-----------------------------|  
|*FetchOffset < 0 AND &#124; FetchOffset &#124; < = LastResultRow*|*LastResultRow + FetchOffset + 1*|  
|*FetchOffset < 0 AND &#124; FetchOffset &#124; > LastResultRow e &#124; FetchOffset &#124; > RowsetSize* <sup>[2]</sup>|*Operazioni preliminari*|  
|*FetchOffset < 0 AND &#124; FetchOffset &#124; > LastResultRow e &#124; FetchOffset &#124; < = RowsetSize* <sup>[2]</sup>|*1* <sup>[1]</sup>|  
|*FetchOffset = 0*|*Operazioni preliminari*|  
|*1 < = FetchOffset \<= LastResultRow*|*FetchOffset*|  
|*FetchOffset > LastResultRow*|*Dopo la fine*|  
  
 [1] **SQLFetchScroll** restituisce SQLSTATE 01S06 (tentativo di recupero prima che il set di risultati restituito il primo set di righe) e SQL_SUCCESS_WITH_INFO.  
  
 [2] se le dimensioni del set di righe sono stata modificata dopo la chiamata precedente al recupero di righe, questa è la nuova dimensione del set di righe.  
  
 Un recupero assoluto eseguito a fronte di un cursore dinamico non è il risultato richiesto perché non sono posizioni delle righe in un cursore dinamico. Questa operazione è equivalente a un'operazione di recupero prima seguita da un'istruzione fetch relative; non è un'operazione atomica, ovvero un recupero assoluto su un cursore statico.  
  
## <a name="sqlfetchfirst"></a>SQL_FETCH_FIRST  
 Le regole seguenti si applicano.  
  
|Condizione|Prima riga del nuovo set di righe|  
|---------------|-----------------------------|  
|*Qualsiasi*|*1*|  
  
## <a name="sqlfetchlast"></a>SQL_FETCH_LAST  
 Le regole seguenti si applicano.  
  
|Condizione|Prima riga del nuovo set di righe|  
|---------------|-----------------------------|  
|*RowsetSize* <sup>[1]</sup> < = LastResultRow|*LastResultRow – RowsetSize + 1* <sup>[1]</sup>|  
|*RowsetSize* <sup>[1]</sup> > LastResultRow|*1*|  
  
 [1] se le dimensioni del set di righe sono stata modificata dopo la chiamata precedente al recupero di righe, questa è la nuova dimensione del set di righe.  
  
## <a name="sqlfetchbookmark"></a>SQL_FETCH_BOOKMARK  
 Le regole seguenti si applicano.  
  
|Condizione|Prima riga del nuovo set di righe|  
|---------------|-----------------------------|  
|*BookmarkRow + FetchOffset < 1*|*Operazioni preliminari*|  
|*1 < = BookmarkRow + FetchOffset \<= LastResultRow*|*BookmarkRow + FetchOffset*|  
|*BookmarkRow + FetchOffset > LastResultRow*|*Dopo la fine*|  
  
 Per informazioni sui segnalibri, vedere [segnalibri (ODBC)](../../../odbc/reference/develop-app/bookmarks-odbc.md).  
  
## <a name="effect-of-deleted-added-and-error-rows-on-cursor-movement"></a>Effetto di aggiunti, eliminati e le righe di errore in uno spostamento del cursore  
 Cursori statici e basati su keyset in alcuni casi rilevano le righe aggiunte al risultato impostare e rimuovere le righe eliminate dal set di risultati. Chiamando **SQLGetInfo** e SQL_STATIC_CURSOR_ATTRIBUTES2 SQL_KEYSET_CURSOR_ATTRIBUTES2 opzioni ed esaminando il SQL_CA2_SENSITIVITY_ADDITIONS SQL_CA2_SENSITIVITY_DELETIONS e SQL_CA2_SENSITIVITY_ Maschere di aggiornamenti, un'applicazione determina se i cursori implementati da un driver specifico eseguire questa operazione. Per i driver che è possibile rilevare le righe eliminate e rimuoverle, nei paragrafi seguenti vengono descritti gli effetti di questo comportamento. Per i driver che è in grado di rilevare le righe eliminate ma non è possibile rimuoverli, le eliminazioni non hanno effetto sui movimenti del cursore e nei paragrafi seguenti non sono applicabili.  
  
 Se il cursore rileva le righe aggiunte al set di risultati o rimuove le righe eliminate dal set di risultati, viene visualizzato come se rileva le modifiche solo quando il recupero dei dati. Include il caso quando **SQLFetchScroll** viene chiamato con FetchOrientation impostato su SQL_FETCH_RELATIVE e FetchOffset impostato su 0 per recupera di nuovo set di righe dello stesso, ma non include il caso quando viene chiamato SQLSetPos con fOption impostato su SQL _ AGGIORNAMENTO. In quest'ultimo caso, vengono aggiornati i dati nei buffer di set di righe, ma le righe non refetched ed eliminate non vengono rimossi dal set di risultati. Pertanto, quando una riga viene eliminata da o inserita nel set di righe corrente, il cursore non modifica i buffer di set di righe. In alternativa, rileva la modifica durante il recupero qualsiasi set di righe che in precedenza, inclusa la riga eliminata o ora include la riga inserita.  
  
 Esempio:  
  
```  
// Fetch the next rowset.  
SQLFetchScroll(hstmt, SQL_FETCH_NEXT, 0);  
// Delete third row of the rowset. Does not modify the rowset buffers.  
SQLSetPos(hstmt, 3, SQL_DELETE, SQL_LOCK_NO_CHANGE);  
// The third row has a status of SQL_ROW_DELETED after this call.  
SQLSetPos(hstmt, 3, SQL_REFRESH, SQL_LOCK_NO_CHANGE);  
// Refetch the same rowset. The third row is removed, replaced by what  
// was previously the fourth row.  
SQLFetchScroll(hstmt, SQL_FETCH_RELATIVE, 0);  
```  
  
 Quando **SQLFetchScroll** restituisce un nuovo set di righe che dispone di una posizione rispetto al set di righe corrente, ovvero FetchOrientation è SQL_FETCH_NEXT, SQL_FETCH_PRIOR o SQL_FETCH_RELATIVE, ovvero non include modifiche al set di righe corrente Quando si calcola la posizione iniziale del nuovo set di righe. Tuttavia, include modifiche all'esterno del set di righe corrente se è in grado di rilevarli. Inoltre, quando **SQLFetchScroll** restituisce un nuovo set di righe che dispone di una posizione indipendente del set di righe corrente, ovvero FetchOrientation è SQL_FETCH_FIRST, SQL_FETCH_LAST, SQL_FETCH_ABSOLUTE o SQL_FETCH_BOOKMARK:, include tutte le modifiche è in grado di rilevare, anche se sono nel set di righe corrente.  
  
 Per determinare se le righe appena aggiunte sono all'interno o all'esterno di set di righe corrente, un set di righe parziale è considerato termina l'ultima riga valido; ovvero, l'ultima riga per il quale lo stato di riga non è SQL_ROW_NOROW. Si supponga, ad esempio, il cursore è in grado di rilevare le righe appena aggiunte, il set di righe corrente è un set di righe parziale, l'applicazione aggiunge nuove righe e il cursore queste righe vengono aggiunte alla fine del set di risultati. Se l'applicazione chiama **SQLFetchScroll** con FetchOrientation impostato su SQL_FETCH_NEXT, **SQLFetchScroll** restituisce il set di righe a partire dalla prima riga appena aggiunta.  
  
 Si supponga, ad esempio, il set di righe corrente è costituito da righe 21-30, la dimensione del set di righe è 10, il cursore rimuove le righe eliminate dal set di risultati e il cursore rileva le righe aggiunte al set di risultati. Nella tabella seguente sono illustrate le righe **SQLFetchScroll** restituisce in diverse situazioni.  
  
|Cambia|Tipo di istruzione FETCH|FetchOffset|Nuovo set di righe [1]|  
|------------|----------------|-----------------|---------------------|  
|Eliminare la riga 21|NEXT|0|31 a 40|  
|Eliminare una riga 31|NEXT|0|32 a 41|  
|Inserire una riga tra le righe 21 e 22|NEXT|0|31 a 40|  
|Inserire una riga tra le righe 30 e 31|NEXT|0|Riga inserita, 31 a 39|  
|Eliminare la riga 21|PRIOR|0|11 a 20|  
|Eliminare la riga 20|PRIOR|0|10 a 19|  
|Inserire una riga tra le righe 21 e 22|PRIOR|0|11 a 20|  
|Inserire una riga tra le righe 20 e 21|PRIOR|0|riga inserita da 12 a 20,|  
|Eliminare la riga 21|RELATIVE|0|22 a 31<sup>[2]</sup>|  
|Eliminare la riga 21|RELATIVE|1|22 a 31|  
|Inserire una riga tra le righe 21 e 22|RELATIVE|0|riga inserita, 21, 22 a 29|  
|Inserire una riga tra le righe 21 e 22|RELATIVE|1|22 a 31|  
|Eliminare la riga 21|ABSOLUTE|21|22 a 31<sup>[2]</sup>|  
|Eliminare una riga 22|ABSOLUTE|21|21, 23 a 31|  
|Inserire una riga tra le righe 21 e 22|ABSOLUTE|22|Riga inserita, 22 a 29|  
  
 [1] la colonna utilizza i numeri di riga prima di tutte le righe inserite o eliminate.  
  
 [2] In questo caso, il cursore tenta di restituire le righe a partire dalla riga 21. Poiché riga 21 è stata eliminata, la prima riga che restituisce è riga 22.  
  
 Le righe di errore (ovvero, le righe con lo stato di SQL_ROW_ERROR) non influenzano lo spostamento del cursore. Ad esempio, se il set di righe corrente inizia con la riga 11 e lo stato di riga 11 è SQL_ROW_ERROR, la chiamata **SQLFetchScroll** con FetchOrientation impostato su SQL_FETCH_RELATIVE e FetchOffset è impostato su 5 restituisce il set di righe a partire dalla riga 16, esattamente come se lo stato di riga 11 SQL_SUCCESS.  
  
## <a name="returning-data-in-bound-columns"></a>Restituzione di dati in colonne associate  
 **SQLFetchScroll** restituisce i dati in colonne associate in modo analogo **SQLFetch**. Per ulteriori informazioni, vedere "restituzione di dati in colonne"associate in [SQLFetch-funzione](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
 Se nessuna colonna è associata, **SQLFetchScroll** non restituisce dati ma sposta il cursore a blocchi nella posizione specificata. Se i dati possono essere recuperati da colonne non associate di un cursore a blocchi con **SQLGetData** dipende dal driver. Questa funzionalità è supportata se una chiamata a **SQLGetInfo** restituisce il SQL_GD_BLOCK bit per il tipo di informazioni SQL_GETDATA_EXTENSIONS.  
  
## <a name="buffer-addresses"></a>Indirizzi di buffer  
 **SQLFetchScroll** utilizza la stessa formula per determinare l'indirizzo del buffer di dati e lunghezza/indicatore come **SQLFetch**. Per ulteriori informazioni, vedere "Buffer indirizzi" in [funzione SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
## <a name="row-status-array"></a>Matrice di stato di riga  
 **SQLFetchScroll** imposta valori della matrice di stato di riga nello stesso modo come SQLFetch. Per ulteriori informazioni, vedere "Matrice di stato di riga" in [SQLFetch-funzione](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
## <a name="rows-fetched-buffer"></a>Buffer di recupero di righe  
 **SQLFetchScroll** restituisce il numero di righe recuperate nel buffer di righe recuperate in modo analogo **SQLFetch**. Per ulteriori informazioni, vedere "Buffer di recupero righe" in [SQLFetch-funzione](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
## <a name="error-handling"></a>Gestione degli errori  
 Quando un'applicazione chiama **SQLFetchScroll** nel driver ODBC 3. x, gestione Driver chiama **SQLFetchScroll** nel driver. Quando un'applicazione chiama **SQLFetchScroll** nel driver ODBC 2. x, gestione Driver chiamate SQLExtendedFetch nel driver. Poiché **SQLFetchScroll** e SQLExtendedFetch gestire gli errori in modo leggermente diverso, l'applicazione non vede il comportamento dell'errore leggermente diverso quando viene chiamata **SQLFetchScroll** in ODBC 2. x e ODBC driver 3. x.  
  
 **SQLFetchScroll** restituisce errori e avvisi in modo analogo **SQLFetch**; per ulteriori informazioni, vedere "Gestione di errori" in **SQLFetch**. **SQLExtendedFetch** restituisce errori nello stesso modo come **SQLFetch**, con le eccezioni seguenti:  
  
 Quando viene generato un avviso che si applica a una particolare riga nel set di righe, SQLExtendedFetch imposta la voce corrispondente nella matrice di stato di riga da SQL_ROW_SUCCESS, non SQL_ROW_SUCCESS_WITH_INFO.  
  
 Se si verificano errori in ogni riga nel set di righe, SQLExtendedFetch restituisce SQL_SUCCESS_WITH_INFO, non SQL_ERROR.  
  
 In ogni gruppo di record di stato che si applica a una singola riga, il primo record di stato restituito da SQLExtendedFetch deve contenere 01S01 SQLSTATE (errore nella riga). **SQLFetchScroll** non restituisce il valore SQLSTATE. Se è in grado di restituire ulteriori SQLSTATE SQLExtendedFetch, ancora deve restituire questo SQLSTATE.  
  
## <a name="sqlfetchscroll-and-optimistic-concurrency"></a>SQLFetchScroll e concorrenza ottimistica  
 Se un cursore utilizza la concorrenza ottimistica, ovvero, l'attributo di istruzione SQL_ATTR_CONCURRENCY ha un valore di SQL_CONCUR_VALUES o SQL_CONCUR_ROWVER, **SQLFetchScroll** Aggiorna i valori di concorrenza ottimistica utilizzati dai dati origine per rilevare se una riga è stata modificata. Questo errore si verifica ogni volta che **SQLFetchScroll** recupera un nuovo set di righe, anche quando recupera nuovamente il set di righe corrente. (Viene chiamato con FetchOrientation impostato su SQL_FETCH_RELATIVE e FetchOffset impostato su 0.)  
  
## <a name="sqlfetchscroll-and-odbc-2x-drivers"></a>Driver di SQLFetchScroll e ODBC 2. x  
 Quando un'applicazione chiama **SQLFetchScroll** nel driver ODBC 2. x, gestione Driver esegue il mapping di questa chiamata a **SQLExtendedFetch**. Passa i valori seguenti per gli argomenti di **SQLExtendedFetch**.  
  
|Argomento SQLExtendedFetch.|Valore|  
|-------------------------------|-----------|  
|StatementHandle|StatementHandle in **SQLFetchScroll**.|  
|FetchOrientation|FetchOrientation in **SQLFetchScroll**.|  
|FetchOffset|Se FetchOrientation non è impostato su SQL_FETCH_BOOKMARK, il valore dell'argomento FetchOffset in **SQLFetchScroll** viene utilizzato.<br /><br /> Se impostato su SQL_FETCH_BOOKMARK FetchOrientation, viene utilizzato il valore archiviato in corrispondenza dell'indirizzo specificato dall'attributo di istruzione SQL_ATTR_FETCH_BOOKMARK_PTR.|  
|RowCountPtr|L'indirizzo specificato dall'attributo SQL_ATTR_ROWS_FETCHED_PTR istruzione.|  
|RowStatusArray|L'indirizzo specificato dall'attributo di istruzione vengono impostati SQL_ATTR_ROW_STATUS_PTR.|  
  
 Per ulteriori informazioni, vedere [cursori a blocchi, i cursori scorrevoli e compatibilità con le versioni precedenti](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) nell'appendice g: Driver le linee guida per la compatibilità con le versioni precedenti.  
  
## <a name="descriptors-and-sqlfetchscroll"></a>Descrittori e SQLFetchScroll  
 **SQLFetchScroll** interagisce con descrittori nello stesso modo come **SQLFetch**. Per ulteriori informazioni, vedere la sezione "Descrittori e SQLFetchScroll" [SQLFetch-funzione](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
## <a name="code-example"></a>Esempio di codice  
 Vedere [associazione per colonna](../../../odbc/reference/develop-app/column-wise-binding.md), [l'associazione per riga](../../../odbc/reference/develop-app/row-wise-binding.md), [posizionato istruzioni Update e Delete](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md), e [l'aggiornamento delle righe nel set di righe con SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md).  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Associazione di un buffer a una colonna in un set di risultati|[Funzione SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Esecuzione delle operazioni bulk insert, update o le operazioni di eliminazione|[Funzione SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|L'elaborazione di istruzione di annullamento|[Funzione SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Restituzione di informazioni su una colonna in un set di risultati|[Funzione SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|Esecuzione di un'istruzione SQL|[Funzione SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|L'esecuzione di un'istruzione SQL preparata|[Funzione SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Recupero di una singola riga o un blocco di dati in una direzione forward-only|[Funzione SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Chiudere il cursore sull'istruzione|[Funzione SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|Restituzione del numero di risultati le colonne del set|[Funzione SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|Posizionando il cursore, l'aggiornamento dei dati del set di righe o l'aggiornamento o eliminazione di dati nel set di risultati|[Funzione SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
|L'impostazione di un attributo di istruzione|[Funzione SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)

