---
title: Sys.dm_xe_database_session_object_columns (Database SQL di Azure) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: dmv's
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 0e6adc54-4d97-4ef0-bf4f-b4538d69f136
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 8745fd9dd6182170adf57db56c8a2fbd1c9414c4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmxedatabasesessionobjectcolumns-azure-sql-database"></a>Sys.dm_xe_database_session_object_columns (Database SQL di Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Mostra i valori di configurazione per gli oggetti associati a una sessione.  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 e tutte le versioni successive.|  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary(8)**|Indirizzo di memoria della sessione dell'evento. Ha una relazione molti-a-uno con sys.dm_xe_database_sessions.address. Non ammette i valori Null.|  
|column_name|**nvarchar(60)**|Nome del valore di configurazione. Non ammette i valori Null.|  
|column_id|**int**|ID della colonna. Valore univoco all'interno dell'oggetto. Non ammette i valori Null.|  
|column_value|**nvarchar(2048)**|Valore configurato della colonna. Ammette i valori Null.|  
|object_type|**nvarchar(60)**|Tipo dell'oggetto.  Non è nullable.object_type è uno di:<br /><br /> evento<br /><br /> target|  
|object_name|**nvarchar(60)**|Nome dell'oggetto a cui appartiene la colonna. Non ammette i valori Null.|  
|object_package_guid|**uniqueidentifier**|GUID del pacchetto che contiene l'oggetto. Non ammette i valori Null.|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW DATABASE STATE.  
  
### <a name="relationship-cardinalities"></a>Cardinalità delle relazioni  
  
|From|Per|Relazione|  
|----------|--------|------------------|  
|dm_xe_database_session_object_columns.object_name<br /><br /> dm_xe_database_session_object_columns.object_package_guid|sys.dm_xe_objects.package_guid<br /><br /> sys.dm_xe_objects.name|Molti-a-uno|  
|dm_xe_database_session_object_columns.column_name<br /><br /> dm_xe_database_session_object_columns.column_id|sys.dm_xe_object_columns.name<br /><br /> sys.dm_xe_object_columns.column_id|Molti-a-uno|  
  
## <a name="see-also"></a>Vedere anche  
 [Eventi estesi](../../relational-databases/extended-events/extended-events.md)  
  
  
