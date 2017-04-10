---
title: "Informazioni sul server di pubblicazione, Elenco verifica sottoscrizioni (Pubblicazione di tipo merge, SQL Server 2005 e versioni successive) | Microsoft Docs"
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
  - "sql13.rep.monitor.publisherinfo.subscriptionssummary.merge.f1"
ms.assetid: 4ec956bf-5cef-4377-a1d1-8c7f0107a6cb
caps.latest.revision: 32
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Informazioni sul server di pubblicazione, Elenco verifica sottoscrizioni (Pubblicazione di tipo merge, SQL Server 2005 e versioni successive)
  Il **elenco verifica sottoscrizioni** scheda è disponibile per i server di distribuzione in esecuzione [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive; consente di visualizzare informazioni sulle sottoscrizioni da tutte le pubblicazioni disponibili nel server di pubblicazione selezionato. È possibile filtrare l'elenco delle sottoscrizioni per visualizzare errori, avvisi ed eventuali sottoscrizioni con prestazioni scarse. Questa scheda fornisce un'unica posizione per un amministratore di monitorare tutte le attività di replica nel server di pubblicazione: Monitoraggio replica vengono visualizzate tutte le sottoscrizioni che richiedono attenzione, in base al tipo di replica selezionato e l'opzione selezionata nel **Mostra** casella di riepilogo a discesa. Poiché gli elementi visualizzati in questa scheda si basano sullo stato e le prestazioni correnti, le sottoscrizioni vengono visualizzate in questa pagina solo se queste corrispondono all'opzione selezionata nella casella di riepilogo **Mostra** .  
  
## Opzioni  
 Per ulteriori informazioni su una sottoscrizione e sulle attività correlate, fare clic con il pulsante destro del mouse sulla riga della sottoscrizione e quindi scegliere un'opzione dal menu di scelta rapida. Per modificare la modalità di visualizzazione dei dati nella griglia, fare clic con il pulsante destro del mouse sulla griglia, quindi scegliere una delle opzioni seguenti:  
  
-   **Ordinamento**: consente di ordinare una o più colonne nella finestra di dialogo **Ordina colonne** .  
  
-   **Seleziona colonne da visualizzare**: consente di selezionare le colonne da visualizzare e l'ordine di visualizzazione nella finestra di dialogo **Seleziona colonne** .  
  
-   **Filtro**: consente di filtrare le righe nella griglia in base a valori di colonna nella finestra di dialogo **Impostazioni filtro** .  
  
-   **Cancella filtro**: consente di cancellare qualsiasi impostazione di filtro per la griglia.  
  
 Le impostazioni di filtro sono specifiche di ogni griglia. La selezione e l'ordinamento delle colonne vengono applicati a tutte le griglie dello stesso tipo, ad esempio la griglia delle pubblicazioni per ogni server di pubblicazione.  
  
 **Mostra sottoscrizioni di tipo merge**  
 Consente di selezionare il tipo di sottoscrizioni (transazionali, snapshot o merge) da visualizzare per il server di distribuzione selezionato.  
  
 **Mostra**  
 Consente di selezionare gli stati della sottoscrizione da visualizzare per il tipo di sottoscrizione selezionato. Ad esempio, è possibile scegliere di visualizzare solo le sottoscrizioni con errori.  
  
 **Stato**  
 Stato di ogni sottoscrizione, determinato dallo stato dell'agente di merge.  
  
 Per impostazione predefinita, la griglia contenente le informazioni di sottoscrizione verrà ordinata i **stato** colonna (e quindi vengono ordinati il **prestazioni** colonna per le sottoscrizioni con lo stesso stato). Nell'elenco seguente vengono indicati i valori di stato possibili e l'ordinamento di tali valori, ad esempio gli errori vengono sempre visualizzati nella parte superiore della griglia.  
  
-   Errore  
  
-   Prestazioni critiche  
  
-   Merge con esecuzione prolungata  
  
-   Scadenza imminente/Scaduta  
  
-   Sottoscrizione non inizializzata  
  
-   Ripetizione comando non riuscito  
  
-   Sincronizzazione in corso  
  
-   Non in sincronizzazione  
  
 L'ordinamento determina inoltre il valore da visualizzare quando per una particolare sottoscrizione sono disponibili più stati. Ad esempio, se per una sottoscrizione sono presenti errori e la scadenza della sottoscrizione è imminente, nella colonna **Stato** viene visualizzato il valore **Errore**.  
  
 I valori di stato **prestazioni critiche**, **merge con esecuzione prolungata**, **scadenza imminente/scaduta**, e **sottoscrizione non inizializzata** sono avvisi. Quando viene visualizzato un avviso, il **stato** colonna viene visualizzato anche se la sincronizzazione di un agente. Ad esempio, lo stato potrebbe essere **sincronizzazione in corso, prestazioni critiche**.  
  
 I valori di stato **scadenza imminente/scaduta** e **merge con esecuzione prolungata** possono essere visualizzati solo se le soglie sono impostate. Il valore di stato **prestazioni critiche** può essere visualizzato solo dopo cinque sincronizzazioni di sottoscrizioni con lo stesso tipo di connessione (remota o LAN). Per informazioni sull'impostazione delle soglie e le misurazioni delle prestazioni, vedere [monitoraggio delle prestazioni con Monitoraggio replica](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md) e [impostare soglie e avvisi in Monitoraggio replica](../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
 **Sottoscrizione**  
 Il nome di ogni sottoscrizione, nel formato:*SubscriberName: SubscriptionDatabaseName*.  
  
 **Nome descrittivo**  
 Descrizione di ogni sottoscrizione. La descrizione viene inserita nel **le proprietà della sottoscrizione** la finestra di dialogo o specificato con il **@description** parametro [sp_addmergesubscription](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md) o [sp_addmergepullsubscription](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md). Gli utenti utilizzano spesso la descrizione come "nome descrittivo" o come nome alternativo per la sottoscrizione.  
  
 **Pubblicazione**  
 Il nome della pubblicazione con cui si sincronizza una sottoscrizione, nel formato: *PublicationDatabaseName: PublicationName*.  
  
 **Prestazioni**  
 Valutazione delle prestazioni per ogni sottoscrizione, basata sulle misurazioni più recenti della frequenza di recapito rilevate da Monitoraggio replica. La valutazione è determinata dal confronto tra le prestazioni delle singole sottoscrizioni e le prestazioni medie passate delle sottoscrizioni della pubblicazione che utilizzano lo stesso tipo di connessione (remota o LAN). In Monitoraggio replica viene visualizzato un valore dopo cinque sincronizzazioni con 50 o più modifiche eseguite con lo stesso tipo di connessione. Se sono state eseguite meno di 5 sincronizzazioni con almeno 50 modifiche oppure durante la sincronizzazione più recente sono state apportate meno di 50 modifiche, la colonna è vuota.  
  
> [!NOTE]  
>  Le prestazioni sono basate sul tipo di connessione nella **connessione** colonna; pertanto è possibile che una sottoscrizione con una frequenza di recapito inferiore visualizzi una valutazione delle prestazioni migliore rispetto a un'altra sottoscrizione se la prima sottoscrizione viene sincronizzata tramite una connessione più lenta.  
  
 La valutazione delle prestazioni può corrispondere a uno dei valori seguenti:  
  
-   Eccellenti  
  
-   Buone  
  
-   Discrete  
  
-   Scarse  
  
 Per ulteriori informazioni su come vengono definite le valutazioni delle prestazioni e impostazione delle soglie di prestazioni, vedere [monitoraggio delle prestazioni con Monitoraggio replica](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md).  
  
 **Frequenza recapito**  
 Numero di righe elaborate al secondo dall'agente di merge.  
  
 **Ultima sincronizzazione**  
 Ora dell'ultima esecuzione dell'agente di merge. Durante tale sincronizzazione le modifiche potrebbero essere state elaborate o meno. Se la sincronizzazione è in corso viene visualizzato un valore di percentuale di completamento.  
  
 **Durata**  
 Tempo di esecuzione dell'agente di merge durante l'ultima sincronizzazione. Il valore di durata rappresenta il tempo trascorso se l'agente di merge è ancora in sincronizzazione e la durata totale se l'agente di merge ha eseguito la sincronizzazione in precedenza.  
  
 **Connessione**  
 Tipo di connessione tra il Sottoscrittore e il server di pubblicazione. I valori possibili sono **LAN**, **remote**, e **Internet**. Il **Internet** valore viene visualizzato se la sottoscrizione utilizza sincronizzazione Web.  
  
## Vedere anche  
 [Avvio di Monitoraggio replica](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Consente di visualizzare informazioni ed eseguire attività per un server di pubblicazione & #40; Monitoraggio replica & #41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publisher-replication-monitor.md)   
 [Monitoraggio della replica](../../relational-databases/replication/monitor/monitoring-replication-overview.md)   
 [Sincronizzazione Web per la replica di tipo merge](../../relational-databases/replication/web-synchronization-for-merge-replication.md)  
  
  