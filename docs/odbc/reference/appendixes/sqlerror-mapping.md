---
title: Mapping SQLError | Documenti Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLError
- SQLError function [ODBC], mapping
ms.assetid: 802ac711-7e5d-4152-9698-db0cafcf6047
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0ba54875173e6836279db6c043a017af8a191dae
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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
