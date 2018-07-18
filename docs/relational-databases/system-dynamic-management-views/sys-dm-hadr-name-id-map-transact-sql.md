---
title: sys.dm_hadr_name_id_map (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_hadr_name_id_map
- sys.dm_hadr_name_id_map_TSQL
- dm_hadr_name_id_map
- dm_hadr_name_id_map_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.dm_hadr_name_id_map dynamic management view
ms.assetid: e07bb8a9-37de-4a39-a257-950d7c3ae8fb
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e775dd8e9b82b8a19ae71889ecd3fbca2df3a1b2
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2018
ms.locfileid: "34467607"
---
# <a name="sysdmhadrnameidmap-transact-sql"></a>sys.dm_hadr_name_id_map (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Mostra il mapping dei gruppi di disponibilità Always On che l'istanza corrente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è stato aggiunto a tre ID univoci: un disponibilità ID gruppo, un ID risorsa WSFC e un ID gruppo WSFC. Lo scopo di questo mapping è gestire lo scenario in cui il gruppo/risorsa WSFC viene rinominato.  
   
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**ag_name**|**nvarchar(256)**|Nome del gruppo di disponibilità. Nome specificato dall'utente che deve essere univoco all'interno del cluster WSFC (Windows Server Failover Cluster).|  
|**ag_id**|**uniqueidentifier**|Identificatore univoco (GUID) del gruppo di disponibilità.|  
|**ag_resource_id**|**nvarchar(256)**|ID univoco del gruppo di disponibilità come una risorsa nel cluster WSFC.|  
|**ag_group_id**|**nvarchar(256)**|ID gruppo WSFC univoco del gruppo di disponibilità.|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW SERVER STATE per il server.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e DMV di Gruppi di disponibilità AlwaysOn &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)   
 [Viste del catalogo dei gruppi di disponibilità AlwaysOn &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [Monitorare gruppi di disponibilità & #40; Transact-SQL & #41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [Gruppi di disponibilità AlwaysOn di &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
