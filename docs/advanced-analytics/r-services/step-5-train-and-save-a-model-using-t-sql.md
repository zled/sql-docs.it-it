---
title: "Passaggio 5: Training e salvataggio di un modello tramite T-SQL (Esercitazione di analisi avanzata dei dati nel database) | Microsoft Docs"
ms.custom: ""
ms.date: "04/19/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
  - "TSQL"
ms.assetid: 3282e8ed-b515-4ed5-8543-fcef68629a92
caps.latest.revision: 10
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 10
---
# Passaggio 5: Training e salvataggio di un modello tramite T-SQL (Esercitazione di analisi avanzata dei dati nel database)
Questo passaggio illustra come eseguire il training di un modello di apprendimento automatico tramite R. I pacchetti R sono già installati insieme a [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. È pertanto possibile chiamare l'algoritmo da una stored procedure. Il training del modello sarà eseguito usando le funzionalità di dati appena create. Il modello sarà poi salvato in una tabella di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## Creazione di un modello R tramite stored procedure  
Il runtime R installato con [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] viene sempre chiamato tramite la stored procedure di sistema, vale a dire [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Se fosse tuttavia necessario rieseguire il training di un modello, è preferibile incapsulare la chiamata a sp_execute_exernal_script in un'altra stored procedure.  
  
In questa sezione si creerà una stored procedure che è possibile usare per compilare un modello con i dati appena preparati. Questa stored procedure definisce i dati di input e usa un pacchetto R per creare un modello di regressione logistica.  
  
#### Per creare la stored procedure  
  
1.  In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] aprire una nuova finestra Query ed eseguire l'istruzione seguente per creare la stored procedure _TrainTipPredictionModel_.  
  
    Si noti che, poiché la stored procedure include già una definizione dei dati di input, non è necessario specificare una query di input.  
  
    ```  
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
  
    Questa stored procedure esegue tali attività perché previsto dal training del modello:  
  
    -   Dalla tabella dati dei taxi viene selezionato casualmente il 70% dei dati. Alcuni dati rimarranno così disponibili per testare il modello.  
  
    -   La query SELECT usa la funzione scalare personalizzata _fnCalculateDistance_ per calcolare la distanza diretta tra la posizione di salita e discesa dei passeggeri.  I risultati della query vengono archiviati nella variabile di input R predefinita `InputDataset`.  
  
    -   Lo script R chiama la funzione `rxLogit`, vale a dire una delle funzioni R avanzate incluse in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], per creare il modello di regressione logistica.  
  
        La variabile binaria _tipped_ viene usata come *etichetta* o come colonna dei risultati. Il modello si adatta usando le colonne delle funzionalità seguenti: _passenger_count_, _trip_distance_, _trip_time_in_secs_ e _direct_distance_.  
  
    -   Il modello con training salvato nella variabile R `logitObj` viene serializzato e inserito in un frame di dati per l'output in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'output viene inserito nella tabella di database _nyc_taxi_models_, in modo che sia possibile usarlo per stime future.  
  
2.  Eseguire l'istruzione per creare la stored procedure.  
  
#### Per creare il modello R tramite la stored procedure  
  
1.  Eseguire l'istruzione seguente in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
    ```  
    EXEC TrainTipPredictionModel  
    ```  
  
    L'elaborazione dei dati e l'adattamento del modello potrebbero richiedere un po' di tempo. I messaggi che sarebbero inoltrati al flusso **stdout** di R vengono visualizzati nella finestra **Messaggi** di [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Esempio:  
  
  
*STDOUT message(s) from external script: Rows Read: 1193025, Total Rows Processed: 1193025, Total Chunk Time: 0.093 seconds*       
  
I blocchi successivi dei dati vengono letti ed elaborati. È anche possibile visualizzare messaggi specifici per la singola funzione `rxLogit`, che indica la variabile e le metriche dei test.  
  
2.  Aprire la tabella *nyc_taxi_models*. È possibile notare che è stata aggiunta una riga nuova contenente il modello serializzato nella colonna _model_.  
  
  
  
*model*  
*0x580A00000002000302020....*  
  
Nel passaggio successivo il modello con training sarà usato per creare stime.  
  
## Passaggio successivo  
[Passaggio 6: Rendere operativo il modello](../../advanced-analytics/r-services/step-6-operationalize-the-model-in-database-advanced-analytics-tutorial.md)  
  
## Passaggio precedente  
[Passaggio 4: Creare funzionalità di dati tramite T-SQL](../../advanced-analytics/r-services/step-4-create-data-features-using-t-sql-in-database-advanced-analytics-tutorial.md)  
  
## Vedere anche  
[Analisi avanzata nel database per sviluppatori SQL &#40;Esercitazione&#41;](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)  
[Esercitazioni di SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
  
  
  
