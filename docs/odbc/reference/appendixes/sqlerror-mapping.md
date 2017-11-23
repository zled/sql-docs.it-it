---
title: Mapping SQLError | Documenti Microsoft
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
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLError
- SQLError function [ODBC], mapping
ms.assetid: 802ac711-7e5d-4152-9698-db0cafcf6047
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1c6cfbf06a9cbbbe635506bbe1e0191879defa1a
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="sqlerror-mapping"></a>Mapping SQLError
Quando un'applicazione chiama **SQLError** tramite un'applicazione ODBC 3*x* driver, la chiamata a  
  
```  
SQLError(henv, hdbc, hstmt, szSqlState, pfNativeError, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)   
```  
  
 è stato eseguito il mapping a  
  
```  
SQLGetDiagRec(HandleType, Handle, RecNumber, szSqlstate, pfNativeErrorPtr, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)  
```  
  
 con il *HandleType* argomento impostato sul valore impostato su SQL_HANDLE_ENV, impostato su SQL_HANDLE_DBC o impostato su SQL_HANDLE_STMT, come appropriato e *gestire* argomento impostato sul valore *henv*, *hdbc*, o *hstmt*, a seconda dei casi. Il *RecNumber* argomento è determinato da Gestione Driver.
