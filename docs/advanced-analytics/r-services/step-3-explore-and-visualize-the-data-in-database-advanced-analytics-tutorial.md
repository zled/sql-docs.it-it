---
title: "Passaggio 3: Esplorare e visualizzare i dati (Esercitazione di analisi avanzata nel database) | Microsoft Docs"
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
ms.assetid: 7fe670f3-5e62-43ef-97eb-b9af54df9128
caps.latest.revision: 11
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 11
---
# Passaggio 3: Esplorare e visualizzare i dati (Esercitazione di analisi avanzata nel database)
Lo sviluppo di una soluzione di analisi scientifica dei dati prevede in genere frequenti esplorazioni e visualizzazioni dei dati. In questo passaggio verranno esaminati i dati di esempio e quindi generati alcuni tracciati usando funzioni R. Le funzioni R sono incluse in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. In questa procedura dettagliata verranno eseguite diverse chiamate alle funzioni R da [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## Rivedere i dati  
In primo luogo, è opportuno esaminare i dati di esempio, se non è già stato fatto.  
  
Nel set di dati originale gli identificatori di taxi e i record delle corse si trovavano in file separati. Tuttavia, per semplificare l'utilizzo dei dati di esempio, i due set di dati originali sono stati uniti nelle colonne _medallion_, _hack_license_ e _pickup_datetime_.  È stato eseguito anche un campionamento dei record in modo da ottenere solo l'1% del numero di record originale. Il set di dati ridotto risultante include 1.703.957 righe e 23 colonne.  
  
**Identificatori di taxi**  
  
-   La colonna _medallion_ rappresenta l'ID univoco del taxi.  
  
-   La colonna _hack_license_ contiene il numero di patente del tassista (in forma anonima) .  
  
**Record delle corse e delle tariffe**  
  
-   Il record di ogni corsa include il luogo e l'ora di inizio e fine della corsa e la distanza percorsa.  
  
-   Il record di ogni tariffa include i dati del pagamento, ad esempio il tipo di pagamento, l'importo totale e l'importo della mancia.  
  
-   Le ultime tre colonne possono essere usate per diverse attività di apprendimento automatico.  La colonna _tip_amount_ contiene valori numerici continui e può essere usata come colonna **label** per l'analisi della regressione. La colonna _tipped_ include solo valori sì/no e viene usata per la classificazione binaria. La colonna _tip_class_ include più **etichette di classe** e può essere quindi usata come etichetta per le attività di classificazione multiclasse.  
  
    In questa procedura dettagliata è descritta soltanto l'attività di classificazione binaria. Si consiglia di provare a creare modelli per le altre due attività di apprendimento automatico, la regressione e la classificazione multiclasse.  
  
-   I valori usati per le colonne etichetta sono basati sulla colonna _tip_amount_ usando le regole di business seguenti:  
  
    |Nome colonna derivata|Rule|  
    |-|-|  
     |tipped|Se tip_amount > 0, tipped = 1, altrimenti tipped = 0|  
    |tip_class|Classe 0: tip_amount = $0<br /><br />Classe 1: tip_amount > $0 e tip_amount <= $5<br /><br />Classe 2: tip_amount > $5 e tip_amount <= $10<br /><br />Classe 3: tip_amount > $10 e tip_amount <= $20<br /><br />Classe 4: tip_amount > $20|  
  
## Creare grafici usando R in T-SQL  
Poiché la visualizzazione è uno strumento efficace per comprendere distribuzione dei dati e outlier, R offre numerosi pacchetti per la visualizzazione dei dati. La distribuzione open source standard di R include anche numerose funzioni per la creazione di istogrammi, grafici a dispersione, box plot e altri grafici di esplorazione dei dati.  
  
R crea in genere le immagini usando un dispositivo R per l'output grafico. È possibile acquisire l'output del dispositivo e archiviare l'immagine in un tipo di dati **varbinary** per il rendering nell'applicazione oppure salvare le immagini in uno dei formati di file supportati (JPG, PDF e così via).  
  
In questa sezione viene descritto come usare ogni tipo di output tramite le stored procedure.  
  
-   Archiviazione dei grafici come tipo di dati varbinary  
  
-   Salvataggio dei grafici in file (JPG, PDF) sul server  
  
### Archiviazione dei grafici come tipo di dati varbinary  
Verrà usata `rxHistogram`, una delle funzioni R avanzate incluse in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], per tracciare un istogramma basato sui dati di una query [!INCLUDE[tsql](../../includes/tsql-md.md)]. Per semplificare la chiamata alla funzione R, racchiuderla nella stored procedure _PlotHistogram_.  
  
La stored procedure restituisce l'immagine come un flusso di dati varbinary, che ovviamente non è possibile visualizzare direttamente. Tuttavia, è possibile usare l'utilità **bcp** utilità per ottenere i dati varbinary e salvarli come file di immagine in un computer client.  
  
##### Per creare la stored procedure PlotHistogram  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] aprire una nuova finestra di query.  
  
2.  Selezionare il database per la procedura dettagliata e creare la stored procedure usando l'istruzione seguente.  
  
    ```  
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
  
    -   L'oggetto grafico R viene serializzato in un data.frame R per l'output. Si tratta di una soluzione temporanea per CTP3.  
  
##### Per restituire i dati varbinary in un file grafico visualizzabile  
  
1.  In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] eseguire l'istruzione seguente:  
  
    ```  
    EXEC [dbo].[PlotHistogram]  
    ```  
  
**Risultati**  
  
*grafico*  
*0xFFD8FFE000104A4649...*  
  
2.  Aprire un prompt dei comandi di PowerShell ed eseguire il comando seguente specificando il nome dell'istanza appropriata, il nome del database, il nome utente e le credenziali come argomenti:  
  
    ```  
    bcp "exec PlotHistogram" queryout "plot.jpg" -S <SQL Server instance name> -d  <database name>  -U <user name> -P <password>  
  
    ```  
  
    > [!NOTE]  
    > Nelle opzioni di comando per **bcp** viene fatta distinzione tra maiuscole e minuscole.  
  
3.  Se la connessione viene stabilita, verrà richiesto di immettere altre informazioni sul formato di file grafico. Premere INVIO a ogni richiesta per accettare le impostazioni predefinite, ad eccezione di quanto segue:  
  
    -   Per **prefix-length of field plot** digitare 0  
  
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
  
*Avvio della copia...*  
*1 righe copiate.*  
*Dimensioni pacchetto di rete (byte): 4096*  
*Tempo di clock (ms.) Totale     : 3922   Media: (0.25 righe/sec.)*  
   
> [!TIP]  
 > Se si salvano le informazioni di formato su file (bcp.fmt), l'utilità **bcp** genera una definizione di formato che è possibile applicare a comandi simili in futuro senza specificare le opzioni di formato di file grafico. Per usare il file di formato, aggiungere `-f bcp.fmt` alla fine di qualsiasi riga di comando, dopo l'argomento password.  
  
4.  Il file di output verrà creato nella stessa directory in cui è stato eseguito il comando di PowerShell. Per visualizzare il grafico, è sufficiente aprire il file plot.jpg.  
  
    ![taxi trips with and without tips](../../advanced-analytics/r-services/media/rsql-devtut-tippedornot.jpg "taxi trips with and without tips")  
  
### Salvataggio dei grafici in file (jpg, pdf) sul server  
L'invio dell'output di un grafico R a un tipo di dati binario può risultare efficace in termini di consumo da parte delle applicazioni, ma non è molto utile per un analista dei dati che necessita di un grafico visualizzabile durante la fase di esplorazione dei dati. L'analista dei dati genera solitamente più visualizzazioni dei dati per ottenere informazioni dettagliate sui dati da prospettive diverse.  
  
Per creare grafici facili da visualizzare, è possibile usare una stored procedure che crea l'output di R in formati comuni, ad esempio JPG, PDF e PNG. Dopo che la stored procedure ha creato il grafico, è sufficiente aprire il file per visualizzare il grafico.  
  
In questo passaggio viene creata una nuova stored procedure, _PlotInOutputFiles_, che illustra come usare le funzioni di creazione di grafici R per creare istogrammi, grafici a dispersione e altri tipi di grafici in formato JPG e PDF. I file grafici vengono salvati in file locali, ovvero in una cartella nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
##### Per creare la stored procedure PlotInOutputFiles  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] aprire una nuova finestra di query e incollare l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] seguente.  
  
    ```  
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
  
    -   Tutti i file vengono salvati nella cartella locale _C:\temp\Plots\\_.  
  
        La cartella di destinazione è definita dagli argomenti specificati nello script R come parte della stored procedure.  È possibile modificare la cartella di destinazione modificando il valore della variabile `mainDir`.  
  
2.  Eseguire l'istruzione per creare la stored procedure.  
  
  
##### Per generare i file grafici  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] eseguire la query SQL seguente:  
  
    ```  
    EXEC PlotInOutputFiles  
  
    ```  
  
**Risultati**  
  
*Messaggi STDOUT dallo script esterno:*  
*[1] Creazione dei file dei grafici di output:[1]* *C:\\\temp\\\plots\\\rHistogram_Tipped_18887f6265d4.jpg[1]* *C:\\\temp\\\plots\\\rHistograms_Tip_and_Fare_Amount_1888441e542c.pdf[1]* *C:\\\temp\\\plots\\\rXYPlots_Tip_vs_Fare_Amount_18887c9d517b.pdf*  
  
2.  Aprire la cartella di destinazione ed esaminare i file creati dal codice R nella stored procedure. (I numeri nei nomi dei file sono generati in modo casuale).  
  
*  rHistogram_Tipped_*nnnn*.jpg: mostra il numero di corse per le quali è stata (1) e non è stata ricevuta una mancia (0). L'istogramma è simile a quello creato nel passaggio precedente.  
  
*  rHistograms_Tip_and_Fare_Amount_*nnnn*.pdf: mostra la distribuzione dei valori nelle colonne tip_amount e fare_amount.  
  
        ![histogram showing tip_amount and fare_amount](../../advanced-analytics/r-services/media/rsql-devtut-tipamtfareamt.PNG "histogram showing tip_amount and fare_amount")  
  
*  rXYPlots_Tip_vs_Fare_Amount_*nnnn*.pdf: grafico a dispersione con l'importo della tariffa sull'asse x e l'importo della mancia sull'asse y.  
  
        ![tip amount plotted over fare amount](../../advanced-analytics/r-services/media/rsql-devtut-tipamtbyfareamt.PNG "tip amount plotted over fare amount")  
  
3.  Per inviare i file in una cartella diversa, modificare il valore della variabile `mainDir` nello script R incorporato nella stored procedure.  
  
    È anche possibile modificare lo script per produrre l'output in formati diversi, in più file e così via.  
  
## Passaggio successivo  
[Passaggio 4: Creare funzionalità di dati mediante T-SQL](../../advanced-analytics/r-services/step-4-create-data-features-using-t-sql-in-database-advanced-analytics-tutorial.md)  
  
## Passaggio precedente  
[Passaggio 2: Importare i dati in SQL Server usando PowerShell](../../advanced-analytics/r-services/step-2-import-data-to-sql-server-using-powershell.md)  
  
## Vedere anche  
[Analisi avanzata nel database per sviluppatori SQL &#40;Esercitazione&#41;](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)  
[Esercitazioni di SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
  
  
  
