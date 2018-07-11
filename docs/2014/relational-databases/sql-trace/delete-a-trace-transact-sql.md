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
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], deleting
- removing traces
- deleting traces
ms.assetid: a5502814-b281-42dd-b885-5c9368025ae6
caps.latest.revision: 21
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e255ab5d72c8d7d0cfd935ba971b7f1c409ee38a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37158002"
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
  
  
