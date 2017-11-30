---
title: sp_change_log_shipping_secondary_database (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_change_log_shipping_secondary_database
- sp_change_log_shipping_secondary_database_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_change_log_shipping_secondary_database
ms.assetid: 3ebcf2f1-980f-4543-a84b-fbaeea54eeac
caps.latest.revision: "23"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c3db64668b68f94eb2ebd919c231f8d8bf0c349c
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="spchangelogshippingsecondarydatabase-transact-sql"></a>sp_change_log_shipping_secondary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifica le impostazioni del database secondario.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_change_log_shipping_secondary_database  
[ @secondary_database = ] 'secondary_database',  
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
 [  **@restore_delay =** ] '*restore_delay*'  
 Indica per quanti minuti il server secondario deve attendere prima di ripristinare un file di backup specifico. *restore_delay* è **int** e non può essere NULL. Il valore predefinito è 0.  
  
 [  **@restore_all =** ] '*restore_all*'  
 Se impostato su 1, il server secondario ripristina tutti i backup del log delle transazioni disponibili al momento dell'esecuzione del processo di ripristino. In caso contrario, l'operazione viene arrestata dopo il ripristino di un file. *restore_all* è **bit** e non può essere NULL.  
  
 [  **@restore_mode =** ] '*restore_mode*'  
 Modalità di ripristino per il database secondario.  
  
 0 = ripristino log con NORECOVERY.  
  
 1 = Ripristina log con STANDBY.  
  
 *ripristinare* è **bit** e non può essere NULL.  
  
 [  **@disconnect_users =** ] '*disconnect_users*'  
 Se impostato su 1, gli utenti vengono disconnessi dal database secondario quando viene eseguita un'operazione di ripristino. Predefinito = 0. *disconnect_users* è **bit** e non può essere NULL.  
  
 [  **@block_size =** ] '*block_size*'  
 Dimensioni, in byte, per il blocco del dispositivo di backup. *block_size* è **int** con un valore predefinito-1.  
  
 [  **@buffer_count =** ] '*buffer_count*'  
 Numero totale di buffer utilizzati dall'operazione di backup o di ripristino. *buffer_count* è **int** con un valore predefinito-1.  
  
 [  **@max_transfer_size =** ] '*max_transfer_size*'  
 Dimensione, espressa in byte, della richiesta di input o output massimo emessa da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per il dispositivo di backup. *max_transfersize* è **int** e può essere NULL.  
  
 [  **@restore_threshold =** ] '*restore_threshold*'  
 Numero di minuti che può trascorrere tra operazioni di ripristino prima che venga generato un avviso. *restore_threshold* è **int** e non può essere NULL.  
  
 [  **@threshold_alert =** ] '*threshold_alert*'  
 Avviso da generare quando viene superato il valore di soglia per il ripristino. *threshold_alert* è **int**, il valore 14420 predefinito.  
  
 [  **@threshold_alert_enabled =** ] '*threshold_alert_enabled*'  
 Specifica se un avviso verrà generato quando *restore_threshold*viene superato. 1 = abilitato; 0 = disabilitato. *threshold_alert_enabled* è **bit** e non può essere NULL.  
  
 [  **@history_retention_period =** ] '*history_retention_period*'  
 Periodo di memorizzazione della cronologia espresso in minuti. *history_retention_period* è **int**. Se non viene specificato, verrà utilizzato il valore 1440.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 **sp_change_log_shipping_secondary_database** deve essere eseguita la **master** database nel server secondario. Questa stored procedure esegue le operazioni seguenti:  
  
1.  Modifica le impostazioni di **log_shipping_secondary_database** registra in base alle esigenze.  
  
2.  Modifica il record di monitoraggio locale in **log_shipping_monitor_secondary** nel server secondario utilizzando gli argomenti specificati, se necessario.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server possono eseguire questa procedura.  
  
## <a name="examples"></a>Esempi  
 In questo esempio viene illustrato l'utilizzo **sp_change_log_shipping_secondary_database** per aggiornare i parametri di database secondario per il database **LogShipAdventureWorks**.  
  
```  
EXEC master.dbo.sp_change_log_shipping_secondary_database   
 @secondary_database =  'LogShipAdventureWorks'  
,  @restore_delay = 0  
,  @restore_all = 1  
,  @restore_mode = 0  
,  @disconnect_users = 0  
,  @threshold_alert = 14420  
,  @threshold_alert_enabled = 1  
,  @history_retention_period = 14420;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sul log shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
