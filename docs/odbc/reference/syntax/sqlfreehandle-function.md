---
title: Funzione SQLFreeHandle | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLFreeHandle
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLFreeHandle
helpviewer_keywords:
- SQLFreeHandle function [ODBC]
ms.assetid: 17a6fcdc-b05a-4de7-be93-a316f39696a1
caps.latest.revision: 35
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 41ed0af53844edfe55203e8310ce326fb2c4e2b8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlfreehandle-function"></a>SQLFreeHandle Function
**Conformità**  
 Introdotta: versione ODBC 3.0 aderenza: 92 ISO  
  
 **Riepilogo**  
 **SQLFreeHandle** libera le risorse associate a un handle di ambiente, connessione, istruzione o descrittore specifico.  
  
> [!NOTE]  
>  Questa funzione è una funzione generica per liberare l'handle. Sostituisce le funzioni ODBC 2.0 **SQLFreeConnect** (per liberare un handle di connessione) e **SQLFreeEnv** (per liberare un handle di ambiente). **SQLFreeConnect** e **SQLFreeEnv** sono deprecati in ODBC 3*x*. **SQLFreeHandle** inoltre sostituisce la funzione ODBC 2.0 **SQLFreeStmt** (con il SQL_DROP *opzione*) per liberare un handle di istruzione. Per ulteriori informazioni, vedere "Commenti". Per ulteriori informazioni su cosa the Driver Manager esegue il mapping di questa funzione per quando un'applicazione ODBC 3*x* applicazione sta utilizzando un'API ODBC 2*x* driver, vedere [Mapping di funzioni di sostituzione per indietro Compatibilità delle applicazioni](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLFreeHandle(  
     SQLSMALLINT   HandleType,  
     SQLHANDLE     Handle);  
```  
  
## <a name="arguments"></a>Argomenti  
 *HandleType*  
 [Input] Il tipo di handle da liberare da **SQLFreeHandle**. Deve essere uno dei valori seguenti:  
  
-   IMPOSTATO SU SQL_HANDLE_DBC  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   IMPOSTATO SU SQL_HANDLE_ENV  
  
-   IMPOSTATO SU SQL_HANDLE_STMT  
  
 Handle SQL_HANDLE_DBC_INFO_TOKEN è utilizzato solo da Gestione Driver e driver. Applicazioni non devono utilizzare questo tipo di handle. Per ulteriori informazioni su SQL_HANDLE_DBC_INFO_TOKEN, vedere [consapevolezza Pool di connessioni lo sviluppo di un Driver ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
 Se *HandleType* non corrisponde a uno di questi valori, **SQLFreeHandle** restituisca SQL_INVALID_HANDLE.  
  
 *Handle*  
 [Input] L'handle deve essere liberata.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS o SQL_ERROR, SQL_INVALID_HANDLE.  
  
 Se **SQLFreeHandle** restituisce SQL_ERROR, l'handle è ancora valido.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLFreeHandle** restituisce SQL_ERROR, associato a un valore SQLSTATE possono essere ottenuti dalla struttura di dati di diagnostica per l'handle che **SQLFreeHandle** è stato eseguito un tentativo di liberare ma non è riuscito. Nella tabella seguente sono elencati i valori SQLSTATE normalmente restituiti dal **SQLFreeHandle** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel  *\*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver non è riuscito ad allocare memoria che è necessario per supportare l'esecuzione o il completamento della funzione.|  
|HY010|Errore nella sequenza (funzione)|(DM) il *HandleType* argomento sia impostato su SQL_HANDLE_ENV e almeno una connessione è in uno stato allocato o connesso. **SQLDisconnect** e **SQLFreeHandle** con un *HandleType* SQL_HANDLE_DBC deve essere chiamato per ogni connessione prima di chiamare **SQLFreeHandle** con un *HandleType* SQL_HANDLE_ENV.<br /><br /> (DM) il *HandleType* argomento è stato impostato su SQL_HANDLE_DBC e la funzione è stata chiamata prima di chiamare **SQLDisconnect** per la connessione.<br /><br /> (DM) il *HandleType* argomento è stato impostato su SQL_HANDLE_DBC. È stata chiamata una funzione in modo asincrono in esecuzione con *gestire* e la funzione era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) il *HandleType* argomento è stato impostato su SQL_HANDLE_STMT. **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos** è stato chiamato con l'handle di istruzione e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima che sono stati inviati dati per tutti i parametri data-at-execution o colonne.<br /><br /> (DM) il *HandleType* argomento è stato impostato su SQL_HANDLE_STMT. Una funzione in modo asincrono in esecuzione è stata chiamata nell'handle di istruzione o dell'handle di connessione associata e la funzione era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) il *HandleType* argomento era SQL_HANDLE_DESC. Una funzione in modo asincrono in esecuzione è stata chiamata sull'handle di connessione associata; e la funzione era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) gestisce tutti filiale e altre risorse non sono state rilasciate prima **SQLFreeHandle** è stato chiamato.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** è stato chiamato per uno degli handle di istruzione associati il *gestire* e *HandleType* è stato impostato su SQL_HANDLE_STMT come o SQL_HANDLE_DESC restituito SQL_PARAM_DATA_AVAILABLE. Questa funzione è stata chiamata prima che i dati sono stati recuperati per tutti i parametri con flusso.|  
|HY013|Errore di gestione della memoria|Il *HandleType* argomento è stato impostato su SQL_HANDLE_STMT o SQL_HANDLE_DESC, e la chiamata di funzione non può essere elaborata perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY017|Utilizzo non valido di un handle di descrittore allocato automaticamente.|(DM) il *gestire* argomento è stato impostato per l'handle per un descrittore allocato automaticamente.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|(DM) il *HandleType* argomento sia SQL_HANDLE_DESC e il driver è un'API ODBC 2*x* driver.<br /><br /> (DM) il *HandleType* argomento è stato impostato su SQL_HANDLE_STMT e il driver non è un driver ODBC valido.|  
  
## <a name="comments"></a>Commenti  
 **SQLFreeHandle** viene utilizzata per liberare l'handle per gli ambienti, le connessioni, istruzioni e i descrittori, come descritto nelle sezioni seguenti. Per informazioni generali sugli handle, vedere [handle](../../../odbc/reference/develop-app/handles.md).  
  
 Un'applicazione non deve utilizzare un handle dopo che è stato liberato; Gestione Driver non verifica la validità di un handle di una chiamata di funzione.  
  
## <a name="freeing-an-environment-handle"></a>Liberare un Handle di ambiente  
 Prima di chiamare **SQLFreeHandle** con un *HandleType* impostato su SQL_HANDLE_ENV, un'applicazione deve chiamare **SQLFreeHandle** con un *HandleType*impostato su SQL_HANDLE_DBC per tutte le connessioni allocata nell'ambiente. In caso contrario, la chiamata a **SQLFreeHandle** restituisce SQL_ERROR e l'ambiente e qualsiasi connessione attiva rimane valido. Per ulteriori informazioni, vedere [ambiente gestisce](../../../odbc/reference/develop-app/environment-handles.md) e [allocare l'Handle di ambiente](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).  
  
 Se l'ambiente è un ambiente condiviso, l'applicazione che chiama **SQLFreeHandle** con un *HandleType* impostato su SQL_HANDLE_ENV non avrà più accesso per l'ambiente dopo la chiamata, ma l'ambiente le risorse non sono necessariamente liberate. La chiamata a **SQLFreeHandle** decrementa il conteggio dei riferimenti dell'ambiente. Il conteggio dei riferimenti è gestito da Gestione Driver. Se non raggiunge lo zero, non viene liberata ambiente condiviso, perché è ancora in uso da un altro componente. Se il conteggio dei riferimenti arriva a zero, vengono liberate le risorse dell'ambiente condiviso.  
  
## <a name="freeing-a-connection-handle"></a>Liberare un Handle di connessione  
 Prima di chiamare **SQLFreeHandle** con un *HandleType* SQL_HANDLE_DBC, un'applicazione deve chiamare **SQLDisconnect** per la connessione se c'è una connessione su questo gestire *.* In caso contrario, la chiamata a **SQLFreeHandle** restituisce SQL_ERROR e la connessione rimane valido.  
  
 Per ulteriori informazioni, vedere [handle di connessione](../../../odbc/reference/develop-app/connection-handles.md) e [disconnessione da un'origine dati o il Driver](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
## <a name="freeing-a-statement-handle"></a>Rilascio di un handle di istruzione  
 Una chiamata a **SQLFreeHandle** con un *HandleType* impostato su SQL_HANDLE_STMT libera tutte le risorse che sono state allocate da una chiamata a **SQLAllocHandle** con un  *HandleType* impostato su SQL_HANDLE_STMT. Quando un'applicazione chiama **SQLFreeHandle** per liberare un'istruzione con risultati in sospeso, vengono eliminati i risultati in sospeso. Quando un'applicazione libera un handle di istruzione, il driver libera i descrittori allocati automaticamente quattro associati a tale handle. Per ulteriori informazioni, vedere [istruzione gestisce](../../../odbc/reference/develop-app/statement-handles.md) e [liberare l'Handle di istruzione](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md).  
  
 Si noti che **SQLDisconnect** Elimina automaticamente eventuali istruzioni e i descrittori aperto per la connessione.  
  
## <a name="freeing-a-descriptor-handle"></a>Liberare un Handle di descrittore  
 Una chiamata a **SQLFreeHandle** con un *HandleType* di SQL_HANDLE_DESC rilascia l'handle di descrittore in *gestire*. La chiamata a **SQLFreeHandle** non rilasci memoria allocata dall'applicazione che è possibile fare riferimento da un campo del puntatore (inclusi SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR e SQL_DESC_OCTET_LENGTH_PTR) di qualsiasi record del descrittore di *gestire*. La memoria allocata dal driver per i campi che non sono campi di tipo puntatore viene liberata quando l'handle viene liberato. Quando viene liberato un handle di descrittore allocato dall'utente, i relativi handle di descrittore allocato automaticamente rispettivi ripristino tutte le istruzioni che era stato associato l'handle liberato.  
  
> [!NOTE]  
>  ODBC 2*x* driver non supporta gli handle di descrittore rilascio, esattamente come allocare gli handle di descrittore non supportano.  
  
 Si noti che **SQLDisconnect** Elimina automaticamente eventuali istruzioni e i descrittori aperto per la connessione. Quando un'applicazione libera un handle di istruzione, il driver libera i descrittori generati automaticamente associati a tale handle.  
  
 Per ulteriori informazioni sui descrittori, vedere [descrittori](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="code-example"></a>Esempio di codice  
 Per ulteriori esempi di codice, vedere [SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md) e [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
### <a name="code"></a>Codice  
  
```  
// SQLFreeHandle.cpp  
// compile with: user32.lib odbc32.lib  
#include <windows.h>  
#include <sqlext.h>  
#include <stdio.h>  
  
int main() {  
   SQLRETURN retCode;  
   HWND desktopHandle = GetDesktopWindow();   // desktop's window handle  
   SQLCHAR connStrbuffer[1024];  
   SQLSMALLINT connStrBufferLen;  
  
   // Initialize the environment, connection, statement handles.  
   SQLHENV henv = NULL;   // Environment     
   SQLHDBC hdbc = NULL;   // Connection handle  
   SQLHSTMT hstmt = NULL;   // Statement handle  
  
   // Allocate the environment.  
   retCode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
  
   // Set environment attributes.  
   retCode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (void*)SQL_OV_ODBC3, -1);  
  
   // Allocate the connection.  
   retCode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
  
   // Set the login timeout.  
   retCode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)10, 0);  
  
   // Let the user select the data source and connect to the database.  
   retCode = SQLDriverConnect(hdbc, desktopHandle, (SQLCHAR *)"Driver={SQL Server}", SQL_NTS, connStrbuffer, 1025, &connStrBufferLen, SQL_DRIVER_PROMPT);  
  
   retCode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
   // Free handles, and disconnect.     
   if (hstmt) {   
      SQLFreeHandle(SQL_HANDLE_STMT, hstmt);  
      hstmt = NULL;   
   }  
   if (hdbc) {   
      SQLDisconnect(hdbc);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc);  
      hdbc = NULL;   
   }  
   if (henv) {   
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
      henv = NULL;   
   }  
}  
```  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Allocazione di un handle|[Funzione SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|L'elaborazione di istruzione di annullamento|[SQLCance Functionl](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Impostazione di un nome di cursore|[Funzione SQLSetCursorName](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Programma di esempio ODBC](../../../odbc/reference/sample-odbc-program.md)
