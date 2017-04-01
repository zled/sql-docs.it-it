---
title: "Scalabilit&#224; | Microsoft Docs"
ms.custom: ""
ms.date: "08/27/2015"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-imoltp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a4891c57-56bb-49f4-9bb5-f11b745279e5
caps.latest.revision: 6
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 6
---
# Scalabilit&#224;
  SQL Server 2016 contiene miglioramenti alla scalabilità per l'archiviazione su disco per le tabelle con ottimizzazione per la memoria.  
  
-   **Più thread per rendere persistenti le tabelle con ottimizzazione per la memoria**  
  
     Nella versione precedente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] era presente un solo thread di gestione del checkpoint offline che analizzava il log delle transazioni per le modifiche alle tabelle con ottimizzazione per la memoria e le rendeva persistenti nei file del checkpoint, ad esempio nei file di dati e differenziali. Con un numero elevato di core, un solo thread di gestione del checkpoint offline potrebbe non essere sufficiente.  
  
     In [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] sono disponibili più thread simultanei responsabili della persistenza delle modifiche nelle tabelle con ottimizzazione per la memoria.  
  
-   **Recupero multithread**  
  
     Nella versione precedente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]l'applicazione del log come parte dell'operazione di recupero era a thread singolo. In [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] l'applicazione del log è multithread.  
  
-   **Operazione MERGE**  
  
     Ora l'operazione MERGE è multithread.  
  
-   **DMV**  
  
     Sono state apportate modifiche significative a [sys.dm_db_xtp_checkpoint_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-stats-transact-sql.md) e [sys.dm_db_xtp_checkpoint_files &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql.md).  
  
 L'unione manuale è stata disabilitata perché si prevede che il carico possa essere gestito da un'unione multithread.  
  
 Il motore OLTP in memoria continua a usare i filegroup con ottimizzazione per la memoria in base a FILESTREAM, ma i singoli file nel filegroup vengono disaccoppiati da FILESTREAM. Questi file sono completamente gestiti dal motore di OLTP in memoria, ad esempio per le operazioni di creazione, eliminazione e Garbage Collection. [DBCC SHRINKFILE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md) non è supportato.  
  
  