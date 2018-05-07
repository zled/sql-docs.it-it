---
title: sp_add_log_shipping_primary_database (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_add_log_shipping_primary_database
- sp_add_log_shipping_primary_database_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_log_shipping_primary_database
ms.assetid: 69531611-113f-46b5-81a6-7bf496d0353c
caps.latest.revision: 35
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 39627cca65071d2f08fe990c63d6e3ce836ce3b0
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="spaddlogshippingprimarydatabase-transact-sql"></a>sp_add_log_shipping_primary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Imposta il database primario per una configurazione di log shipping, inclusi il processo di backup, il record di monitoraggio locale e il record di monitoraggio remoto.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_add_log_shipping_primary_database [ @database = ] 'database',   
[ @backup_directory = ] 'backup_directory',   
[ @backup_share = ] 'backup_share',   
[ @backup_job_name = ] 'backup_job_name',   
[, [ @backup_retention_period = ] backup_retention_period]  
[, [ @monitor_server = ] 'monitor_server']  
[, [ @monitor_server_security_mode = ] monitor_server_security_mode]  
[, [ @monitor_server_login = ] 'monitor_server_login']  
[, [ @monitor_server_password = ] 'monitor_server_password']  
[, [ @backup_threshold = ] backup_threshold ]   
[, [ @threshold_alert = ] threshold_alert ]   
[, [ @threshold_alert_enabled = ] threshold_alert_enabled ]   
[, [ @history_retention_period = ] history_retention_period ]  
[, [ @backup_job_id = ] backup_job_id OUTPUT ]  
[, [ @primary_id = ] primary_id OUTPUT]  
[, [ @backup_compression = ] backup_compression_option ]  
  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@database=** ] '*database*'  
 Nome del database primario per il log shipping. *database* viene **sysname**, non prevede alcun valore predefinito e non può essere NULL.  
  
 [  **@backup_directory=** ] '*backup_directory*'  
 Percorso della cartella di backup nel server primario. *backup_directory* viene **nvarchar(500)**, non prevede alcun valore predefinito e non può essere NULL.  
  
 [  **@backup_share=** ] '*backup_share*'  
 Percorso di rete della directory di backup nel server primario. *backup_share* viene **nvarchar(500)**, non prevede alcun valore predefinito e non può essere NULL.  
  
 [  **@backup_job_name=** ] '*backup_job_name*'  
 Nome del processo di SQL Server Agent nel server primario che copia il backup nella cartella di backup. *backup_job_name* viene **sysname** e non può essere NULL.  
  
 [  **@backup_retention_period=** ] *backup_retention_period*  
 Periodo di tempo, in minuti, per cui il file di backup del log deve essere mantenuto nella directory di backup nel server primario. *backup_retention_period* viene **int**, non prevede alcun valore predefinito e non può essere NULL.  
  
 [ **@monitor_server=** ] '*monitor_server*'  
 Nome del server di monitoraggio. *Monitor_server* viene **sysname**, non prevede alcun valore predefinito e non può essere NULL.  
  
 [  **@monitor_server_security_mode=** ] *monitor_server_security_mode*  
 Modalità di sicurezza utilizzata per connettersi al server di monitoraggio.  
  
 1 = Autenticazione di Windows.  
  
 0 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione. *monitor_server_security_mode* viene **bit** e non può essere NULL.  
  
 [  **@monitor_server_login=** ] '*monitor_server_login*'  
 Nome utente dell'account utilizzato per accedere al server di monitoraggio.  
  
 [  **@monitor_server_password=** ] '*monitor_server_password*'  
 Password dell'account utilizzato per accedere al server di monitoraggio.  
  
 [  **@backup_threshold=** ] *backup_threshold*  
 Periodo di tempo, espresso in minuti, dopo l'ultimo backup prima di un *threshold_alert* viene generato l'errore. *backup_threshold* viene **int**, con un valore predefinito è 60 minuti.  
  
 [  **@threshold_alert=** ] *threshold_alert*  
 Avviso da generare quando viene superata la soglia per il backup. *threshold_alert* viene **int**, con un valore predefinito è 14,420.  
  
 [  **@threshold_alert_enabled=** ] *threshold_alert_enabled*  
 Specifica se un avviso verrà generato quando *backup_threshold* viene superato. Il valore predefinito 0 indica che l'avviso è disabilitato e non verrà generato. *threshold_alert_enabled* viene **bit**.  
  
 [  **@history_retention_period=** ] *history_retention_period*  
 Periodo di memorizzazione della cronologia espresso in minuti. *history_retention_period* viene **int**, con un valore predefinito è NULL. Se non si specifica un valore, verrà utilizzato il valore 14420.  
  
 [  **@backup_job_id=** ] *backup_job_id* OUTPUT  
 ID del processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent associato al processo di backup nel server primario. *backup_job_id* viene **uniqueidentifier** e non può essere NULL.  
  
 [  **@primary_id=** ] *primary_id* OUTPUT  
 ID del database primario nella configurazione per il log shipping. *primary_id* viene **uniqueidentifier** e non può essere NULL.  
  
 [ **@backup_compression**=] *backup_compression_option*  
 Specifica se una configurazione di log shipping utilizza [compressione dei backup](../../relational-databases/backup-restore/backup-compression-sql-server.md). Questo parametro è supportato solo in [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] o versione successiva.  
  
 0 = disabilitati. I backup del log non vengono mai compressi.  
  
 1 = abilitati. I backup del log vengono sempre compressi.  
  
 2 = utilizzare l'impostazione di [consente di visualizzare o configurare l'opzione di configurazione del Server di backup compression default](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md). Si tratta del valore predefinito.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 **sp_add_log_shipping_primary_database** deve essere eseguita la **master** database nel server primario. Questa stored procedure esegue le funzioni seguenti:  
  
1.  Genera un ID primario e aggiunge una voce per il database primario nella tabella **log_shipping_primary_databases** utilizzando gli argomenti specificati.  
  
2.  Crea un processo di backup per il database primario disabilitato.  
  
3.  Imposta l'ID di processo di backup di **log_shipping_primary_databases** voce per l'ID di processo del processo di backup.  
  
4.  Aggiunge un record di monitoraggio locale nella tabella **log_shipping_monitor_primary** nel server primario utilizzando gli argomenti specificati.  
  
5.  Se il server di monitoraggio è diverso dal server primario, aggiunge un record di monitoraggio in **log_shipping_monitor_primary** sul monitor di server utilizzando gli argomenti specificati.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server possono eseguire questa procedura.  
  
## <a name="examples"></a>Esempi  
 In questo esempio il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] viene aggiunto come database primario in una configurazione per il log shipping.  
  
```  
DECLARE @LS_BackupJobId AS uniqueidentifier ;  
DECLARE @LS_PrimaryId AS uniqueidentifier ;  
  
EXEC master.dbo.sp_add_log_shipping_primary_database   
@database = N'AdventureWorks'   
,@backup_directory = N'c:\lsbackup'   
,@backup_share = N'\\tribeca\lsbackup'   
,@backup_job_name = N'LSBackup_AdventureWorks'   
,@backup_retention_period = 1440  
,@monitor_server = N'rockaway'   
,@monitor_server_security_mode = 1   
,@backup_threshold = 60   
,@threshold_alert = 0   
,@threshold_alert_enabled = 0   
,@history_retention_period = 1440   
,@backup_job_id = @LS_BackupJobId OUTPUT   
,@primary_id = @LS_PrimaryId OUTPUT   
,@overwrite = 1   
,@backup_compression = 0;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sul Log Shipping & #40; SQL Server & #41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
