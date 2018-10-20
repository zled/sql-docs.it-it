---
title: Passaggio 2 di importare i dati in SQL Server usando PowerShell | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/07/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: f8b90a18c0cdce9c4c2c73db4b599e488570f018
ms.sourcegitcommit: 3cd6068f3baf434a4a8074ba67223899e77a690b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2018
ms.locfileid: "49461867"
---
# <a name="step-2-import-data-to-sql-server-using-powershell"></a>Passaggio 2: Importare i dati in SQL Server usando PowerShell
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo fa parte di un'esercitazione [analitica di Python nel database per sviluppatori SQL](sqldev-in-database-python-for-sql-developers.md). 

In questo passaggio si esegue uno degli script scaricati per creare gli oggetti di database richiesti per la procedura dettagliata. Inoltre, lo script consente di creare varie stored procedure e carica i dati di esempio in una tabella nel database specificato.

## <a name="create-database-objects-and-load-data"></a>Creare oggetti di database e caricare i dati

Tra i file scaricati dovrebbe essere uno script di PowerShell `RunSQL_SQL_Walkthrough.ps1`. Lo scopo di questo script consiste nel preparare l'ambiente per la procedura dettagliata.

Lo script effettua le seguenti operazioni:

- Installa il Client nativo di SQL e le utilità della riga di comando SQL, se non è già installato. Queste utilità sono necessarie per il caricamento bulk dei dati nel database tramite **bcp**.

- Crea un database e una tabella nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza e gli inserimenti bulk dei dati nella tabella.

- Consente di creare più funzioni SQL e stored procedure.

Se si verificano problemi, è possibile usare lo script come riferimento per eseguire i passaggi manualmente.

### <a name="modify-the-script-to-use-a-trusted-windows-identity"></a>Modificare lo script per usare un'identità Windows attendibile

Per impostazione predefinita, lo script si presuppone un accesso utente di database di SQL Server e una password. Se sei db_owner con l'account utente di Windows, è possibile usare l'identità di Windows per creare gli oggetti. A tale scopo, aprire `RunSQL_SQL_Walkthrough.ps1` in un editor di codice da accodare **`-T`** per l'utilità bcp comandi di inserimento bulk:

```text
bcp $db_tb in $csvfilepath -t ',' -S $server -f taxiimportfmt.xml -F 2 -C "RAW" -b 200000 -U $u -P $p -T
```

### <a name="run-the-script"></a>Eseguire lo script

1. Aprire un prompt dei comandi di PowerShell come amministratore. Se non si è già nella cartella creata nel passaggio precedente, passare alla cartella e quindi eseguire il comando seguente:
  
    ```ps
    .\RunSQL_SQL_Walkthrough.ps1
    ```

2. Lo script richiede le informazioni seguenti:

    - Il nome o l'indirizzo di un [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] istanza in cui è installato Servizi di Machine Learning con Python.
    - Il nome utente e la password di un account nell'istanza. L'account usato deve avere la possibilità di creare database, creare tabelle e stored procedure e caricamento bulk dei dati alle tabelle. 
    - Se non si specifica il nome utente e password, l'identità Windows viene utilizzata per accedere a SQL Server.
    - Il percorso e il nome del file con i dati di esempio appena scaricato. Ad esempio, usare `C:\temp\pysql\nyctaxi1pct.csv`

    > [!NOTE]
    > Per caricare correttamente i dati, la libreria xmlrw. dll deve essere nella stessa cartella bcp.exe.

3. Lo script modifica anche il [!INCLUDE[tsql](../../includes/tsql-md.md)] script che è stato scaricato in precedenza e il nome che sostituisce i segnaposto con il nome del database e l'utente che si forniscono.
  
4. Al termine dell'esecuzione dello script, accedere al [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza utilizzando l'account di accesso è stato specificato, per verificare che il database, tabelle, funzioni e stored procedure sono state create. L'immagine seguente mostra gli oggetti in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].

    ![sfogliare le tabelle in SQL Server Management Studio](media/sqldev-python-browsetables1.png "visualizzare tabelle in SQL Server Management Studio")

    > [!NOTE]
    > Se gli oggetti di database già esistente, non possono essere creati nuovamente.
    > 
    > Se viene trovata una tabella esistente dello stesso nome e dello schema, verranno aggiunti i dati, non verrà sovrascritto. Pertanto, assicurarsi di eliminare o troncare le tabelle esistenti prima di eseguire lo script.

## <a name="list-of-stored-procedures-and-functions"></a>Elenco di stored procedure e funzioni

Gli oggetti di SQL Server seguenti vengono creati dallo script:

|**Nome file script SQL**|**Funzione**|
|------|------|
|create-db-tb-upload-data.sql|Crea un database e due tabelle:<br /><br />nyctaxi_sample: contiene il set di dati principale NYC Taxi. Alla tabella viene aggiunto un indice columnstore cluster per migliorare le prestazioni di archiviazione e query. L'1% del set di dati NYC Taxi sarà inserito in questa tabella.<br /><br />nyc_taxi_models: viene usata per salvare il modello con trainging impiegato per l'analisi avanzata.|
|fnCalculateDistance.sql|Crea una funzione a valori scalari che calcola la distanza diretta tra le posizioni di salita e discesa del passeggero|
|fnEngineerFeatures.sql|Crea una funzione con valori di tabella che definisce nuove funzionalità dati per il training del modello|
|TrainingTestingSplit.sql|Suddividere i dati nella tabella nyctaxi_sample in due parti: nyctaxi_sample_training e nyctaxi_sample_testing.|
|PredictTipSciKitPy.sql|Crea una stored procedure che chiama il modello sottoposto a training (scikit-informazioni su) per creare stime tramite il modello. La stored procedure accetta una query come parametro di input e restituisce una colonna di valori numerici contenente i punteggi per le righe di input.|
|PredictTipRxPy.sql|Crea una stored procedure che chiama il modello sottoposto a training (revoscalepy) per creare stime tramite il modello. La stored procedure accetta una query come parametro di input e restituisce una colonna di valori numerici contenente i punteggi per le righe di input.|
|PredictTipSingleModeSciKitPy.sql|Crea una stored procedure che chiama il modello sottoposto a training (scikit-informazioni su) per creare stime tramite il modello. Questa stored procedure accetta una nuova osservazione come input, con i singoli valori della funzionalità passati come parametri in linea, e restituisce un valore che stima il risultato in base alla nuova osservazione.|
|PredictTipSingleModeRxPy.sql|Crea una stored procedure che chiama il modello sottoposto a training (revoscalepy) per creare stime tramite il modello. Questa stored procedure accetta una nuova osservazione come input, con i singoli valori della funzionalità passati come parametri in linea, e restituisce un valore che stima il risultato in base alla nuova osservazione.|

Nella seconda parte di questa procedura dettagliata, si crea una stored procedure aggiuntive:
    
|**Nome file script SQL**|**Funzione**|
|------|------|
|SerializePlots.sql|Crea una stored procedure per l'esplorazione dei dati. Questa stored procedure crea un grafico con Python e quindi serializzare gli oggetti di graph.|
|TrainTipPredictionModelSciKitPy.sql|Crea una stored procedure che esegue il training di un modello di regressione logistica (scikit-informazioni su). Il modello viene stimato il valore della colonna indicata e viene eseguito il training usando un selezionato casualmente il 60% dei dati. L'output della stored procedure corrisponde al modello con training, che viene salvato nella tabella nyc_taxi_models.|
|TrainTipPredictionModelRxPy.sql|Crea una stored procedure che esegue il training di un modello di regressione logistica (revoscalepy). Il modello viene stimato il valore della colonna indicata e viene eseguito il training usando un selezionato casualmente il 60% dei dati. L'output della stored procedure corrisponde al modello con training, che viene salvato nella tabella nyc_taxi_models.|

## <a name="next-step"></a>Passaggio successivo

[Passaggio 3: Esplorare e visualizzare i dati](sqldev-py3-explore-and-visualize-the-data.md)

## <a name="previous-step"></a>Passaggio precedente

[Passaggio 1: Scaricare i dati di esempio](demo-data-nyctaxi-in-sql.md)

