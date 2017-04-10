---
title: "Inizializzazione manuale di una sottoscrizione | Microsoft Docs"
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
  - "manual subscription initialization [SQL Server replication]"
  - "subscriptions [SQL Server replication], initializing"
  - "inizializzazione della sottoscrizioni [replica di SQL Server], senza snapshot"
ms.assetid: 27a1bc38-e498-4fff-8082-04b52aa4b22c
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# Inizializzazione manuale di una sottoscrizione
  In questo argomento si descrive come inizializzare manualmente una sottoscrizione in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Anche se per inizializzare una sottoscrizione viene in genere utilizzato lo snapshot iniziale, è possibile inizializzare le sottoscrizioni di pubblicazioni senza uno snapshot, purché lo schema e i dati iniziali siano già presenti nel Sottoscrittore.  
  

##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Se in un database pubblicato tramite la replica transazionale sono in corso delle attività nell'intervallo di tempo che intercorre tra la copia dei dati e dello schema nel Sottoscrittore e l'inizializzazione manuale della sottoscrizione, è possibile che le modifiche risultanti da tali attività non vengano replicate nel Sottoscrittore.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Per inizializzare manualmente una sottoscrizione a una pubblicazione, copiare lo schema e, se necessario, i dati nel database di sottoscrizione. Lo schema e i dati devono corrispondere a quelli presenti nel database di pubblicazione. Specificare quindi che la sottoscrizione non richiede schema e dati nella pagina **Inizializzazione sottoscrizioni** della Creazione guidata nuova sottoscrizione. Per ulteriori informazioni sull'accesso a questa procedura guidata, vedere [inizializzare una sottoscrizione transazionale senza uno Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md) e [creare una sottoscrizione Pull](../../relational-databases/replication/create-a-pull-subscription.md).  
  
 Quando si sincronizza la sottoscrizione per la prima volta, gli oggetti e i metadati necessari per la replica vengono copiati nel database di sottoscrizione.  
  
#### Per inizializzare manualmente una sottoscrizione a una pubblicazione  
  
1.  Verificare che lo schema e i dati vengano copiati nel database di sottoscrizione.  
  
2.  Deselezionare la casella di controllo **Inizializza** nella pagina **Inizializzazione sottoscrizioni** della Creazione guidata nuova sottoscrizione. Eseguire questa procedura per ogni sottoscrizione che richiede la copia solo degli oggetti e dei metadati di replica.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 È possibile inizializzare manualmente le sottoscrizioni tramite le stored procedure di replica.  
  
#### Per inizializzare manualmente una sottoscrizione pull di una pubblicazione transazionale  
  
1.  Verificare che lo schema e i dati esistano nel database di sottoscrizione. Per ulteriori informazioni, vedere [inizializzare una sottoscrizione transazionale senza uno Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
2.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Specificare **@publication**, **@subscriber**, il nome del database nel Sottoscrittore contenente i dati pubblicati per **@destination_db**, un valore di **pull** per **@subscription_type**, e il valore **solo supporto replica** per **@sync_type**. Per altre informazioni, vedere [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md).  
  
3.  Nel Sottoscrittore eseguire [sp_addpullsubscription](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md). Per le sottoscrizioni aggiornabili, vedere [creare una sottoscrizione aggiornabile di una pubblicazione transazionale](https://technet.microsoft.com/library/ms152769(v=sql.130).aspx).  
  
4.  Nel Sottoscrittore eseguire [sp_addpullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md). Per altre informazioni, vedere [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md).  
  
5.  Avviare l'agente di distribuzione per trasferire gli oggetti di replica e scaricare le modifiche più recenti dal server di pubblicazione. Per altre informazioni, vedere [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
#### Per inizializzare manualmente una sottoscrizione push di una pubblicazione transazionale  
  
1.  Verificare che lo schema e i dati esistano nel database di sottoscrizione. Per ulteriori informazioni, vedere [inizializzare una sottoscrizione transazionale senza uno Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
2.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Specificare il nome del database nel Sottoscrittore contenente i dati pubblicati per **@destination_db**, un valore di **push** per **@subscription_type**, e il valore **solo supporto replica** per **@sync_type**. Per le sottoscrizioni aggiornabili, vedere [creare una sottoscrizione aggiornabile di una pubblicazione transazionale](https://technet.microsoft.com/library/ms152769(v=sql.130).aspx).  
  
3.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addpushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md). Per altre informazioni, vedere [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md).  
  
4.  Avviare l'agente di distribuzione per trasferire gli oggetti di replica e scaricare le modifiche più recenti dal server di pubblicazione. Per altre informazioni, vedere [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
#### Per inizializzare manualmente una sottoscrizione pull di una pubblicazione di tipo merge  
  
1.  Verificare che lo schema e i dati esistano nel database di sottoscrizione. Questa verifica può essere eseguita ripristinando un backup del database di pubblicazione nel Sottoscrittore.  
  
2.  Server di pubblicazione, eseguire [sp_addmergesubscription](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md). Specificare **@publication**, **@subscriber**, **@subscriber_db**, e il valore **pull** per **@subscription_type**. In questo modo la sottoscrizione pull viene registrata.  
  
3.  Sottoscrittore per il database contenente i dati pubblicati, eseguire [sp_addmergepullsubscription](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md). Specificare un valore di **Nessuno** per **@sync_type**.  
  
4.  Il sottoscrittore, eseguire [sp_addmergepullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md). Per altre informazioni, vedere [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md).  
  
5.  Avviare l'agente di merge per trasferire gli oggetti di replica e scaricare le modifiche più recenti dal server di pubblicazione. Per altre informazioni, vedere [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
#### Per inizializzare manualmente una sottoscrizione push di una pubblicazione di tipo merge  
  
1.  Verificare che lo schema e i dati esistano nel database di sottoscrizione. Questa verifica può essere eseguita ripristinando un backup del database di pubblicazione nel Sottoscrittore.  
  
2.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addmergesubscription](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md). Specificare il nome del database nel Sottoscrittore contenente i dati pubblicati per **@subscriber_db**, un valore di **push** per **@subscription_type**, e il valore **Nessuno** per **@sync_type**.  
  
3.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addmergepushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql.md). Per altre informazioni, vedere [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md).  
  
4.  Avviare l'agente di merge per trasferire gli oggetti di replica e scaricare le modifiche più recenti dal server di pubblicazione. Per altre informazioni, vedere [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
## Vedere anche  
 [Inizializzazione di una sottoscrizione transazionale senza uno snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)   
 [Backup e ripristino di database replicati](../../relational-databases/replication/administration/back-up-and-restore-replicated-databases.md)   
 [Procedure consigliate per la sicurezza della replica](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  