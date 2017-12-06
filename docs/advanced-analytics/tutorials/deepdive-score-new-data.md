---
title: Assegnare un punteggio nuovi dati | Documenti Microsoft
ms.custom: 
ms.date: 05/18/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: 87056467-f67f-4d72-a83c-ac052736d85d
caps.latest.revision: "17"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 83beab637e3740dc41706c34ccfacffe985f2957
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2017
---
# <a name="score-new-data"></a>Valutazione dei nuovi dati

Ora che è disponibile un modello da usare per le stime, è possibile inserirvi i dati estratti dal database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per generare alcune stime.

Per creare i punteggi per un altro set di dati che usa le stesse variabili indipendenti come input, si userà il modello di regressione logistica *logitObj*.

> [!NOTE]
> Per alcuni di questi passaggi saranno necessari privilegi di amministratore DDL.

## <a name="generate-and-save-scores"></a>Generare e salvare i punteggi
  
1. Aggiornare l'origine dati *sqlScoreDS*impostata in precedenza per aggiungere le informazioni necessarie sulla colonna.
  
    ```R
    sqlScoreDS <- RxSqlServerData(
        connectionString = sqlConnString,
        table = sqlScoreTable,
        colInfo = ccColInfo,
        rowsPerRead = sqlRowsPerRead)
    ```
  
2. Per non perdere i risultati, è necessario creare un nuovo oggetto origine dati da usare per popolare una nuova tabella nel database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
  
    ```R
    sqlServerOutDS <- RxSqlServerData(table = "ccScoreOutput",
        connectionString = sqlConnString,
        rowsPerRead = sqlRowsPerRead )
    ```
     A questo punto la tabella non è stata creata. Questa istruzione definisce solo un contenitore per i dati.
     
3. Controllare il contesto di calcolo corrente e impostare il contesto di calcolo per il server, se necessario.
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
4. Prima di eseguire la funzione di stima che genera i risultati, è necessario verificare l'esistenza di una tabella di output esistente. In caso contrario, verrà visualizzato un errore durante il tentativo di scrivere la nuova tabella.
  
    A tale scopo, chiamare le funzioni **rxSqlServerTableExists** e **rxSqlServerDropTable**, passando il nome della tabella come input.
  
    ```R
    if (rxSqlServerTableExists("ccScoreOutput"))     rxSqlServerDropTable("ccScoreOutput")
    ```
  
    -  La funzione rxSqlServerTableExists query al driver ODBC e restituisce TRUE se la tabella esiste, FALSE in caso contrario.
    -  La funzione rxSqlServerDropTable funzione esegue l'istruzione DDL e restituisce TRUE se la tabella è stata rimossa, FALSE in caso contrario.
  
5. È ora possibile usare la funzione **rxPredict** funzione per creare i punteggi e salvarli nella nuova tabella definita nell'origine dati *sqlScoreDS*.
  
    ```R
    rxPredict(modelObject = logitObj,
        data = sqlScoreDS,
        outData = sqlServerOutDS,
        predVarNames = "ccFraudLogitScore",
          type = "link",
        writeModelVars = TRUE,
        overwrite = TRUE)
    ```
  
    La funzione rxPredict è un'altra funzione che supporta l'esecuzione in contesti di calcolo remoto. È possibile utilizzare la funzione rxPredict alla creazione di punteggi da modelli creati utilizzando rxLinMod, rxLogit o rxGlm.
  
    - Il parametro *writeModelVars* è impostato su **TRUE** qui. Ciò significa che le variabili usate per la stima verranno incluse nella nuova tabella.
  
    - Il parametro *predVarNames* specifica la variabile in cui verranno archiviati i risultati. A questo punto viene passata una nuova variabile denominata *ccFraudLogitScore*.
  
    - Il *tipo* parametro per rxPredict definisce la modalità di calcolo stime. Specificare la parola chiave **response** per generare i punteggi in base alla scala della variabile di risposta oppure usare la parola chiave **link** per generare punteggi basati sulla funzione di collegamento sottostante e in questo caso le stime saranno su una scala logistica.

6. Attendere un attimo prima di aggiornare l'elenco delle tabelle in Management Studio e visualizzare la nuova tabella con i dati.

7. Per aggiungere altre variabili alle stime di output, usare l'argomento *extraVarsToWrite* .  In questo codice, ad esempio, la variabile *custID* della tabella dei dati dei punteggi viene aggiunta alla tabella di output delle stime.
  
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

## <a name="display-scores-in-a-histogram"></a>Visualizzare i punteggi in un istogramma

Dopo aver creato la nuova tabella, si potrà calcolare e visualizzare un istogramma dei 10.000 punteggi stimati. Il calcolo sarà più veloce se si specificano i valori minimo e massimo. Estrarli quindi dal database e aggiungerli ai dati in uso.

1. Creare una nuova origine dati *sqlMinMax*per eseguire una query del database e ottenere i valori minimo e massimo.
  
    ```R
    sqlMinMax <- RxSqlServerData(
        sqlQuery = paste("SELECT MIN(ccFraudLogitScore) AS minVal,",
        "MAX(ccFraudLogitScore) AS maxVal FROM ccScoreOutput"),
        connectionString = sqlConnString)
    ```

     Questo esempio, è possibile vedere come è facile da usare RxSqlServerData oggetti origine dei dati per definire i set di dati arbitrari basati su query SQL, funzioni o stored procedure e quindi utilizzare tali nel codice R. La variabile non archivia i valori effettivi, solo la definizione dell'origine dati; per generare i valori solo quando si usa una funzione come rxImport viene eseguita la query.
      
2. Chiamare la funzione rxImport per inserire i valori in un frame di dati che può essere condivise tra i vari contesti di calcolo.
  
    ```R
    minMaxVals <- rxImport(sqlMinMax)
    minMaxVals \<- as.vector(unlist(minMaxVals))
  
    ```
     **Risultati**
     
     *> minMaxVals*
     
     *[1] -23.970256   9.786345*
  
3. Ora che sono disponibili i valori minimi e massimo, utilizzare i valori per creare l'origine dati di punteggio.
  
    ```R
    sqlOutScoreDS <- RxSqlServerData(sqlQuery = "SELECT ccFraudLogitScore FROM ccScoreOutput",
        connectionString = sqlConnString,
        rowsPerRead = sqlRowsPerRead,
            colInfo = list(ccFraudLogitScore = list(
                low = floor(minMaxVals[1]),
                        high = ceiling(minMaxVals[2]) ) ) )
    ```

4. Usare infine l'oggetto origine dati di punteggio per ottenere i dati relativi al punteggio, calcolare e visualizzare un istogramma. Aggiungere il codice per impostare il contesto di calcolo, se necessario.
  
    ```R
    # rxSetComputeContext(sqlCompute)
    rxHistogram(~ccFraudLogitScore, data = sqlOutScoreDS)
    ```
  
    **Risultati**
  
    ![istogramma complesso creato da R](media/rsql-sue-complex-histogram.png "istogramma complesso creato da R")
  
## <a name="next-step"></a>Passaggio successivo

[Trasformare i dati usando R](../../advanced-analytics/tutorials/deepdive-transform-data-using-r.md)

## <a name="previous-step"></a>Passaggio precedente

[Creazione di modelli](../../advanced-analytics/tutorials/deepdive-create-models.md)


