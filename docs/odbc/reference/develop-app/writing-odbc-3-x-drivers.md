---
title: La scrittura di driver ODBC 3.x | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- upgrading drivers [ODBC]
- ODBC drivers [ODBC], upgrading
- backward compatibility [ODBC], drivers
- compatibility [ODBC], drivers
ms.assetid: 9b75f59b-623f-4711-9ca2-e751b3622e00
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 77a94c7505b5ab221fee4896e91f9b26850669df
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47795651"
---
# <a name="writing-odbc-3x-drivers"></a>Scrittura di driver ODBC 3.x
La tabella seguente illustra il supporto di funzione in un'applicazione ODBC 3. *x* driver e un'applicazione ODBC e il mapping eseguito da Gestione Driver quando le funzioni vengono chiamate su un'applicazione ODBC 3. *x* driver.  
  
|Funzione|Supportato<br /><br /> da un<br /><br /> ODBC 3. *x*<br /><br /> driver?|Supportato<br /><br /> da un<br /><br /> ODBC 3. *x*<br /><br /> applicazione?|Il mapping o supportate<br /><br /> da ODBC 3. *x*<br /><br /> Gestione driver per<br /><br /> un'applicazione ODBC 3. *x* driver?|  
|--------------|----------------------------------------------------|---------------------------------------------------------|---------------------------------------------------------------------------------------------|  
|**SQLAllocConnect**|no|[1]|Sì|  
|**SQLAllocEnv**|no|[1]|Sì|  
|**Funzione SQLAllocHandle**|Sì|Sì|no|  
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
|**SQLExtendedFetch**|Sì|no|no|  
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
|**SQLParamOptions**|no|no|Sì|  
|**SQLPrepare**|Sì|Sì|no|  
|**SQLPrimaryKeys**|Sì|Sì|no|  
|**SQLProcedureColumns**|Sì|Sì|no|  
|**SQLProcedures**|Sì|Sì|no|  
|**SQLPutData**|Sì|Sì|no|  
|**SQLRowCount**|Sì|Sì|no|  
|**SQLSetConnectAttr**|Sì|Sì|no|  
|**SQLSetConnectOption**|[5]|[1]|Sì|  
|**SQLSetCursorName**|Sì|Sì|no|  
|**SQLSetDescField**|Sì|Sì|no|  
|**SQLSetDescRec**|Sì|Sì|no|  
|**SQLSetEnvAttr**|Sì|Sì|no|  
|**SQLSetPos**|Sì|Sì|no|  
|**SQLSetParam**|no|no|Sì|  
|**SQLSetScrollOption**|Sì|Sì|no|  
|**SQLSetStmtAttr**|Sì|Sì|no|  
|**SQLSetStmtOption**|[5]|[1]|Sì|  
|**SQLSpecialColumns**|Sì|Sì|no|  
|**SQLStatistics**|Sì|Sì|no|  
|**SQLTablePrivileges**|Sì|Sì|no|  
|**SQLTables**|Sì|Sì|no|  
|**SQLTransact**|no|[1]|Sì|  
  
 [1] questa funzione è deprecata in ODBC 3. *x*. ODBC 3. *x* applicazioni non deve usare questa funzione. Tuttavia, un'applicazione compatibile con ISO CLI o Open Group può chiamare questa funzione.  
  
 [2] ODBC 3. *x* le applicazioni devono utilizzare **SQLBindParameter** anziché **SQLBindParam**. Tuttavia, un'applicazione compatibile con ISO CLI o Open Group può chiamare questa funzione.  
  
 [3] gli sviluppatori di driver di necessario notare che l'API ODBC 2. *x* SQL_COLUMN_PRECISION SQL_COLUMN_SCALE e SQL_COLUMN_LENGTH devono essere supportate con gli attributi di colonna **SQLColAttribute**.  
  
 [4] **SQLCopyDesc** viene implementato parzialmente da Gestione Driver quando un descrittore di vengono copiato tra le connessioni che appartengono a diversi driver. I driver necessari per supportare **SQLCopyDesc** tra due di loro connessioni. Le funzioni come **SQLDrivers**, che vengono implementate esclusivamente da Gestione Driver, non vengono visualizzati nell'elenco.  
  
 [5] in determinate circostanze, i driver potrebbe essere necessario supportare questa funzione. Per altre informazioni, vedere la pagina di riferimento relativa a questa funzione.  
  
 [6] i driver possono scegliere di supportare **SQLGetFunctions** se il set di funzioni supportate dal driver varia da una connessione alla connessione.
