---
title: Trasformare i dati usando R (SQL e R approfondimento) | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 80472b3328c392d886733aad97adf1aa6eeae4ba
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="transform-data-using-r-sql-and-r-deep-dive"></a>Trasformare i dati usando R (SQL e R approfondimento)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo fa parte dell'esercitazione approfondimento di analisi scientifica dei dati, su come usare [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) con SQL Server.

Il pacchetto **RevoScaleR** offre diverse funzioni per la trasformazione dei dati in varie fasi dell'analisi:

- **rxDataStep** può essere usato per creare e trasformare i subset di dati.

- **rxImport** supporta la trasformazione dei dati quando i dati vengono importati in o da un file XDF o un frame di dati in memoria.

- Sebbene non siano specificamente destinate allo spostamento dei dati, le funzioni **rxSummary**, **rxCube**, **rxLinMod**e **rxLogit** supportano tutte le trasformazioni dei dati.

In questa sezione informazioni su come utilizzare queste funzioni. Iniziamo con [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep).

## <a name="use-rxdatastep-to-transform-variables"></a>Utilizzare rxDataStep per trasformare le variabili

La funzione **rxDataStep** elabora i dati un blocco alla volta, leggendo da un'origine dati e scrivendo su un'altra. È possibile specificare le colonne da trasformare, le trasformazioni da caricare e così via.

Per rendere più interessante l'esempio, consente di utilizzare una funzione da un altro pacchetto R per trasformare i dati.  Il pacchetto **Boot** è uno dei pacchetti "consigliati", per questo **Boot** è incluso in ogni distribuzione di R, ma non viene caricato automaticamente all'avvio. Di conseguenza, il pacchetto deve essere già disponibile nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che si sta usando con [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].

Dal **avvio** del pacchetto, utilizzare la funzione `inv.logit`, che calcola l'inverso di un logit. Vale a dire, la funzione `inv.logit` converte una funzione logit di nuovo in una probabilità nella scala [0,1].

> [!TIP] 
> È possibile impostare un altro modo per ottenere stime in scala di *tipo* parametro **risposta** nella chiamata originale a rxPredict.

1. Creare un'origine dati per contenere i dati destinati a per la tabella, innanzitutto `ccScoreOutput`.
  
    ```R
    sqlOutScoreDS <- RxSqlServerData( table =  "ccScoreOutput",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )
    ```
  
2. Aggiungere un'altra origine dati per contenere i dati per la tabella `ccScoreOutput2`.
  
    ```R
    sqlOutScoreDS2 <- RxSqlServerData( table =  "ccScoreOutput2",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )
    ```
  
    Nella nuova tabella, archiviare tutte le variabili dal precedente `ccScoreOutput` tabella più variabile appena creata.
  
3. Impostare il contesto di calcolo sull'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
4. Utilizzare la funzione **rxSqlServerTableExists** per verificare se la tabella di output `ccScoreOutput2` ; esiste già e in tal caso, utilizzare la funzione **rxSqlServerDropTable** per eliminare la tabella.
  
    ```R
    if (rxSqlServerTableExists("ccScoreOutput2"))     rxSqlServerDropTable("ccScoreOutput2")
    ```
  
5. Chiamare la funzione **rxDataStep** e specificare le trasformazioni appropriate in un elenco.
  
    ```R
    rxDataStep(inData = sqlOutScoreDS,
        outFile = sqlOutScoreDS2,
        transforms = list(ccFraudProb = inv.logit(ccFraudLogitScore)),
        transformPackages = "boot",
        overwrite = TRUE)
    ```

    Quando si definiscono le trasformazioni applicate a ogni colonna, è possibile specificare anche eventuali pacchetti di R aggiuntivi necessari per eseguire le trasformazioni.  Per ulteriori informazioni sui tipi di trasformazioni che è possibile eseguire, vedere [come subset e trasformazione dati con RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-transform).
  
6. Chiamare **rxGetVarInfo** per visualizzare un riepilogo delle variabili nel set di dati nuovo.
  
    ```R
    rxGetVarInfo(sqlOutScoreDS2)
    ```

    **Risultati**
    
    *Var 1: ccFraudLogitScore, tipo: numeric*
    
    *Var 2: state, tipo: carattere*
    
    *Var 3: gender, tipo: carattere*
    
    *Var 4: cardholder, tipo: carattere*
    
    *Var 5: balance, tipo: integer*
    
    *Var 6: numTrans, tipo: integer*
    
    *Var 7: numIntlTrans, tipo: integer*
    
    *Var 8: creditLine, tipo: integer*
    
    *Var 9: ccFraudProb, tipo: numeric*

I punteggi della funzione logit originali vengono mantenuti, ma una nuova colonna, *ccFraudProb*, è stata aggiunta, nella quale i punteggi della funzione logit sono rappresentati come valori tra 0 e 1.

Si noti che le variabili di fattori sono stati scritti nella tabella `ccScoreOutput2` come dati di tipo carattere. Se si vuole usarle come fattori nelle analisi successive, specificare i livelli tramite il parametro *colInfo* .

## <a name="next-step"></a>Passaggio successivo

[Caricare i dati in memoria mediante rxImport](../../advanced-analytics/tutorials/deepdive-load-data-into-memory-using-rximport.md)

## <a name="previous-step"></a>Passaggio precedente

[Creare ed eseguire script R](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)
