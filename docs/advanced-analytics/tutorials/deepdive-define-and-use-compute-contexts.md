---
title: Definire e usare i contesti di calcolo (amp;#40;procedura approfondita di R e SQL) | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 6a76e07cb2ecd03a59112f6c39e3fa2f7895e0a2
ms.sourcegitcommit: aa9d2826e3c451f4699c0e69c9fcc8a2781c6213
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2018
ms.locfileid: "45975640"
---
# <a name="define-and-use-compute-contexts-sql-and-r-deep-dive"></a>Definire e usare i contesti di calcolo (amp;#40;procedura approfondita di R e SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo fa parte dell'esercitazione approfondita di Data Science, su come usare [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) con SQL Server.

Questa lezione viene presentato il [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) funzione, che consente di definire un contesto di calcolo per SQL Server e quindi eseguire calcoli complessi nel server, anziché nel computer locale. 

RevoScaleR supporta più contesti di calcolo, in modo che sia possibile eseguire codice R in Hadoop, Spark o nel database. Per SQL Server, è necessario definire il server e la funzione gestisce le attività di creazione del database di connessione e passando oggetti tra il computer locale e il contesto di esecuzione remoto.

La funzione che crea il Server SQL di calcolo contesto utilizza le informazioni seguenti:

- Stringa di connessione per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza
- Specifica della modalità di gestione dell'output
- Argomenti facoltativi, abilitare la traccia o specificano il livello di traccia
- Specifica facoltativa di una directory di dati condiviso

## <a name="create-and-set-a-compute-context"></a>Creare e impostare un contesto di calcolo

1. Specificare la stringa di connessione per l'istanza in cui vengono eseguiti i calcoli.  È possibile riutilizzare la stringa di connessione creata in precedenza. Se si desidera spostare i calcoli in un server diverso o utilizzare un account di accesso diversi per eseguire alcune attività, è possibile creare una stringa di connessione diversa.

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
  
    -   **TRUE**. Il processo è configurato come il blocco e non restituisce fino a quando non viene completato o non è riuscita.  Per altre informazioni, vedere [applicazione distribuita e l'elaborazione parallela in Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing).
  
    -   **FALSE**. I processi sono configurati come non di blocco e restituiranno immediatamente risultati, consentendo di continuare a eseguire altro codice R. Tuttavia, anche in modalità non di blocco, la connessione client con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve essere mantenuta durante l'esecuzione del processo.

3. Facoltativamente, è possibile specificare il percorso di una directory locale per l'uso condiviso dalla sessione R locale e remoto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer e i relativi account.

    ```R
    sqlShareDir <- paste("c:\\AllShare\\", Sys.getenv("USERNAME"), sep="")
    ```
    
4. Se si vuole creare manualmente una directory specifica per la condivisione, è possibile aggiungere una riga simile alla seguente:

    ```
    dir.create(sqlShareDir, recursive = TRUE)
    ```

    Per determinare quale cartella è attualmente in uso per la condivisione, eseguire `rxGetComputeContext()`, che restituisce i dettagli sull'oggetto contesto di calcolo. Per altre informazioni, vedere le [informazioni di riferimento di ScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/).

4. Dopo avere preparato tutte le variabili, fornirle come argomenti per il **RxInSqlServer** costruttore, per creare il *oggetto contesto di calcolo*.

    ```R
    sqlCompute <- RxInSqlServer(  
         connectionString = sqlConnString,
         wait = sqlWait,
         consoleOutput = sqlConsoleOutput)
    ```
    
    La sintassi per **RxInSqlServer** quasi identica a quella delle **RxSqlServerData** funzione usato in precedenza per definire l'origine dati. Esistono tuttavia alcune differenze importanti.
      
    - L'oggetto origine dati definito usando la funzione [RxSqlServerData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata)specifica la posizione in cui vengono archiviati i dati.
    
    - Al contrario, il contesto di calcolo definito usando la funzione [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) indica dove aggregazioni e altri calcoli devono aver luogo.
    
    La definizione di un contesto di calcolo non influenza gli altri calcoli generici di R che possono essere eseguiti nella workstation e non modifica l'origine dei dati. Ad esempio, è possibile definire un file di testo locale come origine dati ma modificare il contesto di calcolo in SQL Server ed effettuare tutte le letture e i riepiloghi nei dati nel computer SQL Server.

## <a name="enable-tracing-on-the-compute-context"></a>Abilitare la traccia sul contesto di calcolo

A volte le operazioni vengono eseguite correttamente nel contesto locale ma si verificano problemi quando vengono eseguite in un contesto di calcolo remoto. Se si desidera analizzare i problemi o monitorare le prestazioni, è possibile abilitare la traccia nel contesto di calcolo, per supportare la risoluzione dei problemi in fase di esecuzione.

1. Creare un nuovo contesto di calcolo che usa la stessa stringa di connessione, ma aggiungere gli argomenti *traceEnabled* e *traceLevel* per il **RxInSqlServer** costruttore.

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
    > Per questa esercitazione, usare il contesto di calcolo che non è abilitata l'analisi. 
    > 
    > Tuttavia, se si decide di utilizzare la traccia, tenere presente che l'esperienza può dipendere dalla connettività di rete. Tenere anche presente che perché le prestazioni per l'opzione di abilitazione della traccia non sono stata testata per tutte le operazioni.

Nel passaggio successivo informazioni su come usare i contesti di calcolo, per eseguire codice R nel server o in locale.

## <a name="next-step"></a>Passaggio successivo

[Creare ed eseguire script R](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)

## <a name="previous-step"></a>Passaggio precedente

[Eseguire query e modificare i dati SQL Server](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)
