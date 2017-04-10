---
title: "Lezione 4: Creare e salvare il modello (Procedura dettagliata end-to-end per l&#39;analisi scientifica dei dati) | Microsoft Docs"
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
ms.assetid: 69b374c1-2042-4861-8f8b-204a6297c0db
caps.latest.revision: 20
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 18
---
# Lezione 4: Creare e salvare il modello (Procedura dettagliata end-to-end per l&#39;analisi scientifica dei dati)
In questa lezione verrà illustrato come creare un modello di apprendimento automatico e salvare il modello in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="creating-a-classification-model"></a>Creazione di un modello di classificazione  
Il modello che verrà creato è un classificatore binario che prevede se un tassista riceverà una mancia in una particolare corsa. Si userà l'origine dati creata nella lezione precedente, `featureDataSource,` , per eseguire il training del classificatore delle mance tramite la regressione logistica.  
  
Queste sono le funzionalità che saranno usate nel modello:  
  
-   passenger_count  
  
-   trip_distance  
  
-   trip_time_in_secs  
  
-   direct_distance  

### <a name="create-the-model-using-rxlogit"></a>Creare il modello con rxLogit  
1.  Chiamare la funzione *rxLogit* inclusa nel pacchetto **RevoScaleR** per creare un modello di regressione logistica.  
  
    ```R  
    system.time(logitObj <- rxLogit(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = featureDataSource))    
    ```  
  
2.  Dopo aver creato il modello, è opportuno controllarlo tramite la funzione `summary` e visualizzare i coefficienti.  
  
    ```  
    summary(logitObj)  
    ```  

     *Risultati*

     *Logistic Regression Results for: tipped ~ passenger_count + trip_distance + trip_time_in_secs +*  
     *direct_distance*  
     *Data: featureDataSource (RxSqlServerData Data Source)*  
     *Dependent variable(s): tipped*  
     *Total independent variables: 5*   
     *Number of valid observations: 17068*  
     *Number of missing observations: 0*   
     *-2\*LogLikelihood: 23540.0602 (Residual deviance on 17063 degrees of freedom)*  
     *Coefficients:*  
     *Estimate Std. Error z value Pr(>|z|)*   
     *(Intercept)       -2.509e-03  3.223e-02  -0.078  0.93793*   
     *passenger_count   -5.753e-02  1.088e-02  -5.289 1.23e-07 \*\*\**  
     *trip_distance     -3.896e-02  1.466e-02  -2.658  0.00786 \*\**   
     *trip_time_in_secs  2.115e-04  4.336e-05   4.878 1.07e-06 \*\*\**  
     *direct_distance    6.156e-02  2.076e-02   2.966  0.00302 \*\**   
     *---*  
     *Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1*  
     *Condition number of final variance-covariance matrix: 48.3933*   
     *Number of iterations: 4*  
  
### <a name="use-the-logistic-regression-model-for-scoring"></a>Usare il modello di regressione logistica per assegnare i punteggi  
Dopo aver compilato il modello, è possibile usarlo per prevedere se il tassista riceverà una mancia in una specifica corsa.  
  
1.  In primo luogo, definire l'oggetto di dati da usare per archiviare i risultati di punteggio  
  
    ```R  
    scoredOutput <- RxSqlServerData(  
      connectionString = connStr,  
      table = "taxiScoreOutput"  )  
    ```  
    + Per semplificare questo esempio, l'input per il modello di regressione logistica è `featureDataSource` , usato per il training del modello.  Più generalmente è possibile usare nuovi dati per i punteggi oppure riservare alcuni dati per il test e non per il training.  
  
    + I risultati della previsione vengono salvati nella tabella _taxiscoreOutput_. Si noti che lo schema per questa tabella non è definito quando lo si crea tramite `rxSqlServerData`, ma viene ottenuto dall'oggetto *scoredOutput* restituito da `rxPredict`.  
  
    + Per creare la tabella che contiene i valori previsti, l'account di accesso SQL che esegue la funzione di dati `rxSqlServer` deve avere privilegi DDL nel database. Se l'account di accesso non può creare tabelle, l'istruzione avrà esito negativo.  
  
2.  Chiamare la funzione *rxPredict* per generare i risultati.  
  
    ```R  
    rxPredict(modelObject = logitObj, data = featureDataSource, outData = scoredOutput,   
                       predVarNames = "Score", type = "response",   
                       writeModelVars = TRUE, overwrite = TRUE)  
    ```  

  
## <a name="plotting-model-accuracy"></a>Creazione di un tracciato per l'accuratezza del modello  
Per avere un'idea dell'accuratezza del modello, è possibile usare la funzione *rxRocCurve* per tracciare la curva operativa del ricevitore. Poiché *rxRocCurve* è una delle nuove funzioni offerte dal pacchetto RevoScaleR che supporta contesti di calcolo remoti, sono disponibili due opzioni:  
  
+ È possibile usare la funzione `rxRocCurve` per eseguire il tracciato nel contesto di un computer remoto e quindi restituire il tracciato al client locale.
+ È inoltre possibile importare i dati nel computer client R e usare altre funzioni di tracciato R per creare il grafico delle prestazioni.  
  
In questa sezione verranno usate entrambe le tecniche.  
  
### <a name="execute-a-plot-in-the-remote-sql-server-compute-context"></a>Eseguire un tracciato nel contesto di calcolo remoto (SQL Server)  
  
1.  Chiamare la funzione *rxRocCurve* e fornire i dati definiti in precedenza come input.  
  
    ```R  
    rxRocCurve( "tipped", "Score", scoredOutput)  
    ```  
  
    Si noti che è inoltre necessario specificare la colonna di etichetta con le mance (la variabile da prevedere) e il nome della colonna che archivia la previsione (_Punteggio_).  
  
2.  Visualizzare il grafico generato aprendo il dispositivo di grafica R oppure facendo clic sulla finestra **Tracciato** in RStudio.  
  
    ![ROC plot for the model](../../advanced-analytics/r-services/media/rsql-e2e-rocplot.png "ROC plot for the model")  

    Il grafico viene creato nel contesto di calcolo remoto e quindi restituito all'ambiente R.   
    
### <a name="create-the-plots-in-the-local-compute-context-using-data-from-sql-server"></a>Creare i tracciati nel contesto di calcolo locale usando i dati di SQL Server  
  
1.  Usare la funzione *rxImport* per portare i dati specificati nell'ambiente R locale.  
  
    ```R  
    scoredOutput = rxImport(scoredOutput)  
    ```  
  
2.  Dopo aver caricato i dati nella memoria locale, è possibile chiamare la libreria **ROCR** per creare alcune previsioni e generare il tracciato.  
  
    ```R  
    library('ROCR')  
    pred <- prediction(scoredOutput$Score, scoredOutput$tipped)  
  
    acc.perf = performance(pred, measure = 'acc')  
    plot(acc.perf)  
    ind = which.max( slot(acc.perf, 'y.values')[[1]] )  
    acc = slot(acc.perf, 'y.values')[[1]][ind]  
    cutoff = slot(acc.perf, 'x.values')[[1]][ind]  
    ```  
  
3.  Il tracciato seguente viene generato in entrambi i casi.  
  
    ![plotting model performance using R](../../advanced-analytics/r-services/media/rsql-e2e-performanceplot.png "plotting model performance using R")  
  
## <a name="deploying-a-model"></a>Distribuzione di un modello  

Dopo avere creato un modello e averne verificato il corretto funzionamento, è possibile *renderlo operativo*. Poiché [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] consente di richiamare un modello R tramite una stored procedure [!INCLUDE[tsql](../../includes/tsql-md.md)] , è molto facile usare R in un'applicazione client.  
  
Tuttavia, prima di poter chiamare il modello da un'applicazione esterna, è necessario salvare il modello nel database usato per la produzione. In [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], i modelli sottoposti a training sono archiviati in formato binario, in un'unica colonna di tipo **varbinary(max)**.

Pertanto, lo spostamento di un modello con training da R a SQL Server include i passaggi seguenti:  
  
+ Serializzazione del modello in una stringa esadecimale
+ Trasmissione dell'oggetto serializzato al database
+ Salvataggio del modello in una colonna varbinary(max)  
  
In questa sezione verrà illustrato come rendere permanente il modello e come chiamarlo per eseguire previsioni.  
  
### <a name="serialize-the-model"></a>Serializzare il modello  
  
+  Nell'ambiente R locale serializzare il modello e salvarlo in una variabile.  
  
    ```R  
    modelbin <- serialize(logitObj, NULL)  
    modelbinstr=paste(modelbin, collapse="")  
    ```  
  
    La funzione *serialize* è inclusa nel pacchetto **di base** di R e offre una semplice interfaccia di basso livello per la serializzazione alle connessioni. Per altre informazioni, vedere [http://www.inside-r.org/r-doc/base/serialize](http://www.inside-r.org/r-doc/base/serialize).  
  
### <a name="move-the-model-to-sql-server"></a>Spostare il modello in SQL Server

+ Aprire una connessione ODBC e chiamare una stored procedure per archiviare la rappresentazione binaria del modello in una colonna del database. 
  
    ```R  
    library(RODBC)  
    conn <- odbcDriverConnect(connStr )  
  
    # persist model by calling a stored procedure from SQL  
    q<-paste("EXEC PersistModel @m='", modelbinstr,"'", sep="")  
    sqlQuery (conn, q)    
    ```  

Il salvataggio di un modello in una tabella richiede solo un'istruzione INSERT. Tuttavia, in questo specifico caso è più facile usare la stored procedure _PersistModel_. 
 
Come riferimento, questo è il codice completo della stored procedure:  
  
```tsql  
CREATE PROCEDURE [dbo].[PersistModel]  @m nvarchar(max)  
AS  
BEGIN  
        -- SET NOCOUNT ON added to prevent extra result sets from  
        -- interfering with SELECT statements.  
        SET NOCOUNT ON;  
        insert into nyc_taxi_models (model) values (convert(varbinary(max),@m,2))  
END   
```  
> [!TIP] Si consiglia di creare funzioni di supporto come la stored procedure per semplificare la gestione e l'aggiornamento dei modelli R in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
  
### <a name="invoke-the-saved-model"></a>Richiamare il modello salvato  
Dopo aver salvato il modello nel database, è possibile chiamarlo direttamente dal codice [!INCLUDE[tsql](../../includes/tsql-md.md)] tramite la stored procedure di sistema [sp_execute_external_script &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).  
  
Ad esempio, per generare le previsioni, è sufficiente connettersi al database ed eseguire una stored procedure che usa il modello salvato e alcuni dati come input.  
  
Tuttavia, se si dispone di un modello di uso frequente, è più semplice eseguire il wrapping della query di input e della chiamata al modello, nonché degli altri parametri, in una stored procedure personalizzata.  
  
Nella lezione successiva verrà illustrato come eseguire il punteggio in relazione al modello salvato tramite [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## <a name="next-lesson"></a>Lezione successiva  
[Lezione 5: Distribuire e usare il modello &#40;Procedura dettagliata end-to-end per l'analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/lesson-5-deploy-and-use-the-model-data-science-end-to-end-walkthrough.md)  
  
## <a name="previous-lesson"></a>Lezione precedente  
[Lezione 3: Creare funzionalità di dati &#40;Procedura dettagliata end-to-end per l'analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/lesson-3-create-data-features-data-science-end-to-end-walkthrough.md)  
  
  
  
