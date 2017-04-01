---
title: "Informazioni sulla pubblicazione, Avvisi (pubblicazione snapshot, SQL Server 2005 e versioni successive) | Microsoft Docs"
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
  - "sql13.rep.monitor.publicationinfo.warningsandagents.snapshot.f1"
ms.assetid: 7aa2eb52-b6b7-4dd3-8483-8ef00d9f0435
caps.latest.revision: 26
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 26
---
# Informazioni sulla pubblicazione, Avvisi (pubblicazione snapshot, SQL Server 2005 e versioni successive)
  La scheda **Avvisi** è disponibile per i server di distribuzione che eseguono [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive. La scheda **Avvisi** consente di eseguire le attività seguenti per la pubblicazione selezionata:  
  
-   Abilitazione di avvisi.  
  
-   Specificare valori soglia associati agli avvisi.  
  
-   Definire messaggi di avviso associati ad avvisi.  
  
## Avvisi, soglie e messaggi di avviso  
 Per impostazione predefinita, Monitoraggio replica visualizza avvisi per le sottoscrizioni non inizializzate, includendo lo stato **Sottoscrizione non inizializzata** come avviso nella colonna **Stato** delle pagine contenenti informazioni sulla sottoscrizione. Per le pubblicazioni snapshot, è inoltre possibile specificare che l'imminente scadenza della sottoscrizione venga notificata tramite un avviso impostando l'opzione **Avvisa se una sottoscrizione scade entro il valore soglia**. Se la soglia specificata viene raggiunta o superata, lo stato della sottoscrizione viene visualizzato come **scadenza imminente/scaduta** (a meno che non debba essere visualizzato un problema con una priorità più alta).  
  
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
 [Monitoraggio della replica](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  