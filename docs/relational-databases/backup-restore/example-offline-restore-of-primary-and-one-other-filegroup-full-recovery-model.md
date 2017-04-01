---
title: "Esempio: Ripristino offline del filegroup primario e di un altro filegroup (modello di recupero con registrazione completa) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modello di recupero con registrazione completa [SQL Server], esempio RESTORE"
  - "ripristini offline [SQL Server]"
  - "sequenze di ripristino [SQL Server], offline"
ms.assetid: 7d6c50eb-dc84-4d66-855a-0b5f1bd89737
caps.latest.revision: 32
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 32
---
# Esempio: Ripristino offline del filegroup primario e di un altro filegroup (modello di recupero con registrazione completa)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Le informazioni contenute in questo argomento sono rilevanti solo per i database basati sul modello di recupero con registrazione completa che includono più filegroup.  
  
 In questo esempio un database denominato `adb` contiene tre filegroup. I filegroup `A` e `C` sono di lettura/scrittura, mentre il filegroup `B` è di sola lettura. Il filegroup primario e il filegroup `B` sono danneggiati, mentre i filegroup `A` e `C` sono integri. Prima dell'emergenza, tutti i filegroup erano online.  
  
 L'amministratore del database decide di ripristinare e recuperare il filegroup primario e il filegroup `B`. Dato che il database utilizza il modello di recupero con registrazione completa, prima dell'avvio del ripristino è necessario eseguire un backup della parte finale del log per il database. Non appena il database è online, viene attivata automaticamente la modalità online per i filegroup `A` e `C`.  
  
> [!NOTE]  
>  La sequenza di ripristino offline prevede un numero di passaggi inferiore rispetto al ripristino online di un file di sola lettura. Per un esempio, vedere [Esempio: Ripristino in linea di un file di sola lettura &#40;modello di recupero con registrazione completa&#41;](../../relational-databases/backup-restore/example-online-restore-of-a-read-only-file-full-recovery-model.md). L'intero database, tuttavia, rimane in modalità offline per tutta la durata della sequenza.  
  
## Backup della parte finale del log  
 Prima di ripristinare il database, è necessario che l'amministratore del database esegua il backup della parte finale del log. Dato che il database è danneggiato, la creazione di tale backup richiede l'utilizzo dell'opzione NO_TRUNCATE:  
  
```  
BACKUP LOG adb TO tailLogBackup   
   WITH NORECOVERY, NO_TRUNCATE  
```  
  
 Il backup della parte finale del log è l'ultimo backup applicato nelle sequenze di ripristino seguenti.  
  
## Sequenza di ripristino  
 Per ripristinare il filegroup primario e il filegroup `B`, l'amministratore del database utilizza una sequenza di ripristino senza l'opzione PARTIAL, come illustrato di seguito:  
  
```  
RESTORE DATABASE adb FILEGROUP='Primary' FROM backup1   
WITH NORECOVERY  
RESTORE DATABASE adb FILEGROUP='B' FROM backup2   
WITH NORECOVERY  
RESTORE LOG adb FROM backup3 WITH NORECOVERY  
RESTORE LOG adb FROM backup4 WITH NORECOVERY  
RESTORE LOG adb FROM backup5 WITH NORECOVERY  
RESTORE LOG adb FROM tailLogBackup WITH RECOVERY  
```  
  
 Per i file non ripristinati viene attivata automaticamente la modalità online. Tutti i filegroup sono ora online.  
  
## Vedere anche  
 [Ripristino in linea &#40;SQL Server&#41;](../../relational-databases/backup-restore/online-restore-sql-server.md)   
 [Ripristini a fasi &#40;SQL Server&#41;](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md)   
 [Ripristini di file &#40;modello di recupero con registrazione completa&#41;](../../relational-databases/backup-restore/file-restores-full-recovery-model.md)   
 [Applicare backup del log delle transazioni &#40;SQL Server&#41;](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)  
  
  