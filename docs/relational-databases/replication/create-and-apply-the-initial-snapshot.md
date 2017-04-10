---
title: "Creazione e applicazione dello snapshot iniziale | Microsoft Docs"
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
  - "snapshot [replica di SQL Server], creazione"
  - "replica snapshot [SQL Server], snapshot iniziali"
ms.assetid: 742727a1-5189-44ec-b3ae-6fd7aa1f5347
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# Creazione e applicazione dello snapshot iniziale
  In questo argomento viene descritto come creare e applicare lo snapshot iniziale in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] o RMO (Replication Management Objects). Per le pubblicazioni di tipo merge che utilizzano filtri con parametri è necessario uno snapshot a due parti. Per altre informazioni, vedere [Create a Snapshot for a Merge Publication with Parameterized Filters](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
 **Contenuto dell'argomento**  
  
-   **Per creare e applicare lo snapshot iniziale, utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Oggetti RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Per impostazione predefinita, se [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent è in esecuzione, l'agente snapshot genera uno snapshot subito dopo la creazione di una pubblicazione mediante la Creazione guidata nuova pubblicazione. Sempre per impostazione predefinita, tale snapshot viene quindi applicato dall'agente di distribuzione (per la replica snapshot e transazionale) o dall'agente di merge (per le sottoscrizioni di tipo merge) per tutte le sottoscrizioni. È anche possibile generare uno snapshot utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] e Monitoraggio replica. Per informazioni sull'avvio di monitoraggio replica, vedere [avviare Monitoraggio replica](../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
#### Per creare uno snapshot in Management Studio  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Pubblicazioni locali** .  
  
3.  Pulsante destro del mouse la pubblicazione per cui si desidera creare uno snapshot, quindi fare clic su **Visualizza stato agente Snapshot**.  
  
4.  Nel **Visualizza stato agente Snapshot - \< pubblicazione>** la finestra di dialogo, fare clic su **avviare**.  
  
 Al termine della generazione dello snapshot, verrà visualizzato un messaggio del tipo "[100%] Generato uno snapshot di 17 articoli."  
  
#### Per creare uno snapshot in Monitoraggio replica  
  
1.  In Monitoraggio replica espandere un gruppo di server di pubblicazione nel riquadro di sinistra e quindi espandere un server di pubblicazione.  
  
2.  Pulsante destro del mouse la pubblicazione per cui si desidera generare uno snapshot, quindi fare clic su **generare Snapshot**.  
  
3.  Per visualizzare lo stato dell'agente snapshot, fare clic sulla scheda **Agenti** . Per ulteriori informazioni, fare doppio clic su agente Snapshot nella griglia e quindi fare clic su **Visualizza dettagli**.  
  
#### Per applicare uno snapshot  
  
1.  Al termine della generazione, lo snapshot verrà applicato mediante la sincronizzazione della sottoscrizione con l'agente di distribuzione o l'agente di merge:  
  
    -   Se l'agente è impostato per l'esecuzione continua, ovvero l'impostazione predefinita per la replica transazionale, lo snapshot verrà applicato automaticamente al termine della generazione.  
  
    -   Se è invece impostato per l'esecuzione in base a una pianificazione, lo snapshot verrà applicato alla successiva esecuzione pianificata dell'agente.  
  
    -   Se l'agente è impostato per l'esecuzione su richiesta, lo snapshot verrà applicato alla successiva esecuzione dell'agente.  
  
     Per ulteriori informazioni sulla sincronizzazione delle sottoscrizioni, vedere [sincronizzare una sottoscrizione Push](../../relational-databases/replication/synchronize-a-push-subscription.md) e [sincronizzare una sottoscrizione Pull](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 Gli snapshot iniziali possono essere creati a livello di programmazione creando ed eseguendo un processo dell'agente snapshot o eseguendo il file eseguibile dell'agente snapshot da un file batch. Dopo la generazione, lo snapshot iniziale viene trasferito e applicato al Sottoscrittore la prima volta che la sottoscrizione viene sincronizzata. Se si esegue l'agente snapshot da un prompt dei comandi o un file batch, sarà necessario rieseguirlo ogni volta che lo snapshot esistente diventa non valido.  
  
> [!IMPORTANT]  
>  Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali in un file script, è fondamentale proteggere il file per evitare accessi non autorizzati.  
  
#### Per creare ed eseguire un processo dell'agente snapshot per generare lo snapshot iniziale  
  
1.  Creare una pubblicazione snapshot, transazionale o di tipo merge. Per altre informazioni, vedere [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
2.  Eseguire [sp_addpublication_snapshot & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Specificare **@publication** e i parametri seguenti:  
  
    -   **Il @job_login, che specifica** le credenziali di autenticazione di Windows con cui viene eseguito l'agente Snapshot nel server di distribuzione.  
  
    -   **Il @job_password**, ovvero la password per le credenziali di Windows.  
  
    -   (Facoltativo) Il valore **0** per **@publisher_security_mode** Se l'agente utilizzerà l'autenticazione di SQL Server quando ci si connette al server di pubblicazione. In questo caso, è necessario specificare anche le informazioni di accesso di autenticazione di SQL Server per **@publisher_login** e **@publisher_password**.  
  
    -   (Facoltativo) Pianificazione della sincronizzazione per il processo dell'agente snapshot. Per altre informazioni, vedere [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md).  
  
    > [!IMPORTANT]  
    >  Quando si configura un server di pubblicazione con un server di distribuzione remoto, i valori specificati per tutti i parametri, inclusi *job_login* e *job_password*, vengono inviati al server di distribuzione come testo normale. È consigliabile crittografare la connessione tra il server di pubblicazione e il server di distribuzione remoto prima di eseguire questa stored procedure. Per ulteriori informazioni, vedere [abilitare connessioni crittografate al motore di Database & #40; SQL Server Configuration Manager & #41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
3.  Aggiungere articoli alla pubblicazione. Per altre informazioni, vedere [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
4.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_startpublication_snapshot & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-startpublication-snapshot-transact-sql.md), che specifica il valore di **@publication** dal passaggio 1.  
  
#### Per eseguire l'agente snapshot per generare lo snapshot iniziale  
  
1.  Creare una pubblicazione snapshot, transazionale o di tipo merge. Per altre informazioni, vedere [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
2.  Aggiungere articoli alla pubblicazione. Per altre informazioni, vedere [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
3.  Dal prompt dei comandi o in un file batch, avviare il [agente Snapshot repliche](../../relational-databases/replication/agents/replication-snapshot-agent.md) eseguendo **snapshot.exe**, gli argomenti della riga di comando seguenti:  
  
    -   **-Publication**  
  
    -   **-Publisher**  
  
    -   **-Distributor**  
  
    -   **-PublisherDB**  
  
    -   **-ReplicationType**  
  
     Se si usano l'autenticazione di SQL Server, è inoltre necessario specificare gli argomenti seguenti:  
  
    -   **-DistributorLogin**  
  
    -   **-DistributorPassword**  
  
    -   **-DistributorSecurityMode** = **0**  
  
    -   **-PublisherLogin**  
  
    -   **-PublisherPassword**  
  
    -   **-PublisherSecurityMode** = **0**  
  
###  <a name="TsqlExample"></a> Esempi (Transact-SQL)  
 In questo esempio viene illustrato come creare una pubblicazione transazionale e aggiungere un processo dell'agente Snapshot per la nuova pubblicazione (utilizzando **sqlcmd** le variabili di scripting). Viene inoltre avviato il processo.  
  
 [!code-sql[HowTo#sp_trangenerate_snapshot](../../relational-databases/replication/codesnippet/tsql/create-and-apply-the-ini_1.sql)]  
  
 In questo esempio viene creata una pubblicazione di tipo merge e aggiunge un processo dell'agente Snapshot (utilizzando **sqlcmd** variabili) per la pubblicazione. Viene inoltre avviato il processo.  
  
 [!code-sql[HowTo#sp_mergegenerate_snapshot](../../relational-databases/replication/codesnippet/tsql/create-and-apply-the-ini_2.sql)]  
  
 Con gli argomenti della riga di comando seguenti l'agente snapshot viene avviato per generare lo snapshot per una pubblicazione di tipo merge.  
  
> [!NOTE]  
>  Le interruzioni di riga sono state aggiunte per agevolare la lettura. I comandi in un file batch devono essere inseriti in un'unica riga.  
  
```  
  
REM -- Declare variables  
SET Publisher=%InstanceName%  
SET PublicationDB=AdventureWorks2012   
SET Publication=AdvWorksSalesOrdersMerge   
  
REM --Start the Snapshot Agent to generate the snapshot for AdvWorksSalesOrdersMerge.  
"C:\Program Files\Microsoft SQL Server\120\COM\SNAPSHOT.EXE" -Publication %Publication%   
-Publisher %Publisher% -Distributor %Publisher% -PublisherDB %PublicationDB%   
-ReplicationType 2 -OutputVerboseLevel 1 -DistributorSecurityMode 1  
  
```  
  
##  <a name="RMOProcedure"></a> Utilizzo di RMO (Replication Management Objects)  
 L'agente snapshot genera gli snapshot al termine della creazione di una pubblicazione. È possibile generare questi snapshot a livello di programmazione tramite gli oggetti RMO (Replication Management Objects) e l'accesso diretto tramite codice gestito alle funzionalità dell'agente di replica. Gli oggetti utilizzati dipendono dal tipo di replica. L'agente snapshot può essere avviato in modo sincrono tramite l'oggetto <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> o in modo asincrono tramite il processo dell'agente. Dopo la generazione, lo snapshot iniziale viene trasferito e applicato al Sottoscrittore la prima volta che la sottoscrizione viene sincronizzata. È necessario rieseguire l'agente ogni volta che lo snapshot esistente non contiene più dati validi e aggiornati. Per ulteriori informazioni, vedere [mantenere pubblicazioni](../../relational-databases/replication/publish/maintain-publications.md).  
  
> [!IMPORTANT]  
>  Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali, utilizzare i [servizi di crittografia](http://go.microsoft.com/fwlink/?LinkId=34733) offerti da [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows .NET Framework.  
  
#### Per generare lo snapshot iniziale per una pubblicazione snapshot o transazionale avviando il processo dell'agente snapshot (modo asincrono)  
  
1.  Creare una connessione al server di pubblicazione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.TransPublication> (classe). Impostare il <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> e <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> proprietà per la pubblicazione, quindi impostare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà per la connessione creata nel passaggio 1.  
  
3.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> per caricare le proprietà rimanenti dell'oggetto. Se questo metodo restituisce **false**, le proprietà della pubblicazione sono state definite in modo non corretto nel passaggio 2 oppure la pubblicazione non esiste.  
  
4.  Se il valore di <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> è **false**, chiamare <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> per creare il processo dell'agente snapshot per questa pubblicazione.  
  
5.  Chiamare il <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> metodo per avviare il processo dell'agente che genera lo snapshot per questa pubblicazione.  
  
6.  (Facoltativo) Quando il valore di <xref:Microsoft.SqlServer.Replication.TransPublication.SnapshotAvailable%2A> è **true**, lo snapshot è disponibile per gli abbonati.  
  
#### Per generare lo snapshot iniziale per una pubblicazione snapshot o transazionale eseguendo il processo dell'agente snapshot (modo sincrono)  
  
1.  Creare un'istanza della classe <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> e impostare le seguenti proprietà obbligatorie:  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publisher%2A> : nome del server di pubblicazione  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherDatabase%2A> : nome del database di pubblicazione  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publication%2A> : nome della pubblicazione  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Distributor%2A> : nome del server di distribuzione  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherSecurityMode%2A> -il valore <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> per utilizzare l'autenticazione di Windows per la connessione al server di pubblicazione o un valore di <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> e valori per <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherLogin%2A> e <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherPassword%2A> utilizzare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione quando ci si connette al server di pubblicazione. L'autenticazione di Windows è la scelta consigliata.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorSecurityMode%2A> -il valore <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> per utilizzare l'autenticazione di Windows per la connessione al server di distribuzione o un valore di <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> e valori per <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorLogin%2A> e <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorPassword%2A> utilizzare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione quando ci si connette al server di distribuzione. L'autenticazione di Windows è la scelta consigliata.  
  
2.  Impostare un valore di <xref:Microsoft.SqlServer.Replication.ReplicationType.Transactional> o <xref:Microsoft.SqlServer.Replication.ReplicationType.Snapshot> per <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.ReplicationType%2A>.  
  
3.  Chiamare il metodo <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.GenerateSnapshot%2A> .  
  
#### Per generare lo snapshot iniziale per una pubblicazione di tipo merge avviando il processo dell'agente snapshot (modo asincrono)  
  
1.  Creare una connessione al server di pubblicazione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.MergePublication> (classe). Impostare il <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> e <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> proprietà per la pubblicazione, quindi impostare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà per la connessione creata nel passaggio 1.  
  
3.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> per caricare le proprietà rimanenti dell'oggetto. Se questo metodo restituisce **false**, le proprietà della pubblicazione sono state definite in modo non corretto nel passaggio 2 oppure la pubblicazione non esiste.  
  
4.  Se il valore di <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> è **false**, chiamare <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> per creare il processo dell'agente snapshot per questa pubblicazione.  
  
5.  Chiamare il <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> metodo per avviare il processo dell'agente che genera lo snapshot per questa pubblicazione.  
  
6.  (Facoltativo) Quando il valore di <xref:Microsoft.SqlServer.Replication.MergePublication.SnapshotAvailable%2A> è **true**, lo snapshot è disponibile per gli abbonati.  
  
#### Per generare lo snapshot iniziale per una pubblicazione di tipo merge eseguendo il processo dell'agente snapshot (modo sincrono)  
  
1.  Creare un'istanza della classe <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> e impostare le seguenti proprietà obbligatorie:  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publisher%2A> : nome del server di pubblicazione  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherDatabase%2A> : nome del database di pubblicazione  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publication%2A> : nome della pubblicazione  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Distributor%2A> : nome del server di distribuzione  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherSecurityMode%2A> -il valore <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> per utilizzare l'autenticazione di Windows per la connessione al server di pubblicazione o un valore di <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> e valori per <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherLogin%2A> e <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherPassword%2A> utilizzare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione quando ci si connette al server di pubblicazione. L'autenticazione di Windows è la scelta consigliata.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorSecurityMode%2A> -il valore <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> per utilizzare l'autenticazione di Windows per la connessione al server di distribuzione o un valore di <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> e valori per <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorLogin%2A> e <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorPassword%2A> utilizzare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione quando ci si connette al server di distribuzione. L'autenticazione di Windows è la scelta consigliata.  
  
2.  Impostare un valore di <xref:Microsoft.SqlServer.Replication.ReplicationType.Merge> per <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.ReplicationType%2A>.  
  
3.  Chiamare il metodo <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.GenerateSnapshot%2A> .  
  
###  <a name="PShellExample"></a> Esempi (RMO)  
 In questo esempio viene eseguito l'agente snapshot in modo sincrono per generare lo snapshot iniziale per una pubblicazione transazionale.  
  
 [!code-csharp[HowTo#rmo_GenerateSnapshot](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_generatesnapshot)]  
  
 [!code-vb[HowTo#rmo_vb_GenerateSnapshot](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_generatesnapshot)]  
  
 In questo esempio viene avviato l'agente snapshot in modo asincrono per generare lo snapshot iniziale per una pubblicazione transazionale.  
  
 [!code-csharp[HowTo#rmo_GenerateSnapshot_WithJob](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_generatesnapshot_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_GenerateSnapshot_WithJob](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_generatesnapshot_withjob)]  
  
## Vedere anche  
 [Creazione di una pubblicazione](../../relational-databases/replication/publish/create-a-publication.md)   
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md)   
 [Creare e applicare lo snapshot](../../relational-databases/replication/create-and-apply-the-snapshot.md)   
 [Inizializzazione di una sottoscrizione con uno snapshot](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [Concetti di base relativi a RMO (Replication Management Objects)](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Procedure consigliate per la sicurezza della replica](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Concetti di base relativi alle stored procedure del sistema di replica](../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Utilizzo di sqlcmd con variabili di scripting](../../relational-databases/scripting/use-sqlcmd-with-scripting-variables.md)  
  
  