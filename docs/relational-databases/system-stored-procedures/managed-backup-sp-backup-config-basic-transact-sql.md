---
title: managed_backup.sp_backup_config_basic (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/03/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_backup_config_basic_TSQL
- sp_backup_config_basic
- managed_backup.sp_backup_config_basic
- managed_backup.sp_backup_config_basic_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- managed_backup.sp_backup_config_basic
- sp_backup_config_basic
ms.assetid: 3ad73051-ae9a-4e41-a889-166146e5508f
caps.latest.revision: 15
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4b1134b0fdf68761a307133bdc9d1f99a906ccf7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="managedbackupspbackupconfigbasic-transact-sql"></a>managed_backup.sp_backup_config_basic (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Configura il [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] le impostazioni di base per un database specifico o per un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Questa procedura può essere chiamata su una proprio per creare una configurazione di backup gestita di base. Tuttavia, se si prevede di aggiungere funzionalità avanzate o una pianificazione personalizzata, prima di tutto configurare tali impostazioni mediante [managed_backup. sp_backup_config_advanced &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-advanced-transact-sql.md) e [managed_backup.sp_ backup_config_schedule &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-schedule-transact-sql.md) prima di abilitare il backup gestito con questa procedura.  
   
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```Transact-SQL   
EXEC managed_backup.sp_backup_config_basic  
    [@enable_backup = ] { 0 | 1}    ,[@database_name = ] 'database_name'    ,[@container_url = ] 'Azure_Storage_blob_container  
    ,[@retention_days = ] 'retention_period_in_days'    ,[@credential_name = ] 'sql_credential_name'  
```  
  
##  <a name="Arguments"></a> Argomenti  
 @enable_backup  
 Abilitare o disabilitare il [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] per il database specificato. Il @enable_backup è **BIT**. Parametro obbligatorio quando si configura [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] per la prima istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se si modifica un'esistente [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] configurazione, questo parametro è facoltativo. In tal caso, i valori di configurazione specificati non mantengono i valori esistenti.  
  
 @database_name  
 Il nome del database per l'attivazione di backup gestito in un database specifico.  
  
 @container_url  
 Un URL che indica la posizione del backup. Quando @credential_name è NULL, questo URL è un URL di firma di accesso condiviso a un contenitore blob in archiviazione di Azure e i backup di usare la nuova funzionalità di backup in blocco blob. Per ulteriori informazioni, vedere [SAS comprensione](http://azure.microsoft.com/documentation/articles/storage-dotnet-shared-access-signature-part-1/). Quando @credential_name viene specificato, si tratta di un URL di account di archiviazione e i backup utilizzano il backup deprecato funzionalità di blob di pagina.  
  
> [!NOTE]  
>  In questo momento, solo un URL SAS è supportato per questo parametro.  
  
 @retention_days  
 Periodo di conservazione dei file di backup espresso in giorni. Il @storage_url è INT. Si tratta di un parametro obbligatorio quando si configura [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] per la prima volta nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Durante la modifica di [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] configurazione, questo parametro è facoltativo. Se non specificato, vengono mantenuti i valori di configurazione esistenti.  
  
 @credential_name  
 Nome delle credenziali SQL utilizzate per l'autenticazione per l'account di archiviazione di Windows Azure. @credentail_name viene **SYSNAME**. Quando specificato, il backup viene archiviato in un blob di pagine. Se questo parametro è NULL, il backup verrà archiviato come blob in blocchi. Backup in blob di pagine è deprecato, pertanto è preferibile utilizzare la nuova funzionalità backup di blob di blocco. Quando utilizzato per modificare la configurazione di [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)], questo parametro è facoltativo. Se non specificato, vengono mantenuti i valori di configurazione esistente.  
  
> [!WARNING]  
>  Il **@credential_name** parametro non è supportato in questo momento. È supportato solo backup per bloccare i blob, che richiede questo parametro deve essere NULL.  
  
## <a name="return-code-value"></a>Valore del codice restituito  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="security"></a>Sicurezza  
  
### <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza **db_backupoperator** ruolo del database con **ALTER ANY CREDENTIAL** , autorizzazioni e **EXECUTE** le autorizzazioni per **sp_delete _ BackupHistory** stored procedure.  
  
## <a name="examples"></a>Esempi  
 Tramite i comandi di PowerShell di Azure più recenti, è possibile creare il contenitore di account di archiviazione sia l'URL di firma di accesso condiviso. Nell'esempio seguente crea un nuovo contenitore, mycontainer, nell'account di archiviazione mystorageaccount e quindi Ottiene un URL SAS per tale con le autorizzazioni complete.  
  
```powershell  
$context = New-AzureStorageContext -StorageAccountName mystorageaccount -StorageAccountKey (Get-AzureStorageKey -StorageAccountName mystorageaccount).Primary  
New-AzureStorageContainer -Name mycontainer -Context $context  
New-AzureStorageContainerSASToken -Name mycontainer -Permission rwdl -FullUri -Context $context  
```  
  
 L'esempio seguente abilita [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] per l'istanza di SQL Server viene eseguito, imposta i criteri di conservazione su 30 giorni, imposta la destinazione in un contenitore denominato 'mycontainer' in un account di archiviazione denominato 'mystorageaccount'.  
  
```Transact-SQL 
Use msdb;  
Go  
   EXEC managed_backup.sp_backup_config_basic  
                @enable_backup=1  
                ,@container_url = 'https://mystorageaccount.blob.core.windows.net/mycontainer'  
                ,@retention_days=30;   
GO  
  
```
  
 Nell'esempio seguente viene disabilitato [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] per l'istanza di SQL Server sui cui è in esecuzione.  
  
```Transact-SQL  
Use msdb;  
Go  
EXEC managed_backup.sp_backup_config_basic  
                @enable_backup=0;  
GO  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [managed_backup.sp_backup_config_advanced &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-advanced-transact-sql.md)   
 [managed_backup.sp_backup_config_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-schedule-transact-sql.md)  
  
  
