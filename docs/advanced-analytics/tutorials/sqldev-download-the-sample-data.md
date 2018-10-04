---
title: Scaricare i dati demo dei Taxi di NYC e gli script per embedded R e Python (SQL Server Machine Learning) | Microsoft Docs
description: Istruzioni per scaricare i dati di esempio relativi ai taxi di New York City e creazione di un database. I dati vengono utilizzati nelle esercitazioni di SQL Server in cui viene illustrato come incorporare R e Python in SQL Server stored procedure e funzioni T-SQL.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/02/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 700720f7538467dc3edc38414544eb2c402437a6
ms.sourcegitcommit: 615f8b5063aed679495d92a04ffbe00451d34a11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48232575"
---
# <a name="nyc-taxi-demo-data-for-sql-server"></a>Dati demo dei Taxi di NYC per SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo illustra come ottenere i dati di esempio per le esercitazioni di R e Python per analitica nel database in SQL Server.

I dati provengono dal [NYC Taxi and Limousine Commission](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml) set di dati pubblico. Daremo uno snapshot del set di dati e acquisito uno percento dei dati disponibili per il database di esempio. Nel sistema, il file di backup di database è leggermente superiore a 90 MB, fornendo 1.7 milioni di righe nella tabella di dati primario.

Dopo aver terminato la procedura descritta in questo articolo, il **NYCTaxi_Sample** database è disponibile nell'istanza locale, che fornisce dati di demo per la formazione pratica. Il nome del database deve essere **NYCTaxi_Sample** se si desidera eseguire gli script di demo con alcuna modifica.

## <a name="prerequisites"></a>Prerequisiti

È necessaria una connessione a internet, i diritti di amministratore locale nel computer e un'istanza del motore di database.

È utile per avere [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) o un altro strumento per verificare la creazione di oggetti.

## <a name="download-demo-database"></a>Scaricare i database di esempio

Il database di esempio è un file di backup ospitato da Microsoft. Download di file inizia immediatamente quando si fa clic sul collegamento. 

Dimensioni del file sono di circa 90 MB.

1. Fare clic su [NYCTaxi_Sample.bak](https://sqlmldoccontent.blob.core.windows.net/sqlml/NYCTaxi_Sample.bak) per scaricare il file di backup di database.

2. Copiare il file C:\Program files\Microsoft SQL Server\MSSQL-istanza-name\MSSQL\Backup cartella.

3. In Management Studio, fare doppio clic **database** e selezionare **Ripristina file e filegroup**.

4. Immettere *NYCTaxi_Sample* come nome del database.

5. Fare clic su **dal dispositivo** e quindi aprire la pagina di selezione file per selezionare il file di backup. Fare clic su **Add** selezionare NYCTaxi_Sample.bak.

6. Selezionare il **ripristinare** casella di controllo e fare clic su **OK** per ripristinare il database.

## <a name="review-database-objects"></a>Esaminare gli oggetti di database
   
Verificare gli oggetti di database siano presenti nella [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Si dovrebbe essere il database, tabelle, funzioni e stored procedure.
  
   ![rsql_devtut_BrowseTables](media/rsql-devtut-browsetables.png "rsql_devtut_BrowseTables")

### <a name="objects-in-nyctaxisample-database"></a>Oggetti nel database NYCTaxi_Sample

La tabella seguente riepiloga gli oggetti creati nel database di esempio dei Taxi di NYC.

|**Nome oggetto**|**Tipo oggetto**|**Descrizione**|
|----------|------------------------|---------------|
|**NYCTaxi_Sample** | Database |Create dallo script create-db-tb-upload-data.sql. Crea un database e due tabelle:<br /><br />Nella tabella dbo. nyctaxi_sample: contiene il set di dati principale NYC Taxi. Alla tabella viene aggiunto un indice columnstore cluster per migliorare le prestazioni di archiviazione e query. Il campione dell'1% del set di dati dei Taxi di NYC viene inserito in questa tabella.<br /><br />tabella dbo.nyc_taxi_models: usato per rendere permanente il modello con training analitica avanzata.|
|**fnCalculateDistance** |funzione a valori scalari | Create dallo script fnCalculateDistance.sql. Calcola la distanza diretta tra posizioni di salita e. Questa funzione viene utilizzata [creare funzionalità di dati](sqldev-create-data-features-using-t-sql.md), [training e salvataggio di un modello](../r/sqldev-train-and-save-a-model-using-t-sql.md) e [Operazionalizzare il modello R](sqldev-operationalize-the-model.md).|
|**fnEngineerFeatures** |funzione con valori di tabella | Create dallo script fnEngineerFeatures.sql. Crea nuova funzionalità di dati per il training del modello. Questa funzione viene utilizzata [creare funzionalità di dati](sqldev-create-data-features-using-t-sql.md) e [Operazionalizzare il modello R](sqldev-operationalize-the-model.md).|
|**PlotHistogram** |stored procedure | Create dallo script PlotHistogram.sql. Chiama una funzione R per tracciare l'istogramma di una variabile e quindi restituisce il tracciato come oggetto binario. Questa stored procedure viene utilizzata [esplorare e visualizzare dati](sqldev-explore-and-visualize-the-data.md).|
|**PlotInOutputFiles** |stored procedure| Create dallo script PlotInOutputFiles.sql. Crea un elemento grafico tramite una funzione R e quindi l'output viene salvato come file PDF locale. Questa stored procedure viene utilizzata [esplorare e visualizzare dati](sqldev-explore-and-visualize-the-data.md).|
|**PersistModel** |stored procedure | Create dallo script PersistModel.sql. Accetta un modello che è stato serializzato in un tipo di dati varbinary e lo scrive nella tabella specificata. |
|**PredictTip**  |stored procedure |Create dallo script PredictTip.sql. Chiama il modello con training per creare stime tramite il modello. La stored procedure accetta una query come parametro di input e restituisce una colonna di valori numerici contenente i punteggi per le righe di input. Questa stored procedure viene utilizzata [Operazionalizzare il modello R](sqldev-operationalize-the-model.md).|
|**PredictTipSingleMode**  |stored procedure| Create dallo script PredictTipSingleMode.sql. Chiama il modello con training per creare stime tramite il modello. Questa stored procedure accetta una nuova osservazione come input, con i singoli valori della funzionalità passati come parametri in linea, e restituisce un valore che stima il risultato in base alla nuova osservazione. Questa stored procedure viene utilizzata [Operazionalizzare il modello R](sqldev-operationalize-the-model.md).|
|**TrainTipPredictionModel**  |stored procedure|Create dallo script TrainTipPredictionModel.sql. Esegue il training di un modello di regressione logistica mediante la chiamata di un pacchetto R. Il modello consente di stimare il valore della colonna indicata. Viene eseguito un training usando il 70% dei dati selezionati casualmente. L'output della stored procedure corrisponde al modello con training, che viene salvato nella tabella nyc_taxi_models. Questa stored procedure viene utilizzata [eseguire il training e salvataggio di un modello](../r/sqldev-train-and-save-a-model-using-t-sql.md).|

## <a name="query-data-for-verification"></a>Eseguire query sui dati per la verifica

Come passaggio di convalida, eseguire una query per verificare che i dati è stati caricati.

1. In Esplora oggetti, nel database, fare doppio clic il **NYCTaxi_Sample** , del database e avviare una nuova query.

2. Eseguire **`select * from dbo.nyctaxi_sample`** per restituire tutte le righe di milioni di 1.7.

## <a name="next-steps"></a>Passaggi successivi

I dati di esempio dei Taxi di NYC sono ora disponibili per la formazione pratica.

+ [Informazioni su analitica nel database con R in SQL Server](sqldev-in-database-r-for-sql-developers.md)