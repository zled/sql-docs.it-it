---
title: "Mapping di funzioni di sostituzione per la compatibilità delle applicazioni - ODBC | Documenti Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mapping replacement functions [ODBC]
- upgrading applications [ODBC], mapping replacement functions
- compatibility [ODBC], mapping replacement functions
- ODBC drivers [ODBC], backward compatibility
- functions [ODBC], mapping replacement functions
- application upgrades [ODBC], mapping replacement functions
- backward compatibility [ODBC], mapping replacement functions
ms.assetid: f5e6d9da-76ef-42cb-b3f5-f640857df732
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 461f41eb5f8ae7481b65d293b0c3a619b59e7f9c
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="mapping-replacement-functions-for-backward-compatibility-of-applications"></a>Mapping di funzioni di sostituzione per la compatibilità delle applicazioni
Un'applicazione ODBC 3*x* applicazione utilizzo tramite ODBC 3*x* gestione Driver funzionerà con un ODBC 2.* x* driver, purché non nuove funzionalità vengono utilizzati. Entrambi duplicati funzionalità e modifiche del comportamento, tuttavia, influiscono sulla modalità che ODBC 3. *x* applicazione funziona su un ODBC 2.* x* driver. Quando si lavora con un ODBC 2. *x* driver, Driver Manager viene eseguito il mapping seguente ODBC 3.* x* funzioni, che sono sostituiti uno o più ODBC 2.* x* funzioni, nel corrispondente ODBC 2.* x* funzioni.  
  
|ODBC 3. *x* (funzione)|ODBC 2. *x* (funzione)|  
|-------------------------|-------------------------|  
|**SQLAllocHandle**|**SQLAllocEnv**, **SQLAllocConnect**, o **SQLAllocStmt**|  
|**SQLBulkOperations**|**SQLSetPos**|  
|**SQLColAttribute**|**SQLColAttributes**|  
|**SQLEndTran**|**SQLTransact**|  
|**SQLFetch**|**SQLExtendedFetch.**|  
|**SQLFetchScroll**|**SQLExtendedFetch.**|  
|**SQLFreeHandle**|**SQLFreeEnv**, **SQLFreeConnect**, o **SQLFreeStmt**|  
|**SQLGetConnectAttr**|**SQLGetConnectOption**|  
|**SQLGetDiagRec**|**SQLError**|  
|**SQLGetStmtAttr**|**SQLGetStmtOption**[1]|  
|**Funzione SQLSetConnectAttr**|**SQLSetConnectOption**|  
|**Funzione SQLSetStmtAttr**|**SQLSetStmtOption**[1]|  
  
 [1] altre azioni potrebbero anche prendere, a seconda dell'attributo richiesto.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
 Gestione Driver esegue il mapping a **SQLAllocEnv**, **SQLAllocConnect**, o **SQLAllocStmt**, a seconda dei casi. La seguente chiamata al **SQLAllocHandle**:  
  
```  
SQLAllocHandle(HandleType, InputHandle, OutputHandlePtr);  
```  
  
 verrà generato in Gestione Driver eseguire le operazioni seguenti (concettuale, controllo degli errori) mapping:  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV: return (SQLAllocEnv(OutputHandlePtr));  
   case SQL_HANDLE_DBC: return (SQLAllocConnect (InputHandle, OutputHandlePtr));  
   case SQL_HANDLE_STMT: return (SQLAllocStmt (InputHandle, OutputHandlePtr));  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlbulkoperations"></a>SQLBulkOperations  
 Gestione Driver esegue il mapping a **SQLSetPos**. La seguente chiamata al **SQLBulkOperations**:  
  
```  
SQLBulkOperations(hstmt, Operation);  
```  
  
 restituirà la sequenza di passaggi seguente:  
  
1.  Se l'argomento dell'operazione è SQL_ADD, gestione Driver chiama **SQLSetPos** come indicato di seguito:  
  
    ```  
    SQLSetPos (hstmt, 0, SQL_ADD, SQL_LOCK_NO_CHANGE);  
    ```  
  
2.  Se l'argomento di operazione non è SQL_ADD, il driver restituisce SQLSTATE HY092 (identificatore di attributo/opzione non valida).  
  
3.  Se l'applicazione tenta di modificare il SQL_ATTR_ROW_STATUS_PTR tra le chiamate a **SQLFetch** o **SQLFetchScroll** e **SQLBulkOperations**, gestione Driver verrà restituire SQLSTATE HY011 (Impossibile impostare l'attributo ora).  
  
4.  Se l'argomento dell'operazione è SQL_ADD, l'applicazione deve chiamare **SQLBindCol** per associare i dati da inserire. Non può chiamare **SQLSetDescField** o **SQLSetDescRec** per associare i dati da inserire.  
  
5.  Se l'argomento dell'operazione è SQL_ADD e il numero di righe da inserire non è la stessa dimensione il set di righe corrente, **SQLSetStmtAttr** deve essere chiamato per impostare l'attributo di istruzione SQL_ATTR_ROW_ARRAY_SIZE sul numero di righe da inserito prima di chiamare **SQLBulkOperations**. Per ripristinare le dimensioni del set di righe precedenti, l'applicazione deve impostare l'attributo di istruzione SQL_ATTR_ROW_ARRAY_SIZE prima **SQLFetch**, **SQLFetchScroll**, o **SQLSetPos**viene chiamato.  
  
## <a name="sqlcolattribute"></a>SQLColAttribute  
 Gestione Driver esegue il mapping a **SQLColAttributes**. La seguente chiamata al **SQLColAttribute**:  
  
```  
SQLColAttribute(StatementHandle, ColumnNumber, FieldIdentifier, CharacterAttributePtr, BufferLength, StringLengthPtr, NumericAttributePtr);  
```  
  
 restituirà la sequenza di passaggi seguente:  
  
1.  Se *FieldIdentifier* è uno dei seguenti:  
  
     SQL_DESC_PRECISION, SQL_DESC_SCALE, SQL_DESC_LENGTH, SQL_DESC_OCTET_LENGTH, SQL_DESC_UNNAMED, SQL_DESC_BASE_COLUMN_NAME, SQL_DESC_LITERAL_PREFIX, SQL_DESC_LITERAL_SUFFIX o SQL_DESC_LOCAL_TYPE_NAME  
  
     Gestione Driver restituisce SQL_ERROR con SQLSTATE HY091 (identificatore di campo del descrittore non valido). Nessun ulteriore regole di questa sezione si applicano.  
  
2.  Gestione Driver viene eseguito il mapping SQL_COLUMN_COUNT, SQL_COLUMN_NAME o SQL_COLUMN_NULLABLE SQL_DESC_COUNT, SQL_DESC_NAME o SQL_DESC_NULLABLE, rispettivamente. (Un ODBC 2*x* driver deve supportare solo SQL_COLUMN_COUNT, SQL_COLUMN_NAME e SQL_COLUMN_NULLABLE, non SQL_DESC_COUNT, SQL_DESC_NAME e SQL_DESC_NULLABLE.) La chiamata a SQLColAttribute è mappata a:  
  
    ```  
    SQLColAttributes(StatementHandle, ColumnNumber, FieldIdentifier, CharacterAttributePtr, BufferLength, StringLengthPtr, NumericAttributePtr);  
    ```  
  
3.  Tutti gli altri *FieldIdentifier* valori vengono passati al driver, con **SQLColAttribute** eseguito il mapping a **SQLColAttributes** come illustrato in precedenza.  
  
4.  Se *BufferLength* è minore di 0, gestione Driver restituisce SQL_ERROR con SQLSTATE HY090 (stringa di lunghezza o non valida del buffer). Nessun ulteriore regole di questa sezione si applicano.  
  
5.  Se *FieldIdentifier* è SQL_DESC_CONCISE_TYPE e il tipo restituito è un tipo di dati datetime conciso, le mappe di gestione Driver la restituzione di valori per i codici di date, time e timestamp.  
  
6.  The Driver Manager esegue controlli necessari per vedere se SQLSTATE HY010 (errore di sequenza di funzioni) deve essere generato. Se in tal caso, la gestione di Driver restituisce SQL_ERROR e SQLSTATE HY010 (funzione di errore nella sequenza). Nessun ulteriore regole di questa sezione si applicano.  
  
## <a name="sqlendtran"></a>SQLEndTran  
 Gestione Driver esegue il mapping a **SQLTransact**. La seguente chiamata al **SQLEndTran**:  
  
```  
SQLEndTran(HandleType, Handle, CompletionType);  
```  
  
 verrà generato in Gestione Driver eseguire le operazioni seguenti (concettuale, controllo degli errori) mapping:  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV:return(SQLTransact(Handle, SQL_NULL_HDBC, CompletionType));  
   case SQL_HANDLE_DBC:return(SQLTransact(SQL_NULL_HENV, Handle, CompletionType);  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlfetch"></a>SQLFetch  
 Gestione Driver esegue il mapping a **SQLExtendedFetch** con un *FetchOrientation* argomento di SQL_FETCH_NEXT. La seguente chiamata al **SQLFetch**:  
  
```  
SQLFetch (StatementHandle);  
```  
  
 comporterà la chiamata di gestione Driver **SQLExtendedFetch**, come segue:  
  
```  
rc = SQLExtendedFetch(StatementHandle, FetchOrientation, FetchOffset, &RowCount, RowStatusArray);  
```  
  
 In questa chiamata, il *pcRow* argomento è impostato sul valore che l'applicazione imposta l'attributo di istruzione SQL_ATTR_ROWS_FETCHED_PTR affinché tramite una chiamata a **SQLSetStmtAttr**.  
  
> [!NOTE]  
>  Quando l'applicazione chiama **SQLSetStmtAttr** per impostare SQL_ATTR_ROW_STATUS_PTR affinché punti a una matrice di stato, gestione Driver memorizza nella cache il puntatore del mouse. *RowStatusArray* può essere uguale a un puntatore null.  
  
 Se il driver non supporta **SQLExtendedFetch** e viene caricata la libreria di cursori, gestione Driver utilizza la libreria di cursori **SQLExtendedFetch** per eseguire il mapping **SQLFetch** per **SQLExtendedFetch**. Se il driver non supporta **SQLExtendedFetch** e la libreria di cursori non è stata caricata, gestione Driver passa la chiamata a **SQLFetch** tramite il driver. Se l'applicazione chiama **SQLSetStmtAttr** per impostare SQL_ATTR_ROW_STATUS_PTR, gestione Driver garantisce che la matrice viene compilata. Se l'applicazione chiama **SQLSetStmtAttr** per impostare SQL_ATTR_ROWS_FETCHED_PTR, gestione Driver questo campo impostato su 1.  
  
## <a name="sqlfetchscroll"></a>SQLFetchScroll  
 Gestione Driver esegue il mapping a **SQLExtendedFetch**. La seguente chiamata al **SQLFetchScroll**:  
  
```  
SQLFetchScroll(StatementHandle, FetchOrientation, FetchOffset);  
```  
  
 restituirà la sequenza di passaggi seguente:  
  
1.  Quando l'applicazione chiama **SQLSetStmtAttr** per impostare SQL_ATTR_ROW_STATUS_PTR (che imposta il campo SQL_DESC_ARRAY_STATUS_PTR nell'implementazione) in modo che punti a una matrice di stato, gestione Driver memorizza nella cache l'indicatore di misura. Si supponga che l'indicatore di misura sia *RowStatusArray*; in caso contrario, consentono *RowStatusArray* essere uguale a un puntatore null. Se il *RowStatusArray* argomento è impostato su un puntatore null, il Driver Manager genera una matrice di stato delle righe.  
  
2.  Se *FetchOrientation* non fa parte di SQL_FETCH_NEXT, SQL_FETCH_PRIOR, SQL_FETCH_ABSOLUTE, SQL_FETCH_RELATIVE, SQL_FETCH_FIRST, SQL_FETCH_LAST o SQL_FETCH_BOOKMARK, gestione Driver restituisce SQL_ERROR con SQLSTATE HY106 (tipo compreso nell'intervallo di recupero). Nessun ulteriore regole di questa sezione si applicano.  
  
3.  Caso:  
  
-   Se *FetchOrientation* è uguale a SQL_FETCH_BOOKMARK, quindi:  
  
    -   Se **SQLSetStmtAttr** è stato chiamato precedentemente per impostare il valore di SQL_ATTR_FETCH_BOOKMARK_PTR, quindi sarà *Bmk* il valore ottenuto dereferenziazione del puntatore SQL_DESC_FETCH_BOOKMARK_PTR.  
  
    -   In caso contrario, restituirà SQL_ERROR con SQLSTATE HY111 (valore di segnalibro non valido). Nessun ulteriore regole di questa sezione si applicano.  
  
     Gestione Driver chiama **SQLExtendedFetch**, come segue:  
  
    ```  
    rc = SQLExtendedFetch(StatementHandle, FetchOrientation, Bmk, pcRow, RowStatusArray);  
    ```  
  
-   In caso contrario, gestione Driver chiama **SQLExtendedFetch**, come segue:  
  
    ```  
    rc = SQLExtendedFetch(StatementHandle, FetchOrientation, FetchOffset, pcRow, RowStatusArray);  
    ```  
  
     Queste chiamate, il *pcRow* argomento è impostato sul valore che l'applicazione imposta l'attributo di istruzione SQL_ATTR_ROWS_FETCHED_PTR affinché tramite una chiamata a **SQLSetStmtAttr**.  
  
-   SQL_ATTR_ROW_ARRAY_SIZE è mappata a SQL_ROWSET_SIZE.  
  
-   Se *rc* è uguale a SQL_SUCCESS o SQL_SUCCESS_WITH_INFO e se *FetchOrientation* è uguale a SQL_FETCH_BOOKMARK e *FetchOffset* è diverso da 0, quindi il Driver Manager registra un avviso, 01S10 SQLSTATE (tenta di recuperare da un offset di segnalibro, offset valore ignorate) e restituisce SQL_SUCCESS_WITH_INFO.  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
 Gestione Driver esegue il mapping a **SQLFreeEnv**, **SQLFreeConnect**, o **SQLFreeStmt** come appropriato. La seguente chiamata al **SQLFreeHandle**:  
  
```  
SQLFreeHandle(HandleType, Handle);  
```  
  
 verrà generato in Gestione Driver eseguire le operazioni seguenti (concettuale, controllo degli errori) mapping:  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV: return (SQLFreeEnv(Handle));  
   case SQL_HANDLE_DBC: return (SQLFreeConnect(Handle));  
   case SQL_HANDLE_STMT: return (SQLFreeStmt(Handle, SQL_DROP));  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlgetconnectattr"></a>SQLGetConnectAttr  
 Gestione Driver esegue il mapping a **SQLGetConnectOption**. La seguente chiamata al **SQLGetConnectAttr**:  
  
```  
SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, StringLengthPtr);  
```  
  
 restituirà la sequenza di passaggi seguente:  
  
1.  Se *attributo* non è un attributo di connessione o istruzione definito dal driver e non è un attributo definito in ODBC 2.* x*, gestione Driver restituisce SQL_ERROR con SQLSTATE HY092 (identificatore di attributo/opzione non valida). Nessun ulteriore regole in questa sezione si applicano.  
  
2.  Se *attributo* è uguale a SQL_ATTR_AUTO_IPD o SQL_ATTR_METADATA_ID, gestione Driver restituisce SQL_ERROR con SQLSTATE HY092 (identificatore di attributo/opzione non valida).  
  
3.  Il Driver Manager esegue controlli necessari per verificare se SQLSTATE 08003 (connessione non aperta) o SQLSTATE HY010 (errore di sequenza di funzioni) deve essere generato. In questo caso, gestione Driver restituisce SQL_ERROR e viene inviato il messaggio di errore appropriato. Nessun ulteriore regole di questa sezione si applicano.  
  
4.  Le chiamate di gestione Driver **SQLGetConnectOption** come indicato di seguito:  
  
    ```  
    SQLGetConnectOption (ConnectionHandle, Attribute, ValuePtr);  
    ```  
  
     Si noti che il *BufferLength* e *StringLengthPtr* vengono ignorati.  
  
## <a name="sqlgetdata"></a>SQLGetData  
 Quando un'applicazione ODBC 3. *x* applicazione che utilizza un ODBC 2*x* driver chiama **SQLGetData** con il *ColumnNumber* argomento uguale a 0, 3 ODBC*x* driver Manager esegue il mapping a una chiamata a **SQLGetStmtOption** con il *opzione* attributo impostato su SQL_GET_BOOKMARK.  
  
## <a name="sqlgetstmtattr"></a>SQLGetStmtAttr  
 Gestione Driver esegue il mapping a **SQLGetStmtOption**. La seguente chiamata al **SQLGetStmtAttr**:  
  
```  
SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, StringLengthPtr);  
```  
  
 restituirà la sequenza di passaggi seguente:  
  
1.  Se *attributo* non è un attributo di connessione o istruzione definito dal driver e non è un attributo definito in ODBC 2.* x*, gestione Driver restituisce SQL_ERROR con SQLSTATE HY092 (identificatore di attributo/opzione non valida). Nessun ulteriore regole in questa sezione si applicano.  
  
2.  Se *attributo* è uno dei seguenti:  
  
     SQL_ATTR_APP_ROW_DESC  
  
     SQL_ATTR_APP_PARAM_DESC  
  
     SQL_ATTR_AUTO_IPD  
  
     SQL_ATTR_ROW_BIND_TYPE  
  
     SQL_ATTR_IMP_ROW_DESC  
  
     SQL_ATTR_IMP_PARAM_DESC  
  
     SQL_ATTR_METADATA_ID  
  
     SQL_ATTR_PARAM_BIND_TYPE  
  
     SQL_ATTR_PREDICATE_PTR  
  
     SQL_ATTR_PREDICATE_OCTET_LENGTH_PTR  
  
     SQL_ATTR_PARAM_BIND_OFFSET_PTR  
  
     SQL_ATTR_ROW_BIND_OFFSET_PTR  
  
     SQL_ATTR_ROW_OPERATION_PTR  
  
     SQL_ATTR_PARAM_OPERATION_PTR  
  
     Gestione Driver restituisce SQL_ERROR con SQLSTATE HY092 (identificatore di attributo/opzione non valida). Nessun ulteriore regole di questa sezione si applicano.  
  
3.  The Driver Manager esegue controlli necessari per vedere se SQLSTATE HY010 (errore di sequenza di funzioni) deve essere generato. Se in tal caso, la gestione di Driver restituisce SQL_ERROR e SQLSTATE HY010 (funzione di errore nella sequenza). Nessun ulteriore regole di questa sezione si applicano.  
  
4.  Se *attributo* è uguale a SQL_ATTR_ROWS_FETCHED_PTR, gestione Driver restituisce un puntatore alla variabile di gestione Driver interno *linea d'aria*, che è usato o verrà utilizzato in una chiamata a ** SQLExtendedFetch**. Nessun ulteriore regole di questa sezione si applicano.  
  
5.  Se *attributo* è uguale a SQL_DESC_FETCH_BOOKMARK_PTR, Driver Manager restituisce il puntatore appropriato che è stato memorizzato nella cache durante una chiamata a **SQLSetStmtAttr**.  
  
6.  Se *attributo* è uguale a SQL_ATTR_ROW_STATUS_PTR, Driver Manager restituisce il puntatore appropriato che è stato memorizzato nella cache durante una chiamata a **SQLSetStmtAttr**.  
  
7.  Le chiamate di gestione Driver **SQLGetStmtOption** come indicato di seguito:  
  
    ```  
    SQLGetStmtOption (hstmt, fOption, pvParam);  
    ```  
  
     dove *hstmt*, *fOption*, e *il parametro pvParam* verrà impostato su valori di *StatementHandle*, *attributo*, e *ValuePtr*, rispettivamente. Il *BufferLength* e *StringLengthPtr* vengono ignorati.  
  
## <a name="sqlsetconnectattr"></a>SQLSetConnectAttr  
 Gestione Driver esegue il mapping a **SQLSetConnectOption**. La seguente chiamata al **SQLSetConnectAttr**:  
  
```  
SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, StringLength);  
```  
  
 restituirà la sequenza di passaggi seguente:  
  
1.  Se *attributo* non è un attributo di connessione o istruzione definito dal driver e non è un attributo definito in ODBC 2.* x*, gestione Driver restituisce SQL_ERROR con SQLSTATE HY092 (identificatore di attributo/opzione non valida). Nessun ulteriore regole in questa sezione si applicano.  
  
2.  Se *attributo* è uguale a SQL_ATTR_AUTO_IPD, gestione Driver restituisce SQL_ERROR con SQLSTATE HY092 (identificatore di attributo/opzione non valida).  
  
3.  The Driver Manager esegue controlli necessari per vedere se SQLSTATE 08003 (connessione non aperta) o SQLSTATE HY010 (errore di sequenza di funzioni) è necessario essere generato. Se uno di questi errori deve essere generato, gestione Driver restituisce SQL_ERROR e invia il messaggio di errore appropriato. Nessun ulteriore regole di questa sezione si applicano.  
  
4.  Le chiamate di gestione Driver **SQLSetConnectOption** come indicato di seguito:  
  
    ```  
    SQLSetConnectOption (hdbc, fOption, vParam);  
    ```  
  
     dove *hdbc*, *fOption*, e *vParam* verrà impostato su valori di *ConnectionHandle*, *attributo*, e *ValuePtr*, rispettivamente. *StringLengthPtr* viene ignorato.  
  
> [!NOTE]  
>  La possibilità di impostare gli attributi di istruzione per il livello di connessione è stata deprecata. Gli attributi di istruzione non devono essere mai impostati a livello di connessione da un'applicazione ODBC 3. *x* dell'applicazione.  
  
## <a name="sqlsetstmtattr"></a>SQLSetStmtAttr  
 Gestione Driver esegue il mapping a **SQLSetStmtOption**. La seguente chiamata al **SQLSetStmtAttr**:  
  
```  
SQLSetStmtAttr(StatementHandle, Attribute, ValuePtr, StringLength);  
```  
  
 restituirà la sequenza di passaggi seguente:  
  
1.  Se *attributo* non è un attributo di connessione o istruzione definito dal driver e non è un attributo definito in ODBC 2.* x*, gestione Driver restituisce SQL_ERROR con SQLSTATE HY092 (identificatore di attributo/opzione non valida). Nessun ulteriore regole in questa sezione si applicano.  
  
2.  Se *attributo* è uno dei seguenti:  
  
     SQL_ATTR_APP_ROW_DESC  
  
     SQL_ATTR_APP_PARAM_DESC  
  
     SQL_ATTR_AUTO_IPD  
  
     SQL_ATTR_ROW_BIND_TYPE  
  
     SQL_ATTR_IMP_ROW_DESC  
  
     SQL_ATTR_IMP_PARAM_DESC  
  
     SQL_ATTR_METADATA_ID  
  
     SQL_ATTR_PARAM_BIND_TYPE  
  
     SQL_ATTR_PREDICATE_PTR  
  
     SQL_ATTR_PREDICATE_OCTET_LENGTH_PTR  
  
     SQL_ATTR_PARAM_BIND_OFFSET_PTR  
  
     SQL_ATTR_ROW_BIND_OFFSET_PTR  
  
     SQL_ATTR_ROW_OPERATION_PTR  
  
     SQL_ATTR_PARAM_OPERATION_PTR  
  
     Gestione Driver restituisce SQL_ERROR con SQLSTATE HY092 (identificatore di attributo/opzione non valida). Nessun ulteriore regole di questa sezione si applicano.  
  
3.  Gestione Driver esegue i controlli necessari per vedere se SQLSTATE HY010 (errore di sequenza di funzioni) necessario per essere generato. Se in tal caso, la gestione di Driver restituisce SQL_ERROR e SQLSTATE HY010 (funzione di errore nella sequenza). Nessun ulteriore regole di questa sezione si applicano.  
  
4.  Se *attributo* è uguale a SQL_ATTR_PARAMSET_SIZE o SQL_ATTR_PARAMS_PROCESSED_PTR, vedere la sezione "Mapping per la gestione delle matrici di parametri," più avanti in questo argomento. Nessun ulteriore regole di questa sezione si applicano.  
  
5.  Se *attributo* è uguale a SQL_ATTR_ROWS_FETCHED_PTR, le cache di gestione Driver l'indicatore di misura valore per un utilizzo successivo con **SQLFetchScroll**.  
  
6.  Se *attributo* è uguale a SQL_ATTR_ROW_STATUS_PTR, le cache di gestione Driver l'indicatore di misura valore per un utilizzo successivo con **SQLFetchScroll** o **SQLSetPos**. Nessun ulteriore regole di questa sezione si applicano.  
  
7.  Se *attributo* è uguale a SQL_ATTR_FETCH_BOOKMARK_PTR, le cache di gestione Driver *ValuePtr* e utilizzerà il valore memorizzato nella cache più avanti in una chiamata a **SQLFetchScroll**. Nessun ulteriore regole di questa sezione si applicano.  
  
8.  Le chiamate di gestione Driver **SQLSetStmtOption** come indicato di seguito:  
  
    ```  
    SQLSetStmtOption (hstmt, fOption, vParam);  
    ```  
  
     dove *hstmt*, *fOption*, e *vParam* verrà impostato su valori di *StatementHandle*, *attributo*, e *ValuePtr*, rispettivamente. Il *StringLength* argomento viene ignorato.  
  
     Se un ODBC 2. *x* driver supporta opzioni dell'istruzione di stringa di caratteri, specifici del driver, un'applicazione ODBC 3.* x* applicazione deve chiamare **SQLSetStmtOption** per impostare le opzioni.  
  
## <a name="mappings-for-handling-parameter-arrays"></a>Mapping per la gestione di matrici di parametri  
 Quando l'applicazione chiama:  
  
```  
SQLSetStmtAttr (StatementHandle, SQL_ATTR_PARAMSET_SIZE, Size, StringLength);  
```  
  
 le chiamate di gestione Driver:  
  
```  
SQLParamOptions (StatementHandle, Size, &RowCount);  
```  
  
 Gestione Driver, in un secondo momento, restituisce un puntatore a questa variabile quando l'applicazione chiama **SQLGetStmtAttr** recuperare SQL_ATTR_PARAMS_PROCESSED_PTR. Gestione Driver non è possibile modificare questa variabile interna finché non viene restituito l'handle di istruzione nello stato prepared o allocato.  
  
 Un database ODBC 3. *x* applicazione può chiamare **SQLGetStmtAttr** per ottenere il valore di SQL_ATTR_PARAMS_PROCESSED_PTR anche se non è esplicitamente impostata nel campo SQL_DESC_ARRAY_SIZE in APD. Questa situazione può verificarsi, ad esempio, se l'applicazione dispone di una routine generica che verifica la presenza di "riga" di parametri corrente in fase di elaborazione quando **SQLExecute** restituisce SQL_NEED_DATA. Questa routine viene richiamata o meno il SQL_DESC_ARRAY_SIZE è 1 o maggiore di 1. Per evitare ciò, sarà necessario definire questa variabile interna o meno l'applicazione ha chiamato gestione Driver **SQLSetStmtAttr** per impostare il campo SQL_DESC_ARRAY_SIZE in APD. Se SQL_DESC_ARRAY_SIZE non è stato impostato, gestione Driver ha la certezza che questa variabile contiene il valore 1 prima della restituzione da **SQLExecDirect** o **SQLExecute**.  
  
## <a name="error-handling"></a>Gestione degli errori  
 In ODBC 3. *x*, la chiamata **SQLFetch** o **SQLFetchScroll** popola la SQL_DESC_ARRAY_STATUS_PTR nell'implementazione e il campo SQL_DIAG_ROW_NUMBER di un determinato record di diagnostica contiene il numero della riga nel set di righe che si riferisce il record a. In tal caso, l'applicazione possibile correlare un messaggio di errore con una posizione di riga specificato.  
  
 Un database ODBC 2. *x* driver sarà in grado di fornire questa funzionalità. Tuttavia, fornirà demarcazione di errore con SQLSTATE 01S01 (errore nella riga). Un database ODBC 3. *x* applicazione che utilizza **SQLFetch** o **SQLFetchScroll** mentre si contro un ODBC 2.* x* driver deve essere a conoscenza del fatto. Si noti inoltre che tale applicazione in grado di chiamare **SQLGetDiagField** effettivamente ottenere comunque il campo SQL_DIAG_ROW_NUMBER. Un database ODBC 3. *x* applicazione che utilizza un ODBC 2.* x* driver sarà in grado di chiamare **SQLGetDiagField** solo con un *DiagIdentifier* argomento SQL_DIAG_MESSAGE_TEXT, SQL_DIAG_NATIVE, SQL_DIAG_RETURNCODE o SQL_DIAG_ SQLSTATE. ODBC 3*x* gestione Driver mantiene la struttura di dati di diagnostica quando si lavora con un ODBC 2.* x* driver, ma l'API ODBC 2.* x* driver restituisce solo questi quattro campi.  
  
 Quando un'applicazione ODBC 2. *x* applicazione sta utilizzando un'API ODBC 2.* x* driver, se un'operazione può causare errori più deve essere restituito da Gestione Driver diversi errori possono essere restituiti da ODBC 3*x* Driver Manager piuttosto da ODBC 2.* x* gestione Driver.  
  
## <a name="mappings-for-bookmark-operations"></a>Mapping per le operazioni di segnalibro  
 ODBC 3*x* Driver Manager esegue i mapping seguenti quando un'applicazione ODBC 3.* x* applicazione che utilizza un ODBC 2.* x* driver esegue operazioni di segnalibro.  
  
### <a name="sqlbindcol"></a>SQLBindCol  
 Quando un'applicazione ODBC 3. *x* applicazione che utilizza un ODBC 2.* x* driver chiama **SQLBindCol** da associare alla colonna 0 con *fCType* uguale a SQL_C_VARBOOKMARK, ODBC 3*x* Controlla gestione Driver Se il *BufferLength* argomento è minore di 4 o maggiore di 4 e in caso affermativo, restituisce SQLSTATE HY090 (stringa di lunghezza o non valida del buffer). Se il *BufferLength* argomento è uguale a 4, le chiamate di gestione Driver **SQLBindCol** nel driver, dopo la sostituzione *fCType* con SQL_C_BOOKMARK.  
  
### <a name="sqlcolattribute"></a>SQLColAttribute  
 Quando un'applicazione ODBC 3. *x* applicazione che utilizza un ODBC 2.* x* driver chiama **SQLColAttribute** con il *ColumnNumber* argomento impostato su 0, la gestione Driver restituisce il *FieldIdentifier* valori elencati nella tabella seguente.  
  
|*FieldIdentifier*|Valore|  
|-----------------------|-----------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQL_FALSE|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|  
|SQL_DESC_CATALOG_NAME|"" (stringa vuota)|  
|SQL_DESC_CONCISE_TYPE|SQL_BINARY|  
|SQL_DESC_COUNT|Il valore restituito da **SQLNumResultCols**|  
|SQL_DESC_DATETIME_INTERVAL_CODE|0|  
|SQL_DESC_DISPLAY_SIZE|8|  
|SQL_DESC_FIXED_PREC_SCALE|SQL_FALSE|  
|SQL_DESC_LABEL|"" (stringa vuota)|  
|SQL_DESC_LENGTH|0|  
|SQL_DESC_LITERAL_PREFIX|"" (stringa vuota)|  
|SQL_DESC_LITERAL_SUFFIX|"" (stringa vuota)|  
|SQL_DESC_LOCAL_TYPE_NAME|"" (stringa vuota)|  
|SQL_DESC_NAME|"" (stringa vuota)|  
|SQL_DESC_NULLABLE|SQL_NO_NULLS|  
|SQL_DESC_OCTET_LENGTH|4|  
|SQL_DESC_PRECISION|4|  
|SQL_DESC_SCALE|0|  
|SQL_DESC_SCHEMA_NAME|"" (stringa vuota)|  
|SQL_DESC_SEARCHABLE|SQL_PRED_NONE|  
|SQL_DESC_TABLE_NAME|"" (stringa vuota)|  
|SQL_DESC_TYPE|SQL_BINARY|  
|SQL_DESC_TYPE_NAME|"" (stringa vuota)|  
|SQL_DESC_UNNAMED|SQL_UNNAMED|  
|SQL_DESC_UNSIGNED|SQL_FALSE|  
|SQL_DESC_UPDATEABLE|SQL_ATTR_READ_ONLY|  
  
### <a name="sqldescribecol"></a>SQLDescribeCol  
 Quando un'applicazione ODBC 3. *x* applicazione che utilizza un ODBC 2.* x* driver chiama **SQLDescribeCol** con il *ColumnNumber* argomento impostato su 0, la gestione Driver restituisce i valori elencati nella tabella seguente.  
  
|Buffer|Valore|  
|------------|-----------|  
|ColumnName|"" (stringa vuota)|  
|* NameLengthPtr|0|  
|* DataTypePtr|SQL_BINARY|  
|* ColumnSizePtr|4|  
|* DecimalDigitsPtr|0|  
|* NullablePtr|SQL_NO_NULLS|  
  
### <a name="sqlgetdata"></a>SQLGetData  
 Quando un'applicazione ODBC 3. *x* applicazione che utilizza un ODBC 2.* x* driver effettua la chiamata seguente a **SQLGetData** per recuperare un segnalibro:  
  
```  
SQLGetData(StatementHandle, 0, SQL_C_VARBOOKMARK, TargetValuePtr, BufferLength, StrLen_or_IndPtr)  
```  
  
 la chiamata viene eseguito il mapping a **SQLGetStmtOption** con un *fOption* di SQL_GET_BOOKMARK, come indicato di seguito:  
  
```  
SQLGetStmtOption(hstmt, SQL_GET_BOOKMARK, TargetValuePtr)  
```  
  
 dove *hstmt* e *il parametro pvParam* sono impostate sui valori in *StatementHandle* e *TargetValuePtr*, rispettivamente. Il segnalibro viene restituito nel buffer a cui fa riferimento il *il parametro pvParam* (*TargetValuePtr*) argomento. Il valore nel buffer a cui punta il *StrLen_or_IndPtr* argomento nella chiamata a **SQLGetData** è impostato su 4.  
  
 Questo mapping è necessario tenere conto per il caso in cui **SQLFetch** è stato chiamato prima della chiamata a **SQLGetData** e ODBC 2.* x* driver non supporta **SQLExtendedFetch**. In questo caso, **SQLFetch** potrebbe essere passato tramite l'API ODBC 2.* x* driver, in cui il recupero di case segnalibro non è supportato.  
  
 **SQLGetData** non può essere chiamato più volte in un ODBC 2.* x* driver di recuperare un segnalibro in parti, pertanto la chiamata di **SQLGetData** con il *BufferLength* argomento impostato su un valore inferiore a 4 e *ColumnNumber*argomento impostato su 0 restituiranno SQLSTATE HY090 (stringa di lunghezza o non valida del buffer). **SQLGetData** , tuttavia, può essere chiamato più volte per recuperare lo stesso segnalibro.  
  
### <a name="sqlsetstmtattr"></a>SQLSetStmtAttr  
 Quando un'applicazione ODBC 3. *x* applicazione che utilizza un ODBC 2.* x* driver chiama **SQLSetStmtAttr** per impostare l'attributo SQL_ATTR_USE_BOOKMARKS SQL_UB_VARIABLE, gestione Driver imposta l'attributo SQL_UB_ON in sottostante ODBC 2.* x* driver.

