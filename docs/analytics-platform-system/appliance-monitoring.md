---
title: Il monitoraggio dello strumento - Analitica Platform System | Documenti Microsoft
description: Questa Guida al monitoraggio dello strumento descrive gli strumenti e le attività per il monitoraggio del dispositivo di sistema della piattaforma Analitica.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: f87734a14337e7e35655439ddf70f0a126147eb7
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="appliance-monitoring-for-analytics-platform-system"></a>Monitoraggio dello strumento per Analitica Platform System
Questa Guida al monitoraggio dello strumento descrive gli strumenti e le attività per il monitoraggio del dispositivo di sistema della piattaforma Analitica.  
  
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
  
-   [Monitorare il dispositivo tramite la Console di amministrazione &#40;Analitica Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
![Avvisi della Console di amministrazione PDW](./media/appliance-monitoring/SQL_Server_PDW_AdminConsol_Queries.png "SQL_Server_PDW_AdminConsol_Queries")  
  
Viste di sistema  
SQL Server PDW include visualizzazioni di sistema completo che consentono di ottenere informazioni dettagliate sull'integrità di dispositivo, stato e delle prestazioni. Per un elenco di viste di sistema per il monitoraggio delle attività, vedere:  
  
-   [Monitorare il dispositivo utilizzando viste di sistema &#40;Analitica Platform System&#41;](monitor-the-appliance-by-using-system-views.md)  
  
System Center Operations Manager (SCOM)  
SQL Server PDW è completa integrazione con Systems Center Operations Manager. I management pack per SQL Server PDW sono disponibili come download gratuito. Per ulteriori informazioni sull'utilizzo di System Center per monitorare SQL Server PDW, vedere gli argomenti seguenti:  
  
-   [Monitorare l'accessorio tramite System Center Operations Manager &#40;Analitica Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)  
  
Soluzioni personalizzate  
Per le situazioni quando System Center non è disponibile con il data center, strumenti di monitoraggio è possibile monitorare il dispositivo utilizzando una soluzione di monitoraggio di terze parti. Installazione degli agenti esterne del software non è attualmente supportata in PDW, ma la maggior parte delle soluzioni di monitoraggio supportano Transact\-integrazione di SQL, in modo che l'amministratore di sistema può implementare Transact diretto\-query SQL del PDW dispositivo.  
  
Se la soluzione di monitoraggio non supporta direttamente Transact\-query SQL, oppure non dispone di uno strumento di monitoraggio, quindi è possibile utilizzare script per eseguire attività di monitoraggio, ad esempio l'invio di posta elettronica quando viene generato un avviso.  Wiki di TechNet contiene un esempio di soluzione di monitoraggio tramite script.  
  
-   [PowerShell di esempio di monitoraggio per SQL Server PDW](http://go.microsoft.com/fwlink/?LinkId=248020)  
   
## <a name="Tasks"></a>Relative attività di monitoraggio  
  
|Attività di monitoraggio|Description|  
|-------------------|---------------|  
|Monitorare l'accessorio utilizzando la Console di amministrazione.|[Monitorare il dispositivo tramite la Console di amministrazione &#40;Analitica Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)|  
|Monitorare l'accessorio utilizzando viste di sistema.|[Monitorare il dispositivo utilizzando viste di sistema &#40;Analitica Platform System&#41;](monitor-the-appliance-by-using-system-views.md)|  
|Monitoraggio del dispositivo tramite System Center|[Monitorare l'accessorio tramite System Center Operations Manager &#40;Analitica Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)|  
|Monitoraggio dello stato del dispositivo.|[Lo stato di integrità dello strumento di monitoraggio &#40;Analitica Platform System&#41;](monitor-appliance-health-state.md)|  
|Monitoraggio heartbeat.|[Inviare commenti e suggerimenti dati di telemetria a Microsoft &#40;SQL Server PDW&#41;](send-telemetry-feedback-to-microsoft-sql-server-pdw.md)|  
|Tenere traccia degli avvisi di dispositivo.|[Tenere traccia degli avvisi accessorio &#40;Analitica Platform System&#41;](track-appliance-alerts.md)|  
|Determinare la quantità di capacità è in uso.|[Utilizzo della capacità di visualizzare &#40;Analitica Platform System&#41;](view-capacity-utilization.md)|  
|Determinare la frequenza di polling del dispositivo.|[Determinare la frequenza di Polling &#40;Analitica Platform System&#41;](determine-polling-frequency.md)|  
|Quando si verifica un errore del cluster, determinare a quale cluster nodo non è riuscita.|[Determinare quale nodo del Cluster non è stato possibile &#40;Analitica Platform System&#41;](determine-which-cluster-node-failed.md)|  


<!-- MISSING LINKS |Monitor loads.|[Monitor Loads &#40;SQL Server PDW&#41;](../sqlpdw/monitor-loads-sql-server-pdw.md)|  -->  
<!-- MISSING LINKS |Monitor backups and restores.|[Monitor Backups and Restores &#40;SQL Server PDW&#41;](../sqlpdw/monitor-backups-and-restores-sql-server-pdw.md)|  -->  
<!-- MISSING LINKS |Monitor the active queries.|[Monitoring Active Queries &#40;SQL Server PDW&#41;](../sqlpdw/monitoring-active-queries-sql-server-pdw.md)|  -->  
  
## <a name="see-also"></a>Vedere anche  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Attività di gestione dello strumento &#40;Analitica Platform System&#41;](appliance-management-tasks.md)  
  
