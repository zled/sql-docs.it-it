---
title: "Creare e applicare lo snapshot | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "snapshot [replica di SQL Server], applicazione"
  - "snapshot [replica di SQL Server], creazione"
ms.assetid: 631f48bf-50c9-4015-b9d8-8f1ad92d1ee2
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# Creare e applicare lo snapshot
  Gli snapshot vengono generati dall'agente snapshot al termine della creazione di una pubblicazione. La generazione può essere eseguita:  
  
-   Immediatamente. Per impostazione predefinita, per una pubblicazione di tipo merge uno snapshot viene generato immediatamente dopo la creazione di una pubblicazione mediante la Creazione guidata nuova pubblicazione.  
  
-   A un'ora pianificata. Specificare una pianificazione sul **agente Snapshot** pagina della procedura guidata nuova pubblicazione o quando si utilizzano stored procedure o gli oggetti RMO (Replication Management Objects).  
  
-   Manualmente. Eseguire l'agente snapshot dal prompt dei comandi o da [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Per ulteriori informazioni sull'esecuzione degli agenti, vedere [concetti eseguibili agente di replica](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md) e [avviare e arrestare un agente di replica & #40; SQL Server Management Studio & #41;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
 Per la replica di tipo merge, viene generato uno snapshot a ogni esecuzione dell'agente snapshot. Per la replica transazionale, la generazione dello snapshot dipende dall'impostazione della proprietà di pubblicazione **immediate_sync**. Se tale proprietà è impostata su TRUE, ovvero il valore predefinito quando si utilizza la Creazione guidata nuova pubblicazione, viene generato uno snapshot ogni volta che viene eseguito l'agente snapshot, che può essere applicato a un Sottoscrittore in qualsiasi momento. Se la proprietà è impostata su FALSE (impostazione predefinita quando si utilizza **sp_addpublication**), lo snapshot viene generato solo se è stato aggiunto un nuovo abbonamento poiché l'agente Snapshot ultima esecuzione. I sottoscrittori devono attendere l'agente Snapshot per il completamento prima di poter eseguire la sincronizzazione.  
  
 Per impostazione predefinita, una volta generati gli snapshot vengono salvati nella cartella snapshot predefinita nel server di distribuzione. È anche possibile salvare i file di snapshot su supporti rimovibili come dischi rimovibili, CD-ROM o in posizioni diverse dalla cartella snapshot predefinita. È inoltre possibile comprimere i file in modo da semplificarne l'archiviazione e il trasferimento ed eseguire script prima o dopo aver applicato lo snapshot nel Sottoscrittore. Per ulteriori informazioni su queste opzioni, vedere [Opzioni Snapshot](../../relational-databases/replication/snapshot-options.md).  
  
 Se lo snapshot è per una pubblicazione di tipo merge che utilizza filtri con parametri, verrà creato utilizzando un processo a due fasi. Viene innanzitutto creato uno snapshot dello schema contenente gli script di replica e lo schema degli oggetti pubblicati, ma non i dati. Ogni sottoscrizione viene quindi inizializzata con uno snapshot che include gli script e lo schema copiati dallo snapshot dello schema e i dati appartenenti alla partizione della sottoscrizione. Per altre informazioni, vedere [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md).  
  
 Dopo aver creato lo snapshot nel server di pubblicazione e averlo archiviato in una posizione snapshot predefinita o alternativa, sarà possibile trasferirlo nel Sottoscrittore e applicarlo. L'agente di distribuzione (per la replica snapshot o transazionale) o l'agente di merge (per la replica di tipo merge) trasferisce lo snapshot e applica lo schema e i file di dati al database di sottoscrizione sul Sottoscrittore durante la sincronizzazione iniziale. Per impostazione predefinita, se si utilizza la Creazione guidata nuova sottoscrizione la sincronizzazione iniziale viene eseguita subito dopo la creazione di una sottoscrizione. Questo comportamento è controllato dal **quando** opzione il **inizializzazione sottoscrizioni** pagina della procedura guidata. Gli snapshot generati in seguito all'inizializzazione di una sottoscrizione non vengono applicati a un Sottoscrittore a meno che la sottoscrizione non sia contrassegnata per la reinizializzazione. Per ulteriori informazioni, vedere [reinizializzare le sottoscrizioni](../../relational-databases/replication/reinitialize-subscriptions.md).  
  
 Dopo aver applicato lo snapshot iniziale, l'agente di distribuzione o l'agente di merge propaga gli aggiornamenti successivi e le altre modifiche dei dati. La distribuzione e l'applicazione degli snapshot nei Sottoscrittori hanno effetto solamente sui Sottoscrittori in attesa dello snapshot iniziale o di nuovi snapshot, mentre non hanno alcun effetto sui Sottoscrittori della pubblicazione in cui sono già state eseguite operazioni di inserimento, aggiornamento ed eliminazione o altre modifiche dei dati pubblicati.  
  
 Per creare e applicare lo snapshot iniziale, [creare e applicare lo Snapshot iniziale](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
 Per visualizzare o modificare la posizione della cartella snapshot predefinita, vedere  
  
-   [! Includi [ssManStudioFull] (... / Token/ssManStudioFull_md.md)]: [Specify the Default Snapshot Location &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/specify-the-default-snapshot-location-sql-server-management-studio.md)  
  
-   Programmazione della replica e programmazione di RMO: [Configura pubblicazione e distribuzione](../../relational-databases/replication/configure-publishing-and-distribution.md)  
  
## Vedere anche  
 [Inizializzazione di una sottoscrizione con uno snapshot](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [Sicurezza della cartella snapshot](../../relational-databases/replication/security/secure-the-snapshot-folder.md)   
 [sp_addpublication & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)  
  
  