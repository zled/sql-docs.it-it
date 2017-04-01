---
title: "Eliminazione di una sottoscrizione pull | Microsoft Docs"
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
  - "removing subscriptions"
  - "deleting subscriptions"
  - "pull subscriptions [SQL Server replication], deleting"
  - "sottoscrizioni [replica di SQL Server], pull"
ms.assetid: 997c0b8e-d8d9-4eed-85b1-6baa1f8594ce
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# Eliminazione di una sottoscrizione pull
  In questo argomento viene descritto come eliminare una sottoscrizione pull in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] o RMO (Replication Management Objects).  
  
 **Contenuto dell'argomento**  
  
-   **Per eliminare una sottoscrizione pull, utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Oggetti RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Eliminare una sottoscrizione pull nel server di pubblicazione (dal **pubblicazioni locali** nella cartella [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]) o nel Sottoscrittore (dal **sottoscrizioni locali** cartella). Se si elimina una sottoscrizione, gli oggetti o i dati non vengono rimossi automaticamente dalla sottoscrizione, ma è necessario rimuoverli manualmente.  
  
#### Per eliminare una sottoscrizione pull nel server di pubblicazione  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Pubblicazioni locali** .  
  
3.  Espandere la pubblicazione associata alla sottoscrizione che si desidera eliminare.  
  
4.  Fare doppio clic su sottoscrizione e quindi fare clic su **eliminare**.  
  
5.  Nella finestra di dialogo di conferma specificare se connettersi al Sottoscrittore per eliminare le informazioni sulla sottoscrizione. Se si deseleziona la casella di controllo **Connetti al Sottoscrittore** , sarà necessario connettersi al Sottoscrittore in seguito per eliminare le informazioni.  
  
#### Per eliminare una sottoscrizione pull nel Sottoscrittore  
  
1.  Connettersi al Sottoscrittore in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Sottoscrizioni locali** .  
  
3.  Fare doppio clic su sottoscrizione si desidera eliminare e quindi fare clic su **eliminare**.  
  
4.  Nella finestra di dialogo di conferma specificare se connettersi al server di pubblicazione per eliminare le informazioni sulla sottoscrizione. Se si deseleziona la casella di controllo **Connetti al server di pubblicazione** , sarà necessario connettersi al server di pubblicazione in seguito per eliminare le informazioni.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 È possibile eliminare sottoscrizioni pull a livello di programmazione tramite le stored procedure di replica. Le stored procedure utilizzate dipenderanno dal tipo di pubblicazione a cui appartiene la sottoscrizione.  
  
#### Per eliminare una sottoscrizione pull di una pubblicazione snapshot o transazionale  
  
1.  Nel database di sottoscrizione del sottoscrittore, eseguire [sp_droppullsubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md). Specificare **@publication**, **@publisher**, e **@publisher_db**.  
  
2.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_dropsubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md). Specificare i parametri **@publication** e **@subscriber**. Specificare il valore **all** per il parametro **@article**. (Facoltativo) Se il server di distribuzione non è accessibile, specificare un valore di **1** per **@ignore_distributor** per eliminare la sottoscrizione senza rimuovere gli oggetti correlati nel server di distribuzione.  
  
#### Per eliminare una sottoscrizione pull di una pubblicazione di tipo merge  
  
1.  Nel database di sottoscrizione del sottoscrittore, eseguire [sp_dropmergepullsubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md). Specificare **@publication**, **@publisher**, e **@publisher_db**.  
  
2.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_dropmergesubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md). Specificare **@publication**, **@subscriber**, e **@subscriber_db**. Specificare un valore di **pull** per **@subscription_type**. (Facoltativo) Se il server di distribuzione non è accessibile, specificare un valore di **1** per **@ignore_distributor** per eliminare la sottoscrizione senza rimuovere gli oggetti correlati nel server di distribuzione.  
  
###  <a name="TsqlExample"></a> Esempi (Transact-SQL)  
 Nell'esempio seguente viene eliminata una sottoscrizione pull di una pubblicazione transazionale. Il primo batch viene eseguito nel Sottoscrittore, mentre il secondo viene eseguito nel server di pubblicazione.  
  
 [!code-sql[HowTo#sp_droptranpullsubscription](../../relational-databases/replication/codesnippet/tsql/delete-a-pull-subscription_1.sql)]  
  
 [!code-sql[HowTo#sp_droptransubscription](../../relational-databases/replication/codesnippet/tsql/delete-a-pull-subscription_2.sql)]  
  
 Nell'esempio seguente viene eliminata una sottoscrizione pull di una pubblicazione di tipo merge. Il primo batch viene eseguito nel Sottoscrittore, mentre il secondo viene eseguito nel server di pubblicazione.  
  
 [!code-sql[HowTo#sp_dropmergepullsubscription](../../relational-databases/replication/codesnippet/tsql/delete-a-pull-subscription_3.sql)]  
  
 [!code-sql[HowTo#sp_dropmergesubscription](../../relational-databases/replication/codesnippet/tsql/delete-a-pull-subscription_4.sql)]  
  
##  <a name="RMOProcedure"></a> Utilizzo di RMO (Replication Management Objects)  
 È possibile eliminare sottoscrizioni pull a livello di programmazione tramite gli oggetti RMO (Replication Management Objects). Le classi RMO utilizzate per l'eliminazione di una sottoscrizione pull dipendono dal tipo di pubblicazione per cui viene creata la sottoscrizione pull.  
  
#### Per eliminare una sottoscrizione pull di una pubblicazione snapshot o transazionale  
  
1.  Creare connessioni per il sottoscrittore e il server di pubblicazione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.TransPullSubscription> classe e impostare il <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, e <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> proprietà. Utilizzare la connessione al sottoscrittore dal passaggio 1 per impostare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà.  
  
3.  Controllare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> proprietà per verificare che la sottoscrizione esista. Se il valore di questa proprietà è **false**, le proprietà di sottoscrizioni sono state definite in modo non corretto nel passaggio 2 oppure la sottoscrizione non esiste.  
  
4.  Chiamare il <xref:Microsoft.SqlServer.Replication.PullSubscription.Remove%2A> metodo.  
  
5.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.TransPublication> classe tramite la connessione server di pubblicazione dal passaggio 1. Specificare <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> e <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
6.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo. Se il metodo restituisce **false**, le proprietà specificate nel passaggio 5 non sono corrette oppure la pubblicazione non esiste nel server.  
  
7.  Chiamare il <xref:Microsoft.SqlServer.Replication.TransPublication.RemovePullSubscription%2A> metodo. Specificare il nome del Sottoscrittore e il database di sottoscrizione per i parametri *subscriber* e *subscriberDB* .  
  
#### Per eliminare una sottoscrizione pull di una pubblicazione di tipo merge  
  
1.  Creare connessioni per il sottoscrittore e il server di pubblicazione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.MergePullSubscription> classe e impostare il <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, e <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> proprietà. Utilizzare la connessione del passaggio 1 per impostare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà.  
  
3.  Controllare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> proprietà per verificare che la sottoscrizione esista. Se il valore di questa proprietà è **false**, le proprietà di sottoscrizioni sono state definite in modo non corretto nel passaggio 2 oppure la sottoscrizione non esiste.  
  
4.  Chiamare il <xref:Microsoft.SqlServer.Replication.PullSubscription.Remove%2A> metodo.  
  
5.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.MergePublication> classe tramite la connessione server di pubblicazione dal passaggio 1. Specificare <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> e <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
6.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo. Se il metodo restituisce **false**, le proprietà specificate nel passaggio 5 non sono corrette oppure la pubblicazione non esiste nel server.  
  
7.  Chiamare il <xref:Microsoft.SqlServer.Replication.MergePublication.RemovePullSubscription%2A> metodo. Specificare il nome del Sottoscrittore e il database di sottoscrizione per i parametri *subscriber* e *subscriberDB* .  
  
###  <a name="PShellExample"></a> Esempi (RMO)  
 In questo esempio viene eliminata una sottoscrizione pull a una pubblicazione transazionale e viene rimossa la registrazione della sottoscrizione nel server di pubblicazione.  
  
 [!code-csharp[HowTo#rmo_DropTranPullSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_droptranpullsub)]  
  
 [!code-vb[HowTo#rmo_vb_DropTranPullSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_droptranpullsub)]  
  
 In questo esempio viene eliminata una sottoscrizione pull a una pubblicazione di tipo merge e viene rimossa la registrazione della sottoscrizione nel server di pubblicazione.  
  
 [!code-csharp[HowTo#rmo_DropMergePullSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_dropmergepullsub)]  
  
 [!code-vb[HowTo#rmo_vb_DropMergePullSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_dropmergepullsub)]  
  
## Vedere anche  
 [Sottoscrizione delle pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)   
 [Procedure consigliate per la sicurezza della replica](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  