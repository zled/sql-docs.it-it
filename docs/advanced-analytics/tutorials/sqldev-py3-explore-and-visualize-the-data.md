---
title: 'Passaggio 3: Esplorare e visualizzare i dati | Documenti Microsoft'
ms.custom: 
ms.date: 10/17/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-python
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
ms.openlocfilehash: 31fa666c98948dc18f7aad988de795809594d2dd
ms.contentlocale: it-it
ms.lasthandoff: 10/18/2017

---
# <a name="step-3-explore-and-visualize-the-data"></a>Passaggio 3: Esplorare e visualizzare i dati

In questo articolo fa parte di un'esercitazione, [analitica Python nel database per gli sviluppatori SQL](sqldev-in-database-python-for-sql-developers.md). 

In questo passaggio, esplorare i dati di esempio e generare alcuni grafici. In un secondo momento, come serializzare oggetti grafici in Python e deserializzare gli oggetti e rendere tracciati.

## <a name="review-the-data"></a>Esaminare i dati

In primo luogo, è opportuno esplorare lo schema di dati, come è stato apportato alcune modifiche per renderne più semplice utilizzare i dati NYC Taxi

+ Set di dati originale utilizzato file distinti per gli identificatori di taxi e un record di andata e ritorno. È stata unita in join due set di dati originale nelle colonne _medallion_, _hack_license_, e _pickup_datetime_.  
+ Set di dati originale volumi con spanning molti file e molto grande. Abbiamo sottocampionate per ottenere solo 1% del numero di record originale. La tabella di dati corrente include 1,703,957 righe e 23 colonne.

**Identificatori di taxi**

Il _medallion_ colonna rappresenta il numero di ID univoco del taxi.

Il _hack_license_ colonna contiene il numero di licenza del driver taxi (resi anonime).

**Record delle corse e delle tariffe**

Il record di ogni corsa include il luogo e l'ora di inizio e fine della corsa e la distanza percorsa.

Il record di ogni tariffa include i dati del pagamento, ad esempio il tipo di pagamento, l'importo totale e l'importo della mancia.

Le ultime tre colonne possono essere usate per diverse attività di apprendimento automatico.  La colonna _tip_amount_ contiene valori numerici continui e può essere usata come colonna **label** per l'analisi della regressione. La colonna _tipped_ include solo valori sì/no e viene usata per la classificazione binaria. La colonna _tip_class_ include più **etichette di classe** e può essere quindi usata come etichetta per le attività di classificazione multiclasse.

I valori utilizzati per le colonne di etichetta sono tutti basati sul `tip_amount` colonna utilizzando le regole business:

+ Colonna di etichetta `tipped` dispone di valori 0 e 1

    Se `tip_amount` > 0, `tipped` = 1; in caso contrario `tipped` = 0

+ Colonna di etichetta `tip_class` dispone di valori possibili di classe 0-4

    Classe 0: `tip_amount` = $0

    Classe 1: `tip_amount` > $0 e `tip_amount` < = $5
    
    Classe 2: `tip_amount` > $5 e `tip_amount` < = $10
    
    Classe 3: `tip_amount` > $10 e `tip_amount` < = $20
    
    Classe 4: `tip_amount` > $20

## <a name="create-plots-using-python-in-t-sql"></a>Creare grafici usando Python in T-SQL

Lo sviluppo di una soluzione di analisi scientifica dei dati prevede in genere frequenti esplorazioni e visualizzazioni dei dati. Poiché la visualizzazione è un potente strumento per le informazioni sulla distribuzione dei dati e gli outlier, Python fornisce molti pacchetti per la visualizzazione dati. Il **matplotlib** modulo è una delle librerie più comuni per la visualizzazione e include numerose funzioni per la creazione di istogrammi, grafici a dispersione, casella grafici e altri grafici di esplorazione dei dati.

In questa sezione, è illustrato come utilizzare i grafici tramite le stored procedure. Invece di aprire l'immagine nel server, archiviare l'oggetto di Python `plot` come **varbinary** dati e quindi scrivere che in un file che possono essere condivisi o visualizzati in un' posizione.

### <a name="create-a-plot-as-varbinary-data"></a>Creare un tracciato come dati varbinary

Il **revoscalepy** modulo incluso in servizi di SQL Server 2017 Machine Learning supporta funzionalità simili a quelli di **RevoScaleR** pacchetto per R.  Questo esempio viene utilizzato l'equivalente di Python di `rxHistogram` per tracciare un istogramma in base ai dati da un [!INCLUDE[tsql](../../includes/tsql-md.md)] query. 

La stored procedure restituisce un Python serializzato `figure` oggetto come flusso di **varbinary** dati. Non è possibile visualizzare direttamente i dati binari, ma è possibile usare il codice Python da deserializzare e visualizzare le cifre nel client e quindi salvare il file di immagine in un computer client.

1. Creare la stored procedure _SerializePlots_, se lo script di PowerShell non è già eseguita questa operazione.

    - La variabile `@query` definisce il testo della query `SELECT tipped FROM nyctaxi_sample`, che viene passato al blocco di codice Python come argomento per la variabile di input di script, `@input_data_1`.
    - Lo script Python è piuttosto semplice: **matplotlib** `figure` gli oggetti vengono utilizzati per eseguire il tracciato istogramma e a dispersione e questi oggetti vengono quindi serializzati utilizzando il `pickle` libreria.
    - L'oggetto graphics Python serializzato in un **pandas** frame di dati per l'output.
  
    ```SQL
    CREATE PROCEDURE [dbo].[SerializePlots]
    AS
    BEGIN
      SET NOCOUNT ON;
      DECLARE @query nvarchar(max) =
      N'SELECT cast(tipped as int) as tipped, tip_amount, fare_amount FROM [dbo].[nyctaxi_sample]'
      EXECUTE sp_execute_external_script
      @language = N'Python',
      @script = N'
    import matplotlib
    matplotlib.use("Agg")
    import matplotlib.pyplot as plt
    import pandas as pd
    import pickle

    fig_handle = plt.figure()
    plt.hist(InputDataSet.tipped)
    plt.xlabel("Tipped")
    plt.ylabel("Counts")
    plt.title("Histogram, Tipped")
    plot0 = pd.DataFrame(data =[pickle.dumps(fig_handle)], columns =["plot"])
    plt.clf()

    plt.hist(InputDataSet.tip_amount)
    plt.xlabel("Tip amount ($)")
    plt.ylabel("Counts")
    plt.title("Histogram, Tip amount")
    plot1 = pd.DataFrame(data =[pickle.dumps(fig_handle)], columns =["plot"])
    plt.clf()

    plt.hist(InputDataSet.fare_amount)
    plt.xlabel("Fare amount ($)")
    plt.ylabel("Counts")
    plt.title("Histogram, Fare amount")
    plot2 = pd.DataFrame(data =[pickle.dumps(fig_handle)], columns =["plot"])
    plt.clf()

    plt.scatter( InputDataSet.fare_amount, InputDataSet.tip_amount)
    plt.xlabel("Fare Amount ($)")
    plt.ylabel("Tip Amount ($)")
    plt.title("Tip amount by Fare amount")
    plot3 = pd.DataFrame(data =[pickle.dumps(fig_handle)], columns =["plot"])
    plt.clf()

    OutputDataSet = plot0.append(plot1, ignore_index=True).append(plot2, ignore_index=True).append(plot3, ignore_index=True)
    ',
    @input_data_1 = @query
    WITH RESULT SETS ((plot varbinary(max)))
    END
    GO
    ```

2. Ora è possibile eseguire la stored procedure senza argomenti per generare un grafico dai dati hardcoded come query di input.

    ```
    EXEC [dbo].[SerializePlots]
    ```

3. I risultati dovrebbero essere simile al seguente:
  
    ```
    plot
    0xFFD8FFE000104A4649...
    0xFFD8FFE000104A4649...
    0xFFD8FFE000104A4649...
    0xFFD8FFE000104A4649...
    ```

  
4. Da un client Python, è ora possibile connettersi all'istanza di SQL Server che ha generato gli oggetti binari di tracciato e visualizzare i grafici. 

    A tale scopo, eseguire il seguente codice Python, sostituendo il nome del server, nome del database e le credenziali come appropriato. Verificare che la versione di Python è lo stesso per il client e server. Assicurarsi inoltre che le librerie di Python nel client (ad esempio matplotlib) sono la versione uguale o maggiore rispetto delle librerie installate nel server.
  
    **Utilizzando l'autenticazione di SQL Server:**
    
    ```python
    import pyodbc
    import pickle
    import os
    cnxn = pyodbc.connect('DRIVER={SQL Server};SERVER={SERVER_NAME};DATABASE={DB_NAME};UID={USER_NAME};PWD={PASSWORD}')
    cursor = cnxn.cursor()
    cursor.execute("EXECUTE [dbo].[SerializePlots]")
    tables = cursor.fetchall()
    for i in range(0, len(tables)):
        fig = pickle.loads(tables[i][0])
        fig.savefig(str(i)+'.png')
    print("The plots are saved in directory: ",os.getcwd())
    ```

    **Utilizzando l'autenticazione di Windows:**

    ```python
    import pyodbc
    import pickle
    import os
    cnxn = pyodbc.connect('DRIVER={SQL Server};SERVER={SERVER_NAME};DATABASE={DB_NAME};Trusted_Connection=yes;')
    cursor = cnxn.cursor()
    cursor.execute("EXECUTE [dbo].[SerializePlots]")
    tables = cursor.fetchall()
    for i in range(0, len(tables)):
        fig = pickle.loads(tables[i][0])
        fig.savefig(str(i)+'.png')
    print("The plots are saved in directory: ",os.getcwd())
    ```

5.  Se la connessione ha esito positivo, si verrà visualizzato un messaggio simile al seguente:
  
    *I grafici vengono salvati nella directory: xxxx*
  
6.  Il file di output viene creato nella directory di lavoro di Python. Per visualizzare il tracciato, individuare la directory di lavoro di Python e aprire il file. La figura seguente mostra un tracciato salvato nel computer client.
  
    ![Suggerimento quantità tariffa di vs quantità](media/sqldev-python-sample-plot.png "quantità tariffa di suggerimento quantità vs") 

## <a name="next-step"></a>Passaggio successivo

[Passaggio 4: Creare funzionalità di dati mediante T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

## <a name="previous-step"></a>Passaggio precedente

[Passaggio 2: Importare i dati in SQL Server usando PowerShell](sqldev-py2-import-data-to-sql-server-using-powershell.md)


