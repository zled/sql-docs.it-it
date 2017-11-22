---
title: TRACES (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- traces
- sys.traces_TSQL
- sys.traces
- traces_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.traces catalog view
ms.assetid: 4a03be22-b7da-4e2a-97ff-94bed890a620
caps.latest.revision: "23"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6e195b27208480e28b6ac18b0b40d36e7c543312
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="systraces-transact-sql"></a>sys.traces (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **TRACES** vista del catalogo contiene le tracce correnti in esecuzione nel sistema. Questa vista è da intendersi come una sostituzione per il **fn_trace_getinfo** (funzione).  
  
 Per un elenco completo degli eventi di traccia supportati, vedere [SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md).  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] In alternativa, utilizzare le viste del catalogo di Eventi estesi.  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**id**|**int**|ID della traccia.|  
|**status**|**int**|Stato della traccia:<br /><br /> 0 = arrestato<br /><br /> 1 = in esecuzione|  
|**percorso**|**nvarchar (260)**|Percorso del file di traccia. Il valore è Null quando la traccia è una traccia di un set di righe.|  
|**max_size**|**bigint**|Dimensioni massime in megabyte (MB) per il file di traccia. Il valore è Null quando la traccia è una traccia di un set di righe.|  
|**stop_time**|**datetime**|Ora di arresto dell'esecuzione della traccia.|  
|**max_files**|**int**|Numero massimo di file di rollover. Il valore è Null se il numero massimo non è impostato.|  
|**is_rowset**|**bit**|1 = traccia di un set di righe.|  
|**is_rollover**|**bit**|1 = l'opzione di rollover è abilitata.|  
|**is_shutdown**|**bit**|1 = l'opzione di chiusura è abilitata.|  
|**is_default**|**bit**|1 = traccia predefinita.|  
|**buffer_count**|**int**|Numero di buffer in memoria utilizzati dalla traccia.|  
|**buffer_size**|**int**|Dimensioni di ogni buffer (KB).|  
|**file_position**|**bigint**|Ultimo percorso del file di traccia. Il valore è Null quando la traccia è una traccia di un set di righe.|  
|**reader_spid**|**int**|ID sessione del lettore di traccia del set di righe. Il valore è Null quando la traccia è una traccia di un file.|  
|**start_time**|**datetime**|Ora di inizio della traccia.|  
|**last_event_time**|**datetime**|Ora di generazione dell'ultimo evento.|  
|**event_count**|**bigint**|Numero totale di eventi generati.|  
|**dropped_event_count**|**int**|Numero totale di eventi eliminati.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto viste del catalogo &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [trace_categories &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-trace-categories-transact-sql.md)   
 [trace_columns &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-trace-columns-transact-sql.md)   
 [trace_events &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-trace-events-transact-sql.md)   
 [Sys. trace_event_bindings &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-trace-event-bindings-transact-sql.md)   
 [Sys. trace_subclass_values &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-trace-subclass-values-transact-sql.md)  
  
  
