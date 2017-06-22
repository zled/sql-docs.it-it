---
title: Gestire i processi in un'organizzazione | Microsoft Docs
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
- multiserver job management [SQL Server]
- jobs [SQL Server Agent], modifying
- modifying jobs
- SQL Server Agent jobs, modifying
- target servers [SQL Server], job changes
ms.assetid: 4fe7f6c6-f89b-4430-979c-4994a5dcf7a6
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b5290d5109618f7c2d05722d5ee304a14b1ab528
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="manage-jobs-across-an-enterprise"></a>Gestire i processi in un'azienda
Se non si usa [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] per apportare modifiche a definizioni di processi multiserver, è necessario inviare le modifiche all'elenco di download per consentire ai server di destinazione di scaricare nuovamente il processo aggiornato. Per garantire che i server di destinazione dispongano delle definizioni dei processi più aggiornate, inviare un'istruzione INSERT dopo l'aggiornamento del processo multiserver:  
  
```  
EXECUTE sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
Per notificare ai server di destinazione che un processo multiserver è stato modificato, è necessario richiamare il comando precedente dopo avere utilizzato una qualsiasi delle procedure seguenti:  
  
-   [sp_add_jobstep (Transact-SQL)](http://msdn.microsoft.com/en-us/97900032-523d-49d6-9865-2734fba1c755)  
  
-   [sp_update_jobstep (Transact-SQL)](http://msdn.microsoft.com/en-us/e158802c-c347-4a5d-bf75-c03e5ae56e6b)  
  
-   [sp_delete_jobstep (Transact-SQL)](http://msdn.microsoft.com/en-us/421ede8e-ad57-474a-9fb9-92f70a3e77e3)  
  
-   [Gestione degli eventi](http://msdn.microsoft.com/en-us/80c80eaf-cf23-4ed8-b8dd-65fe59830dd1)  
  
-   [sp_detach_schedule (Transact-SQL)](http://msdn.microsoft.com/en-us/9a1fc335-1bef-4638-a33a-771c54a5dd19)  
  
    > [!NOTE]  
    > Non è necessario chiamare **sp_post_msx_operation** dopo aver chiamato **sp_update_job** o **sp_delete_job**, in quanto tali stored procedure inviano automaticamente le modifiche necessarie all'elenco di download.  
  
Di seguito sono indicate le operazioni comuni per la gestione di processi in un'organizzazione:  
  
**Per controllare lo stato di un server di destinazione**  
  
-   [Transact-SQL](http://msdn.microsoft.com/en-us/f841d3bd-901a-4980-ad0b-1c6eeba3f717)  
  
-   [Oggetti SMO (SQL Server Management Objects)](http://msdn.microsoft.com/en-us/4cde2b85-2a31-4cac-8d16-7a4196066193)  
  
**Per modificare i server di destinazione per un processo**  
  
-   [SQL Server Management Studio](../../ssms/agent/modify-the-target-servers-for-a-job.md)  
  
-   [Transact-SQL](http://msdn.microsoft.com/en-us/485252cc-0081-490a-9bd1-cbbd68eea286)  
  
-   [Oggetti SMO (SQL Server Management Objects)](http://msdn.microsoft.com/en-us/4cde2b85-2a31-4cac-8d16-7a4196066193)  
  
**Per modificare la posizione di un server di destinazione**  
  
-   [SQL Server Management Studio](../../ssms/agent/specify-a-target-server-s-location-sql-server-management-studio.md)  
  
-   [Transact-SQL](http://msdn.microsoft.com/en-us/ceb3b2bc-0cc4-48d8-9bdc-6a809556e35f)  
  
-   [Oggetti SMO (SQL Server Management Objects)](http://msdn.microsoft.com/en-us/4cde2b85-2a31-4cac-8d16-7a4196066193)  
  
**Per sincronizzare gli orologi dei server di destinazione**  
  
-   [SQL Server Management Studio](../../ssms/agent/synchronize-target-server-clocks-sql-server-management-studio.md)  
  
-   [Transact-SQL](http://msdn.microsoft.com/en-us/40e44df7-d3e3-44ee-b149-08aba629a21f)  
  
**Per forzare un server di destinazione a eseguire il polling del server master**  
  
-   [SQL Server Management Studio](../../ssms/agent/force-a-target-server-to-poll-the-master-server.md)  
  
-   [Transact-SQL](http://msdn.microsoft.com/en-us/085deef8-2709-4da9-bb97-9ab32effdacf)  
  
## <a name="see-also"></a>Vedere anche  
[Gestione di eventi](../../ssms/agent/manage-events.md)  
  

