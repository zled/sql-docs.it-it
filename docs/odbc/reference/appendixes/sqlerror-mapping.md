---
title: Mapping SQLError | Documenti Microsoft
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
- mapping deprecated functions [ODBC], SQLError
- SQLError function [ODBC], mapping
ms.assetid: 802ac711-7e5d-4152-9698-db0cafcf6047
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7ebbe17713149276acbe061bfb8ba41503026306
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

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
