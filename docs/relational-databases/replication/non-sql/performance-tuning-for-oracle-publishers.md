---
title: "Ottimizzazione delle prestazioni per i server di pubblicazione Oracle | Microsoft Docs"
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
  - "pubblicazione Oracle [replica di SQL Server], ottimizzazione delle prestazioni"
ms.assetid: 32c0b4ec-c166-45a3-b41e-38a30fd56813
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 34
---
# Ottimizzazione delle prestazioni per i server di pubblicazione Oracle
  È simile all'architettura di pubblicazione Oracle il [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pubblicazione architettura; pertanto il primo passaggio nella replica di Oracle per le prestazioni di ottimizzazione richiede seguendo le indicazioni generali disponibili in [migliorare le prestazioni della replica generale](../../../relational-databases/replication/administration/enhance-general-replication-performance.md).  
  
 Sono inoltre disponibili due opzioni per i server di pubblicazione Oracle relative alle prestazioni:  
  
-   Impostazione dell'opzione di pubblicazione appropriata: Oracle o Oracle Gateway.  
  
-   Configurazione del processo del set di transazioni in modo che le modifiche vengano elaborate sul server di pubblicazione a intervalli appropriati.  
  
## Impostazione dell'opzione di pubblicazione appropriata  
 L'opzione Oracle Gateway offre prestazioni migliori rispetto all'opzione Oracle Complete, ma non è possibile utilizzarla per pubblicare la stessa tabella in più pubblicazioni transazionali. Una tabella può essere visualizzata al massimo in una pubblicazione transazionale e in qualsiasi numero di pubblicazioni snapshot. Se è necessario pubblicare la stessa tabella in più pubblicazioni transazionali, scegliere l'opzione Oracle Complete. Specificare questa opzione quando si identifica il server di pubblicazione Oracle nel server di distribuzione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per ulteriori informazioni, vedere [creare una pubblicazione da un Database Oracle](../../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md).  
  
## Configurazione del processo del set di transazioni  
 Le modifiche apportate alle tabelle Oracle pubblicate vengono elaborate in gruppi definiti set di transazioni. Per garantire la consistenza transazionale, viene eseguito il commit di ogni set di transazioni come una singola transazione nel database di distribuzione. Se le dimensioni del set di transazioni diventano eccessive, non sarà possibile elaborarlo in modo efficiente come una singola transazione.  
  
 Per impostazione predefinita, i set di transazioni vengono creati solo dall'agente di lettura log. Se durante i periodi di elevata attività di modifica l'agente di lettura log non viene eseguito o non è in grado di stabilire una connessione dal server di distribuzione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] al server di pubblicazione Oracle, i set di transazioni possono raggiungere dimensioni ingestibili. Per evitare questo problema, verificare che i set di transazioni vengano creati a intervalli regolari, anche se l'agente di lettura log non viene eseguito o non è in grado di stabilire una connessione dal server di pubblicazione Oracle.  
  
 I set di transazioni possono essere creati tramite il processo Xactset, un processo del database Oracle installato dalla replica, che utilizza lo stesso meccanismo adottato dall'agente di lettura log per creare i set. Ogni volta che il processo viene eseguito, viene creata una nuova transazione. Alla successiva esecuzione dell'agente di lettura log vengono elaborati tutti i set creati. Se dopo l'elaborazione di tutti i set di transazioni esistenti risultano ancora modifiche in sospeso, l'agente di lettura log crea ed elabora uno o più set di transazioni aggiuntivi.  
  
 Per configurare il processo del set di transazioni, vedere [configurazione del processo di Set di transazioni per un server di pubblicazione Oracle & #40; Programmazione Transact-SQL della replica & #41;](../../../relational-databases/replication/administration/configure the transaction set job for an oracle publisher.md).  
  
## Vedere anche  
 [Configurazione di un server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Panoramica della pubblicazione Oracle](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)  
  
  