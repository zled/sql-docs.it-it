---
title: Modificare i server di destinazione per un processo | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- modifying target servers
- SQL Server Agent jobs, target servers
- target servers [SQL Server], modifying
ms.assetid: 9dbe24f2-acec-4aa2-920c-e8e96efa18e4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a7a3abf08d7b6aceb6a4c832cfaac1a288cbec1b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48221943"
---
# <a name="modify-the-target-servers-for-a-job"></a>Modifica dei server di destinazione di un processo
  In questo argomento viene illustrato come modificare i server di destinazione per i processi di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Security](#Security)  
  
-   **Per modificare i server di destinazione per un processo utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 Per impostazione predefinita, questa stored procedure può essere eseguita dai membri del ruolo predefinito del server sysadmin. Gli altri utenti devono appartenere a uno dei seguenti ruoli predefiniti del database di SQL Server Agent nel database msdb:  
  
1.  `SQLAgentUserRole`  
  
2.  `SQLAgentReaderRole`  
  
3.  SQLAgentOperatorRole  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-modify-the-target-servers-for-a-job"></a>Per modificare i server di destinazione per un processo  
  
1.  In **Esplora oggetti** connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]ed espandere tale istanza.  
  
2.  Espandere **SQL Server Agent**e quindi **Processi**, fare clic con il pulsante destro del mouse sul processo e quindi scegliere **Proprietà**.  
  
3.  Nella finestra di dialogo **Proprietà processo** , fare clic sulla pagina **Server di destinazione**e quindi su **Server di destinazione locale**oppure **Più server di destinazione**.  
  
     Se si sceglie **Più server di destinazione**, specificare quali dovranno essere i server di destinazione del processo selezionando la casella a sinistra del nome di ogni server. Verificare che le caselle di controllo corrispondenti ai server che non saranno server di destinazione del processo siano deselezionate.  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
  
#### <a name="to-modify-the-target-servers-for-a-job"></a>Per modificare i server di destinazione per un processo  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**. In questo esempio il processo multiserver Weekly Sales Backups viene assegnato al server SEATTLE2.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_jobserver  
    @job_name = N'Weekly Sales Backups',   
    @server_name = N'SEATTLE2' ;   
GO  
  
```  
  
 Per altre informazioni, vedere [sp_add_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql).  
  
## <a name="see-also"></a>Vedere anche  
 [Amministrazione automatizzata in un'organizzazione](automated-administration-across-an-enterprise.md)  
  
  
