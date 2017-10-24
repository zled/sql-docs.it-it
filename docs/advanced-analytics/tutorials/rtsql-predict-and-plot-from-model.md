---
title: Stimare e tracciare dal modello (R nella Guida rapida SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- R
- SQL
ms.assetid: 46babd8a-a331-44fc-bbd6-24daf58865e1
caps.latest.revision: 15
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a84e702b364da8614dd21b8f6adb57e4f2bac487
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="predict-and-plot-from-model-r-in-sql-quickstart"></a>Stimare e tracciare dal modello (R nella Guida rapida SQL)

Per eseguire _punteggio_ utilizzando nuovi dati, ottenere uno dei modelli con training dalla tabella e quindi chiamare un nuovo set di dati su cui basare le stime. Il punteggio è un termine utilizzato talvolta scienza dei dati per indicare la generazione di stime, le probabilità o altri valori in base ai nuovi dati inseriti in un modello con training.

## <a name="create-the-table-of-new-speeds"></a>Creare la tabella delle nuove velocità

Si può notare che i dati di training originali non vanno oltre una velocità di 40 chilometri (25 miglia) all'ora, dal momento che sono basati su un esperimento del 1920.

Ci si può chiedere quanto tempo richiederebbe un'automobile del 1920 per fermarsi, presupponendo che possa procedere a una velocità di 100 km/h (60 mph) o addirittura di 150 km/h (100 mph). Per rispondere a questa domanda, è necessario fornire alcuni nuovi valori di velocità.

```sql
CREATE TABLE [dbo].[NewCarSpeed]([speed] [int] NOT NULL,
    [distance] [int]  NULL) ON [PRIMARY]
GO
INSERT [dbo].[NewCarSpeed] (speed)
VALUES (40),  (50),  (60), (70), (80), (90), (100)
```

## <a name="predict-stopping-distance"></a>Prevedere la distanza di arresto

A questo punto, la tabella potrebbe contenere più modelli R, tutti compilati usando parametri o algoritmi diversi o sottoposti a training su subset diversi di dati.

![rsql_basictut_listofmodels](media/rsql-basictut-listofmodels.png)

Per ottenere stime basate su un modello specifico, è necessario scrivere uno script SQL che esegue le operazioni seguenti:

1. Ottiene il modello desiderato
2. Ottiene i nuovi dati di input
3. Chiama una funzione di stima R compatibile con tale modello

In questo esempio, perché il modello è basato sul **rxLinMod** fornito come parte dell'algoritmo di **RevoScaleR** pacchetto, chiamare il [rxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict) funzione, anziché il R generico `predict` (funzione).

```sql
DECLARE @speedmodel varbinary(max) = (SELECT model FROM [dbo].[stopping_distance_models] WHERE model_name = 'latest model');
EXEC sp_execute_external_script
    @language = N'R'
    , @script = N'
            current_model <- unserialize(as.raw(speedmodel));
            new <- data.frame(NewCarData);
            predicted.distance <- rxPredict(current_model, new);
            str(predicted.distance);
            OutputDataSet <- cbind(new, ceiling(predicted.distance));
            '
    , @input_data_1 = N' SELECT speed FROM [dbo].[NewCarSpeed] '
    , @input_data_1_name = N'NewCarData'
    , @params = N'@speedmodel varbinary(max)'
    , @speedmodel = @speedmodel
WITH RESULT SETS (([new_speed] INT, [predicted_distance] INT))
```

+ Usare un'istruzione SELECT per ottenere un singolo modello dalla tabella e passarlo come parametro di input.
+  Dopo avere recuperato il modello dalla tabella, chiamare la funzione `unserialize` nel modello.

    > [!TIP] 
    > Controllare inoltre la nuova [funzioni serializzazione](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel) fornito da RevoScaleR, che supporta [assegnazione dei punteggi in tempo reale](../../advanced-analytics/real-time-scoring.md).
+  Applicare la funzione `rxPredict` con gli argomenti appropriati al modello e fornire i nuovi dati di input.
+  Nell'esempio di `str` funzione viene aggiunto durante la fase di test, per controllare lo schema dei dati restituiti da R. È possibile rimuovere l'istruzione in un secondo momento.
+ I nomi di colonna utilizzati nello script R non sono necessariamente passati all'output della stored procedure. Qui è stata utilizzata la clausola con risultati per definire alcuni nuovi nomi di colonna.

**Risultati**

![rsql_basictut_scoringresults_smalldata](media/rsql-basictut-scoringresults-smalldata.PNG)

## <a name="perform-scoring-in-parallel"></a>Eseguire la valutazione in parallelo

Le stime vengono restituite abbastanza velocemente su questo set di dati di piccole dimensioni. Ma si supponga che sia necessario eseguire un numero elevato di stime molto rapidamente. Esistono diversi modi per velocizzare le operazioni in SQL Server, pertanto più, se le operazioni possono essere elaborate in parallelo. Per la valutazione in particolare, un modo semplice consiste nell'aggiungere il parametro *@parallel* a `sp_execute_external_script` e impostare il valore su **1**.

Si supponga di disporre di una tabella molto più grande di possibili velocità delle auto, contenente centinaia di migliaia di valori. Nella community sono disponibili molti script T-SQL di esempio per generare tabelle numeriche, pertanto non verranno riportati in questo articolo. Si supponga semplicemente di disporre di una colonna contenente molti interi che si vuole usare come input per `speed` nel modello.

A tale scopo, solo eseguire la stessa query di stima, ma sostituire il set di dati più grande e aggiungere il `@parallel = 1` argomento.

```sql
DECLARE @speedmodel varbinary(max) = (select model from [dbo].[stopping_distance_models] where model_name = 'default model');
EXEC sp_execute_external_script
    @language = N'R'
    , @script = N'
            current_model <- unserialize(as.raw(speedmodel));
            new <- data.frame(NewCarData);
            predicted.distance <- rxPredict(current_model, new);
            OutputDataSet <- cbind(new, ceiling(predicted.distance));
            '
    , @input_data_1 = N' SELECT [speed] FROM [dbo].[HugeTableofCarSpeeds] '
    , @input_data_1_name = N'NewCarData'
    , @parallel = 1
    , @params = N'@speedmodel varbinary(max)'
    , @speedmodel = @speedmodel
WITH RESULT SETS (([new_speed] INT, [predicted_distance] INT))
```

+ L'esecuzione parallela offre in genere vantaggi solo quando si lavora con dati molto grandi. Il motore di database SQL potrebbe decidere che l'esecuzione parallela non è necessario. Inoltre, la query SQL per il recupero dei dati deve essere in grado di generare un piano di query parallelo.

+ Quando si usa l'opzione per l'esecuzione parallela, **è necessario** specificare in anticipo lo schema dei risultati di output tramite la clausola WITH RESULT SETS. Specificando lo schema di output in anticipo, si consente a SQL Server di aggregare i risultati di più set di dati paralleli, che in caso contrario potrebbero avere schemi sconosciuti.

+ Se si è *training* un modello anziché *punteggio*, questo parametro non hanno un effetto. A seconda del tipo di modello, la creazione di modelli potrebbe richiedere che tutte le righe vengano lette prima della creazione dei riepiloghi.

+ Per ottenere i vantaggi dell'elaborazione parallela in cui eseguire il training del modello, è consigliabile utilizzare uno del **RevoScaleR** algoritmi. Questi algoritmi sono progettati per distribuire l'elaborazione automaticamente, anche se non si specifica <code>@parallel =1</code> nella chiamata a `sp_execute_external_script`. Per istruzioni su come ottenere le migliori prestazioni con RevoScaleR algoritmi, vedere [distribuita e l'elaborazione in parallelo con ScaleR nella Microsoft R](https://docs.microsoft.com/r-server/r/how-to-revoscaler-distributed-computing).

## <a name="create-an-r-plot-of-the-model"></a>Creare un tracciato R del modello

Molti client, tra cui SQL Server Management Studio, non sono in grado di visualizzare direttamente i tracciati creati con [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Al contrario, il processo generale per la generazione di grafici R consiste nel creare il tracciato come parte del codice R e quindi scrivere l'immagine in un file.

In alternativa, è possibile restituire l'oggetto serializzato tracciato binario a qualsiasi applicazione che consente di visualizzare immagini.

L'esempio seguente illustra come creare una semplice immagine usando una funzione di creazione tracciato inclusa per impostazione predefinita in R. L'immagine viene restituita nel file specificato, oltre che in una variabile SQL dalla stored procedure.

```sql
 EXECUTE sp_execute_external_script
 @language = N'R'
 , @script = N'
     imageDir <- ''C:\\temp\\plots'';
     image_filename = tempfile(pattern = "plot_", tmpdir = imageDir, fileext = ".jpg")
     print(image_filename);
     jpeg(filename=image_filename,  width=600, height = 800);
     print(plot(distance~speed, data=InputDataSet, xlab="Speed", ylab="Stopping distance", main = "1920 Car Safety"));
     abline(lm(distance~speed, data = InputDataSet));
     dev.off();
     OutputDataSet <- data.frame(data=readBin(file(image_filename, "rb"), what=raw(), n=1e6));
     '
  , @input_data_1 = N'SELECT speed, distance from [dbo].[CarSpeed]'
  WITH RESULT SETS ((plot varbinary(max)));
```

+ Il `tempfile` funzione restituisce una stringa che può essere utilizzata come nome di file, ma il file non è stati ancora generato.
+ Per gli argomenti a `tempfile`, è possibile specificare un prefisso di estensione di file, nonché la directory. Per verificare il nome file completo e il percorso, stampa un messaggio utilizzando `str()`.
+ La funzione `jpeg` crea un dispositivo R con i parametri specificati.
+ Dopo aver creato il tracciato, è possibile aggiungere altre funzionalità di visual. In questo caso, viene aggiunta una riga di regressione usando `abline`.
+ Dopo avere aggiunto tutte le funzionalità di creazione tracciato desiderate, è necessario chiudere il dispositivo grafico tramite la funzione `dev.off()`.
+ La funzione `readBin` accetta un file da leggere, una specifica di formato e il numero di record. Il `rb`* * ' parola chiave indica che il file è binario anziché di testo.

**Risultati**

![rsql_basictut_plotresult_small](media/rsql-basictut-plotresult-small.png)

Se si vogliono eseguire tracciati più elaborati usando alcuni dei pacchetti di grafica avanzati per R, è consigliabile leggere gli articoli seguenti. Entrambi prevedono l'uso del pacchetto **ggplot2**, ampiamente diffuso.

+ [Loan Classification using SQL Server 2016 R Services](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2016/09/27/loan-classification-using-sql-server-2016-r-services/) (Classificazione dei prestiti tramite SQL Server 2016 R Services): uno scenario end-to-end basato sui dati delle assicurazioni. Richiede il **rielaborare** pacchetto.
+ [Creare grafici e grafici con R](../../advanced-analytics/tutorials/walkthrough-create-graphs-and-plots-using-r.md)

## <a name="conclusions"></a>Conclusioni

L'integrazione di R con SQL Server rende più semplice distribuire soluzioni R su larga scala, sfruttando le funzionalità migliori di R e dei database relazionali, per una gestione dei dati a prestazioni elevate e un'analisi R più rapida. 

Vedere le risorse aggiuntive per altri esempi di R:

+  [Esercitazioni di SQL Server R](../../advanced-analytics/tutorials/sql-server-r-tutorials.md)

    Ulteriori informazioni sulle soluzioni tramite scenari end-to-end creati dai team di sviluppo R Services e di analisi scientifica dei dati di Microsoft R con SQL Server.

+ [Esercitazioni di SQL Server Python](../../advanced-analytics/tutorials/sql-server-python-tutorials.md)

    Per SQL Server 2017, utilizzare la potenza del contesto di calcolo remoto e l'algoritmo scalabile con il linguaggio Python.

+ [Esercitazioni e i dati di esempio per Microsoft R](https://docs.microsoft.com/r-server/r/tutorial-introduction)

    Informazioni su come usare i nuovi pacchetti RevoScaleR per creare modelli e trasformare i dati.

+ [Introduzione a MicrosoftML](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package)

    Altre informazioni sul veloci e scalabili algoritmi di machine learning di Microsoft Research.

