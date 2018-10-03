---
title: 'Lezione 3: Backup del database su URL | Microsoft Docs'
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: a9ae1501-b614-49d3-b975-6569da8350b2
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: dabe55a05c9028283d481d7504553c2bf117cd32
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47695789"
---
# <a name="lesson-3-database-backup-to-url"></a>Lezione 3: Backup del database su URL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
In questa lezione si eseguirà il backup del database AdventureWorks2014 nell'istanza di SQL Server 2016 locale nel contenitore di Azure creato nella [Lezione 1: Creare criteri di accesso archiviati e una firma di accesso condiviso in un contenitore di Azure](../relational-databases/lesson-1-create-stored-access-policy-and-shared-access-signature.md).  
  
> [!NOTE]  
> Se si vuole eseguire il backup di un database di SQL Server 2012 SP1 CU2 o versione successiva o di un database di SQL Server 2014 nel contenitore di Azure, è possibile usare la sintassi deprecata illustrata [qui](https://technet.microsoft.com/library/dn435916(v=sql.120).aspx) per eseguire il backup nell'URL usando la sintassi con credenziali.  
  
Per eseguire il backup di un database nell'archiviazione BLOB, seguire questi passaggi:  
  
1.  Connettersi a SQL Server Management Studio.  
  
2.  Aprire una nuova finestra di query e connettersi all'istanza di SQL Server 2016 del motore di database nella macchina virtuale di Azure.  
  
3.  Copiare e incollare lo script Transact-SQL seguente nella finestra della query. Modificare l'URL in modo appropriato per il nome di account di archiviazione e il contenitore specificato nella lezione 1 e quindi eseguire questo script.  
  
    ```  
  
    -- To permit log backups, before the full database backup, modify the database to use the full recovery model.  
    USE master;  
    ALTER DATABASE AdventureWorks2014  
       SET RECOVERY FULL;  
  
    -- Back up the full AdventureWorks2014 database to the container that you created in Lesson 1  
    BACKUP DATABASE AdventureWorks2014   
       TO URL = 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/AdventureWorks2014_onprem.bak'  
  
    ```  
  
4.  Aprire Esplora oggetti e connettersi all'archiviazione di Azure usando l'account di archiviazione e la chiave dell'account.  
  
5.  Espandere i contenitori, espandere il contenitore creato nella lezione 1 e verificare che il file di backup usato nel passaggio 3 sia visualizzato in questo contenitore.  
  
    ![File di backup locale visualizzato come file BLOB in un contenitore di Azure](../relational-databases/media/0d060e51-012f-4c61-ab8d-16d461d0ffad.JPG "File di backup locale visualizzato come file BLOB in un contenitore di Azure")  
  
**Lezione successiva:**  
  
[Lezione 4: Ripristinare il database in una macchina virtuale da un URL](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)  
  
