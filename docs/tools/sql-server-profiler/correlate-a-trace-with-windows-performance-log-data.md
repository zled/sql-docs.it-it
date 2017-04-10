---
title: "Correlare una traccia con i dati del log delle prestazioni di Windows | Microsoft Docs"
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
  - "correlazione di una traccia con i dati del log"
  - "log [SQL Server], tracce"
  - "profiler [SQL Server Profiler], correlazione della traccia con i dati del log"
  - "tracce [SQL Server], log"
  - "SQL Server Profiler, correlazione della traccia con i dati del log"
ms.assetid: 1e4412c8-d27c-4aae-9b35-214128d1d00a
caps.latest.revision: 10
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 10
---
# Correlare una traccia con i dati del log delle prestazioni di Windows
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] consente di aprire un log delle prestazioni di Microsoft Windows, scegliere i contatori da correlare a una traccia e visualizzare i contatori delle prestazioni selezionati insieme alla traccia nell'interfaccia utente grafica di [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Quando si seleziona un evento nella finestra della traccia, una barra rossa verticale nel riquadro della finestra dei dati di Monitoraggio di sistema di [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] indica i dati del log delle prestazioni correlati all'evento di traccia selezionato.  
  
 Per correlare una traccia con i contatori delle prestazioni, aprire un file di traccia o una tabella contenente le colonne di dati **StartTime** e **EndTime** e quindi scegliere **Importa dati prestazioni** dal menu **File** di [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. È quindi possibile aprire un log delle prestazioni e selezionare gli oggetti e i contatori di Monitoraggio di sistema da correlare alla traccia.  
  
## Vedere anche  
 [Correlare una traccia e i dati dei registri di prestazioni di Windows &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/correlate-a-trace-with-windows-performance-log-data-sql-server-profiler.md)  
  
  