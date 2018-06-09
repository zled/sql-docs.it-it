---
title: Usare Python con revoscalepy per creare un modello | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: d549b06b9fe371dc2b1966c62776ec4e88c45726
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740830"
---
# <a name="use-python-with-revoscalepy-to-create-a-model"></a>Usare Python con revoscalepy per creare un modello
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questa lezione si informazioni su come eseguire il codice Python da un client di sviluppo remoto, per creare un modello di regressione lineare in SQL Server. 

## <a name="prerequisites"></a>Prerequisiti

+ In questa lezione utilizza dati diversi dalle lezioni precedenti. Non è necessario completare prima le lezioni precedenti. Tuttavia, se si hanno completato le lezioni precedenti e si dispone di un server già configurato per l'esecuzione di Python, utilizzare il server e database come contesto di calcolo.
+ Per eseguire il codice Python utilizzando SQL Server come un calcolo contesto richiede SQL Server 2017 o versione successiva. Inoltre, è necessario installare in modo esplicito e quindi abilitare la funzionalità, **Machine Learning Services**, scegliendo l'opzione di linguaggio Python.

    Se è installata una versione non definitiva di SQL Server 2017, è necessario aggiornare a almeno la versione RTM. Nelle versioni successive del servizio è sono costantemente espandere e migliorare le funzionalità di Python. Alcune funzionalità di questa esercitazione potrebbero non funzionare nelle prime versioni di pre-release.

+ Questo esempio viene utilizzato un ambiente di Python predefinito, denominato `PYTEST_SQL_SERVER`. L'ambiente è stato configurato per contenere **revoscalepy** e altre librerie necessarie. 

    Se non si dispone di un ambiente configurato per l'esecuzione di Python, è necessario farlo separatamente. Informazioni su come creare o modificare gli ambienti Python esula dall'ambito di questa esercitazione. Per ulteriori informazioni su come configurare un client Python che contiene le librerie corrette, vedere [client di installare Python](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter) e [Python collegamento agli strumenti](https://docs.microsoft.com/machine-learning-server/python/quickstart-python-tools).

## <a name="remote-compute-contexts-and-revoscalepy"></a>Revoscalepy e contesti di calcolo remoto

In questo esempio viene illustrato il processo di creazione di un modello di Python in remota _contesto di calcolo_, che consente utilizzare un client, ma scegliere un ambiente remoto, ad esempio SQL Server, Spark o Server di Machine Learning, in cui il operazioni vengono effettivamente eseguite. Contesti di calcolo utilizzando rende più semplice scrivere codice una sola volta e distribuirlo in qualsiasi ambiente supportato.

Per eseguire codice Python in SQL Server, è necessario il **revoscalepy** pacchetto. Si tratta di un pacchetto di Python speciale fornito da Microsoft, simile al **RevoScaleR** pacchetto per il linguaggio R. Il **revoscalepy** pacchetto supporta la creazione di contesti di calcolo e fornisce l'infrastruttura per il passaggio di dati e modelli tra una workstation locale e un server remoto. Il **revoscalepy** funzione che supporta l'esecuzione del codice nel database è [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxinsqlserver).

In questa lezione è utilizzare dati in SQL Server per eseguire il training di un modello lineare basato su [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod), una funzione in **revoscalepy** regressione che supporta i set di dati molto grandi. 

Questa lezione viene illustrato inoltre i concetti di base impostare e utilizzare quindi un **contesto di calcolo di SQL Server** in Python. Per una discussione su come usare contesti di calcolo con altre piattaforme e che i contesti di calcolo sono supportati, vedere [contesto di calcolo per l'esecuzione dello script nel Server di Machine Learning](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context)

## <a name="prepare-the-database-and-sample-data"></a>Preparare i dati e del database

1. In questa lezione viene utilizzato il database `sqlpy`. Se non è stata completata una delle lezioni precedenti, è possibile creare il database eseguendo il codice seguente:

    ```sql
    CREATE DATABASE sqlpy;
    GO
    USE sqlpy;
    GO
    ```

    > [!IMPORTANT]
    > Se si desidera utilizzare un database diverso, assicurarsi di modificare il codice di esempio e il nome del database nella stringa di connessione.

2. In questo esempio viene utilizzato il set di dati Airline, disponibile nelle R e Python. Dopo aver creato un database per gli esempi di Python, popolare una tabella con i dati come descritto qui: [campionare i dati in RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/sample-built-in-data).

3. Modificare il nome dell'ambiente per utilizzare un ambiente disponibile nel client.

## <a name="run-the-sample-code"></a>Eseguire il codice di esempio

Dopo aver preparato i database e avere i dati di training archiviati in una tabella, aprire un ambiente di sviluppo Python ed eseguire l'esempio di codice.

Nel codice vengono eseguite le seguenti operazioni:

1. Importa le funzioni e le librerie richieste.
2. Crea una connessione a SQL Server. Crea **origine dati** oggetti per l'utilizzo con i dati.
3. Modifica dei dati mediante **trasformazioni** in modo che può essere utilizzato dall'algoritmo di regressione logistica.
4. Chiamate `rx_lin_mod` e definisce la formula utilizzata per adattare il modello.
5. Genera un set di stime basate sui dati originali.
6. Crea un riepilogo in base ai valori stimati.

Tutte le operazioni vengono eseguite utilizzando un'istanza di SQL Server come contesto di calcolo.

> [!NOTE]
> Per una dimostrazione di questo esempio in esecuzione dalla riga di comando, vedere il video: [SQL Server 2017 avanzate Analitica con Python](https://www.youtube.com/watch?v=FcoY795jTcc)

### <a name="sample-code"></a>Codice di esempio

```python
from revoscalepy import RxComputeContext, RxInSqlServer, RxSqlServerData
from revoscalepy import rx_lin_mod, rx_predict, rx_summary
from revoscalepy import RxOptions, rx_import

import os

def test_linmod_sql():
    sql_server = os.getenv('PYTEST_SQL_SERVER', '.')
    
    sql_connection_string = 'Driver=SQL Server;Server=' + sqlServer + ';Database=sqlpy;Trusted_Connection=True;'
    print("connectionString={0!s}".format(sql_connection_string))

    data_source = RxSqlServerData(
        sql_query = "select top 10 * from airlinedemosmall",
        connection_string = sql_connection_string,

        column_info = {
            "ArrDelay" : { "type" : "integer" },
            "DayOfWeek" : {
                "type" : "factor",
                "levels" : [ "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday" ]
            }
        })

    sql_compute_context = RxInSqlServer(
        connection_string = sql_connection_string,
        num_tasks = 4,
        auto_cleanup = False
        )

    #
    # Run linmod locally
    #
    linmod_local = rx_lin_mod("ArrDelay ~ DayOfWeek", data = data_source)
    #
    # Run linmod remotely
    #
    linmod = rx_lin_mod("ArrDelay ~ DayOfWeek", data = data_source, compute_context = sql_compute_context)

    # Predict results
    # 
    predict = rx_predict(linmod, data = rx_import(input_data = data_source))
    summary = rx_summary("ArrDelay ~ DayOfWeek", data = data_source, compute_context = sql_compute_context)
```

### <a name="defining-a-data-source-vs-defining-a-compute-context"></a>Definizione di un'origine dati e la definizione di un contesto di calcolo

Un'origine dati è diversa da un contesto di calcolo. Il _origine dati_ definisce i dati utilizzati nel codice. Il _contesto di calcolo_ definisce in cui verrà eseguito il codice. Tuttavia, usano alcune delle stesse informazioni:

+ Variabili di Python, ad esempio `sql_query` e `sql_connection_string`, definire l'origine dei dati. 

    Passare tali variabili di [RxSqlServerData](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxsqlserverdata) costruttore per implementare il **oggetto origine dati** denominato `data_source`.

+ Si crea un **oggetto contesto di calcolo** utilizzando il [RxInSqlServer](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxinsqlserverdata) costruttore. Il valore risultante **oggetto contesto di calcolo** denominato `sql_cc`.

    In questo esempio riutilizza la stessa stringa di connessione utilizzata nell'origine dati, presupponendo che i dati sono nella stessa istanza di SQL Server che verrà utilizzato come contesto di calcolo. 
    
    Tuttavia, l'origine dati e il contesto di calcolo potrebbe essere in server diversi.
 
### <a name="changing-compute-contexts"></a>La modifica di contesti di calcolo

Dopo aver definito un contesto di calcolo, è necessario impostare il **contesto di calcolo attivo**. 

Per impostazione predefinita, la maggior parte delle operazioni vengono eseguite in locale, vale a dire che se non si specifica un contesto di calcolo diverso, verranno recuperati i dati dall'origine dati e il codice verrà eseguito nell'ambiente corrente di Python.

Esistono due modi per impostare il contesto di calcolo attivo:
+ Come argomento di una funzione o metodo
+ Tramite la chiamata `rx_set_computecontext`

#### <a name="set-compute-context-as-an-argument-of-a-method-or-function"></a>Impostare il contesto di calcolo come argomento di una funzione o metodo

In questo esempio, impostare il contesto di calcolo utilizzando un argomento della persona **rx** (funzione).
    
`linmod = rx_lin_mod_ex("ArrDelay ~ DayOfWeek", data = data, compute_context = sql_compute_context)`

In questo contesto di calcolo viene riutilizzato nella chiamata a [rxsummary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary):.

`summary = rx_summary("ArrDelay ~ DayOfWeek", data = data_source, compute_context = sql_compute_context)`

#### <a name="set-a-compute-context-explicitly-using-rxsetcomputecontext"></a>Impostare un contesto di calcolo in modo esplicito utilizzando rx_set_compute_context

La funzione [rx_set_compute_context](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-set-compute-context) che sono già stati definiti i contesti di calcolo consente di passare.

Dopo aver impostato contesto di calcolo attive, rimane attivo finché non si decida di modificarlo.

### <a name="using-parallel-processing-and-streaming"></a>Utilizzo di flusso e l'elaborazione parallela

Quando si definisce il contesto di calcolo, è anche possibile impostare i parametri che controllano la modalità di gestione dei dati in base al contesto di calcolo. Questi parametri sono diversi a seconda del tipo di origine dati.

Per i contesti di calcolo di SQL Server, è possibile impostare le dimensioni del batch o fornire suggerimenti sul grado di parallelismo da utilizzare nell'esecuzione di attività.

+ L'esempio è stato eseguito in un computer con quattro processori, pertanto la `num_tasks` parametro è impostato su 4 per consentire l'utilizzo massimo delle risorse. 
+ Se si imposta questo valore su 0, SQL Server utilizza il valore predefinito, ovvero eseguire tante attività in parallelo possibile, in base alle impostazioni MAXDOP corrente per il server. Tuttavia, il numero esatto di attività che può essere allocata dipende molti altri fattori, ad esempio le impostazioni del server e altri processi in esecuzione.

## <a name="related-samples"></a>Esempi correlati

Queste ulteriori esempi di Python ed esercitazioni illustrano scenari end-to-end utilizzando origini dati più complesse, nonché l'uso di contesti di calcolo remoto.

+ [Nel Database di Python per gli sviluppatori SQL](sqldev-in-database-python-for-sql-developers.md)
+ [Compilare un modello predittivo con Python e SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)
+ [Compilare un modello predittivo con Python e SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)
