---
title: syscollector_execution_stats (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- syscollector_execution_stats
- syscollector_execution_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syscollector_execution_stats view
- data collector view
ms.assetid: 23e35ac5-fbbf-4922-970c-f4fac44c1263
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1e04c57081f19358786dcc723f6ef2f79757fae2
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="syscollectorexecutionstats-transact-sql"></a>syscollector_execution_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fornisce informazioni sull'esecuzione delle attività per un set di raccolta o un pacchetto.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**log_id**|**bigint**|Identifica ogni esecuzione del set di raccolta. Utilizzato per unire questa vista agli altri log dettagliati. Non ammette i valori Null.|  
|**task_name**|**nvarchar(128)**|Nome dell'attività del pacchetto o del set di raccolta a cui sono destinate queste informazioni. Non ammette i valori Null.|  
|**execution_row_count_in**|**int**|Il numero di righe elaborate all'inizio del flusso di dati. Ammette i valori Null.|  
|**execution_row_count_out**|**int**|Il numero di righe elaborate alla fine del flusso di dati. Ammette i valori Null.|  
|**execution_row_count_errors**|**int**|Numero di righe in cui si è verificato un errore durante il flusso di dati. Ammette i valori Null.|  
|**execution_time_ms**|**int**|Intervallo di tempo, in millisecondi, da attendere per il completamento dell'attività. Ammette i valori Null.|  
|**log_time**|**datetime**|L'ora di registrazione di queste informazioni. Non ammette i valori Null.|  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede l'autorizzazione SELECT per **dc_operator**.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure dell'agente di raccolta dati &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Viste dell'agente di raccolta dati &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [Raccolta dati](../../relational-databases/data-collection/data-collection.md)  
  
  
