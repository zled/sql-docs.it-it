---
title: "Creazione di una pubblicazione | Microsoft Docs"
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
  - "pubblicazioni [replica di SQL Server], creazione"
  - "articoli [replica di SQL Server], definizione"
  - "aggiunta di articoli"
  - "articoli [replica di SQL Server], aggiunta"
ms.assetid: 52ee6de9-1d58-4cb9-8711-372bddbe7154
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# Creazione di una pubblicazione
  In questo argomento viene descritto come creare una pubblicazione in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] o RMO (Replication Management Objects).  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Sicurezza](#Security)  
  
-   **Per creare una pubblicazione e definire articoli, utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Oggetti RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   I nomi di pubblicazioni e articoli non possono includere i seguenti caratteri: %, \* , [,], |,:, ",? , ' , \ , / , \< , >. Se gli oggetti del database includono uno di questi caratteri e si desidera replicarli, è necessario specificare un nome di articolo diverso dal nome dell'oggetto nel **Proprietà articolo - \< articolo>** la finestra di dialogo, disponibile tramite il **articoli** pagina della procedura guidata.  
  
###  <a name="Security"></a> Sicurezza  
 Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali, utilizzare i [servizi di crittografia](http://go.microsoft.com/fwlink/?LinkId=34733) offerti da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows .NET Framework.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Creare le pubblicazioni e definire gli articoli utilizzando la Creazione guidata nuova pubblicazione. Dopo aver creata una pubblicazione, visualizzare e modificare le proprietà di pubblicazione nel **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo. Per informazioni sulla creazione di una pubblicazione da un database Oracle, vedere [creare una pubblicazione da un Database Oracle](../../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md).  
  
#### Per creare una pubblicazione e definire articoli  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere il **replica** cartella e quindi fare di **pubblicazioni locali** cartella.  
  
3.  Fare clic su **Nuova pubblicazione**.  
  
4.  Eseguire i vari passaggi della Creazione guidata nuova pubblicazione per:  
  
    -   Specificare un server di distribuzione se la distribuzione non è stata configurata sul server. Per ulteriori informazioni sulla configurazione della distribuzione, vedere [Configura pubblicazione e distribuzione](../../../relational-databases/replication/configure-publishing-and-distribution.md).  
  
         Se si specifica per il **distributore** pagina che il server di pubblicazione fungerà da server di distribuzione (un server di distribuzione locale) e il server non è configurato come server di distribuzione, la creazione guidata nuova pubblicazione verrà configurato il server. Nella pagina **Cartella snapshot** è necessario specificare una cartella snapshot predefinita per il server di distribuzione. La cartella snapshot è semplicemente una directory designata come condivisione. Gli agenti che eseguono letture e scritture in questa cartella devono disporre di autorizzazioni sufficienti per accedervi. Per ulteriori informazioni sulla protezione della cartella in modo appropriato, vedere [sicurezza della cartella Snapshot](../../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
         Se si specifica che un altro server deve agire come server di distribuzione, è necessario immettere una password nella pagina **Password amministrativa** per le connessioni effettuate dal server di pubblicazione a quello di distribuzione. Questa password deve corrispondere a quella specificata quando il server di pubblicazione è stato attivato nel server di distribuzione remoto.  
  
         Per ulteriori informazioni, vedere [Configura distribuzione](../../../relational-databases/replication/configure-distribution.md).  
  
    -   Scegliere un database di pubblicazione.  
  
    -   Selezionare un tipo di pubblicazione. Per ulteriori informazioni, vedere [tipi di replica](../../../relational-databases/replication/types-of-replication.md).  
  
    -   Specificare i dati e gli oggetti di database da pubblicare; facoltativamente, filtrare le colonne dagli articoli di tabelle e impostare le proprietà degli articoli.  
  
    -   Facoltativamente, filtrate le righe dagli articoli di tabelle. Per ulteriori informazioni, vedere [filtrare i dati pubblicati](../../../relational-databases/replication/publish/filter-published-data.md).  
  
    -   Impostare la pianificazione dell'agente snapshot.  
  
    -   Specificare le credenziali con cui gli agenti di replica seguenti vengono eseguiti e stabiliscono le connessioni:  
  
         \- Agente snapshot per tutte le pubblicazioni.  
  
         \- Agente di lettura log per tutte le pubblicazioni transazionali.  
  
         \- Agente di lettura coda per le pubblicazioni transazionali che consentono sottoscrizioni aggiornabili.  
  
         Per ulteriori informazioni, vedere [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md) e [Replication Security Best Practices](../../../relational-databases/replication/security/replication-security-best-practices.md).  
  
    -   Facoltativamente, creare lo script della pubblicazione. Per altre informazioni, vedere [Scripting Replication](../../../relational-databases/replication/scripting-replication.md).  
  
    -   Specificare un nome per la pubblicazione.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 È possibile creare pubblicazioni a livello di programmazione tramite le stored procedure di replica. Le stored procedure utilizzate dipenderanno dal tipo di pubblicazione creato.  
  
#### Per creare una pubblicazione snapshot o transazionale  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_replicationdboption & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md) Per abilitare la pubblicazione del database corrente utilizzando la replica transazionale o snapshot.  
  
2.  Per una pubblicazione transazionale, determinare se esiste un processo dell'agente di lettura log per il database di pubblicazione. Questo passaggio non è necessario per le pubblicazioni snapshot.  
  
    -   Se per il database di pubblicazione esiste un processo dell'agente di lettura log, procedere con il passaggio 3.  
  
    -   Se si è certi se esiste un processo dell'agente di lettura Log per un database pubblicato, eseguire [sp_helplogreader_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md) nel server di pubblicazione nel database di pubblicazione.  
  
    -   Se il set di risultati è vuoto, creare un processo dell'agente di lettura log. Server di pubblicazione, eseguire [sp_addlogreader_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md). Specificare il [!INCLUDE[msCoName](../../../includes/msconame-md.md)] le credenziali di Windows con cui viene eseguito l'agente per **@job_name** e **@password**. Se l'agente utilizzerà l'autenticazione di SQL Server quando ci si connette al server di pubblicazione, è necessario specificare anche un valore di **0** per **@publisher_security_mode** e [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] informazioni di accesso per **@publisher_login** e **@publisher_password**. Procedere al passaggio 3.  
  
3.  Server di pubblicazione, eseguire [sp_addpublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md). Specificare un nome di pubblicazione per **@publication**, e, per il **@repl_freq** parametro, specificare un valore di **snapshot** per una pubblicazione snapshot o un valore di **Continua** per una pubblicazione transazionale. Specificare eventuali altre opzioni della pubblicazione. In questo modo viene definita la pubblicazione.  
  
    > [!NOTE]  
    >  I nomi delle pubblicazioni non possono includere i caratteri seguenti:  
    >   
    >  % * [ ] | : " ? \ / \< >  
  
4.  Server di pubblicazione, eseguire [sp_addpublication_snapshot & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Specificare il nome della pubblicazione utilizzato al passaggio 3 per **@publication** e le credenziali di Windows con cui viene eseguito l'agente Snapshot per **@snapshot_job_name** e **@password**. Se l'agente utilizzerà l'autenticazione di SQL Server quando ci si connette al server di pubblicazione, è necessario specificare anche un valore di **0** per **@publisher_security_mode** e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] informazioni di accesso per **@publisher_login** e **@publisher_password**. Verrà creato un processo dell'agente snapshot per la pubblicazione.  
  
    > [!IMPORTANT]  
    >  Quando si configura un server di pubblicazione con un server di distribuzione remoto, i valori specificati per tutti i parametri, inclusi *job_login* e *job_password*, vengono inviati al server di distribuzione come testo normale. È consigliabile crittografare la connessione tra il server di pubblicazione e il server di distribuzione remoto prima di eseguire questa stored procedure. Per ulteriori informazioni, vedere [abilitare connessioni crittografate al motore di Database & #40; SQL Server Configuration Manager & #41;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
5.  Aggiungere articoli alla pubblicazione. Per altre informazioni, vedere [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
6.  Avviare il processo dell'agente snapshot per generare lo snapshot iniziale per la pubblicazione. Per altre informazioni, vedere [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
#### Per creare una pubblicazione di tipo merge  
  
1.  Server di pubblicazione, eseguire [sp_replicationdboption & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md) Per abilitare la pubblicazione del database corrente tramite la replica di tipo merge.  
  
2.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addmergepublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Specificare il nome della pubblicazione per **@publication** e eventuali altre opzioni della pubblicazione. In questo modo viene definita la pubblicazione.  
  
    > [!NOTE]  
    >  I nomi delle pubblicazioni non possono includere i caratteri seguenti:  
    >   
    >  % * [ ] | : " ? \ / \< >  
  
3.  Server di pubblicazione, eseguire [sp_addpublication_snapshot & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Specificare il nome della pubblicazione utilizzato al passaggio 2 per **@publication** e le credenziali di Windows con cui viene eseguito l'agente Snapshot per **@snapshot_job_name** e **@password**. Se l'agente utilizzerà l'autenticazione di SQL Server quando ci si connette al server di pubblicazione, è necessario specificare anche un valore di **0** per **@publisher_security_mode** e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] informazioni di accesso per **@publisher_login** e **@publisher_password**. Verrà creato un processo dell'agente snapshot per la pubblicazione.  
  
    > [!IMPORTANT]  
    >  Quando si configura un server di pubblicazione con un server di distribuzione remoto, i valori specificati per tutti i parametri, inclusi *job_login* e *job_password*, vengono inviati al server di distribuzione come testo normale. È consigliabile crittografare la connessione tra il server di pubblicazione e il server di distribuzione remoto prima di eseguire questa stored procedure. Per ulteriori informazioni, vedere [abilitare connessioni crittografate al motore di Database & #40; SQL Server Configuration Manager & #41;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
4.  Aggiungere articoli alla pubblicazione. Per altre informazioni, vedere [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
5.  Avviare il processo dell'agente snapshot per generare lo snapshot iniziale per la pubblicazione. Per altre informazioni, vedere [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
###  <a name="TsqlExample"></a> Esempio (Transact-SQL)  
 In questo esempio viene creata una pubblicazione transazionale. Per passare le credenziali di Windows necessarie per la creazione di processi per l'agente snapshot e per l'agente di lettura log, vengono utilizzate variabili di scripting.  
  
 [!code-sql[HowTo#sp_AddTranPub](../../../relational-databases/replication/codesnippet/tsql/create-a-publication_1.sql)]  
  
 In questo esempio viene creata una pubblicazione di tipo merge. Per passare le credenziali di Windows necessarie per la creazione del processo per l'agente snapshot, vengono utilizzate variabili di scripting.  
  
 [!code-sql[HowTo#sp_AddMergePub](../../../relational-databases/replication/codesnippet/tsql/create-a-publication_2.sql)]  
  
##  <a name="RMOProcedure"></a> Utilizzo di RMO (Replication Management Objects)  
 È possibile creare pubblicazioni a livello di programmazione tramite gli oggetti RMO (Replication Management Objects). Le classi RMO utilizzate per creare una pubblicazione dipendono dal tipo di pubblicazione creata.  
  
#### Per creare una pubblicazione snapshot o transazionale  
  
1.  Creare una connessione al server di pubblicazione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza del <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> classe per il database di pubblicazione, impostare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà all'istanza di <xref:Microsoft.SqlServer.Management.Common.ServerConnection> dal passaggio 1 e chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo. Se <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> restituisce **false**, verificare che il database esista.  
  
3.  Se il <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledTransPublishing%2A> è **false**, impostarlo su **true**.  
  
4.  Per una pubblicazione transazionale, controllare il valore di <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.LogReaderAgentExists%2A> proprietà. Se questa proprietà è impostata su **true**, per il database esiste già un processo dell'agente di lettura log. Se questa proprietà è impostata su **false**, eseguire le operazioni seguenti:  
  
    -   Impostare il <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> e <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> o <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword%2A> i campi di <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.LogReaderAgentProcessSecurity%2A> per fornire le credenziali per il [!INCLUDE[msCoName](../../../includes/msconame-md.md)] account di Windows in cui viene eseguito l'agente di lettura Log.  
  
        > [!NOTE]  
        >  L'impostazione <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.LogReaderAgentProcessSecurity%2A> non è richiesto per la pubblicazione viene creata da un membro del **sysadmin** ruolo predefinito del server. In questo caso l'agente rappresenterà l'account di SQL Server Agent. Per altre informazioni, vedere [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
    -   (Facoltativo) Impostare il <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> e <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> o <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> i campi di <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.LogReaderAgentPublisherSecurity%2A> quando si utilizza l'autenticazione di SQL Server per connettersi al server di pubblicazione.  
  
    -   Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.CreateLogReaderAgent%2A> metodo per creare il processo di agente di lettura Log per il database.  
  
5.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.TransPublication> classe e impostare le seguenti proprietà per questo oggetto:  
  
    -   Il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> dal passaggio 1 per <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
    -   Il nome del database pubblicato per <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>.  
  
    -   Un nome per la pubblicazione per <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>.  
  
    -   Oggetto <xref:Microsoft.SqlServer.Replication.PublicationType> tra <xref:Microsoft.SqlServer.Replication.PublicationType.Transactional> o <xref:Microsoft.SqlServer.Replication.PublicationType.Snapshot>.  
  
    -   Il <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> e <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> i campi di <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> per fornire le credenziali per l'account di Windows con cui viene eseguito l'agente Snapshot. Questo account viene utilizzato anche quando l'agente snapshot stabilisce connessioni al server di distribuzione locale e per qualsiasi connessione remota quando si utilizza l'autenticazione di Windows.  
  
        > [!NOTE]  
        >  L'impostazione <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> non è richiesto per la pubblicazione viene creata da un membro del **sysadmin** ruolo predefinito del server. In questo caso l'agente rappresenterà l'account di SQL Server Agent. Per altre informazioni, vedere [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
    -   (Facoltativo) Il <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> e <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> o <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> i campi di <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentPublisherSecurity%2A> quando si utilizza l'autenticazione di SQL Server per connettersi al server di pubblicazione.  
  
    -   (Facoltativo) Utilizzare l'operatore logico OR inclusivo (**|** in Visual c# e **o** in Visual Basic) e l'operatore logico OR esclusivo (**^** in Visual c# e **Xor** in Visual Basic) per impostare il <xref:Microsoft.SqlServer.Replication.PublicationAttributes> i valori per il <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> proprietà.  
  
    -   (Facoltativo) Il nome del server di pubblicazione per <xref:Microsoft.SqlServer.Replication.TransPublication.PublisherName%2A> quando il server di pubblicazione è un Server di pubblicazione non SQL.  
  
6.  Chiamare il <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> metodo per creare la pubblicazione.  
  
    > [!IMPORTANT]  
    >  Quando si configura un server di pubblicazione con un server di distribuzione remoto, i valori specificati per tutte le proprietà, inclusi <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A>, vengono inviati al server di distribuzione come testo normale. È consigliabile crittografare la connessione tra il server di pubblicazione e il relativo server di distribuzione remoto prima di chiamare il <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> metodo. Per ulteriori informazioni, vedere [abilitare connessioni crittografate al motore di Database & #40; SQL Server Configuration Manager & #41;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
7.  Chiamare il <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> metodo per creare il processo dell'agente Snapshot per la pubblicazione.  
  
#### Per creare una pubblicazione di tipo merge  
  
1.  Creare una connessione al server di pubblicazione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza del <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> classe per il database di pubblicazione, impostare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà all'istanza di <xref:Microsoft.SqlServer.Management.Common.ServerConnection> dal passaggio 1 e chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo. Se <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> restituisce **false**, verificare che il database esista.  
  
3.  Se <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledMergePublishing%2A> è **false**, impostarlo su **true**, e chiamare <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A>.  
  
4.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.MergePublication> classe e impostare le seguenti proprietà per questo oggetto:  
  
    -   Il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> dal passaggio 1 per <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
    -   Il nome del database pubblicato per <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>.  
  
    -   Un nome per la pubblicazione per <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>.  
  
    -   Il <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> e <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> i campi di <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> per fornire le credenziali per l'account di Windows con cui viene eseguito l'agente Snapshot. Questo account viene utilizzato anche quando l'agente snapshot stabilisce connessioni al server di distribuzione locale e per qualsiasi connessione remota quando si utilizza l'autenticazione di Windows.  
  
        > [!NOTE]  
        >  L'impostazione <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> non è richiesto per la pubblicazione viene creata da un membro del **sysadmin** ruolo predefinito del server. Per altre informazioni, vedere [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
    -   (Facoltativo) Utilizzare l'operatore logico OR inclusivo (**|** in Visual c# e **o** in Visual Basic) e l'operatore logico OR esclusivo (**^** in Visual c# e **Xor** in Visual Basic) per impostare il <xref:Microsoft.SqlServer.Replication.PublicationAttributes> i valori per il <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> proprietà.  
  
5.  Chiamare il <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> metodo per creare la pubblicazione.  
  
    > [!IMPORTANT]  
    >  Quando si configura un server di pubblicazione con un server di distribuzione remoto, i valori specificati per tutte le proprietà, inclusi <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A>, vengono inviati al server di distribuzione come testo normale. È consigliabile crittografare la connessione tra il server di pubblicazione e il relativo server di distribuzione remoto prima di chiamare il <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> metodo. Per ulteriori informazioni, vedere [abilitare connessioni crittografate al motore di Database & #40; SQL Server Configuration Manager & #41;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
6.  Chiamare il <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> metodo per creare il processo dell'agente Snapshot per la pubblicazione.  
  
###  <a name="PShellExample"></a> Esempi (RMO)  
 In questo esempio il database AdventureWorks viene abilitato per la pubblicazione transazionale, viene definito un processo dell'agente di lettura log e viene creata la pubblicazione AdvWorksProductTran. Per questa pubblicazione è necessario definire un articolo. Le credenziali dell'account di Windows necessarie per creare il processo dell'agente di lettura log e il processo dell'agente snapshot vengono passate in fase di esecuzione. Per informazioni sull'utilizzo di oggetti RMO per definire articoli snapshot e transazionali, vedere [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
 [!code-csharp[HowTo#rmo_CreateTranPub](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createtranpub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateTranPub](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createtranpub)]  
  
 In questo esempio il database AdventureWorks viene abilitato per la pubblicazione di tipo merge e viene creata la pubblicazione AdvWorksSalesOrdersMerge. Per questa pubblicazione è ancora necessario definire gli articoli. Le credenziali dell'account di Windows necessarie per creare il processo dell'agente snapshot vengono passate in fase di esecuzione. Per informazioni sull'utilizzo di oggetti RMO per definire articoli di merge, vedere [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
 [!code-csharp[HowTo#rmo_CreateMergePub](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createmergepub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePub](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createmergepub)]  
  
## Vedere anche  
 [Utilizzo di sqlcmd con variabili di scripting](../../../relational-databases/scripting/use-sqlcmd-with-scripting-variables.md)   
 [Pubblicazione di dati e oggetti di database](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Concetti di base relativi a RMO (Replication Management Objects)](../../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)   
 [Visualizzazione e modifica delle proprietà della pubblicazione](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Configurazione della distribuzione](../../../relational-databases/replication/configure-distribution.md)   
 [Sicurezza del database di distribuzione](../../../relational-databases/replication/security/secure-the-distributor.md)   
 [Sicurezza del server di pubblicazione](../../../relational-databases/replication/security/secure-the-publisher.md)  
  
  