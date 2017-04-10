---
title: "Pubblicazione di dati e oggetti di database | Microsoft Docs"
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
  - "tipi definiti dall'utente [replica di SQL Server]"
  - "articoli [replica di SQL Server], eliminazione"
  - "oggetti [replica di SQL Server]"
  - "pubblicazioni [replica di SQL Server], creazione"
  - "replica di tipo merge [replica di SQL Server], pubblicazioni"
  - "articoli solo schema [replica di SQL Server]"
  - "pubblicazione [replica di SQL Server], oggetti di database"
  - "articoli [replica di SQL Server], definizione"
  - "pubblicazione [replica di SQL Server], funzioni"
  - "replica [SQL Server], pubblicazioni"
  - "pubblicazione [replica di SQL Server], viste"
  - "tabelle [replica di SQL Server]"
  - "schemi [replica di SQL Server]"
  - "pubblicazione [replica di SQL Server], dati"
  - "schemi [replica di SQL Server], pubblicazione"
  - "articoli [replica di SQL Server], stored procedure e"
  - "pubblicazione [replica di SQL Server], tabelle"
  - "tipi di dati alias [replica di SQL Server]"
  - "pubblicazioni [replica di SQL Server], eliminazione"
  - "replica snapshot [SQL Server], pubblicazioni"
  - "articoli [replica di SQL Server], modifica"
  - "replica transazionale, pubblicazioni"
  - "pubblicazione [replica di SQL Server], stored procedure"
  - "pubblicazione [replica di SQL Server]"
  - "viste [replica di SQL Server]"
  - "stored procedure [replica di SQL Server], pubblicazione"
  - "pubblicazioni [replica di SQL Server], opzioni dello schema"
  - "articoli [replica di SQL Server], aggiunta"
  - "pubblicazioni [replica di SQL Server], modifica"
  - "funzioni definite dall'utente [replica di SQL Server]"
ms.assetid: d986032c-3387-4de1-a435-3ec5e82185a2
caps.latest.revision: 83
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 83
---
# Pubblicazione di dati e oggetti di database
  Quando si crea una pubblicazione, è possibile scegliere le tabelle e gli altri oggetti di database che si desidera pubblicare. Tramite la replica è possibile pubblicare gli oggetti di database elencati di seguito.  
  
|Oggetto di database|Replica snapshot e replica transazionale|Replica di tipo merge|  
|---------------------|--------------------------------------------------------|-----------------------|  
|Tabelle|X|X|  
|Tabelle partizionate|X|X|  
|Stored procedure - definizione ([!INCLUDE[tsql](../../../includes/tsql-md.md)] e CLR)|X|X|  
|Stored procedure - esecuzione ([!INCLUDE[tsql](../../../includes/tsql-md.md)] e CLR)|X|no|  
|Viste|X|X|  
|Viste indicizzate|X|X|  
|Viste indicizzate come tabelle|X|no|  
|Tipi definiti dall'utente (CLR)|X|X|  
|Funzioni definite dall'utente ([!INCLUDE[tsql](../../../includes/tsql-md.md)] e CLR).|X|X|  
|Tipi di dati alias|X|X|  
|Indici full-text|X|X|  
|Oggetti dello schema (vincoli, indici, trigger DML dell'utente, proprietà estese e regole di confronto)|X|X|  
  
## Creazione di pubblicazioni  
 Per creare una pubblicazione, si specificano le informazioni seguenti:  
  
-   Server di distribuzione.  
  
-   Percorso dei file di snapshot.  
  
-   Database di pubblicazione.  
  
-   Tipo di pubblicazione da creare (snapshot, transazionale, transazionale con sottoscrizioni aggiornabili o di tipo merge).  
  
-   Dati e oggetti di database (articoli) da includere nella pubblicazione.  
  
-   Filtri di colonna e filtri di riga statici per tutti i tipi di pubblicazioni, nonché filtri join e filtri di riga con parametri per le pubblicazioni di tipo merge.  
  
-   Pianificazione dell'agente snapshot.  
  
-   Account usati per l'esecuzione degli agenti seguenti: agente snapshot per tutte le pubblicazioni, agente di lettura log per tutte le pubblicazioni transazionali e agente di lettura coda per tutte le pubblicazioni transazionali che consentono sottoscrizioni aggiornabili.  
  
-   Nome e descrizione della pubblicazione.  
  
 Per informazioni sull'utilizzo di pubblicazioni, vedere gli argomenti seguenti:  
  
-   [Creazione di una pubblicazione](../../../relational-databases/replication/publish/create-a-publication.md)  
  
-   [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)  
  
-   [Visualizzazione e modifica delle proprietà della pubblicazione](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)  
  
-   [Visualizzazione e modifica delle proprietà degli articoli](../../../relational-databases/replication/publish/view-and-modify-article-properties.md)  
  
-   [Eliminazione di una pubblicazione](../../../relational-databases/replication/publish/delete-a-publication.md)  
  
-   [Delete an Article](../../../relational-databases/replication/publish/delete-an-article.md)  
  
> [!NOTE]  
>  L'eliminazione di un articolo o una pubblicazione non determina la rimozione di oggetti dal Sottoscrittore.  
  
## Pubblicazione di tabelle  
 L'oggetto più comunemente pubblicato è costituito da una tabella. È possibile utilizzare i collegamenti seguenti per ottenere informazioni aggiuntive sulle aree correlate alla pubblicazione di tabelle:  
  
-   [Filtro dei dati pubblicati](../../../relational-databases/replication/publish/filter-published-data.md)  
  
-   [Opzioni degli articoli per la replica transazionale](../../../relational-databases/replication/transactional/article-options-for-transactional-replication.md)  
  
-   [Opzioni degli articoli per la replica di tipo merge](../../../relational-databases/replication/merge/article-options-for-merge-replication.md)  
  
-   [Replica di colonne Identity](../../../relational-databases/replication/publish/replicate-identity-columns.md)  
  
 Quando si pubblica una tabella per la replica, è possibile specificare gli oggetti dello schema da copiare nel Sottoscrittore, ad esempio l'integrità referenziale dichiarata (vincoli di chiave primaria, di riferimento o UNIQUE), indici, trigger DML dell'utente (i trigger DDL non possono essere replicati), proprietà estese e regole di confronto. Le proprietà estese vengono replicate solo nella sincronizzazione iniziale tra il server di pubblicazione e il Sottoscrittore. Se si aggiungono o si modificano proprietà estese dopo la sincronizzazione iniziale, le modifiche apportate non vengono replicate.  
  
 Per specificare le opzioni dello schema, vedere [specificare le opzioni dello Schema](../../../relational-databases/replication/publish/specify-schema-options.md) o <xref:Microsoft.SqlServer.Replication.Article.SchemaOption%2A>.  
  
### Tabelle e indici partizionati  
 La replica supporta la pubblicazione di tabelle e indici partizionati. Il livello di supporto dipende dal tipo di replica utilizzato, nonché dalle opzioni specificate per la pubblicazione e dagli articoli associati alle tabelle partizionate. Per ulteriori informazioni, vedere [replicare tabelle e indici partizionati](../../../relational-databases/replication/publish/replicate-partitioned-tables-and-indexes.md).  
  
## Pubblicazione di stored procedure  
 Tutti i tipi di replica consentono di replicare definizioni di stored procedure, copiando CREATE PROCEDURE in ogni Sottoscrittore. In caso di stored procedure CLR (Common Language Runtime), viene inoltre copiato l'assembly associato. Le modifiche apportate alle procedure vengono replicate nei Sottoscrittori, mentre non vengono replicate le modifiche agli assembly associati.  
  
 Oltre alla replica della definizione di una stored procedure, la replica transazionale consente di replicare l'esecuzione di stored procedure. Ciò risulta utile per la replica dei risultati di stored procedure orientate alla manutenzione che influiscono su ingenti quantità di dati. Per altre informazioni, vedere [Publishing Stored Procedure Execution in Transactional Replication](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md).  
  
## Pubblicazione di viste  
 Tutti i tipi di replica consentono di replicare viste. È possibile copiare la vista e l'indice associato, in caso di vista indicizzata, nel Sottoscrittore, ma è inoltre necessario replicare la tabella di base.  
  
 Per le viste indicizzate, la replica transazionale consente inoltre di replicare la vista indicizzata come tabella anziché come vista, eliminando così l'esigenza di replicare anche la tabella di base. A tale scopo, specificare una delle opzioni "indexed view logbased" per il *@type* parametro [sp_addarticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md). Per ulteriori informazioni sull'utilizzo **sp_addarticle**, vedere [definire un articolo](../../../relational-databases/replication/publish/define-an-article.md).  
  
## Pubblicazione di funzioni definite dall'utente  
 Le istruzioni CREATE FUNCTION per funzioni CLR e [!INCLUDE[tsql](../../../includes/tsql-md.md)] vengono copiate in ogni Sottoscrittore. In caso di funzioni CLR, viene inoltre copiato l'assembly associato. Le modifiche apportate alle funzioni vengono replicate nei Sottoscrittori, mentre non vengono replicate le modifiche agli assembly associati.  
  
## Pubblicazione di tipi di dati definiti dall'utente e tipi di dati alias  
 Le colonne in cui vengono utilizzati tipi definiti dall'utente o tipi di dati alias vengono replicate nei Sottoscrittori come le altre colonne. Il TYPEstatement creare per ogni tipo replicato viene eseguita nel Sottoscrittore prima della creazione della tabella. In caso di tipi definiti dall'utente, viene inoltre copiato l'assembly associato in ogni Sottoscrittore. Le modifiche apportate ai tipi definiti dall'utente e ai tipi di dati alias non vengono replicate nei Sottoscrittori.  
  
 Se a un tipo definito in un database non viene fatto riferimento in alcuna colonna al momento della creazione di una pubblicazione, il tipo non viene copiato nei Sottoscrittori. Se successivamente si crea una colonna di tale tipo nel database e si desidera eseguirne la replica, è innanzitutto necessario copiare manualmente il tipo, nonché l'assembly associato in caso di tipo definito dall'utente, in ogni Sottoscrittore.  
  
## Pubblicazione di indici full-text  
 L'istruzione CREATE FULLTEXT INDEX viene copiata in ogni Sottoscrittore e nel Sottoscrittore viene creato l'indice full-text. Le modifiche apportate agli indici full-text tramite ALTER FULLTEXT INDEX non vengono replicate.  
  
## Modifiche dello schema in oggetti pubblicati  
 La replica supporta una vasta gamma di modifiche dello schema negli oggetti pubblicati. Quando si apporta una delle modifiche dello schema seguenti nell'oggetto pubblicato appropriato nel server di pubblicazione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], tale modifica viene propagata per impostazione predefinita a tutti i Sottoscrittori [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:  
  
-   ALTER TABLE  
  
-   ALTER VIEW  
  
-   ALTER PROCEDURE  
  
-   ALTER FUNCTION  
  
-   ALTER TRIGGER  
  
 Per ulteriori informazioni, vedere [apportare le modifiche dello Schema nei database di pubblicazione](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).  
  
## Considerazioni sulla pubblicazione  
 Durante la pubblicazione di oggetti di database è importante tenere presente quanto segue:  
  
-   Il database è accessibile agli utenti durante la creazione della pubblicazione e dello snapshot iniziale, ma è consigliabile creare le pubblicazioni in periodi di attività ridotta del server di pubblicazione.  
  
-   Non è possibile rinominare un database dopo che vi è stata creata una pubblicazione. Per rinominarlo, è innanzitutto necessario rimuovere la replica dal database.  
  
-   Se si pubblica un oggetto di database che dipende da uno o più oggetti di database diversi, è necessario pubblicare tutti gli oggetti a cui si fa riferimento. Se ad esempio si pubblica una vista che dipende da una tabella, sarà necessario pubblicare anche la tabella.  
  
    > [!NOTE]  
    >  Se si aggiunge un articolo a una pubblicazione di tipo merge e il nuovo articolo dipende da un articolo esistente, è necessario specificare un ordine di elaborazione per entrambi gli articoli utilizzando la **@processing_order** parametro [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) e [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Si consideri lo scenario seguente: viene pubblicata una tabella, ma non viene pubblicata una funzione a cui fa riferimento la tabella. Se non si pubblica la funzione, la tabella non può essere creata nel Sottoscrittore. Quando si aggiunge la funzione per la pubblicazione: specificare un valore di **1** per il **@processing_order** parametro **sp_addmergearticle**; e specificare un valore di **2** per il **@processing_order** parametro di **sp_changemergearticle**, specificando il nome della tabella per il parametro **@article**. Questo ordine di elaborazione consente di creare la funzione nel Sottoscrittore prima della tabella dipendente. È possibile utilizzare numeri diversi per ogni articolo, a condizione che il numero della funzione sia inferiore al numero della tabella.  
  
-   I nomi delle pubblicazioni non possono includere i caratteri seguenti: % * [ ] | : " ? \ / \< >.  
  
### Limitazioni relative alla pubblicazione di oggetti  
  
-   Il numero massimo di articoli e colonne che è possibile pubblicare varia in base al tipo di pubblicazione. Per ulteriori informazioni, vedere la sezione "Oggetti di replica" di [specifiche di capacità massima per SQL Server](../../../sql-server/maximum-capacity-specifications-for-sql-server.md).  
  
-   Le stored procedure, le viste, i trigger e le funzioni definite all'utente specificati come WITH ENCRYPTION non possono essere pubblicati nell'ambito della replica [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   È possibile replicare raccolte di XML Schema, ma le modifiche non vengono replicate dopo lo snapshot iniziale.  
  
-   Le tabelle pubblicate per la replica transazionale devono disporre di una chiave primaria. Se una tabella è inclusa in una pubblicazione per la replica transazionale, non è possibile disabilitare gli indici associati a colonne chiave primaria. Questi indici sono necessari per la replica. Per disabilitare un indice, è innanzitutto necessario eliminare la tabella dalla pubblicazione.  
  
-   Valori predefiniti associati creati con [sp_bindefault & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md) non vengono replicate (valori predefiniti associati sono deprecate a favore di valori predefiniti creati con la parola chiave DEFAULT di ALTER TABLE o CREATE TABLE).  
  
-   Le funzioni contenenti il **NOEXPAND** hint per le viste indicizzate non possono essere pubblicati nella stessa pubblicazione come tabelle con riferimenti e le viste indicizzate, dovuta all'ordine in cui li recapita l'agente di distribuzione. Per risolvere questo problema, inserire la tabella e la creazione di una vista indicizzata in una prima pubblicazione e aggiungere funzioni contenenti il **NOEXPAND** hint in viste indicizzate di una pubblicazione secondo cui la pubblicazione dopo la prima pubblicazione viene completata. In alternativa, creare script per queste funzioni e consegnare lo script utilizzando il *@post_snapshot_script* parametro **sp_addpublication**.  
  
### Schemi e proprietà degli oggetti  
 In relazione agli schemi e alla proprietà degli oggetti, la replica ha il seguente comportamento predefinito nella Creazione guidata nuova pubblicazione:  
  
-   Per gli articoli di pubblicazioni di tipo merge con un livello di compatibilità 90 o superiore, per le pubblicazioni snapshot e quelle transazionali: per impostazione predefinita, il proprietario dell'oggetto nel Sottoscrittore è uguale al proprietario dell'oggetto corrispondente nel server di pubblicazione. Se nel Sottoscrittore non esistono gli schemi che possiedono gli oggetti, vengono creati automaticamente.  
  
-   Per gli articoli delle pubblicazioni di tipo merge con un livello di compatibilità inferiore a 90: per impostazione predefinita, il proprietario viene lasciato vuoto e viene specificato come **dbo** durante la creazione dell'oggetto nel Sottoscrittore.  
  
-   Per gli articoli delle pubblicazioni Oracle: per impostazione predefinita, il proprietario è specificato come **dbo**.  
  
-   Per articoli di pubblicazioni che usano snapshot in modalità carattere (usati per Sottoscrittori non [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e Sottoscrittori [!INCLUDE[ssEW](../../../includes/ssew-md.md)]): per impostazione predefinita, il proprietario rimane vuoto. Il proprietario viene impostato sul proprietario associato all'account utilizzato dall'agente di distribuzione o dall'agente di merge per la connessione al Sottoscrittore.  
  
 Il proprietario dell'oggetto può essere modificato tramite la **Proprietà articolo - \<***articolo***>** la finestra di dialogo e tramite le stored procedure: **sp_addarticle**, **sp_addmergearticle**, **sp_changearticle**, e **sp_changemergearticle**. Per ulteriori informazioni, vedere [visualizzare e modificare le proprietà di pubblicazione](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md), [definire un articolo](../../../relational-databases/replication/publish/define-an-article.md), e [visualizzare e modificare le proprietà di articolo](../../../relational-databases/replication/publish/view-and-modify-article-properties.md).  
  
### Pubblicazione di dati per Sottoscrittori che eseguono versioni precedenti di SQL Server  
  
-   In caso di pubblicazione per un Sottoscrittore che esegue una versione precedente di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], è necessario considerare le limitazioni imposte dalle funzionalità di tale versione, sia in termini di funzionalità specifiche della replica che in termini di funzionalità complessive del prodotto.  
  
-   Nelle pubblicazioni di tipo merge viene utilizzato un livello di compatibilità che determina le funzionalità utilizzabili in una pubblicazione e consente di supportare i Sottoscrittori che eseguono versioni precedenti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
### Pubblicazione di tabelle in più pubblicazioni  
 La replica supporta la pubblicazione di articoli in più pubblicazioni, nonché la ripubblicazione di dati, con le restrizioni seguenti:  
  
-   Se un articolo è pubblicato in una pubblicazione transazionale o di tipo merge, verificare che il *@published_in_tran_pub* è impostata su TRUE per l'articolo di merge. Per ulteriori informazioni sull'impostazione delle proprietà, vedere [visualizzare e modificare le proprietà di pubblicazione](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md) e [visualizzare e modificare le proprietà di articolo](../../../relational-databases/replication/publish/view-and-modify-article-properties.md).  
  
     È necessario impostare anche la *@published_in_tran_pub* proprietà se un articolo appartenente a una sottoscrizione transazionale ed è incluso in una pubblicazione di tipo merge. In questo caso, è importante tenere presente che, per impostazione predefinita, la replica transazionale prevede che le tabelle nel Sottoscrittore siano considerate di sola lettura. La modifica dei dati di una tabella in una sottoscrizione transazionale durante la replica di tipo merge potrebbe pertanto impedire la convergenza dei dati. Per evitare questa eventualità, è consigliabile specificare queste tabelle come di solo download nella pubblicazione di tipo merge. In tal modo si impedisce al Sottoscrittore di tipo merge di caricare le modifiche ai dati nella tabella. Per ulteriori informazioni, vedere [Ottimizza prestazioni della replica di tipo Merge con gli articoli Download-Only](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md).  
  
-   Un articolo non può essere pubblicato sia in una pubblicazione di tipo merge che in una pubblicazione transazionale con sottoscrizioni ad aggiornamento in coda.  
  
-   Gli articoli inclusi in pubblicazioni transazionali che supportano le sottoscrizioni aggiornabili non possono essere ripubblicati.  
  
-   Se un articolo viene pubblicato in più pubblicazioni transazionali con supporto delle sottoscrizioni ad aggiornamento in coda, le proprietà seguenti devono contenere lo stesso valore per l'articolo in tutte le pubblicazioni.  
  
    |Proprietà|Parametro di sp_addarticle|  
    |--------------|---------------------------------|  
    |Gestione intervalli di valori Identity|**@auto_identity_range** (obsoleto) e **@identityrangemangementoption**|  
    |Intervallo di valori Identity del server di pubblicazione|**@pub_identity_range**|  
    |Intervallo di valori Identity|**@identity_range**|  
    |Soglia dell'intervallo di valori Identity|**@threshold**|  
  
     Per ulteriori informazioni su questi parametri, vedere [sp_addarticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md).  
  
-   Se un articolo viene pubblicato in più pubblicazioni di tipo merge, le proprietà seguenti devono disporre dello stesso valore per l'articolo in tutte le pubblicazioni.  
  
    |Proprietà|Parametro di sp_addmergearticle|  
    |--------------|--------------------------------------|  
    |Rilevamento a livello di colonna|**@column_tracking**|  
    |Opzioni schema|**@schema_option**|  
    |Applicazioni filtri alle colonne|**@vertical_partition**|  
    |Opzioni di caricamento Sottoscrittore|**@subscriber_upload_options**|  
    |Rilevamento eliminazioni condizionale|**@delete_tracking**|  
    |Compensazione errori|**@compensate_for_errors**|  
    |Gestione intervalli di valori Identity|**@auto_identity_range** (obsoleto) e **@identityrangemangementoption**|  
    |Intervallo di valori Identity del server di pubblicazione|**@pub_identity_range**|  
    |Intervallo di valori Identity|**@identity_range**|  
    |Soglia dell'intervallo di valori Identity|**@threshold**|  
    |Opzioni partizioni|**@partition_options**|  
    |Flusso colonne BLOB|**@stream_blob_columns**|  
    |Tipo filtro|**@filter_type** (parametro **sp_addmergefilter**)|  
  
     Per ulteriori informazioni su questi parametri, vedere [sp_addmergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) e [sp_addmergefilter & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md).  
  
-   La replica transazionale e la replica di tipo merge non filtrata supportano la pubblicazione di una tabella in più pubblicazioni e quindi la sottoscrizione all'interno di una singola tabella del database di sottoscrizione, in base allo scenario comunemente denominato di rollup. Il rollup viene frequentemente utilizzato per aggregare subset di dati da più posizioni all'interno di una tabella in un Sottoscrittore centrale. Le pubblicazioni di tipo merge filtrate non supportano lo scenario con Sottoscrittore centrale. Per la replica di tipo merge, il rollup viene in genere implementato tramite una singola pubblicazione con filtri di riga con parametri. Per altre informazioni, vedere [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
## Vedere anche  
 [Aggiunta ed eliminazione di articoli a e da pubblicazioni esistenti](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md)   
 [Configurazione della distribuzione](../../../relational-databases/replication/configure-distribution.md)   
 [Inizializzazione di una sottoscrizione](../../../relational-databases/replication/initialize-a-subscription.md)   
 [Creazione di script di replica](../../../relational-databases/replication/scripting-replication.md)   
 [Sicurezza del server di pubblicazione](../../../relational-databases/replication/security/secure-the-publisher.md)   
 [Sottoscrizione delle pubblicazioni](../../../relational-databases/replication/subscribe-to-publications.md)  
  
  