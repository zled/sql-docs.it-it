---
title: Usare Python con revoscalepy per creare un modello | Documenti Microsoft
ms.custom: SQL2016_New_Updated
ms.date: 09/19/2017
mms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: tutorial
caps.latest.revision: "4"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.openlocfilehash: e4fb52ba8597b2499cc3ea094ae1c4b0c9421237
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="use-python-with-revoscalepy-to-create-a-model"></a>Usare Python con revoscalepy per creare un modello

Questo esempio viene illustrato come creare un modello di regressione lineare in SQL Server, usando un algoritmo dal **revoscalepy** pacchetto.

Il **revoscalepy** dal pacchetto per Python contiene oggetti, le trasformazioni, e gli algoritmi simili a quelli forniti per il **RevoScaleR** pacchetto per il linguaggio R. Con questa libreria, è possibile creare un contesto di calcolo, spostare dati tra i contesti di calcolo, la trasformazione dei dati ed eseguire il training di modelli predittivi utilizzando algoritmi comuni, ad esempio la regressione logistica e lineare, gli alberi delle decisioni e altro ancora.

Per ulteriori informazioni, vedere [novità revoscalepy?](../python/what-is-revoscalepy.md) e [riferimento alla funzione di Python](https://docs.microsoft.com/r-server/python-reference/introducing-python-package-reference)

## <a name="prerequisites"></a>Prerequisites

> [!IMPORTANT]
> Per eseguire codice Python in SQL Server, è necessario avere installato SQL Server 2017 CTP 2.0 o versione successiva e, è necessario installare e abilitare la funzionalità, **Machine Learning Services** con Python. Altre versioni di SQL Server non supportano l'integrazione di Python.

## <a name="run-the-sample-code"></a>Eseguire il codice di esempio

Questo codice vengono eseguite le seguenti operazioni:

1. Importa le librerie richieste e le funzioni
2. Crea una connessione a SQL Server e crea gli oggetti origine dati per l'utilizzo con i dati
3. È possibile modificare i dati in modo che può essere utilizzato dall'algoritmo di regressione logistica
4. Chiamate `rx_lin_mod` e definisce la formula utilizzata per adattare il modello
5. Genera un set di stime basate sul set di dati originale
6. Crea un riepilogo in base ai valori stimati

Tutte le operazioni vengono eseguite utilizzando un'istanza di SQL Server come contesto di calcolo.

In generale, il processo di chiamata Python in un contesto di calcolo remoto è simile al modo in cui che si usano R in un contesto di calcolo remoto. Eseguire l'esempio come script Python dalla riga di comando o tramite un ambiente di sviluppo Python che include i componenti di integrazione di Python forniti in questa versione. Nel codice, creare e utilizzare un oggetto di contesto di calcolo per indicare dove si desidera calcoli specifici da eseguire.

> [!NOTE]
> Assicurarsi di modificare i nomi di database e di ambiente come appropriato.
> 
> Per una dimostrazione di questo esempio in esecuzione dalla riga di comando, vedere il video: [SQL Server 2017 avanzate Analitica con Python](https://www.youtube.com/watch?v=FcoY795jTcc)


### <a name="sample-code"></a>Codice di esempio

```python
from revoscalepy import RxComputeContext, RxInSqlServer, RxSqlServerData
from revoscalepy import rx_lin_mod, rx_predict, rx_summary
from revoscalepy import RxOptions, rx_import

from pandas import Categorical
import os

def test_linmod_sql():
    sql_server = os.getenv('PYTEST_SQL_SERVER', '.')
    
    sql_connection_string = 'Driver=SQL Server;Server=' + sqlServer + ';Database=PyTestDb;Trusted_Connection=True;'
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

## <a name="discussion"></a>Discussione

Consente di esaminare il codice ed evidenziare alcuni passaggi chiave.

### <a name="defining-a-data-source-and-compute-context"></a>Definizione di un tipo di dati di origine e di contesto di calcolo

Un'origine dati è diversa da un contesto di calcolo. Il _origine dati_ definisce i dati utilizzati nel codice. Il _contesto di calcolo_ definisce in cui verrà eseguito il codice.

1. Creare le variabili di Python, ad esempio `sql_query` e `sql_connection_string`, che definiscono l'origine e i dati che si desidera utilizzare. Passare tali variabili di [RxSqlServerData](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxsqlserverdata) costruttore per implementare il **oggetto origine dati** denominato `data_source`.
2. Creare un oggetto di contesto di calcolo tramite il [RxInSqlServer](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxinsqlserverdata) costruttore. In questo esempio, passare la stringa di connessione che è definita in precedenza, presupponendo che i dati sono nella stessa istanza di SQL Server che verrà utilizzato come contesto di calcolo. Tuttavia, l'origine dati e il contesto di calcolo potrebbe essere in server diversi. Il valore risultante **oggetto contesto di calcolo** denominato `sql_cc`.
3. Scegliere il contesto di calcolo attivo. Per impostazione predefinita, le operazioni vengono eseguite in locale, vale a dire che se non si specifica un contesto di calcolo diverso, verranno recuperati i dati dall'origine dati e verrà eseguito l'adattamento del modello nell'ambiente corrente di Python.

### <a name="changing-compute-contexts"></a>La modifica di contesti di calcolo

In questo esempio, impostare il contesto di calcolo utilizzando un argomento della persona **rx** (funzione).
    
`linmod = rx_lin_mod_ex("ArrDelay ~ DayOfWeek", data = data, compute_context = sql_compute_context)`

Lo stesso vale nella chiamata a **rxsummary**, in cui viene riutilizzato il contesto di calcolo.

`summary = rx_summary("ArrDelay ~ DayOfWeek", data = data_source, compute_context = sql_compute_context)`

È inoltre possibile utilizzare la funzione [rx_set_computecontext](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rx-set-compute-context) per alternare i contesti di calcolo che sono già stati definiti.

### <a name="setting-the-degree-of-parallelism"></a>L'impostazione di grado di parallelismo

Quando si definisce il contesto di calcolo, è anche possibile impostare i parametri che controllano la modalità di gestione dei dati in base al contesto di calcolo. Questi parametri sono diversi a seconda del tipo di origine dati.

Per i contesti di calcolo di SQL Server, è possibile impostare le dimensioni del batch o fornire suggerimenti sul grado di parallelismo da utilizzare nell'esecuzione di attività.

L'esempio è stato eseguito in un computer con quattro processori, è necessario impostare il *num_tasks* parametro a 4. Se si imposta questo valore su 0, SQL Server utilizza il valore predefinito, ovvero eseguire tante attività in parallelo possibile, in base alle impostazioni MAXDOP corrente per il server. Tuttavia, anche nel server con molti processori, il numero esatto di attività che può essere allocata dipende molti altri fattori, ad esempio le impostazioni del server e altri processi in esecuzione.

## <a name="related-samples"></a>Esempi correlati

Vedere questi esempi di Python e le esercitazioni per suggerimenti avanzati e demo end-to-end.

+ [Nel Database di Python per gli sviluppatori SQL](sqldev-in-database-python-for-sql-developers.md)
+ [Compilare un modello predittivo con Python e SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)
+ [Distribuire e utilizzare i modelli di Python](../python/publish-consume-python-code.md)
