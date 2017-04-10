---
title: "Utilizzo dei profili agenti di replica | Microsoft Docs"
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
  - "replication [SQL Server], agents and profiles"
  - "replication agent profiles [SQL Server]"
  - "agents [SQL Server replication], profiles"
  - "profili [SQL Server], agenti di replica"
ms.assetid: 9c290a88-4e9f-4a7e-aab5-4442137a9918
caps.latest.revision: 49
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 49
---
# Utilizzo dei profili agenti di replica
  In questo argomento viene descritto come utilizzare i profili degli agenti di replica in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] o RMO (Replication Management Objects). Il comportamento di ogni agente di replica è controllato da un set di parametri che è possibile impostare tramite i profili agenti. Ogni agente dispone di un profilo predefinito e alcuni anche di profili predefiniti aggiuntivi. In un momento specifico, per un agente è attivo un solo profilo.  
  
 **Contenuto dell'argomento**  
  
-   **Per utilizzare i profili degli agenti di replica, utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
    -   Accedere alla finestra di dialogo Profili agenti  
  
    -   Specificare un profilo per un agente  
  
    -   Creare un profilo  
  
    -   Modificare un profilo  
  
    -   Eliminare un profilo  
  
     [Transact-SQL](#TsqlProcedure)  
  
    -   Creare un profilo  
  
    -   Modificare un profilo  
  
    -   Eliminare un profilo  
  
    -   Utilizzare i profili agenti durante la sincronizzazione  
  
    -   Esempio Transact-SQL  
  
     [oggetti RMO (Replication Management Objects)](#RMOProcedure)  
  
    -   Creare un profilo  
  
    -   Modificare un profilo  
  
    -   Eliminare un profilo  
  
-   **Completamento:**  [dopo aver modificato i parametri dell'agente](#FollowUp)  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
###  <a name="Access_SSMS"></a> Per accedere alla finestra di dialogo Profili agenti da SQL Server Management Studio  
  
1.  Nel **Generale** pagina della **proprietà server di distribuzione - \< distributore>** nella finestra di dialogo fare clic su **impostazioni predefinite profili**.  
  
#### Per accedere alla finestra di dialogo Profili agenti da Monitoraggio replica  
  
-   Per aprire la finestra di dialogo per tutti gli agenti, fare doppio clic su un server di pubblicazione e quindi fare clic su **Profili agenti**.  
  
-   Per aprire la finestra di dialogo per un singolo agente:  
  
    1.  Espandere un gruppo di server di pubblicazione nel riquadro a sinistra di Monitoraggio replica, espandere un server di pubblicazione e quindi fare clic su una pubblicazione.  
  
    2.  Per i profili dell'agente di distribuzione e l'agente di Merge, fare doppio clic su una sottoscrizione nel **tutte le sottoscrizioni** scheda e quindi fare clic su **profilo agente**. Per gli altri agenti, l'agente fare clic su di **agenti** scheda e quindi fare clic su **profilo agente**.  
  
###  <a name="Specify_SSMS"></a> Per specificare un profilo per un agente  
  
1.  Se nella finestra di dialogo **Profili agenti** vengono visualizzati i profili di più agenti, selezionare un agente.  
  
2.  Selezionare un profilo nella colonna **Predefinito per i nuovi agenti** della griglia **Profili agenti** . Per impostazione predefinita, il profilo viene applicato solo agli agenti per le nuove pubblicazioni e sottoscrizioni.  
  
3.  Per specificare che tutti gli agenti del tipo selezionato per le pubblicazioni o le sottoscrizioni esistenti devono utilizzare questo profilo, fare clic su **Modifica agenti esistenti**.  
  
###  <a name="Modify_SSMS"></a> Per visualizzare e modificare i parametri associati a un profilo  
  
1.  Se nella finestra di dialogo **Profili agenti** vengono visualizzati i profili di più agenti, selezionare un agente.  
  
2.  Fare clic sul pulsante delle proprietà (**...**) accanto a un profilo.  
  
3.  Visualizzare i parametri e valori di **\< ProfileName> le proprietà del profilo** la finestra di dialogo.  
  
    -   È possibile modificare i parametri nei profili definiti dall'utente, ma non quelli nei profili di sistema predefiniti.  
  
    -   Per visualizzare tutti i parametri per un agente, deselezionare la casella di controllo **Mostra solo i parametri utilizzati in questo profilo** . Per informazioni sui parametri degli agenti, vedere i collegamenti alla fine di questo argomento.  
  
4.  Scegliere **Chiudi**.  
  
###  <a name="Create_SSMS"></a> Per creare un profilo definito dall'utente  
  
1.  Se nella finestra di dialogo **Profili agenti** vengono visualizzati i profili di più agenti, selezionare un agente.  
  
2.  Fare clic su **Nuovo**.  
  
3.  Nella finestra di dialogo di inizializzazione **Nuovo profilo agente** selezionare un profilo esistente su cui basare il nuovo profilo.  
  
4.  Nella finestra di dialogo **Nuovo profilo agente** immettere i valori nelle caselle di testo **Nome** e **Descrizione** .  
  
5.  Modificare i parametri per personalizzare il profilo. Per visualizzare tutti i parametri per un agente, deselezionare la casella di controllo **Mostra solo i parametri utilizzati in questo profilo** . Per informazioni sui parametri degli agenti, vedere i collegamenti alla fine di questo argomento.  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
###  <a name="Delete_SSMS"></a> Per eliminare un profilo definito dall'utente  
  
1.  Se nella finestra di dialogo **Profili agenti** vengono visualizzati i profili di più agenti, selezionare un agente.  
  
2.  Se un profilo è associato a uno o più agenti, modificare il profilo per tali agenti:  
  
    1.  Selezionare un altro profilo nella griglia **Profili agenti** .  
  
    2.  Fare clic su **Modifica agenti esistenti**.  
  
        > [!NOTE]  
        >  Verrà modificato il profilo di tutti gli agenti del tipo selezionato per le pubblicazioni o le sottoscrizioni esistenti e non solo di quelli che utilizzano il profilo che si desidera eliminare.  
  
3.  Selezionare il profilo che si desidera eliminare, quindi fare clic su **Elimina**.  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
###  <a name="Create_tsql"></a> Per creare un nuovo profilo agente  
  
1.  Nel server di distribuzione, eseguire [sp_add_agent_profile & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-add-agent-profile-transact-sql.md). Specificare **@name**, un valore di **1** per **@profile_type**, e uno dei seguenti valori per **@agent_type**:  
  
    -   **1** - [agente di replica Snapshot](../../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
    -   **2** - [Agente lettura Log repliche](../../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
    -   **3** - [agente distribuzione repliche](../../../relational-databases/replication/agents/replication-distribution-agent.md)  
  
    -   **4** - [agente Merge repliche](../../../relational-databases/replication/agents/replication-merge-agent.md)  
  
    -   **9** - [agente di lettura coda repliche](../../../relational-databases/replication/agents/replication-queue-reader-agent.md)  
  
     Se si desidera impostare il profilo come nuovo profilo predefinito per il tipo di agente di replica, specificare il valore **1** per **@default**. Viene restituito l'identificatore per il nuovo profilo utilizzando il **@profile_id** parametro di output. Viene creato un nuovo profilo con un set di parametri del profilo basato sul profilo predefinito per il tipo di agente specificato.  
  
2.  Una volta creato il nuovo profilo, è possibile personalizzarlo aggiungendo, rimuovendo o modificando i parametri predefiniti.  
  
###  <a name="Modify_tsql"></a> Per modificare un profilo agente esistente  
  
1.  Nel server di distribuzione, eseguire [sp_help_agent_profile & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql.md). Specificare uno dei valori seguenti per **@agent_type**:  
  
    -   **1** - [agente di replica Snapshot](../../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
    -   **2** - [Agente lettura Log repliche](../../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
    -   **3** - [agente distribuzione repliche](../../../relational-databases/replication/agents/replication-distribution-agent.md)  
  
    -   **4** - [agente Merge repliche](../../../relational-databases/replication/agents/replication-merge-agent.md)  
  
    -   **9** - [agente di lettura coda repliche](../../../relational-databases/replication/agents/replication-queue-reader-agent.md)  
  
     Vengono restituiti tutti i profili per il tipo di agente specificato. Prendere nota del valore di **profile_id** nel set di risultati per il profilo da modificare.  
  
2.  Nel server di distribuzione, eseguire [sp_help_agent_parameter & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql.md). Specificare l'identificatore del profilo dal passaggio 1 per **@profile_id**. Vengono restituiti tutti i parametri per il profilo. Tenere presente il nome dei parametri del profilo da modificare o rimuovere.  
  
3.  Per modificare il valore di un parametro in un profilo, eseguire [sp_change_agent_profile & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-change-agent-profile-transact-sql.md). Specificare l'identificatore del profilo dal passaggio 1 per **@profile_id**, il nome del parametro da modificare per **@property**, e un nuovo valore per il parametro per **@value**.  
  
    > [!NOTE]  
    >  Non è possibile modificare un profilo agente esistente in modo da impostarlo come profilo predefinito di un agente. A tale scopo, è necessario creare un nuovo profilo come profilo predefinito, come indicato nella procedura indicata in precedenza.  
  
4.  Per rimuovere un parametro da un profilo, eseguire [sp_drop_agent_parameter & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql.md). Specificare l'identificatore del profilo dal passaggio 1 per **@profile_id** e il nome del parametro da rimuovere per **@parameter_name**.  
  
5.  Per aggiungere un nuovo parametro a un profilo è necessario effettuare le seguenti operazioni:  
  
    -   Query di [MSagentparameterlist & #40; Transact-SQL & #41;](../../../relational-databases/system-tables/msagentparameterlist-transact-sql.md) tabella nel server di distribuzione per determinare i parametri del profilo possono essere impostati per ogni tipo di agente.  
  
    -   Nel server di distribuzione, eseguire [sp_add_agent_parameter & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md). Specificare l'identificatore del profilo dal passaggio 1 per **@profile_id**, il nome di un parametro valido per aggiungere per **@parameter_name**, e il valore del parametro per **@parameter_value**.  
  
###  <a name="Delete_tsql"></a> Per eliminare un profilo agente  
  
1.  Nel server di distribuzione, eseguire [sp_help_agent_profile & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql.md). Specificare uno dei valori seguenti per **@agent_type**:  
  
    -   **1** - [agente di replica Snapshot](../../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
    -   **2** - [Agente lettura Log repliche](../../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
    -   **3** - [agente distribuzione repliche](../../../relational-databases/replication/agents/replication-distribution-agent.md)  
  
    -   **4** - [agente Merge repliche](../../../relational-databases/replication/agents/replication-merge-agent.md)  
  
    -   **9** - [agente di lettura coda repliche](../../../relational-databases/replication/agents/replication-queue-reader-agent.md)  
  
     Vengono restituiti tutti i profili per il tipo di agente specificato. Prendere nota del valore di **profile_id** nel set di risultati per il profilo da rimuovere.  
  
2.  Nel server di distribuzione, eseguire [sp_drop_agent_profile & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-drop-agent-profile-transact-sql.md). Specificare l'identificatore del profilo dal passaggio 1 per **@profile_id**.  
  
###  <a name="Synch_tsql"></a> Per utilizzare i profili agenti durante la sincronizzazione  
  
1.  Nel server di distribuzione, eseguire [sp_help_agent_profile & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql.md). Specificare uno dei valori seguenti per **@agent_type**:  
  
    -   **1** - [agente di replica Snapshot](../../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
    -   **2** - [Agente lettura Log repliche](../../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
    -   **3** - [agente distribuzione repliche](../../../relational-databases/replication/agents/replication-distribution-agent.md)  
  
    -   **4** - [agente Merge repliche](../../../relational-databases/replication/agents/replication-merge-agent.md)  
  
    -   **9** - [agente di lettura coda repliche](../../../relational-databases/replication/agents/replication-queue-reader-agent.md)  
  
     Vengono restituiti tutti i profili per il tipo di agente specificato. Prendere nota del valore di **profile_name** nel set di risultati per il profilo da utilizzare.  
  
2.  Se l'agente viene avviato da un processo dell'agente, modificare il passaggio del processo che avvia l'agente per specificare il valore di **profile_name** ottenuto nel passaggio 1 dopo il **- ProfileName** parametro della riga di comando. Per ulteriori informazioni, vedere [visualizzare e modificare parametri prompt dei comandi dell'agente di replica e 40 #; SQL Server Management Studio & #41;](../../../relational-databases/replication/agents/view and modify replication agent command prompt parameters.md).  
  
3.  Quando si avvia l'agente dal prompt dei comandi, specificare il valore di **profile_name** ottenuto nel passaggio 1 dopo il **- ProfileName** parametro della riga di comando.  
  
###  <a name="TsqlExample"></a> Esempio (Transact-SQL)  
 Questo esempio viene creato un profilo personalizzato per l'agente di Merge denominato **custom_merge**, modifica il valore di **- UploadReadChangesPerBatch** aggiunge un nuovo parametro, **- ExchangeType** parametro e restituisce informazioni sul profilo creato.  
  
 [!code-sql[HowTo#sp_addagentprofileparam](../../../relational-databases/replication/codesnippet/tsql/work-with-replication-ag_1.sql)]  
  
##  <a name="RMOProcedure"></a> Utilizzo di RMO  
  
###  <a name="Create_RMO"></a> Per creare un nuovo profilo agente  
  
1.  Creare una connessione al server di distribuzione utilizzando un'istanza di <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.AgentProfile> (classe).  
  
3.  Impostare le proprietà indicate di seguito nell'oggetto.  
  
    -   <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> -il nome per il profilo.  
  
    -   <xref:Microsoft.SqlServer.Replication.AgentProfile.AgentType%2A> : una <xref:Microsoft.SqlServer.Replication.AgentType> valore che specifica il tipo di agente di replica per il quale viene creato il profilo.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> - <xref:Microsoft.SqlServer.Management.Common.ServerConnection> creato nel passaggio 1.  
  
    -   (Facoltativo) <xref:Microsoft.SqlServer.Replication.AgentProfile.Description%2A> -una descrizione del profilo.  
  
    -   (Facoltativo) <xref:Microsoft.SqlServer.Replication.AgentProfile.Default%2A> -impostare questa proprietà su **true** se tutti i nuovi processi di agente per questo <xref:Microsoft.SqlServer.Replication.AgentType> utilizzeranno questo profilo per impostazione predefinita.  
  
4.  Chiamare il <xref:Microsoft.SqlServer.Replication.AgentProfile.Create%2A> metodo per creare il profilo nel server.  
  
5.  Una volta reso disponibile il profilo nel server, è possibile personalizzarlo aggiungendo, rimuovendo o modificando i valori dei parametri dell'agente di replica.  
  
6.  Per assegnare il profilo a un processo di agente di replica esistente, chiamare il <xref:Microsoft.SqlServer.Replication.AgentProfile.AssignToAgent%2A> metodo. Passare il nome del database di distribuzione per *distributionDBName* e l'ID del processo per *agentID*.  
  
###  <a name="Modify_RMO"></a> Per modificare un profilo agente esistente  
  
1.  Creare una connessione al server di distribuzione utilizzando un'istanza di <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.ReplicationServer> (classe). Passare il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> oggetto creato nel passaggio 1.  
  
3.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo. Se il metodo restituisce **false**, verificare che il server di distribuzione esista.  
  
4.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationServer.EnumAgentProfiles%2A> metodo. Passare un <xref:Microsoft.SqlServer.Replication.AgentType> valore per limitare i profili restituiti a un tipo specifico di agente di replica.  
  
5.  Ottenere il valore desiderato <xref:Microsoft.SqlServer.Replication.AgentProfile> oggetto restituito <xref:System.Collections.ArrayList>, dove il <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> proprietà dell'oggetto corrisponde al nome di profilo.  
  
6.  Chiamare uno dei seguenti metodi di <xref:Microsoft.SqlServer.Replication.AgentProfile> per modificare il profilo:  
  
    -   <xref:Microsoft.SqlServer.Replication.AgentProfile.AddParameter%2A> -aggiunge un parametro supportato al profilo, in cui *nome* è il nome del parametro dell'agente di replica e *valore* è il valore specificato. Per enumerare tutti i parametri di agente supportato per un tipo di agente specificato, chiamare il <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameterInfo%2A> metodo. Questo metodo restituisce un <xref:System.Collections.ArrayList> di <xref:Microsoft.SqlServer.Replication.AgentProfileParameterInfo> gli oggetti che rappresentano tutti i parametri supportati.  
  
    -   <xref:Microsoft.SqlServer.Replication.AgentProfile.RemoveParameter%2A> -Rimuove un parametro esistente dal profilo, in cui *nome* è il nome del parametro dell'agente di replica. Per enumerare tutti i parametri dell'agente corrente definiti per il profilo, chiamare il <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameters%2A> metodo. Questo metodo restituisce un <xref:System.Collections.ArrayList> di <xref:Microsoft.SqlServer.Replication.AgentProfileParameter> gli oggetti che rappresentano il parametro esistente per questo profilo.  
  
    -   <xref:Microsoft.SqlServer.Replication.AgentProfile.ChangeParameter%2A> -l'impostazione di un parametro esistente nel profilo, in cui *nome* è il nome del parametro dell'agente e *newValue* è il valore a cui il parametro viene modificato. Per enumerare tutti i parametri dell'agente corrente definiti per il profilo, chiamare il <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameters%2A> metodo. Questo metodo restituisce un <xref:System.Collections.ArrayList> di <xref:Microsoft.SqlServer.Replication.AgentProfileParameter> gli oggetti che rappresentano il parametro esistente per questo profilo. Per enumerare tutte le impostazioni di parametro dell'agente è supportato, chiamare il <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameterInfo%2A> metodo. Questo metodo restituisce un <xref:System.Collections.ArrayList> di <xref:Microsoft.SqlServer.Replication.AgentProfileParameterInfo> gli oggetti che rappresentano i valori supportati per tutti i parametri.  
  
###  <a name="Delete_RMO"></a> Per eliminare un profilo agente  
  
1.  Creare una connessione al server di distribuzione utilizzando un'istanza di <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.AgentProfile> (classe). Impostare il nome del profilo per <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> e <xref:Microsoft.SqlServer.Management.Common.ServerConnection> dal passaggio 1 per <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo. Se il metodo restituisce **false**, il nome specificato non è corretto o il profilo non esiste nel server.  
  
4.  Verificare che il <xref:Microsoft.SqlServer.Replication.AgentProfile.Type%2A> è impostata su <xref:Microsoft.SqlServer.Replication.AgentProfileTypeOption.User>, che indica un profilo del cliente. Non è necessario rimuovere un profilo con un valore di <xref:Microsoft.SqlServer.Replication.AgentProfileTypeOption.System> per <xref:Microsoft.SqlServer.Replication.AgentProfile.Type%2A>.  
  
5.  Chiamare il <xref:Microsoft.SqlServer.Replication.AgentProfile.Remove%2A> metodo per rimuovere il profilo definito dall'utente rappresentato da questo oggetto dal server.  
  
##  <a name="FollowUp"></a> Completamento: dopo avere modificato i parametri degli agenti  
 Le modifiche apportate al parametro dell'agente verranno applicate al successivo avvio dell'agente. Se l'agente viene eseguito in modo continuo, è necessario arrestarlo e riavviarlo.  
  
## Vedere anche  
 [Profili degli agenti di replica](../../../relational-databases/replication/agents/replication-agent-profiles.md)   
 [Agente snapshot repliche](../../../relational-databases/replication/agents/replication-snapshot-agent.md)   
 [Agente lettura log repliche](../../../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [Agente distribuzione repliche](../../../relational-databases/replication/agents/replication-distribution-agent.md)   
 [Agente merge repliche](../../../relational-databases/replication/agents/replication-merge-agent.md)   
 [Agente di lettura coda repliche](../../../relational-databases/replication/agents/replication-queue-reader-agent.md)  
  
  