---
title: sys.dm_exec_compute_nodes (Transact-SQL) | Microsoft Docs
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
- DM_EXEC_COMPUTE_NODES_TSQL
- DM_EXEC_COMPUTE_NODES
- SYS.DM_EXEC_COMPUTE_NODES_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_compute_nodes management view
- PolyBase, views
- PolyBase management views
- dm_exec_compute_nodes management view
ms.assetid: 0de4b7a4-401f-4e2d-9ab0-c54587e05154
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 2e0c2b19e9d790e25f78b88160b96a5f0d4d9eb8
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38061559"
---
# <a name="sysdmexeccomputenodes-transact-sql"></a>sys.dm_exec_compute_nodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Contiene informazioni sui nodi usati con la gestione dei dati di PolyBase. Elenca una riga per ogni nodo.  
  
 Utilizzare questa DMV per visualizzare l'elenco di tutti i nodi del cluster di tipo scale-out con il ruolo, nome e indirizzo IP.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|compute_node_id|**int**|Id numerico univoco associato al nodo. Chiave per questa visualizzazione.|Deve essere univoco nel cluster di scalabilità orizzontale, indipendentemente dal tipo.|  
|Tipo|**nvarchar(32)**|Tipo del nodo.|'COMPUTE', 'HEAD'|  
|NAME|**nvarchar(32)**|Nome logico del nodo.|Qualsiasi stringa di lunghezza appropriato.|  
|address|**nvarchar(32)**|Indirizzo IP del nodo.|Intervallo di indirizzi IP|  
  
## <a name="see-also"></a>Vedere anche  
 [PolyBase con DMV di risoluzione dei problemi](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Viste a gestione dinamica relative ai database &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
