---
title: "Impostazione di pianificazioni della sincronizzazione | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "subscriptions [SQL Server replication], synchronizing"
  - "scheduling synchronization [SQL Server replication]"
  - "synchronization [SQL Server replication], schedules"
  - "replica [SQL Server], sincronizzazione"
ms.assetid: 97f2535b-ec19-4973-823d-bcf3d5aa0216
caps.latest.revision: 40
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 40
---
# Impostazione di pianificazioni della sincronizzazione
  In questo argomento viene descritto come specificare le pianificazioni di sincronizzazione in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] o RMO (Replication Management Objects). Quando si crea una sottoscrizione, è possibile definire una pianificazione della sincronizzazione per controllare l'esecuzione dell'agente di replica per la sottoscrizione. Se non si specificano parametri di pianificazione, per la sottoscrizione verrà utilizzata la pianificazione predefinita.  
  
 Le sottoscrizioni vengono sincronizzate dall'agente di distribuzione, per la replica snapshot e transazionale, o dall'agente di merge, per la replica di tipo merge. Gli agenti possono essere in esecuzione continuamente, essere in esecuzione su richiesta o essere in esecuzione su una pianificazione.  
  
 **Contenuto dell'argomento**  
  
-   **Per impostare le pianificazioni della sincronizzazione, utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Oggetti RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Impostare le pianificazioni della sincronizzazione nella pagina **Pianificazione della sincronizzazione** della Creazione guidata nuova sottoscrizione. Per ulteriori informazioni sull'accesso a questa procedura guidata, vedere [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md) e [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md).  
  
 Modificare le pianificazioni della sincronizzazione nella finestra di dialogo **Proprietà pianificazione processo** , alla quale è possibile accedere dalla cartella **Processi** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] e dalle finestre relative ai dettagli dell'agente in Monitoraggio replica. Per informazioni sull'avvio di monitoraggio replica, vedere [avviare Monitoraggio replica](../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
 Se si specificano le pianificazioni dalla cartella **Processi** , utilizzare la tabella seguente per determinare il nome del processo dell'agente.  
  
|Agente|Nome processo|  
|-----------|--------------|  
|Agente di merge per le sottoscrizioni pull|**\< server di pubblicazione>-\< PublicationDatabase>-\< pubblicazione>-\< sottoscrittore>-\< SubscriptionDatabase>-\< numero intero>**|  
|Agente di merge per le sottoscrizioni push|**\< server di pubblicazione>-\< PublicationDatabase>-\< pubblicazione>-\< sottoscrittore>-\< numero intero>**|  
|Agente di distribuzione per le sottoscrizioni push|**\< server di pubblicazione>-\< PublicationDatabase>-\< pubblicazione>-\< sottoscrittore>-\< numero intero>** <sup>1</sup>|  
|Agente di distribuzione per le sottoscrizioni pull|**\< server di pubblicazione>-\< PublicationDatabase>-\< pubblicazione>-\< sottoscrittore>-\< SubscriptionDatabase>-\< GUID>** <sup>2</sup>|  
|Agente di distribuzione per le sottoscrizioni push di Sottoscrittori non SQL Server|**\< server di pubblicazione>-\< PublicationDatabase>-\< pubblicazione>-\< sottoscrittore>-\< numero intero>**|  
  
 <sup>1</sup> per le sottoscrizioni push a pubblicazioni Oracle è **\< server di pubblicazione>-\< Publisher**> anziché **\< server di pubblicazione>-\< PublicationDatabase>**  
  
 <sup>2</sup> per le sottoscrizioni pull a pubblicazioni Oracle, è **\< server di pubblicazione>-\< DistributionDatabase**> anziché **\< server di pubblicazione>-\< PublicationDatabase>**  
  
#### Per impostare le pianificazioni della sincronizzazione  
  
1.  Nel **SynchronizationSchedule** pagina della creazione guidata sottoscrizione, selezionare uno dei seguenti valori del **pianificazione agente** elenco a discesa per ogni sottoscrizione che si sta creando:  
  
    -   **Esecuzione continua**  
  
    -   **Esecuzione solo su richiesta**  
  
    -   **\<Define Schedule…>**  
  
2.  Se si seleziona **\< Definisci pianificazione >**, specificare una pianificazione nel **proprietà pianificazione processo** la finestra di dialogo e quindi fare clic su **OK**.  
  
3.  Completare la procedura guidata.  
  
#### Per modificare una pianificazione della sincronizzazione per una sottoscrizione push in Monitoraggio replica  
  
1.  Espandere un gruppo di server di pubblicazione nel riquadro a sinistra di Monitoraggio replica, espandere un server di pubblicazione e quindi fare clic su una pubblicazione.  
  
2.  Fare clic sulla scheda **Tutte le sottoscrizioni** .  
  
3.  Fare doppio clic su una sottoscrizione e quindi fare clic su **Visualizza dettagli**.  
  
4.  Nel **sottoscrizione \< SubscriptionName >** finestra, fare clic su **azione**, quindi fare clic su **\< AgentName> proprietà processo**.  
  
5.  Nel **pianificazioni** pagina della **proprietà processo - \< Nome_processo>** nella finestra di dialogo fare clic su **Modifica.**  
  
6.  Nel **proprietà pianificazione processo** la finestra di dialogo, selezionare un valore compreso il **tipo pianificazione** elenco a discesa:  
  
    -   Per specificare che l'agente deve essere eseguito in modo continuo, selezionare **Avvia automaticamente all'avvio di SQL Server Agent**.  
  
    -   Per specificare che l'agente deve essere eseguito in base a una pianificazione, selezionare **Periodica**.  
  
    -   Per specificare che l'agente deve essere eseguito su richiesta, selezionare **Singola occorrenza**.  
  
7.  Se si seleziona **Periodica**, specificare una pianificazione per l'agente.  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
#### Per modificare una pianificazione della sincronizzazione per una sottoscrizione push in Management Studio  
  
1.  Connettersi al server di distribuzione in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **SQL Server Agent** e quindi la cartella **Processi** .  
  
3.  Il pulsante destro del processo per l'agente di distribuzione o l'agente di Merge associato alla sottoscrizione e quindi fare clic su **proprietà**.  
  
4.  Nel **pianificazioni** pagina della **proprietà processo - \< Nome_processo>** nella finestra di dialogo fare clic su **Modifica.**  
  
5.  Nel **proprietà pianificazione processo** la finestra di dialogo, selezionare un valore compreso il **tipo pianificazione** elenco a discesa:  
  
    -   Per specificare che l'agente deve essere eseguito in modo continuo, selezionare **Avvia automaticamente all'avvio di SQL Server Agent**.  
  
    -   Per specificare che l'agente deve essere eseguito in base a una pianificazione, selezionare **Periodica**.  
  
    -   Per specificare che l'agente deve essere eseguito su richiesta, selezionare **Singola occorrenza**.  
  
6.  Se si seleziona **Periodica**, specificare una pianificazione per l'agente.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
#### Per modificare una pianificazione della sincronizzazione per una sottoscrizione pull in Management Studio  
  
1.  Connettersi al Sottoscrittore in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **SQL Server Agent** e quindi la cartella **Processi** .  
  
3.  Il pulsante destro del processo per l'agente di distribuzione o l'agente di Merge associato alla sottoscrizione e quindi fare clic su **proprietà**.  
  
4.  Nel **pianificazioni** pagina della **proprietà processo - \< Nome_processo>** nella finestra di dialogo fare clic su **Modifica.**  
  
5.  Nel **proprietà pianificazione processo** la finestra di dialogo, selezionare un valore compreso il **tipo pianificazione** elenco a discesa:  
  
    -   Per specificare che l'agente deve essere eseguito in modo continuo, selezionare **Avvia automaticamente all'avvio di SQL Server Agent**.  
  
    -   Per specificare che l'agente deve essere eseguito in base a una pianificazione, selezionare **Periodica**.  
  
    -   Per specificare che l'agente deve essere eseguito su richiesta, selezionare **Singola occorrenza**.  
  
6.  Se si seleziona **Periodica**, specificare una pianificazione per l'agente.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 È possibile definire pianificazioni della sincronizzazione a livello di programmazione tramite stored procedure di replica. Le stored procedure utilizzate dipendono dal tipo di replica e dal tipo di sottoscrizione (pull o push).  
  
 Viene definita una pianificazione per i seguenti parametri di pianificazione, i cui comportamenti vengono ereditati da [sp_add_schedule & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md):  
  
-   **@frequency_type** -tipo di frequenza utilizzata per la pianificazione dell'agente.  
  
-   **@frequency_interval** : giorno della settimana in cui viene eseguito un agente.  
  
-   **@frequency_relative_interval** : settimana di un determinato mese quando l'agente viene pianificata l'esecuzione mensile.  
  
-   **@frequency_recurrence_factor** -il numero di unità di tipo di frequenza che si verificano tra le sincronizzazioni.  
  
-   **@frequency_subday** -unità della frequenza quando l'agente viene eseguito più di una volta al giorno.  
  
-   **@frequency_subday_interval** -il numero di unità della frequenza tra viene eseguito quando l'agente viene eseguito più di una volta al giorno.  
  
-   **@active_start_time_of_day** : la prima ora di un determinato giorno quando un agente viene avviato.  
  
-   **@active_end_time_of_day** - l'ultima volta in un determinato giorno quando un agente viene avviato.  
  
-   **@active_start_date** : primo giorno in cui verrà applicata la pianificazione dell'agente.  
  
-   **@active_end_date** : ultimo giorno che verrà attivata, la pianificazione dell'agente.  
  
#### Per definire la pianificazione della sincronizzazione per una sottoscrizione pull di una pubblicazione transazionale  
  
1.  Creare una nuova sottoscrizione pull di una pubblicazione transazionale. Per altre informazioni, vedere [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md).  
  
2.  Il sottoscrittore, eseguire [sp_addpullsubscription_agent & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md). Specificare **@publisher**, **@publisher_db**, **@publication**, e [!INCLUDE[msCoName](../../includes/msconame-md.md)] le credenziali di Windows con cui viene eseguito l'agente di distribuzione nel Sottoscrittore per **@job_name** e **@password**. Specificare i parametri di sincronizzazione, descritti in dettaglio in precedenza, con cui definire la pianificazione per il processo dell'agente di distribuzione che sincronizza la sottoscrizione.  
  
#### Per definire la pianificazione della sincronizzazione per una sottoscrizione push di una pubblicazione transazionale  
  
1.  Creare una nuova sottoscrizione push di una pubblicazione transazionale. Per altre informazioni, vedere [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md).  
  
2.  Il sottoscrittore, eseguire [sp_addpushsubscription_agent & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md). Specificare **@subscriber**, **@subscriber_db**, **@publication**, e le credenziali di Windows con cui viene eseguito l'agente di distribuzione nel Sottoscrittore per **@job_name** e **@password**. Specificare i parametri di sincronizzazione, descritti in dettaglio in precedenza, con cui definire la pianificazione per il processo dell'agente di distribuzione che sincronizza la sottoscrizione.  
  
#### Per definire la pianificazione della sincronizzazione per una sottoscrizione pull di una pubblicazione di tipo merge  
  
1.  Creare una nuova sottoscrizione pull di una pubblicazione di tipo merge. Per altre informazioni, vedere [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md).  
  
2.  Il sottoscrittore, eseguire [sp_addmergepullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md). Specificare **@publisher**, **@publisher_db**, **@publication**, e le credenziali di Windows con cui viene eseguito l'agente di Merge nel Sottoscrittore per **@job_name** e **@password**. Specificare i parametri di sincronizzazione, descritti in dettaglio in precedenza, con cui definire la pianificazione per il processo dell'agente di merge che sincronizza la sottoscrizione.  
  
#### Per definire la pianificazione della sincronizzazione per una sottoscrizione push di una pubblicazione di tipo merge  
  
1.  Creare una nuova sottoscrizione push di una pubblicazione di tipo merge. Per altre informazioni, vedere [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md).  
  
2.  Il sottoscrittore, eseguire [sp_addmergepushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql.md). Specificare **@subscriber**, **@subscriber_db**, **@publication**, e le credenziali di Windows con cui viene eseguito l'agente di Merge nel Sottoscrittore per **@job_name** e **@password**. Specificare i parametri di sincronizzazione, descritti in dettaglio in precedenza, con cui definire la pianificazione per il processo dell'agente di merge che sincronizza la sottoscrizione.  
  
##  <a name="RMOProcedure"></a> Utilizzo di RMO (Replication Management Objects)  
 La replica utilizza SQL Server Agent per pianificare i processi per attività che vengono svolte periodicamente, ad esempio la generazione di snapshot e la sincronizzazione delle sottoscrizioni. È possibile utilizzare gli oggetti RMO (Replication Management Objects) a livello di programmazione per specificare le pianificazioni per i processi dell'agente di replica.  
  
> [!NOTE]  
>  Quando si crea una sottoscrizione e specificare un valore **false** per **CreateSyncAgentByDefault** (comportamento predefinito per le sottoscrizioni pull) il processo dell'agente non viene creato e le proprietà di pianificazione vengono ignorate. In questo caso, la pianificazione della sincronizzazione deve essere determinata dall'applicazione. Per ulteriori informazioni, vedere [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md) e [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md).  
  
#### Per definire una pianificazione dell'agente di replica quando si crea una sottoscrizione push di una pubblicazione transazionale  
  
1.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.TransSubscription> classe per la sottoscrizione che si sta creando. Per altre informazioni, vedere [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md).  
  
2.  Prima di chiamare <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A>, impostare una o più dei seguenti campi di <xref:Microsoft.SqlServer.Replication.Subscription.AgentSchedule%2A> proprietà:  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> -tipo di frequenza (ad esempio giornaliera o settimanale) è utilizzata per la pianificazione dell'agente.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> : giorno della settimana in cui viene eseguito un agente.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> : settimana di un determinato mese quando l'agente viene pianificata l'esecuzione mensile.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> -il numero di unità di tipo di frequenza che si verificano tra le sincronizzazioni.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> -unità della frequenza quando l'agente viene eseguito più di una volta al giorno.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> -il numero di unità della frequenza tra viene eseguito quando l'agente viene eseguito più di una volta al giorno.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - prima ora di un determinato giorno in cui un agente viene avviato.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - ora più recente in un determinato giorno in cui un agente viene avviato.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> : primo giorno in cui la pianificazione dell'agente è attivo.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> : ultimo giorno in cui la pianificazione dell'agente è attivo.  
  
    > [!NOTE]  
    >  Se una di queste proprietà viene omessa, viene impostato un valore predefinito.  
  
3.  Chiamare il <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> metodo per creare la sottoscrizione.  
  
#### Per definire una pianificazione dell'agente di replica quando si crea una sottoscrizione pull di una pubblicazione transazionale  
  
1.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.TransPullSubscription> classe per la sottoscrizione che si sta creando. Per altre informazioni, vedere [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md).  
  
2.  Prima di chiamare <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A>, impostare una o più dei seguenti campi di <xref:Microsoft.SqlServer.Replication.PullSubscription.AgentSchedule%2A> proprietà:  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> -tipo di frequenza (ad esempio giornaliera o settimanale) utilizzato durante la pianificazione dell'agente.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> : giorno della settimana in cui viene eseguito un agente.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> : settimana di un determinato mese in cui l'agente è pianificata l'esecuzione mensile.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> -il numero di unità di tipo di frequenza che si verificano tra le sincronizzazioni.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> -unità della frequenza quando l'agente viene eseguito più di una volta al giorno.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> -il numero di unità della frequenza tra viene eseguito quando l'agente viene eseguito più di una volta al giorno.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - prima ora di un determinato giorno in cui un agente viene avviato.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - ora più recente in un determinato giorno in cui un agente viene avviato.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> : primo giorno in cui la pianificazione dell'agente è attivo.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> : ultimo giorno in cui la pianificazione dell'agente è attivo.  
  
    > [!NOTE]  
    >  Se una di queste proprietà viene omessa, viene impostato un valore predefinito.  
  
3.  Chiamare il <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> metodo per creare la sottoscrizione.  
  
#### Per definire una pianificazione dell'agente di replica quando si crea una sottoscrizione pull di una pubblicazione di tipo merge  
  
1.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.MergePullSubscription> classe per la sottoscrizione che si sta creando. Per altre informazioni, vedere [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md).  
  
2.  Prima di chiamare <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A>, impostare una o più dei seguenti campi di <xref:Microsoft.SqlServer.Replication.PullSubscription.AgentSchedule%2A> proprietà:  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> -tipo di frequenza (ad esempio giornaliera o settimanale) utilizzato durante la pianificazione dell'agente.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> : giorno della settimana in cui viene eseguito un agente.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> : settimana di un determinato mese in cui l'agente è pianificata l'esecuzione mensile.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> -il numero di unità di tipo di frequenza che si verificano tra le sincronizzazioni.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> -unità della frequenza quando l'agente viene eseguito più di una volta al giorno.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> -il numero di unità della frequenza tra viene eseguito quando l'agente viene eseguito più di una volta al giorno.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - prima ora di un determinato giorno in cui un agente viene avviato.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - ora più recente in un determinato giorno in cui un agente viene avviato.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> : primo giorno in cui la pianificazione dell'agente è attivo.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> : ultimo giorno in cui la pianificazione dell'agente è attivo.  
  
    > [!NOTE]  
    >  Se una di queste proprietà viene omessa, viene impostato un valore predefinito.  
  
3.  Chiamare il <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> metodo per creare la sottoscrizione.  
  
#### Per definire una pianificazione dell'agente di replica quando si crea una sottoscrizione push di una pubblicazione di tipo merge  
  
1.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.MergeSubscription> classe per la sottoscrizione che si sta creando. Per altre informazioni, vedere [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md).  
  
2.  Prima di chiamare <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A>, impostare una o più dei seguenti campi di <xref:Microsoft.SqlServer.Replication.Subscription.AgentSchedule%2A> proprietà:  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> -tipo di frequenza (ad esempio giornaliera o settimanale) utilizzato durante la pianificazione dell'agente.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> : giorno della settimana in cui viene eseguito un agente.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> : settimana di un determinato mese in cui l'agente è pianificata l'esecuzione mensile.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> -il numero di unità di tipo di frequenza che si verificano tra le sincronizzazioni.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> -unità della frequenza quando l'agente viene eseguito più di una volta al giorno.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> -il numero di unità della frequenza tra viene eseguito quando l'agente viene eseguito più di una volta al giorno.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - prima ora di un determinato giorno in cui un agente viene avviato.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - ora più recente in un determinato giorno in cui un agente viene avviato.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> : primo giorno in cui la pianificazione dell'agente è attivo.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> : ultimo giorno in cui la pianificazione dell'agente è attivo.  
  
    > [!NOTE]  
    >  Se una di queste proprietà viene omessa, viene impostato un valore predefinito.  
  
3.  Chiamare il <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> metodo per creare la sottoscrizione.  
  
###  <a name="PShellExample"></a> Esempio (RMO)  
 In questo esempio viene creata una sottoscrizione push di una pubblicazione di tipo merge e viene specificata la pianificazione per la sincronizzazione di tale sottoscrizione.  
  
 [!code-csharp[HowTo#rmo_CreateMergePushSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createmergepushsub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePushSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createmergepushsub)]  
  
## Vedere anche  
 [Procedure consigliate per la sicurezza della replica](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Sottoscrizione delle pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)   
 [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md)   
 [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md)   
 [Sincronizzare i dati](../../relational-databases/replication/synchronize-data.md)  
  
  