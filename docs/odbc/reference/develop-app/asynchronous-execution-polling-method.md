---
title: Esecuzione asincrona (metodo di Polling) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- asynchronous execution [ODBC]
ms.assetid: 8cd21734-ef8e-4066-afd5-1f340e213f9c
caps.latest.revision: 40
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d64874a4633e7bede14051d882925f633dadc36c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32913826"
---
# <a name="asynchronous-execution-polling-method"></a>Esecuzione asincrona (metodo di Polling)
Prima di ODBC 3.8 e Windows 7 SDK, le operazioni asincrone sono state consentite solo su funzioni a istruzioni. Per ulteriori informazioni, vedere il **esecuzione asincrona delle operazioni istruzione**, più avanti in questo argomento.  
  
 ODBC 3.8 in Windows 7 SDK è stato introdotto esecuzione asincrona nelle operazioni relative alla connessione. Per ulteriori informazioni, vedere il **esecuzione asincrona delle operazioni di connessione** sezione più avanti in questo argomento.  
  
 In Windows 7 SDK, per l'istruzione asincrona o operazioni di connessione, un'applicazione determinato che l'operazione asincrona è completa utilizzando il metodo di polling. A partire da Windows 8 SDK, è possibile determinare che un'operazione asincrona viene completata utilizzando il metodo di notifica. Per ulteriori informazioni, vedere [esecuzione asincrona (metodo di notifica)](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md).  
  
 Per impostazione predefinita, i driver di eseguire funzioni ODBC in modo sincrono; ovvero, l'applicazione chiama una funzione e il driver non restituisce il controllo all'applicazione fino a quando non ha terminato l'esecuzione della funzione. Tuttavia, alcune funzioni possono essere eseguite in modo asincrono; ovvero, l'applicazione chiama la funzione e il driver, dopo l'elaborazione minima, restituisce il controllo all'applicazione. L'applicazione può quindi chiamare altre funzioni, mentre la prima funzione è ancora in esecuzione.  
  
 Esecuzione asincrona è supportato per la maggior parte delle funzioni che vengono eseguite in gran parte dell'origine dati, ad esempio le funzioni per stabilire connessioni, preparare ed eseguire istruzioni SQL, recuperare i metadati, recuperare i dati e il commit delle transazioni. È particolarmente utile quando l'attività viene eseguita sull'origine dati richiede molto tempo, ad esempio un processo di accesso o una query complessa in un database di grandi dimensioni.  
  
 Quando l'applicazione esegue una funzione con un'istruzione o di una connessione in cui è abilitata per l'elaborazione asincrona, il driver esegue una quantità minima di elaborazione (ad esempio gli argomenti per gli errori di verifica), passa all'origine dati di elaborazione e restituisce controllo all'applicazione con il codice restituito SQL_STILL_EXECUTING. Quindi, l'applicazione esegue altre attività. Per determinare quando ha terminato la funzione asincrona, l'applicazione esegue il polling il driver a intervalli regolari, chiamando la funzione con gli stessi argomenti originariamente utilizzato. Se la funzione è ancora in esecuzione, restituisce SQL_STILL_EXECUTING; Se ha terminato l'esecuzione, viene restituito il codice che verrebbe restituito eseguita in modo sincrono, ad esempio SQL_SUCCESS o SQL_ERROR SQL_NEED_DATA.  
  
 Se una funzione viene eseguita in modo sincrono o asincrono è specifici del driver. Si supponga, ad esempio, che viene memorizzato nella cache i metadati di set di risultati nel driver. In questo caso, il tempo minimo per eseguire **SQLDescribeCol** e il driver deve semplicemente eseguire la funzione anziché artificialmente ritardare l'esecuzione. D'altra parte, se il driver deve recuperare i metadati dall'origine dati, deve restituire controllo all'applicazione mentre è in questo modo. Pertanto, l'applicazione deve essere in grado di gestire un codice restituito diverso da SQL_STILL_EXECUTING dopo l'esecuzione di una funzione in modo asincrono.  
  
## <a name="executing-statement-operations-asynchronously"></a>L'esecuzione delle operazioni di istruzione in modo asincrono  
 Le funzioni di istruzione seguenti operano su un'origine dati e possono eseguire in modo asincrono:  
  
||||  
|-|-|-|  
|[SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|[SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|[SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)|  
|[SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)|[SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|[SQLDescribeParam](../../../odbc/reference/syntax/sqldescribeparam-function.md)|  
|[SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|[SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|[SQLForeignKeys](../../../odbc/reference/syntax/sqlforeignkeys-function.md)|[SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|[SQLGetTypeInfo](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)|[SQLMoreResults](../../../odbc/reference/syntax/sqlmoreresults-function.md)|[SQLNumParams](../../../odbc/reference/syntax/sqlnumparams-function.md)|  
|[SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|[SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md)|[SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|[SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|[SQLProcedureColumns](../../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|[SQLProcedures](../../../odbc/reference/syntax/sqlprocedures-function.md)|  
|[SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|[SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|[SQLSpecialColumns](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)|  
|[SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|[SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|[SQLTables](../../../odbc/reference/syntax/sqltables-function.md)|  
  
 L'esecuzione asincrona delle istruzioni è controllata in una singola istruzione o una singola connessione, a seconda dell'origine dati. Ovvero, l'applicazione specifica non è una particolare funzione da eseguire in modo asincrono, ma che qualsiasi funzione eseguita su una particolare istruzione da eseguire in modo asincrono. Per trovare un'applicazione out nella quale è supportata, chiama [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) con un'opzione di SQL_ASYNC_MODE. SQL_AM_CONNECTION viene restituito se è supportata l'esecuzione asincrona del livello di connessione (per un handle di istruzione). SQL_AM_STATEMENT se è supportata a livello di istruzione di esecuzione asincrona.  
  
 Per specificare che devono essere funzioni eseguite con una particolare istruzione eseguita in modo asincrono, l'applicazione chiama **SQLSetStmtAttr** attributo con il SQL_ATTR_ASYNC_ENABLE e lo imposta su SQL_ASYNC_ENABLE_ON. Se è supportata l'elaborazione asincrona a livello di connessione, l'attributo di istruzione SQL_ATTR_ASYNC_ENABLE è di sola lettura e il relativo valore è lo stesso come attributo di connessione della connessione in cui l'istruzione è stata allocata. È specifico del driver che il valore dell'attributo di istruzione è impostato in fase di allocazione di istruzione o in un secondo momento. Il tentativo di impostarla restituirà SQL_ERROR e SQLSTATE HYC00 (funzionalità facoltativa non implementata).  
  
 Per specificare che devono essere funzioni eseguite con una determinata connessione eseguita in modo asincrono, l'applicazione chiama **SQLSetConnectAttr** attributo con il SQL_ATTR_ASYNC_ENABLE e lo imposta su SQL_ASYNC_ENABLE_ON. Tutti gli handle di istruzione future allocati per la connessione verranno abilitati per l'esecuzione asincrona. è definito dal driver se gli handle di istruzione esistente verranno abilitati da questa azione. Se SQL_ATTR_ASYNC_ENABLE è impostata su SQL_ASYNC_ENABLE_OFF, tutte le istruzioni della connessione sono in modalità sincrona. Se è abilitata l'esecuzione asincrona mentre è presente un'istruzione attiva nella connessione, viene restituito un errore.  
  
 Per determinare il numero massimo di istruzioni simultanee attive in modalità asincrona in grado di supportare il driver in una determinata connessione, l'applicazione chiama **SQLGetInfo** con l'opzione SQL_MAX_ASYNC_CONCURRENT_STATEMENTS.  
  
 Il codice seguente viene illustrato come modello di polling.  
  
```  
SQLHSTMT  hstmt1;  
SQLRETURN rc;  
  
// Specify that the statement is to be executed asynchronously.  
SQLSetStmtAttr(hstmt1, SQL_ATTR_ASYNC_ENABLE, SQL_ASYNC_ENABLE_ON, 0);  
  
// Execute a SELECT statement asynchronously.  
while ((rc=SQLExecDirect(hstmt1,"SELECT * FROM Orders",SQL_NTS))==SQL_STILL_EXECUTING) {  
   // While the statement is still executing, do something else.  
   // Do not use hstmt1, because it is being used asynchronously.  
}  
  
// When the statement has finished executing, retrieve the results.  
```  
  
 Durante l'esecuzione di una funzione in modo asincrono, l'applicazione può chiamare funzioni su tutte le altre istruzioni. L'applicazione può anche chiamare funzioni in qualsiasi connessione, ad eccezione di quello associato all'istruzione asincrona. Tuttavia, l'applicazione può solo chiamare la funzione originale e le funzioni seguenti (con l'handle di istruzione o la connessione associata, handle di ambiente), dopo un'operazione di istruzione restituisce SQL_STILL_EXECUTING:  
  
-   [SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)  
  
-   [SQLCancelHandle](../../../odbc/reference/syntax/sqlcancelhandle-function.md) (dell'handle di istruzione)  
  
-   [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)  
  
-   [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)  
  
-   [SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)  
  
-   [SQLGetEnvAttr](../../../odbc/reference/syntax/sqlgetenvattr-function.md)  
  
-   [SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)  
  
-   [SQLDataSources](../../../odbc/reference/syntax/sqldatasources-function.md)  
  
-   [SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)  
  
-   [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)  
  
-   [SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md)  
  
-   [SQLNativeSql](../../../odbc/reference/syntax/sqlnativesql-function.md)  
  
 Se l'applicazione chiama qualsiasi altra funzione con l'istruzione asincrona o con la connessione associata a tale istruzione, la funzione restituisce SQLSTATE HY010 (funzione di errore nella sequenza), ad esempio.  
  
```  
SQLHDBC       hdbc1, hdbc2;  
SQLHSTMT      hstmt1, hstmt2, hstmt3;  
SQLCHAR *     SQLStatement = "SELECT * FROM Orders";  
SQLUINTEGER   InfoValue;  
SQLRETURN     rc;  
  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt2);  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc2, &hstmt3);  
  
// Specify that hstmt1 is to be executed asynchronously.  
SQLSetStmtAttr(hstmt1, SQL_ATTR_ASYNC_ENABLE, SQL_ASYNC_ENABLE_ON, 0);  
  
// Execute hstmt1 asynchronously.  
while ((rc = SQLExecDirect(hstmt1, SQLStatement, SQL_NTS)) == SQL_STILL_EXECUTING) {  
   // The following calls return HY010 because the previous call to  
   // SQLExecDirect is still executing asynchronously on hstmt1. The  
   // first call uses hstmt1 and the second call uses hdbc1, on which  
   // hstmt1 is allocated.  
   SQLExecDirect(hstmt1, SQLStatement, SQL_NTS);   // Error!  
   SQLGetInfo(hdbc1, SQL_UNION, (SQLPOINTER) &InfoValue, 0, NULL);   // Error!  
  
   // The following calls do not return errors. They use a statement  
   // handle other than hstmt1 or a connection handle other than hdbc1.  
   SQLExecDirect(hstmt2, SQLStatement, SQL_NTS);   // OK  
   SQLTables(hstmt3, NULL, 0, NULL, 0, NULL, 0, NULL, 0);   // OK  
   SQLGetInfo(hdbc2, SQL_UNION, (SQLPOINTER) &InfoValue, 0, NULL);   // OK  
}  
```  
  
 Quando un'applicazione chiama una funzione per determinare se è ancora in esecuzione in modo asincrono, è necessario utilizzare l'handle di istruzione originale. Questo avviene perché l'esecuzione asincrona viene tenuta traccia in base a una singola istruzione. L'applicazione deve fornire anche i valori validi per gli altri argomenti, ovvero argomenti originali eseguirà: per risolvere l'errore durante la verifica in Gestione Driver. Tuttavia, dopo che il driver controlla l'handle di istruzione e determina che l'istruzione viene eseguita in modo asincrono, ignora tutti gli altri argomenti.  
  
 Durante l'esecuzione di una funzione in modo asincrono, vale a dire, dopo che ha restituito SQL_STILL_EXECUTING e prima che restituisce un codice diverso, l'applicazione può annullare chiamando **SQLCancel** o **SQLCancelHandle** con lo stesso handle di istruzione. Non è garantito per annullare l'esecuzione di funzione. Ad esempio, la funzione potrebbe essere già stato completato. Inoltre, il codice restituito da **SQLCancel** o **SQLCancelHandle** indica solo se il tentativo di annullare la funzione ha avuto esito positivo, non se è effettivamente annullata la funzione. Per determinare se la funzione è stata annullata, l'applicazione chiama la funzione nuovamente. Se la funzione è stata annullata, viene restituito SQL_ERROR e SQLSTATE HY008 (operazione annullata). Se la funzione non è stata annullata, viene restituito un altro codice, ad esempio SQL_SUCCESS, SQL_STILL_EXECUTING o SQL_ERROR con SQLSTATE un diverso.  
  
 Per disabilitare l'esecuzione asincrona di una particolare istruzione quando il driver supporta l'elaborazione asincrona a livello di istruzione, l'applicazione chiama **SQLSetStmtAttr** attributo con il SQL_ATTR_ASYNC_ENABLE e lo imposta su SQL _ ASYNC_ENABLE_OFF. Se il driver supporta l'elaborazione asincrona a livello di connessione, l'applicazione chiama **SQLSetConnectAttr** per impostare SQL_ATTR_ASYNC_ENABLE su SQL_ASYNC_ENABLE_OFF, che disabilita l'esecuzione asincrona di tutte le istruzioni nel connessione.  
  
 L'applicazione deve elaborare i record di diagnostica nel ciclo ripetuto della funzione originale. Se **SQLGetDiagField** o **SQLGetDiagRec** viene chiamato quando una funzione asincrona è in esecuzione, verrà restituito l'elenco corrente dei record di diagnostica. Ogni volta che la chiamata di funzione originale viene ripetuta, Cancella i record di diagnostica precedenti.  
  
## <a name="executing-connection-operations-asynchronously"></a>L'esecuzione di operazioni di connessione in modo asincrono  
 Prima di ODBC 3.8, esecuzione asincrona era consentito per la preparazione, ad esempio operazioni di istruzione, eseguire e recuperare, come operazioni sui metadati del catalogo. A partire da ODBC 3.8, esecuzione asincrona è inoltre possibile per le operazioni correlate alla connessione che ad come connettere, disconnettere, commit e rollback.  
  
 Per ulteriori informazioni su ODBC 3.8, vedere [novità di ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md).  
  
 L'esecuzione di operazioni di connessione in modo asincrono è utile negli scenari seguenti:  
  
-   Quando un numero ridotto di thread gestisce un numero elevato di dispositivi con dati molto elevate. Per ottimizzare la velocità di risposta e la scalabilità è consigliabile che tutte le operazioni siano asincroni.  
  
-   Quando si desidera la sovrapposizione di operazioni di database tra più connessioni per ridurre i tempi di trasferimento trascorso.  
  
-   Chiamate asincrone efficiente di ODBC e la possibilità di annullare le operazioni di connessione consentono a un'applicazione consentire all'utente di annullare qualsiasi operazione lenta senza dover attendere il timeout.  
  
 Le funzioni seguenti, che operano sugli handle di connessione, ora possono essere eseguite in modo asincrono:  
  
||||  
|-|-|-|  
|[SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|[SQLDisconnect](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|[SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|[Funzione SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
  
 Per determinare se un driver supporta le operazioni asincrone in queste funzioni, un'applicazione chiama **SQLGetInfo** con SQL_ASYNC_DBC_FUNCTIONS. Se sono supportate le operazioni asincrone, viene restituito SQL_ASYNC_DBC_CAPABLE. SQL_ASYNC_DBC_NOT_CAPABLE viene restituito se non sono supportate le operazioni asincrone.  
  
 Per specificare che devono essere funzioni eseguite con una determinata connessione eseguita in modo asincrono, l'applicazione chiama **SQLSetConnectAttr** e imposta l'attributo SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE SQL_ASYNC_DBC_ENABLE ON. L'impostazione di un attributo di connessione prima di stabilire una connessione sempre esegue in modo sincrono. Inoltre, l'operazione di impostazione della connessione attributo SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE con **SQLSetConnectAttr** viene sempre eseguito in modo sincrono.  
  
 Un'applicazione può attivare l'operazione asincrona prima di effettuare una connessione. Poiché gestione Driver non è possibile determinare quale driver prima di eseguire una connessione, gestione Driver restituirà sempre esito positivo in **SQLSetConnectAttr**. Tuttavia, potrebbe non riuscire a connettersi se il driver ODBC non supporta operazioni asincrone.  
  
 In generale, può essere presente al massimo un in modo asincrono l'esecuzione di funzione associata a un handle di connessione specifico o un handle di istruzione. Tuttavia, un handle di connessione può avere più di un handle di istruzione associata. Se non sono presenti operazioni asincrone in esecuzione nell'handle di connessione, un handle di istruzione associata può eseguire un'operazione asincrona. Analogamente, è possibile includere un'operazione asincrona su un handle di connessione se non sono presenti operazioni asincrone in corso alcun handle di istruzione associata. Un tentativo di eseguire un'operazione asincrona mediante un handle di cui è attualmente in esecuzione un'operazione asincrona restituirà HY010, "Errore nella funzione sequenza".  
  
 Se un'operazione di connessione restituisce SQL_STILL_EXECUTING, un'applicazione può solo chiamare la funzione originale e le funzioni seguenti per tale handle di connessione:  
  
-   **SQLCancelHandle** (nell'handle di connessione)  
  
-   **SQLGetDiagField**  
  
-   **SQLGetDiagRec**  
  
-   **SQLAllocHandle** (allocando ENV/DBC)  
  
-   **SQLAllocHandleStd** (allocando ENV/DBC)  
  
-   **SQLGetEnvAttr**  
  
-   **SQLGetConnectAttr**  
  
-   **SQLDataSources**  
  
-   **SQLDrivers**  
  
-   **SQLGetInfo**  
  
-   **SQLGetFunctions**  
  
 L'applicazione deve elaborare i record di diagnostica nel ciclo ripetuto della funzione originale. Se SQLGetDiagField o SQLGetDiagRec viene chiamato quando una funzione asincrona è in esecuzione, verrà restituito l'elenco corrente dei record di diagnostica. Ogni volta che la chiamata di funzione originale viene ripetuta, Cancella i record di diagnostica precedenti.  
  
 Se una connessione viene aperta o chiusa in modo asincrono, l'operazione è completa quando l'applicazione riceve SQL_SUCCESS o SQL_SUCCESS_WITH_INFO nella chiamata di funzione originale.  
  
 Una nuova funzione è stato aggiunto a ODBC 3.8, **SQLCancelHandle**. Questa funzione Annulla le funzioni di sei connessione (**SQLBrowseConnect**, **SQLConnect**, **SQLDisconnect**, **SQLDriverConnect**, **SQLEndTran**, e **SQLSetConnectAttr**). Un'applicazione deve chiamare **SQLGetFunctions** per determinare se il driver supporta **SQLCancelHandle**. Come con **SQLCancel**, se **SQLCancelHandle** restituisce esito positivo, questo non significa che l'operazione è stata annullata. Un'applicazione deve chiamare la funzione originale per determinare se l'operazione è stata annullata. **SQLCancelHandle** consente di annullare le operazioni asincrone in handle di connessione o handle di istruzione. Utilizzando **SQLCancelHandle** handle di annullare un'operazione in un'istruzione è equivale a chiamare **SQLCancel**.  
  
 Non è necessario supportare entrambi **SQLCancelHandle** e le operazioni di connessione asincrona nello stesso momento. Un driver può supportare operazioni di connessione asincrona, ma non **SQLCancelHandle**, o viceversa.  
  
 Operazioni di connessione asincrona e **SQLCancelHandle** può anche essere utilizzato da ODBC 3. x e le applicazioni ODBC 2. x con un driver ODBC 3.8 e gestione dei Driver di ODBC 3.8. Per informazioni su come abilitare un'applicazione usare nuove funzionalità nella versione ODBC meno recente, vedere [matrice di compatibilità](../../../odbc/reference/develop-app/compatibility-matrix.md).  
  
### <a name="connection-pooling"></a>Pool di connessioni  
 Ogni volta che il pool di connessioni è abilitato, le operazioni asincrone sono supportate solo minimamente per stabilire una connessione (con **SQLConnect** e **SQLDriverConnect**) e la chiusura di una connessione con **SQLDisconnect**. Ma un'applicazione deve ancora essere in grado di gestire il valore restituito da SQL_STILL_EXECUTING in **SQLConnect**, **SQLDriverConnect**, e **SQLDisconnect**.  
  
 Quando il pool di connessioni è abilitato, **SQLEndTran** e **SQLSetConnectAttr** sono supportati per le operazioni asincrone.  
  
## <a name="example"></a>Esempio  
  
### <a name="description"></a>Description  
 Nell'esempio seguente viene illustrato come utilizzare **SQLSetConnectAttr** per abilitare l'esecuzione asincrona per le funzioni correlate alla connessione.  
  
### <a name="code"></a>Codice  
  
```  
BOOL AsyncConnect (SQLHANDLE hdbc)   
{  
   SQLRETURN r;  
   SQLHANDLE hdbc;  
  
   // Enable asynchronous execution of connection functions.  
   // This must be executed synchronously, that is r != SQL_STILL_EXECUTING  
   r = SQLSetConnectAttr(  
         hdbc,   
         SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE,  
         reinterpret_cast<SQLPOINTER> (SQL_ASYNC_DBC_ENABLE_ON),  
         0);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO)   
   {  
      return FALSE;  
   }  
  
   TCHAR szConnStrIn[256] = _T("DSN=AsyncDemo");  
  
   r = SQLDriverConnect(hdbc, NULL, (SQLTCHAR *) szConnStrIn, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
  
   if (r == SQL_ERROR)   
   {  
      // Use SQLGetDiagRec to process the error.  
      // If SQLState is HY114, the driver does not support asynchronous execution.  
      return FALSE;  
   }  
  
   while (r == SQL_STILL_EXECUTING)   
   {  
      // Do something else.  
  
      // Check for completion, with the same set of arguments.  
      r = SQLDriverConnect(hdbc, NULL, (SQLTCHAR *) szConnStrIn, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
   }  
  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO)   
   {  
      return FALSE;  
   }  
  
   return TRUE;  
}  
  
```  
  
## <a name="example"></a>Esempio  
  
### <a name="description"></a>Description  
 Questo esempio illustra le operazioni di commit asincrono. Operazioni di rollback possono essere eseguite anche in questo modo.  
  
### <a name="code"></a>Codice  
  
```  
BOOL AsyncCommit ()   
{  
   SQLRETURN r;   
  
   // Assume that SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE is SQL_ASYNC_DBC_ENABLE_ON.  
  
   r = SQLEndTran(SQL_HANDLE_DBC, hdbc, SQL_COMMIT);  
   while (r == SQL_STILL_EXECUTING)   
   {  
      // Do something else.  
  
      // Check for completion with the same set of arguments.  
      r = SQLEndTran(SQL_HANDLE_DBC, hdbc, SQL_COMMIT);  
   }  
  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO)   
   {  
      return FALSE;  
   }  
   return TRUE;  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di istruzioni ODBC](../../../odbc/reference/develop-app/executing-statements-odbc.md)
