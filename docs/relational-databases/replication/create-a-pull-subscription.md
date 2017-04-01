---
title: "Creazione di una sottoscrizione pull | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pull subscriptions [SQL Server replication], creating"
  - "merge replication subscribing [SQL Server replication], pull subscriptions"
  - "subscriptions [SQL Server replication], pull"
  - "snapshot replication [SQL Server], subscribing"
  - "replica transazionale, sottoscrizione"
ms.assetid: 41d1886d-59c9-41fc-9bd6-a59b40e0af6e
caps.latest.revision: 46
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# Creazione di una sottoscrizione pull
  Questo argomento viene descritto come creare una sottoscrizione pull in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], o gli oggetti RMO (Replication Management Objects).  
  
 L'impostazione della sottoscrizione pull per la replica P2P è possibile dallo script, ma non è disponibile tramite la procedura guidata.  
 
  ##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Creare una sottoscrizione pull nel server di pubblicazione o nel Sottoscrittore tramite la Creazione guidata sottoscrizione. Attenersi alle indicazioni presenti nelle pagine della procedura guidata per:  
  
-   Specificare il server di pubblicazione e la pubblicazione.  
  
-   Selezionare la posizione di esecuzione degli agenti di replica. Per una sottoscrizione pull, selezionare **Esegui ogni agente nel relativo sottoscrittore (sottoscrizioni pull)** sul **posizione agente di distribuzione** pagina o **posizione agente di Merge** pagina, a seconda del tipo di pubblicazione.  
  
-   Specificare i Sottoscrittori e i database di sottoscrizione.  
  
-   Specificare gli accessi e le password utilizzati per le connessioni stabilite dagli agenti di replica:  
  
    -   Per effettuare sottoscrizioni di pubblicazioni snapshot e transazionali, specificare le credenziali nella pagina **Sicurezza agente di distribuzione** .  
  
    -   Per effettuare sottoscrizioni di pubblicazioni di tipo merge, specificare le credenziali nella pagina **Sicurezza agente di merge** .  
  
     Per informazioni sulle autorizzazioni necessarie per ogni agente, vedere [modello di sicurezza dell'agente di replica](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
-   Specificare una pianificazione della sincronizzazione e definire quando il Sottoscrittore dovrà essere inizializzato.  
  
-   Specificare le opzioni aggiuntive per le pubblicazioni di tipo merge: il tipo di sottoscrizione, i valori dei filtri con parametri e le informazioni per la sincronizzazione tramite HTTPS se la pubblicazione è abilitata per la sincronizzazione Web.  
  
-   Specificare le opzioni aggiuntive per le pubblicazioni transazionali che consentono l'aggiornamento delle sottoscrizioni, indicando se si desidera che i Sottoscrittori eseguano immediatamente il commit delle modifiche nel server di pubblicazione o se devono aggiungerle a una coda e le credenziali utilizzate per stabilire una connessione dal Sottoscrittore al server di pubblicazione.  
  
-   Facoltativamente, creare lo script della sottoscrizione.  
  
#### Per creare una sottoscrizione pull dal server di pubblicazione  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Pubblicazioni locali** .  
  
3.  Pulsante destro del mouse la pubblicazione per cui si desidera creare una o più sottoscrizioni e quindi fare clic su **nuove sottoscrizioni**.  
  
4.  Completare i passaggi della Creazione guidata nuova sottoscrizione.  
  
#### Per creare una sottoscrizione pull dal Sottoscrittore  
  
1.  Connettersi al Sottoscrittore in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** .  
  
3.  Pulsante destro del mouse il **sottoscrizioni locali** cartella e quindi fare clic su **nuove sottoscrizioni**.  
  
4.  Nel **pubblicazione** pagina della creazione guidata sottoscrizione, selezionare **\< trovare di pubblicazione SQL Server>** o **\< Trova server di pubblicazione Oracle>** dal **Publisher** elenco a discesa.  
  
5.  Connettersi al server di pubblicazione nella finestra di dialogo **Connetti a server** .  
  
6.  Selezionare una pubblicazione nella pagina **Pubblicazione** .  
  
7.  Completare i passaggi della Creazione guidata nuova sottoscrizione.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 È possibile creare sottoscrizioni pull a livello di programmazione tramite le stored procedure di replica. Le stored procedure utilizzate dipenderanno dal tipo di pubblicazione a cui appartiene la sottoscrizione.  
  
#### Per creare una sottoscrizione pull di una pubblicazione snapshot o transazionale  
  
1.  Nel server di pubblicazione, verificare che la pubblicazione supporta le sottoscrizioni pull eseguendo [sp_helppublication &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md).  
  
    -   Se il valore di **allow_pull** nel set di risultati è **1**, la pubblicazione supporta le sottoscrizioni pull.  
  
    -   Se il valore di **allow_pull** è **0**, eseguire [sp_changepublication &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), specificando **allow_pull** per **@property** e **true** per **@value**.  
  
2.  Il sottoscrittore, eseguire [sp_addpullsubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md). Specificare i parametri **@publisher** e **@publication**. Per informazioni sull'aggiornamento delle sottoscrizioni, vedere [creare una sottoscrizione aggiornabile di una pubblicazione transazionale](https://msdn.microsoft.com/library/ms152769.aspx).  
  
3.  Il sottoscrittore, eseguire [sp_addpullsubscription_agent &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md). Specificare le opzioni seguenti:  
  
    -   Il **@publisher**, **@publisher_db**, e **@publication** parametri.  
  
    -   Il [!INCLUDE[msCoName](../../includes/msconame-md.md)] le credenziali di Windows con cui viene eseguito l'agente di distribuzione nel Sottoscrittore per **@job_login** e **@job_password**.  
  
        > [!NOTE]  
        >  Le connessioni stabilite utilizzando sempre l'autenticazione integrata di Windows utilizzano le credenziali Windows specificate da **@job_login** e **@job_password**. L'agente di distribuzione attiva sempre la connessione locale al Sottoscrittore utilizzando l'autenticazione integrata di Windows. Per impostazione predefinita, l'agente si connetterà al server di distribuzione con l'autenticazione integrata di Windows.  
  
    -   (Facoltativo) Il valore **0** per **@distributor_security_mode** e le informazioni di accesso di SQL Server per **@distributor_login** e **@distributor_password**, se è necessario utilizzare l'autenticazione di SQL Server quando ci si connette al server di distribuzione.  
  
    -   Specificare una pianificazione per il processo dell'agente di distribuzione da eseguire per la sottoscrizione. Per altre informazioni, vedere [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md).  
  
4.  Server di pubblicazione, eseguire [sp_addsubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) Per registrare la sottoscrizione pull. Specificare **@publication**, **@subscriber**, e **@destination_db**. Specificare un valore di **pull** per **@subscription_type**.  
  
#### Per creare una sottoscrizione pull di una pubblicazione di tipo merge  
  
1.  Nel server di pubblicazione, verificare che la pubblicazione supporta le sottoscrizioni pull eseguendo [sp_helpmergepublication &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md).  
  
    -   Se il valore di **allow_pull** nel set di risultati è **1**, la pubblicazione supporta le sottoscrizioni pull.  
  
    -   Se il valore di **allow_pull** è **0**, eseguire [sp_changemergepublication &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), specificando **allow_pull** per **@property** e **true** per **@value**.  
  
2.  Il sottoscrittore, eseguire [sp_addmergepullsubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md). Specificare **@publisher**, **@publisher_db**, **@publication**, e i parametri seguenti:  
  
    -   **@subscriber_type** : specificare **locale** per una sottoscrizione client e **globale** per una sottoscrizione server.  
  
    -   **@subscription_priority** : specificare una priorità per la sottoscrizione (**0.00** a **99,99**). Questo parametro è obbligatorio solo per una sottoscrizione server.  
  
         Per altre informazioni, vedere [Advanced Merge Replication Conflict Detection and Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md).  
  
3.  Il sottoscrittore, eseguire [sp_addmergepullsubscription_agent &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md). Specificare i parametri seguenti:  
  
    -   **@publisher**, **@publisher_db**, e **@publication**.  
  
    -   Le credenziali di Windows con cui viene eseguito l'agente di Merge nel Sottoscrittore per **@job_login** e **@job_password**.  
  
        > [!NOTE]  
        >  Le connessioni stabilite utilizzando sempre l'autenticazione integrata di Windows utilizzano le credenziali Windows specificate da **@job_login** e **@job_password**. L'agente di merge attiva sempre la connessione locale al Sottoscrittore utilizzando l'autenticazione integrata di Windows. Per impostazione predefinita, l'agente si connetterà al database di distribuzione e al server di pubblicazione con l'autenticazione integrata di Windows.  
  
    -   (Facoltativo) Il valore **0** per **@distributor_security_mode** e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] informazioni di accesso per **@distributor_login** e **@distributor_password**, se è necessario utilizzare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione quando ci si connette al server di distribuzione.  
  
    -   (Facoltativo) Il valore **0** per **@publisher_security_mode** e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] informazioni di accesso per **@publisher_login** e **@publisher_password**, se è necessario utilizzare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione quando ci si connette al server di pubblicazione.  
  
    -   Una pianificazione per il processo dell'agente di merge per la sottoscrizione. Per ulteriori informazioni, vedere [creare una sottoscrizione aggiornabile di una pubblicazione transazionale](https://msdn.microsoft.com/library/ms152769.aspx).  
  
4.  Server di pubblicazione, eseguire [sp_addmergesubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md). Specificare **@publication**, **@subscriber**, **@subscriber_db**, e il valore **pull** per **@subscription_type**. In questo modo la sottoscrizione pull viene registrata.  
  
###  <a name="TsqlExample"></a> Esempi (Transact-SQL)  
 Nell'esempio seguente viene creata una sottoscrizione pull di una pubblicazione transazionale. Il primo batch viene eseguito nel Sottoscrittore e il secondo batch viene eseguito nel server di pubblicazione. I valori per l'account di accesso e la relativa password vengono specificati in fase di esecuzione tramite variabili di scripting sqlcmd.  
  
```  
-- This script uses sqlcmd scripting variables. They are in the form  
-- $(MyVariable). For information about how to use scripting variables    
-- on the command line and in SQL Server Management Studio, see the   
-- "Executing Replication Scripts" section in the topic  
-- "Programming Replication Using System Stored Procedures".  
  
-- Execute this batch at the Subscriber.  
DECLARE @publication AS sysname;  
DECLARE @publisher AS sysname;  
DECLARE @publicationDB AS sysname;  
SET @publication = N'AdvWorksProductTran';  
SET @publisher = $(PubServer);  
SET @publicationDB = N'AdventureWorks';  
  
-- At the subscription database, create a pull subscription   
-- to a transactional publication.  
USE [AdventureWorksReplica]  
EXEC sp_addpullsubscription   
  @publisher = @publisher,   
  @publication = @publication,   
  @publisher_db = @publicationDB;  
  
-- Add an agent job to synchronize the pull subscription.  
EXEC sp_addpullsubscription_agent   
  @publisher = @publisher,   
  @publisher_db = @publicationDB,   
  @publication = @publication,   
  @distributor = @publisher,   
  @job_login = $(Login),   
  @job_password = $(Password);  
GO  
```  
  
```  
-- This script uses sqlcmd scripting variables. They are in the form  
-- $(MyVariable). For information about how to use scripting variables    
-- on the command line and in SQL Server Management Studio, see the   
-- "Executing Replication Scripts" section in the topic  
-- "Programming Replication Using System Stored Procedures".  
  
-- Execute this batch at the Publisher.  
DECLARE @publication AS sysname;  
DECLARE @subscriber AS sysname;  
DECLARE @subscriptionDB AS sysname;  
SET @publication = N'AdvWorksProductTran';  
SET @subscriber = $(SubServer);  
SET @subscriptionDB = N'AdventureWorksReplica';  
  
-- At the Publisher, register the subscription, using the defaults.  
EXEC sp_addsubscription   
  @publication = @publication,   
  @subscriber = @subscriber,   
  @destination_db = @subscriptionDB,   
  @subscription_type = N'pull',  
  @status = N'subscribed';  
GO  
  
```  
  
 Nell'esempio seguente viene creata una sottoscrizione pull di una pubblicazione di tipo merge. Il primo batch viene eseguito nel Sottoscrittore e il secondo batch viene eseguito nel server di pubblicazione. I valori per l'account di accesso e la relativa password vengono specificati in fase di esecuzione tramite variabili di scripting **sqlcmd** .  
  
```  
-- This script uses sqlcmd scripting variables. They are in the form  
-- $(MyVariable). For information about how to use scripting variables    
-- on the command line and in SQL Server Management Studio, see the   
-- "Executing Replication Scripts" section in the topic  
-- "Programming Replication Using System Stored Procedures".  
  
-- Execute this batch at the Subscriber.  
DECLARE @publication AS sysname;  
DECLARE @publisher AS sysname;  
DECLARE @publicationDB AS sysname;  
DECLARE @hostname AS sysname;  
SET @publication = N'AdvWorksSalesOrdersMerge';  
SET @publisher = $(PubServer);  
SET @publicationDB = N'AdventureWorks';  
SET @hostname = N'adventure-works\david8';  
  
-- At the subscription database, create a pull subscription   
-- to a merge publication.  
USE [AdventureWorksReplica]  
EXEC sp_addmergepullsubscription   
  @publisher = @publisher,   
  @publication = @publication,   
  @publisher_db = @publicationDB;  
  
-- Add an agent job to synchronize the pull subscription.   
EXEC sp_addmergepullsubscription_agent   
  @publisher = @publisher,   
  @publisher_db = @publicationDB,   
  @publication = @publication,   
  @distributor = @publisher,   
  @job_login = $(Login),   
  @job_password = $(Password),  
  @hostname = @hostname;  
GO  
```  
  
```  
-- Execute this batch at the Publisher.  
DECLARE @myMergePub  AS sysname;  
DECLARE @mySub       AS sysname;  
DECLARE @mySubDB     AS sysname;  
  
SET @myMergePub = N'AdvWorksSalesOrdersMerge';  
SET @mySub = N'MYSUBSERVER';  
SET @mySubDB = N'AdventureWorksReplica';  
  
-- At the Publisher, register the subscription, using the defaults.  
USE [AdventureWorks]  
EXEC sp_addmergesubscription @publication = @myMergePub,   
@subscriber = @mySub, @subscriber_db = @mySubDB,   
@subscription_type = N'pull';  
GO  
```  
  
##  <a name="RMOProcedure"></a> Utilizzo di RMO (Replication Management Objects)  
 Le classi RMO utilizzate per la creazione di una sottoscrizione pull dipendono dal tipo di pubblicazione a cui appartiene la sottoscrizione.  
  
#### Per creare una sottoscrizione pull di una pubblicazione snapshot o transazionale  
  
1.  Creare connessioni per il sottoscrittore e il server di pubblicazione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.TransPublication> classe tramite la connessione server di pubblicazione dal passaggio 1. Specificare <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> e <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo. Se il metodo restituisce **false**, le proprietà specificate nel passaggio 2 non sono corrette oppure la pubblicazione non esiste nel server.  
  
4.  Eseguire un'operazione con AND logico bit per bit (**&** in Visual c# e **e** in Visual Basic) tra il <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> proprietà e <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPull>. Se il risultato è <xref:Microsoft.SqlServer.Replication.PublicationAttributes.None>, impostare <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> al risultato di un operatore logico OR bit per bit (**|** in Visual c# e **o** in Visual Basic) tra <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> e <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPull>. Quindi, chiamare <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> per abilitare le sottoscrizioni pull.  
  
5.  Se il database di sottoscrizione non esiste, crearlo utilizzando la <xref:Microsoft.SqlServer.Management.Smo.Database> (classe). Per ulteriori informazioni, vedere [creazione, modifica e rimozione di database](../../relational-databases/server-management-objects-smo/tasks/creating-altering-and-removing-databases.md).  
  
6.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.TransPullSubscription> (classe).  
  
7.  Impostare le proprietà seguenti per la sottoscrizione:  
  
    -   Il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> al sottoscrittore creata nel passaggio 1 per <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
    -   Nome del database di sottoscrizione per <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>.  
  
    -   Nome del server di pubblicazione per <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>.  
  
    -   Nome del database di pubblicazione per <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>.  
  
    -   Nome della pubblicazione per <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>.  
  
    -   Il <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> e <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> o <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword%2A> i campi di <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A> per fornire le credenziali per il [!INCLUDE[msCoName](../../includes/msconame-md.md)] account Windows con cui viene eseguito l'agente di distribuzione nel Sottoscrittore. Questo account viene utilizzato per attivare connessioni locali al Sottoscrittore e stabilire connessioni remote con l'autenticazione di Windows.  
  
        > [!NOTE]  
        >  L'impostazione <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A> non è richiesto per la creazione della sottoscrizione da un membro del **sysadmin** ruolo predefinito del server, tuttavia, è consigliabile. In questo caso l'agente rappresenterà l'account di SQL Server Agent. Per altre informazioni, vedere [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
    -   (Facoltativo) Il valore **true** per <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> per creare un processo dell'agente che viene utilizzato per sincronizzare la sottoscrizione. Se si specifica **false** (impostazione predefinita), la sottoscrizione può essere sincronizzata solo a livello di codice e specificare proprietà aggiuntive di <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent> quando l'accesso all'oggetto dal <xref:Microsoft.SqlServer.Replication.TransPullSubscription.SynchronizationAgent%2A> proprietà. Per altre informazioni, vedere [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
        > [!NOTE]  
        >  SQL Server Agent non è disponibile in tutte le edizioni di [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per un elenco delle funzionalità supportate dalle edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Funzionalità supportate dalle edizioni di SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md). Se si specifica il valore **true** per Sottoscrittori SQL Server Express, il processo agente non viene creato. Tuttavia, i metadati importanti correlati alla sottoscrizione vengono archiviati nel Sottoscrittore.  
  
    -   (Facoltativo) Impostare il <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> e <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> o <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> i campi di <xref:Microsoft.SqlServer.Replication.PullSubscription.DistributorSecurity%2A> quando si utilizza l'autenticazione di SQL Server per connettersi al server di distribuzione.  
  
8.  Chiamare il <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> metodo.  
  
9. Utilizzando l'istanza del <xref:Microsoft.SqlServer.Replication.TransPublication> classe dal passaggio 2, chiamata di <xref:Microsoft.SqlServer.Replication.TransPublication.MakePullSubscriptionWellKnown%2A> metodo per registrare la sottoscrizione pull nel server di pubblicazione. Se la registrazione esiste già, viene generata un'eccezione.  
  
#### Per creare una sottoscrizione pull di una pubblicazione di tipo merge  
  
1.  Creare connessioni per il sottoscrittore e il server di pubblicazione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.MergePublication> classe tramite la connessione server di pubblicazione dal passaggio 1. Specificare <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>, e <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo. Se il metodo restituisce **false**, le proprietà specificate nel passaggio 2 non sono corrette oppure la pubblicazione non esiste nel server.  
  
4.  Eseguire un'operazione con AND logico bit per bit (**&** in Visual c# e **e** in Visual Basic) tra il <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> proprietà e <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPull>. Se il risultato è <xref:Microsoft.SqlServer.Replication.PublicationAttributes.None>, impostare <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> al risultato di un operatore logico OR bit per bit (**|** in Visual c# e **o** in Visual Basic) tra <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> e <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPull>. Quindi, chiamare <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> per abilitare le sottoscrizioni pull.  
  
5.  Se il database di sottoscrizione non esiste, crearlo utilizzando la <xref:Microsoft.SqlServer.Management.Smo.Database> (classe). Per ulteriori informazioni, vedere [creazione, modifica e rimozione di database](../../relational-databases/server-management-objects-smo/tasks/creating-altering-and-removing-databases.md).  
  
6.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.MergePullSubscription> (classe).  
  
7.  Impostare le proprietà seguenti per la sottoscrizione:  
  
    -   Il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> al sottoscrittore creata nel passaggio 1 per <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
    -   Nome del database di sottoscrizione per <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>.  
  
    -   Nome del server di pubblicazione per <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>.  
  
    -   Nome del database di pubblicazione per <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>.  
  
    -   Nome della pubblicazione per <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>.  
  
    -   Il <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> e <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> o <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword%2A> i campi di <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A> per fornire le credenziali per il [!INCLUDE[msCoName](../../includes/msconame-md.md)] account Windows con cui viene eseguito l'agente di Merge nel Sottoscrittore. Questo account viene utilizzato per attivare connessioni locali al Sottoscrittore e stabilire connessioni remote con l'autenticazione di Windows.  
  
        > [!NOTE]  
        >  L'impostazione <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A> non è richiesto per la creazione della sottoscrizione da un membro del **sysadmin** ruolo predefinito del server, tuttavia, è consigliabile. In questo caso l'agente rappresenterà l'account di SQL Server Agent. Per altre informazioni, vedere [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
    -   (Facoltativo) Il valore **true** per <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> per creare un processo dell'agente che viene utilizzato per sincronizzare la sottoscrizione. Se si specifica **false** (impostazione predefinita), la sottoscrizione può essere sincronizzata solo a livello di codice e specificare proprietà aggiuntive di <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent> quando l'accesso all'oggetto dal <xref:Microsoft.SqlServer.Replication.MergePullSubscription.SynchronizationAgent%2A> proprietà. Per altre informazioni, vedere [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
    -   (Facoltativo) Impostare il <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> e <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> o <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> i campi di <xref:Microsoft.SqlServer.Replication.PullSubscription.DistributorSecurity%2A> quando si utilizza l'autenticazione di SQL Server per connettersi al server di distribuzione.  
  
    -   (Facoltativo) Impostare il <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> e <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> o <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> i campi di <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherSecurity%2A> quando si utilizza l'autenticazione di SQL Server per connettersi al server di pubblicazione.  
  
8.  Chiamare il <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> metodo.  
  
9. Utilizzando l'istanza del <xref:Microsoft.SqlServer.Replication.MergePublication> classe dal passaggio 2, chiamata di <xref:Microsoft.SqlServer.Replication.MergePublication.MakePullSubscriptionWellKnown%2A> metodo per registrare la sottoscrizione pull nel server di pubblicazione. Se la registrazione esiste già, viene generata un'eccezione.  
  
###  <a name="PShellExample"></a> Esempio (RMO)  
 In questo esempio viene creata una sottoscrizione pull di una pubblicazione transazionale. Le credenziali dell'account di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows utilizzate per creare il processo dell'agente di distribuzione vengono passate in fase di esecuzione.  
  
```csharp  
// Define the Publisher, publication, and databases.  
string publicationName = "AdvWorksProductTran";  
string publisherName = publisherInstance;  
string subscriberName = subscriberInstance;  
string subscriptionDbName = "AdventureWorksReplica";  
string publicationDbName = "AdventureWorks";  
  
//Create connections to the Publisher and Subscriber.  
ServerConnection subscriberConn = new ServerConnection(subscriberName);  
ServerConnection publisherConn = new ServerConnection(publisherName);  
  
// Create the objects that we need.  
TransPublication publication;  
TransPullSubscription subscription;  
  
try  
{  
    // Connect to the Publisher and Subscriber.  
    subscriberConn.Connect();  
    publisherConn.Connect();  
  
    // Ensure that the publication exists and that   
    // it supports pull subscriptions.  
    publication = new TransPublication();  
    publication.Name = publicationName;  
    publication.DatabaseName = publicationDbName;  
    publication.ConnectionContext = publisherConn;  
  
    if (publication.IsExistingObject)  
    {  
        if ((publication.Attributes & PublicationAttributes.AllowPull) == 0)  
        {  
            publication.Attributes |= PublicationAttributes.AllowPull;  
        }  
  
        // Define the pull subscription.  
        subscription = new TransPullSubscription();  
        subscription.ConnectionContext = subscriberConn;  
        subscription.PublisherName = publisherName;  
        subscription.PublicationName = publicationName;  
        subscription.PublicationDBName = publicationDbName;  
        subscription.DatabaseName = subscriptionDbName;  
  
        // Specify the Windows login credentials for the Distribution Agent job.  
        subscription.SynchronizationAgentProcessSecurity.Login = winLogin;  
        subscription.SynchronizationAgentProcessSecurity.Password = winPassword;  
  
        // Make sure that the agent job for the subscription is created.  
        subscription.CreateSyncAgentByDefault = true;  
  
        // By default, subscriptions to transactional publications are synchronized   
        // continuously, but in this case we only want to synchronize on demand.  
        subscription.AgentSchedule.FrequencyType = ScheduleFrequencyType.OnDemand;  
  
        // Create the pull subscription at the Subscriber.  
        subscription.Create();  
  
        Boolean registered = false;  
  
        // Verify that the subscription is not already registered.  
        foreach (TransSubscription existing  
            in publication.EnumSubscriptions())  
        {  
            if (existing.SubscriberName == subscriberName  
                && existing.SubscriptionDBName == subscriptionDbName)  
            {  
                registered = true;  
            }  
        }  
        if (!registered)  
        {  
            // Register the subscription with the Publisher.  
            publication.MakePullSubscriptionWellKnown(  
                subscriberName, subscriptionDbName,  
                SubscriptionSyncType.Automatic,  
                TransSubscriberType.ReadOnly);  
        }  
    }  
    else  
    {  
        // Do something here if the publication does not exist.  
        throw new ApplicationException(String.Format(  
            "The publication '{0}' does not exist on {1}.",  
            publicationName, publisherName));  
    }  
}  
catch (Exception ex)  
{  
    // Implement the appropriate error handling here.  
    throw new ApplicationException(String.Format(  
        "The subscription to {0} could not be created.", publicationName), ex);  
}  
finally  
{  
    subscriberConn.Disconnect();  
    publisherConn.Disconnect();  
}  
  
```  
  
```vb  
' Define the Publisher, publication, and databases.  
Dim publicationName As String = "AdvWorksProductTran"  
Dim publisherName As String = publisherInstance  
Dim subscriberName As String = subscriberInstance  
Dim subscriptionDbName As String = "AdventureWorksReplica"  
Dim publicationDbName As String = "AdventureWorks"  
  
'Create connections to the Publisher and Subscriber.  
Dim subscriberConn As ServerConnection = New ServerConnection(subscriberName)  
Dim publisherConn As ServerConnection = New ServerConnection(publisherName)  
  
' Create the objects that we need.  
Dim publication As TransPublication  
Dim subscription As TransPullSubscription  
  
Try  
    ' Connect to the Publisher and Subscriber.  
    subscriberConn.Connect()  
    publisherConn.Connect()  
  
    ' Ensure that the publication exists and that   
    ' it supports pull subscriptions.  
    publication = New TransPublication()  
    publication.Name = publicationName  
    publication.DatabaseName = publicationDbName  
    publication.ConnectionContext = publisherConn  
  
    If publication.IsExistingObject Then  
        If (publication.Attributes And PublicationAttributes.AllowPull) = 0 Then  
            publication.Attributes = publication.Attributes _  
            Or PublicationAttributes.AllowPull  
        End If  
  
        ' Define the pull subscription.  
        subscription = New TransPullSubscription()  
        subscription.ConnectionContext = subscriberConn  
        subscription.PublisherName = publisherName  
        subscription.PublicationName = publicationName  
        subscription.PublicationDBName = publicationDbName  
        subscription.DatabaseName = subscriptionDbName  
        subscription.Description = "Pull subscription to " + publicationDbName _  
        + " on " + subscriberName + "."  
  
        ' Specify the Windows login credentials for the Distribution Agent job.  
        subscription.SynchronizationAgentProcessSecurity.Login = winLogin  
        subscription.SynchronizationAgentProcessSecurity.Password = winPassword  
  
        ' Make sure that the agent job for the subscription is created.  
        subscription.CreateSyncAgentByDefault = True  
  
        ' By default, subscriptions to transactional publications are synchronized   
        ' continuously, but in this case we only want to synchronize on demand.  
        subscription.AgentSchedule.FrequencyType = ScheduleFrequencyType.OnDemand  
  
        ' Create the pull subscription at the Subscriber.  
        subscription.Create()  
  
        Dim registered As Boolean = False  
  
        ' Verify that the subscription is not already registered.  
        For Each existing As TransSubscription In publication.EnumSubscriptions()  
            If existing.SubscriberName = subscriberName And _  
                existing.SubscriptionDBName = subscriptionDbName Then  
                registered = True  
            End If  
        Next existing  
        If Not registered Then  
            ' Register the subscription with the Publisher.  
            publication.MakePullSubscriptionWellKnown( _  
             subscriberName, subscriptionDbName, _  
             SubscriptionSyncType.Automatic, _  
             TransSubscriberType.ReadOnly)  
        End If  
    Else  
        ' Do something here if the publication does not exist.  
        Throw New ApplicationException(String.Format( _  
         "The publication '{0}' does not exist on {1}.", _  
         publicationName, publisherName))  
    End If  
Catch ex As Exception  
    ' Implement the appropriate error handling here.  
    Throw New ApplicationException(String.Format( _  
        "The subscription to {0} could not be created.", publicationName), ex)  
Finally  
    subscriberConn.Disconnect()  
    publisherConn.Disconnect()  
End Try  
  
```  
  
 In questo esempio viene creata una sottoscrizione pull di una pubblicazione di tipo merge. Le credenziali dell'account di Windows utilizzate per creare il processo dell'agente di merge vengono passate in fase di esecuzione.  
  
```cpp#  
// Define the Publisher, publication, and databases.  
string publicationName = "AdvWorksSalesOrdersMerge";  
string publisherName = publisherInstance;  
string subscriberName = subscriberInstance;  
string subscriptionDbName = "AdventureWorksReplica";  
string publicationDbName = "AdventureWorks";  
string hostname = @"adventure-works\garrett1";  
  
//Create connections to the Publisher and Subscriber.  
ServerConnection subscriberConn = new ServerConnection(subscriberName);  
ServerConnection publisherConn = new ServerConnection(publisherName);  
  
// Create the objects that we need.  
MergePublication publication;  
MergePullSubscription subscription;  
  
try  
{  
    // Connect to the Subscriber.  
    subscriberConn.Connect();  
  
    // Ensure that the publication exists and that   
    // it supports pull subscriptions.  
    publication = new MergePublication();  
    publication.Name = publicationName;  
    publication.DatabaseName = publicationDbName;  
    publication.ConnectionContext = publisherConn;  
  
    if (publication.LoadProperties())  
    {  
        if ((publication.Attributes & PublicationAttributes.AllowPull) == 0)  
        {  
            publication.Attributes |= PublicationAttributes.AllowPull;  
        }  
  
        // Define the pull subscription.  
        subscription = new MergePullSubscription();  
        subscription.ConnectionContext = subscriberConn;  
        subscription.PublisherName = publisherName;  
        subscription.PublicationName = publicationName;  
        subscription.PublicationDBName = publicationDbName;  
        subscription.DatabaseName = subscriptionDbName;  
        subscription.HostName = hostname;  
  
        // Specify the Windows login credentials for the Merge Agent job.  
        subscription.SynchronizationAgentProcessSecurity.Login = winLogin;  
        subscription.SynchronizationAgentProcessSecurity.Password = winPassword;  
  
        // Make sure that the agent job for the subscription is created.  
        subscription.CreateSyncAgentByDefault = true;  
  
        // Create the pull subscription at the Subscriber.  
        subscription.Create();  
  
        Boolean registered = false;  
  
        // Verify that the subscription is not already registered.  
        foreach (MergeSubscription existing  
            in publication.EnumSubscriptions())  
        {  
            if (existing.SubscriberName == subscriberName  
                && existing.SubscriptionDBName == subscriptionDbName  
                && existing.SubscriptionType == SubscriptionOption.Pull)  
            {  
                registered = true;  
            }  
        }  
        if (!registered)  
        {  
            // Register the local subscription with the Publisher.  
            publication.MakePullSubscriptionWellKnown(  
                subscriberName, subscriptionDbName,  
                SubscriptionSyncType.Automatic,  
                MergeSubscriberType.Local, 0);  
        }  
    }  
    else  
    {  
        // Do something here if the publication does not exist.  
        throw new ApplicationException(String.Format(  
            "The publication '{0}' does not exist on {1}.",  
            publicationName, publisherName));  
    }  
}  
catch (Exception ex)  
{  
    // Implement the appropriate error handling here.  
    throw new ApplicationException(String.Format(  
        "The subscription to {0} could not be created.", publicationName), ex);  
}  
finally  
{  
    subscriberConn.Disconnect();  
    publisherConn.Disconnect();  
}  
  
```  
  
```vb  
' Define the Publisher, publication, and databases.  
Dim publicationName As String = "AdvWorksSalesOrdersMerge"  
Dim publisherName As String = publisherInstance  
Dim subscriberName As String = subscriberInstance  
Dim subscriptionDbName As String = "AdventureWorksReplica"  
Dim publicationDbName As String = "AdventureWorks"  
Dim hostname As String = "adventure-works\garrett1"  
  
'Create connections to the Publisher and Subscriber.  
Dim subscriberConn As ServerConnection = New ServerConnection(subscriberName)  
Dim publisherConn As ServerConnection = New ServerConnection(publisherName)  
  
' Create the objects that we need.  
Dim publication As MergePublication  
Dim subscription As MergePullSubscription  
  
Try  
    ' Connect to the Subscriber.  
    subscriberConn.Connect()  
  
    ' Ensure that the publication exists and that   
    ' it supports pull subscriptions.  
    publication = New MergePublication()  
    publication.Name = publicationName  
    publication.DatabaseName = publicationDbName  
    publication.ConnectionContext = publisherConn  
  
    If publication.LoadProperties() Then  
        If (publication.Attributes And PublicationAttributes.AllowPull) = 0 Then  
            publication.Attributes = publication.Attributes _  
            Or PublicationAttributes.AllowPull  
        End If  
  
        ' Define the pull subscription.  
        subscription = New MergePullSubscription()  
        subscription.ConnectionContext = subscriberConn  
        subscription.PublisherName = publisherName  
        subscription.PublicationName = publicationName  
        subscription.PublicationDBName = publicationDbName  
        subscription.DatabaseName = subscriptionDbName  
        subscription.HostName = hostname  
  
        ' Specify the Windows login credentials for the Merge Agent job.  
        subscription.SynchronizationAgentProcessSecurity.Login = winLogin  
        subscription.SynchronizationAgentProcessSecurity.Password = winPassword  
  
        ' Make sure that the agent job for the subscription is created.  
        subscription.CreateSyncAgentByDefault = True  
  
        ' Create the pull subscription at the Subscriber.  
        subscription.Create()  
  
        Dim registered As Boolean = False  
  
        ' Verify that the subscription is not already registered.  
        For Each existing As MergeSubscription In _  
        publication.EnumSubscriptions()  
            If existing.SubscriberName = subscriberName Then  
                registered = True  
            End If  
        Next  
        If Not registered Then  
            ' Register the local subscription with the Publisher.  
            publication.MakePullSubscriptionWellKnown( _  
             subscriberName, subscriptionDbName, _  
             SubscriptionSyncType.Automatic, _  
             MergeSubscriberType.Local, 0)  
        End If  
    Else  
        ' Do something here if the publication does not exist.  
        Throw New ApplicationException(String.Format( _  
         "The publication '{0}' does not exist on {1}.", _  
         publicationName, publisherName))  
    End If  
Catch ex As Exception  
    ' Implement the appropriate error handling here.  
    Throw New ApplicationException(String.Format( _  
        "The subscription to {0} could not be created.", publicationName), ex)  
Finally  
    subscriberConn.Disconnect()  
    publisherConn.Disconnect()  
End Try  
```  
  
 In questo esempio viene creata una sottoscrizione pull di una pubblicazione di tipo merge senza creare i metadati di processo e sottoscrizione di un agente associato in [MSsubscription_properties](../../relational-databases/system-tables/mssubscription-properties-transact-sql.md). Le credenziali dell'account di Windows utilizzate per creare il processo dell'agente di merge vengono passate in fase di esecuzione.  
  
```csharp  
// Define the Publisher, publication, and databases.  
string publicationName = "AdvWorksSalesOrdersMerge";  
string publisherName = publisherInstance;  
string subscriberName = subscriberInstance;  
string subscriptionDbName = "AdventureWorksReplica";  
string publicationDbName = "AdventureWorks";  
  
//Create connections to the Publisher and Subscriber.  
ServerConnection subscriberConn = new ServerConnection(subscriberName);  
ServerConnection publisherConn = new ServerConnection(publisherName);  
  
// Create the objects that we need.  
MergePublication publication;  
MergePullSubscription subscription;  
  
try  
{  
    // Connect to the Subscriber.  
    subscriberConn.Connect();  
  
    // Ensure that the publication exists and that   
    // it supports pull subscriptions.  
    publication = new MergePublication();  
    publication.Name = publicationName;  
    publication.DatabaseName = publicationDbName;  
    publication.ConnectionContext = publisherConn;  
  
    if (publication.LoadProperties())  
    {  
        if ((publication.Attributes & PublicationAttributes.AllowPull) == 0)  
        {  
            publication.Attributes |= PublicationAttributes.AllowPull;  
        }  
  
        // Define the pull subscription.  
        subscription = new MergePullSubscription();  
        subscription.ConnectionContext = subscriberConn;  
        subscription.PublisherName = publisherName;  
        subscription.PublicationName = publicationName;  
        subscription.PublicationDBName = publicationDbName;  
        subscription.DatabaseName = subscriptionDbName;  
  
        // Specify that an agent job not be created for this subscription. The  
        // subscription can only be synchronized by running the Merge Agent directly.  
        // Subscripition metadata stored in MSsubscription_properties will not  
        // be available and must be specified at run time.  
        subscription.CreateSyncAgentByDefault = false;  
  
        // Create the pull subscription at the Subscriber.  
        subscription.Create();  
  
        Boolean registered = false;  
  
        // Verify that the subscription is not already registered.  
        foreach (MergeSubscription existing  
            in publication.EnumSubscriptions())  
        {  
            if (existing.SubscriberName == subscriberName  
                && existing.SubscriptionDBName == subscriptionDbName  
                && existing.SubscriptionType == SubscriptionOption.Pull)  
            {  
                registered = true;  
            }  
        }  
        if (!registered)  
        {  
            // Register the local subscription with the Publisher.  
            publication.MakePullSubscriptionWellKnown(  
                subscriberName, subscriptionDbName,  
                SubscriptionSyncType.Automatic,  
                MergeSubscriberType.Local, 0);  
        }  
    }  
    else  
    {  
        // Do something here if the publication does not exist.  
        throw new ApplicationException(String.Format(  
            "The publication '{0}' does not exist on {1}.",  
            publicationName, publisherName));  
    }  
}  
catch (Exception ex)  
{  
    // Implement the appropriate error handling here.  
    throw new ApplicationException(String.Format(  
        "The subscription to {0} could not be created.", publicationName), ex);  
}  
finally  
{  
    subscriberConn.Disconnect();  
    publisherConn.Disconnect();  
}  
```  
  
```vb  
' Define the Publisher, publication, and databases.  
Dim publicationName As String = "AdvWorksSalesOrdersMerge"  
Dim publisherName As String = publisherInstance  
Dim subscriberName As String = subscriberInstance  
Dim subscriptionDbName As String = "AdventureWorksReplica"  
Dim publicationDbName As String = "AdventureWorks"  
  
'Create connections to the Publisher and Subscriber.  
Dim subscriberConn As ServerConnection = New ServerConnection(subscriberName)  
Dim publisherConn As ServerConnection = New ServerConnection(publisherName)  
  
' Create the objects that we need.  
Dim publication As MergePublication  
Dim subscription As MergePullSubscription  
  
Try  
    ' Connect to the Subscriber.  
    subscriberConn.Connect()  
  
    ' Ensure that the publication exists and that   
    ' it supports pull subscriptions.  
    publication = New MergePublication()  
    publication.Name = publicationName  
    publication.DatabaseName = publicationDbName  
    publication.ConnectionContext = publisherConn  
  
    If publication.LoadProperties() Then  
        If (publication.Attributes And PublicationAttributes.AllowPull) = 0 Then  
            publication.Attributes = publication.Attributes _  
            Or PublicationAttributes.AllowPull  
        End If  
  
        ' Define the pull subscription.  
        subscription = New MergePullSubscription()  
        subscription.ConnectionContext = subscriberConn  
        subscription.PublisherName = publisherName  
        subscription.PublicationName = publicationName  
        subscription.PublicationDBName = publicationDbName  
        subscription.DatabaseName = subscriptionDbName  
  
        ' Specify that an agent job not be created for this subscription. The  
        ' subscription can only be synchronized by running the Merge Agent directly.  
        ' Subscripition metadata stored in MSsubscription_properties will not  
        ' be available and must be specified at run time.  
        subscription.CreateSyncAgentByDefault = False  
  
        ' Create the pull subscription at the Subscriber.  
        subscription.Create()  
  
        Dim registered As Boolean = False  
  
        ' Verify that the subscription is not already registered.  
        For Each existing As MergeSubscription In _  
        publication.EnumSubscriptions()  
            If existing.SubscriberName = subscriberName Then  
                registered = True  
            End If  
        Next  
        If Not registered Then  
            ' Register the local subscription with the Publisher.  
            publication.MakePullSubscriptionWellKnown( _  
             subscriberName, subscriptionDbName, _  
             SubscriptionSyncType.Automatic, _  
             MergeSubscriberType.Local, 0)  
        End If  
    Else  
        ' Do something here if the publication does not exist.  
        Throw New ApplicationException(String.Format( _  
         "The publication '{0}' does not exist on {1}.", _  
         publicationName, publisherName))  
    End If  
Catch ex As Exception  
    ' Implement the appropriate error handling here.  
    Throw New ApplicationException(String.Format( _  
     "The subscription to {0} could not be created.", publicationName), ex)  
Finally  
    subscriberConn.Disconnect()  
    publisherConn.Disconnect()  
End Try  
```  
  
 In questo esempio viene creata una sottoscrizione pull di una pubblicazione di tipo merge che può essere sincronizzata su Internet con la sincronizzazione Web. Le credenziali dell'account di Windows utilizzate per creare il processo dell'agente di merge vengono passate in fase di esecuzione. Per altre informazioni, vedere [Configure Web Synchronization](../../relational-databases/replication/configure-web-synchronization.md).  
  
```csharp  
// Define the Publisher, publication, and databases.  
string publicationName = "AdvWorksSalesOrdersMerge";  
string publisherName = publisherInstance;  
string subscriberName = subscriberInstance;  
string subscriptionDbName = "AdventureWorksReplica";  
string publicationDbName = "AdventureWorks";  
string hostname = @"adventure-works\garrett1";  
string webSyncUrl = "https://" + publisherInstance + "/WebSync/replisapi.dll";  
  
//Create connections to the Publisher and Subscriber.  
ServerConnection subscriberConn = new ServerConnection(subscriberName);  
ServerConnection publisherConn = new ServerConnection(publisherName);  
  
// Create the objects that we need.  
MergePublication publication;  
MergePullSubscription subscription;  
  
try  
{  
    // Connect to the Subscriber.  
    subscriberConn.Connect();  
  
    // Ensure that the publication exists and that   
    // it supports pull subscriptions and Web synchronization.  
    publication = new MergePublication();  
    publication.Name = publicationName;  
    publication.DatabaseName = publicationDbName;  
    publication.ConnectionContext = publisherConn;  
  
    if (publication.LoadProperties())  
    {  
        if ((publication.Attributes & PublicationAttributes.AllowPull) == 0)  
        {  
            publication.Attributes |= PublicationAttributes.AllowPull;  
        }  
        if ((publication.Attributes & PublicationAttributes.AllowWebSynchronization) == 0)  
        {  
            publication.Attributes |= PublicationAttributes.AllowWebSynchronization;  
        }  
  
        // Define the pull subscription.  
        subscription = new MergePullSubscription();  
        subscription.ConnectionContext = subscriberConn;  
        subscription.PublisherName = publisherName;  
        subscription.PublicationName = publicationName;  
        subscription.PublicationDBName = publicationDbName;  
        subscription.DatabaseName = subscriptionDbName;  
        subscription.HostName = hostname;  
  
        // Specify the Windows login credentials for the Merge Agent job.  
        subscription.SynchronizationAgentProcessSecurity.Login = winLogin;  
        subscription.SynchronizationAgentProcessSecurity.Password = winPassword;  
  
        // Enable Web synchronization.  
        subscription.UseWebSynchronization = true;  
        subscription.InternetUrl = webSyncUrl;  
  
        // Specify the same Windows credentials to use when connecting to the  
        // Web server using HTTPS Basic Authentication.  
        subscription.InternetSecurityMode = AuthenticationMethod.BasicAuthentication;  
        subscription.InternetLogin = winLogin;  
        subscription.InternetPassword = winPassword;  
  
        // Ensure that we create a job for this subscription.  
        subscription.CreateSyncAgentByDefault = true;  
  
        // Create the pull subscription at the Subscriber.  
        subscription.Create();  
  
        Boolean registered = false;  
  
        // Verify that the subscription is not already registered.  
        foreach (MergeSubscription existing  
            in publication.EnumSubscriptions())  
        {  
            if (existing.SubscriberName == subscriberName  
                && existing.SubscriptionDBName == subscriptionDbName  
                && existing.SubscriptionType == SubscriptionOption.Pull)  
            {  
                registered = true;  
            }  
        }  
        if (!registered)  
        {  
            // Register the local subscription with the Publisher.  
            publication.MakePullSubscriptionWellKnown(  
                subscriberName, subscriptionDbName,  
                SubscriptionSyncType.Automatic,  
                MergeSubscriberType.Local, 0);  
        }  
    }  
    else  
    {  
        // Do something here if the publication does not exist.  
        throw new ApplicationException(String.Format(  
            "The publication '{0}' does not exist on {1}.",  
            publicationName, publisherName));  
    }  
}  
catch (Exception ex)  
{  
    // Implement the appropriate error handling here.  
    throw new ApplicationException(String.Format(  
        "The subscription to {0} could not be created.", publicationName), ex);  
}  
finally  
{  
    subscriberConn.Disconnect();  
    publisherConn.Disconnect();  
}  
```  
  
```vb  
' Define the Publisher, publication, and databases.  
Dim publicationName As String = "AdvWorksSalesOrdersMerge"  
Dim publisherName As String = publisherInstance  
Dim subscriberName As String = subscriberInstance  
Dim subscriptionDbName As String = "AdventureWorksReplica"  
Dim publicationDbName As String = "AdventureWorks"  
Dim hostname As String = "adventure-works\garrett1"  
Dim webSyncUrl As String = "https://" + publisherInstance + "/WebSync/replisapi.dll"  
  
'Create connections to the Publisher and Subscriber.  
Dim subscriberConn As ServerConnection = New ServerConnection(subscriberName)  
Dim publisherConn As ServerConnection = New ServerConnection(publisherName)  
  
' Create the objects that we need.  
Dim publication As MergePublication  
Dim subscription As MergePullSubscription  
  
Try  
    ' Connect to the Subscriber.  
    subscriberConn.Connect()  
  
    ' Ensure that the publication exists and that   
    ' it supports pull subscriptions and Web synchronization.  
    publication = New MergePublication()  
    publication.Name = publicationName  
    publication.DatabaseName = publicationDbName  
    publication.ConnectionContext = publisherConn  
  
    If publication.LoadProperties() Then  
        If (publication.Attributes And PublicationAttributes.AllowPull) = 0 Then  
            publication.Attributes = publication.Attributes _  
            Or PublicationAttributes.AllowPull  
        End If  
        If (publication.Attributes And PublicationAttributes.AllowWebSynchronization) = 0 Then  
            publication.Attributes = publication.Attributes _  
            Or PublicationAttributes.AllowWebSynchronization  
        End If  
  
        ' Define the pull subscription.  
        subscription = New MergePullSubscription()  
        subscription.ConnectionContext = subscriberConn  
        subscription.PublisherName = publisherName  
        subscription.PublicationName = publicationName  
        subscription.PublicationDBName = publicationDbName  
        subscription.DatabaseName = subscriptionDbName  
        subscription.HostName = hostname  
        subscription.CreateSyncAgentByDefault = True  
  
        ' Specify the Windows login credentials for the Merge Agent job.  
        subscription.SynchronizationAgentProcessSecurity.Login = winLogin  
        subscription.SynchronizationAgentProcessSecurity.Password = winPassword  
  
        ' Enable Web synchronization.  
        subscription.UseWebSynchronization = True  
        subscription.InternetUrl = webSyncUrl  
  
        ' Specify the same Windows credentials to use when connecting to the  
        ' Web server using HTTPS Basic Authentication.  
        subscription.InternetSecurityMode = AuthenticationMethod.BasicAuthentication  
        subscription.InternetLogin = winLogin  
        subscription.InternetPassword = winPassword  
  
        ' Create the pull subscription at the Subscriber.  
        subscription.Create()  
  
        Dim registered As Boolean = False  
  
        ' Verify that the subscription is not already registered.  
        For Each existing As MergeSubscription In _  
        publication.EnumSubscriptions()  
            If existing.SubscriberName = subscriberName Then  
                registered = True  
            End If  
        Next  
        If Not registered Then  
            ' Register the local subscription with the Publisher.  
            publication.MakePullSubscriptionWellKnown( _  
             subscriberName, subscriptionDbName, _  
             SubscriptionSyncType.Automatic, _  
             MergeSubscriberType.Local, 0)  
        End If  
    Else  
        ' Do something here if the publication does not exist.  
        Throw New ApplicationException(String.Format( _  
         "The publication '{0}' does not exist on {1}.", _  
         publicationName, publisherName))  
    End If  
Catch ex As Exception  
    ' Implement the appropriate error handling here.  
    Throw New ApplicationException(String.Format( _  
     "The subscription to {0} could not be created.", publicationName), ex)  
Finally  
    subscriberConn.Disconnect()  
    publisherConn.Disconnect()  
End Try  
```  
  
## Vedere anche  
 [Concetti di base relativi a RMO (Replication Management Objects)](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Visualizzazione e modifica delle proprietà delle sottoscrizioni pull](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [Configurazione della sincronizzazione Web](../../relational-databases/replication/configure-web-synchronization.md)   
 [Sottoscrizione delle pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)   
 [Procedure consigliate per la sicurezza della replica](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  