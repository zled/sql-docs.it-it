---
title: Arrestare un processo | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- jobs [SQL Server Agent], stopping
- SQL Server Agent jobs, stopping
- stopping jobs
ms.assetid: 4249328a-24d8-4284-9d1d-7d04ed90e3d7
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c3abb964699518b9f9e74967fd0e27a79dc10c57
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="stop-a-job"></a>Stop a Job
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Questo argomento descrive come arrestare un processo di [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent. Un processo è una serie specificata di azioni eseguite da SQL Server Agent.  
  
-   **Prima di iniziare:**  ,  
  
    [Limitazioni e restrizioni](#Restrictions)  
  
    [Security](#Security)  
  
-   **Per arrestare un processo utilizzando:**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server Management Objects](#SMO)  
  
## <a name="BeforeYouBegin"></a>Prima di iniziare  
  
### <a name="Restrictions"></a>Limitazioni e restrizioni  
  
-   Se in un processo è in esecuzione un passaggio di tipo **CmdExec** o **PowerShell**, viene impostata l'interruzione anticipata del processo eseguito, ad esempio MioProgramma.exe. Tale interruzione può causare un comportamento imprevisto, poiché ad esempio i file utilizzati dal processo potrebbero restare aperti.  
  
-   Per un processo multiserver, viene inviata un'istruzione STOP a tutti i server di destinazione del processo.  
  
### <a name="Security"></a>Security  
Per informazioni dettagliate, vedere [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-stop-a-job"></a>Per arrestare un processo  
  
1.  In **Esplora oggetti** connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]ed espandere tale istanza.  
  
2.  Espandere **SQL Server Agent**e **Processi**, fare clic con il pulsante destro del mouse sul processo da arrestare e scegliere **Arresta processo**.  
  
3.  Se si intende arrestare più processi, fare clic con il pulsante destro del mouse su **Monitoraggio attività processi**e scegliere **Visualizza attività processi**. In Monitoraggio attività processo selezionare i processi da arrestare, fare clic con il pulsante destro del mouse sulla selezione e scegliere **Arresta processi**.  
  
## <a name="TSQL"></a>Utilizzo di Transact-SQL  
  
#### <a name="to-stop-a-job"></a>Per arrestare un processo  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**.  
  
    ```  
    -- stops a job named Weekly Sales Data Backup  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_stop_job  
        N'Weekly Sales Data Backup' ;  
    GO  
    ```  
  
Per altre informazioni, vedere [sp_stop_job (Transact-SQL)](http://msdn.microsoft.com/en-us/64b4cc75-99a0-421e-b418-94e37595bbb0).  
  
## <a name="SMO"></a>Utilizzo di SQL Server Management Objects  
**Per arrestare un processo**  
  
Chiamare il metodo **Stop** della classe **Job** tramite un linguaggio di programmazione come Visual Basic, Visual C# o PowerShell. Per altre informazioni, vedere [SQL Server Management Objects (SMO)](http://msdn.microsoft.com/library/ms162169.aspx).  
  
