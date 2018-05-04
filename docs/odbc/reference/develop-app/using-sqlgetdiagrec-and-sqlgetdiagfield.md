---
title: Utilizzando SQLGetDiagRec e SQLGetDiagField | Documenti Microsoft
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
- diagnostic information [ODBC], SqlGetDiagField
- SQLGetDiagField function [ODBC], and SQLGetDiagRec
- SQLGetDiagRec function [ODBC], and SQLGetDiagField
- diagnostic information [ODBC], SqlGetDiagRec
- retrieving diagnostic information [ODBC]
ms.assetid: 4f486bb1-fad8-4064-ac9d-61f2de85b68b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d01e70929d8cc4d9465828d208c0e774ba8b5428
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="using-sqlgetdiagrec-and-sqlgetdiagfield"></a>Utilizzando SQLGetDiagRec e SQLGetDiagField
Le applicazioni chiamano **SQLGetDiagRec** o **SQLGetDiagField** per recuperare le informazioni di diagnostica. Queste funzioni accettano un handle di ambiente, connessione, istruzione o descrittore e torna diagnostica dalla funzione l'handle dell'ultimo utilizzo. La diagnostica registrata su un handle specifico viene rimossi quando viene chiamata utilizzando l'handle di una nuova funzione. Se la funzione ha restituito più record di diagnostica, l'applicazione chiama queste funzioni più volte. il numero totale di record di stato viene recuperato chiamando **SQLGetDiagField** per il record di intestazione (record 0) con l'opzione SQL_DIAG_NUMBER.  
  
 Applicazioni di recuperano i singoli campi di diagnostica chiamando **SQLGetDiagField** e specificando il campo da recuperare. Alcuni campi di diagnostica non ha alcun significato per determinati tipi di handle. Per un elenco di campi di diagnostica e i relativi significati, vedere il [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) descrizione della funzione.  
  
 Le applicazioni di recuperare il valore SQLSTATE, codice di errore nativo e messaggio di diagnostica in una singola chiamata chiamando **SQLGetDiagRec**; **SQLGetDiagRec** non può essere utilizzato per recuperare informazioni dal record di intestazione.  
  
 Ad esempio, il codice seguente richiede l'immissione di un'istruzione SQL e viene eseguito. Se le informazioni di diagnostica è state restituite, chiama **SQLGetDiagField** per ottenere il numero di record di stato e **SQLGetDiagRec** per ottenere la SQLSTATE, un codice di errore nativo e un messaggio di diagnostica da quelli record.  
  
```  
SQLCHAR       SqlState[6], SQLStmt[100], Msg[SQL_MAX_MESSAGE_LENGTH];  
SQLINTEGER    NativeError;  
SQLSMALLINT   i, MsgLen;  
SQLRETURN     rc1, rc2;  
SQLHSTMT      hstmt;  
  
// Prompt the user for an SQL statement.  
GetSQLStmt(SQLStmt);  
  
// Execute the SQL statement and return any errors or warnings.  
rc1 = SQLExecDirect(hstmt, SQLStmt, SQL_NTS);  
if ((rc1 == SQL_SUCCESS_WITH_INFO) || (rc1 == SQL_ERROR)) {
   SQLLEN numRecs = 0;
   SQLGetDiagField(SQL_HANDLE_STMT, hstmt, 0, SQL_DIAG_NUMBER, &numRecs, 0, 0);
   // Get the status records.
   i = 1;  
   while (i <= numRecs && (rc2 = SQLGetDiagRec(SQL_HANDLE_STMT, hstmt, i, SqlState, &NativeError,  
            Msg, sizeof(Msg), &MsgLen)) != SQL_NO_DATA) {  
      DisplayError(SqlState,NativeError,Msg,MsgLen);  
      i++;  
   }  
}  
  
if ((rc1 == SQL_SUCCESS) || (rc1 == SQL_SUCCESS_WITH_INFO)) {  
   // Process statement results, if any.  
}  
```
