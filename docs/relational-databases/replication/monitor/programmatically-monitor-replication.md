---
title: "Monitoraggio della replica a livello di programmazione | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "sp_replmonitorhelppublisher"
  - "sp_replmonitorhelpmergesessiondetail"
  - "monitoring performance [SQL Server replication], publication status"
  - "sp_replmonitorhelpmergesession"
  - "sp_replmonitorhelppublicationthresholds"
  - "monitoring performance [SQL Server replication], subscription status"
  - "monitoring performance [SQL Server replication], Transact-SQL programming"
  - "sp_replmonitorsubscriptionpendingcmds"
  - "sp_replmonitorchangepublicationthreshold"
  - "transactional replication, monitoring"
  - "sp_replmonitorhelppublication"
  - "sp_replmonitorhelpsubscription"
  - "monitoring performance [SQL Server replication], thresholds and warnings"
  - "merge replication monitoring [SQL Server replication]"
  - "replica snapshot [SQL Server], monitoraggio"
ms.assetid: e8bf8850-8da5-4a4f-a399-64232b4e476d
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 34
---
# Monitoraggio della replica a livello di programmazione
  Monitoraggio replica è uno strumento grafico che consente di monitorare una topologia di replica. È possibile accedere agli stessi dati di monitoraggio a livello di programmazione utilizzando le stored procedure di replica [!INCLUDE[tsql](../../../includes/tsql-md.md)] o gli oggetti RMO (Replication Management Objects). Tali oggetti consentono di programmare le attività seguenti:  
  
-   Monitoraggio dello stato dei server di pubblicazione, delle pubblicazioni e delle sottoscrizioni.  
  
-   Monitoraggio delle sessioni dell'agente di merge in uno o più Sottoscrittori.  
  
-   Monitoraggio dei comandi transazionali in attesa di essere applicati a uno o più Sottoscrittori.  
  
-   Definizione delle metriche di soglia che determinano la necessità di un intervento per una pubblicazione.  
  
-   Monitoraggio dello stato dei token di traccia.  
  
 **Contenuto dell'argomento:**  
  
 [Transact-SQL](#Tsql)  
  
 [Oggetti RMO (Replication Management Objects)](#RMO)  
  
##  <a name="Tsql"></a> Transact-SQL  
  
#### Per monitorare i server di pubblicazione, le pubblicazioni e le sottoscrizioni dal database di distribuzione  
  
1.  Nel server di distribuzione nel database di distribuzione, eseguire [sp_replmonitorhelppublisher](../../../relational-databases/system-stored-procedures/sp-replmonitorhelppublisher-transact-sql.md). Vengono restituite le informazioni di monitoraggio per tutti i server di pubblicazione che utilizzano il server di distribuzione. Per limitare il set di risultati a un solo server di pubblicazione, specificare **@publisher**.  
  
2.  Nel server di distribuzione nel database di distribuzione, eseguire [sp_replmonitorhelppublication](../../../relational-databases/system-stored-procedures/sp-replmonitorhelppublication-transact-sql.md). Vengono restituite le informazioni di monitoraggio per tutte le pubblicazioni che utilizzano il server di distribuzione. Per limitare il set di risultati per un singolo server di pubblicazione, pubblicazione o database pubblicato, specificare **@publisher**, **@publication**, o **@publisher_db**, rispettivamente.  
  
3.  Nel server di distribuzione nel database di distribuzione, eseguire [sp_replmonitorhelpsubscription](../../../relational-databases/system-stored-procedures/sp-replmonitorhelpsubscription-transact-sql.md). Vengono restituite le informazioni di monitoraggio per tutte le sottoscrizioni che utilizzano il server di distribuzione. Per limitare il set di risultati a sottoscrizioni appartenenti a un singolo server di pubblicazione, la pubblicazione, o un database pubblicato, specificare **@publisher**, **@publication**, o **@publisher_db**, rispettivamente.  
  
#### Per monitorare i comandi transazionali in attesa di essere applicati al Sottoscrittore  
  
1.  Nel server di distribuzione nel database di distribuzione, eseguire [sp_replmonitorsubscriptionpendingcmds](../../../relational-databases/system-stored-procedures/sp-replmonitorsubscriptionpendingcmds-transact-sql.md). Vengono restituite le informazioni di monitoraggio per tutti i comandi in sospeso per tutte le sottoscrizioni che utilizzano il server di distribuzione. Per limitare il set di risultati a comandi in sospeso per le sottoscrizioni appartenenti a un singolo server di pubblicazione, server di sottoscrizione, pubblicazione o database pubblicato, specificare **@publisher**, **@subscriber**, **@publication**, o **@publisher_db**, rispettivamente.  
  
#### Per monitorare le modifiche di tipo merge in attesa di essere caricate o scaricate  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_showpendingchanges](../../../relational-databases/system-stored-procedures/sp-showpendingchanges-transact-sql.md). Viene restituito un set di risultati in cui sono indicate le informazioni sulle modifiche in attesa di essere replicate nei Sottoscrittori. Per limitare il set di risultati a modifiche che appartengono a una sola pubblicazione o a un solo un articolo, specificare rispettivamente **@publication** o **@article**.  
  
2.  Un sottoscrittore nel database di sottoscrizione, eseguire [sp_showpendingchanges](../../../relational-databases/system-stored-procedures/sp-showpendingchanges-transact-sql.md). Viene restituito un set di risultati in cui sono indicate le informazioni sulle modifiche in attesa di essere replicate nel server di pubblicazione. Per limitare il set di risultati a modifiche che appartengono a una sola pubblicazione o a un solo un articolo, specificare rispettivamente **@publication** o **@article**.  
  
#### Per monitorare sessioni dell'agente di merge  
  
1.  Nel server di distribuzione nel database di distribuzione, eseguire [sp_replmonitorhelpmergesession](../../../relational-databases/system-stored-procedures/sp-replmonitorhelpmergesession-transact-sql.md). Restituisce informazioni sul monitoraggio, tra cui **Session_id**, su tutte le sessioni dell'agente di Merge per tutte le sottoscrizioni tramite il server di distribuzione. È inoltre possibile ottenere **Session_id** eseguendo una query di [MSmerge_sessions](../../../relational-databases/system-tables/msmerge-sessions-transact-sql.md) tabella di sistema.  
  
2.  Nel server di distribuzione nel database di distribuzione, eseguire [sp_replmonitorhelpmergesessiondetail](../../../relational-databases/system-stored-procedures/sp-replmonitorhelpmergesessiondetail-transact-sql.md). Specificare un **Session_id** valore ottenuto al passaggio 1 per **@session_id**. Vengono visualizzate informazioni di monitoraggio dettagliate sulla sessione.  
  
3.  Ripetere il passaggio 2 per ciascuna sessione desiderata.  
  
#### Per monitorare le sessioni dell'agente di merge per le sottoscrizioni pull dal Sottoscrittore  
  
1.  Nel database di sottoscrizione del sottoscrittore, eseguire [sp_replmonitorhelpmergesession](../../../relational-databases/system-stored-procedures/sp-replmonitorhelpmergesession-transact-sql.md). Per una determinata sottoscrizione, specificare **@publisher**, **@publication**, e il nome del database di pubblicazione per **@publisher_db**. Vengono restituite le informazioni di monitoraggio per le ultime cinque sessioni dell'agente di merge della sottoscrizione. Prendere nota del valore di **Session_id** per le sessioni di interesse nel risultato impostata.  
  
2.  Nel database di sottoscrizione del sottoscrittore, eseguire [sp_replmonitorhelpmergesessiondetail](../../../relational-databases/system-stored-procedures/sp-replmonitorhelpmergesessiondetail-transact-sql.md). Specificare un **Session_id** valore ottenuto al passaggio 1 per **@session_id**. Vengono visualizzate informazioni di monitoraggio dettagliate sulla sessione.  
  
3.  Ripetere il passaggio 2 per ciascuna sessione desiderata.  
  
#### Per visualizzare e modificare le misurazioni del valore soglia di monitoraggio per una pubblicazione  
  
1.  Nel server di distribuzione nel database di distribuzione, eseguire [sp_replmonitorhelppublicationthresholds](../../../relational-databases/system-stored-procedures/sp-replmonitorhelppublicationthresholds-transact-sql.md). Vengono restituiti i valore soglia di monitoraggio impostati per tutte le pubblicazioni che utilizzano il server di distribuzione. Per limitare il set di risultati a monitorare le soglie per le pubblicazioni appartenenti a un singolo server di pubblicazione o di un database pubblicato o a una singola pubblicazione, specificare **@publisher**, **@publisher_db**, o **@publication**, rispettivamente. Prendere nota del valore di **Metric_id** per tutte le soglie che devono essere modificate. Per ulteriori informazioni, vedere [impostare soglie e avvisi in Monitoraggio replica](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
2.  Nel server di distribuzione nel database di distribuzione, eseguire [sp_replmonitorchangepublicationthreshold](../../../relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql.md). Specificare i parametri seguenti, in base alle esigenze:  
  
    -   Il **Metric_id** valore ottenuto nel passaggio 1 per **@metric_id**.  
  
    -   Un nuovo valore per la misurazione del valore soglia di monitoraggio per **@value**.  
  
    -   Un valore pari a **1** per **@shouldalert** se è necessaria la registrazione di un avviso al raggiungimento del valore soglia specificato o un valore pari a **0** se la registrazione dell'avviso non è necessaria.  
  
    -   Un valore pari a **1** per **@mode** per abilitare la metrica di soglia di monitoraggio o un valore pari a **2** per disabilitarla.  
  
##  <a name="RMO"></a> Oggetti RMO (Replication Management Objects)  
  
#### Per monitorare una sottoscrizione di una pubblicazione di tipo merge nel Sottoscrittore  
  
1.  Creare una connessione al sottoscrittore utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza del <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor> e impostare il <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.Publisher%2A>, <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.Publication%2A>, <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.PublisherDB%2A>, <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.SubscriberDB%2A> le proprietà per la sottoscrizione, quindi impostare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà per il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> creato nel passaggio 1.  
  
3.  Chiamare uno dei metodi indicati di seguito per ottenere informazioni sulle sessioni dell'agente di merge per la sottoscrizione.  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionsSummary%2A> -Restituisce una matrice di <xref:Microsoft.SqlServer.Replication.MergeSessionSummary> gli oggetti con informazioni su ultime cinque sessioni dell'agente di Merge al massimo. Si noti il <xref:Microsoft.SqlServer.Replication.MergeSessionSummary.SessionId%2A> valore per le sessioni desiderate.  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionsSummary%2A> -Restituisce una matrice di <xref:Microsoft.SqlServer.Replication.MergeSessionSummary> oggetti con informazioni sulle sessioni dell'agente di Merge che si sono verificati durante il numero passato di ore specificato come il *ore* parametro (fino a ultime cinque sessioni). Si noti il <xref:Microsoft.SqlServer.Replication.MergeSessionSummary.SessionId%2A> valore per le sessioni desiderate.  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetLastSessionSummary%2A> -restituisce un <xref:Microsoft.SqlServer.Replication.MergeSessionSummary> oggetto con informazioni sull'ultima sessione dell'agente di Merge. Si noti il <xref:Microsoft.SqlServer.Replication.MergeSessionSummary.SessionId%2A> valore per questa sessione.  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionsSummaryDataSet%2A> -restituisce un <xref:System.Data.DataSet> oggetto con le informazioni fino a ultime cinque sessioni dell'agente di Merge, uno in ogni riga. Prendere nota del valore di **Session_id** colonna per le sessioni desiderate.  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetLastSessionSummaryDataRow%2A> -restituisce un <xref:System.Data.DataRow> oggetto con informazioni sull'ultima sessione dell'agente di Merge. Prendere nota del valore di **Session_id** colonna per la sessione corrente.  
  
4.  (Facoltativo) Chiamare <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.RefreshSessionSummary%2A> Per aggiornare i dati per il <xref:Microsoft.SqlServer.Replication.MergeSessionSummary> oggetto passato come *mss,* o chiamare <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.RefreshSessionSummary%2A> per aggiornare i dati di <xref:System.Data.DataRow> oggetto passato come *drRefresh*.  
  
5.  Utilizzando l'ID sessione ottenuto nel passaggio 3, chiamare uno dei metodi indicati di seguito per ottenere informazioni sui dettagli di una determinata sessione.  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionDetails%2A> -restituisce una matrice di <xref:Microsoft.SqlServer.Replication.MergeSessionDetail> oggetti per l'oggetto fornito *SessionId*.  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionDetailsDataSet%2A> -restituisce un <xref:System.Data.DataSet> oggetto con le informazioni per l'oggetto specificato *SessionId*.  
  
#### Per monitorare le proprietà di replica per tutte le pubblicazioni in un server di distribuzione  
  
1.  Creare una connessione al server di distribuzione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.ReplicationMonitor> (classe).  
  
3.  Impostare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà per il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> creato nel passaggio 1.  
  
4.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo per ottenere le proprietà dell'oggetto.  
  
5.  Eseguire uno o più metodi riportati di seguito per ottenere le informazioni di replica per tutti i server di pubblicazione che utilizzano il server di distribuzione.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumDistributionAgents%2A> -restituisce un <xref:System.Data.DataSet> oggetto che contiene informazioni su tutti gli agenti di distribuzione nel server di distribuzione.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumErrorRecords%2A> -restituisce un <xref:System.Data.DataSet> oggetto che contiene informazioni sugli errori archiviati nel server di distribuzione.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumLogReaderAgents%2A> -restituisce un <xref:System.Data.DataSet> oggetto che contiene informazioni su tutti gli agenti di lettura Log nel server di distribuzione.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumMergeAgents%2A> -restituisce un <xref:System.Data.DataSet> oggetto che contiene informazioni su tutti gli agenti di Merge nel server di distribuzione.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumMiscellaneousAgents%2A> -restituisce un <xref:System.Data.DataSet> oggetto che contiene informazioni su tutti gli altri agenti di replica nel server di distribuzione.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumPublishers%2A> -restituisce un <xref:System.Data.DataSet> oggetto che contiene informazioni su tutti i server di pubblicazione nel server di distribuzione.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumPublishers2%2A> -restituisce un <xref:System.Data.DataSet> oggetto che restituisce i server di pubblicazione che utilizzano questo server di distribuzione.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumQueueReaderAgents%2A> -restituisce un <xref:System.Data.DataSet> oggetto che contiene informazioni su tutti gli agenti di lettura coda nel server di distribuzione.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumQueueReaderAgentSessionDetails%2A> -restituisce un <xref:System.Data.DataSet> oggetto che contiene dettagli sull'agente di lettura coda specificato e sulla sessione.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumQueueReaderAgentSessions%2A> -restituisce un <xref:System.Data.DataSet> oggetto che contiene informazioni di sessione relative all'agente di lettura coda specificato.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumSnapshotAgents%2A> -restituisce un <xref:System.Data.DataSet> oggetto che contiene informazioni su tutti gli agenti Snapshot nel server di distribuzione.  
  
#### Per monitorare le proprietà della pubblicazione per un server di pubblicazione specifico nel server di distribuzione  
  
1.  Creare una connessione al server di distribuzione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Ottenere un <xref:Microsoft.SqlServer.Replication.PublisherMonitor> oggetto in uno dei modi seguenti.  
  
    -   Creare un'istanza di <xref:Microsoft.SqlServer.Replication.PublisherMonitor> (classe). Impostare il <xref:Microsoft.SqlServer.Replication.PublisherMonitor.Name%2A> proprietà per il server di pubblicazione, quindi impostare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà per il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> creato nel passaggio 1. Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo per ottenere le proprietà dell'oggetto. Se questo metodo restituisce **false**, il nome del server di pubblicazione non è definito in modo corretto o la pubblicazione non esiste.  
  
    -   Dal <xref:Microsoft.SqlServer.Replication.PublisherMonitorCollection> si accede tramite il <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.PublisherMonitors%2A> proprietà di un oggetto esistente <xref:Microsoft.SqlServer.Replication.ReplicationMonitor> oggetto.  
  
3.  Eseguire uno o più metodi riportati di seguito per ottenere le informazioni di replica per tutte le pubblicazioni appartenenti al server di pubblicazione.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumDistributionAgentSessionDetails%2A> -restituisce un <xref:System.Data.DataSet> che contiene dettagli sull'agente di distribuzione e sulla sessione specificato.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumDistributionAgentSessions%2A> -restituisce un <xref:System.Data.DataSet> oggetto che contiene informazioni di sessione relative all'agente di distribuzione specificato.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumErrorRecords%2A> -restituisce un <xref:System.Data.DataSet> oggetto che contiene informazioni di record di errore relativi all'errore specificato.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumLogReaderAgentSessionDetails%2A> -restituisce un <xref:System.Data.DataSet> oggetto che contiene i dettagli per l'agente di lettura Log specificato e sulla sessione.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumLogReaderAgentSessions%2A> -restituisce un <xref:System.Data.DataSet> oggetto che contiene informazioni sulla sessione per l'agente di lettura Log specificato.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumMergeAgentSessionDetails%2A> -restituisce un <xref:System.Data.DataSet> oggetto che contiene dettagli sull'agente di Merge specificato e sulla sessione.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumMergeAgentSessionDetails2%2A> -restituisce un <xref:System.Data.DataSet> oggetto che contiene ulteriori dettagli sull'agente di Merge specificato e sulla sessione.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumMergeAgentSessions%2A> -restituisce un <xref:System.Data.DataSet> oggetto che contiene informazioni sulla sessione per l'agente di Merge specificato.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumMergeAgentSessions2%2A> -restituisce un <xref:System.Data.DataSet> oggetto che contiene informazioni aggiuntive sulla sessione dell'agente di Merge specificato.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumPublications%2A> -restituisce un <xref:System.Data.DataSet> oggetto che contiene informazioni su tutte le pubblicazioni nel server di distribuzione.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumPublications2%2A> -restituisce un <xref:System.Data.DataSet> oggetto che contiene informazioni aggiuntive su tutte le pubblicazioni nel server di distribuzione.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumSnapshotAgentSessionDetails%2A> -restituisce un <xref:System.Data.DataSet> oggetto che contiene dettagli sull'agente Snapshot specificato e sulla sessione.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumSnapshotAgentSessions%2A> -restituisce un <xref:System.Data.DataSet> oggetto che contiene informazioni di sessione per l'agente Snapshot specificato.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumSubscriptions%2A> -restituisce un <xref:System.Data.DataSet> oggetto che contiene informazioni su tutte le sottoscrizioni alle pubblicazioni nel server di distribuzione.  
  
#### Per monitorare le proprietà di una pubblicazione specifica nel server di distribuzione  
  
1.  Creare una connessione al server di distribuzione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Ottenere un <xref:Microsoft.SqlServer.Replication.PublicationMonitor> oggetto in uno dei modi seguenti.  
  
    -   Creare un'istanza di <xref:Microsoft.SqlServer.Replication.PublicationMonitor> (classe). Impostare il <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A>, e <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A> proprietà per la pubblicazione, quindi impostare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà per il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> creato nel passaggio 1. Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo per ottenere le proprietà dell'oggetto. Se questo metodo restituisce **false**, le proprietà della pubblicazione non sono state definite in modo corretto o la pubblicazione non esiste.  
  
    -   Dal <xref:Microsoft.SqlServer.Replication.PublicationMonitorCollection> si accede tramite il <xref:Microsoft.SqlServer.Replication.PublisherMonitor.PublicationMonitors%2A> proprietà di un oggetto esistente <xref:Microsoft.SqlServer.Replication.PublisherMonitor> oggetto.  
  
3.  Eseguire uno o più metodi riportati di seguito per ottenere informazioni su questa pubblicazione.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumErrorRecords%2A> -restituisce un <xref:System.Data.DataSet> oggetto che contiene i record degli errori relativi all'errore specificato.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumLogReaderAgent%2A> -restituisce un <xref:System.Data.DataSet> oggetto che contiene informazioni sull'agente di lettura Log per questa pubblicazione.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumMonitorThresholds%2A> -restituisce un <xref:System.Data.DataSet> oggetto che contiene informazioni sulle soglie di avviso di monitoraggio impostati per la pubblicazione.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumQueueReaderAgent%2A> -restituisce un <xref:System.Data.DataSet> oggetto che contiene informazioni sull'agente di lettura coda utilizzato dalla pubblicazione.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumSnapshotAgent%2A> -restituisce un <xref:System.Data.DataSet> oggetto che contiene informazioni relative all'agente Snapshot per questa pubblicazione.  
  
    -   <xref:Microsoft.SqlServer.Replication.Publication.EnumSubscriptions%2A> -restituisce un <xref:System.Data.DataSet> oggetto che contiene informazioni sulle sottoscrizioni della pubblicazione.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumSubscriptions2%2A> -restituisce un <xref:System.Data.DataSet> oggetto che contiene informazioni aggiuntive sulle sottoscrizioni della pubblicazione in base al fornito <xref:Microsoft.SqlServer.Replication.SubscriptionResultOption>.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokenHistory%2A> -restituisce un <xref:System.Data.DataSet> oggetto che contiene informazioni sulla latenza per il token di traccia specificato.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokens%2A> -restituisce un <xref:System.Data.DataSet> oggetto che contiene informazioni su tutti i token di traccia inseriti nella pubblicazione.  
  
#### Per monitorare i comandi transazionali in attesa di essere applicati al Sottoscrittore  
  
1.  Creare una connessione al server di distribuzione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Ottenere un <xref:Microsoft.SqlServer.Replication.PublicationMonitor> oggetto in uno dei modi seguenti.  
  
    -   Creare un'istanza di <xref:Microsoft.SqlServer.Replication.PublicationMonitor> (classe). Impostare il <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A>, e <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A> proprietà per la pubblicazione, quindi impostare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà per il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> creato nel passaggio 1. Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo per ottenere le proprietà dell'oggetto. Se questo metodo restituisce **false**, le proprietà della pubblicazione non sono state definite in modo corretto o la pubblicazione non esiste.  
  
    -   Dal <xref:Microsoft.SqlServer.Replication.PublicationMonitorCollection> si accede tramite il <xref:Microsoft.SqlServer.Replication.PublisherMonitor.PublicationMonitors%2A> proprietà di un oggetto esistente <xref:Microsoft.SqlServer.Replication.PublisherMonitor> oggetto.  
  
3.  Eseguire il <xref:Microsoft.SqlServer.Replication.PublicationMonitor.TransPendingCommandInfo%2A> metodo, che restituisce un <xref:Microsoft.SqlServer.Replication.PendingCommandInfo> oggetto.  
  
4.  Utilizzare le proprietà di questo <xref:Microsoft.SqlServer.Replication.PendingCommandInfo> oggetto per determinare il numero stimato di comandi in sospeso e il periodo di tempo necessario per completare il recapito di questi comandi.  
  
#### Per impostare i valore soglia degli avvisi di monitoraggio per una pubblicazione  
  
1.  Creare una connessione al server di distribuzione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Ottenere un <xref:Microsoft.SqlServer.Replication.PublicationMonitor> oggetto in uno dei modi seguenti.  
  
    -   Creare un'istanza di <xref:Microsoft.SqlServer.Replication.PublicationMonitor> (classe). Impostare il <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A>, e <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A> proprietà per la pubblicazione, quindi impostare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà per il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> creato nel passaggio 1. Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo per ottenere le proprietà dell'oggetto. Se questo metodo restituisce **false**, le proprietà della pubblicazione non sono state definite in modo corretto o la pubblicazione non esiste.  
  
    -   Dal <xref:Microsoft.SqlServer.Replication.PublicationMonitorCollection> si accede tramite il <xref:Microsoft.SqlServer.Replication.PublisherMonitor.PublicationMonitors%2A> proprietà di un oggetto esistente <xref:Microsoft.SqlServer.Replication.PublisherMonitor> oggetto.  
  
3.  Eseguire il <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumMonitorThresholds%2A> metodo. Prendere nota delle impostazioni di soglia corrente nell'oggetto restituito <xref:System.Collections.ArrayList> di <xref:Microsoft.SqlServer.Replication.MonitorThreshold> oggetti.  
  
4.  Eseguire il <xref:Microsoft.SqlServer.Replication.PublicationMonitor.ChangeMonitorThreshold%2A> metodo. Passare i parametri indicati di seguito.  
  
    -   *metricID* : una <xref:System.Int32> che rappresenta la metrica di soglia di monitoraggio nella tabella seguente:  
  
        |Valore|Descrizione|  
        |-----------|-----------------|  
        |1|**scadenza** -monitoraggi delle scadenze imminenti delle sottoscrizioni di pubblicazioni transazionali.|  
        |2|**latenza** -monitoraggi per le prestazioni delle sottoscrizioni di pubblicazioni transazionali.|  
        |4|**mergeexpiration** -esegue il monitoraggio delle scadenze imminenti delle sottoscrizioni di pubblicazioni di tipo merge.|  
        |5|**mergeslowrunduration** -Controlla la durata delle sincronizzazioni di tipo merge su connessioni a larghezza di banda ridotta (remoto).|  
        |6|**mergefastrunduration** -Controlla la durata delle sincronizzazioni di tipo merge su connessioni a banda larga (LAN).|  
        |7|**mergefastrunspeed** -Controlla la frequenza di sincronizzazione delle sincronizzazioni di tipo merge su connessioni a banda larga (LAN).|  
        |8|**mergeslowrunspeed** -Controlla la frequenza di sincronizzazione delle sincronizzazioni di tipo merge su connessioni a larghezza di banda ridotta (remoto).|  
  
    -   *abilitare* - <xref:System.Boolean> valore che indica se la metrica è abilitata per la pubblicazione.  
  
    -   *thresholdValue* -valore integer che imposta la soglia.  
  
    -   *shouldAlert* -numero intero che indica se questa soglia deve generare un avviso.  
  
  