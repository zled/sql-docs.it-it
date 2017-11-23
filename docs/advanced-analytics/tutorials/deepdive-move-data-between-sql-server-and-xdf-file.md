---
title: Spostare dati tra SQL Server e i File con estensione XDF | Documenti Microsoft
ms.custom: 
ms.date: 05/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: 40887cb3-ffbb-4769-9f54-c006d7f4798c
caps.latest.revision: "17"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2579c75a4d99e04d5cae60870632c45b52a56cac
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="move-data-between-sql-server-and-xdf-file"></a>Spostare i dati tra SQL Server e file XDF

Quando si lavora in un contesto di calcolo locale, si ha accesso a entrambi i file di dati locali e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database (definito da un'origine dati RxSqlServerData).

In questa sezione verrà illustrato come ottenere i dati e archiviarli in un file nel computer locale, in modo tale che sia possibile trasformarli. Al termine, si userà i dati nel file per creare un nuovo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella, tramite rxDataStep.
  
## <a name="create-a-sql-server-table-from-an-xdf-file"></a>Creare una tabella di SQL Server da un file XDF

La funzione rxImport consente di importare dati da qualsiasi origine dati supportata in un file con estensione XDF locale. È utile usare un file locale se si vuole sottoporre ad analisi diverse i dati archiviati nel database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] senza continuare a ripetere la stessa query.

Per questo esercizio saranno usati nuovamente i dati di frode di una carta di credito. In questo scenario è stato richiesto di eseguire alcune analisi aggiuntive sugli utenti in California, Oregon e Washington. Per maggiore efficienza, si è deciso di archiviare i dati di questi soli tre paesi nel computer locale e di lavorare con le variabili sesso, titolare carta e saldo.

1. Usare di nuovo il vettore *stateAbb* creato in precedenza per identificare i livelli da includere e stampare la nuova variabile *statesToKeep*nella console.
  
    ```R
    statesToKeep <- sapply(c("CA", "OR", "WA"), grep, stateAbb)
    statesToKeep
    ```
    **Risultati**
    
    CA|OPPURE|WA
    ----|----|----
    5|38|48
    
2. A questo punto definire i dati che si vuole rilevare da SQL Server usando una query [!INCLUDE[tsql](../../includes/tsql-md.md)] .  Questa variabile sarà poi usata come argomento *inData* per *rxImport*.
  
    ```R
    importQuery <- paste("SELECT gender,cardholder,balance,state FROM",  sqlFraudTable,  "WHERE (state = 5 OR state = 38 OR state = 48)")
    ```
  
    Assicurarsi che la query non contenga caratteri nascosti, ad esempio avanzamenti riga e tabulazioni.
  
3. Successivamente, verranno definite le colonne da utilizzare quando si lavora con i dati in R. Ad esempio, nel set di dati più piccoli, è necessario solo tre livelli di fattore, perché la query restituirà i dati relativi solo tre stati.  È possibile usare nuovamente la variabile *statesToKeep* per identificare i livelli appropriati da includere.
  
    ```R
    importColInfo <- list(
        gender = list( type = "factor",  levels = c("1", "2"), newLevels = c("Male", "Female")),
        cardholder = list(  type = "factor",  levels = c("1", "2"), newLevels = c("Principal", "Secondary")),
        state = list(   type = "factor",  levels = as.character(statesToKeep), newLevels = names(statesToKeep))
            )
    ```
  
4. Impostare il contesto di calcolo **locale**, dal momento che tutti i dati disponibili nel computer locale.
  
    ```R
    rxSetComputeContext("local")
    ```
  
5. Creare l'oggetto origine dati mediante il passaggio di tutte le variabili definite come argomenti RxSqlServerData.
  
    ```R
    sqlServerImportDS <- RxSqlServerData(
        connectionString = sqlConnString,
        sqlQuery = importQuery,
        colInfo = importColInfo)
    ```
  
6. Chiamare quindi **rxImport** per scrivere i dati in un file denominato `ccFraudSub.xdf`, nella directory di lavoro corrente.
  
    ```R
    localDS <- rxImport(inData = sqlServerImportDS,
        outFile = "ccFraudSub.xdf",
        overwrite = TRUE)
    ```
  
    Il *localDs* oggetto restituito dalla funzione rxImport è un oggetto di origine dati di RxXdfData leggera che rappresenta il file di dati ccFraud.xdf archiviato localmente sul disco.
  
7. Chiamare rxGetVarInfo su un file con estensione XDF per verificare che lo schema di dati è lo stesso.
  
    ```R
    rxGetVarInfo(data = localDS)
    ```

    **Risultati**
    
    *rxGetVarInfo(data = localDS)*

    *Var 1: gender, Type: factor, no factor levels available*

    *Var 2: cardholder, Type: factor, no factor levels available*

    *Var 3: balance, Type: integer, Low/High: (0, 22463)*

    *Var 4: state, Type: factor, no factor levels available*
  
8. È ora possibile chiamare varie funzioni R per analizzare l'oggetto *localDs* , come si è soliti fare con i dati di origine in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Esempio:
  
    ```R
    rxSummary(~gender + cardholder + balance + state, data = localDS)
    ```

Dopo aver appreso l'uso di contesti di calcolo e aver usato origini dati diverse è possibile passare alla parte più divertente. Nella lezione successiva, che è anche l'ultima, si creerà una semplice simulazione usando una funzione R personalizzata. La simulazione sarà eseguita nel server remoto.

## <a name="next-step"></a>Passaggio successivo

[Creare una simulazione semplice](../../advanced-analytics/tutorials/deepdive-create-a-simple-simulation.md)

## <a name="previous-step"></a>Passaggio precedente

[Analizzare i dati nel contesto di calcolo locale](../../advanced-analytics/tutorials/deepdive-analyze-data-in-local-compute-context.md)



