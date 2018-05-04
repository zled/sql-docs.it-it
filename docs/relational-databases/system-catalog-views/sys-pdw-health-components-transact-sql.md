---
title: sys.pdw_health_components (Transact-SQL) | Microsoft Docs
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
ms.assetid: d5c7589b-09b0-4f12-ab84-feb3ec3fbaaa
caps.latest.revision: 6
author: barbkess
ms.author: barbkess
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: cd7f63e8e65967a4ad161ba06bf2d7d36a333dbc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="syspdwhealthcomponents-transact-sql"></a>sys.pdw_health_components (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Contiene informazioni su tutti i componenti e i dispositivi che esistono nel sistema. Questi includono hardware, dispositivi di archiviazione e i dispositivi di rete.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|component_id|**int**|Identificatore univoco di un componente o un dispositivo.<br /><br /> Chiave per la visualizzazione.|NOT NULL|  
|group_id|**Int**|Il gruppo di componenti logica a cui appartiene questo componente. Vedere [sys.pdw_health_components (Parallel Data Warehouse)](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).|NOT NULL|  
|component_name|**nvarchar(255)**|Nome del componente.|NOT NULL|  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e viste del catalogo Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
