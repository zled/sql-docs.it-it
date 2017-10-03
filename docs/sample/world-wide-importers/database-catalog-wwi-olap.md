---
title: Catalogo del database | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- samples
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e47c0022-ce87-4ba5-a24b-df55efe66431
caps.latest.revision: 3
author: BarbKess
ms.author: barbkess
manager: jhubbard
robots: noindex,nofollow
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 036afa491ae8390c38520d7dff2e5c6cd0d1a419
ms.contentlocale: it-it
ms.lasthandoff: 09/27/2017

---
# <a name="database-catalog"></a>Catalogo del database
Il database WideWorldImporters contiene tutte le informazioni sulle transazioni e dati giornalieri di acquisti e vendite, nonché dati del sensore dei veicoli e chat fredda.

## <a name="schemas"></a>Schemi

WideWorldImporters utilizza gli schemi per scopi diversi, ad esempio l'archiviazione dei dati, che definisce la modalità con cui gli utenti possono accedere i dati e fornisce oggetti per l'integrazione e lo sviluppo di data warehouse.

### <a name="data-schemas"></a>Schemi di dati

Questi schemi contengono i dati. Un numero di tabelle necessarie per tutti gli altri schemi e si trova nello schema dell'applicazione.

|schema|Description|
|-----------------------------|---------------------|
|Applicazione|Livello di applicazione utenti, contatti e i parametri. Contiene anche le tabelle di riferimento con i dati che viene utilizzati da più schemi|
|Purchasing|Magazzino acquisti da fornitori e i dettagli relativi ai fornitori.|  
|Sales|Elemento vendite ai clienti di vendita al dettaglio e dettagli sulle persone di clienti e delle vendite magazzino. |  
|Warehouse|Scorte di magazzino e le transazioni.|  

### <a name="secure-access-schemas"></a>Schemi di accesso protetto

Questi schemi vengono utilizzati per le applicazioni esterne che non è consentite accedere direttamente alle tabelle di dati. Contengono viste e stored procedure utilizzate da applicazioni esterne.

|schema|Description|
|-----------------------------|---------------------|
|Sito Web|Accesso al database dal sito Web aziendale avviene totalmente tramite questo schema.|
|Report|Accesso al database dai report di Reporting Services avviene totalmente tramite questo schema.|
|Power BI|Accesso al database dal dashboard di Power BI tramite il Gateway aziendale avviene totalmente tramite questo schema.|

Si noti che i report e Power BI gli schemi non vengono utilizzati nella versione iniziale del database di esempio. Tuttavia, gli esempi di tutti i Power BI e Reporting Services basati su questo database sono incoraggiati a utilizzare questi schemi.

### <a name="development-schemas"></a>Schemi di sviluppo

Schemi speciale

|schema|Description|
|-----------------------------|---------------------|
|Integrazione|Gli oggetti e le procedure necessari per l'integrazione di data warehouse (ad esempio la migrazione dei dati al database WideWorldImportersDW).|
|Sequenze|Contiene le sequenze utilizzate da tutte le tabelle nell'applicazione.|

## <a name="tables"></a>Tabelle

Tutte le tabelle nel database sono negli schemi di dati.

### <a name="application-schema"></a>Schema dell'applicazione

Dettagli dei parametri e gli utenti (utenti e contatti), insieme alle tabelle di riferimento comuni (comuni a più altri schemi).

|Tabella|Description|
|-----------------------------|---------------------|
|SystemParameters|Contiene i parametri configurabili a livello di sistema.|
|Utenti|Contiene i nomi utente, informazioni di contatto per tutti gli utenti che usano l'applicazione e per le persone che si occupa di Wide World Importers in organizzazioni del cliente. Sono inclusi personale, clienti, fornitori e gli eventuali altri contatti. Per gli utenti che dispongono dell'autorizzazione per utilizzare il sito Web o sistema, le informazioni includono i dettagli di accesso.|
|Città|Esistono molti indirizzi archiviati nel sistema, per gli utenti, indirizzi di recapito di organizzazione dei clienti, gli indirizzi di prelievo a fornitori e così via. Ogni volta che viene archiviato un indirizzo, è presente un riferimento a una città in questa tabella. È inoltre disponibile un percorso spaziale per ogni città.|
|StateProvinces|Città fanno parte di stati o province. Questa tabella contiene i dettagli di questi, tra cui i dati spaziali che descrive i limiti di ogni stato o provincia.|
|Countries|Stati o province fanno parte di terzi. Questa tabella contiene i dettagli di questi, tra cui i dati spaziali che descrive i limiti di ogni paese.|
|DeliveryMethods|Possibilità per fornire le voci (ad esempio, camion/furgone, post, prelievo, courier e così via)|
|PaymentMethods|Le scelte per pagamenti (ad esempio, contanti, assegno, EFT, ecc.)|
|TransactionTypes|Tipi di clienti, fornitori o transazioni predefinite (ad esempio, fattura, nota di credito e così via)|

### <a name="purchasing-schema"></a>Acquisto di Schema

Dettagli di fornitori e acquisti in magazzino.

|Tabella|Description|
|-----------------------------|---------------------|
|Suppliers|Tabella entità principale per i fornitori (le organizzazioni)|
|SupplierCategories|Categorie per i fornitori (ad esempio, novità, giocattoli, clothing, creazione di pacchetti e così via).|
|SupplierTransactions|Tutte le transazioni finanziarie che sono correlati al fornitore (fatture, pagamenti)|
|PurchaseOrders|Dettagli degli ordini di acquisto fornitore|
|PurchaseOrderLines|Gli ordini di acquisto di righe di dettaglio dal fornitore|

 
### <a name="sales-schema"></a>Schema delle vendite

Dettagli di clienti, i venditori e delle vendite in magazzino.

|Tabella|Description|
|-----------------------------|---------------------|
|Customers|Tabelle di entità principale per i clienti (le organizzazioni o singoli utenti)|
|CustomerCategories|Categorie per i clienti (ie originalità archivi, supermercati e così via)|
|BuyingGroups|Le organizzazioni clienti possono far parte di gruppi di esercitare un maggiore potenza di acquisto|
|CustomerTransactions|Tutte le transazioni finanziarie che sono correlati al cliente (fatture, pagamenti)|
|SpecialDeals|Prezzi speciali. Questo può includere prezzi fissi, discount in dollari o percentuale di sconto.|
|Orders|Dettagli degli ordini|
|OrderLines|Righe di dettagli degli ordini cliente|
|Fatture|Dettagli delle fatture cliente|
|InvoiceLines|Righe di dettaglio da fatture cliente|

### <a name="warehouse-schema"></a>Schema del warehouse

Dettagli degli elementi predefiniti, le aziende e transazioni.

|Tabella|Description|
|-----------------------------|---------------------|
|StockItems|Tabella entità principale per gli elementi predefiniti|
|StockItemHoldings|Colonne non temporali per le voci. Queste colonne arefrequently aggiornato.|
|StockGroups|Gruppi per la classificazione magazzino degli articoli (ad esempio, novità, giocattoli, novità commestibili e così via)|
|StockItemStockGroups|Quali azioni sono gli elementi in cui stock gruppi (da molti a molti)|
|Colori|Le voci (facoltativamente) possono avere colori|
|PackageTypes|Modi in cui gli elementi delle scorte possono essere incluso nel pacchetto (ad esempio, casella scatola, tavolozza, kg, e così via.|
|StockItemTransactions|Transazioni che copre tutti i movimenti di tutti gli elementi predefiniti (ricezione, la vendita, annullamento)|
|VehicleTemperatures|Temperature regolarmente registrate da chillers veicolo|
|ColdRoomTemperatures|Regolarmente registrati temperature di chillers deposito|


## <a name="design-considerations"></a>Considerazioni sulla progettazione

Progettazione di database è soggettiva e non è possibile o meno esatte per progettare un database. Gli schemi e le tabelle nel database mostrano idee per come è possibile progettare il database in uso.

### <a name="schema-design"></a>Progettazione di schemi

WideWorldImporters utilizza un numero ridotto di schemi in modo che sia facile da comprendere il sistema di database e illustrano i principi di database.  

Laddove possibile, il database collocates tabelle che sono in genere sottoposti a query insieme nello stesso schema per ridurre al minimo la complessità di join.

Lo schema del database è stato generato codice basato su una serie di tabelle di metadati in un altro database WWI_Preparation. In questo modo WideWorldImporters un livello molto elevato di coerenza di progettazione, denominazione coerenza e completezza. Per informazioni dettagliate su come è stato generato lo schema, vedere il codice sorgente: [wide-world-utilità di importazione/wwi-database-script](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/wwi-database-scripts)

### <a name="table-design"></a>Progettazione tabella

- Tutte le tabelle dispongono di chiavi primarie di singola colonna per la semplicità di join.
- Tutti gli schemi, tabelle, colonne, indici e vincoli check presentano una descrizione estesa di proprietà che può essere usato per identificare lo scopo dell'oggetto o colonna. Le tabelle con ottimizzazione per la memoria sono un'eccezione perché attualmente non supportano le proprietà estese.
- Tutte le chiavi esterne vengono indicizzate automaticamente a meno che non è un altro indice non cluster con lo stesso componente a sinistra.
- La numerazione automatica nelle tabelle è basata su sequenze. Queste sequenze sono più facili da utilizzare tra i server collegati e di ambienti simili rispetto alle colonne di identità. Le tabelle con ottimizzazione per la memoria utilizzano le colonne IDENTITY, poiché non supportate in SQL Server 2016.
- Una singola sequenza (TransactionID) viene utilizzata per queste tabelle: CustomerTransactions SupplierTransactions e StockItemTransactions. Viene descritto come un set di tabelle può avere un'unica sequenza.
- Alcune colonne presentano valori predefiniti appropriati.

### <a name="security-schemas"></a>Schemi di sicurezza

Per la sicurezza, WideWorldImporters non consente alle applicazioni esterne accedere direttamente gli schemi di dati. Per isolare l'accesso, WideWorldImporters utilizza gli schemi di accesso di sicurezza che non contengono dati, ma contengono viste e stored procedure. Le applicazioni esterne utilizzano gli schemi di sicurezza per recuperare i dati che sono autorizzati a visualizzare.  In questo modo, gli utenti possono eseguire solo le viste e stored procedure negli schemi di accesso protetto

Ad esempio, in questo esempio sono inclusi i dashboard di Power BI. Un'applicazione esterna consente di accedere ai dashboard di Power BI dal gateway di Power BI come utente che dispone dell'autorizzazione di sola lettura per lo schema di Power BI.  Per l'autorizzazione di sola lettura, l'utente deve solo l'autorizzazione SELECT ed EXECUTE per lo schema di Power BI. Un amministratore del database WWI assegna le autorizzazioni in base alle esigenze.

## <a name="stored-procedures"></a>Stored procedure

Stored procedure sono organizzate in schemi. La maggior parte degli schemi vengono utilizzata per scopi di esempio o configurazione.

Il `Website` schema contiene le stored procedure che possono essere utilizzate da un front-end Web.

Il `Reports` e `PowerBI` gli schemi sono concepiti per reporting services e a scopo di Power BI. Tutte le estensioni dell'esempio si consiglia di utilizzare questi schemi ai fini dei report.

### <a name="website-schema"></a>Schema di sito Web

Queste sono le procedure utilizzate da un'applicazione client, ad esempio un front-end Web.

|Procedura|Scopo|
|-----------------------------|---------------------|
|ActivateWebsiteLogon|Consente a un utente (da `Application.People`) di accedere al sito Web.|
|ChangePassword|Modifica password di un utente (per gli utenti che non utilizzano meccanismi di autenticazione esterno).|
|InsertCustomerOrders|Consente l'inserimento di uno o più ordini cliente (incluse le righe di ordine).|
|InvoiceCustomerOrders|Accetta un elenco di ordini di ricevere una fattura ed elabora le fatture.|
|RecordColdRoomTemperatures|Accetta un elenco di dati del sensore, come un parametro con valori di tabella (TVP) e applica i dati per il `Warehouse.ColdRoomTemperatures` tabella temporale.|
|RecordVehicleTemperature|Accetta una matrice JSON e viene utilizzato per aggiornare `Warehouse.VehicleTemperatures`.|
|SearchForCustomers|Cerca i clienti in base al nome o parte del nome (il nome della società o il nome di persona).|
|SearchForPeople|Cerca utenti tramite il nome o parte del nome.|
|SearchForStockItems|Cerca le voci per nome o parte del nome o i commenti di marketing.|
|SearchForStockItemsByTags|Cerca le voci dai tag.|
|SearchForSuppliers|Consente di cercare fornitori per nome o parte del nome (il nome della società o il nome di persona).|

### <a name="integration-schema"></a>Schema di integrazione

Le stored procedure in questo schema vengono utilizzate dal processo ETL. Ottenere i dati necessari da diverse tabelle per l'intervallo di tempo necessari per il [pacchetto ETL](etl-workflow.md).

### <a name="dataloadsimulation-schema"></a>Schema DataLoadSimulation

Consente di simulare un carico di lavoro che inserisce le vendite e acquisti. La stored procedure principale è `PopulateDataToCurrentDate`, che viene utilizzato per inserire i dati di esempio fino alla data corrente.

|Procedura|Scopo|
|-----------------------------|---------------------|
|Configuration_ApplyDataLoadSimulationProcedures|Ricreare le procedure necessarie per i dati di simulazione di carico. Questo è necessario per portare i dati fino alla data corrente.|
|Configuration_RemoveDataLoadSimulationProcedures|Consente di rimuovere le procedure nuovamente dopo la simulazione di dati è stata completata.|
|DeactiveTemporalTablesBeforeDataLoad|Rimuove la natura temporale di tutte le tabelle temporali e ove applicabile, applica un trigger in modo che è possibile apportare modifiche come se sono stati applicati a una data precedente rispetto a consentono le tabelle temporali con sys.|
|PopulateDataToCurrentDate|Utilizzato per visualizzare i dati fino alla data corrente. Deve essere eseguito prima di altre opzioni di configurazione dopo il ripristino del database da un backup iniziale.|
|ReactivateTemporalTablesAfterDataLoad|Ristabilisce le tabelle temporali, inclusi la verifica di coerenza dei dati. (Rimuove i trigger associati).|


### <a name="application-schema"></a>Schema dell'applicazione

Queste procedure vengono utilizzate per configurare l'esempio. Vengono utilizzati per applicare le funzionalità dell'edizione enterprise per la versione standard edition dell'esempio, nonché di aggiungere il controllo e l'indicizzazione full-text.

|Procedura|Scopo|
|-----------------------------|---------------------|
|AddRoleMemberIfNonexistant|Aggiunge un membro a un ruolo se non è già membro del ruolo|
|Configuration_ApplyAuditing|Aggiunge il controllo. Il controllo server viene applicato per i database standard edition; il controllo dei database aggiuntivo viene aggiunto per enterprise edition.|
|Configuration_ApplyColumnstoreIndexing|Si applica l'indicizzazione a columnstore `Sales.OrderLines` e `Sales.InvoiceLines` e reindexes in modo appropriato.|
|Configuration_ApplyFullTextIndexing|Si applica a indici full-text da `Application.People`, `Sales.Customers`, `Purchasing.Suppliers`, e `Warehouse.StockItems`. Sostituisce `Website.SearchForPeople`, `Website.SearchForSuppliers`, `Website.SearchForCustomers`, `Website.SearchForStockItems`, `Website.SearchForStockItemsByTags` con le routine di sostituzione che usano l'indicizzazione full-text.|
|Configuration_ApplyPartitioning|Si applica il partizionamento delle tabelle per `Sales.CustomerTransactions and `'Purchasing.SupplierTransactions e ridispone gli indici in base alle esigenze.|
|Configuration_ApplyRowLevelSecurity|Applica protezione a livello di riga per i clienti di filtro per sales territory relativi ruoli.|
|Configuration_ConfigureForEnterpriseEdition|Si applica columnstore l'indicizzazione full-text, in memoria, polybase e partizionamento.|
|Configuration_EnableInMemory|Aggiunge un filegroup con ottimizzazione per la memoria (quando non funziona in Azure), sostituisce `Warehouse.ColdRoomTemperatures`, `Warehouse.VehicleTemperatures` con gli equivalenti in memoria e viene eseguita la migrazione dei dati, ricrea il `Website.OrderIDList`, `Website.OrderList`, `Website.OrderLineList`, `Website.SensorDataList` tipi di tabella con ottimizzazione per la memoria equivalenti, Elimina e ricrea le procedure `Website.InvoiceCustomerOrders`, `Website.InsertCustomerOrders`, e `Website.RecordColdRoomTemperatures` che utilizza questi tipi di tabella.|
|Configuration_RemoveAuditing|Rimuove la configurazione del controllo.|
|Configuration_RemoveRowLevelSecurity|Rimuove la configurazione di sicurezza a livello di riga (è necessaria per le modifiche alle tabelle associate).|
|CreateRoleIfNonExistant|Crea un ruolo del database se non esiste già.|


### <a name="sequences-schema"></a>Schema di sequenze

Procedure per configurare le sequenze nel database.

|Procedura|Scopo|
|-----------------------------|---------------------|
|ReseedAllSequences|Chiama la routine ReseedSequenceBeyondTableValue per tutte le sequenze.|
|ReseedSequenceBeyondTableValue|Usato per riposizionare il valore di sequenza successivo oltre il valore in qualsiasi tabella che utilizza la stessa sequenza. (Ad esempio un DBCC CHECKIDENT per equivalente di colonne di identità per le sequenze, ma tra potenzialmente più tabelle).|

