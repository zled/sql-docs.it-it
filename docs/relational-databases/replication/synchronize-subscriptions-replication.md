---
title: "Sincronizzazione delle sottoscrizioni (replica) | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "sincronizzazione [replica di SQL Server], sottoscrizioni"
  - "sottoscrizioni [replica di SQL Server], sincronizzazione"
  - "replica [SQL Server], sincronizzazione"
ms.assetid: cbe13120-8dd9-4309-88dd-07a801c68f5f
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# Sincronizzazione delle sottoscrizioni (replica)
  Le sottoscrizioni vengono sincronizzate dagli agenti di replica. L'agente di distribuzione sincronizza le sottoscrizioni di pubblicazioni transazionali e snapshot, mentre l'agente di merge sincronizza le sottoscrizioni di pubblicazioni di tipo merge. Per sincronizzare le sottoscrizioni e controllare il comportamento della sincronizzazione, è possibile utilizzare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], le stored procedure di replica e gli oggetti RMO (Replication Management Objects). Negli argomenti seguenti viene descritto come sincronizzare le sottoscrizioni e specificare le opzioni di sincronizzazione.  
  
## Argomenti della sezione  
  
-   [Creazione e applicazione dello snapshot iniziale](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)  
  
-   [Creazione di uno snapshot per una pubblicazione di tipo merge con filtri con parametri](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)  
  
-   [Abilitare l'inizializzazione con un Backup per le pubblicazioni transazionali & #40; SQL Server Management Studio & #41;](../../relational-databases/replication/enable initialization with backup for transactional publications.md)  
  
-   [Inizializzare una sottoscrizione transazionale da un Backup & #40; Programmazione Transact-SQL della replica & #41;](../../relational-databases/replication/initialize a transactional subscription from a backup.md)  
  
-   [Initialize a Subscription Manually](../../relational-databases/replication/initialize-a-subscription-manually.md)  
  
-   [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md)  
  
-   [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md)  
  
-   [Reinizializzare una sottoscrizione](../../relational-databases/replication/reinitialize-a-subscription.md)  
  
-   [Eseguire script prima e dopo aver applicato uno Snapshot & #40; SQL Server Management Studio & #41;](../../relational-databases/replication/execute scripts before and after a snapshot is applied.md)  
  
-   [Esecuzione di script durante la sincronizzazione & #40; Programmazione Transact-SQL della replica & #41;](../../relational-databases/replication/execute-scripts-during-synchronization-replication-transact-sql-programming.md)  
  
-   [Visualizzare e risolvere i conflitti di dati per pubblicazioni di tipo Merge & #40; SQL Server Management Studio & #41;](../../relational-databases/replication/view and resolve data conflicts for merge publications.md)  
  
-   [Visualizza conflitti di dati per le pubblicazioni transazionali e 40 #; SQL Server Management Studio & #41;](../../relational-databases/replication/view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)  
  
-   [Sincronizzare una sottoscrizione tramite Gestione sincronizzazione Microsoft Windows & #40; Gestione sincronizzazione Microsoft Windows & #41;](../../relational-databases/replication/synchronize a subscription using windows synchronization manager.md)  
  
-   [Implementazione di un gestore della logica di business per un articolo di merge](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)  
  
-   [Eseguire il debug di un gestore della logica di Business & #40; Programmazione della replica & #41;](../../relational-databases/replication/debug-a-business-logic-handler-replication-programming.md)  
  
-   [Controllare il comportamento di trigger e vincoli durante la sincronizzazione & #40; Programmazione Transact-SQL della replica & #41;](../../relational-databases/replication/control behavior of triggers and constraints in synchronization.md)  
  
-   [Implement a Custom Conflict Resolver for a Merge Article](../../relational-databases/replication/implement-a-custom-conflict-resolver-for-a-merge-article.md)  
  
## Vedere anche  
 [Sincronizzare i dati](../../relational-databases/replication/synchronize-data.md)  
  
  