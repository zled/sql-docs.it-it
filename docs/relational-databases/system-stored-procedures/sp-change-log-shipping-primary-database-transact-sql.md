---
title: sp_change_log_shipping_primary_database (Transact-SQL) | Microsoft Docs
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
- sp_change_log_shipping_primary_database
- sp_change_log_shipping_primary_database_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_change_log_shipping_primary_database
ms.assetid: 8c9dce6b-d2a3-4ca7-a832-8f59a5adb214
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b064cf2e2005a495f077682404fb7569f683d245
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43033464"
---
# <a name="spchangelogshippingprimarydatabase-transact-sql"></a>sp_change_log_shipping_primary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifica le impostazioni del database primario.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_change_log_shipping_primary_database [ @database = ] 'database'  
[, [ @backup_directory = ] 'backup_directory']   
[, [ @backup_share = ] 'backup_share']   
[, [ @backup_retention_period = ] 'backup_retention_period']  
[, [ @monitor_server_security_mode = ] 'monitor_server_security_mode']  
[, [ @monitor_server_login = ] 'monitor_server_login']  
[, [ @monitor_server_password = ] 'monitor_server_password']  
[, [ @backup_threshold = ] 'backup_threshold']   
[, [ @threshold_alert = ] 'threshold_alert']   
[, [ @threshold_alert_enabled = ] 'threshold_alert_enabled']   
[, [ @history_retention_period = ] 'history_retention_period']  
[, [ @backup_compression = ] backup_compression_option ]   
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@database =** ] '*database*'  
 Nome del database sul server primario. *primary_database* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@backup_directory =** ] '*backup_directory*'  
 Percorso della cartella di backup nel server primario. *backup_directory* viene **nvarchar(500)**, non prevede alcun valore predefinito e non può essere NULL.  
  
 [  **@backup_share =** ] '*backup_share*'  
 Percorso di rete della directory di backup nel server primario. *backup_share* viene **nvarchar(500)**, non prevede alcun valore predefinito e non può essere NULL.  
  
 [  **@backup_retention_period =** ] '*backup_retention_period*'  
 Periodo di tempo, in minuti, per cui il file di backup del log deve essere mantenuto nella directory di backup nel server primario. *backup_retention_period* viene **int**, non prevede alcun valore predefinito e non può essere NULL.  
  
 [  **@monitor_server_security_mode =** ] '*monitor_server_security_mode*'  
 Modalità di sicurezza utilizzata per connettersi al server di monitoraggio.  
  
 1 = Autenticazione di Windows.  
  
 0 = Autenticazione di SQL Server.  
  
 *monitor_server_security_mode* viene **bit** e non può essere NULL.  
  
 [  **@monitor_server_login =** ] '*monitor_server_login*'  
 Nome utente dell'account utilizzato per accedere al server di monitoraggio.  
  
 [  **@monitor_server_password =** ] '*monitor_server_password*'  
 Password dell'account utilizzato per accedere al server di monitoraggio.  
  
 [  **@backup_threshold =** ] '*backup_threshold*'  
 Periodo di tempo, espresso in minuti, trascorso dall'ultimo backup prima di un *threshold_alert* viene generato un errore. *backup_threshold* viene **int**, con un valore predefinito è 60 minuti.  
  
 [  **@threshold_alert =** ] '*threshold_alert*'  
 Avviso da generare quando viene superata la soglia per il backup. *threshold_alert* viene **int** e non può essere NULL.  
  
 [  **@threshold_alert_enabled =** ] '*threshold_alert_enabled*'  
 Specifica se viene generato un avviso quando si *backup_threshold* viene superato.  
  
 1 = Abilitato.  
  
 0 = Disabilitato.  
  
 *threshold_alert_enabled* viene **bit** e non può essere NULL.  
  
 [  **@history_retention_period =** ] '*history_retention_period*'  
 Periodo di memorizzazione della cronologia espresso in minuti. *history_retention_period* viene **int**. Se non si specifica un valore, verrà utilizzato il valore 14420.  
  
 [ **@backup_compression**=] *backup_compression_option*  
 Specifica se Usa una configurazione di log shipping [compressione dei backup](../../relational-databases/backup-restore/backup-compression-sql-server.md). Questo parametro è supportato solo in [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] o versione successiva.  
  
 0 = disabilitati. I backup del log non vengono mai compressi.  
  
 1 = abilitati. I backup del log vengono sempre compressi.  
  
 2 = utilizzare l'impostazione delle [visualizzare o configurare l'opzione di configurazione del Server backup compression default](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md). Si tratta del valore predefinito.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 None  
  
## <a name="remarks"></a>Note  
 **sp_change_log_shipping_primary_database** deve essere eseguita la **master** database nel server primario. Questa stored procedure esegue le operazioni seguenti:  
  
1.  Modifica le impostazioni nel **log_shipping_secondary_database** registrare, se necessario.  
  
2.  Modifica il record locale in **log_shipping_monitor_primary** nel server primario utilizzando gli argomenti specificati, se necessario.  
  
3.  Se il server di monitoraggio è diverso dal server primario, modifica il record in **log_shipping_monitor_primary** sul monitor server utilizzando gli argomenti specificati, se necessario.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server può eseguire questa procedura.  
  
## <a name="examples"></a>Esempi  
 In questo esempio viene illustrato l'utilizzo del **sp_change_log_shipping_primary_database** per aggiornare le impostazioni associate al database primario [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
EXEC master.dbo.sp_change_log_shipping_primary_database   
 @database = N'AdventureWorks'   
, @backup_directory = N'c:\LogShipping'   
, @backup_share = N'\\tribeca\LogShipping'   
, @backup_retention_period = 1440   
, @backup_threshold = 60   
, @threshold_alert = 0   
, @threshold_alert_enabled = 1   
, @history_retention_period = 1440   
,@monitor_server_security_mode = 1  
,@backup_compression = 1;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sul log shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [log_shipping_primary_databases &#40;Transact-SQL&#41;](../../relational-databases/system-tables/log-shipping-primary-databases-transact-sql.md)  
  
  
