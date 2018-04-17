---
title: Scrittura di driver di ODBC 3. x | Documenti Microsoft
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
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 27bdcf1a1254b24c87280fbfc86e4374e277a976
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="writing-odbc-3x-drivers"></a>Driver di scrittura ODBC 3. x
Nella tabella seguente viene illustrato il supporto di funzione in un'applicazione ODBC 3. *x* driver e un'applicazione ODBC e il mapping eseguita da Gestione Driver quando le funzioni vengono chiamate su un'applicazione ODBC 3. *x* driver.  
  
|Funzione|Supported<br /><br /> da un<br /><br /> ODBC 3. *x*<br /><br /> driver?|Supported<br /><br /> da un<br /><br /> ODBC 3. *x*<br /><br /> applicazione?|Il mapping supportati<br /><br /> per ODBC 3. *x*<br /><br /> Gestione driver per<br /><br /> un'applicazione ODBC 3. *x* driver?|  
|--------------|----------------------------------------------------|---------------------------------------------------------|---------------------------------------------------------------------------------------------|  
|**SQLAllocConnect**|no|[1]|Sì|  
|**SQLAllocEnv**|no|[1]|Sì|  
|**SQLAllocHandle**|Sì|Sì|no|  
|**SQLAllocStmt**|no|[1]|Sì|  
|**SQLBindCol**|Sì|Sì|no|  
|**SQLBindParam**|no|Sì [2]|Sì|  
|**SQLBindParameter**|Sì|Sì|no|  
|**SQLBrowseConnect**|Sì|Sì|no|  
|**SQLBulkOperations**|Sì|Sì|no|  
|**SQLCancel**|Sì|Sì|no|  
|**SQLCloseCursor**|Sì|Sì|no|  
|**SQLColAttribute**|Sì|Sì|no|  
|**SQLColAttributes**|[3]|no|Sì|  
|**SQLColumnPrivileges**|Sì|Sì|no|  
|**SQLColumns**|Sì|Sì|no|  
|**SQLConnect**|Sì|Sì|no|  
|**SQLCopyDesc**|Sì|Sì|Sì [4]|  
|**SQLDataSources**|no|Sì|Sì|  
|**SQLDescribeCol**|Sì|Sì|no|  
|**SQLDescribeParam**|Sì|Sì|no|  
|**SQLDisconnect**|Sì|Sì|no|  
|**SQLDriverConnect**|Sì|Sì|no|  
|**SQLDrivers**|no|Sì|Sì|  
|**SQLEndTran**|Sì|Sì|no|  
|**SQLError**|no|[1]|Sì|  
|**SQLExecDirect**|Sì|Sì|no|  
|**SQLExecute**|Sì|Sì|no|  
|**SQLExtendedFetch.**|Sì|No|no|  
|**SQLFetch**|Sì|Sì|no|  
|**SQLFetchScroll**|Sì|Sì|no|  
|**SQLForeignKeys**|Sì|Sì|no|  
|**SQLFreeConnect**|no|Sì [1]|Sì|  
|**SQLFreeEnv**|no|Sì [1]|Sì|  
|**SQLFreeHandle**|Sì|Sì|no|  
|**SQLFreeStmt**|Sì|Sì|no|  
|**SQLGetConnectAttr**|Sì|Sì|no|  
|**SQLGetConnectOption**|[5]|[1]|Sì|  
|**SQLGetCursorName**|Sì|Sì|no|  
|**SQLGetData**|Sì|Sì|no|  
|**SQLGetDescField**|Sì|Sì|no|  
|**SQLGetDescRec**|Sì|Sì|no|  
|**SQLGetDiagField**|Sì|Sì|no|  
|**SQLGetDiagRec**|Sì|Sì|no|  
|**SQLGetEnvAttr**|Sì|Sì|no|  
|**SQLGetFunctions**|[6]|Sì|Sì|  
|**SQLGetInfo**|Sì|Sì|no|  
|**SQLGetStmtAttr**|Sì|Sì|no|  
|**SQLGetStmtOption**|[5]|[1]|Sì|  
|**SQLGetTypeInfo**|Sì|Sì|no|  
|**SQLMoreResults**|Sì|Sì|no|  
|**SQLNativeSql**|Sì|Sì|no|  
|**SQLNumParams**|Sì|Sì|no|  
|**SQLNumResultCols**|Sì|Sì|no|  
|**SQLParamData**|Sì|Sì|no|  
|**SQLParamOptions**|no|No|Sì|  
|**SQLPrepare**|Sì|Sì|no|  
|**SQLPrimaryKeys**|Sì|Sì|no|  
|**SQLProcedureColumns**|Sì|Sì|no|  
|**SQLProcedures**|Sì|Sì|no|  
|**SQLPutData**|Sì|Sì|no|  
|**SQLRowCount**|Sì|Sì|no|  
|**Funzione SQLSetConnectAttr**|Sì|Sì|no|  
|**SQLSetConnectOption**|[5]|[1]|Sì|  
|**SQLSetCursorName**|Sì|Sì|no|  
|**SQLSetDescField**|Sì|Sì|no|  
|**SQLSetDescRec**|Sì|Sì|no|  
|**SQLSetEnvAttr**|Sì|Sì|no|  
|**SQLSetPos**|Sì|Sì|no|  
|**SQLSetParam**|no|No|Sì|  
|**SQLSetScrollOption**|Sì|Sì|no|  
|**Funzione SQLSetStmtAttr**|Sì|Sì|no|  
|**SQLSetStmtOption**|[5]|[1]|Sì|  
|**SQLSpecialColumns**|Sì|Sì|no|  
|**SQLStatistics**|Sì|Sì|no|  
|**SQLTablePrivileges**|Sì|Sì|no|  
|**SQLTables**|Sì|Sì|no|  
|**SQLTransact**|no|[1]|Sì|  
  
 [1] questa funzione è deprecata in ODBC 3. *x*. ODBC 3. *x* applicazioni non devono utilizzare questa funzione. Tuttavia, un'applicazione compatibile con ISO CLI o l'Open Group può chiamare questa funzione.  
  
 [2] ODBC 3. *x* le applicazioni devono utilizzare **SQLBindParameter** anziché **SQLBindParam**. Tuttavia, un'applicazione compatibile con ISO CLI o l'Open Group può chiamare questa funzione.  
  
 [3] gli sviluppatori di driver di è opportuno notare che l'API ODBC 2. *x* SQL_COLUMN_PRECISION SQL_COLUMN_SCALE e SQL_COLUMN_LENGTH devono essere supportate con gli attributi di colonna **SQLColAttribute**.  
  
 [4] **SQLCopyDesc** viene implementato da Gestione Driver parzialmente quando vengono copiato un descrittore per le connessioni che appartengono a diversi driver. I driver necessari per supportare **SQLCopyDesc** tra due delle proprie connessioni. Le funzioni come **SQLDrivers**, che vengono implementati esclusivamente da Gestione Driver, non vengono visualizzati nell'elenco.  
  
 [5] in determinate circostanze, i driver potrebbe essere necessario supportare questa funzione. Per ulteriori informazioni, vedere la pagina di riferimento della funzione.  
  
 [6] il driver può scegliere di supportare **SQLGetFunctions** se il set di funzioni supportate dal driver varia da una connessione per connessione.
