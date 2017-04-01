---
title: "Visualizzazione e modifica delle propriet&#224; delle sottoscrizioni pull | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modifying subscriptions"
  - "viewing replication properties"
  - "modifying replication properties, pull subscriptions"
  - "pull subscriptions [SQL Server replication], modifying"
  - "subscriptions [SQL Server replication], pull"
  - "pull subscriptions [SQL Server replication], properties"
  - "modifica di sottoscrizioni, SQL Server Management Studio"
ms.assetid: 1601e54f-86f0-49e8-b023-87a5d1def033
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# Visualizzazione e modifica delle propriet&#224; delle sottoscrizioni pull
  In questo argomento viene descritto come modificare le proprietà delle sottoscrizioni pull in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] o RMO (Replication Management Objects).  
  
 **Contenuto dell'argomento**  
  
-   **Per visualizzare e modificare le proprietà delle sottoscrizioni pull tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Oggetti RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Visualizzare le proprietà delle sottoscrizioni pull dal server di pubblicazione o del sottoscrittore il **Proprietà sottoscrizione - \< Publisher>: \< PublicationDatabase>** la finestra di dialogo, disponibile in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Nel Sottoscrittore è disponibile un numero maggiore di proprietà ed è inoltre possibile modificare le proprietà. Le proprietà possono inoltre essere visualizzate sul server di pubblicazione nella scheda **Tutte le sottoscrizioni** , disponibile in Monitoraggio replica. Per informazioni sull'avvio di monitoraggio replica, vedere [avviare Monitoraggio replica](../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
#### Per visualizzare le proprietà delle sottoscrizioni pull dal server di pubblicazione in Management Studio  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Pubblicazioni locali** .  
  
3.  Espandere la pubblicazione appropriata, fare doppio clic su una sottoscrizione e quindi fare clic su **proprietà**.  
  
4.  Visualizzare le proprietà e quindi fare clic su **OK**.  
  
#### Per visualizzare e modificare le proprietà delle sottoscrizioni pull dal Sottoscrittore in Management Studio  
  
1.  Connettersi al Sottoscrittore in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Sottoscrizioni locali** .  
  
3.  Fare doppio clic su una sottoscrizione e quindi fare clic su **proprietà**.  
  
4.  Se necessario, modificare le proprietà e quindi fare clic su **OK**.  
  
#### Per visualizzare le proprietà delle sottoscrizioni pull dal server di pubblicazione in Monitoraggio replica  
  
1.  Espandere un gruppo di server di pubblicazione nel riquadro a sinistra di Monitoraggio replica, espandere un server di pubblicazione e quindi fare clic su una pubblicazione.  
  
2.  Fare clic sulla scheda **Tutte le sottoscrizioni** .  
  
3.  Fare doppio clic su una sottoscrizione e quindi fare clic su **proprietà**.  
  
4.  Visualizzare le proprietà e quindi fare clic su **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 È possibile modificare le sottoscrizioni pull e accedere alle relative proprietà a livello di programmazione utilizzando stored procedure di replica. Le stored procedure utilizzate dipendono dal tipo di pubblicazione a cui appartiene la sottoscrizione.  
  
#### Per visualizzare le proprietà di una sottoscrizione pull di una pubblicazione snapshot o transazionale  
  
1.  Il sottoscrittore, eseguire [sp_helppullsubscription](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md). Specificare **@publisher**, **@publisher_db**, e **@publication**. In tal modo verranno restituite le informazioni sulla sottoscrizione archiviate nelle tabelle di sistema del Sottoscrittore.  
  
2.  Il sottoscrittore, eseguire [sp_helpsubscription_properties](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md). Specificare **@publisher**, **@publisher_db**, **@publication**, e uno dei seguenti valori per **@publication_type**:  
  
    -   **0** -sottoscrizione appartiene a una pubblicazione transazionale.  
  
    -   **1** -sottoscrizione appartiene a una pubblicazione snapshot.  
  
3.  Server di pubblicazione, eseguire [sp_helpsubscription](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md). Specificare i parametri **@publication** e **@subscriber**.  
  
4.  Server di pubblicazione, eseguire [sp_helpsubscriberinfo](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md), specificando **@subscriber**. In tal modo verranno visualizzate le informazioni sul Sottoscrittore.  
  
#### Per modificare le proprietà di una sottoscrizione pull di una pubblicazione snapshot o transazionale  
  
1.  Il sottoscrittore, eseguire [sp_change_subscription_properties](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md), specificando **@publisher**, **@publisher_db**, **@publication**, un valore di **0** (transazionale) o **1** (snapshot) per **@publication_type**, la proprietà della sottoscrizione da modificare come **@property**, e il nuovo valore come **@value**.  
  
2.  (Facoltativo) Nel database di sottoscrizione del sottoscrittore, eseguire [sp_changesubscriptiondtsinfo](../../relational-databases/system-stored-procedures/sp-changesubscriptiondtsinfo-transact-sql.md). Specificare l'ID del processo dell'agente di distribuzione per **@jobid**, e proprietà del pacchetto di Data Transformation Services (DTS) seguenti:  
  
    -   **@dts_package_name**  
  
    -   **@dts_package_password**  
  
    -   **@dts_package_location**  
  
     In questo modo le proprietà del pacchetto DTS di una sottoscrizione verranno modificate.  
  
    > [!NOTE]  
    >  Il processo tramite l'esecuzione, è possibile ottenere l'ID [sp_helpsubscription](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md).  
  
#### Per visualizzare le proprietà di una sottoscrizione pull di una pubblicazione di tipo merge  
  
1.  Il sottoscrittore, eseguire [sp_helpmergepullsubscription](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md). Specificare **@publisher**, **@publisher_db**, e **@publication**.  
  
2.  Il sottoscrittore, eseguire [sp_helpsubscription_properties](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md). Specificare **@publisher**, **@publisher_db**, **@publication**, e un valore pari a 2 per **@publication_type**.  
  
3.  Server di pubblicazione, eseguire [sp_helpmergesubscription](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md) per visualizzare le informazioni di sottoscrizione. Per restituire informazioni su una sottoscrizione specifica, è necessario specificare **@publication**, **@subscriber**, e il valore **pull** per **@subscription_type**.  
  
4.  Server di pubblicazione, eseguire [sp_helpsubscriberinfo](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md), specificando **@subscriber**. In tal modo verranno visualizzate le informazioni sul Sottoscrittore.  
  
#### Per modificare le proprietà di una sottoscrizione pull di una pubblicazione di tipo merge  
  
1.  Il sottoscrittore, eseguire [sp_changemergepullsubscription](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md). Specificare **@publication**, **@publisher**, **@publisher_db**, la proprietà della sottoscrizione da modificare come **@property**, e il nuovo valore come **@value**.  
  
##  <a name="RMOProcedure"></a> Utilizzo di RMO (Replication Management Objects)  
 Le classi RMO utilizzate per la visualizzazione o la modifica delle proprietà di una sottoscrizione pull dipendono dal tipo di pubblicazione per cui viene creata la sottoscrizione pull.  
  
#### Per visualizzare o modificare le proprietà di una sottoscrizione pull di una pubblicazione snapshot o transazionale  
  
1.  Creare una connessione al sottoscrittore utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.TransPullSubscription> (classe).  
  
3.  Impostare il <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, e <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> proprietà.  
  
4.  Impostare la connessione del passaggio 1 per il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà.  
  
5.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo per ottenere le proprietà dell'oggetto. Se questo metodo restituisce **false**, le proprietà della sottoscrizione non sono state definite in modo corretto nel passaggio 3 oppure la sottoscrizione non esiste nel server.  
  
6.  (Facoltativo) Per modificare le proprietà, impostare un nuovo valore per uno del <xref:Microsoft.SqlServer.Replication.TransPullSubscription> le proprietà che possono essere impostate e quindi chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> metodo.  
  
7.  (Facoltativo) Per visualizzare le nuove impostazioni, chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> per ricaricare le proprietà per l'articolo.  
  
8.  Chiudere tutte le connessioni.  
  
#### Per visualizzare o modificare le proprietà di una sottoscrizione pull di una pubblicazione di tipo merge  
  
1.  Creare una connessione al sottoscrittore utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.MergePullSubscription> (classe).  
  
3.  Impostare il <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, e <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> proprietà.  
  
4.  Impostare la connessione del passaggio 1 per il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà.  
  
5.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo per ottenere le proprietà dell'oggetto. Se questo metodo restituisce **false**, le proprietà della sottoscrizione non sono state definite in modo corretto nel passaggio 3 oppure la sottoscrizione non esiste nel server.  
  
6.  (Facoltativo) Per modificare le proprietà, impostare un nuovo valore per uno del <xref:Microsoft.SqlServer.Replication.MergePullSubscription> le proprietà che possono essere impostate e quindi chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> metodo.  
  
7.  (Facoltativo) Per visualizzare le nuove impostazioni, chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> per ricaricare le proprietà per l'articolo.  
  
8.  Chiudere tutte le connessioni.  
  
## Vedere anche  
 [Consente di visualizzare informazioni ed eseguire attività per una sottoscrizione & #40; Monitoraggio replica & #41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)   
 [Procedure consigliate per la sicurezza della replica](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Sottoscrizione delle pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)  
  
  