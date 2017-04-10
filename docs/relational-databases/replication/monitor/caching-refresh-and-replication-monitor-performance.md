---
title: "Memorizzazione nella cache, aggiornamento e prestazioni di Monitoraggio replica | Microsoft Docs"
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
  - "monitoraggio delle prestazioni [replica di SQL Server], Monitoraggio replica"
  - "cache [SQL Server], replica"
  - "Monitoraggio replica, memorizzazione nella cache"
  - "aggiornamento di dati"
  - "Monitoraggio replica, aggiornamento"
ms.assetid: a2d8b666-ed41-4f86-b2b8-c8e118416ab7
caps.latest.revision: 12
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 12
---
# Memorizzazione nella cache, aggiornamento e prestazioni di Monitoraggio replica
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Monitoraggio replica è progettato per monitorare in modo efficiente un numero elevato di computer in un sistema di produzione. Le query utilizzate in Monitoraggio replica per eseguire calcoli e raccogliere dati vengono memorizzate nella cache e aggiornate con frequenza periodica. La memorizzazione nella cache riduce il numero di query e di calcoli necessari durante la visualizzazione di pagine diverse in Monitoraggio replica e consente di monitorare più utenti in modo efficiente.  
  
 Aggiornamento della cache viene gestita da un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] processo dell'agente, il **aggiornamento Monitoraggio replica per la distribuzione**. Il processo è impostato per l'esecuzione continua, ma la pianificazione dell'aggiornamento della cache è basata sull'attesa di una certa quantità di tempo dall'aggiornamento precedente:  
  
-   Se dopo l'ultima creazione della cache la cronologia dell'agente ha subito modifiche, il tempo di attesa sarà il valore minimo tra 4 secondi e la quantità di tempo impiegata per creare la cache precedente.  
  
-   Se dopo l'ultima creazione della cache la cronologia dell'agente non ha subito modifiche (ma possono essersi verificate modifiche di altro tipo), il tempo di attesa sarà il valore massimo tra 30 secondi e la quantità di tempo impiegata per creare la cache precedente.  
  
## Aggiornamento dell'interfaccia utente di Monitoraggio replica  
 L'interfaccia utente di Monitoraggio replica può essere aggiornata nei modi seguenti:  
  
-   La finestra principale di Monitoraggio replica, comprese tutte le schede, viene aggiornata automaticamente ogni cinque secondi per impostazione predefinita. Gli aggiornamenti automatici non forzano un aggiornamento della cache. Nell'interfaccia utente viene visualizzata la versione più recente dei dati della cache. È possibile personalizzare la frequenza di aggiornamento utilizzata per tutte le finestre associate a un server di pubblicazione modificando le impostazioni di quest'ultimo. È inoltre possibile disabilitare gli aggiornamenti automatici per un server di pubblicazione.  
  
-   Le finestre dei dettagli che vengono avviate da Monitoraggio replica non vengono aggiornate automaticamente per impostazione predefinita, ad eccezione delle finestre relative alle sottoscrizioni di tipo merge di cui viene eseguita la sincronizzazione. Se si specifica che le finestre dei dettagli devono essere aggiornate automaticamente, l'aggiornamento seguirà la stessa pianificazione della finestra principale di Monitoraggio replica.  
  
-   Tutte le finestre possono essere aggiornate manualmente premendo F5 o facendo clic su un nodo dell'albero di monitoraggio replica e facendo clic su **aggiornamento**. Gli aggiornamenti manuali forzano un aggiornamento della cache.  
  
 Per ulteriori informazioni, vedere [aggiornare dati in Monitoraggio replica](../../../relational-databases/replication/monitor/refresh-data-in-replication-monitor.md).  
  
## Considerazioni sulle prestazioni  
 Sebbene Monitoraggio replica sia progettato per un funzionamento efficiente, considerare gli aspetti seguenti:  
  
-   Se si dispone di una quantità elevata di pubblicazioni o sottoscrizioni, è consigliabile pianificare aggiornamenti automatici meno frequenti per l'interfaccia utente.  
  
-   Evitare di eseguire simultaneamente più istanze di Monitoraggio replica.  
  
-   Evitare di registrare una quantità elevata di server di distribuzione e di configurare Monitoraggio replica affinché si connetta automaticamente a tutti.  
  
## Vedere anche  
 [Eseguire processi di manutenzione della replica & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/administration/run-replication-maintenance-jobs-sql-server-management-studio.md)   
 [Monitoraggio della replica](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  