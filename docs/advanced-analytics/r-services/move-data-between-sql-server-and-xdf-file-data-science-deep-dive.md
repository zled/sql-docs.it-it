---
title: "Spostare i dati tra SQL Server e file XDF (Procedura approfondita per l&#39;analisi scientifica dei dati) | Microsoft Docs"
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
ms.assetid: 40887cb3-ffbb-4769-9f54-c006d7f4798c
caps.latest.revision: 17
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# Spostare i dati tra SQL Server e file XDF (Procedura approfondita per l&#39;analisi scientifica dei dati)
Quando si lavora in un contesto di calcolo locale, si ha accesso sia ai file di dati locali sia al database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], definito come origine dati *RxSqlServerData*.  
  
In questa sezione verrà illustrato come ottenere i dati e archiviarli in un file nel computer locale, in modo tale che sia possibile trasformarli. Alla fine, i dati saranno usati nel file per creare un nuova tabella di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], tramite *rxDataStep*.  
  
## Creare una tabella di SQL Server da un file XDF  

La funzione *rxImport* consente di importare i dati di una qualsiasi origine dati supportata in un file XDF locale. È utile usare un file locale se si vuole sottoporre ad analisi diverse i dati archiviati nel database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] senza continuare a ripetere la stessa query.  
  
Per questo esercizio saranno usati nuovamente i dati di frode di una carta di credito. In questo scenario è stato richiesto di eseguire alcune analisi aggiuntive sugli utenti in California, Oregon e Washington. Per maggiore efficienza, si è deciso di archiviare i dati di questi soli tre paesi nel computer locale e di lavorare con le variabili sesso, titolare carta e saldo.  
  
1.  Usare di nuovo il vettore *stateAbb* creato in precedenza per identificare i livelli da includere e stampare la nuova variabile *statesToKeep* nella console.  
  
    ```  
    statesToKeep <- sapply(c("CA", "OR", "WA"), grep, stateAbb)   
  
    statesToKeep  
  
    ```  
 **Risultati**
CA |  OPPURE  | WA 
-- | -- | --
 5 |  38  | 48 
  
2.  A questo punto definire i dati che si vuole rilevare da SQL Server usando una query [!INCLUDE[tsql](../../includes/tsql-md.md)].  Questa variabile sarà poi usata come argomento *inData* per *rxImport*.  
  
    ```R  
    importQuery <- paste("SELECT gender,cardholder,balance,state FROM",  sqlFraudTable,  "WHERE (state = 5 OR state = 38 OR state = 48)")  
  
    ```  
  
    Assicurarsi che la query non contenga caratteri nascosti, ad esempio avanzamenti riga e tabulazioni.  
  
3.  Definire poi le colonne da usare con i dati in R.  
  Ad esempio, il set di dati più piccolo conterrà solo tre livelli di fattore, poiché la query restituirà i risultati di soli tre stati.  È possibile usare nuovamente la variabile *statesToKeep* per identificare i livelli appropriati da includere.  
  
    ```R  
    importColInfo <- list(   
        gender = list( type = "factor",  levels = c("1", "2"), newLevels = c("Male", "Female")),       
        cardholder = list(  type = "factor",  levels = c("1", "2"), newLevels = c("Principal", "Secondary")),     
        state = list(   type = "factor",  levels = as.character(statesToKeep), newLevels = names(statesToKeep))   
            )  
  
    ```  
  
4.  Impostare il contesto di calcolo su **locale**, dal momento che devono essere considerati tutti i dati disponibili nel computer locale.  
  
    ```R  
    rxSetComputeContext("local")   
    ```  
  
5.  Creare l'oggetto origine dati passando tutte le variabili definite come argomenti a *RxSqlServerData*.  
  
    ```R  
    sqlServerImportDS <- RxSqlServerData(  
        connectionString = sqlConnString,   
        sqlQuery = importQuery,   
        colInfo = importColInfo)  
  
    ```  
  
6.  A questo punto chiamare *rxImport* per salvare i dati nella directory di lavoro corrente, in un file con nome `ccFraudSub.xdf`.  
  
    ```R  
    localDS <- rxImport(inData = sqlServerImportDS,   
        outFile = "ccFraudSub.xdf",    
        overwrite = TRUE)  
  
    ```  
  
    L'oggetto *localDs* restituito dalla funzione *rxImport* è un oggetto origine dati *RxXdfData* disattivo che rappresenta il file di dati ccFraud.xdf archiviato localmente sul disco.  
  
7.  Chiamare *rxGetVarInfo* nel file XDF per verificare che lo schema dei dati sia lo stesso.  
  
    ```R  
    rxGetVarInfo(data = localDS)   
    ```  
    **Risultati**
    
    *rxGetVarInfo(data = localDS)*    
    *Var 1: gender, Type: factor, no factor levels available*    
    *Var 2: cardholder, Type: factor, no factor levels available*    
    *Var 3: balance, Type: integer, Low/High: (0, 22463)*    
    *Var 4: state, Type: factor, no factor levels available*
  
8.  È ora possibile chiamare varie funzioni R per analizzare l'oggetto *localDs*, come si è soliti fare con i dati di origine in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Esempio:  
  
    ```R  
    rxSummary(~gender + cardholder + balance + state, data = localDS)    
    ```  
  
Dopo aver appreso l'uso di contesti di calcolo e aver usato origini dati diverse è possibile passare alla parte più divertente.  
  
Nella lezione successiva, che è anche l'ultima, si creerà una semplice simulazione usando una funzione R personalizzata. La simulazione sarà eseguita nel server remoto.  
  
## Passaggio successivo  
[Lezione 5: Creare una simulazione semplice &#40;procedura approfondita per l'analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/lesson-5-create-a-simple-simulation-data-science-deep-dive.md)  
  
## Passaggio precedente  
[Lezione 4: Analizzare i dati in un contesto di calcolo locale &#40;(Procedura approfondita per l'analisi scientifica dei dati)&#41;](../../advanced-analytics/r-services/lesson-4-analyze-data-in-local-compute-context-data-science-deep-dive.md)  
  
## Vedere anche  
[Procedura approfondita per l'analisi scientifica dei dati: Uso dei pacchetti RevoScaleR](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)  
  
  
  
