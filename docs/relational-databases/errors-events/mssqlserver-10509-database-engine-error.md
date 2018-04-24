---
title: MSSQLSERVER_10509 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 10509 (Database Engine error)
ms.assetid: e9dd5357-ee3d-420a-9a89-d12ab5404e73
caps.latest.revision: 9
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d3aa303297c00b122cb44a6dc4db75942a082164
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver10509"></a>MSSQLSERVER_10509
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|10509|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|PG_INVALID_STMT|  
|Testo del messaggio|Impossibile creare la guida di piano '%.\*ls' perché l'istruzione specificata da **@stmt** o **@statement_start_offset** contiene un errore di sintassi o non può essere usata in una guida di piano. Specificare una singola istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] valida o una posizione di inizio valida dell'istruzione nel batch. Per ottenere una posizione di inizio valida, eseguire una query sulla colonna statement_start_offset nella funzione a gestione dinamica sys.dm_exec_query_stats.|  
  
## <a name="explanation"></a>Spiegazione  
L'istruzione specificata da **@stmt** o **@statement_start_offset** contiene un errore di sintassi o non può essere usata in una guida di piano.  
  
## <a name="user-action"></a>Azione dell'utente  
Specificare una singola istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] valida o una posizione di inizio valida dell'istruzione nel batch. Per ottenere una posizione di inizio valida, eseguire una query sulla colonna statement_start_offset nella funzione a gestione dinamica sys.dm_exec_query_stats.  
  
## <a name="see-also"></a>Vedere anche  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[Guide di piano](~/relational-databases/performance/plan-guides.md)  
[sys.dm_exec_query_stats &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
