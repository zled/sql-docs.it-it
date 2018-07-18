---
title: resource_governor_resource_pools (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.resource_governor_resource_pools
- resource_governor_resource_pools
- sys.resource_governor_resource_pools_TSQL
- resource_governor_resource_pools_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_governor_resource_pools catalog view
ms.assetid: 56793e9c-aa90-452e-88c6-d9b799239888
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bb68e1efdd1261c5bc6204a96b398c55cc80cc43
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33181177"
---
# <a name="sysresourcegovernorresourcepools-transact-sql"></a>sys.resource_governor_resource_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce la configurazione memorizzata del pool di risorse in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ogni riga della vista determina la configurazione di un pool.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|pool_id|**int**|ID univoco del pool di risorse. Non ammette i valori Null.|  
|name|**sysname**|Nome del pool di risorse. Non ammette i valori Null.|  
|min_cpu_percent|**int**|Larghezza di banda media garantita della CPU per tutte le richieste nel pool di risorse, in caso di contesa di CPU. Non ammette i valori Null.|  
|max_cpu_percent|**int**|Larghezza di banda media massima della CPU concessa per tutte le richieste nel pool di risorse, in caso di contesa di CPU. Non ammette i valori Null.|  
|min_memory_percent|**int**|Quantità di memoria garantita per tutte le richieste nel pool di risorse. Non è condivisa con altri pool di risorse. Non ammette i valori Null.|  
|max_memory_percent|**int**|Percentuale di memoria totale del server utilizzabile dalle richieste in questo pool di risorse. Non ammette i valori Null. Il valore massimo effettivo dipende dai valori minimi del pool. Ad esempio, impostando max_memory_percent su 100, il valore massimo effettivo risulta inferiore.|  
|cap_cpu_percent|**int**|**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Limite di utilizzo massimo della larghezza di banda della CPU concesso per tutte le richieste nel pool di risorse. Limita il livello massimo della larghezza di banda della CPU al livello specificato. L'intervallo consentito per il valore è compreso tra 1 e 100.|  
|min_iops_per_volume|**int**|**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Operazioni di I/O minime al secondo (IOPS) per l'impostazione del volume del pool. 0 = Nessuna prenotazione. Non può essere null.|  
|max_iops_per_volume|**int**|**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Operazioni di I/O massime al secondo (IOPS) per l'impostazione del volume del pool. 0 = Numero illimitato. Non può essere null.|  
  
## <a name="remarks"></a>Osservazioni  
 La vista del catalogo visualizza i metadati memorizzati. Per visualizzare la configurazione in memoria, utilizzare la vista a gestione dinamica corrispondente [DM resource_governor_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede l'autorizzazione VIEW ANY DEFINITION per visualizzare i contenuti e l'autorizzazione CONTROL SERVER per modificarli.  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo di Resource Governor &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)   
 [sys.dm_resource_governor_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md)   
 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)   
 [sys.resource_governor_external_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md)  
  
  
