---
title: Eseguire SQL Server Profiler | Documenti Microsoft
ms.custom: 
ms.date: 7/7/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Profiler [SQL Server Profiler], starting
- SQL Server Profiler, starting
- starting SQL Server Profiler
- Profiler [SQL Server Profiler], running
- SQL Server Profiler, running
- running SQL Server Profiler
ms.assetid: 22e57ffa-63b0-4de3-b92e-df297dda1226
caps.latest.revision: 25
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 9ce18e13fa735921846ea7f564ff53983d0c2dca
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="run-sql-server-profiler"></a>Eseguire SQL Server Profiler
  È possibile eseguire [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] in diversi modi, per supportare la raccolta di traccia di output in una vasta gamma di scenari. È possibile avviare [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] da Windows 10 **avviare** dal menu dal **strumenti** menu [!INCLUDE[ssDE](../../includes/ssde-md.md)] Ottimizzazione guidata e da diverse posizioni in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
Quando si inizia a [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] e selezionare **nuova traccia** dal **File** menu, l'applicazione visualizza un **Connetti al Server** la finestra di dialogo in cui è possibile specificare un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza a cui connettersi.  
## <a name="to-start-sql-server-profiler-from-the-windows-10-start-menu"></a>Per avviare SQL Server Profiler dal menu Start di Windows 10  
-  Fare clic su Windows **avviare** oppure premere le finestre della chiave e iniziano a digitare "SQL Server Profiler 17". Quando il **SQL Server Profiler 17** riquadro viene visualizzato, fare clic.   

## <a name="to-start-sql-server-profiler-in-database-engine-tuning-advisor"></a>Per avviare SQL Server Profiler in Ottimizzazione guidata motore di database  
-  Selezionare [!INCLUDE[ssDE](../../includes/ssde-md.md)] SQL Server Profiler **dal menu** Tools **di Ottimizzazione guidata**.  

## <a name="to-start-sql-server-profiler-in-sql-server-management-studio"></a>Per avviare SQL Server Profiler in SQL Server Management Studio  
 È possibile avviare [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] da diverse posizioni nella [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Quando [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] viene avviato, viene caricato il contesto di connessione, il modello di traccia e il contesto di filtro del punto di avvio. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]Avvia ogni sessione di SQL Server Profiler nella rispettiva istanza e Profiler continua a funzionare se si arresta [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
### <a name="to-start-sql-server-profiler-from-the-tools-menu"></a>Per avviare SQL Server Profiler dal menu Strumenti  
-  Scegliere [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Tools** menu, click **SQL Server Profiler**.  

### <a name="to-start-sql-server-profiler-from-the-query-editor"></a>Per avviare SQL Server Profiler dall'editor di query  
- In Editor di query fare clic con il pulsante destro del mouse e scegliere **Traccia query in SQL Server Profiler**.  

  > [!NOTE]  
  >  Il contesto di connessione è la connessione dell'editor, il modello di traccia è TSQL_SPs e il filtro applicato è SPID = finestra della query SPID.  
    
### <a name="to-start-sql-server-profiler-from-activity-monitor"></a>Per avviare SQL Server Profiler da Monitor attività  
- In Monitoraggio attività, fare clic su di **processi** riquadro destro il processo che si desidera analizzare e quindi fare clic su **traccia processo in SQL Server Profiler**.  

    > [!NOTE]  
    >  Quando viene selezionato un processo, il contesto di connessione è la connessione Esplora oggetti stabilita all'apertura di Monitor attività. Il modello di traccia è l'impostazione predefinita basata sul tipo di server e lo SPID corrisponde a quello del processo selezionato.  
    
## <a name="net-framework-security"></a>Sicurezza di .NET Framework  
- In modalità di autenticazione di Windows, l'account utente che esegue [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] deve disporre dell'autorizzazione per connettersi all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
- Per eseguire tracce con [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], gli utenti devono inoltre possedere l'autorizzazione ALTER TRACE.  

## <a name="next-steps"></a>Passaggi successivi  
 [Panoramica di SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)   
 [Utilizzo di SQL Server Management Studio](http://msdn.microsoft.com/library/f289e978-14ca-46ef-9e61-e1fe5fd593be)  

