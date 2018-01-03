---
title: Funzione SQLGetConnectAttr | Documenti Microsoft
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
apiname: SQLGetConnectOption
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLGetConnectAttr
helpviewer_keywords: SQLGetConnectAttr function [ODBC]
ms.assetid: 2cb4ffa8-19d3-4664-8c2f-6682cdcc3f33
caps.latest.revision: "32"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 11e1ae7c2dc3de4611687349295bdd3344c46d47
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sqlgetconnectattr-function"></a>Funzione SQLSetConnectAttr
**Conformità**  
 Introdotta: versione ODBC 3.0 aderenza: 92 ISO  
  
 **Riepilogo**  
 **SQLGetConnectAttr** restituisce l'impostazione corrente di un attributo di connessione.  
  
> [!NOTE]  
>  Per ulteriori informazioni su cosa the Driver Manager esegue il mapping di questa funzione per quando un'applicazione ODBC 3*x* applicazione sta utilizzando un'API ODBC 2*x* driver, vedere [Mapping di funzioni di sostituzione per indietro Compatibilità delle applicazioni](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLGetConnectAttr(  
     SQLHDBC        ConnectionHandle,  
     SQLINTEGER     Attribute,  
     SQLPOINTER     ValuePtr,  
     SQLINTEGER     BufferLength,  
     SQLINTEGER *   StringLengthPtr);  
```  
  
## <a name="arguments"></a>Argomenti  
 *ConnectionHandle*  
 [Input] Handle di connessione.  
  
 *Attribute*  
 [Input] Attributo da recuperare.  
  
 *ValuePtr*  
 [Output] Puntatore alla memoria in cui restituire il valore corrente dell'attributo specificato da *attributo*. Per gli attributi di tipo integer, alcuni driver possono scrivere solo inferiore 32 bit o il bit di ordine più elevato di 16 bit di un buffer e lasciare invariato. Pertanto, devono utilizzare un buffer di SQLULEN o inizializzare il valore su 0 prima di chiamare questa funzione.  
  
 Se *ValuePtr* è NULL, *StringLengthPtr* continuerà a restituire il numero totale di byte (escluso il carattere di terminazione null per i dati di tipo carattere) disponibile da restituire nel buffer a cui puntato  *ValuePtr*.  
  
 *BufferLength*  
 [Input] Se *attributo* è un attributo basato su ODBC e *ValuePtr* punta a una stringa di caratteri o di un buffer binario, la lunghezza di questo argomento deve essere \* *ValuePtr*. Se *attributo* è un attributo basato su ODBC e \* *ValuePtr* è un numero intero, *BufferLength* viene ignorato. Se il valore in  *\*ValuePtr* è una stringa Unicode (quando si chiama **SQLGetConnectAttrW**), il *BufferLength* argomento deve essere un numero pari.  
  
 Se *attributo* è un attributo definito dal driver, l'applicazione indica la natura dell'attributo al Driver Manager impostando il *BufferLength* argomento. *BufferLength* può avere i valori seguenti:  
  
-   Se  *\*ValuePtr* è un puntatore a una stringa di caratteri *BufferLength* è la lunghezza della stringa.  
  
-   Se  *\*ValuePtr* è un puntatore a un buffer binario, le posizioni dell'applicazione il risultato di SQL_LEN_BINARY_ATTR (*lunghezza*) (macro) in *BufferLength*. In questo modo un valore negativo in *BufferLength*.  
  
-   Se  *\*ValuePtr* è un puntatore a un valore diverso da una stringa di caratteri o stringa binaria, *BufferLength* deve avere il valore SQL_IS_POINTER.  
  
-   Se  *\*ValuePtr* contiene un tipo di dati a lunghezza fissa, *BufferLength* è SQL_IS_INTEGER o SQL_IS_UINTEGER, come appropriato.  
  
 *StringLengthPtr*  
 [Output] Un puntatore a un buffer in cui restituire il numero totale di byte (escluso il carattere di terminazione null) disponibile per restituire \* *ValuePtr*. Se \* *ValuePtr* è un puntatore null, non viene restituita alcuna lunghezza. Se il valore dell'attributo è una stringa di caratteri e il numero di byte disponibili da restituire è maggiore di *BufferLength* meno la lunghezza del carattere di terminazione null, i dati in  *\*ValuePtr*viene troncato a *BufferLength* meno la lunghezza del carattere di terminazione null ed è con terminazione null dal driver.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLGetConnectAttr** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato possono essere ottenuti dalla struttura di dati di diagnostica chiamando **SQLGetDiagRec** con un *HandleType* impostato su SQL_HANDLE_DBC e *gestire* di *ConnectionHandle*. Nella tabella seguente sono elencati i valori SQLSTATE normalmente restituiti dal **SQLGetConnectAttr** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver . Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01004|Stringa di dati corretto troncato|I dati restituiti in \* *ValuePtr* troncato per essere *BufferLength* meno la lunghezza di un carattere di terminazione null. Viene restituita la lunghezza del valore di stringa non troncato **StringLengthPtr*. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|08003|Connessione non aperta|(DM) un *attributo* è stato specificato valore che è necessaria una connessione aperta.|  
|08S01|Errore del collegamento di comunicazione|Collegamento di comunicazione tra il driver e l'origine dati a cui era connesso il driver non è stato possibile prima dell'elaborazione della funzione è stata completata.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito dalla struttura di dati di diagnostica dall'argomento *MessageText* in **SQLGetDiagField** descrive l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver non è riuscito ad allocare memoria che è necessario per supportare l'esecuzione o il completamento della funzione.|  
|HY010|Errore nella sequenza (funzione)|(DM) **SQLBrowseConnect** è stato chiamato per il *ConnectionHandle* e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima di **SQLBrowseConnect** restituito SQL_SUCCESS_WITH_INFO o SQL_SUCCESS.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** è stato chiamato per il *ConnectionHandle* e restituito SQL_PARAM_DATA_ È DISPONIBILE. Questa funzione è stata chiamata prima che i dati sono stati recuperati per tutti i parametri con flusso.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY090|Lunghezza di stringa o di buffer non valida|(DM)  *\*ValuePtr* è una stringa di caratteri e BufferLength è minore di zero ma non è uguale a SQL_NTS.|  
|HY092|Identificatore di attributo/opzione non valida|Il valore specificato per l'argomento *attributo* non valido per la versione di ODBC supportati dal driver.|  
|HY114|Driver non supporta l'esecuzione di funzione asincrona a livello di connessione|(DM) un'applicazione ha tentato di attivare l'esecuzione di funzione asincrona con SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE per un driver che non supporta le operazioni di connessione asincrona.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Funzionalità facoltativa non implementata.|Il valore specificato per l'argomento *attributo* è un attributo di connessione ODBC valido per la versione di ODBC supportati dal driver, ma non è supportata dal driver.|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|(DM) il driver che corrisponde alla *ConnectionHandle* non supporta la funzione.|  
  
## <a name="comments"></a>Commenti  
 Per informazioni generali sugli attributi di connessione, vedere [gli attributi di connessione](../../../odbc/reference/develop-app/connection-attributes.md).  
  
 Per un elenco di attributi che è possibile impostare, vedere [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md). Si noti che se *attributo* specifica un attributo che restituisce una stringa, *ValuePtr* deve essere un puntatore a un buffer per la stringa. La lunghezza massima della stringa restituita, incluso il carattere di terminazione null, sarà *BufferLength* byte.  
  
 A seconda dell'attributo, un'applicazione non è necessario stabilire una connessione prima di chiamare **SQLGetConnectAttr**. Tuttavia, se **SQLGetConnectAttr** viene chiamato e l'attributo specificato non è presente un predefinito e non è stata impostata da una precedente chiamata a **SQLSetConnectAttr**, **SQLGetConnectAttr**restituisce SQL_NO_DATA.  
  
 Se *attributo* è traccia sql_attr o sql_attr TRACEFILE, *ConnectionHandle* non deve essere valido, e **SQLGetConnectAttr** non restituirà SQL_ERROR o SQL _ INVALID_HANDLE se *ConnectionHandle* non è valido. Questi attributi si applicano a tutte le connessioni. **SQLGetConnectAttr** restituirà SQL_ERROR o SQL_INVALID_HANDLE se un altro argomento non è valido.  
  
 Sebbene un'applicazione può impostare gli attributi di istruzione tramite **SQLSetConnectAttr**, un'applicazione non è possibile utilizzare **SQLGetConnectAttr** per recuperare l'attributo di istruzione valori; è necessario chiamare  **SQLGetStmtAttr** per recuperare l'impostazione degli attributi di istruzione.  
  
 Gli attributi di connessione SQL_ATTR_AUTO_IPD sia SQL_ATTR_CONNECTION_DEAD possono essere restituiti da una chiamata a **SQLGetConnectAttr** ma non può essere impostata da una chiamata a **SQLSetConnectAttr**.  
  
> [!NOTE]  
>  Nessun supporto asincrono per **SQLGetConnectAttr**. Quando si implementa **SQLGetConnectAttr**, un driver può migliorare le prestazioni riducendo il numero di volte in cui vengono inviati o richieste dal server.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Restituisce l'impostazione di un attributo di istruzione|[Funzione SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|  
|L'impostazione di un attributo di connessione|[Funzione SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|L'impostazione di un attributo di ambiente|[Funzione SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|  
|L'impostazione di un attributo di istruzione|[Funzione SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
