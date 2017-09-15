---
title: Allocando e liberando i buffer | Documenti Microsoft
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
- buffers [ODBC], allocating and freeing
- allocating buffers [ODBC]
- freeing buffers [ODBC]
ms.assetid: 886bc9ed-39d4-43d2-82ff-aebc35b14d39
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 73689fb95eb9b51e7f5f16b10c43256ef63f8dd2
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="allocating-and-freeing-buffers"></a>Allocando e liberando i buffer
Tutti i buffer sono allocati e liberati dall'applicazione. Se un buffer non è stato posticipato, devono esistere solo per la durata della chiamata a una funzione. Ad esempio, **SQLGetInfo** restituisce il valore associato a una particolare opzione nel buffer a cui fa riferimento il *InfoValuePtr* argomento. Questo buffer può essere liberato immediatamente dopo la chiamata a **SQLGetInfo**, come illustrato nell'esempio di codice seguente:  
  
```  
SQLSMALLINT   InfoValueLen;  
SQLCHAR *     InfoValuePtr = malloc(50);   // Allocate InfoValuePtr.  
  
SQLGetInfo(hdbc, SQL_DBMS_NAME, (SQLPOINTER)InfoValuePtr, 50,  
            &InfoValueLen);  
  
free(InfoValuePtr);                        // OK to free InfoValuePtr.  
```  
  
 Poiché posticipata i buffer sono specificati in una funzione e usati in un altro, è un errore di programmazione dell'applicazione per liberare un buffer posticipato, mentre il driver comunque si aspetta che lo esiste. Ad esempio, l'indirizzo del \* *ValuePtr* buffer passato a **SQLBindCol** per un utilizzo futuro da **SQLFetch**. Il buffer non può essere rilasciato fino a quando la colonna non è associata, ad esempio con una chiamata a **SQLBindCol** o **SQLFreeStmt** come illustrato nell'esempio di codice seguente:  
  
```  
SQLRETURN    rc;  
SQLINTEGER   ValueLenOrInd;  
SQLHSTMT     hstmt;  
  
// Allocate ValuePtr  
SQLCHAR * ValuePtr = malloc(50);  
  
// Bind ValuePtr to column 1. It is an error to free ValuePtr here.  
SQLBindCol(hstmt, 1, SQL_C_CHAR, ValuePtr, 50, &ValueLenOrInd);  
  
// Fetch each row of data and place the value for column 1 in *ValuePtr.  
// Code to check if rc equals SQL_ERROR or SQL_SUCCESS_WITH_INFO   
// not shown.  
while ((rc = SQLFetch(hstmt)) != SQL_NO_DATA) {  
   // It is an error to free ValuePtr here.  
}  
  
// Unbind ValuePtr from column 1.  It is now OK to free ValuePtr.  
SQLFreeStmt(hstmt, SQL_UNBIND);  
free(ValuePtr);  
```  
  
 Questo errore è facilmente dichiarando buffer locale in una funzione. il buffer viene liberato quando l'applicazione lascia la funzione. Ad esempio, il codice seguente causa il comportamento non definito e probabilmente irreversibile nel driver:  
  
```  
SQLRETURN   rc;  
SQLHSTMT    hstmt;  
  
BindAColumn(hstmt);  
  
// Fetch each row of data and try to place the value for column 1 in  
// *ValuePtr. Because ValuePtr has been freed, the behavior is undefined  
// and probably fatal. Code to check if rc equals SQL_ERROR or   
// SQL_SUCCESS_WITH_INFO not shown.  
while ((rc = SQLFetch(hstmt)) != SQL_NO_DATA) {}  
  
   .  
   .  
   .  
  
void BindAColumn(SQLHSTMT hstmt)  // WARNING! This function won't work!  
{  
   // Declare ValuePtr locally.  
   SQLCHAR      ValuePtr[50];  
   SQLINTEGER   ValueLenOrInd;  
  
   // Bind rgbValue to column.  
   SQLBindCol(hstmt, 1, SQL_C_CHAR, ValuePtr, sizeof(ValuePtr),  
               &ValueLenOrInd);  
  
   // ValuePtr is freed when BindAColumn exits.  
}  
```
