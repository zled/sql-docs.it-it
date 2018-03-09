---
title: MSSQLSERVER_10507 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 10507 (Database Engine error)
ms.assetid: cd83fa81-ac37-4eda-a3c3-17610b051de2
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3bad7ac89e53fb1de9c814cc64618f966e328b66
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver10507"></a>MSSQLSERVER_10507
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|10507|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|PG_STMT_DOES_NOT_MATCH|  
|Testo del messaggio|Impossibile creare la guida di piano '%.\*ls' perché l'istruzione specificata da **@stmt** e **@module_or_batch** o da **@plan_handle** e **@statement_start_offset** non corrisponde ad alcuna istruzione nel modulo o nel batch specificato. Modificare i valori in modo da corrispondere a un'istruzione nel modulo o nel batch.|  
  
## <a name="explanation"></a>Spiegazione  
Un'istruzione nel modulo o nel batch non corrisponde a quella specificata o al valore dell'offset dell'istruzione.  
  
## <a name="user-action"></a>Azione dell'utente  
Modificare i valori del parametro specificato in modo da corrispondere a un'istruzione nel modulo o nel batch.  
  
## <a name="see-also"></a>Vedere anche  
[Guide di piano](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
