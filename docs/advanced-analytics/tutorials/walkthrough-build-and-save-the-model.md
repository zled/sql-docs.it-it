---
title: Compilare un modello R e salvare in SQL Server | Documenti Microsoft
ms.custom: 
ms.date: 07/14/2017
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
ms.assetid: 69b374c1-2042-4861-8f8b-204a6297c0db
caps.latest.revision: 21
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 437ec62abb0107e8a70926fd60d0c54cc6064122
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="build-an-r-model-and-save-to-sql-server"></a>Compilare un modello R e salvare in SQL Server

In questo passaggio verrà illustrato come compilare un modello di machine learning e salvare il modello in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

## <a name="create-a-classification-model-using-rxlogit"></a>Creare un modello di classificazione utilizzando rxLogit

Il modello che compilazione è un classificatore binario che consente di stimare se il driver taxi è probabile che ottenere un suggerimento su un particolare marcia o non. Si userà l'origine dati creata nella lezione precedente per il training del classificatore di suggerimento, utilizzare la regressione logistica.

1. Chiamare la funzione [rxLogit](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit) inclusa nel pacchetto **RevoScaleR** per creare un modello di regressione logistica. 

    ```R
    system.time(logitObj <- rxLogit(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = sql_feature_ds));
    ```

    La chiamata che crea il modello è racchiusa nella funzione system.time. Ciò consente di ottenere il tempo necessario per compilare il modello.

2. Dopo aver compilato il modello, è possibile controllare tramite il `summary` funzione e visualizzare i coefficienti.

    ```R
    summary(logitObj);
    ```

     *Risultati*

     *Risultati di regressione logistica per: inclinato ~ passenger_count trip_distance + trip_time_in_secs +*
     <br/>*direct_distance*
     <br/>*Dati: featureDataSource (origine dati RxSqlServerData)*
     <br/>*Dependent variable(s): inclinato*
     <br/>*Totale delle variabili indipendenti: 5*
     <br/>*Numero di osservazioni valide: 17068*
     <br/>*Numero di osservazioni mancante: 0*
     <br/>*-2\*LogLikelihood: 23540.0602 (deviazione residuo in gradi di 17063 libertà)*
     <br/>*Coefficienti:*
     <br/>*Estimate Std. Il valore di errore z Pr (> | z |)*
     <br/>*(Intercettare) - 2.509e-03 3.223e-02-0.078 0.93793*
     <br/>*passenger_count-5.753e-02 1.088e-02-5.289 1.23 e-07\*\*\**
     <br/>*trip_distance-3.896e-02 1.466e-02-2.658 0.00786\*\**
     <br/>*trip_time_in_secs 2.115e-04 4.336e-05 4.878 1.07e-06\*\*\**
     <br/>*direct_distance 6.156e-02 2.076e-02 2.966 0.00302\*\**
     <br/>*---*
     <br/>*Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1*
     <br/>*Condizione numero di una matrice di covarianza-varianza finale: 48.3933*
     <br/>*Number of iterations: 4*

## <a name="use-the-logistic-regression-model-for-scoring"></a>Usare il modello di regressione logistica per assegnare i punteggi

Dopo aver compilato il modello, è possibile usarlo per prevedere se il tassista riceverà una mancia in una specifica corsa.

1. Innanzitutto, utilizzare il [RxSqlServerData](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqlserverdata) per definire un oggetto origine dati per archiviare il punteggio resul (funzione)

    ```R
    scoredOutput <- RxSqlServerData(
      connectionString = connStr,
      table = "taxiScoreOutput"  )
    ```

    + Per semplificare questo esempio, l'input per il modello di regressione logistica è la stessa origine dati di funzionalità (`sql_feature_ds`) utilizzata per il training del modello.  Più generalmente è possibile usare nuovi dati per i punteggi oppure riservare alcuni dati per il test e non per il training.
  
    + I risultati di stima verranno salvati nella tabella, _taxiscoreOutput_. Si noti che lo schema per questa tabella non è definito quando si crea mediante rxSqlServerData. Lo schema viene ottenuto dall'output rxPredict.
  
    + Per creare la tabella che contiene i valori stimati, l'account di accesso SQL che esegue la funzione di data rxSqlServer è necessario disporre dei privilegi DDL nel database. Se l'account di accesso non è possibile creare tabelle, l'istruzione ha esito negativo.

2. Chiamare la funzione [rxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict) per generare i risultati.

    ```R
    rxPredict(modelObject = logitObj,
        data = sql_feature_ds,
        outData = scoredOutput,
        predVarNames = "Score",
        type = "response",
        writeModelVars = TRUE, overwrite = TRUE)
    ```
    
    Se l'istruzione ha esito positivo, è necessario tempo per l'esecuzione. Al termine, è possibile aprire SQL Server Management Studio e verificare che la tabella è stata creata e che contiene la colonna di punteggio e altri output previsto.

## <a name="plot-model-accuracy"></a>Tracciare l'accuratezza del modello

Per ottenere un'idea generale dell'accuratezza del modello, è possibile utilizzare il [rxRoc](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxroc) funzione per tracciare la curva operativo ricevitore. Poiché rxRoc è una delle nuove funzioni fornite dal pacchetto RevoScaleR che supporta i contesti di calcolo remoto, sono disponibili due opzioni:

+ È possibile utilizzare la funzione rxRoc per eseguire il tracciato nel contesto di calcolo remoto e quindi restituire il tracciato per il client locale.

+ È inoltre possibile importare i dati nel computer client R e usare altre funzioni di tracciato R per creare il grafico delle prestazioni.

In questa sezione è illustrato come utilizzare entrambe le tecniche.

### <a name="execute-a-plot-in-the-remote-sql-server-compute-context"></a>Eseguire un tracciato nel contesto di calcolo remoto (SQL Server)

1. Chiamare la funzione rxRoc e fornire i dati definiti in precedenza come input.

    ```R
    scoredOutput = rxImport(scoredOutput);
    rxRoc(actualVarName= "tipped", predVarNames = "Score", scoredOutput);
    ```

    Questa chiamata restituisce i valori utilizzati nel calcolo del grafico ROC. La colonna di etichetta è _inclinato_, contenente i risultati effettivi che si sta tentando di stimare, mentre il _punteggio_ della colonna è la stima.

2. Per tracciare effettivamente il grafico, è possibile salvare l'oggetto ROC e quindi disegnare con il `plot` (funzione). Il grafico viene creato nel contesto di calcolo remoti e restituito all'ambiente R.

    ```R
    scoredOutput = rxImport(scoredOutput);
    rocObjectOut <- rxRoc(actualVarName= "tipped", predVarNames = "Score", scoredOutput);
    plot(rocObjectOut);
    ```

    Visualizzare il grafico, aprire il dispositivo di grafica R oppure scegliendo il **tracciare** finestra RStudio.

    ![tracciato ROC per il modello](media/rsql-e2e-rocplot.png "tracciato ROC per il modello")

### <a name="create-the-plots-in-the-local-compute-context-using-data-from-sql-server"></a>Creare i tracciati nel contesto di calcolo locale usando i dati di SQL Server

1. Per il contesto di calcolo locale, il processo è molto simile. Utilizzare il [rxImport](https://docs.microsoft.com/r-server/r-reference/revoscaler/rximport) funzione per portare i dati specificati nell'ambiente R locale.

    ```R
    scoredOutput = rxImport(scoredOutput)
    ```

2. Usando i dati nella memoria locale, caricare il **ROCR** pacchetto e utilizzare la funzione di stima di tale pacchetto per creare alcune nuove stime.

    ```R
    library('ROCR');
    pred <- prediction(scoredOutput$Score, scoredOutput$tipped);

3. Generate a local plot, based on the values stored in the output variable `pred`.

    ```R
    acc.perf = performance(pred, measure = 'acc');
    plot(acc.perf);
    ind = which.max( slot(acc.perf, 'y.values')[[1]] );
    acc = slot(acc.perf, 'y.values')[[1]][ind];
    cutoff = slot(acc.perf, 'x.values')[[1]][ind];
    ```

    ![tracciare le prestazioni del modello con R](media/rsql-e2e-performanceplot.png "tracciare le prestazioni del modello con R")

> [!NOTE]
> I grafici potrebbero essere diversi da queste operazioni, a seconda di quanti punti dati è stato utilizzato.

## <a name="deploy-the-model"></a>Distribuire il modello

Dopo aver compilato un modello e ha accertato che stia funzionando correttamente, consigliabile distribuirlo a un sito in cui gli utenti o gli utenti dell'organizzazione consentono di utilizzare del modello, o forse ripetere il training e ricalibrare il modello a intervalli regolari. Talvolta questo processo è chiamato *operatività* un modello.

Poiché [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] consente di richiamare un modello R usando un [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure, è facile usare il linguaggio R in un'applicazione client.

Tuttavia, prima di poter chiamare il modello da un'applicazione esterna, è necessario salvare il modello nel database usato per la produzione. In [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], i modelli sottoposti a training sono archiviati in formato binario, in un'unica colonna di tipo **varbinary(max)**.

Pertanto, lo spostamento di un modello con training da R a SQL Server include i passaggi seguenti:

+ Serializzazione del modello in una stringa esadecimale

+ Trasmissione dell'oggetto serializzato al database

+ Salvataggio del modello in una colonna varbinary(max)

In questa sezione è illustrato come mantenere il modello e come chiamare questo metodo per eseguire stime.

1. Tornare a ambiente R locale se non si sono già utilizzando, serializza il modello e salvarla in una variabile.

    ```R
    rxSetComputeContext("local");
    modelbin <- serialize(logitObj, NULL);
    modelbinstr=paste(modelbin, collapse="");
    ```

2. Aprire una connessione ODBC tramite **RODBC**.

    ```R
    library(RODBC);
    conn <- odbcDriverConnect(connStr);
    ```

    È possibile omettere la chiamata a RODBC se si dispone già del pacchetto caricato.

3. Chiamare la stored procedure creata dallo script di PowerShell, per archiviare la rappresentazione binaria del modello in una colonna nel database.

    ```R
    q <- paste("EXEC PersistModel @m='", modelbinstr,"'", sep="");
    sqlQuery (conn, q);
    ```

    Il salvataggio di un modello in una tabella richiede solo un'istruzione INSERT. Tuttavia, risulta più semplice quando è stato eseguito il wrapping in una stored procedure, ad esempio _PersistModel_.

    > [!NOTE]
    > Se si verifica un errore, ad esempio "l'autorizzazione EXECUTE è stata negata per l'oggetto PersistModel", verificare che l'account di accesso disponga dell'autorizzazione. È possibile concedere le autorizzazioni esplicite nella stored procedure eseguendo l'istruzione T-SQL seguente:`GRANT EXECUTE ON [dbo].[PersistModel] TO <user_name>`

4. Dopo aver creato un modello e salvato in un database, è possibile chiamare direttamente dal [!INCLUDE[tsql](../../includes/tsql-md.md)] codice, che usa la stored procedure di sistema [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

    Tuttavia, con qualsiasi modello di utilizzo frequente, risulta più semplice eseguire il wrapping di query di input e la chiamata al modello, con altri parametri, in una stored procedure personalizzata.

    Di seguito è riportato il codice completo di un tale stored procedure. Si consiglia di creare stored procedure, ad esempio quella per renderne più semplice gestire e aggiornare i modelli R in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

    ```tsql
    CREATE PROCEDURE [dbo].[PersistModel]  @m nvarchar(max)
    AS
    BEGIN
      SET NOCOUNT ON;
      INSERT INTO nyc_taxi_models (model) values (convert(varbinary(max),@m,2))
    END
    ```

  > [!NOTE]
  > Utilizzare il **SET NOCOUNT ON** clausola per evitare risultati aggiuntivi imposta interferisca con le istruzioni SELECT.


Nella lezione successiva e finale imparare a eseguire l'assegnazione dei punteggi in del modello salvato tramite [!INCLUDE[tsql](../../includes/tsql-md.md)].

## <a name="next-lesson"></a>Lezione successiva

[Distribuire il modello R e utilizzare in SQL](/walkthrough-deploy-and-use-the-model.md)

## <a name="previous-lesson"></a>Lezione precedente

[Creare le funzionalità di dati con R e SQL](/walkthrough-create-data-features.md)


