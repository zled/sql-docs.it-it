---
title: Sys.server_event_session_events (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- server_event_session_events
- server_event_session_events_TSQL
- sys.server_event_session_events
- sys.server_event_session_events_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_event_session_events catalog view
- xe
ms.assetid: 75986e91-1fc7-4f14-98ac-4e90154a74db
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 62909fb21035f6cd9415dab60e4ef6b6d0fa99f9
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43030059"
---
# <a name="sysservereventsessionevents-transact-sql"></a>sys.server_event_session_events (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni evento in una sessione dell'evento.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|ID della sessione dell'evento. Non ammette i valori Null.|  
|event_id|**int**|ID dell'evento. L'ID è univoco all'interno dell'oggetto della sessione dell'evento. Non ammette i valori Null.|  
|NAME|**sysname**|Nome dell'evento. Non ammette i valori Null.|  
|pacchetto|**sysname**|Nome del pacchetto eventi che contiene l'evento. Non ammette i valori Null.|  
|modulo|**sysname**|Nome del modulo contenente l'evento. Non ammette i valori Null.|  
|predicate|**nvarchar(3000)**|Espressione del predicato applicata all'evento. Ammette i valori Null.|  
|predicate_xml|**nvarchar(3000)**|Espressione del predicato XML applicata all'evento. Ammette i valori Null.|  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione VIEW SERVER STATE per il server.  
  
## <a name="remarks"></a>Note  
 Questa vista ha le cardinalità della relazione seguenti.  
  
||||  
|-|-|-|  
|From|Per|Relazione|  
|sys.server_event_session_events.event_session_id|Sys.server_event_sessions.event_session_id|Molti-a-uno|  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Viste del catalogo degli eventi estesi &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql.md)   
 [Eventi estesi](../../relational-databases/extended-events/extended-events.md)  
  
  
