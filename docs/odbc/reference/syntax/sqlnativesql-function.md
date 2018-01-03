---
title: Funzione SQLNativeSql | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLNativeSql
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLNativeSql
helpviewer_keywords: SQLNativeSql function [ODBC]
ms.assetid: b8efc247-27ab-4a00-92b6-1400785783fe
caps.latest.revision: "24"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e233d9742ea7bd9aa5de56962e1d785be78b8066
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sqlnativesql-function"></a>Funzione SQLNativeSql
**Conformità**  
 Introdotta: versione ODBC standard 1.0 conformità: ODBC  
  
 **Riepilogo**  
 **SQLNativeSql** restituisce la stringa SQL come modificata dal driver. **SQLNativeSql** non esegue l'istruzione SQL.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLNativeSql(  
     SQLHDBC        ConnectionHandle,  
     SQLCHAR *      InStatementText,  
     SQLINTEGER     TextLength1,  
     SQLCHAR *      OutStatementText,  
     SQLINTEGER     BufferLength,  
     SQLINTEGER *   TextLength2Ptr);  
```  
  
## <a name="arguments"></a>Argomenti  
 *ConnectionHandle*  
 [Input] Handle di connessione.  
  
 *InStatementText*  
 [Input] Stringa di testo SQL da convertire.  
  
 *TextLength1*  
 [Input] Lunghezza in caratteri del **InStatementText* stringa di testo.  
  
 *OutStatementText*  
 [Output] Puntatore a un buffer in cui si desidera restituire la stringa SQL tradotta.  
  
 Se *OutStatementText* è NULL, *TextLength2Ptr* continuerà a restituire il numero totale di caratteri (escluso il carattere di terminazione null per i dati di tipo carattere) disponibile da restituire nel buffer a cui puntava *OutStatementText*.  
  
 *BufferLength*  
 [Input] Numero di caratteri di \* *OutStatementText* buffer. Se il valore restituito  *\*InStatementText* è una stringa Unicode (quando si chiama **SQLNativeSqlW**), il *BufferLength* argomento deve essere un numero pari.  
  
 *TextLength2Ptr*  
 [Output] Puntatore a un buffer in cui restituire il numero totale di caratteri (ad eccezione di terminazione null) disponibili per restituire \* *OutStatementText*. Se il numero di caratteri disponibili da restituire è maggiore o uguale a *BufferLength*, convertire la stringa SQL in \* *OutStatementText* viene troncato a  *BufferLength* meno la lunghezza di un carattere di terminazione null.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLNativeSql** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato può essere ottenuto chiamando **SQLGetDiagRec** con un *HandleType* impostato su SQL_HANDLE_DBC e *gestire* di *ConnectionHandle*. Nella tabella seguente sono elencati i valori SQLSTATE comunemente restituiti da **SQLNativeSql** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01004|Stringa di dati corretto troncato|Il buffer \* *OutStatementText* non sia abbastanza grande per restituire l'intera stringa SQL, pertanto la stringa SQL è stata troncata. Viene restituita la lunghezza della stringa SQL non troncata **TextLength2Ptr*. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|08003|Connessione non aperta|Il *ConnectionHandle* non è in stato connesso.|  
|08S01|Errore del collegamento di comunicazione|Collegamento di comunicazione tra il driver e l'origine dati a cui era connesso il driver non è stato possibile prima dell'elaborazione della funzione è stata completata.|  
|22007|Formato di datetime non valido|**InStatementText* contenuta una clausola di escape con un valore di data, ora o timestamp non valido.|  
|24000|Stato del cursore non valido|Il cursore a cui l'istruzione è stato posizionato prima dell'inizio del set di risultati o dopo la fine del set di risultati. Questo errore non può essere restituito da un driver con un'implementazione nativa di cursore DBMS.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel  *\*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver è stato in grado di allocare la memoria necessaria per supportare l'esecuzione o il completamento della funzione.|  
|HY009|Utilizzo non valido del puntatore null|(DM) **InStatementText* era un puntatore null.|  
|HY010|Errore nella sequenza (funzione)|(DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione il *ConnectionHandle* ed era ancora in esecuzione quando questa funzione è stata chiamata.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY090|Lunghezza di stringa o di buffer non valida|(DM) l'argomento *TextLength1* è minore di 0, ma non è uguale a SQL_NTS.|  
|||(DM) l'argomento *BufferLength* è minore di 0 e l'argomento *OutStatementText* non è un puntatore null.|  
|HY109|Posizione del cursore non valido|La riga corrente del cursore è stata eliminata o non era stata recuperata. Questo errore non può essere restituito da un driver con un'implementazione nativa di cursore DBMS.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|Il driver (DM) associato il *ConnectionHandle* non supporta la funzione.|  
  
## <a name="comments"></a>Commenti  
 Di seguito sono riportati esempi di ciò che **SQLNativeSql** potrebbe restituire la stringa di input seguente SQL che contiene la funzione scalare CONVERT. Si supponga che empid la colonna è di tipo INTEGER nell'origine dati:  
  
```  
SELECT { fn CONVERT (empid, SQL_SMALLINT) } FROM employee  
```  
  
 Un driver per Microsoft SQL Server potrebbe restituire la stringa SQL tradotta seguente:  
  
```  
SELECT convert (smallint, empid) FROM employee  
```  
  
 Un driver per il Server ORACLE potrebbe restituire la stringa SQL tradotta seguente:  
  
```  
SELECT to_number (empid) FROM employee  
```  
  
 Un driver per Ingres potrebbe restituire la stringa SQL tradotta seguente:  
  
```  
SELECT int2 (empid) FROM employee  
```  
  
 Per ulteriori informazioni, vedere [esecuzione diretta](../../../odbc/reference/develop-app/direct-execution-odbc.md) e [esecuzione preparata](../../../odbc/reference/develop-app/prepared-execution-odbc.md).  
  
## <a name="related-functions"></a>Funzioni correlate  
 nessuna.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
