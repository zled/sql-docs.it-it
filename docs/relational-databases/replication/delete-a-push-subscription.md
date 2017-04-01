---
title: "Eliminazione di una sottoscrizione push | Microsoft Docs"
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
  - "rimozione di sottoscrizioni"
  - "sottoscrizioni push [replica di SQL Server], eliminazione"
  - "eliminazione di sottoscrizioni"
  - "sottoscrizioni [replica di SQL Server], push"
ms.assetid: 3c4847e2-aed9-4488-b45d-8164422bdb10
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# Eliminazione di una sottoscrizione push
  In questo argomento viene descritto come eliminare una sottoscrizione push in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] o RMO (Replication Management Objects).  
  
 **Contenuto dell'argomento**  
  
-   **Per eliminare una sottoscrizione push, utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Oggetti RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Eliminare una sottoscrizione push nel server di pubblicazione (dal **pubblicazioni locali** cartella [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]) o nel Sottoscrittore (dal **sottoscrizioni locali** cartella). Se si elimina una sottoscrizione, gli oggetti o i dati non vengono rimossi automaticamente dalla sottoscrizione, ma è necessario rimuoverli manualmente.  
  
#### Per eliminare una sottoscrizione push dal server di pubblicazione  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Pubblicazioni locali** .  
  
3.  Espandere la pubblicazione associata alla sottoscrizione che si desidera eliminare.  
  
4.  Fare doppio clic su sottoscrizione e quindi fare clic su **eliminare**.  
  
5.  Nella finestra di dialogo di conferma specificare se connettersi al Sottoscrittore per eliminare le informazioni sulla sottoscrizione. Se si deseleziona la casella di controllo **Connetti al Sottoscrittore** , è necessario connettersi al Sottoscrittore in un secondo momento per eliminare le informazioni.  
  
#### Per eliminare una sottoscrizione push dal Sottoscrittore  
  
1.  Connettersi al Sottoscrittore in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Sottoscrizioni locali** .  
  
3.  Fare doppio clic su sottoscrizione si desidera eliminare e quindi fare clic su **eliminare**.  
  
4.  Nella finestra di dialogo di conferma specificare se connettersi al server di pubblicazione per eliminare le informazioni sulla sottoscrizione. Se si deseleziona la casella di controllo **Connetti al server di pubblicazione** , sarà necessario connettersi al server di pubblicazione in seguito per eliminare le informazioni.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 È possibile eliminare sottoscrizioni push a livello di programmazione tramite le stored procedure di replica. Le stored procedure utilizzate dipendono dal tipo di pubblicazione a cui appartiene la sottoscrizione.  
  
#### Per eliminare una sottoscrizione push di una pubblicazione snapshot o transazionale  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_dropsubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md). Specificare i parametri **@publication** e **@subscriber**. Specificare il valore **all** per il parametro **@article**. (Facoltativo) Se il server di distribuzione non è accessibile, specificare un valore di **1** per **@ignore_distributor** per eliminare la sottoscrizione senza rimuovere gli oggetti correlati nel server di distribuzione.  
  
2.  Nel database di sottoscrizione del sottoscrittore, eseguire [sp_subscription_cleanup & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md) Per rimuovere i metadati della replica nel database di sottoscrizione.  
  
#### Per eliminare una sottoscrizione push di una pubblicazione di tipo merge  
  
1.  Server di pubblicazione, eseguire [sp_dropmergesubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md), specificando **@publication**, **@subscriber** e **@subscriber_db**. (Facoltativo) Se il server di distribuzione non è accessibile, specificare un valore di **1** per **@ignore_distributor** per eliminare la sottoscrizione senza rimuovere gli oggetti correlati nel server di distribuzione.  
  
2.  Nel database di sottoscrizione del sottoscrittore, eseguire [sp_mergesubscription_cleanup & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql.md). Specificare **@publisher**, **@publisher_db**, e **@publication**. per rimuovere i metadati di merge dal database di sottoscrizione.  
  
###  <a name="TsqlExample"></a> Esempi (Transact-SQL)  
 In questo esempio viene eliminata una sottoscrizione push di una pubblicazione transazionale.  
  
 [!code-sql[HowTo#sp_droptransubscription](../../relational-databases/replication/codesnippet/tsql/delete-a-push-subscription_1.sql)]  
  
 In questo esempio viene eliminata una sottoscrizione push di una pubblicazione di tipo merge.  
  
 [!code-sql[HowTo#sp_dropmergesubscription](../../relational-databases/replication/codesnippet/tsql/delete-a-push-subscription_2.sql)]  
  
##  <a name="RMOProcedure"></a> Utilizzo di RMO (Replication Management Objects)  
 Le classi RMO utilizzate per l'eliminazione di una sottoscrizione push dipendono dal tipo di pubblicazione per cui viene creata la sottoscrizione push.  
  
#### Per eliminare una sottoscrizione push di una pubblicazione snapshot o transazionale  
  
1.  Creare una connessione al sottoscrittore utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.TransSubscription> (classe).  
  
3.  Impostare il <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, e <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A> proprietà.  
  
4.  Impostare il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> dal passaggio 1 per il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà.  
  
5.  Controllare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> proprietà per verificare che la sottoscrizione esista. Se il valore di questa proprietà è **false**, le proprietà di sottoscrizioni sono state definite in modo non corretto nel passaggio 2 oppure la sottoscrizione non esiste.  
  
6.  Chiamare il <xref:Microsoft.SqlServer.Replication.Subscription.Remove%2A> metodo.  
  
#### Per eliminare una sottoscrizione push di una pubblicazione di tipo merge  
  
1.  Creare una connessione al sottoscrittore utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.MergeSubscription> (classe).  
  
3.  Impostare il <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, e <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A> proprietà.  
  
4.  Impostare il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> dal passaggio 1 per il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà.  
  
5.  Controllare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> proprietà per verificare che la sottoscrizione esista. Se il valore di questa proprietà è **false**, le proprietà di sottoscrizioni sono state definite in modo non corretto nel passaggio 2 oppure la sottoscrizione non esiste.  
  
6.  Chiamare il <xref:Microsoft.SqlServer.Replication.Subscription.Remove%2A> metodo.  
  
###  <a name="PShellExample"></a> Esempi (RMO)  
 È possibile eliminare sottoscrizioni push a livello di programmazione tramite gli oggetti RMO (Replication Management Objects).  
  
 [!code-csharp[HowTo#rmo_DropTranPushSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_droptranpushsub)]  
  
 [!code-vb[HowTo#rmo_vb_DropTranPushSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_droptranpushsub)]  
  
## Vedere anche  
 [Sottoscrizione delle pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)   
 [Procedure consigliate per la sicurezza della replica](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  