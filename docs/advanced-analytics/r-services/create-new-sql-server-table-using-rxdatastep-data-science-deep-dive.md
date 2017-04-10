---
title: "Creare una nuova tabella di SQL Server mediante rxDataStep (procedura approfondita per l&#39;analisi scientifica dei dati) | Microsoft Docs"
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
ms.assetid: 98cead96-6de7-4edf-98b9-a1efb09297b9
caps.latest.revision: 19
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# Creare una nuova tabella di SQL Server mediante rxDataStep (procedura approfondita per l&#39;analisi scientifica dei dati)
In questa lezione verrà illustrato come spostare i dati tra i frame di dati in memoria, il contesto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e i file locali.  
  
> [!NOTE]  
> Per questa lezione, verrà usato un set di dati diverso. Il set di dati dei ritardi delle compagnie aeree è un set di dati pubblico ampiamente usato per gli esperimenti di Machine Learning. Se R viene usato per la prima volta, questo set di dati risulta particolarmente adatto ai test poiché è usato in diversi esempi di prodotti di [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] pubblicati con [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. I file di dati necessari per questo esempio sono disponibili nella stessa directory degli altri esempi del prodotto.  
  
## Creare una tabella di SQL Server dai dati locali  
Nella prima lezione di questa esercitazione è stata usata la funzione *RxTextData* per importare i dati in R da un file di testo e quindi è stata usata la funzione *RxDataStep* per spostare i dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
In questa lezione si userà un approccio diverso e i dati verranno ottenuti da un file salvato nel [formato XDF](https://en.wikipedia.org/wiki/Extensible_Data_Format). Il formato XDF è uno standard XML sviluppato per i dati di dimensioni elevate. Si tratta di un formato di file binario con un'interfaccia R che ottimizza l'elaborazione e l'analisi di righe e colonne.  È possibile usarlo per spostare i dati e archiviare subset di dati utili per l'analisi.
  
Dopo avere eseguito alcune piccole trasformazioni sui dati usando il file XDF, i dati trasformati verranno salvati in una nuova tabella di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
> Per questa operazione sono necessarie autorizzazioni DDL.  
  
1.  Impostare il contesto di calcolo sulla workstation locale.  
  
    ```R  
    rxSetComputeContext("local")   
    ```  
  
2.  Definire un nuovo oggetto origine dati usando la funzione *RxXdfData*. Per un'origine dati XDF, è sufficiente specificare il percorso del file di dati.  È possibile specificare il percorso del file usando una variabile di testo, ma in questo caso esiste una comoda scorciatoia poiché il file di dati di esempio (AirlineDemoSmall.xdf) è nella directory restituita dalla funzione *rxGetOption*.
  
    ```R  
    xdfAirDemo <- RxXdfData(file.path(rxGetOption("sampleDataDir"),  "AirlineDemoSmall.xdf"))   
    ```  
  
  
3.  Chiamare *rxGetVarInfo* nei dati in memoria per visualizzare un riepilogo del set di dati.  
  
    ```R  
    rxGetVarInfo(xdfAirDemo)    
    ```  
  
**Risultati**  
  
*Var 1: ArrDelay, tipo: integer, basso/alto: (-86, 1490)*   
*Var 2: CRSDepTime, tipo: numeric, archiviazione: float32, basso/alto: (0,0167, 23,9833)*   
*Var 3: DayOfWeek 7 livelli di fattori: lunedì, martedì, mercoledì, giovedì, venerdì, sabato e domenica*  

> [!NOTE]
> 
> Si noti che non è stato necessario chiamare altre funzioni per caricare i dati nel file XDF e che è stato possibile chiamare immediatamente *rxGetVarInfo* nei dati. Ciò avviene perché XDF è il metodo di archiviazione provvisorio predefinito per RevoScaleR. Per altre informazioni sui file XDF, vedere [ScaleR Getting Started Guide](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-data-transform#using-the-data-step-to-create-an-xdf-file-from-a-data-frame) (Guida introduttiva di ScaleR) 
  
4.  A questo punto, si posizioneranno questi dati in una tabella di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], archiviando _DayOfWeek_ come integer con valori compresi tra 1 e 7.  
  
    A tale scopo, per prima cosa definire un'origine dati SQL Server.  
  
    ```R  
    sqlServerAirDemo <- RxSqlServerData(table = "AirDemoSmallTest", connectionString = sqlConnString)   
    ```  
  
5.  Verificare l'esistenza di una tabella con lo stesso nome ed eliminare la tabella se esistente.  
  
    ```R  
    if (rxSqlServerTableExists("AirDemoSmallTest",  connectionString = sqlConnString))  rxSqlServerDropTable("AirDemoSmallTest",  connectionString = sqlConnString)    
    ```  
  
6.  Creare la tabella e caricare i dati usando `rxDataStep`.  
  
    ```R  
    rxDataStep(inData = xdfAirDemo, outFile = sqlServerAirDemo,    
            transforms = list( DayOfWeek = as.integer(DayOfWeek),   
            rowNum = .rxStartRow : (.rxStartRow + .rxNumRows - 1) ),   
            overwrite = TRUE )    
    ```  
  
7.  Impostare nuovamente il contesto di calcolo sul computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    ```R  
    rxSetComputeContext(sqlCompute)  
    ```  
  
8.  Definire un subset dei dati usando un'istruzione SQL semplice.  
  
    ```R    
    SqlServerAirDemo <- RxSqlServerData(  
        sqlQuery = "SELECT * FROM AirDemoSmallTest",      
        connectionString = sqlConnString,   
        rowsPerRead = 50000,      
        colInfo = list(DayOfWeek = list(type = "factor",  levels = as.character(1:7))))    
    ```  
  
9. Chiamare *rxSummary* per esaminare un riepilogo dei dati nella query.  
  
    ```R  
    rxSummary(~., data = sqlServerAirDemo)   
    ```  
  
## Passaggio successivo  
[Eseguire un'analisi in blocchi tramite rxDataStep &#40;procedura approfondita per l'analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/perform-chunking-analysis-using-rxdatastep-data-science-deep-dive.md)  
  
## Passaggio precedente  
[Caricare i dati in memoria mediante rxImport &#40;approfondimento di analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/load-data-into-memory-using-rximport-data-science-deep-dive.md)  
  
## Vedere anche  
[Procedura approfondita per l'analisi scientifica dei dati: Uso dei pacchetti RevoScaleR](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)  
  
  
  
