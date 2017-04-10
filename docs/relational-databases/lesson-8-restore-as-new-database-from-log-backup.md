---
title: "Lezione 8. Ripristinare come nuovo database dal backup del log | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: ebba12c7-3d13-4c9d-8540-ad410a08356d
caps.latest.revision: 12
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 12
---
# Lezione 8. Ripristinare come nuovo database dal backup del log
In questa lezione il database AdventureWorks2014 verrà ripristinato come nuovo database dal backup del log delle transazioni dello snapshot di file.  
  
In questo scenario viene eseguito un ripristino in un'istanza di SQL Server in una macchina virtuale diversa per l'analisi business e la creazione di report. Il ripristino in un'altra istanza in una macchina virtuale diversa ripartisce il carico di lavoro su una macchina virtuale dedicata con dimensioni adatte allo scopo eliminando le richieste di risorse dal sistema transazionale.  
  
Il ripristino da un backup del log delle transazioni con backup di snapshot di file è un'operazione rapida, molto più veloce dei backup di flusso tradizionali. Con i backup di flusso tradizionali, è necessario usare il backup di database completo, probabilmente un backup differenziale e alcuni o tutti i backup del log delle transazioni oppure un nuovo backup di database completo. Con i backup del log dello snapshot di file, invece, è necessario solo il backup del log più recente oppure qualsiasi altro backup del log o due backup del log adiacenti per il ripristino temporizzato in un momento tra due orari di backup del log. Per maggiore chiarezza, è necessario un solo set di backup di snapshot di file di log poiché ogni backup del log di snapshot di file crea uno snapshot di ogni file del database (file di dati e file di log).  
  
Per ripristinare un database in un nuovo database da un backup del log delle transazioni usando il backup di snapshot di file, eseguire i passaggi seguenti:  
  
1.  Connettersi a SQL Server Management Studio.  
  
2.  Aprire una nuova finestra di query e connettersi all'istanza di SQL Server 2016 del motore di database in una macchina virtuale di Azure.  
  
    > [!NOTE]  
    > Se si tratta di una macchina virtuale di Azure diversa da quella usata per le lezioni precedenti, assicurarsi di aver eseguito i passaggi descritti in [Lezione 2: Creare una credenziale di SQL Server usando una firma di accesso condiviso](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md). Per eseguire il ripristino in un contenitore diverso, seguire i passaggi descritti in [Lezione 1: Creare i criteri di accesso archiviati e una firma di accesso condiviso in un contenitore di Azure](../relational-databases/lesson-1-create-stored-access-policy-and-shared-access-signature.md) e [Lezione 2: Creare una credenziale di SQL Server usando una firma di accesso condiviso](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md) per il nuovo contenitore.  
  
3.  Copiare e incollare lo script Transact-SQL seguente nella finestra della query. Selezionare il file di backup del log che si vuole usare. Modificare l'URL in modo appropriato per il nome di account di archiviazione e il contenitore specificato nella lezione 1, specificare il nome di file di backup del log e quindi eseguire questo script.  
  
    ```  
  
    -- restore as a new database from a transaction log backup file  
    RESTORE DATABASE AdventureWorks2014_EOM   
        FROM URL = 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/<logbackupfile.bak'    
        WITH MOVE 'AdventureWorks2014_data' to 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/AdventureWorks2014_EOM_Data.mdf'  
       , MOVE 'AdventureWorks2014_log' to 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/AdventureWorks2014_EOM_Log.ldf'  
       , RECOVERY  
    --, REPLACE  
  
    ```  
  
4.  Rivedere l'output per verificare il completamento del ripristino.  
  
5.  In Esplora oggetti connettersi all'archiviazione di Azure.  
  
6.  Espandere Contenitori, espandere il contenitore creato nella lezione 1, aggiornare se necessario e verificare che i nuovi file di dati e di log siano visualizzati nel contenitore con i BLOB delle lezioni precedenti.  
  
    ![Azure container showing the data and log files for the new database](../relational-databases/media/e9705083-86bc-4309-a0bf-92c15f174c0a.JPG "Azure container showing the data and log files for the new database")  
  
[Lezione 9: Gestire set di backup e backup di snapshot di file](../relational-databases/lesson-9-manage-backup-sets-and-file-snapshot-backups.md)  
  
  
  
