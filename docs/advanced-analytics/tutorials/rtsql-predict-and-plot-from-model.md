---
title: Guida introduttiva per stimare e creare un tracciato dal modello usando R in SQL Server Machine Learning | Microsoft Docs
description: In questa Guida introduttiva, informazioni sull'assegnazione del punteggio utilizzando un modello predefinito nei dati di R e SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/15/2018
ms.topic: quickstart
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 60e152948945f4e86cc1114ae7b20c0e48b403bf
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39086653"
---
# <a name="quickstart-predict-and-plot-from-model-using-r-in-sql-server"></a>Guida introduttiva: Stimare e creare un tracciato dal modello usando R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questa Guida introduttiva, usare il modello creato nella precedente Guida introduttiva per assegnare un punteggio stime basate su dati aggiornati. Per eseguire _assegnazione di punteggi_ usando nuovi dati, ottenere uno dei modelli con training dalla tabella e quindi chiamare un nuovo set di dati su cui basare le stime. Assegnazione dei punteggi è un termine usato talvolta in analisi scientifica dei dati per indicare la generazione di stime, le probabilità o altri valori in base a nuovi dati inseriti in un modello con training.

## <a name="prerequisites"></a>Prerequisiti

Questa Guida introduttiva è un'estensione della [creare un modello predittivo](rtsql-create-a-predictive-model-r.md).

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

In questo esempio, poiché il modello è basato sul **rxLinMod** fornito come parte dell'algoritmo il **RevoScaleR** pacchetto, si chiama il [rxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict) funzione, anziché quella di R generico `predict` (funzione).

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
    , @input_data_1 = N'SELECT speed FROM [dbo].[NewCarSpeed]'
    , @input_data_1_name = N'NewCarData'
    , @params = N'@speedmodel varbinary(max)'
    , @speedmodel = @speedmodel
WITH RESULT SETS (([new_speed] INT, [predicted_distance] INT))
```

+ Usare un'istruzione SELECT per ottenere un singolo modello dalla tabella e passarlo come parametro di input.
+ Dopo avere recuperato il modello dalla tabella, chiamare la funzione `unserialize` nel modello.

    > [!TIP] 
    > Controllare anche la nuova [funzioni di serializzazione](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel) forniti da RevoScaleR, che supportano [assegnazione dei punteggi in tempo reale](../real-time-scoring.md).
+  Applicare la funzione `rxPredict` con gli argomenti appropriati al modello e fornire i nuovi dati di input.
+  Nell'esempio di `str` (funzione) viene aggiunto durante la fase di test per verificare lo schema dei dati restituiti da R. È possibile rimuovere l'istruzione in un secondo momento.
+ I nomi delle colonne usate nello script R non vengono necessariamente passati all'output della stored procedure. È qui abbiamo utilizzato la clausola WITH RESULTS per definire alcuni nuovi nomi di colonna.

**Risultati**

![rsql_basictut_scoringresults_smalldata](media/rsql-basictut-scoringresults-smalldata.PNG)

## <a name="perform-scoring-in-parallel"></a>Eseguire la valutazione in parallelo

Le stime vengono restituite abbastanza velocemente su questo set di dati di piccole dimensioni. Ma si supponga che sia necessario eseguire un numero elevato di stime molto rapidamente. Esistono molti modi per velocizzare le operazioni in SQL Server, soprattutto se le operazioni possono essere elaborate in parallelo. Per la classificazione in particolare, un semplice modo consiste nell'aggiungere il *@parallel* parametro in sp_execute_external_script e impostare il valore **1**.

Si supponga di disporre di una tabella molto più grande di possibili velocità delle auto, contenente centinaia di migliaia di valori. Nella community sono disponibili molti script T-SQL di esempio per generare tabelle numeriche, pertanto non verranno riportati in questo articolo. Si supponga semplicemente di disporre di una colonna contenente molti interi che si vuole usare come input per `speed` nel modello.

A tale scopo, semplicemente eseguire la stessa query di stima, ma sostituire il set di dati più grande e aggiungere il `@parallel = 1` argomento.

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

+ L'esecuzione parallela offre vantaggi a livello generale solo quando si lavora con dati molto grandi. Il motore di database SQL potrebbe decidere che non è necessaria l'esecuzione parallela. Inoltre, la query SQL per il recupero dei dati deve essere in grado di generare un piano di query parallelo.

+ Quando si usa l'opzione per l'esecuzione parallela, **è necessario** specificare in anticipo lo schema dei risultati di output tramite la clausola WITH RESULT SETS. Specificando lo schema di output in anticipo, si consente a SQL Server di aggregare i risultati di più set di dati paralleli, che in caso contrario potrebbero avere schemi sconosciuti.

+ Se sei *training* invece di un modello *assegnazione dei punteggi*, questo parametro non avrà alcun effetto. A seconda del tipo di modello, la creazione di modelli potrebbe richiedere che tutte le righe vengano lette prima della creazione dei riepiloghi.

+ Per ottenere i vantaggi dell'elaborazione parallela quando si esegue il training del modello, è consigliabile usare uno dei **RevoScaleR** algoritmi. Questi algoritmi sono progettati per distribuire l'elaborazione automaticamente, anche se non si specifica <code>@parallel =1</code> nella chiamata a `sp_execute_external_script`. Per indicazioni su come ottenere le migliori prestazioni con gli algoritmi di RevoScaleR, vedere [applicazione distribuita e l'elaborazione parallela con ScaleR di Microsoft R](https://docs.microsoft.com/r-server/r/how-to-revoscaler-distributed-computing).

## <a name="create-an-r-plot-of-the-model"></a>Creare un tracciato R del modello

Molti client, tra cui SQL Server Management Studio, non sono in grado di visualizzare direttamente i tracciati creati con [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Al contrario, il processo generale per la generazione di tracciati R consiste nel creare il tracciato come parte del codice R e quindi scrivere l'immagine in un file.

In alternativa, è possibile restituire l'oggetto tracciato binario serializzato a qualsiasi applicazione che consente di visualizzare immagini.

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

+ Il `tempfile` funzione restituisce una stringa che può essere utilizzata come nome di file, ma il file non è ancora stato generato.
+ Per gli argomenti per `tempfile`, è possibile specificare un prefisso ed estensione di file, nonché la directory. Per verificare il nome file completo e il percorso, stampa un messaggio utilizzando `str()`.
+ La funzione `jpeg` crea un dispositivo R con i parametri specificati.
+ Dopo aver creato il tracciato, è possibile aggiungervi altre funzionalità visive. In questo caso, viene aggiunta una riga di regressione usando `abline`.
+ Dopo avere aggiunto tutte le funzionalità di creazione tracciato desiderate, è necessario chiudere il dispositivo grafico tramite la funzione `dev.off()`.
+ La funzione `readBin` accetta un file da leggere, una specifica di formato e il numero di record. Il `rb`* * ' (parola chiave) indica che il file è binario anziché il testo.

**Risultati**

![rsql_basictut_plotresult_small](media/rsql-basictut-plotresult-small.png)

Se si vogliono eseguire tracciati più elaborati usando alcuni dei pacchetti di grafica avanzati per R, è consigliabile leggere gli articoli seguenti. Entrambi prevedono l'uso del pacchetto **ggplot2**, ampiamente diffuso.

+ [Loan Classification using SQL Server 2016 R Services](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2016/09/27/loan-classification-using-sql-server-2016-r-services/) (Classificazione dei prestiti tramite SQL Server 2016 R Services): uno scenario end-to-end basato sui dati delle assicurazioni. Richiede la **reshape** pacchetto.
+ [Creare grafici e tracciati con R](walkthrough-create-graphs-and-plots-using-r.md)

## <a name="next-steps"></a>Passaggi successivi

L'integrazione di R con SQL Server rende più semplice distribuire soluzioni R su larga scala, sfruttando le funzionalità migliori di R e dei database relazionali, per una gestione dei dati a prestazioni elevate e un'analisi R più rapida. 

Altre informazioni sulle soluzioni R con SQL Server tramite scenari end-to-end creati dai team di sviluppo Microsoft Data Science e R Services.

> [!div class="nextstepaction"]
> [Esercitazioni di SQL Server R](sql-server-r-tutorials.md)
