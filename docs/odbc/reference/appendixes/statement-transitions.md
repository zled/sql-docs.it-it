---
title: Istruzione transizioni | Documenti Microsoft
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
- transitioning states [ODBC], statement
- state transitions [ODBC], statement
- statement transitions [ODBC]
ms.assetid: 3d70e0e3-fe83-4b4d-beac-42c82495a05b
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5f20ec0efb42e877695c44f4d62c4ffc1ae79806
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="statement-transitions"></a>Transizioni di istruzione
Le istruzioni ODBC presentano gli stati seguenti.  
  
|State|Description|  
|-----------|-----------------|  
|S0|Istruzione non allocato. (Lo stato di connessione deve essere C4, C5 o C6. Per ulteriori informazioni, vedere [connessione transizioni](../../../odbc/reference/appendixes/connection-transitions.md).)|  
|S1|Istruzione allocato.|  
|S2|Istruzione preparata. Non verrà creato alcun set di risultati.|  
|S3|Istruzione preparata. Verrà creato un set di risultati (eventualmente vuota).|  
|S4|È stato creato alcun set di risultati e di istruzione eseguita.|  
|S5|È stato creato un set di risultati (eventualmente vuota) e di istruzione eseguita. Il cursore è aperta e posizionata prima della prima riga del set di risultati.|  
|S6|Cursore posizionato con **SQLFetch** o **SQLFetchScroll**.|  
|S7|Cursore posizionato con **SQLExtendedFetch**.|  
|S8|Funzione necessita di dati. **SQLParamData** non è stato chiamato.|  
|S9|Funzione necessita di dati. **SQLPutData** non è stato chiamato.|  
|S10|Funzione necessita di dati. **SQLPutData** è stato chiamato.|  
|S11|Ancora in esecuzione. Un'istruzione rimane in questo stato dopo la restituzione di una funzione che viene eseguita in modo asincrono SQL_STILL_EXECUTING. Un'istruzione è temporaneamente in questo stato durante qualsiasi funzione che accetta che un handle di istruzione è in esecuzione. Residenza temporaneo in stato S11 non viene visualizzato in tutte le tabelle di stato, ad eccezione per la tabella di stato **SQLCancel**. Mentre un'istruzione è temporaneamente in stato S11, la funzione può essere annullata chiamando **SQLCancel** da un altro thread.|  
|S12|L'esecuzione asincrona annullata. In S12, un'applicazione deve chiamare la funzione annullata fino a quando non viene restituito un valore diverso da SQL_STILL_EXECUTING. La funzione è stata annullata correttamente solo se la funzione restituisce SQL_ERROR e SQLSTATE HY008 (operazione annullata). Se viene restituito qualsiasi altro valore, ad esempio SQL_SUCCESS, l'operazione di annullamento non riuscito e la funzione eseguita normalmente.|  
  
 Stati S2 e S3 sono noti come stati preparati, stati S5 tramite S7 quando il cursore stati, stati S8 tramite S10 come stati dei dati è necessario e stati S11 e S12 come gli stati asincroni. In ognuno di questi gruppi, le transizioni vengono visualizzate separatamente solo quando sono diversi per ogni stato del gruppo; Nella maggior parte dei casi, le transizioni per ogni stato in ogni un gruppo sono gli stessi.  
  
 Le tabelle seguenti illustrano come ogni funzione ODBC influisce sullo stato istruzione.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--[1], [5], [6]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
|--[2], [5]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
|S1 [3]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
|--[4], [5]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
  
 [1] questa riga vengono mostrate le transizioni quando *HandleType* è stato impostato su SQL_HANDLE_ENV.  
  
 [2] questa riga vengono mostrate le transizioni quando *HandleType* è stato impostato su SQL_HANDLE_DBC.  
  
 [3] questa riga vengono mostrate le transizioni quando *HandleType* è stato impostato su SQL_HANDLE_STMT.  
  
 [4] questa riga vengono mostrate le transizioni quando *HandleType* stato SQL_HANDLE_DESC.  
  
 [5] la chiamata di **SQLAllocHandle** con *OutputHandlePtr* che punta a un handle valido sovrascrive tale handle senza tener conto per il contenuto precedente a quella di gestire e potrebbe causare problemi per i driver ODBC. Si tratta di programmazione di applicazioni ODBC non corretta per chiamare **SQLAllocHandle** due volte con la stessa variabile di applicazione definita per  *\*OutputHandlePtr* senza chiamare  **SQLFreeHandle** per liberare l'handle prima di riallocazione. Sovrascrittura ODBC gestisce in modo potrebbero causare un comportamento incoerente o errori da parte di driver ODBC.  
  
## <a name="sqlbindcol"></a>SQLBindCol  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|QUALI|--|--|--|--|HY010|HY010|  
  
## <a name="sqlbindparameter"></a>SQLBindParameter  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|QUALI|--|--|--|--|HY010|HY010|  
  
## <a name="sqlbrowseconnect-sqlconnect-and-sqldriverconnect"></a>SQLBrowseConnect SQLConnect e SQLDriverConnect  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|08002|08002|08002|08002|08002|08002|08002|  
  
## <a name="sqlbulkoperations"></a>SQLBulkOperations  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|QUALI|HY010|HY010|24000|Vedere la tabella successiva|HY010|O HY010 NS [c]|  
  
## <a name="sqlbulkoperations-cursor-states"></a>SQLBulkOperations (cursore stati)  
  
|S5<br /><br /> Aperto|S6<br /><br /> SQLFetch o SQLFetchScroll|S7<br /><br /> SQLExtendedFetch.|  
|-------------------|---------------------------------------|-----------------------------|  
|-S8 [s] [d] S11 [x]|-S8 [s] [d] S11 [x]|HY010|  
  
## <a name="sqlcancel"></a>SQLCancel  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|QUALI|--|--|--|--|S1 [1] S2 [nr] e [2] [r] S3 e S5 [2] [3] e [5] S6 ([3] o [4]) e S7 [6] [4] e [7]|Vedere la tabella successiva|  
  
 [1] **SQLExecDirect** restituito SQL_NEED_DATA.  
  
 [2] **SQLExecute** restituito SQL_NEED_DATA.  
  
 [3] **SQLBulkOperations** restituito SQL_NEED_DATA.  
  
 [4] **SQLSetPos** restituito SQL_NEED_DATA.  
  
 [5] **SQLFetch**, **SQLFetchScroll**, o **SQLExtendedFetch** non è stato chiamato.  
  
 [6] **SQLFetch** o **SQLFetchScroll** fosse stata chiamata.  
  
 [7] **SQLExtendedFetch** fosse stata chiamata.  
  
## <a name="sqlcancel-asynchronous-states"></a>SQLCancel (Stati asincroni)  
  
|S11<br /><br /> Ancora in esecuzione|S12<br /><br /> Asincrona annullata|  
|-----------------------------|-----------------------------|  
|S12 NS [1] [2]|S12|  
  
 [1] l'istruzione è stata temporaneamente nello stato S11 durante l'esecuzione di una funzione. **SQLCancel** è stato chiamato da un altro thread.  
  
 [2] l'istruzione si trovava nello stato S11 perché una funzione chiamata in modo asincrono restituito SQL_STILL_EXECUTING.  
  
## <a name="sqlclosecursor"></a>SQLCloseCursor  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|QUALI|24000|24000|24000|S1 S3 [np] [p]|HY010|HY010|  
  
## <a name="sqlcolattribute"></a>SQLColAttribute  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|QUALI|HY010|Vedere la tabella successiva|24000|-[s] S11 [x]|HY010|O HY010 NS [c]|  
  
## <a name="sqlcolattribute-prepared-states"></a>SQLColAttribute (preparati stati)  
  
|S2<br /><br /> Nessun risultato|S3<br /><br /> Risultati|  
|-----------------------|--------------------|  
|--[1] 07005[2]|-[s] S11 x|  
  
 [1] *FieldIdentifier* stato SQL_DESC_COUNT.  
  
 [2] *FieldIdentifier* SQL_DESC_COUNT non è stato.  
  
## <a name="sqlcolumnprivileges-sqlcolumns-sqlforeignkeys-sqlgettypeinfo-sqlprimarykeys-sqlprocedurecolumns-sqlprocedures-sqlspecialcolumns-sqlstatistics-sqltableprivileges-and-sqltables"></a>SQLColumnPrivileges, SQLColumns, SQLForeignKeys, SQLGetTypeInfo, SQLPrimaryKeys, SQLProcedureColumns, SQLProcedures, SQLSpecialColumns, SQLStatistics, SQLTablePrivileges e SQLTables  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(IH)|S5 [s] S11 [x]|S1 S5 [e] [s] S11 [x]|S1 [e] e [1] S5 [s] e [1] S11 [x] e [1] 24000 [2]|Vedere la tabella successiva|HY010|O HY010 NS [c]|  
  
 [1] il risultato corrente è l'ultima o un solo risultato o nessun risultato corrente. Per ulteriori informazioni sui più risultati, vedere [più risultati](../../../odbc/reference/develop-app/multiple-results.md).  
  
 [2] il risultato corrente non è l'ultimo risultato.  
  
## <a name="sqlcolumnprivileges-sqlcolumns-sqlforeignkeys-sqlgettypeinfo-sqlprimarykeys-sqlprocedurecolumns-sqlprocedures-sqlspecialcolumns-sqlstatistics-sqltableprivileges-and-sqltables-cursor-states"></a>SQLColumnPrivileges, SQLColumns, SQLForeignKeys, SQLGetTypeInfo, SQLPrimaryKeys, SQLProcedureColumns, SQLProcedures, SQLSpecialColumns, SQLStatistics, SQLTablePrivileges e SQLTables (cursore stati)  
  
|S5<br /><br /> Aperto|S6<br /><br /> SQLFetch o SQLFetchScroll|S7<br /><br /> SQLExtendedFetch.|  
|-------------------|---------------------------------------|-----------------------------|  
|24000|24000[1]|24000|  
  
 [1] questo errore viene restituito da Gestione Driver se **SQLFetch** o **SQLFetchScroll** non è stato restituito SQL_NO_DATA e viene restituito dal driver se **SQLFetch** o **SQLFetchScroll** ha restituito SQL_NO_DATA.  
  
## <a name="sqlcopydesc"></a>SQLCopyDesc  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|QUALI [1]|--|--|--|--|HY010|NS [c] e [3] HY010 [o] o [4]|  
|QUALI [2]|HY010|Vedere la tabella successiva|24000|-[s] S11 x|HY010|NS [c] e [3] HY010 [o] o [4]|  
  
 [1] questa riga vengono mostrate le transizioni quando il *SourceDescHandle* argomento è stato un ARD, APD o IPD.  
  
 [2] questa riga vengono mostrate le transizioni quando il *SourceDescHandle* argomento è un'implementazione.  
  
 [3] di *SourceDescHandle* e *TargetDescHandle* gli argomenti sono uguali a quelle di **SQLCopyDesc** funzione che esegue in modo asincrono.  
  
 [4] sia il *SourceDescHandle* argomento o *TargetDescHandle* argomento (o entrambi) sono stati diversi da quello nel **SQLCopyDesc** funzione è in esecuzione in modo asincrono.  
  
## <a name="sqlcopydesc-prepared-states"></a>SQLCopyDesc (preparati stati)  
  
|S2<br /><br /> Nessun risultato|S3<br /><br /> Risultati|  
|-----------------------|--------------------|  
|24000[1]|-[s] S11 [x]|  
  
 [1] Questa riga vengono mostrate le transizioni quando il *SourceDescHandle* argomento è un'implementazione.  
  
## <a name="sqldatasources-and-sqldrivers"></a>SQLDataSources e SQLDrivers  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqldescribecol"></a>SQLDescribeCol  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|QUALI|HY010|Vedere la tabella successiva|24000|-[s] S11 [x]|HY010|O HY010 NS [c]|  
  
## <a name="sqldescribecol-prepared-states"></a>SQLDescribeCol (preparati stati)  
  
|S2<br /><br /> Nessun risultato|S3<br /><br /> Risultati|  
|-----------------------|--------------------|  
|07005|-[s] S11 [x]|  
  
## <a name="sqldescribeparam"></a>SQLDescribeParam  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|QUALI|HY010|-[s] S11 [x]|HY010|HY010|HY010|HY010 NS [c] [o]|  
  
## <a name="sqldisconnect"></a>SQLDisconnect  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--[1]|S0 [1]|S0 [1]|S0 [1]|S0 [1]|(HY010)|(HY010)|  
  
 [1]. chiamata **SQLDisconnect** libera tutte le istruzioni associate alla connessione. Inoltre, viene restituito lo stato di connessione a C2; lo stato di connessione deve essere C4 prima che lo stato di istruzione è S0.  
  
## <a name="sqlendtran"></a>SQLEndTran  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|: [2] o [3] S1 [1]|: [3] [np] S1 e ([1] o [2]) S1 [p] e [1] S2 [p] e [2]|: [3] [np] S1 e ([1] o [2]) S1 [p] e [1] S3 [p] e [2]|(HY010)|(HY010)|  
  
 [1] di *CompletionType* argomento è SQL_COMMIT e **SQLGetInfo** restituisce SQL_CB_DELETE per il tipo di informazioni SQL_CURSOR_COMMIT_BEHAVIOR o *CompletionType*argomento è SQL_ROLLBACK e **SQLGetInfo** restituisce SQL_CB_DELETE per il tipo di informazioni SQL_CURSOR_ROLLBACK_BEHAVIOR.  
  
 [2] di *CompletionType* argomento è SQL_COMMIT e **SQLGetInfo** restituisce SQL_CB_CLOSE per il tipo di informazioni SQL_CURSOR_COMMIT_BEHAVIOR o *CompletionType*argomento è SQL_ROLLBACK e **SQLGetInfo** restituisce SQL_CB_CLOSE per il tipo di informazioni SQL_CURSOR_ROLLBACK_BEHAVIOR.  
  
 [3] di *CompletionType* argomento è SQL_COMMIT e **SQLGetInfo** restituisce SQL_CB_PRESERVE per il tipo di informazioni SQL_CURSOR_COMMIT_BEHAVIOR o *CompletionType*argomento è SQL_ROLLBACK e **SQLGetInfo** restituisce SQL_CB_PRESERVE per il tipo di informazioni SQL_CURSOR_ROLLBACK_BEHAVIOR.  
  
## <a name="sqlexecdirect"></a>SQLExecDirect  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(IH)|S4 [s] e [nr] S5 [s] e [r] S11 S8 [d] [x]|-[e] e [1] S1 [e] e [2] S4 [s] e [nr] S5 [s] e [r] S11 S8 [d] [x]|-[e], [1], [3] S1 e [e], [2], S4 [3] [s] e [nr,] e [3] S5 [s], [r], S8 [3] e [d] e [3] S11 [x] e [3] 24000 [4]|Vedere la tabella successiva|HY010|HY010 NS [c] [o]|  
  
 [1] errore è stato restituito da Gestione Driver.  
  
 [2] errore non è stato restituito da Gestione Driver.  
  
 [3] è il risultato corrente è l'ultima o un solo risultato o nessun risultato corrente. Per ulteriori informazioni sui più risultati, vedere [più risultati](../../../odbc/reference/develop-app/multiple-results.md).  
  
 [4] il risultato corrente non è l'ultimo risultato.  
  
## <a name="sqlexecdirect-cursor-states"></a>SQLExecDirect (cursore stati)  
  
|S5<br /><br /> Aperto|S6<br /><br /> SQLFetch o SQLFetchScroll|S7<br /><br /> SQLExtendedFetch.|  
|-------------------|---------------------------------------|-----------------------------|  
|24000|24000 [1]|24000|  
  
 [1] questo errore viene restituito da Gestione Driver se **SQLFetch** o **SQLFetchScroll** non è stato restituito SQL_NO_DATA e viene restituito dal driver se **SQLFetch** o  **SQLFetchScroll** ha restituito SQL_NO_DATA.  
  
## <a name="sqlexecute"></a>SQLExecute  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(IH)|(HY010)|Vedere la tabella successiva|S2 [e], p e [1] S4 [s], [p], [nr,] e [1] S5 [s], [p], [r] e S8 [d] [p], [1] e [1] S11 [x], [p] e [1] 24000 [p] e [2] HY010 [np]|Vedere la tabella degli stati di cursore|HY010|HY010 NS [c] [o]|  
  
 [1] il risultato corrente è l'ultima o un solo risultato o nessun risultato corrente. Per ulteriori informazioni sui più risultati, vedere [più risultati](../../../odbc/reference/develop-app/multiple-results.md).  
  
 [2] il risultato corrente non è l'ultimo risultato.  
  
## <a name="sqlexecute-prepared-states"></a>SQLExecute (preparati stati)  
  
|S2<br /><br /> Nessun risultato|S3<br /><br /> Risultati|  
|-----------------------|--------------------|  
|S4 [s] S11 S8 [d] [x]|S5 [s] S11 S8 [d] [x]|  
  
## <a name="sqlexecute-cursor-states"></a>SQLExecute (cursore stati)  
  
|S5<br /><br /> Aperto|S6<br /><br /> SQLFetch o SQLFetchScroll|S7<br /><br /> SQLExtendedFetch.|  
|-------------------|---------------------------------------|-----------------------------|  
|24000 HY010 [p] [np]|24000 [p], [1] HY010 [np]|24000 HY010 [p] [np]|  
  
 [1] questo errore viene restituito da Gestione Driver se **SQLFetch** o **SQLFetchScroll** non è stato restituito SQL_NO_DATA e viene restituito dal driver se **SQLFetch** o  **SQLFetchScroll** ha restituito SQL_NO_DATA.  
  
## <a name="sqlextendedfetch"></a>SQLExtendedFetch.  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|QUALI|S1010|S1010|24000|Vedere la tabella successiva|S1010|S1010 NS [c] [o]|  
  
## <a name="sqlextendedfetch-cursor-states"></a>SQLExtendedFetch (cursore stati)  
  
|S5<br /><br /> Aperto|S6<br /><br /> SQLFetch o SQLFetchScroll|S7<br /><br /> SQLExtendedFetch.|  
|-------------------|---------------------------------------|-----------------------------|  
|S7 [s] o [nf] S11 [x]|S1010|-[s] o [nf] S11 [x]|  
  
## <a name="sqlfetch-and-sqlfetchscroll"></a>SQLFetch e SQLFetchScroll  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|QUALI|HY010|HY010|24000|Vedere la tabella successiva|HY010|HY010 NS [c] [o]|  
  
## <a name="sqlfetch-and-sqlfetchscroll-cursor-states"></a>SQLFetch e SQLFetchScroll (Stati cursore)  
  
|S5<br /><br /> Aperto|S6<br /><br /> SQLFetch o SQLFetchScroll|S7<br /><br /> SQLExtendedFetch.|  
|-------------------|---------------------------------------|-----------------------------|  
|S6 [s] o [nf] S11 [x]|-[s] o [nf] S11 [x]|HY010|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|-- [1]|HY010|HY010|HY010|HY010|HY010|HY010|  
|QUALI [2]|S0|S0|S0|S0|HY010|HY010|  
|-- [3]|--|--|--|--|--|--|  
  
 [1] questa riga vengono mostrate le transizioni quando *HandleType* è stato impostato su SQL_HANDLE_ENV o impostato su SQL_HANDLE_DBC.  
  
 [2] questa riga vengono mostrate le transizioni quando *HandleType* è stato impostato su SQL_HANDLE_STMT.  
  
 [3] questa riga vengono mostrate le transizioni quando *HandleType* era SQL_HANDLE_DESC e il descrittore è stato allocato in modo esplicito.  
  
## <a name="sqlfreestmt"></a>SQLFreeStmt  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|QUALI [1]|--|--|S1 S2 [np] [p]|S1 S3 [np] [p]|HY010|HY010|  
|QUALI [2]|--|--|--|--|HY010|HY010|  
  
 [1] questa riga vengono mostrate le transizioni quando *opzione* stato SQL_CLOSE.  
  
 [2] questa riga vengono mostrate le transizioni quando *opzione* era SQL_UNBIND o SQL_RESET_PARAMS. Se il *opzione* argomento è stato SQL_DROP e il driver sottostante è un'applicazione ODBC 3*x* driver, Driver Manager esegue il mapping a una chiamata a **SQLFreeHandle** con  *HandleType* impostato su SQL_HANDLE_STMT come. Per ulteriori informazioni, vedere la tabella di transizione per [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md).  
  
## <a name="sqlgetconnectattr"></a>SQLGetConnectAttr  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlgetcursorname"></a>SQLGetCursorName  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|QUALI|--|--|--|--|HY010|HY010|  
  
## <a name="sqlgetdata"></a>SQLGetData  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|QUALI|HY010|HY010|24000|Vedere la tabella successiva|HY010|HY010 NS [c] [o]|  
  
## <a name="sqlgetdata-cursor-states"></a>SQLGetData (cursore stati)  
  
|S5<br /><br /> Aperto|S6<br /><br /> SQLFetch o SQLFetchScroll|S7<br /><br /> SQLExtendedFetch.|  
|-------------------|---------------------------------------|-----------------------------|  
|24000|-[s] o [nf] S11 [24000 [b] HY109 x] [i]|-[s] o [nf] S11 [24000 [b] HY109 x] [i]|  
  
## <a name="sqlgetdescfield-and-sqlgetdescrec"></a>SQLGetDescField e SQLGetDescRec  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|QUALI|-[1] o [2] [3] HY010|Vedere la tabella successiva|-[1] o 24000 [2] [3]|-[1], [2], o S11 [3] [3] e [x]|HY010|NS [c] o [4] HY010 [o] e [5]|  
  
 [1] di *DescriptorHandle* argomento è un APD o ARD.  
  
 [2] di *DescriptorHandle* argomento è un IPD.  
  
 [3] di *DescriptorHandle* argomento è un'implementazione.  
  
 [4] di *DescriptorHandle* argomento è lo stesso come il *DescriptorHandle* argomento nel **SQLGetDescField** o **SQLGetDescRec** funzione che esegue in modo asincrono.  
  
 [5] di *DescriptorHandle* argomento è diverso da quello di *DescriptorHandle* argomento in di **SQLGetDescField** o **SQLGetDescRec**funzione che esegue in modo asincrono.  
  
## <a name="sqlgetdescfield-and-sqlgetdescrec-prepared-states"></a>SQLGetDescField e SQLGetDescRec (preparati stati)  
  
|S2<br /><br /> Nessun risultato|S3<br /><br /> Risultati|  
|-----------------------|--------------------|  
|-[1], [2] o [3] S11 [2] e [x]|-[1], [2] o [3] S11 [x]|  
  
 [1] di *DescriptorHandle* argomento è un APD o ARD.  
  
 [2] di *DescriptorHandle* argomento è un IPD.  
  
 [3] di *DescriptorHandle* argomento è un'implementazione. Si noti che queste funzioni restituiscono sempre SQL_NO_DATA nello stato S2 quando *DescriptorHandle* è un'implementazione.  
  
## <a name="sqlgetdiagfield-and-sqlgetdiagrec"></a>SQLGetDiagField e SQLGetDiagRec  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--[1]|--|--|--|--|--|--|  
|QUALI [2]|--[3]|--[3]|--|--|--[3]|--[3]|  
  
 [1] questa riga vengono mostrate le transizioni quando *HandleType* era impostato su SQL_HANDLE_ENV, impostato su SQL_HANDLE_DBC o SQL_HANDLE_DESC.  
  
 [2] questa riga vengono mostrate le transizioni quando *HandleType* è stato impostato su SQL_HANDLE_STMT.  
  
 [3] **SQLGetDiagField** sempre restituito un errore in questo stato quando *DiagIdentifier* è SQL_DIAG_ROW_COUNT.  
  
## <a name="sqlgetenvattr"></a>SQLGetEnvAttr  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlgetfunctions"></a>SQLGetFunctions  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlgetinfo"></a>SQLGetInfo  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlgetstmtattr"></a>SQLGetStmtAttr  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|QUALI|--[1] 24000[2]|--[1] 24000[2]|--[1] 24000[2]|Vedere la tabella successiva|HY010|HY010|  
  
 [1] l'attributo di istruzione non SQL_ATTR_ROW_NUMBER.  
  
 [2] l'attributo di istruzione è stata SQL_ATTR_ROW_NUMBER.  
  
## <a name="sqlgetstmtattr-cursor-states"></a>SQLGetStmtAttr (cursore stati)  
  
|S5<br /><br /> Aperto|S6<br /><br /> SQLFetch o SQLFetchScroll|S7<br /><br /> SQLExtendedFetch.|  
|-------------------|---------------------------------------|-----------------------------|  
|--[1] 24000[2]|-[1] o ([v] e [2]) 24000 [b] e [2] HY109 [i] e [2]|-[i] o ([v] e [2]) 24000 [b] e [2] HY109 [1] e [2]|  
  
 [1] di *attributo* argomento non SQL_ATTR_ROW_NUMBER.  
  
 [2] di *attributo* argomento era SQL_ATTR_ROW_NUMBER.  
  
## <a name="sqlmoreresults"></a>SQLMoreResults  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(IH)|--[1]|--[1]|-[s] e [2] S1 [nf], [np], [4] S2 e [nf], [p], [4] S5 e [s] e [3] S11 [x]|S1 [nf], [np], [4] S3 e [nf], [p] e [4] S4 [s] e [2] S5 [s] e [3] S11 [x]|HY010|HY010 NS [c] [o]|  
  
 [1] la funzione restituisce sempre SQL_NO_DATA in questo stato.  
  
 [2] il risultato successivo è un numero di righe.  
  
 [3] è il risultato successivo è un set di risultati.  
  
 [4] il risultato corrente è l'ultimo risultato.  
  
## <a name="sqlnativesql"></a>SQLNativeSql  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlnumparams"></a>SQLNumParams  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|QUALI|HY010|-[s] S11 [x]|-[s] S11 [x]|-[s] S11 [x]|HY010|HY010 NS [c] [o]|  
  
## <a name="sqlnumresultcols"></a>SQLNumResultCols  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|QUALI|HY010|-[s] S11 [x]|-[s] S11 [x]|-[s] S11 [x]|HY010|HY010 NS [c] [o]|  
  
## <a name="sqlparamdata"></a>SQLParamData  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|QUALI|HY010|HY010|HY010|HY010|Vedere la tabella successiva|HY010 NS [c] [o]|  
  
## <a name="sqlparamdata-need-data-states"></a>SQLParamData (necessario Data stati)  
  
|S8<br /><br /> Dati necessari|S9<br /><br /> Deve essere inserito|S10<br /><br /> Possibile inserire|  
|----------------------|---------------------|---------------------|  
|S1 [e] e [1] S2 [e], [nr] e S3 [2] [e], [r], [2] S5 e [e] [4] S6 e [e] e [5] S7 [e] e S9 [3] [d] S11 [x]|HY010|S1 [e] e [1] S2 [e], [nr,] e S3 [2] [e], [r] e S4 [2] [s], [nr,] e ([1] o [2]) S5 [s], [r], e ([1] o [2]) S5 ([s] o [e]) e S6 [4]\([s] o [e]) e [5] S7 ([s] o [e]) e S9 [3] [d] S11 [x]|  
  
 [1] **SQLExecDirect** restituito SQL_NEED_DATA.  
  
 [2] **SQLExecute** restituito SQL_NEED_DATA.  
  
 [3] **SQLSetPos** era stato chiamato dallo stato S7 e restituito SQL_NEED_DATA.  
  
 [4] **SQLBulkOperations** era stato chiamato dallo stato S5 e restituito SQL_NEED_DATA.  
  
 [5] **SQLSetPos** o **SQLBulkOperations** era stato chiamato dallo stato S6 e restituito SQL_NEED_DATA.  
  
## <a name="sqlprepare"></a>SQLPrepare  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(IH)|S2 [s] e [nr] S3 [s] e [r] S11 [x]|-[s] o ([e] e [1]) S1 [e] e [2] S11 [x]|S1 [e] e [3] S2 [s], [nr,] e [3] S3 [s], [r], [3] S11 e [x] e [3] 24000 [4]|Vedere la tabella successiva|HY010|HY010 NS [c] [o]|  
  
 [1] la preparazione non riesce per una ragione diversa dalla convalida l'istruzione (il valore SQLSTATE è HY009 [valore argomento non valido] o HY090 [stringa di lunghezza o non valida del buffer]).  
  
 [2] la preparazione non riesce durante la convalida dell'istruzione (il valore SQLSTATE non è stato HY009 [valore argomento non valido] o HY090 [stringa di lunghezza o non valida del buffer]).  
  
 [3] è il risultato corrente è l'ultima o un solo risultato o nessun risultato corrente. Per ulteriori informazioni sui più risultati, vedere [più risultati](../../../odbc/reference/develop-app/multiple-results.md).  
  
 [4] il risultato corrente non è l'ultimo risultato.  
  
## <a name="sqlprepare-cursor-states"></a>SQLPrepare (cursore stati)  
  
|S5<br /><br /> Aperto|S6<br /><br /> SQLFetch o SQLFetchScroll|S7<br /><br /> SQLExtendedFetch.|  
|-------------------|---------------------------------------|-----------------------------|  
|24000|24000|24000|  
  
## <a name="sqlputdata"></a>SQLPutData  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|QUALI|HY010|HY010|HY010|HY010|Vedere la tabella successiva|HY010 NS [c] [o]|  
  
## <a name="sqlputdata-need-data-states"></a>SQLPutData (necessario Data stati)  
  
|S8<br /><br /> Dati necessari|S9<br /><br /> Deve essere inserito|S10<br /><br /> Possibile inserire|  
|----------------------|---------------------|---------------------|  
|HY010|S1 [e] e [1] S2 [e], [nr,] e S3 [2] [e], [r] e S5 [2] [e] [4] S6 e [e] e [5] S7 [e] e [3] [s] S11 S10 [x]|-[e] [s] S1 e S2 [1] [e], [nr,] e S3 [2] [e], [r], [2] S5 e [e] e [4] S6 [e] e [5] S7 [e] HY011 S11 [3] [x] e [6]|  
  
 [1] **SQLExecDirect** restituito SQL_NEED_DATA.  
  
 [2] **SQLExecute** restituito SQL_NEED_DATA.  
  
 [3] **SQLSetPos** era stato chiamato dallo stato S7 e restituito SQL_NEED_DATA.  
  
 [4] **SQLBulkOperations** era stato chiamato dallo stato S5 e restituito SQL_NEED_DATA.  
  
 [5] **SQLSetPos** o **SQLBulkOperations** era stato chiamato dallo stato S6 e restituito SQL_NEED_DATA.  
  
 [6] uno o più chiamate a **SQLPutData** per un singolo parametro restituito SQL_SUCCESS, quindi una chiamata a **SQLPutData** è stata effettuata per lo stesso parametro con *StrLen_or_Ind* set su SQL_NULL_DATA.  
  
## <a name="sqlrowcount"></a>SQLRowCount  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(IH)|(HY010)|(HY010)|--|--|(HY010)|(HY010)|  
  
## <a name="sqlsetconnectattr"></a>SQLSetConnectAttr  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--[1]|--|--|--|--[2] 24000[3]|HY010|HY010|  
  
 [1] questa riga vengono mostrate le transizioni quando *attributo* è un attributo di connessione. Per la transizione quando *attributo* è un'istruzione di attributo, vedere la tabella di transizione di istruzione per **SQLSetStmtAttr**.  
  
 [2] di *attributo* argomento non SQL_ATTR_CURRENT_CATALOG.  
  
 [3] di *attributo* argomento era SQL_ATTR_CURRENT_CATALOG.  
  
## <a name="sqlsetcursorname"></a>SQLSetCursorName  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|QUALI|--|--|24000|24000|HY010|HY010|  
  
## <a name="sqlsetdescfield-and-sqlsetdescrec"></a>SQLSetDescField e SQLSetDescRec  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|QUALI [1]|--|--|--|--|HY010|HY010|  
  
 [1] questa riga vengono mostrate le transizioni in cui il *DescriptorHandle* argomento è un ARD, APD, IPD, o (per **SQLSetDescField**) un IRD quando il *FieldIdentifier* argomento è SQL _ DESC_ARRAY_STATUS_PTR o SQL_DESC_ROWS_PROCESSED_PTR. È un errore di chiamare **SQLSetDescField** per un IRD quando *FieldIdentifier* è qualsiasi altro valore.  
  
## <a name="sqlsetenvattr"></a>SQLSetEnvAttr  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|HY011|HY011|HY011|HY011|Y011|HY01|HY011|  
  
## <a name="sqlsetpos"></a>SQLSetPos  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|QUALI|HY010|HY010|24000|Vedere la tabella successiva|HY010|HY010 NS [c] [o]|  
  
## <a name="sqlsetpos-cursor-states"></a>SQLSetPos (cursore stati)  
  
|S5<br /><br /> Aperto|S6<br /><br /> SQLFetch o SQLFetchScroll|S7<br /><br /> SQLExtendedFetch.|  
|-------------------|---------------------------------------|-----------------------------|  
|24000|-[s] [d] S8 S11 [24000 [b] HY109 x] [i]|-[s] [d] S8 S11 [24000 [b] HY109 x] [i]|  
  
## <a name="sqlsetstmtattr"></a>SQLSetStmtAttr  
  
|S0<br /><br /> Non allocato|S1<br /><br /> Allocato|S2 – S3<br /><br /> Prepared|S4<br /><br /> Esecuzione|S5 – S7<br /><br /> Cursore|S8 – S10<br /><br /> Dati necessari|S11 – S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|QUALI|--|-[1] HY011 [2]|--[1] 24000[2]|--[1] 24000[2]|HY010 [np] o [1] HY011 [p] e [2]|HY010 [np] o [1] HY011 [p] e [2]|  
  
 [1] di *attributo* argomento non SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_SIMULATE_CURSOR, SQL_ATTR_USE_BOOKMARKS, SQL_ATTR_CURSOR_SCROLLABLE e SQL_ATTR_CURSOR_SENSITIVITY.  
  
 [2] di *attributo* argomento era SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_SIMULATE_CURSOR, SQL_ATTR_USE_BOOKMARKS, SQL_ATTR_CURSOR_SCROLLABLE e SQL_ATTR_CURSOR_SENSITIVITY.
