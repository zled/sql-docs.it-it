---
title: Sys.geo_replication_links (Database SQL di Azure) | Documenti Microsoft
ms.custom: 
ms.date: 10/18/2016
ms.prod: 
ms.prod_service: sql-database
ms.reviewer: 
ms.service: sql-database
ms.component: dmv's
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- dm_geo_replication_links_TSQL
- dm_geo_replication_links
- sys.dm_geo_replication_links
- sys.dm_geo_replication_links_TSQL
helpviewer_keywords:
- sys.dm_geo_replication_links dynamic management view
- dm_geo_replication_links dynamic management view
ms.assetid: 58911798-1d60-4f28-87ab-2def2bfc3de7
caps.latest.revision: 
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5eb8f74023e90966200aca7603b82f685e0eb9db
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysgeoreplicationlinks-azure-sql-database"></a>Sys.geo_replication_links (Database SQL di Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Contiene una riga per ogni collegamento di replica tra il database primario e secondario in una relazione di replica geografica. Questa visualizzazione si trova nel database master logico.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|database_id|**int**|ID del database corrente nella vista sys. Databases.|  
|start_date|**datetimeoffset**|Ora UTC in un Database di SQL Data Center regionale di quando è stata avviata la replica di database|  
|modify_date|**datetimeoffset**|Ora UTC in Database SQL Data Center regionale di quando è stata completata la replica geografica del database. Il nuovo database è sincronizzato con il database primario al momento. tramite tabelle annidate.|  
|link_guid|**uniqueidentifier**|ID univoco del collegamento di replica geografica.|  
|partner_server|**sysname**|Nome del server logico contenente il database di replica geografica.|  
|partner_database|**sysname**|Nome del database di replica geografica nel server logico collegato.|  
|replication_state|**tinyint**|Lo stato della replica geografica per il database, uno di:.<br /><br /> 0 = in sospeso. Creazione del database secondario attivo è pianificata ma i passaggi necessari per la preparazione non sono ancora stati completati.<br /><br /> 1 = Seeding. La destinazione di replica geografica viene eseguito il seeding, ma i due database non sono ancora sincronizzati. Fino al completamento del seeding non è possibile connettersi al database secondario. Rimozione di database secondario dal server primario verrà annullata l'operazione di seeding.<br /><br /> 2 = recupero. Il database secondario è in uno stato consistente e vengono continuamente sincronizzato con il database primario.|  
|replication_state_desc|**nvarchar(256)**|PENDING<br /><br /> SEEDING<br /><br /> CATCH_UP|  
|ruolo|**tinyint**|Ruolo di replica geografica, uno di:<br /><br /> 0 = database primario. Il database_id fa riferimento al database primario della relazione di replica geografica.<br /><br /> 1 = secondario.  Il database_id fa riferimento al database primario della relazione di replica geografica.|  
|role_desc|**nvarchar(256)**|PRIMARY<br /><br /> SECONDARY|  
|secondary_allow_connections|**tinyint**|Il tipo secondario, uno di:<br /><br /> 0 = No. Il database secondario non è accessibile finché il failover.<br /><br /> 1 = sola lettura. Il database secondario è accessibile solo per le connessioni client con ApplicationIntent = ReadOnly.<br /><br /> 2 = Tutte. Il database secondario è accessibile a tutte le connessioni client.|  
|secondary_allow_connections _desc|**nvarchar(256)**|no<br /><br /> Tutto<br /><br /> Sola lettura|  
  
## <a name="permissions"></a>Autorizzazioni  
 Questa vista è disponibile solo nel **master** database all'account di accesso dell'entità a livello di server.  
  
## <a name="example"></a>Esempio  
 Mostra tutti i database con collegamenti di replica geografica.  
  
```  
SELECT   
     database_id  
   , start_date  
   , partner_server  
   , partner_database  
   , replication_state  
   , role_desc  
   , secondary_allow_connections_desc   
FROM sys.geo_replication_links;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER DATABASE (database SQL di Azure)](../../t-sql/statements/alter-database-azure-sql-database.md)   
 [Sys.dm_geo_replication_link_status &#40; Database SQL di Azure &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-geo-replication-link-status-azure-sql-database.md)   
 [Sys.dm operation_status &#40; Database SQL di Azure &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-operation-status-azure-sql-database.md)  
  
  
