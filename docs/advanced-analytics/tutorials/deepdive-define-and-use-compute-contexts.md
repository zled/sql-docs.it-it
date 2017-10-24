---
title: Definire e usare i contesti di calcolo (procedura approfondita di data science) | Microsoft Docs
ms.custom: 
ms.date: 05/22/2017
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
ms.assetid: b13058d0-9c6a-44e1-849b-72189d9050ba
caps.latest.revision: 17
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 511738cfce795600bcfa06a95de4cdf3d6b503bb
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="define-and-use-compute-contexts"></a>Definire e usare i contesti di calcolo


Si supponga di voler eseguire alcuni dei calcoli più complessi nel server invece che nel computer locale. A tale scopo, è possibile creare un contesto di calcolo che consenta di eseguire codice R nel server.

La funzione **RxInSqlServer** è una delle funzioni R avanzate disponibili nel pacchetto [RevoScaleR](https://msdn.microsoft.com/microsoft-r/scaler/scaler) . La funzione gestisce le attività di creazione della connessione di database e del passaggio di oggetti tra il computer locale e il contesto di esecuzione remoto.

In questo passaggio verrà illustrato come usare la funzione **RxInSqlServer** per definire un contesto di calcolo nel codice R.

Per creare un contesto di calcolo sono necessarie le informazioni di base seguenti relative all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :

- La stringa di connessione per l'istanza
- Una specifica per la modalità di gestione dell'output
- Argomenti facoltativi per abilitare la traccia o specificare una directory condivisa

## <a name="create-and-set-a-compute-context"></a>Creare e impostare un contesto di calcolo

1. Specificare la stringa di connessione per l'istanza in cui verranno eseguiti i calcoli.  Questa è una delle diverse variabili che verranno passate alla funzione *RxInSqlServer* per creare il contesto di calcolo. È possibile riutilizzare la stringa di connessione creata in precedenza oppure crearne una diversa se si vuole spostare i calcoli in un server diverso oppure usare un'identità diversa.

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
  
    L'argomento *wait* per *RxInSqlServer* supporta queste opzioni:
  
    -   **TRUE**. Il processo sarà in modalità di blocco e restituisce risultati finché non viene completato o ha esito negativo.  Per ulteriori informazioni, vedere [distribuita e il calcolo parallelo in Microsoft R](https://msdn.microsoft.com/microsoft-r/scaler-distributed-computing).
  
    -   **FALSE**. I processi saranno in modalità non di blocco e restituiranno immediatamente risultati, consentendo di continuare a eseguire altro codice R. Tuttavia, anche in modalità non di blocco, la connessione client con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve essere mantenuta durante l'esecuzione del processo.

3. Facoltativamente, è possibile specificare il percorso di una directory locale per l'uso condiviso da parte della sessione R locale e del computer  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] remoto e dei relativi account.

    ```R
    sqlShareDir <- paste("c:\\AllShare\\", Sys.getenv("USERNAME"), sep="")
    ```
    
4. Se si desidera creare manualmente una directory specifica per la condivisione, è possibile aggiungere una riga simile alla seguente. Per determinare la cartella è attualmente in uso per la condivisione, eseguire `rxGetComputeContext`, che restituisce i dettagli sull'oggetto contesto di calcolo. Per altre informazioni, vedere le [informazioni di riferimento di ScaleR](https://msdn.microsoft.com/microsoft-r/scaler/packagehelp/rxinsqlserver).

    ```
    dir.create(sqlShareDir, recursive = TRUE)
    ```

4. Avere preparato tutte le variabili, fornirli come argomenti al costruttore RxInSqlServer per creare il *oggetto contesto di calcolo*.

    ```R
    sqlCompute <- RxInSqlServer(  
         connectionString = sqlConnString,
         wait = sqlWait,
         consoleOutput = sqlConsoleOutput)
    ```
    
    È possibile osservare che la sintassi per RxInSqlServer * è praticamente identica a quello della funzione RxSqlServerData utilizzata in precedenza per definire l'origine dati. Esistono tuttavia alcune differenze importanti.
      
    - L'oggetto origine dati, definito tramite la funzione RxSqlServerData, specifica in cui i dati vengono archiviati.
    
    - Al contrario, il contesto di calcolo (definito tramite la funzione RxInSqlServer) indica dove aggregazioni e altri calcoli vengono effettuate al.
    
    La definizione di un contesto di calcolo non influenza gli altri calcoli generici di R che possono essere eseguiti nella workstation e non modifica l'origine dei dati. Ad esempio, è possibile definire un file di testo locale come origine dati ma modificare il contesto di calcolo in SQL Server ed effettuare tutte le letture e i riepiloghi nei dati nel computer SQL Server.

## <a name="enable-tracing-on-the-compute-context"></a>Abilitare la traccia nel contesto di calcolo

A volte le operazioni vengono eseguite correttamente nel contesto locale ma si verificano problemi quando vengono eseguite in un contesto di calcolo remoto. Per analizzare i problemi o monitorare le prestazioni, è possibile abilitare la traccia nel contesto di calcolo per supportare la risoluzione dei problemi in fase di esecuzione.

1. Creare un nuovo contesto di calcolo che utilizza la stessa stringa di connessione, ma è aggiungere gli argomenti *traceEnabled* e *traceLevel* per il *RxInSqlServer* costruttore.

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

2. Per modificare il contesto di calcolo, utilizzare la funzione rxSetComputeContext e specificare il contesto in base al nome.

    ```R
    rxSetComputeContext( sqlComputeTrace)
    ```

    > [!NOTE]
    > 
    > Per questa esercitazione verrà usato il contesto di calcolo senza abilitazione della traccia. Ciò avviene perché non è stata testata le prestazioni per l'opzione abilitata per tutte le operazioni.
    > 
    > Tuttavia, se si decide di utilizzare l'analisi, tenere presente che l'esperienza può dipendere dalla connettività di rete.

Dopo aver creato un contesto di calcolo remoto, verrà descritto come cambiare i contesti di calcolo per eseguire il codice R sul server o in locale.

## <a name="next-step"></a>Passaggio successivo

[Creare ed eseguire gli script R](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)


## <a name="previous-step"></a>Passaggio precedente

[Eseguire una query e modificare i dati SQL Server](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)



