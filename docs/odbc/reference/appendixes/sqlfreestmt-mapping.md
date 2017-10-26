---
title: Mapping SQLFreeStmt | Documenti Microsoft
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
- SQLFreeStmt function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLFreeStmt
ms.assetid: 267d95f2-4f0c-47ab-9411-5afe105215a2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: df3cfba17f19074fbe00f33ef7fba098a4fe8184
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlfreestmt-mapping"></a>Mapping SQLFreeStmt
Quando un'applicazione chiama **SQLFreeStmt** con un *opzione* argomento di SQL_DROP tramite un'applicazione ODBC 3*x* driver, la chiamata a  
  
```  
SQLFreeStmt(hstmt, SQL_DROP)   
```  
  
 è stato eseguito il mapping a  
  
```  
SQLFreeHandle(SQL_HANDLE_STMT,Handle)  
```  
  
 con il *gestire* argomento impostato sul valore *hstmt*.

