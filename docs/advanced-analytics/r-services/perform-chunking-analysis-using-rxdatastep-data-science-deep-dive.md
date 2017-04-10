---
title: "Eseguire un&#39;analisi in blocchi tramite rxDataStep (Procedura approfondita per l&#39;analisi scientifica dei dati) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: 4290ee5f-be90-446a-91e8-3095d694bd82
caps.latest.revision: 17
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# Eseguire un&#39;analisi in blocchi tramite rxDataStep (Procedura approfondita per l&#39;analisi scientifica dei dati)
È possibile usare la funzione *rxDataStep* per elaborare i dati in blocchi, anziché caricare nella memoria l'intero set di dati ed elaborarlo in una sola volta come succede nel codice R tradizionale. Se si usa questa funzione, i dati vengono letti in blocchi, le funzioni R elaborano ogni blocco di dati e i risultati di riepilogo di ogni blocco vengono scritti in un'origine dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] comune.  
  
In questa lezione si useranno questa tecnica e la funzione *table* in R per calcolare una tabella di emergenza.  
  
> [!TIP]  
> Questo esempio è studiato solo per scopi didattici. Per catalogare set di dati reali, è consigliabile usare le funzioni *rxCrossTabs* o *rxCube* incorporate in **RevoScaleR** in quanto sono ottimizzate per questo tipo di operazione.  
  
## Suddividere i dati in partizioni in base ai valori  
  
1.  Creare prima una funzione R personalizzata denominata *ProcessChunk* con la quale chiamare la funzione *table* in ogni blocco di dati.  
  
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
 
  
2.  Impostare il contesto di calcolo server.  
  
    ```R  
    rxSetComputeContext( sqlCompute )   
    ```  
  
3.  È necessario definire un'origine dati SQL Server per contenere i dati che si sta elaborando, assegnando prima una query SQL a una variabile.   
  
    ```R  
    dayQuery <-  "SELECT DayOfWeek FROM AirDemoSmallTest"   
    ```  

4.  Collegare tale variabile all'argomento *sqlQuery* di una nuova origine dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    ```R  
    inDataSource <- RxSqlServerData(sqlQuery = dayQuery,  
        connectionString = sqlConnString,    
        rowsPerRead = 50000,      
        colInfo = list(DayOfWeek = list(type = "factor",   
            levels = as.character(1:7))))    
    ```  
     Se si eseguisse la funzione *rxGetVarInfo* su questa origine dati, si noterebbe che è contenuta solo la singola colonna *Var 1: DayOfWeek, Type: factor, no factor levels available*
     
5.  Prima di applicare questa variabile di fattore all'origine dati, creare una tabella separata in cui includere i risultati intermedi. Anche in questo caso è sufficiente usare la funzione *RxSqlServerData* per definire i dati ed eliminare le tabelle esistenti con lo stesso nome.   
  
    ```R  
    iroDataSource = RxSqlServerData(table = "iroResults",   connectionString = sqlConnString)   
    # Check whether the table already exists.  
    if (rxSqlServerTableExists(table = "iroResults",  connectionString = sqlConnString))  { rxSqlServerDropTable( table = "iroResults", connectionString = sqlConnString) }   
    ```  
  
7.  A questo punto è necessario chiamare la funzione personalizzata *ProcessChunk* per trasformare i dati letti, usandola come argomento *transformFunc* per la funzione *rxDataStep*.  
  
    ```R  
    rxDataStep( inData = inDataSource, outFile = iroDataSource, transformFunc = ProcessChunk, overwrite = TRUE)   
    ```  
  
8.  Per visualizzare i risultati intermedi di *ProcessChunk*, assegnare i risultati di *rxImport* a una variabile e visualizzare i risultati nella console.  
  
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
  
10. Per rimuovere la tabella contenente i risultati intermedi, chiamare nuovamente *rxSqlServerDropTable*.  
  
    ```R  
    rxSqlServerDropTable( table = "iroResults",     connectionString = sqlConnString)    
    ```  
  
## Passaggio successivo  
[Lezione 4: Analizzare i dati in un contesto di calcolo locale &#40;(Procedura approfondita per l'analisi scientifica dei dati)&#41;](../../advanced-analytics/r-services/lesson-4-analyze-data-in-local-compute-context-data-science-deep-dive.md)  
  
## Passaggio precedente  
[Creare una nuova tabella di SQL Server tramite rxDataStep &#40;Procedura approfondita per l'analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/create-new-sql-server-table-using-rxdatastep-data-science-deep-dive.md)  
  
## Vedere anche  
[Procedura approfondita per l'analisi scientifica dei dati: Uso dei pacchetti RevoScaleR](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)  
  
  
  
