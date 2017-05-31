---
title: Migrare le impostazioni di backup gestito di SQL Server 2014 a SQL Server 2016 | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae937ebb-24ff-4a33-be3c-8f85328dfc75
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 902ad2ddd95a26f36ff9519e55d7af77ca7e2d8a
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="migrate-sql-server-2014-managed-backup-settings-to-sql-server-2016"></a>Migrare le impostazioni di backup gestito di SQL Server 2014 a SQL Server 2016
  Questo argomento illustra le considerazioni sulla migrazione per [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] durante l'aggiornamento da [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] a [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  
  
 Le procedure e il comportamento sottostante di [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] sono state modificate in [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. Le sezioni seguenti descrivono le modifiche funzionali e le relative implicazioni.  
  
## <a name="overview"></a>Panoramica  
 La tabella seguente descrive alcune delle principali differenze funzionali per [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] tra [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] e [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  
  
|Area|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|  
|----------|---------------------------|---------------------------|  
|**Spazio dei nomi:**|smart_admin|managed_backup|  
|**Stored procedure di sistema:**|sp_set_db_backup<br /><br /> sp_set_instance_backup|[managed_backup.sp_backup_config_basic (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md)<br /><br /> [sp_backup_config_advanced](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-advanced-transact-sql.md)<br /><br /> [sp_backup_config_schedule](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-schedule-transact-sql.md)|  
|**Sicurezza:**|Credenziali SQL usando un account di archiviazione e una chiave di accesso di Microsoft Azure.|Credenziali SQL usando un token di firma di accesso condiviso di Microsoft Azure.|  
|**Archiviazione sottostante:**|Archiviazione di Microsoft Azure usando BLOB di pagine.|Archiviazione di Microsoft Azure usando BLOB di blocchi.|  
  
## <a name="benefits"></a>Vantaggi  
 Esistono diversi vantaggi offerti dall'uso delle nuove funzionalità di [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  
  
-   L'archiviazione BLOB in blocchi è meno costosa.  
  
-   Con lo striping è possibile archiviare backup di dimensioni molto maggiori (12 TB e 1 TB per BLOB di pagine).  
  
-   Lo striping migliora anche il tempo di ripristino per database di grandi dimensioni  
  
-   Per conoscere gli altri miglioramenti apportati a [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] in [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)][Backup gestito di SQL Server in Microsoft Azure](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)  
  
## <a name="considerations"></a>Considerazioni  
 Dopo l'aggiornamento da [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], tenere presenti le considerazioni di [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] seguenti:  
  
-   Qualsiasi database configurato in precedenza per [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] continuerà a usare le procedure di sistema e il comportamento sottostante di **smart_admin** in [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  
  
-   Le procedure **smart_admin** non sono supportate per le nuove configurazioni di [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] in [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. È necessario usare le nuove procedure e funzionalità **managed_backup** .  
  
## <a name="see-also"></a>Vedere anche  
 [Backup gestito di SQL Server in Microsoft Azure](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)  
  
  
