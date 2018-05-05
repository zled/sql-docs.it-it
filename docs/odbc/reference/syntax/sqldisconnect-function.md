---
title: Funzione SQLDisconnect | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLDisconnect
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDisconnect
helpviewer_keywords:
- SQLDisconnect function [ODBC]
ms.assetid: 9e84a58e-db48-4821-a0cd-5c711fcbe36b
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b052ba319ad8944e26c23237dd365bc34e57fb73
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqldisconnect-function"></a>Funzione SQLDisconnect
**Conformità**  
 Introdotta: versione ODBC standard 1.0 conformità: 92 ISO  
  
 **Riepilogo**  
 **SQLDisconnect** chiude la connessione associata a un handle di connessione specifica.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLDisconnect(  
     SQLHDBC     ConnectionHandle);  
```  
  
## <a name="arguments"></a>Argomenti  
 *ConnectionHandle*  
 [Input] Handle di connessione.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE o SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLDisconnect** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato possono essere ottenuti chiamando **SQLGetDiagRec** con un *HandleType* di SQL _ HANDLE_DBC e *gestire* di *ConnectionHandle*. Nella tabella seguente sono elencati i valori SQLSTATE comunemente restituiti da **SQLDisconnect** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01002|Errore di disconnessione|Si è verificato un errore durante la disconnessione. Tuttavia, la disconnessione ha avuto esito positivo. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|08003|Connessione non aperta|(DM) la connessione specificata nell'argomento *ConnectionHandle* non è stato aperto.|  
|25000|Stato della transazione non valido|Durante una transazione in corso per la connessione specificata dall'argomento *ConnectionHandle*. La transazione rimane attiva.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel  *\*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver è stato in grado di allocare la memoria necessaria per supportare l'esecuzione o il completamento della funzione.|  
|HY008|Operazione annullata|L'elaborazione asincrona è stata abilitata per il *ConnectionHandle*. È stata chiamata la funzione, e prima che l'esecuzione è stato completato [SQLCancelHandle funzione](../../../odbc/reference/syntax/sqlcancelhandle-function.md) è stato chiamato sul *ConnectionHandle*. Quindi la funzione è stata chiamata nuovamente sul *ConnectionHandle*.<br /><br /> La funzione è stata chiamata e prima di completare l'esecuzione di **SQLCancelHandle** è stato chiamato sul *ConnectionHandle* da un thread diverso in un'applicazione multithread.|  
|HY010|Errore nella sequenza (funzione)|(DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione un *StatementHandle* associato il *ConnectionHandle* ed era ancora in esecuzione quando **SQLDisconnect** stato chiamato.<br /><br /> (DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione (non è presente uno) di *ConnectionHandle* ed era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos** è stato chiamato per un *StatementHandle*  associato il *ConnectionHandle* e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima che sono stati inviati dati per tutti i parametri data-at-execution o colonne.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta, mentre la connessione è ancora attiva. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|Il driver (DM) associato il *ConnectionHandle* non supporta la funzione.|  
|IM017|Polling è disabilitato in modalità di notifica asincrona|Ogni volta che viene utilizzato il modello di notifica, il polling è disabilitato.|  
|IM018|**SQLCompleteAsync** non è stato chiamato per completare l'operazione asincrona precedente su questo handle.|Se la chiamata di funzione precedente dell'handle restituisce SQL_STILL_EXECUTING e se è abilitata la modalità di notifica, **SQLCompleteAsync** deve essere chiamato per l'handle per eseguire la post-elaborazione e completare l'operazione.|  
  
## <a name="comments"></a>Commenti  
 Se un'applicazione chiama **SQLDisconnect** dopo **SQLBrowseConnect** restituisce SQL_NEED_DATA e prima di restituire un codice restituito diverso, il driver Annulla la connessione al processo di esplorazione e restituisce la connessione a uno stato non è connesso.  
  
 Se un'applicazione chiama **SQLDisconnect** mentre è presente una transazione incompleta associata all'handle di connessione, il driver restituisce SQLSTATE 25000 (stato di transazione non valido), che indica che la transazione è invariata e la connessione è aperta. Una transazione incompleta è uno che non è stato eseguito il commit o rollback con **SQLEndTran**.  
  
 Se un'applicazione chiama **SQLDisconnect** prima che è liberata tutte le istruzioni associate alla connessione, il driver, dopo aver completato si disconnette dall'origine dati, libera le istruzioni e tutti i descrittori di cui sono stato allocato in modo esplicito per la connessione. Tuttavia, se uno o più istruzioni associate alla connessione sono ancora in esecuzione in modo asincrono, **SQLDisconnect** restituisce SQL_ERROR con un valore SQLSTATE HY010 (funzione di errore nella sequenza). Inoltre, **SQLDisconnect** consente di liberare le istruzioni di tutti i relativi e tutti i descrittori che sono stati assegnati in modo esplicito per la connessione, se la connessione è in uno stato sospeso o **SQLDisconnect** stato correttamente annullato da **SQLCancelHandle**.  
  
 Per informazioni sull'utilizzo di un'applicazione **SQLDisconnect**, vedere [disconnessione da un'origine dati o il Driver](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
## <a name="disconnecting-from-a-pooled-connection"></a>Disconnessione da una connessione in pool  
 Se il pool di connessioni è abilitato per un ambiente condiviso e un'applicazione chiama **SQLDisconnect** su una connessione in tale ambiente, la connessione viene restituita al pool di connessioni ed è ancora disponibile per altri componenti utilizzando lo stesso ambiente condiviso.  
  
## <a name="code-example"></a>Esempio di codice  
 Vedere [ODBC programma di esempio](../../../odbc/reference/sample-odbc-program.md), [funzione SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md), e [funzione SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Allocazione di un handle|[Funzione SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Connessione a un'origine dati|[Funzione SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Connessione a un'origine dati tramite una connessione stringa o una finestra di dialogo|[Funzione SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Esecuzione di un'operazione di commit o rollback|[Funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|Liberare un handle di connessione|[Funzione SQLFreeConnect](../../../odbc/reference/syntax/sqlfreeconnect-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
