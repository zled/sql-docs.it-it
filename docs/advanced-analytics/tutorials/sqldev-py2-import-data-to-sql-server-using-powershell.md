---
title: 'Passaggio 2: Importare dati in SQL Server tramite PowerShell | Documenti Microsoft'
ms.custom: 
ms.date: 10/17/2017
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
ms.sourcegitcommit: 2f28400200105e8e63f787cbcda58c183ba00da5
ms.openlocfilehash: b4741dcfee4bdc2e5ca2327b50f5dd727be9de55
ms.contentlocale: it-it
ms.lasthandoff: 10/18/2017

---
# <a name="step-2-import-data-to-sql-server-using-powershell"></a>Passaggio 2: Importare dati in SQL Server tramite PowerShell

In questo articolo fa parte di un'esercitazione, [analitica Python nel database per gli sviluppatori SQL](sqldev-in-database-python-for-sql-developers.md). 

In questo passaggio viene eseguito uno script scaricato, per creare gli oggetti di database richiesti per la procedura dettagliata. Inoltre, lo script crea diverse stored procedure e carica i dati di esempio in una tabella nel database specificato.

## <a name="create-database-objects-and-load-data"></a>Creare oggetti di database e caricare i dati

Verrà visualizzato uno script di PowerShell, tra i file scaricati `RunSQL_SQL_Walkthrough.ps1`. Lo scopo di questo script consiste nel preparare l'ambiente per la procedura dettagliata.

Lo script effettua le seguenti operazioni:

- Installazione di SQL Native Client e le utilità della riga di comando SQL, se non già installato. Queste utilità sono necessarie per il caricamento bulk dei dati nel database tramite **bcp**.

- Crea un database e una tabella nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza e inserimenti bulk dei dati nella tabella.

- Crea più funzioni SQL e stored procedure.

Se si verificano problemi, è possibile utilizzare lo script come riferimento per eseguire i passaggi manualmente.

1. Aprire un prompt dei comandi di PowerShell come amministratore. Se non si già nella cartella creata nel passaggio precedente, passare alla cartella e quindi eseguire il comando seguente:
  
    ```ps
    .\RunSQL_SQL_Walkthrough.ps1
    ```

2. Lo script richiede le seguenti informazioni:

    - Il nome o l'indirizzo di un [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] istanza in cui è installato Servizi di Machine Learning con Python.
    - Il nome utente e la password di un account nell'istanza. L'account utilizzato deve avere la possibilità di creare database, creare tabelle e stored procedure e caricamento bulk dei dati alle tabelle. 
    - Se non si specifica il nome utente e password, l'identità di Windows viene utilizzata per accedere a SQL Server e vengono alzate di livello per immettere una password.
    - Il percorso e il nome del file con i dati di esempio appena scaricato. Ad esempio, usare `C:\temp\pysql\nyctaxi1pct.csv`

    > [!NOTE]
    > Per caricare i dati correttamente, il file xmlrw.dll sia libreria deve essere nella stessa cartella bcp.exe.

3. Lo script anche di modificare il [!INCLUDE[tsql](../../includes/tsql-md.md)] fornire script che è stato scaricato in precedenza e assegnare un nome che si sostituisce i segnaposto con il nome del database e l'utente.
  
4. Quando lo script viene completato, l'accesso per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza utilizzando l'account di accesso specificato, per verificare che il database, tabelle, funzioni e stored procedure sono state create. La figura seguente mostra gli oggetti in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].

    ![sfogliare le tabelle in SQL Server Management Studio](media/sqldev-python-browsetables1.png "visualizzare tabelle in SQL Server Management Studio")

    > [!NOTE]
    > Se gli oggetti di database già esistente, non possono essere creati nuovamente.
    > 
    > Se viene trovata una tabella esistente dello stesso nome e lo stesso schema, verranno aggiunti i dati, non verrà sovrascritto. Assicurarsi, pertanto, eliminare o troncare le tabelle esistenti prima di eseguire lo script.

## <a name="list-of-stored-procedures-and-functions"></a>Elenco di stored procedure e funzioni

I seguenti oggetti di SQL Server vengono creati dallo script:

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

Nella seconda parte di questa procedura dettagliata, è creare stored procedure aggiuntive:
    
|**Nome file script SQL**|**Funzione**|
|------|------|
|SerializePlots.sql|Crea una stored procedure per l'esplorazione dei dati. Questa stored procedure crea un'immagine usando Python e quindi serializzare gli oggetti del grafico.|
|TrainTipPredictionModelSciKitPy.sql|Crea una stored procedure che esegue il training di un modello di regressione logistica (scikit-informazioni). Il modello consente di stimare il valore della colonna inclinato e viene eseguito mediante un selezionato in modo casuale il 60% dei dati. L'output della stored procedure corrisponde al modello con training, che viene salvato nella tabella nyc_taxi_models.|
|TrainTipPredictionModelRxPy.sql|Crea una stored procedure che esegue il training di un modello di regressione logistica (revoscalepy). Il modello consente di stimare il valore della colonna inclinato e viene eseguito mediante un selezionato in modo casuale il 60% dei dati. L'output della stored procedure corrisponde al modello con training, che viene salvato nella tabella nyc_taxi_models.|

## <a name="next-step"></a>Passaggio successivo

[Passaggio 3: Esplorare e visualizzare i dati](sqldev-py3-explore-and-visualize-the-data.md)

## <a name="previous-step"></a>Passaggio precedente

[Passaggio 1: Scaricare i dati di esempio](sqldev-py1-download-the-sample-data.md)


