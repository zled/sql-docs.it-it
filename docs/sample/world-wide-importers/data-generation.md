---
title: La generazione dei dati | Documenti Microsoft
ms.custom: 
ms.date: 01/30/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.prod: sql-non-specified
ms.technology:
- " database-engine "
ms.topic: article
ms.assetid: f387273b-8b5f-4687-b033-09499ea2d68f
caps.latest.revision: 4
author: BarbKess
ms.author: barbkess
manager: jhubbard
robots: noindex,nofollow
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: c17ad40220d46ab6e19054818ce2abfdce7251f4
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="wideworldimporters-data-generation"></a>Generazione di dati WideWorldImporters
Le versioni rilasciate dei database WideWorldImporters e WideWorldImportersDW contiene dati iniziale 2013 1 ° gennaio, fino a di questi database sono stati generati al giorno.

Se i database di esempio vengono utilizzati in un secondo momento, per scopi dimostrativi o illustrazione, potrebbe essere utile includere dati di esempio più recenti nel database.

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

Questa istruzione aggiunge vendita di esempio e i dati di acquisto nel database, fino alla data corrente. Viene restituito lo stato di avanzamento dei dati generazione giorno per giorno. Richiederà circa 10 minuti per ogni anno che necessita di dati. Si noti che esistono alcune differenze nei dati generati da un'esecuzione, poiché è un fattore casuale la generazione di dati.

Per aumentare o diminuire la quantità di dati generati, in termini di ordini per ogni giorno, modificare il valore per il parametro `@AverageNumberOfCustomerOrdersPerDay`. I parametri `@SaturdayPercentageOfNormalWorkDay` e `@SundayPercentageOfNormalWorkDay` vengono utilizzati per determinare il volume degli ordini per giorni del fine settimana.

## <a name="importing-generated-data-in-wideworldimportersdw"></a>Importazione di dati generati in WideWorldImportersDW

Per importare i dati di esempio fino alla data corrente nel database OLAP WideWorldImportersDW, seguire questi passaggi:

1. Eseguire la logica di generazione dati nel database OLTP WideWorldImporters, utilizzando i passaggi precedenti.
2. Se non è ancora stato fatto, installare una versione pulita del database WideWorldImportersDW. Per istruzioni sull'installazione, **WideWorldImporters installazione e configurazione**.
3. Reinizializzare il database OLAP eseguendo l'istruzione seguente nel database:

```
    EXECUTE [Application].Configuration_ReseedETL
```

4. Eseguire il pacchetto SSIS **ETL.ispac giornaliero** per importare i dati nel database OLAP. Per istruzioni su come eseguire il processo ETL, vedere **flusso di lavoro ETL WideWorldImporters**.

## <a name="generating-data-in-wideworldimportersdw-for-performance-testing"></a>La generazione di dati in WideWorldImportersDW per il test delle prestazioni

WideWorldImportersDW ha la possibilità di aumentare la dimensione dei dati, allo scopo di test delle prestazioni, ad esempio con columnstore cluster arbitrariamente.

Uno dei problemi per la spedizione di un esempio di come World Wide Importers consiste nel mantenere le dimensioni del download sufficientemente piccolo per essere sufficientemente grande da essere in grado di illustrare le caratteristiche delle prestazioni di SQL Server ma distribuibile. Un'area in cui questo è un problema specifico è quando si lavora con gli indici columnstore. Vantaggi significativi provengono solo quando si lavora con un numero maggiore di righe. 

La procedura `Application.Configuration_PopulateLargeSaleTable` consente di aumentare notevolmente il numero di righe di `Fact.Sale` tabella. Si noti che le righe vengono inserite nell'anno di calendario 2012 per evitare la collisione con dati esistenti di World Wide Importers a partire dal 1 ° gennaio 2013.

### <a name="procedure-details"></a>Dettagli delle procedure

#### <a name="name"></a>Nome: 

    Application.Configuration_PopulateLargeSaleTable

#### <a name="parameters"></a>Parametri:

  `@EstimatedRowsFor2012`**bigint** (il valore predefinito è 12000000)

#### <a name="result"></a>Risultato:

Circa il numero richiesto di righe viene inserito le `Fact.Sale` tabella nell'anno 2012. La procedura limita artificialmente il numero di righe per ogni giorno a 50000. È possibile modificare, ma è presente per evitare overinflations accidentale della tabella.

Inoltre, la procedura viene applicata l'indicizzazione columnstore cluster, se non è già stato applicato.

