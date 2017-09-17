---
title: Mapping SQLAllocStmt | Documenti Microsoft
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
- mapping deprecated functions [ODBC], SQLAllocStmt
- SQLAllocStmt function [ODBC], mapping
ms.assetid: a2449dbb-1b6c-4b49-81b9-ebdddd4442fd
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e8361f0b77e8f15f775eece7aae9b599be5e62ac
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlallocstmt-mapping"></a>Mapping di SQLAllocStmt
Quando un'applicazione chiama **SQLAllocStmt** tramite un'applicazione ODBC 3*x* driver, la chiamata a:  
  
```  
SQLAllocStmt(hdbc, phstmt)  
```  
  
 è stato eseguito il mapping a **SQLAllocHandle** da Gestione Driver nel driver come indicato di seguito:  
  
```  
SQLAllocHandle(SQL_HANDLE_STMT, InputHandle, OutputHandlePtr)  
```  
  
 con *InputHandle* impostato su *hdbc* e *OutputHandlePtr* impostato su *phstmt*.
