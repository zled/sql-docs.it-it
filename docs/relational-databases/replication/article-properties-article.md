---
title: "Propriet&#224; articolo - &lt;Articolo&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newpubwizard.articleproperties.f1"
helpviewer_keywords: 
  - "Proprietà articolo - finestra di dialogo"
ms.assetid: 6dd601a4-1233-43d9-a9f0-bc8d84e5d188
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# Propriet&#224; articolo - &lt;Articolo&gt;
  Il **Proprietà articolo** la finestra di dialogo è disponibile dalla creazione guidata pubblicazione e la **Proprietà pubblicazione** la finestra di dialogo. Questa finestra di dialogo consente di visualizzare e impostare le proprietà per tutti i tipi di articoli. Alcune proprietà possono essere impostate solo dopo aver creato la pubblicazione, mentre altre possono essere impostate solo se la pubblicazione non dispone di sottoscrizioni attive. Le proprietà non impostabili vengono visualizzate in sola lettura.  
  
> [!NOTE]  
>  Dopo la creazione di una pubblicazione, per alcune modifiche delle proprietà è necessario un nuovo snapshot. Se la pubblicazione dispone di sottoscrizioni, per alcune modifiche è inoltre necessario reinizializzare tutte le sottoscrizioni. Per ulteriori informazioni, vedere [Modifica proprietà della pubblicazione e articolo](../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
 Ogni proprietà di **Proprietà articolo** la finestra di dialogo include una descrizione. Fare clic su una proprietà per visualizzarne la descrizione nella parte inferiore della finestra di dialogo. In questo argomento sono specificate informazioni aggiuntive su diverse proprietà. Le proprietà sono raggruppate nelle categorie seguenti:  
  
-   Proprietà che si applicano a tutte le pubblicazioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Proprietà che si applicano alle pubblicazioni transazionali di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Proprietà che si applicano alle pubblicazioni di tipo merge.  
  
-   Proprietà che si applicano alle pubblicazioni transazionali e snapshot di server di pubblicazione Oracle.  
  
## Opzioni per tutte le pubblicazioni  
 **Copia schemi di partizionamento delle tabelle** e **Copia schemi di partizione dell'indice**  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] partizionamento delle tabelle introdotte e il partizionamento degli indici, che non sono correlati alla replica di partizionamento offre con la riga e colonna filtri. Il **Copia schemi di partizionamento delle tabelle** e **Copia schemi di partizione dell'indice** opzioni consentono di specificare se gli schemi di partizione devono essere copiati nel Sottoscrittore. Per ulteriori informazioni sul partizionamento, vedere [tabelle e indici partizionati](../../relational-databases/partitions/partitioned-tables-and-indexes.md).  
  
 **Converti tipi di dati**  
 Determina se convertire tipi di dati definiti dall'utente in tipi di dati di base durante la creazione di oggetti nel Sottoscrittore. I tipi di dati definiti dall'utente includono i tipi di dati CLR definiti dall'utente introdotti in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Specificare un valore di **True** se questi tipi di dati verranno replicati in versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; ciò garantisce che vengano gestiti correttamente nel Sottoscrittore.  
  
 **Crea schemi nel Sottoscrittore**  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] stati introdotti gli schemi, che vengono definiti utilizzando l'istruzione CREATE SCHEMA. Uno schema è il proprietario di un oggetto. viene utilizzato un nome composto da più parti, ad esempio \< Database>. \< Schema>. \< oggetto>. Se nel database esistono oggetti di proprietà di schemi diversi da DBO, la replica è in grado di creare tali schemi nel Sottoscrittore in modo che sia possibile creare gli oggetti pubblicati.  
  
 Se i dati verranno replicati in versioni [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] precedenti a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]:  
  
-   Impostare questa opzione su **False**, perché le versioni precedenti non supportano CREATE SCHEMA.  
  
-   Per ogni schema, aggiungere un utente al database di sottoscrizione utilizzando lo stesso nome dello schema.  
  
 **Converti XML in NTEXT**, **tipi di dati di convertire MAX in NTEXT e IMAGE**, **Converti nuovi tipi datetime in NVARCHAR**, **Converti tipo filestream nei tipi di dati MAX**, **convertire CLR di grandi dimensioni in tipi di dati MAX**, **Converti tipo hierarchyId in tipi di dati MAX**, e **Converti tipo spaziale nei tipi di dati MAX**.  
 Determina se convertire i tipi di dati e gli attributi come descritto. Specificare un valore di **True** se questi tipi di dati verranno replicati in versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. In questo modo i tipi di dati verranno gestiti correttamente nel Sottoscrittore.  
  
 **Nome oggetto di destinazione**  
 Nome dell'oggetto creato nel database di sottoscrizione. Non è possibile modificare questa opzione per articoli contenuti in pubblicazioni abilitate per la replica transazionale peer-to-peer.  
  
 **Proprietario oggetto di destinazione**  
 Schema con cui è stato creato l'oggetto nel database di sottoscrizione. L'impostazione predefinita è rappresentata dallo schema al quale appartiene l'oggetto nel database di pubblicazione, con le eccezioni seguenti:  
  
-   Per gli articoli delle pubblicazioni di tipo merge con un livello di compatibilità inferiore a 90: per impostazione predefinita, il proprietario viene lasciato vuoto e viene specificato come **dbo** durante la creazione dell'oggetto nel Sottoscrittore.  
  
-   Per gli articoli delle pubblicazioni Oracle: per impostazione predefinita, il proprietario è specificato come **dbo**.  
  
-   Per articoli di pubblicazioni che usano snapshot in modalità carattere (usati per Sottoscrittori non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e Sottoscrittori [!INCLUDE[ssEW](../../includes/ssew-md.md)]): per impostazione predefinita, il proprietario rimane vuoto. Il proprietario viene impostato sul proprietario associato all'account utilizzato dall'agente di distribuzione o dall'agente di merge per la connessione al Sottoscrittore.  
  
 Non è possibile modificare questa opzione per articoli contenuti in pubblicazioni abilitate per la replica transazionale peer-to-peer.  
  
 **Gestisci automaticamente gli intervalli di valori Identity**  
 Per impostazione predefinita, la replica gestisce tutte le colonne Identity nel server di pubblicazione e in ogni Sottoscrittore. Ogni nodo di replica viene assegnato un intervallo di valori identity (specificata con il **Dimensioni intervallo server di pubblicazione** e **Dimensioni intervallo Sottoscrittore** Opzioni) per garantire che un determinato valore viene utilizzato in un solo nodo. Per ulteriori informazioni, vedere [replicare colonne Identity](../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
## Opzioni per le pubblicazioni transazionali  
 **Copia stored procedure INSERT, UPDATE e DELETE**  
 Se, nel **Recapito istruzione** sezione della finestra di dialogo, si sceglie di utilizzare le stored procedure per propagare le modifiche ai sottoscrittori (impostazione predefinita), selezionare questa opzione per copiare le procedure in ogni sottoscrittore. Se si seleziona **False**, è necessario copiare manualmente le procedure o l'agente di distribuzione avrà esito negativo durante il tentativo di recapito delle modifiche.  
  
 **Recapito istruzione**  
 Le opzioni contenute in questa sezione si applicano a tutte le tabelle, incluse le viste indicizzate che vengono replicate come tabelle. [!INCLUDE[msCoName](../../includes/msconame-md.md)] è consigliabile utilizzare le opzioni predefinite, a meno che l'applicazione richiede funzionalità diverse. Per impostazione predefinita, la replica transazionale propaga le modifiche ai Sottoscrittori utilizzando un set di stored procedure installate in ogni Sottoscrittore. Quando viene eseguito un inserimento, un aggiornamento o un'eliminazione in una tabella nel server di pubblicazione, l'operazione viene tradotta in una chiamata alla stored procedure nel Sottoscrittore.  
  
 Il **recapito dell'istruzione** opzioni consentono di specificare se utilizzare una stored procedure, e se, pertanto, il formato deve essere utilizzato per i parametri passati per la procedura. Il **stored procedure di** opzioni consentono di utilizzare le procedure di replica automaticamente consente di creare o sostituire le procedure personalizzate create.  
  
 Per ulteriori informazioni, vedere [specificare modalità di propagazione delle modifiche per gli articoli transazionali](../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md).  
  
 **Replica**  
 Questa opzione si applica solo alle stored procedure e determina se replicare la definizione della stored procedure, ovvero l'istruzione CREATE PROCEDURE, oppure la relativa esecuzione. Se si replica l'esecuzione della procedura, la definizione della procedura viene replicata nel Sottoscrittore nel momento in cui la sottoscrizione viene inizializzata. Quando la procedura viene eseguita nel server di pubblicazione, il processo di replica esegue la procedura corrispondente nel Sottoscrittore. Ciò consente di ottenere un miglioramento significativo delle prestazioni nel caso in cui vengano eseguite operazioni su batch di grandi dimensioni. Per altre informazioni, vedere [Publishing Stored Procedure Execution in Transactional Replication](../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md).  
  
## Opzioni per le pubblicazioni di tipo merge  
 Il **Proprietà articolo** la finestra di dialogo per le pubblicazioni di tipo merge è disponibili due schede: **proprietà** e **Resolver**.  
  
### Scheda Proprietà  
 **Direzione sincronizzazione**  
 Determina se le modifiche possono essere caricate dai Sottoscrittori che utilizzano il tipo di sottoscrizione client:  
  
-   **Bidirezionale** (predefinito): le modifiche possono essere scaricate nel sottoscrittore e caricate nel server di pubblicazione.  
  
-   **Solo download sul sottoscrittore, non consentire modifiche del sottoscrittore**: le modifiche possono essere scaricate nel Sottoscrittore, ma non possono essere caricate nel server di pubblicazione. I trigger impediscono che le modifiche vengano apportate al Sottoscrittore.  
  
-   **Solo download sul sottoscrittore, Consenti modifiche del sottoscrittore**: le modifiche possono essere scaricate nel Sottoscrittore, ma non possono essere caricate nel server di pubblicazione.  
  
 Per ulteriori informazioni, vedere [Ottimizza prestazioni della replica di tipo Merge con gli articoli Download-Only](../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md).  
  
 **Opzioni partizioni**  
 Specifica il tipo di partizioni create da un filtro con parametri. Per ulteriori informazioni, vedere la sezione "Impostazione 'opzioni di partizionamento'" di [i filtri di riga con parametri](../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
 **Livello rilevamento**  
 Determina se gestire come conflitto le modifiche apportate alla stessa riga o alla stessa colonna.  
  
 **Verifica autorizzazione INSERT**, **Verifica autorizzazione UPDATE**, e **Verifica autorizzazione DELETE**  
 Determina se durante la sincronizzazione viene controllata la disponibilità delle autorizzazioni INSERT, UPDATE o DELETE da parte dell'account di accesso del Sottoscrittore per le tabelle pubblicate nel database di pubblicazione. Il valore predefinito è **False** perché la replica di tipo merge non richiede queste autorizzazioni da concedere; l'accesso alle tabelle pubblicate viene controllato tramite l'accesso elenco di pubblicazione. Per ulteriori informazioni sull'elenco di accesso, vedere [proteggere il server di pubblicazione](../../relational-databases/replication/security/secure-the-publisher.md).  
  
 È possibile richiedere che vengano verificate le autorizzazioni se si desidera consentire a uno o più Sottoscrittori di caricare solo determinate modifiche nei dati pubblicati. Ad esempio, è possibile aggiungere un Sottoscrittore all'elenco di accesso alla pubblicazione senza concedere al Sottoscrittore alcuna autorizzazione per le tabelle contenute nel database di pubblicazione. È quindi possibile impostare verifica autorizzazioni DELETE **True**: sarebbe in grado di caricare inserimenti e aggiornamenti, ma non elimina il sottoscrittore.  
  
 **UPDATE multicolonna**  
 Quando la replica di tipo merge esegue un aggiornamento, vengono aggiornate tutte le colonne modificate in un'unica istruzione UPDATE e reimpostati i valori originali per le colonne non modificate. L'alternativa in questi casi consiste nell'inoltrare più istruzioni UPDATE, con una istruzione UPDATE per ogni colonna che ha subito modifiche. L'istruzione UPDATE multicolonna risulta in genere più efficiente, ma è consigliabile impostare l'opzione su **False** se trigger della tabella vengono impostati per rispondere agli aggiornamenti di determinate colonne e rispondano in modo non appropriato perché tali colonne vengono reimpostate durante gli aggiornamenti.  
  
> [!IMPORTANT]  
>  questa opzione è deprecata e verrà rimossa a partire da una delle prossime versioni.  
  
### Scheda Sistema di risoluzione  
 **Usa il sistema di risoluzione predefinito**  
 Se si seleziona il sistema di risoluzione predefinito, i conflitti vengono risolti in base alla priorità assegnata a ogni Sottoscrittore o alla prima modifica scritta nel server di pubblicazione, a seconda del tipo di sottoscrizioni utilizzate. Per ulteriori informazioni, vedere [rilevare e risolvere i conflitti di replica di tipo Merge](../../relational-databases/replication/merge/detect-and-resolve-merge-replication-conflicts.md).  
  
 **Usa un sistema di risoluzione personalizzato (registrato nel server di distribuzione)**  
 Se si sceglie di utilizzare un sistema di risoluzione dei conflitti dell'articolo fornito da [!INCLUDE[msCoName](../../includes/msconame-md.md)] o scritto dall'utente, è necessario selezionare un sistema di risoluzione nella casella di riepilogo. Per altre informazioni, vedere [Advanced Merge Replication Conflict Detection and Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md).  
  
 Se il sistema di risoluzione necessita di un input, specificarlo nella **Immettere le informazioni necessarie da parte del resolver** casella di testo. Per ulteriori informazioni sull'input richiesto da [!INCLUDE[msCoName](../../includes/msconame-md.md)] sistemi di risoluzione personalizzati, vedere [Microsoft sistemi di risoluzione basati su COM](../../relational-databases/replication/merge/microsoft-com-based-resolvers.md).  
  
 **Consenti la risoluzione interattiva dei conflitti nel Sottoscrittore durante la sincronizzazione su richiesta**  
 Selezionare questa opzione se i Sottoscrittori utilizzeranno la sincronizzazione su richiesta, ovvero l'impostazione predefinita per la replica di tipo merge, e si desidera risolvere i conflitti in modo interattivo. Specificare la sincronizzazione su richiesta sul **pianificazione della sincronizzazione** pagina della procedura guidata nuova sottoscrizione. Per risolvere i conflitti in modo interattivo, utilizzare l'interfaccia utente del sistema di risoluzione dei conflitti interattivo. Per altre informazioni, vedere [Interactive Conflict Resolution](../../relational-databases/replication/merge/interactive-conflict-resolution.md).  
  
 **Prima di eseguire il processo di merge, richiedi la verifica della firma digitale**  
 Tutti i sistemi di risoluzione dei conflitti basati su COM forniti da [!INCLUDE[msCoName](../../includes/msconame-md.md)] sono firmati. Selezionare questa opzione per verificare la validità del sistema di risoluzione dei conflitti durante la sincronizzazione.  
  
## Opzioni per le pubblicazioni Oracle  
 Il **Proprietà articolo** la finestra di dialogo per le pubblicazioni Oracle dispone di due schede: **proprietà** e **Mapping dei dati**. Le pubblicazioni Oracle non supportano tutte le proprietà supportate dalle pubblicazioni [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per ulteriori informazioni, vedere [Considerazioni sulla progettazione e limitazioni per server di pubblicazione Oracle](../../relational-databases/replication/non-sql/design-considerations-and-limitations-for-oracle-publishers.md).  
  
### Scheda Proprietà  
 **Copia stored procedure INSERT, UPDATE e DELETE**  
 Se l'articolo è in una pubblicazione transazionale e, nel **Recapito istruzione** sezione della finestra di dialogo, si sceglie di utilizzare le stored procedure per propagare le modifiche ai sottoscrittori (impostazione predefinita), selezionare questa opzione per copiare le procedure in ogni sottoscrittore. Se si seleziona **False**, è necessario copiare manualmente le procedure o l'agente di distribuzione avrà esito negativo durante il tentativo di recapito delle modifiche.  
  
 **Proprietario oggetto di destinazione**  
 Se si immette un valore diverso da **dbo**:  
  
-   Per i Sottoscrittori che eseguono [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] o versione successiva è necessario garantire che lo schema venga creato nel Sottoscrittore con lo stesso nome del valore immesso. Per ulteriori informazioni, vedere [CREATE SCHEMA & #40; Transact-SQL & #41;](../../t-sql/statements/create-schema-transact-sql.md).  
  
-   Per i Sottoscrittori che eseguono versioni di SQL Server precedenti a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], per ogni schema aggiungere un utente al database di sottoscrizione utilizzando lo stesso nome dello schema.  
  
 **Nome spazio tabella**  
 Spazio tabella in cui creare le tabelle per il rilevamento delle modifiche della replica nell'istanza del server Oracle. Per ulteriori informazioni, vedere [gestire spazi di tabella Oracle](../../relational-databases/replication/non-sql/manage-oracle-tablespaces.md).  
  
 **Recapito istruzione**  
 Le opzioni descritte in questa sezione si applicano a tutte le tabelle contenute in pubblicazioni transazionali. [!INCLUDE[msCoName](../../includes/msconame-md.md)] è consigliabile utilizzare le opzioni predefinite, a meno che l'applicazione richiede funzionalità diverse. Per impostazione predefinita, la replica transazionale propaga le modifiche ai Sottoscrittori utilizzando un set di stored procedure installate in ogni Sottoscrittore. Quando viene eseguito un inserimento, un aggiornamento o un'eliminazione in una tabella nel server di pubblicazione, l'operazione viene tradotta in una chiamata alla stored procedure nel Sottoscrittore.  
  
 Il **recapito dell'istruzione** opzioni consentono di specificare se utilizzare una stored procedure, e se, pertanto, il formato deve essere utilizzato per i parametri passati per la procedura. Il **stored procedure di** opzioni consentono di utilizzare le procedure di replica automaticamente consente di creare o sostituire le procedure personalizzate create.  
  
 Per ulteriori informazioni, vedere [specificare modalità di propagazione delle modifiche per gli articoli transazionali](../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md).  
  
### Scheda Mapping dei dati  
 **Nome colonna**  
 Nome della colonna nel server di pubblicazione (informazione di sola lettura).  
  
 **Tipo di dati server di pubblicazione**  
 Tipo di dati Oracle per la colonna nel server di pubblicazione (informazione di sola lettura). È possibile modificare direttamente il tipo di dati solo nel database Oracle. Per ulteriori informazioni, vedere la documentazione di Oracle.  
  
 **Tipo di dati del Sottoscrittore**  
 Tipo di dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a cui viene eseguito il mapping del tipo di dati Oracle durante la replica dei dati:  
  
-   Per alcuni tipi di dati è disponibile un solo tipo di mapping. In questo caso, la colonna nella proprietà è di sola lettura.  
  
-   Per alcuni tipi è possibile selezionare più tipi di mapping. [!INCLUDE[msCoName](../../includes/msconame-md.md)] consiglia di utilizzare il mapping predefinito, a meno che l'applicazione utilizzata non richieda un tipo di mapping diverso. Per altre informazioni, vedere [Data Type Mapping for Oracle Publishers](../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md).  
  
## Vedere anche  
 [Creazione di una pubblicazione](../../relational-databases/replication/publish/create-a-publication.md)   
 [Visualizzazione e modifica delle proprietà della pubblicazione](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Creazione e applicazione dello snapshot iniziale](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)   
 [Reinizializzare una sottoscrizione](../../relational-databases/replication/reinitialize-a-subscription.md)   
 [Pubblicazione di dati e oggetti di database](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  