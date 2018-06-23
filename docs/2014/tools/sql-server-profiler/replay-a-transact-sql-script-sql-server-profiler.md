---
title: Riprodurre uno script Transact-SQL (SQL Server Profiler) | Microsoft Docs
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
- traces [SQL Server], replaying
- scripts [SQL Server], traces
- replaying traces
ms.assetid: 9c0eb222-e6e3-4bc1-a25f-a41e962d361b
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7f380638bca07e1db034df0c35209e144130b4a6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157854"
---
# <a name="replay-a-transact-sql-script-sql-server-profiler"></a>Riprodurre uno script Transact-SQL (SQL Server Profiler)
  Quando si desidera provare possibili soluzioni a un problema di prestazioni, è possibile utilizzare [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] per riprodurre script [!INCLUDE[tsql](../../includes/tsql-md.md)] e confrontare così le prestazioni prima e dopo aver effettuato le modifiche.  
  
### <a name="to-replay-a-transact-sql-script"></a>Per riprodurre uno script Transact-SQL  
  
1.  Scegliere **Apri** dal menu **File**e quindi **File script**.  
  
2.  Selezionare il file script [!INCLUDE[tsql](../../includes/tsql-md.md)] che si desidera aprire. Verificare che lo script [!INCLUDE[tsql](../../includes/tsql-md.md)] contenga gli eventi necessari per la riproduzione. Per altre informazioni, vedere [Requisiti per la riproduzione](replay-requirements.md).  
  
3.  Scegliere **Avvia** dal menu **Riproduci**e connettersi al server in cui si vuole riprodurre lo script.  
  
4.  Nella finestra di dialogo **Configurazione riproduzione** verificare le impostazioni e quindi fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Riprodurre le tracce](replay-traces.md)   
 [SQL Server Profiler](sql-server-profiler.md)  
  
  