---
title: MSSQLSERVER_10536 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 10536 (Database Engine error)
ms.assetid: 9f97b41f-0ef8-4ad2-aec0-906a5d7522ba
caps.latest.revision: 10
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: ffa9509c55632c5f041f060c499be0a8bc7cbf4b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055922"
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
|Testo del messaggio|Impossibile creare la Guida di piano ' %. \*ls' perché il batch o il modulo corrispondente all'oggetto specificato `@plan_handle` contiene più di 1000 istruzioni idonee. Creare una guida di piano per ciascuna istruzione nel batch o nel modulo specificando un valore `statement_start_offset` per ciascuna istruzione.|  
  
## <a name="explanation"></a>Spiegazione  
 Il batch o il modulo corrispondente al valore `@plan_handle` contiene più di 1000 istruzioni idonee.  
  
## <a name="user-action"></a>Azione dell'utente  
 Creare una guida di piano per ciascuna istruzione nel batch o nel modulo specificando un valore `statement_start_offset` per ciascuna istruzione.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Guide di piano](../performance/plan-guides.md)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
