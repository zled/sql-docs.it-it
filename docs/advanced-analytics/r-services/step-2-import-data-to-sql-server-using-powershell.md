---
title: "Passaggio 2: Importare i dati in SQL Server usando PowerShell (esercitazione sull&#39;analisi avanzata nel database) | Microsoft Docs"
ms.custom: ""
ms.date: "08/05/2016"
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
ms.assetid: 3c5b5145-fa57-455a-b153-0400fc062dc0
caps.latest.revision: 11
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 11
---
# Passaggio 2: Importare i dati in SQL Server usando PowerShell (esercitazione sull&#39;analisi avanzata nel database)
In questo passaggio si eseguirà uno degli script scaricati per creare gli oggetti di database necessari per la procedura dettagliata. Lo script consente anche di creare molte delle stored procedure che saranno usate e di caricare i dati di esempio in una tabella del database specificato.  
  
## Eseguire gli script per creare oggetti SQL  
Tra i file scaricati dovrebbe essere incluso un script di PowerShell, che sarà eseguito per preparare l'ambiente per la procedura dettagliata.  
  
Con lo script vengono eseguite le azioni seguenti:  
  
-   Installazione di SQL Native Client e delle utilità della riga di comando SQL, qualora non siano ancora installate. Queste utilità sono necessarie per il caricamento bulk dei dati nel database tramite **bcp**.  
  
-   Creazione di un database e di una tabella nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e inserimento bulk dei dati nella tabella.  
  
-   Creazione di più funzioni SQL e stored procedure.  
  
#### Per eseguire lo script  
1.  Aprire un prompt dei comandi di PowerShell come amministratore ed eseguire il comando seguente.  
  
    ```  
    .\RunSQL_SQL_Walkthrough.ps1  
    ```  
  
    Sarà richiesto di immettere le informazioni seguenti:  
  
    -   Il nome o l'indirizzo di un'istanza di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in cui [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] è stato installato  
  
    -   Il nome utente e la password di un account nell'istanza. L'account usato deve essere autorizzato a creare database, tabelle e stored procedure e caricare i dati nelle tabelle.  
  
    -   Il percorso e il nome del file con i dati di esempio appena scaricato. Esempio:  
  
        `C:\tempRSQL\nyctaxi1pct.csv`  
  
2.  Questo passaggio prevede anche che tutti gli script di [!INCLUDE[tsql](../../includes/tsql-md.md)] vengano modificati per sostituire i segnaposto con il nome del database e il nome utente specificati come input dello script.  
  
    Controllare velocemente le stored procedure e le funzioni create dallo script.  
  
    |||  
    |-|-|  
    |**Nome file script SQL**|**Funzione**|  
    |create-db-tb-upload-data.sql|Crea un database e due tabelle:<br /><br />nyctaxi_sample: contiene il set di dati principale NYC Taxi. Alla tabella viene aggiunto un indice columnstore cluster per migliorare le prestazioni di archiviazione e query. L'1% del set di dati NYC Taxi sarà inserito in questa tabella.<br /><br />nyc_taxi_models: viene usata per salvare il modello con trainging impiegato per l'analisi avanzata.|  
    |fnCalculateDistance.sql|Crea una funzione a valori scalari che calcola la distanza diretta tra le posizioni di salita e discesa del passeggero|  
    |fnEngineerFeatures.sql|Crea una funzione con valori di tabella che definisce nuove funzionalità dati per il training del modello|  
    |PersistModel.sql|Crea una stored procedure richiamabile per salvare un modello. La stored procedure usa un modello serializzato in un tipo di dati varbinary e lo scrive nella tabella specificata.|  
    |PredictTipBatchMode.sql|Crea una stored procedure che chiama il modello con training per creare stime tramite il modello. La stored procedure accetta una query come parametro di input e restituisce una colonna di valori numerici contenente i punteggi per le righe di input.|  
    |PredictTipSingleMode.sql|Crea una stored procedure che chiama il modello con training per creare stime tramite il modello. Questa stored procedure accetta una nuova osservazione come input, con i singoli valori della funzionalità passati come parametri in linea, e restituisce un valore che stima il risultato in base alla nuova osservazione.|  
  
    Nella seconda parte di questa procedura dettagliata si creeranno altre stored procedure:  
  
    |||  
    |-|-|  
    |**Nome file script SQL**|**Funzione**|  
    |PlotHistogram.sql|Crea una stored procedure per l'esplorazione dei dati. Questa stored procedure chiama una funzione R per tracciare l'istogramma di una variabile e restituisce il tracciato come oggetto binario.|  
    |PlotInOutputFiles.sql|Crea una stored procedure per l'esplorazione dei dati. Questa stored procedure crea un elemento grafico tramite una funzione R. L'output viene salvato come file PDF locale.|  
    |TrainTipPredictionModel.sql|Crea una stored procedure che esegue il training di un modello di regressione logistica mediante la chiamata di un pacchetto R. Il modello consente di stimare il valore della colonna indicata. Viene eseguito un training usando il 70% dei dati selezionati casualmente. L'output della stored procedure corrisponde al modello con training, che viene salvato nella tabella nyc_taxi_models.|  
  
3.  Accedere all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] e l'account di accesso specificato per verificare che sia possibile visualizzare il database, le tabelle, le funzioni e le stored procedure che sono state create.  
  
    ![rsql_devtut_BrowseTables](../../advanced-analytics/r-services/media/rsql-devtut-browsetables.PNG "rsql_devtut_BrowseTables")  
  
    > [!NOTE]  
    > Se gli oggetti di database sono già esistenti, non possono essere creati nuovamente.  
    >   
    > Se la tabella è già esistente, i dati saranno aggiunti senza sovrascrivere. Assicurarsi pertanto di eliminare tutti gli oggetti esistenti prima di eseguire lo script.  
  
## Passaggio successivo  
[Passaggio 3: Esplorare e visualizzare i dati](../../advanced-analytics/r-services/step-3-explore-and-visualize-the-data-in-database-advanced-analytics-tutorial.md)  
  
## Passaggio precedente  
[Passaggio 1: Scaricare i dati di esempio](../../advanced-analytics/r-services/step-1-download-the-sample-data-in-database-advanced-analytics-tutorial.md)  
  
## Vedere anche  
[Analisi avanzata nel database per sviluppatori SQL &#40;Esercitazione&#41;](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)  
[Esercitazioni di SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
  
  
  
