---
title: Eliminare una traccia (Transact-SQL) | Microsoft Docs
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
- traces [SQL Server], deleting
- removing traces
- deleting traces
ms.assetid: a5502814-b281-42dd-b885-5c9368025ae6
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b808de9ad1f60aae9380ae20487aa3187e8d6218
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36068454"
---
# <a name="delete-a-trace-transact-sql"></a>Eliminare una traccia (Transact-SQL)
  In questo argomento viene illustrata la procedura di utilizzo di stored procedure per eliminare una traccia.  
  
 Per un esempio dell'uso di stored procedure relative alla traccia, vedere [Creare una traccia &#40;Transact-SQL&#41;](create-a-trace-transact-sql.md).  
  
### <a name="to-delete-a-trace"></a>Per eliminare una traccia  
  
1.  Eseguire **sp_trace_setstatus** specificando **@status = 0** per arrestare la traccia.  
  
2.  Eseguire **sp_trace_setstatus** specificando **@status = 2** per chiudere la traccia ed eliminare le relative informazioni dal server.  
  
> [!NOTE]  
>  È necessario che la traccia venga arrestata prima di chiuderla.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_trace_setstatus &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql)   
 [Stored procedure di SQL Server Profiler &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)  
  
  
