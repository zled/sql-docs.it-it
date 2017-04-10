---
title: "Configurazione delle propriet&#224; dello snapshot (programmazione Transact-SQL della replica) | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
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
  - "snapshot [replica di SQL Server], proprietà"
ms.assetid: 978d150f-8971-458a-ab2b-3beba5937b46
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# Configurazione delle propriet&#224; dello snapshot (programmazione Transact-SQL della replica)
  Le proprietà dello snapshot possono essere definite e modificate a livello di programmazione tramite le stored procedure di replica. Le stored procedure utilizzate dipendono dal tipo di pubblicazione.  
  
### Per configurare le proprietà dello snapshot durante la creazione di una pubblicazione snapshot o transazionale  
  
1.  Server di pubblicazione, eseguire [sp_addpublication](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md). Specificare un nome di pubblicazione per **@publication**, un valore di **snapshot** o **Continua** per **@repl_freq**, e uno o più dei parametri relativi snapshot seguenti:  
  
    -   **@alt_snapshot_folder** -specificare un percorso se lo snapshot per questa pubblicazione è accessibile da tale percorso anziché o oltre alla cartella snapshot predefinita.  
  
    -   **@compress_snapshot** -specificare un valore di **true** se i file di snapshot nella cartella snapshot alternativa sono compressi nel [!INCLUDE[msCoName](../../../includes/msconame-md.md)] formato del file CAB.  
  
    -   **@pre_snapshot_script** -specificare il nome di file e percorso completo di un **SQL** file che verrà eseguito nel Sottoscrittore durante l'inizializzazione prima di applicata lo snapshot iniziale.  
  
    -   **@post_snapshot_script** -specificare il nome di file e percorso completo di un **SQL** file che verrà eseguito nel Sottoscrittore durante l'inizializzazione dopo aver applicato lo snapshot iniziale.  
  
    -   **@snapshot_in_defaultfolder** -specificare un valore di **false** Se lo snapshot è disponibile solo in un percorso non predefinito.  
  
     Per ulteriori informazioni sulla creazione di pubblicazioni, vedere [creare una pubblicazione](../../../relational-databases/replication/publish/create-a-publication.md).  
  
### Per configurare le proprietà dello snapshot durante la creazione di una pubblicazione di tipo merge  
  
1.  Server di pubblicazione, eseguire [sp_addmergepublication](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Specificare un nome di pubblicazione per **@publication**, un valore di **snapshot** o **Continua** per **@repl_freq**, e uno o più dei parametri relativi snapshot seguenti:  
  
    -   **@alt_snapshot_folder** -specificare un percorso se lo snapshot per questa pubblicazione è accessibile da tale percorso anziché o oltre alla cartella snapshot predefinita.  
  
    -   **@compress_snapshot** -specificare un valore di **true** se i file di snapshot nella cartella snapshot alternativa sono compressi nel formato di file CAB.  
  
    -   **@pre_snapshot_script** -specificare il nome di file e percorso completo di un **SQL** file che verrà eseguito nel Sottoscrittore durante l'inizializzazione prima di applicata lo snapshot iniziale.  
  
    -   **@post_snapshot_script** -specificare il nome di file e percorso completo di un **SQL** file che verrà eseguito nel Sottoscrittore durante l'inizializzazione dopo aver applicato lo snapshot iniziale.  
  
    -   **@snapshot_in_defaultfolder** -specificare un valore di **false** Se lo snapshot è disponibile solo in un percorso non predefinito.  
  
2.  Per ulteriori informazioni sulla creazione di pubblicazioni, vedere [creare una pubblicazione](../../../relational-databases/replication/publish/create-a-publication.md).  
  
### Per modificare le proprietà dello snapshot di una pubblicazione snapshot o transazionale esistente  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md). Specificare un valore di **1** per **@force_invalidate_snapshot** e uno dei seguenti valori per **@property**:  
  
    -   **alt_snapshot_folder** -anche specificare un nuovo percorso della cartella snapshot alternativa per **@value**.  
  
    -   **compress_snapshot** -inoltre specificare un valore di **true** o **false** per **@value** per indicare se i file di snapshot nella cartella snapshot alternativa sono compressi nel formato di file CAB.  
  
    -   **pre_snapshot_script** anche per **@value** specificare il nome di file e percorso completo di un **SQL** file che verrà eseguito nel Sottoscrittore durante l'inizializzazione prima di applicata lo snapshot iniziale.  
  
    -   **post_snapshot_script** anche per **@value** specificare il nome di file e percorso completo di un **SQL** file che verrà eseguito nel Sottoscrittore durante l'inizializzazione dopo aver applicato lo snapshot iniziale.  
  
    -   **snapshot_in_defaultfolder** -inoltre specificare un valore di **true** o **false** per indicare se lo snapshot è disponibile solo in un percorso non predefinito.  
  
2.  (Facoltativo) Server di pubblicazione nel database di pubblicazione, eseguire [sp_changepublication_snapshot](../../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md). Specificare **@publication** e uno o più parametri pianificazione o la sicurezza delle credenziali da modificare.  
  
    > [!IMPORTANT]  
    >  Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali in un file script, è fondamentale proteggere il file per evitare accessi non autorizzati.  
  
3.  Eseguire il [agente Snapshot repliche](../../../relational-databases/replication/agents/replication-snapshot-agent.md) dal prompt dei comandi o avviare il processo dell'agente Snapshot per generare un nuovo snapshot. Per altre informazioni, vedere [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
### Per modificare le proprietà dello snapshot di una pubblicazione di tipo merge esistente  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md). Specificare un valore di **1** per **@force_invalidate_snapshot** e uno dei seguenti valori per **@property**:  
  
    -   **alt_snapshot_folder** -anche specificare un nuovo percorso della cartella snapshot alternativa per **@value**.  
  
    -   **compress_snapshot** -inoltre specificare un valore di **true** o **false** per **@value** per indicare se i file di snapshot nella cartella snapshot alternativa sono compressi nel formato di file CAB.  
  
    -   **pre_snapshot_script** anche per **@value** specificare il nome di file e percorso completo di un **SQL** file che verrà eseguito nel Sottoscrittore durante l'inizializzazione prima di applicata lo snapshot iniziale.  
  
    -   **post_snapshot_script** anche per **@value** specificare il nome di file e percorso completo di un **SQL** file che verrà eseguito nel Sottoscrittore durante l'inizializzazione dopo aver applicato lo snapshot iniziale.  
  
    -   **snapshot_in_defaultfolder** -inoltre specificare un valore di **true** o **false** per indicare se lo snapshot è disponibile solo in un percorso non predefinito.  
  
2.  Eseguire il [agente Snapshot repliche](../../../relational-databases/replication/agents/replication-snapshot-agent.md) dal prompt dei comandi o avviare il processo dell'agente Snapshot per generare un nuovo snapshot. Per altre informazioni, vedere [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
## Esempio  
 In questo esempio viene creata una pubblicazione che utilizza una cartella snapshot alternativa e uno snapshot compresso.  
  
 [!code-sql[HowTo#sp_mergealtsnapshot](../../../relational-databases/replication/codesnippet/tsql/configure-snapshot-prope_1.sql)]  
  
## Vedere anche  
 [Posizioni alternative della cartella snapshot](../../../relational-databases/replication/alternate-snapshot-folder-locations.md)   
 [Snapshot compressi](../../../relational-databases/replication/compressed-snapshots.md)   
 [Eseguire gli script prima e dopo l'applicazione dello snapshot](../../../relational-databases/replication/execute-scripts-before-and-after-the-snapshot-is-applied.md)   
 [Concetti di base relativi alle stored procedure del sistema di replica](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Trasferimento di snapshot tramite FTP](../../../relational-databases/replication/transfer-snapshots-through-ftp.md)   
 [Modifica delle proprietà di pubblicazioni e articoli](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)  
  
  