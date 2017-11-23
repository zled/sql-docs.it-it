---
title: Esecuzione asincrona (metodo di notifica) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e509dad9-5263-4a10-9a4e-03b84b66b6b3
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 56eadba88bc229b4d3f3560c60988124b54f33b9
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="asynchronous-execution-notification-method"></a>Esecuzione asincrona (metodo di notifica)
ODBC consente l'esecuzione asincrona di connessione e le operazioni di istruzione. Un thread dell'applicazione può chiamare una funzione ODBC in modalità asincrona e la funzione può restituire prima che l'operazione è stata completata, consentendo il thread dell'applicazione eseguire altre attività. In Windows 7 SDK, per l'istruzione asincrona o operazioni di connessione, un'applicazione determinato che l'operazione asincrona è completa utilizzando il metodo di polling. Per ulteriori informazioni, vedere [esecuzione asincrona (metodo di Polling)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md). A partire da Windows 8 SDK, è possibile determinare che un'operazione asincrona viene completata utilizzando il metodo di notifica.  
  
 Il metodo di polling, è necessario chiamare la funzione asincrona ogni volta che desidera che lo stato dell'operazione di applicazioni. Il metodo di notifica è simile a callback e tempo di attesa in ADO.NET. ODBC, tuttavia, utilizza gli eventi di Win32 come oggetto di notifica.  
  
 Impossibile utilizzare la libreria di cursori ODBC e notifica asincrona ODBC nello stesso momento. L'impostazione entrambi gli attributi restituirà un errore con SQLSTATE S1119 (libreria di cursori e la notifica asincrona non possono essere abilitate nello stesso momento).  
  
 Vedere [notifica di completamento asincrono funzione](../../../odbc/reference/develop-driver/notification-of-asynchronous-function-completion.md) per informazioni per gli sviluppatori di driver.  
  
> [!NOTE]  
>  Il metodo di notifica non è supportato con libreria di cursori. Un'applicazione verrà visualizzato il messaggio di errore se tenta di abilitare la libreria di cursori tramite SQLSetConnectAttr, quando il metodo di notifica è abilitato.  
  
## <a name="overview"></a>Panoramica  
 Quando una funzione ODBC viene chiamata in modalità asincrona, il controllo viene restituito all'applicazione chiamante immediatamente con il codice restituito SQL_STILL_EXECUTING. L'applicazione deve ripetutamente il polling la funzione che restituisca un valore diverso da SQL_STILL_EXECUTING. Il ciclo di polling aumenta l'utilizzo della CPU, causando una riduzione delle prestazioni in molti scenari asincroni.  
  
 Ogni volta che viene utilizzato il modello di notifica, il modello di polling è disabilitato. Applicazioni non devono chiamare nuovamente la funzione originale. Chiamare [SQLCompleteAsync funzione](../../../odbc/reference/syntax/sqlcompleteasync-function.md) per completare l'operazione asincrona. Se un'applicazione chiama la funzione originale nuovamente prima del completamento dell'operazione asincrona, la chiamata restituisce SQL_ERROR con SQLSTATE IM017 (Polling è disabilitato in modalità di notifica asincrona).  
  
 Quando si utilizza il modello di notifica, l'applicazione può chiamare **SQLCancel** o **SQLCancelHandle** per annullare un'operazione di connessione o istruzione. Se la richiesta di annullamento ha esito positivo, ODBC restituisce SQL_SUCCESS. Questo messaggio non indica che la funzione è stata effettivamente annullata; indica che è stata elaborata la richiesta di annullamento. Se la funzione è effettivamente annullata è dipendente dal driver e dipende dall'origine dati. Quando un'operazione viene annullata, gestione Driver verrà comunque in grado di segnalare l'evento. Gestione Driver restituisce SQL_ERROR nel buffer del codice restituito e lo stato è HY008 SQLSTATE (operazione annullata) per indicare l'annullamento è riuscito. Se la funzione è stata completata la normale elaborazione, gestione Driver restituisce SQL_SUCCESS o SQL_SUCCESS_WITH_INFO.  
  
### <a name="downlevel-behavior"></a>Comportamento di livello inferiore  
 La versione di gestione Driver ODBC che supporti questa notifica il completamento è 3,81 ODBC.  
  
|Versione dell'applicazione ODBC|Versione di Gestione driver|Versione driver|Comportamento|  
|------------------------------|----------------------------|--------------------|--------------|  
|Nuova applicazione di qualsiasi versione ODBC|ODBC 3,81|ODBC 3.80 Driver|Applicazione può utilizzare questa funzionalità se il driver supporta questa funzionalità, in caso contrario gestione Driver verrà generato un errore.|  
|Nuova applicazione di qualsiasi versione ODBC|ODBC 3,81|Driver pre-ODBC 3.80|Gestione Driver verrà generato un errore se il driver non supporta questa funzionalità.|  
|Nuova applicazione di qualsiasi versione ODBC|Pre-ODBC 3,81|Qualsiasi|Quando l'applicazione utilizza questa funzionalità, una gestione Driver precedente considererà i nuovi attributi come attributi specifici del driver e il driver deve generato un errore. Una nuova gestione Driver non supera questi attributi per il driver.|  
  
 Un'applicazione deve verificare la versione di gestione Driver prima di utilizzare questa funzionalità. In caso contrario, se un driver scritto male non non errore e la versione di gestione Driver è pre 3,81 ODBC, comportamento è indefinito.  
  
## <a name="use-cases"></a>Modalità di utilizzo comuni  
 Questa sezione illustra i casi di utilizzo per il meccanismo di polling e l'esecuzione asincrona.  
  
### <a name="integrate-data-from-multiple-odbc-sources"></a>Integrare dati da più origini ODBC  
 Un'applicazione di integrazione di dati recupera in modo asincrono i dati da più origini dati. Alcuni dei dati da origini dati remote e alcuni dati provengono da file locali. L'applicazione non può continuare finché non vengono completate le operazioni asincrone.  
  
 Anziché eseguire continuamente il polling di un'operazione per determinare se è stata completata, l'applicazione può creare un oggetto evento e associarlo a un handle di connessione ODBC o un handle di istruzione ODBC. L'applicazione chiama quindi API in attesa di molti oggetti di eventi (eventi di ODBC e altri eventi di Windows) o di oggetto di un evento di sincronizzazione del sistema operativo. ODBC segnalerà l'oggetto evento quando viene completata l'operazione asincrona di ODBC corrispondente.  
  
 In Windows, gli oggetti evento Win32 verranno utilizzati e che fornirà all'utente un modello di programmazione unificato. Driver Manager su altre piattaforme è possibile utilizzare l'implementazione dell'oggetto evento specifica per tali piattaforme.  
  
 Esempio di codice seguente viene illustrato l'utilizzo della connessione e la notifica asincrona istruzione:  
  
```  
// This function opens NUMBER_OPERATIONS connections and executes one query on statement of each connection.  
// Asynchronous Notification is used  
  
#define NUMBER_OPERATIONS 5  
int AsyncNotificationSample(void)  
{  
    RETCODE     rc;  
  
    SQLHENV     hEnv              = NULL;  
    SQLHDBC     arhDbc[NUMBER_OPERATIONS]         = {NULL};  
    SQLHSTMT    arhStmt[NUMBER_OPERATIONS]        = {NULL};  
  
    HANDLE      arhDBCEvent[NUMBER_OPERATIONS]    = {NULL};  
    RETCODE     arrcDBC[NUMBER_OPERATIONS]        = {0};  
    HANDLE      arhSTMTEvent[NUMBER_OPERATIONS]   = {NULL};  
    RETCODE     arrcSTMT[NUMBER_OPERATIONS]       = {0};  
  
    rc = SQLAllocHandle(SQL_HANDLE_ENV, NULL, &hEnv);  
    if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
  
    rc = SQLSetEnvAttr(hEnv,  
        SQL_ATTR_ODBC_VERSION,  
        (SQLPOINTER) SQL_OV_ODBC3_80,  
        SQL_IS_INTEGER);  
    if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
  
    // Connection operations begin here  
  
    // Alloc NUMBER_OPERATIONS connection handles  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc = SQLAllocHandle(SQL_HANDLE_DBC, hEnv, &arhDbc[i]);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Enable DBC Async on all connection handles  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc= SQLSetConnectAttr(arhDbc[i], SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE, (SQLPOINTER)SQL_ASYNC_DBC_ENABLE_ON, SQL_IS_INTEGER);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Application must create event objects  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        arhDBCEvent[i] = CreateEvent(NULL, FALSE, FALSE, NULL); // Auto-reset, initial state is not-signaled  
        if (!arhDBCEvent[i]) goto Cleanup;  
    }  
  
    // Enable notification on all connection handles  
    // Event  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc= SQLSetConnectAttr(arhDbc[i], SQL_ATTR_ASYNC_DBC_EVENT, arhDBCEvent[i], SQL_IS_POINTER);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Initiate connect establishing  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLDriverConnect(arhDbc[i], NULL, (SQLTCHAR*)TEXT("Driver={ODBC Driver 11 for SQL Server};SERVER=dp-srv-sql2k;DATABASE=pubs;UID=sa;PWD=XYZ;"), SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
    }  
  
    // Can do some other staff before calling WaitForMultipleObjects  
    WaitForMultipleObjects(NUMBER_OPERATIONS, arhDBCEvent, TRUE, INFINITE); // Wait All  
  
    // Complete connect API calls  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLCompleteAsync(SQL_HANDLE_DBC, arhDbc[i], & arrcDBC[i]);  
    }  
  
    BOOL fFail = FALSE; // Whether some connection openning fails.  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if ( !SQL_SUCCEEDED(arrcDBC[i]) )   
            fFail = TRUE;  
    }  
  
    // If some SQLDriverConnect() fail, clean up.  
    if (fFail)  
    {  
        for (int i=0; i<NUMBER_OPERATIONS; i++)  
        {  
            if (SQL_SUCCEEDED(arrcDBC[i]) )   
            {  
                SQLDisconnect(arhDbc[i]); // This is also async  
            }  
            else  
            {  
                SetEvent(arhDBCEvent[i]); // Previous SQLDriverConnect() failed. No need to call SQLDisconnect().  
            }  
        }  
        WaitForMultipleObjects(NUMBER_OPERATIONS, arhDBCEvent, TRUE, INFINITE);   
        for (int i=0; i<NUMBER_OPERATIONS; i++)  
        {  
            if (SQL_SUCCEEDED(arrcDBC[i]) )   
            {     
                SQLCompleteAsync(SQL_HANDLE_DBC, arhDbc[i], &arrcDBC[i]);; // To Complete  
            }  
        }  
  
        goto Cleanup;  
    }  
  
    // Statement Operations begin here  
  
    // Alloc statement handle  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc = SQLAllocHandle(SQL_HANDLE_STMT, arhDbc[i], &arhStmt[i]);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Enable STMT Async on all statement handles  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc = SQLSetStmtAttr(arhStmt[i], SQL_ATTR_ASYNC_ENABLE, (SQLPOINTER)SQL_ASYNC_ENABLE_ON, SQL_IS_INTEGER);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Create event objects  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        arhSTMTEvent[i] = CreateEvent(NULL, FALSE, FALSE, NULL); // Auto-reset, initial state is not-signaled  
        if (!arhSTMTEvent[i]) goto Cleanup;  
    }  
  
    // Enable notification on all statement handles  
    // Event  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc= SQLSetStmtAttr(arhStmt[i], SQL_ATTR_ASYNC_STMT_EVENT, arhSTMTEvent[i], SQL_IS_POINTER);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Initiate SQLExecDirect() calls  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLExecDirect(arhStmt[i], (SQLTCHAR*)TEXT("select au_lname, au_fname from authors"), SQL_NTS);  
    }  
  
    // Can do some other staff before calling WaitForMultipleObjects  
    WaitForMultipleObjects(NUMBER_OPERATIONS, arhSTMTEvent, TRUE, INFINITE); // Wait All  
  
    // Now, call SQLCompleteAsync to complete the operation and get return code  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLCompleteAsync(SQL_HANDLE_STMT, arhStmt[i], &arrcSTMT[i]);  
    }  
  
    // Check return values  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if ( !SQL_SUCCEEDED(arrcSTMT[i]) ) goto Cleanup;  
    }  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        //Do some binding jobs here, set SQL_ATTR_ROW_ARRAY_SIZE   
    }  
  
    // Now, initiate fetching  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLFetch(arhStmt[i]);  
    }  
  
    // Can do some other staff before calling WaitForMultipleObjects  
    WaitForMultipleObjects(NUMBER_OPERATIONS, arhSTMTEvent, TRUE, INFINITE);   
  
    // Now, to complete the operations and get return code  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLCompleteAsync(SQL_HANDLE_STMT, arhStmt[i], &arrcSTMT[i]);  
    }  
  
    // Check return code  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if ( !SQL_SUCCEEDED(arrcSTMT[i]) ) goto Cleanup;  
    }  
  
    // USE fetched data here!!  
  
Cleanup:  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if (arhStmt[NUMBER_OPERATIONS])  
        {  
            SQLFreeHandle(SQL_HANDLE_STMT, arhStmt[i]);  
            arhStmt[i] = NULL;  
        }  
    }  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if (arhSTMTEvent[i])  
        {  
            CloseHandle(arhSTMTEvent[i]);  
            arhSTMTEvent[i] = NULL;  
        }  
    }  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if (arhDbc[i])  
        {  
            SQLFreeHandle(SQL_HANDLE_DBC, arhDbc[i]);  
            arhDbc[i] = NULL;  
        }  
    }  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if (arhDBCEvent[i])  
        {  
            CloseHandle(arhDBCEvent[i]);  
            arhDBCEvent[i] = NULL;  
        }  
    }  
  
    if (hEnv)  
    {  
        SQLFreeHandle(SQL_HANDLE_ENV, hEnv);  
        hEnv = NULL;  
    }  
  
    return 0;  
}  
  
```  
  
### <a name="determining-if-a-driver-supports-asynchronous-notification"></a>Determinare se un Driver supporta la notifica asincrona  
 Un'applicazione ODBC è possibile determinare se un driver ODBC supporta la notifica asincrona chiamando [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md). Gestione Driver ODBC di conseguenza chiamerà il **SQLGetInfo** del driver con SQL_ASYNC_NOTIFICATION.  
  
```  
SQLUINTEGER InfoValue;  
SQLLEN      cbInfoLength;  
  
SQLRETURN retcode;  
retcode = SQLGetInfo (hDbc,   
                      SQL_ASYNC_NOTIFICATION,   
                      &InfoValue,  
                      sizeof(InfoValue),  
                      NULL);  
if (SQL_SUCCEEDED(retcode))  
{  
if (SQL_ASYNC_NOTIFICATION_CAPABLE == InfoValue)  
      {  
          // The driver supports asynchronous notification  
      }  
      else if (SQL_ASYNC_NOTIFICATION_NOT_CAPABLE == InfoValue)  
      {  
          // The driver does not support asynchronous notification  
      }  
}  
```  
  
### <a name="associating-a-win32-event-handle-with-an-odbc-handle"></a>Associazione di un Handle di evento Win32 con un Handle ODBC  
 Le applicazioni sono responsabili della creazione di oggetti evento Win32 utilizzando le funzioni Win32 corrispondente. Un'applicazione è possibile associare un handle di evento Win32 a un handle di connessione ODBC o un handle di istruzione ODBC.  
  
 Attributi di connessione SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE e SQL_ATTR_ASYNC_DBC_EVENT determinano se ODBC viene eseguito in modalità asincrona e se ODBC attiva la modalità di notifica per un handle di connessione. Gli attributi di istruzione SQL_ATTR_ASYNC_ENABLE e SQL_ATTR_ASYNC_STMT_EVENT determinano se ODBC viene eseguito in modalità asincrona e se ODBC attiva la modalità di notifica per un handle di istruzione.  
  
|SQL_ATTR_ASYNC_ENABLE o SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE|SQL_ATTR_ASYNC_STMT_EVENT o SQL_ATTR_ASYNC_DBC_EVENT|Mode|  
|-------------------------------------------------------------------------|-------------------------------------------------------------------|----------|  
|Abilitare|non null|Notifica asincrona|  
|Abilitare|null|Asincrono di Polling|  
|Disable|any|Sincrona|  
  
 Un'applicazione può disabilitare temporaneamente in modalità asincrona. ODBC ignora i valori di SQL_ATTR_ASYNC_DBC_EVENT se l'operazione asincrona livello di connessione è disabilitata. ODBC ignora i valori di SQL_ATTR_ASYNC_STMT_EVENT se l'operazione asincrona livello di istruzione è disabilitata.  
  
 Chiamata sincrona di **SQLSetStmtAttr** e **SQLSetConnectAttr**  
 -   **La funzione SQLSetConnectAttr** supporta operazioni asincrone, ma la chiamata di **SQLSetConnectAttr** impostare SQL_ATTR_ASYNC_DBC_EVENT è sempre sincrono.  
  
-   **SQLSetStmtAttr** non supporta l'esecuzione asincrona.  
  
 Scenario di errore-out  
 Quando **SQLSetConnectAttr** viene chiamato prima di effettuare una connessione, gestione Driver non è possibile determinare quale driver da utilizzare. Di conseguenza, gestione Driver restituisce l'esito positivo per **SQLSetConnectAttr** ma l'attributo potrebbe non essere possibile impostare nel driver. Gestione Driver imposterà questi attributi quando l'applicazione chiama una funzione di connessione. Gestione Driver potrebbe errore in uscita perché il driver non supporta operazioni asincrone.  
  
 Ereditarietà degli attributi di connessione  
 In genere, le istruzioni di una connessione erediteranno gli attributi di connessione. Tuttavia, l'attributo SQL_ATTR_ASYNC_DBC_EVENT non è ereditabile e interessa solo le operazioni di connessione.  
  
 Per associare un handle di evento a un handle di connessione ODBC, un'applicazione ODBC chiama l'API ODBC **SQLSetConnectAttr** e specifica SQL_ATTR_ASYNC_DBC_EVENT come l'attributo e l'evento da gestire come valore dell'attributo. Il nuovo attributo ODBC SQL_ATTR_ASYNC_DBC_EVENT è di tipo SQL_IS_POINTER.  
  
```  
HANDLE hEvent;  
hEvent = CreateEvent(   
            NULL,                // default security attributes  
            FALSE,               // auto-reset event  
            FALSE,               // initial state is non-signaled  
            NULL                 // no name  
            );  
```  
  
 In genere, le applicazioni creare oggetti evento di reimpostazione automatica. ODBC non verranno reimpostate l'oggetto evento. Le applicazioni devono assicurarsi che l'oggetto non è in stato segnalato prima di chiamare una funzione ODBC asincrona.  
  
```  
SQLRETURN retcode;  
retcode = SQLSetConnectAttr ( hDBC,  
                              SQL_ATTR_ASYNC_DBC_EVENT, // Attribute name  
                              (SQLPOINTER) hEvent,      // Win32 Event handle  
                              SQL_IS_POINTER);          // Length Indicator  
```  
  
 SQL_ATTR_ASYNC_DBC_EVENT è un attributo di sola gestione Driver che non vengano impostato nel driver.  
  
 Il valore predefinito di SQL_ATTR_ASYNC_DBC_EVENT è NULL. Se il driver non supporta la notifica asincrona, ottenere o impostare SQL_ATTR_ASYNC_DBC_EVENT restituirà SQL_ERROR con SQLSTATE HY092 (identificatore di attributo/opzione non valida).  
  
 Se l'ultimo valore SQL_ATTR_ASYNC_DBC_EVENT impostato su un handle di connessione ODBC non è NULL e l'applicazione attivata la modalità asincrona impostando l'attributo SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE con SQL_ASYNC_DBC_ENABLE_ON, la chiamata a qualsiasi connessione ODBC funzione che supporta la modalità asincrona riceverà una notifica di completamento. Se l'ultimo valore SQL_ATTR_ASYNC_DBC_EVENT impostato su un handle di connessione ODBC è NULL, ODBC non verrà inviato all'applicazione le notifiche, indipendentemente dal fatto che se è abilitata la modalità asincrona.  
  
 Un'applicazione può impostare SQL_ATTR_ASYNC_DBC_EVENT prima o dopo l'impostazione dell'attributo SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE.  
  
 Le applicazioni possono impostare l'attributo SQL_ATTR_ASYNC_DBC_EVENT su un handle di connessione ODBC prima di chiamare una funzione di connessione (**SQLConnect**, **SQLBrowseConnect**, o  **SQLDriverConnect**). Poiché gestione Driver ODBC non conosce il driver ODBC verrà utilizzato dall'applicazione, verrà restituito SQL_SUCCESS. Quando l'applicazione chiama una funzione di connessione, gestione Driver ODBC verifica se il driver supporta la notifica asincrona. Se il driver non supporta la notifica asincrona, gestione Driver ODBC restituisce SQL_ERROR con SQLSTATE S1_118 (Driver non supporta la notifica asincrona). Se il driver supporta la notifica asincrona, gestione Driver ODBC verrà chiamare il driver e impostare gli attributi corrispondenti SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK e SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT.  
  
 Analogamente, un'applicazione chiama **SQLSetStmtAttr** su un'istruzione ODBC gestire e specifica l'attributo SQL_ATTR_ASYNC_STMT_EVENT per abilitare o disabilitare la notifica asincrona livello di istruzione. Poiché una funzione di istruzione viene sempre chiamata una volta stabilita la connessione, **SQLSetStmtAttr** restituirà SQL_ERROR con SQLSTATE S1_118 (Driver non supporta la notifica asincrona) immediatamente se corrispondente driver non supporta operazioni asincrone o il driver supporta l'operazione asincrona, ma non supporta la notifica asincrona.  
  
```  
SQLRETURN retcode;  
retcode = SQLSetStmtAttr ( hSTMT,  
                           SQL_ATTR_ASYNC_STMT_EVENT, // Attribute name   
                           (SQLPOINTER) hEvent,       // Win32 Event handle  
                           SQL_IS_POINTER);           // length Indicator  
```  
  
 SQL_ATTR_ASYNC_STMT_EVENT, che può essere impostata su NULL, è un attributo di sola gestione Driver che non vengano impostato nel driver.  
  
 Il valore predefinito di SQL_ATTR_ASYNC_STMT_EVENT è NULL. Se il driver non supporta la notifica asincrona, ottenere o impostare l'attributo SQL_ATTR_ASYNC_ STMT_EVENT restituirà SQL_ERROR con SQLSTATE HY092 (identificatore di attributo/opzione non valida).  
  
 Un'applicazione deve associare lo stesso handle di evento con più di un handle ODBC. In caso contrario, una notifica andranno persi se due chiamate di funzione ODBC asincrone completata su due handle che condividono lo stesso handle di evento. Per evitare un handle di istruzione eredita sullo stesso handle di evento da handle di connessione, se un'applicazione imposta SQL_ATTR_ASYNC_STMT_EVENT su un handle di connessione ODBC restituisce SQL_ERROR con SQLSTATE IM016 (Impossibile impostare attributi di istruzione nell'handle di connessione).  
  
### <a name="calling-asynchronous-odbc-functions"></a>Chiamata di funzioni ODBC asincrona  
 Dopo aver attivato la notifica asincrona e iniziare un'operazione asincrona, l'applicazione può chiamare una funzione ODBC. Se la funzione appartiene al set di funzioni che supportano l'operazione asincrona, l'applicazione verrà visualizzata una notifica di completamento al termine dell'operazione, indipendentemente dal fatto che indica se la funzione non è riuscita o è stato completato.  L'unica eccezione è che l'applicazione chiama una funzione ODBC con un handle di istruzione o di connessione non valido. In questo caso, ODBC non otterrà l'handle dell'evento e impostarla sullo stato segnalato.  
  
 L'applicazione deve garantire che l'oggetto evento associato è in uno stato non segnalato prima di avviare un'operazione asincrona dell'handle ODBC corrispondente. ODBC non verranno reimpostate l'oggetto evento.  
  
### <a name="getting-notification-from-odbc"></a>Ricevere una notifica da ODBC  
 Un thread dell'applicazione può chiamare **WaitForSingleObject** in attesa di handle di un evento o chiamata **WaitForMultipleObjects** di attesa su una matrice di handle di evento e sospesa fino a uno o tutti gli oggetti evento la segnalazione o l'intervallo di timeout scade.  
  
```  
DWORD dwStatus = WaitForSingleObject(  
                        hEvent,  // The event associated with the ODBC handle  
                        5000     // timeout is 5000 millisecond   
);  
  
If (dwStatus == WAIT_TIMEOUT)  
{  
    // time-out interval elapsed before all the events are signaled.   
}  
Else  
{  
    // Call the corresponding Asynchronous ODBC API to complete all processing and retrieve the return code.  
}  
```
