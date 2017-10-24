---
title: Eseguire una query e modificare i dati SQL Server | Documenti Microsoft
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
ms.assetid: 8c7007a9-9a8f-4dcd-8068-40060d4f6444
caps.latest.revision: 17
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4970a681733d8920b9eef6b27023f9ae1c7ce981
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="query-and-modify-the-sql-server-data"></a>Eseguire query e modificare i dati SQL Server

Ora che i dati sono stati caricati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è possibile usare le origini dati create come argomenti per le funzioni R in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], per ottenere le informazioni di base sulle variabili e generare riepiloghi e istogrammi.

In questo passaggio si userà nuovamente le origini dati per eseguire un'analisi rapida e quindi per ottimizzare i dati.

## <a name="query-the-data"></a>Esecuzione di query sui dati

Per prima cosa ottenere un elenco delle colonne e dei relativi tipi di dati.

1.  Utilizzare la funzione **rxGetVarInfo** e specificare l'origine dati che si desidera analizzare.
  
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

In questo passaggio verrà specificato un vettore di stringhe contenente le abbreviazioni e verrà eseguito il mapping dei valori relativi alle categorie agli identificatori interi originali. La variabile creata verrà usata nell'argomento *colInfo* per specificare che la colonna deve essere gestita come fattore. Da quel momento, ogni volta che i dati vengono analizzati o importati, verranno usate le abbreviazioni e la colonna gestita come fattore.

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
  
3. Per creare l'origine dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che usa i dati aggiornati, chiamare la funzione *RxSqlServerData* come in precedenza, ma aggiungere l'argomento *colInfo* .
  
    ```R
    sqlFraudDS <- RxSqlServerData(connectionString = sqlConnString,
    table = sqlFraudTable, colInfo = ccColInfo,
    rowsPerRead = sqlRowsPerRead)
    ```
  
    - Per il parametro *table* , passare la variabile *sqlFraudTable*che contiene l'origine dati creata in precedenza.
    - Per il parametro *colInfo* , passare la variabile *ccColInfo* che contiene i tipi di dati di colonna e i livelli di fattore.
    - Il mapping della colonna alle abbreviazioni prima di usarla come fattore consente di migliorare anche le prestazioni. Per altre informazioni, vedere [R e ottimizzazione dei dati](https://msdn.microsoft.com/library/mt723575.aspx)
  
4.  È ora possibile utilizzare rxGetVarInfo la funzione per visualizzare le variabili nella nuova origine dati.
  
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

[Definire e utilizzare i contesti di calcolo](../../advanced-analytics/tutorials/deepdive-define-and-use-compute-contexts.md)

## <a name="previous-step"></a>Passaggio precedente

[Creare oggetti dati di SQL Server usando RxSqlServerData](../../advanced-analytics/tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)




