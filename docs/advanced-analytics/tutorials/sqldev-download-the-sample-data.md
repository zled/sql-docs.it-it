---
title: Scaricare i dati demo dei Taxi di NYC e gli script per embedded R e Python (SQL Server Machine Learning) | Microsoft Docs
description: Istruzioni per scaricare i dati di esempio relativi ai taxi di New York City e creazione di un database. I dati vengono utilizzati nelle esercitazioni di SQL Server in cui viene illustrato come incorporare R e Python in SQL Server stored procedure e funzioni T-SQL.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/22/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 6d5030287e7ad526816f89fd23b13fedae070c56
ms.sourcegitcommit: 320958d0f55b6974abf46f8a04f7a020ff86a0ae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2018
ms.locfileid: "42703604"
---
# <a name="nyc-taxi-demo-data-for-sql-server"></a>Dati demo dei Taxi di NYC per SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo prepara il sistema per le esercitazioni su come usare R e Python per analitica nel database in SQL Server.

In questo esercizio si scaricherà i dati di esempio, uno script di PowerShell per la preparazione dell'ambiente, e [!INCLUDE[tsql](../../includes/tsql-md.md)] file di script usati in diverse esercitazioni. Al termine, un **NYCTaxi_Sample** database è disponibile nell'istanza locale, che fornisce dati di demo per la formazione pratica. 

## <a name="prerequisites"></a>Prerequisiti

È necessario una connessione a internet, PowerShell e i diritti amministrativi locali sul computer. È necessario disporre [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) o un altro strumento per verificare la creazione di oggetti.

## <a name="download-nyc-taxi-demo-data-and-scripts-from-github"></a>Scaricare i dati demo dei Taxi di NYC e gli script da Github

1.  Aprire una console dei comandi di Windows PowerShell.
  
    Usare la **Esegui come amministratore** scegliere di creare la directory di destinazione oppure per scrivere file nella destinazione specificata.
  
2.  Eseguire i seguenti comandi di PowerShell modificando il valore del parametro *DestDir* in una directory locale. Il valore predefinito usato in questo caso è **TempRSQL**.
  
    ```ps
    $source = ‘https://raw.githubusercontent.com/Azure/Azure-MachineLearning-DataScience/master/Misc/RSQL/Download_Scripts_SQL_Walkthrough.ps1’  
    $ps1_dest = “$pwd\Download_Scripts_SQL_Walkthrough.ps1”
    $wc = New-Object System.Net.WebClient
    $wc.DownloadFile($source, $ps1_dest)
    .\Download_Scripts_SQL_Walkthrough.ps1 –DestDir ‘C:\tempRSQL’
    ```
  
    Se la cartella *DestDir* specificata non esiste, verrà creata dallo script di PowerShell.
  
    > [!TIP]
    > Se si verifica un errore, è possibile impostare temporaneamente i criteri per l'esecuzione di script di PowerShell per **senza restrizioni** solo per questa procedura dettagliata usando l'argomento Bypass e le modifiche alla sessione corrente di ambito.
    >   
    >````
    > Set\-ExecutionPolicy Bypass \-Scope Process
    >````
    > Questo comando non comporta una modifica della configurazione.
  
    A seconda della connessione Internet, il download potrebbe richiedere alcuni minuti.
  
3.  Quando tutti i file sono stati scaricati, lo script di PowerShell viene aperto per la *DestDir* cartella. Nel prompt dei comandi di PowerShell eseguire il comando seguente ed esaminare i file scaricati.
  
    ```
    ls
    ```
  
    **Risultati:**
  
    ![Elenco dei file scaricati dallo script di PowerShell](media/rsql-devtut-filelist.png "Elenco dei file scaricati dallo script di PowerShell")

## <a name="create-nyctaxisample-database"></a>Creare database NYCTaxi_Sample

Tra i file scaricati, dovrebbe essere uno script di PowerShell (**RunSQL_SQL_Walkthrough.ps1**) che crea un database e di caricamento bulk dei dati. Con lo script vengono eseguite le azioni seguenti:

+ Installa il Client nativo di SQL e le utilità della riga di comando SQL, se non è già installato. Queste utilità sono necessarie per il caricamento bulk dei dati nel database tramite **bcp**.

+ Creare un database e tabelle nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di istanza e inserimento bulk dei dati originati da un file con estensione csv.

+ Creare più funzioni SQL e stored procedure utilizzate in diverse esercitazioni.

### <a name="modify-the-script-to-use-a-trusted-windows-identity"></a>Modificare lo script per usare un'identità Windows attendibile

Per impostazione predefinita, lo script si presuppone un accesso utente di database di SQL Server e una password. Se sei db_owner con l'account utente di Windows, è possibile usare l'identità di Windows per creare gli oggetti. A tale scopo, aprire `RunSQL_SQL_Walkthrough.ps1` in un editor di codice e di aggiunta **`-T`** per l'utilità bcp bulk insert comando (riga 238):

```text
bcp $db_tb in $csvfilepath -t ',' -S $server -f taxiimportfmt.xml -F 2 -C "RAW" -b 200000 -U $u -P $p -T
```

### <a name="run-the-script-to-create-objects"></a>Eseguire lo script per creare oggetti

Usando un prompt dei comandi di PowerShell come amministratore in C:\tempRSQL, eseguire il comando seguente.
  
```ps
.\RunSQL_SQL_Walkthrough.ps1
```
Viene chiesto di immettere le informazioni seguenti:

- Server istanza in cui [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] sia stato installato. In un'istanza predefinita, questo può essere semplice come nome del computer.

- Nome del database. Per questa esercitazione, gli script presuppongono `NYCTaxi_Sample`.

- Nome utente e password dell'utente. Immettere un account di accesso di database di SQL Server per questi valori. In alternativa, se è stato modificato lo script per l'accettazione di un'identità di Windows trusted, premere INVIO per lasciare questi valori vuoto. La connessione viene utilizzata l'identità Windows.

- Nome completo del file per i dati di esempio scaricati nella lezione precedente. Ad esempio: `C:\tempRSQL\nyctaxi1pct.csv`

Dopo aver impostato questi valori, lo script viene eseguito immediatamente. Durante l'esecuzione di script, tutti i nomi di segnaposto nel [!INCLUDE[tsql](../../includes/tsql-md.md)] gli script sono stati aggiornati per usare l'input è fornire.

## <a name="review-database-objects"></a>Esaminare gli oggetti di database
   
Al termine dell'esecuzione dello script, verificare gli oggetti di database siano presenti nella [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Si dovrebbe essere il database, tabelle, funzioni e stored procedure.
  
   ![rsql_devtut_BrowseTables](media/rsql-devtut-browsetables.png "rsql_devtut_BrowseTables")

> [!NOTE]
> Se gli oggetti di database sono già esistenti, non possono essere creati nuovamente.
>   
> Se la tabella è già esistente, i dati saranno aggiunti senza sovrascrivere. Assicurarsi pertanto di eliminare tutti gli oggetti esistenti prima di eseguire lo script.

### <a name="objects-in-nyctaxisample-database"></a>Oggetti nel database NYCTaxi_Sample

La tabella seguente riepiloga gli oggetti creati nel database di esempio dei Taxi di NYC. Anche se si esegue solo uno script di PowerShell (`RunSQL_SQL_Walkthrough.ps1`), lo script chiama altri script SQL, a sua volta per creare gli oggetti nel database. Gli script usati per creare ogni oggetto sono indicati nella descrizione.

|**Nome oggetto**|**Tipo oggetto**|**Descrizione**|
|----------|------------------------|---------------|
|**TaxiNYC_Sample** | Database |Create dallo script create-db-tb-upload-data.sql. Crea un database e due tabelle:<br /><br />Nella tabella dbo. nyctaxi_sample: contiene il set di dati principale NYC Taxi. Alla tabella viene aggiunto un indice columnstore cluster per migliorare le prestazioni di archiviazione e query. Il campione dell'1% del set di dati dei Taxi di NYC viene inserito in questa tabella.<br /><br />tabella dbo.nyc_taxi_models: usato per rendere permanente il modello con training analitica avanzata.|
|**fnCalculateDistance** |funzione a valori scalari | Create dallo script fnCalculateDistance.sql. Calcola la distanza diretta tra posizioni di salita e. Questa funzione viene utilizzata [creare funzionalità di dati](sqldev-create-data-features-using-t-sql.md), [training e salvataggio di un modello](../r/sqldev-train-and-save-a-model-using-t-sql.md) e [Operazionalizzare il modello R](sqldev-operationalize-the-model.md).|
|**fnEngineerFeatures** |funzione con valori di tabella | Create dallo script fnEngineerFeatures.sql. Crea nuova funzionalità di dati per il training del modello. Questa funzione viene utilizzata [creare funzionalità di dati](sqldev-create-data-features-using-t-sql.md) e [Operazionalizzare il modello R](sqldev-operationalize-the-model.md).|
|**PlotHistogram** |stored procedure | Create dallo script PlotHistogram.sql. Chiama una funzione R per tracciare l'istogramma di una variabile e quindi restituisce il tracciato come oggetto binario. Questa stored procedure viene utilizzata [esplorare e visualizzare dati](sqldev-explore-and-visualize-the-data.md).|
|**PlotInOutputFiles** |stored procedure| Create dallo script PlotInOutputFiles.sql. Crea un elemento grafico tramite una funzione R e quindi l'output viene salvato come file PDF locale. Questa stored procedure viene utilizzata [esplorare e visualizzare dati](sqldev-explore-and-visualize-the-data.md).|
|**PersistModel** |stored procedure | Create dallo script PersistModel.sql. Accetta un modello che è stato serializzato in un tipo di dati varbinary e lo scrive nella tabella specificata. |
|**PredictTip**  |stored procedure |Create dallo script PredictTip.sql. Chiama il modello con training per creare stime tramite il modello. La stored procedure accetta una query come parametro di input e restituisce una colonna di valori numerici contenente i punteggi per le righe di input. Questa stored procedure viene utilizzata [Operazionalizzare il modello R](sqldev-operationalize-the-model.md).|
|**PredictTipSingleMode**  |stored procedure| Create dallo script PredictTipSingleMode.sql. Chiama il modello con training per creare stime tramite il modello. Questa stored procedure accetta una nuova osservazione come input, con i singoli valori della funzionalità passati come parametri in linea, e restituisce un valore che stima il risultato in base alla nuova osservazione. Questa stored procedure viene utilizzata [Operazionalizzare il modello R](sqldev-operationalize-the-model.md).|
|**TrainTipPredictionModel**  |stored procedure|Create dallo script TrainTipPredictionModel.sql. Esegue il training di un modello di regressione logistica mediante la chiamata di un pacchetto R. Il modello consente di stimare il valore della colonna indicata. Viene eseguito un training usando il 70% dei dati selezionati casualmente. L'output della stored procedure corrisponde al modello con training, che viene salvato nella tabella nyc_taxi_models. Questa stored procedure viene utilizzata [eseguire il training e salvataggio di un modello](../r/sqldev-train-and-save-a-model-using-t-sql.md).|

## <a name="next-steps"></a>Passaggi successivi

I dati di esempio dei Taxi di NYC sono ora disponibili per la formazione pratica.

+ [Informazioni su analitica nel database con R in SQL Server](sqldev-in-database-r-for-sql-developers.md)