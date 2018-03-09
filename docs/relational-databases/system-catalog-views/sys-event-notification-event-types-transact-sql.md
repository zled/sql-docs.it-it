---
title: event_notification_event_types (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4e3db92e75198dd61db2107b0b6ebd0eda03db81
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="syseventnotificationeventtypes-transact-sql"></a>sys.event_notification_event_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce una riga per ogni evento o gruppo di eventi in corrispondenza del quale una notifica degli eventi può essere attivata.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**tipo**|**int**|Tipo di evento o gruppo di eventi che attiva una notifica degli eventi.|  
|**TYPE_NAME**|**nvarchar (128)**|Nome di un evento o gruppo di eventi. Questo valore può essere specificato nella clausola FOR di un [CREATE EVENT NOTIFICATION](../../t-sql/statements/create-event-notification-transact-sql.md) istruzione.|  
|**parent_type**|**int**|Tipo del gruppo di eventi padre dell'evento o del gruppo di eventi.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto viste del catalogo &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
