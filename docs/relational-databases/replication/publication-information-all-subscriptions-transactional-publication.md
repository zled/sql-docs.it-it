---
title: "Informazioni sulla pubblicazione, Tutte le sottoscrizioni (Pubblicazione transazionale) | Microsoft Docs"
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
  - "sql13.rep.monitor.publicationinfo.allsubscriptions.tran.f1"
ms.assetid: 7073350c-f667-4f70-88e9-152c9a1b08dd
caps.latest.revision: 30
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 30
---
# Informazioni sulla pubblicazione, Tutte le sottoscrizioni (Pubblicazione transazionale)
  La scheda **Tutte le sottoscrizioni** visualizza informazioni su tutte le sottoscrizioni della pubblicazione transazionale selezionata.  
  
## Opzioni  
 Per ulteriori informazioni su una sottoscrizione e sulle attività correlate, fare clic con il pulsante destro del mouse sulla riga della sottoscrizione e quindi scegliere un'opzione dal menu di scelta rapida. Per modificare la modalità di visualizzazione dei dati nella griglia, fare clic con il pulsante destro del mouse sulla griglia, quindi scegliere una delle opzioni seguenti:  
  
-   **Ordinamento**: consente di ordinare una o più colonne nella finestra di dialogo **Ordina colonne** .  
  
-   **Seleziona colonne da visualizzare**: consente di selezionare le colonne da visualizzare e l'ordine di visualizzazione nella finestra di dialogo **Seleziona colonne** .  
  
-   **Filtro**: consente di filtrare le righe nella griglia in base a valori di colonna nella finestra di dialogo **Impostazioni filtro** .  
  
-   **Cancella filtro**: consente di cancellare qualsiasi impostazione di filtro per la griglia.  
  
 Le impostazioni di filtro sono specifiche di ogni griglia. La selezione e l'ordinamento delle colonne vengono applicati a tutte le griglie dello stesso tipo, ad esempio la griglia delle pubblicazioni per ogni server di pubblicazione.  
  
 **Mostra**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive. Consente di selezionare gli stati della sottoscrizione da visualizzare per il tipo di sottoscrizione selezionato. Ad esempio, è possibile scegliere di visualizzare solo le sottoscrizioni con errori.  
  
 **Stato**  
 Stato di ogni sottoscrizione determinato dallo stato dell'agente di distribuzione o dell'agente di lettura log. Viene visualizzato lo stato con priorità più alta. Lo stato può inoltre essere determinato dall'agente di lettura coda nel caso in cui vengano utilizzate sottoscrizioni ad aggiornamento in coda.  
  
 Per impostazione predefinita, la griglia contenente le informazioni di sottoscrizione verrà ordinata i **stato** colonna (e quindi vengono ordinati il **prestazioni** colonna per le sottoscrizioni con lo stesso stato). Nell'elenco seguente vengono indicati i valori di stato possibili e l'ordinamento di tali valori, ad esempio gli errori vengono sempre visualizzati nella parte superiore della griglia.  
  
-   Errore  
  
-   Prestazioni critiche (solo [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive).  
  
-   Scadenza imminente/Scaduta (solo [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive)  
  
-   Sottoscrizione non inizializzata (solo [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive)  
  
-   Ripetizione comando non riuscito  
  
-   Non in esecuzione  
  
-   In esecuzione  
  
 L'ordinamento determina inoltre il valore da visualizzare quando per una particolare sottoscrizione sono disponibili più stati. Ad esempio, se per una sottoscrizione sono presenti errori e la scadenza della sottoscrizione è imminente, nella colonna **Stato** viene visualizzato il valore **Errore**.  
  
 I valori di stato **prestazioni critiche**, **scadenza imminente/scaduta**, e **sottoscrizione non inizializzata** sono avvisi. Quando viene visualizzato un avviso, nella colonna **Stato** viene inoltre visualizzato se è in esecuzione un agente. Ad esempio, lo stato potrebbe essere **In esecuzione, Prestazioni critiche**.  
  
 I valori di stato **prestazioni critiche** e **scadenza imminente/scaduta** vengono visualizzate solo se le soglie sono impostate. Per informazioni sull'impostazione delle soglie e le misurazioni delle prestazioni, vedere [monitoraggio delle prestazioni con Monitoraggio replica](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md) e [impostare soglie e avvisi in Monitoraggio replica](../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
 **Sottoscrizione**  
 Il nome di ogni sottoscrizione, nel formato: *SubscriberName: SubscriptionDatabaseName*.  
  
 **Prestazioni**  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive. La valutazione delle prestazioni per ogni sottoscrizione è basata sulle misure più recenti rilevate da Monitoraggio replica e non riflette le prestazioni cronologiche. Le prestazioni vengono misurate per le sottoscrizioni delle pubblicazioni per le quali sono state definite soglie di prestazione. Se le soglie di prestazione non sono state definite per una pubblicazione, in questa colonna viene visualizzato **Non attivato**. La valutazione delle prestazioni può corrispondere a uno dei valori seguenti:  
  
-   Eccellenti  
  
-   Buone  
  
-   Discrete  
  
-   Scarse  
  
-   Critico  
  
 Se le prestazioni sono critiche, nella colonna **Stato** viene visualizzato **Prestazioni critiche** . Per ulteriori informazioni su come vengono definite le valutazioni delle prestazioni e impostazione delle soglie di prestazioni, vedere [monitoraggio delle prestazioni con Monitoraggio replica](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md).  
  
 **Latenza**  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive. Tempo medio che intercorre tra l'esecuzione del commit di una transazione nel server di pubblicazione e l'esecuzione del commit della transazione corrispondente nel Sottoscrittore. La latenza visualizzata è basata sulle misure più recenti rilevate da Monitoraggio replica. Per ulteriori informazioni sulla misurazione della latenza, vedere [misurazione latenza e convalidare le connessioni per la replica transazionale](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md).  
  
## Vedere anche  
 [Avvio di Monitoraggio replica](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Consente di visualizzare informazioni ed eseguire attività per una sottoscrizione & #40; Monitoraggio replica & #41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)   
 [Consente di visualizzare informazioni ed eseguire attività relative agli agenti associati a una sottoscrizione & #40; Monitoraggio replica & #41;](../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md)   
 [Monitoraggio della replica](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  