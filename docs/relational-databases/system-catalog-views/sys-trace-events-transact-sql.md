---
title: trace_events (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- trace_events_TSQL
- trace_events
- sys.trace_events
- sys.trace_events_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.trace_events catalog view
ms.assetid: e7d2c5df-0e17-4e94-9d41-d36c7ee60662
caps.latest.revision: "24"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dde83548228baaaa8e33fe30485e62476ed6c42a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="systraceevents-transact-sql"></a>sys.trace_events (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **trace_events** vista del catalogo contiene un elenco di tutti gli eventi di traccia SQL. Questi eventi di traccia non variano in una versione specifica di [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
> **IMPORTANTE** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] In alternativa, utilizzare le viste del catalogo di Eventi estesi.  
  
 Per ulteriori informazioni su questi eventi di traccia, vedere [SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md).  
  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**trace_event_id**|**smallint**|ID univoco dell'evento. Questa colonna è disponibile anche nella **Sys. trace_event_bindings** e **Sys. trace_subclass_values** viste del catalogo.|  
|**category_id**|**smallint**|ID della categoria dell'evento. Questa colonna è disponibile anche nella **trace_categories** vista del catalogo.|  
|**name**|**nvarchar (128)**|Nome univoco dell'evento. Questo parametro non è localizzato.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto viste del catalogo &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [TRACES &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-traces-transact-sql.md)   
 [trace_categories &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-trace-categories-transact-sql.md)   
 [trace_columns &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-trace-columns-transact-sql.md)   
 [Sys. trace_event_bindings &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-trace-event-bindings-transact-sql.md)   
 [Sys. trace_subclass_values &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-trace-subclass-values-transact-sql.md)  
  
  
