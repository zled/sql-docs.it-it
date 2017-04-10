---
title: "Passaggio 6: Rendere operativo il modello (Esercitazione di analisi avanzata nel database) | Microsoft Docs"
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
ms.assetid: 52b05828-11f5-4ce3-9010-59c213a674d1
caps.latest.revision: 11
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 11
---
# Passaggio 6: Rendere operativo il modello (Esercitazione di analisi avanzata nel database)
In questo passaggio si apprenderà a *rendere operativo* il modello mediante una stored procedure. La stored procedure può essere chiamata direttamente da altre applicazioni, per l'esecuzione di stime relative a nuove osservazioni.  
  
In questo passaggio si apprenderanno due metodi per chiamare un modello R da una stored procedure:  
  
-   **Modalità di valutazione batch**: usare una query SELECT per rendere disponibili più righe di dati. La stored procedure restituisce una tabella di osservazioni corrispondenti ai casi di input.  
  
-   **Modalità di valutazione singola**: passare come input un set di valori di parametro singoli.  La stored procedure restituisce una singola riga o un singolo valore.  
  
In primo luogo si prenderà in analisi il funzionamento generale della valutazione.  
  
## Valutazione di base  
La stored procedure _PredictTip_ illustra la sintassi di base per il wrapping di una chiamata di stima in una stored procedure.  
  
```  
CREATE PROCEDURE [dbo].[PredictTip] @inquery nvarchar(max)  
AS  
BEGIN  
  
  DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model  
  FROM nyc_taxi_models);  
  EXEC sp_execute_external_script @language = N'R',  
                                  @script = N'  
mod <- unserialize(as.raw(model));  
print(summary(mod))  
OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL,   
          predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);  
str(OutputDataSet)  
print(OutputDataSet)  
',  
                                  @input_data_1 = @inquery,  
                                  @params = N'@model varbinary(max)',  
                                  @model = @lmodel2  
  WITH RESULT SETS ((Score float));  
  
END  
  
GO  
  
```  
  
-   L'istruzione SELECT recupera il modello serializzato dal database e lo archivia nella variabile R `mod` per l'ulteriore elaborazione con R.  
  
-   I nuovi casi valutati vengono ottenuti dalla query [!INCLUDE[tsql](../../includes/tsql-md.md)] specificata in `@inquery`, il primo parametro della stored procedure. Man mano che vengono letti i dati della query, le righe vengono salvate nel frame di dati predefinito `InputDataSet`. Tale frame di dati viene passato alla funzione `rxPredict` di R, che genera le valutazioni.  
  
    `OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL,            predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);`  
  
    Poiché un data.frame può contenere una riga singola, è possibile usare lo stesso codice per la valutazione batch e la valutazione singola.  
  
-   Il valore restituito dalla funzione `rxPredict` è un **float** che rappresenta la probabilità che venga lasciata una mancia (di qualsiasi importo).  
  
## Valutazione batch mediante una query SELECT  
Ora si procede ad analizzare il funzionamento della valutazione batch.  
  
1.  Per iniziare si ottiene un set di dati di input più piccolo sul quale lavorare.  
  
    ```  
    select top 10 a.passenger_count as passenger_count,   
        a.trip_time_in_secs as trip_time_in_secs,  
        a.trip_distance as trip_distance,  
        a.dropoff_datetime as dropoff_datetime,    
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude,dropoff_longitude) as direct_distance   
    from  
    (  
        select medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance,    
            dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude  
        from nyctaxi_sample  
    )a  
    left outer join  
    (  
    select medallion, hack_license, pickup_datetime  
    from nyctaxi_sample  
    tablesample (70 percent) repeatable (98052)  
    )b  
    on a.medallion=b.medallion and a.hack_license=b.hack_license and a.pickup_datetime=b.pickup_datetime  
    where b.medallion is null  
    ```  
  
    Questa query crea un elenco "top 10" delle corse, con il numero di passeggeri e altre funzionalità necessarie per effettuare una stima.  
  
 **Risultati**  
  
*passenger_count   trip_time_in_secs    trip_distance  dropoff_datetime   direct_distance*  
*1  283 0.7 2013-03-27 14:54:50.000   0.5427964547*  
*1  289 0.7 2013-02-24 12:55:29.000   0.3797099614*  
*1  214 0.7 2013-06-26 13:28:10.000   0.6970098661*  
*1  276 0.7 2013-06-27 06:53:04.000   0.4478814362*  
*1  282 0.7 2013-02-21 07:59:54.000   0.5340645749*  
*1  260 0.7 2013-03-27 15:40:49.000   0.5513900727*  
*1  230 0.7 2013-02-05 09:47:59.000   0.5161578519*  
*1  250 0.7 2013-05-08 14:35:51.000   0.5626440915*  
*1  280 0.7 2013-05-11 12:22:01.000   0.5598517959*  
*1  308 0.7 2013-04-10 08:06:00.000   0.4478814362*  
  
La query verrà usata come input per la stored procedure _PredictTipBatchMode_, inclusa nel download.  
  
2.  In primo luogo è opportuno esaminare il codice della stored procedure _PredictTipBatchMode_ in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
    ```  
    /****** Object:  StoredProcedure [dbo].[PredictTipBatchMode]  ******/  
    SET ANSI_NULLS ON  
    GO  
    SET QUOTED_IDENTIFIER ON  
    GO  
  
    CREATE PROCEDURE [dbo].[PredictTipBatchMode] @inquery nvarchar(max)  
    AS  
    BEGIN  
  
      DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model  
      FROM nyc_taxi_models);  
      EXEC sp_execute_external_script @language = N'R',  
                                      @script = N'  
    mod <- unserialize(as.raw(model));  
    print(summary(mod))  
    OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL,   
              predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);  
    str(OutputDataSet)  
    print(OutputDataSet)  
    ',  
                                      @input_data_1 = @inquery,  
                                      @params = N'@model varbinary(max)',  
                                      @model = @lmodel2  
      WITH RESULT SETS ((Score float));  
  
    END  
    ```  
  
3.  Per creare stime sarà necessario specificare il testo della query in una variabile e passarla come parametro alla stored procedure, usando un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] simile alla seguente.  
  
    ```  
    -- Specify input query  
  
    DECLARE @query_string nvarchar(max)  
    SET @query_string='  
    select top 10 a.passenger_count as passenger_count,   
        a.trip_time_in_secs as trip_time_in_secs,  
        a.trip_distance as trip_distance,  
        a.dropoff_datetime as dropoff_datetime,    
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude,dropoff_longitude) as direct_distance   
    from  
        select medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance,    
            dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude  
        from nyctaxi_sample  
    )a  
    left outer join  
    (  
    select medallion, hack_license, pickup_datetime  
    from nyctaxi_sample  
    tablesample (70 percent) repeatable (98052)  
    )b  
    on a.medallion=b.medallion and a.hack_license=b.hack_license and a.pickup_datetime=b.pickup_datetime  
    where b.medallion is null'  
  
    -- Call stored procedure for scoring  
    EXEC [dbo].[PredictTip] @inquery = @query_string;  
  
    ```  
  
4.  La stored procedure restituirà una serie di valori che rappresentano la stima per ognuna delle corse "top 10". Se si osservano i valori di input, tutte le corse "top 10" sono caratterizzate da un singolo passeggero e una distanza relativamente breve. In base ai dati, è poco probabile che il conducente riceva una mancia per una corsa di questo tipo.  
  
    Invece di restituire solo i risultati di tipo mancia sì/mancia no sarebbe possibile restituire anche il punteggio di probabilità per la stima, quindi applicare una clausola WHERE ai valori della colonna _Score_ per classificare il punteggio come "mancia probabile" o "mancia poco probabile" usando un valore di soglia, ad esempio 0.5 o 0.7. Questo passaggio non è incluso nella stored procedure, ma la sua implementazione non sarebbe difficile.  
  
## Valutare singole righe  
A volte risulta utile passare valori singoli da un'applicazione e ottenere un risultato singolo basato su tali valori. Ad esempio è possibile impostare un foglio di lavoro di Excel, un'applicazione web o un report di Reporting Services in modo che chiami la stored procedure e renda disponibili input digitati o selezionati dagli utenti.  
  
In questa sezione si apprenderà come creare stime singole usando una stored procedure.  
  
1.  Esaminare in dettaglio il codice della stored procedure _PredictTipSingleMode_ inclusa nel download.  
  
    ```  
    CREATE PROCEDURE [dbo].[PredictTipSingleMode] @passenger_count int = 0,  
    @trip_distance float = 0,  
    @trip_time_in_secs int = 0,  
    @pickup_latitude float = 0,  
    @pickup_longitude float = 0,  
    @dropoff_latitude float = 0,  
    @dropoff_longitude float = 0  
    AS  
    BEGIN  
      DECLARE @inquery nvarchar(max) = N'  
      SELECT * FROM [dbo].[fnEngineerFeatures](@passenger_count,  
    @trip_distance,  
    @trip_time_in_secs,  
    @pickup_latitude,  
    @pickup_longitude,  
    @dropoff_latitude,  
    @dropoff_longitude)  
        '  
      DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model  
      FROM nyc_taxi_models);  
      EXEC sp_execute_external_script @language = N'R',  
                                      @script = N'  
    mod <- unserialize(as.raw(model));  
    print(summary(mod))  
    OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL,   
              predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);  
    str(OutputDataSet)  
    print(OutputDataSet)  
    ',  
    @input_data_1 = @inquery,  
    @params = N'@model varbinary(max),@passenger_count int,@trip_distance float,@trip_time_in_secs int ,  
    @pickup_latitude float ,@pickup_longitude float ,@dropoff_latitude float ,@dropoff_longitude float',  
    @model = @lmodel2,  
    @passenger_count =@passenger_count ,  
    @trip_distance=@trip_distance,  
    @trip_time_in_secs=@trip_time_in_secs,    
    @pickup_latitude=@pickup_latitude,  
    @pickup_longitude=@pickup_longitude,  
    @dropoff_latitude=@dropoff_latitude,  
    @dropoff_longitude=@dropoff_longitude  
      WITH RESULT SETS ((Score float));  
  
    END  
  
    ```  
  
    -   Questa stored procedure accetta come input più valori singoli, quali il numero di passeggeri, la distanza della corsa e così via.  
  
        Se si chiama la stored procedure da un'applicazione esterna, assicurarsi che i dati soddisfino i requisiti del modello R. Ciò può includere la verifica che i dati di input siano sottoponibili a cast o convertibili in un tipo di dati di R o la convalida del tipo di dati e della lunghezza dei dati. Per altre informazioni, vedere [Uso dei tipi di dati di R](https://msdn.microsoft.com/library/mt590948.aspx).  
  
    -   La stored procedure crea un punteggio in base al modello R archiviato.  
  
2.  Provare la stored procedure inserendo manualmente i valori.  
  
    Aprire una nuova finestra **Query**, quindi chiamare la stored procedure digitando i parametri per ogni colonna di funzionalità.  
  
    ```  
  
    EXEC [dbo].[PredictTipSingleMode] 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303  
  
    ```  
  
    I valori corrispondono a queste colonne di funzionalità, nell'ordine:  
  
    -   *trip_time_in_secs*  
    -   *pickup_latitude*  
    -   *pickup_longitude*  
    -   *dropoff_latitude*  
    -   *dropoff_longitude*  
  
3.  I risultati indicano che la probabilità di ricevere una mancia è molto bassa in queste corse "top 10", che sono tutte corse con un solo passeggero e su una distanza relativamente breve.  
  
## Conclusioni  
In questa esercitazione si è appreso come usare il codice R incorporato nelle stored procedure. L'integrazione con [!INCLUDE[tsql](../../includes/tsql-md.md)] semplifica notevolmente la distribuzione di modelli R per le stime e l'inclusione delle ripetizioni del training dei modelli nel flusso di lavoro dei dati enterprise.  
  
  
## Passaggio precedente  
[Passaggio 4: Creare funzionalità di dati mediante T-SQL](../../advanced-analytics/r-services/step-4-create-data-features-using-t-sql-in-database-advanced-analytics-tutorial.md)  
  
## Vedere anche  
[Analisi avanzata nel database per sviluppatori SQL &#40;Esercitazione&#41;](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)  
[Esercitazioni di SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
  
  
  
