---
title: 'Aggiornato: avanzato Analitica per i documenti del Server SQL | Documenti Microsoft'
description: Visualizzare i frammenti di contenuto aggiornato per modificati di recente nella documentazione, Analitica avanzato per Microsoft SQL Server.
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: 
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 07/17/2017
ms.author: genemi
ms.workload: advanced-analytics
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 79f979ecda1ff0851978d19ef28fa3cf909f9a43
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="new-and-recently-updated-advanced-analytics-for-sql-server"></a>Nuovi e aggiornati: Advanced Analitica per SQL Server



Microsoft aggiorna quasi quotidianamente alcuni degli articoli presenti nel sito Web della documentazione [Docs.Microsoft.com](http://docs.microsoft.com/). Questo articolo contiene estratti degli articoli aggiornati di recente. Possono essere indicati anche collegamenti a nuovi articoli.

Questo articolo è generato da un programma che viene rieseguito periodicamente. In alcuni casi un estratto può avere una formattazione imperfetta o essere visualizzato come markdown dell'articolo di origine. Qui le immagini non vengono mai visualizzate.

Sono riportati gli aggiornamenti recenti per l'intervallo di date e l'area di interesse seguenti:



- *Intervallo di date degli aggiornamenti:* &nbsp; **23/05/2017** &nbsp; - &nbsp; **17/07/2017**
- *Area di interesse:* &nbsp; **Analitica avanzate per SQL Server**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


1. [Problemi comuni con l'esecuzione dello Script esterno](common-issues-external-script-execution.md)
2. [Raccolta dei dati per la risoluzione dei problemi di Machine Learning](data-collection-ml-troubleshooting-process.md)
3. [Esercitazioni di Python SQL Server](tutorials/sql-server-python-tutorials.md)
4. [Esercitazioni su SQL Server R](tutorials/sql-server-r-tutorials.md)




&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Elenco compatto degli articoli aggiornati di recente

Questo elenco compatto include i collegamenti a tutti gli articoli aggiornati elencati nella sezione degli estratti.



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione sono visualizzati gli estratti degli aggiornamenti raccolti dagli articoli che recentemente sono stati sottoposti a un aggiornamento di grande entità.

Gli estratti visualizzati qui sono separati dal relativo contesto semantico. Inoltre è possibile che un estratto sia talvolta separato da importanti elementi di sintassi markdown che lo circondano nell'articolo vero e proprio. Di conseguenza, questi estratti devono essere usati solo come indicazioni generali. Gli estratti consentono solo di comprendere se sia utile o meno consultare l'articolo completo.

Per queste e altre ragioni, non copiare codice da questi estratti e non prendere come verità assoluta ciò che si legge negli estratti. Visitare piuttosto gli articoli veri e propri.



&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-introducing-revoscalepypythonwhat-is-revoscalepymd"></a>1. &nbsp;[Introduzione revoscalepy](python/what-is-revoscalepy.md)

*Aggiornamento: 23/06/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Successivo](#TitleNum_2))

<!-- Source markdown line 112.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 cab7330ac9944508aaa360e00cbc2e866455776d 33f4e0e2421fa79fc11931dc7f29bff4432c6f5a  (PR=2171  ,  Filename=what-is-revoscalepy.md  ,  Dirpath=docs\advanced-analytics\python\  ,  MergeCommitSha40=7d2dbe0bdc4cbd05f11eacf938b35a9c35ace2e7) -->



**Con revoscalepy MicrosoftML**


Le funzioni di Python per MicrosoftML sono integrate con le origini di dati che sono state fornite nel revoscalepy e i contesti di calcolo. Pertanto, è possibile utilizzare un algoritmo MicrosoftML per definire ed eseguire il training di un modello di Python e utilizzare le funzioni revoscalepy per eseguire il codice Python localmente o in un contesto di calcolo di SQl Server.

Importa i moduli di codice Python e quindi fare riferimento le singole funzioni che è necessario.

```
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

**Requisiti**


Per eseguire codice Python in SQL Server, è necessario avere installato SQL Server 2017 con la funzionalità di **Machine Learning Services**e abilitato il linguaggio Python. Le versioni precedenti di SQL Server non supportano l'integrazione di Python.

> [!NOTE]
> Contesti di calcolo di SQL Server non supportano distribuzioni Apri origine di Python. Tuttavia, se si desidera pubblicare e utilizzare le applicazioni di Python da Windows, è possibile installare Server di Microsoft Machine Learning senza installazione di SQL Server. Per ulteriori informazioni, vedere [creare Standalone R Server--... /r/create-a-standalone-r-server.MD)

**Ulteriori informazioni**





&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-step-5-train-and-save-a-model-using-t-sqltutorialssqldev-py5-train-and-save-a-model-using-t-sqlmd"></a>2. &nbsp;[Passaggio 5: eseguire il training e salvataggio di un modello utilizzando T-SQL](tutorials/sqldev-py5-train-and-save-a-model-using-t-sql.md)

*Ultimo aggiornamento: 2017-06-01* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_1) | [Avanti](#TitleNum_3))

<!-- Source markdown line 121.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 5c1cbe92282b96105ffdb69efa803f58dc0ac7e2 e4077a2154a90de468c435efa5b2225125d5b0e7  (PR=1904  ,  Filename=sqldev-py5-train-and-save-a-model-using-t-sql.md  ,  Dirpath=docs\advanced-analytics\tutorials\  ,  MergeCommitSha40=dbf91e0d6f8257227cfe8ac6d13c484d0a566f57) -->



1. In [! Includi [ssManStudio--... /.. /Includes/ssmanstudio-MD.MD)], aprire una nuova finestra Query ed eseguire l'istruzione seguente per creare la stored procedure _TrainTipPredictionModelRxPy_.  Questo modello sarà basato sui dati di training che è stato appena predisposto. Poiché la stored procedure include già una definizione dei dati di input, non è necessario fornire una query di input.

    ```SQL
    DROP PROCEDURE IF EXISTS TrainTipPredictionModelRxPy;
    GO

    CREATE PROCEDURE [dbo].[TrainTipPredictionModelRxPy] (@trained_model varbinary(max) OUTPUT)
    AS
    BEGIN
    EXEC sp_execute_external_script 
      @language = N'Python',
      @script = N'
    import numpy
    import pickle
    import pandas
    from revoscalepy.functions.RxLogit import rx_logit_ex
    
    ## Create a logistic regression model using rx_logit_ex function from revoscalepy package
    logitObj = rx_logit_ex("tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance", data = InputDataSet);
    
    ## Serialize model
    trained_model = pickle.dumps(logitObj)
    ',
    @input_data_1 = N'
    select tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance, 
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
    from nyctaxi_sample_training
    ',
    @input_data_1_name = N'InputDataSet',
    @params = N'@trained_model varbinary(max) OUTPUT',
    @trained_model = @trained_model OUTPUT;
    ;
    END;
    ```



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-step-6-operationalize-the-modeltutorialssqldev-py6-operationalize-the-modelmd"></a>3. &nbsp;[Passaggio 6: rendere operativo il modello](tutorials/sqldev-py6-operationalize-the-model.md)

*Ultimo aggiornamento: 2017-06-01* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_2) | [Avanti](#TitleNum_4))

<!-- Source markdown line 236.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 1eb50ac902d4e80bafb1dd7fdf8f607dcdf0d33f 57d5abdc6119db1ecd81587d625054a5bbfb5fc8  (PR=1904  ,  Filename=sqldev-py6-operationalize-the-model.md  ,  Dirpath=docs\advanced-analytics\tutorials\  ,  MergeCommitSha40=dbf91e0d6f8257227cfe8ac6d13c484d0a566f57) -->



Qui è la definizione della stored procedure che esegue l'assegnazione dei punteggi usando il **revoscalepy** modello.

```
CREATE PROCEDURE [dbo].[PredictTipSingleModeRxPy] (@model varchar(50), @passenger_count int = 0,
  @trip_distance float = 0,
  @trip_time_in_secs int = 0,
  @pickup_latitude float = 0,
  @pickup_longitude float = 0,
  @dropoff_latitude float = 0,
  @dropoff_longitude float = 0)
AS
BEGIN
  DECLARE @inquery nvarchar(max) = N'
    SELECT * FROM [dbo].[fnEngineerFeatures-- 
      @passenger_count,
      @trip_distance,
      @trip_time_in_secs,
      @pickup_latitude,
      @pickup_longitude,
      @dropoff_latitude,
      @dropoff_longitude)
    '
  DECLARE @lmodel2 varbinary(max) = (select model from nyc_taxi_models2 where name = @model);
  EXEC sp_execute_external_script 
    @language = N'Python',
    @script = N'
      import pickle;
      import numpy;
      import pandas;
      from revoscalepy.functions.RxPredict import rx_predict_ex;
```




&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-use-python-with-revoscalepy-to-create-a-modeltutorialsuse-python-revoscalepy-to-create-modelmd"></a>4. &nbsp;[Usare Python con revoscalepy per creare un modello](tutorials/use-python-revoscalepy-to-create-model.md)

*Ultimo aggiornamento: 2017-06-21* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_3))

<!-- Source markdown line 119.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0886939f86fe12d7ff7b339689a02c7fc75e0786 23dd469349a05d535063aab3c14aec152ed2cd7b  (PR=2141  ,  Filename=use-python-revoscalepy-to-create-model.md  ,  Dirpath=docs\advanced-analytics\tutorials\  ,  MergeCommitSha40=76839e39427e24688609353b8708d59fee772d28) -->



**Esaminare il codice**


Consente di esaminare il codice ed evidenziare alcuni passaggi chiave.

**Definizione di un tipo di dati di origine e di contesto di calcolo**


Si tratta di una parte importante dell'utilizzo di **revoscalepy** e il relativo pacchetto R correlato **RevoScaleR**. Un'origine dati è diversa da un contesto di calcolo. Il _origine dati_ definisce i dati utilizzati nel codice. Il _contesto di calcolo_ definisce in cui verrà eseguito il codice.

> [!NOTE]
> Supporto per alcuni tipi di origini dati supportate in RevoScaleR potrebbe limitare la versione non definitiva. Per ulteriori informazioni sulle funzioni incluse nella versione più recente, vedere [novità revoscalepy--... /Python/What-is-revoscalepy.MD).

Generale di processo per la creazione e utilizzo di un'origine dati e di calcolo contesto è indicato di seguito:

1. Creare le variabili di Python, ad esempio _sqlQuery_ e _connectionString_, che definiscono l'origine e i dati che si desidera utilizzare. Passare tali variabili di **RxSqlServerData** costruttore per implementare il **oggetto origine dati** denominato _dataSource_.
2. Creare un oggetto di contesto di calcolo tramite il **RxInSqlServer** costruttore. In questo esempio, passare la stringa di connessione che è definita in precedenza, presupponendo che i dati sono nella stessa istanza di SQL Server che verrà utilizzato come contesto di calcolo. Tuttavia, l'origine dati e il contesto di calcolo potrebbe essere in server diversi. Il valore risultante **oggetto contesto di calcolo** denominato _computeContext_.
3. Scegliere il contesto di calcolo attivo. Per impostazione predefinita, le operazioni vengono eseguite in locale, vale a dire che se non si specifica un contesto di calcolo diverso, verranno recuperati i dati dall'origine dati e verrà eseguito l'adattamento del modello nell'ambiente corrente di Python.

    In RevoScaleR, è inoltre possibile utilizzare la funzione `rxSetComputeContext` per alternare i contesti di calcolo. La funzione non è ancora implementata nella versione di anteprima di **revoscalepy**, ma è possibile specificare il contesto di calcolo come argomento di **rx_lin_mod_ex**.





<a name="similars2"/>

&nbsp;

## <a name="similar-articles"></a>Articoli simili

In questa sezione sono elencati articoli molto simili ad articoli aggiornati di recente in altre aree di interesse all'interno dello stesso repository GitHub: [MicrosoftDocs/**sql-docs-pr**](https://github.com/microsoftdocs/sql-docs-pr/).

<!--  20170717-1101  -->

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Aree di interesse con articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (4+4): **Advanced Analytics per SQL** Docs](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (2+0): documentazione di **Analysis Services per SQL**](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (1+2): documentazione di **Connetti a SQL Server**](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (6+0): documentazione di **Motore di database per SQL**](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (13+2): documentazione di **Linux per SQL**](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (1+0): documentazione di **Master Data Services (MDS) per SQL**](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (1+0): documentazione di **ODBC (Open Database Connectivity) per SQL**](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornato (8+4): documentazione di **Database relazionali per SQL**](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornato (2+2): documentazione di **Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (0+1): documentazione di **SQL Server Management Studio (SSMS)**](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornato (1+0): documentazione di **Transact-SQL**](../t-sql/new-updated-t-sql.md)
- [Nuovo + aggiornato (1+0): **Strumenti per SQL** Docs](../tools/new-updated-tools.md)


#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Aree di interesse senza articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (0+0): **ActiveX Data Objects (ADO) for SQL (ActiveX Data Objects (ADO) per SQL)** Docs](../ado/new-updated-ado.md)
- [Nuovo + aggiornato (0+0): **Data Quality Services for SQL (Data Quality Services per SQL)** Docs](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0+0): **Data Mining Extensions (DMX) for SQL (Estensioni di data mining (DMX) per SQL)** Docs](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0+0): **Integration Services per SQL** Docs](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (0+0): **Multidimensional Expressions (MDX) for SQL(Espressioni MDX per SQL)** Docs](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0+0): **PowerShell for SQL (PowerShell per SQL)** Docs](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (0+0): **Reporting Services per SQL** Docs](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (0+0): **Samples for SQL (Esempi per SQL)** Docs](../sample/new-updated-sample.md)
- [Nuovo + aggiornato (0+0): **SQL Server Data Tools (SSDT)** Docs](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (0+0): **SQL Server Migration Assistant (SSMA)** Docs](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (0+0): **XQuery for SQL (XQuery per SQL)** Docs](../xquery/new-updated-xquery.md)


&nbsp;


