---
title: log_shipping_secondary_databases (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- log_shipping_secondary_databases_TSQL
- log_shipping_secondary_databases
dev_langs:
- TSQL
helpviewer_keywords:
- log_shipping_secondary_databases system table
ms.assetid: ba2374af-86b8-480c-a10c-51e7c4e3ae23
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b21229c59cf54e500c47942a2bc2d763c776b330
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="logshippingsecondarydatabases-transact-sql"></a>log_shipping_secondary_databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Archivia un record per database secondario in una configurazione per il log shipping. Questa tabella è archiviata nel **msdb** database.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**secondary_database**|**sysname**|Nome del database secondario nella configurazione di log shipping.|  
|**secondary_id**|**uniqueidentifier**|ID del server secondario nella configurazione per il log shipping.|  
|**restore_delay**|**int**|Tempo massimo di attesa, in minuti, prima che il server secondario ripristini un file di backup specificato. Il valore predefinito è 0 minuti.|  
|**restore_all**|**bit**|Se impostato su 1, il server secondario ripristina tutti i backup del log delle transazioni disponibili al momento dell'esecuzione del processo di ripristino. In caso contrario, l'operazione viene arrestata dopo il ripristino di un file.|  
|**restore_mode**|**bit**|Modalità di ripristino per il database secondario.<br /><br /> 0 = Ripristina log con NORECOVERY.<br /><br /> 1 = Ripristina log con STANDBY.|  
|**disconnect_users**|**bit**|Se impostato su 1, gli utenti vengono disconnessi dal database secondario quando viene eseguita un'operazione di ripristino. Il valore predefinito è 0.|  
|**block_size**|**int**|Dimensioni, in byte, per il blocco del dispositivo di backup.|  
|**buffer_count**|**int**|Numero totale di buffer utilizzati dall'operazione di backup o di ripristino.|  
|**max_transfer_size**|**int**|Le dimensioni, in byte, della massima di input o richiesta di output che è stato rilasciato da [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nel dispositivo di backup.|  
|**last_restored_file**|**nvarchar(500)**|Nome dell'ultimo file di backup ripristinato nel database secondario.|  
|**last_restored_date**|**datetime**|Data e ora dell'ultima operazione di ripristino nel database secondario.|  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sul Log Shipping & #40; SQL Server & #41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_add_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql.md)   
 [sp_delete_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql.md)   
 [sp_help_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-database-transact-sql.md)   
 [log_shipping_secondary &#40;Transact-SQL&#41;](../../relational-databases/system-tables/log-shipping-secondary-transact-sql.md)   
 [Tabelle di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
