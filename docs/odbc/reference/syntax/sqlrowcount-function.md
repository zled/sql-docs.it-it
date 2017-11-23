---
title: Funzione SQLRowCount | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLRowCount
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLRowCount
helpviewer_keywords: SQLRowCount function [ODBC]
ms.assetid: 61e00a8a-9b3b-45b9-b397-7fe818822416
caps.latest.revision: "22"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c46515b464ea694cfa6184072efb95e2459b1d00
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="sqlrowcount-function"></a>SQLRowCount Function
**Conformità**  
 Introdotta: versione ODBC standard 1.0 conformità: 92 ISO  
  
 **Riepilogo**  
 **SQLRowCount** restituisce il numero di righe interessate da un **aggiornamento**, **inserire**, o **eliminare** istruzione; un SQL_ADD, SQL_UPDATE_BY_BOOKMARK o SQL _ Operazione DELETE_BY_BOOKMARK **SQLBulkOperations**; o di un'operazione SQL_UPDATE o SQL_DELETE in **SQLSetPos**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLRowCount(  
      SQLHSTMT   StatementHandle,  
      SQLLEN *   RowCountPtr);  
```  
  
## <a name="arguments"></a>Argomenti  
 *StatementHandle*  
 [Input] Handle di istruzione.  
  
 *RowCountPtr*  
 [Output] Punta a un buffer in cui si desidera restituire un conteggio delle righe. Per **aggiornamento**, **inserire**, e **eliminare** istruzioni, per le operazioni SQL_ADD SQL_UPDATE_BY_BOOKMARK e SQL_DELETE_BY_BOOKMARK  **SQLBulkOperations**e per le operazioni SQL_UPDATE o SQL_DELETE **SQLSetPos**, il valore restituito in **RowCountPtr* è il numero di righe interessate dal richiesta o – 1 se il numero di righe interessate non è disponibile.  
  
 Quando **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, **SQLSetPos o SQLMoreResults** viene chiamato, il SQL_DIAG_ROW_COUNT campo della struttura di dati di diagnostica è impostato per il conteggio delle righe e il conteggio delle righe viene memorizzato nella cache in modo dipendente dall'implementazione. **SQLRowCount** restituisce il valore di numero di riga memorizzata nella cache. Il valore di numero di riga memorizzata nella cache è valido finché l'handle di istruzione viene impostato lo stato allocato o preparato, l'istruzione viene rieseguita, o **SQLCloseCursor** viene chiamato. Si noti che se una funzione è stata chiamata poiché il campo SQL_DIAG_ROW_COUNT è stato impostato, il valore restituito da **SQLRowCount** potrebbe essere diverso dal valore nel campo SQL_DIAG_ROW_COUNT perché il campo SQL_DIAG_ROW_COUNT viene reimpostato su 0 per qualsiasi chiamata di funzione.  
  
 Per altre istruzioni e funzioni, il driver può definire il valore restituito in \* *RowCountPtr*. Ad esempio, alcune origini dati possono essere in grado di restituire il numero di righe restituite da una **selezionare** istruzione o una funzione di catalogo prima di recuperare le righe.  
  
> [!NOTE]  
>  Molte origini dati non possono restituire il numero di righe in un set di risultati prima scaricarle; Per garantire la massima interoperabilità, applicazioni non devono basarsi su questo comportamento.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLRowCount** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato possono essere ottenuti chiamando **SQLGetDiagRec** con un *HandleType* di SQL _ HANDLE_STMT e *gestire* di *StatementHandle*. Nella tabella seguente sono elencati i valori SQLSTATE comunemente restituiti da **SQLRowCount** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel  *\*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver è stato in grado di allocare la memoria necessaria per supportare l'esecuzione o il completamento della funzione.|  
|HY010|Errore nella sequenza (funzione)|(DM) a cui è stata chiamata per l'handle di connessione associata a una funzione in modo asincrono in esecuzione il *StatementHandle*. Questa funzione asincrona era ancora in esecuzione quando il **SQLRowCount** funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** è stato chiamato per il *StatementHandle* e restituito SQL_PARAM_DATA_ È DISPONIBILE. Questa funzione è stata chiamata prima che i dati sono stati recuperati per tutti i parametri con flusso.<br /><br /> (DM) a cui è stata chiamata prima di chiamare la funzione **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos** per il  *StatementHandle*.<br /><br /> (DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione il *StatementHandle* ed era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos** è stato chiamato per il  *StatementHandle* e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima che sono stati inviati dati per tutti i parametri data-at-execution o colonne.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|Il driver (DM) associato il *StatementHandle* non supporta la funzione.|  
  
## <a name="comments"></a>Commenti  
 Se l'ultima istruzione SQL eseguita nell'handle di istruzione non è un **aggiornamento**, **inserire**, o **eliminare** istruzione o se il *operazione* argomento nella chiamata precedente a **SQLBulkOperations** non è stata SQL_ADD, SQL_UPDATE_BY_BOOKMARK o SQL_DELETE_BY_BOOKMARK, o se il *operazione* argomento nella chiamata precedente a  **SQLSetPos** non è stata SQL_UPDATE o SQL_DELETE, il valore di **RowCountPtr* è definito dal driver. Per ulteriori informazioni, vedere [determinare il numero di righe interessate](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md).  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Esecuzione di un'istruzione SQL|[Funzione SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|L'esecuzione di un'istruzione SQL preparata|[Funzione SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
