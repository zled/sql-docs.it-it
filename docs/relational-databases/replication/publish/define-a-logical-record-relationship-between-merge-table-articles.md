---
title: "Definizione di una relazione tra record logici degli articoli di tabelle di merge | Microsoft Docs"
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
  - "record logici di replica di tipo merge [replica di SQL Server]"
  - "articoli [replica di SQL Server], record logici"
  - "record logici [replica di SQL Server]"
ms.assetid: ff847b3a-c6b0-4eaf-b225-2ffc899c5558
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# Definizione di una relazione tra record logici degli articoli di tabelle di merge
  In questo argomento viene descritto come definire una relazione tra record logici tra articoli di tabella del merge in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] o RMO (Replication Management Objects).  
  
 La replica di tipo merge consente di definire una relazione tra righe correlate in tabelle diverse. Queste righe possono quindi essere elaborate come un'unità transazionale durante la sincronizzazione. È possibile definire un record logico tra due articoli indipendentemente dal fatto che per essi sia stata definita una relazione tra filtri di join. Per ulteriori informazioni, vedere [modifiche a un gruppo di righe correlate con record logici](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
-   **Per definire una relazione tra record logici degli articoli di tabelle di merge, utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Oggetti RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Se si aggiunge, modifica o elimina un record logico dopo che sono state inizializzate sottoscrizioni per la pubblicazione, è necessario generare un nuovo snapshot e reinizializzare tutte le sottoscrizioni in seguito alla modifica. Per ulteriori informazioni sui requisiti per le modifiche alle proprietà, vedere [Modifica proprietà della pubblicazione e articolo](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Definire record logici nella **Aggiungi Join** la finestra di dialogo, disponibile nella creazione guidata pubblicazione e la **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo. Per ulteriori informazioni sull'utilizzo della procedura guidata e l'accesso nella finestra di dialogo, vedere [creare una pubblicazione](../../../relational-databases/replication/publish/create-a-publication.md) e [visualizzare e modificare le proprietà di pubblicazione](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
 È possibile definire record logici nella finestra di dialogo **Aggiungi join** solo se vengono applicati a un filtro join di una pubblicazione di tipo merge e la pubblicazione soddisfa i requisiti per l'utilizzo di partizioni pre-calcolate. Per definire record logici che non vengono applicati a filtri di join e per impostare il rilevamento e la risoluzione dei conflitti a livello di record logici, è necessario utilizzare le stored procedure.  
  
#### Per definire una relazione tra record logici  
  
1.  Nel **filtro righe tabella** pagina della procedura guidata nuova pubblicazione o **Filtra righe** pagina della **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, selezionare un filtro di riga nel **tabelle filtrate** riquadro.  
  
     A una relazione tra record logici è associato un filtro join che estende un filtro di riga. È pertanto necessario definire un filtro di riga prima di poter estendere il filtro con un join e applicare una relazione tra record logici. Dopo aver definito un filtro join, è possibile estenderlo con un altro filtro join. Per ulteriori informazioni sulla definizione di filtri join, vedere [Define and Modify a Join Filter Between Merge Articles](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
2.  Fare clic su **Aggiungi**e quindi su **Aggiungi join per estendere il filtro selezionato**.  
  
3.  Nella finestra di dialogo **Aggiungi join** definire un filtro join e quindi selezionare la casella di controllo **Record logico**.  
  
4.  Se è la **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, fare clic su **OK** per salvare e chiudere la finestra di dialogo.  
  
#### Per eliminare una relazione tra record logici  
  
-   Eliminare solo la relazione tra record logici oppure eliminare la relazione e il filtro join ad essa associato.  
  
     Per eliminare solo la relazione tra record logici:  
  
    1.  Nel **filtro righe** pagina della procedura guidata nuova pubblicazione o **filtro righe** pagina del **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, selezionare il filtro di join associato la relazione tra record logici nel **tabelle filtrate** riquadro e quindi fare clic su **modificare**.  
  
    2.  Nella finestra di dialogo **Modifica join** deselezionare la casella di controllo **Record logico**.  
  
    3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     Per eliminare la relazione tra record logici e il filtro join ad essa associato:  
  
    -   Nel **Filtra righe** pagina della procedura guidata nuova pubblicazione o **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, selezionare un filtro nel **tabelle filtrate** riquadro e quindi fare clic su **eliminare**. Se il filtro di join eliminato è esteso da altri join, anch'essi verranno eliminati.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 Per specificare a livello di programmazione relazioni tra record logici tra gli articoli, è possibile utilizzare stored procedure di replica.  
  
#### Per definire una relazione tra record logici senza un filtro di join associato  
  
1.  Se la pubblicazione contiene tutti gli articoli che vengono filtrati, eseguire [sp_helpmergepublication](../../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md), e prendere nota del valore di **use_partition_groups** nel set di risultati.  
  
    -   Se il valore è **1**, le partizioni calcolate vengono già utilizzate.  
  
    -   Se il valore è **0**, quindi eseguire [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md) nel server di pubblicazione nel database di pubblicazione. Specificare un valore di **use_partition_groups** per **@property** e il valore **true** per **@value**.  
  
        > [!NOTE]  
        >  Se la pubblicazione non supporta le partizioni calcolate, non sarà possibile utilizzare i record logici. Per ulteriori informazioni, vedere requisiti per l'utilizzo delle partizioni precalcolate nell'argomento [Ottimizza prestazioni filtro con parametri con le partizioni precalcolate](../../../relational-databases/replication/merge/optimize-parameterized-filter-performance-with-precomputed-partitions.md).  
  
    -   Se il valore è NULL, è necessario eseguire l'agente snapshot per generare lo snapshot iniziale per la pubblicazione.  
  
2.  Se gli articoli che costituiscono il record logico non esistono, eseguire [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) nel server di pubblicazione nel database di pubblicazione. Specificare una delle opzioni di rilevamento e risoluzione dei conflitti seguenti per il record logico:  
  
    -   Per rilevare e risolvere i conflitti che si verificano all'interno di righe correlate del record logico, specificare un valore di **true** per **@logical_record_level_conflict_detection** e **@logical_record_level_conflict_resolution**.  
  
    -   Per utilizzare il rilevamento dei conflitti standard o colonna a livello di riga e la risoluzione, specificare un valore di **false** per **@logical_record_level_conflict_detection** e **@logical_record_level_conflict_resolution**, ossia l'impostazione predefinita.  
  
3.  Ripetere il passaggio 2 per ogni articolo che includerà il record logico. È necessario utilizzare la stessa opzione di rilevamento e risoluzione dei conflitti per ogni articolo del record logico. Per altre informazioni, vedere [Detecting and Resolving Conflicts in Logical Records](../../../relational-databases/replication/merge/detecting-and-resolving-conflicts-in-logical-records.md).  
  
4.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addmergefilter](../../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md). Specificare **@publication**, il nome di un articolo nella relazione per **@article**, il nome del secondo articolo per **@join_articlename**, un nome per la relazione per **@filtername**, una clausola che definisce la relazione tra i due articoli per **@join_filterclause**, il tipo di join per **@join_unique_key** e uno dei seguenti valori per **@filter_type**:  
  
    -   **2** -definisce una relazione logica.  
  
    -   **3** -definisce una relazione logica con un filtro di join.  
  
    > [!NOTE]  
    >  Se il filtro join non viene utilizzato, la direzione della relazione tra i due articoli non ha rilevanza.  
  
5.  Ripetere il passaggio 2 per tutte le altre relazioni tra record logici incluse nella pubblicazione.  
  
#### Per modificare l'opzione di rilevamento e risoluzione dei conflitti per i record logici  
  
1.  Per rilevare e risolvere conflitti che si verificano all'interno di righe correlate nel record logico:  
  
    -   Server di pubblicazione nel database di pubblicazione, eseguire [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Specificare un valore di **logical_record_level_conflict_detection** per **@property** e il valore **true** per **@value**. Specificare un valore di **1** per **@force_invalidate_snapshot** e **@force_reinit_subscription**.  
  
    -   Server di pubblicazione nel database di pubblicazione, eseguire [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Specificare un valore di **logical_record_level_conflict_resolution** per **@property** e il valore **true** per **@value**. Specificare un valore di **1** per **@force_invalidate_snapshot** e **@force_reinit_subscription**.  
  
2.  Per utilizzare l'opzione standard di rilevamento e risoluzione dei conflitti a livello di riga o di colonna:  
  
    -   Server di pubblicazione nel database di pubblicazione, eseguire [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Specificare un valore di **logical_record_level_conflict_detection** per **@property** e il valore **false** per **@value**. Specificare un valore di **1** per **@force_invalidate_snapshot** e **@force_reinit_subscription**.  
  
    -   Server di pubblicazione nel database di pubblicazione, eseguire [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Specificare un valore di **logical_record_level_conflict_resolution** per **@property** e il valore **false** per **@value**. Specificare un valore di **1** per **@force_invalidate_snapshot** e **@force_reinit_subscription**.  
  
#### Per rimuovere una relazione tra record logici  
  
1.  Nel database di pubblicazione del server di pubblicazione eseguire la query seguente per restituire informazioni su tutte le relazioni tra record logici definite per la pubblicazione specificata:  
  
     [!code-sql[HowTo#sp_ReturnMergeLogicalRecords](../../../relational-databases/replication/codesnippet/tsql/define-a-logical-record-_1.sql)]  
  
     Si noti il nome della relazione tra record logici da rimuovere nella colonna **filtername** del set di risultati.  
  
    > [!NOTE]  
    >  Questa query restituisce le stesse informazioni [sp_helpmergefilter](../../../relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql.md); tuttavia, stored procedure di sistema solo restituisce informazioni sulle relazioni tra record logici che sono anche a filtri join.  
  
2.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_dropmergefilter](../../../relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql.md). Specificare **@publication**, il nome di uno degli articoli della relazione per **@article**e il nome della relazione ottenuto al passaggio 1 per **@filtername**.  
  
###  <a name="TsqlExample"></a> Esempio (Transact-SQL)  
 In questo esempio le partizioni pre-calcolate vengono abilitate in una pubblicazione esistente e viene creato un record logico che comprende i due nuovi articoli per le tabelle `SalesOrderHeader` e `SalesOrderDetail` .  
  
 [!code-sql[HowTo#sp_AddMergeLogicalRecord](../../../relational-databases/replication/codesnippet/tsql/define-a-logical-record-_2.sql)]  
  
##  <a name="RMOProcedure"></a> Utilizzo di RMO (Replication Management Objects)  
  
> [!NOTE]  
>  La replica di tipo merge consente di specificare che i conflitti vengano rilevati e risolti a livello di record logico. Queste opzioni tuttavia non possono essere impostate tramite RMO.  
  
#### Per definire una relazione tra record logici senza un filtro di join associato  
  
1.  Creare una connessione al server di pubblicazione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza del <xref:Microsoft.SqlServer.Replication.MergePublication> classe, impostare il <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> e <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> proprietà per la pubblicazione, quindi impostare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà per la connessione creata nel passaggio 1.  
  
3.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo per ottenere le proprietà dell'oggetto. Se questo metodo restituisce **false**, le proprietà della pubblicazione sono state definite in modo non corretto nel passaggio 2 oppure la pubblicazione non esiste.  
  
4.  Se il <xref:Microsoft.SqlServer.Replication.MergePublication.PartitionGroupsOption%2A> è impostata su <xref:Microsoft.SqlServer.Replication.PartitionGroupsOption.False>, impostarlo su <xref:Microsoft.SqlServer.Replication.PartitionGroupsOption.True>.  
  
5.  Se gli articoli che dovranno includere il record logico non esistono, creare un'istanza di <xref:Microsoft.SqlServer.Replication.MergeArticle> classe e impostare le proprietà seguenti:  
  
    -   Il nome dell'articolo per <xref:Microsoft.SqlServer.Replication.Article.Name%2A>.  
  
    -   Il nome della pubblicazione per <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>.  
  
    -   (Facoltativo) Se l'articolo è filtrato orizzontalmente, specificare la clausola di filtro di riga per il <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> proprietà. Utilizzare questa proprietà per specificare un filtro di riga statico o con parametri. Per altre informazioni, vedere [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
     Per altre informazioni, vedere [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
6.  Chiamare il <xref:Microsoft.SqlServer.Replication.Article.Create%2A> metodo.  
  
7.  Ripetere i passaggi 5 e 6 per ogni articolo che includerà il record logico.  
  
8.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> classe per definire la relazione tra record logici tra gli articoli. Impostare quindi le proprietà seguenti:  
  
    -   Il nome dell'articolo figlio nella relazione tra record logici per il <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.ArticleName%2A> proprietà.  
  
    -   Il nome dell'articolo padre esistente, la relazione tra record logici per il <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinArticleName%2A> proprietà.  
  
    -   Un nome per la relazione tra record logici per il <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterName%2A> proprietà.  
  
    -   L'espressione che definisce la relazione affinché il <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinFilterClause%2A> proprietà.  
  
    -   Un valore di <xref:Microsoft.SqlServer.Replication.FilterTypes.LogicalRecordLink> per il <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterTypes%2A> proprietà. Se la relazione tra record logici è anche un filtro di join, specificare un valore di <xref:Microsoft.SqlServer.Replication.FilterTypes.JoinFilterAndLogicalRecordLink> per questa proprietà. Per ulteriori informazioni, vedere [modifiche a un gruppo di righe correlate con record logici](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
9. Chiamare il <xref:Microsoft.SqlServer.Replication.MergeArticle.AddMergeJoinFilter%2A> metodo sull'oggetto che rappresenta l'articolo figlio nella relazione. Passare il <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> oggetto indicato nel passaggio 8 per definire la relazione.  
  
10. Ripetere i passaggi 8 e 9 per tutte le altre relazioni tra record logici incluse nella pubblicazione.  
  
###  <a name="PShellExample"></a> Esempio (RMO)  
 In questo esempio viene creato un record logico che comprende i due nuovi articoli per le tabelle `SalesOrderHeader` e `SalesOrderDetail` .  
  
 [!code-csharp[HowTo#rmo_CreateLogicalRecord](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createlogicalrecord)]  
  
 [!code-vb[HowTo#rmo_vb_CreateLogicalRecord](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createlogicalrecord)]  
  
## Vedere anche  
 [Definizione e modifica di un filtro di join tra articoli di merge](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)   
 [Definizione e modifica di un filtro di riga con parametri per un articolo di merge](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)   
 [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)   
 [Raggruppamento di modifiche alla righe correlate con record logici](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)   
 [Ottimizzazione delle prestazioni dei filtri con parametri con le partizioni pre-calcolate](../../../relational-databases/replication/merge/optimize-parameterized-filter-performance-with-precomputed-partitions.md)   
 [Raggruppamento di modifiche alla righe correlate con record logici](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)  
  
  