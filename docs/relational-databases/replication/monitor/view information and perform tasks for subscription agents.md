---
title: "Visualizzare le informazioni ed eseguire attivit&#224; degli agenti associati a una sottoscrizione (Monitoraggio replica) | Microsoft Docs"
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
  - "agenti [replica di SQL Server], visualizzazione di informazioni"
  - "visualizzazione di informazioni sugli agenti di replica"
  - "agenti [replica di SQL Server], attività in Monitoraggio replica"
ms.assetid: fbb59d31-2424-4552-9195-0da8d83e755f
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Visualizzare le informazioni ed eseguire attivit&#224; degli agenti associati a una sottoscrizione (Monitoraggio replica)
  In Monitoraggio replica sono disponibili due schede che consentono di accedere a informazioni sugli agenti associati a una sottoscrizione:  
  
-   **Tutte le sottoscrizioni**  
  
     In questa scheda vengono visualizzate informazioni su tutte le sottoscrizioni della pubblicazione selezionata.  
  
-   **Elenco verifica sottoscrizioni**  
  
     In questa scheda vengono visualizzate informazioni sulle sottoscrizioni di tutte le pubblicazioni disponibili sul server di pubblicazione selezionato che presentano errori, avvisi o un livello di prestazioni insufficiente. Questa scheda non viene visualizzata per i server di distribuzione che eseguono versioni precedenti a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
 Per ulteriori informazioni sulle opzioni di ogni scheda, fare clic sulla scheda nel riquadro di destra e quindi fare clic su **Guida** nella barra dei menu. Per informazioni sull'avvio di monitoraggio replica, vedere [avviare Monitoraggio replica](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
### Per visualizzare le informazioni ed eseguire le attività degli agenti associati a una sottoscrizione (scheda Tutte le sottoscrizioni)  
  
1.  Espandere un gruppo di server di pubblicazione nel riquadro sinistro, espandere un server di pubblicazione e quindi fare clic su una pubblicazione.  
  
2.  Fare clic su di **tutte le sottoscrizioni** scheda per visualizzare informazioni sulle sottoscrizioni. In questa scheda è inoltre possibile accedere a informazioni più dettagliate ed eseguire altre attività:  
  
    -   Per visualizzare informazioni dettagliate sull'agente di cui è associata a una sottoscrizione, fare doppio clic su sottoscrizione e quindi fare clic su **Visualizza dettagli**. Le informazioni dettagliate includono la cronologia dell'agente e i messaggi di errore, statistiche sulle prestazioni nella replica transazionale e statistiche sulla sincronizzazione dei singoli articoli nella replica di tipo merge.  
  
         Le schede della finestra Dettagli che viene avviata dipendono dal tipo di sottoscrizione: per le sottoscrizioni snapshot la scheda è **sottoscrittore cronologia server di distribuzione**; per le sottoscrizioni transazionali, le schede sono **Publisher alla cronologia del server di distribuzione**, **sottoscrittore cronologia server di distribuzione**, e **comandi non distribuiti**; per le sottoscrizioni di tipo merge, la scheda **Cronologia sincronizzazione**.  
  
    -   Per sincronizzare una sottoscrizione push, fare doppio clic su sottoscrizione e quindi fare clic su **Avvia sincronizzazione**.  
  
    -   Per reinizializzare una sottoscrizione, fare doppio clic su sottoscrizione e quindi fare clic su **Reinizializza sottoscrizione**.  
  
    -   Per convalidare una sottoscrizione di tipo merge singolo, fare doppio clic su sottoscrizione e quindi fare clic su **Convalida sottoscrizione**. Per convalidare tutte le sottoscrizioni di una pubblicazione di tipo merge, fare doppio clic su pubblicazione e quindi fare clic su **convalida tutte le sottoscrizioni**; per convalidare tutte le sottoscrizioni per una pubblicazione transazionale, fare doppio clic su pubblicazione e quindi fare clic su **Convalida sottoscrizioni**.  
  
    -   Per gestire i profili per l'agente, fare doppio clic sull'agente e quindi fare clic su **profilo agente**. Per ulteriori informazioni, vedere [utilizzare profili agenti di replica](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md).  
  
### Per visualizzare le informazioni ed eseguire le attività degli agenti associati a una sottoscrizione (scheda Elenco verifica sottoscrizioni)  
  
1.  Espandere un gruppo di server di pubblicazione nel riquadro sinistro e quindi fare clic su un server di pubblicazione.  
  
2.  Fare clic sui **elenco verifica sottoscrizioni** scheda per visualizzare informazioni sulle sottoscrizioni. In questa scheda è inoltre possibile accedere a informazioni più dettagliate ed eseguire altre attività:  
  
    -   Per visualizzare informazioni dettagliate sull'agente di cui è associata a una sottoscrizione, fare doppio clic su sottoscrizione e quindi fare clic su **Visualizza dettagli**. Le informazioni dettagliate includono la cronologia dell'agente e i messaggi di errore, statistiche sulle prestazioni nella replica transazionale e statistiche sulla sincronizzazione dei singoli articoli nella replica di tipo merge.  
  
         Le schede della finestra Dettagli che viene avviata dipendono dal tipo di sottoscrizione: per le sottoscrizioni snapshot la scheda è **sottoscrittore cronologia server di distribuzione**; per le sottoscrizioni transazionali, le schede sono **Publisher alla cronologia del server di distribuzione**, **sottoscrittore cronologia server di distribuzione**, e **prestazioni**; per le sottoscrizioni di tipo merge, la scheda **Cronologia sincronizzazione**.  
  
    -   Per sincronizzare una sottoscrizione push, fare doppio clic su sottoscrizione e quindi fare clic su **Avvia sincronizzazione**.  
  
    -   Per reinizializzare una sottoscrizione, fare doppio clic su sottoscrizione e quindi fare clic su **Reinizializza sottoscrizione**.  
  
    -   Per convalidare una sottoscrizione di tipo merge singolo, fare doppio clic su sottoscrizione e quindi fare clic su **Convalida sottoscrizione**. Per convalidare tutte le sottoscrizioni di una pubblicazione di tipo merge, fare doppio clic su pubblicazione e quindi fare clic su **convalida tutte le sottoscrizioni**; per convalidare tutte le sottoscrizioni per una pubblicazione transazionale, fare doppio clic su pubblicazione e quindi fare clic su **Convalida sottoscrizioni**.  
  
    -   Per gestire i profili per l'agente, fare doppio clic sull'agente e quindi fare clic su **profilo agente**. Per ulteriori informazioni, vedere [utilizzare profili agenti di replica](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md).  
  
## Vedere anche  
 [Consente di visualizzare informazioni ed eseguire attività per una sottoscrizione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)   
 [Monitoraggio della replica](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  