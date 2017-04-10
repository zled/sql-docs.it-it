---
title: "Visualizzazione e modifica delle propriet&#224; della pubblicazione | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "visualizzazione di proprietà di replica"
  - "modifica delle proprietà di replica, articoli"
  - "articoli [replica di SQL Server], modifica"
  - "pubblicazioni [replica di SQL Server], proprietà"
  - "articoli [replica di SQL Server], proprietà"
  - "modifica delle proprietà di replica, pubblicazioni"
  - "pubblicazioni [replica di SQL Server], modifica"
ms.assetid: 27d72ea4-bcb6-48f2-b4aa-eb1410da7efc
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# Visualizzazione e modifica delle propriet&#224; della pubblicazione
  In questo argomento viene descritto come modificare le proprietà delle pubblicazioni in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] o RMO (Replication Management Objects).  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Indicazioni](#Recommendations)  
  
-   **Per visualizzare e modificare le proprietà delle pubblicazioni tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Oggetti RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Alcune proprietà non possono essere modificate dopo la creazione di una pubblicazione, mentre altre proprietà non possono essere modificate se sono presenti sottoscrizioni alla pubblicazione. Le proprietà che non possono essere modificate vengono visualizzate come di sola lettura.  
  
###  <a name="Recommendations"></a> Indicazioni  
  
-   Dopo la creazione di una pubblicazione, per alcune modifiche delle proprietà è necessario un nuovo snapshot. Se la pubblicazione dispone di sottoscrizioni, per alcune modifiche è inoltre necessario reinizializzare tutte le sottoscrizioni. Per ulteriori informazioni, vedere [Modifica proprietà della pubblicazione e articolo](../../../relational-databases/replication/publish/change-publication-and-article-properties.md) e [eliminare articoli da pubblicazioni esistenti e aggiungere articoli alla](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Consente di visualizzare e modificare le proprietà di pubblicazione nel **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, disponibile in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] e Monitoraggio replica. Per informazioni sull'avvio di monitoraggio replica, vedere [avviare Monitoraggio replica](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
 Il **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo include le pagine seguenti:  
  
-   Nella pagina **Generale** sono presenti il nome e la descrizione della pubblicazione, il nome del database, il tipo di pubblicazione e le impostazioni di scadenza della sottoscrizione.  
  
-   La pagina **Articoli** corrisponde alla pagina **Articoli** presente nella Creazione guidata nuova pubblicazione. Utilizzare questa pagina per aggiungere ed eliminare articoli e per modificare le proprietà e l'applicazione di filtri a colonne per gli articoli.  
  
-   La pagina **Filtra righe** corrisponde alla pagina **Filtro righe tabella** presente nella Creazione guidata nuova pubblicazione. Utilizzare questa pagina per aggiungere, modificare ed eliminare filtri di righe statici per tutti i tipi di pubblicazioni e aggiungere, modificare ed eliminare filtri di righe con parametri e filtri join per le pubblicazioni di tipo merge.  
  
-   La pagina **Snapshot** consente di specificare il formato e la posizione dello snapshot, se comprimere lo snapshot e gli script da eseguire prima e dopo l'applicazione dello snapshot.  
  
-   Il **FTP Snapshot** pagina (per snapshot e transazionali e pubblicazioni di tipo merge per i server di pubblicazione che eseguono versioni precedenti a SQL Server 2005) consente di specificare se i sottoscrittori possono scaricare i file di snapshot tramite FTP File Transfer Protocol ().  
  
-   Il **FTP Snapshot e Internet** pagina (per pubblicazioni di tipo merge da server di pubblicazione che eseguono SQL Server 2005 o versioni successive) consente di specificare se i sottoscrittori possono scaricare i file di snapshot tramite FTP, e se i sottoscrittori possono sincronizzare le sottoscrizioni tramite HTTPS.  
  
-   Nella pagina **Opzioni della sottoscrizione** è possibile impostare alcune opzioni che si applicano a tutte le sottoscrizioni. Le opzioni variano in relazione al tipo di pubblicazione.  
  
-   La pagina **Elenco accesso pubblicazione** consente di specificare quali account di accesso e gruppi possono accedere a una pubblicazione.  
  
-   La pagina **Sicurezza agente** consente di accedere alle impostazioni degli account utilizzati per l'esecuzione degli agenti seguenti e per la creazione di connessioni ai computer in una topologia di replica: l'agente snapshot per tutte le pubblicazioni, l'agente di lettura log per tutte le pubblicazioni transazionali e l'agente di lettura coda per le pubblicazioni transazionali che consentono sottoscrizioni ad aggiornamento in coda.  
  
-   Il **partizioni di dati** pagina (per pubblicazioni di tipo merge da server di pubblicazione che eseguono SQL Server 2005 o versioni successive) consente di specificare se i sottoscrittori delle pubblicazioni con filtri con parametri possono richiedere uno snapshot, se non è disponibile. In questa pagina è inoltre possibile generare snapshot per una o più partizioni, una sola volta o in base a una pianificazione periodica.  
  
#### Per visualizzare e modificare le proprietà delle pubblicazioni in Management Studio  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Pubblicazioni locali** .  
  
3.  Fare doppio clic su una pubblicazione e quindi fare clic su **proprietà**.  
  
4.  Se necessario, modificare le proprietà e quindi fare clic su **OK**.  
  
#### Per visualizzare e modificare le proprietà delle pubblicazioni in Monitoraggio replica  
  
1.  Espandere un gruppo di server di pubblicazione nel riquadro sinistro di Monitoraggio replica e quindi espandere un server di pubblicazione.  
  
2.  Fare doppio clic su una pubblicazione e quindi fare clic su **proprietà**.  
  
3.  Se necessario, modificare le proprietà e quindi fare clic su **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 È possibile modificare le pubblicazioni e restituire a livello di programmazione le relative proprietà tramite le stored procedure di replica. Le stored procedure utilizzate dipenderanno dal tipo di pubblicazione.  
  
#### Per visualizzare le proprietà di una pubblicazione snapshot o transazionale  
  
1.  Eseguire [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md), specificando il nome della pubblicazione per il **@publication** parametro. Se questo parametro viene omesso, verranno restituite le informazioni su tutte le pubblicazioni disponibili nel server di pubblicazione.  
  
#### Per modificare le proprietà di una pubblicazione snapshot o transazionale  
  
1.  Eseguire [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), specificando la proprietà della pubblicazione da modificare nel **@property** parametro e il nuovo valore di questa proprietà nel **@value** parametro.  
  
    > [!NOTE]  
    >  Se la modifica richiederà la generazione di un nuovo snapshot, è necessario specificare anche un valore di **1** per **@force_invalidate_snapshot**, e se richiederà la reinizializzazione dei sottoscrittori, è necessario specificare un valore di **1** per **@force_reinit_subscription**. Per ulteriori informazioni sulle proprietà che, quando è cambiato, richiedono un nuovo snapshot o la reinizializzazione, vedere [Modifica proprietà della pubblicazione e articolo](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
#### Per visualizzare le proprietà di una pubblicazione di tipo merge  
  
1.  Eseguire [sp_helpmergepublication](../../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md), specificando il nome della pubblicazione per il **@publication** parametro. Se questo parametro viene omesso, verranno restituite le informazioni su tutte le pubblicazioni disponibili nel server di pubblicazione.  
  
#### Per modificare le proprietà di una pubblicazione di tipo merge  
  
1.  Eseguire [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), specificando la proprietà della pubblicazione da modificare nel **@property** parametro e il nuovo valore di questa proprietà nel **@value** parametro.  
  
    > [!NOTE]  
    >  Se la modifica richiederà la generazione di un nuovo snapshot, è necessario specificare anche un valore di **1** per **@force_invalidate_snapshot**, e se richiederà la reinizializzazione dei sottoscrittori, è necessario specificare un valore di **1** per **@force_reinit_subscription** Per ulteriori informazioni sulle proprietà che, quando è cambiato, richiedono un nuovo snapshot o la reinizializzazione, vedere [modificare pubblicazioni e le proprietà di articolo](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
#### Per visualizzare le proprietà di uno snapshot  
  
1.  Eseguire [sp_helppublication_snapshot](../../../relational-databases/system-stored-procedures/sp-helppublication-snapshot-transact-sql.md), specificando il nome della pubblicazione per il **@publication** parametro.  
  
#### Per modificare le proprietà di uno snapshot  
  
1.  Eseguire [sp_changepublication_snapshot](../../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md), specificare uno o più delle proprietà del nuovo snapshot per i parametri appropriati dello snapshot.  
  
###  <a name="TsqlExample"></a> Esempi (Transact-SQL)  
 In questo esempio di replica transazionale vengono restituite le proprietà della pubblicazione.  
  
 [!code-sql[HowTo#sp_helppublication](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-publicat_1.sql)]  
  
 In questo esempio di replica transazionale viene disabilitata la replica dello schema per la pubblicazione.  
  
 [!code-sql[HowTo#sp_changepublication](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-publicat_2.sql)]  
  
 In questo esempio di replica di tipo merge vengono restituite le proprietà della pubblicazione.  
  
 [!code-sql[HowTo#sp_helpmergepublication](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-publicat_3.sql)]  
  
 In questo esempio di replica di tipo merge viene disabilitata la replica dello schema per la pubblicazione.  
  
 [!code-sql[HowTo#sp_changemergepublication](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-publicat_4.sql)]  
  
##  <a name="RMOProcedure"></a> Utilizzo di RMO (Replication Management Objects)  
 È possibile modificare le pubblicazioni e accedere alle relative proprietà a livello di programmazione utilizzando oggetti RMO (Replication Management Objects). Le classi RMO utilizzate per visualizzare o modificare le proprietà della pubblicazione dipendono dal tipo di pubblicazione.  
  
#### Per visualizzare o modificare le proprietà di una pubblicazione snapshot o transazionale  
  
1.  Creare una connessione al server di pubblicazione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza del <xref:Microsoft.SqlServer.Replication.TransPublication> classe, impostare il <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> e <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> proprietà per la pubblicazione, quindi impostare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà per la connessione creata nel passaggio 1.  
  
3.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo per ottenere le proprietà dell'oggetto. Se questo metodo restituisce **false**, le proprietà della pubblicazione sono state definite in modo non corretto nel passaggio 2 oppure la pubblicazione non esiste.  
  
4.  (Facoltativo) Per modificare le proprietà, specificare un nuovo valore per una o più proprietà che è possibile impostare. Utilizzare l'operatore AND logico (**&** in Microsoft Visual c# e **e** in Microsoft Visual Basic) per determinare se un determinato <xref:Microsoft.SqlServer.Replication.PublicationAttributes> è impostato per il <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> proprietà. Utilizzare l'operatore logico OR inclusivo (**|** in Visual c# e **o** in Visual Basic) e l'operatore logico OR esclusivo (**^** in Visual c# e **Xor** in Visual Basic) per modificare il <xref:Microsoft.SqlServer.Replication.PublicationAttributes> i valori per il <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> proprietà.  
  
5.  (Facoltativo) Se si specifica un valore di **true** per <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> per eseguire il commit delle modifiche nel server. Se si specifica un valore di **false** per <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (impostazione predefinita), le modifiche vengono inviate al server immediatamente.  
  
#### Per visualizzare o modificare le proprietà di una pubblicazione di tipo merge  
  
1.  Creare una connessione al server di pubblicazione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza del <xref:Microsoft.SqlServer.Replication.MergePublication> classe, impostare il <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> e <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> proprietà per la pubblicazione, quindi impostare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà per la connessione creata nel passaggio 1.  
  
3.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo per ottenere le proprietà dell'oggetto. Se questo metodo restituisce **false**, le proprietà della pubblicazione sono state definite in modo non corretto nel passaggio 2 oppure la pubblicazione non esiste.  
  
4.  (Facoltativo) Per modificare le proprietà, specificare un nuovo valore per una o più proprietà che è possibile impostare. Utilizzare l'operatore AND logico (**&** in Visual c# e **e** in Visual Basic) per determinare se un determinato <xref:Microsoft.SqlServer.Replication.PublicationAttributes> è impostato per il <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> proprietà. Utilizzare l'operatore logico OR inclusivo (**|** in Visual c# e **o** in Visual Basic) e l'operatore logico OR esclusivo (**^** in Visual c# e **Xor** in Visual Basic) per modificare il <xref:Microsoft.SqlServer.Replication.PublicationAttributes> i valori per il <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> proprietà.  
  
5.  (Facoltativo) Se si specifica un valore di **true** per <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> per eseguire il commit delle modifiche nel server. Se si specifica un valore di **false** per <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (impostazione predefinita), le modifiche vengono inviate al server immediatamente.  
  
###  <a name="PShellExample"></a> Esempi (RMO)  
 In questo esempio vengono impostati gli attributi di pubblicazione per una pubblicazione transazionale. Le modifiche vengono memorizzate nella cache finché non vengono inviate al server in modo esplicito.  
  
 [!code-csharp[HowTo#rmo_ChangeTranPub_cached](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_changetranpub_cached)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeTranPub_cached](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_changetranpub_cached)]  
  
 In questo esempio viene disabilitata la replica DDL per una pubblicazione di tipo merge.  
  
 [!code-csharp[HowTo#rmo_ChangeMergePub_ddl](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_changemergepub_ddl)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergePub_ddl](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_changemergepub_ddl)]  
  
## Vedere anche  
 [Pubblicazione di dati e oggetti di database](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Modifica delle proprietà di pubblicazioni e articoli](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Modifiche allo schema nei database di pubblicazione](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)   
 [Concetti di base relativi alle stored procedure del sistema di replica](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Aggiunta ed eliminazione di articoli di una pubblicazione & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-a-publication.md)   
 [Consente di visualizzare informazioni ed eseguire attività per una pubblicazione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md)   
 [Visualizzazione e modifica delle proprietà degli articoli](../../../relational-databases/replication/publish/view-and-modify-article-properties.md)  
  
  