---
title: Eseguire analisi di suddivisione in blocchi utilizzando rxDataStep (SQL e R approfondimento) | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 5db0acfb90c200442489cd7c3ec464223195eec6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="perform-chunking-analysis-using-rxdatastep-sql-and-r-deep-dive"></a>Eseguire analisi di suddivisione in blocchi utilizzando rxDataStep (SQL e R approfondimento)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo fa parte dell'esercitazione approfondimento di analisi scientifica dei dati, su come usare [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) con SQL Server.

In questa lezione, utilizza il **rxDataStep** funzione per elaborare i dati in blocchi, anziché richiedere che l'intero set di dati essere caricati in memoria ed elaborati in una sola volta, come r tradizionale. Il **rxDataStep** funzioni legge i dati in blocco, si applica funzioni R per ogni blocco di dati e quindi Salva i risultati di riepilogo per ogni blocco di un comune [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] origine dati. Quando tutti i dati sono stati letti, i risultati vengono combinati.

> [!TIP]
> Per questa lezione, si consente di calcolare una tabella di emergenza utilizzando il `table` funzione in R. In questo esempio è destinato solo a scopo informativo. 
> 
> Se è necessario per il set di dati reali tabulare, è consigliabile utilizzare il **rxCrossTabs** o **rxCube** funzioni in **RevoScaleR**, ottimizzati per l'ordinamento di operazione.

## <a name="partition-data-by-values"></a>Partizionare i dati dai valori

1. Creare una funzione R personalizzata che chiama l'oggetto R `table` funzione in ogni blocco di dati e il nome della nuova funzione `ProcessChunk`.
  
    ```R
    ProcessChunk <- function( dataList) {
    # Convert the input list to a data frame and compute contingency table
    chunkTable <- table(as.data.frame(dataList))
  
    # Convert table output to a data frame with a single row
    varNames <- names(chunkTable)
    varValues <- as.vector(chunkTable)
    dim(varValues) <- c(1, length(varNames))
    chunkDF <- as.data.frame(varValues)
    names(chunkDF) <- varNames
  
    # Return the data frame, which has a single row
    return( chunkDF )
    }
    ```

2. Impostare il contesto di calcolo server.
  
    ```R
    rxSetComputeContext( sqlCompute )
    ```
  
3. Definire un'origine dati di SQL Server per contenere i dati che si sta elaborando. assegnando prima una query SQL a una variabile. Quindi, utilizzare tale variabile nel *sqlQuery* argomento di un nuovo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] origine dati.
  
  
    ```R
    dayQuery <-  "SELECT DayOfWeek FROM AirDemoSmallTest"
    inDataSource <- RxSqlServerData(sqlQuery = dayQuery,
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",
            levels = as.character(1:7))))
    ```
4. Facoltativamente, è possibile eseguire **rxGetVarInfo** su questa origine dati. A questo punto, contiene una singola colonna: *Var 1: DayOfWeek, digitare: non refactoring, a fattori sono disponibili livelli*
     
5. Prima di applicare questa variabile di fattore all'origine dati, creare una tabella separata in cui includere i risultati intermedi. Nuovamente, solo la funzione RxSqlServerData per definire i dati, makign assicurarsi di eliminare tutte le tabelle esistenti con lo stesso nome.
  
    ```R
    iroDataSource = RxSqlServerData(table = "iroResults",   connectionString = sqlConnString)
    # Check whether the table already exists.
    if (rxSqlServerTableExists(table = "iroResults",  connectionString = sqlConnString))  { rxSqlServerDropTable( table = "iroResults", connectionString = sqlConnString) }
    ```
  
7.  Chiamare la funzione personalizzata `ProcessChunk` per trasformare i dati in fase di lettura, utilizzando come il *transformFunc* argomento per il **rxDataStep** (funzione).
  
    ```R
    rxDataStep( inData = inDataSource, outFile = iroDataSource, transformFunc = ProcessChunk, overwrite = TRUE)
    ```
  
8.  Per visualizzare i risultati intermedi di `ProcessChunk`, assegnare i risultati di **rxImport** a una variabile e quindi i risultati alla console.
  
    ```R
    iroResults <- rxImport(iroDataSource)
    iroResults
    ```

**Risultati parziali**

|      |    1  |   2   |  3   |  4   |  5  |   6   |  7 |
| --- | ---  | --- | ---  |  ---  | ---  | ---  | --- |
| 1 | 8228 | 8924 | 6916 | 6932 | 6944 | 5602 | 6454 |
| 2  | 8321  | 5351 | 7329 | 7411 | 7409 | 6487 | 7692 |

9. Per calcolare i risultati finali di tutti i blocchi, sommare le colonne e visualizzare i risultati nella console.

    ```R
    finalResults <- colSums(iroResults)
    finalResults
    ```

 **Risultati**
  1  |   2  |   3  |   4  |   5  |   6  |   7
---  |   ---  |   ---  |   ---  |   ---  |   ---  |   ---
97975 | 77725 | 78875 | 81304 | 82987 | 86159 | 94975 

10. Per rimuovere la tabella di risultati intermedi, effettuare una chiamata a **rxSqlServerDropTable**.
  
    ```R
    rxSqlServerDropTable( table = "iroResults", connectionString = sqlConnString)
    ```

## <a name="next-step"></a>Passaggio successivo

[Analizzare i dati in un contesto di calcolo locale](../../advanced-analytics/tutorials/deepdive-analyze-data-in-local-compute-context.md)

## <a name="previous-step"></a>Passaggio precedente

[Creare una nuova tabella di SQL Server mediante rxDataStep](../../advanced-analytics/tutorials/deepdive-create-new-sql-server-table-using-rxdatastep.md)
