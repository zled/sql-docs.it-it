---
title: "Lezione 6: Generare attività e backup del log usando il backup di snapshot di file | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: 26aa534a-afe7-4a14-b99f-a9184fc699bd
caps.latest.revision: 15
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 8f3ea59fb612ea692b52ab46bb342d8c4031fb71
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup"></a>Lezione 6: Generare attività e backup del log usando il backup di snapshot di file
In questa lezione viene generata un'attività nel database AdventureWorks2014 e periodicamente vengono eseguiti i backup del log delle transazioni tramite backup di snapshot di file. Per altre informazioni sui backup di snapshot di file, vedere [Backup di snapshot di file per i file di database in Azure](../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md).  
  
Per generare un'attività nel database AdventureWorks2014 e creare periodicamente backup del log delle transazioni tramite backup di snapshot di file, seguire questa procedura:  
  
1.  Connettersi a SQL Server Management Studio.  
  
2.  Aprire due nuove finestra di query e connettere ogni finestra all'istanza di SQL Server 2016 del motore di database nella macchina virtuale di Azure.  
  
3.  Copiare, incollare ed eseguire lo script Transact-SQL seguente in una delle finestre di query. Si noti che, prima di aggiungere nuove righe nel passaggio 4, la tabella Production.Location contiene 14 righe.  
  
    ```  
  
    -- Verify row count at start  
    SELECT COUNT (*) from AdventureWorks2014.Production.Location;  
  
    ```  
  
4.  Copiare e incollare gli script Transact-SQL seguenti nelle due diverse finestre di query. Modificare l'URL in modo appropriato per il nome di account di archiviazione e il contenitore specificato nella lezione 1 ed eseguire questi script contemporaneamente in due finestre di query distinte. Dopo 7 minuti circa questi script saranno completi.  
  
    ```  
    -- Insert 30,000 new rows into the Production.Location table in the AdventureWorks2014 database in batches of 75  
    DECLARE @count INT=1, @inner INT;  
    WHILE @count < 400  
       BEGIN  
          BEGIN TRAN;  
             SET @inner =1;  
                WHILE @inner <= 75  
                   BEGIN;  
                      INSERT INTO AdventureWorks2014.Production.Location    
                         (Name, CostRate, Availability, ModifiedDate)   
                            VALUES (NEWID(), .5, 5.2, GETDATE());  
                      SET @inner = @inner + 1;  
                   END;  
          COMMIT;  
       WAITFOR DELAY '00:00:01';   
       SET @count = @count + 1;  
       END;  
    SELECT COUNT (*) from AdventureWorks2014.Production.Location;  
  
    ```  
  
    ```  
    --take 7 transaction log backups with FILE_SNAPSHOT, one per minute, and include the row count and the execution time in the backup file name   
    DECLARE @count INT=1, @device NVARCHAR(120), @numrows INT;  
    WHILE @count <= 7  
       BEGIN  
             SET @numrows = (SELECT COUNT (*) FROM AdventureWorks2014.Production.Location);  
             SET @device = 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/tutorial-' + CONVERT (varchar(10),@numrows) + '-' + FORMAT(GETDATE(), 'yyyyMMddHHmmss') + '.bak';  
             BACKUP LOG AdventureWorks2014 TO URL = @device WITH FILE_SNAPSHOT;  
             SELECT * from sys.fn_db_backup_file_snapshots ('AdventureWorks2014');  
          WAITFOR DELAY '00:1:00';   
             SET @count = @count + 1;  
       END;  
    ```  
  
5.  Esaminare l'output del primo script. Si noti che il numero di righe finale è ora 29.939.  
  
    ![Visualizzato un numero di righe pari a 29.939](../relational-databases/media/5e2f4229-1970-49c9-89b3-e96b6f7fde83.JPG "Visualizzato un numero di righe pari a 29.939")  
  
6.  Esaminare l'output del secondo script. Si noti che ogni volta che si esegue l'istruzione BACKUP LOG vengono creati due nuovi snapshot di file, vale a dire uno snapshot del file di log e uno del file di dati, per un totale di due snapshot per ogni file di database. Dopo aver completato il secondo script, si noti che gli snapshot di file sono in totale 16, 8 per ogni file di database, uno proveniente dall'istruzione BACKUP DATABASE e uno per ogni esecuzione dell'istruzione BACKUP LOG.  
  
    ![riquadro risultati con gli snapshot del file di log e del file di dati quando viene eseguito il backup del log](../relational-databases/media/acd213b8-895e-425c-bd72-2bf10e65a5ba.JPG "riquadro risultati con gli snapshot del file di log e del file di dati quando viene eseguito il backup del log")  
  
    ![quattro snapshot di file visualizzati](../relational-databases/media/e7eff77d-85b9-4e52-abd8-e49952c8118a.JPG "quattro snapshot di file visualizzati")  
  
    ![riquadro risultati con un totale di 16 snapshot di file](../relational-databases/media/c3ddff17-a83c-4bf0-a670-a38834f9c922.JPG "riquadro risultati con un totale di 16 snapshot di file")  
  
7.  In Esplora oggetti connettersi all'archiviazione di Azure.  
  
8.  Espandere Contenitori, espandere il contenitore creato nella lezione 1, verificare che i 7 nuovi file di backup siano visualizzati nel contenitore con i BLOB delle lezioni precedenti. Se necessario aggiornare il nodo.  
  
    ![Contenitore di Azure con 7 file BLOB di backup del log](../relational-databases/media/cfa5a326-87a2-4202-9a04-38bf577d2d0b.JPG "Contenitore di Azure con 7 file BLOB di backup del log")  
  
**Lezione successiva:**  
  
[Lezione 7: Eseguire il ripristino temporizzato di un database](../relational-databases/lesson-7-restore-a-database-to-a-point-in-time.md)  
  
  
  

