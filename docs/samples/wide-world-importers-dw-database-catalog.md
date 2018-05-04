---
title: Catalogo del database OLAP WideWorldImporters - SQL | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
robots: noindex,nofollow
monikerRange: '>= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 72369c26ae73272fcec22edbd046eaa2d3a6ec1b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="wideworldimportersdw-database-catalog"></a>Catalogo del database WideWorldImportersDW
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Spiegazione per gli schemi, tabelle e stored procedure nel database WideWorldImportersDW. 

Il database WideWorldImportersDW viene utilizzato per l'elaborazione analitica e di data warehouse. I dati sulle vendite e acquisti transazionali vengano generati nel database WideWorldImporters e caricati nel database WideWorldImportersDW utilizzando un **processo ETL giornaliero**.

I dati in WideWorldImportersDW rispecchia pertanto i dati in WideWorldImporters, ma le tabelle vengono organizzate in modo diverso. Mentre WideWorldImporters ha uno schema di normalizzato tradizionale, WideWorldImportersDW Usa il [schema a stella](https://wikipedia.org/wiki/Star_schema) approccio per la progettazione della tabella. Oltre alle tabelle dei fatti e delle dimensioni, il database include un numero di tabelle di gestione temporanea vengono utilizzati nel processo ETL.

## <a name="schemas"></a>Schemi

I diversi tipi di tabelle sono organizzati in tre schemi.

|Schema|Description|
|-----------------------------|---------------------|
|Dimensione|Tabelle delle dimensioni.|
|Fatti|Tabelle dei fatti.|  
|Integrazione|Le tabelle di gestione temporanea e altri oggetti necessari per ETL.|  

## <a name="tables"></a>Tabelle

Di seguito sono elencate le tabelle di dimensioni e fatti. Le tabelle nello schema di integrazione vengono utilizzate solo per il processo ETL e non sono elencate.

### <a name="dimension-tables"></a>Tabelle delle dimensioni

WideWorldImportersDW ha le seguenti tabelle delle dimensioni. La descrizione include la relazione con le tabelle di origine nel database WideWorldImporters.

|Tabella|Tabelle di origine|
|-----------------------------|---------------------|
|City|`Application.Cities`, `Application.StateProvinces`, `Application.Countries`.|
|Customer|`Sales.Customers`, `Sales.BuyingGroups`, `Sales.CustomerCategories`.|
|Data|Nuova tabella con le informazioni sulle date, tra cui esercizio (in base al 1 ° novembre avviare esercizio).|
|Employee|`Application.People`.|
|StockItem|`Warehouse.StockItems`, `Warehouse.Colors`, `Warehouse.PackageType`.|
|Fornitore|`Purchasing.Suppliers`, `Purchasing.SupplierCategories`.|
|PaymentMethod|`Application.PaymentMethods`.|
|TransactionType|`Application.TransactionTypes`.|

### <a name="fact-tables"></a>Tabelle dei fatti

WideWorldImportersDW ha le seguenti tabelle dei fatti. La descrizione include la relazione con le tabelle di origine del database WideWorldImporters, nonché le classi di query o reporting analitica che ogni tabella dei fatti viene generalmente utilizzato con.

|Tabella|Tabelle di origine|Esempio Analitica|
|-----------------------------|---------------------|---------------------|
|JSON|`Sales.Orders`e`Sales.OrderLines`|Vendite persone, la produttività di selezione/chi e nel tempo per prelevare ordini. Inoltre, bassa situazioni predefinite iniziali per eseguire il backup degli ordini.|
|Vendita|`Sales.Invoices`e`Sales.InvoiceLines`|Le date di vendita, le date di consegna, redditività nel tempo, redditività dal venditore.|
|Acquisto|`Purchasing.PurchaseOrderLines`|Vs previsto effettivo lead time|
|Transazione|`Sales.CustomerTransactions`e`Purchasing.SupplierTransactions`|Misurazione date vs finalizzazione date e importi.|
|Spostamento|`Warehouse.StockTransactions`|Spostamenti nel tempo.|
|Azienda azionario|`Warehouse.StockItemHoldings`|Livelli di scorte disponibili e il valore.|

## <a name="stored-procedures"></a>Stored procedure

Le stored procedure vengono utilizzate principalmente per il processo ETL e per scopi di configurazione.

Tutte le estensioni dell'esempio si consiglia di utilizzare il `Reports` dello schema per i report di Reporting Services e `PowerBI` dello schema per l'accesso a Power BI.

### <a name="application-schema"></a>Schema dell'applicazione

Queste procedure vengono utilizzate per configurare l'esempio. Vengono utilizzati per applicare le funzionalità dell'edizione enterprise alla versione standard edition dell'esempio, aggiungere PolyBase, reseed ETL.

|Procedura|Scopo|
|-----------------------------|---------------------|
|Configuration_ApplyPartitionedColumnstoreIndexing|Si applica il partizionamento e columnstore indici per le tabelle dei fatti.|
|Configuration_ConfigureForEnterpriseEdition|Si applica il partizionamento columnstore indicizzazione e in memoria.|
|Configuration_EnableInMemory|Sostituisce le tabelle di gestione temporanea di integrazione con le tabelle con ottimizzazione per la memoria SCHEMA_ONLY per migliorare le prestazioni di ETL.|
|Configuration_ApplyPolybase|Configura un'origine dati esterna, un formato di file e una tabella.|
|Configuration_PopulateLargeSaleTable|Applica le modifiche all'edizione enterprise, quindi popola una maggiore quantità di dati per l'anno di calendario 2012 come cronologia aggiuntiva.|
|Configuration_ReseedETL|Rimuove i dati esistenti e riavvia il seeding ETL. In questo modo per ripopolare il database OLAP in modo che corrisponda alle righe aggiornate nel database OLTP.|

### <a name="integration-schema"></a>Schema di integrazione

Le procedure utilizzate per il processo ETL rientrano nelle seguenti categorie:
- Procedure di supporto per il pacchetto ETL - Get * tutte le procedure.
- Le procedure utilizzate dal pacchetto ETL per la migrazione di dati di gestione temporanea nelle tabelle del data Warehouse - tutte le procedure di migrazione *.
- `PopulateDateDimensionForYear` -Accetta un anno e assicura che tutte le date per tale anno vengono popolate nel `Dimension.Date` tabella.

### <a name="sequences-schema"></a>Schema di sequenze

Procedure per configurare le sequenze nel database.

|Procedura|Scopo|
|-----------------------------|---------------------|
|ReseedAllSequences|Chiama la routine `ReseedSequenceBeyondTableValue` per tutte le sequenze.|
|ReseedSequenceBeyondTableValue|Usato per riposizionare il valore di sequenza successivo oltre il valore in qualsiasi tabella che utilizza la stessa sequenza. (Ad esempio un `DBCC CHECKIDENT` per equivalente di colonne di identità per le sequenze, ma tra potenzialmente più tabelle.)|
