---
title: dbo.slo_database_objectives (Database SQL di Azure) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: 
ms.reviewer: 
ms.suite: sql
ms.prod_service: sql-database
ms.service: sql-database
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.slo_database_objectives
- dbo.slo_database_objectives_TSQL
- slo_database_objectives_TSQL
- slo_database_objectives
dev_langs: TSQL
helpviewer_keywords:
- slo_database_objectives
- dbo.slo_database_objectives
ms.assetid: a522569d-8cfc-4643-a170-1cd291e61eee
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6210e47a8178cf8f6f0f5a3aa50a6541010eb492
ms.sourcegitcommit: b603dcac7326bba387befe68544619e026e6a15e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="dboslodatabaseobjectives-azure-sql-database"></a>dbo.slo_database_objectives (Database SQL di Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

    
> [!IMPORTANT]  
>  **Si applica solo alle [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]V11.**  
>   
>  Per [! INCLUDERE[ssSDSfull](../system-dynamic-management-views/sys-dm-operation-status-azure-sql-database.md) (sul master) per l'operazione ALTER DATABASE.   
  
 Restituisce lo stato di assegnazione di un obiettivo del livello di servizio (SLO) in un database SQL.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|database_name|**sysname**|Nome del database.|  
|current_slo|**sysname**|SLO corrente del database.|  
|target_slo|**sysname**|SLO di destinazione del database come specificato nella richiesta di modifica SLO.|  
|state_desc|**nvarchar**|Stato della richiesta di modifica SLO: completato o in sospeso.|  
  
## <a name="permissions"></a>Autorizzazioni  
 Questa vista è disponibile per tutti i ruoli utente con autorizzazioni per connettersi al virtuale **master** database.  
  
## <a name="examples"></a>Esempi  
  
```  
SELECT   
database_name=database_name.name   
    , current_slo=current_slo.name   
    , target_slo=target_slo.name   
    , state_desc=database_slo.state_desc   
FROM slo_database_objectives AS database_slo  
INNER JOIN slo_service_objectives AS current_slo ON database_slo.current_objective_id = current_slo.objective_id  
INNER JOIN slo_service_objectives AS target_slo ON database_slo.configured_objective_id = target_slo.objective_id  
INNER JOIN sys.databases AS database_name  ON database_slo.database_id = database_name.database_id;  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione di database Premium](http://go.microsoft.com/fwlink/?LinkID=311927)  
[sys.dm_operation_status (database di SQL Azure)](../system-dynamic-management-views/sys-dm-operation-status-azure-sql-database.md) 
