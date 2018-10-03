---
title: Sys.trigger_event_types (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- trigger_event_types_TSQL
- sys.trigger_event_types_TSQL
- sys.trigger_event_types
- trigger_event_types
dev_langs:
- TSQL
helpviewer_keywords:
- sys.trigger_event_types catalog view
ms.assetid: 054aed54-7151-4760-934a-149fa434f1ae
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f97837a7e6bdc9b84f15512cf20a3791e5cf433c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47705469"
---
# <a name="systriggereventtypes-transact-sql"></a>sys.trigger_event_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni evento o gruppo di eventi in corrispondenza del quale un trigger può essere attivato.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**type**|**int**|Tipo di evento o gruppo di eventi che attiva il trigger.|  
|**type_name**|**nvarchar(64)**|Nome di un evento o gruppo di eventi. Questo valore può essere specificato nella clausola FOR di un' [CREATE TRIGGER](../../t-sql/statements/create-trigger-transact-sql.md) istruzione.|  
|**parent_type**|**int**|Tipo del gruppo di eventi padre dell'evento o del gruppo di eventi.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo dell'oggetto &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
