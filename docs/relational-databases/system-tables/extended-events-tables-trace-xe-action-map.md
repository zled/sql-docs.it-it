---
title: contenute (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- trace_xe_action_map_TSQL
- trace_xe_action_map
dev_langs:
- TSQL
helpviewer_keywords:
- extended events [SQL Server], tables
- trace_xe_action_map
ms.assetid: 208a1413-ce7f-4521-b765-d74723627302
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 29fba0bc16dc42798ecd37d234dd79e30e9db856
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256755"
---
# <a name="extended-events-tables---tracexeactionmap"></a>Estendere le tabelle degli eventi - contenute
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni azione degli eventi estesi di cui è stato eseguito il mapping a un ID della colonna di Traccia SQL. Questa tabella è archiviata nel database master, nello schema sys.  
  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|trace_column_id|**smallint**|ID della colonna di Traccia SQL di cui viene eseguito il mapping.|  
|package_name|**nvarchar(60)**|Nome del pacchetto degli eventi estesi in cui si trova l'azione di cui è stato eseguito il mapping.|  
|xe_action_name|**nvarchar(60)**|Nome dell'azione degli eventi estesi di cui è stato eseguito il mapping alla colonna di Traccia SQL.|  
  
## <a name="remarks"></a>Osservazioni  
 È possibile utilizzare la query seguente per identificare le azioni degli eventi estesi equivalenti alle colonne di Traccia SQL:  
  
```  
SELECT tc.name AS trace_column, am.package_name, am.xe_action_name  
FROM sys.trace_columns AS tc  
INNER JOIN sys.trace_xe_action_map AS am  
   ON tc.trace_column_id = am.trace_column_id  
```  
  
 Le colonne di Traccia SQL di cui non è stato eseguito il mapping alle azioni non sono incluse nella tabella.  
  
## <a name="see-also"></a>Vedere anche  
 [trace_xe_event_map &#40;Transact-SQL&#41;](../../relational-databases/system-tables/extended-events-tables-trace-xe-event-map.md)  
  
  
