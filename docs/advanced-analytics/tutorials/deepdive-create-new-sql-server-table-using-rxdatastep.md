---
title: Creare una nuova tabella di SQL Server utilizzando rxDataStep | Documenti Microsoft
ms.custom: 
ms.date: 05/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
dev_langs:
- R
ms.assetid: 98cead96-6de7-4edf-98b9-a1efb09297b9
caps.latest.revision: 19
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4a5a8aaa8df1df4d34216f9d55806ccf5594292a
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="create-new-sql-server-table-using-rxdatastep"></a>Creare una nuova tabella di SQL Server mediante rxDataStep

In questa lezione verrà illustrato come spostare i dati tra i frame di dati in memoria, il contesto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e i file locali.

> [!NOTE]
> Per questa lezione, verrà usato un set di dati diverso. Il set di dati di ritardi Airline è un set di dati pubblico che è ampiamente utilizzata per esperimenti di apprendimento. Se R viene usato per la prima volta, questo set di dati risulta particolarmente adatto ai test poiché è usato in diversi esempi di prodotti di [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] pubblicati con [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. I file di dati necessari per questo esempio sono disponibili nella stessa directory degli altri esempi del prodotto.

## <a name="create-sql-server-table-from-local-data"></a>Creare una tabella di SQL Server dai dati locali

Nella prima parte di questa esercitazione, è utilizzato il **RxTextData** funzione per importare dati in R da un file di testo e quindi usata la **RxDataStep** funzione per spostare i dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

In questa lezione si userà un approccio diverso e i dati verranno ottenuti da un file salvato nel [formato XDF](https://en.wikipedia.org/wiki/Extensible_Data_Format). Il formato XDF è uno standard XML sviluppato per i dati di dimensioni elevate. Si tratta di un formato di file binario con un'interfaccia R che ottimizza l'elaborazione e l'analisi di righe e colonne.  È possibile usarlo per spostare i dati e archiviare subset di dati utili per l'analisi.

Dopo avere eseguito alcune piccole trasformazioni sui dati usando il file XDF, i dati trasformati verranno salvati in una nuova tabella di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

> [!NOTE]
> Per questa operazione sono necessarie autorizzazioni DDL.

1. Impostare il contesto di calcolo sulla workstation locale.
  
    ```R
    rxSetComputeContext("local")
    ```
  
2. Definire un nuovo oggetto origine dati usando la funzione **RxXdfData** . Per un'origine dati XDF, è sufficiente specificare il percorso del file di dati.  È possibile specificare il percorso del file di utilizzo di una variabile di testo, ma in questo caso, è presente un collegamento utile, perché il file di dati di esempio (AirlineDemoSmall.xdf) nella directory restituita dalla funzione rxGetOption.
  
    ```R
    xdfAirDemo <- RxXdfData(file.path(rxGetOption("sampleDataDir"),  "AirlineDemoSmall.xdf"))
    ```

3. Chiamare rxGetVarInfo sui dati in memoria per visualizzare un riepilogo del set di dati.
  
    ```R
    rxGetVarInfo(xdfAirDemo)
    ```

**Risultati**

*Var 1: ArrDelay, tipo: integer, basso/alto: (-86, 1490)*

*Var 2: CRSDepTime, tipo: numeric, archiviazione: float32, basso/alto: (0,0167, 23,9833)*

*Var 3: DayOfWeek 7 livelli di fattori: lunedì, martedì, mercoledì, giovedì, venerdì, sabato e domenica*

> [!NOTE]
> 
> Si noti che non sono necessarie chiamare qualsiasi altra funzione per caricare i dati nel file con estensione XDF e potrebbe chiamare rxGetVarInfo sui dati immediatamente? Ciò avviene perché XDF è il metodo di archiviazione provvisorio predefinito per RevoScaleR. Per ulteriori informazioni sui file con estensione XDF, vedere [creare un con estensione XDF](https://msdn.microsoft.com/microsoft-r/scaler-data-xdf).
  
4. A questo punto, si posizioneranno questi dati in una tabella di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , archiviando _DayOfWeek_ come integer con valori compresi tra 1 e 7.
  
    A tale scopo, per prima cosa definire un'origine dati SQL Server.
  
    ```R
    sqlServerAirDemo <- RxSqlServerData(table = "AirDemoSmallTest", connectionString = sqlConnString)
    ```
  
5. Verificare se esiste già una tabella con lo stesso nome e, se esiste, eliminarla.
  
    ```R
    if (rxSqlServerTableExists("AirDemoSmallTest",  connectionString = sqlConnString))  rxSqlServerDropTable("AirDemoSmallTest",  connectionString = sqlConnString)
    ```
  
6. Creare la tabella e caricare i dati usando **rxDataStep**. Questa funzione consente di spostare dati tra due già definito le origini dati e di trasformare i dati sulla route.
  
    ```R
    rxDataStep(inData = xdfAirDemo, outFile = sqlServerAirDemo,
            transforms = list( DayOfWeek = as.integer(DayOfWeek),
            rowNum = .rxStartRow : (.rxStartRow + .rxNumRows - 1) ),
            overwrite = TRUE )
    ```
  
    Si tratta di una tabella piuttosto grande, quindi attendere che venga visualizzato il messaggio di stato finale: *Righe lette: 200000, Totale righe elaborate: 600000*.
     
7. Impostare nuovamente il contesto di calcolo sul computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
8. Creare una nuova origine dati SQL Server, usando una semplice query SQL sulla nuova tabella. Questa definizione aggiunge livelli di fattore per la colonna *DayOfWeek*, usando l'argomento *colInfo* di RxSqlServerData.
  
    ```R
    SqlServerAirDemo <- RxSqlServerData(
        sqlQuery = "SELECT * FROM AirDemoSmallTest",
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",  levels = as.character(1:7))))
    ```
  
9. Chiamare rxSummary ancora una volta per visualizzare un riepilogo dei dati nella query.
  
    ```R
    rxSummary(~., data = sqlServerAirDemo)
    ```

## <a name="next-step"></a>Passaggio successivo

[Eseguire l'analisi di suddivisione in blocchi utilizzando rxDataStep](../../advanced-analytics/tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)

## <a name="previous-step"></a>Passaggio precedente

[Caricare i dati in memoria usando rxImport](../../advanced-analytics/tutorials/deepdive-load-data-into-memory-using-rximport.md)



