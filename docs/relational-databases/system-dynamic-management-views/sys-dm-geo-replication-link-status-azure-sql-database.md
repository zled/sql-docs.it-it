---
title: Sys.dm_geo_replication_link_status (Database SQL di Azure) | Documenti Microsoft
ms.custom: 
ms.date: 10/13/2016
ms.prod: 
ms.prod_service: sql-database
ms.reviewer: 
ms.service: sql-database
ms.component: dmv's
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- dm_geo_replication_link_status
- dm_geo_replication_link_status_TSQL
- sys.dm_geo_replication_link_status
- sys.dm_geo_replication_link_status_TSQL
helpviewer_keywords:
- dm_geo_replication_link_status dynamic management view
- sys.dm_geo_replication_link_status dynamic management view
ms.assetid: d763d679-470a-4c21-86ab-dfe98d37e9fd
caps.latest.revision: "15"
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0399e0ef7587a7a7cb8a7ef32419518f1b95d53e
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
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
|secondary_allow_connections_desc|**nvarchar(256)**|No<br /><br /> Tutto|  
|last_commit|**datetimeoffset**|Ora dell'ultima transazione di commit nel database. Se quando il database primario del collegamento di replica è attivo, recuperare nel database secondario, indica fino a quando il punto il database secondario viene aggiornato rispetto.|
  
> [!NOTE]  
>  Se la relazione di replica viene terminata rimuovendo il database secondario (sezione 4.2), la riga per il database nel **sys.dm_geo_replication_link_status** visualizzazione scomparirà.  
  
## <a name="permissions"></a>Permissions  
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
 [ALTER DATABASE &#40; Database SQL di Azure &#41;](../../t-sql/statements/alter-database-azure-sql-database.md)   
 [Sys.geo_replication_links &#40; Database SQL di Azure &#41;](../../relational-databases/system-dynamic-management-views/sys-geo-replication-links-azure-sql-database.md)   
 [Sys.dm operation_status &#40; Database SQL di Azure &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-operation-status-azure-sql-database.md)  
  
  
