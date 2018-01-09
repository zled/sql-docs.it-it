---
title: Creare una nuova tabella di SQL Server utilizzando rxDataStep (SQL e R approfondimento) | Documenti Microsoft
ms.custom: 
ms.date: 12/14/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to:
- SQL Server 2016
- SQL Server 2017
dev_langs: R
ms.assetid: 98cead96-6de7-4edf-98b9-a1efb09297b9
caps.latest.revision: "19"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 1f7e7c185df2a82c9cbe915e3f1248b8f17aa971
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="create-new-sql-server-table-using-rxdatastep-sql-and-r-deep-dive"></a>Creare una nuova tabella di SQL Server utilizzando rxDataStep (SQL e R approfondimento)

Questo articolo fa parte dell'esercitazione approfondimento di analisi scientifica dei dati, su come usare [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) con SQL Server.

In questa lezione, è illustrato come spostare i dati tra i frame di dati in memoria, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contesto e i file locali.

> [!NOTE]
> In questa lezione viene utilizzato un set di dati diverso. Il set di dati di ritardi Airline è un set di dati pubblico che è ampiamente utilizzata per esperimenti di apprendimento. I file di dati utilizzati in questo esempio sono disponibili nella stessa directory degli altri esempi di prodotto.

## <a name="create-sql-server-table-from-local-data"></a>Creare una tabella di SQL Server dai dati locali

Nella prima metà di questa esercitazione, è utilizzato il **RxTextData** funzione per importare dati in R da un file di testo e quindi usata la **RxDataStep** funzione per spostare i dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

In questa lezione adotta un approccio diverso, e vengono utilizzati i dati da un file salvato nel [formato con estensione XDF](https://en.wikipedia.org/wiki/Extensible_Data_Format). Dopo aver eseguito alcune trasformazioni ai dati utilizzando il file con estensione XDF leggeri, salvare i dati trasformati in un nuovo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella.

**Che cos'è con estensione XDF?**

Il formato con estensione XDF è uno standard XML sviluppato per i dati di dimensioni elevate e viene utilizzato il formato di file nativi da [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-xdf). Si tratta di un formato di file binario con un'interfaccia R che ottimizza l'elaborazione e l'analisi di righe e colonne.  È possibile usarlo per spostare i dati e archiviare subset di dati utili per l'analisi.

1. Impostare il contesto di calcolo sulla workstation locale. **Per questo passaggio, sono necessarie le autorizzazioni di DDL.**

  
    ```R
    rxSetComputeContext("local")
    ```
  
2. Definire un nuovo oggetto origine dati usando la funzione **RxXdfData** . Per definire un'origine dati con estensione XDF, specificare il percorso al file di dati.  

    È possibile specificare il percorso del file di utilizzo di una variabile di testo. Tuttavia, in questo caso, è un collegamento utile, in cui è possibile utilizzare il **rxGetOption** funzione e ottenere il file (AirlineDemoSmall.xdf) dalla directory di dati di esempio.
  
    ```R
    xdfAirDemo <- RxXdfData(file.path(rxGetOption("sampleDataDir"),  "AirlineDemoSmall.xdf"))
    ```

3. Chiamare [rxGetVarInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf) nei dati in memoria per visualizzare un riepilogo del set di dati.
  
    ```R
    rxGetVarInfo(xdfAirDemo)
    ```

**Risultati**

*Var 1: ArrDelay, tipo: integer, basso/alto: (-86, 1490)*

*Var 2: CRSDepTime, tipo: numeric, archiviazione: float32, basso/alto: (0,0167, 23,9833)*

*Var 3: DayOfWeek 7 livelli di fattori: lunedì, martedì, mercoledì, giovedì, venerdì, sabato e domenica*

> [!NOTE]
> 
> Si noti che non è stato necessario chiamare altre funzioni per caricare i dati nel file XDF e che è stato possibile chiamare immediatamente **rxGetVarInfo** nei dati. Ciò avviene perché XDF è il metodo di archiviazione provvisorio predefinito per RevoScaleR. Oltre ai file con estensione XDF, il **rxGetVarInfo** funzione ora supporta più tipi di origine.
  
4. Inserire dati in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella, l'archiviazione _DayOfWeek_ come integer con valori compresi tra 1 e 7.
  
    A tale scopo, per prima cosa definire un'origine dati SQL Server.
  
    ```R
    sqlServerAirDemo <- RxSqlServerData(table = "AirDemoSmallTest", connectionString = sqlConnString)
    ```
  
5. Verificare se esiste già una tabella con lo stesso nome e, se esiste, eliminarla.
  
    ```R
    if (rxSqlServerTableExists("AirDemoSmallTest",  connectionString = sqlConnString))  rxSqlServerDropTable("AirDemoSmallTest",  connectionString = sqlConnString)
    ```
  
6. Creare la tabella e caricare i dati usando **rxDataStep**. Questa funzione consente di spostare dati tra due già definito origini dati e facoltativamente possono trasformare i dati sulla route.
  
    ```R
    rxDataStep(inData = xdfAirDemo, outFile = sqlServerAirDemo,
            transforms = list( DayOfWeek = as.integer(DayOfWeek),
            rowNum = .rxStartRow : (.rxStartRow + .rxNumRows - 1) ),
            overwrite = TRUE )
    ```
  
    Si tratta di una tabella di dimensioni piuttosto grande, quindi attendere fino a quando non viene visualizzato un messaggio di stato finale simile alla seguente: *righe lette: 200000, totale righe elaborate: 600000*.
     
7. Impostare nuovamente il contesto di calcolo sul computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
8. Creare una nuova origine dati SQL Server, usando una semplice query SQL sulla nuova tabella. Questa definizione aggiunge livelli fattore per il *DayOfWeek* colonna, utilizzando il *colInfo* argomento **RxSqlServerData**.
  
    ```R
    SqlServerAirDemo <- RxSqlServerData(
        sqlQuery = "SELECT * FROM AirDemoSmallTest",
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",  levels = as.character(1:7))))
    ```
  
9. Chiamare **rxSummary** ancora una volta per visualizzare un riepilogo dei dati nella query.
  
    ```R
    rxSummary(~., data = sqlServerAirDemo)
    ```

## <a name="next-step"></a>Passaggio successivo

[Eseguire un'analisi in blocchi tramite rxDataStep](../../advanced-analytics/tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)

## <a name="previous-step"></a>Passaggio precedente

[Caricare i dati in memoria mediante rxImport](../../advanced-analytics/tutorials/deepdive-load-data-into-memory-using-rximport.md)
