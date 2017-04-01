---
title: "Eliminazione di una pubblicazione | Microsoft Docs"
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
  - "rimozione di pubblicazioni"
  - "pubblicazioni [replica di SQL Server], eliminazione"
  - "articoli [replica di SQL Server], eliminazione"
  - "eliminazione di pubblicazioni"
ms.assetid: 408a1360-12ee-4896-ac94-482ae839593b
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# Eliminazione di una pubblicazione
  In questo argomento viene descritto come eliminare una pubblicazione in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] o RMO (Replication Management Objects).  
  
 **Contenuto dell'argomento**  
  
-   **Per eliminare una pubblicazione, utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Oggetti RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Eliminare le pubblicazioni dalla cartella **Pubblicazioni locali** in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
#### Per eliminare una pubblicazione  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Pubblicazioni locali** .  
  
3.  Fare doppio clic su di pubblicazione che si desidera eliminare e quindi fare clic su **eliminare**.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 È possibile eliminare pubblicazioni a livello di programmazione tramite le stored procedure di replica. Le stored procedure utilizzate dipendono dal tipo di pubblicazione eliminato.  
  
> [!NOTE]  
>  L'eliminazione di una pubblicazione non comporta la rimozione degli oggetti pubblicati dal database di pubblicazione o degli oggetti corrispondenti dal database di sottoscrizione. Utilizzare il comando `DROP <object>` per rimuovere manualmente questi oggetti, se necessario.  
  
#### Per eliminare una pubblicazione snapshot o transazionale  
  
1.  Eseguire una delle operazioni seguenti:  
  
    -   Per eliminare una singola pubblicazione, eseguire [sp_droppublication](../../../relational-databases/system-stored-procedures/sp-droppublication-transact-sql.md) nel server di pubblicazione nel database di pubblicazione.  
  
    -   Per eliminare tutte le pubblicazioni e rimuovere tutti gli oggetti di replica da un database pubblicato, eseguire [sp_removedbreplication](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) nel server di pubblicazione. Specificare il valore **tran** per **@type**. (Facoltativo) Se il server di distribuzione non è accessibile o se lo stato del database è sospetto oppure offline, specificare un valore di **1** per **@force**. (Facoltativo) Specificare il nome del database per **@dbname** Se [sp_removedbreplication](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) non viene eseguita nel database di pubblicazione.  
  
        > [!NOTE]  
        >  Se si specifica un valore di **1** per **@force** potrebbe lasciare gli oggetti di pubblicazione correlate alla replica nel database.  
  
2.  (Facoltativo) Se questo database non contiene altre pubblicazioni, eseguire [sp_replicationdboption & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md) Per disabilitare la pubblicazione del database corrente utilizzando la replica transazionale o snapshot.  
  
3.  (Facoltativo) Nel database di sottoscrizione del sottoscrittore, eseguire [sp_subscription_cleanup](../../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md) per rimuovere eventuali metadati di replica rimanenti nel database di sottoscrizione.  
  
#### Per eliminare una pubblicazione di tipo merge  
  
1.  Eseguire una delle operazioni seguenti:  
  
    -   Per eliminare una singola pubblicazione, eseguire [sp_dropmergepublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-dropmergepublication-transact-sql.md) nel server di pubblicazione nel database di pubblicazione.  
  
    -   Per eliminare tutte le pubblicazioni e rimuovere tutti gli oggetti di replica da un database pubblicato, eseguire [sp_removedbreplication](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) nel server di pubblicazione. Specificare il valore **merge** per **@type**. (Facoltativo) Se il server di distribuzione non è accessibile o se lo stato del database è sospetto oppure offline, specificare un valore di **1** per **@force**. (Facoltativo) Specificare il nome del database per **@dbname** Se [sp_removedbreplication](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) non viene eseguita nel database di pubblicazione.  
  
        > [!NOTE]  
        >  Se si specifica un valore di **1** per **@force** potrebbe lasciare gli oggetti di pubblicazione correlate alla replica nel database.  
  
2.  (Facoltativo) Se questo database non contiene altre pubblicazioni, eseguire [sp_replicationdboption & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md) Per disabilitare la pubblicazione del database corrente utilizzando la replica di tipo merge.  
  
3.  (Facoltativo) Nel database di sottoscrizione del sottoscrittore, eseguire [sp_mergesubscription_cleanup & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql.md) Per rimuovere eventuali metadati di replica rimanenti nel database di sottoscrizione.  
  
###  <a name="TsqlExample"></a> Esempi (Transact-SQL)  
 In questo esempio viene illustrato come rimuovere una pubblicazione transazionale e disabilitare la pubblicazione transazionale per un database. Si presuppone che in precedenza siano state rimosse tutte le sottoscrizioni. Per ulteriori informazioni, vedere [Delete a Pull Subscription](../../../relational-databases/replication/delete-a-pull-subscription.md) o [Delete a Push Subscription](../../../relational-databases/replication/delete-a-push-subscription.md).  
  
 [!code-sql[HowTo#sp_droppublication](../../../relational-databases/replication/codesnippet/tsql/delete-a-publication_1.sql)]  
  
 In questo esempio viene illustrato come rimuovere una pubblicazione di tipo merge e disabilitare la pubblicazione di tipo merge per un database. Si presuppone che in precedenza siano state rimosse tutte le sottoscrizioni. Per ulteriori informazioni, vedere [Delete a Pull Subscription](../../../relational-databases/replication/delete-a-pull-subscription.md) o [Delete a Push Subscription](../../../relational-databases/replication/delete-a-push-subscription.md).  
  
 [!code-sql[HowTo#sp_dropmergepublication](../../../relational-databases/replication/codesnippet/tsql/delete-a-publication_2.sql)]  
  
##  <a name="RMOProcedure"></a> Utilizzo di RMO (Replication Management Objects)  
 È possibile eliminare pubblicazioni a livello di programmazione tramite gli oggetti RMO (Replication Management Objects). Le classi RMO utilizzate per rimuovere una pubblicazione dipendono dal tipo di pubblicazione rimossa.  
  
#### Per rimuovere una pubblicazione snapshot o transazionale  
  
1.  Creare una connessione al server di pubblicazione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.TransPublication> (classe).  
  
3.  Impostare il <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> e <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> proprietà per la pubblicazione, quindi impostare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà per la connessione creata nel passaggio 1.  
  
4.  Controllare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> proprietà per verificare l'esistenza della pubblicazione. Se il valore di questa proprietà è **false**, le proprietà di pubblicazione sono state definite in modo non corretto nel passaggio 3 oppure la pubblicazione non esiste.  
  
5.  Chiamare il <xref:Microsoft.SqlServer.Replication.Publication.Remove%2A> metodo.  
  
6.  (Facoltativo) Se per il database non esistono altre pubblicazioni transazionali, è possibile disabilitare il database per la pubblicazione transazionale come illustrato di seguito:  
  
    1.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> (classe). Impostare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà all'istanza di <xref:Microsoft.SqlServer.Management.Common.ServerConnection> dal passaggio 1.  
  
    2.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo. Se il metodo restituisce **false**, verificare che il database esista.  
  
    3.  Impostare il <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledTransPublishing%2A> proprietà **false**.  
  
    4.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> metodo.  
  
7.  Chiudere le connessioni.  
  
#### Per rimuovere una pubblicazione di tipo merge  
  
1.  Creare una connessione al server di pubblicazione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.MergePublication> (classe).  
  
3.  Impostare il <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> e <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> proprietà per la pubblicazione, quindi impostare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà per la connessione creata nel passaggio 1.  
  
4.  Controllare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> proprietà per verificare l'esistenza della pubblicazione. Se il valore di questa proprietà è **false**, le proprietà di pubblicazione sono state definite in modo non corretto nel passaggio 3 oppure la pubblicazione non esiste.  
  
5.  Chiamare il <xref:Microsoft.SqlServer.Replication.Publication.Remove%2A> metodo.  
  
6.  (Facoltativo) Se per il database non esistono altre pubblicazioni di tipo merge, è possibile disabilitare il database per la pubblicazione di tipo merge come illustrato di seguito:  
  
    1.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> (classe). Impostare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà all'istanza di <xref:Microsoft.SqlServer.Management.Common.ServerConnection> dal passaggio 1.  
  
    2.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo. Se il metodo restituisce **false**, verificare che il database esista.  
  
    3.  Impostare il <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledMergePublishing%2A> proprietà **false**.  
  
    4.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> metodo.  
  
7.  Chiudere le connessioni.  
  
###  <a name="PShellExample"></a> Esempi (RMO)  
 Nell'esempio seguente viene eliminata una pubblicazione transazionale. Se per il database non esistono altre pubblicazioni transazionali, verrà anche disabilitata la pubblicazione transazionale.  
  
 [!code-csharp[HowTo#rmo_DropTranPub](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_droptranpub)]  
  
 [!code-vb[HowTo#rmo_vb_DropTranPub](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_droptranpub)]  
  
 Nell'esempio seguente viene eliminata una pubblicazione di tipo merge. Se per il database non esistono altre pubblicazioni di tipo merge, verrà anche disabilitata la pubblicazione di tipo merge.  
  
 [!code-csharp[HowTo#rmo_DropMergePub](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_dropmergepub)]  
  
 [!code-vb[HowTo#rmo_vb_DropMergePub](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_dropmergepub)]  
  
## Vedere anche  
 [Concetti di base relativi alle stored procedure del sistema di replica](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Pubblicazione di dati e oggetti di database](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  