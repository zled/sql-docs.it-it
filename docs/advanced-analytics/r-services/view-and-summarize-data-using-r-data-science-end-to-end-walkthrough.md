---
title: "Visualizzare e riepilogare i dati tramite R (Procedura dettagliata end-to-end per l&#39;analisi scientifica dei dati) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/14/2017"
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
ms.assetid: 358e1431-8f47-4d32-a02f-f90e519eef49
caps.latest.revision: 21
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# Visualizzare e riepilogare i dati tramite R (Procedura dettagliata end-to-end per l&#39;analisi scientifica dei dati)
Si useranno ora gli stessi dati con il codice R. Verrà anche illustrato l'uso delle funzioni nel pacchetto **RevoScaleR** incluso con [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] che consente di generare riepiloghi di dati nel contesto del server [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e restituire i risultati all'ambiente R.  

In questa procedura dettagliata, oltre a tutti i codici necessari per creare gli oggetti dati, generare riepiloghi e creare modelli, è incluso uno script R. Il file di script R **RSQL_RWalkthrough.R**è disponibile nel percorso in cui sono stati installati i file di script.  
+ Se si ha familiarità con R, è possibile eseguire lo script in una sola volta.
+ Per imparare a usare RevoScaleR, questa esercitazione illustra lo script riga per riga.
+ Per eseguire singole righe dello script, è possibile evidenziare una o più righe nel file e premere CTRL + INVIO.    
  
> [!TIP]  Salvare l'area di lavoro R nel caso in cui si voglia completare il resto della procedura dettagliata in un secondo momento.  In questo modo gli oggetti dati e le altre variabili rimarranno disponibili per essere riusati.   

## <a name="defining-sql-server-data-sources-and-compute-contexts"></a>Definizione delle origini dei dati e dei contesti di calcolo di SQL Server
Per ottenere dati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da usare nel codice R, è necessario:  
  
- Creare una connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
- Definire una query che contiene i dati necessari oppure specificare una tabella o una vista    
- Definire uno o più contesti di calcolo da usare durante l'esecuzione del codice R    
-   Facoltativamente, definire le funzioni che possono essere applicate all'origine dati  
 

### <a name="load-the-revoscaler-library"></a>Caricare la libreria RevoScaleR

+  Se il pacchetto **RevoScaleR** non è già caricato, eseguire:
    ```R
    library("RevoScaleR")`.  
    ```  
    In caso di errore, assicurarsi che l'ambiente di sviluppo R usi la libreria che include il pacchetto RevoScaleR. Usare un comando come `.libPaths())` per visualizzare il percorso corrente:  

    Se si usa il pacchetto **RevoScaleR** per la prima volta, digitare `help("RevoScaleR")` o `help("RxSqlServerData")` per aprire la Guida nell'ambiente R.  

### <a name="create-connection-strings"></a>Creare stringhe di connessione


1. Definire stringhe di connessione. Per questa procedura dettagliata, sono stati forniti esempi di account di accesso SQL e dell'autenticazione integrata di Windows. È consigliabile usare l'autenticazione di Windows laddove possibile per evitare di salvare le password nel codice R.

    L'account usato deve avere le autorizzazioni per leggere i dati e per creare nuove tabelle nel database specificato. Per informazioni su come aggiungere utenti al database SQL e concedere loro le autorizzazioni corrette, vedere la [pagina relativa alla configurazione del server successiva all'installazione&#40;SQL Server R Services&#41;](../Topic/Post-Installation%20Server%20Configuration%20(SQL%20Server%20R%20Services).md). 

    ```R  
    # SQL authentication  
    connStrSql <- "Driver=SQL Server;Server=<SQL_instance_name>;Database=<database_name>;    Uid=<user_name>;Pwd=<user password>"  

    # Windows authentication  
    connStrWin <- "Driver=SQL Server;Server=<SQL_instance_name>;Database=<database_name>;Trusted_Connection=Yes" 
    
    # Use one of the connection strings
    connStr <- connStrWin 
    ```
    > [!NOTE] Assicurarsi di modificare, se necessario, il nome del server, il nome del database, il nome utente e la password. 
      
  
### <a name="define-and-set-a-compute-context"></a>Definire e impostare un contesto di calcolo  

Verrà definito un *calcolo contesto* che consente di eseguire il codice R nel computer SQL Server. In genere, quando si usa R, tutte le operazioni vengono eseguite nella memoria del computer. Tuttavia, se si indica di voler eseguire le operazioni R nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è possibile eseguire alcune attività in parallelo e sfruttare le risorse del server.  

Per impostazione predefinita, il contesto di calcolo è locale, pertanto è necessario impostare in modo esplicito il contesto di calcolo, a seconda dell'operazione.  


1.  Per prima cosa definire alcune variabili usate per creare il contesto di calcolo.  
  
    ```R    
    sqlShareDir <- paste("C:\\AllShare\\",Sys.getenv("USERNAME"),sep="")  
    sqlWait <- TRUE  
    sqlConsoleOutput <- FALSE    
    ```    
    -   R usa una directory temporanea per la serializzazione degli oggetti R tra la workstation e il computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. È possibile specificare la directory locale che viene usata come *sqlShareDir* o accettare quella predefinita.  
  
    -   Usare *sqlWait* per indicare se si vuole che R attenda o meno i risultati.  Per una descrizione dei processi in attesa e non in attesa, vedere l'articolo relativo al [calcolo distribuito ScaleR](https://msdn.microsoft.com/microsoft-r/scaler-distributed-computing).
  
    -   Usare l'argomento *sqlConsoleOutput* per indicare che non si vuole visualizzare l'output dalla console R.  
  
2.  Creare l'oggetto contesto di calcolo con le variabili e le stringhe di connessione già definite e salvarlo nella variabile R *sqlcc*.  
  
    ```  
    sqlcc <- RxInSqlServer(connectionString = connStr, shareDir = sqlShareDir,   
                        wait = sqlWait, consoleOutput = sqlConsoleOutput)  
    ```  

4. Impostare il contesto di calcolo.
    ```R
    rxSetComputeContext(sqlcc)  
    ```  
   + `rxSetComputeContext` restituisce il contesto di calcolo precedentemente attivo in modo invisibile in modo che sia possibile usarlo
   + `rxGetComputeContext` restituisce il contesto di calcolo attivo  
  
    L'impostazione di un contesto di calcolo ha effetto solo alle operazioni che usano le funzioni nel pacchetto **RevoScaleR**. Il contesto di calcolo non ha alcun effetto sul modo in cui vengono eseguite le operazioni R open source.  
  
### <a name="create-an-rxsqlserver-data-object"></a>Creare un oggetto dati RxSqlServer  

Dopo avere definito la connessione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da usare, è possibile impiegare tale oggetto connessione dati come base per definire altre origini dati. Un'*origine dati* specifica i set dati che si vuole usare per un'attività, come ad esempio il training, l'esplorazione, l'assegnazione di punteggi e la generazione di funzionalità.  
    
Per definire set di dati di SQL Server, usare la funzione *RxSqlServer* e passare una stringa di connessione e la definizione dei dati da recuperare.  
  
1. Salvare l'istruzione SQL come una variabile di stringa. Questa query definisce i dati da usare per il training del modello.    
    ```R
    sampleDataQuery <- "SELECT TOP 1000 tipped, fare_amount, 
           passenger_count,trip_time_in_secs,trip_distance,   
           pickup_datetime, dropoff_datetime, pickup_longitude, 
           pickup_latitude, dropoff_longitude,    
           dropoff_latitude 
           FROM nyctaxi_sample"  
    ```

2. Passare la definizione della query come argomento all'origine dati SQL Server. L'argomento *colClasses* specifica lo schema dei dati da restituire, eseguendo il mapping di SQL 

    ```R  
    inDataSource <- RxSqlServerData(sqlQuery = sampleDataQuery, 
         connectionString = connStr,
         colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric",
         dropoff_longitude = "numeric", dropoff_latitude = "numeric"),  
         rowsPerRead=500)  
    ```
    
    + L'argomento *colClasses* specifica i tipi di colonna da usare durante lo spostamento dei dati tra [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e R. Questo aspetto è importante perché [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usa tipi di dati diversi rispetto a R e più tipi di dati. Per altre informazioni, vedere [Uso dei tipi di dati di R](../../advanced-analytics/r-services/working-with-r-data-types.md).  
  
    + L'argomento *rowsPerRead* è importante per la gestione dell'utilizzo della memoria e per calcoli ottimizzati.  La maggior parte delle funzioni analitiche avanzate in[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] elabora i dati in blocchi e raggruppa risultati intermedi, restituendo i calcoli finali dopo che tutti i dati sono stati letti.  Aggiungendo il parametro `rowsPerRead` , è possibile controllare il numero di righe di dati lette in ogni blocco da elaborare.  Se il valore di questo parametro è troppo alto, l'accesso ai dati potrebbe risultare lento perché la memoria disponibile non è sufficiente a elaborare in modo efficiente un blocco troppo grande di dati.  In alcuni sistemi, se il parametro `rowsPerRead` viene impostato su valore troppo basso, è possibile assistere a una riduzione delle prestazioni.  

> [!TIP] Dopo aver creato l'oggetto *inDataSource*, è possibile ricorrere a tale oggetto ogni volta in cui è necessario, ad esempio per ottenere informazioni di base sui dati e sulle variabili usati, per manipolare e per trasformare i dati. È anche possibile usare questo oggetto per il training di un modello.  Tuttavia, l'oggetto *inDataSource* di per sé non contiene ancora i dati dalla query SQL. I dati non vengono spostati nell'ambiente locale finché non si esegue una funzione come ad esempio *rxImport* o *rxSummary*.          
  
## <a name="using-the-sql-server-data-in-r"></a>Uso dei dati SQL Server in R  
A questo punto è possibile applicare le funzioni R all'origine dati per esplorare, riepilogare e classificare i dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . In questa sezione saranno trattate alcune delle funzioni disponibili in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] a supporto dei contesti di calcolo remoti.  
  
-   `rxGetVarInfo`: usare questa funzione con un qualsiasi frame di dati o set di dati in un oggetto dati remoto, e anche con alcuni elenchi e matrici, per ottenere informazioni, ad esempio i valori minimo e massimo, il tipo di dati e il numero di livelli nelle colonne fattore.  
  
    È consigliabile eseguire questa funzione dopo qualsiasi tipo di input dei dati, dopo la trasformazione o la progettazione di una funzionalità. In questo modo è possibile garantire che tutte le funzionalità che si vogliono usare nel modello siano del tipo di dati previsto, evitando così errori.  
 
  
-   `rxSummary`: usare questa funzione per ottenere statistiche più dettagliate sulle singole variabili. È anche possibile trasformare i valori, calcolare i valori di riepilogo usando livelli di fattore e salvare i riepiloghi per usarli in un altro momento.  
  
  
### <a name="inspect-variables-in-the-data-source"></a>Verificare le variabili nell'origine dei dati  
    
+ Chiamare la funzione `rxGetVarInfo`usando l'origine dati  `inDataSource` come argomento per ottenere un elenco delle variabili dell'origine dati e i relativi tipi di dati.  
  
    ```R  
    rxGetVarInfo(data = inDataSource)  
    ```  
  
    *Risultati:*  
    *Var 1: tipped, Type: integer*  
    *Var 2: fare_amount, Type: numeric*  
    *Var 3: passenger_count, Type: integer*  
    *Var 4: trip_time_in_secs, Type: numeric, Storage: int64*  
    *Var 5: trip_distance, Type: numeric*  
    *Var 6: pickup_datetime, Type: character*  
    *Var 7: dropoff_datetime, Type: character*  
    *Var 8: pickup_longitude, Type: numeric*  
    *Var 9: pickup_latitude, Type: numeric*  
    *Var 10: dropoff_longitude, Type: numeric*  
  
### <a name="create-a-summary-using-r"></a>Creare un riepilogo con R

+ Chiamare la funzione RevoScaleR `rxSummary` per riepilogare l'importo della tariffa in base al numero dei passeggeri. 
    ```R  
    start.time <- proc.time()  
    rxSummary(~fare_amount:F(passenger_count), data = inDataSource)  
    used.time <- proc.time() - start.time  
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds,
      Elapsed Time=", round(used.time[3],2), 
      " seconds to summarize the inDataSource.", sep=""))
    ```  
 
    + Il primo argomento di `rxSummary` specifica la formula o il termine in base al quale eseguire il riepilogo. In questo esempio la funzione `F()` viene usata per convertire i valori di passenger_count in fattori prima di eseguire il riepilogo.  
    + Se non si specificano le statistiche per l'output, per impostazione predefinita `rxSummary` genera i valori Mean, StDev, Min, Max, il numero di osservazioni valide e mancanti.  
    + Questo esempio include anche una parte di codice per tenere traccia dell'ora in cui la funzione ha inizio e termina in modo da poter confrontare le prestazioni.  
  
    *Risultati*  
    *rxSummary(formula = ~fare_amount:F(passenger_count), data = inDataSource)*  
    *Summary Statistics Results for: ~fare_amount:F(passenger_count)*  
    *Data: inDataSource (RxSqlServerData Data Source)*  
    *Number of valid observations: 1000*   
    *Name                          Mean    StdDev   Min Max ValidObs MissingObs*  
    *fare_amount:F_passenger_count 12.4875 9.682605 2.5 64  1000     0*   
    *Statistiche per categoria (6 categorie):   *Category                             F_passenger_count Means    StdDev    Min*   
    *fare_amount for F(passenger_count)=1 1                 12.00901  9.219458  2.5*  
    *fare_amount for F(passenger_count)=2 2                 11.61893  8.858739  3.0*  
    *fare_amount for F(passenger_count)=3 3                 14.40196 10.673340  3.5*  
    *fare_amount for F(passenger_count)=4 4                 13.69048  8.647942  4.5*  
    *fare_amount for F(passenger_count)=5 5                 19.30909 14.122969  3.5*  
    *fare_amount for F(passenger_count)=6 6                 12.00000        NA 12.0*  
    *Max ValidObs*  
    *55  666*   
    *52  206*   
    *52   51*   
    *39   21*   
    *64   55*   
    *12    1*   
    *"It takes CPU Time=0.5 seconds, Elapsed Time=4.59 seconds to summarize the inDataSource."*  
  

  
## <a name="next-step"></a>Passaggio successivo  
[Creare grafici e tracciati con R &#40;procedura dettagliata end-to-end per l'analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/create-graphs-and-plots-using-r-data-science-end-to-end-walkthrough.md)  
  
## <a name="previous-lesson"></a>Lezione precedente  
[Lezione 1: Preparare i dati &#40;Procedura dettagliata end-to-end per l'analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/lesson-1-prepare-the-data-data-science-end-to-end-walkthrough.md)  
  
  
  
