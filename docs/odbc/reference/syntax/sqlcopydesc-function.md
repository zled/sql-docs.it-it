---
title: Funzione SQLCopyDesc | Documenti Microsoft
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
- SQLCopyDesc
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLCopyDesc
helpviewer_keywords:
- SQLCopyDesc function [ODBC]
ms.assetid: d5450895-3824-44c4-8aa4-d4f9752a9602
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e8e7383a16b40a966612784e864594588cc37199
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlcopydesc-function"></a>SQLCopyDesc (funzione)
**Conformità**  
 Introdotta: versione ODBC 3.0 aderenza: 92 ISO  
  
 **Riepilogo**  
 **SQLCopyDesc** copia informazioni sul descrittore da un descrittore handle a un altro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLCopyDesc(  
     SQLHDESC     SourceDescHandle,  
     SQLHDESC     TargetDescHandle);  
```  
  
## <a name="arguments"></a>Argomenti  
 *SourceDescHandle*  
 [Input] Handle di descrittore di origine.  
  
 *TargetDescHandle*  
 [Input] Handle di descrittore di destinazione. Il *TargetDescHandle* argomento può essere un handle a un descrittore di applicazione o un IPD. *TargetDescHandle* non può essere impostata su un handle a un IRD, o **SQLCopyDesc** restituiranno SQLSTATE HY016 (non è possibile modificare un descrittore della riga di implementazione).  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLCopyDesc** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato possono essere ottenuti chiamando **SQLGetDiagRec** con un *HandleType* di SQL _ HANDLE_DESC e *gestire* di *TargetDescHandle*. Se un oggetto non valido *SourceDescHandle* passato nella chiamata, verrà restituito SQL_INVALID_HANDLE ma non verrà restituito alcun errore SQLSTATE. Nella tabella seguente sono elencati i valori SQLSTATE comunemente restituiti da **SQLCopyDesc** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
 Quando viene restituito un errore, la chiamata a **SQLCopyDesc** viene interrotta immediatamente e il contenuto dei campi di *TargetDescHandle* descrittore sono definiti.  
  
 Poiché **SQLCopyDesc** può essere implementata chiamando **SQLGetDescField** e **SQLSetDescField**, **SQLCopyDesc** può restituire SQLSTATE restituiti da **SQLGetDescField** o **SQLSetDescField**.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|08S01|Errore del collegamento di comunicazione|Collegamento di comunicazione tra il driver e l'origine dati a cui era connesso il driver non è stato possibile prima dell'elaborazione della funzione è stata completata.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel * \*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver è stato in grado di allocare la memoria necessaria per supportare l'esecuzione o il completamento della funzione.|  
|HY007|L'istruzione associata non è stato preparato|*SourceDescHandle* è stata associata a un IRD e l'handle di istruzione associata non è nello stato preparato o eseguito.|  
|HY010|Errore nella sequenza (funzione)|(DM) il descrittore di gestire *SourceDescHandle* o *TargetDescHandle* è stato associato un *StatementHandle* per il quale un'esecuzione asincrona (not (funzione) uno) è stato chiamato ed era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) il descrittore di gestire *SourceDescHandle* o *TargetDescHandle* è stato associato un *StatementHandle* per il quale **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos** è stato chiamato e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima che sono stati inviati dati per tutti i parametri data-at-execution o colonne.<br /><br /> (DM) a cui è stata chiamata per l'handle di connessione associata a una funzione in modo asincrono in esecuzione il *SourceDescHandle* o *TargetDescHandle*. Questa funzione asincrona era ancora in esecuzione quando il **SQLCopyDesc** funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** è stato chiamato per uno degli handle di istruzione associati il *SourceDescHandle* o *TargetDescHandle* e SQL_PARAM_DATA_AVAILABLE restituito. Questa funzione è stata chiamata prima che i dati sono stati recuperati per tutti i parametri con flusso.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY016|Non è possibile modificare un descrittore della riga di implementazione|*TargetDescHandle* è stata associata a un IRD.|  
|HY021|Informazioni del descrittore incoerenti.|Le informazioni sul descrittore controllati durante una verifica coerenza non era coerente. Per ulteriori informazioni, vedere "Verifiche coerenza" nella **SQLSetDescField**.|  
|HY092|Identificatore di attributo/opzione non valida|La chiamata a **SQLCopyDesc** richiesto una chiamata a **SQLSetDescField**, ma * \*ValuePtr* non valido per il *FieldIdentifier* argomento *TargetDescHandle*.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|Il driver (DM) associato il *SourceDescHandle* o *TargetDescHandle* non supporta la funzione.|  
  
## <a name="comments"></a>Commenti  
 Una chiamata a **SQLCopyDesc** copie di gestire i campi del descrittore di origine per l'handle di descrittore di destinazione. I campi possono essere copiati solo a un descrittore di applicazione o un IPD, ma non a un IRD. I campi possono essere copiati da un'applicazione o un descrittore di implementazione.  
  
 I campi possono essere copiati da un IRD solo se l'handle di istruzione si trova nello stato preparato o eseguito; in caso contrario, la funzione restituisce SQLSTATE HY007 (istruzione associata non è stato preparato).  
  
 I campi possono essere copiati da un IPD o meno un'istruzione è stata preparata. Se è stata preparata un'istruzione SQL con parametri dinamici e il popolamento automatico il IPD è supportato e abilitato, il IPD viene popolata dal driver. Quando **SQLCopyDesc** viene chiamato con il IPD come il *SourceDescHandle*, vengono copiati i campi popolati. Se il IPD non viene popolata dal driver, il contenuto dei campi di origine di IPD viene copiato.  
  
 Tutti i campi del descrittore, ad eccezione di SQL_DESC_ALLOC_TYPE (che specifica se l'handle di descrittore è stato allocato automaticamente o in modo esplicito), vengono copiati, se il campo viene definito per il descrittore di destinazione. Campi copiati sovrascrivere i campi esistenti.  
  
 Il driver vengono copiati tutti i campi di descrizione, se il *SourceDescHandle* e *TargetDescHandle* argomenti associati con lo stesso driver, anche se i driver sono in due diverse connessioni o ambienti. Se il *SourceDescHandle* e *TargetDescHandle* gli argomenti sono associati a diversi driver, Driver Manager copia campi definite da ODBC, ma non la copia di campi definito dal driver o campi non è definito da ODBC per il tipo di descrittore.  
  
 La chiamata a **SQLCopyDesc** viene interrotta immediatamente se si verifica un errore.  
  
 Quando il campo SQL_DESC_DATA_PTR viene copiato, viene eseguita una verifica coerenza nel descrittore di destinazione. Se la verifica coerenza ha esito negativo, HY021 SQLSTATE (le informazioni del descrittore incoerenti) viene restituite e la chiamata a **SQLCopyDesc** viene interrotta immediatamente. Per altre informazioni sui controlli di coerenza, vedere "Verifiche coerenza" nella [funzione SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).  
  
 Gli handle di descrittore possono essere copiati tra connessioni anche se le connessioni sono in ambienti diversi. Se Gestione Driver rileva che l'origine e il descrittore di destinazione gli handle non appartengono alla stessa connessione e le due connessioni appartenere per separare i driver, implementa **SQLCopyDesc** mediante l'esecuzione di un campo per campo copiare mediante **SQLGetDescField** e **SQLSetDescField**.  
  
 Quando **SQLCopyDesc** viene chiamato con un *SourceDescHandle* in un driver e un *TargetDescHandle* in un altro driver, la coda di errore dei * SourceDescHandle* è deselezionata. Questo errore si verifica perché **SQLCopyDesc** in questo caso viene implementato dalle chiamate a **SQLGetDescField** e **SQLSetDescField**.  
  
> [!NOTE]  
>  Un'applicazione potrebbe essere in grado di associare un handle di descrittore allocato in modo esplicito con un *StatementHandle*, anziché chiamare **SQLCopyDesc** per copiare i campi da un descrittore. Un descrittore allocato in modo esplicito può essere associato a un altro *StatementHandle* sullo stesso *ConnectionHandle* impostando l'istruzione SQL_ATTR_APP_ROW_DESC o SQL_ATTR_APP_PARAM_DESC attributo per l'handle di descrittore allocato in modo esplicito. Quando questa operazione viene eseguita, **SQLCopyDesc** non deve essere chiamato per copiare i valori dei campi descrittore da un descrittore. Un handle di descrittore non può essere associato a un *StatementHandle* in un altro *ConnectionHandle*, tuttavia, per utilizzare gli stessi valori di campo descrittore su *StatementHandles*su diversi *ConnectionHandles*, **SQLCopyDesc** deve essere chiamato.  
  
 Per una descrizione dei campi in un'intestazione di descrittore o di un record, vedere [funzione SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Per ulteriori informazioni su descrittori, vedere [descrittori](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="copying-rows-between-tables"></a>Copia delle righe tra le tabelle  
 Un'applicazione può copiare dati da una tabella a un altro senza copiare i dati a livello di applicazione. A tale scopo, l'applicazione associa stesso buffer di dati e informazioni sul descrittore da un'istruzione che recupera i dati e l'istruzione che inserisce i dati in una copia. Può essere eseguita tramite la condivisione di un descrittore di applicazione (associazione a un descrittore allocato in modo esplicito come il ARD per un'istruzione e APD in un altro) o tramite **SQLCopyDesc** per copiare le associazioni tra il ARD e APD delle due istruzioni. Se le istruzioni sono in diverse connessioni, **SQLCopyDesc** deve essere utilizzato. Inoltre, **SQLCopyDesc** deve essere chiamato per copiare le associazioni tra il IRD e IPD delle due istruzioni. Durante la copia tra le istruzioni sulla stessa connessione, il tipo di informazioni SQL_ACTIVE_STATEMENTS restituito dal driver per una chiamata a **SQLGetInfo** deve essere maggiore di 1 per eseguire questa operazione. (Questo non è il caso durante la copia tra connessioni.)  
  
### <a name="code-example"></a>Esempio di codice  
 Nell'esempio seguente, operazioni di descrittore vengono utilizzate per copiare i campi della tabella PartsSource nella tabella di PartsCopy. Nei buffer di set di righe in cui viene recuperato il contenuto della tabella PartsSource *hstmt0*. Questi valori vengono utilizzati come parametri di un'istruzione INSERT su *hstmt1* per popolare le colonne della tabella PartsCopy. A tale scopo, i campi di implementazione di *hstmt0* vengono copiati i campi del IPD di *hstmt1*e i campi del ARD di *hstmt0* vengono copiati i campi di APD di *hstmt1*. Utilizzare **SQLSetDescField** per impostare l'attributo SQL_DESC_PARAMETER_TYPE del IPD per SQL_PARAM_INPUT quando si copiano campi IRD da un'istruzione con parametri di output per i campi IPD che devono essere parametri di input.  
  
```  
#define ROWS 100  
#define DESC_LEN 50  
#define SQL_SUCCEEDED(rc) (rc == SQL_SUCCESS || rc == SQL_SUCCESS_WITH_INFO)  
  
// Template for a row  
typedef struct {  
   SQLINTEGER   sPartID;  
   SQLINTEGER   cbPartID;  
   SQLUCHAR     szDescription[DESC_LENGTH];  
   SQLINTEGER   cbDescription;  
   REAL         sPrice;  
   SQLINTEGER   cbPrice;  
} PartsSource;  
  
PartsSource    rget[ROWS];          // rowset buffer  
SQLUSMALLINT   sts_ptr[ROWS];       // status pointer  
SQLHSTMT       hstmt0, hstmt1;  
SQLHDESC       hArd0, hIrd0, hApd1, hIpd1;  
  
// ARD and IRD of hstmt0  
SQLGetStmtAttr(hstmt0, SQL_ATTR_APP_ROW_DESC, &hArd0, 0, NULL);  
SQLGetStmtAttr(hstmt0, SQL_ATTR_IMP_ROW_DESC, &hIrd0, 0, NULL);  
  
// APD and IPD of hstmt1  
SQLGetStmtAttr(hstmt1, SQL_ATTR_APP_PARAM_DESC, &hApd1, 0, NULL);  
SQLGetStmtAttr(hstmt1, SQL_ATTR_IMP_PARAM_DESC, &hIpd1, 0, NULL);  
  
// Use row-wise binding on hstmt0 to fetch rows  
SQLSetStmtAttr(hstmt0, SQL_ATTR_ROW_BIND_TYPE, (SQLPOINTER) sizeof(PartsSource), 0);  
  
// Set rowset size for hstmt0  
SQLSetStmtAttr(hstmt0, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER) ROWS, 0);  
  
// Execute a select statement  
SQLExecDirect(hstmt0, "SELECT PARTID, DESCRIPTION, PRICE FROM PARTS ORDER BY 3, 1, 2"",  
               SQL_NTS);  
  
// Bind  
SQLBindCol(hstmt0, 1, SQL_C_SLONG, rget[0].sPartID, 0,   
   &rget[0].cbPartID);  
SQLBindCol(hstmt0, 2, SQL_C_CHAR, &rget[0].szDescription, DESC_LEN,   
   &rget[0].cbDescription);  
SQLBindCol(hstmt0, 3, SQL_C_FLOAT, rget[0].sPrice,   
   0, &rget[0].cbPrice);  
  
// Perform parameter bindings on hstmt1.   
SQLCopyDesc(hArd0, hApd1);  
SQLCopyDesc(hIrd0, hIpd1);  
  
// Set the array status pointer of IRD  
SQLSetStmtAttr(hstmt0, SQL_ATTR_ROW_STATUS_PTR, sts_ptr, SQL_IS_POINTER);  
  
// Set the ARRAY_STATUS_PTR field of APD to be the same  
// as that in IRD.  
SQLSetStmtAttr(hstmt1, SQL_ATTR_PARAM_OPERATION_PTR, sts_ptr, SQL_IS_POINTER);  
  
// Set the hIpd1 records as input parameters  
rc = SQLSetDescField(hIpd1, 1, SQL_DESC_PARAMETER_TYPE, (SQLPOINTER)SQL_PARAM_INPUT, SQL_IS_INTEGER);  
rc = SQLSetDescField(hIpd1, 2, SQL_DESC_PARAMETER_TYPE, (SQLPOINTER)SQL_PARAM_INPUT, SQL_IS_INTEGER);  
rc = SQLSetDescField(hIpd1, 3, SQL_DESC_PARAMETER_TYPE, (SQLPOINTER)SQL_PARAM_INPUT, SQL_IS_INTEGER);  
  
// Prepare an insert statement on hstmt1. PartsCopy is a copy of  
// PartsSource  
SQLPrepare(hstmt1, "INSERT INTO PARTS_COPY VALUES (?, ?, ?)", SQL_NTS);  
  
// In a loop, fetch a rowset, and copy the fetched rowset to PARTS_COPY  
  
rc = SQLFetchScroll(hstmt0, SQL_FETCH_NEXT, 0);  
while (SQL_SUCCEEDED(rc)) {  
  
   // After the call to SQLFetchScroll, the status array has row   
   // statuses. This array is used as input status in the APD  
   // and hence determines which elements of the rowset buffer  
   // are inserted.  
   SQLExecute(hstmt1);  
  
   rc = SQLFetchScroll(hstmt0, SQL_FETCH_NEXT, 0);  
} // while  
```  
  
### <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Recupero di più campi di descrizione|[Funzione SQLGetDescRec](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Impostazione di un campo singolo descrittore|[Funzione SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|L'impostazione di più campi di descrizione|[Funzione SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)

