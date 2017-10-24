---
title: 'Lezione 5: Eseguire il training e salvare un modello utilizzando T-SQL | Documenti Microsoft'
ms.custom: 
ms.date: 07/26/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
dev_langs:
- R
- TSQL
ms.assetid: 3282e8ed-b515-4ed5-8543-fcef68629a92
caps.latest.revision: 10
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 785e4dc3db234447c806ddc349682d08a8447923
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-5-train-and-save-a-model-using-t-sql"></a>Lezione 5: Eseguire il training e salvare un modello utilizzando T-SQL

In questo articolo fa parte di un'esercitazione per gli sviluppatori SQL su come usare il linguaggio R in SQL Server.

In questa lezione si apprenderà come eseguire il training di un modello di machine learning usando R. Sarà il training del modello mediante le funzionalità di dati appena creato e quindi salvare il modello con Training in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella. In questo caso, i pacchetti R già installati con [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], in modo che tutti gli elementi possono essere eseguiti da SQL.

## <a name="create-the-stored-procedure"></a>Creare la stored procedure

Quando si chiama R da T-SQL, utilizzare la stored procedure di sistema [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Tuttavia, per i processi che ripetono spesso, ad esempio un modello, ripetizione di training è più semplice incapsulare la chiamata a `sp_execute_exernal_script` in un'altra stored procedure.

1.  Creare innanzitutto una stored procedure che contiene il codice R per compilare il modello di stima suggerimento. In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], aprire una nuova **Query** finestra ed eseguire l'istruzione seguente per creare la stored procedure _TrainTipPredictionModel_. Questa stored procedure definisce i dati di input e usa un pacchetto R per creare un modello di regressione logistica.

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

    - Tuttavia, per garantire che alcuni dati rimasti per testare il modello, il 70% dei dati vengono selezionate casualmente dalla tabella di dati taxi.
    
    - La query SELECT usa la funzione scalare personalizzata _fnCalculateDistance_ per calcolare la distanza diretta tra la posizione di salita e discesa dei passeggeri.  I risultati della query vengono archiviati nella variabile di input R predefinita `InputDataset`.
  
    - Le chiamate di script R di `rxLogit` funzione, ovvero una delle funzioni R avanzate incluso con [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], per creare il modello di regressione logistica.
  
        La variabile binaria _tipped_ viene usata come *etichetta* o come colonna dei risultati. Il modello si adatta usando le colonne delle funzionalità seguenti:  _passenger_count_, _trip_distance_, _trip_time_in_secs_e _direct_distance_.
  
    -   Il modello con training salvato nella variabile R `logitObj`viene serializzato e inserito in un frame di dati per l'output in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'output viene inserito nella tabella di database _nyc_taxi_models_, in modo che sia possibile usarlo per stime future.
  
2.  Eseguire l'istruzione per creare la stored procedure, se non esiste già.

## <a name="generate-the-r-model-using-the-stored-procedure"></a>Generare il modello R usando la stored procedure

Poiché la stored procedure include già una definizione dei dati di input, non è necessario fornire una query di input.

1. Per generare il modello R, chiamare la stored procedure senza altri parametri:

    ```SQL
    EXEC TrainTipPredictionModel
    ```

2. Espressioni di controllo di **messaggi** finestra di [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] per i messaggi che potrebbero essere reindirizzati al R **stdout** flusso, ad esempio questo messaggio: 

    "Messaggi STDOUT dallo script esterno: righe lette: 1193025, totale righe elaborate: 1193025, totale tempo di blocco: 0.093 secondi"

    È possibile visualizzare messaggi specifici a singola funzione, `rxLogit`, visualizzare le variabili e metriche generato come parte della creazione del modello.

3.  Quando l'istruzione è stata completata, aprire la tabella *nyc_taxi_models*. L'elaborazione dei dati e l'adattamento del modello potrebbe richiedere qualche istante.

    È possibile notare che è stata aggiunta una riga nuova contenente il modello serializzato nella colonna _model_.

    ```
    model
    ------
    0x580A00000002000302020....
    ```

Nel passaggio successivo il modello con training sarà usato per creare stime.

## <a name="next-lesson"></a>Lezione successiva

[Lezione 6: Rendere operativo il modello](../tutorials/sqldev-operationalize-the-model.md)

## <a name="previous-lesson"></a>Lezione precedente

[Lezione 4: Creare funzionalità di dati con T-SQL](..//tutorials/sqldev-create-data-features-using-t-sql.md)


