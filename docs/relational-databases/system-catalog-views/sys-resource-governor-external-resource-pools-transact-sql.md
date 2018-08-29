---
title: Sys. resource_governor_external_resource_pools (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/13/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.resource_governor_external_resource_pools
- sys.resource_governor_external_resource_pools_TSQL
- resource_governor_external_resource_pools
- resource_governor_external_resource_pools_TSQL
helpviewer_keywords:
- sys.resource_governor_external_resource_pools
- resource_governor_external_resource_pools
ms.assetid: 75063e36-a91b-496f-9936-88f3d57bd447
caps.latest.revision: 10
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2a6d224b1a8f5f419a43a92357e250cdc655165b
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43018417"
---
# <a name="sysresourcegovernorexternalresourcepools-transact-sql"></a>Sys. resource_governor_external_resource_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]
**Si applica a:**  [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] e [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

Restituisce la configurazione del pool di risorse esterne stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ogni riga della vista determina la configurazione di un pool.
  
|Nome colonna|Tipo di dati|Description|
|-----------------|---------------|-----------------|
|pool_id|**int**|ID univoco del pool di risorse. Non ammette i valori Null.<br /><br /> **Nota:** venga rinominato in futuro.|
|NAME|**sysname**|Nome del pool di risorse. Non ammette i valori Null.|
|max_cpu_percent|**int**|Larghezza di banda media massima della CPU concessa per tutte le richieste nel pool di risorse, in caso di contesa di CPU. Non ammette i valori Null.|
|max_memory_percent|**int**|Percentuale di memoria totale del server utilizzabile dalle richieste in questo pool di risorse. Non ammette i valori Null. Il valore massimo effettivo dipende dai valori minimi del pool. Ad esempio, impostando max_memory_percent su 100, il valore massimo effettivo risulta inferiore.|
|max_processes|**int**|Numero massimo di processi esterni simultanei. Il valore predefinito, 0, non specifica alcun limite. Non ammette i valori Null.|
|version|**bigint**|Numero di versione interno.|
  
## <a name="permissions"></a>Permissions

È richiesta l'autorizzazione VIEW SERVER STATE.

## <a name="see-also"></a>Vedere anche

[Governance delle risorse per Machine Learning in SQL Server](../../advanced-analytics/r/resource-governance-for-r-services.md)

[Viste del catalogo di Resource Governor &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)

[sys.dm_resource_governor_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md)

[Resource Governor](../../relational-databases/resource-governor/resource-governor.md)

[sys.dm_resource_governor_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md)

[Opzione di configurazione del server external scripts enabled](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)

[ALTER EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)
