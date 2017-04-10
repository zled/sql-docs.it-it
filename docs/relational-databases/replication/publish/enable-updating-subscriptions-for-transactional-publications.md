---
title: "Abilitazione delle sottoscrizioni aggiornabili per le pubblicazioni transazionali | Microsoft Docs"
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
  - "transactional replication, updatable subscriptions"
  - "updatable subscriptions, enabling"
  - "sottoscrizioni [replica di SQL Server], aggiornabili"
ms.assetid: 539d5bb0-b808-4d8c-baf4-cb6d32d2c595
caps.latest.revision: 42
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 42
---
# Abilitazione delle sottoscrizioni aggiornabili per le pubblicazioni transazionali
  In questo argomento viene descritto come abilitare l'aggiornamento delle sottoscrizioni per pubblicazioni transazionali in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
> **NOTA** [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  

##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
 Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali in un file script, è fondamentale proteggere il file per evitare accessi non autorizzati.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Abilitare le sottoscrizioni aggiornabili per le pubblicazioni transazionali nella pagina **Tipo di pubblicazione** della Creazione guidata nuova pubblicazione.  
  
 Per utilizzare le sottoscrizioni aggiornabili, è inoltre necessario configurare le opzioni della Creazione guidata nuova sottoscrizione.  
  
#### Per attivare le sottoscrizioni aggiornabili  
  
1.  Nella pagina **Tipo di pubblicazione** della Creazione guidata nuova pubblicazione, selezionare **Pubblicazione transazionale con sottoscrizioni aggiornabili**.  
  
2.  Nella pagina **Sicurezza agente** , specificare le impostazioni di sicurezza per l'agente di lettura coda, per l'agente snapshot e per l'agente di lettura log. Per ulteriori informazioni sulle autorizzazioni necessarie per l'account con cui viene eseguito l'agente di lettura coda, vedere [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
    > **Nota:** l'agente di lettura coda è configurato anche se si utilizzano solo le sottoscrizioni ad aggiornamento immediato.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 Quando si crea una pubblicazione transazionale a livello di programmazione utilizzando stored procedure di replica, è possibile abilitare sottoscrizioni ad aggiornamento immediato o in coda.  
  
#### Per creare una pubblicazione che supporta sottoscrizioni ad aggiornamento immediato  
  
1.  Se necessario, creare un processo dell'agente di lettura log per il database di pubblicazione.  
  
    -   Se per il database di pubblicazione esiste già un processo dell'agente di lettura log, procedere con il passaggio 2.  
  
    -   Se si è certi se esiste un processo dell'agente di lettura Log per un database pubblicato, eseguire [sp_helplogreader_agent &#40; Transact-SQL &#41;](../../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md) nel server di pubblicazione nel database di pubblicazione. Se il set di risultati è vuoto, sarà necessario creare un processo dell'agente di lettura log.  
  
    -   Server di pubblicazione, eseguire [sp_addlogreader_agent &#40; Transact-SQL &#41;](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md). Specificare il [!INCLUDE[msCoName](../../../includes/msconame-md.md)] le credenziali di Windows con cui viene eseguito l'agente per **@job_name** e **@password**. Se l'agente utilizzerà l'autenticazione di SQL Server quando ci si connette al server di pubblicazione, è necessario specificare anche un valore di **0** per **@publisher_security_mode** e [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] informazioni di accesso per **@publisher_login** e **@publisher_password**.  
  
2.  Eseguire [sp_addpublication &#40; Transact-SQL &#41;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md), specificando il valore **true** per il parametro **@allow_sync_tran**.  
  
3.  Server di pubblicazione, eseguire [sp_addpublication_snapshot &#40; Transact-SQL &#41;](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Specificare il nome della pubblicazione utilizzato al passaggio 2 per **@publication** e le credenziali di Windows con cui viene eseguito l'agente Snapshot per **@job_name** e **@password**. Se l'agente utilizzerà l'autenticazione di SQL Server quando ci si connette al server di pubblicazione, è necessario specificare anche un valore di **0** per **@publisher_security_mode** e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] informazioni di accesso per **@publisher_login** e **@publisher_password**. Verrà creato un processo dell'agente snapshot per la pubblicazione.  
  
4.  Aggiungere articoli alla pubblicazione. Per altre informazioni, vedere [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
5.  Nel Sottoscrittore creare una sottoscrizione aggiornabile per la pubblicazione.   
  
#### Per creare una pubblicazione che supporta sottoscrizioni ad aggiornamento in coda  
  
1.  Se necessario, creare un processo dell'agente di lettura log per il database di pubblicazione.  
  
    -   Se per il database di pubblicazione esiste già un processo dell'agente di lettura log, procedere con il passaggio 2.  
  
    -   Se si è certi se esiste un processo dell'agente di lettura Log per un database pubblicato, eseguire [sp_helplogreader_agent &#40; Transact-SQL &#41;](../../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md) nel server di pubblicazione nel database di pubblicazione. Se il set di risultati è vuoto, sarà necessario creare un processo dell'agente di lettura log.  
  
    -   Server di pubblicazione, eseguire [sp_addlogreader_agent &#40; Transact-SQL &#41;](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md). Specificare le credenziali di Windows con cui viene eseguito l'agente per **@job_name** e **@password**. Se l'agente utilizzerà l'autenticazione di SQL Server quando ci si connette al server di pubblicazione, è necessario specificare anche un valore di **0** per **@publisher_security_mode** e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] informazioni di accesso per **@publisher_login** e **@publisher_password**.  
  
2.  Se necessario, creare un processo dell'agente di lettura coda per il server di distribuzione.  
  
    -   Se per il database di distribuzione esiste già un processo dell'agente di lettura coda, procedere con il passaggio 3.  
  
    -   Se si è certi se esiste un processo dell'agente di lettura coda per il database di distribuzione, eseguire [sp_helpqreader_agent &#40; Transact-SQL &#41;](../../../relational-databases/system-stored-procedures/sp-helpqreader-agent-transact-sql.md) nel server di distribuzione nel database di distribuzione. Se il set di risultati è vuoto, sarà necessario creare un processo dell'agente di lettura coda.  
  
    -   Nel server di distribuzione, eseguire [sp_addqreader_agent &#40; Transact-SQL &#41;](../../../relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql.md). Specificare le credenziali di Windows con cui viene eseguito l'agente per **@job_name** e **@password**. Queste credenziali vengono utilizzate quando l'agente di lettura coda si connette al server di pubblicazione e al Sottoscrittore. Per altre informazioni, vedere [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
3.  Eseguire [sp_addpublication &#40; Transact-SQL &#41;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md), specificando il valore **true** per il parametro **@allow_queued_tran** e il valore **wins pub**, **sub reinit**, o **sub wins** per **@conflict_policy**.  
  
4.  Server di pubblicazione, eseguire [sp_addpublication_snapshot (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Specificare il nome della pubblicazione utilizzato al passaggio 3 per **@publication** e le credenziali di Windows con cui viene eseguito l'agente Snapshot per **@snapshot_job_name** e **@password**. Se l'agente utilizzerà l'autenticazione di SQL Server quando ci si connette al server di pubblicazione, è necessario specificare anche un valore di **0** per **@publisher_security_mode** e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] informazioni di accesso per **@publisher_login** e **@publisher_password**. Verrà creato un processo dell'agente snapshot per la pubblicazione.  
  
5.  Aggiungere articoli alla pubblicazione. Per altre informazioni, vedere [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
6.  Nel Sottoscrittore creare una sottoscrizione aggiornabile per la pubblicazione.  
  
#### Per modificare i criteri per la gestione dei conflitti per una pubblicazione che consente le sottoscrizioni ad aggiornamento in coda  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_changepublication &#40; Transact-SQL &#41;](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md). Specificare un valore di **conflict_policy** per **@property** e la modalità desiderata dei conflitti di **wins pub**, **sub reinit**, o **sub wins** per **@value**.  
  
###  <a name="TsqlExample"></a> Esempio (Transact-SQL)  
 In questo esempio viene creata una pubblicazione che supporta le sottoscrizioni pull ad aggiornamento immediato e in coda.  
  
 [!code-sql[HowTo#sp_createtranupdatingpub](../../../relational-databases/replication/codesnippet/tsql/enable-updating-subscrip_1.sql)]  
  
## Vedere anche  
 [Imposta opzioni di risoluzione dei conflitti ad aggiornamento in coda &#40; SQL Server Management Studio &#41;](../../../relational-databases/replication/publish/set-queued-updating-conflict-resolution-options-sql-server-management-studio.md)   
 [Tipi di pubblicazioni per la replica transazionale](../../../relational-databases/replication/transactional/publication-types-for-transactional-replication.md)   
 [Updatable Subscriptions for Transactional Replication](../../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Creazione di una pubblicazione](../../../relational-databases/replication/publish/create-a-publication.md)   
 [Creazione di una sottoscrizione aggiornabile di una pubblicazione transazionale](https://msdn.microsoft.com/library/mt740635.aspx)   
 [Updatable Subscriptions for Transactional Replication](../../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Utilizzo di sqlcmd con variabili di scripting](../../../relational-databases/scripting/use-sqlcmd-with-scripting-variables.md)  
  
  