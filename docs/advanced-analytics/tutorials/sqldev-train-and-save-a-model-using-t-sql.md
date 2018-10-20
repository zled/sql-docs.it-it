---
title: Lezione 3 training e salvataggio di un modello usando R e T-SQL (SQL Server Machine Learning Services) | Microsoft Docs
description: Esercitazione che illustra come incorporare R in SQL Server stored procedure e funzioni T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/07/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 73e1b2ef70821af2247de000eba45a495075e614
ms.sourcegitcommit: 3cd6068f3baf434a4a8074ba67223899e77a690b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2018
ms.locfileid: "49463046"
---
# <a name="lesson-3-train-and-save-a-model-using-t-sql"></a>Lezione 3: Eseguire il training e salvataggio di un modello usando T-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo fa parte di un'esercitazione per sviluppatori SQL su come usare R in SQL Server.

In questa lezione si apprenderà come eseguire il training di un modello di machine learning tramite R. Si sarà il training del modello usando le funzionalità di dati creato nella lezione precedente e quindi salvare il modello con Training in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella. In questo caso, i pacchetti R sono già installati insieme [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], in modo che tutto ciò che può essere eseguita da SQL.

## <a name="create-the-stored-procedure"></a>Creare la stored procedure

Quando si chiama R da T-SQL, si utilizza la stored procedure di sistema [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Tuttavia, per i processi che si ripete spesso, ad esempio un modello di ripetizione del training è più semplice incapsulare la chiamata a `sp_execute_exernal_script` in un'altra stored procedure.

1.  In primo luogo, creare una stored procedure che contiene il codice R per compilare il modello di stima di Mancia. Nelle [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], aprire una nuova **Query** finestra ed eseguire l'istruzione seguente per creare la stored procedure _TrainTipPredictionModel_. Questa stored procedure definisce i dati di input e usa un pacchetto R per creare un modello di regressione logistica.

    ```SQL
    CREATE PROCEDURE [dbo].[TrainTipPredictionModel]
    
    AS
    BEGIN
      DECLARE @inquery nvarchar(max) = N'
        select tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance,
        pickup_datetime, dropoff_datetime,
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
        from nyctaxi_sample
        tablesample (70 percent) repeatable (98052)
    '
      -- Insert the trained model into a database table
      INSERT INTO nyc_taxi_models
      EXEC sp_execute_external_script @language = N'R',
                                      @script = N'
    
    ## Create model
    logitObj <- rxLogit(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = InputDataSet)
    summary(logitObj)
    
    ## Serialize model and put it in data frame
    trained_model <- data.frame(model=as.raw(serialize(logitObj, NULL)));
    ',
      @input_data_1 = @inquery,
      @output_data_1_name = N'trained_model'
      ;
    
    END
    GO
    ```

    - Tuttavia, per garantire che alcuni dati rimarranno per testare il modello, il 70% dei dati vengono selezionate casualmente tra la tabella di dati dei taxi.
    
    - La query SELECT usa la funzione scalare personalizzata _fnCalculateDistance_ per calcolare la distanza diretta tra la posizione di salita e discesa dei passeggeri.  I risultati della query vengono archiviati nella variabile di input R predefinita `InputDataset`.
  
    - Lo script R chiama il `rxLogit` funzione, vale a dire una delle funzioni R avanzate incluse con [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], per creare il modello di regressione logistica.
  
        La variabile binaria _tipped_ viene usata come *etichetta* o come colonna dei risultati. Il modello si adatta usando le colonne delle funzionalità seguenti:  _passenger_count_, _trip_distance_, _trip_time_in_secs_e _direct_distance_.
  
    -   Il modello con training salvato nella variabile R `logitObj`viene serializzato e inserito in un frame di dati per l'output in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'output viene inserito nella tabella di database _nyc_taxi_models_, in modo che sia possibile usarlo per stime future.
  
2.  Eseguire l'istruzione per creare la stored procedure, se non esiste già.

## <a name="generate-the-r-model-using-the-stored-procedure"></a>Generare il modello R tramite stored procedure

Poiché la stored procedure include già una definizione dei dati di input, non è necessario fornire una query di input.

1. Per generare il modello R, chiamare la stored procedure senza altri parametri:

    ```SQL
    EXEC TrainTipPredictionModel
    ```

2. Guarda il **messaggi** finestra di [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] per i messaggi che sarebbero inoltrati di R **stdout** flusso, ad esempio questo messaggio: 

    "Messaggi STDOUT dallo script esterno: righe lette: 1193025, totale righe elaborate: 1193025, totale tempo blocco: 0.093 secondi"

    È anche possibile visualizzare messaggi specifici per la singola funzione, `rxLogit`, visualizzare le variabili e le metriche generate come parte della creazione del modello di test.

3.  Quando l'istruzione è stata completata, aprire la tabella *nyc_taxi_models*. L'elaborazione dei dati e l'adattamento del modello potrebbe richiedere qualche minuto.

    È possibile notare che è stata aggiunta una riga nuova contenente il modello serializzato nella colonna _model_.

    ```
    model
    ------
    0x580A00000002000302020....
    ```

Nel passaggio successivo il modello con training sarà usato per creare stime.

## <a name="next-lesson"></a>Lezione successiva

[Lezione 4: Rendere operativo il modello](../tutorials/sqldev-operationalize-the-model.md)

## <a name="previous-lesson"></a>Lezione precedente

[Lezione 2: Creare funzionalità di dati usando funzioni R e T-SQL](..//tutorials/sqldev-create-data-features-using-t-sql.md)

