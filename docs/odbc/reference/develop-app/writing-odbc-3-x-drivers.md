---
title: Scrittura di driver di ODBC 3. x | Documenti Microsoft
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
- upgrading drivers [ODBC]
- ODBC drivers [ODBC], upgrading
- backward compatibility [ODBC], drivers
- compatibility [ODBC], drivers
ms.assetid: 9b75f59b-623f-4711-9ca2-e751b3622e00
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 41ca6ddf1535899ed8e5e0f065cf2f5f0ca19dca
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="writing-odbc-3x-drivers"></a>Driver di scrittura ODBC 3. x
Nella tabella seguente viene illustrato il supporto di funzione in un'applicazione ODBC 3. *x* driver e un'applicazione ODBC e il mapping eseguita da Gestione Driver quando le funzioni vengono chiamate su un'applicazione ODBC 3.* x* driver.  
  
|Funzione|Supportato<br /><br /> da un<br /><br /> ODBC 3. *x*<br /><br /> driver?|Supportato<br /><br /> da un<br /><br /> ODBC 3. *x*<br /><br /> applicazione?|Il mapping supportati<br /><br /> per ODBC 3. *x*<br /><br /> Gestione driver per<br /><br /> un'applicazione ODBC 3. *x* driver?|  
|--------------|----------------------------------------------------|---------------------------------------------------------|---------------------------------------------------------------------------------------------|  
|**SQLAllocConnect**|No|[1]|Sì|  
|**SQLAllocEnv**|No|[1]|Sì|  
|**SQLAllocHandle**|Sì|Sì|No|  
|**SQLAllocStmt**|No|[1]|Sì|  
|**SQLBindCol**|Sì|Sì|No|  
|**SQLBindParam**|No|Sì [2]|Sì|  
|**SQLBindParameter**|Sì|Sì|No|  
|**SQLBrowseConnect**|Sì|Sì|No|  
|**SQLBulkOperations**|Sì|Sì|No|  
|**SQLCancel**|Sì|Sì|No|  
|**SQLCloseCursor**|Sì|Sì|No|  
|**SQLColAttribute**|Sì|Sì|No|  
|**SQLColAttributes**|[3]|No|Sì|  
|**SQLColumnPrivileges**|Sì|Sì|No|  
|**SQLColumns**|Sì|Sì|No|  
|**SQLConnect**|Sì|Sì|No|  
|**SQLCopyDesc**|Sì|Sì|Sì [4]|  
|**SQLDataSources**|No|Sì|Sì|  
|**SQLDescribeCol**|Sì|Sì|No|  
|**SQLDescribeParam**|Sì|Sì|No|  
|**SQLDisconnect**|Sì|Sì|No|  
|**SQLDriverConnect**|Sì|Sì|No|  
|**SQLDrivers**|No|Sì|Sì|  
|**SQLEndTran**|Sì|Sì|No|  
|**SQLError**|No|[1]|Sì|  
|**SQLExecDirect**|Sì|Sì|No|  
|**SQLExecute**|Sì|Sì|No|  
|**SQLExtendedFetch.**|Sì|No|No|  
|**SQLFetch**|Sì|Sì|No|  
|**SQLFetchScroll**|Sì|Sì|No|  
|**SQLForeignKeys**|Sì|Sì|No|  
|**SQLFreeConnect**|No|Sì [1]|Sì|  
|**SQLFreeEnv**|No|Sì [1]|Sì|  
|**SQLFreeHandle**|Sì|Sì|No|  
|**SQLFreeStmt**|Sì|Sì|No|  
|**SQLGetConnectAttr**|Sì|Sì|No|  
|**SQLGetConnectOption**|[5]|[1]|Sì|  
|**SQLGetCursorName**|Sì|Sì|No|  
|**SQLGetData**|Sì|Sì|No|  
|**SQLGetDescField**|Sì|Sì|No|  
|**SQLGetDescRec**|Sì|Sì|No|  
|**SQLGetDiagField**|Sì|Sì|No|  
|**SQLGetDiagRec**|Sì|Sì|No|  
|**SQLGetEnvAttr**|Sì|Sì|No|  
|**SQLGetFunctions**|[6]|Sì|Sì|  
|**SQLGetInfo**|Sì|Sì|No|  
|**SQLGetStmtAttr**|Sì|Sì|No|  
|**SQLGetStmtOption**|[5]|[1]|Sì|  
|**SQLGetTypeInfo**|Sì|Sì|No|  
|**SQLMoreResults**|Sì|Sì|No|  
|**SQLNativeSql**|Sì|Sì|No|  
|**SQLNumParams**|Sì|Sì|No|  
|**SQLNumResultCols**|Sì|Sì|No|  
|**SQLParamData**|Sì|Sì|No|  
|**SQLParamOptions**|No|No|Sì|  
|**SQLPrepare**|Sì|Sì|No|  
|**SQLPrimaryKeys**|Sì|Sì|No|  
|**SQLProcedureColumns**|Sì|Sì|No|  
|**SQLProcedures**|Sì|Sì|No|  
|**SQLPutData**|Sì|Sì|No|  
|**SQLRowCount**|Sì|Sì|No|  
|**Funzione SQLSetConnectAttr**|Sì|Sì|No|  
|**SQLSetConnectOption**|[5]|[1]|Sì|  
|**SQLSetCursorName**|Sì|Sì|No|  
|**SQLSetDescField**|Sì|Sì|No|  
|**SQLSetDescRec**|Sì|Sì|No|  
|**SQLSetEnvAttr**|Sì|Sì|No|  
|**SQLSetPos**|Sì|Sì|No|  
|**SQLSetParam**|No|No|Sì|  
|**SQLSetScrollOption**|Sì|Sì|No|  
|**Funzione SQLSetStmtAttr**|Sì|Sì|No|  
|**SQLSetStmtOption**|[5]|[1]|Sì|  
|**SQLSpecialColumns**|Sì|Sì|No|  
|**SQLStatistics**|Sì|Sì|No|  
|**SQLTablePrivileges**|Sì|Sì|No|  
|**SQLTables**|Sì|Sì|No|  
|**SQLTransact**|No|[1]|Sì|  
  
 [1] questa funzione è deprecata in ODBC 3. *x*. ODBC 3. *x* applicazioni non devono utilizzare questa funzione. Tuttavia, un'applicazione compatibile con ISO CLI o l'Open Group può chiamare questa funzione.  
  
 [2] ODBC 3. *x* le applicazioni devono utilizzare **SQLBindParameter** anziché **SQLBindParam**. Tuttavia, un'applicazione compatibile con ISO CLI o l'Open Group può chiamare questa funzione.  
  
 [3] gli sviluppatori di driver di è opportuno notare che l'API ODBC 2. *x* SQL_COLUMN_PRECISION SQL_COLUMN_SCALE e SQL_COLUMN_LENGTH devono essere supportate con gli attributi di colonna **SQLColAttribute**.  
  
 [4] **SQLCopyDesc** viene implementato da Gestione Driver parzialmente quando vengono copiato un descrittore per le connessioni che appartengono a diversi driver. I driver necessari per supportare **SQLCopyDesc** tra due delle proprie connessioni. Le funzioni come **SQLDrivers**, che vengono implementati esclusivamente da Gestione Driver, non vengono visualizzati nell'elenco.  
  
 [5] in determinate circostanze, i driver potrebbe essere necessario supportare questa funzione. Per ulteriori informazioni, vedere la pagina di riferimento della funzione.  
  
 [6] il driver può scegliere di supportare **SQLGetFunctions** se il set di funzioni supportate dal driver varia da una connessione per connessione.

