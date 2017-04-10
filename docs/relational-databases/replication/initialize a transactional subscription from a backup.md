---
title: "Inizializzazione di una sottoscrizione transazionale da un backup (programmazione Transact-SQL della replica) | Microsoft Docs"
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
  - "manual subscription initialization [SQL Server replication]"
  - "subscriptions [SQL Server replication], initializing"
  - "inizializzazione delle sottoscrizioni [replica di SQL Server], senza snapshot"
  - "replica transazionale, backup e ripristino"
  - "backup [replica di SQL Server], replica transazionale"
ms.assetid: d0637fc4-27cc-4046-98ea-dc86b7a3bd75
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Inizializzazione di una sottoscrizione transazionale da un backup (programmazione Transact-SQL della replica)
  Anche se una sottoscrizione di una pubblicazione transazionale viene in genere inizializzata con uno snapshot, è possibile inizializzarla da un backup utilizzando le stored procedure di replica. Per ulteriori informazioni, vedere [inizializzare una sottoscrizione transazionale senza uno Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
### Per inizializzare un Sottoscrittore transazionale da un backup  
  
1.  Per una pubblicazione esistente, assicurarsi che la pubblicazione supporta la possibilità di inizializzazione da backup eseguendo [sp_helppublication & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) nel server di pubblicazione nel database di pubblicazione. Prendere nota del valore di **allow_initialize_from_backup** nel set di risultati.  
  
    -   Se il valore è **1**, la pubblicazione supporta questa funzionalità.  
  
    -   Se il valore è **0**, eseguire [sp_changepublication & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md) nel server di pubblicazione nel database di pubblicazione. Specificare un valore di **allow_initialize_from_backup** per **@property** e il valore **true** per **@value**.  
  
2.  Per una nuova pubblicazione, eseguire [sp_addpublication & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md) nel server di pubblicazione nel database di pubblicazione. Specificare un valore di **true** per **allow_initialize_from_backup**. Per altre informazioni, vedere [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
    > [!WARNING]  
    >  Per evitare la perdita di dati del sottoscrittore, quando si utilizza **sp_addpublication** con `@allow_initialize_from_backup = N'true'`, utilizzare sempre `@immediate_sync = N'true'`.  
  
3.  Creare un backup del database di pubblicazione utilizzando il [BACKUP & #40; Transact-SQL & #41;](../../t-sql/statements/backup-transact-sql.md) istruzione.  
  
4.  Ripristinare il backup nel Sottoscrittore utilizzando il [Ripristina & #40; Transact-SQL & #41;](../Topic/RESTORE%20\(Transact-SQL\).md) istruzione.  
  
5.  Nel server di pubblicazione nel database di pubblicazione, eseguire la stored procedure [sp_addsubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Specificare i parametri seguenti:  
  
    -   **@sync_type** -il valore **inizializzazione con backup**.  
  
    -   **@backupdevicetype** -tipo di dispositivo di backup: **logico** (predefinito), **disco**, o **nastro**.  
  
    -   **@backupdevicename** -il dispositivo di backup logico o fisico da utilizzare per il ripristino.  
  
         Per un dispositivo logico, specificare il nome del dispositivo di backup specificato quando **sp_addumpdevice** utilizzato per creare il dispositivo.  
  
         Per un dispositivo fisico, specificare un nome e un percorso completo di file, ad esempio `DISK = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\BACKUP\Mybackup.dat'` o `TAPE = '\\.\TAPE0'`.  
  
    -   (Facoltativo) **@password** -una password che è stata fornita quando è stato creato il set di backup.  
  
    -   (Facoltativo) **@mediapassword** -una password che è stata fornita quando il set di supporti è stato formattato.  
  
    -   (Facoltativo) **@fileidhint** -identificatore per il set di backup da ripristinare. Ad esempio, specificando **1** indica il primo set di backup nel supporto di backup e **2** indica il secondo set di backup.  
  
    -   (Facoltativo per i dispositivi a nastro) **@unload** -specificare un valore di **1** (predefinito) se il nastro deve essere scaricato dall'unità dopo il ripristino è stato completato e **0** Se non deve essere scaricato.  
  
6.  (Facoltativo) Per una sottoscrizione pull, eseguire [sp_addpullsubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md) e [sp_addpullsubscription_agent & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md) nel database di sottoscrizione del sottoscrittore. Per altre informazioni, vedere [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md).  
  
7.  (Facoltativo) Avviare l'agente di distribuzione. Per ulteriori informazioni, vedere [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) o [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
## Vedere anche  
 [Copiare database tramite backup e ripristino](../../relational-databases/databases/copy-databases-with-backup-and-restore.md)   
 [Backup e ripristino di database SQL Server](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
  