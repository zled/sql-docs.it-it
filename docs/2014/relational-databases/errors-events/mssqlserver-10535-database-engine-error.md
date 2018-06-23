---
title: MSSQLSERVER_10535 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 10535 (Database Engine error)
ms.assetid: 478fd978-11d9-4155-8329-f599fdbec14b
caps.latest.revision: 9
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: ff4797fdd9d206ca459bc84facccfc588aafba00
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36166400"
---
# <a name="mssqlserver10535"></a>MSSQLSERVER_10535
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|10535|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|PG_NO_PLAN|  
|Testo del messaggio|Impossibile cerare la guida di piano '%.*ls' perché non è stato trovato alcun piano nella cache dei piani corrispondente all'handle di piani specificato. Specificare un handle di piani memorizzati nella cache. Per un elenco degli handle di piani memorizzati nella cache, eseguire una query sulla vista a gestione dinamica sys.dm_exec_query_stats.|  
  
## <a name="explanation"></a>Spiegazione  
 Non è stato trovato alcun piano nella cache dei piani corrispondente all'handle di piani specificato.  
  
## <a name="user-action"></a>Azione dell'utente  
 Specificare un handle di piani memorizzati nella cache. Per un elenco degli handle di piani memorizzati nella cache, eseguire una query sulla vista a gestione dinamica sys.dm_exec_query_stats.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)   
 [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql)  
  
  
