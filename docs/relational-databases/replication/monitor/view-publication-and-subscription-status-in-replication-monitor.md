---
title: "Visualizzazione dello stato delle pubblicazioni e delle sottoscrizioni in Monitoraggio replica | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "agente di lettura log, monitoraggio"
  - "agente di merge, monitoraggio"
  - "agente di lettura coda, monitoraggio"
  - "pubblicazioni [replica di SQL Server], visualizzazione di informazioni"
  - "agente snapshot, monitoraggio"
  - "agente di distribuzione, monitoraggio"
  - "monitoraggio delle prestazioni [replica di SQL Server], stato delle pubblicazioni"
  - "monitoraggio delle prestazioni [replica di SQL Server], stato delle sottoscrizioni"
  - "sottoscrizioni [replica di SQL Server], visualizzazione dello stato"
  - "Monitoraggio replica, stato delle pubblicazioni e delle sottoscrizioni"
ms.assetid: 16590771-9867-463e-a973-36a5c145ac16
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 34
---
# Visualizzazione dello stato delle pubblicazioni e delle sottoscrizioni in Monitoraggio replica
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Monitoraggio replica vengono visualizzate informazioni sullo stato per le pubblicazioni e sottoscrizioni:  
  
-   Lo stato di una pubblicazione è determinato dallo stato con priorità più alta delle relative sottoscrizioni. Ad esempio, se una sottoscrizione a una pubblicazione presenta un errore e in un'altra sottoscrizione viene rilevato un problema di prestazioni, per la pubblicazione viene visualizzato uno stato di errore.  
  
-   Lo stato di una sottoscrizione è determinato dallo stato degli agenti associati alla sottoscrizione. Nel caso della replica di tipo merge si tratta dell'agente di merge. Nella replica transazionale, può trattarsi dell'agente di lettura log o dell'agente di distribuzione (viene visualizzato lo stato con priorità più alta). Lo stato può anche essere determinato dall'agente di lettura coda se si utilizzano sottoscrizioni ad aggiornamento in coda. Nella replica snapshot, si tratta dell'agente snapshot o dell'agente di distribuzione (viene visualizzato lo stato con priorità più alta).  
  
 Le tabelle riportate nelle sezioni seguenti includono i valori possibili per lo stato delle pubblicazioni e delle sottoscrizioni. Tre dei valori di stato vengono visualizzati solo se si raggiunge o supera una soglia:  
  
-   Scadenza imminente  
  
     Questo valore di stato si applica a tutti i tipi di replica. Per ulteriori informazioni, vedere [impostare soglie e avvisi in Monitoraggio replica](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
-   Prestazioni critiche  
  
     Questo valore di stato si applica alla replica transazionale e alla replica di tipo merge. Per ulteriori informazioni, vedere [monitoraggio delle prestazioni con Monitoraggio replica](../../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md).  
  
-   Merge con esecuzione prolungata  
  
     Questo valore di stato si applica alla replica di tipo merge. Per ulteriori informazioni, vedere [monitoraggio delle prestazioni con Monitoraggio replica](../../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md).  
  
 Oltre allo stato delle pubblicazioni e delle sottoscrizioni, nella replica di tipo merge è possibile ottenere statistiche a livello di articolo che offrono informazioni dettagliate sul tempo ancora necessario per completare una fase di merge, sul tempo impiegato per l'elaborazione di un determinato articolo, sul tipo di connessione utilizzato da un Sottoscrittore e su altri aspetti importanti. Le statistiche vengono visualizzate nella finestra Agente di merge in Monitoraggio replica. Nella replica snapshot e transazionale vengono offerte informazioni dettagliate sull'elaborazione dell'agente di distribuzione.  
  
 **Per visualizzare lo stato delle pubblicazioni e delle sottoscrizioni**  
  
-   Monitoraggio replica: [consente di visualizzare informazioni ed eseguire attività per una pubblicazione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md) e [consente di visualizzare informazioni ed eseguire attività per una sottoscrizione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)  
  
 **Per visualizzare informazioni dettagliate sugli agenti**  
  
-   Monitoraggio replica: [consente di visualizzare informazioni ed eseguire attività relative agli agenti associati a una pubblicazione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md) e [consente di visualizzare informazioni ed eseguire attività relative agli agenti associati a una sottoscrizione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
## Valori di stato delle pubblicazioni  
 Nella tabella seguente vengono mostrati i valori di stato delle pubblicazioni e le relative icone in ordine di priorità.  
  
|Stato|Icona|  
|------------|----------|  
|Errore|![Icona interfaccia utente: errore](../../../database-engine/availability-groups/windows/media/repl-icon-error.png "Icona interfaccia utente: errore")|  
|Prestazioni critiche|![Icona interfaccia utente: avviso](../../../database-engine/availability-groups/windows/media/repl-icon-warn.png "Icona interfaccia utente: avviso")|  
|Ripetizione comando non riuscito|![Icona interfaccia utente: nuovo tentativo dell'agente di replica](../../../relational-databases/replication/monitor/media/repl-icon-retry.png "Icona interfaccia utente: nuovo tentativo dell'agente di replica")|  
|OK|none|  
  
## Valori di stato delle sottoscrizioni  
 Nelle tabelle seguenti vengono mostrati i valori di stato delle sottoscrizioni e le relative icone in ordine di priorità. È possibile che una sottoscrizione essere in due stati allo stesso tempo, ad esempio **scadenza imminente/scaduta** e **ripetizione comando non riuscito**; viene visualizzato lo stato di priorità più alto.  
  
 I valori di stato **prestazioni critiche**, **scadenza imminente/scaduta**, e **Uninitialized** sono avvisi. Se viene visualizzato un avviso, in Monitoraggio replica viene inoltre segnalato se un agente è in esecuzione. Ad esempio, lo stato potrebbe essere **In esecuzione, Prestazioni critiche**.  
  
### Sottoscrizioni transazionali  
  
|Stato|Icona|  
|------------|----------|  
|Errore|![Icona interfaccia utente: errore](../../../database-engine/availability-groups/windows/media/repl-icon-error.png "Icona interfaccia utente: errore")|  
|Prestazioni critiche|![Icona interfaccia utente: avviso](../../../database-engine/availability-groups/windows/media/repl-icon-warn.png "Icona interfaccia utente: avviso")|  
|Scadenza imminente/Scaduta|![Icona interfaccia utente: avviso](../../../database-engine/availability-groups/windows/media/repl-icon-warn.png "Icona interfaccia utente: avviso")|  
|Sottoscrizione non inizializzata|![Icona interfaccia utente: avviso](../../../database-engine/availability-groups/windows/media/repl-icon-warn.png "Icona interfaccia utente: avviso")|  
|Ripetizione comando non riuscito|![Icona interfaccia utente: nuovo tentativo dell'agente di replica](../../../relational-databases/replication/monitor/media/repl-icon-retry.png "Icona interfaccia utente: nuovo tentativo dell'agente di replica")|  
|Non in esecuzione|![Icona interfaccia utente: agente di replica arrestato](../../../relational-databases/replication/monitor/media/repl-icon-stopped.png "Icona interfaccia utente: agente di replica arrestato")|  
|In esecuzione|![Icona interfaccia utente: agente di replica in esecuzione](../../../relational-databases/replication/monitor/media/repl-icon-running.png "Icona interfaccia utente: agente di replica in esecuzione")|  
  
### Sottoscrizioni di tipo merge  
  
|Stato|Icona|  
|------------|----------|  
|Errore|![Icona interfaccia utente: errore](../../../database-engine/availability-groups/windows/media/repl-icon-error.png "Icona interfaccia utente: errore")|  
|Prestazioni critiche|![Icona interfaccia utente: avviso](../../../database-engine/availability-groups/windows/media/repl-icon-warn.png "Icona interfaccia utente: avviso")|  
|Merge con esecuzione prolungata|![Icona interfaccia utente: avviso](../../../database-engine/availability-groups/windows/media/repl-icon-warn.png "Icona interfaccia utente: avviso")|  
|Scadenza imminente/Scaduta|![Icona interfaccia utente: avviso](../../../database-engine/availability-groups/windows/media/repl-icon-warn.png "Icona interfaccia utente: avviso")|  
|Sottoscrizione non inizializzata|![Icona interfaccia utente: avviso](../../../database-engine/availability-groups/windows/media/repl-icon-warn.png "Icona interfaccia utente: avviso")|  
|Ripetizione comando non riuscito|![Icona interfaccia utente: nuovo tentativo dell'agente di replica](../../../relational-databases/replication/monitor/media/repl-icon-retry.png "Icona interfaccia utente: nuovo tentativo dell'agente di replica")|  
|Sincronizzazione in corso|![Icona interfaccia utente: agente di replica in esecuzione](../../../relational-databases/replication/monitor/media/repl-icon-running.png "Icona interfaccia utente: agente di replica in esecuzione")|  
|Non in sincronizzazione|![Icona interfaccia utente: agente di replica arrestato](../../../relational-databases/replication/monitor/media/repl-icon-stopped.png "Icona interfaccia utente: agente di replica arrestato")|  
  
### Sottoscrizioni snapshot  
  
|Stato|Icona|  
|------------|----------|  
|Errore|![Icona interfaccia utente: errore](../../../database-engine/availability-groups/windows/media/repl-icon-error.png "Icona interfaccia utente: errore")|  
|Scadenza imminente/Scaduta|![Icona interfaccia utente: avviso](../../../database-engine/availability-groups/windows/media/repl-icon-warn.png "Icona interfaccia utente: avviso")|  
|Sottoscrizione non inizializzata|![Icona interfaccia utente: avviso](../../../database-engine/availability-groups/windows/media/repl-icon-warn.png "Icona interfaccia utente: avviso")|  
|Ripetizione comando non riuscito|![Icona interfaccia utente: nuovo tentativo dell'agente di replica](../../../relational-databases/replication/monitor/media/repl-icon-retry.png "Icona interfaccia utente: nuovo tentativo dell'agente di replica")|  
|Sincronizzazione in corso|![Icona interfaccia utente: agente di replica in esecuzione](../../../relational-databases/replication/monitor/media/repl-icon-running.png "Icona interfaccia utente: agente di replica in esecuzione")|  
|Non in sincronizzazione|![Icona interfaccia utente: agente di replica arrestato](../../../relational-databases/replication/monitor/media/repl-icon-stopped.png "Icona interfaccia utente: agente di replica arrestato")|  
  
## Vedere anche  
 [Monitoraggio della replica](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  