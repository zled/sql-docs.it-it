---
title: Spostare dati tra SQL Server e il file con estensione XDF (SQL e R approfondimento) | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 6eb2ed7bdda7fab662048d7e8da692253cf9c164
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31204593"
---
# <a name="move-data-between-sql-server-and-xdf-file-sql-and-r-deep-dive"></a>Spostare dati tra SQL Server e il file con estensione XDF (SQL e R approfondimento)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo fa parte dell'esercitazione approfondimento di analisi scientifica dei dati, su come usare [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) con SQL Server.

In questo passaggio descritto come utilizzare un file con estensione XDF per trasferire dati tra i contesti di calcolo remoti e locali. L'archiviazione dei dati in un file con estensione XDF consente di eseguire trasformazioni sui dati.

Al termine, utilizzare i dati nel file per creare un nuovo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella. La funzione [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) possono applicare trasformazioni ai dati ed esegue la conversione tra i frame di dati e i file con estensione xdf.
  
## <a name="create-a-sql-server-table-from-an-xdf-file"></a>Creare una tabella di SQL Server da un file con estensione XDF

Per questo esercizio, utilizzare nuovamente i dati di frodi carta di credito. In questo scenario è stato richiesto di eseguire alcune analisi aggiuntive sugli utenti in California, Oregon e Washington. In modo più efficiente, si è deciso di archiviare i dati per solo questi stati nel computer locale e utilizzare solo il sesso di variabili, titolare della carta, stato e saldo.

1. Riutilizzo di `stateAbb` variabile creata in precedenza per identificare i livelli da includere e scriverli in una nuova variabile, `statesToKeep`.
  
    ```R
    statesToKeep <- sapply(c("CA", "OR", "WA"), grep, stateAbb)
    statesToKeep
    ```
    **Risultati**
    
    CA|OPPURE|WA
    ----|----|----
    5|38|48
    
2. Definire i dati che si desidera trasferire tramite da SQL Server, utilizzando un [!INCLUDE[tsql](../../includes/tsql-md.md)] query.  In un secondo momento si utilizza questa variabile come il *inData* argomento per **rxImport**.
  
    ```R
    importQuery <- paste("SELECT gender,cardholder,balance,state FROM",  sqlFraudTable,  "WHERE (state = 5 OR state = 38 OR state = 48)")
    ```
  
    Assicurarsi che la query non contenga caratteri nascosti, ad esempio avanzamenti riga e tabulazioni.
  
3. Successivamente, definire le colonne da utilizzare quando si lavora con i dati in R. Ad esempio, nel set di dati più piccoli, è necessario solo tre livelli di fattore, poiché la query restituisce i dati per solo tre stati.  Applicare il `statesToKeep` variabile per identificare i livelli appropriati da includere.
  
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
    
    Il [rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata) funzione possibile importare dati da qualsiasi origine dati supportata in un file con estensione XDF locale. Utilizzando una copia locale dei dati è utile quando si desidera effettuare molti analisi diverse sui dati, ma evitare di eseguire ripetutamente la stessa query.

5. Creare l'oggetto origine dati, passando le variabili definite in precedenza come argomenti **RxSqlServerData**.
  
    ```R
    sqlServerImportDS <- RxSqlServerData(
        connectionString = sqlConnString,
        sqlQuery = importQuery,
        colInfo = importColInfo)
    ```
  
6. Chiamare **rxImport** per scrivere i dati in un file denominato `ccFraudSub.xdf`, nella directory di lavoro corrente.
  
    ```R
    localDS <- rxImport(inData = sqlServerImportDS,
        outFile = "ccFraudSub.xdf",
        overwrite = TRUE)
    ```
  
    Il `localDs` oggetto restituito dal **rxImport** funzione è un leggero **RxXdfData** oggetto origine dati che rappresenta il `ccFraud.xdf` file di dati archiviati localmente sul disco.
  
7. Chiamare [rxGetVarInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf) nel file XDF per verificare che lo schema dei dati sia lo stesso.
  
    ```R
    rxGetVarInfo(data = localDS)
    ```

    **Risultati**
    
    *rxGetVarInfo(data = localDS)*

    *Var 1: gender, Type: factor, no factor levels available*

    *Var 2: cardholder, Type: factor, no factor levels available*

    *Var 3: balance, Type: integer, Low/High: (0, 22463)*

    *Var 4: state, Type: factor, no factor levels available*
  
8. È ora possibile chiamare varie funzioni R per analizzare l'oggetto `localDs`, come si è soliti fare con i dati di origine in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ad esempio, è possibile creare un riepilogo per sesso:
  
    ```R
    rxSummary(~gender + cardholder + balance + state, data = localDS)
    ```

Dopo aver appreso l'uso di contesti di calcolo e aver usato origini dati diverse è possibile passare alla parte più divertente. Nella lezione successiva e finale creare una simulazione semplice che esegue una funzione R personalizzata nel server remoto.

## <a name="next-step"></a>Passaggio successivo

[Creare una simulazione semplice](../../advanced-analytics/tutorials/deepdive-create-a-simple-simulation.md)

## <a name="previous-step"></a>Passaggio precedente

[Analizzare i dati in un contesto di calcolo locale](../../advanced-analytics/tutorials/deepdive-analyze-data-in-local-compute-context.md)



