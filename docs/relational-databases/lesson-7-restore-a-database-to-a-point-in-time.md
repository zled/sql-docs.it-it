---
title: 'Lezione 7: Eseguire il ripristino temporizzato di un database | Microsoft Docs'
ms.custom: SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
ms.assetid: a9f99670-e1de-441e-972c-69faffcac17a
caps.latest.revision: "13"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 479f890cd6623b457b53cc0024691f9169937538
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="lesson-7-restore-a-database-to-a-point-in-time"></a>Lezione 7: Ripristino di un database con temporizzazione
In questa lezione il database AdventureWorks2014 verrà ripristinato in base a un dato momento tra due backup del log delle transazioni.  
  
Con i backup tradizionali, per eseguire il ripristino temporizzato è necessario usare il backup completo del database, ad esempio un backup differenziale, e tutti i file di log delle transazioni fino al e subito dopo il momento in base al quale si esegue il ripristino. Per i backup di snapshot di file sono necessari solo i due file di backup del log che rappresentano i due limiti del periodo di tempo a cui si riferisce il ripristino. Sono necessari due soli set di backup di snapshot di file di log poiché ogni backup del log crea uno snapshot di ogni file del database (file di dati e file di log).  
  
Per ripristinare un database in base a un momento specifico dal set di backup di snapshot di file, seguire questa procedura:  
  
1.  Connettersi a SQL Server Management Studio.  
  
2.  Aprire una nuova finestra di query e connettersi all'istanza di SQL Server 2016 del motore di database nella macchina virtuale di Azure.  
  
3.  Copiare, incollare ed eseguire lo script Transact-SQL seguente nella finestra della query. Verificare che la tabella Production.Location contenga 29.939 righe prima di eseguire il ripristino temporizzato quando sono presenti meno righe nel passaggio 5.  
  
    ```  
  
    -- Verify row count at start  
    SELECT COUNT (*) from AdventureWorks2014.Production.Location  
  
    ```  
  
    ![Visualizzato un numero di righe pari a 29.939](../relational-databases/media/5e2f4229-1970-49c9-89b3-e96b6f7fde83.JPG "Visualizzato un numero di righe pari a 29.939")  
  
4.  Copiare e incollare lo script Transact-SQL seguente nella finestra della query. Selezionare due file di backup del log adiacenti e convertire il nome del file nella data e nell'ora necessarie per questo script. Modificare l'URL in modo appropriato per il nome di account di archiviazione e il contenitore specificato nella lezione 1, specificare i nomi del primo e del secondo file di backup, indicare il tempo STOPAT nel formato "June 26, 2015 01:48 PM" e quindi eseguire lo script. Il completamento di questo script richiederà alcuni minuti  
  
    ```  
  
    -- restore and recover to a point in time between the times of two transaction log backups, and then verify the row count  
    ALTER DATABASE AdventureWorks2014 SET SINGLE_USER WITH ROLLBACK IMMEDIATE;  
    RESTORE DATABASE AdventureWorks2014   
       FROM URL = 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/<firstbackupfile>.bak'   
       WITH NORECOVERY,REPLACE;  
    RESTORE LOG AdventureWorks2014   
       FROM URL = 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/<secondbackupfile>.bak'    
       WITH RECOVERY, STOPAT = 'June 26, 2015 01:48 PM';  
    ALTER DATABASE AdventureWorks2014 set multi_user;  
    -- get new count  
    SELECT COUNT (*) FROM AdventureWorks2014.Production.Location ;  
  
    ```  
  
5.  Esaminare l'output. Si noti che dopo il ripristino il conteggio delle righe è 18.389, il numero di righe tra i backup del log 5 e 6 (il numero di righe conteggiato può variare).  
  
    ![Riquadro dei risultati con il numero di righe dopo il ripristino temporizzato](../relational-databases/media/4a0c6d8b-e2ed-4e93-bd7a-ade22a4aecc6.JPG "Riquadro dei risultati con il numero di righe dopo il ripristino temporizzato")  
  
**Lezione successiva:**  
  
[Lezione 8. Ripristinare come nuovo database dal backup del log](../relational-databases/lesson-8-restore-as-new-database-from-log-backup.md)  
  
  
  
