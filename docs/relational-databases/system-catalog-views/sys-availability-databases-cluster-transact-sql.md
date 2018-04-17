---
title: Sys. availability_databases_cluster (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.availability_databases_cluster_TSQL
- sys.availability_databases_cluster
- availability_databases_cluster_TSQL
- availability_databases_cluster
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], WSFC clusters
- sys.availability_databases_cluster catalog view
- Availability Groups [SQL Server], databases
ms.assetid: 8d9c57e5-7f39-4315-b466-92748231140a
caps.latest.revision: 14
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c781a3e8d09596096244e95855aa7ce0c71074e7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sysavailabilitydatabasescluster-transact-sql"></a>sys.availability_databases_cluster (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni database di disponibilità nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che ospita una replica di disponibilità per qualsiasi gruppo di disponibilità AlwaysOn nel cluster Windows Server Failover Clustering (WSFC), indipendentemente dal fatto che la copia locale del database è stato aggiunto al gruppo di disponibilità ancora.  
  
> [!NOTE]  
>  Quando un database viene aggiunto a un gruppo di disponibilità, viene automaticamente creato un join del database primario con il gruppo. È necessario preparare i database secondari su ogni replica secondaria prima di poterne creare un join al gruppo di disponibilità.   
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**group_id**|**uniqueidentifier**|Identificatore univoco del gruppo di disponibilità a cui partecipa il database.<br /><br /> NULL = il database non fa parte di una replica di disponibilità di un gruppo di disponibilità.|  
|**group_database_id**|**uniqueidentifier**|Identificatore univoco del database nel gruppo di disponibilità a cui partecipa il database. **group_database_id** è lo stesso per il database nella replica primaria e in ogni replica secondaria in cui il database è stato aggiunto al gruppo di disponibilità.<br /><br /> NULL = il database non fa parte di una replica di disponibilità in alcun gruppo di disponibilità.|  
|**database_name**|**sysname**|Nome del database aggiunto al gruppo di disponibilità.|  
  
## <a name="permissions"></a>Autorizzazioni  
 Se il chiamante di **Sys. availability_databases_cluster** non è il proprietario del database, le autorizzazioni minime necessarie per visualizzare la riga corrispondente sono ALTER ANY DATABASE o autorizzazione a livello di server VIEW ANY DATABASE o CREATE Autorizzazione DATABASE per il **master** database.  
  
## <a name="see-also"></a>Vedere anche  
 [sys.availability_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.dm_hadr_database_replica_states &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md)   
 [sys.dm_hadr_database_replica_cluster_states &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql.md)   
 [Panoramica di Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  
