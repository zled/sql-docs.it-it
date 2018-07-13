---
title: Estrarre uno script da una traccia (SQL Server Profiler) | Microsoft Docs
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
- scripts [SQL Server], traces
- extracting script from trace [SQL Server]
ms.assetid: 431126a6-ff91-4818-8763-4442152bd571
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1233028af8fe5cd4c18f25efe3fe82260e86c5d6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37168212"
---
# <a name="extract-a-script-from-a-trace-sql-server-profiler"></a>Estrarre uno script da una traccia (SQL Server Profiler)
  In questo argomento vengono descritti l'estrazione di eventi [!INCLUDE[tsql](../../includes/tsql-md.md)] da un file o da una tabella di traccia e il relativo salvataggio come file script [!INCLUDE[tsql](../../includes/tsql-md.md)] tramite [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-extract-a-transact-sql-script-from-a-trace-file-or-table"></a>Per estrarre uno script Transact-SQL da un file o una tabella di traccia  
  
1.  Aprire il file o la tabella di traccia contenente gli eventi [!INCLUDE[tsql](../../includes/tsql-md.md)] che si desidera salvare in un file script [!INCLUDE[tsql](../../includes/tsql-md.md)]. Per altre informazioni, vedere [Aprire un file di traccia &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) o [Aprire una tabella di traccia &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md).  
  
2.  Nel menu **File** scegliere **Esporta**, **Estrai eventi di SQL Server** e quindi **Estrai eventi Transact-SQL**.  
  
3.  Nella finestra di dialogo **Salva con nome** digitare un nome per il file [!INCLUDE[tsql](../../includes/tsql-md.md)] e quindi fare clic su **Salva**.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
