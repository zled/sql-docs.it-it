---
title: sp_help_log_shipping_monitor_primary (Transact-SQL) | Documenti Microsoft
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
- sp_help_log_shipping_monitor_primary
- sp_help_log_shipping_monitor_primary_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_log_shipping_monitor_primary
ms.assetid: d9dfcb8f-1da6-49ca-a2c8-411574915434
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d2a361718ab281ee376e4ebe4951bd582dc85a3a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sphelplogshippingmonitorprimary-transact-sql"></a>sp_help_log_shipping_monitor_primary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce le informazioni relative a un database primario dalle tabelle di monitoraggio.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_help_log_shipping_monitor_primary  
[ @primary_server = ] 'primary_server',   
[ @primary_database = ] 'primary_database'  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@primary_server =** ] '*primary_server*'  
 Il nome dell'istanza primaria del [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] nella configurazione di log shipping. *primary_server* viene **sysname** e non può essere NULL.  
  
 [  **@primary_database =** ] '*primary_database*'  
 Nome del database sul server primario. *primary_database* viene **sysname**, non prevede alcun valore predefinito.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Description|  
|-----------------|-----------------|  
|**primary_id**|ID del database primario nella configurazione per il log shipping.|  
|**primary_server**|Nome dell'istanza primaria di [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] nella configurazione per il log shipping.|  
|**primary_database**|Nome del database primario nella configurazione di log shipping.|  
|**backup_threshold**|Numero di minuti consentiti tra le operazioni di backup prima che venga generato un avviso.|  
|**threshold_alert**|Avviso da generare quando viene superata la soglia per il backup.|  
|**threshold_alert_enabled**|Determina se sono abilitati gli avvisi relativi alla soglia per il backup. 1 = abilitato; 0 = disabilitato.|  
|**last_backup_file**|Percorso assoluto del backup del log delle transazioni più recente.|  
|**last_backup_date**|Data e ora dell'ultima operazione di backup del log delle transazioni nel database primario.|  
|**last_backup_date_utc**|Data e ora dell'ultima operazione di backup del log delle transazioni nel database primario in base all'ora UTC (Coordinated Universal Time).|  
|**history_retention_period**|Intervallo di tempo, espresso in minuti, di conservazione dei record relativi alla cronologia di log shipping per un database primario specifico trascorso il quale i record vengono eliminati.|  
  
## <a name="remarks"></a>Osservazioni  
 **sp_help_log_shipping_monitor_primary** deve essere eseguita la **master** database nel server di monitoraggio.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server possono eseguire questa procedura.  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sul Log Shipping & #40; SQL Server & #41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
