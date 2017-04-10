---
title: "Eseguire gli script prima e dopo l&#39;applicazione dello snapshot | Microsoft Docs"
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
  - "snapshot [replica di SQL Server], script"
  - "script [replica di SQL Server], snapshot"
  - "replica snapshot [SQL Server], script"
  - "script [replica di SQL Server]"
ms.assetid: 9a6872c2-9bed-477f-9d2f-332d640edcf2
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# Eseguire gli script prima e dopo l&#39;applicazione dello snapshot
  È possibile specificare gli script da eseguire nel Sottoscrittore prima o dopo l'applicazione dello snapshot. È possibile utilizzare script per diversi scopi, ad esempio per creare account di accesso e schemi (proprietari di oggetti) in ogni Sottoscrittore.  
  
 Dopo avere specificato un percorso per ogni script, l'agente snapshot copia i file script nella cartella snapshot corrente ogni volta che viene eseguita l'elaborazione dello snapshot. Quando si applica uno snapshot, l'agente di distribuzione o l'agente di merge esegue lo script pre-snapshot prima di qualsiasi script degli oggetti replicati. L'agente di distribuzione o l'agente di merge esegue lo script post-snapshot dopo l'applicazione di tutti gli altri script degli oggetti replicati e dei dati. Al termine dell'applicazione dello snapshot e dell'esecuzione corretta dei file script, gli script vengono rimossi dalla directory di lavoro del Sottoscrittore.  
  
 Lo script viene eseguito avviando il **sqlcmd** utilità. Prima di distribuire uno script, eseguirlo con **sqlcmd** a garantire la corretta esecuzione. È necessario che il contenuto degli script eseguiti prima e dopo l'applicazione dello snapshot sia ripetibile. Se, ad esempio, si crea una tabella nello script, è innanzitutto necessario verificarne l'esistenza e, in tal caso, eseguire le azioni appropriate. Lo script deve essere ripetibile perché, se è necessario reinizializzare una sottoscrizione per cui lo script è già stato applicato, lo script viene applicato nuovamente in corrispondenza dell'applicazione del nuovo snapshot in fase di reinizializzazione.  
  
 Se il file di snapshot viene compresso in formato [!INCLUDE[msCoName](../../includes/msconame-md.md)] CAB, vengono compressi e inclusi nel file CAB anche gli script. Dopo il trasferimento e la decompressione del file di snapshot compresso in una directory di lavoro nel Sottoscrittore, vengono eseguiti tutti gli script indicati come pre-snapshot. In modo analogo, tutti gli script post-snapshot vengono decompressi ed eseguiti nel Sottoscrittore come ultimo passaggio dell'applicazione dello snapshot.  
  
 **Per eseguire gli script prima e dopo l'applicazione dello snapshot**  
  
-   [! Includi [ssManStudioFull] (... / Token/ssManStudioFull_md.md)]: [How to: Execute Scripts Before and After a Snapshot is Applied \(SQL Server Management Studio\)](../../relational-databases/replication/execute scripts before and after a snapshot is applied.md)  
  
-   Replica [!INCLUDE[tsql](../../includes/tsql-md.md)] di programmazione: [configurare le proprietà dello Snapshot & #40; Programmazione Transact-SQL della replica & #41;](../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)  
  
## Vedere anche  
 [Inizializzazione di una sottoscrizione con uno snapshot](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [Opzioni per gli snapshot](../../relational-databases/replication/snapshot-options.md)  
  
  