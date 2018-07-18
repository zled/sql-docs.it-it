---
title: sys.pdw_health_component_status_mappings (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4272cfad-5ad7-493d-9edd-d9111619bda0
caps.latest.revision: 7
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 4b2d572b79c15c369e33190c183c249de3b8fb0c
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38000863"
---
# <a name="syspdwhealthcomponentstatusmappings-transact-sql"></a>sys.pdw_health_component_status_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Definisce il mapping tra il [!INCLUDE[ssDW](../../includes/ssdw-md.md)] stato dei componenti e i nomi definiti produttore del componente.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|property_id|**int**|Identificatore univoco della proprietà.<br /><br /> property_id e id_componente physical_name formano la chiave per questa visualizzazione.|NOT NULL|  
|component_id|**int**|L'ID del componente. Visualizzare [sys.pdw_health_components &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> property_id e id_componente physical_name formano la chiave per questa visualizzazione.|NOT NULL|  
|physical_name|**nvarchar(32)**|Nome della proprietà definita dal produttore.<br /><br /> property_id e id_componente physical_name formano la chiave per questa visualizzazione.|NOT NULL|  
|logical_name|**nvarchar(255)**|Nome della proprietà come definito da [!INCLUDE[ssDW](../../includes/ssdw-md.md)].|NOT NULL<br /><br /> 0 - istanza del dispositivo è univoco.<br /><br /> 1 - istanza dispositivo non è univoco.|  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e Parallel Data Warehouse viste del catalogo](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
