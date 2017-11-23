---
title: 'Lezione 2: Importare dati in SQL Server tramite PowerShell | Documenti Microsoft'
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs:
- R
- TSQL
ms.assetid: 3c5b5145-fa57-455a-b153-0400fc062dc0
caps.latest.revision: "11"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8c9190157b005158bb2ca8b9aeb7addbdbf1e69f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="lesson-2-import-data-to-sql-server-using-powershell"></a>Lezione 2: Importare dati in SQL Server tramite PowerShell

In questo articolo fa parte di un'esercitazione per gli sviluppatori SQL su come usare il linguaggio R in SQL Server.

In questo passaggio si eseguirà uno degli script scaricati per creare gli oggetti di database necessari per la procedura dettagliata. Lo script consente anche di creare molte delle stored procedure che saranno usate e di caricare i dati di esempio in una tabella del database specificato.

## <a name="run-the-scripts-to-create-sql-objects"></a>Eseguire gli script per creare oggetti SQL

Tra i file scaricati, verrà visualizzato uno script di PowerShell che è possibile eseguire per preparare l'ambiente per la procedura dettagliata. Con lo script vengono eseguite le azioni seguenti:

- Installazione di SQL Native Client e delle utilità della riga di comando SQL, qualora non siano ancora installate. Queste utilità sono necessarie per il caricamento bulk dei dati nel database tramite **bcp**.

- Creazione di un database e di una tabella nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e inserimento bulk dei dati nella tabella.

- Creazione di più funzioni SQL e stored procedure.

### <a name="run-the-script"></a>Eseguire lo script

1.  Aprire un prompt dei comandi di PowerShell come amministratore ed eseguire il comando seguente.
  
    ```ps
    .\RunSQL_SQL_Walkthrough.ps1
    ```
  
    Sarà richiesto di immettere le informazioni seguenti:
  
    - Il nome o l'indirizzo di un'istanza di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in cui [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] è stato installato
  
    - Il nome utente e la password di un account nell'istanza. L'account deve disporre delle autorizzazioni necessarie per creare database, creare tabelle e stored procedure e caricare i dati di tabelle. Se non si specifica il nome utente e password, l'identità di Windows viene utilizzata per accedere a SQL Server.
  
    - Il percorso e il nome del file con i dati di esempio appena scaricato. Esempio:
  
        `C:\tempRSQL\nyctaxi1pct.csv`
  
2.  Questo passaggio prevede anche che tutti gli script di [!INCLUDE[tsql](../../includes/tsql-md.md)] vengano modificati per sostituire i segnaposto con il nome del database e il nome utente specificati come input dello script.
  
    Controllare velocemente le stored procedure e le funzioni create dallo script.
  
    |**Nome file script SQL**|**Funzione**|
    |-|-|
    |create-db-tb-upload-data.sql|Crea un database e due tabelle:<br /><br />nyctaxi_sample: contiene il set di dati principale NYC Taxi. Alla tabella viene aggiunto un indice columnstore cluster per migliorare le prestazioni di archiviazione e query. L'1% del set di dati NYC Taxi sarà inserito in questa tabella.<br /><br />nyc_taxi_models: viene usata per salvare il modello con trainging impiegato per l'analisi avanzata.|
    |fnCalculateDistance.sql|Crea una funzione a valori scalari che calcola la distanza diretta tra le posizioni di salita e discesa del passeggero|
    |fnEngineerFeatures.sql|Crea una funzione con valori di tabella che definisce nuove funzionalità dati per il training del modello|
    |PersistModel.sql|Crea una stored procedure richiamabile per salvare un modello. La stored procedure usa un modello serializzato in un tipo di dati varbinary e lo scrive nella tabella specificata.|
    |PredictTipBatchMode.sql|Crea una stored procedure che chiama il modello con training per creare stime tramite il modello. La stored procedure accetta una query come parametro di input e restituisce una colonna di valori numerici contenente i punteggi per le righe di input.|
    |PredictTipSingleMode.sql|Crea una stored procedure che chiama il modello con training per creare stime tramite il modello. Questa stored procedure accetta una nuova osservazione come input, con i singoli valori della funzionalità passati come parametri in linea, e restituisce un valore che stima il risultato in base alla nuova osservazione.|
  
    Nella seconda parte di questa procedura dettagliata si creeranno altre stored procedure:
  
    |**Nome file script SQL**|**Funzione**|
    |------|------|
    |PlotHistogram.sql|Crea una stored procedure per l'esplorazione dei dati. Questa stored procedure chiama una funzione R per tracciare l'istogramma di una variabile e restituisce il tracciato come oggetto binario.|
    |PlotInOutputFiles.sql|Crea una stored procedure per l'esplorazione dei dati. Questa stored procedure crea un elemento grafico tramite una funzione R. L'output viene salvato come file PDF locale.|
    |TrainTipPredictionModel.sql|Crea una stored procedure che esegue il training di un modello di regressione logistica mediante la chiamata di un pacchetto R. Il modello consente di stimare il valore della colonna indicata. Viene eseguito un training usando il 70% dei dati selezionati casualmente. L'output della stored procedure corrisponde al modello con training, che viene salvato nella tabella nyc_taxi_models.|
  
3.  Accedere all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] e l'account di accesso specificato per verificare che sia possibile visualizzare il database, le tabelle, le funzioni e le stored procedure che sono state create.
  
    ![rsql_devtut_BrowseTables](media/rsql-devtut-browsetables.png "rsql_devtut_BrowseTables")
  
    > [!NOTE]
    > Se gli oggetti di database sono già esistenti, non possono essere creati nuovamente.
    >   
    > Se la tabella è già esistente, i dati saranno aggiunti senza sovrascrivere. Assicurarsi pertanto di eliminare tutti gli oggetti esistenti prima di eseguire lo script.

## <a name="next-lesson"></a>Lezione successiva

[Lezione 3: Esplorare e visualizzare i dati](../tutorials/sqldev-explore-and-visualize-the-data.md)

## <a name="previous-lesson"></a>Lezione precedente

[Lezione 1: Scaricare i dati di esempio](../tutorials/sqldev-download-the-sample-data.md)
