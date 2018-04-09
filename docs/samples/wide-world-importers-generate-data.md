---
title: WideWorldImporters generare dati - database SQL di esempio | Documenti Microsoft
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: ''
ms.component: samples
ms.technology:
- " database-engine "
ms.topic: article
author: BarbKess
ms.author: barbkess
manager: craigg
robots: noindex,nofollow
ms.workload: Inactive
ms.openlocfilehash: d99cdfacbe08cd3b81fb46bb61b49cab290780f4
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2018
---
# <a name="wideworldimporters-data-generation"></a>Generazione di dati WideWorldImporters
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Le versioni rilasciate dei database WideWorldImporters e WideWorldImportersDW contiene dati 2013 1 gennaio, fino al giorno questi database sono stati generati iniziale.

Quando si utilizzano i database di esempio, potrebbe essere utile includere dati di esempio più recenti.

## <a name="data-generation-in-wideworldimporters"></a>Generazione di dati in WideWorldImporters

Per generare dati di esempio fino alla data corrente, procedere come segue:

1. Se non è ancora stato fatto, installare una versione pulita del database WideWorldImporters. Per istruzioni sull'installazione, **WideWorldImporters installazione e configurazione**.
2. Eseguire l'istruzione seguente nel database:

```
    EXECUTE DataLoadSimulation.PopulateDataToCurrentDate
        @AverageNumberOfCustomerOrdersPerDay = 60,
        @SaturdayPercentageOfNormalWorkDay = 50,
        @SundayPercentageOfNormalWorkDay = 0,
        @IsSilentMode = 1,
        @AreDatesPrinted = 1;
```

Questa istruzione aggiunge vendita di esempio e i dati di acquisto nel database, fino alla data corrente. Viene restituito lo stato di avanzamento dei dati generazione giorno per giorno. Può richiedere circa 10 minuti per ogni anno che necessita di dati. Esistono alcune differenze nei dati generati da un'esecuzione, poiché è un fattore casuale la generazione di dati.

Per aumentare o diminuire la quantità di dati generati, in termini di ordini per ogni giorno, modificare il valore per il parametro `@AverageNumberOfCustomerOrdersPerDay`. I parametri `@SaturdayPercentageOfNormalWorkDay` e `@SundayPercentageOfNormalWorkDay` vengono utilizzati per determinare il volume degli ordini per giorni del fine settimana.

## <a name="importing-generated-data-in-wideworldimportersdw"></a>Importazione di dati generati in WideWorldImportersDW

Per importare i dati di esempio fino alla data corrente nel database OLAP WideWorldImportersDW, seguire questi passaggi:

1. Eseguire la logica di generazione dati nel database OLTP WideWorldImporters, utilizzando i passaggi precedenti.
2. Se non è ancora stato fatto, installare una versione pulita del database WideWorldImportersDW. Per istruzioni sull'installazione, **WideWorldImporters installazione e configurazione**.
3. Reinizializzare il database OLAP eseguendo l'istruzione seguente nel database:

    ```sql
    EXECUTE [Application].Configuration_ReseedETL
    ```

4. Eseguire il pacchetto SSIS **ETL.ispac giornaliero** per importare i dati nel database OLAP. Per istruzioni su come eseguire il processo ETL, vedere **flusso di lavoro ETL WideWorldImporters**.

## <a name="generating-data-in-wideworldimportersdw-for-performance-testing"></a>La generazione di dati in WideWorldImportersDW per il test delle prestazioni

WideWorldImportersDW ha la possibilità di aumentare la dimensione dei dati, allo scopo di test delle prestazioni, ad esempio con columnstore cluster arbitrariamente.

Una delle sfide consiste nel mantenere le dimensioni del download sufficientemente ridotto da scaricare con facilità, ma grandi dimensioni sufficienti per illustrare le caratteristiche delle prestazioni di SQL Server. Vantaggi significativi per gli indici columnstore, ad esempio, si verificano solo quando si utilizza con un numero elevato di righe. 

La procedura `Application.Configuration_PopulateLargeSaleTable` consente di aumentare notevolmente il numero di righe di `Fact.Sale` tabella. Si noti che le righe vengono inserite nell'anno di calendario 2012 per evitare in conflitto con i dati esistenti di World Wide Importers iniziando in corrispondenza di 1 ° gennaio 2013.

### <a name="procedure-details"></a>Dettagli delle procedure

#### <a name="name"></a>Nome: 

    Application.Configuration_PopulateLargeSaleTable

#### <a name="parameters"></a>Parametri:

  `@EstimatedRowsFor2012` **bigint** (valore predefinito è 12000000)

#### <a name="result"></a>Risultato:

Circa il numero richiesto di righe viene inserito le `Fact.Sale` tabella nell'anno 2012. La procedura limita artificialmente il numero di righe per ogni giorno a 50000. Questa limitazione è stato possibile modificare, ma è presente per evitare overinflations accidentale della tabella.

Inoltre, la procedura viene applicata l'indicizzazione columnstore cluster, se non è già stato applicato.
