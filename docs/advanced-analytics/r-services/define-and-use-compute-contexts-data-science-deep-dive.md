---
title: "Definire e usare i contesti di calcolo (procedura approfondita per l&#39;analisi scientifica dei dati) | Microsoft Docs"
ms.custom: ""
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
ms.assetid: b13058d0-9c6a-44e1-849b-72189d9050ba
caps.latest.revision: 17
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# Definire e usare i contesti di calcolo (procedura approfondita per l&#39;analisi scientifica dei dati)
Si è deciso che alcuni dei calcoli più complessi verranno eseguiti sul server anziché nel computer locale. A tale scopo, è necessario creare un contesto di calcolo che consenta di eseguire codice R nel server.  
  
La funzione [RxInSqlServer](https://msdn.microsoft.com/microsoft-r/scaler/rxinsqlserver) è una delle funzioni R avanzate disponibili nel pacchetto [RevoScaleR](https://msdn.microsoft.com/microsoft-r/scaler/scaler). La funzione gestisce le attività di creazione della connessione di database e del passaggio di oggetti tra il computer locale e il contesto di esecuzione remoto.  
  
In questo passaggio verrà illustrato come usare la funzione *RxInSqlServer* per definire un contesto di calcolo nel codice R.  


  
## Creare e impostare un contesto di calcolo  
Per creare un contesto di calcolo sono necessarie le informazioni di base seguenti relative all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   La stringa di connessione per l'istanza  
-   Una specifica per la modalità di gestione dell'output  
-   Argomenti facoltativi per abilitare la traccia o specificare una directory condivisa


 È ora possibile iniziare.

1.  Specificare la stringa di connessione per l'istanza in cui verranno eseguiti i calcoli.  Questa è una delle diverse variabili che verranno passate alla funzione *RxInSqlServer* per creare il contesto di calcolo. 

    **Uso di un account di accesso SQL**

      ```R
      sqlConnString <- "Driver=SQL Server;Server=<SQL Server instance name>; Database=<database name>;Uid=<SQL user name>;Pwd=<password>" 
      ```

    **Uso dell'autenticazione di Windows integrata**

      ```R
      sqlConnString <- "Driver=SQL Server;Server=instance_name;Database=DeepDive;Trusted_Connection=True"" 
      ```
2.  Specificare il modo in cui si vuole gestire l'output. Nel codice seguente viene indicato che la sessione di R nella workstation deve sempre attendere i risultati del processo R e non restituire l'output della console dei calcoli remoti.  
  
    ```R  
    sqlWait <- TRUE   
    sqlConsoleOutput <- FALSE   
    ```  
  
    L'argomento *wait* per *RxInSqlServer* supporta queste opzioni:  
  
    -   **TRUE**. Il processo sarà in modalità di blocco e restituisce risultati finché non viene completato o ha esito negativo.  Per altre informazioni sui processi in modalità di blocco e non di blocco, vedere 
  
    -   **FALSE**. I processi saranno in modalità non di blocco e restituiranno immediatamente risultati, consentendo di continuare a eseguire altro codice R. Tuttavia, anche in modalità non di blocco, la connessione client con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve essere mantenuta durante l'esecuzione del processo.  

3. Facoltativamente, è possibile specificare il percorso di una directory locale per l'uso condiviso da parte della sessione R locale e del computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] remoto e dei relativi account.
    
    ```R  
    sqlShareDir <- paste("c:\\AllShare\\", Sys.getenv("USERNAME"), sep="")   
    
    ## Add this line to create directory if it does not exist
    dir.create(sqlShareDir, recursive = TRUE) 
    ```  
    È consigliabile usare l'impostazione predefinita anziché specificare manualmente una cartella per questo argomento. Per altre informazioni, vedere le [informazioni di riferimento di ScaleR](https://msdn.microsoft.com/microsoft-r/scaler/rxinsqlserver).
    
    Per sapere quale cartella è in uso, è possibile eseguire `rxGetComputeContext` per visualizzare informazioni dettagliate sul contesto di calcolo corrente. 
  

4.  Dopo avere preparato tutte le variabili, inserirle come argomenti per il costruttore `RxInSqlServer` in modo da definire l'oggetto di contesto di calcolo.  
  
    ```R  
    sqlCompute <- RxInSqlServer(  
         connectionString = sqlConnString,        
         #shareDir = sqlShareDir,       
         wait = sqlWait,   
         consoleOutput = sqlConsoleOutput)  
    ```  
  
    Si noti che la sintassi per *RxInSqlServer* è quasi identica a quella della funzione *RxSqlServerData* usata in precedenza per definire l'origine dati. Esistono tuttavia alcune differenze importanti.  
  
    -   L'oggetto origine dati definito usando la funzione *RxSqlServerData* specifica la posizione in cui vengono archiviati i dati.  
  
    -   Al contrario, il contesto di calcolo definito usando la funzione *RxInSqlServer* indica la posizione in cui eseguire le aggregazioni e altri calcoli.  
  
    La definizione di un contesto di calcolo non influenza gli altri calcoli generici di R che possono essere eseguiti nella workstation e non modifica l'origine dei dati. Ad esempio, è possibile definire un file di testo locale come origine dati ma modificare il contesto di calcolo in SQL Server ed effettuare tutte le letture e i riepiloghi nei dati nel computer SQL Server. 
  
## Abilitare la traccia nel contesto di calcolo  
A volte per le operazioni che vengono eseguite correttamente nel contesto locale si verificano problemi quando vengono eseguite in un contesto di calcolo remoto specifico. Per analizzare i problemi o monitorare le prestazioni, è possibile abilitare la traccia nel contesto di calcolo per supportare la risoluzione dei problemi in fase di esecuzione.  
  
1. Creare un nuovo contesto di calcolo che usa la stessa stringa di connessione, ma aggiungere gli argomenti *traceEnabled* e *traceLevel* al costruttore *RxInSqlServer*.  
  
    ```R  
    sqlComputeTrace <- RxInSqlServer(   
        connectionString = sqlConnString,        
        #shareDir = sqlShareDir,  
        wait = sqlWait,   
        consoleOutput = sqlConsoleOutput,       
        traceEnabled = TRUE,
        traceLevel = 7)  
    ```  
  
    Nell'esempio la proprietà *traceLevel* è impostata su 7, ovvero sulla visualizzazione di tutte le informazioni di traccia.  

2. Per passare a questo contesto di calcolo in qualsiasi momento, usare la funzione *rxSetComputeContext* e specificare il contesto per nome.

    ```R  
    rxSetComputeContext( sqlComputeTrace)
    ```

    Per questa esercitazione verrà usato il contesto di calcolo senza abilitazione della traccia. Le prestazioni per l'opzione con abilitazione della traccia non sono state testate per tutte le operazioni e il funzionamento può variare a seconda della connettività di rete.  
  
Dopo aver creato un contesto di calcolo remoto, verrà descritto come cambiare i contesti di calcolo per eseguire il codice R sul server o in locale.  
  
## Passaggio successivo  
[Lezione 2: Creare ed eseguire script R &#40;procedura approfondita per l'analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/lesson-2-create-and-run-r-scripts-data-science-deep-dive.md)  
  
## Passaggio precedente  
[Eseguire query e modificare i dati SQL Server &#40;procedura approfondita per l'analisi scientifica&#41;](../../advanced-analytics/r-services/query-and-modify-the-sql-server-data-data-science-deep-dive.md)  
  
## Vedere anche  
[Procedura approfondita per l'analisi scientifica dei dati: Uso dei pacchetti RevoScaleR](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)  
  
  
  
