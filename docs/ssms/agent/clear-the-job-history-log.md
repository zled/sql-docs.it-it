---
title: Cancellare il contenuto del log di cronologia processi | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- jobs [SQL Server Agent], history
- clearing job history log
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: 34b9398a-c409-4040-8ea1-0deceb18f961
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 8ece46cd518c4b94094015e26d1c8d6587edce50
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="clear-the-job-history-log"></a>Clear the Job History Log
In questo argomento viene descritto come eliminare il contenuto del log della cronologia processi di [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)], [!INCLUDE[tsql](../../includes/tsql_md.md)]o SQL Server Management Objects (SMO).  
  
**Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
    [Security](#Security)  
  
-   **Per cancellare il contenuto del log di cronologia processo utilizzando:**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server Management Objects](#SMO)  
  
## <a name="BeforeYouBegin"></a>Prima di iniziare  
  
### <a name="Security"></a>Security  
Per informazioni dettagliate, vedere [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-clear-the-job-history-log"></a>Per cancellare il contenuto del log di cronologia processo  
  
1.  In **Esplora oggetti** connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]ed espandere tale istanza.  
  
2.  Espandere **SQL Server Agent**e quindi espandere **Processi**.  
  
3.  Fare clic con il pulsante destro del mouse su un processo e scegliere **Visualizza cronologia**.  
  
4.  Nel **Visualizzatore file di log**selezionare il processo di cui si desidera cancellare la cronologia e quindi eseguire una delle operazioni seguenti:  
  
    -   Fare clic su **Elimina**e quindi su **Elimina tutta la cronologia** nella finestra di dialogo **Elimina cronologia** . È possibile eliminare tutta la cronologia processo oppure solo quella precedente a una data specificata. Per rimuovere tutta la cronologia processo, fare clic su **Elimina tutta la cronologia**. Per rimuovere solo i log cronologia processo più vecchi, fare clic su **Elimina la cronologia precedente a**e quindi specificare una data.  
  
    -   Fare clic su **Stato processo** se si desidera cancellare il contenuto del log della cronologia di un processo multiserver. Fare clic su **Processo**, selezionare il nome di un processo e quindi fare clic su **Visualizza cronologia processi remoti**.  
  
5.  Fare clic su **Elimina**.  
  
## <a name="TSQL"></a>Utilizzo di Transact-SQL  
  
#### <a name="to-clear-the-job-history-log"></a>Per cancellare il contenuto del log di cronologia processo  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**.  
  
    ```  
    -- example removes the history for a job named NightlyBackups.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_purge_jobhistory  
        @job_name = N'NightlyBackups' ;  
    GO  
    ```  
  
## <a name="SMO"></a>Utilizzo di SQL Server Management Objects  
**Per cancellare il contenuto del log di cronologia processo**  
  
Usare il metodo **PurgeJobHistory** della classe **JobServer** tramite un linguaggio di programmazione come Visual Basic, Visual C# o PowerShell. Per altre informazioni, vedere [SQL Server Management Objects (SMO)](http://msdn.microsoft.com/library/ms162169.aspx).  
  

