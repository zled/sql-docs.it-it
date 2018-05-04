---
title: L'aggiornamento di un Driver 3.5 a un Driver 3.8 | Documenti Microsoft
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
ms.assetid: ffba36ac-d22e-40b9-911a-973fa9e10bd3
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 15a97c470d18bab1d5c62e1f2c194ba9f69b20b3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="upgrading-a-35-driver-to-a-38-driver"></a>L'aggiornamento di un Driver 3.5 a un Driver 3.8
In questo argomento vengono fornite indicazioni e considerazioni per l'aggiornamento di un driver ODBC 3.5 a un driver ODBC 3.8.  
  
##### <a name="version-numbers"></a>Numeri di versione  
 Le linee guida seguenti si riferiscono ai numeri di versione:  
  
-   Un driver deve supportare SQL_OV_ODBC3_80 per SQL_ATTR_ODBC_VERSION, restituzione di SQL_ERROR per valori diversi da SQL_OV_ODBC2 SQL_OV_ODBC3 e SQL_OV_ODBC3_80. Le versioni future di gestione Driver presuppone che un driver supporta un livello di conformità ODBC, se il driver restituisce SQL_SUCCESS da [SQLSetEnvAttr-funzione](../../../odbc/reference/syntax/sqlsetenvattr-function.md).  
  
-   Un driver versione 3.8 deve restituire 03.80 da **SQLGetInfo** quando SQL_DRIVER_ODBC_VER viene passato a *InfoType*. Tuttavia, gestioni Driver precedente, che sono stati inclusi nelle versioni precedenti di Microsoft Windows, verrà considerato il driver a un driver versione 3.5 ed emette un avviso.  
  
     In Windows 7, la versione di gestione Driver è 03.80. In Windows 8, la versione di gestione Driver è 03.81 tramite il SQL_DM_VER SQLGetInfo (*InfoType* parametro). La versione viene segnalato SQL_ODBC_VER 03.80 in Windows 7 e Windows 8.  
  
##### <a name="driver-specific-c-data-types"></a>Tipi di dati C specifici del driver  
 Un driver sono personalizzabili tipi di dati C quando viene usata con un'applicazione ODBC versione 3.8. (Per ulteriori informazioni, vedere [tipi di dati C in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).) Tuttavia, non vi è alcun requisito per un driver 3.8 implementare qualsiasi tipo di C specifici del driver. Ma il driver deve comunque eseguire la verifica dell'intervallo dei tipi C. Gestione Driver non verrà eseguita che per i 3.8 driver. Per semplificare lo sviluppo di driver, il valore del tipo di dati C specifico, driver può essere definito nel formato seguente:  
  
```  
SQL_DRIVER_C_TYPE_BASE+0, SQL_DRIVER_C_TYPE_BASE+1  
```  
  
##### <a name="driver-specific-data-types-descriptor-types-information-types-diagnostic-types-and-attributes"></a>Tipi di dati specifici del driver, i tipi di descrittore, tipi di informazioni, i tipi di diagnostica e attributi  
 Quando si sviluppa un nuovo driver, utilizzare l'intervallo di specifiche del driver per i tipi di dati, i tipi di descrittore, tipi di informazioni, i tipi di diagnostica e attributi. Gli intervalli specifici del driver e i relativi valori di tipo di base sono descritti nella [tipi di dati specifici del Driver, descrittore di tipi, tipi di informazioni, tipi di diagnostica e gli attributi](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
##### <a name="connection-pooling"></a>Pool di connessioni  
 Per una migliore gestione del pool di connessioni, ODBC 3.8 introduce l'attributo di connessione SQL_ATTR_RESET_CONNECTION in **SQLSetConnectAttr**. SQL_RESET_CONNECTION_YES è l'unico valore valido per questo attributo. Verrà impostato SQL_ATTR_RESET_CONNECTION prima di gestione Driver inserisce una connessione in pool di connessioni, consentendo il driver reimpostare gli altri attributi di connessione in base ai valori predefiniti.  
  
 Per evitare inutili comunicazioni con il server, un driver di rinviare l'attributo di connessione reimpostato fino alla successiva comunicazione con il server remoto, dopo la connessione viene riutilizzata dal pool.  
  
 Si noti che SQL_ATTR_RESET_CONNECTION viene utilizzato solo nelle comunicazioni tra gestione Driver e un driver. Un'applicazione non è possibile impostare l'attributo direttamente. Tutti i driver versione 3.8 devono implementare l'attributo di connessione.  
  
##### <a name="streamed-output-parameters"></a>Parametri di flusso di Output  
 ODBC versione 3.8 introduce parametri flusso di output, in modo più scalabile per recuperare i parametri di output. (Per ulteriori informazioni, vedere [il recupero dei parametri di Output tramite SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).) Per supportare questa funzionalità, un driver necessario impostare SQL_GD_OUTPUT_PARAMS nel valore restituito quando è SQL_GETDATA_EXTENSIONS il *InfoType* in un **SQLGetInfo** chiamare. Supporto per un tipo SQL con parametri di flusso di output deve essere implementato nel driver. Gestione Driver non genererà un errore per un tipo SQL non valido. I tipi SQL che supportano i parametri di flusso di output è definito nel driver.  
  
 Un driver deve restituire SQL_ERROR se l'applicazione usa **SQLGetData** per recuperare un parametro che non corrisponde a quello del parametro restituito da **SQLParamData**.  
  
##### <a name="asynchronous-execution-for-connection-operations-polling-method"></a>Esecuzione asincrona per le operazioni di connessione (metodo di Polling)  
 Un driver è possibile abilitare il supporto asincrono per diverse operazioni di connessione.  
  
 A partire da Windows 7, ODBC supporta il metodo di polling (per ulteriori informazioni, vedere [esecuzione asincrona (metodo di Polling)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md). Non è richiesto per un driver ODBC versione 3.8 implementare operazioni asincrone sugli handle di connessione. Anche se un driver non implementa le operazioni asincrone sugli handle di connessione, il driver deve comunque implementare il SQL_ASYNC_DBC_FUNCTIONS *InfoType* e restituire **SQL_ASYNC_DBC_NOT_CAPABLE**.  
  
 Quando sono abilitate le operazioni di connessione asincrona, il tempo di esecuzione di un'operazione di connessione è il tempo totale di tutte le chiamate ripetute. Se l'ultimo ripetuto chiamata viene eseguita dopo il tempo totale ha superato il valore impostato dall'attributo SQL_ATTR_CONNECTION_TIMEOUT connessione e l'operazione non è stata completata, il driver restituisce SQL_ERROR e registra un record di diagnostica con SQLState HYT01 e messaggio "timeout di connessione scaduto". Se l'operazione è terminata, non è impostato alcun timeout.  
  
##### <a name="sqlcancelhandle-function"></a>SQLCancelHandle (funzione)  
 Supporta ODBC 3.8 [SQLCancelHandle funzione](../../../odbc/reference/syntax/sqlcancelhandle-function.md), che consente di annullare le operazioni di connessione e delle istruzioni. Un driver che supporta **SQLCancelHandle** necessario esportare la funzione. Un driver non deve annullare qualsiasi funzione di connessione sincrono o asincrono che è in corso l'applicazione chiama **SQLCancel** o **SQLCancelHandle** su un handle di istruzione. Analogamente, un driver non deve annullare qualsiasi funzione istruzione sincrono o asincrono che è in corso, se un'applicazione chiama **SQLCancelHandle** nell'handle di connessione. Inoltre, un driver necessario annullare l'operazione di esplorazione (**SQLBrowseConnect** restituisce SQL_NEED_DATA) se l'applicazione chiama **SQLCancelHandle** nell'handle di connessione. In questi casi, un driver deve restituire HY010, "Errore nella funzione sequenza".  
  
 Non è necessario supportare entrambi **SQLCancelHandle** e le operazioni di connessione asincrona nello stesso momento. Un driver può supportare operazioni di connessione asincrona, ma non **SQLCancelHandle**, o viceversa.  
  
##### <a name="suspended-connections"></a>Connessioni sospese  
 La gestione driver ODBC 3.8 per è possibile inserire una connessione in stato sospeso. Un'applicazione chiamerà **SQLDisconnect** per rilasciare le risorse associate alla connessione. In questo caso, un driver deve provare a rilasciare le risorse di quante possibile senza verificare lo stato della connessione. Per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
##### <a name="driver-aware-connection-pooling"></a>Pool di connessioni compatibile con il driver  
 ODBC in Windows 8 consente di driver personalizzare il comportamento del pool di connessioni. Per ulteriori informazioni, vedere [Driver-Aware Connection Pooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md).  
  
##### <a name="asynchronous-execution-notification-method"></a>Esecuzione asincrona (metodo di notifica)  
 ODBC 3.8 supporta il metodo di notifica per operazioni asincrone, disponibile a partire in Windows 8. Per ulteriori informazioni, vedere [esecuzione asincrona (metodo di notifica)](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di un Driver ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Driver ODBC fornito da Microsoft](../../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)   
 [Novità di ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md)
