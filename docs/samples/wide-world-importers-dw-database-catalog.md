---
title: Catalogo del database OLAP WideWorldImporters - SQL | Microsoft Docs
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
monikerRange: '>= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: de537c60f8adf2d4860e236421dd0457871ea025
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37984803"
---
# <a name="wideworldimportersdw-database-catalog"></a>Catalogo del database WideWorldImportersDW
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-asdw-pdw-md.md)]
Spiegazioni per gli schemi, tabelle e stored procedure nel database WideWorldImportersDW. 

Il database WideWorldImportersDW viene utilizzato per il data warehousing e l'elaborazione analitica. I dati transazionali sull'analisi di vendite e acquisti vengano generati nel database WideWorldImporters e caricati nel database WideWorldImportersDW utilizzando un **processo ETL giornaliera**.

I dati in WideWorldImportersDW rispecchia pertanto i dati in WideWorldImporters, ma le tabelle vengono organizzate in modo diverso. Mentre WideWorldImporters ha uno schema normalizzato tradizionali, WideWorldImportersDW Usa il [dello schema a stella](https://wikipedia.org/wiki/Star_schema) approccio per la progettazione di tabella. Oltre alle tabelle dei fatti e delle dimensioni, il database include un numero di tabelle di staging che vengono usati nel processo ETL.

## <a name="schemas"></a>Schemi

I diversi tipi di tabelle sono organizzati in tre schemi.

|schema|Description|
|-----------------------------|---------------------|
|Dimension|Tabelle delle dimensioni.|
|Fatti|Tabelle dei fatti.|  
|Integrazione|Le tabelle di staging e altri oggetti necessari per ETL.|  

## <a name="tables"></a>Tabelle

Le tabelle dei fatti e dimensione sono elencate di seguito. Le tabelle nello schema di integrazione vengono usate solo per il processo ETL e non sono elencate.

### <a name="dimension-tables"></a>Tabelle delle dimensioni

WideWorldImportersDW ha le seguenti tabelle delle dimensioni. La descrizione include la relazione con le tabelle di origine del database WideWorldImporters.

|Tabella|Tabelle di origine|
|-----------------------------|---------------------|
|Città|`Application.Cities`, `Application.StateProvinces`, `Application.Countries`.|
|Customer|`Sales.Customers`, `Sales.BuyingGroups`, `Sales.CustomerCategories`.|
|date|Nuova tabella con le informazioni sulle date, inclusi anno fiscale (in base 1 ° novembre avviare per anno fiscale).|
|Employee|`Application.People`(Indici per tabelle con ottimizzazione per la memoria).|
|StockItem|`Warehouse.StockItems`, `Warehouse.Colors`, `Warehouse.PackageType`.|
|Fornitore|`Purchasing.Suppliers`, `Purchasing.SupplierCategories`.|
|PaymentMethod|`Application.PaymentMethods`(Indici per tabelle con ottimizzazione per la memoria).|
|TransactionType|`Application.TransactionTypes`(Indici per tabelle con ottimizzazione per la memoria).|

### <a name="fact-tables"></a>Tabelle dei fatti

WideWorldImportersDW ha le seguenti tabelle dei fatti. La descrizione include la relazione con le tabelle di origine nel database WideWorldImporters, nonché le classi di query o il reporting analitica che ogni tabella dei fatti viene generalmente utilizzato con.

|Tabella|Tabelle di origine|Esempio Analitica|
|-----------------------------|---------------------|---------------------|
|JSON|`Sales.Orders` e `Sales.OrderLines`|Vendite persone, produttività di selezione/packer e sul tempo necessario per selezionare gli ordini. Inoltre, bassa scorte portano a ordini arretrati.|
|Vendita|`Sales.Invoices` e `Sales.InvoiceLines`|Le date di vendita, le date di consegna, redditività nel corso del tempo, redditività dal venditore.|
|Acquisto|`Purchasing.PurchaseOrderLines`|Visual Studio previsto effettivo lead time|
|Transazione|`Sales.CustomerTransactions` e `Purchasing.SupplierTransactions`|Problema date vs finalizzazione date e importi di misurazione.|
|Spostamento dei|`Warehouse.StockTransactions`|Spostamenti nel tempo.|
|Possiedono|`Warehouse.StockItemHoldings`|Livelli di scorte disponibili e il valore.|

## <a name="stored-procedures"></a>Stored procedure

Le stored procedure vengono utilizzate principalmente per il processo ETL e per scopi di configurazione.

Tutte le estensioni dell'esempio sono invitate a usare il `Reports` dello schema per i report di Reporting Services e il `PowerBI` dello schema per l'accesso a Power BI.

### <a name="application-schema"></a>Schema dell'applicazione

Queste procedure vengono utilizzate per configurare l'esempio. Vengono utilizzati per applicare le funzionalità dell'edizione enterprise alla versione standard edition dell'esempio, aggiungere PolyBase e reseed ETL.

|Procedura|Scopo|
|-----------------------------|---------------------|
|Configuration_ApplyPartitionedColumnstoreIndexing|Si applica sia il partizionamento e gli indici columnstore per le tabelle dei fatti.|
|Configuration_ConfigureForEnterpriseEdition|Si applica il partizionamento, columnstore in memoria e indicizzazione.|
|Configuration_EnableInMemory|Sostituisce le tabelle di staging di integrazione con le tabelle ottimizzate per la memoria SCHEMA_ONLY per migliorare le prestazioni ETL.|
|Configuration_ApplyPolybase|Configura un'origine dati esterna, formato di file e tabelle.|
|Configuration_PopulateLargeSaleTable|Applica le modifiche all'edizione enterprise, quindi popola una maggiore quantità di dati per l'anno di calendario 2012 come cronologia aggiuntiva.|
|Configuration_ReseedETL|Rimuove i dati esistenti e riavvia i valori di inizializzazione ETL. Ciò consente il ripopolamento del database OLAP in modo che corrisponda alle righe aggiornate nel database OLTP.|

### <a name="integration-schema"></a>Schema di integrazione

Le procedure utilizzate nel processo ETL rientrano nelle categorie seguenti:
- Procedure di supporto per il pacchetto ETL - Get * tutte le procedure.
- Le procedure utilizzate dal pacchetto ETL per la migrazione di dati di gestione temporanea nelle tabelle del data Warehouse - tutte le procedure di migrazione *.
- `PopulateDateDimensionForYear` -Accetta un anno e assicura che tutte le date per tale anno vengono popolate nel `Dimension.Date` tabella.

### <a name="sequences-schema"></a>Schema di sequenze

Procedure per configurare le sequenze nel database.

|Procedura|Scopo|
|-----------------------------|---------------------|
|ReseedAllSequences|Chiama la routine `ReseedSequenceBeyondTableValue` per tutte le sequenze.|
|ReseedSequenceBeyondTableValue|Usato per riposizionare il valore di sequenza successivo oltre il valore in qualsiasi tabella che utilizza la stessa sequenza. (Ad esempio un `DBCC CHECKIDENT` per equivalente a colonne identity per le sequenze ma tra potenzialmente più tabelle.)|
