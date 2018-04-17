---
title: Sys. server_events (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- server_events_TSQL
- sys.server_events_TSQL
- server_events
- sys.server_events
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_events catalog view
ms.assetid: 996f6c9b-6426-4847-95d9-6b77541422be
caps.latest.revision: 32
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 88ffe9532b566261b789db56b707303fb26303cb
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sysserverevents-transact-sql"></a>sys.server_events (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni evento per cui viene attivato un trigger DDL a livello di server o viene generata una notifica di evento a livello di server. Le colonne **object_id** e **tipo** identificare in modo univoco l'evento del server.  

  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID del trigger DDL a livello di server o della notifica di evento a livello di server da generare.|  
|**type**|**int**|Tipo di evento che causa la generazione della notifica di evento o l'attivazione del trigger DDL.|  
|**type_desc**|**nvarchar(60)**|Descrizione dell'evento che causa l'attivazione del trigger DDL o la generazione della notifica di evento.|  
|**event_group_type**|**int**|Gruppo di eventi nel quale viene creato il trigger o la notifica di evento, o null se non viene creato in un gruppo di eventi.|  
|**event_group_type_desc**|**nvarchar(60)**|Descrizione del gruppo di eventi nel quale viene creato il trigger o la notifica di evento, o null se non viene creato in un gruppo di eventi|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo dell'oggetto &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
