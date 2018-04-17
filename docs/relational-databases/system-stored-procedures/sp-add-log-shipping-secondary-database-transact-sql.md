---
title: sp_add_log_shipping_secondary_database (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
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
- sp_add_log_shipping_secondary_database
- sp_add_log_shipping_secondary_database_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_log_shipping_secondary_database
ms.assetid: d29e1c24-3a3c-47a4-a726-4584afa6038a
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c2cc8460059274458016d24e106e554f78394618
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="spaddlogshippingsecondarydatabase-transact-sql"></a>sp_add_log_shipping_secondary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Imposta un database secondario per il log shipping.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_add_log_shipping_secondary_database  
[ @secondary_database = ] 'secondary_database',  
[ @primary_server = ] 'primary_server',   
[ @primary_database = ] 'primary_database',  
[, [ @restore_delay = ] 'restore_delay']  
[, [ @restore_all = ] 'restore_all']  
[, [ @restore_mode = ] 'restore_mode']  
[, [ @disconnect_users = ] 'disconnect_users']  
[, [ @block_size = ] 'block_size']  
[, [ @buffer_count = ] 'buffer_count']  
[, [ @max_transfer_size = ] 'max_transfer_size']  
[, [ @restore_threshold = ] 'restore_threshold']   
[, [ @threshold_alert = ] 'threshold_alert']   
[, [ @threshold_alert_enabled = ] 'threshold_alert_enabled']   
[, [ @history_retention_period = ] 'history_retention_period']  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@secondary_database** =] '*secondary_database*'  
 Nome del database secondario. *secondary_database* viene **sysname**, non prevede alcun valore predefinito.  
  
 [ **@primary_server** = ] '*primary_server*'  
 Il nome dell'istanza primaria del [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] nella configurazione di log shipping. *primary_server* viene **sysname** e non può essere NULL.  
  
 [ **@primary_database** =] '*primary_database*'  
 Nome del database sul server primario. *primary_database* viene **sysname**, non prevede alcun valore predefinito.  
  
 [ **@restore_delay** =] '*restore_delay*'  
 Indica per quanti minuti il server secondario deve attendere prima di ripristinare un file di backup specifico. *restore_delay* viene **int** e non può essere NULL. Il valore predefinito è 0.  
  
 [ **@restore_all** =] '*restore_all*'  
 Se impostato su 1, il server secondario ripristina tutti i backup del log delle transazioni disponibili al momento dell'esecuzione del processo di ripristino. In caso contrario, l'operazione viene arrestata dopo il ripristino di un file. *restore_all* viene **bit** e non può essere NULL.  
  
 [ **@restore_mode** =] '*restore_mode*'  
 Modalità di ripristino per il database secondario.  
  
 0 = Ripristina log con NORECOVERY.  
  
 1 = Ripristina log con STANDBY.  
  
 *ripristinare* viene **bit** e non può essere NULL.  
  
 [ **@disconnect_users** =] '*disconnect_users*'  
 Se impostato su 1, gli utenti vengono disconnessi dal database secondario quando viene eseguita un'operazione di ripristino. Predefinito = 0. *disconnettere* agli utenti viene **bit** e non può essere NULL.  
  
 [ **@block_size** =] '*block_size*'  
 Dimensioni, in byte, per il blocco del dispositivo di backup. *block_size* viene **int** con valore predefinito è -1.  
  
 [ **@buffer_count** =] '*buffer_count*'  
 Numero totale di buffer utilizzati dall'operazione di backup o di ripristino. *buffer_count* viene **int** con valore predefinito è -1.  
  
 [ **@max_transfer_size** = ] '*max_transfer_size*'  
 Dimensione, espressa in byte, della richiesta di input o output massimo emessa da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per il dispositivo di backup. *max_transfersize* viene **int** e può essere NULL.  
  
 [ **@restore_threshold** =] '*restore_threshold*'  
 Numero di minuti che può trascorrere tra operazioni di ripristino prima che venga generato un avviso. *restore_threshold* viene **int** e non può essere NULL.  
  
 [ **@threshold_alert** =] '*threshold_alert*'  
 Avviso da generare quando viene superata la soglia per il backup. *threshold_alert* viene **int**, con un valore predefinito è 14,420.  
  
 [ **@threshold_alert_enabled** =] '*threshold_alert_enabled*'  
 Specifica se viene generato un avviso quando *backup_threshold* viene superato. Il valore 1 (valore predefinito) indica che l'avviso viene generato. *threshold_alert_enabled* viene **bit**.  
  
 [ **@history_retention_period** =] '*history_retention_period*'  
 Periodo di memorizzazione della cronologia espresso in minuti. *history_retention_period* viene **int**, con un valore predefinito è NULL. Se non si specifica un valore, verrà utilizzato il valore 14420.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 **sp_add_log_shipping_secondary_database** deve essere eseguita la **master** database nel server secondario. Questa stored procedure esegue le operazioni seguenti:  
  
1.  **sp_add_log_shipping_secondary_primary** deve essere chiamato prima di questa stored procedure per inizializzare primario per il log shipping informazioni del database nel server secondario.  
  
2.  Aggiunge una voce per il database secondario in **log_shipping_secondary_databases** utilizzando gli argomenti specificati.  
  
3.  Aggiunge un record di monitoraggio locale in **log_shipping_monitor_secondary** nel server secondario utilizzando gli argomenti specificati.  
  
4.  Se il server di monitoraggio è diverso dal server secondario, aggiunge un record di monitoraggio in **log_shipping_monitor_secondary** sul monitor di server utilizzando gli argomenti specificati.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server possono eseguire questa procedura.  
  
## <a name="examples"></a>Esempi  
 In questo esempio viene illustrato l'utilizzo di **sp_add_log_shipping_secondary_database** stored procedure per aggiungere il database di **LogShipAdventureWorks** come database secondario in una configurazione di log shipping con il database primario [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] che si trovano nel server primario TRIBECA.  
  
```  
EXEC master.dbo.sp_add_log_shipping_secondary_database   
@secondary_database = N'LogShipAdventureWorks'   
,@primary_server = N'TRIBECA'   
,@primary_database = N'AdventureWorks2012'   
,@restore_delay = 0   
,@restore_mode = 1   
,@disconnect_users = 0   
,@restore_threshold = 45     
,@threshold_alert_enabled = 0   
,@history_retention_period = 1440 ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sul Log Shipping & #40; SQL Server & #41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
