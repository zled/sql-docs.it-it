---
title: Funzione SQLFreeStmt | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLFreeStmt
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLFreeStmt
helpviewer_keywords:
- SQLFreeStmt function [ODBC]
ms.assetid: 03408162-8b63-4470-90c4-e6c7d8d33892
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2d758d7ec03a7d67e7f943a01d19c4959aa18bc9
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sqlfreestmt-function"></a>SQLFreeStmt Function
**Conformità**  
 Introdotta: versione ODBC standard 1.0 conformità: 92 ISO  
  
 **Riepilogo**  
 **SQLFreeStmt** Arresta elaborazione associata a un'istruzione specifica, chiude tutti i cursori aperti associati all'istruzione, Elimina risultati in sospeso o, facoltativamente, libera tutte le risorse associate all'handle di istruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLFreeStmt(  
     SQLHSTMT       StatementHandle,  
     SQLUSMALLINT   Option);  
```  
  
## <a name="arguments"></a>Argomenti  
 *StatementHandle*  
 [Input] Handle di istruzione  
  
 *Opzione*  
 [Input] Una delle opzioni seguenti:  
  
 Chiudere SQL _: Chiude il cursore associato *StatementHandle* (se ne è stata definita) ed Elimina tutti i risultati in sospeso. L'applicazione possibile riaprire il cursore in un secondo momento mediante l'esecuzione di un **selezionare** istruzione nuovamente con i valori dei parametri uguale o diverso. Se nessun cursore è aperto, questa opzione ha effetto per l'applicazione. **SQLCloseCursor** può anche essere chiamato per chiudere un cursore. Per ulteriori informazioni, vedere [la chiusura del cursore](../../../odbc/reference/develop-app/closing-the-cursor.md).  
  
 SQL_DROP: Questa opzione è deprecata. Una chiamata a **SQLFreeStmt** con un *opzione* di SQL_DROP viene eseguito il mapping in Gestione Driver per [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md).  
  
 SQL_UNBIND: Imposta il campo SQL_DESC_COUNT di ARD su 0, il rilascio di tutti i buffer di colonna associato da **SQLBindCol** per il dato *StatementHandle*. Questo non disassociare la colonna del segnalibro. a tale scopo, il campo SQL_DESC_DATA_PTR del ARD per la colonna del segnalibro è impostato su NULL. Si noti che se questa operazione viene eseguita in un descrittore allocato in modo esplicito che viene condiviso da più di un'istruzione, l'operazione influirà sulle associazioni di tutte le istruzioni che condividono il descrittore. Per ulteriori informazioni, vedere [Panoramica di recupero di risultati (Basic)](../../../odbc/reference/develop-app/retrieving-results-basic.md).  
  
 SQL_RESET_PARAMS: Imposta il campo SQL_DESC_COUNT di APD su 0, il rilascio di tutti i buffer di parametro impostati da **SQLBindParameter** per il dato *StatementHandle*. Se questa operazione viene eseguita in un descrittore allocato in modo esplicito che viene condiviso da più di un'istruzione, questa operazione interesserà le associazioni di tutte le istruzioni che condividono il descrittore. Per ulteriori informazioni, vedere [parametri di associazione](../../../odbc/reference/develop-app/binding-parameters-odbc.md).  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLFreeStmt** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato possono essere ottenuti chiamando **SQLGetDiagRec** con un *HandleType* di SQL _ HANDLE_STMT e *gestire* di *StatementHandle*. Nella tabella seguente sono elencati i valori SQLSTATE normalmente restituiti dal **SQLFreeStmt** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel  *\*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver è stato in grado di allocare la memoria necessaria per supportare l'esecuzione o il completamento della funzione.|  
|HY010|Errore nella sequenza (funzione)|(DM) a cui è stata chiamata per l'handle di connessione associata a una funzione in modo asincrono in esecuzione il *StatementHandle*. Questa funzione asincrona era ancora in esecuzione quando **SQLFreeStmt** è stato chiamato.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** è stato chiamato per il *StatementHandle* e restituito SQL_PARAM_DATA_ È DISPONIBILE. Questa funzione è stata chiamata con *opzione* impostato su SQL_RESET_PARAMS prima che i dati sono stati recuperati per tutti i parametri con flusso.<br /><br /> (DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione il *StatementHandle* ed era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos** è stato chiamato per il  *StatementHandle* e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima che sono stati inviati dati per tutti i parametri data-at-execution o colonne.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY092|Tipo di opzione non compreso nell'intervallo|(DM) il valore specificato per l'argomento *opzione* non era:<br /><br /> SQL_CLOSE SQL_DROP SQL_UNBIND SQL_RESET_PARAMS|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|Il driver (DM) associato il *StatementHandle* non supporta la funzione.|  
  
## <a name="comments"></a>Commenti  
 La chiamata **SQLFreeStmt** con il SQL_CLOSE opzione è equivalente alla chiamata **SQLCloseCursor**, ad eccezione del fatto che **SQLFreeStmt** con SQL_CLOSE non influenza l'applicazione Se nessun tipo di cursore è aperto nell'istruzione. Se nessun cursore è aperto, una chiamata a **SQLCloseCursor** restituisce SQLSTATE 24000 (stato del cursore non valido).  
  
 Un'applicazione non deve utilizzare un handle di istruzione dopo che è stato liberato; Gestione Driver non verifica la validità di un handle di una chiamata di funzione.  
  
## <a name="example"></a>Esempio  
 È una buona norma di programmazione per liberare l'handle. Tuttavia, per semplicità, l'esempio seguente non include codice che libera allocato handle. Per un esempio di come liberare l'handle, vedere [SQLFreeHandle-funzione](../../../odbc/reference/syntax/sqlfreehandle-function.md).  
  
```  
// SQLFreeStmt.cpp  
// compile with: user32.lib odbc32.lib  
#include <windows.h>  
#include <sqlext.h>  
  
int main() {  
   // declare and initialize the environment, connection, statement handles  
   SQLHENV henv = NULL;   // Environment     
   SQLHDBC hdbc = NULL;   // Connection handle  
   SQLHSTMT hstmt = NULL;   // Statement handle  
  
   SQLRETURN retCode;  
   HWND desktopHandle = GetDesktopWindow();   // desktop's window handle  
   SQLCHAR connStrbuffer[1024];  
   SQLSMALLINT connStrBufferLen;  
   retCode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retCode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (void*)SQL_OV_ODBC3, -1);  
   retCode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
   retCode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)10, 0);  
   retCode = SQLDriverConnect(hdbc, desktopHandle, (SQLCHAR *)"Driver={SQL Server}", SQL_NTS, connStrbuffer, 1024 + 1, &connStrBufferLen, SQL_DRIVER_PROMPT);  
   retCode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
   retCode = SQLFreeStmt(hstmt, SQL_CLOSE);  
   retCode = SQLFreeStmt(hstmt, SQL_UNBIND);  
   retCode = SQLFreeStmt(hstmt, SQL_RESET_PARAMS);  
}  
```  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Allocazione di un handle|[Funzione SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|L'elaborazione di istruzione di annullamento|[Funzione SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Chiusura di un cursore|[Funzione SQLCloseCursor](../../../odbc/reference/syntax/sqlclosecursor-function.md)|  
|Liberare un handle|[Funzione SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|Impostazione di un nome di cursore|[Funzione SQLSetCursorName](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
