---
title: "Riprodurre fino a un cursore (SQL Server Profiler) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "riproduzione di cursori"
  - "tracce [SQL Server], riproduzione"
  - "riproduzione di tracce"
ms.assetid: 89eadc41-4424-4a1c-ba61-0b52c851cdb1
caps.latest.revision: 22
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 22
---
# Riprodurre fino a un cursore (SQL Server Profiler)
  In questo argomento viene descritto come sospendere la riproduzione di tabelle o file di traccia in corrispondenza di un cursore utilizzando [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. La sospensione della riproduzione delle tracce in corrispondenza dei cursori supporta il debug in quanto è possibile interrompere la riproduzione di script di traccia lunghi in segmenti più brevi per eseguirne l'analisi incrementale.  
  
### Per eseguire la riproduzione fino al cursore  
  
1.  Aprire il file o la tabella di traccia che si desidera riprodurre. Per altre informazioni, vedere [Aprire un file di traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) o [Aprire una tabella di traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md).  
  
     Verificare che il file o la tabella di traccia aperta contenga le classi di evento necessarie per la riproduzione. Per altre informazioni, vedere [Requisiti per la riproduzione](../../tools/sql-server-profiler/replay-requirements.md).  
  
2.  Nella finestra di traccia fare clic su un evento.  
  
3.  Scegliere **Esegui fino al cursore** dal menu **Riproduci** e quindi connettersi al server di cui si vuole riprodurre la traccia.  
  
4.  Nella finestra di dialogo **Configurazione riproduzione** verificare le impostazioni e quindi fare clic su **OK**.  
  
     La riproduzione viene avviata e quindi sospesa in corrispondenza del primo cursore.  
  
5.  Premere F5 per riprendere la riproduzione della traccia.  
  
6.  Ripetere l'operazione descritta al passaggio 5 fino alla fine della traccia.  
  
## Vedere anche  
 [Riprodurre fino a un punto di interruzione &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/replay-to-a-breakpoint-sql-server-profiler.md)   
 [Riprodurre le tracce](../../tools/sql-server-profiler/replay-traces.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  