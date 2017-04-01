---
title: "Introduzione alla ricerca full-text | Microsoft Docs"
ms.date: "08/22/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-search"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "cataloghi full-text [SQL Server], creazione"
  - "indici full-text [SQL Server], creazione"
  - "ricerca full-text [SQL Server], informazioni"
  - "ricerca full-text [SQL Server], configurazione"
ms.assetid: 1fa628ba-0ee4-4d8f-b086-c4e52962ca4a
caps.latest.revision: 76
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 72
---
# Introduzione alla ricerca full-text
La ricerca full-text supporta più lingue con l'uso dei *componenti linguistici* seguenti: word breaker e stemmer, elenchi di parole non significative e file del thesaurus. I file del thesaurus e, in alcuni casi, gli elenchi di parole non significative richiedono la configurazione da parte di un amministratore di database. Un determinato file del thesaurus supporta tutti gli indici full-text che utilizzano la lingua corrispondente. È inoltre possibile associare un determinato elenco di parole non significative al numero desiderato di indici full-text.  
 
I database di SQL Server sono abilitati per impostazione predefinita per la funzionalità full-text, ma prima è necessario [creare un catalogo full-text](https://msdn.microsoft.com/library/bb326035.aspx) e un indice full-text nelle tabelle o nelle viste indicizzate in cui eseguire la ricerca.
 
 ## Istruzioni dettagliate 
 
 Passare all'argomento [Usare l'indicizzazione guidata full-text](https://msdn.microsoft.com/library/ms180091.aspx) per ottenere le istruzioni dettagliate.

Questo argomento include considerazioni, esempi e collegamenti ad altri argomenti.
##  <a name="configure"></a> Pianificare la configurazione

Esistono due passaggi di base per configurare le colonne della tabella in un database per la ricerca full-text:  
  
- Creazione di un catalogo full-text.  
  
- Creare un indice full-text nelle tabelle o nelle viste indicizzate in cui eseguire la ricerca. 

     Un indice full-text è un tipo speciale di indice funzionale basato su token compilato e gestito dal motore di ricerca full-text. Per creare una ricerca full-text su una tabella o una vista, è necessario disporre di un indice univoco a colonna singola che non ammette valori Null. Questo indice univoco viene utilizzato dal motore di ricerca full-text per eseguire il mapping di ogni riga della tabella a una chiave univoca comprimibile. Un indice full-text può includere colonne **char**, **varchar**, **nchar**, **nvarchar**, **text**, **ntext**, **image**, **xml**, **varbinary** e **varbinary(max)**. Per altre informazioni, vedere [Creare e gestire indici full-text](../../relational-databases/search/create-and-manage-full-text-indexes.md).   
  
     Ogni indice full-text deve appartenere a un catalogo full-text. È possibile creare un catalogo di testo separato per ogni indice full-text oppure associare più indici full-text a un determinato catalogo. Un catalogo full-text è un oggetto virtuale e non appartiene ad alcun filegroup. Il catalogo full-text è un concetto logico che fa riferimento a un gruppo di indici full-text.  
  

 Differenze tra indici full-text e indici SQL Server normali:  
  
|Indici full-text|Indici di SQL Server normali|  
|------------------------|--------------------------------|  
|È consentito un solo indice full-text per tabella.|Sono consentiti più indici normali per tabella.|  
|L'aggiunta di dati a indici full-text, definita *popolamento*, può essere richiesta in modo specifico, tramite pianificazione oppure può avvenire in modo automatico con l'aggiunta di nuovi dati.|Vengono automaticamente aggiornati quando si inseriscono, aggiornano o eliminano dati.|  
|Sono raggruppati all'interno dello stesso database in uno o più cataloghi full-text.|Non sono raggruppati.|  
    
##  <a name="options"></a> Opzioni  
  
### Lingua delle colonne  
 Per informazioni sulla scelta della lingua delle colonne, vedere [Scegliere una lingua durante la creazione di un indice full-text](../../relational-databases/search/choose-a-language-when-creating-a-full-text-index.md).  
  
### Scegliere un filegroup per un indice full-text  
 Il processo di compilazione di un indice full-text richiede l'esecuzione di molte operazioni di I/O (in senso lato, consiste nella lettura di dati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]e nella propagazione dei dati filtrati all'indice full-text). La procedura consigliata consiste nell'individuare l'indice full-text nel filegroup del database ideale per ottimizzare le prestazioni di I/O oppure gli indici full-text in un filegroup diverso in un altro volume.  
  
 È consigliabile archiviare i dati della tabella e i cataloghi full-text associati nello stesso filegroup. Per motivi legati alle prestazioni, a volte potrebbe essere necessario mantenere i dati delle tabelle e l'indice full-text in filegroup diversi archiviati in volumi diversi allo scopo di ottimizzare il parallelismo di I/O.  

  
### Assegnare l'indice full-text   
 
 È consigliabile associare nello stesso catalogo full-text le tabelle con caratteristiche di aggiornamento equivalenti, ad esempio un numero ridotto o elevato di modifiche oppure modifiche frequenti apportate a una determinata ora del giorno. Pianificando il popolamento del catalogo full-text, gli indici full-text mantengono la sincronizzazione con le tabelle senza influire negativamente sull'utilizzo delle risorse del server di database durante i periodi di elevata attività del database.  
  
 Tenere presenti le linee guida seguenti:  
  
-   Selezionare sempre il più piccolo indice univoco disponibile per la chiave univoca full-text. Un indice basato su valori interi a quattro byte è l'impostazione ottimale. Ciò consente di ridurre notevolmente le risorse richieste dal servizio [!INCLUDE[msCoName](../../includes/msconame-md.md)] Search nel file system. Se la chiave primaria è di grandi dimensioni (oltre 100 byte), considerare la possibilità di scegliere un altro indice univoco nella tabella (o di creare un altro indice univoco) come chiave univoca full-text. In caso contrario, se le dimensioni della chiave univoca raggiungono il massimo consentito (900 byte), non sarà possibile eseguire il popolamento full-text.  
  
-   Se viene indicizzata una tabella che include milioni di righe, assegnarla al relativo catalogo full-text.  
  
-   Considerare la quantità di modifiche apportate alle tabelle durante l'indicizzazione full-text, nonché il numero totale di righe. Se il numero totale di righe modificate sommato al numero di righe della tabella presenti durante l'ultimo popolamento full-text corrisponde a milioni di righe, assegnare la tabella al relativo catalogo full-text.  

  
### Associare un elenco di parole non significative   
  Un *elenco di parole non significative* è un elenco di termini che non vengono considerati nelle query, viene associato a ogni indice full-text e le parole in esso contenute vengono applicate alle query full-text di quell'indice. Per impostazione predefinita, a un nuovo indice full-text viene associato l'elenco di parole non significative di sistema. È anche possibile creare e usare un elenco di parole non significative personalizzato. Per altre informazioni, vedere [Configurare e gestire parole non significative ed elenchi di parole non significative per la ricerca full-text](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md).  
  
 Ad esempio, l'istruzione [CREATE FULLTEXT STOPLIST](../../t-sql/statements/create-fulltext-stoplist-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] seguente consente di creare un nuovo elenco di parole non significative full-text denominato myStoplist3, copiando dall'elenco di parole non significative di sistema:  
  
```  
CREATE FULLTEXT STOPLIST myStoplist FROM SYSTEM STOPLIST;  
GO  
```  
  
 L'istruzione [ALTER FULLTEXT STOPLIST](../../t-sql/statements/alter-fulltext-stoplist-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] seguente consente di modificare un elenco di parole non significative denominato myStoplist, aggiungendo la parola "en" per lo spagnolo e poi per il francese:  
  
```  
ALTER FULLTEXT STOPLIST MyStoplist ADD 'en' LANGUAGE 'Spanish';  
ALTER FULLTEXT STOPLIST MyStoplist ADD 'en' LANGUAGE 'French';  
GO  
```  
    
## Aggiornare un indice  
 Come i normali indici [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], gli indici full-text possono essere aggiornati automaticamente alla modifica dei dati delle tabelle associate. Questo è il comportamento predefinito. In alternativa, è possibile aggiornare gli indici full-text manualmente o a intervalli pianificati specificati. Poiché il popolamento di un indice full-text può richiedere tempi lunghi e l'utilizzo di molte risorse, l'aggiornamento dell'indice full-text viene in genere eseguito in background come processo asincrono in seguito alle modifiche apportate alla tabella di base. 
 
 L'aggiornamento immediato di un indice full-text dopo ogni modifica apportata alla tabella di base può richiedere l'utilizzo di molte risorse. Pertanto, se la frequenza con cui si eseguono aggiornamenti, inserimenti ed eliminazioni è molto elevata, è possibile notare un calo delle prestazioni a livello di esecuzione delle query. In questo caso, considerare la pianificazione di aggiornamenti con rilevamento manuale delle modifiche per gestire gradualmente le numerose modifiche, anziché dividere le risorse con le query.  
  
 Monitorare lo stato del popolamento usando la funzione FULLTEXTCATALOGPROPERTY o OBJECTPROPERTYEX. Per ottenere lo stato del popolamento del catalogo, eseguire l'istruzione seguente:  
  
```  
SELECT FULLTEXTCATALOGPROPERTY('AdvWksDocFTCat', 'Populatestatus');  
```  
  
 In genere, se è in corso un popolamento completo, il risultato restituito è 1.  
 

##  <a name="example"></a> Esempio: configurare la ricerca full-text  
 L'esempio in due parti seguente consiste nella creazione di un catalogo full-text denominato `AdvWksDocFTCat` nel database AdventureWorks e quindi nella creazione di un indice full-text nella tabella `Document` in [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Questa istruzione determina la creazione del catalogo full-text nella directory predefinita specificata durante l'installazione. La cartella denominata `AdvWksDocFTCat` si trova nella directory predefinita.  
  
1.  Per creare un catalogo full-text denominato `AdvWksDocFTCat`, nell'esempio viene usata un'istruzione [CREATE FULLTEXT CATALOG](../../t-sql/statements/create-fulltext-catalog-transact-sql.md):  
  
    ```  
    USE AdventureWorks;  
    GO  
    CREATE FULLTEXT CATALOG AdvWksDocFTCat;  
    ```  
  
2.  Prima di creare un indice full-text nella tabella Document, assicurarsi che la tabella disponga di un indice univoco a singola colonna che non ammette valori Null. L'istruzione [CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md) seguente consente di creare un indice univoco, `ui_ukDoc`, nella colonna DocumentID della tabella Document:  
  
    ```  
    CREATE UNIQUE INDEX ui_ukDoc ON Production.Document(DocumentID);  
    ```  
  
3.  Quando si dispone di una chiave univoca, è possibile creare un indice full-text nella tabella `Document` usando l'istruzione [CREATE FULLTEXT INDEX](../../t-sql/statements/create-fulltext-index-transact-sql.md) seguente.  
  
    ```  
    CREATE FULLTEXT INDEX ON Production.Document  
    (  
        Document                         --Full-text index column name   
            TYPE COLUMN FileExtension    --Name of column that contains file type information  
            Language 2057                 --2057 is the LCID for British English  
    )  
    KEY INDEX ui_ukDoc ON AdvWksDocFTCat --Unique index  
    WITH CHANGE_TRACKING AUTO            --Population type;  
    GO  
  
    ```  
  
     L'elemento TYPE COLUMN definito in questo esempio specifica la colonna del tipo nella tabella che contiene il tipo di documento in ciascuna riga della colonna 'Document' (che è di tipo binario). Nella colonna del tipo è archiviata l'estensione file fornita dall'utente, ovvero "doc", "xls" e così via, del documento in una determinata riga. Il motore di ricerca full-text utilizza l'estensione file in una determinata riga per richiamare il filtro corretto da utilizzare per l'analisi dei dati di quella riga. Al termine dell'analisi dei dati binari della riga eseguita tramite il filtro, il word breaker specificato analizzerà il contenuto. In questo esempio viene utilizzato il word breaker per l'Inglese britannico. Si noti che il processo di filtro viene eseguito unicamente durante l'indicizzazione o quando un utente inserisce o aggiorna una colonna della tabella di base con il rilevamento delle modifiche automatico abilitato per l'indice full-text. Per altre informazioni, vedere [Configurazione e gestione di filtri per la ricerca](../../relational-databases/search/configure-and-manage-filters-for-search.md).  
  
   
## Creazione di un catalogo full-text  
  
-   [CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)  
  
-   [Creazione e gestione dei cataloghi full-text](../../relational-databases/search/create-and-manage-full-text-catalogs.md)  
  
## Visualizzare gli indici  
  
-   [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)  
  
## Creare un indice univoco  
  
-   [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)  
  
-   [Aprire Progettazione tabelle &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/open-table-designer-visual-database-tools.md)  
  
## Creare un indice full-text  
  
-   [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)  
  
-   [Creazione e gestione di indici full-text](../../relational-databases/search/create-and-manage-full-text-indexes.md)  
  
## Visualizzare informazioni su un indice full-text  
  
|Catalogo o vista a gestione dinamica|Descrizione|  
|----------------------------------------|-----------------|  
|[sys.fulltext_index_catalog_usages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-index-catalog-usages-transact-sql.md)|Restituisce una riga per ogni catalogo full-text in riferimento all'indice full-text.|  
|[sys.fulltext_index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md)|Contiene una riga per ogni colonna che fa parte di un indice full-text.|  
|[sys.fulltext_index_fragments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-index-fragments-transact-sql.md)|Un indice full-text utilizza tabelle interne denominate frammenti di indice full-text per archiviare i dati dell'indice invertito. Questa vista può essere utilizzata per eseguire una query sui metadati relativi a tali frammenti. Nella vista è contenuta una riga per ogni frammento di indice full-text presente in ogni tabella contenente un indice full-text.|  
|[sys.fulltext_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md)|Contiene una riga per indice full-text di un oggetto in formato di tabella.|  
|[sys.dm_fts_index_keywords &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-transact-sql.md)|Restituisce informazioni sul contenuto di un indice full-text per la tabella specificata.|  
|[sys.dm_fts_index_keywords_by_document &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)|Restituisce informazioni sul contenuto a livello di documento di un indice full-text per la tabella specificata. Una determinata parola chiave può essere inclusa in diversi documenti.|  
|[sys.dm_fts_index_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql.md)|Restituisce informazioni sui popolamenti di indici full-text in corso.|  
  

  
## E altre informazioni 
 [CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)   
 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)   
 [CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-stoplist-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [Popolamento degli indici full-text](../../relational-databases/search/populate-full-text-indexes.md)   
 [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md)   
 [OBJECTPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/objectpropertyex-transact-sql.md)  
  
  