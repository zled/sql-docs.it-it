---
title: Funzione SQLGetStmtAttr | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLGetStmtAttr
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetStmtAttr
helpviewer_keywords:
- SQLGetStmtAttr function [ODBC]
ms.assetid: e321d460-e997-4527-aee6-207cf5a498e9
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1a45674ecbb65fcedd64551af3b7a2440b2b4621
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlgetstmtattr-function"></a>Funzione SQLGetStmtAttr
**Conformità**  
 Introdotta: versione ODBC 3.0 aderenza: 92 ISO  
  
 **Riepilogo**  
 **SQLGetStmtAttr** restituisce l'impostazione corrente di un attributo di istruzione.  
  
> [!NOTE]  
>  Per ulteriori informazioni su quali il Driver Manager esegue il mapping di questa funzione per quando un'applicazione ODBC 3. *x* applicazione sta utilizzando un'API ODBC 2. *x* driver, vedere [Mapping di funzioni di sostituzione per la compatibilità con le versioni precedenti di applicazioni](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLGetStmtAttr(  
     SQLHSTMT        StatementHandle,  
     SQLINTEGER      Attribute,  
     SQLPOINTER      ValuePtr,  
     SQLINTEGER      BufferLength,  
     SQLINTEGER *    StringLengthPtr);  
```  
  
## <a name="arguments"></a>Argomenti  
 *StatementHandle*  
 [Input] Handle di istruzione.  
  
 *Attributo*  
 [Input] Attributo da recuperare.  
  
 *ValuePtr*  
 [Output] Puntatore a un buffer in cui restituire il valore dell'attributo specificato *attributo*.  
  
 Se *ValuePtr* è NULL, *StringLengthPtr* continuerà a restituire il numero totale di byte (escluso il carattere di terminazione null per i dati di tipo carattere) disponibile da restituire nel buffer a cui puntato  *ValuePtr*.  
  
 *BufferLength*  
 [Input] Se *attributo* è un attributo basato su ODBC e *ValuePtr* punta a una stringa di caratteri o di un buffer binario, la lunghezza di questo argomento deve essere \* *ValuePtr*. Se *attributo* è un attributo basato su ODBC e \* *ValuePtr* è un numero intero, *BufferLength* viene ignorato. Se il valore restituito  *\*ValuePtr* è una stringa Unicode (quando si chiama **SQLGetStmtAttrW**), il *BufferLength* argomento deve essere un numero pari.  
  
 Se *attributo* è un attributo definito dal driver, l'applicazione indica la natura dell'attributo al Driver Manager impostando il *BufferLength* argomento. *BufferLength* può avere i valori seguenti:  
  
-   Se  *\*ValuePtr* è un puntatore a una stringa di caratteri, quindi *BufferLength* è la lunghezza della stringa o SQL_NTS.  
  
-   Se  *\*ValuePtr* è un puntatore a un buffer binario, quindi viene visualizzato il risultato di SQL_LEN_BINARY_ATTR (*lunghezza*) (macro) in *BufferLength*. In questo modo un valore negativo in *BufferLength*.  
  
-   Se  *\*ValuePtr* è un puntatore a un valore diverso da una stringa di caratteri o binario, quindi *BufferLength* deve avere il valore SQL_IS_POINTER.  
  
-   Se  *\*ValuePtr* è contiene un tipo di dati a lunghezza fissa, quindi *BufferLength* è SQL_IS_INTEGER o SQL_IS_UINTEGER, come appropriato.  
  
 *StringLengthPtr*  
 [Output] Un puntatore a un buffer in cui restituire il numero totale di byte (escluso il carattere di terminazione null) disponibile per restituire  *\*ValuePtr*. Se *ValuePtr* è un puntatore null, non viene restituita alcuna lunghezza. Se il valore dell'attributo è una stringa di caratteri e il numero di byte disponibili da restituire è maggiore o uguale a *BufferLength*, i dati in  *\*ValuePtr* viene troncato a *BufferLength* meno la lunghezza di un carattere di terminazione null ed è con terminazione null dal driver.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLGetStmtAttr** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato possono essere ottenuti chiamando **SQLGetDiagRec** con un *HandleType* di SQL _HANDLE_STMT e *gestire* di *StatementHandle*. Nella tabella seguente sono elencati i valori SQLSTATE comunemente restituiti da **SQLGetStmtAttr** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01004|Stringa di dati corretto troncato|I dati restituiti in  *\*ValuePtr* troncato per essere *BufferLength* meno la lunghezza di un carattere di terminazione null. Viene restituita la lunghezza del valore di stringa non troncato **StringLengthPtr*. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|24000|Stato del cursore non valido|L'argomento *attributo* stato SQL_ATTR_ROW_NUMBER e il cursore non è stato aperto o è stato posizionato il cursore prima dell'inizio del set di risultati o dopo la fine del set di risultati.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nell'argomento *MessageText* descrive l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver è stato in grado di allocare la memoria necessaria per supportare l'esecuzione o il completamento della funzione.|  
|HY010|Errore nella sequenza (funzione)|(DM) a cui è stata chiamata per l'handle di connessione associata a una funzione in modo asincrono in esecuzione il *StatementHandle*. Questa funzione asincrona era ancora in esecuzione quando il **SQLGetStmtAttr** funzione è stata chiamata.<br /><br /> (DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione il *StatementHandle* ed era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos** è stato chiamato per il  *StatementHandle* e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima che sono stati inviati dati per tutti i parametri data-at-execution o colonne.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY090|Lunghezza di stringa o di buffer non valida|*(DM) \*ValuePtr* è una stringa di caratteri e BufferLength era minore di zero, ma non è uguale a SQL_NTS.|  
|HY092|Identificatore di attributo/opzione non valida|Il valore specificato per l'argomento *attributo* non valido per la versione di ODBC supportati dal driver.|  
|HY109|Posizione del cursore non valido|Il *attributo* argomento è stato SQL_ATTR_ROW_NUMBER e la riga è stata eliminata o non può essere recuperata.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Funzionalità facoltativa non implementata.|Il valore specificato per l'argomento *attributo* è un attributo di istruzione ODBC valido per la versione di ODBC supportati dal driver, ma non è supportata dal driver.|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|(DM) il driver corrispondente il *StatementHandle* non supporta la funzione.|  
  
## <a name="comments"></a>Commenti  
 Per informazioni generali sugli attributi di istruzione, vedere [gli attributi di istruzione](../../../odbc/reference/develop-app/statement-attributes.md).  
  
 Una chiamata a **SQLGetStmtAttr** restituisce  *\*ValuePtr* il valore dell'attributo di istruzione specificato *attributo*. Tale valore può essere un valore SQLULEN o una stringa di caratteri con terminazione null. Se il valore è un valore SQLULEN, alcuni driver possono scrivere solo inferiore 32 bit o il bit di ordine più elevato di 16 bit di un buffer e lasciare invariato. Pertanto, devono utilizzare un buffer di SQLULEN o inizializzare il valore su 0 prima di chiamare questa funzione. Inoltre, il *BufferLength* e *StringLengthPtr* non vengono utilizzati gli argomenti. Se il valore è una stringa con terminazione null, l'applicazione specifica la lunghezza massima di tale stringa nel *BufferLength* argomento e il driver restituisce la lunghezza della stringa nel  *\* StringLengthPtr* buffer.  
  
 Per consentire alle applicazioni chiamata **SQLGetStmtAttr** per funzionare con ODBC 2. *x* driver, una chiamata a **SQLGetStmtAttr** viene eseguito il mapping in Gestione Driver per **SQLGetStmtOption**.  
  
 I seguenti attributi di istruzione sono di sola lettura, pertanto può essere recuperata da **SQLGetStmtAttr**, tuttavia, non impostare **SQLSetStmtAttr**:  
  
-   SQL_ATTR_IMP_PARAM_DESC  
  
-   SQL_ATTR_IMP_ROW_DESC  
  
-   SQL_ATTR_ROW_NUMBER  
  
 Per un elenco di attributi che è possibile impostare e recuperare, vedere [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md).  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Restituisce l'impostazione di un attributo di connessione|[Funzione SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|L'impostazione di un attributo di connessione|[Funzione SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|L'impostazione di un attributo di istruzione|[Funzione SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
