---
title: Creare una pianificazione | Microsoft Docs
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
- scheduling jobs [SQL Server]
- SQL Server Agent jobs, scheduling
- jobs [SQL Server Agent], scheduling
- schedules [SQL Server], jobs
ms.assetid: 8c7ef3b3-c06d-4a27-802d-ed329dc86ef3
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a3c13b9d82ba7085e3542bf246b94d6813affa67
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37325531"
---
# <a name="create-a-schedule"></a>Create a Schedule
  È possibile creare una pianificazione per i processi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]o SQL Server Management Objects.  
  
-   **Prima di iniziare:**  
  
     [Security](#Security)  
  
-   **Per creare una pianificazione utilizzando:**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server Management Objects](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
 Per informazioni dettagliate, vedere [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-create-a-schedule"></a>Per creare una pianificazione  
  
1.  In **Esplora oggetti** connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]ed espandere tale istanza.  
  
2.  Espandere **SQL Server Agent**, fare clic con il pulsante destro del mouse su **Processi**e scegliere **Gestisci pianificazioni**.  
  
3.  Nella finestra di dialogo **Gestione pianificazioni** fare clic su **Nuovo**.  
  
4.  Nella casella **Nome** digitare un nome per la nuova pianificazione.  
  
5.  Se non si desidera rendere effettiva la pianificazione subito dopo la creazione, deselezionare la casella di controllo **Abilitata** .  
  
6.  Per **Tipo pianificazione**, selezionare una delle opzioni seguenti:  
  
    -   Fare clic su **Avvia quando la CPU diventa inattiva**per avviare il processo quando la CPU raggiunge una condizione di inattività.  
  
    -   Se si desidera eseguire ripetutamente una pianificazione, fare clic su **Periodica**. Per impostare la pianificazione periodica, completare i gruppi **Frequenza**, **Frequenza giornaliera**e **Durata** della finestra di dialogo.  
  
    -   Fare clic su **Singola occorrenza**se si desidera che la pianificazione venga eseguita una sola volta. Per impostare la pianificazione di tipo **Singola occorrenza** , compilare il gruppo **Singola occorrenza** della finestra di dialogo.  
  
##  <a name="TSQL"></a> Uso di Transact-SQL  
  
#### <a name="to-create-a-schedule"></a>Per creare una pianificazione  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**.  
  
    ```  
    -- creates a schedule named RunOnce.   
    -- The schedule runs one time, at 23:30 on the day that the schedule is created.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',  
        @freq_type = 1,  
        @active_start_time = 233000 ;  
  
    GO  
    ```  
  
 Per altre informazioni, vedere [sp_add_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql).  
  
##  <a name="SMO"></a> Utilizzo di SQL Server Management Objects  
 **Per creare una pianificazione**  
  
 Usare il `JobSchedule` classe utilizzando un linguaggio di programmazione desiderato, ad esempio Visual Basic, Visual c# o PowerShell. Per altre informazioni, vedere [SQL Server Management Objects (SMO)](http://msdn.microsoft.com/library/ms162169.aspx).  
  
  
