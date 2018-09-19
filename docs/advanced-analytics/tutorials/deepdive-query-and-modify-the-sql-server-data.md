---
title: Eseguire query e modificare i dati di SQL Server (SQL e R approfondita) | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 57fff9b8ddfd6507876bd6eb174a127d70d0b916
ms.sourcegitcommit: aa9d2826e3c451f4699c0e69c9fcc8a2781c6213
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2018
ms.locfileid: "45975650"
---
# <a name="query-and-modify-the-sql-server-data-sql-and-r-deep-dive"></a>Eseguire query e modificare i dati di SQL Server (SQL e R approfondita)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo fa parte dell'esercitazione approfondita di Data Science, su come usare [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) con SQL Server.

Ora che i dati sono stati caricati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è possibile usare le origini dati create come argomenti per le funzioni R in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], per ottenere le informazioni di base sulle variabili e generare riepiloghi e istogrammi.

In questo passaggio è usare nuovamente le origini dati per eseguire un'analisi rapida e quindi ottimizzare i dati.

## <a name="query-the-data"></a>Eseguire query sui dati

Per prima cosa ottenere un elenco delle colonne e dei relativi tipi di dati.

1.  Utilizzare la funzione [rxGetVarInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf) e specificare l'origine dati da analizzare.

    A seconda della versione di RevoScaleR, è anche possibile usare [rxGetVarNames](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarnames). 
  
    ```R
    rxGetVarInfo(data = sqlFraudDS)
    ```

    **Risultati**
    
    *Var 1: custID, tipo: integer*
    
    *Var 2: gender, tipo: integer*
    
    *Var 3: state, tipo: integer*
    
    *Var 4: cardholder, tipo: integer*
    
    *Var 5: balance, tipo: integer*
    
    *Var 6: numTrans, tipo: integer*
    
    *Var 7: numIntlTrans, tipo: integer*
    
    *Var 8: creditLine, tipo: integer*
    
    *Var 9: fraudRisk, tipo: integer*


## <a name="modify-metadata"></a>Modificare i metadati

Tutte le variabili vengono archiviate come numeri interi, ma alcune variabili rappresentano dati categorici, chiamati *variabili di fattore* in R. Ad esempio, la colonna *stato* contiene numeri utilizzati come identificatori per i 50 stati più District of Columbia.  Per facilitare la comprensione dei dati, sostituire i numeri con un elenco di codici di stato.

In questo passaggio si crea un vettore di stringhe contenente le abbreviazioni e quindi eseguire il mapping di valori relativi alle categorie agli identificatori interi originali. Usare la nuova variabile nel *colInfo* argomento, per specificare che la colonna gestita come fattore. Ogni volta che si analizzano i dati o spostarlo, vengono usate le abbreviazioni e la colonna viene gestita come fattore.

Il mapping della colonna alle abbreviazioni prima di usarla come fattore consente di migliorare anche le prestazioni. Per altre informazioni, vedere [ottimizzazione R e i dati](..\r\r-and-data-optimization-r-services.md).

1. Iniziare creando la variabile R *stateAbb*e definendo il vettore di stringhe da aggiungere alla variabile come segue:
  
    ```R
    stateAbb <- c("AK", "AL", "AR", "AZ", "CA", "CO", "CT", "DC",
        "DE", "FL", "GA", "HI","IA", "ID", "IL", "IN", "KS", "KY", "LA",
        "MA", "MD", "ME", "MI", "MN", "MO", "MS", "MT", "NB", "NC", "ND",
        "NH", "NJ", "NM", "NV", "NY", "OH", "OK", "OR", "PA", "RI","SC",
        "SD", "TN", "TX", "UT", "VA", "VT", "WA", "WI", "WV", "WY")
    ```

2. Quindi, creare un oggetto informazioni di colonna denominato *ccColInfo*che specifichi il mapping dei valori interi esistenti ai livelli di categoria, ovvero le abbreviazioni per gli stati.
  
    Questa istruzione crea anche le variabili di fattore per gender e cardholder.
  
    ```R
    ccColInfo <- list(
    gender = list(
              type = "factor",
              levels = c("1", "2"),
              newLevels = c("Male", "Female")
              ),
    cardholder = list(
                  type = "factor",
                  levels = c("1", "2"),
                  newLevels = c("Principal", "Secondary")
                   ),
    state = list(
             type = "factor",
             levels = as.character(1:51),
             newLevels = stateAbb
             ),
    balance = list(type = "numeric")
    )
    ```
  
3. Per creare l'origine dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che usa i dati aggiornati, chiamare la funzione **RxSqlServerData** come in precedenza, ma aggiungere l'argomento *colInfo* .
  
    ```R
    sqlFraudDS <- RxSqlServerData(connectionString = sqlConnString,
    table = sqlFraudTable, colInfo = ccColInfo,
    rowsPerRead = sqlRowsPerRead)
    ```
  
    - Per il parametro *table* , passare la variabile *sqlFraudTable*che contiene l'origine dati creata in precedenza.
    - Per il parametro *colInfo* , passare la variabile *ccColInfo* che contiene i tipi di dati di colonna e i livelli di fattore.

4.  È ora possibile usare la funzione **rxGetVarInfo** per visualizzare le variabili nella nuova origine dati.
  
    ```R
    rxGetVarInfo(data = sqlFraudDS)
    ```

    **Risultati**
    
    *Var 1: custID, tipo: integer*
    
    *Var 2: gender 2 livelli di fattore: Male Female*
    
    *Var 3: state 51 livelli di fattore: AK AL AR AZ CA... VT WA WI WV WY*
    
    *Var 4: cardholder 2 livelli di fattore: Principal Secondary*
    
    *Var 5: balance, tipo: integer*
    
    *Var 6: numTrans, tipo: integer*
    
    *Var 7: numIntlTrans, tipo: integer*
    
    *Var 8: creditLine, tipo: integer*
    
    *Var 9: fraudRisk, tipo: integer*

A questo punto le tre variabili specificate (_gender_, _state_e _cardholder_) vengono trattate come fattori.

## <a name="next-step"></a>Passaggio successivo

[Definire e usare i contesti di calcolo](../../advanced-analytics/tutorials/deepdive-define-and-use-compute-contexts.md)

## <a name="previous-step"></a>Passaggio precedente

[Creare oggetti dati di SQL Server usando RxSqlServerData](../../advanced-analytics/tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)
