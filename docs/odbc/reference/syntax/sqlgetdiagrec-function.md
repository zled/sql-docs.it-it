---
title: Funzione SQLGetDiagRec | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLGetDiagRec
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetDiagRec
helpviewer_keywords:
- SQLGetDiagRec function [ODBC]
ms.assetid: ebdbac93-3d68-438f-8416-ef1f08e04269
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 591664f329f4c7feeb24fff52b809dba567d0b80
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgetdiagrec-function"></a>Funzione SQLGetDiagRec
**Conformità**  
 Introdotta: versione ODBC 3.0 aderenza: 92 ISO  
  
 **Riepilogo**  
 **SQLGetDiagRec** restituisce i valori di più campi di un record di diagnostica che contiene informazioni sull'errore, avviso e lo stato correnti. A differenza di **SQLGetDiagField**, che restituisce un campo di diagnostica per ogni chiamata, **SQLGetDiagRec** restituisce diversi campi di un record di diagnostica, tra cui il valore SQLSTATE, il codice di errore nativo di uso comune e il testo del messaggio di diagnostica.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLGetDiagRec(  
     SQLSMALLINT     HandleType,  
     SQLHANDLE       Handle,  
     SQLSMALLINT     RecNumber,  
     SQLCHAR *       SQLState,  
     SQLINTEGER *    NativeErrorPtr,  
     SQLCHAR *       MessageText,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   TextLengthPtr);  
```  
  
## <a name="arguments"></a>Argomenti  
 *HandleType*  
 [Input] Un identificatore di tipo di handle che descrive il tipo di handle per cui è richiesto diagnostica. I possibili valori sono i seguenti:  
  
-   IMPOSTATO SU SQL_HANDLE_DBC  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   IMPOSTATO SU SQL_HANDLE_ENV  
  
-   IMPOSTATO SU SQL_HANDLE_STMT  
  
 Handle SQL_HANDLE_DBC_INFO_TOKEN è utilizzato solo da Gestione Driver e driver. Applicazioni non devono utilizzare questo tipo di handle. Per ulteriori informazioni su SQL_HANDLE_DBC_INFO_TOKEN, vedere [consapevolezza Pool di connessioni lo sviluppo di un Driver ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
 *Handle*  
 [Input] Un handle per la struttura di dati di diagnostica, del tipo indicato dalla *HandleType*. Se *HandleType* è impostato su SQL_HANDLE_ENV, *gestire* può essere condivisa o un handle di ambiente non condiviso.  
  
 *RecNumber*  
 [Input] Indica se il record di stato da cui l'applicazione cerca di informazioni. Record di stato vengono numerati da 1.  
  
 *SQLState*  
 [Output] Puntatore a un buffer in cui si desidera restituire un codice SQLSTATE di cinque caratteri (e il carattere di terminazione NULL) per il record di diagnostica *RecNumber*. I primi due caratteri indicano la classe. i successivi tre indicano la sottoclasse. Queste informazioni sono contenute nel campo SQL_DIAG_SQLSTATE diagnostica. Per ulteriori informazioni, vedere [SQLSTATE](../../../odbc/reference/develop-app/sqlstates.md).  
  
 *NativeErrorPtr*  
 [Output] Puntatore a un buffer in cui restituire il codice di errore nativo, specifico dell'origine dati. Queste informazioni sono contenute nel campo SQL_DIAG_NATIVE diagnostica.  
  
 *MessageText*  
 [Output] Puntatore a un buffer in cui si desidera restituire la stringa di testo del messaggio di diagnostica. Queste informazioni sono contenute nel campo SQL_DIAG_MESSAGE_TEXT diagnostica. Per il formato della stringa, vedere [messaggi diagnostici](../../../odbc/reference/develop-app/diagnostic-messages.md).  
  
 Se *MessageText* è NULL, *TextLengthPtr* continuerà a restituire il numero totale di caratteri (escluso il carattere di terminazione null per i dati di tipo carattere) disponibile da restituire nel buffer a cui fa riferimento *MessageText*.  
  
 *BufferLength*  
 [Input] Lunghezza di **MessageText* buffer in caratteri. È prevista una lunghezza massima del testo del messaggio di diagnostica.  
  
 *TextLengthPtr*  
 [Output] Puntatore a un buffer in cui restituire il numero totale di caratteri (escluso il numero di caratteri necessari per il carattere di terminazione null) disponibile per restituire * \*MessageText*. Se il numero di caratteri disponibili da restituire è maggiore di *BufferLength*, il testo del messaggio di diagnostica in * \*MessageText* viene troncato a *BufferLength* meno la lunghezza di un carattere di terminazione null.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 **SQLGetDiagRec** non registra record di diagnostica per se stesso. Usa i seguenti valori restituiti per segnalare il risultato della propria esecuzione:  
  
-   SQL_SUCCESS: La funzione ha restituito correttamente le informazioni di diagnostica.  
  
-   SQL_SUCCESS_WITH_INFO: Il \* *MessageText* buffer è troppo piccolo per contenere il messaggio di diagnostica richiesto. Nessun record di diagnostica sono stati generati. Per determinare che si è verificato un troncamento, l'applicazione deve confrontare *BufferLength* sul numero effettivo di byte disponibili, che viene scritto **StringLengthPtr*.  
  
-   SQL_INVALID_HANDLE: L'handle indicato da *HandleType* e *gestire* non è un handle valido.  
  
-   SQL_ERROR: Uno dei seguenti si è verificato:  
  
    -   *RecNumber* è negativo o 0.  
  
    -   *BufferLength* è minore di zero.  
  
    -   Quando si utilizza la notifica asincrona, l'operazione asincrona dell'handle non è completo.  
  
-   SQL_NO_DATA: *RecNumber* è maggiore del numero di record di diagnostica esistenti per l'handle specificato nel *gestire.* La funzione restituisce SQL_NO_DATA per qualsiasi positivo *RecNumber* se non sono presenti record di diagnostica per *gestire*.  
  
## <a name="comments"></a>Commenti  
 Un'applicazione chiama in genere **SQLGetDiagRec** quando una chiamata precedente a una funzione ODBC ha restituito SQL_ERROR o SQL_SUCCESS_WITH_INFO. Tuttavia, poiché una funzione ODBC registrare zero o più record di diagnostica ogni volta che viene chiamato, un'applicazione può chiamare **SQLGetDiagRec** dopo ogni chiamata di funzione ODBC. Un'applicazione può chiamare **SQLGetDiagRec** più volte per restituire alcuni o tutti i record nella struttura di dati di diagnostica. ODBC non impone alcun limite al numero di record di diagnostica che possono essere archiviati in qualsiasi momento.  
  
 **SQLGetDiagRec** non può essere utilizzata per restituire i campi dall'intestazione della struttura di dati di diagnostica. (Il *RecNumber* argomento deve essere maggiore di 0.) L'applicazione deve chiamare **SQLGetDiagField** a questo scopo.  
  
 **SQLGetDiagRec** recupera solo le informazioni di diagnostica più di recente associate all'handle specificato nella *gestire* argomento. Se l'applicazione chiama un'altra funzione ODBC, ad eccezione di **SQLGetDiagRec**, **SQLGetDiagField**, o **SQLError**, le informazioni di diagnostica dalle precedenti chiamate di stesso handle è perso.  
  
 Un'applicazione può analizzare tutti i record di diagnostica dal ciclo, incremento *RecNumber*, purché **SQLGetDiagRec** restituisce SQL_SUCCESS. Le chiamate a **SQLGetDiagRec** siano distruttive ai campi di intestazione e il record. L'applicazione può chiamare **SQLGetDiagRec** nuovamente in un secondo momento per recuperare un campo da un record, purché in quanto non altra funzione, ad eccezione di **SQLGetDiagRec**, **SQLGetDiagField**, o **SQLError**, è stato chiamato nel frattempo. L'applicazione può recuperare anche un conteggio del numero totale di record di diagnostica disponibile chiamando **SQLGetDiagField** per recuperare il valore del campo SQL_DIAG_NUMBER e quindi chiamando **SQLGetDiagRec**numero di volte indicato.  
  
 Per una descrizione dei campi della struttura di dati di diagnostica, vedere [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md). Per ulteriori informazioni, vedere [utilizzando SQLGetDiagRec e SQLGetDiagField](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md) e [implementazione SQLGetDiagRec e SQLGetDiagField](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md).  
  
 Chiama un'API diverso da quello che viene eseguita in modo asincrono genererà HY010 "Errore nella sequenza Function". Tuttavia, il record di errore non è possibile recuperare prima che venga completata l'operazione asincrona.  
  
## <a name="handletype-argument"></a>Argomento HandleType  
 Ogni tipo di handle può avere le informazioni di diagnostica associate. Il *HandleType* argomento indica il tipo di handle del *gestire* argomento.  
  
 Alcuni campi di intestazione e record non possono essere restituiti per l'ambiente, connessione, l'istruzione e descrittore di handle. Tali handle per il quale non è applicabile un campo sono indicati nelle sezioni "Campi di intestazione" e "Record" in [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md).  
  
 Una chiamata a **SQLGetDiagRec** restituirà SQL_INVALID_HANDLE se *HandleType* è SQL_HANDLE_SENV, che indica un handle di ambiente condiviso. Tuttavia, se *HandleType* è impostato su SQL_HANDLE_ENV, *gestire* può essere condivisa o un handle di ambiente non condiviso.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Recupero di un campo di un record di diagnostica o di un campo di intestazione di diagnostica|[Funzione SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Programma di esempio ODBC](../../../odbc/reference/sample-odbc-program.md)
