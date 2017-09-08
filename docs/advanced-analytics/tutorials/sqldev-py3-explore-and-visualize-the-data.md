---
title: 'Passaggio 3: Esplorare e visualizzare i dati | Microsoft Docs'
ms.custom: 
ms.date: 05/25/2017
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
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: dfb80fcd3241b22f0ac72c2cf4cd8a18d1add857
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="step-3-explore-and-visualize-the-data"></a>Passaggio 3: Esplorare e visualizzare i dati

Lo sviluppo di una soluzione di analisi scientifica dei dati prevede in genere frequenti esplorazioni e visualizzazioni dei dati. In questo passaggio, si sarà esplorare i dati di esempio e generare alcuni grafici. In un secondo momento, si apprenderà come serializzare oggetti grafici in Python e quindi deserializzare tali oggetti e le funzionalità di grafici.

> [!NOTE]
> Questa procedura dettagliata illustra solo le attività di classificazione binaria. si è di provare a compilare modelli separati per gli altri due learning macchina attività, la regressione e classificazione multiclasse.

## <a name="review-the-data"></a>Rivedere i dati

Nel set di dati originale gli identificatori di taxi e i record delle corse si trovavano in file separati. Tuttavia, per semplificare l'utilizzo dei dati di esempio, i due set di dati originali sono stati uniti nelle colonne _medallion_, _hack_license_e _pickup_datetime_.  È stato eseguito anche un campionamento dei record in modo da ottenere solo l'1% del numero di record originale. Il set di dati ridotto risultante include 1.703.957 righe e 23 colonne.

**Identificatori di taxi**

- La colonna _medallion_ rappresenta l'ID univoco del taxi.
- La colonna _hack_license_ contiene il numero di patente del tassista (in forma anonima) .

**Record delle corse e delle tariffe**

- Il record di ogni corsa include il luogo e l'ora di inizio e fine della corsa e la distanza percorsa.
- Il record di ogni tariffa include i dati del pagamento, ad esempio il tipo di pagamento, l'importo totale e l'importo della mancia.
- Le ultime tre colonne possono essere usate per diverse attività di apprendimento automatico.  La colonna _tip_amount_ contiene valori numerici continui e può essere usata come colonna **label** per l'analisi della regressione. La colonna _tipped_ include solo valori sì/no e viene usata per la classificazione binaria. La colonna _tip_class_ include più **etichette di classe** e può essere quindi usata come etichetta per le attività di classificazione multiclasse.
- I valori usati per le colonne etichetta sono basati sulla colonna _tip_amount_ usando le regole di business seguenti:
  
    |Nome colonna derivata|Rule|
    |-|-|
     |tipped|Se tip_amount > 0, tipped = 1, altrimenti tipped = 0|
    |tip_class|Classe 0: tip_amount = $0<br /><br />Classe 1: tip_amount > $0 e tip_amount <= $5<br /><br />Classe 2: tip_amount > $5 e tip_amount <= $10<br /><br />Classe 3: tip_amount > $10 e tip_amount <= $20<br /><br />Classe 4: tip_amount > $20|

## <a name="create-plots-using-python-in-t-sql"></a>Creare grafici usando Python in T-SQL

Poiché la visualizzazione è un potente strumento per le informazioni sulla distribuzione dei dati e gli outlier, Python fornisce molti pacchetti per la visualizzazione dati. Il **matplotlib** modulo è una libreria comune che include numerose funzioni per la creazione di istogrammi, grafici a dispersione, casella grafici e altri grafici di esplorazione dei dati.

In questa sezione si apprenderà come usare i grafici tramite le stored procedure. Archiviare il `plot` Python oggetto come un **varbinary** dati digitare e salvare i grafici generati nel server.

### <a name="storing-plots-as-varbinary-data-type"></a>Archiviazione dei grafici come tipo di dati varbinary

Il **revoscalepy** modulo incluso in servizi di SQL Server 2017 Machine Learning contiene le librerie analoghe alle librerie R nel pacchetto RevoScaleR. In questo esempio, si userà l'equivalente di Python di `rxHistogram` per tracciare un istogramma in base ai dati da un [!INCLUDE[tsql](../../includes/tsql-md.md)] query. Per rendere più semplice, si esegue il wrapping in una stored procedure, _PlotHistogram_.

La stored procedure restituisce un Python serializzato `figure` oggetto come flusso di **varbinary** dati. Non è possibile visualizzare direttamente i dati binari, ma è possibile usare il codice Python da deserializzare e visualizzare le cifre nel client e quindi salvare il file di immagine in un computer client.

### <a name="create-the-stored-procedure-plotspython"></a>Creare la stored procedure Plots_Python

1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], aprire una nuova **Query** finestra.

2.  Selezionare il database per la procedura dettagliata e creare la stored procedure usando l'istruzione seguente. Se necessario, assicurarsi di modificare il codice per usare il nome di tabella corretto.
  
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
**Note:**

- La variabile `@query` definisce il testo della query (`'SELECT tipped FROM nyctaxi_sample'`), che viene passato al blocco di codice Python come argomento per la variabile di input di script, `@input_data_1`.
- Lo script Python è piuttosto semplice: **matplotlib** `figure` gli oggetti vengono utilizzati per eseguire il tracciato istogramma e a dispersione e questi oggetti vengono quindi serializzati utilizzando il `pickle` libreria.
- L'oggetto graphics Python serializzato in un Python **pandas** frame di dati per l'output.

### <a name="output-varbinary-data-to-viewable-graphics-file"></a>Dati varbinary di output al file immagine visualizzabile

1.  In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]eseguire l'istruzione seguente:
  
    ```
    EXEC [dbo].[SerializePlots]
    ```
  
    **Risultati**
  
    *tracciato*
    *0xFFD8FFE000104A4649... * 
     *0xFFD8FFE000104A4649... * 
     *0xFFD8FFE000104A4649... * 
     *0xFFD8FFE000104A4649...*

  
2.  Nel computer client, eseguire il seguente codice Python, sostituendo il nome del server, nome del database e le credenziali come appropriato.
  
    **Per l'autenticazione di SQL server:**
    
        ```python
        import pyodbc
        import pickle
        import os
        cnxn = pyodbc.connect('DRIVER={SQL Server};SERVER={SERVER_NAME};DATABASE={DB_NAME};UID={USER_NAME};PWD={PASSOWRD}')
        cursor = cnxn.cursor()
        cursor.execute("EXECUTE [dbo].[SerializePlots]")
        tables = cursor.fetchall()
        for i in range(0, len(tables)):
            fig = pickle.loads(tables[i][0])
            fig.savefig(str(i)+'.png')
        print("The plots are saved in directory: ",os.getcwd())
        ```  
    **Per l'autenticazione di Windows:**

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

    > [!NOTE]
    > Verificare che la versione di Python è lo stesso per il client e server. Inoltre, assicurarsi che le librerie di Python in uso nel client (ad esempio matplotlib) sono della versione uguale o maggiore rispetto delle librerie installate nel server.


3.  Se la connessione ha esito positivo, verrà visualizzato i seguenti risultati
  
    *I grafici vengono salvati nella directory: xxxx*
  
4.  Il file di output verrà creato nella directory di lavoro di Python. Per visualizzare il tracciato, è sufficiente aprire la cartella di lavoro di Python. La figura seguente mostra un tracciato di esempio viene salvato nel computer client.
  
    ![Suggerimento quantità tariffa di vs quantità](media/sqldev-python-sample-plot.png "quantità tariffa di suggerimento quantità vs") 

## <a name="next-step"></a>Passaggio successivo

[Passaggio 4: Creare funzionalità di dati mediante T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

## <a name="previous-step"></a>Passaggio precedente

[Passaggio 2: Importare i dati in SQL Server usando PowerShell](sqldev-py2-import-data-to-sql-server-using-powershell.md)

## <a name="see-also"></a>Vedere anche

[Servizi di Machine Learning con Python](../python/sql-server-python-services.md)

