---
title: Utilizzo del buffer adattivo | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 92d4e3be-c3e9-4732-9a60-b57f4d0f7cb7
caps.latest.revision: 53
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ae4120b567d876556c29254eae65d4471ab63924
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="using-adaptive-buffering"></a>Utilizzo del buffer adattivo
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  La memorizzazione nel buffer adattiva è progettata per recuperare qualsiasi tipo di dati con valori di grandi dimensioni senza l'overhead dei cursori server. Le applicazioni possono utilizzare la funzionalità di memorizzazione nel buffer ADATTIVA con tutte le versioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] supportati dal driver.  
  
 In genere, quando il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] esegue una query, vengono recuperati tutti i risultati dal server nella memoria dell'applicazione. Sebbene questo approccio riduce al minimo il consumo di risorse nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], può generare un OutOfMemoryError nell'applicazione JDBC per le query che producono risultati di dimensioni molto grandi.  
  
 Per consentire alle applicazioni di gestire i risultati di dimensioni molto grandi, il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] offre il buffer adattivo. Con il buffer adattivo il driver recupera i risultati dell'esecuzione di istruzioni dal [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] come questi sono necessari per l'applicazione, anziché tutti contemporaneamente. Quando l'applicazione non necessita più di accedere ai dati, questi vengono inoltre eliminati dal driver. Di seguito sono illustrati alcuni esempi di casi in cui il buffer adattivo può rivelarsi utile:  
  
-   **La query produce un set di risultati molto grandi:** l'applicazione può eseguire un'istruzione SELECT che produce più righe di quante possano essere archiviate in memoria. Nelle versioni precedenti, l'applicazione deve utilizzare un cursore server per evitare un OutOfMemoryError. Il buffer adattivo consente di passare in modalità forward-only di sola lettura un set di risultati anche molto grande senza che sia necessario un cursore server.  
  
-   **La query produce valori delle colonne**[SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)**colonne oppure**[SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)**i valori di parametro:** L'applicazione può recuperare un singolo valore (colonna o parametro OUT) troppo grande per essere caricato interamente nella memoria dell'applicazione. Il buffer adattivo consente all'applicazione client di recuperare tale valore come flusso, utilizzando il getAsciiStream, il getBinaryStream o i metodi getCharacterStream. L'applicazione recupera il valore di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] durante la lettura dal flusso.  
  
> [!NOTE]  
>  Con il buffer adattivo il driver JDBC memorizza nel buffer solo la quantità di dati necessaria e non fornisce alcun metodo pubblico per controllare o limitare le dimensioni del buffer.  
  
## <a name="setting-adaptive-buffering"></a>Impostazione del buffer adattivo  
 A partire da Microsoft JDBC driver versione 2.0, il comportamento predefinito del driver è "**adattivo**". In altre parole, per ottenere il comportamento del buffer adattivo in questa versione, l'applicazione non deve richiederlo in modo esplicito. Nella versione 1.2, tuttavia, la modalità di buffer è stato "**completo**" per impostazione predefinita e l'applicazione deve richiedere la modalità di buffer adattivo in modo esplicito.  
  
 Un'applicazione può richiedere l'utilizzo del buffer adattivo nell'esecuzione di un'istruzione in tre modi:  
  
-   L'applicazione può impostare la proprietà di connessione **responseBuffering** su "adaptive". Per ulteriori informazioni sull'impostazione delle proprietà di connessione, vedere [impostando le proprietà di connessione](../../connect/jdbc/setting-the-connection-properties.md).  
  
-   L'applicazione può utilizzare il [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverdatasource.md) metodo il [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md) per impostare la modalità per tutte le connessioni create tramite tale memorizzazione delle risposte [ SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md) oggetto.  
  
-   L'applicazione può utilizzare il [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) metodo il [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) classe per impostare la modalità per un particolare oggetto istruzione di memorizzazione delle risposte.  
  
 Quando si utilizza il Driver JDBC versione 1.2, le applicazioni necessarie per eseguire il cast dell'oggetto istruzione in un [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) classe da utilizzare il [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) metodo. Esempi di codice il [campione di dati di grandi dimensioni la lettura](../../connect/jdbc/reading-large-data-sample.md) e [lettura di dati di grandi dimensioni con Stored procedure di esempio](../../connect/jdbc/reading-large-data-with-stored-procedures-sample.md) illustrano questo tipo di utilizzo.  
  
 Tuttavia, con il driver JDBC versione 2.0, applicazioni possono utilizzare il [isWrapperFor](../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md) (metodo) e [unwrap](../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md) metodo per accedere alle funzionalità specifiche del fornitore senza alcun presupposto sul gerarchia di classi di implementazione. Ad esempio di codice, vedere il [l'aggiornamento di grandi dimensioni campione di dati](../../connect/jdbc/updating-large-data-sample.md) argomento.  
  
## <a name="retrieving-large-data-with-adaptive-buffering"></a>Recupero di dati di grandi dimensioni con il buffer adattivo  
 Quando i valori di grandi dimensioni vengono letti una volta tramite get\<tipo > sono accessibili da metodi di flusso e le colonne ResultSet e ai parametri OUT CallableStatement nell'ordine restituito per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], il buffer adattivo consente di ridurre l'applicazione utilizzo della memoria durante l'elaborazione dei risultati. Quando si utilizza il buffer adattivo, si verifica quanto indicato di seguito:  
  
-   Get\<tipo > metodi definiti nel flusso di [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) e [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) classi restituiscono letti una sola volta per impostazione predefinita, anche se i flussi possono essere reimpostati se contrassegnati dall'applicazione. Se l'applicazione desidera `reset` il flusso, sarà necessario chiamare il `mark` metodo in cui il flusso prima.  
  
-   Get\<tipo > metodi definiti nel flusso di [SQLServerClob](../../connect/jdbc/reference/sqlserverclob-class.md) e [SQLServerBlob](../../connect/jdbc/reference/sqlserverblob-class.md) classi restituiscono flussi che possono essere sempre spostati nella posizione iniziale del flusso senza la chiamata di `mark` metodo.  
  
 Quando l'applicazione utilizza il buffer adattivo, i valori recuperati tramite get\<tipo > metodi flusso possono essere recuperati solo una volta. Se si tenta di chiamare qualsiasi get\<tipo > metodo sulla stessa colonna o parametro dopo la chiamata a get\<tipo > metodo flusso dello stesso oggetto, un'eccezione viene generata con il messaggio, "i dati che si accede e non sono disponibili per questo colonna o parametro".  
  
> [!NOTE]
> Microsoft JDBC Driver per SQL Server leggere ed eliminare tutti i pacchetti rimanenti richiedono una chiamata a ResultSet.close() durante l'elaborazione di un set di risultati. Se la query ha restituito un set di dati di grandi dimensioni e in particolare se la connessione di rete è lenta, l'operazione potrebbe richiedere tempo.     
  
## <a name="guidelines-for-using-adaptive-buffering"></a>Linee guida per l'utilizzo del buffer adattivo  
 Per ridurre al minimo l'utilizzo della memoria da parte dell'applicazione, gli sviluppatori devono attenersi alle importanti linee guida seguenti:  
  
-   Evitare di utilizzare la proprietà di stringa di connessione **selectMethod = cursor** per consentire all'applicazione di elaborare i risultati di grandi set. La caratteristica di buffer adattivo consente alle applicazioni di elaborare set di risultati forward-only di sola lettura di dimensioni molto grandi senza utilizzare un cursore server. Si noti che quando si imposta **selectMethod = cursor**tutti forward- only, il set di risultati di sola lettura prodotto da tale connessione è interessato. In altre parole, se l'applicazione elabora regolarmente set di risultati brevi contenenti alcune righe, la creazione, lettura e la chiusura di un cursore del server per ogni set di risultati, verrà usato più di risorse sul lato client sia sul lato server rispetto al caso in cui il  **selectMethod** non è impostata su **cursore**.  
  
-   Leggere i valori binari o testo di grandi dimensioni come flussi utilizzando il getAsciiStream, il getBinaryStream o i metodi getCharacterStream anziché il getBlob o i metodi getClob. A partire dalla versione 1.2, il [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) fornisce nuovi get\<tipo > flusso metodi a questo scopo.  
  
-   Assicurarsi che le colonne con valori potenzialmente grandi siano posizionate per ultime nell'elenco di colonne in un'istruzione SELECT e che get\<tipo > metodi di flusso di [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) vengono utilizzati per accedere alle colonne nel ordine in che cui vengono selezionate.  
  
-   Verificare che i parametri OUT con valori potenzialmente grandi siano dichiarati per ultimi nell'elenco dei parametri nel linguaggio SQL utilizzato per creare il [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md). Assicurarsi inoltre che get\<tipo > metodi del flusso di [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) vengono utilizzati per accedere ai parametri OUT nell'ordine in cui sono dichiarati.  
  
-   Evitare di eseguire simultaneamente più di un'istruzione nella stessa connessione. Se viene eseguita un'altra istruzione prima dell'elaborazione dei risultati dell'istruzione precedente, i risultati non elaborati potrebbero venire memorizzati nel buffer della memoria dell'applicazione.  
  
-   Vi sono casi in cui l'utilizzo **selectMethod = cursor** anziché **responseBuffering = adaptive** sarebbe più utile, ad esempio:  
  
    -   Se l'applicazione elabora forward-only, ad esempio la lettura di ogni riga dopo alcuni input dell'utente, utilizzando lentamente, set di risultati di sola lettura **selectMethod = cursor** anziché **responseBuffering = adaptive** potrebbe ridurre l'utilizzo delle risorse da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
    -   Se l'applicazione elabora due o set di risultati di più forward-only di sola lettura contemporaneamente nella stessa connessione, l'utilizzo **selectMethod = cursor** anziché **responseBuffering = adaptive** può contribuire a ridurre la memoria richiesta dal driver durante l'elaborazione dei set di risultati.  
  
     In entrambi i casi, è opportuno considerare l'overhead generato dalla creazione, dalla lettura e dalla chiusura dei cursori server.  
  
 Nel seguente elenco vengono inoltre fornite alcune indicazioni relative ai set di risultati scorrevoli e forward-only aggiornabili.  
  
-   Per il set di risultati scorrevoli, durante il recupero sempre un blocco di righe il driver legge in memoria il numero di righe indicate dal [getFetchSize](../../connect/jdbc/reference/getfetchsize-method-sqlserverresultset.md) metodo il [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) dell'oggetto, anche quando il il buffer adattivo è abilitato. Se lo scorrimento causa un OutOfMemoryError, è possibile ridurre il numero di righe recuperate chiamando il [setFetchSize](../../connect/jdbc/reference/setfetchsize-method-sqlserverresultset.md) metodo il [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) per impostare la dimensione di recupero su un numero inferiore di righe, persino fino a una 1 riga, se necessario. Se ciò non impedisce un OutOfMemoryError, evitare di includere colonne particolarmente estese nei set di risultati scorrevoli.  
  
-   Per i set di risultati forward-only aggiornabili, durante il recupero di un blocco di righe il driver in genere legge in memoria il numero di righe indicate dal [getFetchSize](../../connect/jdbc/reference/getfetchsize-method-sqlserverresultset.md) metodo il [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto, anche quando il buffer adattivo è abilitato per la connessione. Se la chiamata di [Avanti](../../connect/jdbc/reference/next-method-sqlserverresultset.md) metodo il [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto implica un OutOfMemoryError, è possibile ridurre il numero di righe recuperate chiamando il [setFetchSize](../../connect/jdbc/reference/setfetchsize-method-sqlserverresultset.md) metodo di [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) per impostare la dimensione di recupero su un numero inferiore di righe, persino fino a una 1 riga, se necessario. È inoltre possibile forzare il driver non memorizzare nel buffer alcuna riga chiamando la [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) metodo il [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) dell'oggetto con "**adattivo**" parametro prima l'esecuzione dell'istruzione. Poiché il set di risultati non è scorrevole, se l'applicazione accede a un valore di colonna di grandi dimensioni utilizzando uno dei get\<tipo > metodi di flusso, il driver ignora il valore come letto dall'applicazione come avviene per il forward-only in sola lettura set di risultati.  
  
## <a name="see-also"></a>Vedere anche  
 [Uso del driver JDBC per il miglioramento di prestazioni e affidabilità](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  
