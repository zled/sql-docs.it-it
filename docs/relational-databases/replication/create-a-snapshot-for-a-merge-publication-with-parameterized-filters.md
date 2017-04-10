---
title: "Creazione di uno snapshot per una pubblicazione di tipo merge con filtri con parametri | Microsoft Docs"
ms.custom: ""
ms.date: "05/03/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "filtri con parametri [replica di SQL Server], snapshot"
  - "snapshot [replica di SQL Server], filtri con parametri e"
  - "filtri [replica di SQL Server], con parametri"
ms.assetid: 00dfb229-f1de-4d33-90b0-d7c99ab52dcb
caps.latest.revision: 45
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 45
---
# Creazione di uno snapshot per una pubblicazione di tipo merge con filtri con parametri
  In questo argomento viene descritto come creare un snapshot per una pubblicazione di tipo merge con i filtri con parametri in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] o Replication Management Objects (RMO).  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Indicazioni](#Recommendations)  
  
-   **Per creare uno snapshot per una pubblicazione di tipo merge con filtri con parametri, utilizzare:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Oggetti RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Recommendations"></a> Indicazioni  
  
-   Quando si genera uno snapshot per una pubblicazione di tipo merge utilizzando filtri con parametri, è necessario innanzitutto generare uno snapshot (schema) standard che contiene tutti i dati pubblicati e i metadati del Sottoscrittore per la sottoscrizione. Per altre informazioni, vedere [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md). Dopo aver creato lo snapshot dello schema, è possibile generare lo snapshot che contiene la partizione dei dati pubblicati specifica del Sottoscrittore.  
  
-   Se il filtro di uno o più articoli nella pubblicazione restituisce partizioni non sovrapposte univoche per ogni sottoscrizione, i metadati vengono eliminati a ogni esecuzione dell'agente di merge. Lo snapshot partizionato scade quindi più rapidamente. Quando si utilizza questa opzione, è consigliabile consentire ai Sottoscrittori di inizializzare la generazione e il recapito dello snapshot. Per ulteriori informazioni sulle opzioni di filtro, vedere la sezione "Impostazione 'opzioni di partizionamento'" di [snapshot per pubblicazioni di tipo Merge con filtri con parametri](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md).  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Genera gli snapshot per le partizioni nel **partizioni di dati** pagina della **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo. Per ulteriori informazioni sull'accesso a questa finestra di dialogo, vedere [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md). È possibile consentire ai Sottoscrittori di avviare la generazione e il recapito degli snapshot e/o di generare snapshot.  
  
 Prima di generare gli snapshot per una o più partizioni, è necessario:  
  
1.  Creare una pubblicazione di tipo merge mediante Creazione guidata nuova pubblicazione e specificare uno o più filtri di righe con parametri nella pagina **Aggiungi filtro** della procedura guidata. Per altre informazioni, vedere [Define and Modify a Parameterized Row Filter for a Merge Article](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
2.  Generare uno snapshot dello schema per la pubblicazione. Per impostazione predefinita, lo snapshot dello schema viene generato quando si completa la Creazione guidata nuova pubblicazione, ma è possibile generarne uno anche mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
#### Per generare uno snapshot dello schema  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Pubblicazioni** .  
  
3.  Pulsante destro del mouse la pubblicazione per cui si desidera creare uno snapshot, quindi fare clic su **Visualizza stato agente Snapshot**.  
  
4.  Nel **Visualizza stato agente Snapshot - \< pubblicazione>** la finestra di dialogo, fare clic su **avviare**.  
  
     Al termine della generazione dello snapshot, verrà visualizzato un messaggio del tipo "[100%] Generato uno snapshot di 17 articoli."  
  
#### Per consentire ai Sottoscrittori di avviare la generazione e il recapito di snapshot  
  
1.  Nel **partizioni di dati** pagina della **Proprietà pubblicazione - \< pubblicazione>** nella finestra di dialogo **definire una partizione e generare uno snapshot, se necessario, quando un nuovo sottoscrittore cerca di sincronizzare automaticamente**.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
#### Per generare e aggiornare gli snapshot  
  
1.  Nel **partizioni di dati** pagina della **Proprietà pubblicazione - \< pubblicazione>** nella finestra di dialogo fare clic su **Aggiungi**.  
  
2.  Immettere un valore per il **HOST_NAME ()** e/o **SUSER_SNAME ()** valore associato alla partizione per cui si desidera creare uno snapshot.  
  
3.  Facoltativamente, specificare una pianificazione per l'aggiornamento degli snapshot:  
  
    1.  Selezionare **esecuzione pianificata dell'agente Snapshot per questa partizione per l'esecuzione seguente**  
  
    2.  Accettare la pianificazione predefinita per l'aggiornamento degli snapshot oppure fare clic su **Cambia** per specificare una pianificazione diversa.  
  
4.  Fare clic su **OK**, è possibile che restituisce la **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo.  
  
5.  Selezionare la partizione nella griglia delle proprietà e quindi fare clic su **Genera gli snapshot selezionati adesso**.  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 L'utilizzo di stored procedure e dell'agente snapshot consente di eseguire le attività indicate di seguito:  
  
-   Consentire ai Sottoscrittori di richiedere la generazione e l'applicazione dello snapshot alla prima sincronizzazione.  
  
-   Pregenerare uno snapshot per ogni partizione.  
  
-   Generare manualmente uno snapshot per ciascun Sottoscrittore.  
  
    > [!IMPORTANT]  
    >  Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali in un file script, è fondamentale proteggere il file per evitare accessi non autorizzati.  
  
#### Per creare una pubblicazione che consente ai Sottoscrittori di avviare la generazione e il recapito di snapshot  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addmergepublication & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Specificare i parametri seguenti:  
  
    -   Il nome della pubblicazione per **@publication**.  
  
    -   Il valore **true** per **@allow_subscriber_initiated_snapshot**, che consente ai sottoscrittori di avviare il processo di snapshot.  
  
    -   (Facoltativo) Il numero di processi snapshot dinamici che possono essere eseguiti contemporaneamente per **@max_concurrent_dynamic_snapshots**. Se è in esecuzione il numero massimo di processi e un Sottoscrittore tenta di generare uno snapshot, il processo verrà inserito in una coda. Per impostazione predefinita, non esiste nessun limite per il numero di processi simultanei.  
  
2.  Server di pubblicazione, eseguire [sp_addpublication_snapshot & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Specificare il nome della pubblicazione utilizzato al passaggio 1 per **@publication** e [!INCLUDE[msCoName](../../includes/msconame-md.md)] le credenziali di Windows in cui il [agente Snapshot repliche](../../relational-databases/replication/agents/replication-snapshot-agent.md) viene eseguito per **@job_login** e **@password**. Se l'agente utilizzerà [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione quando ci si connette al server di pubblicazione, è necessario specificare anche un valore di **0** per **@publisher_security_mode** e [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] informazioni di accesso per **@publisher_login** e **@publisher_password**. Verrà creato un processo dell'agente snapshot per la pubblicazione. Per ulteriori informazioni sulla generazione di uno snapshot iniziale e sulla definizione di una pianificazione personalizzata per l'agente snapshot, vedere [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
    > [!IMPORTANT]  
    >  Quando si configura un server di pubblicazione con un server di distribuzione remoto, i valori specificati per tutti i parametri, inclusi *job_login* e *job_password*, vengono inviati al server di distribuzione come testo normale. È consigliabile crittografare la connessione tra il server di pubblicazione e il server di distribuzione remoto prima di eseguire questa stored procedure. Per ulteriori informazioni, vedere [abilitare connessioni crittografate al motore di Database & #40; SQL Server Configuration Manager & #41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
3.  Eseguire [sp_addmergearticle & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) Per aggiungere articoli alla pubblicazione. Questa stored procedure deve essere eseguita una sola volta per ogni articolo della pubblicazione. Quando si utilizzano filtri con parametri, è necessario specificare un filtro di riga con parametri per uno o più articoli tramite il **@subset_filterclause** parametro. Per altre informazioni, vedere [Define and Modify a Parameterized Row Filter for a Merge Article](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
4.  Se altri articoli verranno filtrati in base al filtro di riga con parametri, eseguire [sp_addmergefilter & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md) Per definire le relazioni tra record logici tra gli articoli di join. Questa stored procedure deve essere eseguita una sola volta per ogni relazione da definire. Per altre informazioni, vedere [Define and Modify a Join Filter Between Merge Articles](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
5.  Quando l'agente di merge richiede che il Sottoscrittore venga inizializzato dallo snapshot, lo snapshot relativo alla partizione della sottoscrizione che ha eseguito la richiesta viene generato automaticamente.  
  
#### Per creare una pubblicazione e pregenerare o aggiornare automaticamente gli snapshot  
  
1.  Eseguire [sp_addmergepublication & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md) Per creare la pubblicazione. Per altre informazioni, vedere [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
2.  Server di pubblicazione, eseguire [sp_addpublication_snapshot & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Specificare il nome della pubblicazione utilizzato al passaggio 1 per **@publication** e le credenziali di Windows con cui viene eseguito l'agente Snapshot per **@job_login** e **@password**. Se l'agente utilizzerà [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione quando ci si connette al server di pubblicazione, è necessario specificare anche un valore di **0** per **@publisher_security_mode** e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] informazioni di accesso per **@publisher_login** e **@publisher_password**. Verrà creato un processo dell'agente snapshot per la pubblicazione. Per ulteriori informazioni sulla generazione di uno snapshot iniziale e sulla definizione di una pianificazione personalizzata per l'agente snapshot, vedere [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
    > [!IMPORTANT]  
    >  Quando si configura un server di pubblicazione con un server di distribuzione remoto, i valori specificati per tutti i parametri, inclusi *job_login* e *job_password*, vengono inviati al server di distribuzione come testo normale. È consigliabile crittografare la connessione tra il server di pubblicazione e il server di distribuzione remoto prima di eseguire questa stored procedure. Per ulteriori informazioni, vedere [abilitare connessioni crittografate al motore di Database & #40; SQL Server Configuration Manager & #41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
3.  Eseguire [sp_addmergearticle & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) Per aggiungere articoli alla pubblicazione. Questa stored procedure deve essere eseguita una sola volta per ogni articolo della pubblicazione. Quando si utilizzano filtri con parametri, è necessario specificare un filtro di riga con parametri per un articolo utilizzando il **@subset_filterclause** parametro. Per altre informazioni, vedere [Define and Modify a Parameterized Row Filter for a Merge Article](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
4.  Se altri articoli verranno filtrati in base al filtro di riga con parametri, eseguire [sp_addmergefilter & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md) Per definire le relazioni tra record logici tra gli articoli di join. Questa stored procedure deve essere eseguita una sola volta per ogni relazione da definire. Per altre informazioni, vedere [Define and Modify a Join Filter Between Merge Articles](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
5.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_helpmergepublication & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md), che specifica il valore di **@publication** dal passaggio 1. Si noti il valore di **snapshot_jobid** nel set di risultati.  
  
6.  Convertire il valore di **snapshot_jobid** ottenuto nel passaggio 5 per **uniqueidentifier**.  
  
7.  Nel server di pubblicazione di **msdb** del database, eseguire [sp_start_job & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md), specificando il valore convertito ottenuto nel passaggio 6 per **@job_id**.  
  
8.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addmergepartition & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql.md). Specificare il nome della pubblicazione ottenuto al passaggio 1 per **@publication** e il valore utilizzato per definire la partizione per **@suser_sname** Se [SUSER_SNAME & #40; Transact-SQL & #41;](../../t-sql/functions/suser-sname-transact-sql.md) viene utilizzato nella clausola di filtro o per **@host_name** Se [HOST_NAME & #40; Transact-SQL & #41;](../../t-sql/functions/host-name-transact-sql.md) viene utilizzata nella clausola di filtro.  
  
9. Server di pubblicazione nel database di pubblicazione, eseguire [sp_adddynamicsnapshot_job & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-adddynamicsnapshot-job-transact-sql.md). Specificare il nome della pubblicazione ottenuto al passaggio 1 per **@publication**, il valore di **@suser_sname** o **@host_name** ottenuto al passaggio 8 e una pianificazione per il processo. In tal modo verrà creato il processo che genera lo snapshot con parametri per la partizione specificata. Per altre informazioni, vedere [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md).  
  
    > [!NOTE]  
    >  Per l'esecuzione di questo processo viene utilizzato lo stesso account di Windows del processo snapshot iniziale definito al passaggio 2. Per rimuovere il processo di snapshot con parametri e la partizione dati correlata, eseguire [sp_dropdynamicsnapshot_job & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-dropdynamicsnapshot-job-transact-sql.md).  
  
10. Server di pubblicazione nel database di pubblicazione, eseguire [sp_helpmergepartition & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-helpmergepartition-transact-sql.md), che specifica il valore di **@publication** dal passaggio 1 e il valore di **@suser_sname** o **@host_name** ottenuto al passaggio 8. Si noti il valore di **dynamic_snapshot_jobid** nel set di risultati.  
  
11. Nel server di distribuzione di **msdb** del database, eseguire [sp_start_job & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md), che specifica il valore ottenuto nel passaggio 9 per **@job_id**. In tal modo verrà avviato il processo snapshot con parametri per la partizione.  
  
12. Ripetere i passaggi da 8 a 11 per generare uno snapshot partizionato per ogni sottoscrizione.  
  
#### Per creare una pubblicazione e creare manualmente gli snapshot per ogni partizione  
  
1.  Eseguire [sp_addmergepublication & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md) Per creare la pubblicazione. Per altre informazioni, vedere [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
2.  Server di pubblicazione, eseguire [sp_addpublication_snapshot & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Specificare il nome della pubblicazione utilizzato al passaggio 1 per **@publication** e le credenziali di Windows con cui viene eseguito l'agente Snapshot per **@job_login** e **@password**. Se l'agente utilizzerà [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione quando ci si connette al server di pubblicazione, è necessario specificare anche un valore di **0** per **@publisher_security_mode** e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] informazioni di accesso per **@publisher_login** e **@publisher_password**. Verrà creato un processo dell'agente snapshot per la pubblicazione. Per ulteriori informazioni sulla generazione di uno snapshot iniziale e sulla definizione di una pianificazione personalizzata per l'agente snapshot, vedere [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
    > [!IMPORTANT]  
    >  Quando si configura un server di pubblicazione con un server di distribuzione remoto, i valori specificati per tutti i parametri, inclusi *job_login* e *job_password*, vengono inviati al server di distribuzione come testo normale. È consigliabile crittografare la connessione tra il server di pubblicazione e il server di distribuzione remoto prima di eseguire questa stored procedure. Per ulteriori informazioni, vedere [abilitare connessioni crittografate al motore di Database & #40; SQL Server Configuration Manager & #41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
3.  Eseguire [sp_addmergearticle & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) Per aggiungere articoli alla pubblicazione. Questa stored procedure deve essere eseguita una sola volta per ogni articolo della pubblicazione. Quando si utilizzano filtri con parametri, è necessario specificare un filtro di riga con parametri per almeno un articolo utilizzando il **@subset_filterclause** parametro. Per altre informazioni, vedere [Define and Modify a Parameterized Row Filter for a Merge Article](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
4.  Se altri articoli verranno filtrati in base al filtro di riga con parametri, eseguire [sp_addmergefilter & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md) Per definire le relazioni tra record logici tra gli articoli di join. Questa stored procedure deve essere eseguita una sola volta per ogni relazione da definire. Per altre informazioni, vedere [Define and Modify a Join Filter Between Merge Articles](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
5.  Avviare il processo snapshot o eseguire Agente snapshot repliche dal prompt dei comandi per generare lo schema standard dello snapshot standard e gli altri file. Per altre informazioni, vedere [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
6.  Eseguire nuovamente l'agente Snapshot repliche dal prompt dei comandi per generare file di copia (bcp) in blocco, che specifica la posizione dello snapshot partizionato per **- DynamicSnapshotLocation** e una o entrambe le seguenti proprietà che definisce la partizione:  
  
    -   **-DynamicFilterHostName** -il valore se [HOST_NAME & #40; Transact-SQL & #41;](../../t-sql/functions/host-name-transact-sql.md) viene utilizzato.  
  
    -   **-DynamicFilterLogin** -il valore se [SUSER_SNAME & #40; Transact-SQL & #41;](../../t-sql/functions/suser-sname-transact-sql.md) viene utilizzato.  
  
7.  Ripetere il passaggio 6 per generare uno snapshot partizionato per ogni sottoscrizione.  
  
8.  Eseguire l'agente di merge per consentire a ogni sottoscrizione di applicare lo snapshot partizionato iniziale ai Sottoscrittori, specificando le proprietà seguenti:  
  
    -   **Nome host -** -il valore utilizzato per definire la partizione se il valore effettivo di HOST_NAME da sottoporre a override.  
  
    -   **-DynamicSnapshotLocation** -il percorso dello snapshot dinamico per questa partizione.  
  
> [!NOTE]  
>  Per ulteriori informazioni sulla programmazione degli agenti di replica, vedere [concetti eseguibili agente di replica](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
###  <a name="TsqlExample"></a> Esempi (Transact-SQL)  
 In questo esempio viene creata una pubblicazione di tipo merge con filtri con parametri in cui i Sottoscrittori avviano il processo di generazione dello snapshot. I valori per **@job_login** e **@job_password** vengono passati utilizzando variabili di scripting.  
  
 [!code-sql[HowTo#sp_MergeDynamicPub1](../../relational-databases/replication/codesnippet/tsql/create-a-snapshot-for-a-_1.sql)]  
  
 Questo esempio viene creata una pubblicazione che utilizza un filtro con parametri in cui ogni sottoscrittore ha una partizione definita eseguendo [sp_addmergepartition](../../relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql.md) e il processo di snapshot dei dati filtrati creato eseguendo [sp_adddynamicsnapshot_job](../../relational-databases/system-stored-procedures/sp-adddynamicsnapshot-job-transact-sql.md) passando le informazioni sul partizionamento. I valori per **@job_login** e **@job_password** vengono passati utilizzando variabili di scripting.  
  
 [!code-sql[HowTo#sp_MergeDynamicPubPlusPartition](../../relational-databases/replication/codesnippet/tsql/create-a-snapshot-for-a-_2.sql)]  
  
 In questo esempio viene creata una pubblicazione utilizzando un filtro con parametri in cui il Sottoscrittore deve disporre di una propria partizione dati e il processo snapshot con filtro viene creato fornendo le informazioni sul partizionamento. Un Sottoscrittore fornisce le informazioni sul partizionamento utilizzando i parametri della riga di comando durante l'esecuzione manuale degli agenti di replica. In questo esempio si presuppone che sia stata creata anche una sottoscrizione della pubblicazione.  
  
 [!code-sql[HowTo#sp_MergeDynamicPubPartitionManual](../../relational-databases/replication/codesnippet/tsql/create-a-snapshot-for-a-_3.sql)]  
  
```  
  
REM Line breaks are added to improve readability.   
REM In a batch file, commands must be made in a single line.  
REM Run the Snapshot agent from the command line to generate the standard snapshot   
REM schema and other files.   
SET DistPub=%computername%  
SET PubDB=AdventureWorks2012   
SET PubName=AdvWorksSalesPersonMerge  
  
"C:\Program Files\Microsoft SQL Server\120\COM\SNAPSHOT.EXE" -Publication %PubName%    
-Publisher %DistPub% -Distributor  %DistPub%  -PublisherDB %PubDB%  -ReplicationType 2    
-OutputVerboseLevel 1  -DistributorSecurityMode 1  
  
PAUSE  
  
```  
  
```  
  
REM Run the Snapshot agent from the command line, this time to generate   
REM the bulk copy (.bcp) data for each Subscriber partition.    
SET DistPub=%computername%  
SET PubDB=AdventureWorks2012   
SET PubName=AdvWorksSalesPersonMerge  
SET SnapshotDir=\\%DistPub%\repldata\unc\fernando  
  
MD %SnapshotDir%  
  
"C:\Program Files\Microsoft SQL Server\120\COM\SNAPSHOT.EXE" -Publication %PubName%    
-Publisher %DistPub%  -Distributor  %DistPub%  -PublisherDB %PubDB%  -ReplicationType 2    
-OutputVerboseLevel 1  -DistributorSecurityMode 1  -DynamicFilterHostName "adventure-works\Fernando"    
-DynamicSnapshotLocation %SnapshotDir%  
  
PAUSE  
  
```  
  
```  
  
REM Run the Merge Agent for each subscription to apply the partitioned   
REM snapshot for each Subscriber.    
SET Publisher = %computername%  
SET Subscriber = %computername%  
SET PubDB = AdventureWorks2012   
SET SubDB = AdventureWorks2012Replica   
SET PubName = AdvWorksSalesPersonMerge   
SET SnapshotDir=\\%DistPub%\repldata\unc\fernando  
  
"C:\Program Files\Microsoft SQL Server\120\COM\REPLMERG.EXE" -Publisher  %Publisher%    
-Subscriber  %Subscriber%  -Distributor %Publisher%  -PublisherDB %PubDB%    
-SubscriberDB %SubDB% -Publication %PubName%  -PublisherSecurityMode 1  -OutputVerboseLevel 3    
-Output -SubscriberSecurityMode 1  -SubscriptionType 3 -DistributorSecurityMode 1    
-Hostname "adventure-works\Fernando"  -DynamicSnapshotLocation %SnapshotDir%  
  
PAUSE  
  
```  
  
##  <a name="RMOProcedure"></a> Utilizzo di RMO (Replication Management Objects)  
 È possibile utilizzare oggetti RMO (Replication Management Objects) per generare snapshot partizionati a livello di programmazione nelle modalità seguenti:  
  
-   Consentire ai Sottoscrittori di richiedere la generazione e l'applicazione dello snapshot alla prima sincronizzazione.  
  
-   Pregenerare uno snapshot per ogni partizione.  
  
-   Generare manualmente uno snapshot per ogni Sottoscrittore eseguendo l'agente snapshot.  
  
> [!NOTE]  
>  Quando il filtro per un articolo restituisce partizioni non sovrapposte, univoche per ogni sottoscrizione (specificando un valore di F:Microsoft.SqlServer.Replication.PartitionOptions.NonOverlappingSingleSubscription per P:Microsoft.SqlServer.Replication.MergeArticle.PartitionOption durante la creazione di un articolo di merge), i metadati vengono puliti ogni volta che viene eseguito l'agente di Merge. Lo snapshot partizionato scade quindi più rapidamente. Quando si utilizza questa opzione, è consigliabile consentire ai Sottoscrittori di richiedere la generazione degli snapshot. Per ulteriori informazioni, vedere la sezione relativa all'utilizzo delle opzioni di filtro appropriate nell'argomento [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
> [!IMPORTANT]  
>  Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali, utilizzare i [servizi di crittografia](http://go.microsoft.com/fwlink/?LinkId=34733) offerti da [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows .NET Framework.  
  
#### Per creare una pubblicazione che consente ai Sottoscrittori di avviare la generazione e il recapito di snapshot  
  
1.  Creare una connessione al server di pubblicazione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza del <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> classe per il database di pubblicazione, impostare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà all'istanza di <xref:Microsoft.SqlServer.Management.Common.ServerConnection> dal passaggio 1 e chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo. Se <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> restituisce **false**, verificare che il database esista.  
  
3.  Se <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledMergePublishing%2A> è **false**, impostarlo su **true** e chiamare <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A>.  
  
4.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.MergePublication> classe e impostare le seguenti proprietà per questo oggetto:  
  
    -   Il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> dal passaggio 1 per <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
    -   Il nome del database pubblicato per <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>.  
  
    -   Un nome per la pubblicazione per <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>.  
  
    -   Il numero massimo di esecuzione dei processi snapshot dinamici <xref:Microsoft.SqlServer.Replication.MergePublication.MaxConcurrentDynamicSnapshots%2A>. Poiché le richieste di snapshot avviate dal Sottoscrittore possono verificarsi in qualsiasi momento, questa proprietà limita il numero di processi dell'agente snapshot che possono essere eseguiti simultaneamente quando più Sottoscrittori richiedono il rispettivo snapshot partizionato contemporaneamente. Quando è in esecuzione il numero massimo di processi, le richieste aggiuntive di snapshot partizionati vengono inserite nella coda fino al completamento di uno dei processi.  
  
    -   Utilizzare l'operatore logico OR bit per bit (**|** in Visual c# e **o** in Visual Basic) per aggiungere il valore <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowSubscriberInitiatedSnapshot> a <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A>.  
  
    -   Il <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> e <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> i campi di <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> per fornire le credenziali per il [!INCLUDE[msCoName](../../includes/msconame-md.md)] account di Windows in cui viene eseguito il processo dell'agente Snapshot.  
  
        > [!NOTE]  
        >  L'impostazione <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> è consigliata per la creazione della pubblicazione da un membro del **sysadmin** ruolo predefinito del server. Per altre informazioni, vedere [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
5.  Chiamare il <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> metodo per creare la pubblicazione.  
  
    > [!IMPORTANT]  
    >  Quando si configura un server di pubblicazione con un server di distribuzione remoto, i valori specificati per tutte le proprietà, inclusi <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A>, vengono inviati al server di distribuzione come testo normale. È consigliabile crittografare la connessione tra il server di pubblicazione e il relativo server di distribuzione remoto prima di chiamare il <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> metodo. Per ulteriori informazioni, vedere [abilitare connessioni crittografate al motore di Database & #40; SQL Server Configuration Manager & #41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
6.  Utilizzare il <xref:Microsoft.SqlServer.Replication.MergeArticle> proprietà per aggiungere articoli alla pubblicazione. Specificare il <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> proprietà per almeno un articolo che definisce il filtro con parametri. (Facoltativo) Creare <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> gli oggetti che definiscono i filtri join tra articoli. Per altre informazioni, vedere [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
7.  Se il valore di <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> è **false**, chiamare <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> per creare il processo dell'agente Snapshot iniziale per questa pubblicazione.  
  
8.  Chiamare il <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> metodo il <xref:Microsoft.SqlServer.Replication.MergePublication> oggetto creato nel passaggio 4. In questo modo viene avviato il processo dell'agente che genera lo snapshot iniziale. Per ulteriori informazioni sulla generazione di uno snapshot iniziale e sulla definizione di una pianificazione personalizzata per l'agente snapshot, vedere [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
9. (Facoltativo) Verificare la presenza di un valore di **true** per il <xref:Microsoft.SqlServer.Replication.MergePublication.SnapshotAvailable%2A> proprietà per determinare quando lo snapshot iniziale è pronto per l'uso.  
  
10. La prima volta che l'agente di merge per un Sottoscrittore si connette, verrà generato automaticamente uno snapshot partizionato.  
  
#### Per creare una pubblicazione e pregenerare o aggiornare automaticamente gli snapshot  
  
1.  Utilizzare un'istanza di <xref:Microsoft.SqlServer.Replication.MergePublication> classe per definire una pubblicazione di tipo merge. Per altre informazioni, vedere [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
2.  Utilizzare il <xref:Microsoft.SqlServer.Replication.MergeArticle> proprietà per aggiungere articoli alla pubblicazione. Specificare il <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> proprietà per almeno un articolo che definisce il filtro con parametri, quindi crea eventuali <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> gli oggetti che definiscono i filtri join tra articoli. Per altre informazioni, vedere [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
3.  Se il valore di <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> è **false**, chiamare <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> per creare il processo dell'agente snapshot per questa pubblicazione.  
  
4.  Chiamare il <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> metodo il <xref:Microsoft.SqlServer.Replication.MergePublication> oggetto creato nel passaggio 1. Questo metodo avvia il processo dell'agente che genera lo snapshot iniziale. Per ulteriori informazioni sulla generazione di uno snapshot iniziale e sulla definizione di una pianificazione personalizzata per l'agente snapshot, vedere [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
5.  Verificare la presenza di un valore di **true** per il <xref:Microsoft.SqlServer.Replication.MergePublication.SnapshotAvailable%2A> proprietà per determinare quando lo snapshot iniziale è pronto per l'uso.  
  
6.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.MergePartition> e impostare i criteri di filtro con parametri per il sottoscrittore utilizzando una o entrambe le proprietà seguenti:  
  
    -   Se la partizione del sottoscrittore è definita dal risultato di [SUSER_SNAME & #40; Transact-SQL & #41;](../../t-sql/functions/suser-sname-transact-sql.md), utilizzare <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterLogin%2A>.  
  
    -   Se la partizione del sottoscrittore è definita dal risultato di [HOST_NAME & #40; Transact-SQL & #41;](../../t-sql/functions/host-name-transact-sql.md) un overload di questa funzione, utilizzare o <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterHostName%2A>.  
  
7.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.MergeDynamicSnapshotJob> classe e impostare la stessa proprietà indicata nel passaggio 6.  
  
8.  Utilizzare il <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule> classe per definire una pianificazione per la generazione dello snapshot filtrato per la partizione del sottoscrittore.  
  
9. Utilizzando l'istanza di <xref:Microsoft.SqlServer.Replication.MergePublication> dal passaggio 1, chiamare <xref:Microsoft.SqlServer.Replication.MergePublication.AddMergePartition%2A>. Passare il <xref:Microsoft.SqlServer.Replication.MergePartition> oggetto dal passaggio 6.  
  
10. Utilizzando l'istanza di <xref:Microsoft.SqlServer.Replication.MergePublication> dal passaggio 1, chiamare il <xref:Microsoft.SqlServer.Replication.MergePublication.AddMergeDynamicSnapshotJob%2A> metodo. Passare il <xref:Microsoft.SqlServer.Replication.MergeDynamicSnapshotJob> oggetto ottenuto nel passaggio 7 e <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule> oggetto indicato nel passaggio 8.  
  
11. Chiamare <xref:Microsoft.SqlServer.Replication.MergePublication.EnumMergeDynamicSnapshotJobs%2A>, e individuare il <xref:Microsoft.SqlServer.Replication.MergeDynamicSnapshotJob> oggetto per il processo di snapshot partizionato appena aggiunto nella matrice restituita.  
  
12. Ottenere il <xref:Microsoft.SqlServer.Replication.MergeDynamicSnapshotJob.Name%2A> proprietà per il processo.  
  
13. Creare una connessione al server di distribuzione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
14. Creare un'istanza di SQL Server Management Objects (SMO) <xref:Microsoft.SqlServer.Management.Smo.Server> classe, passando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> oggetto passaggio 13.  
  
15. Creare un'istanza del <xref:Microsoft.SqlServer.Management.Smo.Agent.Job> classe, passando il <xref:Microsoft.SqlServer.Management.Smo.Server.JobServer%2A> proprietà del <xref:Microsoft.SqlServer.Management.Smo.Server> oggetto dal passaggio 14 e il nome del processo del passaggio 12.  
  
16. Chiamare il <xref:Microsoft.SqlServer.Management.Smo.Agent.Job.Start%2A> metodo per avviare il processo di snapshot partizionato.  
  
17. Ripetere i passaggi da 6 a 16 per ogni Sottoscrittore.  
  
#### Per creare una pubblicazione e creare manualmente gli snapshot per ogni partizione  
  
1.  Utilizzare un'istanza di <xref:Microsoft.SqlServer.Replication.MergePublication> classe per definire una pubblicazione di tipo merge. Per altre informazioni, vedere [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
2.  Utilizzare il <xref:Microsoft.SqlServer.Replication.MergeArticle> proprietà per aggiungere articoli alla pubblicazione. specificare il <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> proprietà per almeno un articolo che definisce il filtro con parametri, quindi crea eventuali <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> gli oggetti che definiscono i filtri join tra articoli. Per altre informazioni, vedere [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
3.  Generare lo snapshot iniziale. Per altre informazioni, vedere [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
4.  Creare un'istanza della classe <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> e impostare le seguenti proprietà obbligatorie:  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publisher%2A> : nome del server di pubblicazione  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherDatabase%2A> : nome del database di pubblicazione  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publication%2A> : nome della pubblicazione  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Distributor%2A> : nome del server di distribuzione  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherSecurityMode%2A> -il valore <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> utilizzata l'autenticazione integrata di Windows o un valore di <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> utilizzare autenticazione di SQL Server.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorSecurityMode%2A> -il valore <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> utilizzata l'autenticazione integrata di Windows o un valore di <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> per utilizzare l'autenticazione di SQL Server.  
  
5.  Impostare un valore di <xref:Microsoft.SqlServer.Replication.ReplicationType.Merge> per <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.ReplicationType%2A>.  
  
6.  Impostare una o più delle seguenti proprietà per definire i parametri di partizionamento:  
  
    -   Se la partizione del sottoscrittore è definita dal risultato di [SUSER_SNAME & #40; Transact-SQL & #41;](../../t-sql/functions/suser-sname-transact-sql.md), utilizzare <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DynamicFilterLogin%2A>.  
  
    -   Se la partizione del sottoscrittore è definita dal risultato di [HOST_NAME & #40; Transact-SQL & #41;](../../t-sql/functions/host-name-transact-sql.md) un overload di questa funzione, utilizzare o <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DynamicFilterHostName%2A>.  
  
7.  Chiamare il metodo <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.GenerateSnapshot%2A> .  
  
8.  Ripetere i passaggi da 4 a 7 per ogni Sottoscrittore.  
  
###  <a name="PShellExample"></a> Esempi (RMO)  
 In questo esempio viene creata una pubblicazione di tipo merge che consente ai Sottoscrittori di richiedere la generazione di snapshot.  
  
 [!code-csharp[HowTo#rmo_CreateMergePub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createmergepub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createmergepub)]  
  
 In questo esempio vengono creati manualmente la partizione del Sottoscrittore e lo snapshot filtrato per una pubblicazione di tipo merge con filtri di riga con parametri.  
  
 [!code-csharp[HowTo#rmo_CreateMergePartition](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createmergepartition)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePartition](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createmergepartition)]  
  
 In questo esempio viene avviato manualmente l'agente snapshot per generare lo snapshot di dati filtrati per un Sottoscrittore in una pubblicazione di tipo merge con filtri di riga con parametri.  
  
 [!code-csharp[HowTo#rmo_GenerateFilteredSnapshot](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_generatefilteredsnapshot)]  
  
 [!code-vb[HowTo#rmo_vb_GenerateFilteredSnapshot](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_generatefilteredsnapshot)]  
  
## Vedere anche  
 [Filtri di riga con parametri](../../relational-databases/replication/merge/parameterized-row-filters.md)   
 [Concetti di base relativi alle stored procedure del sistema di replica](../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Snapshot per pubblicazioni di tipo merge con filtri con parametri](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)   
 [Procedure consigliate per la sicurezza della replica](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  