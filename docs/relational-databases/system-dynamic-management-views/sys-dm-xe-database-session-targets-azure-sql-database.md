---
title: Sys.dm_xe_database_session_targets (Database SQL di Azure) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: 
ms.prod_service: sql-database
ms.reviewer: 
ms.service: sql-database
ms.component: dmv's
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 7f353e2a-f8fc-4366-97e4-aa1c49eadaf4
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d3da18c7d3fb07f228b06343678c81c475d34364
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmxedatabasesessiontargets-azure-sql-database"></a>Sys.dm_xe_database_session_targets (Database SQL di Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Restituisce informazioni sulle destinazioni della sessione.  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 e tutte le versioni future.|  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary(8)**|Indirizzo di memoria della sessione dell'evento. Ha una relazione molti-a-uno con sys.dm_xe_database_sessions.address. Non ammette i valori Null.|  
|target_name|**nvarchar(60)**|Nome della destinazione in una sessione. Non ammette i valori Null.|  
|target_package_guid|**uniqueidentifier**|GUID del pacchetto che contiene la destinazione. Non ammette i valori Null.|  
|execution_count|**bigint**|Numero di volte in cui la destinazione è stata eseguita per la sessione. Non ammette i valori Null.|  
|execution_duration_ms|**bigint**|Tempo totale di esecuzione della destinazione, espresso in millisecondi. Non ammette i valori Null.|  
|target_data|**nvarchar(max)**|Dati che la destinazione gestisce, ad esempio informazioni di aggregazione di evento. Ammette i valori Null.|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW DATABASE STATE.  
  
### <a name="relationship-cardinalities"></a>Cardinalità delle relazioni  
  
|From|Per|Relazione|  
|----------|--------|------------------|  
|sys.dm_xe_database_session_targets.event_session_address|sys.dm_xe_database_sessions.address|Molti-a-uno|  
  
  
