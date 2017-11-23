---
title: Sys.dm_pdw_component_health_alerts (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88f05392-1e97-4693-ba60-a4910af3c000
caps.latest.revision: "7"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2f8a0a4af0fafa03492217a72626c17e394c3afc
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmpdwcomponenthealthalerts-transact-sql"></a>Sys.dm_pdw_component_health_alerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Archivi emesso in precedenza gli avvisi sui componenti dello strumento.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Identificatore univoco di un [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] nodo.<br /><br /> pdw_node_id id_componente, component_instance_id, alert_id e alert_instance_id formano la chiave per la visualizzazione.|NOT NULL|  
|id_componente|**int**|L'ID del componente. Vedere [sys.pdw_health_components &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> pdw_node_id id_componente, component_instance_id, alert_id e alert_instance_id formano la chiave per la visualizzazione.|NOT NULL|  
|component_instance_id|**nvarchar(255)**|pdw_node_id id_componente, component_instance_id, alert_id e alert_instance_id formano la chiave per la visualizzazione.|NOT NULL|  
|alert_id|**int**|L'ID per il tipo di avviso. Vedere [sys.pdw_health_alerts &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md).<br /><br /> pdw_node_id id_componente, component_instance_id, alert_id e alert_instance_id formano la chiave per la visualizzazione.|NOT NULL|  
|alert_instance_id|**nvarchar(36)**|Identifica un'istanza di un determinato avviso.<br /><br /> pdw_node_id id_componente, component_instance_id, alert_id e alert_instance_id formano la chiave per la visualizzazione.|NOT NULL|  
|previous_value|**nvarchar(255)**|Utilizzato quando l'avviso è di tipo StatusChange. Si tratta dello stato componente precedente. Valore è NULL per gli avvisi di tipo soglia. Vedere [sys.pdw_health_alerts &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md) per un elenco dei tipi di avviso.|NULL|  
|current_value|**nvarchar(255)**|Utilizzato quando l'avviso è di tipo StatusChange. Questo è lo stato corrente dei componenti. Valore è NULL per gli avvisi di tipo soglia. Vedere [sys.pdw_health_alerts &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md) per un elenco dei tipi di avviso.|NULL|  
|create_time|**datetime**|Quando è stato generato l'avviso di data e ora.|NOT NULL|  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e viste a gestione dinamica Parallel Data Warehouse &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
