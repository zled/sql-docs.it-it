---
title: "Informazioni sul server di pubblicazione, Elenco verifica sottoscrizioni (Pubblicazione snapshot, SQL Server 2005 e versioni successive) | Microsoft Docs"
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
  - "sql13.rep.monitor.publisherinfo.subscriptionssummary.snapshot.f1"
ms.assetid: 2ebeee62-7f54-4c77-9d37-15708bc5cc23
caps.latest.revision: 32
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Informazioni sul server di pubblicazione, Elenco verifica sottoscrizioni (Pubblicazione snapshot, SQL Server 2005 e versioni successive)
  Il **elenco verifica sottoscrizioni** scheda è disponibile per i server di distribuzione in esecuzione [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive; consente di visualizzare informazioni sulle sottoscrizioni da tutte le pubblicazioni disponibili nel server di pubblicazione selezionato. È possibile filtrare l'elenco delle sottoscrizioni per visualizzare errori, avvisi ed eventuali sottoscrizioni con prestazioni scarse. Questa scheda fornisce un'unica posizione per un amministratore di monitorare tutte le attività di replica nel server di pubblicazione: Monitoraggio replica vengono visualizzate tutte le sottoscrizioni che richiedono attenzione, in base al tipo di replica selezionato e l'opzione selezionata nel **Mostra** casella di riepilogo a discesa. Poiché gli elementi visualizzati in questa scheda si basano sullo stato e le prestazioni correnti, le sottoscrizioni vengono visualizzate in questa pagina solo se queste corrispondono all'opzione selezionata nella casella di riepilogo **Mostra** .  
  
## Opzioni  
 Per ulteriori informazioni su una sottoscrizione e sulle attività correlate, fare clic con il pulsante destro del mouse sulla riga della sottoscrizione e quindi scegliere un'opzione dal menu di scelta rapida. Per modificare la modalità di visualizzazione dei dati nella griglia, fare clic con il pulsante destro del mouse sulla griglia, quindi scegliere una delle opzioni seguenti:  
  
-   **Ordinamento**: consente di ordinare una o più colonne nella finestra di dialogo **Ordina colonne** .  
  
-   **Seleziona colonne da visualizzare**: consente di selezionare le colonne da visualizzare e l'ordine di visualizzazione nella finestra di dialogo **Seleziona colonne** .  
  
-   **Filtro**: consente di filtrare le righe nella griglia in base a valori di colonna nella finestra di dialogo **Impostazioni filtro** .  
  
-   **Cancella filtro**: consente di cancellare qualsiasi impostazione di filtro per la griglia.  
  
 Le impostazioni di filtro sono specifiche di ogni griglia. La selezione e l'ordinamento delle colonne vengono applicati a tutte le griglie dello stesso tipo, ad esempio la griglia delle pubblicazioni per ogni server di pubblicazione.  
  
 **Mostra sottoscrizioni snapshot**  
 Consente di selezionare il tipo di sottoscrizioni (transazionali, snapshot o merge) da visualizzare per il server di distribuzione selezionato.  
  
 **Mostra**  
 Consente di selezionare gli stati della sottoscrizione da visualizzare per il tipo di sottoscrizione selezionato. Ad esempio, è possibile scegliere di visualizzare solo le sottoscrizioni con errori.  
  
 **Stato**  
 Stato di ogni sottoscrizione determinato dallo stato dell'agente snapshot o dell'agente di distribuzione. Viene visualizzato lo stato con priorità più alta.  
  
 Per impostazione predefinita, la griglia contenente le informazioni di sottoscrizione verrà ordinata i **stato** colonna. Nell'elenco seguente vengono indicati i valori di stato possibili e l'ordinamento di tali valori, ad esempio gli errori vengono sempre visualizzati nella parte superiore della griglia.  
  
-   Errore  
  
-   Scadenza imminente/Scaduta  
  
-   Sottoscrizione non inizializzata  
  
-   Ripetizione comando non riuscito  
  
-   Sincronizzazione in corso  
  
-   Non in sincronizzazione  
  
 L'ordinamento determina inoltre il valore da visualizzare quando per una particolare sottoscrizione sono disponibili più stati. Ad esempio, se per una sottoscrizione sono presenti errori e la scadenza della sottoscrizione è imminente, nella colonna **Stato** viene visualizzato il valore **Errore**.  
  
 I valori di stato **scadenza imminente/scaduta** e **sottoscrizione non inizializzata** sono avvisi. Quando viene visualizzato un avviso, nella colonna **Stato** viene inoltre visualizzato se è in esecuzione un agente. Ad esempio, lo stato potrebbe essere **in esecuzione, scadenza imminente/scaduta**.  
  
 Il valore di stato **scadenza imminente/scaduta** viene visualizzata solo se è impostata una soglia. Per informazioni sull'impostazione delle soglie, vedere [impostare soglie e avvisi in Monitoraggio replica](../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
 **Sottoscrizione**  
 Il nome di ogni sottoscrizione, nel formato: *SubscriberName: SubscriptionDatabaseName*.  
  
 **Pubblicazione**  
 Il nome della pubblicazione con cui si sincronizza una sottoscrizione, nel formato: *PublicationDatabaseName: PublicationName*.  
  
 **Ultima sincronizzazione**  
 Data e ora dell'ultima esecuzione dell'agente di distribuzione. Se il processo di sincronizzazione è in corso, viene visualizzato **In corso** .  
  
## Vedere anche  
 [Avvio di Monitoraggio replica](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Consente di visualizzare informazioni ed eseguire attività per un server di pubblicazione & #40; Monitoraggio replica & #41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publisher-replication-monitor.md)   
 [Monitoraggio della replica](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  