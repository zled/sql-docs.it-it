---
title: managed_backup.sp_set_parameter (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_set_parameter_TSQL
- sp_set_parameter
- smart_admin.sp_set_parameter
- smart_admin.sp_set_parameter_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_set_parameter
- smart_admin.sp_set_parameter
ms.assetid: bd8ae5fd-1337-4b7f-b0a4-153cbca9fa5f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 578997f57c4092689e49cb0e3102c8bdf7b4f8d2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47843893"
---
# <a name="managedbackupspsetparameter-transact-sql"></a>managed_backup.sp_set_parameter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Imposta il valore del parametro di sistema dell'amministrazione intelligente specificato.  
  
 I parametri disponibili sono correlati al [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Questi parametri vengono utilizzati per impostare le notifiche tramite posta elettronica, abilitare eventi estesi specifici e abilitare i criteri di gestione basata su criteri impostati dall'utente. È necessario specificare il nome del parametro e le coppie di valori del parametro.  

  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
EXEC managed_backup.sp_set_parameter   
    [@parameter_name = ] {'SSMBackup2WANotificationEmailIds' | 'SSMBackup2WAEnableUserDefinedPolicy' | 'SSMBackup2WADebugXevent' | 'FileRetentionDebugXevent' | 'StorageOperationDebugXevent'}  
    ,[@parameter_value = ] 'parameter_value'  
```  
  
##  <a name="Arguments"></a> Argomenti  
 @parameter_name  
 Nome del parametro per cui si desidera impostare il valore. @parameter_name è nvarchar (128). I nomi dei parametri disponibili sono **SSMBackup2WANotificationEmailIds**, **SSMBackup2WADebugXevent**, **SSMBackup2WAEnableUserDefinedPolicy**, **FileRetentionDebugXevent**, e **StorageOperationDebugXevent**.  
  
 @parameter_value  
 Valore del parametro che si desidera impostare. @parameter il valore è nvarchar (128).  Di seguito vengono indicati il nome del parametro e le coppie di valori consentiti:  
  
-   @parameter_name = 'SSMBackup2WANotificationEmailIds': @parameter_value = "email"  
  
-   @parameter_name = 'SSMBackup2WAEnableUserDefinedPolicy' : @parameter_value  = { 'true' | 'false' }  
  
-   @parameter_name = 'SSMBackup2WADebugXevent': @parameter_value  = { 'true' | 'false' }  
  
-   @parameter_name = 'FileRetentionDebugXevent' : @parameter_value  = { 'true' | 'false' }  
  
-   @parameter_name = 'StorageOperationDebugXevent' = { 'true' | 'false' }  
  
## <a name="return-code-value"></a>Valore del codice restituito  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="best-practices"></a>Procedure consigliate  
 Sezione facoltativa in cui vengono descritte le procedure consigliate che l'utente deve conoscere quando viene eseguita l'istruzione o la routine.  
  
## <a name="security"></a>Sicurezza  
  
### <a name="permissions"></a>Permissions  
 È necessario **EXECUTE** autorizzazioni sul **managed_backup.sp_set_parameter** stored procedure.  
  
## <a name="examples"></a>Esempi  
 Negli esempi seguenti vengono abilitati eventi estesi operativi e di debug.  
  
```  
-- to enable operational events  
Use msdb;  
Go  
         EXEC managed_backup.sp_set_parameter 'FileRetentionOperationalXevent', 'True'  
--  to enable debug events  
Use msdb;  
Go  
         EXEC managed_backup.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
  
```  
  
 Nell'esempio seguente vengono abilitate le notifiche tramite posta elettronica di errori e avvisi e viene impostato l'ID di posta elettronica da utilizzare per inviare notifiche a:  
  
```  
Use msdb  
Go  
EXEC managed_backup.sp_set_parameter @parameter_name = 'SSMBackup2WANotificationEmailIds', @parameter_value = '<email address>'  
  
```  
  
  
