---
title: Sys.dm database_copies (Database SQL di Azure) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
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
- dm_database_copies_TSQL
- sys.dm_database_copies
- dm_database_copies
- sys.dm_database_copies_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dm_database_copies
- sys.dm_database_copies
ms.assetid: d03d4657-86d1-4496-97e6-cc3bc292e0b1
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: af4c4327b5b3448014566dbf75a02c666247f85a
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmdatabasecopies-azure-sql-database"></a>sys.dm_database_copies (Database di SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Restituisce informazioni sulla copia del database.  
  
Per restituire informazioni sui collegamenti di replica geografica, utilizzare il [sys.geo_replication_links](../../relational-databases/system-dynamic-management-views/sys-geo-replication-links-azure-sql-database.md) o [sys.dm_geo_replication_link_status](../../relational-databases/system-dynamic-management-views/sys-dm-geo-replication-link-status-azure-sql-database.md) viste (disponibile nel Database SQL V12).
  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|ID del database corrente nella vista `sys.databases`.|  
|**start_date**|**datetimeoffset**|Ora UTC in un data center del [!INCLUDE[ssSDS](../../includes/sssds-md.md)] regionale in cui è stata avviata la copia del database.|  
|**modify_date**|**datetimeoffset**|Ora UTC in un data center del [!INCLUDE[ssSDS](../../includes/sssds-md.md)] regionale in cui è stata completata la copia del database. Al momento, il nuovo database è transazionalmente coerente con il database primario. Le informazioni sul completamento viene aggiornati ogni minuto.<br /><br />Ora UTC che riflette l'ultimo aggiornamento del campo percent_complete.|  
|**percent_complete**|**real**|Percentuale di byte copiati. I valori validi sono compresi tra 0 e 100. Il [!INCLUDE[ssSDS](../../includes/sssds-md.md)] potrebbe recuperare automaticamente da alcuni errori, ad esempio il failover, e riavviare la copia del database. In questo caso, percent_complete inizierebbe di nuovo da 0.|  
|**error_code**|**int**|Se maggiore di 0, il codice che indica l'errore che si è verificato durante copia. Il valore è uguale a 0 se non si sono verificati errori.|  
|**error_desc**|**nvarchar(4096)**|Descrizione dell'errore che si è verificato durante la copia.|  
|**error_severity**|**int**|Restituisce 16 se la copia del database ha esito negativo.|  
|**error_state**|**int**|Restituisce 1 se la copia ha esito negativo.|  
|**copy_guid**|**uniqueidentifier**|ID univoco dell'operazione di copia.|  
|**partner_server**|**sysname**|Nome del Database SQL server in cui viene creata la copia.|  
|**partner_database**|**sysname**|Nome della copia del database nel server partner.|  
|**replication_state**|**tinyint**|Lo stato della replica di copia continua per questo database. I valori possibili sono:<br /><br /> 0 = in sospeso. Creazione della copia del database è stata pianificata ma i passaggi necessari per la preparazione non sono ancora stati completati o sono temporaneamente bloccati dalla quota di seeding.<br /><br /> 1 = Seeding. Il copia database in fase di seeding non è ancora completamente sincronizzato con il database di origine. In questo stato non è possibile connettersi alla copia. Per annullare l'operazione di seeding in corso, è necessario eliminare il database della copia.|  
|**replication_state_desc**|**nvarchar(256)**|Descrizione di replication_state. I valori possibili sono:<br /><br /> PENDING<br /><br /> SEEDING<br />|  
|**maximum_lag**|**int**|Campo riservato.|  
|**is_continuous_copy**|**bit**|0 = restituisce 0|  
|**is_target_role**|**bit**|0 = database di origine<br /><br /> 1 = copia del database|  
|**is_interlink_connected**|bit|Campo riservato.|  
|**is_offline_secondary**|bit|Campo riservato.|  
  
## <a name="permissions"></a>Autorizzazioni  
 Questa vista è disponibile solo nel **master** database all'account di accesso dell'entità a livello di server.  
  
## <a name="remarks"></a>Osservazioni  
 È possibile utilizzare il **Sys.dm database_copies** visualizzare il **master** database di origine o destinazione [!INCLUDE[ssSDS](../../includes/sssds-md.md)] server. Quando la copia del database viene completata correttamente e il nuovo database diventa ONLINE, la riga di **Sys.dm database_copies** vista viene rimossa automaticamente.  
  
  
