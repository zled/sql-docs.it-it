---
title: Ambiente di esercitazione preparare R lezione 2 tramite PowerShell (SQL Server Machine Learning) | Documenti Microsoft
description: Esercitazione che illustra come incorporare R in SQL Server funzioni e stored procedure T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/07/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 1280d7c82d48c8ed596271cd7a73fa13ec1664c7
ms.sourcegitcommit: b52b5d972b1a180e575dccfc4abce49af1a6b230
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2018
ms.locfileid: "35249744"
---
# <a name="lesson-2-set-up-the-tutorial-environment-using-powershell"></a>Lezione 2: Configurare l'ambiente dell'esercitazione tramite PowerShell
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo articolo fa parte di un'esercitazione per gli sviluppatori SQL su come usare il linguaggio R in SQL Server.

In questo passaggio, è necessario eseguire uno script di PowerShell per creare gli oggetti di database richiesti per la procedura dettagliata. Lo script crea e carica un database utilizzando i dati di esempio ottenuti nel passaggio precedente. Crea anche le funzioni e stored procedure utilizzate nel corso dell'esercitazione.

## <a name="create-and-load-database-objects"></a>Creare e caricare gli oggetti di database

Tra i file scaricati, verrà visualizzato uno script di PowerShell (`RunSQL_SQL_Walkthrough.ps1`) che consente di preparare l'ambiente per la procedura dettagliata. Con lo script vengono eseguite le azioni seguenti:

- Installare le utilità della riga di comando SQL, SQL Native Client se non è già installato. Queste utilità sono necessarie per il caricamento bulk dei dati nel database tramite **bcp**.

- Creare un database e tabelle nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza e inserimento bulk dei dati originati da un file CSV.

- Creare più funzioni SQL e stored procedure.

### <a name="modify-the-script-to-use-a-trusted-windows-identity"></a>Modificare lo script per l'utilizzo di un'identità di Windows trusted

Per impostazione predefinita, questo script presuppone che un account di accesso di SQL Server database utente e una password. Se si è db_owner con l'account utente di Windows, è possibile utilizzare la propria identità Windows per creare gli oggetti. A tale scopo, aprire `RunSQL_SQL_Walkthrough.ps1` in un editor di codice e aggiungere **`-T`** da parte di bcp bulk insert comando (riga 238):

```text
bcp $db_tb in $csvfilepath -t ',' -S $server -f taxiimportfmt.xml -F 2 -C "RAW" -b 200000 -U $u -P $p -T
```

### <a name="run-the-script-to-create-objects"></a>Eseguire lo script per creare oggetti

Aprire un prompt dei comandi di PowerShell come amministratore ed eseguire il comando seguente.
  
```ps
.\RunSQL_SQL_Walkthrough.ps1
```
Viene chiesto di immettere le informazioni seguenti:

- Istanza di server in cui [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] è stato installato. In un'istanza predefinita, questo può essere semplice come il nome del computer.

- Nome del database. Per questa esercitazione, gli script presuppongono `TaxiNYC_Sample`.

- Nome utente e password dell'utente. Immettere un account di accesso di database di SQL Server per questi valori. In alternativa, se è stato modificato lo script per l'accettazione di un'identità di Windows trusted, premere INVIO per lasciare vuoti questi valori. Identità di Windows viene utilizzato per la connessione.

- Nome file completo per i dati di esempio scaricati nella lezione precedente. Ad esempio: `C:\tempRSQL\nyctaxi1pct.csv`

Dopo aver fornito tali valori, lo script venga eseguito immediatamente. Durante l'esecuzione di script, tutti i nomi di segnaposto nel [!INCLUDE[tsql](../../includes/tsql-md.md)] gli script vengono aggiornati per l'utilizzo di input è fornire.

## <a name="review-database-objects"></a>Riesamina gli oggetti di database
   
Al termine dell'esecuzione dello script, verificare gli oggetti di database presenti nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Si dovrebbe essere il database, tabelle, funzioni e stored procedure.
  
   ![rsql_devtut_BrowseTables](media/rsql-devtut-browsetables.png "rsql_devtut_BrowseTables")

> [!NOTE]
> Se gli oggetti di database sono già esistenti, non possono essere creati nuovamente.
>   
> Se la tabella è già esistente, i dati saranno aggiunti senza sovrascrivere. Assicurarsi pertanto di eliminare tutti gli oggetti esistenti prima di eseguire lo script.

## <a name="objects-used-in-this-tutorial"></a>Oggetti utilizzati in questa esercitazione

Nella tabella seguente sono riepilogati gli oggetti creati in questa lezione. Anche se si esegue solo uno script di PowerShell (`RunSQL_SQL_Walkthrough.ps1`), lo script richiama gli altri script SQL per creare gli oggetti nel database. Script utilizzato per creare ciascun oggetto sono indicate nella descrizione.

|**Nome oggetto**|**Tipo oggetto**|**Descrizione**|
|----------|------------------------|---------------|
|**TaxiNYC_Sample** | Database |Creato tramite lo script crea-db-tb-caricamento-data.sql. Crea un database e due tabelle:<br /><br />tabella dbo.nyctaxi_sample: contiene il set di dati NYC Taxi principale. Alla tabella viene aggiunto un indice columnstore cluster per migliorare le prestazioni di archiviazione e query. L'esempio di % 1 del set di dati NYC Taxi viene inserita in questa tabella.<br /><br />tabella dbo.nyc_taxi_models: utilizzato per mantenere il modello con training analitica avanzate.|
|**fnCalculateDistance** |funzione a valori scalari | Creata dallo script fnCalculateDistance.sql. Calcola la distanza tra i percorsi di ritiro e dropoff diretta. Questa funzione viene utilizzata [creare le funzionalità di data](../tutorials/sqldev-create-data-features-using-t-sql.md), [Train e salvare un modello](sqldev-train-and-save-a-model-using-t-sql.md) e [rendere operativo il modello R](../tutorials/sqldev-operationalize-the-model.md).|
|**fnEngineerFeatures** |funzione con valori di tabella | Creata dallo script fnEngineerFeatures.sql. Crea nuova funzionalità di dati per il training del modello. Questa funzione viene utilizzata [creare le funzionalità di data](../tutorials/sqldev-create-data-features-using-t-sql.md) e [rendere operativo il modello R](../tutorials/sqldev-operationalize-the-model.md).|
|**PlotHistogram** |stored procedure | Creata dallo script PlotHistogram.sql. Chiama una funzione R per tracciare l'istogramma di una variabile e quindi restituisce il tracciato come un oggetto binario. Questa stored procedure viene utilizzata [esplorare e visualizzare dati](../tutorials/sqldev-explore-and-visualize-the-data.md).|
|**PlotInOutputFiles** |stored procedure| Creata dallo script PlotInOutputFiles.sql. Crea un'immagine utilizzando una funzione di R e quindi l'output viene salvato come file PDF locale. Questa stored procedure viene utilizzata [esplorare e visualizzare dati](../tutorials/sqldev-explore-and-visualize-the-data.md).|
|**PersistModel** |stored procedure | Creata dallo script PersistModel.sql. Accetta un modello che è stato serializzato in un tipo di dati varbinary e lo scrive nella tabella specificata. |
|**PredictTip**  |stored procedure |Creata dallo script PredictTip.sql. Chiama il modello con training per creare stime tramite il modello. La stored procedure accetta una query come parametro di input e restituisce una colonna di valori numerici contenente i punteggi per le righe di input. Questa stored procedure viene utilizzata [rendere operativo il modello R](../tutorials/sqldev-operationalize-the-model.md).|
|**PredictTipSingleMode**  |stored procedure| Creata dallo script PredictTipSingleMode.sql. Chiama il modello con training per creare stime tramite il modello. Questa stored procedure accetta una nuova osservazione come input, con i singoli valori della funzionalità passati come parametri in linea, e restituisce un valore che stima il risultato in base alla nuova osservazione. Questa stored procedure viene utilizzata [rendere operativo il modello R](../tutorials/sqldev-operationalize-the-model.md).|
|**TrainTipPredictionModel**  |stored procedure|Creata dallo script TrainTipPredictionModel.sql. Esegue il training di un modello di regressione logistica chiamando un pacchetto R. Il modello consente di stimare il valore della colonna indicata. Viene eseguito un training usando il 70% dei dati selezionati casualmente. L'output della stored procedure corrisponde al modello con training, che viene salvato nella tabella nyc_taxi_models. Questa stored procedure viene utilizzata [Train e salvare un modello](sqldev-train-and-save-a-model-using-t-sql.md).|

## <a name="next-lesson"></a>Lezione successiva

[Lezione 3: Esplorare e visualizzare i dati](../tutorials/sqldev-explore-and-visualize-the-data.md)

## <a name="previous-lesson"></a>Lezione precedente

[Lezione 1: Scaricare i dati di esempio](../tutorials/sqldev-download-the-sample-data.md)
