---
title: Arrestare un processo | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], stopping
- SQL Server Agent jobs, stopping
- stopping jobs
ms.assetid: 4249328a-24d8-4284-9d1d-7d04ed90e3d7
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 14fe8bcb95f37a538ac2a4c7d68a808bdd2f4025
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37218511"
---
# <a name="stop-a-job"></a>Stop a Job
  In questo argomento viene illustrato l'arresto di un processo di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Un processo è una serie specificata di azioni eseguite da SQL Server Agent.  
  
-   **Prima di iniziare:**  ,  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Security](#Security)  
  
-   **Per arrestare un processo utilizzando:**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server Management Objects](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Se in un processo è in esecuzione un passaggio di tipo **CmdExec** o **PowerShell**, viene impostata l'interruzione anticipata del processo eseguito, ad esempio MioProgramma.exe. Tale interruzione può causare un comportamento imprevisto, poiché ad esempio i file utilizzati dal processo potrebbero restare aperti.  
  
-   Per un processo multiserver, viene inviata un'istruzione STOP a tutti i server di destinazione del processo.  
  
###  <a name="Security"></a> Sicurezza  
 Per informazioni dettagliate, vedere [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-stop-a-job"></a>Per arrestare un processo  
  
1.  In **Esplora oggetti** connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]ed espandere tale istanza.  
  
2.  Espandere **SQL Server Agent**e **Processi**, fare clic con il pulsante destro del mouse sul processo da arrestare e scegliere **Arresta processo**.  
  
3.  Se si intende arrestare più processi, fare clic con il pulsante destro del mouse su **Monitoraggio attività processi**e scegliere **Visualizza attività processi**. In Monitoraggio attività processo selezionare i processi da arrestare, fare clic con il pulsante destro del mouse sulla selezione e scegliere **Arresta processi**.  
  
##  <a name="TSQL"></a> Uso di Transact-SQL  
  
#### <a name="to-stop-a-job"></a>Per arrestare un processo  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**.  
  
    ```  
    -- stops a job named Weekly Sales Data Backup  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_stop_job  
        N'Weekly Sales Data Backup' ;  
    GO  
    ```  
  
 Per altre informazioni, vedere [sp_stop_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-stop-job-transact-sql).  
  
##  <a name="SMO"></a> Utilizzo di SQL Server Management Objects  
 **Per arrestare un processo**  
  
 Chiamare il metodo `Stop` della classe `Job` usando un linguaggio di programmazione come Visual Basic, Visual C# o PowerShell. Per altre informazioni, vedere [SQL Server Management Objects (SMO)](http://msdn.microsoft.com/library/ms162169.aspx).  
  
  
