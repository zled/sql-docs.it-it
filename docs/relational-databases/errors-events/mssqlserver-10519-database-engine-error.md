---
title: MSSQLSERVER_10519 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 10519 (Database Engine error)
ms.assetid: 3be393a1-b186-41ae-afb9-a3d07ff354bb
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: db940e5befce39f3e8fa41775e66ceacca858a7d
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver10519"></a>MSSQLSERVER_10519
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|10519|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|PG_INCOMPATIBLE_STMT_AND_HINTS|  
|Testo del messaggio|Impossibile creare la guida di piano '%.\*ls' perché gli hint specificati in **@hints** non possono essere applicati all'istruzione specificata da **@stmt** o **@statement_start_offset**. Verificare che gli hint possano essere applicati all'istruzione.|  
  
## <a name="explanation"></a>Spiegazione  
Gli hint specificati in **@hints** non possono essere applicati all'istruzione specificata da **@stmt** o **@statement_start_offset**.  
  
## <a name="user-action"></a>Azione dell'utente  
Specificare hint che possono essere applicati all'istruzione.  
  
## <a name="see-also"></a>Vedere anche  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[Guide di piano](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  

