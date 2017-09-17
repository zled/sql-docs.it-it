---
title: Mapping SQLSetStmtOption | Documenti Microsoft
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
- mapping deprecated functions [ODBC], SQLSetStmtOption
- SQLSetStmtOption function [ODBC], mapping
ms.assetid: 6a9921aa-8a53-4668-9b13-87164062f1e5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3aba3d69d8bbb90b1296bf821b6552d25a05b7b2
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetstmtoption-mapping"></a>Mapping SQLSetStmtOption
Quando un'applicazione chiama **SQLSetStmtOption** tramite un'applicazione ODBC 3*x* driver, la chiamata a  
  
```  
SQLSetStmtOption(StatementHandle, fOption, vParam)  
```  
  
 restituirà come indicato di seguito:  
  
-   Se *fOption* indica un attributo di istruzione definite da ODBC che è una stringa, le chiamate di gestione Driver  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, SQL_NTS)  
    ```  
  
-   Se *fOption* indica un attributo di istruzione definite da ODBC che restituisce un valore integer a 32 bit, le chiamate di gestione Driver  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, 0)  
    ```  
  
-   Se *fOption* indica un attributo di istruzione definito dal driver, le chiamate di gestione Driver  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, BufferLength)  
    ```  
  
 Nei tre casi precedenti, il **StatementHandle** argomento è impostato sul valore *hstmt*, *attributo* argomento è impostato sul valore *fOption *e *ValuePtr* argomento è impostato sul valore come *vParam*.  
  
 Poiché gestione Driver non è noto se l'attributo di istruzione definito dal driver è necessario un valore stringa o integer a 32 bit, deve passare un valore valido per il *StringLength* argomento di **SQLSetStmtAttr**. Se il driver è definita una semantica speciale per gli attributi di istruzione definito dal driver e deve essere chiamato utilizzando **SQLSetStmtOption**, deve supportare **SQLSetStmtOption**.  
  
 Se un'applicazione chiama **SQLSetStmtOption** per impostare un'opzione di istruzione specifici del driver in un'applicazione ODBC 3*x* driver e l'opzione è stata definita in un ODBC 2.* x* la versione del driver, una nuova costante di manifesto deve essere definita per l'opzione in ODBC 3*x* driver. Se la costante manifesto precedente viene utilizzata nella chiamata a **SQLSetStmtOption**, Driver Manager chiamerà **SQLSetStmtAttr** con il *StringLength* argomento impostato su 0.  
  
 Quando un'applicazione chiama **SQLSetStmtAttr** su cui impostare SQL_ATTR_USE_BOOKMARKS SQL_UB_ON in un'applicazione ODBC 3*x* driver, l'attributo di istruzione di SQL_ATTR_USE_BOOKMARKS è impostato su SQL_UB_FIXED. SQL_UB_ON è la stessa costante come SQL_UB_FIXED. Gestione Driver passa SQL_UB_FIXED tramite il driver. SQL_UB_FIXED è stato deprecato in ODBC 3*x*, ma un'applicazione ODBC 3*x* driver deve implementare per funzionare con ODBC 2.* x* le applicazioni che utilizzano i segnalibri di lunghezza fissa.  
  
 Per un'applicazione ODBC 3*x* driver, gestione Driver non controlla se *opzione* è tra SQL_STMT_OPT_MIN e SQL_STMT_OPT_MAX, oppure è maggiore di SQL_CONNECT_OPT_DRVR_START.
