---
title: "Modifiche allo schema nei database di pubblicazione | Microsoft Docs"
ms.custom: ""
ms.date: "03/20/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "replica [SQL Server], modifiche dello schema"
  - "replica snapshot [SQL Server], replica di modifiche dello schema"
  - "replica di tipo merge [replica di SQL Server], replica di modifiche dello schema"
  - "replica transazionale, replica di modifiche dello schema"
  - "schemi [replica di SQL Server], replica di modifiche"
  - "pubblicazione [replica di SQL Server], modifiche dello schema"
ms.assetid: 926c88d7-a844-402f-bcb9-db49e5013b69
caps.latest.revision: 73
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 73
---
# Modifiche allo schema nei database di pubblicazione
  La replica supporta una vasta gamma di modifiche dello schema negli oggetti pubblicati. Quando si apporta una delle modifiche dello schema seguenti sull'oggetto appropriato pubblicato oggetto in un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] server di pubblicazione, tale modifica viene propagata per impostazione predefinita a tutti [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] abbonati:  
  
-   ALTER TABLE  
  
-   ALTER TABLE SET LOCK ESCALATION non deve essere utilizzato se la replica della modifica dello schema è abilitata e una topologia include [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] o [!INCLUDE[ssEWnoversion](../../../includes/ssewnoversion-md.md)] Subscribers.ALTER VIEW  
  
-   ALTER PROCEDURE  
  
-   ALTER FUNCTION  
  
-   ALTER TRIGGER  
  
     È possibile utilizzare ALTER TRIGGER solo per trigger [DML] (Data Manipulation Language), in quanto non è possibile replicare trigger [DDL] (Data Definition Language).  
  
> [!IMPORTANT]  
>  È necessario apportare le modifiche dello schema nelle tabelle tramite [!INCLUDE[tsql](../../../includes/tsql-md.md)] o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO). Quando si apportano modifiche dello schema in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] tenta di eliminare e ricreare la tabella. Poiché non è possibile eliminare gli oggetti pubblicati, la modifica dello schema ha esito negativo.  
  
 Per la replica transazionale e di tipo merge, le modifiche dello schema vengono propagate in modo incrementale quando l'agente di distribuzione o l'agente di merge è in esecuzione. Per la replica snapshot, le modifiche dello schema vengono propagate quando viene applicato un nuovo snapshot al Sottoscrittore. Nella replica snapshot, una nuova copia dello schema viene inviata al Sottoscrittore ogni volta che viene eseguita la sincronizzazione. Pertanto, tutte le modifiche dello schema, non solo quelle elencate sopra, negli oggetti pubblicati in precedenza vengono automaticamente propagate con ogni sincronizzazione.  
  
 Per informazioni sull'aggiunta e rimozione di articoli dalle pubblicazioni, vedere [eliminare articoli da pubblicazioni esistenti e aggiungere articoli alla](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
 **Per replicare le modifiche dello schema**  
  
 Le modifiche dello schema elencate sopra vengono replicate per impostazione predefinita. Per informazioni sulla disabilitazione della replica delle modifiche dello schema, vedere [replicare le modifiche dello Schema](../../../relational-databases/replication/publish/replicate-schema-changes.md).  
  
## Considerazioni sulle modifiche dello schema  
 Quando si replicano le modifiche dello schema, tenere presenti le considerazioni seguenti.  
  
### Considerazioni generali  
  
-   Le modifiche dello schema sono soggette a tutte le restrizioni imposte da [!INCLUDE[tsql](../../../includes/tsql-md.md)]. ALTER TABLE, ad esempio, non consente di eseguire l'istruzione ALTER per le colonne chiave primaria.  
  
-   Il mapping dei tipi di dati viene eseguito solo per lo snapshot iniziale. Il mapping delle modifiche dello schema alle versioni precedenti dei tipi di dati non viene eseguito. Ad esempio, se l'istruzione `ALTER TABLE ADD datetime2 column` viene utilizzata in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], il tipo di dati non viene convertito in **nvarchar** per [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] i sottoscrittori. In alcuni casi, le modifiche dello schema vengono bloccate nel server di pubblicazione.  
  
-   Se si imposta una pubblicazione in modo da consentire la propagazione delle modifiche dello schema, queste ultime vengono propagate indipendentemente da come è impostata la relativa opzione dello schema per un articolo nella pubblicazione. Se, ad esempio, si sceglie di non replicare i vincoli di chiave esterna per un articolo di tabella, ma in seguito si esegue un comando ALTER TABLE che aggiunge una chiave esterna alla tabella nel server di pubblicazione, la chiave esterna viene aggiunta alla tabella nel Sottoscrittore. Per evitare questo problema, disabilitare la propagazione delle modifiche dello schema prima di eseguire il comando ALTER TABLE.  
  
-   Le modifiche dello schema devono essere apportate solo nel server di pubblicazione, non nei Sottoscrittori, inclusi i Sottoscrittori di ripubblicazione. La replica di tipo merge impedisce le modifiche dello schema nel Sottoscrittore. La replica transazionale non impedisce le modifiche, ma le modifiche possono provocare errori nella replica.  
  
-   Per impostazione predefinita, le modifiche propagate a un Sottoscrittore di ripubblicazione vengono propagate ai relativi Sottoscrittori.  
  
-   Se la modifica dello schema fa riferimento a oggetti o vincoli esistenti nel server di pubblicazione, ma non nel Sottoscrittore, la modifica dello schema avrà esito positivo nel server di pubblicazione, ma negativo nel Sottoscrittore.  
  
-   È necessario che il nome e il proprietario di tutti gli oggetti nel Sottoscrittore a cui si fa riferimento quando si aggiunge una chiave esterna siano gli stessi dell'oggetto corrispondente nel server di pubblicazione.  
  
-   L'aggiunta, la rimozione e la modifica di indici in modo esplicito non sono supportate. Gli indici creati in modo implicito per i vincoli, ad esempio un vincolo di chiave primaria, sono supportati.  
  
-   La modifica o l'eliminazione di colonne Identity gestite dalla replica non è supportata. Per ulteriori informazioni sulla gestione automatica delle colonne identity, vedere [replicare colonne Identity](../../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
-   Le modifiche dello schema che includono funzioni non deterministiche non sono supportate, in quanto possono restituire dati diversi nel server di pubblicazione e nel Sottoscrittore, impedendo la convergenza. Se, ad esempio, si esegue il comando `ALTER TABLE SalesOrderDetail ADD OrderDate DATETIME DEFAULT GETDATE()` nel server di pubblicazione, i valori saranno diversi quando il comando viene replicato nel Sottoscrittore ed eseguito. Per ulteriori informazioni sulle funzioni non deterministiche, vedere [funzioni deterministiche e non](../../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).  
  
-   È consigliabile denominare i vincoli in modo esplicito. Se un vincolo non viene denominato in modo esplicito, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] genera un nome per il vincolo, che sarà diverso nel server di pubblicazione e in ogni Sottoscrittore. Ciò può causare problemi durante la replica delle modifiche dello schema. Se ad esempio viene eliminata una colonna nel server di pubblicazione, insieme a un vincolo dipendente, il processo di replica tenterà di eliminare tale vincolo nel Sottoscrittore. L'eliminazione del vincolo nel Sottoscrittore non potrà tuttavia essere eseguita, poiché il nome del vincolo è diverso. Se la sincronizzazione ha esito negativo per un problema di denominazione del vincolo, eliminare manualmente il vincolo nel Sottoscrittore e quindi eseguire nuovamente l'agente di merge.  
  
-   Se viene pubblicata una tabella per la replica, non è possibile modificare una colonna in tale tabella impostando il tipo di dati XML se è già stato generato uno snapshot di pubblicazione. Per modificare la colonna, è necessario prima rimuovere la replica.  
  
-   Read Uncommitted non è un livello di isolamento supportato quando si esegue la DDL in una tabella pubblicata.  
  
-   **Istruzione SET CONTEXT_INFO** non deve essere utilizzato per modificare il contesto delle transazioni in cui vengono effettuate le modifiche dello schema negli oggetti pubblicati.  
  
#### Aggiunta di colonne  
  
-   Per aggiungere una nuova colonna a una tabella e include la colonna in una pubblicazione esistente, eseguire ALTER TABLE \< tabella> Aggiungi \< colonna>. Per impostazione predefinita, la colonna viene quindi replicata a tutti i Sottoscrittori. È necessario che la colonna consenta i valori NULL o che includa un vincolo DEFAULT. Per altre informazioni sull'aggiunta di colonne, vedere la sezione "Replica di tipo merge" in questo argomento.  
  
-   Per aggiungere una nuova colonna a una tabella e non includere tale colonna in una pubblicazione esistente, disabilitare la replica delle modifiche dello schema e quindi eseguire ALTER TABLE \< tabella> Aggiungi \< colonna>.  
  
-   Per includere una colonna esistente in una pubblicazione esistente, utilizzare [sp_articlecolumn & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md), [sp_mergearticlecolumn & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md), o **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo.  
  
     Per altre informazioni, vedere [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md). Sarà necessario reinizializzare le sottoscrizioni.  
  
-   Non è consentito aggiungere una colonna Identity a una tabella pubblicata, perché ciò può impedire la convergenza dei dati durante la replica della colonna nel Sottoscrittore. I valori della colonna Identity nel server di pubblicazione dipendono dall'ordine in cui vengono fisicamente archiviate le righe della tabella interessata. Nel caso in cui le righe siano state archiviate in modo diverso nel Sottoscrittore, il valore della colonna Identity può essere diverso per le stesse righe.  
  
#### Eliminazione di colonne  
  
-   Per eliminare una colonna da una pubblicazione esistente e di eliminare la colonna dalla tabella nel server di pubblicazione, eseguire ALTER TABLE \< tabella> DROP \< colonna>. Per impostazione predefinita, la colonna viene quindi eliminata dalla tabella in tutti i Sottoscrittori.  
  
-   Per eliminare una colonna da una pubblicazione esistente, conservando la colonna della tabella nel server di pubblicazione, utilizzare [sp_articlecolumn & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md), [sp_mergearticlecolumn & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md), o **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo.  
  
     Per altre informazioni, vedere [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md). Sarà necessario generare un nuovo snapshot.  
  
-   La colonna da eliminare non può essere utilizzata nelle clausole di filtro degli articoli contenuti nelle pubblicazioni del database.  
  
-   Quando si elimina una colonna da un articolo pubblicato, considerare eventuali vincoli, indici o proprietà della colonna che potrebbero avere conseguenze sul database. Esempio:  
  
    -   Non è possibile eliminare le colonne utilizzate in una chiave primaria dagli articoli nelle pubblicazioni transazionali, in quanto vengono utilizzate dalla replica.  
  
    -   Non è possibile eliminare la colonna rowguid dagli articoli nelle pubblicazioni di tipo merge o la colonna mstran_repl_version dagli articoli nelle pubblicazioni transazionali che supportano l'aggiornamento delle sottoscrizioni, in quanto queste colonne vengono utilizzate dalla replica.  
  
    -   Le modifiche degli indici non vengono propagate ai Sottoscrittori. Se si elimina una colonna e un indice dipendente nel server di pubblicazione, l'eliminazione dell'indice non viene replicata. È necessario eliminare l'indice nel Sottoscrittore prima di eliminare la colonna nel server di pubblicazione, in modo che l'eliminazione della colonna abbia esito positivo quando viene replicata dal server di pubblicazione al Sottoscrittore. Se la sincronizzazione non riesce a causa di un indice nel Sottoscrittore, eliminare manualmente l'indice nel Sottoscrittore e quindi eseguire nuovamente l'agente di merge.  
  
    -   I vincoli devono essere denominati in modo esplicito per poter essere eliminati. Per altre informazioni, vedere la sezione "Considerazioni generali" più indietro in questo argomento.  
  
### Replica transazionale  
  
-   Le modifiche dello schema vengono propagate ai Sottoscrittori in cui sono in esecuzione versioni precedenti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], ma l'istruzione DDL deve includere solo la sintassi supportata dalla versione nel Sottoscrittore.  
  
     Se il Sottoscrittore ripubblica i dati, le uniche modifiche dello schema supportate sono l'aggiunta e l'eliminazione di una colonna. Queste modifiche devono essere apportate nel server di pubblicazione utilizzando [sp_repladdcolumn & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-repladdcolumn-transact-sql.md) e [sp_repldropcolumn & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-repldropcolumn-transact-sql.md) anziché la sintassi ALTER TABLE DDL.  
  
-   Le modifiche dello schema non vengono replicate nei Sottoscrittori non SQL Server.  
  
-   Le modifiche dello schema non vengono propagate dai server di pubblicazione non [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Non è possibile modificare le viste indicizzate replicate come tabelle. È possibile modificare le viste indicizzate replicate come viste indicizzate, ma la modifica ne comporta la trasformazione in viste normali.  
  
-   Se la pubblicazione supporta le sottoscrizioni ad aggiornamento immediato o ad aggiornamento in coda, il sistema deve essere messo in stato di inattività prima di apportare modifiche dello schema: è necessario arrestare tutte le attività nella tabella pubblicata nel server di pubblicazione e nei Sottoscrittori e propagare a tutti i nodi le modifiche ai dati in sospeso. Dopo avere propagato a tutti i nodi le modifiche dello schema, è possibile riprendere le attività nelle tabelle pubblicate.  
  
-   Se la pubblicazione si trova in una topologia peer-to-peer, è necessario mettere il sistema in stato di inattività prima di apportare modifiche dello schema. Per ulteriori informazioni, vedere [mettere una topologia di replica & #40; Programmazione Transact-SQL della replica & #41;](../../../relational-databases/replication/administration/quiesce-a-replication-topology-replication-transact-sql-programming.md).  
  
-   L'aggiunta di una colonna timestamp a una tabella e il mapping tra timestamp e binary(8) provoca la reinizializzazione dell'articolo per tutte le sottoscrizioni attive.  
  
### Replica di tipo merge  
  
-   La modalità di gestione delle modifiche dello schema da parte della replica di tipo merge è determinata dal livello di compatibilità della pubblicazione e dal fatto che lo snapshot sia impostato in modalità nativa (impostazione predefinita) o in modalità carattere:  
  
    -   Per replicare le modifiche dello schema, è necessario che il livello di compatibilità della pubblicazione sia almeno 90RTM. Se i Sottoscrittori eseguono versioni precedenti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] o il livello di compatibilità è minore di 90RTM è possibile utilizzare [sp_repladdcolumn & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-repladdcolumn-transact-sql.md) e [sp_repldropcolumn & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-repldropcolumn-transact-sql.md) Per aggiungere ed eliminare colonne. Tuttavia, queste procedure sono deprecate.  
  
    -   Se si tenta di aggiungere a un articolo esistente una colonna con un tipo di dati introdotto in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] presenta il comportamento seguente:  
  
        ||100RTM, snapshot nativo|100RTM, snapshot carattere|Tutti gli altri livelli di compatibilità|  
        |-|-----------------------------|--------------------------------|------------------------------------|  
        |**hierarchyid**|Modifica consentita|Modifica bloccata|Modifica bloccata|  
        |**Geography** e **geometry**|Modifica consentita|Modifica consentita*|Modifica bloccata|  
        |**filestream**|Modifica consentita|Modifica bloccata|Modifica bloccata|  
        |**Data**, **ora**, **datetime2**, e **datetimeoffset**|Modifica consentita|Modifica consentita*|Modifica bloccata|  
  
         * I Sottoscrittori di SQL Server Compact convertono questi tipi di dati nel Sottoscrittore.  
  
-   Se si verifica un errore quando si applica una modifica dello schema, ad esempio un errore dovuto all'aggiunta di una chiave esterna che fa riferimento a una tabella non disponibile nel Sottoscrittore, la sincronizzazione ha esito negativo ed è necessario reinizializzare la sottoscrizione.  
  
-   Se si apporta una modifica dello schema in una colonna coinvolta in un filtro join o in un filtro con parametri, è necessario reinizializzare tutte le sottoscrizioni e rigenerare lo snapshot.  
  
-   La replica di tipo merge offre stored procedure che consentono di ignorare le modifiche dello schema durante la risoluzione dei problemi. Per ulteriori informazioni, vedere [sp_markpendingschemachange & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-markpendingschemachange-transact-sql.md) e [sp_enumeratependingschemachanges & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-enumeratependingschemachanges-transact-sql.md).  
  
## Vedere anche  
 [Istruzione ALTER TABLE & #40; Transact-SQL & #41;](../../../t-sql/statements/alter-table-transact-sql.md)   
 [ALTER VIEW & #40; Transact-SQL & #41;](../../../t-sql/statements/alter-view-transact-sql.md)   
 [ALTER PROCEDURE & #40; Transact-SQL & #41;](../../../t-sql/statements/alter-procedure-transact-sql.md)   
 [ALTER FUNCTION & #40; Transact-SQL & #41;](../../../t-sql/statements/alter-function-transact-sql.md)   
 [Istruzione ALTER TRIGGER & #40; Transact-SQL & #41;](../../../t-sql/statements/alter-trigger-transact-sql.md)   
 [Pubblicazione di dati e oggetti di database](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Rigenerazione di procedure transazionali personalizzate per riflettere le modifiche dello schema](../../../relational-databases/replication/transactional/regenerate-custom-transactional-procedures-to-reflect-schema-changes.md)  
  
  