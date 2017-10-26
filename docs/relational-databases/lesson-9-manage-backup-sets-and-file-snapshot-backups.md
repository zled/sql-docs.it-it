---
title: 'Lezione 9: Gestire set di backup e backup di snapshot di file | Microsoft Docs'
ms.custom:
- SQL2016_New_Updated
ms.date: 06/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: 766a0846-db15-4346-b814-4049039bcbfc
caps.latest.revision: 10
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 9747a3c7730db5d3fe1eda6145ece133c7b6d523
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="lesson-9-manage-backup-sets-and-file-snapshot-backups"></a>Lezione 9: Gestire set di backup e backup di snapshot di file
In questa lezione, verrà eliminato un set di backup tramite la stored procedure di sistema [sp_delete_backup &#40;Transact-SQL&#41;](../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup.md) . Questa stored procedure di sistema elimina il file di backup e lo snapshot del file in ogni file di database associato a questo set di backup.  
  
> [!NOTE]  
> Se si tenta di eliminare un set di backup semplicemente eliminando il file di backup dal contenitore BLOB di Azure, verrà rimosso solo file di backup, mentre gli snapshot dei file rimarranno. Se ci si ritrova in questo scenario, usare la funzione di sistema [sys.fn_db_backup_file_snapshots &#40;Transact-SQL&#41;](../relational-databases/system-functions/sys-fn-db-backup-file-snapshots-transact-sql.md) per identificare l'URL degli snapshot di file orfani e usare la stored procedure di sistema [sp_delete_backup_file_snapshot &#40;Transact-SQL&#41;](../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md) per eliminare ogni snapshot di file orfano. Per altre informazioni, vedere  [Backup di snapshot di file per i file di database in Azure](../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md).  
  
Per eliminare un set di backup di snapshot di file, seguire questi passaggi:  
  
1.  Connettersi a SQL Server Management Studio.  
  
2.  Aprire una nuova finestra Query e connettersi all'istanza di SQL Server 2016 del motore di database nella macchina virtuale di Azure (o a qualsiasi istanza di SQL Server 2016 con autorizzazioni di lettura e scrittura sul contenitore).  
  
3.  Copiare e incollare lo script Transact-SQL seguente nella finestra della query. Selezionare il backup del log che si vuole eliminare insieme ai relativi snapshot di file associati. Modificare l'URL in modo appropriato per il nome di account di archiviazione e il contenitore specificato nella lezione 1, specificare il nome di file di backup del log e quindi eseguire questo script.  
  
    ```  
  
    sys.sp_delete_backup 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/tutorial-9164-20150726012420.bak';  
  
    ```  
  
4.  In Esplora oggetti connettersi all'archiviazione di Azure.  
  
5.  Espandere i contenitori, espandere il contenitore creato nella lezione 1 e verificare che il file di backup usato nel passaggio 3 non sia più visualizzato in questo contenitore (aggiornare il nodo se necessario).  
  
    ![Contenitore di Azure che illustra l'eliminazione dei file BLOB di backup del log](../relational-databases/media/c0070b08-4667-4db5-aaff-987a404ec934.JPG "Contenitore di Azure che illustra l'eliminazione dei file BLOB di backup del log")  
  
6.  Copiare, incollare ed eseguire lo script Transact-SQL seguente nella finestra della query per verificare che i due snapshot di file siano stati eliminati.  
  
    ```  
  
    -- verify that two file snapshots have been removed  
    SELECT * from sys.fn_db_backup_file_snapshots ('AdventureWorks2014');  
  
    ```  
  
    ![Pagina dei risultati con 2 snapshot di file eliminati](../relational-databases/media/f3891361-dfb6-4f4d-a090-ebfeb977981e.JPG "Pagina dei risultati con 2 snapshot di file eliminati")  
  
**Fine dell'esercitazione**  
  
## <a name="see-also"></a>Vedere anche  
[Backup di snapshot di file per i file di database in Azure](../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md)  
[sp_delete_backup &#40;Transact-SQL&#41;](../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup.md)  
[sys.fn_db_backup_file_snapshots &#40;Transact-SQL&#41;](../relational-databases/system-functions/sys-fn-db-backup-file-snapshots-transact-sql.md)  
[sp_delete_backup_file_snapshot &#40;Transact-SQL&#41;](../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md)  
  
  
  


