---
title: "Aggiornamento di script di replica (programmazione Transact-SQL della replica) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "script [replica di SQL Server], aggiornamento"
  - "aggiornamento SQL Server, database replicati"
  - "aggiornamento di applicazioni di replica"
  - "replica [SQL Server], script"
  - "replica [SQL Server], aggiornamento"
  - "aggiornamento di database replicati"
ms.assetid: 0b8720bd-f339-4842-bc8f-b35a46f6d3ee
caps.latest.revision: 41
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 41
---
# Aggiornamento di script di replica (programmazione Transact-SQL della replica)
  [!INCLUDE[tsql](../../../includes/tsql-md.md)] per configurare a livello di programmazione una topologia di replica. Per ulteriori informazioni, vedere [replica sistema Stored procedure concetti](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md).  
  
> [!IMPORTANT]  
>  Sebbene non sia necessario aggiornare gli script eseguiti da membri del ruolo **sysadmin** , si consiglia di modificare gli script esistenti come descritto in questo argomento. Specificare un account con autorizzazioni minime per ogni agente di replica, come descritto nella sezione relativa alle autorizzazioni necessarie per gli agenti dell'argomento [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
 Oltre a offrire un maggior controllo delle autorizzazioni, consentendo di specificare in modo esplicito gli account di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows in cui vengono eseguiti i processi dell'agente di replica, questi miglioramenti apportati alla sicurezza influiscono sulle seguenti stored procedure negli script esistenti:  
  
-   **sp_addpublication_snapshot**:  
  
     È necessario specificare le credenziali di Windows come **@job_login** e **@job_password** durante l'esecuzione [sp_addpublication_snapshot & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md) Per creare il processo con cui viene eseguito l'agente Snapshot nel server di distribuzione.  
  
-   **sp_addpushsubscription_agent**:  
  
     È necessario eseguire [sp_addpushsubscription_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md) Per aggiungere un processo in modo esplicito e fornire le credenziali di Windows (**@job_login** e **@job_password**) in cui viene eseguito il processo dell'agente di distribuzione nel server di distribuzione. Nelle versioni di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] precedenti a [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]tale operazione viene eseguita automaticamente al momento della creazione di una sottoscrizione push.  
  
-   **sp_addmergepushsubscription_agent**:  
  
     È necessario eseguire [sp_addmergepushsubscription_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql.md) Per aggiungere un processo in modo esplicito e fornire le credenziali di Windows (**@job_login** e **@job_password**) in cui viene eseguito il processo di agente di Merge nel server di distribuzione. Nelle versioni di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] precedenti a [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]tale operazione viene eseguita automaticamente al momento della creazione di una sottoscrizione push.  
  
-   **sp_addpullsubscription_agent**:  
  
     È necessario specificare le credenziali di Windows come **@job_login** e **@job_password** durante l'esecuzione [sp_addpullsubscription_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md) Per creare il processo con cui viene eseguito l'agente di distribuzione nel Sottoscrittore.  
  
-   **sp_addmergepullsubscription_agent**:  
  
     È necessario specificare le credenziali di Windows come **@job_login** e **@job_password** durante l'esecuzione [sp_addmergepullsubscription_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md) Per creare il processo con cui viene eseguito l'agente di Merge nel Sottoscrittore.  
  
-   **sp_addlogreader_agent**:  
  
     È necessario eseguire [sp_addlogreader_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md) Per aggiungere il processo manuale e fornire le credenziali di Windows con cui viene eseguito l'agente di lettura Log nel server di distribuzione. Nelle versioni di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] precedenti a [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]tale operazione viene eseguita automaticamente al momento della creazione di una pubblicazione transazionale.  
  
-   **sp_addqreader_agent**:  
  
     È necessario eseguire [sp_addqreader_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql.md) Per aggiungere il processo manuale e fornire le credenziali di Windows con cui viene eseguito l'agente di lettura coda nel server di distribuzione. Nelle versioni di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] precedenti a [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]tale operazione viene eseguita automaticamente al momento della creazione di una pubblicazione transazionale con supporto dell'aggiornamento in coda.  
  
 Nel modello di sicurezza introdotte in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], gli agenti di replica stabiliscono sempre le connessioni all'istanza locale di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] con l'autenticazione di Windows utilizzando le credenziali specificate **@job_name** e **@job_password**. Per informazioni sui requisiti degli account di Windows utilizzati quando si eseguono processi dell'agente di replica, vedere [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
> [!IMPORTANT]  
>  Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se si archiviano le credenziali in un file script, assicurarsi che quest'ultimo sia protetto.  
  
### Per aggiornare gli script di configurazione di una pubblicazione snapshot o transazionale  
  
1.  Nello script esistente, prima di [sp_addpublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md), eseguire [sp_addlogreader_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md) nel server di pubblicazione nel database di pubblicazione. Specificare le credenziali di Windows con cui viene eseguito l'agente di lettura Log per **@job_name** e **@job_password**. Se l'agente utilizzerà [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] l'autenticazione quando ci si connette al server di pubblicazione, è necessario specificare anche un valore di **0** per **@publisher_security_mode** e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] informazioni di accesso per **@publisher_login** e **@publisher_password**. Verrà creato un processo dell'agente di lettura log per il database di pubblicazione.  
  
    > [!NOTE]  
    >  Questo passaggio è necessario solo per le pubblicazioni transazionali, non per le pubblicazioni snapshot.  
  
2.  (Facoltativo) Prima di [sp_addpublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md), eseguire [sp_addqreader_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql.md) nel server di distribuzione nel database di distribuzione. Specificare le credenziali di Windows con cui viene eseguito l'agente di lettura coda per **@job_name** e **@job_password**. Verrà creato un processo dell'agente di lettura coda per il server di distribuzione.  
  
    > [!NOTE]  
    >  Questo passaggio è necessario solo per le pubblicazioni transazionali che supportano Sottoscrittori ad aggiornamento in coda.  
  
3.  (Facoltativo) Aggiornare l'esecuzione di [sp_addpublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md) Per impostare valori non predefiniti per i parametri che implementano nuove funzionalità di replica.  
  
4.  Dopo aver [sp_addpublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md), eseguire [sp_addpublication_snapshot & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md) nel server di pubblicazione nel database di pubblicazione. Specificare **@publication** e le credenziali di Windows con cui viene eseguito l'agente Snapshot per **@job_name** e **@job_password**. Se l'agente utilizzerà [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] l'autenticazione quando ci si connette al server di pubblicazione, è necessario specificare anche un valore di **0** per **@publisher_security_mode** e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] informazioni di accesso per **@publisher_login** e **@publisher_password**. Verrà creato un processo dell'agente snapshot per la pubblicazione.  
  
5.  (Facoltativo) Aggiornare l'esecuzione di [sp_addarticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) Per impostare valori non predefiniti per i parametri che implementano nuove funzionalità di replica.  
  
### Per aggiornare gli script per l'aggiunta di sottoscrizioni di una pubblicazione snapshot o transazionale  
  
1.  Dopo avere eseguito la stored procedure di creazione della sottoscrizione, assicurarsi di eseguire la stored procedure di creazione di un processo dell'agente di distribuzione per sincronizzare la sottoscrizione. La stored procedure utilizzata varia in base al tipo di sottoscrizione.  
  
    -   Per una sottoscrizione pull, aggiornare l'esecuzione di [sp_addpullsubscription_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md) Per specificare le credenziali di Windows con cui viene eseguito l'agente di distribuzione nel Sottoscrittore per **@job_name** e **@job_password**. Questa operazione viene eseguita dopo l'esecuzione di [sp_addpullsubscription](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md). Per altre informazioni, vedere [Create a Pull Subscription](../../../relational-databases/replication/create-a-pull-subscription.md).  
  
    -   Per una sottoscrizione push, eseguire [sp_addpushsubscription_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md) nel server di pubblicazione. Specificare **@subscriber**, **@subscriber_db**, **@publication**, le credenziali di Windows con cui viene eseguito l'agente di distribuzione nel server di distribuzione per **@job_name** e **@job_password**, e una pianificazione per il processo dell'agente. Per altre informazioni, vedere [Specify Synchronization Schedules](../../../relational-databases/replication/specify-synchronization-schedules.md). Questa operazione viene eseguita dopo l'esecuzione di [sp_addsubscription](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Per altre informazioni, vedere [Create a Push Subscription](../../../relational-databases/replication/create-a-push-subscription.md).  
  
### Per aggiornare gli script di configurazione di una pubblicazione di tipo merge  
  
1.  (Facoltativo) Nello script esistente, aggiornare l'esecuzione di [sp_addmergepublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md) Per impostare valori non predefiniti per i parametri che implementano nuove funzionalità di replica.  
  
2.  Dopo aver [sp_addmergepublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md), eseguire [sp_addpublication_snapshot & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md) nel server di pubblicazione nel database di pubblicazione. Specificare **@publication** e le credenziali di Windows con cui viene eseguito l'agente Snapshot per **@job_name** e **@job_password**. Se l'agente utilizzerà [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] l'autenticazione quando ci si connette al server di pubblicazione, è necessario specificare anche un valore di **0** per **@publisher_security_mode** e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] informazioni di accesso per **@publisher_login** e **@publisher_password**. Verrà creato un processo dell'agente snapshot per la pubblicazione.  
  
3.  (Facoltativo) Aggiornare l'esecuzione di [sp_addmergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) Per impostare valori non predefiniti per i parametri che implementano nuove funzionalità di replica.  
  
### Per aggiornare gli script per l'aggiunta di sottoscrizioni di una pubblicazione di tipo merge  
  
1.  Dopo avere eseguito la stored procedure di creazione della sottoscrizione, assicurarsi di eseguire la stored procedure di creazione di un processo dell'agente di merge per sincronizzare la sottoscrizione. La stored procedure utilizzata varia in base al tipo di sottoscrizione.  
  
    -   Per una sottoscrizione pull, aggiornare l'esecuzione di [sp_addmergepullsubscription_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md) Per specificare le credenziali di Windows con cui viene eseguito l'agente di Merge nel Sottoscrittore per **@job_name** e **@job_password**. Questa operazione viene eseguita dopo l'esecuzione di [sp_addmergepullsubscription](../../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md). Per altre informazioni, vedere [Create a Pull Subscription](../../../relational-databases/replication/create-a-pull-subscription.md).  
  
    -   Per una sottoscrizione push, eseguire [sp_addmergepushsubscription_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql.md) nel server di pubblicazione. Specificare **@subscriber**, **@subscriber_db**, **@publication**, le credenziali di Windows con cui viene eseguito l'agente di Merge nel server di distribuzione per **@job_name** e **@job_password**, e una pianificazione per il processo dell'agente. Per altre informazioni, vedere [Specify Synchronization Schedules](../../../relational-databases/replication/specify-synchronization-schedules.md). Questa operazione viene eseguita dopo l'esecuzione di [sp_addmergesubscription](../../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md). Per altre informazioni, vedere [Create a Push Subscription](../../../relational-databases/replication/create-a-push-subscription.md).  
  
## Esempio  
 Di seguito è riportato un esempio di uno script [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] per la creazione di una pubblicazione transazionale per la tabella Product. Questa pubblicazione supporta l'aggiornamento immediato sostituito dall'aggiornamento in coda come soluzione di failover. I parametri predefiniti sono stati rimossi per una maggiore leggibilità.  
  
 [!code-sql[HowTo#sp_createtranpub_NWpreupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_1.sql)]  
  
## Esempio  
 Di seguito è riportato un esempio dello script precedente per la creazione di una pubblicazione transazionale, aggiornato in modo da essere eseguito correttamente in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] e versioni successive. Questa pubblicazione supporta l'aggiornamento immediato sostituito dall'aggiornamento in coda come soluzione di failover. I valori predefiniti dei nuovi parametri sono stati dichiarati in modo esplicito.  
  
> [!NOTE]  
>  Le credenziali di Windows vengono fornite in fase di esecuzione tramite **sqlcmd** le variabili di scripting.  
  
 [!code-sql[HowTo#sp_createtranpub_NWpostupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_2.sql)]  
  
## Esempio  
 Di seguito è riportato un esempio di uno script [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] per la creazione di una pubblicazione di tipo merge per la tabella Customers. I parametri predefiniti sono stati rimossi per una maggiore leggibilità.  
  
 [!code-sql[HowTo#sp_createmergepub_NWpreupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_3.sql)]  
  
## Esempio  
 Di seguito è riportato un esempio dello script precedente per la creazione di una pubblicazione di tipo merge, aggiornato in modo da essere eseguito correttamente in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] e versioni successive. I valori predefiniti dei nuovi parametri sono stati dichiarati in modo esplicito.  
  
> [!NOTE]  
>  Le credenziali di Windows vengono fornite in fase di esecuzione tramite **sqlcmd** le variabili di scripting.  
  
 [!code-sql[HowTo#sp_createmergepub_NWpostupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_4.sql)]  
  
## Esempio  
 Di seguito è riportato un esempio di uno script [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] per la creazione di una sottoscrizione push di una pubblicazione transazionale. I parametri predefiniti sono stati rimossi per una maggiore leggibilità.  
  
 [!code-sql[HowTo#sp_createtranpushsub_NWpreupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_5.sql)]  
  
## Esempio  
 Di seguito è riportato un esempio dello script precedente per la creazione di una sottoscrizione push di una pubblicazione transazionale, aggiornato in modo da essere eseguito correttamente in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] e versioni successive. I valori predefiniti dei nuovi parametri sono stati dichiarati in modo esplicito.  
  
> [!NOTE]  
>  Le credenziali di Windows vengono fornite in fase di esecuzione tramite **sqlcmd** le variabili di scripting.  
  
 [!code-sql[HowTo#sp_createtranpushsub_NWpostupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_6.sql)]  
  
## Esempio  
 Di seguito è riportato un esempio di uno script [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] per la creazione di una sottoscrizione push di una pubblicazione di tipo merge. I parametri predefiniti sono stati rimossi per una maggiore leggibilità.  
  
 [!code-sql[HowTo#sp_createmergepushsub_NWpreupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_7.sql)]  
  
## Esempio  
 Di seguito è riportato un esempio dello script precedente per la creazione di una sottoscrizione push di una pubblicazione di tipo merge, aggiornato in modo da essere eseguito correttamente in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] e versioni successive. I valori predefiniti dei nuovi parametri sono stati dichiarati in modo esplicito.  
  
> [!NOTE]  
>  Le credenziali di Windows vengono fornite in fase di esecuzione tramite **sqlcmd** le variabili di scripting.  
  
 [!code-sql[HowTo#sp_createmergepushsub_NWpostupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_8.sql)]  
  
## Esempio  
 Di seguito è riportato un esempio di uno script [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] per la creazione di una sottoscrizione pull di una pubblicazione transazionale. I parametri predefiniti sono stati rimossi per una maggiore leggibilità.  
  
 [!code-sql[HowTo#sp_createmergepushsub_NWpreupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_7.sql)]  
  
## Esempio  
 Di seguito è riportato un esempio dello script precedente per la creazione di una sottoscrizione pull di una pubblicazione transazionale, aggiornato in modo da essere eseguito correttamente in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] e versioni successive. I valori predefiniti dei nuovi parametri sono stati dichiarati in modo esplicito.  
  
> [!NOTE]  
>  Le credenziali di Windows vengono fornite in fase di esecuzione tramite **sqlcmd** le variabili di scripting.  
  
 [!code-sql[HowTo#sp_createtranpullsub_NWpostupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_9.sql)]  
  
## Esempio  
 Di seguito è riportato un esempio di uno script [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] per la creazione di una sottoscrizione pull di una pubblicazione di tipo merge. I parametri predefiniti sono stati rimossi per una maggiore leggibilità.  
  
 [!code-sql[HowTo#sp_createmergepullsub_NWpreupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_10.sql)]  
  
## Esempio  
 Di seguito è riportato un esempio dello script precedente per la creazione di una sottoscrizione pull di una pubblicazione di tipo merge, aggiornato in modo da essere eseguito correttamente in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] e versioni successive. I valori predefiniti dei nuovi parametri sono stati dichiarati in modo esplicito.  
  
> [!NOTE]  
>  Le credenziali di Windows vengono fornite in fase di esecuzione tramite **sqlcmd** le variabili di scripting.  
  
 [!code-sql[HowTo#sp_createmergepullsub_NWpostupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_11.sql)]  
  
## Vedere anche  
 [Creazione di una pubblicazione](../../../relational-databases/replication/publish/create-a-publication.md)   
 [Create a Push Subscription](../../../relational-databases/replication/create-a-push-subscription.md)   
 [Create a Pull Subscription](../../../relational-databases/replication/create-a-pull-subscription.md)   
 [View and Modify Replication Security Settings](../../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [MSSQL_ENG021797](../../../relational-databases/replication/mssql-eng021797.md)   
 [MSSQL_ENG021798](../../../relational-databases/replication/mssql-eng021798.md)   
 [Concetti di base relativi alle stored procedure del sistema di replica](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Aggiornare database replicati](../../../database-engine/install-windows/upgrade-replicated-databases.md)  
  
  