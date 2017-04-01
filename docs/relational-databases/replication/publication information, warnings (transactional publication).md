---
title: "Informazioni sulla pubblicazione, Avvisi (pubblicazione transazionale, SQL Server 2005 e versioni successive) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.monitor.publicationinfo.warningsandagents.tran.f1"
ms.assetid: 4d4baf1d-d0a1-4d09-bec7-137811f43f09
caps.latest.revision: 30
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Informazioni sulla pubblicazione, Avvisi (pubblicazione transazionale, SQL Server 2005 e versioni successive)
  La scheda **Avvisi** è disponibile per i server di distribuzione che eseguono [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive. La scheda **Avvisi** consente di eseguire le attività seguenti per la pubblicazione selezionata:  
  
-   Consentire la visualizzazione degli avvisi in Monitoraggio replica.  
  
-   Specificare valori soglia associati agli avvisi.  
  
-   Definire messaggi di avviso associati ad avvisi.  
  
## Avvisi, soglie e messaggi di avviso  
 Per impostazione predefinita, Monitoraggio replica visualizza avvisi per le sottoscrizioni non inizializzate, includendo lo stato **Sottoscrizione non inizializzata** come avviso nella colonna **Stato** delle pagine contenenti informazioni sulla sottoscrizione. Per le pubblicazioni transazionali è possibile specificare se le condizioni aggiuntive seguenti generano avvisi:  
  
-   Scadenza imminente della sottoscrizione.  
  
     Corrisponde all'opzione **Avvisa se una sottoscrizione scade entro la soglia**. Se la soglia specificata viene raggiunta o superata, lo stato della sottoscrizione viene visualizzato come **scadenza imminente/scaduta** (a meno che non debba essere visualizzato un problema con una priorità più alta).  
  
-   Superamento della latenza specificata. Indica la quantità di tempo che intercorre tra l'esecuzione del commit di una transazione nel server di pubblicazione e l'esecuzione del commit della transazione corrispondente nel Sottoscrittore.  
  
     Corrisponde all'opzione **Avvisa se la latenza supera la soglia**. Se la soglia specificata viene raggiunta o superata, lo stato della sottoscrizione viene visualizzato come **prestazioni critiche** (a meno che non debba essere visualizzato un problema con una priorità più alta). La soglia viene inoltre utilizzata per fornire una valutazione delle prestazioni, che viene visualizzata nel **prestazioni** colonna delle pagine che contengono informazioni sulla sottoscrizione. La valutazione delle prestazioni può corrispondere a uno dei valori seguenti:  
  
    -   Eccellenti  
  
    -   Buone  
  
    -   Discrete  
  
    -   Scarse  
  
    -   Critico  
  
 Quando si abilita un avviso, è inoltre necessario impostare un valore soglia. Ad esempio, se si attiva l'avviso **Avvisa se la latenza supera la soglia**, selezionare la quantità di tempo consentita tra una transazione viene eseguito il commit nel server di pubblicazione e il commit della transazione nel Sottoscrittore.  
  
 Oltre a visualizzare un avviso in Monitoraggio replica, il raggiungimento di un valore soglia può inoltre attivare un messaggio di avviso. Gli avvisi vengono definiti facendo clic su **Configura avvisi** e specificando le informazioni appropriate nella finestra di dialogo **Configura avvisi di replica** .  
  
## Opzioni  
 **Abilitata**  
 Selezionare questa opzione per abilitare un avviso e specificare un valore soglia.  
  
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
  
  