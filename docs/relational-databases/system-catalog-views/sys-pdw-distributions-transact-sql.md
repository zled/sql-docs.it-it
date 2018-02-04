---
title: sys.pdw_distributions (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 572b5187-9753-4063-adf8-65dea87d11f8
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 07694ebc741c769e97991e81de40fe73023106a0
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="syspdwdistributions-transact-sql"></a>sys.pdw_distributions (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contiene informazioni riguardanti le distribuzioni nel dispositivo. Contiene una riga per ogni distribuzione dello strumento.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|distribution_id|**int**|Id numerico univoco associata alla distribuzione.<br /><br /> Chiave per la visualizzazione.|1 al numero di nodi di calcolo di appliance moltiplicato per il numero di distribuzioni per ogni nodo di calcolo.|  
|pdw_node_id|**int**|ID del nodo in questa distribuzione.|Vedere pdw_node_id in [sys.dm_pdw_nodes &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|name|**nvarchar(32)**|Stringa associata alla distribuzione, utilizzata come un suffisso nelle tabelle distribuite identificatore.|Stringa di risultato di "A-Z", 'a-z','0-9', '_','-'.|  
|position|**int**|Posizione della distribuzione all'interno di un nodo rispetto al altre distribuzioni su tale nodo.|1 al numero di distribuzioni per ogni nodo.|  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e viste del catalogo Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
