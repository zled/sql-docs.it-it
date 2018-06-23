---
title: MSSQLSERVER_10507 | Microsoft Docs
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
- 10507 (Database Engine error)
ms.assetid: cd83fa81-ac37-4eda-a3c3-17610b051de2
caps.latest.revision: 10
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: dc1510ff82b619ef4462be95b592ca89133eecdb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36158225"
---
# <a name="mssqlserver10507"></a>MSSQLSERVER_10507
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|10507|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|PG_STMT_DOES_NOT_MATCH|  
|Testo del messaggio|Impossibile creare la Guida di piano ' %. \*ls' perché l'istruzione specificata da `@stmt` e `@module_or_batch`, o dal `@plan_handle` e `@statement_start_offset`, non corrisponde ad alcuna istruzione nel modulo specificato o batch. Modificare i valori in modo da corrispondere a un'istruzione nel modulo o nel batch.|  
  
## <a name="explanation"></a>Spiegazione  
 Un'istruzione nel modulo o nel batch non corrisponde a quella specificata o al valore dell'offset dell'istruzione.  
  
## <a name="user-action"></a>Azione dell'utente  
 Modificare i valori del parametro specificato in modo da corrispondere a un'istruzione nel modulo o nel batch.  
  
## <a name="see-also"></a>Vedere anche  
 [Guide di piano](../performance/plan-guides.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
