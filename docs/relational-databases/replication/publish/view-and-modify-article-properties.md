---
title: "Visualizzazione e modifica delle propriet&#224; degli articoli | Microsoft Docs"
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
  - "sp_changearticle"
  - "sp_helparticle"
  - "visualizzazione di proprietà di replica"
  - "sp_changemergearticle"
  - "sp_helpmergearticle"
  - "modifica delle proprietà di replica, articoli"
  - "articoli [replica di SQL Server], modifica"
  - "articoli [replica di SQL Server], proprietà"
ms.assetid: e71831fa-3d39-4e4a-9706-4d3a497082cc
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# Visualizzazione e modifica delle propriet&#224; degli articoli
  In questo argomento viene descritto come modificare le proprietà degli articoli in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] o RMO (Replication Management Objects).  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Indicazioni](#Recommendations)  
  
-   **Per visualizzare e modificare le proprietà degli articoli, utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Oggetti RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Alcune proprietà non possono essere modificate dopo la creazione di una pubblicazione, mentre altre proprietà non possono essere modificate se sono presenti sottoscrizioni alla pubblicazione. Le proprietà che non possono essere modificate vengono visualizzate come di sola lettura.  
  
###  <a name="Recommendations"></a> Indicazioni  
  
-   Dopo la creazione di una pubblicazione, per alcune modifiche delle proprietà è necessario un nuovo snapshot. Se la pubblicazione dispone di sottoscrizioni, per alcune modifiche è inoltre necessario reinizializzare tutte le sottoscrizioni. Per ulteriori informazioni, vedere [Modifica proprietà della pubblicazione e articolo](../../../relational-databases/replication/publish/change-publication-and-article-properties.md) e [eliminare articoli da pubblicazioni esistenti e aggiungere articoli alla](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Consente di visualizzare e modificare le proprietà di articolo nella **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, disponibile in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] e Monitoraggio replica. Per informazioni sull'avvio di monitoraggio replica, vedere [avviare Monitoraggio replica](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
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
  
#### Per visualizzare e modificare le proprietà degli articoli  
  
1.  Nel **articoli** pagina della **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, selezionare un articolo e quindi fare clic su **Proprietà articolo**.  
  
2.  Selezionare gli articoli a cui si applicano le modifiche delle proprietà:  
  
    -   Fare clic su **impostare proprietà di evidenziate \< ObjectType> articolo** per avviare il **Proprietà articolo - \< ObjectName>** la finestra di dialogo; Proprietà le modifiche apportate in questa finestra di dialogo vengono applicate solo all'oggetto evidenziato nel riquadro degli oggetti nel **articoli** pagina.  
  
    -   Fare clic su **impostare le proprietà di tutti \< ObjectType> articoli**, per avviare il **le proprietà per tutti \< ObjectType> articoli** la finestra di dialogo; Proprietà le modifiche apportate in questa finestra di dialogo vengono applicate a tutti gli oggetti di quel tipo nel riquadro degli oggetti nel **articoli** pagina, inclusi quelli non ancora selezionati per la pubblicazione.  
  
        > [!NOTE]  
        >  Modifiche delle proprietà apportate nel **le proprietà per tutti \< ObjectType> articoli** la finestra di dialogo sostituire qualsiasi apportate in precedenza il **Proprietà articolo - \< ObjectName>** la finestra di dialogo. Se ad esempio si desidera impostare alcuni valori predefiniti per tutti gli articoli di un tipo di oggetto e, al contempo, alcune proprietà per singoli oggetti, è necessario impostare innanzitutto i valori predefiniti per tutti gli articoli, quindi le proprietà relative ai singoli oggetti.  
  
3.  Se necessario, modificare le proprietà e quindi fare clic su **OK**.  
  
4.  Fare clic su **OK** sulla **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 È possibile modificare gli articoli e restituire a livello di programmazione le relative proprietà tramite le stored procedure di replica. Le stored procedure utilizzate dipenderanno dal tipo di pubblicazione a cui appartiene l'articolo.  
  
#### Per visualizzare le proprietà di un articolo appartenente a una pubblicazione snapshot o transazionale  
  
1.  Eseguire [sp_helparticle](../../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md), specificando il nome della pubblicazione per il **@publication** parametro e il nome dell'articolo per il **@article** parametro. Se **@article**viene omesso, verranno restituite informazioni su tutti gli articoli della pubblicazione.  
  
2.  Eseguire [sp_helparticlecolumns](../../../relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql.md) per gli articoli di tabella per elencare tutte le colonne disponibili nella tabella di base.  
  
#### Per modificare le proprietà di un articolo appartenente a una pubblicazione snapshot o transazionale  
  
1.  Eseguire [sp_changearticle](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md), specificando la proprietà dell'articolo da modificare nel **@property** parametro e il nuovo valore di questa proprietà nel **@value** parametro.  
  
    > [!NOTE]  
    >  Se la modifica richiede la generazione di un nuovo snapshot, è necessario specificare anche un valore di **1** per **@force_invalidate_snapshot**, e se la modifica richiede la reinizializzazione dei sottoscrittori, è necessario specificare anche un valore di **1** per **@force_reinit_subscription**. Per ulteriori informazioni sulle proprietà che, quando è cambiato, richiedono un nuovo snapshot o la reinizializzazione, vedere [Modifica proprietà della pubblicazione e articolo](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
#### Per visualizzare le proprietà di un articolo appartenente a una pubblicazione di tipo merge  
  
1.  Eseguire [sp_helpmergearticle](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md), specificando il nome della pubblicazione per il **@publication** parametro e il nome dell'articolo per il **@article** parametro. Se questi parametri vengono omessi, verranno restituite informazioni su tutti gli articoli della pubblicazione o del server di pubblicazione.  
  
2.  Eseguire [sp_helpmergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-helpmergearticlecolumn-transact-sql.md) per gli articoli di tabella per elencare tutte le colonne disponibili nella tabella di base.  
  
#### Per modificare le proprietà di un articolo appartenente a una pubblicazione di tipo merge  
  
1.  Eseguire [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), specificando la proprietà dell'articolo da modificare nel **@property** parametro e il nuovo valore di questa proprietà nel **@value** parametro.  
  
    > [!NOTE]  
    >  Se la modifica richiede la generazione di un nuovo snapshot, è necessario specificare anche un valore di **1** per **@force_invalidate_snapshot**, e se la modifica richiede la reinizializzazione dei sottoscrittori, è necessario specificare anche un valore di **1** per **@force_reinit_subscription**. Per ulteriori informazioni sulle proprietà che, quando è cambiato, richiedono un nuovo snapshot o la reinizializzazione, vedere [Modifica proprietà della pubblicazione e articolo](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
###  <a name="TsqlExample"></a> Esempio (Transact-SQL)  
 In questo esempio di replica transazionale vengono restituite le proprietà dell'articolo pubblicato.  
  
 [!code-sql[HowTo#sp_helptranarticle](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-article-_1.sql)]  
  
 In questo esempio di replica transazionale vengono modificate le opzioni dello schema per l'articolo pubblicato.  
  
 [!code-sql[HowTo#sp_changetranarticle](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-article-_2.sql)]  
  
 In questo esempio di replica di tipo merge vengono restituite le proprietà dell'articolo pubblicato.  
  
 [!code-sql[HowTo#sp_helpmergearticle](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-article-_3.sql)]  
  
 In questo esempio di replica di tipo merge vengono modificate le impostazioni di rilevamento dei conflitti per un articolo pubblicato.  
  
 [!code-sql[HowTo#sp_changemergearticle](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-article-_4.sql)]  
  
##  <a name="RMOProcedure"></a> Utilizzo di RMO (Replication Management Objects)  
 È possibile modificare gli articoli e accedere alle relative proprietà a livello di programmazione utilizzando oggetti RMO (Replication Management Objects). Le classi RMO utilizzate per la visualizzazione o la modifica degli articoli dipendono dal tipo di pubblicazione cui appartiene l'articolo.  
  
#### Per visualizzare o modificare le proprietà di un articolo che appartiene a una pubblicazione snapshot o transazionale  
  
1.  Creare una connessione al server di pubblicazione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.TransArticle> (classe).  
  
3.  Impostare il <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, e <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> proprietà.  
  
4.  Impostare la connessione del passaggio 1 per il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà.  
  
5.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo per ottenere le proprietà dell'oggetto. Se questo metodo restituisce **false**, le proprietà dell'articolo sono state definite in modo non corretto nel passaggio 3 oppure l'articolo non esiste.  
  
6.  (Facoltativo) Per modificare le proprietà, impostare un nuovo valore per uno del <xref:Microsoft.SqlServer.Replication.TransArticle> proprietà che possono essere impostate.  
  
7.  (Facoltativo) Se si specifica un valore di **true** per <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> per eseguire il commit delle modifiche nel server. Se si specifica un valore di **false** per <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (impostazione predefinita), le modifiche vengono inviate al server immediatamente.  
  
#### Per visualizzare o modificare le proprietà di un articolo che appartiene a una pubblicazione di tipo merge  
  
1.  Creare una connessione al server di pubblicazione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.MergeArticle> (classe).  
  
3.  Impostare il <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, e <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> proprietà.  
  
4.  Impostare la connessione del passaggio 1 per il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà.  
  
5.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo per ottenere le proprietà dell'oggetto. Se questo metodo restituisce **false**, le proprietà dell'articolo sono state definite in modo non corretto nel passaggio 3 oppure l'articolo non esiste.  
  
6.  (Facoltativo) Per modificare le proprietà, impostare un nuovo valore per uno del <xref:Microsoft.SqlServer.Replication.MergeArticle> proprietà che possono essere impostate.  
  
7.  (Facoltativo) Se si specifica un valore di **true** per <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> per eseguire il commit delle modifiche nel server. Se si specifica un valore di **false** per <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (impostazione predefinita), le modifiche vengono inviate al server immediatamente.  
  
###  <a name="PShellExample"></a> Esempio (RMO)  
 In questo esempio viene modificato un articolo di merge per specificare il gestore della logica di business utilizzato dall'articolo.  
  
 [!code-csharp[HowTo#rmo_ChangeMergeArticle_BLH](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_changemergearticle_blh)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergeArticle_BLH](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_changemergearticle_blh)]  
  
## Vedere anche  
 [Implementazione di un gestore della logica di business per un articolo di merge](../../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)   
 [Pubblicazione di dati e oggetti di database](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Modifica delle proprietà di pubblicazioni e articoli](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Concetti di base relativi alle stored procedure del sistema di replica](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Rilevamento e risoluzione avanzati dei conflitti nella replica di tipo merge](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  