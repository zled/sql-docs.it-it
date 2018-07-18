---
title: sys.dm_pdw_node_status (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 8e263b65-81d0-49d0-8873-62ef424369d6
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 423bae3ce66e21721e328a23d51a8356be40ea2a
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38000803"
---
# <a name="sysdmpdwnodestatus-transact-sql"></a>sys.dm_pdw_node_status (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Contiene informazioni aggiuntive (tramite [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)) sulle prestazioni e lo stato di tutti i nodi di appliance. Elenca una riga per ogni nodo nell'appliance.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Id numerico univoco associato al nodo.<br /><br /> Chiave per questa visualizzazione.|Deve essere univoco nell'intera appliance, indipendentemente dal tipo.|  
|process_id|**int**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|process_name|**nvarchar(255)**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|allocated_memory|**bigint**|Memoria totale allocata in questo nodo.||  
|available_memory|**bigint**|Memoria totale disponibile in questo nodo.||  
|process_cpu_usage|**bigint**|Utilizzo CPU totale del processo, in segni di graduazione.||  
|total_cpu_usage|**bigint**|Utilizzo di CPU totale, espressa in tick.||  
|thread_count|**bigint**|Numero totale di thread in uso in questo nodo.||  
|handle_count|**bigint**|Numero totale di handle usati in questo nodo.||  
|total_elapsed_time|**bigint**|Tempo totale trascorso dal sistema avviare o riavviare.|Tempo totale trascorso dal sistema avviare o riavviare. Se total_elapsed_time supera il valore massimo per un numero intero (24,8 giorni in millisecondi), si verificherà errore materialization a causa un overflow.<br /><br /> Il valore massimo in millisecondi è equivalente a 24,8 giorni.|  
|is_available|**bit**|Flag che indica se questo nodo è disponibile.||  
|sent_time|**datetime**|Ultima volta da questo nodo è stato inviato un pacchetto di rete.||  
|received_time|**datetime**|Ultima volta da questo nodo è stato ricevuto un pacchetto di rete.||  
|error_id|**nvarchar(36)**|Identificatore univoco dell'ultimo errore che si sono verificati in questo nodo.||  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e Parallel Data Warehouse viste a gestione dinamica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
