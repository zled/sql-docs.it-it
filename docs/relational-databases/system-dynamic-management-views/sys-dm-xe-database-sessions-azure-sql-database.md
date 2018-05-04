---
title: Sys.dm xe_database_sessions (Database SQL di Azure) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
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
ms.assetid: 33ea5179-16bb-4abd-96cc-9bc696e80987
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: cfe1957ede96e473759267f47753f3efce3a6796
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmxedatabasesessions-azure-sql-database"></a>Sys.dm xe_database_sessions (Database SQL di Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Restituisce informazioni sugli eventi di sessione. Gli eventi sono punti di esecuzione discreti. I predicati possono essere applicati agli eventi per arrestarne la generazione se l'evento non contiene le informazioni necessarie.  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 e tutte le versioni successive.|  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary(8)**|Indirizzo di memoria della sessione dell'evento. Non ammette i valori Null.|  
|event_name|**nvarchar(60)**|Nome dell'evento associato all'azione. Non ammette i valori Null.|  
|event_package_guid|**uniqueidentifier**|GUID per il pacchetto che contiene l'evento. Non ammette i valori Null.|  
|event_predicate|**nvarchar(2048)**|Rappresentazione XML dell'albero predicativo applicato all'evento. Ammette i valori Null.|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW DATABASE STATE.  
  
### <a name="relationship-cardinalities"></a>Cardinalità delle relazioni  
A partire da 2015-07-13, xe_objects' fa parte di queste DMV XEvent che non contengono nel nome "database". Non è un errore di digitazione o un errore nella colonna a destra della tabella seguente. Il nome è lo stesso in Microsoft SQL Server e Database SQL di Azure. GeneMi.  
  
|From|Per|Relazione|  
|--------|------|----------------|  
|sys.dm_xe_database_session_events.event_session_address|sys.dm_xe_database_sessions.address|Molti-a-uno|  
|Sys.dm_xe_database_session_events.event_package_guid, sys.dm_xe_database_session_events.event_name|sys.dm_xe_objects.name, sys.dm_xe_objects.package_guid|Molti-a-uno|  
  
## <a name="see-also"></a>Vedere anche  
[Eventi estesi nel Database SQL di Azure](http://azure.microsoft.com/documentation/articles/sql-database-xevent-db-diff-from-svr/)  
[Eventi estesi](../../relational-databases/extended-events/extended-events.md)  
  
 
