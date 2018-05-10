---
title: Sys.dm continuous_copy_status (Database SQL di Azure) | Documenti Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: dmv's
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_continuous_copy_status_TSQL
- dm_continuous_copy_status_TSQL
- dm_continuous_copy_status
- sys.dm_continuous_copy_status
dev_langs:
- TSQL
helpviewer_keywords:
- dm_continuous_copy_status
- sys.dm_continuous_copy_status
ms.assetid: 411b2e71-4421-4ef5-900d-5af068750899
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 03a54b1ebebaaca66628fd7ad9817d90787c45be
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmcontinuouscopystatus-azure-sql-database"></a>Sys.dm continuous_copy_status (Database SQL di Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Restituisce una riga per ogni database utente (V11) che è attualmente occupato in una relazione di copia continua della replica geografica. Se è stata avviata più di una relazione di copia continua per un determinato database primario, questa tabella contiene una riga per ogni database secondario attivo.  
  
Se si utilizza SQL Database V12 è necessario utilizzare [sys.dm_geo_replication_link_status](../../relational-databases/system-dynamic-management-views/sys-dm-geo-replication-link-status-azure-sql-database.md) (perché *Sys.dm continuous_copy_status* si applica solo ai V11).

  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**copy_guid**|**uniqueidentifier**|ID univoco del database di replica.|  
|**partner_server**|**sysname**|Nome del server di database SQL collegato.|  
|**partner_database**|**sysname**|Nome del database collegato nel server di database SQL collegato.|  
|**last_replication**|**datetimeoffset**|Timestamp dell'ultima transazione replicata applicata.|  
|**replication_lag_sec**|**int**|Differenza di tempo in secondi tra l'ora corrente e il timestamp dell'ultimo commit della transazione completato nel database primario che non è stato riconosciuto dal database secondario attivo.|  
|**replication_state**|**tinyint**|Lo stato della replica di copia continua per questo database. Di seguito sono i valori possibili e le relative descrizioni.<br /><br /> 1: seeding. La destinazione della replica viene sottoposta a seeding ed è dal punto di vista transazionale in uno stato non coerente. Finché il seeding non viene completato, non è possibile connettersi al database secondario attivo. <br />2: recuperando. Il database secondario attivo attualmente esegue l'aggiornamento al database primario e si trova in uno stato coerente dal punto di vista transazionale.<br />3: nuovo seeding. Il database secondario attivo automaticamente viene sottoposto nuovamente a seeding a causa di un errore di replica irreversibile.<br />4: sospesa. Non è presente una relazione di copia continua attiva. Questo stato indica in genere che la larghezza di banda disponibile per l'interlink è insufficiente per il livello di attività di transazione nel database primario. La relazione di copia continua tuttavia rimane invariata.|  
|**replication_state_desc**|**nvarchar(256)**|Descrizione di replication_state. I valori possibili sono:<br /><br /> SEEDING<br /><br /> CATCH_UP<br /><br /> RE_SEEDING<br /><br /> SUSPENDED|  
|**is_rpo_limit_reached**|**bit**|Questo valore è sempre impostato su 0|  
|**is_target_role**|**bit**|0 = Origine della relazione di copia<br /><br /> 1 = Destinazione della relazione di copia|  
|**is_interlink_connected**|**bit**|1 = L'interlink è connesso.<br /><br /> 0 = L'interlink è disconnesso.|  
  
## <a name="permissions"></a>Autorizzazioni  
 Per recuperare i dati, è richiesta l'appartenenza di **db_owner** ruolo del database. L'utente dbo, i membri del **dbmanager** ruolo del database e l'account di accesso sa possono effettuare query anche questa visualizzazione.  
  
## <a name="remarks"></a>Osservazioni  
 Il **Sys.dm continuous_copy_status** vista viene creata nel **risorse** database ed è visibile in tutti i database, inclusi i database master logico. Tuttavia, se si esegue una query su questa vista nel database master logico viene restituito un set vuoto.  
  
 Se la relazione di copia continua viene terminata in un database, la riga per il database nel **Sys.dm continuous_copy_status** visualizzazione scomparirà.  
  
 Ad esempio il **Sys.dm database_copies** visualizzazione **Sys.dm continuous_copy_status** riflette lo stato della relazione di copia continua in cui il database è entrambi un database primario o attivo secondario . A differenza di **Sys.dm database_copies**, **Sys.dm continuous_copy_status** contiene più colonne che forniscono i dettagli sulle operazioni e le prestazioni. Queste colonne sono **last_replication**, e **replication_lag_sec**...  
  
## <a name="see-also"></a>Vedere anche  
 [DM database_copies &#40;Database SQL di Azure&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-database-copies-azure-sql-database.md)   
 [Stored procedure di replica geografica attiva &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/81658ee4-4422-4d73-bf7a-86a07422cb0d)  
  
  
