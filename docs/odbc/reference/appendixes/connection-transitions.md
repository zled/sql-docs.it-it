---
title: Le transizioni di connessione | Documenti Microsoft
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
- transitioning states [ODBC], connection
- connection transitions [ODBC]
- state transitions [ODBC], connection
ms.assetid: 6b6e1a47-4a52-41c8-bb9e-7ddeae09913e
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8af5cd175cdd9ab7d96cdb141bcd0a6b6100ea80
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="connection-transitions"></a>Transizioni di connessione
Connessioni ODBC presentano gli stati seguenti.  
  
|State|Description|  
|-----------|-----------------|  
|C0|Ambiente non allocato, non allocato connessione|  
|C1|Ambiente allocato, non allocato connessione|  
|C2|Ambiente di connessione allocato allocato|  
|C3|Funzione di connessione sono necessari dati|  
|C4|Connessione connessi|  
|C5|Connessione, allocata istruzione connesso|  
|C6|Connessione connesso, delle transazioni in corso. È possibile che una connessione sia nello stato C6 senza istruzioni allocate nella connessione. Si supponga, ad esempio, la connessione è in modalità di commit manuale e si trova in stato C4. Se un'istruzione è allocata, eseguita (avvio di una transazione) e quindi liberata, la transazione rimane attiva, ma non sono presenti istruzioni per la connessione.|  
  
 Le tabelle seguenti illustrano come ogni funzione ODBC interessa lo stato di connessione.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|C0<br /><br /> Nessun Env.|C1 non allocato|C2<br /><br /> Allocato|C3<br /><br /> Dati necessari|C4<br /><br /> Connesso|C5<br /><br /> .|C6<br /><br /> Transazione|  
|--------------------|--------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|C1 [1]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
|(QUALI) [2]|C2|--[5]|--[5]|--[5]|--[5]|--[5]|  
|(QUALI) [3]|(QUALI)|(08003)|(08003)|C5|--[5]|--[5]|  
|(QUALI) [4]|(QUALI)|(08003)|(08003)|--[5]|--[5]|--[5]|  
  
 [1] questa riga vengono mostrate le transizioni quando *HandleType* è stato impostato su SQL_HANDLE_ENV.  
  
 [2] questa riga vengono mostrate le transizioni quando *HandleType* è stato impostato su SQL_HANDLE_DBC.  
  
 [3] questa riga vengono mostrate le transizioni quando *HandleType* è stato impostato su SQL_HANDLE_STMT.  
  
 [4] questa riga vengono mostrate le transizioni quando *HandleType* stato SQL_HANDLE_DESC.  
  
 [5] la chiamata di **SQLAllocHandle** con *OutputHandlePtr* che punta a un handle valido sovrascrive tale handle senza tener conto per l'handle di ofthat contenuto precedente e potrebbe causare problemi per i driver ODBC. Si tratta di programmazione di applicazioni ODBC non corretta per chiamare **SQLAllocHandle** due volte con la stessa variabile di applicazione definita per  *\*OutputHandlePtr* senza chiamare  **SQLFreeHandle** per liberare l'handle prima di riallocazione. Sovrascrittura ODBC gestisce in modo possono causare un comportamento incoerente o errori da parte di driver ODBC.  
  
## <a name="sqlbrowseconnect"></a>SQLBrowseConnect  
  
|C0<br /><br /> Nessun Env.|C1<br /><br /> Non allocato|C2<br /><br /> Allocato|C3<br /><br /> Dati necessari|C4<br /><br /> Connesso|C5<br /><br /> .|C6<br /><br /> Transazione|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(QUALI)|(QUALI)|C4 C3 [d] [s]|-[d] [e] C4 C2 [s]|(08002)|(08002)|(08002)|  
  
## <a name="sqlclosecursor"></a>SQLCloseCursor  
  
|C0<br /><br /> Nessun Env.|C1<br /><br /> Non allocato|C2<br /><br /> Allocato|C3<br /><br /> Dati necessari|C4<br /><br /> Connesso|C5<br /><br /> .|C6<br /><br /> Transazione|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(QUALI)|(QUALI)|(QUALI)|(QUALI)|(QUALI)|--|-[1] C5 [2]|  
  
 [1] la connessione è in modalità di commit manuale.  
  
 [2] la connessione è in modalità autocommit.  
  
## <a name="sqlcolumnprivileges-sqlcolumns-sqlforeignkeys-sqlgettypeinfo-sqlprimarykeys-sqlprocedurecolumns-sqlprocedures-sqlspecialcolumns-sqlstatistics-sqltableprivileges-and-sqltables"></a>SQLColumnPrivileges, SQLColumns, SQLForeignKeys, SQLGetTypeInfo, SQLPrimaryKeys, SQLProcedureColumns, SQLProcedures, SQLSpecialColumns, SQLStatistics, SQLTablePrivileges e SQLTables  
  
|C0<br /><br /> Nessun Env.|C1<br /><br /> Non allocato|C2<br /><br /> Allocato|C3<br /><br /> Dati necessari|C4<br /><br /> Connesso|C5<br /><br /> .|C6<br /><br /> Transazione|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(QUALI)|(QUALI)|(QUALI)|(QUALI)|(QUALI)|-[1] C6 [2]|--|  
  
 [1] la connessione è in modalità autocommit o l'origine dati non è iniziato una transazione.  
  
 [2] connessione non è in modalità di commit manuale e l'origine dati ha iniziato una transazione.  
  
## <a name="sqlconnect"></a>SQLConnect  
  
|C0<br /><br /> Nessun Env.|C1<br /><br /> Non allocato|C2<br /><br /> Allocato|C3<br /><br /> Dati necessari|C4<br /><br /> Connesso|C5<br /><br /> .|C6<br /><br /> Transazione|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(QUALI)|(QUALI)|C4|(08002)|(08002)|(08002)|(08002)|  
  
## <a name="sqlcopydesc-sqlgetdescfield-sqlgetdescrec-sqlsetdescfield-and-sqlsetdescrec"></a>SQLCopyDesc, SQLGetDescField, SQLGetDescRec, SQLSetDescField e SQLSetDescRec  
  
|C0<br /><br /> Nessun Env.|C1<br /><br /> Non allocato|C2<br /><br /> Allocato|C3<br /><br /> Dati necessari|C4<br /><br /> Connesso|C5<br /><br /> .|C6<br /><br /> Transazione|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(QUALI)|(QUALI)|(QUALI)|(QUALI)|--[1]|--|--|  
  
 [1] in questo stato, i descrittori soli disponibili per l'applicazione vengono allocati in modo esplicito i descrittori.  
  
## <a name="sqldatasources-and-sqldrivers"></a>SQLDataSources e SQLDrivers  
  
|C0<br /><br /> Nessun Env.|C1<br /><br /> Non allocato|C2<br /><br /> Allocato|C3<br /><br /> Dati necessari|C4<br /><br /> Connesso|C5<br /><br /> .|C6<br /><br /> Transazione|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(QUALI)|--|--|--|--|--|--|  
  
## <a name="sqldisconnect"></a>SQLDisconnect  
  
|C0<br /><br /> Nessun Env.|C1<br /><br /> Non allocato|C2<br /><br /> Allocato|C3<br /><br /> Dati necessari|C4<br /><br /> Connesso|C5<br /><br /> .|C6<br /><br /> Transazione|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(QUALI)|(QUALI)|(08003)|C2|C2|C2|25000|  
  
## <a name="sqldriverconnect"></a>SQLDriverConnect  
  
|C0<br /><br /> Nessun Env.|C1<br /><br /> Non allocato|C2<br /><br /> Allocato|C3<br /><br /> Dati necessari|C4<br /><br /> Connesso|C5<br /><br /> .|C6<br /><br /> Transazione|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(QUALI)|(QUALI)|C4 s n [f]|(08002)|(08002)|(08002)|(08002)|  
  
## <a name="sqlendtran"></a>SQLEndTran  
  
|C0<br /><br /> Nessun Env.|C1<br /><br /> Non allocato|C2<br /><br /> Allocato|C3<br /><br /> Dati necessari|C4<br /><br /> Connesso|C5<br /><br /> .|C6<br /><br /> Transazione|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(QUALI) [1]|--[3]|--[3]|--[3]|--|--|: [4] o ([5], [6] e [8]) C4 [5] e [7] C5 [5], [6] e [9]|  
|(QUALI) [2]|(QUALI)|(08003)|(08003)|--|--|C5|  
  
 [1] questa riga vengono mostrate le transizioni quando *HandleType* è stato impostato su SQL_HANDLE_ENV.  
  
 [2] questa riga vengono mostrate le transizioni quando *HandleType* è stato impostato su SQL_HANDLE_DBC.  
  
 [3] in quanto la connessione non è in uno stato di connessione, e non viene influenzato dalla transazione.  
  
 [4] la connessione non riuscito il commit o rollback. La funzione restituisce SQL_ERROR in questo caso.  
  
 [5] il commit o rollback ha avuto esito positivo per la connessione. La funzione restituisce SQL_ERROR se il commit o il rollback non riuscita in un'altra connessione o la funzione restituisce SQL_SUCCESS se il commit o rollback completata in tutte le connessioni.  
  
 [6] si è verificato almeno un'istruzione allocata nella connessione.  
  
 [7] non esistevano istruzioni allocate nella connessione.  
  
 [8] la connessione ha almeno un'istruzione per il quale si è un cursore aperto, e l'origine dati consente di mantenere i cursori durante il commit o rollback le transazioni, a seconda del valore si applica (a seconda che *CompletionType* stato SQL _ Il COMMIT o SQL_ROLLBACK). Per ulteriori informazioni, vedere gli attributi SQL_CURSOR_COMMIT_BEHAVIOR e SQL_CURSOR_ROLLBACK_BEHAVIOR [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md).  
  
 [9] se la connessione ha tutte le istruzioni per cui sono state i cursori aperti, i cursori non sono stati mantenuti quando è stato eseguito il commit o il rollback della transazione.  
  
## <a name="sqlexecdirect-and-sqlexecute"></a>SQLExecDirect e SQLExecute  
  
|C0<br /><br /> Nessun Env.|C1<br /><br /> Non allocato|C2<br /><br /> Allocato|C3<br /><br /> Dati necessari|C4<br /><br /> Connesso|C5<br /><br /> .|C6<br /><br /> Transazione|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(QUALI)|(QUALI)|(QUALI)|(QUALI)|(QUALI)|-C6 C6 [1] [2] [3]|--|  
  
 [1] la connessione sia in modalità autocommit, e dell'esecuzione dell'istruzione non è un *cursore* *specifica* (ad esempio un'istruzione SELECT); o la connessione è in modalità di commit manuale e l'istruzione esecuzione non è iniziato una transazione.  
  
 [2] la connessione sia in modalità autocommit e dell'esecuzione dell'istruzione è un *cursore* *specifica* (ad esempio un'istruzione SELECT).  
  
 [3] della connessione non è in modalità di commit manuale e l'origine dati ha iniziato una transazione.  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|C0<br /><br /> Nessun Env.|C1<br /><br /> Non allocato|C2<br /><br /> Allocato|C3<br /><br /> Dati necessari|C4<br /><br /> Connesso|C5<br /><br /> .|C6<br /><br /> Transazione|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(QUALI) [1]|C0|(HY010)|(HY010)|(HY010)|(HY010)|(HY010)|  
|(QUALI) [2]|(QUALI)|(C1)|(HY010)|(HY010)|(HY010)|(HY010)|  
|(QUALI) [3]|(QUALI)|(QUALI)|(QUALI)|(QUALI)|C4 [5], [6]|-C4 [7] [5] e [8] C5 [6] e [8]|  
|(QUALI) [4]|(QUALI)|(QUALI)|(QUALI)|--|--|--|  
  
 [1] questa riga vengono mostrate le transizioni quando *HandleType* è stato impostato su SQL_HANDLE_ENV.  
  
 [2] questa riga vengono mostrate le transizioni quando *HandleType* è stato impostato su SQL_HANDLE_DBC.  
  
 [3] questa riga vengono mostrate le transizioni quando *HandleType* è stato impostato su SQL_HANDLE_STMT.  
  
 [4] questa riga vengono mostrate le transizioni quando *HandleType* stato SQL_HANDLE_DESC.  
  
 [5] durante un'unica istruzione allocata nella connessione.  
  
 [6] sono presenti più istruzioni allocate nella connessione.  
  
 [7] la connessione è in modalità di commit manuale.  
  
 [8] la connessione è in modalità autocommit.  
  
## <a name="sqlfreestmt"></a>SQLFreeStmt  
  
|C0<br /><br /> Nessun Env.|C1<br /><br /> Non allocato|C2<br /><br /> Allocato|C3<br /><br /> Dati necessari|C4<br /><br /> Connesso|C5<br /><br /> .|C6<br /><br /> Transazione|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(QUALI) [1]|(QUALI)|(QUALI)|(QUALI)|(QUALI)|--|C5 [3]: [4]|  
|(QUALI) [2]|(QUALI)|(QUALI)|(QUALI)|(QUALI)|--|--|  
  
 [1] questa riga vengono visualizzate le transazioni quando il *opzione* argomento è SQL_CLOSE.  
  
 [2] questa riga vengono visualizzate le transazioni quando il *opzione* argomento è SQL_UNBIND o SQL_RESET_PARAMS.  
  
 [3] della connessione è in modalità di commit automatico e non i cursori sono aperti in tutte le istruzioni, ad eccezione di quello.  
  
 [4] la connessione è in modalità di commit manuale, o di cui si trovava in modalità autocommit e un cursore è stato aperto in almeno un'altra istruzione.  
  
## <a name="sqlgetconnectattr"></a>SQLGetConnectAttr  
  
|C0<br /><br /> Nessun Env.|C1<br /><br /> Non allocato|C2<br /><br /> Allocato|C3<br /><br /> Dati necessari|C4<br /><br /> Connesso|C5<br /><br /> .|C6<br /><br /> Transazione|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|QUALI|QUALI|--[1] 08003[2]|HY010|--|--|--|  
  
 [1] di *attributo* argomento è stato SQL_ATTR_ACCESS_MODE, SQL_ATTR_AUTOCOMMIT, SQL_ATTR_LOGIN_TIMEOUT, SQL_ATTR_ODBC_CURSORS, SQL_ATTR_TRACE o SQL_ATTR_TRACEFILE o fosse stato impostato un valore per l'attributo di connessione.  
  
 [2] di *attributo* argomento non SQL_ATTR_ACCESS_MODE, SQL_ATTR_AUTOCOMMIT, SQL_ATTR_LOGIN_TIMEOUT, SQL_ATTR_ODBC_CURSORS, SQL_ATTR_TRACE o SQL_ATTR_TRACEFILE, e non era stato impostato un valore per la connessione attributo.  
  
## <a name="sqlgetdiagfield-and-sqlgetdiagrec"></a>SQLGetDiagField e SQLGetDiagRec  
  
|C0<br /><br /> Nessun Env.|C1<br /><br /> Non allocato|C2<br /><br /> Allocato|C3<br /><br /> Dati necessari|C4<br /><br /> Connesso|C5<br /><br /> .|C6<br /><br /> Transazione|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(QUALI) [1]|--|--|--|--|--|--|  
|(QUALI) [2]|(QUALI)|--|--|--|--|--|  
|(QUALI) [3]|(QUALI)|(QUALI)|(QUALI)|(QUALI)|--|--|  
|(QUALI) [4]|(QUALI)|(QUALI)|(QUALI)|--|--|--|  
  
 [1] questa riga vengono mostrate le transizioni quando *HandleType* è stato impostato su SQL_HANDLE_ENV.  
  
 [2] questa riga vengono mostrate le transizioni quando *HandleType* è stato impostato su SQL_HANDLE_DBC.  
  
 [3] questa riga vengono mostrate le transizioni quando *HandleType* è stato impostato su SQL_HANDLE_STMT.  
  
 [4] questa riga vengono mostrate le transizioni quando *HandleType* stato SQL_HANDLE_DESC.  
  
## <a name="sqlgetenvattr"></a>SQLGetEnvAttr  
  
|C0<br /><br /> Nessun Env.|C1<br /><br /> Non allocato|C2<br /><br /> Allocato|C3<br /><br /> Dati necessari|C4<br /><br /> Connesso|C5<br /><br /> .|C6<br /><br /> Transazione|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|QUALI|--|--|--|--|--|--|  
  
## <a name="sqlgetfunctions"></a>SQLGetFunctions  
  
|C0<br /><br /> Nessun Env.|C1<br /><br /> Non allocato|C2<br /><br /> Allocato|C3<br /><br /> Dati necessari|C4<br /><br /> Connesso|C5<br /><br /> .|C6<br /><br /> Transazione|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|QUALI|QUALI|HY010|HY010|--|--|--|  
  
## <a name="sqlgetinfo"></a>SQLGetInfo  
  
|C0<br /><br /> Nessun Env.|C1<br /><br /> Non allocato|C2<br /><br /> Allocato|C3<br /><br /> Dati necessari|C4<br /><br /> Connesso|C5<br /><br /> .|C6<br /><br /> Transazione|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|QUALI|QUALI|--[1] 08003[2]|08003|--|--|--|  
  
 [1] di *InfoType* argomento era SQL_ODBC_VER.  
  
 [2] di *InfoType* argomento non SQL_ODBC_VER.  
  
## <a name="sqlmoreresults"></a>SQLMoreResults  
  
|C0<br /><br /> Nessun Env.|C1<br /><br /> Non allocato|C2<br /><br /> Allocato|C3<br /><br /> Dati necessari|C4<br /><br /> Connesso|C5<br /><br /> .|C6<br /><br /> Transazione|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(QUALI)|(QUALI)|(QUALI)|(QUALI)|(QUALI)|-[1] C6 [2]|-C5 [3] [1]|  
  
 [1] la connessione non è in modalità di commit automatico e la chiamata a **SQLMoreResults** l'elaborazione di un set di risultati di una specifica di cursore non è stato inizializzato.  
  
 [2] la connessione non è in modalità di commit automatico e la chiamata a **SQLMoreResults** l'elaborazione di un set di risultati di una specifica di cursore è stato inizializzato.  
  
 [3] della connessione è in modalità di commit manuale.  
  
## <a name="sqlnativesql"></a>SQLNativeSql  
  
|C0<br /><br /> Nessun Env.|C1<br /><br /> Non allocato|C2<br /><br /> Allocato|C3<br /><br /> Dati necessari|C4<br /><br /> Connesso|C5<br /><br /> .|C6<br /><br /> Transazione|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(QUALI)|(QUALI)|(08003)|(08003)|--|--|--|  
  
## <a name="sqlprepare"></a>SQLPrepare  
  
|C0<br /><br /> Nessun Env.|C1<br /><br /> Non allocato|C2<br /><br /> Allocato|C3<br /><br /> Dati necessari|C4<br /><br /> Connesso|C5<br /><br /> .|C6<br /><br /> Transazione|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(QUALI)|(QUALI)|(QUALI)|(QUALI)|(QUALI)|-[1] C6 [2]|--|  
  
 [1] la connessione è in modalità autocommit o l'origine dati non è iniziato una transazione.  
  
 [2] la connessione non è in modalità manuale: commit e l'origine dati ha iniziato una transazione.  
  
## <a name="sqlsetconnectattr"></a>SQLSetConnectAttr  
  
|C0<br /><br /> Nessun Env.|C1<br /><br /> Non allocato|C2<br /><br /> Allocato|C3<br /><br /> Dati necessari|C4<br /><br /> Connesso|C5<br /><br /> .|C6<br /><br /> Transazione|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|QUALI|QUALI|--[1] 08003[2]|HY010|-08002 [3] [4] HY011 [5]|-08002 [3] [4] HY011 [5]|: [3] e [6] C5 [8] 08002 HY011 [4] [5] o [7]|  
  
 [1] di *attributo* argomento non è stata SQL_ATTR_TRANSLATE_LIB o SQL_ATTR_TRANSLATE_OPTION.  
  
 [2] di *attributo* argomento è stato SQL_ATTR_TRANSLATE_LIB o SQL_ATTR_TRANSLATE_OPTION.  
  
 [3] di *attributo* argomento non è stata SQL_ATTR_ODBC_CURSORS o SQL_ATTR_PACKET_SIZE.  
  
 [4] di *attributo* argomento era SQL_ATTR_ODBC_CURSORS.  
  
 [5] di *attributo* argomento è stato SQL_ATTR_PACKET_SIZE.  
  
 [6] di *attributo* argomento non SQL_ATTR_AUTOCOMMIT, o *attributo* argomento era SQL_ATTR_AUTOCOMMIT e l'impostazione di questo attributo non il commit della transazione.  
  
 [7] di *attributo* argomento era SQL_ATTR_TXN_ISOLATION.  
  
 [8] di *attributo* argomento era SQL_ATTR_AUTOCOMMIT e l'impostazione di questo attributo eseguito il commit della transazione.  
  
## <a name="sqlsetenvattr"></a>SQLSetEnvAttr  
  
|C0<br /><br /> Nessun Env.|C1<br /><br /> Non allocato|C2<br /><br /> Allocato|C3<br /><br /> Dati necessari|C4<br /><br /> Connesso|C5<br /><br /> .|C6<br /><br /> Transazione|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(QUALI)|--|--|(HY010)|--|--|--|  
  
## <a name="all-other-odbc-functions"></a>Tutte le altre funzioni ODBC  
  
|C0<br /><br /> Nessun Env.|C1<br /><br /> Non allocato|C2<br /><br /> Allocato|C3<br /><br /> Dati necessari|C4<br /><br /> Connesso|C5<br /><br /> .|C6<br /><br /> Transazione|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(QUALI)|(QUALI)|(QUALI)|(QUALI)|(QUALI)|--|--|

