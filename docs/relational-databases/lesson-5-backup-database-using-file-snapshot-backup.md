---
title: 'Lezione 5: Eseguire il backup del database con il backup di snapshot di file | Microsoft Docs'
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: tutorial
ms.reviewer: ''
ms.suite: sql
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016
ms.assetid: d9134ade-7b03-4c5c-8ed3-3bc369a61691
caps.latest.revision: 19
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f56a7cfbf4303ca03d3d6e5cda360643a892c35b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32943546"
---
# <a name="lesson-5-backup-database-using-file-snapshot-backup"></a>Lezione 5: Eseguire il backup del database con il backup di snapshot di file
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
In questa lezione si eseguirà il backup del database AdventureWorks2014 nella macchina virtuale di Azure usando il backup di snapshot di file per eseguire un backup quasi istantaneo con gli snapshot di Azure. Per altre informazioni sui backup di snapshot, vedere [Backup di snapshot di file per i file di database in Azure](../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md)  
  
Per eseguire il backup del database AdventureWorks2014 usando un backup di snapshot, eseguire queste operazioni:  
  
1.  Connettersi a SQL Server Management Studio.  
  
2.  Aprire una nuova finestra di query e connettersi all'istanza di SQL Server 2016 del motore di database nella macchina virtuale di Azure.  
  
3.  Copiare, incollare ed eseguire lo script Transact-SQL seguente nella finestra di query. Non chiudere questa finestra di query, lo script verrà eseguito di nuovo nel passaggio 5. Questa store procedure di sistema consente di visualizzare i backup di snapshot esistenti per ogni file che include un database specificato. Si noterà che non esistono backup di snapshot per questo database.  
  
    ```  
  
    -- Verify that no file snapshot backups exist  
    SELECT * FROM sys.fn_db_backup_file_snapshots ('AdventureWorks2014');  
  
    ```  
  
4.  Copiare e incollare lo script Transact-SQL seguente nella finestra della query. Modificare l'URL in modo appropriato per il nome di account di archiviazione e il contenitore specificato nella lezione 1 e quindi eseguire questo script. Si noti la rapidità con cui viene eseguito il backup.  
  
    ```  
  
    -- Backup the AdventureWorks2014 database with FILE_SNAPSHOT  
    BACKUP DATABASE AdventureWorks2014   
       TO URL = 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/AdventureWorks2014_Azure.bak'   
       WITH FILE_SNAPSHOT;  
  
    ```  
  
    ![riquadro dei risultati con snapshot di ogni file di database](../relational-databases/media/2a9320e0-067a-485a-8e0e-636660005e5c.JPG "riquadro dei risultati con snapshot di ogni file di database")  
  
5.  Dopo aver verificato che lo script del passaggio 4 è stato eseguito correttamente, eseguire di nuovo lo script seguente. Si noti che l'operazione di backup di snapshot di file del passaggio 4 ha generato snapshot sia per il file di dati che per il file di log.  
  
    ```  
  
    -- Verify that two file-snapshot backups exist  
    SELECT * FROM sys.fn_db_backup_file_snapshots ('AdventureWorks2014');  
  
    ```  
  
    ![risultati della funzione sys.fn_db_backup_file_snapshots con 2 snapshot](../relational-databases/media/fca1436e-9607-4432-97ee-f66ac2f2108d.JPG "risultati della funzione sys.fn_db_backup_file_snapshots con 2 snapshot")  
  
6.  In Object Explorer, nell'istanza di SQL Server 2016 nella macchina virtuale di Azure, espandere il nodo Databases e verificare che il database AdventureWorks2014 sia stato ripristinato in questa istanza. Aggiornare il nodo in base alle esigenze.  
  
7.  In Esplora oggetti connettersi all'archiviazione di Azure.  
  
8.  Espandere il contenitore creato nella lezione 1 e verificare che AdventureWorks2014_Azure.bak del passaggio 4 appaia nel contenitore, insieme ai file di backup dalla lezione 3 e i file di database della lezione 4 (aggiornare il nodo in base alle esigenze).  
  
    ![Backup di snapshot di file nel contenitore di Azure](../relational-databases/media/181bc970-4af7-4272-a9ae-4bef674f2e02.JPG "Backup di snapshot di file nel contenitore di Azure")  
  
**Lezione successiva:**  
  
[Lezione 6: Generare attività e backup del log usando il backup di snapshot di file](../relational-databases/lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup.md)  
  
## <a name="see-also"></a>Vedere anche  
[Backup di snapshot di file per i file di database in Azure](../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md)  
[sys.fn_db_backup_file_snapshots &#40;Transact-SQL&#41;](../relational-databases/system-functions/sys-fn-db-backup-file-snapshots-transact-sql.md)  
  
  
  
