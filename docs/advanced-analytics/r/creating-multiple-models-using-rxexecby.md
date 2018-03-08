---
title: "Creazione di più modelli utilizzando rxExecBy | Documenti Microsoft"
ms.custom: 
ms.date: 04/18/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 685833317453c1ed5765385a73ff892a85989c2c
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2018
---
# <a name="creating-multiple-models-using-rxexecby"></a>Creazione di più modelli utilizzando rxExecBy
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server 2017 CTP 2.0 include una nuova funzione **rxExecBy**, che supporta l'elaborazione parallela di più modelli correlati. Anziché train un modello di dimensioni molto grande in base ai dati da più entità simile, l'esperto di dati è possibile creare rapidamente molti modelli correlati, ognuna con dati specifici di una singola entità.

Si supponga, ad esempio, si monitoraggio degli errori del dispositivo e l'acquisizione dei dati per molti tipi diversi di apparecchiature. Tramite rxExecBy, è possibile fornire un singolo set di dati di grandi dimensioni come input, specificare una colonna in cui il set di dati, ad esempio il tipo di dispositivo, stratificazione e quindi creare più modelli di modelli per i singoli dispositivi.

Questo processo è stato definito l'elaborazione "piacevolmente parallela", poiché accetta un'attività che è stata in qualche modo oneroso per il data scientist o noiosa nella migliore delle ipotesi e lo rende un'operazione semplice e veloce.

Le applicazioni tipiche di questo approccio includono previsioni per singoli metri smart familiari, la creazione di proiezioni sui ricavi per le linee di prodotto separato o creazione di modelli per l'approvazione del prestito personalizzati in base ai rami bank singoli.

## <a name="how-rxexec-works"></a>Funzionamento di rxExec

La funzione rxExecBy in RevoScaleR è progettata per l'elaborazione su un numero elevato di set di dati di piccole dimensioni parallela di volumi elevati.

1. Chiamare la funzione rxExecBy come parte del codice R e passare un set di dati di dati non ordinati.
2. Specificare la partizione mediante il quale i dati devono essere raggruppati e ordinati.
3. Definisce una trasformazione o una funzione che deve essere applicato a ogni partizione di dati di modellazione
4. Quando viene eseguita la funzione, le query di dati vengono elaborate in parallelo se l'ambiente lo supporta. Inoltre, le attività di modellazione o trasformazione vengono distribuite a core singoli ed eseguite in parallelo. Contesto di calcolo supportati per tre operazioni includono RxSpark e RxInSQLServer.
5. Vengono restituiti più risultati.

## <a name="rxexecby-syntax-and-examples"></a>rxExecBy sintassi ed esempi

**rxExecBy** accetta quattro input, uno degli input da un oggetto origine dati o set di dati che può essere partizionato in uno specifico **chiave** colonna. La funzione restituisce un output per ogni partizione. Il formato dell'output dipende dalla funzione che viene passata come argomento, ad esempio, se si passa una funzione di modellazione, ad esempio rxLinMod, è possibile restituire un modello con training separato per ogni partizione del set di dati.

### <a name="supported-functions"></a>Funzioni supportate

Modellazione: `rxLinMod`, `rxLogit`, `rxGlm`,`rxDtree`

Assegnazione dei punteggi: `rxPredict`,

Trasformazione o l'analisi:`rxCovCor`

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato come creare più modelli utilizzando il set di dati Airline partizionata sulla colonna [DayOfWeek]. La funzione definita dall'utente, `delayFunc`, per rxExecBy chiamante viene applicato a ognuna delle partizioni. La funzione Crea modelli separati per lunedì, martedì, e così via.

```SQL
EXEC sp_execute_external_script
@language = N'R'
, @script = N'
delayFunc <- function(key, data, params) { 
    df <- rxImport(inData = airlineData) 
    rxLinMod(ArrDelay ~ CRSDepTime, data = df) 
} 
OutputDataSet <- rxExecBy(airlineData, c("DayOfWeek"), delayFunc)
'
, @input_data_1 = N'select ArrDelay, DayOfWeek, CRSDepTime from AirlineDemoSmall]'
, @input_data_1_name = N'airlineData'

```

Se viene visualizzato l'errore, `varsToPartition is invalid`, controllare se il nome della colonna chiave o delle colonne sia stato digitato correttamente. Il linguaggio R è tra maiuscole e minuscole.

Si noti che in questo esempio non è ottimizzato per SQL Server e in molti casi cui è possibile ottenere prestazioni migliori tramite SQL per raggruppare i dati. Tuttavia, utilizza rxExecBy, è possibile creare processi paralleli da R.

L'esempio seguente illustra il processo di R, utilizzando SQL Server come contesto di calcolo:

```R
sqlServerConnString <- "SERVER=hostname;DATABASE=TestDB;UID=DBUser;PWD=Password;"
inTable <- paste("airlinedemosmall")
sqlServerDataDS <- RxSqlServerData(table = inTable, connectionString = sqlServerConnString)

# user function
".Count" <- function(keys, data, params)
{
  myDF <- rxImport(inData = data)
  return (nrow(myDF))
}

# Set SQL Server compute context with level of parallelism = 2
sqlServerCC <- RxInSqlServer(connectionString = sqlServerConnString, numTasks = 4)
rxSetComputeContext(sqlServerCC)

# Execute rxExecBy in SQL Server compute context
sqlServerCCResults <- rxExecBy(inData = sqlServerDataDS, keys = c("DayOfWeek"), func = .Count)
```


