---
title: "Prerequisiti per la registrazione minima nell&#39;importazione bulk | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-bulk-import-export"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "registrazione minima [SQL Server]"
  - "copia bulk con registrazione [SQL Server]"
  - "log [SQL Server], registrazione minima"
  - "operazioni con registrazione minima [SQL Server]"
  - "importazione bulk [SQL Server], registrazione minima"
ms.assetid: bd1dac6b-6ef8-4735-ad4e-67bb42dc4f66
caps.latest.revision: 48
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 47
---
# Prerequisiti per la registrazione minima nell&#39;importazione bulk
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Per un database con modello di recupero con registrazione completa, tutte le operazioni di inserimento di righe eseguite durante l'importazione bulk vengono registrate in modo completo nel log delle transazioni. In caso di importazioni di grandi quantità di dati, l'utilizzo del modello di recupero con registrazione completa può causare un rapido esaurimento dello spazio disponibile nel log. Nel caso si utilizzi un modello di recupero con registrazione minima o un modello di recupero con registrazione minima delle operazioni bulk invece, la registrazione minima delle operazioni di importazione bulk riduce la possibilità che un'operazione di questo tipo esaurisca lo spazio nel log. La registrazione minima inoltre è più efficiente di quella completa.  
  
> [!NOTE]  
>  Il modello di recupero con registrazione minima delle operazioni bulk è progettato per sostituire temporaneamente il modello di recupero con registrazione completa durante le operazioni bulk di notevoli dimensioni.  
  
## Requisiti della tabella per la registrazione minima di operazioni di importazione bulk  
 La registrazione minima richiede che la tabella di destinazione soddisfi le condizioni seguenti:  
  
-   La tabella di destinazione non viene replicata.  
  
-   Il blocco di tabella è specificato (utilizzando TABLOID). Per la tabella con indice columnstore di cluster, non è necessaria l'opzione TABLOCK per la registrazione minima.  Inoltre, viene eseguita la registrazione minima solo del caricamento dei dati in gruppi di righe compressi, che richiede una proprietà batchsize pari a 102400 o superiori.  
  
    > [!NOTE]  
    >  Sebbene gli inserimenti di dati non vengano registrati nel log delle transazioni quando viene eseguita un'importazione bulk con registrazione minima, nel [!INCLUDE[ssDE](../../includes/ssde-md.md)] vengono registrate le allocazioni degli extent per ogni nuovo extent allocato alla tabella.  
  
-   Questa non è una tabella con ottimizzazione per la memoria.  
  
 La registrazione minima in una tabella dipende inoltre dal fatto che la tabella sia indicizzata e, in tal caso, dal fatto che sia vuota:  
  
-   Se la tabella non include indici, le pagine di dati vengono registrate tramite registrazione minima.  
  
-   Se la tabella non include indici cluster ma uno o più indici non cluster, le pagine di dati vengono sempre registrate con registrazione minima. La modalità di registrazione delle pagine di indice, tuttavia, dipende dal fatto che la tabella sia o meno vuota:  
  
    -   Se la tabella è vuota, le pagine di indice vengono registrate tramite registrazione minima.  
  
    -   Se la tabella non è vuota, le pagine di indice vengono registrate tramite registrazione completa.  
  
        > [!NOTE]  
        >  Se si parte da una tabella vuota e si esegue l'importazione bulk dei dati in più batch, per il primo batch le pagine di indice e di dati vengono registrate con registrazione minima. A partire dal secondo batch, tuttavia, la registrazione minima viene applicata solo alle pagine di dati.  
  
-   Se la tabella include un indice cluster ed è vuota, le pagine di dati e di indice vengono registrate tramite registrazione minima. Se, invece, una tabella include un indice cluster basato sull'albero B e non è vuota, le pagine di dati e di indice vengono registrate con registrazione completa indipendentemente dal modello di recupero. Per le tabelle con indice columnstore di cluster, viene sempre eseguita la registrazione minima del caricamento dei dati nel gruppo di righe compresso indipendentemente dal fatto che la tabella sia vuota o no quando la proprietà batchsize > = 102400.  
  
    > [!NOTE]  
    >  Se si parte da una tabella rowstore vuota e si esegue l'importazione bulk dei dati in batch, per il primo batch le pagine di indice e di dati vengono registrate con registrazione minima. A partire dal secondo batch, tuttavia, la registrazione minima viene applicata solo alle pagine di dati.  
  
> [!NOTE]  
>  Quando la replica transazionale è abilitata, le operazioni BULK INSERT vengono registrate completamente persino nel modello di recupero con registrazione minima delle operazioni bulk.  
  
##  <a name="RelatedTasks"></a> Attività correlate  
  
-   [Visualizzazione o modifica del modello di recupero di un database &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md)  
  
 ![Icona freccia usata con il collegamento Torna all'inizio](../../analysis-services/instances/media/uparrow16x16.png "Icona freccia usata con il collegamento Torna all'inizio") [&#91;Torna all'inizio&#93;](#Top)  
  
## Vedere anche  
 [Modelli di recupero &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md)   
 [Utilità bcp](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md)   
 [OPENROWSET &#40;Transact-SQL&#41;](../../t-sql/functions/openrowset-transact-sql.md)   
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [Hint di tabella &#40;Transact-SQL&#41;](../Topic/Table%20Hints%20\(Transact-SQL\).md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)  
  
  