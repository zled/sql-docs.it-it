---
title: Mapping di funzioni deprecate | Documenti Microsoft
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
- mapping deprecated functions [ODBC], about mapping deprecated functions
- backward compatibility [ODBC], mapping deprecated functions
- deprecated functions [ODBC]
- compatibility [ODBC], mapping deprecated functions
- functions [ODBC], mapping deprecated functions
- mapping deprecated functions [ODBC]
ms.assetid: ee462617-1d79-4c88-afeb-b129cff34cc6
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 61d05017039673989e1477501feb17b3da6d7220
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="mapping-deprecated-functions"></a>Mapping di funzioni deprecate
Questa sezione vengono descritte le funzioni deprecate come viene eseguito il mapping da ODBC 3*x* gestione Driver per garantire la compatibilità con le versioni precedenti di ODBC 3*x* driver che vengono utilizzati con ODBC 2. *x* applicazioni. Gestione Driver esegue il mapping indipendentemente dalla versione dell'applicazione. Poiché ogni ODBC 2. *x* funzioni nell'elenco seguente viene eseguito il mapping per il corrispondente di ODBC 3*x* funzione quando viene chiamato in un'applicazione ODBC 3*x* driver ODBC 3*x*driver non è necessario implementare ODBC 2. *x* funzioni.  
  
 Il mapping nell'elenco viene generato quando il driver è un'applicazione ODBC 3*x* e il driver non supporta la funzione che viene eseguito il mapping.  
  
 Nella tabella seguente sono elencate le funzionalità di tutti i duplicati che è stata introdotta in ODBC 3*x*.  
  
|ODBC 2. *x* (funzione)|ODBC 3*x* (funzione)|  
|-------------------------|-------------------------|  
|**SQLAllocConnect**|**SQLAllocHandle**|  
|**SQLAllocEnv**|**SQLAllocHandle**|  
|**SQLAllocStmt**|**SQLAllocHandle**|  
|**SQLBindParam**[1]|**SQLBindParameter**|  
|**SQLColAttributes**|**SQLColAttribute**|  
|**SQLError**|**SQLGetDiagRec**|  
|**SQLFreeConnect**|**SQLFreeHandle**|  
|**SQLFreeEnv**|**SQLFreeHandle**|  
|**SQLFreeStmt** con un *opzione* di SQL_DROP|**SQLFreeHandle**|  
|**SQLGetConnectOption**|**SQLGetConnectAttr**|  
|**SQLGetStmtOption**|**SQLGetStmtAttr**|  
|**SQLParamOptions**|**Funzione SQLSetStmtAttr**|  
|**SQLSetConnectOption**|**Funzione SQLSetConnectAttr**|  
|**SQLSetParam**[2]|**SQLBindParameter**|  
|**SQLSetScrollOption**|**Funzione SQLSetStmtAttr**|  
|**SQLSetStmtOption**|**Funzione SQLSetStmtAttr**|  
|**SQLTransact**|**SQLEndTran**|  
  
 [1] anche se questa funzione non esisteva in ODBC 2*x*, è lo standard Open Group e ISO.  
  
 [2] è una funzione ODBC 1.0.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Mapping di SQLAllocConnect](../../../odbc/reference/appendixes/sqlallocconnect-mapping.md)  
  
-   [Mapping di SQLAllocEnv](../../../odbc/reference/appendixes/sqlallocenv-mapping.md)  
  
-   [Mapping di SQLAllocStmt](../../../odbc/reference/appendixes/sqlallocstmt-mapping.md)  
  
-   [Mapping di SQLBindParam](../../../odbc/reference/appendixes/sqlbindparam-mapping.md)  
  
-   [Mapping di SQLColAttributes](../../../odbc/reference/appendixes/sqlcolattributes-mapping.md)  
  
-   [Mapping SQLError](../../../odbc/reference/appendixes/sqlerror-mapping.md)  
  
-   [Mapping di SQLFreeConnect](../../../odbc/reference/appendixes/sqlfreeconnect-mapping.md)  
  
-   [Mapping di SQLFreeEnv](../../../odbc/reference/appendixes/sqlfreeenv-mapping.md)  
  
-   [Mapping SQLFreeStmt](../../../odbc/reference/appendixes/sqlfreestmt-mapping.md)  
  
-   [Mapping di SQLGetConnectOption](../../../odbc/reference/appendixes/sqlgetconnectoption-mapping.md)  
  
-   [Mapping di SQLGetStmtOption](../../../odbc/reference/appendixes/sqlgetstmtoption-mapping.md)  
  
-   [La funzione SQLInstallTranslator Mapping](../../../odbc/reference/appendixes/sqlinstalltranslator-mapping.md)  
  
-   [Mapping SQLParamOptions](../../../odbc/reference/appendixes/sqlparamoptions-mapping.md)  
  
-   [Mapping SQLSetConnectOption](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md)  
  
-   [Mapping di SQLSetParam](../../../odbc/reference/appendixes/sqlsetparam-mapping.md)  
  
-   [Mapping di SQLSetScrollOptions](../../../odbc/reference/appendixes/sqlsetscrolloptions-mapping.md)  
  
-   [Mapping SQLSetStmtOption](../../../odbc/reference/appendixes/sqlsetstmtoption-mapping.md)  
  
-   [Mapping di SQLTransact](../../../odbc/reference/appendixes/sqltransact-mapping.md)

