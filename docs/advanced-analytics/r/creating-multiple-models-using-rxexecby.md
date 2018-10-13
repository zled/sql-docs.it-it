---
title: Creazione di più modelli usando rxExecBy (SQL Server Machine Learning Services) | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: b83abad65689e3e12310251d09199f5aa0e7c3cb
ms.sourcegitcommit: 0d6e4cafbb5d746e7d00fdacf8f3ce16f3023306
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/11/2018
ms.locfileid: "49085127"
---
# <a name="creating-multiple-models-using-rxexecby"></a>Creazione di più modelli con rxExecBy
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server 2017 CTP 2.0 include una nuova funzione **rxExecBy**, che supporta l'elaborazione parallela di più modelli correlati. Anziché train un modello di dimensioni molto grande basato sui dati da più entità simile, il data scientist molto rapidamente possibile creare molti modelli correlati, ognuna con i dati specifici di una singola entità.

Si supponga, ad esempio, si è un monitoraggio degli errori del dispositivo e acquisizione dei dati per molti tipi diversi di apparecchiature. Usando rxExecBy, è possibile fornire un singolo set di dati di grandi dimensioni come input, specificare una colonna in cui clinico il set di dati, ad esempio tipo di dispositivo e quindi creare più modelli per i singoli dispositivi.

Questo processo è stato detto "piacevolmente parallel" Processing, elaborazione, perché richiede un'attività che è stato alquanto oneroso per il data scientist o quantomeno noioso e la rende un'operazione semplice e veloce.

Le applicazioni tipiche di questo approccio includono previsione per singoli contatori intelligenti componenti del nucleo familiare, la creazione di proiezioni dei ricavi per le linee di prodotti separata o creazione di modelli per le approvazioni del prestito personalizzate in base ai rami singoli bank.

## <a name="how-rxexec-works"></a>Come funziona rxExec

La funzione rxExecBy in RevoScaleR è progettata per l'elaborazione su un numero elevato di piccoli set di dati parallela con volumi elevati.

1. Chiamare la funzione rxExecBy come parte del codice R e passare un set di dati non ordinati.
2. Specificare la partizione mediante il quale i dati devono essere raggruppati e ordinati.
3. Definisce una trasformazione o una funzione che deve essere applicato a ogni partizione di dati di modellazione
4. Quando viene eseguita la funzione, le query di dati vengono elaborate in parallelo se l'ambiente lo supporta. Inoltre, le attività di modellazione o trasformazione vengono distribuite tra core singoli ed eseguite in parallelo. Contesto di calcolo supportati per tre operazioni includono RxSpark e RxInSQLServer.
5. Vengono restituiti più risultati.

## <a name="rxexecby-syntax-and-examples"></a>rxExecBy sintassi ed esempi

**rxExecBy** accetta quattro specifica di input, uno degli input da un oggetto origine dati o set di dati che può essere partizionato in uno specifico **chiave** colonna. La funzione restituisce un output per ogni partizione. Il formato dell'output dipende dalla funzione che viene passata come argomento, ad esempio, se si passa una funzione di modellazione, ad esempio rxLinMod, è possibile restituire un modello con training separato per ogni partizione del set di dati.

### <a name="supported-functions"></a>Funzioni supportate

Modellazione delle minacce: `rxLinMod`, `rxLogit`, `rxGlm`, `rxDtree`

Assegnazione di punteggi: `rxPredict`,

Trasformazione o l'analisi: `rxCovCor`

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato come creare più modelli utilizzando il set di dati relativi alle compagnie aeree, che viene partizionata sulla colonna [DayOfWeek]. La funzione definita dall'utente, `delayFunc`, viene applicata a ognuna delle partizioni da rxExecBy chiamante. La funzione Crea modelli separati per lunedì, martedì, e così via.

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

Se viene visualizzato l'errore, `varsToPartition is invalid`, controllare se il nome della colonna chiave o colonne sia stato digitato correttamente. Il linguaggio R è tra maiuscole e minuscole.

Si noti che questo esempio non è ottimizzato per SQL Server e in molti casi cui è possibile ottenere prestazioni migliori utilizzando SQL per raggruppare i dati. Tuttavia, usando rxExecBy, è possibile creare processi paralleli da R.

Nell'esempio seguente illustra il processo in R usando SQL Server come contesto di calcolo:

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


