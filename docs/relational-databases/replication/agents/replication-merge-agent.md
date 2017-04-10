---
title: "Agente merge repliche | Microsoft Docs"
ms.custom: ""
ms.date: "08/24/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "agente di merge, eseguibili"
  - "agente di merge, informazioni di riferimento sui parametri"
  - "agenti [replica di SQL Server], agente di merge"
  - "prompt dei comandi [replica di SQL Server]"
ms.assetid: fe1e7f60-b0c8-45e9-a5e8-4fedfa73d7ea
caps.latest.revision: 64
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 64
---
# Agente merge repliche
  Agente merge repliche è un eseguibile dell'utilità che consente di applicare lo snapshot iniziale incluso nelle tabelle di database ai Sottoscrittori. Consente inoltre di unire le modifiche ai dati incrementali apportate nel server di pubblicazione dopo la creazione dello snapshot iniziale e di riconciliare i conflitti in base alle regole configurate oppure utilizzando un sistema di risoluzione personalizzato.  
  
> [!NOTE]  
>  I parametri possono essere specificati in qualsiasi ordine. Quando i parametri facoltativi non vengono specificati, vengono usati i valori delle impostazioni predefinite del Registro di sistema nel computer locale.  
  
## Sintassi  
  
```  
  
replmerg [-?]   
-Publisher server_name[\instance_name]  
-PublisherDB publisher_database  
-Publication publication  
-Subscriber server_name[\instance_name]  
-SubscriberDB subscriber_database  
[-AltSnapshotFolder alt_snapshot_folder_path]  
[-Continuous]  
[-DefinitionFile def_path_and_file_name]  
[-DestThreads number_of_destination_threads]  
[-Distributor server_name[\instance_name]]  
[-DistributorLogin distributor_login]  
[-DistributorPassword distributor_password]  
[-DistributorSecurityMode [0|1]]  
[-DownloadGenerationsPerBatch download_generations_per_batch]  
[-DownloadReadChangesPerBatch download_read_changes_per_batch]  
[-DownloadWriteChangesPerBatch download_write_changes_per_batch]  
[-DynamicSnapshotLocation dynamic_snapshot_location]  
[-EncryptionLevel [0|1|2]]  
[-ExchangeType [1|2|3]]  
[-FastRowCount [0|1]]  
[-FileTransferType [0|1]]  
[-ForceConvergenceLevel [0|1|2 (Publisher|Subscriber|Both)]]  
[-FtpAddress ftp_address]  
[-FtpPassword ftp_password]  
[-FtpPort ftp_port]  
[-FtpUserNameftp_user_name]  
[-HistoryVerboseLevel [0|1|2|3]]  
[-Hostname host_name]  
[-InteractiveResolution [0|1]]  
[-InternetLogin internet_login]  
[-InternetPassword internet_password]  
[-InternetProxyLogin internet_proxy_login]  
[–InternetProxyPassword internet_proxy_password]  
[-InternetProxyServer internet_proxy_server]  
[-InternetSecurityMode [0|1]]  
[-InternetTimeout internet_timeout]  
[-InternetURL internet_url]  
[-KeepAliveMessageInterval keep_alive_message_interval_seconds]  
[-LoginTimeOut login_time_out_seconds]  
[-MakeGenerationInterval make_generation_interval_seconds]  
[-MaxBcpThreads number_of_threads]  
[-MaxDownloadChanges number_of_download_changes]  
[-MaxUploadChanges number_of_upload_changes]  
[-MetadataRetentionCleanup [0|1]]  
[-Output]  
[-OutputVerboseLevel [0|1|2]]  
[-ParallelUploadDownload [0|1]]  
[-PacketSize packet_size]   
[-PollingInterval polling_interval]  
[-ProfileName profile_name]  
[-PublisherFailoverPartner server_name[\instance_name] ]  
[-PublisherLogin publisher_login]  
[-PublisherPassword publisher_password]  
[-PublisherSecurityMode [0|1]]  
[-QueryTimeOut query_time_out_seconds]  
[-SrcThreads number_of_source_threads]  
[-StartQueueTimeout start_queue_timeout_seconds]  
[-SubscriberConflictClean [0|1]]  
[-SubscriberDatabasePath subscriber_path]  
[-SubscriberDBAddOption [0|1|2|3]]  
[-SubscriberLogin subscriber_login]  
[-SubscriberPassword subscriber_password   
[-SubscriberSecurityMode [0|1]]  
[-SubscriberType [0|1|2|3|4|5|6|7|8|9]]  
[-SubscriptionType [0|1|2]]  
[-SyncToAlternate [0|1]  
[-UploadGenerationsPerBatch upload_generations_per_batch]  
[-UploadReadChangesPerBatch upload_read_changes_per_batch]  
[-UploadWriteChangesPerBatch upload_write_changes_per_batch]  
[-UseInprocLoader]  
[-Validate [0|1|2|3]]  
[-ValidateInterval validate_interval]  
```  
  
## Argomenti  
 **-?**  
 Stampa tutti i parametri disponibili.  
  
 **-Server di pubblicazione** *nome_server*[**\\***instance_name*]  
 Nome del server di pubblicazione. Specificare *nome_server* per l'istanza predefinita di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] su tale server. Specificare *nome_server***\\***instance_name* per un'istanza denominata di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] su tale server.  
  
 **-PublisherDB** *publisher_database*  
 Nome del database del server di pubblicazione.  
  
 **-Pubblicazione** *pubblicazione*  
 Nome della pubblicazione. Questo parametro è valido solo se la pubblicazione è configurata in modo che sia sempre disponibile uno snapshot per le sottoscrizioni nuove o reinizializzate.  
  
 **-Sottoscrittore** *nome_server*[**\\***instance_name*]  
 Nome del Sottoscrittore. Specificare *nome_server* per l'istanza predefinita di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] su tale server. Specificare *nome_server***\\***instance_name* per un'istanza denominata di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] su tale server.  
  
 **-SubscriberDB** *subscriber_database*  
 Nome del database Sottoscrittore.  
  
 **-AltSnapshotFolder** *alt_snapshot_folder_path*  
 Percorso della cartella che contiene lo snapshot iniziale per una sottoscrizione.  
  
 **-Continuous**  
 Specifica se l'agente tenta di eseguire continuamente il polling delle transazioni replicate. Se specificato, l'agente esegue il polling delle transazioni replicate dall'origine in base agli intervalli di polling, anche se non vi sono transazioni in sospeso.  
  
 **-DestThreads** *number_of_destination_threads*  
 Specifica il numero di thread di destinazione utilizzati dall'agente di merge per applicare le modifiche nella destinazione. La destinazione è costituita dal server di pubblicazione durante il caricamento e dal Sottoscrittore durante il download. Il valore predefinito è 4.  
  
 **-DefinitionFile** *def_path_and_file_name*  
 Percorso del file di definizione dell'agente. Un file di definizione dell'agente contiene argomenti del prompt dei comandi per l'agente. Il contenuto del file viene analizzato come file eseguibile. Utilizzare virgolette doppie (") per specificare valori dell'argomento contenenti caratteri arbitrari.  
  
 **-Server di distribuzione** *nome_server*[**\\***instance_name*]  
 Nome del database di distribuzione. Specificare *nome_server* per l'istanza predefinita di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] su tale server. Specificare *nome_server***\\***instance_name* per un'istanza denominata di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] su tale server. Per la distribuzione (push) del database di distribuzione, per impostazione predefinita viene utilizzato il nome dell'istanza predefinita di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nel computer locale.  
  
 **-DistributorLogin** *distributor_login*  
 Nome dell'account di accesso del database di distribuzione.  
  
 **-DistributorPassword** *distributor_password*  
 Password del database di distribuzione.  
  
 **-DistributorSecurityMode** [ **0**| **1**]  
 Specifica la modalità di sicurezza del database di distribuzione. Il valore **0** indica [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] modalità di autenticazione (impostazione predefinita) e il valore di **1** indica la modalità di autenticazione di Windows.  
  
 **-DownloadGenerationsPerBatch** *download_generations_per_batch*  
 Numero di generazioni da elaborare in un singolo batch durante il download delle modifiche dal server di pubblicazione al Sottoscrittore. Una generazione è definita come un gruppo logico di modifiche per articolo. Il valore predefinito per un collegamento di comunicazione affidabile è 100. Il valore predefinito per un collegamento di comunicazione non affidabile è 10.  
  
 **-DownloadReadChangesPerBatch** *download_read_changes_per_batch*  
 Numero di modifiche da leggere in un singolo batch durante il download delle modifiche dal server di pubblicazione al Sottoscrittore. Il valore predefinito è 100.  
  
 **-DownloadWriteChangesPerBatch** *download_write_changes_per_batch*  
 Numero di modifiche da applicare in un singolo batch durante il download delle modifiche dal server di pubblicazione al Sottoscrittore. Il valore predefinito è 100.  
  
 **-DynamicSnapshotLocation** *dynamic_snapshot_location*  
 Posizione dei file di snapshot dei dati filtrati quando nella pubblicazione vengono utilizzati filtri di riga con parametri.  
  
 **-EncryptionLevel** [ **0** | **1** | **2** ]  
 Livello di crittografia SSL (Secure Sockets Layer) utilizzato dall'agente di merge quando vengono stabilite le connessioni.  
  
|Valore di EncryptionLevel|Descrizione|  
|---------------------------|-----------------|  
|**0**|Specifica che SSL non viene utilizzato.|  
|**1**|Specifica che SSL viene utilizzato, ma l'agente non verifica che il certificato server SSL sia firmato da un'autorità emittente attendibile.|  
|**2**|Specifica che SSL viene utilizzato e che il certificato viene verificato.|  
  
 Per ulteriori informazioni, vedere [Cenni preliminari sulla sicurezza & #40; Replica & #41;](../../../relational-databases/replication/security/security-overview-replication.md).  
  
 **-ExchangeType** [ **1**| **2**| **3**]  
 > [!WARNING]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../../includes/ssnotedepfuturedontuse-md.md)] Per limitare il caricamento, utilizzare il **@subscriber_upload_options** di **sp_addmergearticle** invece.  
  
 Specifica il tipo di scambio di dati durante la sincronizzazione. I possibili valori sono i seguenti:  
  
|Valore di ExchangeType|Descrizione|  
|------------------------|-----------------|  
|**1**|L'agente deve caricare le modifiche ai dati dal Sottoscrittore al server di pubblicazione.|  
|**2**|L'agente deve eseguire il download delle modifiche ai dati dal server di pubblicazione al Sottoscrittore.|  
|**3** (impostazione predefinita)|L'agente deve prima caricare le modifiche ai dati dal Sottoscrittore al server di pubblicazione, quindi eseguirne il download dal server di pubblicazione al Sottoscrittore. È necessario utilizzare questa opzione con la sincronizzazione Web.|  
  
 Gli articoli di solo download consentono di controllare il comportamento della sincronizzazione dei singoli articoli in una pubblicazione e possono offrire un vantaggio a livello di prestazioni. Per ulteriori informazioni, vedere [Ottimizza prestazioni della replica di tipo Merge con gli articoli Download-Only](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md).  
  
 Se si utilizza **ExchangeType** per separare il caricamento e download fase della replica di tipo merge in sessioni separate, è necessario eseguire l'agente di merge con **ExchangeType** impostato su 1 e quindi eseguire nuovamente l'agente di merge con il valore 2. L'esito negativo dell'esecuzione dell'agente di merge per entrambi i parametri causa l'eliminazione dei metadati e la rinizializzazione della sottoscrizione senza caricamento.  
  
 **-FastRowCount** [**0**|**1**]  
 Specifica il tipo di metodo di calcolo del conteggio delle righe che deve essere utilizzato per la convalida mediante il conteggio delle righe. Il valore **1** (impostazione predefinita) indica il metodo rapido. Il valore **0** indica il metodo di conteggio delle righe completo.  
  
 **-FileTransferType** [**0**|**1**]  
 Specifica il tipo di trasferimento di file. Il valore **0** indica UNC (convenzione di denominazione universale) e il valore di **1** indica FTP (file transfer protocol).  
  
 **-ForceConvergenceLevel** [**0**|**1**|**2** ( **Publisher**| **sottoscrittore**| **entrambi**)]  
 Specifica il livello di convergenza che l'agente di merge deve utilizzare. I possibili valori sono i seguenti:  
  
|Valore di ForceConvergenceLevel|Descrizione|  
|---------------------------------|-----------------|  
|**0** (impostazione predefinita)|Valore predefinito. Esegue un'operazione di merge standard senza convergenza aggiuntiva.|  
|**1**|Forza la convergenza per tutte le generazioni.|  
|**2**|Forza la convergenza per tutte le generazioni e corregge le derivazioni danneggiate. Quando si specifica questo valore, specificare dove devono essere corrette le derivazioni, ovvero nel server di pubblicazione, nel Sottoscrittore o in entrambi.|  
  
 **-FtpAddress** *ftp_address*  
 Indirizzo di rete del servizio FTP per il database di distribuzione. Quando non viene specificato, **distributore** viene utilizzato.  
  
 **-FtpPassword** *ftp_password*  
 Password utente utilizzata per la connessione al servizio FTP.  
  
 **-FtpPort** *ftp_port*  
 Numero di porta del servizio FTP per il database di distribuzione. Quando non è specificato, viene utilizzato il numero di porta predefinito per il servizio FTP, ovvero 21.  
  
 **-FtpUserName** *ftp_user_name*  
 Nome utente utilizzato per la connessione al servizio FTP. Quando non è specificato, viene utilizzato anonymous.  
  
 **-HistoryVerboseLevel** [**1**|**2**|**3**]  
 Specifica la quantità di cronologia registrata durante un'operazione di unione. È possibile ridurre l'effetto della registrazione della cronologia sulle prestazioni selezionando **1**.  
  
|Valore di HistoryVerboseLevel|Descrizione|  
|-------------------------------|-----------------|  
|**0**|Registra il messaggio di stato dell'agente finale, i dettagli di sessione finali ed eventuali errori.|  
|**1**|Registra i dettagli di sessione incrementali a ogni stato della sessione, inclusa la percentuale di completamento, oltre al messaggio di stato dell'agente finale, ai dettagli di sessione finali e a eventuali errori.|  
|**2**|Valore predefinito. Registra sia i dettagli di sessione incrementali a ogni stato della sessione che i dettagli di sessione a livello di articolo, inclusa la percentuale di completamento, oltre al messaggio di stato dell'agente finale, ai dettagli di sessione finali e a eventuali errori. Vengono inoltre registrati i messaggi di stato dell'agente.|  
|**3**|Identico **- HistoryVerboseLevel** = **2**, ad eccezione del fatto che vengono registrati ulteriori messaggi di stato dell'agente.|  
  
 **-Hostname** *host_name*  
 Nome di rete del computer locale. Il valore predefinito è il nome del computer locale.  
  
 **-InteractiveResolution** [**0**|**1**]  
 Specifica se viene utilizzata la risoluzione dei conflitti interattiva quando si verifica un conflitto durante la sincronizzazione. Il valore predefinito è **0**, che indica che la risoluzione dei conflitti interattivo non viene utilizzata.  
  
 **-InternetLogin** *internet_login*  
 Specifica il nome di accesso utilizzato per la connessione a una DLL ISAPI del listener per la replica di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] che richiede l'autenticazione.  
  
 **-InternetPassword** *internet_password*  
 Specifica la password utilizzata per la connessione a una DLL ISAPI del listener per la replica di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] che richiede l'autenticazione.  
  
 **-InternetProxyLogin**  *internet_proxy_login*  
 Specifica il nome di account di accesso utilizzato per la connessione a un server proxy, definito in *internet_proxy_server*, che richiede l'autenticazione.  
  
 **-InternetProxyPassword**  *internet_proxy_password*  
 Specifica la password utilizzata per la connessione a un server proxy, definito in *internet_proxy_server*, che richiede l'autenticazione.  
  
 **-InternetProxyServer**  *internet_proxy_server*  
 Specifica il server proxy da utilizzare per l'accesso alla risorsa HTTP specificata *internet_url*.  
  
 **-InternetSecurityMode** [**0**|**1**]  
 Specifica la modalità di sicurezza di IIS da utilizzare per la connessione al server Web durante la sincronizzazione Web. Il valore **0** indica l'autenticazione di base e il valore di **1** indica l'autenticazione integrata di Windows (impostazione predefinita).  
  
 **-InternetTimeout** *internet_timeout*  
 Numero di secondi prima che si verifichi il timeout di una connessione alla DLL ISAPI del listener per la replica di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 **-InternetURL** *internet_url*  
 Specifica l'URL utilizzato per la connessione alla DLL ISAPI del listener per la replica di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. È necessario specificare questa proprietà.  
  
 **-KeepAliveMessageInterval** *keep_alive_message_interval_seconds*  
 Numero di secondi prima che il thread per la cronologia controlli se una delle connessioni esistenti è in attesa di una risposta dal server. Questo valore può essere ridotto per evitare che l'agente di controllo contrassegni l'agente di merge come sospetto in caso di esecuzione di un batch con esecuzione prolungata. Il valore predefinito è **300** secondi.  
  
 **-LoginTimeOut** *login_time_out_seconds*  
 Numero di secondi prima del timeout di accesso. Il valore predefinito è **15** secondi.  
  
 **-MakeGenerationInterval** *make_generation_interval_seconds*  
 Numero di secondi di attesa tra la creazione di generazioni, o batch di modifiche, per il download nel client. Il valore predefinito è **1** secondo.  
  
 Makegeneration è il processo che prepara il download delle modifiche del server di pubblicazione nei Sottoscrittori e può rappresentare un collo di bottiglia per le prestazioni durante i download. Se il processo makegeneration già stato eseguito entro l'intervallo specificato da **- MakeGenerationInterval**, il processo viene ignorato per la sessione di sincronizzazione corrente. Questa operazione può procurare vantaggio alla simultaneità della sincronizzazione e risulta particolarmente utile se i Sottoscrittori non prevedono il download di modifiche.  
  
 **-MaxBcpThreads** *number_of_threads*  
 Specifica il numero di operazioni di copia bulk che possono essere eseguite in parallelo. Il numero massimo di thread e connessioni ODBC disponibili contemporaneamente sia il valore minore di **MaxBcpThreads** o il numero di massa copiare le richieste che vengono visualizzati nella tabella di sistema **sysmergeschemachange** nel database di pubblicazione. **MaxBcpThreads** deve avere un valore maggiore di 0 e non presenta alcun limite superiore hardcoded. Il valore predefinito è **1**.  
  
 **-MaxDownloadChanges** *number_of_download_changes*  
 Specifica il numero massimo di righe modificate che possono essere scaricate dal server di pubblicazione al Sottoscrittore. Il numero di righe scaricate può essere superiore al valore massimo specificato se vengono elaborate generazioni complete e possono essere eseguiti thread di destinazione paralleli, ognuno dei quali elabora almeno 100 modifiche nel primo passaggio. Per impostazione predefinita, tutte le modifiche pronte per essere scaricate vengono inviate.  
  
 **-MaxUploadChanges** *number_of_upload_changes*  
 Specifica il numero massimo di righe modificate che possono essere caricate dal Sottoscrittore al server di pubblicazione. Il numero di righe caricate può essere superiore al valore massimo specificato se vengono elaborate generazioni complete e possono essere eseguiti thread di destinazione paralleli, ognuno dei quali elabora almeno 100 modifiche nel primo passaggio. Per impostazione predefinita, tutte le modifiche pronte per essere caricate vengono inviate.  
  
 **-MetadataRetentionCleanup** [**0**|**1**]  
 Specifica se i metadati vengono rimossi dal [MSmerge_genhistory](../../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md), [MSmerge_contents](../../../relational-databases/system-tables/msmerge-contents-transact-sql.md), [MSmerge_tombstone](../../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md), [MSmerge_past_partition_mappings](../../../relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql.md), e [MSmerge_current_partition_mappings](../../../relational-databases/system-tables/msmerge-current-partition-mappings.md) in base al periodo di memorizzazione della pubblicazione. Il valore predefinito è **1**, che indica che la pulizia si verifichi. Il valore **0** indica che la pulizia non dovrebbe verificarsi automaticamente.  
  
 **-Output** *output_path_and_file_name*  
 Percorso del file di output dell'agente. Se non viene specificato il nome file, l'output viene inviato alla console. Se il nome file specificato esiste già, l'output viene aggiunto al file.  
  
 **-OutputVerboseLevel** [**0**|**1**|**2**]  
 Specifica se l'output deve essere dettagliato. Se il livello di dettaglio è **0**, vengono stampati solo i messaggi di errore. Se il livello di dettaglio è **1**, tutto lo stato di avanzamento del report vengono stampati i messaggi. Se il livello di dettaglio è **2** (predefinito), vengono stampati tutti i messaggi di errore e i messaggi di rapporto di stato di avanzamento, che è utile per il debug.  
  
 **-ParallelUploadDownload** [**0**|**1**]  
 Specifica se l'agente di merge deve elaborare in parallelo le modifiche caricate nel server di pubblicazione e quelle scaricate nel Sottoscrittore. Questa opzione è utile negli ambienti caratterizzati da volumi di traffico elevati con un'ampia larghezza di banda di rete. Se **ParallelUploadDownload** è **1**, quindi l'elaborazione parallela è abilitata.  
  
 **-PacketSize**  
 Dimensioni del pacchetto, in byte. Il valore predefinito è 4096 byte.  
  
 **-PollingInterval** *polling_interval*  
 Frequenza, in secondi, di esecuzione di query sul server di pubblicazione o sul Sottoscrittore per le modifiche ai dati. Il valore predefinito è 60 secondi.  
  
 **-ProfileName** *profile_name*  
 Specifica un profilo agente da utilizzare per i parametri dell'agente. Se **ProfileName** è NULL, il profilo agente è disabilitato. Se **ProfileName** non viene specificato, viene utilizzato il profilo predefinito per il tipo di agente. Per informazioni, vedere [Profili agenti di replica](../../../relational-databases/replication/agents/replication-agent-profiles.md).  
  
 **-PublisherFailoverPartner** *nome_server*[**\\***instance_name*]  
 Specifica l'istanza del partner di failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] che partecipa in una sessione di mirroring del database con il database di pubblicazione. Per ulteriori informazioni, vedere [il mirroring del Database e la replica e 40 #; SQL Server & #41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).  
  
 **-PublisherLogin** *publisher_login*  
 Nome dell'account di accesso del server di pubblicazione. Se **PublisherSecurityMode** è **0** (per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] autenticazione), questo parametro deve essere specificato.  
  
 **-PublisherPassword** *publisher_password*  
 Password del server di pubblicazione. Se **PublisherSecurityMode** è **0** (per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] autenticazione), questo parametro deve essere specificato.  
  
 **-PublisherSecurityMode** [**0**|**1**]  
 Specifica la modalità di sicurezza del server di pubblicazione. Il valore **0** indica [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] autenticazione (impostazione predefinita) e il valore di **1** indica la modalità di autenticazione di Windows.  
  
 **-QueryTimeOut** *query_time_out_seconds*  
 Numero di secondi prima del timeout delle query. Il valore predefinito è 300 secondi. L'agente di Merge utilizza anche il valore di **QueryTimeout** per determinare il tempo di attesa per la generazione di uno snapshot partizionato quando questo valore è maggiore di 1800.  
  
 **-SrcThreads** *number_of_source_threads*  
 Specifica il numero di thread di origine utilizzati dall'agente di merge per enumerare le modifiche dall'origine. L'origine è costituita dal Sottoscrittore durante il caricamento e dal server di pubblicazione durante il download. Il valore predefinito è **3**.  
  
 **-StartQueueTimeout** *start_queue_timeout_seconds*  
 È il numero massimo di secondi di attesa da parte dell'agente di Merge quando il numero di processi di merge simultanei in esecuzione raggiunge il limite impostato tramite il **@max_concurrent_merge** proprietà di **sp_addmergepublication**. Se viene raggiunto il numero massimo di secondi e l'agente di merge è ancora in attesa, si chiude. Un valore 0 indica che l'agente attende indefinitamente, sebbene possa essere annullato.  
  
 **-SubscriberDatabasePath** *subscriber_database_path*  
 È il percorso del database Jet (file con estensione mdb) se **SubscriberType** è **2** (consente una connessione a un database Jet senza un nome di origine dati (DSN) ODBC,).  
  
 **-SubscriberDBAddOption** [**0**| **1**| **2**| **3**]  
 Specifica se esiste un database Sottoscrittore.  
  
|Valore di SubscriberDBAddOption|Descrizione|  
|---------------------------------|-----------------|  
|**0**|Utilizza il database esistente (impostazione predefinita).|  
|**1**|Crea un nuovo database Sottoscrittore vuoto.|  
|**2**|Crea un nuovo database e lo collega al file specificato.|  
|**3**|Crea un nuovo database, collega il database e abilita tutte le sottoscrizioni che potrebbero essere presenti nel file.|  
  
> [!NOTE]  
>  Quando si utilizzano valori **2** e **3**, il percorso del database per il Sottoscrittore deve essere specificato nel **SubscriberDatabasePath** (opzione).  
  
 **SubscriberLogin -** *subscriber_login*  
 Nome dell'account di accesso del Sottoscrittore. Se **SubscriberSecurityMode** è **0** (per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] autenticazione), questo parametro deve essere specificato.  
  
 **-SubscriberPassword** *subscriber_password*  
 Password del Sottoscrittore. Se **SubscriberSecurityMode** è **0** (per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] autenticazione), questo parametro deve essere specificato.  
  
 **-SubscriberSecurityMode** [ **0**| **1**]  
 Specifica la modalità di sicurezza del Sottoscrittore. Il valore **0** indica [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] autenticazione (impostazione predefinita) e il valore di **1** indica la modalità di autenticazione di Windows.  
  
 **-SubscriberConflictClean** [ **0**| **1**]  
 Se le tabelle dei conflitti vengono pulite nel Sottoscrittore durante il processo di sincronizzazione, dove il valore è **1** indica che le tabelle dei conflitti nel Sottoscrittore vengono pulite. Questo parametro viene utilizzato solo per le sottoscrizioni alle pubblicazioni con registrazione dei conflitti decentralizzata.  
  
 **-SubscriberType** [ **0**| **1**| **3**| **4**| **5**| **6**| **7**| **8**]  
 Specifica il tipo di connessione al Sottoscrittore utilizzato dall'agente di merge. Solo il valore predefinito di **0** è supportato per questo parametro.  
  
 **-SubscriptionType**[ **0**| **1**| **2**]  
 Specifica il tipo di sottoscrizione per la distribuzione. Il valore **0** indica una sottoscrizione push (predefinito), un valore di **1** indica una sottoscrizione pull e il valore di **2** indica una sottoscrizione anonima.  
  
 **-SyncToAlternate** [ **0 | 1**]  
 Specifica se l'agente di merge sta eseguendo la sincronizzazione tra un Sottoscrittore e un server di pubblicazione alternativo. Il valore **1** indica che si tratta di un server di pubblicazione alternativo. Il valore predefinito è **0**.  
  
 **-UploadGenerationsPerBatch** *upload_generations_per_batch*  
 Numero di generazioni da elaborare in un singolo batch mentre vengono caricate le modifiche dal Sottoscrittore al server di pubblicazione. Una generazione è definita come un gruppo logico di modifiche per articolo. Il valore predefinito per un collegamento di comunicazione affidabile è **100**. Il valore predefinito per un collegamento di comunicazione non affidabile è **1**.  
  
 **-UploadReadChangesPerBatch** *upload_read_changes_per_batch*  
 Numero di modifiche da leggere in un singolo batch mentre vengono caricate le modifiche dal Sottoscrittore al server di pubblicazione. Il valore predefinito è **100**.  
  
 **-UploadWriteChangesPerBatch** *upload_write_changes_per_batch*  
 Numero di modifiche da applicare in un singolo batch mentre vengono caricate le modifiche dal Sottoscrittore al server di pubblicazione. Il valore predefinito è **100**.  
  
 **-UseInprocLoader**  
 Migliora le prestazioni dello snapshot iniziale facendo in modo che l'agente di merge utilizzi il comando BULK INSERT in caso di applicazione dei file di snapshot al Sottoscrittore. Questo parametro è deprecato in quanto non è compatibile con il tipo di dati XML. Se non si sta eseguendo la replica di dati XML, è possibile utilizzare questo parametro. Questo parametro non può essere utilizzato con snapshot in modalità carattere. Se si utilizza questo parametro, l'account del servizio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nel Sottoscrittore deve disporre di autorizzazioni di lettura nella directory in cui si trovano i file di dati di snapshot, con estensione bcp. Quando questo parametro non viene utilizzato, il driver ODBC caricato dall'agente legge dai file, pertanto il contesto di sicurezza dell'account del servizio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] non viene utilizzato.  
  
 **-Validate** [**0**|**1**|**2**|**3**]  
 Specifica se la convalida deve essere effettuata al termine della sessione di merge, e, in tal caso, indica il tipo di convalida. Il valore di **3** è il valore consigliato.  
  
|Valore di Validate|Descrizione|  
|--------------------|-----------------|  
|**0** (impostazione predefinita)|Nessuna convalida.|  
|**1**|Convalida solo tramite conteggio delle righe.|  
|**2**|Convalida mediante conteggio delle righe e checksum.|  
|**3**|Convalida mediante conteggio delle righe e checksum binario.|  
  
> [!NOTE]  
>  La convalida eseguita mediante checksum o checksum binario può segnalare erroneamente un problema se nel Sottoscrittore vi sono tipi di dati diversi rispetto al server di pubblicazione. Per ulteriori informazioni, vedere la sezione "Considerazioni per la convalida dei dati" in [convalidare i dati replicati](../../../relational-databases/replication/validate-replicated-data.md).  
  
 **-ValidateInterval** *validate_interval*  
 Frequenza, in minuti, di convalida della sottoscrizione in modalità continua. Il valore predefinito è **60** minuti.  
  
## Osservazioni  
  
> [!IMPORTANT]  
>  Se [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent è stato installato per l'esecuzione con un account di sistema locale anziché un account utente di dominio (impostazione predefinita), il servizio può accedere solo al computer locale. Se l'agente di merge in esecuzione in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent è configurato per l'utilizzo della modalità di autenticazione di Windows durante l'accesso a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], l'agente di merge si interrompe. L'impostazione predefinita prevede l'autenticazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 Per avviare l'agente di Merge, eseguire **replmerg.exe** dal prompt dei comandi. Per informazioni, vedere [degli eseguibili degli agenti di replica](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
 La cronologia dell'agente di merge per la sessione corrente non viene eliminata durante l'esecuzione in modalità continua. Un agente con esecuzione prolungata può comportare un numero elevato di voci nelle tabelle della cronologia di merge che potrebbero ridurre le prestazioni. Per risolvere questo problema, passare alla modalità pianificata o continuare a utilizzare la modalità continua, ma creare un processo dedicato per riavviare periodicamente l'agente di merge oppure ridurre i dettagli del livello di cronologia per diminuire il numero di righe e, pertanto, l'impatto sulle prestazioni.  
  
## Vedere anche  
 [Amministrazione dell'agente di replica](../../../relational-databases/replication/agents/replication-agent-administration.md)  
  
  