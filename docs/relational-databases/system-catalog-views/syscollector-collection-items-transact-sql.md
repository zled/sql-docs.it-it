---
title: syscollector_collection_items (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- syscollector_collection_items_TSQL
- syscollector_collection_items
dev_langs:
- TSQL
helpviewer_keywords:
- syscollector_collection_items view
- add data collector view
ms.assetid: a279ecd1-a59c-4315-9f08-bf221f00a465
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9e1113453ebe83221fb8dd8b9de92113bcb346c3
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33220572"
---
# <a name="syscollectorcollectionitems-transact-sql"></a>syscollector_collection_items (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni su un elemento di un set di raccolta.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**collection_set_id**|**int**|Identifica il set di raccolta. Non ammette i valori Null.|  
|**collection_item_id**|**int**|Identifica un elemento del set di raccolta. Non ammette i valori Null.|  
|**collector_type_uid**|**uniqueidentifier**|GUID utilizzato per identificare il tipo agente di raccolta dati. Non ammette i valori Null.|  
|**name**|**nvarchar(4000)**|Nome del set di raccolta. Ammette i valori Null.|  
|**Frequenza**|**int**|La frequenza con cui i dati sono raccolti da un elemento della raccolta. Non ammette i valori Null.|  
|**parameters**|**xml**|Descrive la parametrizzazione per il tipo di agente di raccolta associato all'elemento della raccolta. Lo schema XML per questo elemento della raccolta viene convalidato con il XML Schema (XSD) archiviato nel **parameter_schema** per un tipo di agente di raccolta specifico. Ammette i valori Null. Per altre informazioni, vedere [syscollector_collector_types &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-collector-types-transact-sql.md).|  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede SELECT per **dc_operator**, **dc_proxy**.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure dell'agente di raccolta dati &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Viste dell'agente di raccolta dati &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [Raccolta dati](../../relational-databases/data-collection/data-collection.md)  
  
  
