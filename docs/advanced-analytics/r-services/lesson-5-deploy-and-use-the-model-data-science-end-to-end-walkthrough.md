---
title: "Lezione 5: Distribuire e usare il modello (Procedura dettagliata end-to-end per l&#39;analisi scientifica dei dati) | Microsoft Docs"
ms.custom: ""
ms.date: "11/22/2016"
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
ms.assetid: f28a7aac-6d08-4781-ad28-b48d18cc16a0
caps.latest.revision: 17
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 17
---
# Lezione 5: Distribuire e usare il modello (Procedura dettagliata end-to-end per l&#39;analisi scientifica dei dati)
In questa lezione verranno usati i modelli R in un ambiente di produzione racchiudendo il modello persistente in una stored procedure. Sarà quindi possibile richiamare la stored procedure da R o da qualsiasi linguaggio di programmazione di applicazioni che supporti [!INCLUDE[tsql](../../includes/tsql-md.md)] (ad esempio C#, Java, Python, ecc.) per usare il modello per creare stime sulle nuove osservazioni.  
  
È possibile richiamare un modello per la classificazione in due modi:  
  
-   La**modalità di assegnazione del punteggio batch** consente di creare più stime in base all'input di una query SELECT.  
  
-   La**modalità di assegnazione dei punteggi singoli** consente di creare una stima alla volta passando un set di valori di funzionalità per un singolo caso alla stored procedure, che restituisce una sola stima o un altro valore come risultato.  
  
Verrà illustrato come creare le stime usando entrambi i metodi di punteggio singolo e batch.  
  
## <a name="batch-scoring"></a>Assegnazione del punteggio batch  
Per praticità, è possibile usare una stored procedure che è stata creata durante l'esecuzione dello script di PowerShell nella Lezione 1. Questa stored procedure esegue le operazioni seguenti:  
  
-   Ottiene un set di dati di input come query SQL    
-   Chiama il modello di regressione logistica di cui è stato eseguito il training e che è stato salvato nella lezione precedente    
-   Stima la probabilità del tassista di ricevere una mancia  
  
### <a name="use-the-stored-procedure-predicttipbatchmode"></a>Usare la stored procedure PredictTipBatchMode

1. Esaminare lo script che definisce la stored procedure *PredictTipBatchMode*. Illustra diversi aspetti della modalità con la quale un modello può diventare operativo usando [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].  
  
    ```tsql  
    CREATE PROCEDURE [dbo].[PredictTipBatchMode]   
    @input nvarchar(max)  
    AS  
    BEGIN  
  
      DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model  FROM nyc_taxi_models);  
      EXEC sp_execute_external_script @language = N'R',  
         @script = N'  
           mod <- unserialize(as.raw(model));  
           print(summary(mod))  
           OutputDataSet<-rxPredict(modelObject = mod, 
               data = InputDataSet, 
               outData = NULL, 
               predVarNames = "Score", type = "response", 
               writeModelVars = FALSE, overwrite = TRUE);  
           str(OutputDataSet)  
           print(OutputDataSet)',  
      @input_data_1 = @input,  
      @params = N'@model varbinary(max)',  
      @model = @lmodel2  
      WITH RESULT SETS ((Score float));  
    END    
    ```  

    + Si noti l'istruzione SELECT che chiama il modello archiviato. È possibile archiviare qualsiasi modello di cui è stato eseguito il training in una tabella SQL usando una colonna di tipo **varbinary (max)**. In questo codice, il modello viene recuperato dalla tabella, archiviato nella variabile SQL _@lmodel2_ e passato come parametro *mod* alla stored procedure di sistema [sp_execute_external_script &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).
    + I dati di input usati per il punteggio vengono passati come stringa alla stored procedure.  
  
        Per definire i dati di input per questo particolare modello, creare una query che restituisce dati validi. I dati recuperati dal database vengono archiviati in un frame di dati denominato *InputDataSet*. Tutte le righe di questo frame di dati vengono usate per l'assegnazione dei punteggi batch.
        + *InputDataSet* è il nome predefinito per i dati di input della procedura [sp_execute_external_script &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Se necessario, è possibile definire un altro nome di variabile.
        + Per generare i punteggi, la stored procedure chiama la funzione *rxPredict* dalla libreria **RevoScaleR**.
    + Il valore restituito della stored procedure, *Score*, è una probabilità stimata che il tassista riceva una mancia.  
  
2.  Facoltativamente è possibile applicare facilmente un filtro ai valori restituiti per suddividere i valori restituiti in gruppi "con mancia" o "senza mancia".  Ad esempio, una probabilità minore dello 0,5 indica che probabilmente non verrà data alcuna mancia.  
  
3.  Chiamare la stored procedure in modalità batch:  
  
    ```R  
    input = "N' 
      SELECT TOP 10 
          a.passenger_count AS passenger_count,   
          a.trip_time_in_secs AS trip_time_in_secs,  
          a.trip_distance AS trip_distance,  
          a.dropoff_datetime AS dropoff_datetime,    
          dbo.fnCalculateDistance(
            pickup_latitude, 
            pickup_longitude, 
            dropoff_latitude,
            dropoff_longitude) AS direct_distance   
      FROM  
      
      (SELECT medallion, hack_license, pickup_datetime,   
      passenger_count,trip_time_in_secs,trip_distance,    
      dropoff_datetime, pickup_latitude, pickup_longitude,   
      dropoff_latitude, dropoff_longitude from nyctaxi_sample)a  
      
      LEFT OUTER JOIN  
 
      ( SELECT medallion, hack_license, pickup_datetime 
        FROM nyctaxi_sample  tablesample (1 percent) repeatable (98052)  )b  

      ON a.medallion=b.medallion 
        AND a.hack_license=b.hack_license 
        AND a.pickup_datetime=b.pickup_datetime  

      WHERE b.medallion is null  
    '"  
    q<-paste("EXEC PredictTipBatchMode @inquery = ", input, sep="")  
    sqlQuery (conn, q)  
  
    ```  
  
## <a name="single-row-scoring"></a>Assegnazione di un punteggio alle singole righe  

Anziché usare una query per passare i valori di input al modello R salvato, è possibile specificare le funzionalità come argomenti nella stored procedure.  

### <a name="use-the-stored-procedure-predicttipsinglemode"></a>Usare la stored procedure PredictTipSingleMode
1.  Esaminare il codice seguente relativo alla stored procedure *PredictTipSingleMode*, che dovrebbe essere già stata creata nel database.  
  
    ```tsql  
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
      DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model FROM nyc_taxi_models);  

      EXEC sp_execute_external_script @language = N'R',  @script = N'  
            mod <- unserialize(as.raw(model));  
            print(summary(mod))  
            OutputDataSet<-rxPredict(
                     modelObject = mod, 
                     data = InputDataSet, 
                     outData = NULL,   
                     predVarNames = "Score", 
                     type = "response", 
                     writeModelVars = FALSE, 
                     overwrite = TRUE);  
            str(OutputDataSet)  
            print(OutputDataSet)  
            ',  
      @input_data_1 = @inquery,  
      @params = N'@model varbinary(max),
                @passenger_count int,
                @trip_distance float,
                @trip_time_in_secs int ,  
                @pickup_latitude float ,
                @pickup_longitude float ,
                @dropoff_latitude float ,
                @dropoff_longitude float',  
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
  
    La stored procedure accetta i valori delle funzionalità come input, ad esempio il numero di passeggeri e la distanza della corsa, assegna un punteggio alle funzionalità usando il modello R archiviato e genera un punteggio.  
  
### <a name="call-the-stored-procedure-and-pass-parameters"></a>Chiamare la stored procedure e passare i parametri

1. In SQL Server Management Studio è possibile usare l'istruzione **EXEC** di [!INCLUDE[tsql](../../includes/tsql-md.md)] per chiamare la stored procedure e passarle gli input necessari. .  
    ```tsql  
    EXEC [dbo].[PredictTipSingleMode] 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303   
    ```  
  
    Vengono passati i valori rispettivamente per le variabili _passenger_count_, _trip_distance_, _trip_time_in_secs_, _pickup_latitude_, _pickup_longitude_, _dropoff_latitude_e _dropoff_longitude_.  
  
2.  Per eseguire questa stessa chiamata dal codice R, è sufficiente definire una variabile R contenente l'intera chiamata alla stored procedure. 
  
    ```R  
    q = "EXEC PredictTipSingleMode 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303 "  
    ```  
  
    Vengono passati i valori rispettivamente per le variabili _passenger_count_, _trip_distance_, _trip_time_in_secs_, _pickup_latitude_, _pickup_longitude_, _dropoff_latitude_e _dropoff_longitude_.  
  
### <a name="generate-scores"></a>Generare i punteggi

1. Chiamare la funzione *sqlQuery* del pacchetto **RODBC** e passare la stringa di connessione e la variabile di stringa contenente la chiamata alla stored procedure.  
  
    ```R  
    # predict with stored procedure in single mode  
    sqlQuery (conn, q)   
    ```  
  
    Per altre informazioni su **RODBC**, vedere [http://www.inside-r.org/packages/cran/RODBC/docs/sqlQuery](http://www.inside-r.org/packages/cran/RODBC/docs/sqlQuery).  
  
## <a name="conclusion"></a>Conclusioni  
Dopo aver appreso come usare i dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e aver salvato permanentemente i modelli R sottoposti a training in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], risulterà semplice creare alcuni modelli aggiuntivi basati sul set di dati. Ad esempio, è possibile provare a creare i modelli seguenti:  
  
-   Un modello di regressione che stima l'importo della mancia    
-   Un modello di classificazione multiclasse che stima l'importo piccolo, medio o grande della mancia.  

È inoltre consigliabile controllare alcuni di questi esempi e risorse aggiuntivi: 
+ [Scenari di analisi scientifica dei dati e modelli di soluzioni](../../advanced-analytics/r-services/data-science-scenarios-and-solution-templates.md)
+ [Analisi avanzata nel database](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)
+ [Microsoft R - Diving into Data Analysis](https://msdn.microsoft.com/microsoft-r/data-analysis-in-microsoft-r) (Microsoft R - Approfondimento dell'analisi dei dati)
+ [Risorse aggiuntive](https://msdn.microsoft.com/microsoft-r/microsoft-r-more-resources)
## <a name="previous-lesson"></a>Lezione precedente  
[Lezione 4: Creare e salvare il modello &#40;Procedura dettagliata end-to-end per l'analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/lesson-4-build-and-save-the-model-data-science-end-to-end-walkthrough.md)  
  
## <a name="see-also"></a>Vedere anche  
[Esercitazioni di SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
  
  
  
