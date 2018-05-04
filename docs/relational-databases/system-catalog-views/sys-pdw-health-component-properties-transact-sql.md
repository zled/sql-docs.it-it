---
title: sys.pdw_health_component_properties (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: pdw
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 66999c0c-dc43-4327-99fb-8366f465e69d
caps.latest.revision: 7
author: barbkess
ms.author: barbkess
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: bcdf577e71d2452f4dcee66efc46af6ba171d2a0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="syspdwhealthcomponentproperties-transact-sql"></a>sys.pdw_health_component_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Memorizza le proprietà che descrivono un dispositivo. Alcune proprietà mostrano lo stato del dispositivo e alcune proprietà descrivono il dispositivo stesso.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|property_id|**int**|Identificatore univoco della proprietà di un componente.<br /><br /> property_id e id_componente formano la chiave per la visualizzazione.|NOT NULL|  
|component_id|**int**|L'ID del componente. Vedere [sys.pdw_health_components &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> property_id e id_componente formano la chiave per la visualizzazione.|NOT NULL|  
|property_name|**nvarchar(255)**|Nome della proprietà.|NOT NULL|  
|physical_name|**nvarchar(32)**|Nome della proprietà definita dal produttore.|NOT NULL|  
|is_key|**bit**|Determina se l'istanza del dispositivo è o meno univoco.|NOT NULL<br /><br /> 0 - istanza del dispositivo è univoco.<br /><br /> 1 - istanza del dispositivo non è univoco.|  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e viste del catalogo Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
