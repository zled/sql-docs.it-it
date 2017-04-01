---
title: "Creazione di una sottoscrizione push | Microsoft Docs"
ms.custom: ""
ms.date: "08/25/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "push subscriptions [SQL Server replication], creating"
  - "merge replication subscribing [SQL Server replication], push subscriptions"
  - "subscriptions [SQL Server replication], push"
  - "snapshot replication [SQL Server], subscribing"
  - "replica transazionale, sottoscrizione"
ms.assetid: adfbbc61-58d1-4330-9ad6-b14ab1142e2b
caps.latest.revision: 41
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 41
---
# Creazione di una sottoscrizione push
  In questo argomento viene descritto come creare una sottoscrizione push in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], o gli oggetti RMO (Replication Management Objects). Per informazioni sulla creazione di una sottoscrizione push per non[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sottoscrittore, vedere [creare una sottoscrizione per un sottoscrittore Non SQL Server](../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md).  
  
 
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Creare una sottoscrizione push nel server di pubblicazione o nel Sottoscrittore utilizzando la Creazione guidata nuova sottoscrizione. Attenersi alle indicazioni presenti nelle pagine della procedura guidata per:  
  
-   Specificare il server di pubblicazione e la pubblicazione.  
  
-   Selezionare la posizione di esecuzione degli agenti di replica. Per una sottoscrizione push, selezionare **Esegui tutti gli agenti nel server di distribuzione (sottoscrizioni push)** sul **posizione agente di distribuzione** pagina o **posizione agente di Merge** pagina, a seconda del tipo di pubblicazione.  
  
-   Specificare i Sottoscrittori e i database di sottoscrizione.  
  
-   Specificare gli accessi e le password utilizzati per le connessioni stabilite dagli agenti di replica:  
  
    -   Per effettuare sottoscrizioni di pubblicazioni snapshot e transazionali, specificare le credenziali nella pagina **Sicurezza agente di distribuzione** .  
  
    -   Per effettuare sottoscrizioni di pubblicazioni di tipo merge, specificare le credenziali nella pagina **Sicurezza agente di merge** .  
  
     Per informazioni sulle autorizzazioni necessarie per ogni agente, vedere [modello di sicurezza dell'agente di replica](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
-   Specificare una pianificazione della sincronizzazione e definire quando il Sottoscrittore dovrà essere inizializzato.  
  
-   Specificare le opzioni aggiuntive per le pubblicazioni di tipo merge, ovvero tipo di sottoscrizione e valori per il filtro con parametri.  
  
-   Specificare le opzioni aggiuntive per le pubblicazioni transazionali che consentono l'aggiornamento delle sottoscrizioni, indicando se si desidera che i Sottoscrittori eseguano immediatamente il commit delle modifiche nel server di pubblicazione o se devono aggiungerle a una coda e le credenziali utilizzate per stabilire una connessione dal Sottoscrittore al server di pubblicazione.  
  
-   Facoltativamente, creare lo script della sottoscrizione.  
  
#### Per creare una sottoscrizione push dal server di pubblicazione  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Pubblicazioni locali** .  
  
3.  Pulsante destro del mouse la pubblicazione per cui si desidera creare una o più sottoscrizioni e quindi fare clic su **nuove sottoscrizioni**.  
  
4.  Completare i passaggi della Creazione guidata nuova sottoscrizione.  
  
#### Per creare una sottoscrizione push dal Sottoscrittore  
  
1.  Connettersi al Sottoscrittore in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** .  
  
3.  Pulsante destro del mouse il **sottoscrizioni locali** cartella e quindi fare clic su **nuove sottoscrizioni**.  
  
4.  Nel **pubblicazione** pagina della creazione guidata sottoscrizione, selezionare **\< trovare di pubblicazione SQL Server>** o **\< Trova server di pubblicazione Oracle>** dal **Publisher** elenco a discesa.  
  
5.  Connettersi al server di pubblicazione nella finestra di dialogo **Connetti a server** .  
  
6.  Selezionare una pubblicazione nella pagina **Pubblicazione** .  
  
7.  Completare i passaggi della Creazione guidata nuova sottoscrizione.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 Le sottoscrizioni push possono essere create a livello di programmazione utilizzando stored procedure di replica. Le stored procedure utilizzate dipenderanno dal tipo di pubblicazione a cui appartiene la sottoscrizione.  
  
> **IMPORTANTE** Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali in un file script, è fondamentale proteggere il file per evitare accessi non autorizzati.  
  
#### Per creare una sottoscrizione push di una pubblicazione snapshot o transazionale  
  
1.  Nel server di pubblicazione nel database di pubblicazione, verificare che la pubblicazione supporta le sottoscrizioni push eseguendo [sp_helppublication](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md).  
  
    -   Se il valore di **allow_push** è **1**, sono supportate le sottoscrizioni push.  
  
    -   Se il valore di **allow_push** è **0**, eseguire [sp_changepublication](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), specificando **allow_push** per **@property** e **true** per **@value**.  
  
2.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addsubscription](https://msdn.microsoft.com/library/ms181702.aspx). Specificare **@publication**, **@subscriber** e **@destination_db**. Specificare un valore di **push** per **@subscription_type**. Per informazioni su come aggiornare le sottoscrizioni, vedere [creare una sottoscrizione aggiornabile di una pubblicazione transazionale](https://msdn.microsoft.com/library/ms152769.aspx).  
  
3.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addpushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md). Specificare le opzioni seguenti:  
  
    -   Il **@subscriber**, **@subscriber_db**, e **@publication** parametri.  
  
    -   Il [!INCLUDE[msCoName](../../includes/msconame-md.md)] le credenziali di Windows con cui viene eseguito l'agente di distribuzione nel server di distribuzione per **@job_login** e **@job_password**.  
  
        > **Nota:** le connessioni stabilite utilizzando sempre l'autenticazione integrata di Windows utilizzano le credenziali Windows specificate da **@job_login** e **@job_password**. L'agente di distribuzione esegue sempre la connessione locale al server di distribuzione utilizzando l'autenticazione integrata di Windows. Per impostazione predefinita, l'agente si connette al Sottoscrittore utilizzando l'autenticazione integrata di Windows.  
  
    -   (Facoltativo) Il valore **0** per **@subscriber_security_mode** e [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] informazioni di accesso per **@subscriber_login** e **@subscriber_password**. Specificare questi parametri se è necessario utilizzare l'autenticazione di SQL Server per la connessione al Sottoscrittore.  
  
    -   Specificare una pianificazione per il processo dell'agente di distribuzione da eseguire per la sottoscrizione. Per altre informazioni, vedere [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md).  
  
    > **IMPORTANTE** Quando si crea una sottoscrizione push in un server di pubblicazione con un server di distribuzione remoto, i valori specificati per tutti i parametri, inclusi *job_login* e *job_password*, vengono inviati al server di distribuzione come testo normale. È consigliabile crittografare la connessione tra il server di pubblicazione e il server di distribuzione remoto prima di eseguire questa stored procedure. Per altre informazioni, vedere [Abilitare le connessioni crittografate al motore di database &#40;Gestione configurazione SQL Server&#41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
#### Per creare una sottoscrizione push di una pubblicazione di tipo merge  
  
1.  Nel server di pubblicazione nel database di pubblicazione, verificare che la pubblicazione supporta le sottoscrizioni push eseguendo [sp_helpmergepublication](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md).  
  
    -   Se il valore di **allow_push** è **1**, la pubblicazione supporta le sottoscrizioni push.  
  
    -   Se il valore di **allow_push** non **1**, eseguire [sp_changemergepublication](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), specificando **allow_push** per **@property** e **true** per **@value**.  
  
2.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addmergesubscription](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md), specificando i parametri seguenti:  
  
    -   **@publication**. Nome della pubblicazione.  
  
    -   **@subscriber_type**. Per una sottoscrizione client specificare **local** e per una sottoscrizione server specificare **global**.  
  
    -   **@subscription_priority**. Per una sottoscrizione server, specificare una priorità per la sottoscrizione (**0.00** a **99,99**).  
  
         Per altre informazioni, vedere [Advanced Merge Replication Conflict Detection and Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md).  
  
3.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addmergepushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql.md). Specificare le opzioni seguenti:  
  
    -   Il **@subscriber**, **@subscriber_db**, e **@publication** parametri.  
  
    -   Le credenziali di Windows con cui viene eseguito l'agente di Merge nel server di distribuzione per **@job_login** e **@job_password**.  
  
        > **Nota:**  le connessioni stabilite utilizzando sempre l'autenticazione integrata di Windows utilizzano le credenziali Windows specificate da **@job_login** e **@job_password**. L'agente di merge esegue sempre la connessione locale al server di distribuzione utilizzando l'autenticazione integrata di Windows. Per impostazione predefinita, l'agente si connette al Sottoscrittore utilizzando l'autenticazione integrata di Windows.  
  
    -   (Facoltativo) Il valore **0** per **@subscriber_security_mode** e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] informazioni di accesso per **@subscriber_login** e **@subscriber_password**. Specificare questi parametri se è necessario utilizzare l'autenticazione di SQL Server per la connessione al Sottoscrittore.  
  
    -   (Facoltativo) Il valore **0** per **@publisher_security_mode** e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] informazioni di accesso per **@publisher_login** e **@publisher_password**. Specificare questi valori se è necessario utilizzare l'autenticazione di SQL Server per la connessione al server di pubblicazione.  
  
    -   Una pianificazione per il processo dell'agente di merge per la sottoscrizione. Per altre informazioni, vedere [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md).  
  
    > **IMPORTANTE** Quando si crea una sottoscrizione push in un server di pubblicazione con un server di distribuzione remoto, i valori specificati per tutti i parametri, inclusi *job_login* e *job_password*, vengono inviati al server di distribuzione come testo normale. È consigliabile crittografare la connessione tra il server di pubblicazione e il server di distribuzione remoto prima di eseguire questa stored procedure. Per altre informazioni, vedere [Abilitare le connessioni crittografate al motore di database &#40;Gestione configurazione SQL Server&#41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
###  <a name="TsqlExample"></a> Esempi (Transact-SQL)  
 Nell'esempio seguente viene creata una sottoscrizione push a una pubblicazione transazionale. I valori dell'account di accesso e della password vengono forniti in fase di esecuzione tramite le variabili di scripting **sqlcmd** .  
  
 [!code-sql[HowTo#sp_addtranpushsubscription_agent](../../relational-databases/replication/codesnippet/tsql/create-a-push-subscription_1.sql)]  
  
 Nell'esempio seguente viene creata una sottoscrizione push a una pubblicazione di tipo merge. I valori dell'account di accesso e della password vengono forniti in fase di esecuzione tramite le variabili di scripting **sqlcmd** .  
  
 [!code-sql[HowTo#sp_addmergepushsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/create-a-push-subscription_2.sql)]  
  
##  <a name="RMOProcedure"></a> Utilizzo di RMO (Replication Management Objects)  
 È possibile creare sottoscrizioni push a livello di programmazione tramite gli oggetti RMO (Replication Management Objects). Le classi RMO utilizzate per la creazione di una sottoscrizione push dipendono dal tipo di pubblicazione per cui viene creata la sottoscrizione.  
  
> **IMPORTANTE** Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali, utilizzare i [servizi di crittografia](http://go.microsoft.com/fwlink/?LinkId=34733) offerti da [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows .NET Framework.  
  
#### Per creare una sottoscrizione push di una pubblicazione snapshot o transazionale  
  
1.  Creare una connessione al server di pubblicazione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.TransPublication> classe tramite la connessione server di pubblicazione dal passaggio 1. Specificare <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>, e <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo. Se il metodo restituisce **false**, le proprietà specificate nel passaggio 2 non sono corrette oppure la pubblicazione non esiste nel server.  
  
4.  Eseguire un'operazione con AND logico bit per bit (**&** in Visual c# e **e** in Visual Basic) tra il <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> proprietà e <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPush>. Se il risultato è <xref:Microsoft.SqlServer.Replication.PublicationAttributes.None>, impostare <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> al risultato di un operatore logico OR bit per bit (**|** in Visual c# e **o** in Visual Basic) tra <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> e <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPush>. Quindi, chiamare <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> per abilitare le sottoscrizioni push.  
  
5.  Se il database di sottoscrizione non esiste, crearlo utilizzando la <xref:Microsoft.SqlServer.Management.Smo.Database> (classe). Per ulteriori informazioni, vedere [creazione, modifica e rimozione di database](../../relational-databases/server-management-objects-smo/tasks/creating-altering-and-removing-databases.md).  
  
6.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.TransSubscription> (classe).  
  
7.  Impostare le proprietà seguenti per la sottoscrizione:  
  
    -   Il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> al server di pubblicazione creato nel passaggio 1 per <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
    -   Nome del database di sottoscrizione per <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>.  
  
    -   Nome del sottoscrittore per <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>.  
  
    -   Nome del database di pubblicazione per <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>.  
  
    -   Nome della pubblicazione per <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>.  
  
    -   Il <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> e <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> o <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword%2A> i campi di <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A> per fornire le credenziali per il [!INCLUDE[msCoName](../../includes/msconame-md.md)] account Windows con cui viene eseguito l'agente di distribuzione nel server di distribuzione. Questo account viene utilizzato per attivare connessioni locali al server di distribuzione e stabilire connessioni remote con l'autenticazione di Windows.  
  
        > **Nota:** impostazione <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A> non è richiesto per la creazione della sottoscrizione da un membro del **sysadmin** ruolo predefinito del server, tuttavia, è consigliabile. In questo caso l'agente rappresenterà l'account di SQL Server Agent. Per altre informazioni, vedere [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
    -   (Facoltativo) Il valore **true** (predefinito) per <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A> per creare un processo dell'agente che viene utilizzato per sincronizzare la sottoscrizione. Se si specifica **false**, la sottoscrizione può essere sincronizzata solo a livello di programmazione.  
  
    -   (Facoltativo) Impostare il <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> e <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> o <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> i campi di <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberSecurity%2A> quando si utilizza l'autenticazione di SQL Server per la connessione al sottoscrittore.  
  
8.  Chiamare il <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> metodo.  
  
    > **IMPORTANTE!!**Quando si crea una sottoscrizione push in un server di pubblicazione con un server di distribuzione remoto, i valori specificati per tutte le proprietà, inclusi <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A>, vengono inviati al server di distribuzione come testo normale. È consigliabile crittografare la connessione tra il server di pubblicazione e il relativo server di distribuzione remoto prima di chiamare il <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> metodo. Per altre informazioni, vedere [Abilitare le connessioni crittografate al motore di database &#40;Gestione configurazione SQL Server&#41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
#### Per creare una sottoscrizione push di una pubblicazione di tipo merge  
  
1.  Creare una connessione al server di pubblicazione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.MergePublication> classe tramite la connessione server di pubblicazione dal passaggio 1. Specificare <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>, e <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo. Se il metodo restituisce **false**, le proprietà specificate nel passaggio 2 non sono corrette oppure la pubblicazione non esiste nel server.  
  
4.  Eseguire un'operazione con AND logico bit per bit (**&** in Visual c# e **e** in Visual Basic) tra il <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> proprietà e <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPush>. Se il risultato è <xref:Microsoft.SqlServer.Replication.PublicationAttributes.None>, impostare <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> al risultato di un operatore logico OR bit per bit (**|** in Visual c# e **o** in Visual Basic) tra <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> e <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPush>. Quindi, chiamare <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> per abilitare le sottoscrizioni push.  
  
5.  Se il database di sottoscrizione non esiste, crearlo utilizzando la <xref:Microsoft.SqlServer.Management.Smo.Database> (classe). Per ulteriori informazioni, vedere [creazione, modifica e rimozione di database](../../relational-databases/server-management-objects-smo/tasks/creating-altering-and-removing-databases.md).  
  
6.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.MergeSubscription> (classe).  
  
7.  Impostare le proprietà seguenti per la sottoscrizione:  
  
    -   Il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> al server di pubblicazione creato nel passaggio 1 per <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
    -   Nome del database di sottoscrizione per <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>.  
  
    -   Nome del sottoscrittore per <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>.  
  
    -   Nome del database di pubblicazione per <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>.  
  
    -   Nome della pubblicazione per <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>.  
  
    -   Il <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> e <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> o <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword%2A> i campi di <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A> per fornire le credenziali per il [!INCLUDE[msCoName](../../includes/msconame-md.md)] account Windows con cui viene eseguito l'agente di Merge nel server di distribuzione. Questo account viene utilizzato per attivare connessioni locali al server di distribuzione e stabilire connessioni remote con l'autenticazione di Windows.  
  
        > **Nota:** impostazione <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A> non è richiesto per la creazione della sottoscrizione da un membro del **sysadmin** ruolo predefinito del server, tuttavia, è consigliabile. In questo caso l'agente rappresenterà l'account di SQL Server Agent. Per altre informazioni, vedere [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
    -   (Facoltativo) Il valore **true** (predefinito) per <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A> per creare un processo dell'agente che viene utilizzato per sincronizzare la sottoscrizione. Se si specifica **false**, la sottoscrizione può essere sincronizzata solo a livello di programmazione.  
  
    -   (Facoltativo) Impostare il <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> e <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> o <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> i campi di <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberSecurity%2A> quando si utilizza l'autenticazione di SQL Server per la connessione al sottoscrittore.  
  
    -   (Facoltativo) Impostare il <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> e <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> o <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> i campi di <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherSecurity%2A> quando si utilizza l'autenticazione di SQL Server per connettersi al server di pubblicazione.  
  
8.  Chiamare il <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> metodo.  
  
    > **IMPORTANTE**  Quando si crea una sottoscrizione push in un server di pubblicazione con un server di distribuzione remoto, i valori specificati per tutte le proprietà, inclusi <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A>, vengono inviati al server di distribuzione come testo normale. È consigliabile crittografare la connessione tra il server di pubblicazione e il relativo server di distribuzione remoto prima di chiamare il <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> metodo. Per altre informazioni, vedere [Abilitare le connessioni crittografate al motore di database &#40;Gestione configurazione SQL Server&#41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
###  <a name="PShellExample"></a> Esempi (RMO)  
 In questo esempio viene creata una nuova sottoscrizione push di una pubblicazione transazionale. Le credenziali dell'account di Windows utilizzate per eseguire il processo dell'agente di distribuzione vengono passate in fase di esecuzione.  
  
 [!code-csharp[HowTo#rmo_CreateTranPushSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createtranpushsub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateTranPushSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createtranpushsub)]  
  
 In questo esempio viene creata una nuova sottoscrizione push di una pubblicazione di tipo merge. Le credenziali dell'account di Windows utilizzate per eseguire il processo dell'agente di merge vengono passate in fase di esecuzione.  
  
 [!code-csharp[HowTo#rmo_CreateMergePushSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createmergepushsub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePushSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createmergepushsub)]  
  
## Vedere anche  
 [Visualizzazione e modifica delle proprietà delle sottoscrizioni push](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [Procedure consigliate per la sicurezza della replica](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Creazione di una pubblicazione](../../relational-databases/replication/publish/create-a-publication.md)   
 [Concetti di base relativi a RMO (Replication Management Objects)](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Sincronizzazione di una sottoscrizione push](../../relational-databases/replication/synchronize-a-push-subscription.md)   
 [Sottoscrizione delle pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)   
 [Utilizzo di sqlcmd con variabili di scripting](../../relational-databases/scripting/use-sqlcmd-with-scripting-variables.md)  
  
  