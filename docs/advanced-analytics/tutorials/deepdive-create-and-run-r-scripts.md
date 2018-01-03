---
title: Creare ed eseguire gli script R (SQL e R approfondimento) | Documenti Microsoft
ms.date: 12/14/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to:
- SQL Server 2016
- SQL Server 2017
dev_langs: R
ms.assetid: 51e8e66f-a0a5-4e96-aa71-f5c870e6d0d4
caps.latest.revision: "18"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 3f26a5850ffe3245029486a2be4406790e36b6ab
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2017
---
# <a name="create-and-run-r-scripts-sql-and-r-deep-dive"></a>Creare ed eseguire gli script R (SQL e R approfondimento)

Questo articolo fa parte dell'esercitazione approfondimento di analisi scientifica dei dati, su come usare [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) con SQL Server.

Dopo aver impostato le origini dati e stabilito uno o più contesti di calcolo, è possibile usare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]per eseguire alcuni script R avanzati.  In questa lezione, si utilizza il contesto di calcolo di server per eseguire alcune attività comuni di apprendimento:

- Visualizzare dati e generare alcune statistiche di riepilogo
- Creare un modello di regressione lineare
- Creare un modello di regressione logistica
- Assegnare punteggi ai nuovi dati e creare un istogramma dei punteggi

## <a name="change-compute-context-to-the-server"></a>Modifica contesto per il server di calcolo

Prima di eseguire qualsiasi codice R è necessario specificare il contesto di calcolo *current* o *active* .

1. Per attivare un contesto di calcolo già definito tramite R, usare la funzione **rxSetComputeContext** come illustrato di seguito:
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
    Non appena si esegue questa istruzione, tutti i calcoli successivi intervenire il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] specificato nel computer il *sqlCompute* parametro.
  
2. Se si decide di eseguire il codice R sulla propria workstation, reimpostare il contesto di calcolo sul computer locale mediante la parola chiave  **local** .
  
    ```R
    rxSetComputeContext ("local")
    ```
  
    Per l'elenco delle parole chiave supportate da questa funzione digitare `help("rxSetComputeContext")` da una riga di comando di R.
  
3. Dopo che è stato specificato, il contesto di calcolo resta attivo fino a quando non lo si modifica. Tuttavia, qualsiasi script R *non* eseguibile in un contesto server remoto verrà eseguito localmente.

## <a name="compute-some-summary-statistics"></a>Calcolare alcune statistiche di riepilogo

Per verificare il funzionamento del contesto di calcolo, provare la generazione di statistiche di riepilogo mediante il `sqlFraudDS` origine dati.  Tenere presente che l'oggetto origine dati definisce solo i dati usati; non modifica il contesto di calcolo.

+ Per eseguire il riepilogo localmente, utilizzare **rxSetComputeContext** e specificare il _locale_ (parola chiave).
+ Per creare gli stessi calcoli nel computer con SQL Server, passare al contesto di calcolo SQL definito in precedenza.

1. Chiamare il [rxSummary](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsummary) funzione e passare gli argomenti obbligatori, ad esempio la formula e l'origine dati e assegnare i risultati alla variabile `sumOut`.
  
    ```R
    sumOut <- rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlFraudDS)
    ```
  
    Il linguaggio R offre molte funzioni di riepilogo, ma **rxSummary** supporta l'esecuzione in diversi contesti di calcolo remoto, tra cui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per informazioni sulle funzioni simili, vedere [i riepiloghi dei dati con RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-summaries).
  
2. Quando viene eseguita l'elaborazione, è possibile stampare il contenuto del `sumOut` variabile nella console.
  
    ```R
    sumOut
    ```
  
    > [!NOTE]
    > Non stampare i risultati prima che siano stati restituiti dal computer con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Potrebbe verificarsi un errore.

**Risultati**

*Summary Statistics Results for: ~gender + balance + numTrans +*

 *numIntlTrans + creditLine*

 *Data: sqlFraudDS (RxSqlServerData Data Source)*

 *Number of valid observations: 10000*

 *Name  Mean    StdDev  Min Max ValidObs    MissingObs*

 *balance       4075.0318 3926.558714            0   25626 100000*

 *numTrans        29.1061   26.619923 0     100 10000    0           100000*

 *numIntlTrans     4.0868    8.726757 0      60 10000    0           100000*

 *creditLine 9.1856 9.870364 1 75 10000 0 100000*

 *Conteggi delle categorie per sesso*

 *Number of categories: 2*

 *Number of valid observations: 10000*

 *Number of missing observations: 0*

 *gender Counts*

 *Male   6154*

  *Female 3846*

## <a name="add-maximum-and-minimum-values"></a>Aggiungere i valori minimi e massimo

Le statistiche di riepilogo calcolate hanno restituito informazioni utili sui dati da inserire nell'origine dati per l'uso in ulteriori calcoli. Ad esempio, è possono utilizzare i valori minimo e massimi per calcolare gli istogrammi. Per questo motivo, aggiungere i valori minimo e massimo per il **RxSqlServerData** origine dati.

Fortunatamente [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] include le funzioni ottimizzate in grado di convertire in modo efficiente dati integer per i dati categorici fattore.

1. Per iniziare si configurano alcune variabili temporanee.
  
    ```R
    sumDF <- sumOut$sDataFrame
    var <- sumDF$Name
    ```
  
2. Usare la variabile `ccColInfo` creata in precedenza per definire le colonne nell'origine dati.
  
    Inoltre, aggiungere alcune colonne calcolate di nuovo (`numTrans`, `numIntlTrans`, e `creditLine`) per la raccolta delle colonne.
  
    ```R 
    ccColInfo <- list(
        gender = list(type = "factor",
          levels = c("1", "2"), 
          newLevels = c("Male", "Female")),
        cardholder = list(type = "factor",
          levels = c("1", "2"), 
          newLevels = c("Principal", "Secondary")), 
        state = list(type = "factor", 
          levels = as.character(1:51), 
          newLevels = stateAbb), 
        balance  = list(type = "numeric"),
        numTrans = list(type = "factor", 
          levels = as.character(sumDF[var == "numTrans", "Min"]:sumDF[var == "numTrans", "Max"])),
        numIntlTrans = list(type = "factor",  
            levels = as.character(sumDF[var == "numIntlTrans", "Min"]:sumDF[var =="numIntlTrans", "Max"])),
        creditLine = list(type = "numeric")
            )
    ```
  
3. Dover aggiornare la raccolta di colonne, applicare l'istruzione seguente per creare una versione aggiornata del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] origine dati definita in precedenza.
  
    ```R
    sqlFraudDS <- RxSqlServerData(
        connectionString = sqlConnString,
        table = sqlFraudTable,
        colInfo = ccColInfo,
        rowsPerRead = sqlRowsPerRead)
    ```
  
    Il `sqlFraudDS` origine dati include ora le nuove colonne aggiunte utilizzando `ccColInfo`.
  

A questo punto, le modifiche interessano solo l'oggetto di origine dati in R; Nessun nuovo dato è stato ancora scritto alla tabella di database. Tuttavia, è possibile utilizzare i dati acquisiti nel `sumOut` variabile da creare visualizzazioni e riepiloghi. Nel passaggio successivo si informazioni su come eseguire questa operazione durante il cambio di contesti di calcolo.

> [!TIP]
> Se si dimentica di cui si sta utilizzando il contesto di calcolo, eseguire `rxGetComputeContext()`.  Valore restituito di "Contesto di calcolo RxLocalSeq" indica che siano in esecuzione nel contesto di calcolo locale.

## <a name="next-step"></a>Passaggio successivo

[Visualizzare i dati di SQL Server tramite R](../../advanced-analytics/tutorials/deepdive-visualize-sql-server-data-using-r.md)

## <a name="previous-step"></a>Passaggio precedente

[Definire e usare i contesti di calcolo](../../advanced-analytics/tutorials/deepdive-define-and-use-compute-contexts.md)
