---
title: Lezione 3 Esplora e visualizzare i dati | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 4be76ebbb8f082e84a00bfe93b36c9bd8c2c0a81
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="lesson-3-explore-and-visualize-the-data"></a>Lezione 3: Esplorare e visualizzare i dati
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo articolo fa parte di un'esercitazione per gli sviluppatori SQL su come usare il linguaggio R in SQL Server.

In questa lezione verranno esaminare i dati di esempio e quindi generare alcuni grafici utilizzando funzioni R. Queste funzioni R sono già inclusi [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. È possibile chiamare le funzioni di R da [!INCLUDE[tsql](../../includes/tsql-md.md)].

## <a name="review-the-data"></a>Esaminare i dati

Lo sviluppo di una soluzione di analisi scientifica dei dati prevede in genere frequenti esplorazioni e visualizzazioni dei dati. Tale scopo, è opportuno esaminare i dati di esempio, se hai già fatto.

Nel set di dati originale gli identificatori di taxi e i record delle corse si trovavano in file separati. Tuttavia, per rendere più facile da utilizzare i dati di esempio, due set di dati originale sono state unite nelle colonne di _medallion_, _hack\_licenza_, e _prelievo\_ DateTime_.  È stato eseguito anche un campionamento dei record in modo da ottenere solo l'1% del numero di record originale. Il set di dati ridotto risultante include 1.703.957 righe e 23 colonne.

**Identificatori di taxi**
  
-   La colonna _medallion_ rappresenta l'ID univoco del taxi.
  
-   Il _hack\_licenza_ colonna contiene il numero di licenza del driver taxi (resi anonime).
  
**Record delle corse e delle tariffe**
  
-   Il record di ogni corsa include il luogo e l'ora di inizio e fine della corsa e la distanza percorsa.
  
-   Il record di ogni tariffa include i dati del pagamento, ad esempio il tipo di pagamento, l'importo totale e l'importo della mancia.
  
-   Le ultime tre colonne possono essere usate per diverse attività di apprendimento automatico.  Il _suggerimento\_quantità_ colonna contiene valori numerici continui e può essere utilizzato come il **etichetta** colonna per l'analisi di regressione. La colonna _tipped_ include solo valori sì/no e viene usata per la classificazione binaria. Il _suggerimento\_classe_ colonna ha più **classe etichette** e pertanto può essere utilizzato come etichetta per le attività di classificazione multiclasse.
  
    In questa procedura dettagliata è descritta soltanto l'attività di classificazione binaria. Si consiglia di provare a creare modelli per le altre due attività di apprendimento automatico, la regressione e la classificazione multiclasse.
  
-   I valori utilizzati per le colonne di etichetta sono tutti basati sul _suggerimento\_quantità_ colonna utilizzando le regole business:
  
    |Nome colonna derivata|Rule|
    |-|-|
     |tipped|Se tip_amount > 0, tipped = 1, altrimenti tipped = 0|
    |tip_class|Classe 0: tip_amount = $0<br /><br />Classe 1: tip_amount > $0 e tip_amount <= $5<br /><br />Classe 2: tip_amount > $5 e tip_amount <= $10<br /><br />Classe 3: tip_amount > $10 e tip_amount <= $20<br /><br />Classe 4: tip_amount > $20|

## <a name="create-plots-using-r-in-t-sql"></a>Creare grafici usando R in T-SQL

Poiché la visualizzazione è uno strumento efficace per comprendere distribuzione dei dati e outlier, R offre numerosi pacchetti per la visualizzazione dei dati. La distribuzione open source standard di R include anche numerose funzioni per la creazione di istogrammi, grafici a dispersione, box plot e altri grafici di esplorazione dei dati.

R crea in genere le immagini usando un dispositivo R per l'output grafico. È possibile acquisire l'output del dispositivo e archiviare l'immagine in un tipo di dati **varbinary** per il rendering nell'applicazione oppure salvare le immagini in uno dei formati di file supportati (JPG, PDF e così via).

In questa sezione viene descritto come usare ogni tipo di output tramite le stored procedure. Il processo generale è il seguente:

- Creare una stored procedure per generare un tracciato di R come dati varbinary

- Generare il tracciato e salvarlo in un file di immagine

- Utilizzare una stored procedure per convertire i dati binari tracciato in un file JPG o PDF

### <a name="create-the-stored-procedure-plothistogram"></a>Creare la stored procedure PlotHistogram

1. Per creare il tracciato, utilizzare `rxHistogram`, una delle funzioni R avanzate disponibili in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], per tracciare un istogramma in base ai dati da un [!INCLUDE[tsql](../../includes/tsql-md.md)] query. Per semplificare la chiamata alla funzione R, racchiuderla nella stored procedure _PlotHistogram_.

    In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], aprire una nuova **Query** finestra.

2. Nel database che contiene i dati dell'esercitazione, creare la procedura utilizza l'istruzione:

    ```SQL
    CREATE PROCEDURE [dbo].[PlotHistogram]
    AS
    BEGIN
      SET NOCOUNT ON;
      DECLARE @query nvarchar(max) =  
      N'SELECT tipped FROM nyctaxi_sample'  
      EXECUTE sp_execute_external_script @language = N'R',  
                                         @script = N'  
       image_file = tempfile();  
       jpeg(filename = image_file);  
       #Plot histogram  
       rxHistogram(~tipped, data=InputDataSet, col=''lightgreen'',   
       title = ''Tip Histogram'', xlab =''Tipped or not'', ylab =''Counts'');  
       dev.off();  
       OutputDataSet <- data.frame(data=readBin(file(image_file, "rb"), what=raw(), n=1e6));  
       ',  
       @input_data_1 = @query  
       WITH RESULT SETS ((plot varbinary(max)));  
    END
    GO
    ```

    Se necessario, assicurarsi di modificare il codice per usare il nome di tabella corretto.
  
    -   La variabile `@query` definisce il testo della query (`'SELECT tipped FROM nyctaxi_sample'`) che viene passato allo script R come argomento alla variabile di input dello script `@input_data_1`.
  
    -   Lo script R è semplice: viene definita una variabile R (`image_file`) per archiviare l'immagine e viene quindi chiamata la funzione `rxHistogram` per la creazione del grafico.
  
    -   Il dispositivo R viene impostato su **off**.
  
        In R, quando viene eseguito un comando di tracciamento di livello elevato, viene aperta una finestra grafica chiamata *dispositivo*. È possibile modificare le dimensioni, i colori e altre caratteristiche della finestra oppure spegnere il dispositivo se è in corso una scrittura su file o l'output viene gestito in altro modo.
  
    -   L'oggetto grafico R viene serializzato in un data.frame R per l'output.

### <a name="generate-the-graphics-data-and-save-to-file"></a>Generare i dati del grafico e salvare in file

La stored procedure restituisce l'immagine come un flusso di dati varbinary, che ovviamente non è possibile visualizzare direttamente. Tuttavia, è possibile usare l'utilità **bcp** utilità per ottenere i dati varbinary e salvarli come file di immagine in un computer client.
  
1.  In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]eseguire l'istruzione seguente:
  
    ```SQL
    EXEC [dbo].[PlotHistogram]
    ```
  
    **Risultati**
    
    *plot*
    *0xFFD8FFE000104A4649...*
  
2.  Aprire un prompt dei comandi di PowerShell ed eseguire il comando seguente specificando il nome dell'istanza appropriata, il nome del database, il nome utente e le credenziali come argomenti:
  
     ```
     bcp "exec PlotHistogram" queryout "plot.jpg" -S <SQL Server instance name> -d  <database name>  -U <user name> -P <password>
     ```

    > [!NOTE]
    > Opzioni di comando per bcp maiuscole e minuscole.
  
3.  Se la connessione viene stabilita, verrà richiesto di immettere altre informazioni sul formato di file grafico. Premere INVIO a ogni richiesta per accettare le impostazioni predefinite, ad eccezione di quanto segue:
  
    -   Per **prefix-length of field plot**digitare 0
  
    -   Digitare **Y** per salvare i parametri di output e riutilizzarli in seguito.
  
    ```
    Enter the file storage type of field plot [varbinary(max)]:
    Enter prefix-length of field plot [8]: 0
    Enter length of field plot [0]:
    Enter field terminator [none]:
  
    Do you want to save this format information in a file? [Y/n]
    Host filename [bcp.fmt]:
    ```
  
    **Risultati**
    
    ```
    Starting copy...
    1 rows copied.
    Network packet size (bytes): 4096
    Clock Time (ms.) Total     : 3922   Average : (0.25 rows per sec.)
    ```

    > [!TIP]
    > Se si salvano le informazioni di formato su file (bcp.fmt), l'utilità **bcp** genera una definizione di formato che è possibile applicare a comandi simili in futuro senza specificare le opzioni di formato di file grafico. Per usare il file di formato, aggiungere `-f bcp.fmt` alla fine di qualsiasi riga di comando, dopo l'argomento password.
  
4.  Il file di output verrà creato nella stessa directory in cui è stato eseguito il comando di PowerShell. Per visualizzare il grafico, è sufficiente aprire il file plot.jpg.
  
    ![Corse di taxi con e senza mancia](media/rsql-devtut-tippedornot.jpg "Corse di taxi con e senza mancia")  
  
### <a name="export-the-plot-data-to-a-viewable-file"></a>Esportare i dati di traccia in un file visualizzabile

L'output di un tracciato di R a un dato binario tipo potrebbe essere utile per l'utilizzo dalle applicazioni, ma non è molto utile un esperto di dati che necessita il tracciato di rendering durante la fase di esplorazione dei dati. L'analista dei dati genera solitamente più visualizzazioni dei dati per ottenere informazioni dettagliate sui dati da prospettive diverse.

Per generare grafici per gli utenti, è possibile utilizzare una stored procedure che crea l'output di R in formati più diffusi, ad esempio. JPG. PDF, e. PNG. Dopo che la stored procedure ha creato il grafico, è sufficiente aprire il file per visualizzare il grafico.

1. Creare una nuova stored procedure, _PlotInOutputFiles_, che viene illustrato come scrivere istogrammi, scatterplots e altri elementi grafici R a. JPG e. Formato PDF.

    In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], aprire una nuova **Query** finestra e incollare quanto segue [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione.
  
    ```SQL
    CREATE PROCEDURE [dbo].[PlotInOutputFiles]  
    AS  
    BEGIN  
      SET NOCOUNT ON;  
      DECLARE @query nvarchar(max) =  
      N'SELECT cast(tipped as int) as tipped, tip_amount, fare_amount FROM [dbo].[nyctaxi_sample]'  
      EXECUTE sp_execute_external_script @language = N'R',  
      @script = N'  
       # Set output directory for files and check for existing files with same names   
        mainDir <- ''C:\\temp\\plots''  
        dir.create(mainDir, recursive = TRUE, showWarnings = FALSE)  
        setwd(mainDir);  
        print("Creating output plot files:", quote=FALSE)
        
        # Open a jpeg file and output histogram of tipped variable in that file.  
        dest_filename = tempfile(pattern = ''rHistogram_Tipped_'', tmpdir = mainDir)  
        dest_filename = paste(dest_filename, ''.jpg'',sep="")  
        print(dest_filename, quote=FALSE);  
        jpeg(filename=dest_filename);  
        hist(InputDataSet$tipped, col = ''lightgreen'', xlab=''Tipped'',   
            ylab = ''Counts'', main = ''Histogram, Tipped'');  
         dev.off();  

        # Open a pdf file and output histograms of tip amount and fare amount.   
        # Outputs two plots in one row  
        dest_filename = tempfile(pattern = ''rHistograms_Tip_and_Fare_Amount_'', tmpdir = mainDir)  
        dest_filename = paste(dest_filename, ''.pdf'',sep="")  
        print(dest_filename, quote=FALSE);  
        pdf(file=dest_filename, height=4, width=7);  
        par(mfrow=c(1,2));  
        hist(InputDataSet$tip_amount, col = ''lightgreen'',   
            xlab=''Tip amount ($)'',   
            ylab = ''Counts'',   
            main = ''Histogram, Tip amount'', xlim = c(0,40), 100);  
        hist(InputDataSet$fare_amount, col = ''lightgreen'',   
            xlab=''Fare amount ($)'',   
            ylab = ''Counts'',   
            main = ''Histogram,   
            Fare amount'',   
            xlim = c(0,100), 100);  
       dev.off();  
  
        # Open a pdf file and output an xyplot of tip amount vs. fare amount using lattice;  
        # Only 10,000 sampled observations are plotted here, otherwise file is large.  
        dest_filename = tempfile(pattern = ''rXYPlots_Tip_vs_Fare_Amount_'', tmpdir = mainDir)  
        dest_filename = paste(dest_filename, ''.pdf'',sep="")  
        print(dest_filename, quote=FALSE);  
        pdf(file=dest_filename, height=4, width=4);  
        plot(tip_amount ~ fare_amount,   
            data = InputDataSet[sample(nrow(InputDataSet), 10000), ],   
            ylim = c(0,50),   
            xlim = c(0,150),   
            cex=.5,   
            pch=19,   
            col=''darkgreen'',    
            main = ''Tip amount by Fare amount'',   
            xlab=''Fare Amount ($)'',   
            ylab = ''Tip Amount ($)'');   
        dev.off();',  
     @input_data_1 = @query  
     END
    ```
  
    -   L'output della query SELECT all'interno della stored procedure viene archiviato nel frame di dati R predefinito `InputDataSet`. Sarà quindi possibile chiamare diverse funzioni di creazione dei grafici R per generare i file grafici.
  
        La maggior parte degli script R incorporati rappresenta le opzioni di queste funzioni di grafici,  ad esempio `plot` o `hist`.
  
    -   Tutti i file vengono salvati nella cartella locale _C:\temp\Plots\\_. La cartella di destinazione è definita dagli argomenti specificati nello script R come parte della stored procedure.  È possibile modificare la cartella di destinazione modificando il valore della variabile `mainDir`.
  
2.  Eseguire l'istruzione per creare la stored procedure.

    ```SQL
    EXEC PlotInOutputFiles
    ```

    **Risultati**
    
    ```
    STDOUT message(s) from external script:
    [1] Creating output plot files:[1] C:\temp\plots\rHistogram_Tipped_18887f6265d4.jpg[1] 
    
    C:\temp\plots\rHistograms_Tip_and_Fare_Amount_1888441e542c.pdf[1]
    
    C:\temp\plots\rXYPlots_Tip_vs_Fare_Amount_18887c9d517b.pdf
    ```

    I numeri nei nomi dei file vengono generati in modo casuale per garantire che non si ottiene un errore durante il tentativo di scrivere in un file esistente.

3. Per visualizzare il tracciato, aprire la cartella di destinazione ed esaminare i file creati dal codice R nella stored procedure.

    + Il file `rHistogram_Tipped.jpg` Mostra il numero di percorsi che ha ricevuto un suggerimento e trip che ha ricevuto alcuna descrizione. (Questo istogramma è molto simile a quello generato nel passaggio precedente).

    + Il file `rHistograms_Tip_and_Fare_Amount.pdf` Mostra la distribuzione degli importi di suggerimento, tracciata rispetto alle quantità fare.
    
    ![istogramma che mostra tip_amount e fare_amount](media/rsql-devtut-tipamtfareamt.PNG "istogramma che mostra tip_amount e fare_amount")

    + Il file `rXYPlots_Tip_vs_Fare_Amount.pdf` contiene un scatterplot con la quantità di tariffa sull'asse x e la quantità di suggerimento sull'asse y.

    ![quantità di suggerimento tracciate nel quantità tariffa](media/rsql-devtut-tipamtbyfareamt.PNG "quantità suggerimento tracciate nel quantità tariffa")

2.  Per inviare i file in una cartella diversa, modificare il valore della variabile `mainDir` nello script R incorporato nella stored procedure. È anche possibile modificare lo script per produrre l'output in formati diversi, in più file e così via.

## <a name="next-lesson"></a>Lezione successiva

[Lezione 4: Creare funzionalità di dati con T-SQL](../tutorials/sqldev-create-data-features-using-t-sql.md)

## <a name="previous-lesson"></a>Lezione precedente

[Lezione 2: Importare dati in SQL Server tramite PowerShell](../r/sqldev-import-data-to-sql-server-using-powershell.md)
