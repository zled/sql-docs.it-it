---
title: "Agente di lettura coda repliche | Microsoft Docs"
ms.custom: ""
ms.date: "06/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "agenti [SQL Server replication], agente di lettura coda"
  - "prompt dei comandi [replica di SQL Server]"
  - "agente di lettura coda, informazioni di riferimento sui parametri"
  - "agente di lettura coda, file eseguibili"
ms.assetid: 8e227793-11f6-47c6-99dc-ffc282f5d4bf
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# Agente di lettura coda repliche
  L'agente di lettura coda repliche è un eseguibile che legge i messaggi archiviati in un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] coda o un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] coda di messaggi e quindi applica tali messaggi al server di pubblicazione. L'agente di lettura coda viene utilizzato con le pubblicazioni snapshot e transazionali che consentono l'aggiornamento in coda.  
  
> [!NOTE]  
>  I parametri possono essere specificati in qualsiasi ordine. Quando i parametri facoltativi non vengono specificati, vengono utilizzati i valori predefiniti basati sul profilo agente predefinito.  
  
## Sintassi  
  
```  
  
qrdrsvc [-?]  
[-Continuous]  
[-DefinitionFile definition_file]  
[-Distributor server_name[\instance_name]]  
[-DistributionDB distribution_database]  
[-DistributorLogin distributor_login]  
[-DistributorPassword distributor_password]  
[-DistributorSecurityMode [0|1]]  
[-EncryptionLevel [0|1|2]]  
[-HistoryVerboseLevel [0|1|2|3]]  
[-LoginTimeOut login_time_out_seconds]  
[-Output output_path_and_file_name]  
[-OutputVerboseLevel [0|1|2]]  
[-PollingInterval polling_interval]  
[-PublisherFailoverPartner server_name[\instance_name] ]  
[-ProfileName agent_profile_name]  
[-QueryTimeOut query_time_out_seconds]  
[-ResolverState [1|2|3]]  
```  
  
## Argomenti  
 **-?**  
 Visualizza le informazioni sull'utilizzo.  
  
 **-Continuous**  
 Specifica se l'agente tenta di elaborare continuamente le transazioni in coda. Se è specificato, l'agente continua l'esecuzione anche se non vi sono transazioni in coda in sospeso in alcuno dei Sottoscrittori.  
  
 **-DefinitionFile** *def_path_and_file_name*  
 Percorso del file di definizione dell'agente. Un file di definizione dell'agente contiene argomenti della riga di comando per l'agente. Il contenuto del file viene analizzato come file eseguibile. Utilizzare virgolette doppie (") per specificare valori dell'argomento contenenti caratteri arbitrari.  
  
 **-Server di distribuzione** *nome_server*[**\\***instance_name*]  
 Nome del database di distribuzione. Specificare *nome_server* per l'istanza predefinita di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] su tale server. Specificare *nome_server*\\*instance_name* per un'istanza denominata di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] su tale server. Se non specificato, per impostazione predefinita viene utilizzato il nome dell'istanza predefinita di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nel computer locale.  
  
 **-DistributionDB** *distribution_database*  
 Database di distribuzione.  
  
 **-DistributorLogin** *distributor_login*  
 Nome dell'account di accesso del database di distribuzione.  
  
 **-DistributorPassword** *distributor_password*  
 Password del database di distribuzione.  
  
 **-DistributorSecurityMode** [ **0**| **1**]  
 Specifica la modalità di sicurezza del database di distribuzione. Il valore **0** indica [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] modalità di autenticazione (impostazione predefinita) e il valore di **1** indica la modalità di autenticazione di Windows.  
  
 **-EncryptionLevel** [ **0** | **1** | **2** ]  
 Livello di crittografia SSL (Secure Sockets Layer) utilizzato dall'agente di lettura coda quando vengono stabilite le connessioni.  
  
|Valore di EncryptionLevel|Descrizione|  
|---------------------------|-----------------|  
|**0**|Specifica che SSL non viene utilizzato.|  
|**1**|Specifica che SSL viene utilizzato, ma l'agente non verifica che il certificato server SSL sia firmato da un'autorità emittente attendibile.|  
|**2**|Specifica che SSL viene utilizzato e che il certificato viene verificato.|  
  
 Per ulteriori informazioni, vedere [Cenni preliminari sulla sicurezza & #40; Replica & #41;](../../../relational-databases/replication/security/security-overview-replication.md).  
  
 **-HistoryVerboseLevel** [ **0**| **1**| **2**| **3**]  
 Specifica la quantità di cronologia registrata durante un'operazione dell'agente di lettura coda. È possibile ridurre l'effetto della registrazione della cronologia sulle prestazioni selezionando **1**.  
  
|Valore di HistoryVerboseLevel|Descrizione|  
|-------------------------------|-----------------|  
|**0**|Nessuna registrazione della cronologia (opzione non consigliata).|  
|**1**|Valore predefinito. Aggiorna sempre un messaggio di cronologia precedente con lo stesso stato (avvio, avanzamento, esito positivo e così via). Se non è presente un record precedente con lo stesso stato, inserisce un nuovo record.|  
|**2**|Inserisce nuovi record della cronologia, inclusi record per messaggi inattivi o messaggi di processo con esecuzione prolungata.|  
|**3**|Inserisce nuovi record della cronologia che includono informazioni aggiuntive che potrebbero essere utili per la risoluzione dei problemi.|  
  
 **-LoginTimeOut** *login_time_out_seconds*  
 Numero di secondi prima del timeout di accesso. Il valore predefinito è 15 secondi.  
  
 **-Output** *output_path_and_file_name*  
 Percorso del file di output dell'agente. Se non viene specificato il nome file, l'output viene inviato alla console. Se il nome file specificato esiste già, l'output viene aggiunto al file.  
  
 **-OutputVerboseLevel** [ **0**| **1**| **2**]  
 Specifica se l'output deve essere dettagliato. Se il livello di dettaglio è **0**, vengono stampati solo i messaggi di errore. Se il livello di dettaglio è **1**, vengono stampati tutti i messaggi di report di stato. Se il livello di dettaglio è **2** (predefinito), vengono stampati tutti i messaggi di errore e i messaggi di rapporto di stato di avanzamento, che è utile per il debug.  
  
 **-PollingInterval** *polling_interval*  
 Rilevante solo per sottoscrizioni aggiornabili che utilizzano code basate su [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Specifica la frequenza, in secondi, di polling della coda [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per le transazioni in coda in sospeso. Il valore può essere compreso tra 0 e 240 secondi. Il valore predefinito è 5 secondi.  
  
 **-PublisherFailoverPartner** *nome_server*[**\\***instance_name*]  
 Specifica l'istanza del partner di failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] che partecipa in una sessione di mirroring del database con il database di pubblicazione. Per ulteriori informazioni, vedere [il mirroring del Database e la replica e 40 #; SQL Server & #41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).  
  
 **-ProfileName** *agent_profile_name*  
 Nome di un profilo agente utilizzato per fornire un set di valori predefiniti all'agente. Per informazioni, vedere [Profili agenti di replica](../../../relational-databases/replication/agents/replication-agent-profiles.md).  
  
 **-QueryTimeOut** *query_time_out_seconds*  
 Numero di secondi prima del timeout delle query. Il valore predefinito è 1800 secondi.  
  
 **-ResolverState** [ **1**| **2**| **3**]  
 Specifica in che modo vengono risolti i conflitti degli aggiornamenti in coda. Il valore **1** indica i prevale il conflitto e l'oggetto in conflitto verrà rollback nel server di pubblicazione e sottoscrizione ad aggiornamento di origine della transazione in coda, l'elaborazione delle transazioni in coda successive continuerà. Il valore **2** indica prevale il sottoscrittore e la transazione in coda sostituirà i valori nel server di pubblicazione. Il valore **3** indica che qualsiasi conflitto comporterà la reinizializzazione del sottoscrittore; prevale il server di pubblicazione, l'elaborazione delle transazioni in coda successive verrà interrotta e la sottoscrizione verrà reinizializzata. L'impostazione predefinita è **1** per le pubblicazioni transazionali e **3** per le pubblicazioni snapshot.  
  
## Osservazioni  
 Per avviare l'agente di lettura coda, eseguire **qrdrsvc.exe** dal prompt dei comandi. Per informazioni, vedere [degli eseguibili degli agenti di replica](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
## Vedere anche  
 [Amministrazione dell'agente di replica](../../../relational-databases/replication/agents/replication-agent-administration.md)  
  
  