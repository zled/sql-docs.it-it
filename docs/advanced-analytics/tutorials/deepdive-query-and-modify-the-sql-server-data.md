---
title: Eseguire una query e modificare i dati di SQL Server (SQL e R approfondimento) | Documenti Microsoft
ms.custom: 
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
ms.assetid: 8c7007a9-9a8f-4dcd-8068-40060d4f6444
caps.latest.revision: "17"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 38273ac15673344ff00714d38ec87386ca5dae64
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2017
---
# <a name="query-and-modify-the-sql-server-data-sql-and-r-deep-dive"></a>Eseguire una query e modificare i dati di SQL Server (SQL e R approfondimento)

Questo articolo fa parte dell'esercitazione approfondimento di analisi scientifica dei dati, su come usare [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) con SQL Server.

Ora che i dati sono stati caricati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è possibile usare le origini dati create come argomenti per le funzioni R in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], per ottenere le informazioni di base sulle variabili e generare riepiloghi e istogrammi.

In questo passaggio, utilizzare nuovamente le origini dati per eseguire un'analisi rapida e quindi per ottimizzare i dati.

## <a name="query-the-data"></a>Eseguire query sui dati

Per prima cosa ottenere un elenco delle colonne e dei relativi tipi di dati.

1.  Utilizzare la funzione [rxGetVarInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf) e specificare l'origine dati che si desidera analizzare.

    A seconda della versione di RevoScaleR, è inoltre possibile utilizzare [rxGetVarNames](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarnames). 
  
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

Tutte le variabili vengono archiviate come valori interi, ma alcune variabili rappresentano dati relativi alle categorie denominati *variabili di fattore* in R. Ad esempio, la colonna *stato* contiene numeri che rappresentano gli identificatori di 50 stati più District of Columbia.  Per facilitare la comprensione dei dati, sostituire i numeri con un elenco di codici di stato.

In questo passaggio, creare un vettore di stringhe contenente le abbreviazioni e quindi eseguire il mapping di questi valori categorici per gli identificatori di tipo integer originale. È quindi utilizzare la nuova variabile nel *colInfo* argomento, per specificare che la colonna deve essere gestito come un fattore. Ogni volta che si analizzano i dati o spostarlo, vengono utilizzate le abbreviazioni e la colonna viene gestita come un fattore.

Il mapping della colonna alle abbreviazioni prima di usarla come fattore consente di migliorare anche le prestazioni. Per ulteriori informazioni, vedere [R e i dati di ottimizzazione](..\r\r-and-data-optimization-r-services.md).

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
    
    *Var 2: sesso 2 livelli factor: maschile femminile*
    
    *Var 3: stato livelli fattore 51: AK AL AR AZ CA... VT WA WI WV WY*
    
    *Var 4: livelli di fattore titolare 2: entità secondaria*
    
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
