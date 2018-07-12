---
title: Configurare il Backup gestito (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.managedbackup.configure.f1
ms.assetid: 79397cf6-0611-450a-b0d8-e784a76e3091
caps.latest.revision: 9
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4d09c001bc7c267b2235377a1312609ee8b7b3fa
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37209831"
---
# <a name="configure-managed-backup-sql-server-management-studio"></a>Configurare il backup gestito (SQL Server Management Studio)
  Il **Backup gestito** finestra di dialogo consente di configurare [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] valori predefiniti per l'istanza. In questo argomento viene descritto come utilizzare questa finestra di dialogo per configurare [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] impostazioni per l'istanza e in tal caso, è necessario considerare le opzioni predefinite. Quando si [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] è configurato per l'istanza, le impostazioni vengono applicate a qualsiasi nuovo database creato successivamente.  
  
 Se si desidera configurare [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] per un database specifico, vedere [abilitare e configurare SQL Server Managed Backup to Windows Azure per un Database](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md#DatabaseConfigure).  
 
> [!NOTE] 
> Il backup gestito di SQL Server non è supportato con i server proxy. 
  
## <a name="task-list"></a>Elenco attività  
  
## <a name="includesssmartbackupincludesss-smartbackup-mdmd-functions-using-managed-backup-interface-in-sql-server-management-studio"></a>[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Le funzioni usando Managed interfaccia Backup in SQL Server Management Studio  
 In questa versione, è possibile configurare solo le impostazioni predefinite a livello di istanza utilizzando il **Gestione Backup** interfaccia. Non è possibile configurare [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] per un database, sospendere o riprendere [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] operazioni o le notifiche di posta elettronica il programma di installazione. Per informazioni su come eseguire operazioni non è attualmente supportate tramite il **Backup gestito** l'interfaccia, vedere [SQL Server Managed Backup to Windows Azure - impostazioni di archiviazione e memorizzazione](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 **Visualizza il nodo Backup gestito è SQL Server Management Studio:** per visualizzare **Backup gestito** nodo **Esplora oggetti**, è necessario essere un amministratore di sistema o disporre delle seguenti autorizzazioni concesse in modo specifico al proprio account utente:  
  
-   `db_backupoperator`  
  
-   `VIEW SERVER STATE`  
  
-   `ALTER ANY CREDENTIAL`  
  
-   `VIEW ANY DEFINITION`  
  
-   `EXECUTE` in `smart_admin.fn_is_master_switch_on`.  
  
-   `SELECT` in `smart_admin.fn_backup_instance_config`.  
  
 **Per configurare il Backup gestito:** per configurare [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] in SQL Server Management Studio, è necessario essere un amministratore di sistema o disporre delle autorizzazioni seguenti:  
  
 L'appartenenza al `db_backupoperator` ruolo del database con `ALTER ANY CREDENTIAL` le autorizzazioni, e `EXECUTE` le autorizzazioni per `sp_delete_backuphistory` stored procedure.  
  
 `SELECT` le autorizzazioni per il `smart_admin.fn_get_current_xevent_settings` (funzione).  
  
 `EXECUTE` le autorizzazioni per il `smart_admin.sp_get_backup_diagnostics` stored procedure. È inoltre richiesta l'autorizzazione `VIEW SERVER STATE` poiché vengono chiamati internamente altri oggetti di sistema che richiedono tale autorizzazione.  
  
 `EXECUTE` le autorizzazioni per `smart_admin.sp_set_instance_backup`, e `smart_admin.sp_backup_master_switch`.  
  
## <a name="configure-includesssmartbackupincludesss-smartbackup-mdmd-using-sql-server-management-studio"></a>Configurare [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] tramite SQL Server Management Studio  
 Dal **Esplora oggetti**, espandere il **Management** nodo e a destra fare clic su **Backup gestito di**. Selezionare **Configura**. Viene aperta la finestra di dialogo **Backup gestito** .  
  
 Controllare **abilitare il Backup gestito** opzione e specificare i valori di configurazione:  
  
 Il **File di conservazione** periodo viene specificato in giorni e deve essere compreso tra 1 e 30.  
  
 Il **credenziali SQL** è select deve corrispondere all'account di archiviazione. Se attualmente non è una credenziale di SQL che archivia le informazioni di autenticazione, è possibile crearne uno facendo **Create**. È anche possibile creare le credenziali usando l'istruzione Transact-SQL CREATE CREDENTIAL e fornire il nome account di archiviazione per l'identità e la chiave di accesso per i parametri chiave privati. Per altre informazioni, vedere [creare una credenziale](../relational-databases/backup-restore/sql-server-backup-to-url.md#credential).  
  
 Specificare il **URL di archiviazione** per l'account di archiviazione Windows Azure, le credenziali SQL che archivia le informazioni di autenticazione per l'account di archiviazione e il periodo di conservazione per i file di backup.  
  
 Il formato di URL di archiviazione: https://\<StorageAccount >.blob.core.windows.net/  
  
 Per impostare le impostazioni di crittografia a livello di istanza, controllare **Crittografa file di Backup** opzione e specificare l'algoritmo e un certificato o chiave asimmetrica da usare per la crittografia.  Questa proprietà è impostata a livello di istanza e viene usata per tutti i nuovi database creati dopo l'applicazione di questa configurazione.  
  
> [!WARNING]  
>  Questa finestra di dialogo non può essere usata per specificare le opzioni di crittografia senza configurare [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]. Queste opzioni di crittografia si applicano solo a [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] operazioni. Per utilizzare la crittografia per altre procedure di backup, vedere [crittografia dei Backup](../relational-databases/backup-restore/backup-encryption.md).  
  
### <a name="considerations"></a>Considerazioni  
 Se si configura [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] a livello di istanza, le impostazioni vengono applicate a qualsiasi nuovo database creato successivamente.  Tuttavia, i database esistenti non ereditano automaticamente queste impostazioni. Per configurare [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] su database già esistenti, è necessario configurare ogni database in modo specifico. Per altre informazioni, vedere [abilitare e configurare SQL Server Managed Backup to Windows Azure per un Database](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md#DatabaseConfigure).  
  
 Se [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] è stato sospeso tramite il `smart_admin.sp_backup_master_switch`, verrà visualizzato un messaggio di avviso "Backup gestito è disabilitato e le configurazioni correnti non avranno effetto..." quando si tenta di completare la configurazione. Usare la `smart_admin.sp_backup_master_switch` archiviata e impostare il @new_state= 1. Questa attività riprenderà [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] servizi e le impostazioni di configurazione diventeranno attive. Per altre informazioni sulla stored procedure, vedere [smart_admin.sp_ backup_master_switch &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-master-switch-transact-sql).  
  
## <a name="see-also"></a>Vedere anche  
 [Backup gestito di SQL Server in Windows Azure: interoperabilità e coesistenza](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)  
  
  
