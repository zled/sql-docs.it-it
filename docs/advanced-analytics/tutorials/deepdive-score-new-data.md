---
title: Assegnare un punteggio nuovi dati (SQL e R approfondimento) | Documenti Microsoft
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
ms.assetid: 87056467-f67f-4d72-a83c-ac052736d85d
caps.latest.revision: "17"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 9b4192252edff42275acff6902677e3dadd3122e
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="score-new-data-sql-and-r-deep-dive"></a>Assegnare un punteggio nuovi dati (SQL e R approfondimento)

Questo articolo fa parte dell'esercitazione approfondimento di analisi scientifica dei dati, su come usare [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) con SQL Server.

In questo passaggio, utilizzare il modello di regressione logistica creato in precedenza, per creare punteggi per un altro set di dati che utilizza le stesse variabili indipendenti come input.

> [!NOTE]
> Sono necessari privilegi di amministratore DDL per alcuni di questi passaggi.

## <a name="generate-and-save-scores"></a>Generare e salvare i punteggi
  
1. Aggiornare l'origine dati che è impostato in precedenza, `sqlScoreDS`, per aggiungere le informazioni di colonna richiesta.
  
    ```R
    sqlScoreDS <- RxSqlServerData(
        connectionString = sqlConnString,
        table = sqlScoreTable,
        colInfo = ccColInfo,
        rowsPerRead = sqlRowsPerRead)
    ```
  
2. Per assicurarsi di non perdere i risultati, creare un nuovo oggetto origine dati. Quindi, usare il nuovo oggetto origine dati per popolare una nuova tabella nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.
  
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
  
    -  La funzione **rxSqlServerTableExists** esegue una query del driver ODBC e restituisce TRUE se la tabella esiste, FALSE in caso contrario.
    -  La funzione **rxSqlServerDropTable** esegue l'istruzione DDL e restituisce TRUE se la tabella è stata eliminata, FALSE in caso contrario.
    - Riferimento per entrambe le funzioni sono disponibili qui: [rxSqlServerDropTable](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable)
  
5. È ora possibile utilizzare il [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) funzione per creare i punteggi e salvarle nella nuova tabella definita nell'origine dati `sqlScoreDS`.
  
    ```R
    rxPredict(modelObject = logitObj,
        data = sqlScoreDS,
        outData = sqlServerOutDS,
        predVarNames = "ccFraudLogitScore",
          type = "link",
        writeModelVars = TRUE,
        overwrite = TRUE)
    ```
  
    La funzione **rxPredict** è un'altra funzione che supporta l'esecuzione in contesti di calcolo remoti. È possibile usare la funzione **rxPredict** per creare punteggi da modelli creati tramite [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod), [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit)o [rxGlm](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxglm).
  
    - Il parametro *writeModelVars* è impostato su **TRUE** qui. Ciò significa che le variabili usate per la stima verranno incluse nella nuova tabella.
  
    - Il parametro *predVarNames* specifica la variabile in cui verranno archiviati i risultati. In questo caso si passa una nuova variabile, `ccFraudLogitScore`.
  
    - Il parametro *type* per **rxPredict** definisce la modalità di calcolo delle stime. Specificare la parola chiave **risposta** per generare punteggi in base alla scala della variabile di risposta. In alternativa, usare la parola chiave **collegamento** per generare punteggi basati sulla funzione collegamento sottostante, nel qual caso le stime vengono create utilizzando una scala logistica.

6. Attendere un attimo prima di aggiornare l'elenco delle tabelle in Management Studio e visualizzare la nuova tabella con i dati.

7. Per aggiungere variabili aggiuntive alle stime di output, usare l'argomento *extraVarsToWrite*.  Ad esempio, nel codice seguente, la variabile `custID` aggiunti dalla tabella di dati di punteggio nella tabella di output di stime.
  
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

## <a name="display-scores-in-a-histogram"></a>Punteggi di visualizzazione in un istogramma

Dopo aver creata la nuova tabella, è possibile calcolare e visualizzare un istogramma che mostra i punteggi stimati 10.000. Calcolo è più veloce se si specificano i valori minimo e massimo, quindi accedere a queste dal database e aggiungerli ai dati di utilizzo.

1. Creare una nuova origine dati, `sqlMinMax`, che esegue una query del database per ottenere i valori minimo e massimo.
  
    ```R
    sqlMinMax <- RxSqlServerData(
        sqlQuery = paste("SELECT MIN(ccFraudLogitScore) AS minVal,",
        "MAX(ccFraudLogitScore) AS maxVal FROM ccScoreOutput"),
        connectionString = sqlConnString)
    ```

     Questo esempio spiega come è facile usare gli oggetti origine dati **RxSqlServerData** per definire set di dati arbitrari basati su query SQL, funzioni o stored procedure e usarli nel codice R. La variabile non archivia i valori effettivi, ma solo la definizione dell'origine dati. La query viene eseguita per generare i valori solo se usata in una funzione come **rxImport**.
      
2. Chiamare il [rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport) funzione per inserire i valori in un frame di dati che può essere condivise tra i vari contesti di calcolo.
  
    ```R
    minMaxVals <- rxImport(sqlMinMax)
    minMaxVals \<- as.vector(unlist(minMaxVals))
  
    ```
     **Risultati**
     
     *> minMaxVals*
     
     *[1] -23.970256   9.786345*
  
3. Ora che sono disponibili i valori minimi e massimo, utilizzare i valori per creare un'altra origine dati per i punteggi generati.
  
    ```R
    sqlOutScoreDS <- RxSqlServerData(sqlQuery = "SELECT ccFraudLogitScore FROM ccScoreOutput",
        connectionString = sqlConnString,
        rowsPerRead = sqlRowsPerRead,
            colInfo = list(ccFraudLogitScore = list(
                low = floor(minMaxVals[1]),
                        high = ceiling(minMaxVals[2]) ) ) )
    ```

4. Utilizzare l'oggetto origine dati `sqlOutScoreDS` per ottenere i punteggi e di calcolo e di visualizzare un istogramma. Aggiungere il codice per impostare il contesto di calcolo, se necessario.
  
    ```R
    # rxSetComputeContext(sqlCompute)
    rxHistogram(~ccFraudLogitScore, data = sqlOutScoreDS)
    ```
  
    **Risultati**
  
    ![istogramma complesso creato da R](media/rsql-sue-complex-histogram.png "istogramma complesso creato da R")
  
## <a name="next-step"></a>Passaggio successivo

[Trasformare i dati con R](../../advanced-analytics/tutorials/deepdive-transform-data-using-r.md)

## <a name="previous-step"></a>Passaggio precedente

[Creare modelli](../../advanced-analytics/tutorials/deepdive-create-models.md)


