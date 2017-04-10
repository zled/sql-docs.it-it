---
title: "Amministrazione di una topologia peer-to-peer (programmazione Transact-SQL della replica) | Microsoft Docs"
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
  - "replica transazionale, replica peer-to-peer"
ms.assetid: 4d0fa941-f9ea-4a14-aed9-34df593fc6f2
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# Amministrazione di una topologia peer-to-peer (programmazione Transact-SQL della replica)
  L'amministrazione di una topologia peer-to-peer è simile all'amministrazione di una tipica topologia di replica transazionale, sebbene diverse aree richiedano speciali considerazioni. La differenza principale nell'amministrazione di una topologia peer-to-peer è che alcune modifiche richiedono il sistema sia *inattivo*. Mettere in stato di inattività un sistema significa arrestare le attività sulle tabelle pubblicate in tutti i nodi e verificare che ogni nodo abbia ricevuto tutte le modifiche dagli altri nodi. Per ulteriori informazioni, vedere [mettere una topologia di replica & #40; Programmazione Transact-SQL della replica & #41;](../../../relational-databases/replication/administration/quiesce-a-replication-topology-replication-transact-sql-programming.md).  
  
> [!NOTE]  
>  In una topologia peer-to-peer il database di distribuzione non può utilizzare una versione precedente di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] rispetto a un Sottoscrittore pull.  
  
### Per aggiungere un articolo a una configurazione esistente  
  
1.  Mettere in stato di inattività il sistema.  
  
2.  Arrestare l'agente di distribuzione in ciascun nodo nella topologia. Per ulteriori informazioni, vedere [concetti eseguibili agente di replica](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md) o [avviare e arrestare un agente di replica & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
3.  Eseguire l'istruzione CREATE TABLE per aggiungere la tabella nuova a ogni nodo nella topologia.  
  
4.  Effettuare manualmente la copia bulk dei dati per la nuova tabella in tutti i nodi utilizzando l' [utilità bcp](../../../tools/bcp-utility.md).  
  
5.  Eseguire [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) per creare il nuovo articolo in ogni nodo nella topologia. Per altre informazioni, vedere [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
    > [!NOTE]  
    >  Dopo aver [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) viene eseguita, la replica aggiunge automaticamente l'articolo per le sottoscrizioni nella topologia.  
  
6.  Riavviare gli agenti di distribuzione in ciascun nodo nella topologia.  
  
### Per apportare le modifiche dello schema nel database di pubblicazione  
  
1.  Mettere in stato di inattività il sistema.  
  
2.  Eseguire le istruzioni DLL (Data Definition Language) per modificare lo schema delle tabelle pubblicate. Per ulteriori informazioni sulle modifiche dello schema supportate, vedere [apportare le modifiche dello Schema nei database di pubblicazione](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).  
  
3.  Prima di riprendere l'attività nelle tabelle pubblicate, mettere di nuovo il sistema in stato di inattività. Ciò garantisce che le modifiche dello schema siano ricevute da tutti i nodi prima che venga eseguita la replica di nuove modifiche dei dati.  
  
## Esempio  
 Nell'esempio seguente è illustrato come aggiungere un nuovo articolo di tabella a una topologia di replica peer-to-peer esistente con due nodi.  
  
 [!code-sql[HowTo#sp_addp2particle_createtables](../../../relational-databases/replication/codesnippet/tsql/administer-a-peer-to-pee_1.sql)]  
  
 [!code-sql[HowTo#sp_addp2particle_cmdline](../../../relational-databases/replication/codesnippet/tsql/administer-a-peer-to-pee_2.sql)]  
  
 [!code-sql[HowTo#sp_addp2particle_createarticle](../../../relational-databases/replication/codesnippet/tsql/administer-a-peer-to-pee_3.sql)]  
  
## Vedere anche  
 [Amministrazione & #40; Replica & #41;](../../../relational-databases/replication/administration/administration-replication.md)   
 [Backup e ripristino di database SQL Server](../../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [Replica transazionale peer-to-peer](../../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  