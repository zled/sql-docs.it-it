---
title: Funzione conformità | Documenti Microsoft
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
- conformance levels [ODBC], function
- function conformance levels [ODBC]
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
ms.assetid: bb5d68cf-d238-481e-babc-2e9401b4700e
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 182b53071f5d7d4c3486a84f789954e12772e0bc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32914256"
---
# <a name="function-conformance"></a>Conformità (funzione)
Nella tabella seguente indica il livello di conformità di ogni funzione ODBC, in cui questo è ben definito.  
  
|Funzione|Livello di conformità|  
|--------------|-----------------------|  
|**SQLAllocHandle**|Core|  
|**SQLBindCol**|Core|  
|**SQLBindParameter**|Componenti di base [1]|  
|**SQLBrowseConnect**|Livello 1|  
|**SQLBulkOperations**|Livello 1|  
|**SQLCancel**|Componenti di base [1]|  
|**SQLCloseCursor**|Core|  
|**SQLColAttribute**|Componenti di base [1]|  
|**SQLColumnPrivileges**|Livello 2|  
|**SQLColumns**|Core|  
|**SQLConnect**|Core|  
|**SQLCopyDesc**|Core|  
|**SQLDataSources**|Core|  
|**SQLDescribeCol**|Componenti di base [1]|  
|**SQLDescribeParam**|Livello 2|  
|**SQLDisconnect**|Core|  
|**SQLDriverConnect**|Core|  
|**SQLDrivers**|Core|  
|**SQLEndTran**|Componenti di base [1]|  
|**SQLExecDirect**|Core|  
|**SQLExecute**|Core|  
|**SQLFetch**|Core|  
|**SQLFetchScroll**|Componenti di base [1]|  
|**SQLForeignKeys**|Livello 2|  
|**SQLFreeHandle**|Core|  
|**SQLFreeStmt**|Core|  
|**SQLGetConnectAttr**|Core|  
|**SQLGetCursorName**|Core|  
|**SQLGetData**|Core|  
|**SQLGetDescField**|Core|  
|**SQLGetDescRec**|Core|  
|**SQLGetDiagField**|Core|  
|**SQLGetDiagRec**|Core|  
|**SQLGetEnvAttr**|Core|  
|**SQLGetFunctions**|Core|  
|**SQLGetInfo**|Core|  
|**SQLGetStmtAttr**|Core|  
|**SQLGetTypeInfo**|Core|  
|**SQLMoreResults**|Livello 1|  
|**SQLNativeSql**|Core|  
|**SQLNumParams**|Core|  
|**SQLNumResultCols**|Core|  
|**SQLParamData**|Core|  
|**SQLPrepare**|Core|  
|**SQLPrimaryKeys**|Livello 1|  
|**SQLProcedureColumns**|Livello 1|  
|**SQLProcedures**|Livello 1|  
|**SQLPutData**|Core|  
|**SQLRowCount**|Core|  
|**Funzione SQLSetConnectAttr**|Componenti di base [2]|  
|**SQLSetCursorName**|Core|  
|**SQLSetDescField**|Componenti di base [1]|  
|**SQLSetDescRec**|Core|  
|**SQLSetEnvAttr**|Componenti di base [2]|  
|**SQLSetPos**|Livello 1, [1]|  
|**Funzione SQLSetStmtAttr**|Componenti di base [2]|  
|**SQLSpecialColumns**|Componenti di base [1]|  
|**SQLStatistics**|Core|  
|**SQLTablePrivileges**|Livello 2|  
|**SQLTables**|Core|  
  
 [1] funzionalità significative di questa funzione sono disponibili solo a livelli superiori di conformità.  
  
 [2] impostazione di valori non predefiniti determinati attributi dipende dal livello di conformità. Per ulteriori informazioni, vedere la sezione successiva, [conformità attributo](../../../odbc/reference/develop-app/attribute-conformance.md).
