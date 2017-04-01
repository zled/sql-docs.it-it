---
title: "Miglioramento delle prestazioni della replica di tipo merge | Microsoft Docs"
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
  - "pubblicazioni [replica di SQL Server], progettazione e prestazioni"
  - "progettazione di database [SQL Server], prestazioni di replica"
  - "agente di merge, prestazioni"
  - "snapshot [replica di SQL Server], considerazioni sulle prestazioni"
  - "prestazioni della replica di tipo merge [replica di SQL Server]"
  - "sottoscrizioni [replica di SQL Server], considerazioni sulle prestazioni"
  - "prestazioni [replica di SQL Server], replica di tipo merge"
  - "agenti [replica di SQL Server], prestazioni"
ms.assetid: f929226f-b83d-4900-a07c-a62f64527c7f
caps.latest.revision: 47
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 47
---
# Miglioramento delle prestazioni della replica di tipo merge
  Dopo aver prendere in considerazione i suggerimenti sulle prestazioni generali descritti [miglioramento generale delle prestazioni di replica](../../../relational-databases/replication/administration/enhance-general-replication-performance.md), considerare queste aree aggiuntive specifiche di replica di tipo merge.  
  
## Progettazione di database  
  
-   Colonne di indice utilizzate in filtri di riga e filtri join.  
  
     Se si applica un filtro di riga a un articolo pubblicato, è necessario creare un indice per ogni colonna specificata nella clausola WHERE del filtro. Senza un indice, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] deve leggere ogni riga della tabella per determinare se la riga deve essere inclusa nella partizione. In presenza dell'indice, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] è in grado di individuare rapidamente le righe da includere. L'elaborazione più rapida si ottiene quando tramite la replica è possibile risolvere completamente la clausola WHERE del filtro solo in base all'indice.  
  
     È inoltre importante indicizzare tutte le colonne utilizzate nei filtri join. A ogni esecuzione dell'agente di merge viene eseguita la ricerca della tabella di base per determinare quali righe della tabella padre e delle tabelle correlate sono incluse in una partizione. La creazione di un indice delle colonne unite in join consente di evitare la lettura di ogni riga della tabella da parte di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] a ogni esecuzione dell'agente di merge.  
  
     Per ulteriori informazioni sui filtri, vedere [filtrare i dati pubblicati per la replica di tipo Merge](../../../relational-databases/replication/merge/filter-published-data-for-merge-replication.md).  
  
-   ‏Si considerino le tabelle in fase di sovranormalizzazione che includono tipi di dati LOB (Large Object).  
  
     Quando viene eseguita la sincronizzazione, è possibile che l'agente di merge debba leggere e trasferire l'intera riga di dati da un server di pubblicazione o un Sottoscrittore. Se la riga include colonne con dati LOB, questo processo può richiedere l'allocazione di memoria aggiuntiva e influire negativamente sulle prestazioni anche se tali colonne non sono state aggiornate. Per ridurre la probabilità di tale impatto negativo sulle prestazioni, è possibile inserire le colonne LOB in una tabella distinta utilizzando una relazione uno-a-uno con la parte rimanente della riga di dati. I tipi di dati **testo**, **ntext**, e **immagine** sono deprecati. Se è necessario includere dati LOB, è consigliabile utilizzare i tipi di dati **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, rispettivamente.  
  
## Progettazione della pubblicazione  
  
-   Impostare il livello di compatibilità della pubblicazione su 90RTM ([!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] o versione successiva).  
  
     A meno che uno o più sottoscrittori utilizzino una versione diversa di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], specificare che la pubblicazione deve supportare solo [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] o versione successiva. Ciò consente di sfruttare le nuove funzionalità e le ottimizzazioni delle prestazioni.  
  
-   Utilizzare impostazioni appropriate relative al periodo di memorizzazione della pubblicazione.  
  
     Il periodo di memorizzazione della pubblicazione, ovvero il periodo di tempo massimo prima che una sottoscrizione debba essere sincronizzata, determina la durata dell'archiviazione dei metadati di rilevamento. Un valore elevato può influire sulle prestazioni di elaborazione e archiviazione. Per ulteriori informazioni sull'impostazione del periodo di memorizzazione, vedere [disattivazione e scadenza della sottoscrizione](../../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
-   Utilizzare articoli di solo download per le tabelle modificate solo nel server di pubblicazione. Per ulteriori informazioni, vedere [Ottimizza prestazioni della replica di tipo Merge con gli articoli Download-Only](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md).  
  
### Progettazione e utilizzo dei filtri  
  
-   Limitare la complessità delle clausole dei filtri di riga.  
  
     Limitando la complessità dei criteri di filtro è possibile migliorare le prestazioni durante la valutazione da parte dell'agente di merge delle modifiche delle righe da inviare ai Sottoscrittori. Evitare di utilizzare selezioni secondarie all'interno delle clausole dei filtri di riga. Considerare, invece, l'opportunità di utilizzare filtri di join, in genere più efficienti se utilizzati per partizionare i dati di una tabella in base alla clausola del filtro di riga di un'altra tabella. Per ulteriori informazioni sull'applicazione di filtri, vedere [filtrare i dati pubblicati per la replica di tipo Merge](../../../relational-databases/replication/merge/filter-published-data-for-merge-replication.md).  
  
-   Utilizzare partizioni pre-calcolate con filtri con parametri (funzionalità utilizzata per impostazione predefinita). Per ulteriori informazioni, vedere [Ottimizza prestazioni filtro con parametri con le partizioni precalcolate](../../../relational-databases/replication/merge/optimize-parameterized-filter-performance-with-precomputed-partitions.md).  
  
     Le partizioni pre-calcolate impongono vari limiti al funzionamento dei filtri. Se l'applicazione non sono conformi a queste limitazioni, impostare il **keep_partition_changes** opzione **True**, che offre un miglioramento delle prestazioni. Per altre informazioni, vedere [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
-   Utilizzare partizioni non sovrapposte se i dati vengono filtrati ma non condivisi tra gli utenti.  
  
     La replica consente di ottimizzare le prestazioni dei dati che non vengono condivisi tra partizioni o sottoscrizioni. Per altre informazioni, vedere [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
-   Evitare di creare gerarchie di filtri join complesse.  
  
     I filtri join composti da più di cinque tabelle possono avere un impatto decisivo sulle prestazioni durante l'elaborazione di tipo merge. Se è necessario generare filtri join per cinque o più tabelle, è consigliabile optare per altre soluzioni:  
  
    -   Evitare di filtrare le tabelle che fungono principalmente da tabelle di ricerca, le tabelle di dimensioni ridotte e le tabelle non soggette a modifica, che è preferibile inserire nella pubblicazione senza ricorrere ad alcun filtro. È consigliabile utilizzare filtri join solo tra tabelle che devono essere partizionate tra i Sottoscrittori. Per ulteriori informazioni, vedere [filtri Join](../../../relational-databases/replication/merge/join-filters.md).  
  
    -   Considerare la denormalizzazione della progettazione del database o l'utilizzo di una tabella di mapping qualora in un join siano presenti molte tabelle. Ad esempio, se un venditore necessita solo dei dati relativi ai propri clienti e per associare un cliente a un determinato venditore sono necessari sei join, considerare l'opportunità di aggiungere alla tabella dei clienti una colonna che identifica il venditore. I dati del venditore sono ridondanti, ma i costi della denormalizzazione delle tabelle vengono compensati in una certa misura dai vantaggi a livello delle prestazioni per la partizione della replica.  
  
    -   Per migliorare le prestazioni delle partizioni pre-calcolate quando i batch contengono molte modifiche ai dati, progettare l'applicazione con attenzione. Assicurare che le modifiche ai dati nella tabella padre in un filtro join vengano apportate prima delle corrispondenti modifiche nelle tabelle figlio.  
  
-   Impostare il **join_unique_key** opzione **1** se logica lo consente.  
  
     Impostando questo parametro su **1** indica che la relazione tra le tabelle padre e figlio in un filtro join è uno a uno o uno a molti. Impostare questo parametro solo **1** Se si dispone di un vincolo nella colonna di join della tabella figlio che garantisce l'univocità. Se il parametro è impostato su **1** in modo non corretto, può verificarsi non convergenza dei dati. Per ulteriori informazioni, vedere [filtri Join](../../../relational-databases/replication/merge/join-filters.md).  
  
-   Non eseguire batch con molte modifiche se si utilizzano partizioni pre-calcolate.  
  
     Se l'agente di merge viene eseguito dopo un batch che contiene molte modifiche ai dati, tenterà di suddividere il batch di grandi dimensioni in batch minori. Nel frattempo altri processi dell'agente di merge potrebbero risultare bloccati. Provare a ridurre il numero di modifiche contenute in un batch e ad eseguire l'agente di merge tra i batch. Se questa operazione non può essere eseguita, aumentare il valore di **generation_leveling_threshold** per la pubblicazione.  
  
## Considerazioni sulle sottoscrizioni  
  
-   Scaglionare le pianificazioni di sincronizzazione delle sottoscrizioni.  
  
     Nel caso in cui un numero elevato di Sottoscrittori esegua la sincronizzazione con un server di pubblicazione, considerare l'opportunità di scaglionare le pianificazioni in modo che gli agenti di merge vengano eseguiti in momenti diversi. Per altre informazioni, vedere [Specify Synchronization Schedules](../../../relational-databases/replication/specify-synchronization-schedules.md).  
  
## Parametri dell'agente di merge  
 Per informazioni sull'agente di Merge e i relativi parametri, vedere [agente Merge repliche](../../../relational-databases/replication/agents/replication-merge-agent.md).  
  
-   Aggiornare tutti i sottoscrittori per le sottoscrizioni pull [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] o versione successiva.  
  
     Aggiorna il sottoscrittore a [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] o versione successiva consente di aggiornare l'agente di Merge utilizzato dalle sottoscrizioni nel Sottoscrittore. Per poter utilizzare molte delle nuove funzionalità e ottimizzazioni delle prestazioni, è necessario l'agente di merge di [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] o versione successiva.  
  
-   Se una sottoscrizione viene sincronizzata tramite una connessione veloce e le modifiche vengono inviate dal server di pubblicazione e sottoscrizione, utilizzare il **– ParallelUploadDownload** parametro per l'agente di Merge.  
  
     [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] stato introdotto un nuovo parametro di agente di Merge: **– ParallelUploadDownload**. L'impostazione di questo parametro consente di elaborare in parallelo le modifiche caricate nel server di pubblicazione e le modifiche scaricate nel Sottoscrittore. Ciò è utile negli ambienti caratterizzati da volumi di traffico elevati con un'ampia larghezza di banda di rete. I parametri degli agenti possono essere specificati nei profili agente e dalla riga di comando. Per altre informazioni, vedere:  
  
    -   [Work with Replication Agent Profiles](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)  
  
    -   [Visualizzare e modificare i parametri di prompt dei comandi dell'agente di replica & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/agents/view and modify replication agent command prompt parameters.md)  
  
    -   [Concetti di base relativi ai file eseguibili dell'agente di replica](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)  
  
-   Provare ad aumentare il valore di **- MakeGenerationInterval** parametro, specialmente se la sincronizzazione prevede più caricamenti dai sottoscrittori che download nei Sottoscrittori.  
  
-   Quando si sincronizzano righe di dati con un'ingente quantità di dati, ad esempio righe con colonne LOB, la sincronizzazione tramite il Web può richiedere l'allocazione di memoria aggiuntiva e ridurre le prestazioni. Ciò si verifica quando l'agente di merge genera un messaggio XML contenente un numero troppo elevato di righe di dati con ingenti quantità di dati. Se l'agente di merge utilizza una quantità eccessiva di risorse durante la sincronizzazione tramite il Web, ridurre il numero di righe inviate in un singolo messaggio in uno dei modi seguenti:  
  
    -   Utilizzare il profilo agente a collegamento lento per l'agente di merge. Per altre informazioni, vedere [Replication Agent Profiles](../../../relational-databases/replication/agents/replication-agent-profiles.md).  
  
    -   Ridurre il **- DownloadGenerationsPerBatch** e **- UploadGenerationsPerBatch** i parametri per l'agente di Merge in un valore pari a 10 o meno. Il valore predefinito di questi parametri è 50.  
  
## Considerazioni sugli snapshot  
  
-   Creare una colonna ROWGUIDCOL nelle tabelle di grandi dimensioni prima di generare lo snapshot iniziale.  
  
     La replica di tipo merge richiede che ogni tabella pubblicata includa una colonna ROWGUIDCOL. Se la colonna ROWGUIDCOL non è disponibile quando l'agente snapshot crea i file di snapshot iniziali, l'agente dovrà innanzitutto aggiungere e popolare la colonna ROWGUIDCOL. Per migliorare le prestazioni delle operazioni di generazione di snapshot durante la replica di tipo merge, creare la colonna ROWGUIDCOL in tutte le tabelle prima della pubblicazione. La colonna può avere qualsiasi nome (**rowguid** viene utilizzato dall'agente Snapshot per impostazione predefinita), ma devono avere i seguenti dati di tipo caratteristiche:  
  
    -   Un tipo di dati UNIQUEIDENTIFIER.  
  
    -   Un valore predefinito di tipo NEWSEQUENTIALID() o NEWID(). Per garantire un migliore livello di prestazioni durante l'inserimento e il rilevamento di modifiche, è consigliabile utilizzare NEWSEQUENTIALID().  
  
    -   Il set di proprietà ROWGUIDCOL.  
  
    -   Un indice univoco nella colonna.  
  
-   Creare snapshot preliminari e/o consentire ai Sottoscrittori di richiedere la generazione e l'applicazione di snapshot alla prima sincronizzazione.  
  
     Utilizzare una o entrambe le opzioni per generare snapshot per le pubblicazioni che utilizzando filtri con parametri. Se non si specifica una di queste opzioni, le sottoscrizioni vengono inizializzate tramite una serie di SELECT e le istruzioni INSERT, anziché utilizzare il **bcp** utilità; questo processo è molto lento. Per altre informazioni, vedere [Snapshots for Merge Publications with Parameterized Filters](../../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md).  
  
## Considerazioni sulla manutenzione e sul monitoraggio  
  
-   Eseguire occasionalmente la reindicizzazione delle tabelle di sistema per la replica di tipo merge.  
  
     Come parte della manutenzione della replica di tipo merge, verificare occasionalmente l'aumento delle tabelle di sistema associate alla replica di tipo merge: **MSmerge_contents**, **MSmerge_genhistory**, e **MSmerge_tombstone**, **MSmerge_current_partition_mappings**, e **MSmerge_past_partition_mappings**. Reindicizzare periodicamente queste tabelle. Per ulteriori informazioni, vedere [riorganizzazione e ricompilazione degli indici](../../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).  
  
-   Monitorare la sincronizzazione delle prestazioni tramite il **Cronologia sincronizzazione** scheda in Monitoraggio replica.  
  
     Per la replica di tipo merge, Monitoraggio replica vengono visualizzate statistiche dettagliate nel **Cronologia sincronizzazione** scheda per ogni articolo elaborato durante la sincronizzazione, inclusa la quantità di tempo impiegato in ogni fase di elaborazione (caricamento delle modifiche, download delle modifiche e così via). Ciò può essere utile per individuare tabelle specifiche che determinano rallentamenti ed è l'opzione migliore per risolvere problemi relativi alle prestazioni delle sottoscrizioni di tipo merge. Per ulteriori informazioni sulla visualizzazione di statistiche dettagliate, vedere [visualizzare le informazioni ed esecuzione delle attività degli agenti associati con una sottoscrizione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
  