---
title: "Disabilitare Estensione database e ripristinare i dati remoti | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "08/05/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.service: "sql-server-stretch-database"
ms.suite: ""
ms.technology: 
  - "dbe-stretch"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Estensione database, disabilitazione"
  - "disabilitazione di Estensione database"
ms.assetid: c1bbb24e-47e3-46aa-b786-fcadf9fb65ce
caps.latest.revision: 33
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 32
---
# Disabilitare Estensione database e ripristinare i dati remoti
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Per disabilitare Estensione database per una tabella, selezionare **Estendi** per una tabella in SQL Server Management Studio. Selezionare quindi una delle opzioni seguenti.  
  
-   **Disabilita |Ripristina dati da Azure**. Copiare i dati remoti per la tabella da Azure a SQL Server e quindi disabilitare Estensione database per la tabella. Questa operazione comporta costi di trasferimento dati e non può essere annullata.  
  
-   **Disabilita | Lascia dati in Azure**. Disabilitare Estensione database per una tabella.  Abbandonare i dati remoti per la tabella in Azure.  
  
 È anche possibile usare Transact-SQL per disabilitare Estensione database per una tabella o un database.  
  
 Dopo aver disabilitato Estensione database per una tabella, si interrompe la migrazione dei dati e i risultati delle query non includono più risultati dalla tabella remota.  
  
 Se si vuole sospendere la migrazione dei dati, vedere [Pause and resume data migration 40 &#40;Stretch Database&#41;](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md) (Sospendere e riprendere la migrazione dei dati (Estensione database)).  
  
> [!NOTE] La disabilitazione di Estensione database per una tabella o per un database non elimina l'oggetto remoto. Se si vuole eliminare la tabella remota o il database remoto, è necessario eliminarlo tramite il portale di gestione di Azure. Gli oggetti remoti continuano a generare costi di Azure fino a quando non vengono eliminati. Per altre informazioni, vedere [Prezzi di Estensione database di SQL Server](https://azure.microsoft.com/pricing/details/sql-server-stretch-database/).  
  
## Disabilitare Estensione database per una tabella  
  
### Usare SQL Server Management Studio per disabilitare Estensione database per una tabella.  
  
1.  In Esplora oggetti di SQL Server Management Studio selezionare la tabella per cui si vuole disabilitare Estensione database.  
  
2.  Fare clic con il pulsante destro del mouse e scegliere **Estendi** e quindi selezionare una delle opzioni seguenti.  
  
    -   **Disabilita |Ripristina dati da Azure**. Copiare i dati remoti per la tabella da Azure a SQL Server e quindi disabilitare Estensione database per la tabella. Questo comando non può essere annullato.  
  
        > [!NOTE] Copiare i dati remoti per la tabella da Azure a SQL Server comporta costi per il trasferimento dei dati. Per altre informazioni, vedere [Dettagli prezzi dei trasferimenti di dati](https://azure.microsoft.com/pricing/details/data-transfers/).  
  
         Dopo aver copiato tutti i dati remoti da Azure a SQL Server, l'estensione viene disabilitata per la tabella.  
  
    -   **Disabilita | Lascia dati in Azure**. Disabilitare Estensione database per una tabella.  Abbandonare i dati remoti per la tabella in Azure.  
  
    > [!NOTE] La disabilitazione di Estensione database per una tabella non comporta l'eliminazione dei dati remoti o della tabella remota. Se si vuole eliminare la tabella remota, è necessario eliminarla tramite il portale di gestione di Azure. La tabella remota continua a generare costi di Azure fino a quando non viene eliminata. Per altre informazioni, vedere [Prezzi di Estensione database di SQL Server](https://azure.microsoft.com/pricing/details/sql-server-stretch-database/).  
  
### Usare Transact-SQL per disabilitare Estensione database per una tabella  
  
-   Per disabilitare l'estensione per una tabella e copiare i dati remoti per la tabella da Azure a SQL Server, eseguire il comando seguente. Dopo aver copiato tutti i dati remoti da Azure a SQL Server, l'estensione viene disabilitata per la tabella.

    Questo comando non può essere annullato.  
  
    ```tsql  
    USE <Stretch-enabled database name>;
    GO
    ALTER TABLE <Stretch-enabled table name>  
       SET ( REMOTE_DATA_ARCHIVE ( MIGRATION_STATE = INBOUND ) ) ; 
    GO 
    ```  
  
    > [!NOTE] Copiare i dati remoti per la tabella da Azure a SQL Server comporta costi per il trasferimento dei dati. Per altre informazioni, vedere [Dettagli prezzi dei trasferimenti di dati](https://azure.microsoft.com/pricing/details/data-transfers/).    
  
-   Per disabilitare l'estensione per una tabella e abbandonare i dati remoti, eseguire il comando seguente.  
  
    ```tsql  
    USE <Stretch-enabled database name>;
    GO
    ALTER TABLE <Stretch-enabled table name>  
       SET ( REMOTE_DATA_ARCHIVE = OFF_WITHOUT_DATA_RECOVERY ( MIGRATION_STATE = PAUSED ) ) ; 
    GO
    ```  
  
> [!NOTE] La disabilitazione di Estensione database per una tabella non comporta l'eliminazione dei dati remoti o della tabella remota. Se si vuole eliminare la tabella remota, è necessario eliminarla tramite il portale di gestione di Azure. La tabella remota continua a generare costi di Azure fino a quando non viene eliminata. Per altre informazioni, vedere [Prezzi di Estensione database di SQL Server](https://azure.microsoft.com/pricing/details/sql-server-stretch-database/).  
  
## Disabilitare Estensione database per un database  
 Prima di poter disabilitare Estensione database per un database, è necessario disabilitare Estensione database nelle singole tabelle abilitate per l'estensione nel database.  
  
### Usare SQL Server Management Studio per disabilitare Estensione database per un database  
  
1.  In Esplora oggetti di SQL Server Management Studio selezionare il database per cui si vuole disabilitare Estensione database.  
  
2.  Fare clic con il pulsante destro del mouse e scegliere **Attività**, selezionare **Estendi** e quindi **Disabilita**.  
  
> [!NOTE] La disabilitazione di Estensione database per un database non comporta l'eliminazione del database remoto. Se si vuole eliminare il database remoto, è necessario eliminarlo tramite il portale di gestione di Azure. Il database remoto continua a generare costi di Azure fino a quando non viene eliminato. Per altre informazioni, vedere [Prezzi di Estensione database di SQL Server](https://azure.microsoft.com/pricing/details/sql-server-stretch-database/).  
  
### Usare Transact-SQL per disabilitare Estensione database per un database  
 Eseguire il comando seguente.  
  
```tsql  
ALTER DATABASE <Stretch-enabled database name>  
    SET REMOTE_DATA_ARCHIVE = OFF ;  
GO 
```  
  
> [!NOTE] La disabilitazione di Estensione database per un database non comporta l'eliminazione del database remoto. Se si vuole eliminare il database remoto, è necessario eliminarlo tramite il portale di gestione di Azure. Il database remoto continua a generare costi di Azure fino a quando non viene eliminato. Per altre informazioni, vedere [Prezzi di Estensione database di SQL Server](https://azure.microsoft.com/pricing/details/sql-server-stretch-database/).  
  
## Vedere anche  
 [Opzioni di ALTER DATABASE SET &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20SET%20Options%20\(Transact-SQL\).md)   
 [Pause and resume data migration &#40;Stretch Database&#41; (Sospendere e riprendere la migrazione dei dati (Estensione database))](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md)  
  
  