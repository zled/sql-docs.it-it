---
title: Mapping SQLGetStmtOption | Documenti Microsoft
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
- SQLGetStmtOption function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLGetStmtOption
ms.assetid: fa599517-3f3e-4dad-a65a-b8596ae3f330
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 503af3ea0dbac61cee506b932f79eccab5dedcf8
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgetstmtoption-mapping"></a>Mapping di SQLGetStmtOption
Quando un'applicazione chiama **SQLGetStmtOption** per un'applicazione ODBC 3*x* driver che non lo supporta, la chiamata a  
  
```  
SQLGetStmtOption(hstmt, fOption, pvParam)  
```  
  
 restituirà come indicato di seguito:  
  
-   Se *fOption* indica un'opzione ODBC definita dall'istruzione che restituisce una stringa, le chiamate di gestione Driver  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
-   Se *fOption* indica un'opzione ODBC definita dall'istruzione che restituisce un valore integer a 32 bit, le chiamate di gestione Driver  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, 0, NULL)  
    ```  
  
-   Se *fOption* indica un'opzione di istruzione definito dal driver, le chiamate di gestione Driver  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
 Nei tre casi precedenti, il *StatementHandle* argomento è impostato sul valore *hstmt*, *attributo* argomento è impostato sul valore *fOption *e *ValuePtr* argomento è impostato sullo stesso valore di *il parametro pvParam*.  
  
 Per le opzioni di connessione di stringa definite da ODBC Driver Manager imposta la *BufferLength* argomento nella chiamata a **SQLGetConnectAttr** per la lunghezza massima predefinita (SQL_MAX_OPTION_STRING_LENGTH); per un'opzione di connessione non di tipo stringa, *BufferLength* è impostato su 0.  
  
 L'opzione dell'istruzione SQL_GET_BOOKMARK è stato deprecato in ODBC 3*x*. Per un'applicazione ODBC 3*x* driver per funzionare con ODBC 2.* x* le applicazioni che utilizzano SQL_GET_BOOKMARK, deve supportare SQL_GET_BOOKMARK. Per un'applicazione ODBC 3*x* driver per funzionare con ODBC 2.* x* applicazioni, deve supportare l'impostazione SQL_USE_BOOKMARKS su SQL_UB_ON e devono essere esposti a lunghezza fissa segnalibri. Se un'applicazione ODBC 3*x* driver supporta solo segnalibri di lunghezza variabile, i segnalibri non a lunghezza fissa, mentre deve restituire un valore SQLSTATE HYC00 (funzionalità facoltativa non implementata) se un ODBC 2.* x* applicazione tenta di impostare SQL_USE_BOOKMARKS SQL_UB_ON.  
  
 Per un'applicazione ODBC 3*x* driver, Driver Manager non consente di controllare se *opzione* è tra SQL_STMT_OPT_MIN e SQL_STMT_OPT_MAX, oppure è maggiore di SQL_CONNECT_OPT_DRVR_START. Il driver è necessario selezionare questa opzione.

