---
title: SQLGetFunctions-funzione | Documenti Microsoft
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
- SQLGetFunctions
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetFunctions
helpviewer_keywords:
- SQLGetFunctions function [ODBC]
ms.assetid: 0451d2f9-0f4f-46ba-b252-670956a52183
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e7359f5e652c2db21a991845accc15aaea5710e7
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgetfunctions-function"></a>SQLGetFunctions Function
**Conformità**  
 Introdotta: versione ODBC standard 1.0 conformità: 92 ISO  
  
 **Riepilogo**  
 **SQLGetFunctions** restituisce informazioni sul supporto di una funzione ODBC specifica se un driver. Questa funzione è implementata in Gestione Driver. può inoltre essere implementata nel driver. Se un driver implementa **SQLGetFunctions**, gestione Driver chiama la funzione nel driver. In caso contrario, esegue la funzione stessa.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLGetFunctions(  
     SQLHDBC           ConnectionHandle,  
     SQLUSMALLINT      FunctionId,  
     SQLUSMALLINT *    SupportedPtr);  
```  
  
## <a name="arguments"></a>Argomenti  
 *ConnectionHandle*  
 [Input] Handle di connessione.  
  
 *FunctionId*  
 [Input] Oggetto **#define** valore che identifica la funzione ODBC degli interessi. **SQL_API_ODBC3_ALL_FUNCTIONS orSQL_API_ALL_FUNCTIONS**. **SQL_API_ODBC3_ALL_FUNCTIONS** viene utilizzato da un'applicazione ODBC 3*x* applicazione per determinare il supporto di ODBC 3*x* e le funzioni precedenti. **SQL_API_ALL_FUNCTIONS** viene utilizzato un ODBC 2*x* applicazione per determinare il supporto di ODBC 2*x* e le funzioni precedenti.  
  
 Per un elenco di **#define** i valori che identificano le funzioni ODBC, vedere le tabelle in "Commenti".  
  
 *SupportedPtr*  
 [Output]  Se *FunctionId* identifica una singola funzione ODBC, *SupportedPtr* punta a un singolo SQLUSMALLINT valore SQL_TRUE se la funzione specificata è supportata dal driver e SQL_FALSE in caso contrario è supportato.  
  
 Se *FunctionId* è SQL_API_ODBC3_ALL_FUNCTIONS, *SupportedPtr* punta a una matrice SQLSMALLINT con un numero di elementi è uguali a SQL_API_ODBC3_ALL_FUNCTIONS_SIZE. Questa matrice viene considerata da Gestione Driver come bitmap 4.000 bit che può essere usata per determinare se un'applicazione ODBC 3*x* o la funzione precedente è supportata. La macro SQL_FUNC_EXISTS viene chiamata per determinare il supporto di funzione. (Vedere "Commenti".) Un'applicazione ODBC 3*x* applicazione può chiamare **SQLGetFunctions** con SQL_API_ODBC3_ALL_FUNCTIONS su entrambi un ODBC 3*x* o 2 di ODBC*x* driver.  
  
 Se *FunctionId* è SQL_API_ALL_FUNCTIONS, *SupportedPtr* punta a una matrice SQLUSMALLINT di 100 elementi. La matrice è indicizzata dai **#define** i valori utilizzati dalla *FunctionId* per identificare ogni funzione ODBC; alcuni elementi della matrice sono utilizzata ed è riservata per utilizzi futuri. Un elemento è SQL_TRUE se identifica un ODBC 2*x* o la funzione precedente è supportato dal driver. Se identifica una funzione ODBC non supportata dal driver o non identifica una funzione ODBC è SQL_FALSE.  
  
 Le matrici restituite **SupportedPtr* utilizzare l'indicizzazione in base zero.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLGetFunctions** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato possono essere ottenuti chiamando **SQLGetDiagRec** con un *HandleType* di Impostato su SQL_HANDLE_DBC e *gestire* di *ConnectionHandle*. Nella tabella seguente sono elencati i valori SQLSTATE comunemente restituiti da **SQLGetFunctions** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------|-----|-----------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|08S01|Errore del collegamento di comunicazione|Collegamento di comunicazione tra il driver e l'origine dati a cui era connesso il driver non è stato possibile prima dell'elaborazione della funzione è stata completata.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel * \*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver è stato in grado di allocare la memoria necessaria per supportare l'esecuzione o il completamento della funzione.|  
|HY010|Errore nella sequenza (funzione)|(DM) **SQLGetFunctions** è stato chiamato prima di **SQLConnect**, **SQLBrowseConnect**, o **SQLDriverConnect**.<br /><br /> (DM) **SQLBrowseConnect** è stato chiamato per il *ConnectionHandle* e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima di **SQLBrowseConnect** restituito SQL_SUCCESS_WITH_INFO o SQL_SUCCESS.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** è stato chiamato per il *ConnectionHandle* e restituito SQL_PARAM_DATA_ È DISPONIBILE. Questa funzione è stata chiamata prima che i dati sono stati recuperati per tutti i parametri con flusso.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY095|Tipo di funzione non compreso nell'intervallo|(DM) non valido *FunctionId* valore specificato.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
  
## <a name="comments"></a>Commenti  
 **SQLGetFunctions** restituisce sempre che **SQLGetFunctions**, **SQLDataSources**, e **SQLDrivers** sono supportati. Ciò avviene perché queste funzioni vengono implementate in Gestione Driver. Gestione Driver verrà eseguito il mapping una funzione ANSI per la funzione Unicode corrispondente se la funzione Unicode esiste e verrà eseguito il mapping una funzione Unicode alla funzione ANSI se esiste la funzione ANSI. Per informazioni sull'utilizzano di applicazioni **SQLGetFunctions**, vedere [livelli di conformità interfaccia](../../../odbc/reference/develop-app/interface-conformance-levels.md).  
  
 Di seguito è riportato un elenco di valori validi per *FunctionId* per le funzioni che è conforme al livello: conformità agli standard ISO 92:  
  
|Valore FunctionId|Valore FunctionId|  
|----------|----------|  
|SQL_API_SQLALLOCHANDLE|SQL_API_SQLGETDESCFIELD|  
|SQL_API_SQLBINDCOL|SQL_API_SQLGETDESCREC|  
|SQL_API_SQLCANCEL|SQL_API_SQLGETDIAGFIELD|  
|SQL_API_SQLCLOSECURSOR|SQL_API_SQLGETDIAGREC|  
|SQL_API_SQLCOLATTRIBUTE|SQL_API_SQLGETENVATTR|  
|SQL_API_SQLCONNECT|SQL_API_SQLGETFUNCTIONS|  
|SQL_API_SQLCOPYDESC|SQL_API_SQLGETINFO|  
|SQL_API_SQLDATASOURCES|SQL_API_SQLGETSTMTATTR|  
|SQL_API_SQLDESCRIBECOL|SQL_API_SQLGETTYPEINFO|  
|SQL_API_SQLDISCONNECT|SQL_API_SQLNUMRESULTCOLS|  
|SQL_API_SQLDRIVERS|SQL_API_SQLPARAMDATA|  
|SQL_API_SQLENDTRAN|SQL_API_SQLPREPARE|  
|SQL_API_SQLEXECDIRECT|SQL_API_SQLPUTDATA|  
|SQL_API_SQLEXECUTE|SQL_API_SQLROWCOUNT|  
|SQL_API_SQLFETCH|SQL_API_SQLSETCONNECTATTR|  
|SQL_API_SQLFETCHSCROLL|SQL_API_SQLSETCURSORNAME|  
|SQL_API_SQLFREEHANDLE|SQL_API_SQLSETDESCFIELD|  
|SQL_API_SQLFREESTMT|SQL_API_SQLSETDESCREC|  
|SQL_API_SQLGETCONNECTATTR|SQL_API_SQLSETENVATTR|  
|SQL_API_SQLGETCURSORNAME|SQL_API_SQLSETSTMTATTR|  
|SQL_API_SQLGETDATA| |  
  
 Di seguito è riportato un elenco di valori validi per *FunctionId* per le funzioni conforme al livello: conformità agli standard Open Group:  
  
|Valore FunctionId|Valore FunctionId|  
|-|-|  
|SQL_API_SQLCOLUMNS|SQL_API_SQLSTATISTICS|  
|SQL_API_SQLSPECIALCOLUMNS|SQL_API_SQLTABLES|  
  
 Di seguito è riportato un elenco di valori validi per *FunctionId* per le funzioni conforme al livello: conformità agli standard ODBC.  
  
|Valore FunctionId|Valore FunctionId|  
|-|-|  
|SQL_API_SQLBINDPARAMETER|SQL_API_SQLNATIVESQL|  
|SQL_API_SQLBROWSECONNECT|SQL_API_SQLNUMPARAMS|  
|SQL_API_SQLBULKOPERATIONS [1]|SQL_API_SQLPRIMARYKEYS|  
|SQL_API_SQLCOLUMNPRIVILEGES|SQL_API_SQLPROCEDURECOLUMNS|  
|SQL_API_SQLDESCRIBEPARAM|SQL_API_SQLPROCEDURES|  
|SQL_API_SQLDRIVERCONNECT|SQL_API_SQLSETPOS|  
|SQL_API_SQLFOREIGNKEYS|SQL_API_SQLTABLEPRIVILEGES|  
|SQL_API_SQLMORERESULTS| |  
  
 [1] quando si lavora con un ODBC 2*x* driver, **SQLBulkOperations** verranno restituiti come supportato solo se vengono soddisfatte entrambe le operazioni seguenti: ODBC 2*x* driver supporta ** SQLSetPos**, e il tipo di informazioni SQL_POS_OPERATIONS restituisce il bit SQL_POS_ADD come set.  
  
 Di seguito è riportato un elenco di valori validi per *FunctionId* per le funzioni introdotte in ODBC 3.8 o versione successiva:  
  
|Valore FunctionId|  
|-|  
|SQL_API_SQLCANCELHANDLE [2]|  
  
 [2] **SQLCancelHandle** verranno restituiti come supportato solo se il driver supporta sia **SQLCancel** e **SQLCancelHandle**. Se **SQLCancel** è supportata ma **SQLCancelHandle** non lo è, l'applicazione può chiamare ancora **SQLCancelHandle** su un handle di istruzione, in quanto esso verrà mappato a ** SQLCancel**.  
  
## <a name="sqlfuncexists-macro"></a>Macro SQL_FUNC_EXISTS  
 Il SQL_FUNC_EXISTS (*SupportedPtr*, *FunctionID*) macro viene usata per determinare il supporto di ODBC 3*x* o le funzioni precedenti dopo **SQLGetFunctions ** è stata chiamata con un *FunctionId* argomento di SQL_API_ODBC3_ALL_FUNCTIONS. L'applicazione chiama SQL_FUNC_EXISTS con il *SupportedPtr* argomento impostato sul *SupportedPtr* passato *SQLGetFunctions*e con il * FunctionID* argomento impostato sul **#define** per la funzione. SQL_FUNC_EXISTS restituisce SQL_TRUE se la funzione è supportata e SQL_FALSE in caso contrario.  
  
> [!NOTE]  
>  Quando si lavora con un ODBC 2*x* driver ODBC 3*x* gestione Driver restituirà SQL_TRUE per **SQLAllocHandle** e **SQLFreeHandle**perché **SQLAllocHandle** viene eseguito il mapping a **SQLAllocEnv**, **SQLAllocConnect**, o **SQLAllocStmt**, e Poiché **SQLFreeHandle** viene eseguito il mapping a **SQLFreeEnv**, **SQLFreeConnect**, o **SQLFreeStmt**. **SQLAllocHandle** o **SQLFreeHandle** con un *HandleType* argomento di SQL_HANDLE_DESC non è supportata, tuttavia, anche se SQL_TRUE viene restituito per le funzioni, poiché non esiste alcun ODBC 2*x* funzione per eseguire il mapping in questo caso.  
  
## <a name="code-example"></a>Esempio di codice  
 I tre esempi seguenti mostrano come un'applicazione usa **SQLGetFunctions** per determinare se un driver supporta **SQLTables**, **SQLColumns**, e ** SQLStatistics**. Se il driver non supporta queste funzioni, l'applicazione verrà terminata dal driver. Nell'esempio viene chiamato prima **SQLGetFunctions** una volta per ogni funzione.  
  
```  
SQLUSMALLINT TablesExists, ColumnsExists, StatisticsExists;  
RETCODE retcodeTables, retcodeColumns, retcodeStatistics  
  
retcodeTables = SQLGetFunctions(hdbc, SQL_API_SQLTABLES, &TablesExists);  
retcodeColumns = SQLGetFunctions(hdbc, SQL_API_SQLCOLUMNS, &ColumnsExists);  
retcodeStatistics = SQLGetFunctions(hdbc, SQL_API_SQLSTATISTICS, &StatisticsExists);  
  
// SQLGetFunctions is completed successfully and SQLTables, SQLColumns, and SQLStatistics are supported by the driver.  
if (retcodeTables == SQL_SUCCESS && TablesExists == SQL_TRUE &&   
retcodeColumns == SQL_SUCCESS && ColumnsExists == SQL_TRUE &&   
retcodeStatistics == SQL_SUCCESS && StatisticsExists == SQL_TRUE)   
{  
  
   // Continue with application  
  
}  
  
SQLDisconnect(hdbc);  
```  
  
 Nel secondo esempio, un'applicazione di 3. x ODBC chiama **SQLGetFunctions** e passa una matrice in cui **SQLGetFunctions** restituisce informazioni su tutti ODBC 3. x e le funzioni precedenti.  
  
```  
RETCODE retcodeTables, retcodeColumns, retcodeStatistics  
SQLUSMALLINT fExists[SQL_API_ODBC3_ALL_FUNCTIONS_SIZE];  
  
retcode = SQLGetFunctions(hdbc, SQL_API_ODBC3_ALL_FUNCTIONS, fExists);  
  
// SQLGetFunctions is completed successfully and SQLTables, SQLColumns, and SQLStatistics are supported by the driver.  
if (reccode == SQL_SUCCESS &&   
SQL_FUNC_EXISTS(fExists, SQL_API_SQLTABLES) == SQL_TRUE &&  
   SQL_FUNC_EXISTS(fExists, SQL_API_SQLCOLUMNS) == SQL_TRUE &&  
   SQL_FUNC_EXISTS(fExists, SQL_API_SQLSTATISTICS) == SQL_TRUE)   
{  
  
   // Continue with application  
  
}  
  
SQLDisconnect(hdbc);  
```  
  
 Il terzo esempio viene chiamato da un'applicazione di ODBC 2. x **SQLGetFunctions** e passa una matrice di 100 elementi in cui **SQLGetFunctions** restituisce informazioni su ODBC tutte le funzioni precedenti e 2. x.  
  
```  
#define FUNCTIONS 100  
  
RETCODE retcodeTables, retcodeColumns, retcodeStatistics  
SQLUSMALLINT fExists[FUNCTIONS];  
  
retcode = SQLGetFunctions(hdbc, SQL_API_ALL_FUNCTIONS, fExists);  
  
/* SQLGetFunctions is completed successfully and SQLTables, SQLColumns, and SQLStatistics are supported by the driver. */  
if (retcode == SQL_SUCCESS &&   
fExists[SQL_API_SQLTABLES] == SQL_TRUE &&  
   fExists[SQL_API_SQLCOLUMNS] == SQL_TRUE &&  
   fExists[SQL_API_SQLSTATISTICS] == SQL_TRUE)   
{  
  
   /* Continue with application */  
  
}  
  
SQLDisconnect(hdbc);  
```  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Restituisce l'impostazione di un attributo di connessione|[Funzione SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Restituzione di informazioni su un'origine dati o il driver|[Funzione SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
|Restituisce l'impostazione di un attributo di istruzione|[Funzione SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
