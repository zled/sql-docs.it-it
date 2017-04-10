---
title: "Informazioni sulla pubblicazione, Avvisi (pubblicazione di tipo merge, SQL Server 2005 e versioni successive) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.monitor.publicationinfo.warningsandagents.merge.f1"
ms.assetid: 9bef3565-5f13-42ac-8723-ebe55b0c11e6
caps.latest.revision: 27
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 27
---
# Informazioni sulla pubblicazione, Avvisi (pubblicazione di tipo merge, SQL Server 2005 e versioni successive)
  La scheda **Avvisi** è disponibile per i server di distribuzione che eseguono [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive. La scheda **Avvisi** consente di eseguire le attività seguenti per la pubblicazione selezionata:  
  
-   Abilitazione di avvisi.  
  
-   Specificare valori soglia associati agli avvisi.  
  
-   Definire messaggi di avviso associati ad avvisi.  
  
## Avvisi, soglie e messaggi di avviso  
 Per impostazione predefinita, Monitoraggio replica visualizza avvisi per le sottoscrizioni non inizializzate, includendo lo stato **Sottoscrizione non inizializzata** come avviso nella colonna **Stato** delle pagine contenenti informazioni sulla sottoscrizione. Per le pubblicazioni di tipo merge è possibile specificare se le condizioni aggiuntive seguenti generano avvisi:  
  
-   Scadenza imminente della sottoscrizione.  
  
     Corrisponde all'opzione **Avvisa se una sottoscrizione scade entro la soglia**. Se la soglia specificata viene raggiunta o superata, lo stato della sottoscrizione viene visualizzato come **scadenza imminente/scaduta** (a meno che non debba essere visualizzato un problema con una priorità più alta).  
  
-   Superamento del tempo di sincronizzazione specificato.  
  
     Corrisponde alle opzioni **Avvisa se una lunghezza di tipo merge per le connessioni remote supera la soglia** e **Avvisa se una lunghezza di tipo merge per le connessioni LAN supera la soglia**. È possibile impostare entrambe le soglie, ma solo una delle due viene utilizzata durante una determinata sincronizzazione. L'agente di merge applica la soglia appropriata in base al tipo di connessione.  
  
     Se la soglia specificata viene raggiunta o superata, lo stato della sottoscrizione viene visualizzato come **merge con esecuzione prolungata** (a meno che non debba essere visualizzato un problema con una priorità più alta).  
  
-   Impossibilità di elaborare il numero di righe specificato in un determinato intervallo di tempo.  
  
     Corrisponde alle opzioni **Avvisa se righe unite al secondo per le connessioni remote è inferiore alla soglia** e **Avvisa se una lunghezza di tipo merge per le connessioni LAN supera la soglia**. È possibile impostare entrambe le soglie, ma solo una delle due viene utilizzata durante una determinata sincronizzazione. L'agente di merge applica la soglia appropriata in base al tipo di connessione.  
  
     Se la soglia specificata viene raggiunta o superata, lo stato della sottoscrizione viene visualizzato come **prestazioni critiche** (a meno che non debba essere visualizzato un problema con una priorità più alta).  
  
 Quando si abilita un avviso, è inoltre necessario impostare un valore soglia. Ad esempio, se si attiva l'avviso **Avvisa se una lunghezza di tipo merge per le connessioni LAN supera la soglia**, impostare la lunghezza massima consentita di tempo per una sincronizzazione di tipo merge.  
  
 Oltre a visualizzare un avviso in Monitoraggio replica, il raggiungimento di un valore soglia può inoltre attivare un messaggio di avviso. Gli avvisi vengono definiti facendo clic su **Configura avvisi** e specificando le informazioni appropriate nella finestra di dialogo **Configura avvisi di replica** .  
  
## Opzioni  
 **Abilitata**  
 Selezionare questa opzione per abilitare un avviso e specificare un valore soglia.  
  
 **Avviso**  
 Selezionare questa opzione per abilitare l'impostazione di avvisi per un determinato avviso di replica.  
  
 **Avviso**  
 Descrizione dell'avviso associato al valore soglia.  
  
 **Soglia**  
 Consente di specificare un valore per la soglia.  
  
 **Configura avvisi**  
 Selezionare una riga nella **avvisi** della griglia e fare clic su **Configura avvisi** per avviare il **Configura avvisi di replica** la finestra di dialogo. Tramite questa finestra di dialogo è possibile definire un avviso associato al valore soglia e all'avviso selezionati.  
  
 **Ignora modifiche**  
 Fare clic su questo pulsante per ignorare le eventuali modifiche apportate agli avvisi e alle soglie.  
  
> [!NOTE]  
>  Fare clic su **Ignora modifiche** non influisce sugli avvisi definiti nel **Configura avvisi di replica** la finestra di dialogo.  
  
 **Salva modifiche**  
 Fare clic su questo pulsante per salvare le eventuali modifiche apportate agli avvisi e alle soglie.  
  
## Vedere anche  
 [Avvio di Monitoraggio replica](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Consente di visualizzare informazioni ed eseguire attività per una pubblicazione & #40; Monitoraggio replica & #41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md)   
 [Monitoraggio delle prestazioni con Monitoraggio replica](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md)   
 [Monitoraggio della replica](../../relational-databases/replication/monitor/monitoring-replication-overview.md)   
 [Impostazione di valore soglia e avvisi in Monitoraggio replica](../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md)  
  
  