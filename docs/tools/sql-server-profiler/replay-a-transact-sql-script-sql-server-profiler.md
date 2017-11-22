---
title: Riprodurre uno Script Transact-SQL (SQL Server Profiler) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- traces [SQL Server], replaying
- scripts [SQL Server], traces
- replaying traces
ms.assetid: 9c0eb222-e6e3-4bc1-a25f-a41e962d361b
caps.latest.revision: "24"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3cf5e12702ea3e46caec693673303315d12e8fcc
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="replay-a-transact-sql-script-sql-server-profiler"></a>Riprodurre uno script Transact-SQL (SQL Server Profiler)
  Quando si desidera provare possibili soluzioni a un problema di prestazioni, è possibile utilizzare [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] per riprodurre script [!INCLUDE[tsql](../../includes/tsql-md.md)] e confrontare così le prestazioni prima e dopo aver effettuato le modifiche.  
  
### <a name="to-replay-a-transact-sql-script"></a>Per riprodurre uno script Transact-SQL  
  
1.  Scegliere **Apri** dal menu **File**e quindi **File script**.  
  
2.  Selezionare il file script [!INCLUDE[tsql](../../includes/tsql-md.md)] che si desidera aprire. Verificare che lo script [!INCLUDE[tsql](../../includes/tsql-md.md)] contenga gli eventi necessari per la riproduzione. Per altre informazioni, vedere [Requisiti per la riproduzione](../../tools/sql-server-profiler/replay-requirements.md).  
  
3.  Scegliere **Avvia** dal menu **Riproduci**e connettersi al server in cui si vuole riprodurre lo script.  
  
4.  Nella finestra di dialogo **Configurazione riproduzione** verificare le impostazioni e quindi fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Riprodurre le tracce](../../tools/sql-server-profiler/replay-traces.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
