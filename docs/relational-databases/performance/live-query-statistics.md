---
title: "Statistiche sulle query dinamiche | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "10/28/2015"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "statistiche sulle query [SQL Server] statistiche sulle query dinamiche"
  - "statistiche sulle query dinamiche"
  - "debug [SQL Server], statistiche sulle query dinamiche"
  - "statistiche [SQL Server], statistiche sulle query dinamiche"
ms.assetid: 07f8f594-75b4-4591-8c29-d63811d7753e
caps.latest.revision: 16
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# Statistiche sulle query dinamiche
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] consente di visualizzare il piano di esecuzione dinamico di una query attiva. Il piano dinamico delle query offre informazioni approfondite in tempo reale sul processo di esecuzione della query, man mano che i controlli passano da un operatore del piano di query a un altro. Il piano dinamico delle query visualizza lo stato complessivo delle query e le statistiche di esecuzione a livello di operatore, ad esempio il numero di righe prodotte, il tempo trascorso, lo stato di avanzamento dell'operatore e così via. Poiché questi dati sono disponibili in tempo reale senza dover attendere il completamento della query, queste statistiche di esecuzione sono estremamente utili per il debug di problemi relativi alle prestazioni delle query. Questa funzionalità è disponibile a partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], tuttavia può funzionare con [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
> [!WARNING]  
>  Questa funzionalità viene usata principalmente per la risoluzione dei problemi. L'uso di questa funzionalità può rallentare in parte le prestazioni complessive delle query. Questa funzionalità può essere usata con il [debugger Transact-SQL](../../relational-databases/scripting/configure-firewall-rules-before-running-the-tsql-debugger.md).  
  
#### <a name="to-view-live-query-statistics"></a>Per visualizzare le statistiche sulle query dinamiche  
  
1.  Per visualizzare il piano di esecuzione dinamico delle query, dal menu degli strumenti scegliere l'icona **Live Query Statistics** (Statistiche query dinamiche).  
  
     ![Live Query Stats button on toolbar](../../relational-databases/performance/media/livequerystatstoolbar.png "Live Query Stats button on toolbar")  
  
     È anche possibile accedere al piano di esecuzione dinamico delle query facendo clic con il pulsante destro del mouse su una query selezionata in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] e quindi scegliendo **Includi statistiche query dinamiche**.  
  
     ![Live Query Stats button on popup menu](../../relational-databases/performance/media/livequerystatsmenu.png "Live Query Stats button on popup menu")  
  
2.  A questo punto, eseguire la query. Il piano di query dinamiche descrive lo stato di avanzamento complessivo delle query e le statistiche di esecuzione, ad esempio il tempo trascorso, lo stato di avanzamento e così via, degli operatori del piano di query. Le informazioni sullo stato di avanzamento e le statistiche di esecuzione delle query vengono aggiornate periodicamente durante l'esecuzione delle query. Usare queste informazioni per comprendere il processo generale di esecuzione delle query e per eseguire il debug di query a esecuzione prolungata, query eseguite per un periodo illimitato, query che causano l'overflow di tempdb e problemi di timeout.  
  
     ![Live Query Stats button in showplan](../../relational-databases/performance/media/livequerystatsplan.png "Live Query Stats button in showplan")  
  
 È anche possibile accedere al piano di esecuzione dinamico delle query da **Monitoraggio attività** facendo clic con il pulsante destro del mouse sulle query nella tabella **Query attive con costo elevato** .  
  
 ![Live Query Stats button in Activity Monitor](../../relational-databases/performance/media/livequerystatsactmon.png "Live Query Stats button in Activity Monitor")  
  
## <a name="remarks"></a>Osservazioni  
 Perché le statistiche delle query dinamiche possano acquisire informazioni sullo stato di avanzamento delle query, è necessario che l'infrastruttura del profilo delle statistiche sia stata abilitata. Se si specifica **Includi statistiche query dinamiche** in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] , l'infrastruttura delle statistiche viene abilitata per la sessione di query corrente. 
 
Fino a [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] saranno disponibili altri due modi per abilitare l'infrastruttura delle statistiche che è possibile usare per visualizzare le statistiche sulle query dinamiche da altre sessioni, ad esempio da Monitoraggio attività:  
  
-   Eseguire `SET STATISTICS XML ON;` o `SET STATISTICS PROFILE ON;` nella sessione di destinazione.  
  
 o  
  
-   Abilitare l'evento esteso **query_post_execution_showplan** . Si tratta di un'impostazione a livello di server che abilita le statistiche delle query dinamiche su tutte le sessioni. Per abilitare gli eventi estesi, vedere [Monitor System Activity Using Extended Events](../../relational-databases/extended-events/monitor-system-activity-using-extended-events.md).  

A partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] include una versione leggera dell'infrastruttura del profilo delle statistiche. Esistono due modi per abilitare l'infrastruttura leggera delle statistiche che è possibile usare per visualizzare le statistiche sulle query dinamiche da altre sessioni, ad esempio da Monitoraggio attività:

-   Usare il flag di traccia globale 7412.  
  
 o  
  
-   Abilitare l'evento esteso **query_thread_profile**. Si tratta di un'impostazione a livello di server che abilita le statistiche delle query dinamiche su tutte le sessioni. Per abilitare gli eventi estesi, vedere [Monitor System Activity Using Extended Events](../../relational-databases/extended-events/monitor-system-activity-using-extended-events.md).
  
 > [!NOTE] Le stored procedure compilate in modo nativo non sono supportate.  
  
## <a name="permissions"></a>Autorizzazioni  
 Sono necessarie l'autorizzazione a livello di database **SHOWPLAN** per popolare la pagina dei risultati delle **statistiche sulle query dinamiche** , l'autorizzazione a livello di server **VIEW SERVER STATE** per visualizzare le statistiche dinamiche e le autorizzazioni necessarie per eseguire la query.  
  
## <a name="see-also"></a>Vedere anche  
 [Monitoraggio e ottimizzazione delle prestazioni](../../relational-databases/performance/monitor-and-tune-for-performance.md)   
 [Strumenti per il monitoraggio e l'ottimizzazione delle prestazioni](../../relational-databases/performance/performance-monitoring-and-tuning-tools.md)   
 [Aprire Monitoraggio attività &#40;SQL Server Management Studio&#41;](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md)   
 [Monitoraggio attività](../../relational-databases/performance-monitor/activity-monitor.md)   
 [Monitoraggio delle prestazioni con Archivio query](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [sys.dm_exec_query_statistics_xml](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-statistics-xml-transact-sql.md)   
 [sys.dm_exec_query_profiles](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql.md)   
 [Flag di traccia](Trace%20Flags%20\(Transact-SQL\).md)