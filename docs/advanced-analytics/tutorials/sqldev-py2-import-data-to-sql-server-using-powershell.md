---
title: 'Passaggio 2: Importare i dati in SQL Server usando PowerShell | Microsoft Docs'
ms.custom: 
ms.date: 05/25/2017
ms.prod: sql-server-vnext-ctp2
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2017
dev_langs:
- Python
- TSQL
ms.assetid: 
caps.latest.revision: 2
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 62a06d6c442428132f84b3f8e5a665e872a8d361
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="step-2-import-data-to-sql-server-using-powershell"></a>Passaggio 2: Importare i dati in SQL Server usando PowerShell

In questo passaggio si eseguirà uno degli script scaricati per creare gli oggetti di database necessari per la procedura dettagliata. Lo script consente anche di creare molte delle stored procedure che saranno usate e di caricare i dati di esempio in una tabella del database specificato.

## <a name="create-sql-objects-and-data"></a>Creare dati e oggetti SQL

Tra i file scaricati dovrebbe essere incluso un script di PowerShell, che sarà eseguito per preparare l'ambiente per la procedura dettagliata.  Lo script effettua le seguenti operazioni:

- Installazione di SQL Native Client e le utilità della riga di comando SQL, se non già installato. Queste utilità sono necessarie per il caricamento bulk dei dati nel database tramite **bcp**.

- Crea un database e una tabella nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza e inserimenti bulk dei dati nella tabella.

- Crea più funzioni SQL e stored procedure.

### <a name="run-the-script"></a>Eseguire lo script

1. Aprire un prompt dei comandi di PowerShell come amministratore ed eseguire il comando seguente.
  
    ```  
    .\RunSQL_SQL_Walkthrough.ps1  
    ```  

    Sarà richiesto di immettere le informazioni seguenti:
    - Il nome o l'indirizzo di un [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] istanza in cui è installato Servizi con Python di apprendimento automatico
    - Il nome utente e la password di un account nell'istanza. L'account usato deve essere autorizzato a creare database, tabelle e stored procedure e caricare i dati nelle tabelle. Se non si specifica il nome utente e password, l'identità di Windows viene utilizzata per accedere a SQL Server.
    - Il percorso e il nome del file con i dati di esempio appena scaricato. Ad esempio, usare `C:\tempRSQL\nyctaxi1pct.csv`

    > [!NOTE]
    > Assicurarsi che il file xmlrw.dll sia sia nella stessa cartella del bcp.exe. In caso contrario, viene copiato.

2.  Questo passaggio prevede anche che tutti gli script di [!INCLUDE[tsql](../../includes/tsql-md.md)] vengano modificati per sostituire i segnaposto con il nome del database e il nome utente specificati come input dello script.
  
3. Controllare velocemente le stored procedure e le funzioni create dallo script.
     
    |**Nome file script SQL**|**Funzione**|
    |------|------|
    |create-db-tb-upload-data.sql|Crea un database e due tabelle:<br /><br />nyctaxi_sample: contiene il set di dati principale NYC Taxi. Alla tabella viene aggiunto un indice columnstore cluster per migliorare le prestazioni di archiviazione e query. L'1% del set di dati NYC Taxi sarà inserito in questa tabella.<br /><br />nyc_taxi_models: viene usata per salvare il modello con trainging impiegato per l'analisi avanzata.|
    |fnCalculateDistance.sql|Crea una funzione a valori scalari che calcola la distanza diretta tra le posizioni di salita e discesa del passeggero|
    |fnEngineerFeatures.sql|Crea una funzione con valori di tabella che definisce nuove funzionalità dati per il training del modello|
    |TrainingTestingSplit.sql|Suddividere i dati nella tabella nyctaxi_sample in due parti: nyctaxi_sample_training e nyctaxi_sample_testing.|
    |PredictTipSciKitPy.sql|Crea una stored procedure che chiama il modello con training (scikit-informazioni) per creare stime utilizzando il modello. La stored procedure accetta una query come parametro di input e restituisce una colonna di valori numerici contenente i punteggi per le righe di input.|
    |PredictTipRxPy.sql|Crea una stored procedure che chiama il modello con training (revoscalepy) per creare stime tramite il modello. La stored procedure accetta una query come parametro di input e restituisce una colonna di valori numerici contenente i punteggi per le righe di input.|
    |PredictTipSingleModeSciKitPy.sql|Crea una stored procedure che chiama il modello con training (scikit-informazioni) per creare stime utilizzando il modello. Questa stored procedure accetta una nuova osservazione come input, con i singoli valori della funzionalità passati come parametri in linea, e restituisce un valore che stima il risultato in base alla nuova osservazione.|
    |PredictTipSingleModeRxPy.sql|Crea una stored procedure che chiama il modello con training (revoscalepy) per creare stime tramite il modello. Questa stored procedure accetta una nuova osservazione come input, con i singoli valori della funzionalità passati come parametri in linea, e restituisce un valore che stima il risultato in base alla nuova osservazione.|
  
4. Nella seconda parte di questa procedura dettagliata si creeranno altre stored procedure:
    
    |**Nome file script SQL**|**Funzione**|
    |------|------|
    |SerializePlots.sql|Crea una stored procedure per l'esplorazione dei dati. Questa stored procedure crea un'immagine usando Python e quindi serializzare gli oggetti del grafico.|
    |TrainTipPredictionModelSciKitPy.sql|Crea una stored procedure che esegue il training di un modello di regressione logistica (scikit-informazioni). Il modello consente di stimare il valore della colonna inclinato e viene eseguito mediante un selezionato in modo casuale il 60% dei dati. L'output della stored procedure corrisponde al modello con training, che viene salvato nella tabella nyc_taxi_models.|
    |TrainTipPredictionModelRxPy.sql|Crea una stored procedure che esegue il training di un modello di regressione logistica (revoscalepy). Il modello consente di stimare il valore della colonna inclinato e viene eseguito mediante un selezionato in modo casuale il 60% dei dati. L'output della stored procedure corrisponde al modello con training, che viene salvato nella tabella nyc_taxi_models.|
  
3. Accedere all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] e l'account di accesso specificato per verificare che sia possibile visualizzare il database, le tabelle, le funzioni e le stored procedure che sono state create.

    ![sfogliare le tabelle in SQL Server Management Studio](media/sqldev-python-browsetables1.png "visualizzare tabelle in SQL Server Management Studio")

    > [!NOTE]
    > Se gli oggetti di database sono già esistenti, non possono essere creati nuovamente. Se la tabella è già esistente, i dati saranno aggiunti senza sovrascrivere. Assicurarsi pertanto di eliminare tutti gli oggetti esistenti prima di eseguire lo script.
    > Seguire le istruzioni [qui](https://docs.microsoft.com/en-us/sql/advanced-analytics/r/set-up-sql-server-r-services-in-database#bkmk_enableFeature) per abilitare i servizi di scripting esterno.
    


## <a name="next-step"></a>Passaggio successivo

[Passaggio 3: Esplorare e visualizzare i dati](sqldev-py3-explore-and-visualize-the-data.md)

## <a name="previous-step"></a>Passaggio precedente

[Passaggio 1: Scaricare i dati di esempio](sqldev-py1-download-the-sample-data.md)

## <a name="see-also"></a>Vedere anche

[Servizi di Machine Learning con Python](../python/sql-server-python-services.md)



