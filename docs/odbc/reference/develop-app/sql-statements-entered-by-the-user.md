---
title: Istruzioni SQL immesse dall'utente | Documenti Microsoft
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
- user-entered SQL statements [ODBC]
- SQL statements [ODBC], constructing
- SQL statements [ODBC], entered by user
ms.assetid: 109af162-93ba-425a-8fe5-49c7dc7cc784
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b234123c01d4bdf4590c000b996a4febe4ad485e
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sql-statements-entered-by-the-user"></a>Istruzioni SQL immesse dall'utente
Applicazioni che eseguono analisi ad hoc anche comunemente consentono all'utente di immettere istruzioni SQL direttamente. Esempio:  
  
```  
SQLCHAR *     Statement, SqlState[6], Msg[SQL_MAX_MESSAGE_LENGTH];  
SQLSMALLINT   i, MsgLen;  
SQLINTEGER    NativeError;  
SQLRETURN     rc1, rc2;  
  
// Prompt user for SQL statement.  
GetSQLStatement(Statement);  
  
// Execute the statement directly. Because it will be executed only once,  
// do not prepare it.  
rc1 = SQLExecDirect(hstmt, Statement, SQL_NTS);  
  
// Process any errors or returned information.  
if ((rc1 == SQL_ERROR) || rc1 == SQL_SUCCESS_WITH_INFO) {  
   i = 1;  
   while ((rc2 = SQLGetDiagRec(SQL_HANDLE_STMT, hstmt, i, SqlState, &NativeError,  
         Msg, sizeof(Msg), &MsgLen)) != SQL_NO_DATA) {  
      DisplayError(SqlState, NativeError, Msg, MsgLen);  
      i++;  
   }  
}  
```  
  
 Questo approccio semplifica la generazione di codice di applicazione; l'applicazione si basa sull'utente per compilare l'istruzione SQL e sull'origine dati per verificare la validità dell'istruzione. Poiché è difficile scrivere un'interfaccia utente grafica che adeguatamente espone gli aspetti complessi relativi a SQL, è sufficiente che chiede all'utente di immettere il testo dell'istruzione SQL può essere un'alternativa preferibile. Tuttavia, questo richiede all'utente di conoscere non solo SQL, ma anche lo schema dell'origine dati sottoposte a query. Alcune applicazioni forniscono un'interfaccia utente grafica mediante il quale l'utente può creare un'istruzione SQL di base e inoltre fornire un'interfaccia di testo con cui l'utente può modificarlo.
