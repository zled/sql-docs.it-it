---
title: Riprodurre uno script Transact-SQL (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: sql-server-profiler
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- traces [SQL Server], replaying
- scripts [SQL Server], traces
- replaying traces
ms.assetid: 9c0eb222-e6e3-4bc1-a25f-a41e962d361b
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b21ed5c4b270a64c6eee3cc2d41cb4f1ba0518df
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="replay-a-transact-sql-script-sql-server-profiler"></a>Riprodurre uno script Transact-SQL (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Quando si provano soluzioni possibili per un problema di prestazioni, usare [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] per riprodurre script [!INCLUDE[tsql](../../includes/tsql-md.md)] e confrontare le prestazioni prima e dopo aver effettuato le modifiche.  
  
### <a name="to-replay-a-transact-sql-script"></a>Per riprodurre uno script Transact-SQL  
  
1.  Scegliere **Apri** dal menu **File**e quindi **File script**.  
  
2.  Selezionare il file script [!INCLUDE[tsql](../../includes/tsql-md.md)] che si desidera aprire. Verificare che lo script [!INCLUDE[tsql](../../includes/tsql-md.md)] contenga gli eventi necessari per la riproduzione. Per altre informazioni, vedere [Requisiti per la riproduzione](../../tools/sql-server-profiler/replay-requirements.md).  
  
3.  Scegliere **Avvia** dal menu **Riproduci**e connettersi al server in cui si vuole riprodurre lo script.  
  
4.  Nella finestra di dialogo **Configurazione riproduzione** verificare le impostazioni e quindi fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Riprodurre le tracce](../../tools/sql-server-profiler/replay-traces.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
