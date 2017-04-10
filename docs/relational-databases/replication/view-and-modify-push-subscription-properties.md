---
title: "Visualizzazione e modifica delle propriet&#224; delle sottoscrizioni push | Microsoft Docs"
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
  - "viewing replication properties"
  - "push subscriptions [SQL Server replication], properties"
  - "subscriptions [SQL Server replication], push"
  - "push subscriptions [SQL Server replication], modifying"
  - "modifying replication properties, push subscriptions"
  - "modifica di sottoscrizioni, SQL Server Management Studio"
ms.assetid: 801d2995-7aa5-4626-906e-c8190758ec71
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# Visualizzazione e modifica delle propriet&#224; delle sottoscrizioni push
  In questo argomento viene descritto come modificare le proprietà delle sottoscrizioni push in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] o RMO (Replication Management Objects).  
  
 **Contenuto dell'argomento**  
  
-   **Per visualizzare e modificare le proprietà delle sottoscrizioni push, utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Oggetti RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Visualizzare e modificare le proprietà della sottoscrizione push dal server di pubblicazione nella:  
  
-   Il **Proprietà sottoscrizione - \< Publisher>: \< PublicationDatabase>** la finestra di dialogo, disponibile in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
-   Scheda **Tutte le sottoscrizioni** , disponibile in Monitoraggio replica. Per informazioni sull'avvio di monitoraggio replica, vedere [avviare Monitoraggio replica](../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
#### Per visualizzare e modificare le proprietà della sottoscrizione push in Management Studio  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Pubblicazioni locali** .  
  
3.  Espandere la pubblicazione appropriata, fare doppio clic su una sottoscrizione e quindi fare clic su **proprietà**.  
  
4.  Se necessario, modificare le proprietà e quindi fare clic su **OK**.  
  
#### Per visualizzare e modificare le proprietà della sottoscrizione push in Monitoraggio replica  
  
1.  Espandere un gruppo di server di pubblicazione nel riquadro a sinistra di Monitoraggio replica, espandere un server di pubblicazione e quindi fare clic su una pubblicazione.  
  
2.  Fare clic sulla scheda **Tutte le sottoscrizioni** .  
  
3.  Fare doppio clic su una sottoscrizione e quindi fare clic su **proprietà**.  
  
4.  Se necessario, modificare le proprietà e quindi fare clic su **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 È possibile modificare le sottoscrizioni push e accedere alle relative proprietà a livello di programmazione utilizzando stored procedure di replica. Le stored procedure utilizzate dipendono dal tipo di pubblicazione a cui appartiene la sottoscrizione.  
  
#### Per visualizzare le proprietà di una sottoscrizione push di una pubblicazione snapshot o transazionale  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_helpsubscription](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md). Specificare **@publication**, **@subscriber**e il valore **all** per **@article**.  
  
2.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_helpsubscriberinfo](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md), specificando **@subscriber**.  
  
#### Per modificare le proprietà di una sottoscrizione push di una pubblicazione snapshot o transazionale  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_changesubscriber](../../relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql.md), specificando **@subscriber** ed eventuali parametri per le proprietà del sottoscrittore da modificare.  
  
2.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_changesubscription](../../relational-databases/system-stored-procedures/sp-changesubscription-transact-sql.md). Specificare **@publication**, **@subscriber**, **@destination_db**, un valore di **tutti** per **@article**, la proprietà della sottoscrizione da modificare come **@property**, e il nuovo valore come **@value**. In questo modo vengono modificate le impostazioni di sicurezza per la sottoscrizione push.  
  
3.  (Facoltativo) Per modificare le proprietà del pacchetto Data Transformation Services (DTS) di una sottoscrizione, eseguire [sp_changesubscriptiondtsinfo](../../relational-databases/system-stored-procedures/sp-changesubscriptiondtsinfo-transact-sql.md) nel database di sottoscrizione del sottoscrittore. Specificare l'ID del processo dell'agente di distribuzione per **@jobid** e le proprietà del pacchetto DTS seguenti:  
  
    -   **@dts_package_name**  
  
    -   **@dts_package_password**  
  
    -   **@dts_package_location**  
  
     In questo modo le proprietà del pacchetto DTS di una sottoscrizione verranno modificate.  
  
    > [!NOTE]  
    >  Il processo tramite l'esecuzione, è possibile ottenere l'ID [sp_helpsubscription](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md).  
  
#### Per visualizzare le proprietà di una sottoscrizione push di una pubblicazione di tipo merge  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_helpmergesubscription](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md). Specificare i parametri **@publication** e **@subscriber**.  
  
2.  Server di pubblicazione, eseguire [sp_helpsubscriberinfo](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md), specificando **@subscriber**.  
  
#### Per modificare le proprietà di una sottoscrizione push di una pubblicazione di tipo merge  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_changemergesubscription](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md). Specificare **@publication**, **@subscriber**, **@subscriber_db**, la proprietà della sottoscrizione da modificare come **@property**, e il nuovo valore come **@value**.  
  
###  <a name="TsqlExample"></a> Esempio (Transact-SQL)  
  
##  <a name="RMOProcedure"></a> Utilizzo di RMO (Replication Management Objects)  
 Le classi RMO utilizzate per la visualizzazione o la modifica delle proprietà di una sottoscrizione push dipendono dal tipo di pubblicazione per cui viene creata la sottoscrizione push.  
  
#### Per visualizzare o modificare le proprietà di una sottoscrizione push di una pubblicazione snapshot o transazionale  
  
1.  Creare una connessione al server di pubblicazione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.TransSubscription> (classe).  
  
3.  Impostare il <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, e <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> proprietà.  
  
4.  Impostare il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> dal passaggio 1 per il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> l'impostazione della proprietà.  
  
5.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo per ottenere le proprietà dell'oggetto. Se questo metodo restituisce **false**, le proprietà della sottoscrizione non sono state definite in modo corretto nel passaggio 3 oppure la sottoscrizione non esiste.  
  
6.  (Facoltativo) Per modificare le proprietà, impostare un nuovo valore per uno del <xref:Microsoft.SqlServer.Replication.TransSubscription> le proprietà che possono essere impostate e quindi chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> metodo.  
  
7.  (Facoltativo) Per visualizzare le nuove impostazioni, chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> per ricaricare le proprietà per la sottoscrizione.  
  
#### Per visualizzare o modificare le proprietà di una sottoscrizione push di una pubblicazione di tipo merge  
  
1.  Creare una connessione al sottoscrittore utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.MergeSubscription> (classe).  
  
3.  Impostare il <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, e <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> proprietà.  
  
4.  Impostare il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> dal passaggio 1 per il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> l'impostazione della proprietà.  
  
5.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo per ottenere le proprietà dell'oggetto. Se questo metodo restituisce **false**, le proprietà della sottoscrizione non sono state definite in modo corretto nel passaggio 3 oppure la sottoscrizione non esiste.  
  
6.  (Facoltativo) Per modificare le proprietà, impostare un nuovo valore per uno del <xref:Microsoft.SqlServer.Replication.MergeSubscription> le proprietà che possono essere impostate e quindi chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> metodo.  
  
7.  (Facoltativo) Per visualizzare le nuove impostazioni, chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> per ricaricare le proprietà per la sottoscrizione.  
  
## Vedere anche  
 [Consente di visualizzare informazioni ed eseguire attività per una sottoscrizione & #40; Monitoraggio replica & #41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)   
 [Procedure consigliate per la sicurezza della replica](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Sottoscrizione delle pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)  
  
  