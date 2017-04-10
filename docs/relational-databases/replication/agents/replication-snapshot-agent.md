---
title: "Agente snapshot repliche | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "agente snapshot, eseguibili"
  - "agenti [replica di SQL Server], agente snapshot"
  - "prompt dei comandi [replica di SQL Server]"
  - "agente snapshot, riferimento sui parametri"
ms.assetid: 2028ba45-4436-47ed-bf79-7c957766ea04
caps.latest.revision: 41
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 41
---
# Agente snapshot repliche
  Agente snapshot repliche è un file eseguibile che consente di preparare i file di snapshot contenenti lo schema e i dati delle tabelle pubblicate e degli oggetti di database, di archiviare i file nella cartella snapshot e di registrare i processi di sincronizzazione nel database di distribuzione.  
  
> [!NOTE]  
>  I parametri possono essere specificati in qualsiasi ordine.  
  
## Sintassi  
  
```  
  
snapshot [ -?]   
-Publisher server_name[\instance_name]   
-Publication publication_name   
[-70Subscribers]   
[-BcpBatchSize bcp_batch_size]  
[-DefinitionFile def_path_and_file_name]  
[-Distributor server_name[\instance_name]]  
[-DistributorDeadlockPriority [-1|0|1] ]  
[-DistributorLogin distributor_login]  
[-DistributorPassword distributor_password]  
[-DistributorSecurityMode [0|1] ]  
[-DynamicFilterHostName dynamic_filter_host_name]  
[-DynamicFilterLogin dynamic_filter_login]  
[-DynamicSnapshotLocation dynamic_snapshot_location]   
[-EncryptionLevel [0|1|2]]  
[-FieldDelimiter field_delimiter]  
[-HistoryVerboseLevel [0|1|2|3] ]  
[-HRBcpBlocks number_of_blocks ]  
[-HRBcpBlockSize block_size ]  
[-HRBcpDynamicBlocks ]  
[-KeepAliveMessageInterval keep_alive_interval]  
[-LoginTimeOut login_time_out_seconds]  
[-MaxBcpThreads number_of_threads ]  
[-MaxNetworkOptimization [0|1]]  
[-Output output_path_and_file_name]  
[-OutputVerboseLevel [0|1|2] ]  
[-PacketSize packet_size]  
[-ProfileName profile_name]  
[-PublisherDB publisher_database]  
[-PublisherDeadlockPriority [-1|0|1] ]  
[-PublisherFailoverPartner server_name[\instance_name] ]  
[-PublisherLogin publisher_login]  
[-PublisherPassword publisher_password]   
[-PublisherSecurityMode [0|1] ]  
[-QueryTimeOut query_time_out_seconds]  
[-ReplicationType [1|2] ]  
[-RowDelimiter row_delimiter]  
[-StartQueueTimeout start_queue_timeout_seconds]  
[-UsePerArticleContentsView use_per_article_contents_view]  
```  
  
## Argomenti  
 **-?**  
 Stampa tutti i parametri disponibili.  
  
 **-Server di pubblicazione**  *nome_server*[**\\***instance_name*]    
 Nome del server di pubblicazione. Specificare server_name per l'istanza predefinita di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] su tale server. Specificare *nome_server***\\***instance_name* per un'istanza denominata di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] su tale server.  
  
 **-Pubblicazione** *pubblicazione*  
 Nome della pubblicazione. Questo parametro è valido solo se la pubblicazione è configurata in modo che sia sempre disponibile uno snapshot per le sottoscrizioni nuove o reinizializzate.  
  
 **-70Subscribers**  
 Deve essere utilizzata se i Sottoscrittori eseguono [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] versione 7.0.  
  
 **-BcpBatchSize** *bcp*_ *batch*\_ *dimensioni*  
 Numero di righe da inviare in un'operazione di copia bulk. Quando si esegue un'operazione **bcp in** , la dimensione del batch indica il numero di righe da inviare al server come unica transazione, nonché il numero di righe che devono essere inviate prima che l'agente di distribuzione registri un messaggio di stato **bcp** . Quando si esegue un **bcp out** viene utilizzata l'operazione, una dimensione batch fissa di 1000. Il valore 0 indica che non vengono registrati messaggi.  
  
 **-DefinitionFile** *def_path_and_file_name*  
 Percorso del file di definizione dell'agente. Un file di definizione dell'agente contiene argomenti della riga di comando per l'agente. Il contenuto del file viene analizzato come file eseguibile. Utilizzare virgolette doppie (") per specificare valori dell'argomento contenenti caratteri arbitrari.  
  
 **-Server di distribuzione** *nome_server*[**\\***instance_name*]  
 Nome del database di distribuzione. Specificare *nome_server* per l'istanza predefinita di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] su tale server. Specificare *nome_server***\\***instance_name* per un'istanza denominata di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] su tale server.  
  
 **-DistributorDeadlockPriority** [**-1**|**0**|**1**]  
 Priorità della connessione dell'agente snapshot con il server di distribuzione quando si verifica un deadlock. Questo parametro è specificato per risolvere deadlock che possono verificarsi tra l'agente snapshot e le applicazioni utente durante la generazione dello snapshot.  
  
|Valore di DistributorDeadlockPriority|Descrizione|  
|---------------------------------------|-----------------|  
|**-1**|Le applicazioni diverse dall'agente snapshot hanno la priorità quando si verifica un deadlock nel server di distribuzione.|  
|**0** (predefinito)|La priorità non è assegnata.|  
|**1**|L'agente snapshot ha la priorità quando si verifica un deadlock nel server di distribuzione.|  
  
 **-DistributorLogin** *distributor_login*  
 Account di accesso utilizzato per la connessione al server di distribuzione mediante l'autenticazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 **-DistributorPassword** *distributor_password*  
 Password utilizzata per la connessione al server di distribuzione mediante l'autenticazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. .  
  
 **-DistributorSecurityMode** [ **0**| **1**]  
 Specifica la modalità di sicurezza del database di distribuzione. Il valore **0** indica [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] modalità di autenticazione (impostazione predefinita) e il valore di **1** indica la modalità di autenticazione di Windows.  
  
 **-DynamicFilterHostName** *dynamic_filter_host_name*  
 Viene utilizzato per impostare un valore per [HOST_NAME & #40; Transact-SQL & #41;](../../../t-sql/functions/host-name-transact-sql.md) nel filtro di quando uno snapshot dinamico viene creato. Se, ad esempio, la clausola di filtro di subset `rep_id = HOST_NAME()` specificato per un articolo, e si imposta la **DynamicFilterHostName** proprietà su "FBJones" prima di chiamare l'agente di Merge, solo le righe con "FBJones" **rep_id** colonna verrà replicata.  
  
 **-DynamicFilterLogin** *dynamic_filter_login*  
 Viene utilizzato per impostare un valore per [SUSER_SNAME & #40; Transact-SQL & #41;](../../../t-sql/functions/suser-sname-transact-sql.md)nel filtro di quando uno snapshot dinamico viene creato. Se, ad esempio, la clausola di filtro di subset `user_id = SUSER_SNAME()` specificato per un articolo, e si imposta il **DynamicFilterLogin** proprietà su "rsmith" prima di chiamare il **eseguire** metodo il **SQLSnapshot** dell'oggetto, solo le righe con "rsmith" **user_id** colonna verrà inclusi nello snapshot.  
  
 **-DynamicSnapshotLocation** *dynamic_snapshot_location*  
 Posizione di generazione dello snapshot dinamico.  
  
 **-EncryptionLevel** [ **0** | **1** | **2** ]  
 Livello di crittografia SSL (Secure Sockets Layer) utilizzato dall'agente snapshot quando vengono stabilite le connessioni.  
  
|Valore di EncryptionLevel|Descrizione|  
|---------------------------|-----------------|  
|**0**|Specifica che SSL non viene utilizzato.|  
|**1**|Specifica che SSL viene utilizzato, ma l'agente non verifica che il certificato server SSL sia firmato da un'autorità emittente attendibile.|  
|**2**|Specifica che SSL viene utilizzato e che il certificato viene verificato.|  
  
 Per ulteriori informazioni, vedere [Cenni preliminari sulla sicurezza & #40; Replica & #41;](../../../relational-databases/replication/security/security-overview-replication.md).  
  
 **-FieldDelimiter** *field_delimiter*  
 Carattere o sequenza di caratteri che contrassegna la fine di un campo nel file di dati di copia bulk [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il valore predefinito è \n\<x$3>\n.  
  
 **-HistoryVerboseLevel** [ **1**| **2**| **3**]  
 Specifica la quantità di cronologia registrata durante un'operazione snapshot. È possibile ridurre l'effetto della registrazione della cronologia sulle prestazioni selezionando **1**.  
  
|Valore di HistoryVerboseLevel|Descrizione|  
|-------------------------------|-----------------|  
|**0**|I messaggi di stato vengono scritti nella console o in un file di output. I record della cronologia non vengono registrati nel database di distribuzione.|  
|**1**|Aggiorna sempre un messaggio di cronologia precedente con lo stesso stato (avvio, avanzamento, esito positivo e così via). Se non è presente un record precedente con lo stesso stato, inserisce un nuovo record.|  
|**2** (impostazione predefinita)|Inserisce nuovi record della cronologia, a meno che il record sia per eventi come messaggi inattivi o messaggi di processo con esecuzione prolungata, nel qual caso aggiorna i record precedenti.|  
|**3**|Inserisce sempre nuovi record, a meno che non si tratti di record per messaggi inattivi.|  
  
 **-HRBcpBlocks** *number_of_blocks*  
 È il numero di **bcp** blocchi di dati che vengono messe in coda tra i thread writer e lettore. Il valore predefinito è 50. **HRBcpBlocks** viene utilizzato solo con pubblicazioni Oracle.  
  
> [!NOTE]  
>  Questo parametro viene utilizzato per ottimizzare le prestazioni di **bcp** prestazioni dal server di pubblicazione Oracle.  
  
 -**HRBcpBlockSize***block_size*  
 È la dimensione, espressa in kilobyte (KB), di ogni **bcp** blocco di dati. Il valore predefinito è 64 KB. **HRBcpBlocks** viene utilizzato solo con pubblicazioni Oracle.  
  
> [!NOTE]  
>  Questo parametro viene utilizzato per ottimizzare le prestazioni di **bcp** prestazioni dal server di pubblicazione Oracle.  
  
 **-HRBcpDynamicBlocks**  
 È o meno le dimensioni di ogni **bcp** blocco di dati può aumentare in modo dinamico. **HRBcpBlocks** viene utilizzato solo con pubblicazioni Oracle.  
  
> [!NOTE]  
>  Questo parametro viene utilizzato per ottimizzare le prestazioni di **bcp** prestazioni dal server di pubblicazione Oracle.  
  
 **-KeepAliveMessageInterval** *keep_alive_interval*  
 È la quantità di tempo, espresso in secondi, di attesa prima della registrazione "in attesa di messaggi di back-end" dell'agente Snapshot per il [MSsnapshot_history](../../../relational-databases/system-tables/mssnapshot-history-transact-sql.md) tabella. Il valore predefinito è 300 secondi.  
  
 **-LoginTimeOut** *login_time_out_seconds*  
 Numero di secondi prima del timeout di accesso. Il valore predefinito è **15** secondi.  
  
 **-MaxBcpThreads** *number_of_threads*  
 Specifica il numero di operazioni di copia bulk che possono essere eseguite in parallelo. Il numero massimo di connessioni ODBC e thread presenti simultaneamente corrisponde a **MaxBcpThreads** o al numero di richieste di copia bulk presenti nella transazione di sincronizzazione nel database di distribuzione, a seconda di quale sia il valore minore. **MaxBcpThreads** deve avere un valore maggiore di **0** e non presenta alcun limite superiore hardcoded. Il valore predefinito è **1**.  
  
 \- **MaxNetworkOptimization** [ **0**| **1**]  
 Indica se le eliminazioni irrilevanti vengono inviate al Sottoscrittore. Le eliminazioni irrilevanti sono comandi DELETE inviati ai Sottoscrittori per righe che non appartengono alla partizione del Sottoscrittore. Le eliminazioni irrilevanti non influiscono sulla convergenza o sull'integrità dei dati, ma possono comportare traffico di rete non necessario. Il valore predefinito di **MaxNetworkOptimization** è **0**. L'impostazione **MaxNetworkOptimization** a **1** riducendo al minimo la possibilità di eliminazioni irrilevanti, pertanto la riduzione del traffico di rete e massimizzando ottimizzazione della rete. Impostando questo parametro su **1** possibile aumentare l'archiviazione dei metadati e causare una riduzione del server di pubblicazione se sono presenti più livelli di filtri di join e filtri di subset complessi delle prestazioni. Deve valutare la topologia di replica e impostare con attenzione **MaxNetworkOptimization** a **1** solo se il traffico di rete da eliminazioni irrilevanti è eccessivo.  
  
> [!NOTE]  
>  Impostando questo parametro su **1** è utile solo quando l'opzione di ottimizzazione della sincronizzazione della pubblicazione di tipo merge è impostata su **true** (il **@keep_partition_changes** parametro [sp_addmergepublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)).  
  
 **-Output** *output_path_and_file_name*  
 Percorso del file di output dell'agente. Se non viene specificato il nome file, l'output viene inviato alla console. Se il nome file specificato esiste già, l'output viene aggiunto al file.  
  
 **-OutputVerboseLevel** [ **0**| **1**| **2**]  
 Specifica se l'output deve essere dettagliato.  
  
|Valore di OutputVerboseLevel|Descrizione|  
|------------------------------|-----------------|  
|**0**|Vengono stampati solo i messaggi di errore.|  
|**1** (impostazione predefinita)|Vengono stampati tutti i messaggi di report di stato (impostazione predefinita).|  
|**2**|Vengono stampati tutti i messaggi di errore e i messaggi di report di stato. Questa opzione è utile per l'esecuzione del debug.|  
  
 **-PacketSize** *packet_size*  
 Dimensione del pacchetto, in byte, utilizzata dall'agente snapshot durante la connessione a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il valore predefinito è 8192 byte.  
  
> [!NOTE]  
>  È consigliabile modificare le dimensioni dei pacchetti solo se si è certi che l'operazione determinerà un miglioramento delle prestazioni. Per la maggior parte delle applicazioni, le dimensioni predefinite risultano ottimali.  
  
 **-ProfileName** *profile_name*  
 Specifica un profilo agente da utilizzare per i parametri dell'agente. Se **ProfileName** è NULL, il profilo agente è disabilitato. Se **ProfileName** non viene specificato, viene utilizzato il profilo predefinito per il tipo di agente. Per informazioni, vedere [Profili agenti di replica](../../../relational-databases/replication/agents/replication-agent-profiles.md).  
  
 **-PublisherDB** *publisher_database*  
 Nome del database di pubblicazione. *Questo parametro non è supportato per server di pubblicazione Oracle*.  
  
 **-PublisherDeadlockPriority** [**-1**|**0**|**1**]  
 Priorità della connessione dell'agente snapshot con il server di pubblicazione quando si verifica un deadlock. Questo parametro è specificato per risolvere deadlock che possono verificarsi tra l'agente snapshot e le applicazioni utente durante la generazione dello snapshot.  
  
|Valore di PublisherDeadlockPriority|Descrizione|  
|-------------------------------------|-----------------|  
|**-1**|Le applicazioni diverse dall'agente snapshot hanno la priorità quando si verifica un deadlock nel server di pubblicazione.|  
|**0** (predefinito)|La priorità non è assegnata.|  
|**1**|L'agente snapshot ha la priorità quando si verifica un deadlock nel server di pubblicazione.|  
  
 **-PublisherFailoverPartner** *nome_server*[**\\***instance_name*]  
 Specifica l'istanza del partner di failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] che partecipa in una sessione di mirroring del database con il database di pubblicazione. Per ulteriori informazioni, vedere [il mirroring del Database e la replica e 40 #; SQL Server & #41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).  
  
 **-PublisherLogin** *publisher_login*  
 Account di accesso utilizzato per la connessione al server di pubblicazione mediante l'autenticazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 **-PublisherPassword**  *publisher_password*  
 Password utilizzata per la connessione al server di pubblicazione mediante l'autenticazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. .  
  
 **-PublisherSecurityMode** [ **0**| **1**]  
 Specifica la modalità di sicurezza del server di pubblicazione. Il valore **0** indica [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] autenticazione (impostazione predefinita) e il valore di **1** indica la modalità di autenticazione di Windows.  
  
 **-QueryTimeOut** *query_time_out_seconds*  
 Numero di secondi prima del timeout delle query. Il valore predefinito è 1800 secondi.  
  
 **-ReplicationType** [ **1**| **2**]  
 Specifica il tipo di replica. Il valore **1** indica la replica transazionale e il valore di **2** indica la replica di tipo merge.  
  
 **-RowDelimiter** *row_delimiter*  
 Carattere o sequenza di caratteri che contrassegna la fine di una riga nel file di dati di copia bulk [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il valore predefinito è \n\<,@g>\n.  
  
 **-StartQueueTimeout** *start_queue_timeout_seconds*  
 È il numero massimo di secondi di attesa da parte dell'agente Snapshot quando il numero di processi snapshot dinamici simultanei in esecuzione raggiunge il limite impostato tramite il **@max_concurrent_dynamic_snapshots** proprietà di [sp_addmergepublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Se viene raggiunto il numero massimo di secondi e l'agente snapshot è ancora in attesa, si chiude. Un valore 0 indica che l'agente attende indefinitamente, sebbene possa essere annullato.  
  
 \- **UsePerArticleContentsView** *use_per_article_contents_view*  
 Questo parametro è deprecato ed è ancora supportato solo per garantire la compatibilità con le versioni precedenti.  
  
## Osservazioni  
  
> [!IMPORTANT]  
>  Se [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent è stato installato per l'esecuzione con un account di sistema locale anziché un account utente di dominio (impostazione predefinita), il servizio può accedere solo al computer locale. Se l'agente snapshot in esecuzione in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent è configurato per l'utilizzo della modalità di autenticazione di Windows durante l'accesso a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], l'agente snapshot si interrompe. L'impostazione predefinita prevede l'autenticazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 Per avviare l'agente Snapshot, eseguire **snapshot.exe** dal prompt dei comandi. Per informazioni, vedere [degli eseguibili degli agenti di replica](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
## Vedere anche  
 [Amministrazione dell'agente di replica](../../../relational-databases/replication/agents/replication-agent-administration.md)  
  
  