---
title: 'Lezione 2: Creare una credenziale di SQL Server | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 64f8805c-1ddc-4c96-a47c-22917d12e1ab
caps.latest.revision: 13
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 0dbf7ee01520d139ce6b56912f6b35500ee35352
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2018
ms.locfileid: "40392330"
---
# <a name="lesson-2-create-a-sql-server-credential"></a>Lezione 2: Creare le credenziali di SQL Server
  **Credenziale:** una credenziale di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] è un oggetto utilizzato per archiviare le informazioni di autenticazione necessarie per connettersi a una risorsa all'esterno di SQL Server.  In questo caso, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] processi di backup e ripristino usano credenziali per l'autenticazione al servizio di archiviazione Blob di Windows Azure. Nelle credenziali vengono archiviati il nome dell'account di archiviazione e i relativi valori della **chiave di accesso** . Una volta create, le credenziali devono essere specificate nell'opzione WITH CREDENTIAL durante l'esecuzione delle istruzioni BACKUP/RESTORE. Per altre informazioni su come visualizzare, copiare o rigenerare le **access keys**dell'account di archiviazione, vedere la pagina relativa alle [chiavi di accesso dell'account di archiviazione](http://msdn.microsoft.com/library/windowsazure/hh531566.aspx).  
  
 Per informazioni generali sulle credenziali, vedere [credenziali](../relational-databases/security/authentication-access/credentials-database-engine.md).  
  
 Per informazioni su altri esempi in cui vengono utilizzate le credenziali, vedere [creare un Proxy di SQL Server Agent](../ssms/agent/create-a-sql-server-agent-proxy.md).  
  
> [!IMPORTANT]  
>  I requisiti per la creazione di una credenziale di SQL Server descritta di seguito sono specifici per i processi di backup di SQL Server ([SQL Server Backup to URL](../relational-databases/backup-restore/sql-server-backup-to-url.md), e [SQL Server Managed Backup to Windows Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)). Per accedere alla risorsa di archiviazione di Azure, SQL Server usa le informazioni sul nome dell'account di archiviazione e sulla chiave di accesso.  Per altre informazioni sulla creazione delle credenziali per l'archiviazione file di database in archiviazione di Azure, vedere [lezione 3: creare una credenziale di SQL Server](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)  
  
## <a name="create-a-sql-server-credential"></a>Creare le credenziali di SQL Server  
 Per creare le credenziali di SQL Server, attenersi ai passaggi seguenti:  
  
1.  Connettersi a SQL Server Management Studio.  
  
2.  In Esplora oggetti connettersi all'istanza del motore di database con il database AdventureWorks2012 installato; in alternativa, utilizzare il proprio database da utilizzare per questa esercitazione.  
  
3.  Sulla barra degli strumenti **Standard** fare clic su **Nuova query**.  
  
4.  Copiare e incollare l'esempio seguente nella finestra Query e modificare se necessario.  
  
    ```  
    CREATE CREDENTIAL mycredential   
    WITH IDENTITY= 'mystorageaccount' – this is the name of the storage account you specified when creating a storage account (See Lesson 1)   
    , SECRET = '<storage account access key>' – this should be either the Primary or Secondary Access Key for the storage account (See Lesson 1)  
  
    ```  
  
     ![mapping di account di archiviazione alle credenziali sql](../../2014/tutorials/media/backuptocloud-storage-credential-mapping.gif "mapping account di archiviazione alle credenziali sql")  
  
5.  Verificare l'istruzione T-SQL e fare clic su **Esegui**.  
  
 Per altre informazioni sul servizio di archiviazione Blob di Windows Azure per i requisiti e i concetti di backup, vedere [SQL Server Backup and Restore with Windows Azure Blob Storage Service](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  
  
### <a name="next-lesson"></a>Lezione successiva  
 [Lezione 3: Scrivere un Backup completo del Database per il servizio di Windows Azure Blob Storage](../../2014/tutorials/lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service.md).  
  
  
