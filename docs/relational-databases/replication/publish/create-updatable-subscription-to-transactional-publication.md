---
title: "Creare una sottoscrizione aggiornabile di una pubblicazione transazionale con Transact-SQL | Microsoft Docs"
ms.custom: ""
ms.date: "07/21/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "sottoscrizioni transazionali aggiornabili, T-SQL"
ms.assetid: a6e80857-0a69-4867-b6b7-f3629d00c312
caps.latest.revision: 6
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 6
---
# Creare una sottoscrizione aggiornabile di una pubblicazione transazionale con Transact-SQL

> [!NOTE]  
>  Questa funzionalità continuerà a essere supportata nelle versioni di [!INCLUDE[ssNoVersion_md](../../../includes/ssnoversion-md.md)] dalla 2012 alla 2016.  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
 
La replica transazionale consente di ripropagare al server di pubblicazione le modifiche apportate a un Sottoscrittore utilizzando sottoscrizioni ad aggiornamento immediato o ad aggiornamento in coda. È possibile creare una sottoscrizione ad aggiornamento a livello di programmazione tramite le stored procedure di replica. Vedere anche [Creare una sottoscrizione aggiornabile di una pubblicazione transazionale (Management Studio)](../../../relational-databases/replication/publish/create-an-updatable-subscription-to-a-transactional-publication.md). 

## Per creare una sottoscrizione pull ad aggiornamento immediato ##

1. Nel server di pubblicazione eseguire [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) per verificare che la pubblicazione supporti le sottoscrizioni ad aggiornamento immediato. 

    * Se il valore di `allow_sync_tran` nel set di risultati è `1`, la pubblicazione supporta le sottoscrizioni ad aggiornamento immediato.

    * Se il valore di `allow_sync_tran` nel set di risultati è `0`, sarà necessario creare nuovamente la pubblicazione abilitando le sottoscrizioni ad aggiornamento immediato.

2. Nel server di pubblicazione eseguire [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) per verificare che la pubblicazione supporti le sottoscrizioni pull. 

    * Se il valore di `allow_pull` nel set di risultati è `1`, la pubblicazione supporta le sottoscrizioni pull.

    * Se il valore di `allow_pull` è `0`, eseguire [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), specificando `allow_pull` per `@property` e `true` per `@value`. 

3. Nel Sottoscrittore eseguire [sp_addpullsubscription](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md). Specificare `@publisher` e `@publication`, nonché uno dei seguenti valori per `@update_mode`:

    * `sync tran` - abilita la sottoscrizione per l'aggiornamento immediato.

    * `failover` - abilita la sottoscrizione per l'aggiornamento immediato sostituito dall'aggiornamento in coda in caso di failover.

    > [!NOTE]  
>  `failover` richiede che la pubblicazione sia abilitata anche per le sottoscrizioni ad aggiornamento in coda. 
 
4. Nel Sottoscrittore eseguire [sp_addpullsubscription_agent](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md). Specificare le opzioni seguenti:

    * I parametri `@publisher`, `@publisher_db` e `@publication`. 

    * Le credenziali di Microsoft Windows per l'esecuzione dell'agente di distribuzione nel Sottoscrittore per `@job_login``@job_password`. 

    > [!NOTE]  
>  Per le connessioni attivate con l'autenticazione integrata di Windows vengono sempre usate le credenziali di Windows specificate da `@job_login` e `@job_password`. L'agente di distribuzione attiva sempre la connessione locale al Sottoscrittore utilizzando l'autenticazione integrata di Windows. Per impostazione predefinita, l'agente si connette al server di distribuzione con l'autenticazione integrata di Windows. 
 
    * (Facoltativo) Il valore `0` per `@distributor_security_mode` e le informazioni sull'account di accesso di Microsoft SQL Server per `@distributor_login` e `@distributor_password`, se è necessario usare l'autenticazione di SQL Server per la connessione al server di distribuzione. 

    * Specificare una pianificazione per il processo dell'agente di distribuzione da eseguire per la sottoscrizione. 

5. Nel database di sottoscrizione del Sottoscrittore eseguire [sp_link_publication](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md). Specificare `@publisher`, `@publication`, il nome del database di pubblicazione per `@publisher_db` e uno dei valori seguenti per `@security_mode`: 

    * `0` - Usare l'autenticazione di SQL Server quando si eseguono aggiornamenti nel server di pubblicazione. Questa opzione richiede di specificare un account di accesso valido nel server di pubblicazione per `@login` e `@password`.

    * `1` - Usare il contesto di sicurezza dell'utente che esegue le modifiche nel Sottoscrittore quando ci si connette al server di pubblicazione. Per informazioni sulle restrizioni correlate a questa modalità di sicurezza, vedere [sp_link_publication](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md).

    * `2` - Usare un account di accesso esistente e definito dall'utente per il server collegato, creato con [sp_addlinkedserver](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md).

6. Nel server di pubblicazione eseguire [sp_addsubscription](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) specificando `@publication`, `@subscriber`, `@destination_db`, il valore pull per `@subscription_type` e lo stesso valore specificato al passaggio 3 per `@update_mode`.

La sottoscrizione pull verrà registrata nel server di pubblicazione. 


## Per creare una sottoscrizione push ad aggiornamento immediato ##

1. Nel server di pubblicazione eseguire [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) per verificare che la pubblicazione supporti le sottoscrizioni ad aggiornamento immediato. 

    * Se il valore di `allow_sync_tran` nel set di risultati è `1`, la pubblicazione supporta le sottoscrizioni ad aggiornamento immediato.

    * Se il valore di `allow_sync_tran` nel set di risultati è `0`, sarà necessario creare nuovamente la pubblicazione abilitando le sottoscrizioni ad aggiornamento immediato.

2. Nel server di pubblicazione eseguire [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) per verificare che la pubblicazione supporti le sottoscrizioni push. 

    * Se il valore di `allow_push` nel set di risultati è `1`, la pubblicazione supporta le sottoscrizioni push.

    * Se il valore di `allow_push` è `0`, eseguire [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), specificando `allow_push` per `@property` e `true` per `@value`. 

3. Nel server di pubblicazione eseguire [sp_addsubscription](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Specificare `@publication`, `@subscriber`, `@destination_db`, nonché uno dei seguenti valori per `@update_mode`:

    * `sync tran` - abilita il supporto per l'aggiornamento immediato.

    * `failover` - abilita il supporto per l'aggiornamento immediato sostituito dall'aggiornamento in coda in caso di failover.

    > [!NOTE]  
>  `failover` richiede che la pubblicazione sia abilitata anche per le sottoscrizioni ad aggiornamento in coda. 
 
4. Nel server di pubblicazione eseguire [sp_addpushsubscription_agent](../../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md). Specificare i parametri seguenti:

    * `@subscriber`, `@subscriber_db` e `@publication`. 

    * Le credenziali di Windows usate per eseguire l'agente di distribuzione nel server di distribuzione per `@job_login` e `@job_password`. 

    > [!NOTE]  
>  Per le connessioni attivate con l'autenticazione integrata di Windows vengono sempre usate le credenziali di Windows specificate da `@job_login` e `@job_password`. L'agente di distribuzione esegue sempre la connessione locale al server di distribuzione utilizzando l'autenticazione integrata di Windows. Per impostazione predefinita, l'agente si connette al Sottoscrittore utilizzando l'autenticazione integrata di Windows. 

    * (Facoltativo) Il valore `0` per `@subscriber_security_mode` e le informazioni sull'account di accesso di SQL Server per `@subscriber_login` e `@subscriber_password`, se è necessario usare l'autenticazione di SQL Server per la connessione al Sottoscrittore. 

    * Specificare una pianificazione per il processo dell'agente di distribuzione da eseguire per la sottoscrizione.

5. Nel database di sottoscrizione del Sottoscrittore eseguire [sp_link_publication](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md). Specificare `@publisher`, `@publication`, il nome del database di pubblicazione per `@publisher_db` e uno dei valori seguenti per `@security_mode`: 

     * `0` - Usare l'autenticazione di SQL Server quando si eseguono aggiornamenti nel server di pubblicazione. Questa opzione richiede di specificare un account di accesso valido nel server di pubblicazione per `@login` e `@password`.

     * `1` - Usare il contesto di sicurezza dell'utente che esegue le modifiche nel Sottoscrittore quando ci si connette al server di pubblicazione. Per informazioni sulle restrizioni correlate a questa modalità di sicurezza, vedere [sp_link_publication](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md).

     * `2` - Usare un account di accesso esistente e definito dall'utente per il server collegato, creato con [sp_addlinkedserver](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md).


## Per creare una sottoscrizione pull ad aggiornamento in coda ##

1. Nel server di pubblicazione eseguire [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) per verificare che la pubblicazione supporti le sottoscrizioni ad aggiornamento in coda. 

    * Se il valore di `allow_queued_tran` nel set di risultati è `1`, la pubblicazione supporta le sottoscrizioni ad aggiornamento immediato.

    * Se il valore di `allow_queued_tran` nel set di risultati è `0`, sarà necessario creare nuovamente la pubblicazione abilitando le sottoscrizioni ad aggiornamento in coda.

2. Nel server di pubblicazione eseguire [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) per verificare che la pubblicazione supporti le sottoscrizioni pull. 

    * Se il valore di `allow_pull` nel set di risultati è `1`, la pubblicazione supporta le sottoscrizioni pull.

    * Se il valore di `allow_pull` è `0`, eseguire [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), specificando `allow_pull` per `@property` e `true` per `@value`. 

3. Nel Sottoscrittore eseguire [sp_addpullsubscription](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md). Specificare `@publisher` e `@publication`, nonché uno dei seguenti valori per `@update_mode`:

    * `queued tran` - abilita la sottoscrizione per l'aggiornamento in coda.

    * `queued failover` - abilita il supporto per l'aggiornamento in coda sostituito dall'aggiornamento immediato in caso di failover.

    > [!NOTE]  
>  `queued failover` richiede che la pubblicazione sia abilitata anche per le sottoscrizioni ad aggiornamento immediato. Per eseguire il failover all'aggiornamento immediato, è necessario usare [sp_link_publication](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md) per definire le credenziali con cui replicare nel server di pubblicazione le modifiche apportate al Sottoscrittore.
 
4. Nel Sottoscrittore eseguire [sp_addpullsubscription_agent](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md). Specificare i parametri seguenti:

    * @publisher, `@publisher_db` e `@publication`. 

    * Le credenziali di Windows per l'esecuzione dell'agente di distribuzione nel Sottoscrittore per `@job_login` e `@job_password`. 

    > [!NOTE]  
>  Per le connessioni attivate con l'autenticazione integrata di Windows vengono sempre usate le credenziali di Windows specificate da `@job_login` e `@job_password`. L'agente di distribuzione attiva sempre la connessione locale al Sottoscrittore utilizzando l'autenticazione integrata di Windows. Per impostazione predefinita, l'agente si connette al server di distribuzione con l'autenticazione integrata di Windows. 
 
    * (Facoltativo) Il valore `0` per `@distributor_security_mode` e le informazioni sull'account di accesso di SQL Server per `@distributor_login` e `@distributor_password`, se è necessario usare l'autenticazione di SQL Server per la connessione al server di distribuzione. 

    * Specificare una pianificazione per il processo dell'agente di distribuzione da eseguire per la sottoscrizione.

5. Nel server di pubblicazione eseguire [sp_addsubscriber](../../../relational-databases/system-stored-procedures/sp-addsubscriber-transact-sql.md) per registrare il Sottoscrittore nel server di pubblicazione specificando `@publication`, `@subscriber`, `@destination_db`, il valore pull per `@subscription_type` e lo stesso valore specificato al passaggio 3 per `@update_mode`.

La sottoscrizione pull verrà registrata nel server di pubblicazione. 


## Per creare una sottoscrizione push ad aggiornamento in coda ##

1. Nel server di pubblicazione eseguire [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) per verificare che la pubblicazione supporti le sottoscrizioni ad aggiornamento in coda. 

    * Se il valore di allow_queued_tran nel set di risultati è 1, la pubblicazione supporta le sottoscrizioni ad aggiornamento immediato.

    * Se il valore di allow_queued_tran nel set di risultati è 0, sarà necessario creare nuovamente la pubblicazione abilitando le sottoscrizioni ad aggiornamento in coda. Per altre informazioni, vedere Procedura: Abilitare le sottoscrizioni aggiornabili per le pubblicazioni transazionali (programmazione Transact-SQL della replica).

2. Nel server di pubblicazione eseguire [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) per verificare che la pubblicazione supporti le sottoscrizioni push. 

    * Se il valore di `allow_push` nel set di risultati è `1`, la pubblicazione supporta le sottoscrizioni push.

    * Se il valore di `allow_push` è `0`, eseguire [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), specificando allow_push per `@property` e `true` per `@value`. 

3. Nel server di pubblicazione eseguire [sp_addsubscription](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Specificare `@publication`, `@subscriber`, `@destination_db`, nonché uno dei seguenti valori per `@update_mode`:

    * `queued tran` - abilita la sottoscrizione per l'aggiornamento in coda.

    * `queued failover` - abilita il supporto per l'aggiornamento in coda sostituito dall'aggiornamento immediato in caso di failover.

    > [!NOTE]  
>  Con l'opzione queued failover è necessario che la pubblicazione sia abilitata anche per le sottoscrizioni ad aggiornamento immediato. Per eseguire il failover all'aggiornamento immediato, è necessario usare [sp_link_publication](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md) per definire le credenziali con cui replicare nel server di pubblicazione le modifiche apportate al Sottoscrittore.

4. Nel server di pubblicazione eseguire [sp_addpushsubscription_agent](../../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md). Specificare i parametri seguenti:

    * `@subscriber`, `@subscriber_db` e `@publication`. 

    * Le credenziali di Windows usate per eseguire l'agente di distribuzione nel server di distribuzione per `@job_login` e `@job_password`. 

    > [!NOTE]  
>  Per le connessioni attivate con l'autenticazione integrata di Windows vengono sempre usate le credenziali di Windows specificate da `@job_login` e `@job_password`. L'agente di distribuzione esegue sempre la connessione locale al server di distribuzione utilizzando l'autenticazione integrata di Windows. Per impostazione predefinita, l'agente si connette al Sottoscrittore con l'autenticazione integrata di Windows. 
 
    * (Facoltativo) Il valore `0` per `@subscriber_security_mode` e le informazioni sull'account di accesso di SQL Server per `@subscriber_login` e `@subscriber_password`, se è necessario usare l'autenticazione di SQL Server per la connessione al Sottoscrittore. 

    * Specificare una pianificazione per il processo dell'agente di distribuzione da eseguire per la sottoscrizione.


## Esempio ##

In questo esempio viene creata una sottoscrizione pull ad aggiornamento immediata di una pubblicazione che supporta le sottoscrizioni ad aggiornamento immediato. I valori per l'account di accesso e la relativa password vengono specificati in fase di esecuzione tramite variabili di scripting sqlcmd.

> [!NOTE]  
>  Questo script usa le variabili di scripting di sqlcmd, nel formato `$(MyVariable)`. Per informazioni su come usare le variabili di scripting nella riga di comando e in SQL Server Management Studio, vedere la sezione **Esecuzione di script di replica** nell'argomento [Concetti di base relativi alle stored procedure del sistema di replica](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md).

```
-- Execute this batch at the Subscriber.
DECLARE @publication AS sysname;
DECLARE @publicationDB AS sysname;
DECLARE @publisher AS sysname;
DECLARE @login AS sysname;
DECLARE @password AS nvarchar(512);
SET @publication = N'AdvWorksProductTran';
SET @publicationDB = N'AdventureWorks2008R2';
SET @publisher = $(PubServer);
SET @login = $(Login);
SET @password = $(Password);

-- At the subscription database, create a pull subscription to a transactional 
-- publication using immediate updating with queued updating as a failover.
EXEC sp_addpullsubscription 
    @publisher = @publisher, 
    @publication = @publication, 
    @publisher_db = @publicationDB, 
    @update_mode = N'failover', 
    @subscription_type = N'pull';

-- Add an agent job to synchronize the pull subscription, 
-- which uses Windows Authentication when connecting to the Distributor.
EXEC sp_addpullsubscription_agent 
    @publisher = @publisher, 
    @publisher_db = @publicationDB, 
    @publication = @publication,
    @job_login = @login,
    @job_password = @password; 

-- Add a Windows Authentication-based linked server that enables the 
-- Subscriber-side triggers to make updates at the Publisher. 
EXEC sp_link_publication 
    @publisher = @publisher, 
    @publication = @publication,
    @publisher_db = @publicationDB, 
    @security_mode = 0,
    @login = @login,
    @password = @password;
GO

USE AdventureWorks2008R2;
GO

-- Execute this batch at the Publisher.
DECLARE @publication AS sysname;
DECLARE @subscriptionDB AS sysname;
DECLARE @subscriber AS sysname;
SET @publication = N'AdvWorksProductTran'; 
SET @subscriptionDB = N'AdventureWorks2008R2Replica'; 
SET @subscriber = $(SubServer);

-- At the Publisher, register the subscription, using the defaults.
USE [AdventureWorks2008R2]
EXEC sp_addsubscription 
    @publication = @publication, 
    @subscriber = @subscriber, 
    @destination_db = @subscriptionDB, 
    @subscription_type = N'pull', 
    @update_mode = N'failover';
GO
```

## Vedere anche ##

[Updatable Subscriptions for Transactional Replication](../../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)

[Utilizzo di sqlcmd con variabili di scripting](../../../relational-databases/scripting/use-sqlcmd-with-scripting-variables.md)

[Creare una sottoscrizione aggiornabile di una pubblicazione transazionale (Management Studio)](../../../relational-databases/replication/publish/create-an-updatable-subscription-to-a-transactional-publication.md)
