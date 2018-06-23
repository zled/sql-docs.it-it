---
title: 'Esercitazione: Servizio di archiviazione Blob SQL Server Backup e ripristino di Microsoft Azure | Documenti Microsoft'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e1d94ce-2c93-45d1-ae2a-2a7d1fa094c4
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 85f16d4f3a96c8d661981a998eab93eaffdc67d7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36171181"
---
# <a name="tutorial-sql-server-backup-and-restore-to-windows-azure-blob-storage-service"></a>Esercitazione: Backup e ripristino di SQL Server nel servizio di archiviazione Blob di Windows Azure
  Nell'esercitazione Introduzione al backup e ripristino di SQL Server con il servizio di archiviazione BLOB di Windows Azure sono incluse nozioni utili sulla scrittura di backup in questo servizio e sul ripristino dallo stesso.  
  
## <a name="what-you-will-learn"></a>Lezioni dell'esercitazione  
 In questa esercitazione viene illustrato come creare un account di archiviazione di Windows, un contenitore BLOB, la creazione di credenziali per l'accesso all'account di archiviazione, la scrittura di un backup nel servizio BLOB e l'esecuzione di un ripristino semplice. Questa esercitazione è suddivisa in quattro lezioni:  
  
 [Lezione 1: Creare gli oggetti di archiviazione di Azure di Windows](../tutorials/lesson-1-create-windows-azure-storage-objects.md)  
 In questa lezione verranno creati un account di archiviazione e un contenitore BLOB di Windows Azure.  
  
 [Lezione 2: Creare le credenziali di SQL Server](../tutorials/lesson-2-create-a-sql-server-credential.md)  
 In questa lezione verranno create le credenziali per archiviare le informazioni di sicurezza utilizzate per accedere all'account di archiviazione di Windows Azure.  
  
 [Lezione 3: Scrivere un Backup completo del Database per il servizio di archiviazione Blob di Azure di Windows](../tutorials/lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service.md)  
 In questa lezione verrà eseguita un'istruzione T-SQL per scrivere un backup del database AdventureWorks2012 nel servizio di archiviazione BLOB di Windows Azure.  
  
 [Lezione 4: Eseguire un ripristino da un backup completo del database](../tutorials/lesson-4-perform-a-restore-from-a-full-database-backup.md)  
 In questa lezione verrà eseguita un'istruzione T-SQL per il ripristino dal backup del database creato nella lezione precedente.  
  
### <a name="requirements"></a>Requisiti  
 Per completare l'esercitazione è necessario conoscere i concetti di backup e ripristino di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e la sintassi T-SQL. Per utilizzare l'esercitazione, il sistema deve soddisfare i requisiti seguenti.  
  
-   Un'istanza di [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] e il database AdventureWorks2012 installati.  
  
     L'istanza di SQL Server può essere in locale o in una macchina virtuale di Windows Azure.  
  
     È possibile utilizzare un database utente al posto di AdventureWorks2012 e modificare la sintassi tsql di conseguenza.  
  
-   All'account utente usato per eseguire i comandi BACKUP o RESTORE deve essere associato il ruolo del database **db_backup operator** con autorizzazioni **Modifica qualsiasi credenziale** .  
  
### <a name="additional-reading"></a>Ulteriori informazioni  
 Di seguito sono indicati alcuni argomenti consigliati per comprendere i concetti e le procedure consigliate quando si utilizza il servizio di archiviazione BLOB di Windows Azure per i backup di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
1.  [SQL Server Backup and Restore with Windows Azure Blob Storage Service](backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
2.  [Procedure consigliate e risoluzione dei problemi per il backup di SQL Server nell'URL](backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
  