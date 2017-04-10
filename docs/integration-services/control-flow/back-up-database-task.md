---
title: "Attivit&#224; Backup database | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.backupdatabasetask.f1"
helpviewer_keywords: 
  - "backup di database [Integration Services]"
  - "Backup database - attività [Integration Services]"
  - "backup di database [Integration Services]"
  - "backup di log delle transazioni [Integration Services]"
  - "backup di log delle transazioni [Integration Services]"
ms.assetid: b8839d71-13b7-41f2-a434-cb95020e79d7
caps.latest.revision: 46
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 46
---
# Attivit&#224; Backup database
  L'attività Backup database consente di eseguire diversi tipi di backup dei database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [Back Up and Restore of SQL Server Databases](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).  
  
 Tramite l'attività Backup database un pacchetto può eseguire il backup di uno o più database. Se si utilizza l'attività per eseguire il backup di un singolo database, sarà possibile scegliere il componente di cui eseguire il backup, ovvero il database o i relativi file e filegroup.  
  
## Modelli di recupero e tipi di backup supportati  
 Nella tabella seguente sono elencati i modelli di recupero e i tipi di backup supportati dall'attività Backup database.  
  
|Modello di recupero|Database|Differenziale del database|Log delle transazioni|File o differenziale del file|  
|--------------------|--------------|---------------------------|---------------------|-------------------------------|  
|Simple|Obbligatorio|Facoltativo|Non supportato|Non supportato|  
|Completo|Obbligatorio|Facoltativo|Obbligatorio|Facoltativo|  
|Registrazione minima delle operazioni bulk|Obbligatorio|Facoltativo|Obbligatorio|Facoltativo|  
  
 L'attività Backup database incapsula l'istruzione Transact-SQL BACKUP. Per altre informazioni, vedere [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md).  
  
## Configurazione dell'attività Backup database  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Questa attività è disponibile nella sezione **Attività di manutenzione** della casella degli strumenti **** di Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Per ulteriori informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , fare clic sull'argomento seguente:  
  
-   [Attività Backup database &#40;Piano di manutenzione&#41;](../../relational-databases/maintenance-plans/back-up-database-task-maintenance-plan.md)  
  
 Per altre informazioni sull'impostazione di queste proprietà in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , fare clic sull'argomento seguente:  
  
-   [Impostazione delle proprietà di un'attività o di un contenitore](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
  