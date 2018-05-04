---
title: Funzione SQLGetEnvAttr | Documenti Microsoft
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
- SQLGetEnvAttr
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetEnvAttr
helpviewer_keywords:
- SQLGetEnvAttr function [ODBC]
ms.assetid: 01f4590f-427a-4280-a1c3-18de9f7d86c1
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b1a31f7d374a06a4e9cfe963c92b73fa681a41d9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlgetenvattr-function"></a>SQLGetEnvAttr (funzione)
**Conformità**  
 Introdotta: versione ODBC 3.0 aderenza: 92 ISO  
  
 **Riepilogo**  
 **SQLGetEnvAttr** restituisce l'impostazione corrente di un attributo di ambiente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLGetEnvAttr(  
     SQLHENV        EnvironmentHandle,  
     SQLINTEGER     Attribute,  
     SQLPOINTER     ValuePtr,  
     SQLINTEGER     BufferLength,  
     SQLINTEGER *   StringLengthPtr);  
```  
  
## <a name="arguments"></a>Argomenti  
 *EnvironmentHandle*  
 [Input] Handle di ambiente.  
  
 *Attributo*  
 [Input] Attributo da recuperare.  
  
 *ValuePtr*  
 [Output] Puntatore a un buffer in cui restituire il valore corrente dell'attributo specificato da *attributo*.  
  
 Se *ValuePtr* è NULL, *StringLengthPtr* continuerà a restituire il numero totale di byte (escluso il carattere di terminazione null per i dati di tipo carattere) disponibile da restituire nel buffer a cui puntato  *ValuePtr*.  
  
 *BufferLength*  
 [Input] Se *ValuePtr* punta a una stringa di caratteri, la lunghezza di questo argomento deve essere \* *ValuePtr*. Se \* *ValuePtr* è un numero intero, *BufferLength* viene ignorato. Se  *\*ValuePtr* è una stringa Unicode (quando si chiama **SQLGetEnvAttrW**), il *BufferLength* argomento deve essere un numero pari. Se il valore dell'attributo non è una stringa di caratteri *BufferLength* è inutilizzato.  
  
 *StringLengthPtr*  
 [Output] Un puntatore a un buffer in cui restituire il numero totale di byte (escluso il carattere di terminazione null) disponibile per restituire  *\*ValuePtr*. Se *ValuePtr* è un puntatore null, non viene restituita alcuna lunghezza. Se il valore dell'attributo è una stringa di caratteri e il numero di byte disponibili da restituire è maggiore o uguale a *BufferLength*, i dati in \* *ValuePtr* viene troncato a  *BufferLength* meno la lunghezza di un carattere di terminazione null ed è con terminazione null dal driver.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLGetEnvAttr** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato possono essere ottenuti chiamando **SQLGetDiagRec** con un *HandleType* di SQL _ HANDLE_ENV e *gestire* di *EnvironmentHandle*. Nella tabella seguente sono elencati i valori SQLSTATE comunemente restituiti da **SQLGetEnvAttr** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01004|Stringa di dati corretto troncato|I dati restituiti in \* *ValuePtr* troncato per essere *BufferLength* meno il carattere di terminazione null. Viene restituita la lunghezza del valore di stringa non troncato **StringLengthPtr*. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel  *\*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver è stato in grado di allocare la memoria necessaria per supportare l'esecuzione o il completamento della funzione.|  
|HY010|Errore nella sequenza (funzione)|(DM) **SQL_ATTR_ODBC_VERSION** non è ancora stato impostato tramite **SQLSetEnvAttr**. Non è necessario impostare **SQL_ATTR_ODBC_VERSION** in modo esplicito se si utilizza **SQLAllocHandleStd**.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY092|Identificatore di attributo/opzione non valida|Il valore specificato per l'argomento *attributo* non valido per la versione di ODBC supportati dal driver.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Funzionalità facoltativa non implementata.|Il valore specificato per l'argomento *attributo* è un attributo di ambiente ODBC valido per la versione di ODBC supportati dal driver, ma non è supportata dal driver.|  
|IM001|Driver non supporta questa funzione|(DM) il driver corrispondente il *EnvironmentHandle* non supporta la funzione.|  
  
## <a name="comments"></a>Commenti  
 Per un elenco di attributi, vedere [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md). Non sono presenti attributi di ambiente specifiche del driver. Se *attributo* specifica un attributo che restituisce una stringa, *ValuePtr* deve essere un puntatore a un buffer in cui si desidera restituire la stringa. La lunghezza massima della stringa, incluso il byte di terminazione null, sarà *BufferLength* byte.  
  
 **SQLGetEnvAttr** può essere chiamato in qualsiasi momento compreso tra l'allocazione e la liberazione di un handle di ambiente. Tutti gli attributi di ambiente impostati correttamente dall'applicazione per l'ambiente mantenuta fino al **SQLFreeHandle** viene chiamato sul *EnvironmentHandle* con un *HandleType*impostato su SQL_HANDLE_ENV. Più di un handle di ambiente può essere allocato contemporaneamente in ODBC 3*x*. Un attributo di ambiente in un ambiente non viene modificato quando è stato allocato un altro ambiente.  
  
> [!NOTE]  
>  L'attributo di ambiente SQL_ATTR_OUTPUT_NTS è supportato dalle applicazioni conformi agli standard. Quando **SQLGetEnvAttr** viene chiamato, ODBC 3*x* gestione Driver sempre restituisce SQL_TRUE per questo attributo. SQL_ATTR_OUTPUT_NTS può essere impostato su SQL_TRUE solo da una chiamata a **SQLSetEnvAttr**.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Restituisce l'impostazione di un attributo di connessione|[Funzione SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Restituisce l'impostazione di un attributo di istruzione|[Funzione SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|  
|L'impostazione di un attributo di connessione|[Funzione SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|L'impostazione di un attributo di ambiente|[Funzione SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|  
|L'impostazione di un attributo di istruzione|[Funzione SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
