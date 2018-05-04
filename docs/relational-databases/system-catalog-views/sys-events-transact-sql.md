---
title: Sys. Events (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.events_TSQL
- sys.events
- events_TSQL
- events
dev_langs:
- TSQL
helpviewer_keywords:
- sys.events catalog view
ms.assetid: f245a97a-80fc-43fb-a6e4-139420c9a47a
caps.latest.revision: 38
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 234efbff70573bac682971aa2df65e9d5c9a1502
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysevents-transact-sql"></a>sys.events (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Contiene una riga per ogni evento per il quale si verifica l'attivazione di un trigger o di una notifica degli eventi. Questi eventi rappresentano i tipi di evento specificati quando viene creata la notifica di evento o trigger utilizzando [CREATE TRIGGER](../../t-sql/statements/create-trigger-transact-sql.md) o [CREATE EVENT NOTIFICATION](../../t-sql/statements/create-event-notification-transact-sql.md).  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID del trigger o della notifica degli eventi. Questo valore, insieme a **tipo**, in modo univoco identifica la riga.|  
|**type**|**int**|Evento che attiva il trigger.|  
|**type_desc**|**nvarchar(60)**|Descrizione dell'evento che attiva il trigger.|  
|**is_trigger_event**|**bit**|1 = evento di trigger.<br /><br /> 0 = evento di notifica.|  
|**event_group_type**|**int**|Gruppo di eventi nel quale viene creato il trigger o la notifica di evento, o null se non viene creato in un gruppo di eventi.|  
|**event_group_type_desc**|**nvarchar(60)**|Descrizione del gruppo di eventi nel quale viene creato il trigger o la notifica di evento, o null se non viene creato in un gruppo di eventi.|  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo dell'oggetto &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
