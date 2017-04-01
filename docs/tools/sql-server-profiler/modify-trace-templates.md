---
title: "Modificare modelli di traccia | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modelli [SQL Server], SQL Server Profiler"
  - "Profiler [SQL Server Profiler], modelli"
  - "modelli di traccia [SQL Server]"
  - "modifica dei modelli di traccia"
  - "SQL Server Profiler, modelli"
ms.assetid: 75b62a54-8d16-4599-bd2d-c42cfcc209f4
caps.latest.revision: 24
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 24
---
# Modificare modelli di traccia
  È possibile modificare i modelli salvati in un file nel computer locale che esegue [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] e inoltre modificare i modelli da essi derivati. Per modificare i modelli esistenti, è possibile modificarne le proprietà, ad esempio le classi di evento e le colonne di dati, nell'ordine in cui sono state originariamente impostate nella scheda **Selezione eventi** della finestra di dialogo **Proprietà traccia**. È possibile aggiungere o rimuovere classi di evento e colonne di dati, nonché modificare i filtri. Dopo avere modificato il modello, viene creato un modello specifico dell'utente e il modello di sistema originale rimarrà inalterato. Per altre informazioni, vedere [Salvare tracce e modelli di traccia](../../tools/sql-server-profiler/save-traces-and-trace-templates.md).  
  
 Potrebbe essere necessario ricavare un modello da un file di traccia esistente nel caso non sia possibile risalire al modello originale utilizzato per creare la traccia oppure se si desidera rieseguire la stessa traccia in un momento successivo. Quando si utilizzano tracce esistenti, è possibile visualizzare le proprietà ma non modificarle. Per modificare le proprietà, arrestare o sospendere la traccia. Per altre informazioni, vedere [Derivare un modello da un file di traccia o da una tabella di traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md) e [Ottenere un modello da una traccia in esecuzione &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/derive-a-template-from-a-running-trace-sql-server-profiler.md).  
  
 **Per creare un modello di traccia**  
  
 [Creare un modello di traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md)  
  
 **Per eseguire una traccia da un modello di traccia**  
  
 [Creare una traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
 **Per modificare un modello di traccia**  
  
 [Utilizzo di SQL Server Profiler](../../tools/sql-server-profiler/modify-a-trace-template-sql-server-profiler.md)  
  
 [Utilizzo di Transact-SQL](../../relational-databases/sql-trace/modify-an-existing-trace-transact-sql.md)  
  
 **Per aggiungere o rimuovere eventi da un modello di traccia o da un file di traccia**  
  
 [Utilizzo di SQL Server Profiler](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
  
 [Utilizzo di Transact-SQL](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
## Vedere anche  
 [Avviare una traccia](../../tools/sql-server-profiler/start-a-trace.md)  
  
  