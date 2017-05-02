---
title: Eliminare una sottoscrizione pull | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- removing subscriptions
- deleting subscriptions
- pull subscriptions [SQL Server replication], deleting
- subscriptions [SQL Server replication], pull
ms.assetid: 997c0b8e-d8d9-4eed-85b1-6baa1f8594ce
caps.latest.revision: 35
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3c927203ed13ec7eaf359816669ac8b85c44714f
ms.lasthandoff: 04/11/2017

---
# <a name="delete-a-pull-subscription"></a>Eliminazione di una sottoscrizione pull
  In questo argomento viene descritto come eliminare una sottoscrizione pull in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]o RMO (Replication Management Objects).  
  
 **Contenuto dell'argomento**  
  
-   **Per eliminare una sottoscrizione pull, utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Oggetti RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Eliminare una sottoscrizione pull nel server di pubblicazione, dalla cartella **Pubblicazioni locali** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], o nel Sottoscrittore, dalla cartella **Sottoscrizioni locali** . Se si elimina una sottoscrizione, gli oggetti o i dati non vengono rimossi automaticamente dalla sottoscrizione, ma è necessario rimuoverli manualmente.  
  
#### <a name="to-delete-a-pull-subscription-at-the-publisher"></a>Per eliminare una sottoscrizione pull nel server di pubblicazione  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Pubblicazioni locali** .  
  
3.  Espandere la pubblicazione associata alla sottoscrizione che si desidera eliminare.  
  
4.  Fare clic con il pulsante destro del mouse sulla sottoscrizione e quindi scegliere **Elimina**.  
  
5.  Nella finestra di dialogo di conferma specificare se connettersi al Sottoscrittore per eliminare le informazioni sulla sottoscrizione. Se si deseleziona la casella di controllo **Connetti al Sottoscrittore** , sarà necessario connettersi al Sottoscrittore in seguito per eliminare le informazioni.  
  
#### <a name="to-delete-a-pull-subscription-at-the-subscriber"></a>Per eliminare una sottoscrizione pull nel Sottoscrittore  
  
1.  Connettersi al Sottoscrittore in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Sottoscrizioni locali** .  
  
3.  Fare clic con il pulsante destro del mouse sulla sottoscrizione che si desidera eliminare e quindi scegliere **Elimina**.  
  
4.  Nella finestra di dialogo di conferma specificare se connettersi al server di pubblicazione per eliminare le informazioni sulla sottoscrizione. Se si deseleziona la casella di controllo **Connetti al server di pubblicazione** , sarà necessario connettersi al server di pubblicazione in seguito per eliminare le informazioni.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 È possibile eliminare sottoscrizioni pull a livello di programmazione tramite le stored procedure di replica. Le stored procedure utilizzate dipenderanno dal tipo di pubblicazione a cui appartiene la sottoscrizione.  
  
#### <a name="to-delete-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a>Per eliminare una sottoscrizione pull di una pubblicazione snapshot o transazionale  
  
1.  Nel database di sottoscrizione del Sottoscrittore eseguire [sp_droppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md). Specificare i parametri **@publication**, **@publisher**e **@publisher_db**.  
  
2.  Nel database di pubblicazione del server di pubblicazione eseguire [sp_dropsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md). Specificare i parametri **@publication** e **@subscriber**. Specificare il valore **all** per il parametro **@article**. (Facoltativo) Se non è possibile accedere al database di distribuzione, specificare il valore **1** per il parametro **@ignore_distributor** per eliminare la sottoscrizione senza rimuovere gli oggetti correlati nel database di distribuzione.  
  
#### <a name="to-delete-a-pull-subscription-to-a-merge-publication"></a>Per eliminare una sottoscrizione pull di una pubblicazione di tipo merge  
  
1.  Nel database di sottoscrizione del Sottoscrittore eseguire [sp_dropmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md). Specificare i parametri **@publication**, **@publisher**e **@publisher_db**.  
  
2.  Nel database di pubblicazione del server di pubblicazione eseguire [sp_dropmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md). Specificare i parametri **@publication**, **@subscriber**e **@subscriber_db**. Specificare il valore **pull** per il parametro **@subscription_type**. (Facoltativo) Se non è possibile accedere al database di distribuzione, specificare il valore **1** per il parametro **@ignore_distributor** per eliminare la sottoscrizione senza rimuovere gli oggetti correlati nel database di distribuzione.  
  
###  <a name="TsqlExample"></a> Esempi (Transact-SQL)  
 Nell'esempio seguente viene eliminata una sottoscrizione pull di una pubblicazione transazionale. Il primo batch viene eseguito nel Sottoscrittore, mentre il secondo viene eseguito nel server di pubblicazione.  
  
 [!code-sql[HowTo#sp_droptranpullsubscription](../../relational-databases/replication/codesnippet/tsql/delete-a-pull-subscription_1.sql)]  
  
 [!code-sql[HowTo#sp_droptransubscription](../../relational-databases/replication/codesnippet/tsql/delete-a-pull-subscription_2.sql)]  
  
 Nell'esempio seguente viene eliminata una sottoscrizione pull di una pubblicazione di tipo merge. Il primo batch viene eseguito nel Sottoscrittore, mentre il secondo viene eseguito nel server di pubblicazione.  
  
 [!code-sql[HowTo#sp_dropmergepullsubscription](../../relational-databases/replication/codesnippet/tsql/delete-a-pull-subscription_3.sql)]  
  
 [!code-sql[HowTo#sp_dropmergesubscription](../../relational-databases/replication/codesnippet/tsql/delete-a-pull-subscription_4.sql)]  
  
##  <a name="RMOProcedure"></a> Utilizzo di RMO (Replication Management Objects)  
 È possibile eliminare sottoscrizioni pull a livello di programmazione tramite gli oggetti RMO (Replication Management Objects). Le classi RMO utilizzate per l'eliminazione di una sottoscrizione pull dipendono dal tipo di pubblicazione per cui viene creata la sottoscrizione pull.  
  
#### <a name="to-delete-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a>Per eliminare una sottoscrizione pull di una pubblicazione snapshot o transazionale  
  
1.  Creare una connessione sia al Sottoscrittore che al server di pubblicazione tramite la classe <xref:Microsoft.SqlServer.Management.Common.ServerConnection>.  
  
2.  Creare un'istanza della classe <xref:Microsoft.SqlServer.Replication.TransPullSubscription> e impostare le proprietà <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A> e <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>. Usare la connessione al Sottoscrittore del passaggio 1 per impostare la proprietà <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Controllare la proprietà <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> per verificare che la sottoscrizione esista. Se il valore di questa proprietà è **false**, le proprietà di sottoscrizioni sono state definite in modo non corretto nel passaggio 2 oppure la sottoscrizione non esiste.  
  
4.  Chiamare il metodo <xref:Microsoft.SqlServer.Replication.PullSubscription.Remove%2A>.  
  
5.  Creare un'istanza della classe <xref:Microsoft.SqlServer.Replication.TransPublication> usando la connessione al server di pubblicazione creata nel passaggio 1. Specificare <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> e <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
6.  Chiamare il metodo <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A>. Se il metodo restituisce **false**, le proprietà specificate nel passaggio 5 non sono corrette oppure la pubblicazione non esiste nel server.  
  
7.  Chiamare il metodo <xref:Microsoft.SqlServer.Replication.TransPublication.RemovePullSubscription%2A>. Specificare il nome del Sottoscrittore e il database di sottoscrizione per i parametri *subscriber* e *subscriberDB* .  
  
#### <a name="to-delete-a-pull-subscription-to-a-merge-publication"></a>Per eliminare una sottoscrizione pull di una pubblicazione di tipo merge  
  
1.  Creare una connessione sia al Sottoscrittore che al server di pubblicazione tramite la classe <xref:Microsoft.SqlServer.Management.Common.ServerConnection>.  
  
2.  Creare un'istanza della classe <xref:Microsoft.SqlServer.Replication.MergePullSubscription> e impostare le proprietà <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A> e <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>. Usare la connessione del passaggio 1 per impostare la proprietà <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Controllare la proprietà <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> per verificare che la sottoscrizione esista. Se il valore di questa proprietà è **false**, le proprietà di sottoscrizioni sono state definite in modo non corretto nel passaggio 2 oppure la sottoscrizione non esiste.  
  
4.  Chiamare il metodo <xref:Microsoft.SqlServer.Replication.PullSubscription.Remove%2A>.  
  
5.  Creare un'istanza della classe <xref:Microsoft.SqlServer.Replication.MergePublication> usando la connessione al server di pubblicazione creata nel passaggio 1. Specificare <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> e <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
6.  Chiamare il metodo <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A>. Se il metodo restituisce **false**, le proprietà specificate nel passaggio 5 non sono corrette oppure la pubblicazione non esiste nel server.  
  
7.  Chiamare il metodo <xref:Microsoft.SqlServer.Replication.MergePublication.RemovePullSubscription%2A>. Specificare il nome del Sottoscrittore e il database di sottoscrizione per i parametri *subscriber* e *subscriberDB* .  
  
###  <a name="PShellExample"></a> Esempi (RMO)  
 In questo esempio viene eliminata una sottoscrizione pull a una pubblicazione transazionale e viene rimossa la registrazione della sottoscrizione nel server di pubblicazione.  
  
 [!code-cs[HowTo#rmo_DropTranPullSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_droptranpullsub)]  
  
 [!code-vb[HowTo#rmo_vb_DropTranPullSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_droptranpullsub)]  
  
 In questo esempio viene eliminata una sottoscrizione pull a una pubblicazione di tipo merge e viene rimossa la registrazione della sottoscrizione nel server di pubblicazione.  
  
 [!code-cs[HowTo#rmo_DropMergePullSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_dropmergepullsub)]  
  
 [!code-vb[HowTo#rmo_vb_DropMergePullSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_dropmergepullsub)]  
  
## <a name="see-also"></a>Vedere anche  
 [Sottoscrivere le pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)   
 [Replication Security Best Practices](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  
