---
title: sys.dm_pdw_diag_processing_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: df659c55-4f63-45f8-8afe-ce300031bc5b
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f1e2180e6d22cee81c94d880eca1debaa20c8c5d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47837189"
---
# <a name="sysdmpdwdiagprocessingstats-transact-sql"></a>sys.dm_pdw_diag_processing_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Visualizza informazioni relative a tutti gli eventi di diagnostica interni che potrebbe essere incorporati nelle sessioni di diagnostica definite dall'amministratore. Eseguire una query in questa vista per comprendere le statistiche dietro la diagnostica e i sottosistemi di gestione degli eventi del popolamento di tutte le altre DMV tale unità. Sono disponibili un gruppo di code per ogni processo in ogni nodo.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**pdw_node_id**|**int**|Nodo di Appliance che proviene questo log.|  
|**process_id**|**int**|Identificatore del processo in esecuzione inviando la statistica.|  
|**target_name**|**nvarchar(255)**|Nome della coda.|  
|**queue_size**|**int**|Il numero di elementi nella coda dei processi. Le dimensioni della coda è in genere 0. Un numero positivo indica che il sistema è in condizioni di stress e sta realizzando backlog degli eventi. Un numero positivo nelle altre colonne significa system sono danneggiati per quel particolare coda e le relative viste a gestione dinamica.|  
|**lost_events_count**|**bigint**|Il numero di eventi perdita.|  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e Parallel Data Warehouse viste a gestione dinamica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
