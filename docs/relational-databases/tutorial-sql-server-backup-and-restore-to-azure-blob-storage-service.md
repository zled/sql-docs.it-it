---
title: "Esercitazione: Backup e ripristino di SQL Server nel servizio di archiviazione Blob di Windows Azure | Microsoft Docs"
ms.custom: ""
ms.date: "02/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-query-tuning"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016 Preview"
ms.assetid: 9e1d94ce-2c93-45d1-ae2a-2a7d1fa094c4
caps.latest.revision: 11
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 9
---
# Esercitazione: Backup e ripristino di SQL Server nel servizio di archiviazione Blob di Windows Azure
Nell'esercitazione Introduzione al backup e ripristino di SQL Server con il servizio di archiviazione BLOB di Windows Azure sono incluse nozioni utili sulla scrittura di backup in questo servizio e sul ripristino dallo stesso.  
  
## Lezioni dell'esercitazione  
In questa esercitazione viene illustrato come creare un account di archiviazione di Windows, un contenitore BLOB, la creazione di credenziali per l'accesso all'account di archiviazione, la scrittura di un backup nel servizio BLOB e l'esecuzione di un ripristino semplice. Questa esercitazione è suddivisa in quattro lezioni:  
  
[Lezione 1: Creare gli oggetti della risorsa di archiviazione di Windows Azure](../Topic/Lesson%201:%20Create%20Windows%20Azure%20Storage%20Objects.md)  
In questa lezione verranno creati un account di archiviazione e un contenitore BLOB di Windows Azure.  
  
[Lezione 2: Creare una credenziale di SQL Server](../Topic/Lesson%202:%20Create%20a%20SQL%20Server%20Credential.md)  
In questa lezione verranno create le credenziali per archiviare le informazioni di sicurezza utilizzate per accedere all'account di archiviazione di Windows Azure.  
  
[Lezione 3: Scrivere un backup completo del database nel servizio di archiviazione BLOB di Windows Azure](../Topic/Lesson%203:%20Write%20a%20Full%20Database%20Backup%20to%20the%20Windows%20Azure%20Blob%20Storage%20Service.md)  
In questa lezione verrà eseguita un'istruzione T-SQL per scrivere un backup del database AdventureWorks2012 nel servizio di archiviazione BLOB di Windows Azure.  
  
[Lezione 4: Eseguire un ripristino da un backup completo del database](../Topic/Lesson%204:%20Perform%20a%20Restore%20From%20a%20Full%20Database%20Backup.md)  
In questa lezione verrà eseguita un'istruzione T-SQL per il ripristino dal backup del database creato nella lezione precedente.  
  
### Requisiti  
Per completare questa esercitazione, è necessario avere familiarità con [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] di backup e ripristino concetti e la sintassi T-SQL. Per utilizzare l'esercitazione, il sistema deve soddisfare i requisiti seguenti.  
  
-   Un'istanza di [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]e il database AdventureWorks2012 installati.  
  
    L'istanza di SQL Server può essere in locale o in una macchina virtuale di Windows Azure.  
  
    È possibile utilizzare un database utente al posto di AdventureWorks2012 e modificare la sintassi tsql di conseguenza.  
  
-   All'account utente usato per eseguire i comandi BACKUP o RESTORE deve essere associato il ruolo del database **db_backup operator** con autorizzazioni **Modifica qualsiasi credenziale**.  
  
### Ulteriori informazioni  
Di seguito sono indicati alcuni argomenti consigliati per comprendere i concetti e le procedure consigliate quando si utilizza il servizio di archiviazione BLOB di Windows Azure per i backup di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
1.  [Backup e ripristino di SQL Server con il servizio di archiviazione BLOB di Microsoft Azure](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
2.  [Procedure consigliate e risoluzione dei problemi per il backup di SQL Server nell'URL](../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
## Vedere anche  
[Backup del database e del log](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md#databaselog)  
[Creazione di un backup di file completo del filegroup primario](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md#filegroups)  
[Ripristino di un database e spostamento dei file](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md#restoredbwithmove)  
  
