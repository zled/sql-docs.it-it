---
title: "Creare tracce del profiler per la riproduzione (Analysis Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SQL Server Profiler, Analysis Services"
  - "monitoraggio di Analysis Services [SQL Server]"
  - "riproduzione di query"
  - "riproduzione di richieste di individuazione"
  - "eventi [Analysis Services]"
  - "riproduzione di comandi"
  - "Profiler [SQL Server Profiler], Analysis Services"
  - "prestazioni [Analysis Services], riproduzioni"
  - "tracce [Analysis Services]"
ms.assetid: 93b2fc46-7cfb-4ab5-abeb-1475a7d6f0f2
caps.latest.revision: 33
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 33
---
# Creare tracce del profiler per la riproduzione (Analysis Services)
  Per riprodurre query, richieste di individuazione e comandi inviati dagli utenti a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], è necessario che [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] raccolga gli eventi richiesti. Per avviare la raccolta di questi eventi, è necessario selezionare opportune classi di evento nella scheda **Selezione eventi** della finestra di dialogo **Proprietà traccia**. Se ad esempio viene selezionata la classe di evento Query Begin, verranno raccolti gli eventi contenenti query e questi eventi verranno utilizzati per la riproduzione. In questo caso il file di traccia conterrà informazioni sufficienti a supportare la riproduzione di transazioni di server nella sequenza originale e in un ambiente distribuito.  
  
## Riproduzione di query  
 Per la riproduzione di query, è necessario che in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] vengano acquisiti gli eventi seguenti:  
  
-   Classe di evento Audit Login con tutte le colonne di dati. Questa classe di evento contiene informazioni sugli utenti connessi e sulle impostazioni della sessione. L'ID di processo server (SPID) contiene il riferimento alla sessione utente. Per altre informazioni, vedere [Colonne di dati degli eventi di controllo di sicurezza](../../analysis-services/trace-events/security-audit-data-columns.md).  
  
-   Classe di evento Query Begin con tutte le colonne di dati. Questa classe di evento contiene le informazioni sulla query inviata a [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. La colonna Event Subclass contiene informazioni sul tipo di query. La colonna TextData contiene il testo effettivo della query. La colonna RequestParameters contiene i parametri per le query con parametri, mentre la colonna RequestProperties contiene le proprietà di una richiesta XMLA (XML for Analysis). Per altre informazioni, vedere [Colonne di dati degli eventi di query](../../analysis-services/trace-events/queries-events-data-columns.md).  
  
-   Classe di evento Query End con tutte le colonne di dati. Questa classe di evento verifica lo stato di esecuzione della query. Per altre informazioni, vedere [Colonne di dati degli eventi di query](../../analysis-services/trace-events/queries-events-data-columns.md).  
  
## Riproduzione di richieste di individuazione  
 Per la riproduzione di richieste di individuazione, è necessario che in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] vengano acquisiti gli eventi seguenti:  
  
-   Classe di evento Audit Login con tutte le colonne di dati. Questa classe di evento contiene informazioni sugli utenti connessi e sulle impostazioni della sessione. L'ID di processo server (SPID) contiene il riferimento alla sessione utente. Per altre informazioni, vedere [Colonne di dati degli eventi di controllo di sicurezza](../../analysis-services/trace-events/security-audit-data-columns.md).  
  
-   Classe di evento Discover Begin con tutte le colonne di dati. Nella colonna TextData viene fornita l'informazione \<RequestType> della richiesta di individuazione, mentre nella colonna RequestProperties viene fornita l'informazione \<Properties> della richiesta di individuazione. La colonna EventSubclass contiene il tipo di richiesta di individuazione. Per altre informazioni, vedere [Colonne di dati degli eventi di individuazione](../../analysis-services/trace-events/discover-events-data-columns.md).  
  
-   Classe di evento Discover End con tutte le colonne di dati. Questa classe di evento verifica lo stato della richiesta di individuazione. Per altre informazioni, vedere [Colonne di dati degli eventi di individuazione](../../analysis-services/trace-events/discover-events-data-columns.md).  
  
## Riproduzione di comandi  
 Per la riproduzione di comandi, è necessario che in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] vengano acquisiti gli eventi seguenti:  
  
-   Classe di evento Command Begin con tutte le colonne di dati. La colonna TextData fornisce informazioni dettagliate sul comando, ad esempio il tipo di processo, l'ID database e l'ID cubo. La colonna RequestParameters contiene i parametri per i comandi con parametri, mentre la colonna RequestProperties contiene le proprietà di una richiesta XMLA. Per altre informazioni, vedere [Colonne di dati degli eventi di comando](../../analysis-services/trace-events/command-events-data-columns.md).  
  
-   Classe di evento Command End con tutte le colonne di dati. Questa classe di evento verifica lo stato del comando. Per altre informazioni, vedere [Colonne di dati degli eventi di comando](../../analysis-services/trace-events/command-events-data-columns.md).  
  
## Vedere anche  
 [Eventi di traccia di Analysis Services](../../analysis-services/trace-events/analysis-services-trace-events.md)   
 [Introduzione al monitoraggio di Analysis Services tramite SQL Server Profiler](../../analysis-services/instances/introduction-to-monitoring-analysis-services-with-sql-server-profiler.md)  
  
  