---
title: Funzione SQLGetCursorName | Documenti Microsoft
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
ms.topic: article
apiname:
- SQLGetCursorName
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetCursorName
helpviewer_keywords:
- SQLGetCursorName function [ODBC]
ms.assetid: e6e92199-7bb6-447c-8987-049a4c6ce05d
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 28220550d868976aded368a88bdc8268cfad490c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sqlgetcursorname-function"></a>Funzione SQLGetCursorName
**Conformità**  
 Introdotta: versione ODBC standard 1.0 conformità: 92 ISO  
  
 **Riepilogo**  
 **SQLGetCursorName** restituisce il nome di cursore associato a un'istruzione specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLGetCursorName(  
     SQLHSTMT        StatementHandle,  
     SQLCHAR *       CursorName,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   NameLengthPtr);  
```  
  
## <a name="arguments"></a>Argomenti  
 *StatementHandle*  
 [Input] Handle di istruzione.  
  
 *Nomecursore*  
 [Output] Puntatore a un buffer in cui restituire il nome del cursore.  
  
 Se *Nomecursore* è NULL, *NameLengthPtr* continuerà a restituire il numero totale di caratteri (escluso il carattere di terminazione null per i dati di tipo carattere) disponibile da restituire nel buffer a cui fa riferimento *Nomecursore*.  
  
 *BufferLength*  
 [Input] Lunghezza di \* *Nomecursore*, in caratteri. Se il valore in  *\*Nomecursore* è una stringa Unicode (quando si chiama **SQLGetCursorNameW**), il *BufferLength* argomento deve essere un numero pari.  
  
 *NameLengthPtr*  
 [Output] Puntatore alla memoria in cui restituire il numero totale di caratteri (escluso il carattere di terminazione null) disponibile per restituire \* *Nomecursore*. Se il numero di caratteri disponibili da restituire è maggiore o uguale a *BufferLength*, il nome del cursore in \* *Nomecursore* viene troncato a *BufferLength*meno la lunghezza di un carattere di terminazione null.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLGetCursorName** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato può essere ottenuto chiamando **SQLGetDiagRec** con un *HandleType*impostato su SQL_HANDLE_STMT e *gestire* di *StatementHandle*. Nella tabella seguente sono elencati i valori SQLSTATE comunemente restituiti da **SQLGetCursorName** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01004|Stringa di dati corretto troncato|Il buffer \* *Nomecursore* non sia abbastanza grande per restituire il nome del cursore intero, pertanto il nome del cursore è stato troncato. Viene restituita la lunghezza del nome del cursore non troncato **NameLengthPtr*. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel  *\*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver è stato in grado di allocare la memoria necessaria per supportare l'esecuzione o il completamento della funzione.|  
|HY010|Errore nella sequenza (funzione)|(DM) a cui è stata chiamata per l'handle di connessione associata a una funzione in modo asincrono in esecuzione il *StatementHandle*. Questa funzione asincrona era ancora in esecuzione quando il **SQLGetCursorName** funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** è stato chiamato per il *StatementHandle* e restituito SQL_PARAM_DATA_ È DISPONIBILE. Questa funzione è stata chiamata prima che i dati sono stati recuperati per tutti i parametri con flusso.<br /><br /> (DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione il *StatementHandle* ed era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos** è stato chiamato per il  *StatementHandle* e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima che sono stati inviati dati per tutti i parametri data-at-execution o colonne.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY015|Nessun nome di cursore disponibile.|(DM) il driver non è un'API ODBC 2*x* driver, si è verificato alcun cursore aperto nell'istruzione e fosse stato impostato alcun nome di cursore con **SQLSetCursorName**.|  
|HY090|Lunghezza di stringa o di buffer non valida|(DM) il valore specificato nell'argomento *BufferLength* era minore di 0.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|Il driver (DM) associato il *StatementHandle* non supporta la funzione.|  
  
## <a name="comments"></a>Commenti  
 I nomi di cursore vengono utilizzati solo per gli aggiornamenti posizionati e istruzioni delete (ad esempio, **aggiornare** *-nome della tabella* ... **WHERE CURRENT OF** *-nome del cursore*). Per ulteriori informazioni, vedere [istruzioni di eliminazione e aggiornamento posizionato](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md). Se l'applicazione non chiama **SQLSetCursorName** per definire un nome di cursore, il driver genera un nome. Questo nome inizia con le lettere SQL_CUR.  
  
> [!NOTE]  
>  In ODBC 2*x*, quando si è verificato alcun cursore aperto e fosse stato impostato alcun nome da una chiamata a **SQLSetCursorName**, una chiamata a **SQLGetCursorName** restituito HY015 SQLSTATE (Nessun nome di cursore disponibile). In ODBC 3*x*, non è più true; indipendentemente dal fatto che quando **SQLGetCursorName** viene chiamato, il driver restituisce il nome del cursore.  
  
 **SQLGetCursorName** restituisce il nome di un cursore o meno il nome è stato creato in modo esplicito o implicito. Se viene generato in modo implicito un nome di cursore **SQLSetCursorName** non viene chiamato. **SQLSetCursorName** può essere chiamato per rinominare un cursore su un'istruzione fino a quando il cursore si trova in uno stato allocato o preparato.  
  
 Il nome di un cursore che viene impostato in modo esplicito o implicito rimane impostato fino a quando il *StatementHandle* al quale è associato viene eliminato, utilizzando **SQLFreeHandle** con un *HandleType* impostato su SQL_HANDLE_STMT.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Esecuzione di un'istruzione SQL|[Funzione SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|L'esecuzione di un'istruzione SQL preparata|[Funzione SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Preparazione di un'istruzione per l'esecuzione|[Funzione SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|Impostazione di un nome di cursore|[Funzione SQLSetCursorName](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
