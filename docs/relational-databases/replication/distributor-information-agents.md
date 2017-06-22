---
title: Informazioni sul database di distribuzione, Agenti | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.monitor.Distributor.commonjobs..f1
ms.assetid: 5d601a64-6af0-42f9-81b1-cf0087f1c50d
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5b1db16b9faf24e2255857203ac4a685d5326ca3
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="distributor-information-agents"></a>Informazioni sul server di distribuzione, Agenti
  Nella scheda **Agenti** vengono visualizzate le informazioni sugli agenti e sui processi di manutenzione associati al server di pubblicazione e al Sottoscrittore.  
  
 Tra gli agenti disponibili nella scheda **Agenti** per un server di distribuzione nella vista Server di distribuzione sono inclusi tutti gli agenti disponibili nella scheda **Agenti** per un server di pubblicazione. Tuttavia, in tale scheda **** sono inclusi anche un agente del server di distribuzione e un agente di merge.  
  
 Per ulteriori informazioni sugli agenti snapshot, di lettura log, di lettura coda nonché sui processi di manutenzione, vedere [Publisher Information, Agents](../../relational-databases/replication/publisher-information-agents.md). Si noti che quando si visualizzano le informazioni sugli agenti nella scheda **Agenti** per un server di distribuzione, le informazioni sul server di pubblicazione sono disponibili per gli agenti snapshot e di lettura log. Tuttavia, nella scheda **Agenti** per un server di distribuzione nella vista Server di distribuzione è possibile selezionare anche **Agente del server di distribuzione** e **Agente di merge**.  
  
## <a name="options"></a>Opzioni  
 Nelle sezioni seguenti sono descritti i dati visualizzati in questa scheda per l'agente del server di distribuzione e per quello di merge.  
  
### <a name="distributor-agent"></a>Agente del server di distribuzione  
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
 Nome della sottoscrizione nel formato [*SubscriberName*].[*Database*].  
  
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
  
 **N. transazioni**  
 Numero di transazioni di cui è stato eseguito il commit nel database di distribuzione durante la più recente esecuzione dell'agente.  
  
 **N. comandi**  
 Numero di comandi di cui è stato eseguito il commit nel database di distribuzione durante la più recente esecuzione dell'agente. Un comando è equivalente a una modifica dei dati, ad esempio un aggiornamento.  
  
 **Media n. comandi**  
 Numero medio di comandi per transazione durante la più recente esecuzione dell'agente.  
  
### <a name="merge-agent"></a>Agente di merge  
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
 Nome della sottoscrizione nel formato [*SubscriberName*].[*Database*].  
  
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
  
## <a name="see-also"></a>Vedere anche  
 [Avviare Monitoraggio replica](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Visualizzare le informazioni ed eseguire attività relative a un server di pubblicazione &#40;Monitoraggio replica&#41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publisher-replication-monitor.md)   
 [Visualizzare le informazioni ed eseguire attività relative agli agenti associati a una pubblicazione &#40;Monitoraggio replica&#41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-publication-agents.md)   
 [Monitoraggio della replica](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
