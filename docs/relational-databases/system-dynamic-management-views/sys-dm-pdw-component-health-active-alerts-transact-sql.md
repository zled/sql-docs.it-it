---
title: sys.dm_pdw_component_health_active_alerts (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: pdw
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c53e4a36-b841-424a-b8e2-255b1878deb6
caps.latest.revision: 8
author: barbkess
ms.author: barbkess
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 2376f7a068335fbf37585f552fd697cc3294f103
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmpdwcomponenthealthactivealerts-transact-sql"></a>sys.dm_pdw_component_health_active_alerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Archivia gli avvisi attivi su [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] componenti.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Identificatore univoco di un [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] nodo.<br /><br /> pdw_node_id id_componente, component_instance_id, alert_id e alert_instance_id formano la chiave per la visualizzazione.|NOT NULL|  
|component_id|**int**|L'ID del componente. Vedere [sys.pdw_health_components &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> pdw_node_id id_componente, component_instance_id, alert_id e alert_instance_id formano la chiave per la visualizzazione.|NOT NULL|  
|component_instance_id|**nvarchar(255)**|pdw_node_id id_componente, component_instance_id, alert_id e alert_instance_id formano la chiave per la visualizzazione.|NOT NULL|  
|alert_id|**int**|L'ID per il tipo di avviso. Vedere [sys.pdw_health_alerts &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md).<br /><br /> pdw_node_id id_componente, component_instance_id, alert_id e alert_instance_id formano la chiave per la visualizzazione.|NOT NULL|  
|alert_instance_id|**nvarchar(36)**|Identifica un'istanza di un determinato avviso.<br /><br /> pdw_node_id id_componente, component_instance_id, alert_id e alert_instance_id formano la chiave per la visualizzazione.|NOT NULL|  
|current_value|**nvarchar(255)**|Utilizzato quando l'avviso è di tipo StatusChange. Questo è lo stato corrente dei componenti. Valore è NULL per gli avvisi di tipo soglia. Vedere [sys.pdw_health_alerts &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md) per un elenco dei tipi di avviso.|NULL|  
|previous_value|**nvarchar(255)**|Utilizzato quando l'avviso è di tipo StatusChange. Si tratta dello stato componente precedente. Valore è NULL per gli avvisi di tipo soglia. Vedere [sys.pdw_health_alerts &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md) per un elenco dei tipi di avviso.|NULL|  
|create_time|**datetime**|Quando è stato generato l'avviso di data e ora.|NOT NULL|  
  
 Per informazioni sulle righe massimi mantenuto da questa vista, vedere "Minimo e massimo valori" nel [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e Parallel Data Warehouse, viste a gestione dinamica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
