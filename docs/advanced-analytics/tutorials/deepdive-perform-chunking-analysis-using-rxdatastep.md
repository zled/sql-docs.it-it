---
title: Eseguire l'analisi di suddivisione in blocchi utilizzando rxDataStep | Documenti Microsoft
ms.custom: 
ms.date: 05/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: 4290ee5f-be90-446a-91e8-3095d694bd82
caps.latest.revision: "17"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7fb2f00e3506514c7d4870763052df2558f47aa4
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="perform-chunking-analysis-using-rxdatastep"></a>Eseguire un'analisi in blocchi tramite rxDataStep

È possibile usare la funzione **rxDataStep** per elaborare i dati in blocchi, anziché caricare nella memoria l'intero set di dati ed elaborarlo in una sola volta come succede nel codice R tradizionale. Se si usa questa funzione, i dati vengono letti in blocchi, le funzioni R elaborano ogni blocco di dati e i risultati di riepilogo di ogni blocco vengono scritti in un'origine dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] comune.

In questa lezione, è possibile mettere in pratica questa tecnica utilizzando il `table` funzione in R, per calcolare una tabella di emergenza.

> [!TIP]
> Questo esempio è studiato solo per scopi didattici. Se è necessario per il set di dati reali tabulare, è consigliabile utilizzare il **rxCrossTabs** o **rxCube** funzioni in **RevoScaleR**, ottimizzati per l'ordinamento di operazione.

## <a name="partition-data-by-values"></a>Suddividere i dati in partizioni in base ai valori

1. Innanzitutto, creare una funzione R personalizzata che chiama il *tabella* funzione in ogni blocco di dati e denominarlo `ProcessChunk`.
  
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
  
3. È necessario definire un'origine dati SQL Server per contenere i dati che si sta elaborando, assegnando prima una query SQL a una variabile.
  
    ```R
    dayQuery <-  "SELECT DayOfWeek FROM AirDemoSmallTest"
    ```

4. Collegare tale variabile all'argomento *sqlQuery* di una nuova origine dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
  
    ```R
    inDataSource <- RxSqlServerData(sqlQuery = dayQuery,
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",
            levels = as.character(1:7))))
    ```
     Se si eseguisse la funzione *rxGetVarInfo* su questa origine dati, si noterebbe che è contenuta solo la singola colonna *Var 1: DayOfWeek, Type: factor, no factor levels available*
     
5. Prima di applicare questa variabile di fattore all'origine dati, creare una tabella separata in cui includere i risultati intermedi. Nuovamente, sufficiente utilizzare la funzione RxSqlServerData per definire i dati ed eliminare le tabelle esistenti con lo stesso nome.
  
    ```R
    iroDataSource = RxSqlServerData(table = "iroResults",   connectionString = sqlConnString)
    # Check whether the table already exists.
    if (rxSqlServerTableExists(table = "iroResults",  connectionString = sqlConnString))  { rxSqlServerDropTable( table = "iroResults", connectionString = sqlConnString) }
    ```
  
7.  Ora sarà richiamata la funzione personalizzata `ProcessChunk` per trasformare i dati in fase di lettura, utilizzando come il *transformFunc* argomento della funzione rxDataStep.
  
    ```R
    rxDataStep( inData = inDataSource, outFile = iroDataSource, transformFunc = ProcessChunk, overwrite = TRUE)
    ```
  
8.  Per visualizzare i risultati intermedi di `ProcessChunk`, assegnare i risultati di rxImport a una variabile e quindi i risultati alla console.
  
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

10. Per rimuovere la tabella di risultati intermedi, eseguire un'altra chiamata a rxSqlServerDropTable.
  
    ```R
    rxSqlServerDropTable( table = "iroResults",     connectionString = sqlConnString)
    ```

## <a name="next-step"></a>Passaggio successivo

[Analizzare i dati nel contesto di calcolo locale.](../../advanced-analytics/tutorials/deepdive-analyze-data-in-local-compute-context.md)

## <a name="previous-step"></a>Passaggio precedente

[Creare una nuova tabella di SQL Server utilizzando rxDataStep](../../advanced-analytics/tutorials/deepdive-create-new-sql-server-table-using-rxdatastep.md)


