---
title: sys.dm_pdw_nodes (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 93966909-d758-4d50-950b-f5066d104fa6
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: e609a3e5d6963a5e643df86a61588586984baf20
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmpdwnodes-transact-sql"></a>sys.dm_pdw_nodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contiene informazioni su tutti i nodi in [!INCLUDE[ssAPS](../../includes/ssaps-md.md)]. Contiene una riga per ogni nodo nel dispositivo.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Id numerico univoco associato al nodo.<br /><br /> Chiave per la visualizzazione.|Univoche tra il dispositivo, indipendentemente dal tipo.|  
|Tipo|**nvarchar(32)**|Tipo di nodo.|'COMPUTE', 'CONTROL', 'GESTIONE'|  
|name|**nvarchar(32)**|Nome logico del nodo.|Qualsiasi stringa di lunghezza appropriata.|  
|address|**nvarchar(32)**|Indirizzo IP del nodo.|Nel formato [0-255]. [0-255]. [0-255]. [0-255].|  
|is_passive|**int**|Indica se la macchina virtuale in esecuzione il nodo è in esecuzione sul server assegnato o ha eseguito il failover al server di riserva.|0 – macchina virtuale del nodo è in esecuzione nel server originale.<br /><br /> 1-macchina virtuale del nodo è in esecuzione nel server di riserva.|  
|regione|**nvarchar(32)**|L'area in cui il nodo è in esecuzione.|'PDW', 'HDINSIGHT'|  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e Parallel Data Warehouse, viste a gestione dinamica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
