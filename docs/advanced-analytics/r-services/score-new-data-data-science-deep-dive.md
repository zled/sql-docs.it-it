---
title: "Valutazione dei nuovi dati (procedura approfondita per l&#39;analisi scientifica dei dati) | Microsoft Docs"
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
ms.assetid: 87056467-f67f-4d72-a83c-ac052736d85d
caps.latest.revision: 17
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# Valutazione dei nuovi dati (procedura approfondita per l&#39;analisi scientifica dei dati)
Ora che è disponibile un modello da usare per le stime, è possibile inserirvi i dati estratti dal database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per generare alcune stime.  
  
## Valutazione dei nuovi dati  
Per creare i punteggi per un altro set di dati che usa le stesse variabili indipendenti come input, si userà il modello di regressione logistica *logitObj*.  
  
> [!NOTE]  
> Per alcuni di questi passaggi saranno necessari privilegi di amministratore DDL.  
  
1.  Aggiornare l'origine dati *sqlScoreDS* impostata in precedenza per aggiungere le informazioni necessarie sulla colonna.  
  
    ```R  
    sqlScoreDS <- RxSqlServerData(  
        connectionString = sqlConnString,   
        table = sqlScoreTable,   
        colInfo = ccColInfo,   
        rowsPerRead = sqlRowsPerRead)    
    ```  
  
2.  Per non perdere i risultati, è necessario creare un nuovo oggetto origine dati da usare per popolare una nuova tabella nel database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    ```R    
    sqlServerOutDS <- RxSqlServerData(table = "ccScoreOutput",   
        connectionString = sqlConnString,   
        rowsPerRead = sqlRowsPerRead )    
    ```  
     A questo punto la tabella non è stata creata. Questa istruzione definisce solo un contenitore per i dati.
     
3.  Controllare il contesto di calcolo corrente e impostare il contesto di calcolo per il server, se necessario.  
  
    ```R  
    rxSetComputeContext(sqlCompute)  
    ```  
  
4.  Prima di eseguire la funzione di stima che genera i risultati, è necessario verificare l'esistenza di una tabella di output esistente. In caso contrario, verrà visualizzato un errore quando si tenta di scrivere la nuova tabella  
  
    A tale scopo, chiamare le funzioni *rxSqlServerTableExists* e *rxSqlServerDropTable*, passando il nome della tabella come input.  
  
    ```R  
    if (rxSqlServerTableExists("ccScoreOutput"))     rxSqlServerDropTable("ccScoreOutput")   
    ```  
  
    -   La funzione *rxSqlServerTableExists* esegue una query del driver ODBC e restituisce TRUE se la tabella esiste, FALSE in caso contrario.    
    -   La funzione *rxSqlServerDropTable* esegue l'istruzione DDL e restituisce TRUE se la tabella è stata eliminata, FALSE in caso contrario.   
  
5.  È ora possibile usare la funzione *rxPredict* funzione per creare i punteggi e salvarli nella nuova tabella definita nell'origine dati *sqlScoreDS*.  
  
    ```R  
    rxPredict(modelObject = logitObj,   
        data = sqlScoreDS,        
        outData = sqlServerOutDS,     
        predVarNames = "ccFraudLogitScore",   
          type = "link",      
        writeModelVars = TRUE,        
        overwrite = TRUE)    
    ```  
  
    La funzione *rxPredict* è un'altra funzione che supporta l'esecuzione in contesti di calcolo remoti. È possibile usare la funzione *rxPredict* per creare punteggi da modelli creati tramite *rxLinMod*, *rxLogit* o *rxGlm*.  
  
    -   Il parametro *writeModelVars* è impostato su **TRUE** qui. Ciò significa che le variabili usate per la stima verranno incluse nella nuova tabella.  
  
    -   Il parametro *predVarNames* specifica la variabile in cui verranno archiviati i risultati. A questo punto viene passata una nuova variabile denominata *ccFraudLogitScore*.  
  
    -   Il parametro *type* per *rxPredict* definisce la modalità di calcolo delle stime. Specificare la parola chiave **response** per generare i punteggi in base alla scala della variabile di risposta oppure usare la parola chiave **link** per generare punteggi basati sulla funzione di collegamento sottostante e in questo caso le stime saranno su una scala logistica.  

6. Attendere un attimo prima di aggiornare l'elenco delle tabelle in Management Studio e visualizzare la nuova tabella con i dati.

7. Per aggiungere altre variabili alle stime di output, usare l'argomento *extraVarsToWrite*.  In questo codice, ad esempio, la variabile *custID* della tabella dei dati dei punteggi viene aggiunta alla tabella di output delle stime.  
  
    ```R   
    rxPredict(modelObject = logitObj,    
            data = sqlScoreDS,        
            outData = sqlServerOutDS,     
            predVarNames = "ccFraudLogitScore",   
              type = "link",      
            writeModelVars = TRUE,        
            extraVarsToWrite = "custID",      
            overwrite = TRUE)    
    ```  
  
## Visualizzare i punteggi in un istogramma  
Dopo aver creato la nuova tabella, si potrà calcolare e visualizzare un istogramma dei 10.000 punteggi stimati. Il calcolo sarà più veloce se si specificano i valori minimo e massimo. Estrarli quindi dal database e aggiungerli ai dati in uso.  
  
1.  Creare una nuova origine dati *sqlMinMax* per eseguire una query del database e ottenere i valori minimo e massimo.  
  
    ```R  
    sqlMinMax <- RxSqlServerData(  
        sqlQuery = paste("SELECT MIN(ccFraudLogitScore) AS minVal,",   
        "MAX(ccFraudLogitScore) AS maxVal FROM ccScoreOutput"),   
        connectionString = sqlConnString)    
    ```  
     Questo esempio spiega come è facile usare gli oggetti origine dati *RxSqlServerData* per definire set di dati arbitrari basati su query SQL, funzioni o stored procedure e usarli nel codice R. La variabile non archivia i valori effettivi, ma solo la definizione dell'origine dati. La query viene eseguita per generare i valori solo se usata in una funzione come *rxImport*.  
      
2.  Chiamare la funzione *rxImport* per inserire i valori in un frame di dati che può essere condiviso tra vari contesti di calcolo.  
  
    ```R  
    minMaxVals <- rxImport(sqlMinMax)   
    minMaxVals <- as.vector(unlist(minMaxVals))  
  
    ```  
     **Risultati**
 
     *> minMaxVals*
     
     *[1] -23.970256   9.786345*
  
3.  Ora che sono disponibili i valori massimo e minimo, è possibile usarli per creare l'origine dati di punteggio.  
  
    ```R  
    sqlOutScoreDS <- RxSqlServerData(sqlQuery = "SELECT ccFraudLogitScore FROM ccScoreOutput",    
        connectionString = sqlConnString,   
        rowsPerRead = sqlRowsPerRead,   
            colInfo = list(ccFraudLogitScore = list(   
                low = floor(minMaxVals[1]),    
                        high = ceiling(minMaxVals[2]) ) ) )  
  
    ```  

  
4.  Usare infine l'oggetto origine dati di punteggio per ottenere i dati relativi al punteggio, calcolare e visualizzare un istogramma. Aggiungere il codice per impostare il contesto di calcolo, se necessario.  
  
    ```R  
    # rxSetComputeContext(sqlCompute)   
    rxHistogram(~ccFraudLogitScore, data = sqlOutScoreDS)  
  
    ```  
  
    **Risultati**  
  
    ![complex histogram created by R](../../advanced-analytics/r-services/media/rsql-sue-complex-histogram.png "complex histogram created by R")  
  
## Passaggio successivo  
[Lezione 3: Trasformare i dati con R &#40;procedura approfondita per l'analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/lesson-3-transform-data-using-r-data-science-deep-dive.md)  
  
## Passaggio precedente  
[Creare modelli &#40;procedura approfondita per l'analisi scientifica dei dati &#41;](../../advanced-analytics/r-services/create-models-data-science-deep-dive.md)  
  
## Vedere anche  
[Procedura approfondita per l'analisi scientifica dei dati: Panoramica &#40;SQL Server R Services&#41;](http://msdn.microsoft.com/library/mt637368(SQL.130).aspx)  
  
  
  
