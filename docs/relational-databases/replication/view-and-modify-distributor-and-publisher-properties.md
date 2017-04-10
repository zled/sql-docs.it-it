---
title: "Visualizzazione e modifica delle propriet&#224; del server di pubblicazione e del database di distribuzione | Microsoft Docs"
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
  - "viewing replication properties"
  - "Distributors [SQL Server replication], modifying"
  - "modifying replication properties, Distributors"
  - "database di distribuzione [replica di SQL Server], proprietà"
ms.assetid: 5dae1d59-c377-4c6e-adc9-b68c5b328f79
caps.latest.revision: 43
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 43
---
# Visualizzazione e modifica delle propriet&#224; del server di pubblicazione e del database di distribuzione
  In questo argomento viene descritto come visualizzare e modificare le proprietà del database di distribuzione e del server di pubblicazione in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] o RMO (Replication Management Objects).  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Indicazioni](#Recommendations)  
  
     [Sicurezza](#Security)  
  
-   **Per visualizzare e modificare le proprietà di server di pubblicazione e database di distribuzione, utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Oggetti RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Recommendations"></a> Indicazioni  
  
-   Per i server di pubblicazione che eseguono versioni precedenti a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], un utente nel ruolo predefinito del server **sysadmin** può registrare i Sottoscrittori nella pagina **Sottoscrittori** . A partire da [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]non è più necessario registrare esplicitamente i Sottoscrittori per la replica.  
  
###  <a name="Security"></a> Sicurezza  
 Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### Per visualizzare e modificare le proprietà del database di distribuzione  
  
1.  Connettersi al database di distribuzione in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], quindi espandere il nodo del server.  
  
2.  Pulsante destro del mouse il **replica** cartella e quindi fare clic su **proprietà server di distribuzione**.  
  
3.  Visualizzare e modificare le proprietà di **proprietà server di distribuzione - \< distributore>** la finestra di dialogo.  
  
    -   Per visualizzare e modificare le proprietà per un database di distribuzione, fare clic sul pulsante delle proprietà (**...**) per il database sul **Generale** pagina della finestra di dialogo casella.  
  
    -   Per visualizzare e modificare le proprietà del server di pubblicazione associate al server di distribuzione, fare clic sul pulsante delle proprietà (**...**) per il server di pubblicazione di **editori** pagina della finestra di dialogo.  
  
    -   Per accedere ai profili degli agenti di replica, fare clic sul pulsante **Impostazioni predefinite profili** nella pagina **Generale** della finestra di dialogo. Per altre informazioni, vedere [Replication Agent Profiles](../../relational-databases/replication/agents/replication-agent-profiles.md).  
  
    -   Per modificare la password dell'account utilizzato quando stored procedure di amministrazione vengono eseguite sul server di pubblicazione e aggiornano le informazioni sul server di distribuzione, immettere una nuova password nelle caselle **Password** e **Conferma password** della pagina **Server di pubblicazione** della finestra di dialogo. Per ulteriori informazioni, vedere [proteggere il server di distribuzione](../../relational-databases/replication/security/secure-the-distributor.md).  
  
4.  Se necessario, modificare le proprietà e quindi fare clic su **OK**.  
  
#### Per visualizzare e modificare le proprietà del server di pubblicazione  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]e quindi espandere il nodo del server.  
  
2.  Pulsante destro del mouse il **replica** cartella e quindi fare clic su **proprietà server di pubblicazione**.  
  
3.  Visualizzare e modificare le proprietà di **proprietà server di pubblicazione - \< Publisher >** la finestra di dialogo.  
  
    -   Un utente nel ruolo predefinito del server **sysadmin** può abilitare i database per la replica nella pagina **Database di pubblicazione** . Attivazione di un database non pubblicare tale database. piuttosto, consente a qualsiasi utente il **db_owner** ruolo predefinito del database per il database creare una o più pubblicazioni nel database.  
  
4.  Se necessario, modificare le proprietà e quindi fare clic su **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 È possibile visualizzare le proprietà del server di pubblicazione e del database di distribuzione a livello di programmazione utilizzando le stored procedure di replica.  
  
#### Per visualizzare le proprietà del database di distribuzione  
  
1.  Eseguire [sp_helpdistributor](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md) per restituire informazioni su server di distribuzione, database di distribuzione e la directory di lavoro.  
  
2.  Eseguire [sp_helpdistributiondb](../../relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql.md) per restituire le proprietà di un database di distribuzione specificato.  
  
#### Per modificare le proprietà del server di distribuzione e del database di distribuzione  
  
1.  Nel server di distribuzione, eseguire [sp_changedistributor_property](../../relational-databases/system-stored-procedures/sp-changedistributor-property-transact-sql.md) per modificare le proprietà del server di distribuzione.  
  
2.  Nel server di distribuzione, eseguire [sp_changedistributiondb](../../relational-databases/system-stored-procedures/sp-changedistributiondb-transact-sql.md) per modificare le proprietà di database di distribuzione.  
  
3.  Nel server di distribuzione, eseguire [sp_changedistributor_password](../../relational-databases/system-stored-procedures/sp-changedistributor-password-transact-sql.md) per modificare la password del server di distribuzione.  
  
    > [!IMPORTANT]  
    >  Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali in un file di script, proteggere tale file per impedire l'accesso non autorizzato.  
  
4.  Nel server di distribuzione, eseguire [sp_changedistpublisher](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md) per modificare le proprietà di un server di pubblicazione tramite il server di distribuzione.  
  
###  <a name="TsqlExample"></a> Esempi (Transact-SQL)  
 Lo script [!INCLUDE[tsql](../../includes/tsql-md.md)] di esempio riportato di seguito restituisce informazioni sul database di distribuzione e sul database di distribuzione.  
  
 [!code-sql[HowTo#sp_helpdistributor](../../relational-databases/replication/codesnippet/tsql/view-and-modify-distribu_1.sql)]  
  
 [!code-sql[HowTo#sp_helpdistributiondb](../../relational-databases/replication/codesnippet/tsql/view-and-modify-distribu_2.sql)]  
  
 In questo esempio vengono modificati i periodi di memorizzazione per il server di distribuzione, la password utilizzata per la connessione al server di distribuzione e l'intervallo con cui il server di distribuzione verifica lo stato di diversi agenti di replica, noto anche come intervallo di heartbeat.  
  
> [!IMPORTANT]  
>  Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali in un file di script, proteggere tale file per impedire l'accesso non autorizzato.  
  
 [!code-sql[HowTo#sp_changedistributor_property](../../relational-databases/replication/codesnippet/tsql/view-and-modify-distribu_3.sql)]  
  
 [!code-sql[HowTo#sp_changedistributiondb](../../relational-databases/replication/codesnippet/tsql/view-and-modify-distribu_4.sql)]  
  
 [!code-sql[HowTo#sp_changedistributor_password](../../relational-databases/replication/codesnippet/tsql/view-and-modify-distribu_5.sql)]  
  
##  <a name="RMOProcedure"></a> Utilizzo di RMO (Replication Management Objects)  
  
#### Per visualizzare e modificare le proprietà del database di distribuzione  
  
1.  Creare una connessione al server di distribuzione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.ReplicationServer> (classe). Passare il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> oggetto ottenuto al passaggio 1.  
  
3.  (Facoltativo) Controllare il <xref:Microsoft.SqlServer.Replication.ReplicationServer.IsDistributor%2A> proprietà per verificare che il server attualmente connesso sia un server di distribuzione.  
  
4.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> metodo per ottenere le proprietà del server.  
  
5.  (Facoltativo) Per modificare le proprietà, impostare un nuovo valore per uno o più delle proprietà server di distribuzione che può essere impostata sul <xref:Microsoft.SqlServer.Replication.ReplicationServer> oggetto.  
  
6.  (Facoltativo) Se il <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> proprietà di <xref:Microsoft.SqlServer.Replication.ReplicationServer> oggetto è impostato su **true**, chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> metodo per salvare le modifiche al server.  
  
#### Per visualizzare e modificare le proprietà del database di distribuzione  
  
1.  Creare una connessione al server di distribuzione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.DistributionDatabase> (classe). Specificare la proprietà name e passare il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> oggetto ottenuto al passaggio 1.  
  
3.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo per ottenere le proprietà del server. Se questo metodo restituisce **false**, il database con il nome specificato non esiste nel server.  
  
4.  (Facoltativo) Per modificare le proprietà, impostare un nuovo valore per uno del <xref:Microsoft.SqlServer.Replication.DistributionDatabase> proprietà che possono essere impostate.  
  
5.  (Facoltativo) Se il <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> proprietà di <xref:Microsoft.SqlServer.Replication.DistributionDatabase> oggetto è impostato su **true**, chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> metodo per salvare le modifiche al server.  
  
#### Per visualizzare e modificare le proprietà del server di pubblicazione  
  
1.  Creare una connessione al server di pubblicazione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.DistributionPublisher> (classe). Specificare il <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> proprietà e passare il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> oggetto ottenuto al passaggio 1.  
  
3.  (Facoltativo) Per modificare le proprietà, impostare un nuovo valore per uno del <xref:Microsoft.SqlServer.Replication.DistributionPublisher> proprietà che possono essere impostate.  
  
4.  (Facoltativo) Se il <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> proprietà di <xref:Microsoft.SqlServer.Replication.DistributionPublisher> oggetto è impostato su **true**, chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> metodo per salvare le modifiche al server.  
  
#### Per modificare la password per la connessione amministrativa dal server di pubblicazione al database di distribuzione  
  
1.  Creare una connessione al server di distribuzione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.ReplicationServer> (classe).  
  
3.  Impostare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà per la connessione creata nel passaggio 1.  
  
4.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> metodo per ottenere le proprietà dell'oggetto.  
  
5.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeDistributorPassword%2A> metodo. Passare il nuovo valore della password per il parametro *password* .  
  
    > [!IMPORTANT]  
    >  Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali, utilizzare i [servizi di crittografia](http://go.microsoft.com/fwlink/?LinkId=34733) offerti da [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows .NET Framework.  
  
6.  (Facoltativo) Eseguire i passaggi seguenti per modificare la password in ogni server di pubblicazione remoto che utilizza questo server di distribuzione:  
  
    1.  Creare una connessione al server di pubblicazione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
    2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.ReplicationServer> (classe).  
  
    3.  Impostare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà per la connessione creata nel passaggio 6a.  
  
    4.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> metodo per ottenere le proprietà dell'oggetto.  
  
    5.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeDistributorPassword%2A> metodo. Passare il nuovo valore della password indicato nel passaggio 5 per il parametro *password* .  
  
###  <a name="PShellExample"></a> Esempio (RMO)  
 In questo esempio viene illustrato come modificare le proprietà del database di distribuzione e del database di distribuzione.  
  
> [!IMPORTANT]  
>  Per evitare di archiviare le credenziali del codice, la nuova password del server di distribuzione viene specificata in fase di esecuzione.  
  
 [!code-csharp[HowTo#rmo_ChangeDistPub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_changedistpub)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeDistPub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_changedistpub)]  
  
## Vedere anche  
 [Concetti di base relativi a RMO (Replication Management Objects)](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Disabilitazione della pubblicazione e della distribuzione](../../relational-databases/replication/disable-publishing-and-distribution.md)   
 [Configurazione della distribuzione](../../relational-databases/replication/configure-distribution.md)   
 [Concetti di base relativi a RMO (Replication Management Objects)](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Script di informazioni sui server di distribuzione e di pubblicazione](../../relational-databases/replication/administration/distributor-and-publisher-information-script.md)   
 [Concetti di base relativi alle stored procedure del sistema di replica](../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Consente di visualizzare informazioni ed eseguire attività per un server di pubblicazione & #40; Monitoraggio replica & #41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publisher-replication-monitor.md)  
  
  