---
title: Pool di connessioni di Gestione driver | Documenti Microsoft
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
helpviewer_keywords:
- connection pooling [ODBC]
- pooled connections [ODBC]
- connecting to driver [ODBC], connection pooling
- connecting to data source [ODBC], connection pooling
ms.assetid: ee95ffdb-5aa1-49a3-beb2-7695b27c3df9
caps.latest.revision: "32"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5a2b77875c442720d452b8520e5c8fe03b122e2b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="driver-manager-connection-pooling"></a>Pool di connessioni di Gestione driver
Il pool di connessioni consente a un'applicazione di utilizzare una connessione da un pool di connessioni che non è necessario ristabilire per ogni utilizzo. Una volta una connessione è stata creata e inserita in un pool, un'applicazione può riutilizzare la connessione senza eseguire il processo di connessione completa.  
  
 Utilizzando una connessione in pool può provocare miglioramenti significativi delle prestazioni, poiché le applicazioni è possono salvare l'overhead necessario per stabilire una connessione. Può essere particolarmente significativo per le applicazioni di livello intermedio che si connettono tramite una rete o per le applicazioni che ripetutamente connettono e disconnettersi, ad esempio applicazioni Internet.  
  
 Oltre a miglioramenti delle prestazioni, il pool di connessioni architettura consente un ambiente e le relative connessioni associate per essere utilizzata da più componenti in un unico processo. Ciò significa che i componenti autonomi nello stesso processo possono interagire tra loro senza tener conto di altra. Una connessione in un pool di connessioni può essere utilizzata ripetutamente da più componenti.  
  
> [!NOTE]  
>  Il pool di connessioni può essere utilizzato da un'applicazione ODBC che esibisce ODBC 2. *x* comportamento, a condizione che l'applicazione può chiamare *SQLSetEnvAttr*. Quando si utilizza il pool di connessioni, l'applicazione non deve eseguire istruzioni SQL che modificano il database o il contesto del database, ad esempio la modifica di \< *database**nome*>, che modifica il catalogo utilizzato da un'origine dati.  
  
 Un driver ODBC deve essere completamente thread-safe e le connessioni non devono essere affinità di thread per supportare il pool di connessioni. Ciò significa che il driver è in grado di gestire una chiamata in qualsiasi thread in qualsiasi momento ed è in grado di connettersi su un singolo thread, utilizzare la connessione in un altro thread e disconnettere in un terzo thread.  
  
 Il pool di connessioni viene gestito da Gestione Driver. Le connessioni vengono recuperate dal pool quando l'applicazione chiama **SQLConnect** o **SQLDriverConnect** e vengono restituiti al pool quando l'applicazione chiama **SQLDisconnect**. La dimensione del pool di aumenta in modo dinamico, in base alle allocazioni risorsa richiesta. Riduce in base al timeout di inattività: se una connessione rimane inattiva per un periodo di tempo (non è stata utilizzata in una connessione), verrà rimosso dal pool. La dimensione del pool è limitata solo da vincoli di memoria e i limiti sul server.  
  
 Gestione Driver determina se è necessario utilizzare una connessione specifica in un pool in base agli argomenti passati **SQLConnect** o **SQLDriverConnect**e gli attributi di connessione impostare dopo la connessione è stata allocata.  
  
 Quando Gestione Driver è il pool di connessioni, è necessario essere in grado di determinare se una connessione sta ancora lavorando prima di passare il timeout della connessione. In caso contrario, gestione Driver via mantiene passando il timeout della connessione di messaggi non recapitabili per applicazione ogni volta che si verifica un errore di rete temporanei. Un nuovo attributo di connessione è stato definito in ODBC 3*x*: SQL_ATTR_CONNECTION_DEAD. Si tratta di un attributo di connessione di sola lettura che restituisce SQL_CD_TRUE o SQL_CD_FALSE. Il valore SQL_CD_TRUE significa che la connessione è stata persa, mentre il valore SQL_CD_FALSE significa che la connessione è ancora attiva. (Driver conforme alle versioni precedenti di ODBC supporta anche l'attributo.)  
  
 Un driver necessario implementare questa opzione in modo efficiente o rallenta le prestazioni di pool di connessioni. In particolare, una chiamata per ottenere l'attributo di connessione non dovrebbe causare un round trip al server. Al contrario, un driver deve restituire l'ultimo stato noto della connessione. La connessione è inattivo se non è riuscita l'ultima trip al server e non messaggi non recapitabili se l'ultimo trip ha avuto esito positivo.  
  
## <a name="remarks"></a>Osservazioni  
 Se una connessione è stata persa (indicato tramite SQL_ATTR_CONNECTION_DEAD), gestione Driver ODBC comporta l'eliminazione della connessione chiamando SQLDisconnect nel driver. Nuove richieste di connessione potrebbero non trovare una connessione utilizzabile nel pool. Alla fine di gestione Driver potrebbe creare una nuova connessione, presupponendo che il pool è vuoto.  
  
 Per utilizzare un pool di connessioni, un'applicazione esegue i passaggi seguenti:  
  
1.  Consente il pool di connessioni chiamando **SQLSetEnvAttr** per impostare l'attributo di ambiente SQL_ATTR_CONNECTION_POOLING SQL_CP_ONE_PER_DRIVER o SQL_CP_ONE_PER_HENV. Deve essere chiamato prima che l'applicazione alloca ambiente condiviso per la connessione che il pool è necessario abilitare. L'handle di ambiente nella chiamata a **SQLSetEnvAttr** deve essere impostato su null, che rende SQL_ATTR_CONNECTION_POOLING un attributo a livello di processo. Se l'attributo è impostato su SQL_CP_ONE_PER_DRIVER, un pool di connessioni singolo è supportato per ogni driver. Se un'applicazione funziona con molti driver e alcuni ambienti, questa potrebbe essere più efficiente poiché i confronti di un numero inferiore potrebbero essere necessari. Se impostato su SQL_CP_ONE_PER_HENV, un pool di connessioni singolo è supportato per ogni ambiente. Se un'applicazione funziona con alcuni driver e di molti ambienti, questa potrebbe essere più efficiente poiché i confronti di un numero inferiore potrebbero essere necessari. Il pool di connessioni è disabilitato impostando SQL_ATTR_CONNECTION_POOLING su SQL_CP_OFF.  
  
2.  Alloca un ambiente chiamando **SQLAllocHandle** con il *HandleType* argomento impostato su SQL_HANDLE_ENV. L'ambiente allocato da questa chiamata sarà un ambiente condiviso implicito perché il pool di connessioni è stato abilitato. Non è stato determinato l'ambiente da utilizzare, tuttavia, finché non **SQLAllocHandle** con un *HandleType* impostato su SQL_HANDLE_DBC viene chiamato in questo ambiente.  
  
3.  Alloca una connessione chiamando **SQLAllocHandle** con *InputHandle* impostato su SQL_HANDLE_DBC e *InputHandle* impostato su allocata per l'handle di ambiente il pool di connessioni. Gestione Driver tenta di trovare un ambiente esistente che corrisponde agli attributi di ambiente impostati dall'applicazione. Se l'ambiente non esiste, uno viene creato, con un conteggio dei riferimenti (gestito da Gestione Driver) pari a 1. Se viene trovato un ambiente condiviso corrispondente, l'ambiente viene restituito all'applicazione e il conteggio dei riferimenti viene incrementato. (Non l'effettiva connessione da utilizzare è determinata da Gestione Driver finché **SQLConnect** o **SQLDriverConnect** viene chiamato.)  
  
4.  Chiamate **SQLConnect** o **SQLDriverConnect** per stabilire la connessione. Gestione Driver utilizza le opzioni di connessione nella chiamata a **SQLConnect** (o le parole chiave di connessione nella chiamata a **SQLDriverConnect**) e impostare gli attributi di connessione dopo l'allocazione di connessione a stabilire la connessione nel pool di deve essere utilizzata.  
  
    > [!NOTE]  
    >  Il modo in cui è associata una richiesta di connessione a una connessione in pool è determinato dall'attributo SQL_ATTR_CP_MATCH ambiente. Per ulteriori informazioni, vedere [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md).  
  
     Applicazioni ODBC che utilizzano il pool di connessioni devono chiamare [CoInitializeEx](http://go.microsoft.com/fwlink/?LinkID=116307) durante l'inizializzazione dell'applicazione e [CoUninitialize](http://go.microsoft.com/fwlink/?LinkId=116310) quando la chiusura dell'applicazione.  
  
5.  Chiamate **SQLDisconnect** dopo la connessione. La connessione viene restituita al pool di connessioni e diventa disponibile per il riutilizzo.  
  
 Per informazioni più dettagliate, vedere [pool in Microsoft Data Access Components](http://go.microsoft.com/fwlink/?LinkId=120776).  
  
## <a name="connection-pooling-considerations"></a>Considerazioni di pool di connessioni  
 Eseguire le operazioni seguenti utilizzando un comando SQL (anziché tramite l'API ODBC), è possibile influire sullo stato della connessione e causare problemi imprevisti quando il pool di connessioni è attivo:  
  
-   Apertura di una connessione e la modifica del database predefinito.  
  
-   Tramite l'istruzione SET per modificare le opzioni configurabili (inclusi SET ROWCOUNT, ANSI_NULL, IMPLICIT_TRANSACTIONS, SHOWPLAN, le statistiche, TEXTSIZE e DATEFORMAT).  
  
-   Creazione di tabelle e stored procedure temporanee.  
  
 Se una di queste azioni vengono eseguita all'esterno dell'API ODBC, la persona successiva che utilizza la connessione erediterà automaticamente le impostazioni precedenti, le tabelle o procedure.  
  
> [!NOTE]  
>  Non si prevede alcune impostazioni deve essere presente nello stato della connessione. È sempre deve impostare lo stato di connessione dell'applicazione e verificare che l'applicazione rimuove le impostazioni di pool di connessioni inutilizzati.  
  
## <a name="driver-aware-connection-pooling"></a>Pool di connessioni compatibile con il driver  
 A partire da Windows 8, un driver ODBC può utilizzare connessioni nel pool in modo più efficiente. Per ulteriori informazioni, vedere [Driver-Aware Connection Pooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Connessione ai dati di un Driver o origine](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md)   
 [Sviluppo di un Driver ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Il pool di Microsoft Data Access Components](http://go.microsoft.com/fwlink/?LinkId=120776)
