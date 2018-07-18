---
title: sys.dm_exec_compute_node_status (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DM_EXEC_COMPUTE_NODE_STATUS_TSQL
- DM_EXEC_COMPUTE_NODE_STATUS
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- dm_exec_compute_node_status
- sys.dm_exec_compute_node_status management view
ms.assetid: b606f91f-3a08-4a4f-bb57-32ae155b3738
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 79f0c7a7596f04f768a0ec4398ec90800bbbd08e
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38051499"
---
# <a name="sysdmexeccomputenodestatus-transact-sql"></a>sys.dm_exec_compute_node_status (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Contiene informazioni aggiuntive sulle prestazioni e lo stato di tutti i nodi PolyBase. Elenca una riga per ogni nodo.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|compute_node_id|**int**|Id numerico univoco associato al nodo.|Deve essere univoco nel cluster di scalabilità orizzontale, indipendentemente dal tipo.|  
|process_id|**int**|||  
|process_name|**nvarchar(255)**|Nome logico del nodo.|Qualsiasi stringa di lunghezza appropriato.|  
|allocated_memory|**bigint**|Memoria totale allocata in questo nodo.||  
|available_memory|**bigint**|Memoria totale disponibile in questo nodo.||  
|process_cpu_usage|**bigint**|Utilizzo CPU totale del processo, in segni di graduazione.||  
|total_cpu_usage|**bigint**|Utilizzo di CPU totale, espressa in tick.||  
|thread_count|**bigint**|Numero totale di thread in uso in questo nodo.||  
|handle_count|**bigint**|Numero totale di handle usati in questo nodo.||  
|total_elapsed_time|**bigint**|Tempo totale trascorso dal sistema avviare o riavviare.|Tempo totale trascorso dal sistema avviare o riavviare. Se total_elapsed_time supera il valore massimo per un numero intero (24,8 giorni in millisecondi), si verificherà errore materialization a causa un overflow. Il valore massimo in millisecondi è equivalente a 24,8 giorni.|  
|is_available|**bit**|Flag che indica se questo nodo è disponibile.||  
|sent_time|**datetime**|Ultima volta da questo oggetto è stato inviato un pacchetto di rete||  
|received_time|**datetime**|Ultima volta da questo nodo è stato inviato un pacchetto di rete.||  
|error_id|**nvarchar(36)**|Identificatore univoco dell'ultimo errore che si sono verificati in questo nodo.||  
  
## <a name="see-also"></a>Vedere anche  
 [PolyBase con DMV di risoluzione dei problemi](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Viste a gestione dinamica relative ai database &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
