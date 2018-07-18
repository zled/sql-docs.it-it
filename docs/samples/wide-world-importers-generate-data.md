---
title: WideWorldImporters generare dati - database SQL di esempio | Documenti Microsoft
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6ace1f771ef3a77a6f7db0072442affe181d7872
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2018
---
# <a name="wideworldimporters-data-generation"></a>Generazione di dati WideWorldImporters
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Le versioni rilasciate dei database WideWorldImporters e WideWorldImportersDW sono dati da 1 gennaio 2013, fino al giorno in cui sono stati generati i database.

Quando si usano questi database di esempio, è possibile includere più recente dei dati di esempio.

## <a name="data-generation-in-wideworldimporters"></a>Generazione di dati in WideWorldImporters

Per generare dati di esempio fino alla data corrente:

1. Se non è ancora stato fatto, installare una versione pulita del database WideWorldImporters. Per istruzioni sull'installazione, vedere [installazione e configurazione](wide-world-importers-oltp-install-configure.md).
2. Eseguire l'istruzione seguente nel database:

    ```
        EXECUTE DataLoadSimulation.PopulateDataToCurrentDate
            @AverageNumberOfCustomerOrdersPerDay = 60,
            @SaturdayPercentageOfNormalWorkDay = 50,
            @SundayPercentageOfNormalWorkDay = 0,
            @IsSilentMode = 1,
            @AreDatesPrinted = 1;
    ```

    Questa istruzione aggiunge vendita di esempio e i dati di acquisto per il database, fino alla data corrente. Visualizza lo stato di avanzamento della generazione di dati per giorno. Generazione dei dati può richiedere circa 10 minuti per ogni anno che necessita di dati. A causa di un fattore casuale la generazione di dati, esistono alcune differenze nei dati che viene generati da un'esecuzione.

    Per aumentare o diminuire la quantità di dati generati per gli ordini per ogni giorno, modificare il valore per il parametro `@AverageNumberOfCustomerOrdersPerDay`. Usare i parametri `@SaturdayPercentageOfNormalWorkDay` e `@SundayPercentageOfNormalWorkDay` per determinare il volume degli ordini per giorni del fine settimana.

## <a name="import-generated-data-in-wideworldimportersdw"></a>Dati di importazione generata in WideWorldImportersDW

Per importare dati di esempio fino alla data corrente nel database OLAP WideWorldImportersDW:

1. Eseguire la logica di generazione dati nel database OLTP WideWorldImporters utilizzando la procedura nella sezione precedente.
2. Se non è ancora stato fatto, installare una versione pulita del database WideWorldImportersDW. Per istruzioni sull'installazione, vedere [installazione e configurazione](wide-world-importers-oltp-install-configure.md).
3. Reinizializzare il database OLAP eseguendo l'istruzione seguente nel database:

    ```sql
    EXECUTE [Application].Configuration_ReseedETL
    ```

4. Eseguire la *ETL.ispac giornaliero* pacchetto SQL Server Integration Services per l'importazione dei dati del database OLAP. Per informazioni su come eseguire il processo ETL, vedere [flusso di lavoro WideWorldImporters ETL](wide-world-importers-perform-etl.md).

## <a name="generate-data-in-wideworldimportersdw-for-performance-testing"></a>Generare i dati nei WideWorldImportersDW per il test delle prestazioni

WideWorldImportersDW arbitrariamente può aumentare la dimensione dei dati per il test delle prestazioni. Ad esempio, è possibile aumentare le dimensioni dei dati da utilizzare con indice columnstore cluster.

Una delle sfide consiste nel mantenere le dimensioni del download sufficientemente ridotto da scaricare con facilità, ma grandi dimensioni sufficienti per illustrare le caratteristiche delle prestazioni di SQL Server. Ad esempio, si ottengono vantaggi significativi per gli indici columnstore solo quando si lavora con un numero elevato di righe. 

È possibile usare il `Application.Configuration_PopulateLargeSaleTable` procedura per aumentare il numero di righe il `Fact.Sale` tabella. Le righe vengono inserite nell'anno di calendario 2012 per evitare in conflitto con i dati del World Wide Importers esistenti che inizia il 1 gennaio 2013.

### <a name="procedure-details"></a>Dettagli di procedure

#### <a name="name"></a>Nome

    Application.Configuration_PopulateLargeSaleTable

#### <a name="parameters"></a>Parametri

  `@EstimatedRowsFor2012` **bigint** (valore predefinito è 12000000)

#### <a name="result"></a>Risultato

Circa il numero richiesto di righe viene inserito le `Fact.Sale` tabella nell'anno 2012. La procedura limita artificialmente il numero di righe a 50.000 al giorno. È possibile modificare questo limite, ma la limitazione consente di evitare overinflations accidentale della tabella.

La procedura si applica anche se non è già stata applicata l'indicizzazione di columnstore cluster.
