---
title: sp_change_log_shipping_secondary_primary (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_change_log_shipping_secondary_primary
- sp_change_log_shipping_secondary_primary_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_change_log_shipping_secondary_primary
ms.assetid: 5bcb4df7-6df3-4f2b-9207-b97b5addf2a6
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 26e82dc23da2641019fc0b6215dd633479ae0272
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="spchangelogshippingsecondaryprimary-transact-sql"></a>sp_change_log_shipping_secondary_primary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifica le impostazioni del database secondario.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_change_log_shipping_secondary_primary  
[ @primary_server = ] 'primary_server',  
[ @primary_database = ] 'primary_database',  
[, [ @backup_source_directory = ] 'backup_source_directory']  
[, [ @backup_destination_directory = ] 'backup_destination_directory']  
[, [ @file_retention_period = ] file_retention_period]  
[, [ @monitor_server_security_mode = ] monitor_server_security_mode]  
[, [ @monitor_server_login = ] 'monitor_server_login']  
[, [ @monitor_server_password = ] 'monitor_server_password']  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@primary_server** = ] '*primary_server*'  
 Il nome dell'istanza primaria del [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] nella configurazione di log shipping. *primary_server* è **sysname** e non può essere NULL.  
  
 [  **@primary_database**  =] '*primary_database*'  
 Nome del database sul server primario. *primary_database* è **sysname**, non prevede alcun valore predefinito.  
  
 [ **@backup_source_directory** = ] '*backup_source_directory*'  
 Directory in cui vengono archiviati i file di backup del log delle transazioni dal server primario. *backup_source_directory* è **nvarchar (500)** e non può essere NULL.  
  
 [  **@backup_destination_directory**  =] '*backup_destination_directory*'  
 Directory nel server secondario in cui vengono copiati i file di backup. *backup_destination_directory* è **nvarchar (500)** e non può essere NULL.  
  
 [  **@file_retention_period**  =] '*file_retention_period*'  
 Periodo di memorizzazione della cronologia espresso in minuti. *history_retention_period* è **int**, con un valore predefinito è NULL. Se non si specifica un valore, verrà utilizzato il valore 14420.  
  
 [ **@monitor_server_security_mode** = ] '*monitor_server_security_mode*'  
 Modalità di sicurezza utilizzata per connettersi al server di monitoraggio.  
  
 1 = Autenticazione di Windows  
  
 0 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione. *monitor_server_security_mode* è **bit** e non può essere NULL.  
  
 [ **@monitor_server_login** = ] '*monitor_server_login*'  
 Nome utente dell'account utilizzato per accedere al server di monitoraggio.  
  
 [ **@monitor_server_password** = ] '*monitor_server_password*'  
 Password dell'account utilizzato per accedere al server di monitoraggio.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 **sp_change_log_shipping_secondary_primary** deve essere eseguita la **master** database nel server secondario. Questa stored procedure esegue le operazioni seguenti:  
  
1.  Modifica le impostazioni nel **log_shipping_secondary** registra in base alle esigenze.  
  
2.  Se il server di monitoraggio è diverso dal server secondario, modifiche record di monitoraggio in **log_shipping_monitor_secondary** sul monitor di server utilizzando gli argomenti specificati, se necessario.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server possono eseguire questa procedura.  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sul Log Shipping &#40; SQL Server &#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
