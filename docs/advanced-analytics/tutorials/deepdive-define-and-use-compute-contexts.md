---
title: Definire e utilizzare i contesti di calcolo (SQL e R approfondimento) | Documenti Microsoft
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
ms.assetid: b13058d0-9c6a-44e1-849b-72189d9050ba
caps.latest.revision: "17"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 09612d8f8f31e020215567e6e3fa2d1981d0b385
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="define-and-use-compute-contexts-sql-and-r-deep-dive"></a>Definire e utilizzare i contesti di calcolo (SQL e R approfondimento)

Questo articolo fa parte dell'esercitazione approfondimento di analisi scientifica dei dati, su come usare [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) con SQL Server.

In questa lezione introduce il [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) funzione, che consente di definire un contesto di calcolo per SQL Server e quindi eseguire calcoli complessi sul server, anziché nel computer locale. 

RevoScaleR supporta più contesti di calcolo, in modo che sia possibile eseguire codice R in Hadoop, Spark o nel database. Per SQL Server, è necessario definire il server e la funzione gestisce le attività di creazione del database come oggetti connessione e il passaggio tra il computer locale e il contesto di esecuzione remoto.

La funzione che crea il Server SQL calcolo contesto utilizza le informazioni seguenti:

- Stringa di connessione per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza
- Specifica della modalità di gestione di output
- Argomenti facoltativi che abilita la traccia oppure specificare il livello di traccia
- Specifica facoltativa di una directory di dati condivisi

## <a name="create-and-set-a-compute-context"></a>Creare e impostare un contesto di calcolo

1. Specificare la stringa di connessione per l'istanza in cui vengono eseguiti i calcoli.  È possibile utilizzare nuovamente la stringa di connessione creata in precedenza. Se si desidera spostare i calcoli in un server diverso oppure utilizzare un account di accesso diverso per eseguire alcune attività, è possibile creare una stringa di connessione diversi.

    **Uso di un account di accesso SQL**

      ```R
      sqlConnString <- "Driver=SQL Server;Server=<SQL Server instance name>; Database=<database name>;Uid=<SQL user name>;Pwd=<password>"
      ```

    **Uso dell'autenticazione di Windows**

      ```R
      sqlConnString <- "Driver=SQL Server;Server=instance_name;Database=DeepDive;Trusted_Connection=True"
      ```
2. Specificare il modo in cui si vuole gestire l'output. Nel codice seguente viene indicato che la sessione di R nella workstation deve sempre attendere i risultati del processo R e non restituire l'output della console dei calcoli remoti.
  
    ```R
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    ```
  
    L'argomento *wait* per **RxInSqlServer** supporta queste opzioni:
  
    -   **TRUE**. Il processo viene configurato come il blocco e non restituisce fino a quando è stata completata o non è riuscita.  Per ulteriori informazioni, vedere [distribuita e il calcolo parallelo in Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing).
  
    -   **FALSE**. I processi sono configurati come non bloccanti e restituiscono immediatamente consentendo di continuare a eseguire altro codice R. Tuttavia, anche in modalità non di blocco, la connessione client con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve essere mantenuta durante l'esecuzione del processo.

3. Facoltativamente, è possibile specificare il percorso di una directory locale per la condivisione, la sessione R locale e remoto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer e i relativi account.

    ```R
    sqlShareDir <- paste("c:\\AllShare\\", Sys.getenv("USERNAME"), sep="")
    ```
    
4. Se si desidera creare manualmente una directory specifica per la condivisione, è possibile aggiungere una riga simile alla seguente:

    ```
    dir.create(sqlShareDir, recursive = TRUE)
    ```

    Per determinare la cartella è attualmente in uso per la condivisione, eseguire `rxGetComputeContext()`, che restituisce i dettagli sull'oggetto contesto di calcolo. Per altre informazioni, vedere le [informazioni di riferimento di ScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/).

4. Come argomenti per avere preparato tutte le variabili, fornire loro il **RxInSqlServer** costruttore, per creare il *oggetto contesto di calcolo*.

    ```R
    sqlCompute <- RxInSqlServer(  
         connectionString = sqlConnString,
         wait = sqlWait,
         consoleOutput = sqlConsoleOutput)
    ```
    
    La sintassi per **RxInSqlServer** quasi identica a quella del **RxSqlServerData** funzione utilizzata in precedenza per definire l'origine dati. Esistono tuttavia alcune differenze importanti.
      
    - L'oggetto origine dati definito usando la funzione [RxSqlServerData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata)specifica la posizione in cui vengono archiviati i dati.
    
    - Al contrario, il contesto di calcolo, definito tramite la funzione [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) indica dove aggregazioni e altri calcoli vengono effettuate al.
    
    La definizione di un contesto di calcolo non influenza gli altri calcoli generici di R che possono essere eseguiti nella workstation e non modifica l'origine dei dati. Ad esempio, è possibile definire un file di testo locale come origine dati ma modificare il contesto di calcolo in SQL Server ed effettuare tutte le letture e i riepiloghi nei dati nel computer SQL Server.

## <a name="enable-tracing-on-the-compute-context"></a>Abilitare la traccia nel contesto di calcolo

A volte le operazioni vengono eseguite correttamente nel contesto locale ma si verificano problemi quando vengono eseguite in un contesto di calcolo remoto. Per analizzare i problemi o monitorare le prestazioni, è possibile abilitare la traccia nel contesto di calcolo per supportare la risoluzione dei problemi in fase di esecuzione.

1. Creare un nuovo contesto di calcolo che utilizza la stessa stringa di connessione, ma è aggiungere gli argomenti *traceEnabled* e *traceLevel* per il **RxInSqlServer** costruttore.

    ```R
    sqlComputeTrace <- RxInSqlServer(
        connectionString = sqlConnString,
        #shareDir = sqlShareDir,
        wait = sqlWait,
        consoleOutput = sqlConsoleOutput,
        traceEnabled = TRUE,
        traceLevel = 7)
    ```
  
    Nell'esempio la proprietà *traceLevel* è impostata su 7, ovvero sulla visualizzazione di tutte le informazioni di traccia.

2. Per modificare il contesto di calcolo, usare la funzione [rxSetComputeContext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) e specificare il contesto per nome.

    ```R
    rxSetComputeContext( sqlComputeTrace)
    ```

    > [!NOTE]
    > 
    > Per questa esercitazione, usare il contesto di calcolo che non dispone di funzionalità di traccia abilitato. 
    > 
    > Tuttavia, se si decide di utilizzare l'analisi, tenere presente che l'esperienza può dipendere dalla connettività di rete. Occorre essere consapevoli che perché non è stata testata le prestazioni per l'opzione abilitata per tutte le operazioni.

Nel passaggio successivo che si informazioni sull'utilizzo di calcolo contesti, per eseguire il codice R nel server o in locale.

## <a name="next-step"></a>Passaggio successivo

[Creare ed eseguire script R](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)

## <a name="previous-step"></a>Passaggio precedente

[Eseguire query e modificare i dati SQL Server](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)
