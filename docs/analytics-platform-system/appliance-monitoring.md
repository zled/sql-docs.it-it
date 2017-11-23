---
title: Strumento di monitoraggio (Analitica piattaforma sistema)
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 253864fb-9178-41d2-a0ae-5dd9fd0a4fda
caps.latest.revision: "25"
ms.openlocfilehash: dbbae960d5e4d88b6cb725c9e22fc36a428b9264
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="appliance-monitoring"></a>Strumento di monitoraggio
Questa Guida dello strumento di monitoraggio vengono descritti gli strumenti e attività per il monitoraggio del dispositivo di SQL Server PDW.  
  
## <a name="Basics"></a>Nozioni di base e gli strumenti di monitoraggio  
I valori e informazioni che è possibile monitorare lo strumento di SQL Server PDW sono numerose. Ad esempio, di seguito sono tipici di attività di monitoraggio.  
  
-   Verifica per qualsiasi avviso emesso da SQL Server PDW.  
  
-   Monitoraggio per l'hardware non riuscito.  
  
-   Monitoraggio di problemi di connettività di rete.  
  
-   Controllare gli errori restituiti agli utenti durante l'elaborazione delle query.  
  
-   Visualizza il numero di sessioni attualmente attive e query.  
  
-   Verificare lo stato di caricamento, backup e ripristini.  
  
### <a name="appliance-monitoring-tools"></a>Strumenti di monitoraggio del dispositivo  
Sono disponibili più strumenti disponibili per il monitoraggio del dispositivo.  
  
Console di amministrazione  
SQL Server PDW è una Console di amministrazione. Questo è uno strumento basato sul web che consente di visualizzare informazioni sulle query, caricamenti, backup e ripristino, i blocchi, le sessioni, avvisi e stato dello strumento. Esegue la Console di amministrazione nel dispositivo; gli utenti di connettersi alla Console di amministrazione tramite Internet Explorer. Per altre informazioni, vedere:  
  
-   [Monitorare il dispositivo tramite la Console di amministrazione &#40; Sistema della piattaforma Analitica &#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
![Avvisi della Console di amministrazione PDW](./media/appliance-monitoring/SQL_Server_PDW_AdminConsol_Queries.png "SQL_Server_PDW_AdminConsol_Queries")  
  
Viste di sistema  
SQL Server PDW include visualizzazioni di sistema completo che consentono di ottenere informazioni dettagliate sull'integrità di dispositivo, stato e delle prestazioni. Per un elenco di viste di sistema per il monitoraggio delle attività, vedere:  
  
-   [Monitorare l'accessorio utilizzando viste di sistema &#40; Sistema della piattaforma Analitica &#41;](monitor-the-appliance-by-using-system-views.md)  
  
System Center Operations Manager (SCOM)  
SQL Server PDW è completa integrazione con Systems Center Operations Manager. I management pack per SQL Server PDW sono disponibili come download gratuito. Per ulteriori informazioni sull'utilizzo di System Center per monitorare SQL Server PDW, vedere gli argomenti seguenti:  
  
-   [Monitorare il dispositivo con System Center Operations Manager &#40; Sistema della piattaforma Analitica &#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)  
  
Soluzioni personalizzate  
Per le situazioni quando System Center non è disponibile con il data center, strumenti di monitoraggio è possibile monitorare il dispositivo utilizzando una soluzione di monitoraggio di terze parti. Installazione degli agenti esterne del software non è attualmente supportata in PDW, ma la maggior parte delle soluzioni di monitoraggio supportano Transact\-integrazione di SQL, in modo che l'amministratore di sistema può implementare Transact diretto\-query SQL del PDW dispositivo.  
  
Se la soluzione di monitoraggio non supporta direttamente Transact\-query SQL, oppure non dispone di uno strumento di monitoraggio, quindi è possibile utilizzare script per eseguire attività di monitoraggio, ad esempio l'invio di posta elettronica quando viene generato un avviso.  Wiki di TechNet contiene un esempio di soluzione di monitoraggio tramite script.  
  
-   [PowerShell di esempio di monitoraggio per SQL Server PDW](http://go.microsoft.com/fwlink/?LinkId=248020)  
   
## <a name="Tasks"></a>Relative attività di monitoraggio  
  
|Attività di monitoraggio|Description|  
|-------------------|---------------|  
|Monitorare l'accessorio utilizzando la Console di amministrazione.|[Monitorare il dispositivo tramite la Console di amministrazione &#40; Sistema della piattaforma Analitica &#41;](monitor-the-appliance-by-using-the-admin-console.md)|  
|Monitorare l'accessorio utilizzando viste di sistema.|[Monitorare l'accessorio utilizzando viste di sistema &#40; Sistema della piattaforma Analitica &#41;](monitor-the-appliance-by-using-system-views.md)|  
|Monitoraggio del dispositivo tramite System Center|[Monitorare il dispositivo con System Center Operations Manager &#40; Sistema della piattaforma Analitica &#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)|  
|Monitoraggio dello stato del dispositivo.|[Stato di integrità dello strumento di monitoraggio &#40; Sistema della piattaforma Analitica &#41;](monitor-appliance-health-state.md)|  
|Monitoraggio heartbeat.|[Inviare commenti e suggerimenti dati di telemetria a Microsoft &#40; SQL Server PDW &#41;](send-telemetry-feedback-to-microsoft-sql-server-pdw.md)|  
|Tenere traccia degli avvisi di dispositivo.|[Gli avvisi dello strumento di traccia &#40; Sistema della piattaforma Analitica &#41;](track-appliance-alerts.md)|  
|Determinare la quantità di capacità è in uso.|[Visualizzare l'utilizzo della capacità &#40; Sistema della piattaforma Analitica &#41;](view-capacity-utilization.md)|  
|Determinare la frequenza di polling del dispositivo.|[Determinare la frequenza di Polling &#40; Sistema della piattaforma Analitica &#41;](determine-polling-frequency.md)|  
|Quando si verifica un errore del cluster, determinare a quale cluster nodo non è riuscita.|[Determinare quale nodo del Cluster non riuscita &#40; Sistema della piattaforma Analitica &#41;](determine-which-cluster-node-failed.md)|  


<!-- MISSING LINKS |Monitor loads.|[Monitor Loads &#40;SQL Server PDW&#41;](../sqlpdw/monitor-loads-sql-server-pdw.md)|  -->  
<!-- MISSING LINKS |Monitor backups and restores.|[Monitor Backups and Restores &#40;SQL Server PDW&#41;](../sqlpdw/monitor-backups-and-restores-sql-server-pdw.md)|  -->  
<!-- MISSING LINKS |Monitor the active queries.|[Monitoring Active Queries &#40;SQL Server PDW&#41;](../sqlpdw/monitoring-active-queries-sql-server-pdw.md)|  -->  
  
## <a name="see-also"></a>Vedere anche  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Attività di gestione dispositivo &#40; Sistema della piattaforma Analitica &#41;](appliance-management-tasks.md)  
  
