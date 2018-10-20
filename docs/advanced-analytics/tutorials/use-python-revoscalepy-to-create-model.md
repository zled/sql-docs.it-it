---
title: Usare Python con revoscalepy per creare un modello | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 5c8ff387c3abda3f147700dce6349009a027a778
ms.sourcegitcommit: 3cd6068f3baf434a4a8074ba67223899e77a690b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2018
ms.locfileid: "49461957"
---
# <a name="use-python-with-revoscalepy-to-create-a-model"></a>Usare Python con revoscalepy per creare un modello
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questa lezione si informazioni su come eseguire il codice Python da un client di sviluppo remoto, creare un modello linear regression in SQL Server. 

## <a name="prerequisites"></a>Prerequisiti

+ In questa lezione Usa dati diversi rispetto alle lezioni precedenti. Non devi completare prima di tutto le lezioni precedenti. Tuttavia, se si hanno completato le lezioni precedenti e si dispone di un server già configurato per l'esecuzione di Python, usare tale server e il database come contesto di calcolo.
+ Per eseguire il codice Python con SQL Server come un calcolo contesto richiede SQL Server 2017 o versione successiva. Inoltre, è necessario installare in modo esplicito e quindi abilitare la funzionalità **servizi di Machine Learning**, scegliendo l'opzione di linguaggio Python.

    Se è installata una versione non definitiva di SQL Server 2017, è necessario aggiornare per almeno la versione RTM. Versioni future del servizio hanno continuato a espandere e migliorare la funzionalità di Python. Alcune funzionalità di questa esercitazione potrebbero non funzionare nelle prime versioni di versioni non definitive.

+ Questo esempio Usa un ambiente Python predefinito, denominato `PYTEST_SQL_SERVER`. L'ambiente è stato configurato per contenere **revoscalepy** e altre librerie necessarie. 

    Se non si dispone di un ambiente configurato per l'esecuzione di Python, è necessario farlo separatamente. Informazioni su come creare o modificare gli ambienti Python non è compreso nell'ambito di questa esercitazione. Per altre informazioni su come configurare un client di Python che contiene le librerie corrette, vedere [client Python per installare](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter) e [Python collegamento agli strumenti](https://docs.microsoft.com/machine-learning-server/python/quickstart-python-tools).

## <a name="remote-compute-contexts-and-revoscalepy"></a>Contesti di calcolo remoti e revoscalepy

Questo esempio viene illustrato il processo di creazione di un modello Python in un server remoto _contesto di calcolo_, che consente di lavorare da un client, ma scegliere un ambiente remoto, ad esempio SQL Server, Spark o Machine Learning Server, in cui il operazioni vengono effettivamente eseguite. Uso di contesti di calcolo rende più semplice scrivere codice una volta e distribuirlo in qualsiasi ambiente supportato.

Per eseguire il codice Python in SQL Server, è necessario il **revoscalepy** pacchetto. Si tratta di un pacchetto Python speciale fornito da Microsoft, simile al **RevoScaleR** pacchetto per il linguaggio R. Il **revoscalepy** pacchetto supporta la creazione di contesti di calcolo e fornisce l'infrastruttura per il trasferimento di dati e i modelli tra una workstation locale e un server remoto. Il **revoscalepy** funzione che supporta l'esecuzione di codice nel database viene [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxinsqlserver).

In questa lezione usare i dati in SQL Server per il training di un modello lineare basato su [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod), una funzione in **revoscalepy** che supporta la regressione su set di dati molto grandi. 

In questa lezione illustra anche le nozioni di base di come configurare e quindi usare una **contesto di calcolo di SQL Server** in Python. Per informazioni su come usare contesti di calcolo con altre piattaforme e che i contesti di calcolo supportati, vedere [contesto di calcolo per l'esecuzione di script in Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context)

## <a name="prepare-the-database-and-sample-data"></a>Preparare i dati e del database

1. In questa lezione viene utilizzato il database **sqlpy**. Se non è stata completata una delle lezioni precedenti, è possibile creare il database eseguendo il codice seguente:

    ```sql
    CREATE DATABASE sqlpy;
    GO
    USE sqlpy;
    GO
    ```

    > [!IMPORTANT]
    > Se si desidera utilizzare un database diverso, assicurarsi di modificare il codice di esempio e modificare il nome del database nella stringa di connessione.

2. Questo esempio Usa il set di dati relativi alle compagnie aeree, che è disponibile in R e Python. Dopo aver creato un database per gli esempi di Python, popolare una tabella con i dati come descritto qui: [campionare i dati in RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/sample-built-in-data).

3. Modificare il nome dell'ambiente per usare un ambiente disponibile nel client.

## <a name="run-the-sample-code"></a>Eseguire il codice di esempio

Dopo aver preparato i database e avere i dati per il training, archiviato in una tabella, aprire un ambiente di sviluppo Python ed eseguire l'esempio di codice.

Il codice esegue i passaggi seguenti:

1. Consente di importare le librerie necessarie e le funzioni.
2. Crea una connessione a SQL Server. Consente di creare **zdroj dat** oggetti per l'uso con i dati.
3. Modifica dei dati mediante **trasformazioni** in modo che può essere utilizzato dall'algoritmo di regressione logistica.
4. Le chiamate `rx_lin_mod` e definisce la formula utilizzata per adattarlo al modello.
5. Genera un set di stime basate sui dati originali.
6. Crea un riepilogo in base ai valori stimati.

Tutte le operazioni vengono eseguite utilizzando un'istanza di SQL Server come contesto di calcolo.

> [!NOTE]
> Per una dimostrazione di questo esempio in esecuzione dalla riga di comando, vedere questo video: [la Analitica avanzata di SQL Server 2017 con Python](https://www.youtube.com/watch?v=FcoY795jTcc)

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

Un'origine dati è diversa da un contesto di calcolo. Il _zdroj dat_ definisce i dati usati nel codice. Il _contesto di calcolo_ definisce in cui verrà eseguito il codice. Tuttavia, usano alcune delle stesse informazioni:

+ Le variabili di Python, ad esempio `sql_query` e `sql_connection_string`, definire l'origine dei dati. 

    Passare tali variabili per il [RxSqlServerData](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxsqlserverdata) costruttore per implementare le **oggetto origine dati** denominato `data_source`.

+ Si crea una **oggetto contesto di calcolo** tramite il [RxInSqlServer](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxinsqlserverdata) costruttore. L'oggetto risultante **oggetto contesto di calcolo** denominata `sql_cc`.

    Questo esempio Usa nuovamente la stessa stringa di connessione utilizzata nell'origine dati, in base al presupposto che i dati sono nella stessa istanza di SQL Server che verrà utilizzato come contesto di calcolo. 
    
    Tuttavia, l'origine dati e il contesto di calcolo potrebbe essere in server diversi.
 
### <a name="changing-compute-contexts"></a>La modifica di contesti di calcolo

Dopo aver definito un contesto di calcolo, è necessario impostare il **contesto di calcolo attivo**. 

Per impostazione predefinita, la maggior parte delle operazioni vengono eseguite in locale, vale a dire che se non si specifica un contesto di calcolo diverse, verranno recuperati i dati dall'origine dati e il codice verrà eseguito nell'ambiente Python corrente.

Esistono due modi per impostare il contesto di calcolo attivo:
+ Come argomento di un metodo o funzione
+ Tramite la chiamata `rx_set_computecontext`

#### <a name="set-compute-context-as-an-argument-of-a-method-or-function"></a>Impostare il contesto di calcolo come argomento di un metodo o funzione

In questo esempio, è impostato il contesto di calcolo usando un argomento dell'individuo **rx** (funzione).
    
`linmod = rx_lin_mod_ex("ArrDelay ~ DayOfWeek", data = data, compute_context = sql_compute_context)`

Questo contesto di calcolo viene riutilizzato nella chiamata a [rxsummary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary):.

`summary = rx_summary("ArrDelay ~ DayOfWeek", data = data_source, compute_context = sql_compute_context)`

#### <a name="set-a-compute-context-explicitly-using-rxsetcomputecontext"></a>Impostare un contesto di calcolo in modo esplicito usando rx_set_compute_context

La funzione [rx_set_compute_context](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-set-compute-context) consente di passare un contesto che è già stati definiti di calcolo.

Dopo aver impostato contesto di calcolo attive, rimane attivo fino alla successiva modifica.

### <a name="using-parallel-processing-and-streaming"></a>Tramite l'elaborazione parallela e streaming

Quando si definisce il contesto di calcolo, è anche possibile impostare i parametri che controllano la modalità di gestione dei dati per il contesto di calcolo. Questi parametri sono diversi a seconda del tipo di origine dati.

Per i contesti di calcolo di SQL Server, è possibile impostare le dimensioni del batch o fornire suggerimenti sul grado di parallelismo da utilizzare nell'esecuzione di attività.

+ L'esempio è stato eseguito in un computer con quattro processori, in modo che il `num_tasks` parametro è impostato su 4 per consentire l'utilizzo massimo delle risorse. 
+ Se si imposta questo valore su 0, SQL Server Usa l'impostazione predefinita, che consiste nell'eseguire qualsiasi numero di attività in parallelo possibili, in base alle impostazioni MAXDOP corrente per il server. Tuttavia, il numero esatto di attività che può essere allocata dipende molti altri fattori, ad esempio le impostazioni di server e altri processi in esecuzione.

## <a name="related-samples"></a>Esempi correlati

Questi esempi Python ed esercitazioni aggiuntive illustrano scenari end-to-end usando origini dati più complesse, nonché l'uso di contesti di calcolo remoti.

+ [Python nel Database per sviluppatori SQL](sqldev-in-database-python-for-sql-developers.md)
+ [Creare un modello predittivo usando Python e SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)
+ [Creare un modello predittivo usando Python e SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)
