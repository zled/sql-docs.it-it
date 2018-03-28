---
title: managed_backup.sp_backup_config_schedule (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql-non-specified
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
- sp_backup_config_schedule_TSQL
- managed_backup.sp_backup_config_schedule
- managed_backup.sp_backup_config_schedule_TSQL
- sp_backup_config_schedule
dev_langs:
- TSQL
helpviewer_keywords:
- managed_backup.sp_backup_config_schedule
- sp_backup_config_schedule
ms.assetid: 82541160-d1df-4061-91a5-6868dd85743a
caps.latest.revision: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6325c940487b37fea083a923a20f884bd872a0b4
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2018
---
# <a name="managedbackupspbackupconfigschedule-transact-sql"></a>managed_backup.sp_backup_config_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Configura opzioni di pianificazione automatica o personalizzate per [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
    
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
EXEC managed_backup.sp_backup_config_schedule   
    [@database_name = ] 'database_name'    ,[@scheduling_option = ] {'Custom' | 'System'}  
    ,[@full_backup_freq_type = ] {'Daily' | 'Weekly'}  
    ,[@days_of_week = ] 'days_of_the_week'  
    ,[@backup_begin_time = ] 'begin time of the backup window'  
    ,[@backup_duration = ] 'backup window length'  
    ,[@log_backup_freq = ] 'frequency of log backup'  
```  
  
##  <a name="Arguments"></a> Argomenti  
 @database_name  
 Il nome del database per l'attivazione di backup gestito in un database specifico. Se è NULL o *, il backup gestito si applicano a tutti i database nel server.  
  
 @scheduling_option  
 Specificare 'System' per la pianificazione del backup e controllato dal sistema. Specificare 'Custom' per una pianificazione personalizzata definita per i parametri di altro.  
  
 @full_backup_freq_type  
 Il tipo di frequenza per l'operazione di backup gestito, che può essere impostata su 'Weekly' o 'Daily'.  
  
 @days_of_week  
 I giorni della settimana per i backup quando @full_backup_freq_type è impostata su settimanale. Specificare nomi di stringa completa come "Lunedì".  È inoltre possibile specificare più di nome di un giorno, separati da Pipe. Ad esempio N'Monday | Mercoledì | Venerdì '.  
  
 @backup_begin_time  
 L'ora di inizio della finestra di backup. I backup non verranno avviati all'esterno dell'intervallo di tempo, definito da una combinazione di @backup_begin_time e @backup_duration.  
  
 @backup_duration  
 La durata dell'intervallo di tempo di backup. Si noti che non c'è garanzia che i backup verranno completati durante il periodo di tempo definito da @backup_begin_time e @backup_duration. Operazioni di backup che vengono avviate nell'intervallo di tempo ma superano la durata della finestra non verranno annullate.  
  
 @log_backup_freq  
 Questa impostazione determina la frequenza di backup del log delle transazioni. Questi backup eseguito a intervalli regolari anziché in base alla pianificazione specificata per il backup del database. @log_backup_freq può essere espresso in minuti o ore e 0 è valida, a non indicare alcun backup del log. La disabilitazione di backup del log solo sarebbe ideale per i database con un modello di recupero con registrazione minima.  
  
> [!NOTE]  
>  Se il modello di recupero viene modificato da simple a full, è necessario riconfigurare il log_backup_freq da 0 a un valore diverso da zero.  
  
## <a name="return-code-value"></a>Valore del codice restituito  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="security"></a>Sicurezza  
  
### <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza **db_backupoperator** ruolo del database con **ALTER ANY CREDENTIAL** , autorizzazioni e **EXECUTE** le autorizzazioni per **sp_delete _ BackupHistory** stored procedure.  
  
## <a name="see-also"></a>Vedere anche  
 [managed_backup.sp_backup_config_basic (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md)   
 [managed_backup.sp_backup_config_advanced &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-advanced-transact-sql.md)  
  
  
