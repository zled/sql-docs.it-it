---
title: "Informazioni sulla pubblicazione, Tutte le sottoscrizioni (Pubblicazione di tipo merge) | Microsoft Docs"
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
  - "sql13.rep.monitor.publicationinfo.allsubscriptions.merge.f1"
ms.assetid: 0f4fa946-a0d9-4d3b-b90b-53503c40fba2
caps.latest.revision: 28
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 28
---
# Informazioni sulla pubblicazione, Tutte le sottoscrizioni (Pubblicazione di tipo merge)
  Il **tutte le sottoscrizioni** scheda vengono visualizzate informazioni su tutte le sottoscrizioni per la pubblicazione di tipo merge selezionata.  
  
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
 Stato di ogni sottoscrizione, determinato dallo stato dell'agente di merge.  
  
 Per impostazione predefinita, la griglia contenente le informazioni di sottoscrizione verrà ordinata i **stato** colonna (e quindi vengono ordinati il **prestazioni** colonna per le sottoscrizioni con lo stesso stato). Nell'elenco seguente vengono indicati i valori di stato possibili e l'ordinamento di tali valori, ad esempio gli errori vengono sempre visualizzati nella parte superiore della griglia.  
  
-   Errore  
  
-   Prestazioni critiche (solo [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive).  
  
-   Merge con esecuzione prolungata (solo [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive)  
  
-   Scadenza imminente/Scaduta (solo [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive)  
  
-   Sottoscrizione non inizializzata (solo [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive)  
  
-   Ripetizione comando non riuscito  
  
-   Sincronizzazione in corso  
  
-   Non in sincronizzazione  
  
 L'ordinamento determina inoltre il valore da visualizzare quando per una particolare sottoscrizione sono disponibili più stati. Ad esempio, se per una sottoscrizione sono presenti errori e la scadenza della sottoscrizione è imminente, nella colonna **Stato** viene visualizzato il valore **Errore**.  
  
 I valori di stato **prestazioni critiche**, **merge con esecuzione prolungata**, **scadenza imminente/scaduta**, e **sottoscrizione non inizializzata** sono avvisi. Quando viene visualizzato un avviso, il **stato** colonna viene visualizzato anche se la sincronizzazione di un agente. Ad esempio, lo stato potrebbe essere **sincronizzazione in corso, prestazioni critiche**.  
  
 I valori di stato **scadenza imminente/scaduta** e **merge con esecuzione prolungata** possono essere visualizzati solo se le soglie sono impostate. Il valore di stato **prestazioni critiche** può essere visualizzato solo dopo cinque sincronizzazioni di sottoscrizioni con lo stesso tipo di connessione (remota o LAN). Per informazioni sull'impostazione delle soglie e le misurazioni delle prestazioni, vedere [monitoraggio delle prestazioni con Monitoraggio replica](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md) e [impostare soglie e avvisi in Monitoraggio replica](../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
 **Sottoscrizione**  
 Il nome di ogni sottoscrizione, nel formato:*SubscriberName: SubscriptionDatabaseName*.  
  
 **Nome descrittivo**  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive. Descrizione di ogni sottoscrizione. La descrizione viene inserita nel **le proprietà della sottoscrizione** la finestra di dialogo o specificato con il **@description** parametro [sp_addmergesubscription](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md) o [sp_addmergepullsubscription](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md). Gli utenti utilizzano spesso la descrizione come "nome descrittivo" o come nome alternativo per la sottoscrizione.  
  
 **Prestazioni**  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive. Valutazione delle prestazioni per ogni sottoscrizione, basata sulle misurazioni più recenti della frequenza di recapito rilevate da Monitoraggio replica. La valutazione è determinata dal confronto tra le prestazioni delle singole sottoscrizioni e le prestazioni medie passate delle sottoscrizioni della pubblicazione che utilizzano lo stesso tipo di connessione (remota o LAN). In Monitoraggio replica viene visualizzato un valore dopo cinque sincronizzazioni con 50 o più modifiche eseguite con lo stesso tipo di connessione. Se sono state eseguite meno di 5 sincronizzazioni con almeno 50 modifiche oppure durante la sincronizzazione più recente sono state apportate meno di 50 modifiche, la colonna è vuota.  
  
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
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive. Tipo di connessione tra il Sottoscrittore e il server di pubblicazione. I valori possibili sono **LAN**, **remote**, e **Internet**. Il **Internet** valore viene visualizzato se la sottoscrizione utilizza sincronizzazione Web.  
  
## Vedere anche  
 [Avvio di Monitoraggio replica](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Consente di visualizzare informazioni ed eseguire attività per una sottoscrizione & #40; Monitoraggio replica & #41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)   
 [Consente di visualizzare informazioni ed eseguire attività relative agli agenti associati a una sottoscrizione & #40; Monitoraggio replica & #41;](../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md)   
 [Monitoraggio della replica](../../relational-databases/replication/monitor/monitoring-replication-overview.md)   
 [Sincronizzazione Web per la replica di tipo merge](../../relational-databases/replication/web-synchronization-for-merge-replication.md)  
  
  