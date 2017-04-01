---
title: "Informazioni sul server di distribuzione, Agenti | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.monitor.Distributor.commonjobs..f1"
ms.assetid: 5d601a64-6af0-42f9-81b1-cf0087f1c50d
caps.latest.revision: 13
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 13
---
# Informazioni sul server di distribuzione, Agenti
  Il **agenti** scheda vengono visualizzate informazioni sugli agenti e i processi di manutenzione che sono associati server di pubblicazione e sottoscrizione.  
  
 Gli agenti che sono disponibili nel **agenti** scheda per un server di distribuzione nella vista server di distribuzione includa tutti gli agenti che sono disponibili nel **agenti** scheda per un server di pubblicazione. Tuttavia, il **agenti** scheda per un server di distribuzione nella vista server di distribuzione include inoltre un agente di distribuzione e un agente di Merge.  
  
 Per ulteriori informazioni su Snapshot, agente di lettura Log e gli agenti di lettura coda e processi di manutenzione, vedere [agenti, le informazioni sull'editore](../../relational-databases/replication/publisher-information-agents.md). Si noti che quando si visualizzano informazioni sull'agente nel **agenti** scheda per un server di distribuzione, le informazioni sull'editore è presente per gli agenti Snapshot e di lettura Log. Tuttavia, nel **agenti** scheda per un server di distribuzione nella vista server di distribuzione, è inoltre possibile selezionare **agente di distribuzione** e **agente di Merge**.  
  
## Opzioni  
 Nelle sezioni seguenti sono descritti i dati visualizzati in questa scheda per l'agente del server di distribuzione e per quello di merge.  
  
### Agente del server di distribuzione  
 **Stato**  
 Stato dell'agente. Nell'elenco seguente vengono indicati i valori di stato possibili:  
  
-   Errore  
  
-   Riprova  
  
-   In esecuzione  
  
-   Non in esecuzione  
  
-   Mai avviato  
  
 **Server di pubblicazione**  
 Istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] del server di pubblicazione.  
  
 **Pubblicazione**  
 Nome della pubblicazione a cui è associato l'agente.  
  
 **Sottoscrizione**  
 Il nome della sottoscrizione, nel formato: [*SubscriberName*]. [*Database*].  
  
 **Tipo**  
 Tipo di replica: push, pull o anonima.  
  
 **Ultima ora inizio**  
 Ultima ora di avvio dell'agente.  
  
 **Durata**  
 Durata dell'esecuzione dell'agente. Il valore di durata rappresenta il tempo trascorso se l'agente è ancora in esecuzione e il tempo totale se l'agente è stato eseguito in precedenza.  
  
 **Ultima azione**  
 Ultima azione eseguita durante la più recente esecuzione dell'agente.  
  
 **Frequenza recapito**  
 Frequenza, in comandi al secondo, con cui viene eseguito il commit dei comandi di inizializzazione nel database di distribuzione durante la più recente esecuzione dell'agente.  
  
 **Latenza**  
 Tempo, espresso in secondi, trascorso tra il commit della modifica più recente nel database di pubblicazione e il commit del comando corrispondente nel database di distribuzione.  
  
 **#Trans**  
 Numero di transazioni di cui è stato eseguito il commit nel database di distribuzione durante la più recente esecuzione dell'agente.  
  
 **#Comandi recapitati**  
 Numero di comandi di cui è stato eseguito il commit nel database di distribuzione durante la più recente esecuzione dell'agente. Un comando è equivalente a una modifica dei dati, ad esempio un aggiornamento.  
  
 **Microsec. #Comandi recapitati**  
 Numero medio di comandi per transazione durante la più recente esecuzione dell'agente.  
  
### Agente di merge  
 **Stato**  
 Stato dell'agente. Nell'elenco seguente vengono indicati i valori di stato possibili:  
  
-   Errore  
  
-   Riprova  
  
-   In esecuzione  
  
-   Non in esecuzione  
  
-   Mai avviato  
  
 **Server di pubblicazione**  
 Istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] del server di pubblicazione.  
  
 **Pubblicazione**  
 Nome della pubblicazione a cui è associato l'agente.  
  
 **Sottoscrizione**  
 Il nome della sottoscrizione, nel formato: [*SubscriberName*]. [*Database*].  
  
 **Tipo**  
 Tipo di replica: push, pull o anonima.  
  
 **Ultima ora inizio**  
 Ultima ora di avvio dell'agente.  
  
 **Durata**  
 Durata dell'esecuzione dell'agente. Il valore di durata rappresenta il tempo trascorso se l'agente è ancora in esecuzione e il tempo totale se l'agente è stato eseguito in precedenza.  
  
 **Ultima azione**  
 Ultima azione eseguita durante la più recente esecuzione dell'agente.  
  
 **Frequenza recapito**  
 Frequenza, in comandi al secondo, con cui viene eseguito il commit delle modifiche nel database di distribuzione.  
  
 **Inserimenti del server di pubblicazione**  
 Numero di comandi INSERT applicati nel server di pubblicazione.  
  
 **Aggiornamenti del server di pubblicazione**  
 Numero di comandi UPDATE applicati nel server di pubblicazione.  
  
 **Eliminazioni del server di pubblicazione**  
 Numero di comandi DELETE applicati nel server di pubblicazione.  
  
 **Conflitti del server di pubblicazione**  
 Numero di conflitti che si verificano nel server di pubblicazione durante il processo di merge.  
  
 **Inserimenti del Sottoscrittore**  
 Numero di comandi INSERT applicati nel Sottoscrittore.  
  
 **Aggiornamenti del Sottoscrittore**  
 Numero di comandi UPDATE applicati nel Sottoscrittore.  
  
 **Eliminazioni del Sottoscrittore**  
 Numero di comandi DELETE applicati nel Sottoscrittore.  
  
 **Conflitti del Sottoscrittore**  
 Numero di conflitti che si verificano nel Sottoscrittore durante il processo di merge.  
  
## Vedere anche  
 [Avvio di Monitoraggio replica](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Consente di visualizzare informazioni ed eseguire attività per un server di pubblicazione & #40; Monitoraggio replica & #41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publisher-replication-monitor.md)   
 [Consente di visualizzare informazioni ed eseguire attività relative agli agenti associati a una pubblicazione & #40; Monitoraggio replica & #41;](../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md)   
 [Monitoraggio della replica](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  