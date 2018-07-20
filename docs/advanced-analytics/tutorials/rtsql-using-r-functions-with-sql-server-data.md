---
title: Guida introduttiva che illustra R funziona con dati di SQL Server (SQL Server Machine Learning Services) | Microsoft Docs
description: In questa Guida introduttiva, informazioni su come scrivere una funzione R che usa i dati di SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/15/2018
ms.topic: quickstart
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 5785b8b8162fdde25dea13eb3aead55c10dbfc3b
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39086673"
---
# <a name="quickstart-using-r-functions-with-sql-server-data"></a>Guida introduttiva: Uso delle funzioni R con dati di SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Se sono completate le guide introduttive precedenti, si ha familiarità con le operazioni di base ed è pronto per un elemento più complesso, ad esempio funzioni statistiche. Funzioni statistiche avanzate che sono piuttosto complesse da implementare in T-SQL possono essere eseguite in R con una sola riga di codice.

In questa Guida introduttiva, verranno incorporate R matematica e stored procedure di funzioni di utilità SQL Server.

## <a name="prerequisites"></a>Prerequisiti

Una Guida introduttiva precedente [Hello World in R e SQL](rtsql-using-r-code-in-transact-sql-quickstart.md), vengono fornite informazioni e collegamenti per configurare l'ambiente R necessario per questa Guida introduttiva.

## <a name="create-a-stored-procedure-to-generate-random-numbers"></a>Creare una stored procedure per generare numeri casuali

Per semplicità, si userà R `stats` pacchetto, che viene installato e caricato per impostazione predefinita quando si installa il supporto di funzionalità di R in SQL Server. Il pacchetto contiene centinaia di funzioni per le attività statistiche comuni, tra cui la funzione `rnorm`, che genera una quantità specificata di numeri casuali usando la distribuzione normale, in base a una deviazione e a una media standard.

Ad esempio, questo codice R restituisce 100 numeri, in una media di 50, in base alla deviazione standard 3.

```R
as.data.frame(rnorm(100, mean = 50, sd = 3));
```

Per chiamare questa riga di codice R da T-SQL, eseguire sp_execute_external_script e aggiungere la funzione R nel parametro di script R, in questo modo:

```sql
EXEC sp_execute_external_script
      @language = N'R'
    , @script = N'
         OutputDataSet <- as.data.frame(rnorm(100, mean = 50, sd =3));'
    , @input_data_1 = N'   ;'
      WITH RESULT SETS (([Density] float NOT NULL));
```

Si vuole semplificare la generazione di un set diverso di numeri casuali?

La risposta è semplice quando combinato con SQL Server: definire una stored procedure che ottiene gli argomenti da parte dell'utente. Passare quindi gli argomenti nello script R come variabili.

```sql
CREATE PROCEDURE MyRNorm (@param1 int, @param2 int, @param3 int)
AS
    EXEC sp_execute_external_script
      @language = N'R'
    , @script = N'
         OutputDataSet <- as.data.frame(rnorm(mynumbers, mymean, mysd));'
    , @input_data_1 = N'   ;'
    , @params = N' @mynumbers int, @mymean int, @mysd int'
    , @mynumbers = @param1
    , @mymean = @param2
    , @mysd = @param3
    WITH RESULT SETS (([Density] float NOT NULL));
```

+ La prima riga definisce ognuno dei parametri di input SQL necessari quando viene eseguita la stored procedure.

+ La riga che inizia con `@params` definisce tutte le variabili usate dal codice R e i tipi di dati SQL corrispondenti.

+ Le righe immediatamente successive eseguono il mapping dei nomi dei parametri SQL ai nomi delle variabili R corrispondenti.

Dopo aver eseguito il wrapping della funzione R in una stored procedure, è possibile chiamare facilmente la funzione e passare valori diversi, in questo modo:

```sql
EXEC MyRNorm @param1 = 100,@param2 = 50, @param3 = 3
```

## <a name="use-r-utility-functions-for-troubleshooting"></a>Usare funzioni di utilità R per la risoluzione dei problemi

Per impostazione predefinita, un'installazione di R include la `utils` pacchetto, che offre un'ampia gamma di funzioni di utilità per esaminare l'ambiente R corrente. Questo può essere utile se si riscontrano discrepanze nel modo in cui il codice R viene eseguito in SQL Server e in ambienti esterni.

Ad esempio, è possibile usare la funzione R `memory.limit()` per ottenere memoria per l'ambiente R corrente. Poiché il pacchetto `utils` viene installato, ma non viene caricato per impostazione predefinita, prima di tutto è necessario usare la funzione `library()` per caricarlo.

```sql
EXECUTE sp_execute_external_script
      @language = N'R'
    , @script = N'
        library(utils);
        mymemory <- memory.limit();
        OutputDataSet <- as.data.frame(mymemory);'
    , @input_data_1 = N' ;'
WITH RESULT SETS (([Col1] int not null));
```

Numero di utenti come usare le funzioni di temporizzazione di sistema in R, ad esempio `system.time` e `proc.time`, per acquisire il tempo usato dai processi R e analizzare i problemi di prestazioni.

Per un esempio, vedere questa esercitazione: [Creare funzionalità di dati](../tutorials/walkthrough-create-data-features.md). In questa procedura dettagliata vengono incorporate funzioni di temporizzazione R nella soluzione per confrontare le prestazioni di due metodi per la creazione di funzionalità dai dati: funzioni R e funzioni T-SQL.

## <a name="next-steps"></a>Passaggi successivi

Il passaggio successivo consiste nella creazione di un modello predittivo tramite R in SQL Server.

> [!div class="nextstepaction"]
> [Guida introduttiva: Creare un modello predittivo](rtsql-create-a-predictive-model-r.md)
