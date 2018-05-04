---
title: sys.dm_pdw_wait_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.component: dmv's
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: cfb8d905-c34f-44de-9574-dde81e170916
caps.latest.revision: 7
author: barbkess
ms.author: barbkess
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: c254643b6f035b5a9c463b9ee852f3b24e89fda3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmpdwwaitstats-transact-sql"></a>sys.dm_pdw_wait_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contiene informazioni riguardanti il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stato del sistema operativo è correlata a istanze in esecuzione in nodi diversi. Per un elenco di tipi di attesa e la relativa descrizione, vedere [Sys.dm os_wait_stats](http://msdn.microsoft.com/en-us/library/ms179984\(v=sql.120\).aspx).  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|**pdw_node_id**|**int**|ID del nodo di a che questa voce fa riferimento.||  
|**wait_name**|**nvarchar(255)**|Nome del tipo di attesa.||  
|**max_wait_time**|**bigint**|Tempo di attesa massimo di questo tipo di attesa.||  
|**request_count**|**bigint**|Numero di attese di questo tipo in attesa di attesa.||  
|**signal_time**|**bigint**|Differenza tra il momento in cui è stato rilevato il thread in attesa e quello in cui è stata avviata l'esecuzione del thread.||  
|**completed_count**|**bigint**|Numero totale di attesa di questo tipo completata dopo l'ultimo server di riavvio.||  
|**tempo_attesa**|**bigint**|Tempo di attesa totale per questo tipo di attesa in millisecons. Comprende signal_time.||  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e Parallel Data Warehouse, viste a gestione dinamica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)   
 [sys.dm_pdw_waits &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md)  
  
  
