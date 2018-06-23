---
title: MSSQLSERVER_10519 | Microsoft Docs
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
- 10519 (Database Engine error)
ms.assetid: 3be393a1-b186-41ae-afb9-a3d07ff354bb
caps.latest.revision: 10
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: fa8bb26aeb39ca6b46f29063664a15ec43a86cc1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069165"
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
|Testo del messaggio|Impossibile creare la Guida di piano ' %. \*ls' perché gli hint specificati nel `@hints` non può essere applicato all'istruzione specificata da uno degli identificatori `@stmt` o `@statement_start_offset`. Verificare che gli hint possano essere applicati all'istruzione.|  
  
## <a name="explanation"></a>Spiegazione  
 Gli hint specificati in `@hints` non possono essere applicati all'istruzione specificata da `@stmt` o `@statement_start_offset`.  
  
## <a name="user-action"></a>Azione dell'utente  
 Specificare hint che possono essere applicati all'istruzione.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Guide di piano](../performance/plan-guides.md)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
