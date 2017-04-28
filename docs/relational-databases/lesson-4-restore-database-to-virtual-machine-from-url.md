---
title: 'Lezione 4: Ripristinare il database in una macchina virtuale da un URL | Microsoft Docs'
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
ms.assetid: ba793c8f-665a-4c46-b68d-f558a37906b2
caps.latest.revision: 23
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 31d30195b648f48b149021a7bf80aba2543a14ea
ms.lasthandoff: 04/11/2017

---
# <a name="lesson-4-restore-database-to-virtual-machine-from-url"></a>Lezione 4: Ripristinare il database in una macchina virtuale da un URL
In questa lezione il database AdventureWorks2014 viene ripristinato nell'istanza di SQL Server 2016 nella macchina virtuale di Azure.  
  
> [!NOTE]  
> Ai fini della semplicità dell'esercitazione, viene usato lo stesso contenitore per i file di dati e di log usato per il backup del database. In un ambiente di produzione probabilmente si usano più contenitori e spesso anche più file di dati. Con SQL Server 2016 si può anche considerare lo striping del backup in più BLOB per migliorare le prestazioni del backup quando si esegue il backup di un database di grandi dimensioni.  
  
Per ripristinare il database di SQL Server 2014 dall'archiviazione BLOB di Azure nell'istanza di SQL Server 2016 nella macchina virtuale di Azure, seguire questi passaggi:  
  
1.  Connettersi a SQL Server Management Studio.  
  
2.  Aprire una nuova finestra di query e connettersi all'istanza di SQL Server 2016 del motore di database nella macchina virtuale di Azure.  
  
3.  Copiare e incollare lo script Transact-SQL seguente nella finestra della query. Modificare l'URL in modo appropriato per il nome di account di archiviazione e il contenitore specificato nella lezione 1 e quindi eseguire questo script.  
  
    ```  
  
    -- Restore AdventureWorks2014 from URL to SQL Server instance using Azure blob storage for database files  
    RESTORE DATABASE AdventureWorks2014   
       FROM URL = 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/AdventureWorks2014_onprem.bak'   
       WITH  
          MOVE 'AdventureWorks2014_data' to 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/AdventureWorks2014_Data.mdf'  
         ,MOVE 'AdventureWorks2014_log' to 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/AdventureWorks2014_Log.ldf'  
    --, REPLACE  
  
    ```  
  
4.  Aprire Esplora oggetti e connettersi all'istanza di Azure SQL Server 2016.  
  
5.  In Esplora oggetti espandere il nodo Database e verificare che il database AdventureWorks2014 sia stato ripristinato, aggiornando il nodo se necessario.  
  
    ![Database Adventure Works 2014 ripristinato in SQL Server 2016 in una macchina virtuale](../relational-databases/media/311f69a6-8443-4df5-8f30-3103c2472300.JPG "Database Adventure Works 2014 ripristinato in SQL Server 2016 in una macchina virtuale")  
  
6.  In Esplora oggetti fare clic con il pulsante destro del mouse su AdventureWorks2014 e fare clic su Proprietà. Al termine fare clic su Annulla.  
  
7.  Fare clic su File e verificare che il percorso dei due file di database sono URL che puntano ai BLOB nel contenitore del blog di Azure.  
  
    ![Proprietà del database con il percorso di file dati logici come URL](../relational-databases/media/cfeee576-6319-460e-9fa2-f0922e02ee23.JPG "Proprietà del database con il percorso di file dati logici come URL")  
  
8.  In Esplora oggetti connettersi all'archiviazione di Azure.  
  
9. Espandere il contenitore creato nella lezione 1 e verificare che i file AdventureWorks2014_Data.mdf e AdventureWorks2014_Log.ldf del passaggio 3 appaiano nel contenitore, insieme ai file di backup dalla lezione 3. Aggiornare il nodo in base alle esigenze.  
  
    ![File di dati e di log di Adventure Works 2014 visualizzati come file BLOB in un contenitore di Azure](../relational-databases/media/156c7d73-44be-4754-9653-04cccb6c3066.JPG "File di dati e di log di Adventure Works 2014 visualizzati come file BLOB in un contenitore di Azure")  
  
**Lezione successiva:**  
  
[Lezione 5: Backup del database con il backup di snapshot di file](../relational-databases/lesson-5-backup-database-using-file-snapshot-backup.md)  
  
  
  

