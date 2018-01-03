---
title: Riferimento all'API ODBC | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apitype: dllExport
ms.assetid: b7a49774-f458-44ce-9a04-a0457501405b
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 025ad811b25f822c22c9ff81402de196b191baa6
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-api-reference"></a>Riferimento all'API ODBC
Gli argomenti in questa sezione descrivono ogni funzione ODBC in ordine alfabetico. Ogni funzione è definita come funzione del linguaggio di programmazione C. Di seguito sono riportate le descrizioni:  
  
-   Scopo  
  
-   Versione ODBC  
  
-   Livello di conformità standard CLI  
  
-   Sintassi  
  
-   Argomenti  
  
-   Valori restituiti  
  
-   Diagnostica  
  
-   Commenti sull'utilizzo e sull'implementazione  
  
-   Esempio di codice  
  
-   Riferimenti a funzioni correlate  
  
 Il livello di conformità standard CLI può essere uno dei seguenti: 92 ISO, Open Group, ODBC o obsoleto. Una funzione contrassegnata come conforme allo standard ISO 92 viene visualizzato anche nella versione 1 di Open Group perché Open Group è un superset puro di ISO 92. Una funzione contrassegnata come conforme a Open gruppo viene visualizzato anche in ODBC 3. *x*, in quanto ODBC 3. *x* è un superset puro di Open Group versione 1. Una funzione contrassegnata come conforme a ODBC viene visualizzato in nessuna delle due standard. Una funzione contrassegnata come deprecata è stata deprecata in ODBC 3. *x*.  
  
 Gestione delle informazioni di diagnostica è descritta nel [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) descrizione della funzione. Il testo associato ai valori SQLSTATE è incluso per fornire una descrizione della condizione, ma non è destinato a prescrivere un testo specifico.  
  
> [!NOTE]  
>  Per informazioni specifiche del driver su funzioni ODBC, vedere la sezione per il driver.  
  
 In questa sezione contiene argomenti per le funzioni seguenti:  
  
-   [Funzione SQLAllocConnect](../../../odbc/reference/syntax/sqlallocconnect-function.md)  
  
-   [Funzione SQLAllocEnv](../../../odbc/reference/syntax/sqlallocenv-function.md)  
  
-   [Funzione SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)  
  
-   [Funzione SQLAllocHandle](../../../odbc/reference/syntax/sqlallocstmt-function.md)  
  
-   [Funzione SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)  
  
-   [Funzione SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)  
  
-   [Funzione SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)  
  
-   [Funzione SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)  
  
-   [Funzione SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)  
  
-   [Funzione SQLCancelHandle](../../../odbc/reference/syntax/sqlcancelhandle-function.md)  
  
-   [Funzione SQLCloseCursor](../../../odbc/reference/syntax/sqlclosecursor-function.md)  
  
-   [Funzione SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)  
  
-   [Funzione SQLColAttributes](../../../odbc/reference/syntax/sqlcolattributes-function.md)  
  
-   [Funzione SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)  
  
-   [Funzione SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)  
  
-   [Funzione SQLCompleteAsync](../../../odbc/reference/syntax/sqlcompleteasync-function.md)  
  
-   [Funzione SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)  
  
-   [Funzione SQLCopyDesc](../../../odbc/reference/syntax/sqlcopydesc-function.md)  
  
-   [Funzione SQLDataSources](../../../odbc/reference/syntax/sqldatasources-function.md)  
  
-   [Funzione SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)  
  
-   [Funzione SQLDescribeParam](../../../odbc/reference/syntax/sqldescribeparam-function.md)  
  
-   [Funzione SQLDisconnect](../../../odbc/reference/syntax/sqldisconnect-function.md)  
  
-   [Funzione SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)  
  
-   [Funzione SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)  
  
-   [Funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)  
  
-   [Funzione SQLError](../../../odbc/reference/syntax/sqlerror-function.md)  
  
-   [Funzione SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)  
  
-   [Funzione SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)  
  
-   [Funzione SQLExtendedFetch](../../../odbc/reference/syntax/sqlextendedfetch-function.md)  
  
-   [Funzione SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)  
  
-   [Funzione SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)  
  
-   [Funzione SQLForeignKeys](../../../odbc/reference/syntax/sqlforeignkeys-function.md)  
  
-   [Funzione SQLFreeConnect](../../../odbc/reference/syntax/sqlfreeconnect-function.md)  
  
-   [Funzione SQLFreeEnv](../../../odbc/reference/syntax/sqlfreeenv-function.md)  
  
-   [Funzione SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)  
  
-   [Funzione SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md)  
  
-   [Funzione SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)  
  
-   [Funzione SQLGetConnectOption](../../../odbc/reference/syntax/sqlgetconnectoption-function.md)  
  
-   [Funzione SQLGetCursorName](../../../odbc/reference/syntax/sqlgetcursorname-function.md)  
  
-   [Funzione SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)  
  
-   [Funzione SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)  
  
-   [Funzione SQLGetDescRec](../../../odbc/reference/syntax/sqlgetdescrec-function.md)  
  
-   [Funzione SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)  
  
-   [Funzione SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)  
  
-   [Funzione SQLGetEnvAttr](../../../odbc/reference/syntax/sqlgetenvattr-function.md)  
  
-   [Funzione SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md)  
  
-   [Funzione SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)  
  
-   [Funzione SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)  
  
-   [Funzione SQLGetStmtOption](../../../odbc/reference/syntax/sqlgetstmtoption-function.md)  
  
-   [Funzione SQLGetTypeInfo](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)  
  
-   [Funzione SQLMoreResults](../../../odbc/reference/syntax/sqlmoreresults-function.md)  
  
-   [Funzione SQLNativeSql](../../../odbc/reference/syntax/sqlnativesql-function.md)  
  
-   [Funzione SQLNumParams](../../../odbc/reference/syntax/sqlnumparams-function.md)  
  
-   [Funzione SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)  
  
-   [Funzione SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md)  
  
-   [Funzione SQLParamOptions](../../../odbc/reference/syntax/sqlparamoptions-function.md)  
  
-   [Funzione SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)  
  
-   [Funzione SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)  
  
-   [Funzione SQLProcedureColumns](../../../odbc/reference/syntax/sqlprocedurecolumns-function.md)  
  
-   [Funzione SQLProcedures](../../../odbc/reference/syntax/sqlprocedures-function.md)  
  
-   [Funzione SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)  
  
-   [Funzione SQLRowCount](../../../odbc/reference/syntax/sqlrowcount-function.md)  
  
-   [Funzione SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)  
  
-   [Funzione SQLSetConnectOption](../../../odbc/reference/syntax/sqlsetconnectoption-function.md)  
  
-   [Funzione SQLSetCursorName](../../../odbc/reference/syntax/sqlsetcursorname-function.md)  
  
-   [Funzione SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)  
  
-   [Funzione SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)  
  
-   [Funzione SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)  
  
-   [Funzione SQLSetParam](../../../odbc/reference/syntax/sqlsetparam-function.md)  
  
-   [Funzione SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)  
  
-   [Funzione SQLSetScrollOptions](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md)  
  
-   [Funzione SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)  
  
-   [Funzione SQLSetStmtOption](../../../odbc/reference/syntax/sqlsetstmtoption-function.md)  
  
-   [Funzione SQLSpecialColumns](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)  
  
-   [Funzione SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)  
  
-   [Funzione SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)  
  
-   [Funzione SQLTables](../../../odbc/reference/syntax/sqltables-function.md)  
  
-   [Funzione SQLTransact](../../../odbc/reference/syntax/sqltransact-function.md)
