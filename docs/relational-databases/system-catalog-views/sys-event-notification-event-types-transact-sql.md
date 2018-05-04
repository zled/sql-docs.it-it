---
title: event_notification_event_types (Transact-SQL) | Documenti Microsoft
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
- sys.event_notification_event_types_TSQL
- sys.event_notification_event_types
- event_notification_event_types_TSQL
- event_notification_event_types
dev_langs:
- TSQL
helpviewer_keywords:
- sys.event_notification_event_types catalog view
ms.assetid: 73dae456-7044-4b00-b0bd-990ef810b356
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 48021783863019ed68c59a1610129592f38db37e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="syseventnotificationeventtypes-transact-sql"></a>sys.event_notification_event_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce una riga per ogni evento o gruppo di eventi in corrispondenza del quale una notifica degli eventi può essere attivata.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**type**|**int**|Tipo di evento o gruppo di eventi che attiva una notifica degli eventi.|  
|**type_name**|**nvarchar(128)**|Nome di un evento o gruppo di eventi. Questo valore può essere specificato nella clausola FOR di un [CREATE EVENT NOTIFICATION](../../t-sql/statements/create-event-notification-transact-sql.md) istruzione.|  
|**parent_type**|**int**|Tipo del gruppo di eventi padre dell'evento o del gruppo di eventi.|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo dell'oggetto &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
