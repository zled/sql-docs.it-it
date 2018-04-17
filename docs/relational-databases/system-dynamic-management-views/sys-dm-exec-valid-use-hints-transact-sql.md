---
title: Sys.dm_exec_valid_use_hints (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 11/17/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sys.dm_exec_valid_use_hints
- sys.dm_exec_valid_use_hints_TSQL
- dm_exec_valid_use_hints
- dm_exec_valid_use_hints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_valid_use_hints management view
ms.assetid: 65d50589-39c2-4046-92b6-0c4587d8c593
caps.latest.revision: 5
author: pmasl
ms.author: pelopes
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b3df254ec44164e88cf9ec801f92898bbdeeafc7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmexecvalidusehints-transact-sql"></a>sys.dm_exec_valid_use_hints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Restituisce [HINT USE](../../t-sql/queries/hints-transact-sql-query.md) nomi hint è supportato. Elenca un nome di hint per ogni riga.  
  
Utilizzare questa DMV per visualizzare l'elenco di tutti gli hint supportati con la notazione HINT USE.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|name|**sysname**|Il nome del suggerimento.|

Vedere [hint per la Query](../../t-sql/queries/hints-transact-sql-query.md) per una descrizione di ogni suggerimento.

Introdotto in [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] SP1.
  
## <a name="see-also"></a>Vedere anche  
    
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Viste a gestione dinamica relative ai database &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  

