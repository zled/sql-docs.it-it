---
title: "Ricerca full-text | Microsoft Docs"
ms.custom: ""
ms.date: "07/29/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-search"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ricerca full-text [SQL Server]"
ms.assetid: a0ce315d-f96d-4e5d-b4eb-ff76811cab75
caps.latest.revision: 54
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 49
---
# Ricerca full-text
  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)] la ricerca full-text consente a utenti e applicazioni di eseguire query full-text su dati di tipo carattere in tabelle di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Affinché le query full-text possano essere eseguite in una determinata tabella, l'amministratore del database deve prima creare un indice full-text nella tabella in questione. L'indice full-text include una o più colonne basate su caratteri nella tabella. Queste colonne possono avere uno dei tipi di dati seguenti: **char**, **varchar**, **nchar**, **nvarchar**, **text**, **ntext**, **image**, **xml** o **varbinary(max)** e FILESTREAM. Ogni indice full-text consente di indicizzare una o più colonne della tabella e ciascuna colonna può essere utilizzata con una lingua specifica.  
  
 Attraverso le query full-text è possibile eseguire ricerche linguistiche rispetto ai dati di testo contenuti negli indici full-text, utilizzando parole e frasi in base alle regole di una determinata lingua, come ad esempio l'inglese o il giapponese. Le query full-text possono contenere semplici parole e frasi oppure più forme di una parola o frase. Una query full-text restituisce qualsiasi documento contenente almeno una corrispondenza, nota anche come *riscontro*. Si ottiene una corrispondenza quando un documento di destinazione contiene tutti i termini specificati nella query full-text e soddisfa qualsiasi altra condizione di ricerca, come ad esempio la distanza entro i termini corrispondenti.  
  
> **NOTA** La ricerca full-text è un componente facoltativo del Motore di database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [Installare SQL Server 2016](../../database-engine/install-windows/install-sql-server-2016.md).  
  
##  <a name="queries"></a> Ricerca full-text - query  
 Dopo l'aggiunta delle colonne a un indice full-text, gli utenti e le applicazioni possono eseguire query full-text sul testo contenuto all'interno delle colonne. Queste query possono consentire la ricerca degli elementi seguenti:  
  
-   Una o più parole o frasi specifiche (*termine semplice*)  
  
-   Parola o frase in cui le parole iniziano con il testo specificato (*termine di prefisso*)  
  
-   Forme flessive di una parola specifica (*termine di generazione*)  
  
-   Una parola o frase vicina a un'altra parola o frase (*termine di prossimità*)  
  
-   Sinonimi di una parola specifica (*thesaurus*)  
  
-   Parole o frasi che usano valori ponderati (*termine ponderato*)  
  
 Per le query di ricerca full-text non viene fatta distinzione tra maiuscole e minuscole. Ad esempio, dalla ricerca di "Alluminio" o "alluminio" vengono restituiti gli stessi risultati.  
  
 Nelle query full-text viene utilizzato un set ridotto di predicati (CONTAINS e FREETEXT) e funzioni (CONTAINSTABLE e FREETEXTTABLE) [!INCLUDE[tsql](../../includes/tsql-md.md)]. Tuttavia, gli obiettivi di ricerca di un determinato scenario aziendale influiscono sulla struttura delle query full-text. Esempio:  
  
-   Commercio elettronico: ricerca di un prodotto in un sito Web  
  
    ```  
    SELECT product_id   
    FROM products   
    WHERE CONTAINS(product_description, ”Snap Happy 100EZ” OR FORMSOF(THESAURUS,’Snap Happy’) OR ‘100EZ’)   
    AND product_cost < 200 ;  
    ```  
  
-   Assunzione di personale: ricerca di candidati con esperienza in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
    ```  
    SELECT candidate_name,SSN   
    FROM candidates   
    WHERE CONTAINS(candidate_resume,”SQL Server”) AND candidate_division =DBA;  
    ```  
  
 Per altre informazioni, vedere [Esecuzione della query con ricerca Full-Text](../../relational-databases/search/query-with-full-text-search.md).  
  
##  <a name="like"></a> Confronto tra LIKE e la ricerca full-text  
 Contrariamente alla ricerca full-text, il predicato [LIKE](../../t-sql/language-elements/like-transact-sql.md)[!INCLUDE[tsql](../../includes/tsql-md.md)] funziona unicamente con i modelli di caratteri. Non è inoltre possibile utilizzare il predicato LIKE per eseguire query su dati binari formattati. Inoltre, l'esecuzione di una query LIKE su una grande quantità di dati di testo non strutturati è molto più lenta dell'esecuzione di una query full-text equivalente sugli stessi dati. Una query LIKE eseguita su milioni di righe di dati di testo può richiedere diversi minuti, mentre per una query full-text sugli stessi dati possono essere necessari al massimo pochi secondi, a seconda del numero di righe restituite.  
  
##  <a name="architecture"></a> Pianificazione e architettura  
 L'architettura della ricerca full-text è costituita dai processi seguenti:  
  
-   Processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (sqlservr.exe).  
  
-   Processo host del daemon di filtri (fdhost.exe).  
  
     Ai fini della sicurezza, i filtri vengono caricati da processi separati definiti host del daemon di filtri. I processi fdhost.exe vengono creati da un servizio dell'utilità di avvio di FDHOST (MSSQLFDLauncher) e vengono eseguiti con le credenziali di sicurezza dell'account del servizio dell'utilità di avvio di FDHOST. Il funzionamento delle query e dell'indicizzazione full-text dipende quindi dall'esecuzione del servizio dell'utilità di avvio di FDHOST. Per informazioni sulla configurazione dell'account del servizio per questo servizio, vedere [Impostazione dell'account del servizio dell'Utilità di avvio del daemon di filtri full-text](../../relational-databases/search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md).  
  
 In questi due processi sono inclusi i componenti dell'architettura della ricerca full-text, riepilogati con le relative relazioni nell'illustrazione seguente. I componenti vengono descritti dopo l'illustrazione.  
  
 ![Architettura della ricerca full-text](../../relational-databases/search/media/ifts-arch.gif "Architettura della ricerca full-text")  
  
###  <a name="sqlprocess"></a> Processo di SQL Server  
 Nel processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono utilizzati i componenti seguenti per la ricerca full-text:  
  
-   **Tabelle utente.** In queste tabelle sono contenuti i dati da inserire nell'indice full-text.  
  
-   **Gatherer full-text.** Il gatherer full-text funziona con i thread della ricerca per indicizzazione full-text e consente di pianificare e gestire il popolamento degli indici full-text, nonché di monitorare i cataloghi full-text.  
  
-   **File del thesaurus.** In questi file sono contenuti i sinonimi dei termini da cercare. Per altre informazioni, vedere [Configurare e gestire i file del thesaurus per la ricerca full-text](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md).  
  
-   **Oggetti dell'elenco di parole non significative.** Negli oggetti dell'elenco di parole non significative sono inclusi un insieme di parole comuni che non risultano utili per la ricerca. Per altre informazioni, vedere [Configurare e gestire parole non significative ed elenchi di parole non significative per la ricerca full-text](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md).  
  
-   **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Query Processor.** Query Processor consente di compilare ed eseguire query SQL. Se in una query SQL è inclusa una query di ricerca full-text, la query viene inviata al motore di ricerca full-text sia durante la compilazione sia durante l'esecuzione. Il risultato della query viene messo a confronto con l'indice full-text.  
  
-   **Motore di ricerca full-text.** Il motore di ricerca full-text in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è attualmente completamente integrato con Query Processor. Il motore di ricerca full-text compila ed esegue query full-text. Come parte dell'esecuzione di query, il motore di ricerca full-text può ricevere input dal thesaurus e dall'elenco di parole non significative.  
  
-   **Writer di indici (indicizzatore).** Il writer di indici consente di compilare la struttura utilizzata per archiviare i token indicizzati.  
  
-   **Strumento di gestione del daemon di filtri.** Lo strumento di gestione del daemon di filtri consente di monitorare lo stato dell'host del daemon di filtri per il motore di ricerca full-text.  
  
##  <a name="fdhostprocess"></a> Processo host del daemon di filtri  
 L'host del daemon di filtri è un processo avviato dal motore di ricerca full-text e consente l'esecuzione dei componenti della ricerca full-text seguenti, responsabili dell'accesso, del filtraggio e del word breaking di dati dalle tabelle, nonché del word breaking e dello stemming dell'input della query.  
  
 I componenti dell'host del daemon di filtri sono i seguenti:  
  
-   **Protocol handler.** Questo componente consente di effettuare il pull dei dati dalla memoria per un'ulteriore elaborazione e di accedere ai dati da una tabella utente in un database specificato. È inoltre responsabile della raccolta dei dati dalle colonne oggetto dell'indicizzazione full-text e del loro passaggio all'host del daemon di filtri tramite il quale verrà applicato il filtro e il word breaker in base alle specifiche esigenze.  
  
-   **Filtri.** Per alcuni tipi di dati è richiesta l'applicazione di un filtro prima che i dati di un documento possano essere sottoposti all'indicizzazione full-text, inclusi i dati nelle colonne **varbinary**, **varbinary(max)**, **image** o **xml**. Il filtro utilizzato per un documento dipende dal relativo tipo. Vengono infatti utilizzati filtri diversi per documenti di Microsoft Word (doc), documenti di Microsoft Excel (xls) e documenti XML (xml). Il filtro estrae blocchi di testo dal documento, rimuovendo la formattazione incorporata e mantenendo il testo e, potenzialmente, le informazioni sulla posizione del testo. Il risultato è un flusso di informazioni testuali. Per altre informazioni, vedere [Configurazione e gestione di filtri per la ricerca](../../relational-databases/search/configure-and-manage-filters-for-search.md).  
  
-   **Word breaker e stemmer.** Un word breaker è un componente specifico della lingua che consente di trovare i delimitatori di parola in base alle regole lessicali di una determinata lingua (*word breaking*). Ogni word breaker è associato a uno stemmer specifico della lingua che coniuga i verbi ed esegue le espansioni flessionali. In fase di indicizzazione, l'host del daemon di filtri utilizza un word breaker e uno stemmer per eseguire l'analisi linguistica sui dati testuali di una colonna di tabella specificata. Il word breaker e lo stemmer utilizzati per l'indicizzazione della colonna sono determinati dalla lingua associata a una colonna di tabella nell'indice full-text. Per altre informazioni, vedere [Configurare e gestire word breaker e stemmer per la ricerca](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md).  
  
##  <a name="processing"></a> Elaborazione della ricerca full-text  
 La ricerca full-text è supportata dal motore di ricerca full-text che svolge due ruoli, vale a dire il supporto per l'indicizzazione e quello per l'esecuzione di query.  
  
###  <a name="indexing"></a> Processo di indicizzazione full-text  
 Quando viene iniziato un popolamento full-text, noto anche come ricerca per indicizzazione, tramite il motore di ricerca full-text viene eseguito il push di batch di grandi dimensioni di dati in memoria e viene inviata una notifica all'host del daemon di filtri. L'host filtra ed esegue il word breaking dei dati ed esegue inoltre la conversione dei dati convertiti in elenchi di parole invertiti. La ricerca full-text effettua quindi il pull dei dati convertiti dagli elenchi di parole, elabora i dati per rimuovere le parole non significative e salva in modo permanente gli elenchi di parole per un batch in uno o più indici invertiti.  
  
 Durante l'indicizzazione dei dati archiviati in una colonna **varbinary(max)** o **image**, il filtro, che implementa l'interfaccia **IFilter**, estrae testo in base al formato file specificato per tali dati, ad esempio [!INCLUDE[msCoName](../../includes/msconame-md.md)] Word. Per i componenti filtro talvolta i dati di tipo **varbinary(max)** o **image** devono essere scritti nella cartella filterdata e non deve esserne eseguito il push in memoria.  
  
 Nell'ambito dell'elaborazione, i dati di testo raccolti vengono sottoposti a un word breaker per separare il testo in singoli token o parole chiave. La lingua usata per la tokenizzazione viene specificata a livello di colonna o può essere identificata all'interno dei dati **varbinary(max)**, **image** o **xml** dal componente filtro.  
  
 È possibile eseguire un'ulteriore elaborazione per rimuovere le parole non significative e normalizzare i token prima di archiviarli nell'indice full-text o in un frammento di indice.  
  
 Al termine di un popolamento, viene attivato un processo di unione conclusivo che associa i frammenti di indice in un singolo indice full-text master. Ciò consente prestazioni di query superiori poiché è necessario eseguire query solo sull'indice master anziché su alcuni frammenti di indice ed è possibile utilizzare statistiche di punteggio migliori per la classificazione della pertinenza.  
  
###  <a name="querying"></a> Processo di esecuzione di query full-text  
 Query Processor consente di passare le parti full-text di una query al motore di ricerca full-text affinché vengano elaborate. Il motore di ricerca full-text esegue il word breaking e, facoltativamente, le espansioni del thesaurus, lo stemming e l'elaborazione delle parole non significative. Le parti full-text della query vengono rappresentate come operatori SQL, principalmente come funzioni di flusso con valori di tabella. Durante l'esecuzione della query, queste funzioni accedono all'indice invertito per recuperare i risultati corretti. I risultati vengono restituiti al client immediatamente oppure dopo essere stati ulteriormente elaborati.  
  
##  <a name="components"></a> Componenti linguistici e supporto per la lingua nella ricerca full-text  
 La ricerca full-text supporta quasi 50 lingue, tra cui inglese, spagnolo, cinese, giapponese, arabo, bengali e hindi. Per un elenco completo delle lingue full-text supportate, vedere [sys.fulltext_languages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md). A ognuna delle colonne contenute nell'indice full-text è associato un identificatore delle impostazioni locali (LCID) di Microsoft Windows che corrisponde a una lingua supportata dalla ricerca full-text. L'identificatore LCID 1033, ad esempio, corrisponde all'inglese americano, mentre l'identificatore LCID 2057 corrisponde all'inglese britannico. Per ogni lingua full-text supportata, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono forniti componenti linguistici che supportano l'indicizzazione e l'esecuzione di query su dati full-text archiviati in quella lingua.  
  
 Tra i componenti specifici della lingua sono inclusi gli elementi seguenti:  
  
-   **Word breaker e stemmer.** Un word breaker consente di trovare i delimitatori di parola in base alle regole lessicali di una determinata lingua (*word breaking*). A ogni word breaker è associato uno stemmer tramite cui vengono coniugati i verbi per la stessa lingua. Per altre informazioni, vedere [Configurare e gestire word breaker e stemmer per la ricerca](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md).  
  
-   **Elenchi di parole non significative.** Viene inoltre fornito un elenco di parole non significative di sistema. Per *parola non significativa* si intende una parola inutile ai fini della ricerca e quindi ignorata dalle query full-text. Ad esempio, nelle impostazioni locali della lingua italiana parole quali "circa", "con", "devo" e "cui" sono considerate non significative. In genere, è necessario configurare uno o più file del thesaurus ed elenchi di parole non significative. Per altre informazioni, vedere [Configurare e gestire parole non significative ed elenchi di parole non significative per la ricerca full-text](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md).  
  
-   **File del thesaurus.** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installa anche un file del thesaurus per ogni lingua full-text e un file del thesaurus globale. I file del thesaurus installati sono praticamente vuoti, ma è possibile modificarli per definire sinonimi per una lingua o uno scenario aziendale specifico. Sviluppando un thesaurus basato sui dati full-text in uso, è possibile ampliare in modo efficace l'ambito delle query full-text su tali dati. Per altre informazioni, vedere [Configurare e gestire i file del thesaurus per la ricerca full-text](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md).  
  
-   **Filtri (iFilters).**  Per l'indicizzazione di un documento in una colonna del tipo di dati **varbinary(max)**, **image** o **xml** è richiesta l'applicazione di un filtro per eseguire altre operazioni di elaborazione. Il filtro deve essere specifico del tipo di documento (doc, pdf, xls, xml e così via). Per altre informazioni, vedere [Configurazione e gestione di filtri per la ricerca](../../relational-databases/search/configure-and-manage-filters-for-search.md).  
  
 I word breaker, gli stemmer e i filtri vengono eseguiti nel processo host del daemon di filtri (fdhost.exe).  
  
##  <a name="reltasks"></a> Attività correlate  
  
-   [Introduzione alla ricerca full-text](../../relational-databases/search/get-started-with-full-text-search.md)  
  
-   **Scrittura di query full-text**  
  
    -   [Esecuzione della query con ricerca Full-Text](../../relational-databases/search/query-with-full-text-search.md)  
  
    -   [Ricerca di parole vicine a un'altra parola con NEAR](../../relational-databases/search/search-for-words-close-to-another-word-with-near.md)  
  
    -   [Limitazione dei risultati della ricerca mediante RANK](../../relational-databases/search/limit-search-results-with-rank.md)  
  
    -   [Migliorare le prestazioni delle query full-text](../../relational-databases/search/improve-the-performance-of-full-text-queries.md)  
  
    -   [Eseguire ricerche nelle proprietà dei documenti con elenchi delle proprietà di ricerca](../../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
    -   [Trovare GUID del set di proprietà e ID di tipo integer delle proprietà per le proprietà di ricerca](../../relational-databases/search/find-property-set-guids-and-property-integer-ids-for-search-properties.md)  
  
-   **Gestione di cataloghi e indici**  
  
    -   [Creazione e gestione dei cataloghi full-text](../../relational-databases/search/create-and-manage-full-text-catalogs.md)  
  
    -   [Creazione e gestione di indici full-text](../../relational-databases/search/create-and-manage-full-text-indexes.md)  
  
    -   [Scelta di una lingua durante la creazione di un indice full-text](../../relational-databases/search/choose-a-language-when-creating-a-full-text-index.md)  
  
    -   [Popolamento degli indici full-text](../../relational-databases/search/populate-full-text-indexes.md)  
  
    -   [Gestione di indici full-text.](../Topic/Manage%20Full-Text%20Indexes.md)  
  
    -   [Miglioramento delle prestazioni di indici full-text](../../relational-databases/search/improve-the-performance-of-full-text-indexes.md)  
  
    -   [Risoluzione dei problemi nell'indicizzazione full-text](../../relational-databases/search/troubleshoot-full-text-indexing.md)  
  
    -   [Backup e ripristino di indici e cataloghi full-text](../../relational-databases/search/back-up-and-restore-full-text-catalogs-and-indexes.md)  
  
-   **Gestione dei componenti linguistici**  
  
    -   [Configurazione e gestione di filtri per la ricerca](../../relational-databases/search/configure-and-manage-filters-for-search.md)  
  
    -   [Configurazione e gestione di word breaker e stemmer per la ricerca](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)  
  
    -   [Visualizzazione o modifica di word breaker e filtri registrati](../../relational-databases/search/view-or-change-registered-filters-and-word-breakers.md)  
  
    -   [Ripristinare i word breaker utilizzati dalla ricerca alla versione precedente](../../relational-databases/search/revert-the-word-breakers-used-by-search-to-the-previous-version.md)  
  
    -   [Modifica del word breaker utilizzato per le lingue Inglese (Stati Uniti) e Inglese (Regno Unito)](../../relational-databases/search/change-the-word-breaker-used-for-us-english-and-uk-english.md)  
  
    -   [Personalizzare Comportamento di word breaker con un dizionario personalizzato](../../relational-databases/search/customize-the-behavior-of-word-breakers-with-a-custom-dictionary.md)  
  
    -   [Configurare e gestire parole non significative ed elenchi di parole non significative per la ricerca full-text](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)  
  
    -   [Configurare e gestire i file del thesaurus per la ricerca full-text](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md)  
  
-   **Gestione della ricerca full-text**  
  
    -   [Gestione e monitoraggio della ricerca full-text per un'istanza del server](../../relational-databases/search/manage-and-monitor-full-text-search-for-a-server-instance.md)  
  
    -   [Impostazione dell'account del servizio dell'Utilità di avvio del daemon di filtri full-text](../../relational-databases/search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md)  
  
-   [Aggiornamento della ricerca full-text](../../relational-databases/search/upgrade-full-text-search.md)Aggiornamento della ricerca full-text  
  
##  <a name="relcontent"></a> Contenuto correlato  
  
-   [DDL di ricerca full-text, funzioni, stored procedure e viste](../../relational-databases/search/full-text-search-ddl-functions-stored-procedures-and-views.md)  
  
  
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]
