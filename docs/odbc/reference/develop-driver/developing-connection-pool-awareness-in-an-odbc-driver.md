---
title: Sviluppo di un Driver ODBC consapevolezza Pool di connessioni | Documenti Microsoft
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
ms.assetid: c63d5cae-24fc-4fee-89a9-ad0367cddc3e
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 678d44bb439804246b84a7f8d60f59be45a6dce0
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="developing-connection-pool-awareness-in-an-odbc-driver"></a>Sviluppo di un Driver ODBC consapevolezza Pool di connessioni
In questo argomento vengono illustrati i dettagli dello sviluppo di un driver ODBC che contiene informazioni su come il driver deve fornire i servizi del pool di connessione.  
  
## <a name="enabling-driver-aware-connection-pooling"></a>Abilitazione del pool di connessioni compatibile con il Driver  
 Un driver deve implementare le funzioni ODBC Service Provider Interface (SPI) seguenti:  
  
-   SQLSetConnectAttrForDbcInfo  
  
-   SQLSetConnectInfo  
  
-   SQLSetDriverConnectInfo  
  
-   SQLGetPoolID  
  
-   SQLRateConnection  
  
-   SQLPoolConnect  
  
-   SQLCleanupConnectionPoolID  
  
 Vedere [riferimento ODBC Service Provider Interface (SPI)](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md) per ulteriori informazioni.  
  
 Un driver deve implementare anche le seguenti funzioni esistenti in modo che il pool compatibile con il driver può essere abilitato:  
  
|Funzione|Aggiunta di funzionalità|  
|--------------|-------------------------|  
|[SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)<br /><br /> [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)<br /><br /> [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)<br /><br /> [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)|Supportano il nuovo tipo di handle: SQL_HANDLE_DBC_INFO_TOKEN (vedere la descrizione riportata sotto).|  
|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|Supporta il nuovo attributo di connessione di sola: SQL_ATTR_DBC_INFO_TOKEN per il ripristino della connessione (vedere la descrizione riportata sotto).|  
  
> [!NOTE]  
>  Funzioni deprecate come **SQLError** e **SQLSetConnectOption** non sono supportate per il pool di connessioni compatibile con il driver.  
  
## <a name="the-pool-id"></a>L'ID del Pool  
 L'ID del pool è un ID di specifiche del driver della lunghezza di indicatore di misura per rappresentare un determinato gruppo di connessioni che possono essere utilizzate indifferentemente. Dato un set di informazioni di connessione, un driver deve essere in grado di dedurre rapidamente il corrispondente ID del pool.  
  
 Ad esempio, l'ID del pool deve codificare le informazioni di nome e le credenziali del server. Tuttavia, il nome del database non è necessario perché un driver potrebbe essere in grado di riutilizzare una connessione e quindi modificare il database in meno tempo rispetto alla creazione di una nuova connessione.  
  
 Un driver necessario definire un set di attributi principali che includerà l'ID del pool. Il valore di questi attributi chiavi può provenire da attributi di connessione, la stringa di connessione e DSN. Nel caso in cui sono presenti conflitti in queste origini, i criteri di risoluzione specifiche del driver esistente da utilizzare per la compatibilità con le versioni precedenti.  
  
 Gestione Driver utilizzerà un pool diverso per il pool di diversi ID. Tutte le connessioni nello stesso pool sono riutilizzabili. Gestione Driver mai riutilizzerà una connessione con un ID pool diversi.  
  
 Pertanto i driver devono assegnare un ID univoco del pool per ogni gruppo di connessioni con lo stesso valore nei relativi attributi chiavi definiti. Se un driver utilizza lo stesso ID di pool per due connessioni con valori diversi nei relativi attributi chiave, gestione Driver ancora inseriranno nella stesso pool (gestione Driver non riconosce gli attributi di chiave specifici del driver). Ciò significa che il driver necessario segnalare al Driver Manager che non è riutilizzabile all'interno di una connessione con un diverso set di attributi chiave [SQLRateConnection funzione](../../../odbc/reference/syntax/sqlrateconnection-function.md). Questo può ridurre le prestazioni e questa operazione è sconsigliata.  
  
 Gestione Driver non riutilizzerà una connessione allocata da un altro ambiente driver anche se corrispondano a tutte le informazioni di connessione. Gestione Driver verrà utilizzato un pool differente per un ambiente diverso, anche quando le connessioni hanno lo stesso ID di pool. Pertanto, l'ID del pool è locale al relativo ambiente di driver.  
  
 La funzione per ottenere l'ID del pool dal driver è [SQLGetPoolID funzione](../../../odbc/reference/syntax/sqlgetpoolid-function.md).  
  
## <a name="the-connection-rating"></a>La classificazione di connessione  
 Rispetto alla creazione di una nuova connessione, è possibile ottenere prestazioni migliori reimpostando alcune informazioni di connessione (ad esempio DATABASE) in una connessione in pool. In tal caso, è possibile evitare il nome del database da tutti i set di attributi chiavi. In caso contrario, è possibile disporre di un pool separato per ogni database, che potrebbe non essere valida nelle applicazioni di livello intermedio, in cui i clienti utilizzare varie stringhe di connessione diverse.  
  
 Ogni volta che si riutilizza una connessione con una mancata corrispondenza di alcuni attributi, gli attributi non corrispondenti in base alla nuova richiesta di applicazione, è consigliabile reimpostare in modo che la connessione restituita è identica alla richiesta di applicazione (vedere la discussione dell'attributo SQL_ATTR _DBC_INFO_TOKEN in [funzione SQLSetConnectAttr](http://go.microsoft.com/fwlink/?LinkId=59368)). Tuttavia, reimpostare questi attributi possono ridurre le prestazioni. Ad esempio, la reimpostazione di un database richiede una chiamata di rete al server. Pertanto, riutilizzare una connessione perfettamente corrispondente, se disponibile.  
  
 Una funzione di classificazione nel driver può valutare una connessione esistente con una nuova richiesta di connessione. Ad esempio, è possibile determinare la funzione del driver classificazione:  
  
-   Se la connessione esistente è perfettamente corrispondente alla richiesta.  
  
-   Se sono presenti solo alcuni non significativi non corrispondenti, ad esempio timeout di connessione, che non richiedono la comunicazione con il server per ripristinare.  
  
-   Se sono presenti alcuni attributi non corrispondenti che richiedono una comunicazione con il server per reimpostare ma che comunque comporta un miglioramento delle prestazioni rispetto a una nuova connessione.  
  
-   Se il non corrispondenti si è verificato per un attributo che richiede molto tempo reimpostare (lo sviluppatore del driver potrebbe considerare l'aggiunta di questo attributo nel set di attributi chiave, che viene utilizzato per generare l'ID del pool).  
  
 Un punteggio compreso tra 0 e 100 è possibile, dove 0 indica che non riutilizzare e 100 indica che corrisponde esattamente. [SQLRateConnection](../../../odbc/reference/syntax/sqlrateconnection-function.md) è la funzione di classificazione di una connessione.  
  
## <a name="new-odbc-handle---sqlhandledbcinfotoken"></a>Nuovo Handle ODBC - SQL_HANDLE_DBC_INFO_TOKEN  
 Per supportare i pool di connessioni compatibile con il driver, il driver richiede informazioni di connessione per calcolare l'ID del Pool. Il driver deve anche informazioni di connessione da confrontare con le connessioni del pool di nuove richieste di connessione.  Ogni volta che non può essere riutilizzati alcuna connessione in pool, il driver deve stabilire una nuova connessione, richiedendo pertanto le informazioni di connessione.  
  
 Poiché le informazioni di connessione possono provenire da più origini (stringa di connessione, gli attributi di connessione e DSN), il driver potrebbe essere necessario analizzare la stringa di connessione e risolvere il conflitto tra queste origini in ogni chiamata di funzione precedente.  
  
 Pertanto, è stato introdotto un nuovo handle ODBC: SQL_HANDLE_DBC_INFO_TOKEN. Con SQL_HANDLE_DBC_INFO_TOKEN, un driver non è necessario analizzare la stringa di connessione e risolvere i conflitti nelle informazioni di connessione più volte. Poiché si tratta di una struttura di dati specifici del driver, il driver può archiviare i dati, ad esempio informazioni di connessione o pool di ID.  
  
 Questo handle viene utilizzato solo come un'interfaccia tra il gestore dei Driver e il driver. Un'applicazione non è possibile allocare l'handle direttamente.  
  
 L'handle del padre di questo handle è di tipo impostato su SQL_HANDLE_ENV, vale a dire che il driver può ottenere le informazioni sull'ambiente dall'handle HENV durante la risoluzione di informazioni di connessione.  
  
 Ogni volta che riceve una nuova richiesta di connessione, gestione Driver allocherà un handle di tipo SQL_HANDLE_DBC_INFO_TOKEN per archiviare le informazioni di connessione, dopo la conferma che il driver supporta il riconoscimento di pool di connessioni. Quando è terminato di utilizzare l'handle (ma prima della restituzione alcuni codici restituiti, diverso da SQL_STILL_EXECUTING da [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) o [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)), gestione Driver consente di liberare l'handle. Di conseguenza, l'handle è creato dopo la chiamata di funzione SQLAllocHandle ed eliminati definitivamente dopo la chiamata SQLFreeHandle. Gestione Driver garantisce l'handle verrà liberato liberato relativo HENV associato (quando [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) o [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) restituisce un errore).  
  
 Il driver deve modificare le seguenti funzioni per accettare il nuovo tipo di handle SQL_HANDLE_DBC_INFO_TOKEN:  
  
1.  [SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)  
  
2.  [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)  
  
3.  [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)  
  
4.  [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)  
  
 Gestione Driver garantisce che più thread non utilizzerà lo stesso handle SQL_HANDLE_DBC_INFO_TOKEN contemporaneamente. Pertanto, il modello di sincronizzazione dell'handle può essere molto semplice interno al driver. Gestione Driver non avranno un blocco di ambiente prima di allocare e liberare SQL_HANDLE_DBC_INFO_TOKEN.  
  
 Il Driver Manager **SQLAllocHandle** e **SQLFreeHandle** non accetterà questo nuovo tipo di handle.  
  
 SQL_HANDLE_DBC_INFO_TOKEN possono contenere informazioni riservate, ad esempio le credenziali. Pertanto, un driver in modo sicuro cancellare il buffer di memoria (tramite [SecureZeroMemory](http://msdn.microsoft.com/library/windows/desktop/aa366877\(v=vs.85\).aspx)) che contiene le informazioni sensibili prima di rilasciare l'handle con **SQLFreeHandle**. Ogni volta che viene chiuso l'handle di ambiente dell'applicazione, tutti i pool di connessione associata verranno chiusa.  
  
## <a name="driver-manager-connection-pool-rating-algorithm"></a>Pool di connessioni di Gestione driver algoritmo di classificazione  
 In questa sezione viene descritto l'algoritmo di classificazione per il pool di connessioni di gestione Driver. Gli sviluppatori di driver possono implementare lo stesso algoritmo per la compatibilità con le versioni precedenti. Questo algoritmo potrebbe non essere quello più adatto. È necessario ridefinire questo algoritmo di implementazione di base (in caso contrario, non vi è alcun motivo per implementare questa funzionalità).  
  
 Gestione Driver restituirà un valore integrale di classificazione da 0 a 100 per ogni connessione dal pool. 0 indica che la connessione non è possibile riutilizzare e 100 indica una soluzione perfetta corrispondenza. Si supponga che la richiesta di connessione è denominata hRequest e la connessione esistente dal pool come hCandidate. Se una qualsiasi delle condizioni seguenti è false, hCandidate la connessione in pool non può essere riutilizzato per hRequest (Driver Manager assegnerà una classificazione uguale a 0).  
  
-   hCandidate e hRequest provenire da UNICODE API (ad esempio, SQLDriverConnectW) o ANSI API (ad esempio, SQLDriverConnectA). (Driver UNICODE può diverso comportamento specificato API ANSI e UNICODE API (vedere l'attributo di connessione SQL_ATTR_ANSI_APP)).  
  
-   hCandidate e hRequest vengono creati dalla stessa funzione. SQLDriverConnect o SQLConnect.  
  
-   La stringa di connessione utilizzata per aprire hCandidate deve essere identico hRequest, quando viene utilizzato SQLDriverConnect.  
  
-   Il nome utente ServerName (o DSN), e la password utilizzata per aprire hCandidate deve essere lo stesso utilizzato per aprire hRequest quando viene utilizzato SQLConnect.  
  
-   L'ID di sicurezza (SID) del thread corrente deve essere lo stesso SID utilizzato per aprire hCandidate.  
  
-   Per il driver che è dispendioso integrare e rimuovere (vedere la discussione relativa SQL_DTC_TRANSITION_COST in [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)), viene riutilizzata *hRequest* non deve richiedere un'integrazione aggiuntivo o unenlistment.  
  
 La tabella seguente illustra l'assegnazione del punteggio per scenari diversi.  
  
|Confronto tra gli attributi di connessione tra la connessione in pool e la richiesta|Alcuna integrazione / unenlistment|Richiede l'integrazione aggiuntivo / Unenlistment|  
|---------------------------------------------------------------------------------------|-----------------------------------|----------------------------------------------|  
|Catalogo (SQL_ATTR_CURRENT_CATALOG) è diverso|60|50|  
|Alcuni attributi di connessione sono diversi, ma catalogo corrisponde al|90|70|  
|Tutti gli attributi di connessione perfettamente corrispondenti.|100|80|  
  
## <a name="sequence-diagram"></a>Diagramma sequenza  
 Questo diagramma di sequenza Mostra il meccanismo di base del pool descritte in questo argomento. Visualizza solo l'utilizzo di [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) ma la [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) è simile.  
  
 ![Diagramma di sequenza](../../../odbc/reference/develop-driver/media/odbc_seq_dia.gif "odbc_seq_dia")  
  
## <a name="state-diagram"></a>Diagramma di stato  
 Questo diagramma di stato Mostra informazioni token oggetto connection, descritte in questo argomento. Il diagramma mostra solo [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) ma la [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) è simile. Poiché gestione Driver potrebbe essere necessario gestire gli errori in qualsiasi momento, è possibile chiamare gestione Driver [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md) per qualsiasi stato.  
  
 ![Diagramma di stato](../../../odbc/reference/develop-driver/media/odbc_state_diagram.gif "odbc_state_diagram")  
  
## <a name="see-also"></a>Vedere anche  
 [Il pool di connessioni compatibile con il driver](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Riferimento dell'interfaccia del provider di servizi (SPI) ODBC](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md)
