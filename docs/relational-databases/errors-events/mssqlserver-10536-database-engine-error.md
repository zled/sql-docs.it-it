---
title: MSSQLSERVER_10536 | Microsoft Docs
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
- 10536 (Database Engine error)
ms.assetid: 9f97b41f-0ef8-4ad2-aec0-906a5d7522ba
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b00f374672490cf9823a3c7700d4ae0e53e18c3f
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver10536"></a>MSSQLSERVER_10536
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|10536|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|PG_TOO_MANY_STMTS|  
|Testo del messaggio|Impossibile creare la guida di piano '%.\*ls' perché il batch o il modulo corrispondente al valore **@plan_handle** specificato contiene più di 1000 istruzioni idonee. Creare una guida di piano per ogni istruzione nel batch o nel modulo specificando un valore **statement_start_offset** per ogni istruzione.|  
  
## <a name="explanation"></a>Spiegazione  
Il batch o il modulo corrispondente al valore **@plan_handle** specificato contiene più di 1000 istruzioni idonee.  
  
## <a name="user-action"></a>Azione dell'utente  
Creare una guida di piano per ogni istruzione nel batch o nel modulo specificando un valore **statement_start_offset** per ogni istruzione.  
  
## <a name="see-also"></a>Vedere anche  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[Guide di piano](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  

