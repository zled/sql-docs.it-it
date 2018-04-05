---
title: Funzione SQLAllocHandle | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
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
- SQLAllocHandle
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLAllocHandle
helpviewer_keywords:
- SQLAllocHandle function [ODBC]
ms.assetid: 6e7fe420-8cf4-4e72-8dad-212affaff317
caps.latest.revision: 43
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: b8bf173bf0055dc06cf475aa72e137d9ca426222
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sqlallochandle-function"></a>SQLAllocHandle-funzione
**Conformità**  
 Introdotta: versione ODBC 3.0 aderenza: 92 ISO  
  
 **Riepilogo**  
 **SQLAllocHandle** alloca un handle di ambiente, connessione, istruzione o descrittore.  
  
> [!NOTE]  
>  Questa funzione è una funzione generica per allocare gli handle che sostituisce le funzioni ODBC 2.0 **SQLAllocConnect**, **SQLAllocEnv**, e **SQLAllocStmt**. Per consentire alle applicazioni chiamata **SQLAllocHandle** per funzionare con ODBC 2. *x* driver, una chiamata a **SQLAllocHandle** viene eseguito il mapping in Gestione Driver per **SQLAllocConnect**, **SQLAllocEnv**, o  **SQLAllocStmt**, a seconda dei casi. Per ulteriori informazioni, vedere "Commenti". Per ulteriori informazioni su quali il Driver Manager esegue il mapping di questa funzione per quando un'applicazione ODBC 3. *x* applicazione sta utilizzando un'API ODBC 2. *x* driver, vedere [Mapping di funzioni di sostituzione per la compatibilità con le versioni precedenti di applicazioni](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLAllocHandle(  
      SQLSMALLINT   HandleType,  
      SQLHANDLE     InputHandle,  
      SQLHANDLE *   OutputHandlePtr);  
```  
  
## <a name="arguments"></a>Argomenti  
 *HandleType*  
 [Input] Il tipo di handle deve essere allocata da **SQLAllocHandle**. Deve essere uno dei valori seguenti:  
  
-   IMPOSTATO SU SQL_HANDLE_DBC  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   IMPOSTATO SU SQL_HANDLE_ENV  
  
-   IMPOSTATO SU SQL_HANDLE_STMT  
  
 Handle SQL_HANDLE_DBC_INFO_TOKEN è utilizzato solo da Gestione Driver e driver. Applicazioni non devono utilizzare questo tipo di handle. Per ulteriori informazioni su SQL_HANDLE_DBC_INFO_TOKEN, vedere [consapevolezza Pool di connessioni lo sviluppo di un Driver ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
 *InputHandle*  
 [Input] L'handle di input nel cui contesto è necessario allocare nuovo handle. Se *HandleType* è impostato su SQL_HANDLE_ENV, si tratta di SQL_NULL_HANDLE. Se *HandleType* è impostato su SQL_HANDLE_DBC, deve trattarsi di un handle di ambiente e se è impostato su SQL_HANDLE_STMT o SQL_HANDLE_DESC, deve essere un handle di connessione.  
  
 *OutputHandlePtr*  
 [Output] Puntatore a un buffer in cui restituire l'handle per la struttura di dati appena allocato.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_INVALID_HANDLE o SQL_ERROR.  
  
 Quando si alloca un handle diverso da un handle di ambiente, se **SQLAllocHandle** restituisce SQL_ERROR, imposta *OutputHandlePtr* SQL_NULL_HDBC, SQL_NULL_HSTMT o SQL_NULL_HDESC, a seconda di valore di *HandleType*, a meno che l'argomento di output è un puntatore null. L'applicazione può quindi ottenere informazioni aggiuntive dalla struttura di dati di diagnostica associata all'handle nel *InputHandle* argomento.  
  
## <a name="environment-handle-allocation-errors"></a>Errori di allocazione di Handle di ambiente  
 Allocazione di ambiente si verifica all'interno di gestione Driver e all'interno di ogni driver. L'errore restituito da **SQLAllocHandle** con un *HandleType* impostato su SQL_HANDLE_ENV dipende dal livello in cui si è verificato l'errore.  
  
 Se Gestione Driver non è possibile allocare memoria per  *\*OutputHandlePtr* quando **SQLAllocHandle** con un *HandleType* impostato su SQL_HANDLE_ENV viene chiamato, o l'applicazione fornisce un puntatore null per *OutputHandlePtr*, **SQLAllocHandle** restituisce SQL_ERROR. Gestione Driver imposta **OutputHandlePtr* a SQL_NULL_HENV (a meno che l'applicazione è specificato un puntatore null, che restituisce SQL_ERROR). Non c'è alcun handle a cui associare informazioni diagnostiche aggiuntive.  
  
 Gestione Driver non chiama la funzione di allocazione di handle di ambiente a livello di driver fino a quando l'applicazione chiama **SQLConnect**, **SQLBrowseConnect**, o **SQLDriverConnect**. Se si verifica un errore a livello di driver **SQLAllocHandle** (funzione), quindi il livello di gestione Driver: **SQLConnect**, **SQLBrowseConnect**, o  **SQLDriverConnect** funzione restituisce SQL_ERROR. La struttura di dati di diagnostica contiene IM004 SQLSTATE (patente **SQLAllocHandle** non riuscita). Viene restituito l'errore su un handle di connessione.  
  
 Per ulteriori informazioni sul flusso di chiamate di funzione tra gestione Driver e un driver, vedere [funzione SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLAllocHandle** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato possono essere ottenuti chiamando **SQLGetDiagRec** con l'appropriato *HandleType* e *gestire* impostato sul valore di *InputHandle*. SQL_SUCCESS_WITH_INFO (ma non SQL_ERROR) possono essere restituite per il *OutputHandle* argomento. Nella tabella seguente sono elencati i valori SQLSTATE normalmente restituiti dal **SQLAllocHandle** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|08003|Connessione non aperta|(DM) il *HandleType* argomento è stato impostato su SQL_HANDLE_STMT o SQL_HANDLE_DESC, ma la connessione specificata per il *InputHandle* argomento non è aperto. Il processo di connessione deve essere completato (e la connessione deve essere aperta) per il driver ad allocare un'istruzione o un descrittore di handle.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel **MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|La gestione di Driver (DM) non è riuscita ad allocare memoria per l'handle specificato.<br /><br /> Il driver non è riuscito ad allocare memoria per l'handle specificato.|  
|HY009|Utilizzo non valido del puntatore null|(DM) il *OutputHandlePtr* argomento è un puntatore null.|  
|HY010|Errore nella sequenza (funzione)|(DM) il *HandleType* argomento è stato impostato su SQL_HANDLE_DBC, e **SQLSetEnvAttr** non è stato chiamato per impostare l'attributo di ambiente SQL_ODBC_VERSION.<br /><br /> (DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione il **InputHandle** ed era ancora in esecuzione quando il **SQLAllocHandle** funzione è stata chiamata con **HandleType** impostato impostato su SQL_HANDLE_STMT o SQL_HANDLE_DESC.|  
|HY013|Errore di gestione della memoria|Il *HandleType* argomento è stato impostato su SQL_HANDLE_DBC, impostato su SQL_HANDLE_STMT o SQL_HANDLE_DESC; e la chiamata di funzione non può essere elaborata perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di memoria insufficiente condizioni.|  
|HY014|Il numero di handle ha superato il limite|Il limite definito dal driver per il numero di handle che può essere allocata per il tipo di handle indicato dal *HandleType* argomento è stato raggiunto.|  
|HY092|Identificatore di attributo/opzione non valida|(DM) il *HandleType* argomento non è stato: impostato su SQL_HANDLE_ENV, impostato su SQL_HANDLE_DBC, impostato su SQL_HANDLE_STMT o SQL_HANDLE_DESC.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Funzionalità facoltativa non implementata.|Il *HandleType* argomento è stato SQL_HANDLE_DESC e il driver non è un'API ODBC 2. *x* driver.|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|(DM) il *HandleType* argomento è stato impostato su SQL_HANDLE_STMT e il driver non è un driver ODBC valido.<br /><br /> (DM) il *HandleType* argomento è stato SQL_HANDLE_DESC e il driver non supporta l'allocazione di un handle descrittore.|  
  
## <a name="comments"></a>Commenti  
 **SQLAllocHandle** viene utilizzata per allocare gli handle per gli ambienti, le connessioni, istruzioni e descrittori, come descritto nelle sezioni seguenti. Per informazioni generali sugli handle, vedere [handle](../../../odbc/reference/develop-app/handles.md).  
  
 Più di un handle di ambiente, connessione o dell'istruzione può essere allocato da un'applicazione in un momento se più allocazioni sono supportate dal driver. In ODBC, è definito alcun limite al numero di ambiente, connessione, istruzione o handle di descrittore allocato in qualsiasi momento. I driver possono imporre un limite al numero di un determinato tipo di handle che può essere allocata alla volta. Per ulteriori informazioni, vedere la documentazione del driver.  
  
 Se l'applicazione chiama **SQLAllocHandle** con  *\*OutputHandlePtr* impostato su un ambiente, connessione, l'istruzione o handle di descrittore che esiste già, il driver sovrascrive il le informazioni associate di *gestire*, a meno che l'applicazione sta utilizzando una connessione del pool di connessioni (vedere "Allocazione di un ambiente di attributo per il pool di connessioni" più avanti in questa sezione). Gestione Driver consente di verificare se il *gestire* immesso  *\*OutputHandlePtr* è già in uso, né lo fa controllare il contenuto di un handle precedente prima di sovrascriverli .  
  
> [!NOTE]  
>  Si tratta di programmazione di applicazioni ODBC non corretta per chiamare **SQLAllocHandle** due volte con la stessa variabile di applicazione definita per  *\*OutputHandlePtr* senza chiamare  **SQLFreeHandle** per liberare l'handle prima di riallocazione. Sovrascrittura ODBC gestisce in modo potrebbero causare un comportamento incoerente o errori da parte di driver ODBC.  
  
 Nei sistemi operativi che supportano più thread, le applicazioni possono utilizzare lo stesso handle di ambiente, connessione, istruzione o descrittore in thread diversi. I driver devono supportare pertanto accedere multithread-safe a queste informazioni. un modo per eseguire questa operazione, è ad esempio, tramite un semaforo o una sezione critica. Per ulteriori informazioni sul threading, vedere [Multithreading](../../../odbc/reference/develop-app/multithreading.md).  
  
 **SQLAllocHandle** non impostare l'attributo di ambiente SQL_ATTR_ODBC_VERSION quando viene chiamata per allocare un handle di ambiente; l'attributo di ambiente deve essere impostato dall'applicazione oppure SQLSTATE HY010 sarà (errore di sequenza di funzioni) restituito quando **SQLAllocHandle** viene chiamata per allocare un handle di connessione.  
  
 Per le applicazioni conformi agli standard, **SQLAllocHandle** viene eseguito il mapping a **SQLAllocHandleStd** in fase di compilazione. La differenza tra queste due funzioni è che **SQLAllocHandleStd** impostato l'attributo di ambiente SQL_ATTR_ODBC_VERSION SQL_OV_ODBC3 quando viene chiamato con il *HandleType* argomento impostato su SQL _HANDLE_ENV. Questo avviene perché le applicazioni conformi agli standard sono sempre ODBC 3. *x* applicazioni. Inoltre, gli standard non richiedono la versione dell'applicazione da registrare. Questo è l'unica differenza tra queste due funzioni. in caso contrario, sono identici. **SQLAllocHandleStd** viene eseguito il mapping a **SQLAllocHandle** all'interno di Gestione driver. Di conseguenza, i driver di terze parti non è necessario implementare **SQLAllocHandleStd**.  
  
 Le applicazioni ODBC 3.8 dovrebbe usare:  
  
-   **SQLAllocHandle e non SQLAllocHandleStd** per allocare un handle di ambiente.  
  
-   **SQLSetEnvAttr** per impostare l'attributo di ambiente SQL_ATTR_ODBC_VERSION SQL_OV_ODBC3_80.  
  
## <a name="allocating-an-environment-handle"></a>Allocazione di un handle di ambiente  
 Un handle di ambiente fornisce accesso alle informazioni globali come handle di connessione valida e connessione attiva. Per informazioni generali sull'handle di ambiente, vedere [handle di ambiente](../../../odbc/reference/develop-app/environment-handles.md).  
  
 Per richiedere un handle di ambiente, un'applicazione chiama **SQLAllocHandle** con un *HandleType* impostato su SQL_HANDLE_ENV e un *InputHandle* di SQL_NULL_HANDLE. Il driver alloca memoria per le informazioni sull'ambiente e passa il valore di handle associato nuovamente il  *\*OutputHandlePtr* argomento. Passa l'applicazione di  *\*OutputHandle* valore in tutte le chiamate successive che richiedono un argomento dell'handle di ambiente. Per ulteriori informazioni, vedere [allocare l'Handle di ambiente](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).  
  
 In un Driver dell'ambiente di gestione, se esiste già handle di ambiente di un driver, quindi **SQLAllocHandle** con un *HandleType* impostato su SQL_HANDLE_ENV non viene chiamato nel driver quando un connessione viene eseguita solo **SQLAllocHandle** con un *HandleType* impostato su SQL_HANDLE_DBC. Se non esiste alcun handle di ambiente patente con handle di ambiente di gestione Driver, nel driver vengono chiamati SQLAllocHandle con un HandleType su SQL_HANDLE_ENV sia SQLAllocHandle con un HandleType su SQL_HANDLE_DBC quando la prima connessione handle dell'ambiente è connessa al driver.  
  
 Quando Gestione Driver elabora il **SQLAllocHandle** funzione con un *HandleType* impostato su SQL_HANDLE_ENV, controlla la **traccia** (parola chiave) nella sezione del sistema [ODBC] informazioni. Se è impostato su 1, gestione Driver abilita la traccia per l'applicazione corrente. Se è impostato il flag di traccia, traccia inizia quando il primo handle di ambiente viene allocato e termina quando l'ultimo handle di ambiente viene liberata. Per ulteriori informazioni, vedere [origini dati di configurazione](../../../odbc/reference/install/configuring-data-sources.md).  
  
 Dopo aver allocato un handle di ambiente, un'applicazione deve chiamare **SQLSetEnvAttr** dell'handle di ambiente per impostare l'attributo di ambiente SQL_ATTR_ODBC_VERSION. Se questo attributo non viene impostato prima **SQLAllocHandle** viene chiamata per allocare un handle di connessione all'ambiente, la chiamata di allocare la connessione restituisce SQLSTATE HY010 (funzione di errore nella sequenza). Per ulteriori informazioni, vedere [la dichiarazione ODBC versione dell'applicazione](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md).  
  
## <a name="allocating-shared-environments-for-connection-pooling"></a>Allocazione di ambienti condivisi per il pool di connessioni  
 Gli ambienti possono essere condivise tra più componenti in un singolo processo. Un ambiente condiviso può essere utilizzato da più di un componente nello stesso momento. Quando un componente utilizza un ambiente condiviso, è possibile utilizzare le connessioni in pool, che consentono di allocare e utilizzare una connessione esistente senza ricreare la connessione.  
  
 Prima di allocare un ambiente condiviso che può essere utilizzato per il pool di connessioni, un'applicazione deve chiamare **SQLSetEnvAttr** per impostare l'attributo di ambiente SQL_ATTR_CONNECTION_POOLING SQL_CP_ONE_PER_DRIVER o SQL_CP_ONE_PER_ HENV. **SQLSetEnvAttr** in questo caso, viene chiamato con *EnvironmentHandle* impostato su null, che rende l'attributo di un attributo a livello di processo.  
  
 Dopo aver abilitato il pool di connessioni, un'applicazione chiama **SQLAllocHandle** con il *HandleType* argomento impostato su SQL_HANDLE_ENV. L'ambiente allocato da questa chiamata sarà un ambiente condiviso implicito perché il pool di connessioni è stato abilitato.  
  
 Quando viene allocato un ambiente condiviso, l'ambiente da utilizzare viene determinata solo **SQLAllocHandle** con un *HandleType* impostato su SQL_HANDLE_DBC viene chiamato. A questo punto, gestione Driver tenta di trovare un ambiente esistente che corrisponde agli attributi di ambiente richiesti dall'applicazione. Se l'ambiente non esiste, ne viene creato come un ambiente condiviso. Gestione Driver mantiene un conteggio dei riferimenti per ogni ambiente condiviso. il conteggio è impostato su 1 quando si crea l'ambiente. Se viene trovato un ambiente corrispondente, viene restituito l'handle di ambiente per l'applicazione e il conteggio dei riferimenti viene incrementato. Un handle di ambiente allocato in questo modo può essere utilizzato in una funzione ODBC che accetta un handle di ambiente come argomento di input.  
  
## <a name="allocating-a-connection-handle"></a>Allocazione di un handle di connessione  
 Un handle di connessione fornisce l'accesso a informazioni quali l'istruzione valido e aprire gli handle di descrittore nella connessione e indica se una transazione è attualmente. Per informazioni generali sugli handle di connessione, vedere [handle di connessione](../../../odbc/reference/develop-app/connection-handles.md).  
  
 Per richiedere un handle di connessione, un'applicazione chiama **SQLAllocHandle** con un *HandleType* impostato su SQL_HANDLE_DBC. Il *InputHandle* argomento è impostato per l'handle di ambiente che è stato restituito dalla chiamata a **SQLAllocHandle** che allocata tale handle. Il driver alloca memoria per la connessione e passa il valore di handle associato nuovamente  *\*OutputHandlePtr*. Passa l'applicazione di  *\*OutputHandlePtr* valore in tutte le chiamate successive che richiedono un handle di connessione. Per ulteriori informazioni, vedere [allocare un Handle di connessione](../../../odbc/reference/develop-app/allocating-a-connection-handle-odbc.md).  
  
 Gestione Driver elabora il **SQLAllocHandle** funzione e il driver chiama **SQLAllocHandle** funzione quando l'applicazione chiama **SQLConnect**, **SQLBrowseConnect**, o **SQLDriverConnect**. (Per ulteriori informazioni, vedere [funzione SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md).)  
  
 Se l'attributo di ambiente SQL_ATTR_ODBC_VERSION non viene impostato prima **SQLAllocHandle** viene chiamata per allocare un handle di connessione all'ambiente, la chiamata di allocare la connessione restituisce SQLSTATE HY010 (funzione di sequenza Errore).  
  
 Quando un'applicazione chiama **SQLAllocHandle** con il *InputHandle* argomento impostato su SQL_HANDLE_DBC e inoltre impostata su un handle di ambiente condiviso, gestione Driver tenta di trovare un oggetto condiviso esistente ambiente che corrisponde agli attributi di ambiente impostati dall'applicazione. Se l'ambiente non esiste, uno viene creato, con un conteggio dei riferimenti (gestito da Gestione Driver) pari a 1. Se una corrispondenza condiviso viene trovato l'ambiente, tale handle viene restituito all'applicazione e il conteggio dei riferimenti viene incrementato.  
  
 Da Gestione Driver fino a quando non è determinata l'effettiva connessione che verrà utilizzata **SQLConnect** o **SQLDriverConnect** viene chiamato. Gestione Driver utilizza le opzioni di connessione nella chiamata a **SQLConnect** (o le parole chiave di connessione nella chiamata a **SQLDriverConnect**) e impostare gli attributi di connessione dopo l'allocazione di connessione a stabilire la connessione nel pool di deve essere utilizzata. Per ulteriori informazioni, vedere [funzione SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
## <a name="allocating-a-statement-handle"></a>Allocazione di un handle di istruzione  
 Un handle di istruzione consente di accedere alle informazioni di istruzione, ad esempio i messaggi di errore, il nome del cursore e le informazioni sullo stato per l'elaborazione di istruzione SQL. Per informazioni generali sull'handle di istruzione, vedere [handle di istruzione](../../../odbc/reference/develop-app/statement-handles.md).  
  
 Per richiedere un handle di istruzione, un'applicazione si connette a un'origine dati e quindi chiama **SQLAllocHandle** prima di inviare istruzioni SQL. In questa chiamata, *HandleType* deve essere impostato su SQL_HANDLE_STMT come e *InputHandle* deve essere impostato per l'handle di connessione che è stato restituito dalla chiamata a **SQLAllocHandle** che allocato tale handle. Il driver alloca memoria per le informazioni di istruzione, associa l'handle di istruzione con la connessione specificata e passa il valore di handle associato nuovamente  *\*OutputHandlePtr*. Passa l'applicazione di  *\*OutputHandlePtr* valore in tutte le chiamate successive che richiedono un handle di istruzione. Per ulteriori informazioni, vedere [allocare un Handle di istruzione](../../../odbc/reference/develop-app/allocating-a-statement-handle-odbc.md).  
  
 Quando viene allocato l'handle di istruzione, il driver automaticamente alloca un set di descrittori di quattro e assegna gli handle per i descrittori di SQL_ATTR_APP_ROW_DESC, SQL_ATTR_APP_PARAM_DESC, SQL_ATTR_IMP_ROW_DESC e SQL_ATTR_IMP_PARAM_DESC attributi di istruzione. Queste sono denominate *in modo implicito* allocata descrittori. Per allocare in modo esplicito un descrittore di applicazione, vedere la sezione seguente, "Allocare un Handle di descrittore".  
  
## <a name="allocating-a-descriptor-handle"></a>Allocazione di un Handle di descrittore  
 Quando un'applicazione chiama **SQLAllocHandle** con un *HandleType* di SQL_HANDLE_DESC, il driver alloca un descrittore di applicazione. Queste sono denominate *in modo esplicito* allocata descrittori. L'applicazione indirizza un driver di utilizzare un descrittore allocato in modo esplicito dell'applicazione anziché una allocato automaticamente per un handle di istruzione specificato chiamando il **SQLSetStmtAttr** con il SQL_ATTR_APP_ROW_DESC (funzione) attributo SQL_ATTR_APP_PARAM_DESC o. Un descrittore di implementazione non può essere allocato in modo esplicito, né un descrittore di implementazione può essere specificato in un **SQLSetStmtAttr** chiamata di funzione.  
  
 Descrittori allocati in modo esplicito sono associati a un handle di connessione anziché un handle di istruzione (come descrittori allocati automaticamente). Descrittori rimangono pertanto allocati solo quando un'applicazione è connessa al database. Perché un handle di connessione associati descrittori allocati in modo esplicito, un'applicazione è possibile associare un descrittore allocato in modo esplicito a più di un'istruzione all'interno di una connessione. Un descrittore di applicazione in modo implicito allocato, d'altra parte, non può essere associato a più di un handle di istruzione. (Non può essere associata a un handle di istruzione diverso da quello che è stato allocato per.) Gli handle di descrittore allocato in modo esplicito possono essere liberati in modo esplicito dall'applicazione o chiamando **SQLFreeHandle** con un *HandleType* di SQL_HANDLE_DESC o in modo implicito quando la connessione è chiuso.  
  
 Quando viene liberato il descrittore allocato in modo esplicito, il descrittore allocato in modo implicito è associato con l'istruzione. (L'attributo SQL_ATTR_APP_ROW_DESC o SQL_ATTR_APP_PARAM_DESC per l'istruzione è impostata nuovamente all'handle di descrittore allocato in modo implicito). Questo vale per tutte le istruzioni che sono state associate con il descrittore allocato in modo esplicito per la connessione.  
  
 Per ulteriori informazioni sui descrittori, vedere [descrittori](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="code-example"></a>Esempio di codice  
 Vedere [ODBC programma di esempio](../../../odbc/reference/sample-odbc-program.md), [funzione SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md), [funzione SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md), e [funzione SQLSetCursorName](../../../odbc/reference/syntax/sqlsetcursorname-function.md).  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Esecuzione di un'istruzione SQL|[Funzione SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|L'esecuzione di un'istruzione SQL preparata|[Funzione SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Liberare un handle di ambiente, connessione, istruzione o descrittore|[Funzione SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|Preparazione di un'istruzione per l'esecuzione|[Funzione SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|L'impostazione di un attributo di connessione|[Funzione SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|L'impostazione di un campo di descrizione|[Funzione SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|L'impostazione di un attributo di ambiente|[Funzione SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|  
|L'impostazione di un attributo di istruzione|[Funzione SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
