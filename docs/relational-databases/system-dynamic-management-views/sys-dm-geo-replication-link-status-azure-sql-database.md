---
title: Sys.dm_geo_replication_link_status (Database SQL di Azure) | Documenti Microsoft
ms.custom: ''
ms.date: 10/13/2016
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: dmv's
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- dm_geo_replication_link_status
- dm_geo_replication_link_status_TSQL
- sys.dm_geo_replication_link_status
- sys.dm_geo_replication_link_status_TSQL
helpviewer_keywords:
- dm_geo_replication_link_status dynamic management view
- sys.dm_geo_replication_link_status dynamic management view
ms.assetid: d763d679-470a-4c21-86ab-dfe98d37e9fd
caps.latest.revision: 15
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 5eb252c42cb8c455c4dff4f5c65e638edb140158
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmgeoreplicationlinkstatus-azure-sql-database"></a>Sys.dm_geo_replication_link_status (Database SQL di Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Contiene una riga per ogni collegamento di replica tra il database primario e secondario in una relazione di replica geografica. Sono inclusi i database primari e secondari. Se è presente più di un collegamento di replica continua per un determinato database primario, questa tabella contiene una riga per ognuna delle relazioni. La vista viene creata in tutti i database, inclusi i database master logico. Tuttavia, se si esegue una query su questa vista nel database master logico viene restituito un set vuoto.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|link_guid|**uniqueidentifier**|ID univoco del collegamento di replica.|  
|partner_server|**sysname**|Nome del server logico contenente il database collegato.|  
|partner_database|**sysname**|Nome del database collegato nel server logico collegato.|  
|last_replication|**datetimeoffset**|Il timestamp di riconoscimento dell'ultima transazione dal database secondario in base al clock di database primario. Questo valore è disponibile nel database primario.|  
|replication_lag_sec|**int**|Differenza di tempo in secondi tra il valore last_replication e il timestamp del commit della transazione sul database primario in base al clock di database primario.  Questo valore è disponibile nel database primario.|  
|replication_state|**tinyint**|Lo stato della replica geografica per il database, uno di:.<br /><br /> 1 = Seeding. La destinazione di replica geografica viene eseguito il seeding, ma i due database non sono ancora sincronizzati. Fino al completamento del seeding non è possibile connettersi al database secondario. Rimozione di database secondario dal server primario verrà annullata l'operazione di seeding.<br /><br /> 2 = recupero. Il database secondario è in uno stato consistente e vengono continuamente sincronizzato con il database primario.<br /><br /> 4 = sospeso. Non è presente una relazione di copia continua attiva. Questo stato indica in genere che la larghezza di banda disponibile per l'interlink è insufficiente per il livello di attività di transazione nel database primario. La relazione di copia continua tuttavia rimane invariata.|  
|replication_state_desc|**nvarchar(256)**|PENDING<br /><br /> SEEDING<br /><br /> CATCH_UP|  
|ruolo|**tinyint**|Ruolo di replica geografica, uno di:<br /><br /> 0 = database primario. Il database_id fa riferimento al database primario della relazione di replica geografica.<br /><br /> 1 = secondario.  Il database_id fa riferimento al database primario della relazione di replica geografica.|  
|role_desc|**nvarchar(256)**|PRIMARY<br /><br /> SECONDARY|  
|secondary_allow_connections|**tinyint**|Il tipo secondario, uno di:<br /><br /> 0 non = Nessun direct sono consentite connessioni al database secondario e il database non è disponibile per l'accesso in lettura.<br /><br /> 2 = tutte le connessioni sono consentite al database nella replica secondaria; ication per l'accesso in sola lettura.|  
|secondary_allow_connections_desc|**nvarchar(256)**|no<br /><br /> Tutto|  
|last_commit|**datetimeoffset**|Ora dell'ultima transazione di commit nel database. Se recuperata nel database primario, indica l'ultima ora di commit nel database primario. Se recuperata nel database secondario, indica l'ultima ora di commit nel database secondario. Se quando il database primario del collegamento di replica è attivo, recuperare nel database secondario, indica fino a quando il punto il database secondario viene aggiornato rispetto.|
  
> [!NOTE]  
>  Se la relazione di replica viene terminata rimuovendo il database secondario (sezione 4.2), la riga per il database nel **sys.dm_geo_replication_link_status** visualizzazione scomparirà.  
  
## <a name="permissions"></a>Autorizzazioni  
 Eseguire una query qualsiasi account con autorizzazione view_database_state **sys.dm_geo_replication_link_status**.  
  
## <a name="example"></a>Esempio  
 Mostra i ritardi di replica e l'ora dell'ultima replica di database secondari.  
  
```  
SELECT   
     link_guid  
   , partner_server  
   , last_replication  
   , replication_lag_sec   
FROM sys.dm_geo_replication_link_status;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER DATABASE &#40;Database SQL di Azure&#41;](../../t-sql/statements/alter-database-azure-sql-database.md)   
 [Sys.geo_replication_links &#40;Database SQL di Azure&#41;](../../relational-databases/system-dynamic-management-views/sys-geo-replication-links-azure-sql-database.md)   
 [DM operation_status &#40;Database SQL di Azure&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-operation-status-azure-sql-database.md)  
  
  
