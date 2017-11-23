---
title: Sys.pdw_health_component_properties (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66999c0c-dc43-4327-99fb-8366f465e69d
caps.latest.revision: "7"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 66fb48b26de19aca26c9edb41af4cb31b8f0f01b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="syspdwhealthcomponentproperties-transact-sql"></a>Sys.pdw_health_component_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Memorizza le proprietà che descrivono un dispositivo. Alcune proprietà mostrano lo stato del dispositivo e alcune proprietà descrivono il dispositivo stesso.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|property_id|**int**|Identificatore univoco della proprietà di un componente.<br /><br /> property_id e id_componente formano la chiave per la visualizzazione.|NOT NULL|  
|id_componente|**int**|L'ID del componente. Vedere [sys.pdw_health_components &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> property_id e id_componente formano la chiave per la visualizzazione.|NOT NULL|  
|property_name|**nvarchar(255)**|Nome della proprietà.|NOT NULL|  
|physical_name|**nvarchar(32)**|Nome della proprietà definita dal produttore.|NOT NULL|  
|is_key|**bit**|Determina se l'istanza del dispositivo è o meno univoco.|NOT NULL<br /><br /> 0 - istanza del dispositivo è univoco.<br /><br /> 1 - istanza del dispositivo non è univoco.|  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e viste del catalogo Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
