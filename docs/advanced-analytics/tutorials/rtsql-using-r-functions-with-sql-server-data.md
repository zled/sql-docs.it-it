---
title: Utilizzo di funzioni R con i dati di SQL Server (R nella Guida rapida SQL) | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 226712010118a54ac1c5350e128bf50cc261a128
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="using-r-functions-with-sql-server-data-r-in-sql-quickstart"></a>Utilizzo di funzioni R con i dati di SQL Server (R nella Guida rapida SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dopo aver acquisito familiarità con le operazioni di base, è possibile iniziare a scoprire tutti i vantaggi di R. Molte funzioni statistiche avanzate, ad esempio, possono essere complesse da implementare con T-SQL, mentre richiedono una sola riga di codice R.  Con R Services è facile incorporare script di utilità R in una stored procedure.

In questi esempi verranno incorporate funzioni matematiche e di utilità R in una stored procedure di SQL Server.

## <a name="create-a-stored-procedure-to-generate-random-numbers"></a>Creare una stored procedure per generare numeri casuali

Per semplicità, utilizziamo R `stats` pacchetto, di cui è installato e caricato per impostazione predefinita con R Services. Il pacchetto contiene centinaia di funzioni per le attività statistiche comuni, tra cui la funzione `rnorm`, che genera una quantità specificata di numeri casuali usando la distribuzione normale, in base a una deviazione e a una media standard.

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

È facile in combinazione con SQL Server: definire una stored procedure che ottiene gli argomenti da parte dell'utente. Passare quindi gli argomenti nello script R come variabili.

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

## <a name="related-resources"></a>Risorse correlate

+ Si desidera installare più pacchetti di R, per ottenere più funzioni statistiche avanzato? Vedere [installazione e la gestione dei pacchetti R](../r/installing-and-managing-r-packages.md).

+ Che consentono di convertire il codice R autonomo in un formato che può essere parametrizzato facilmente stored procedure SQL Server, il team Microsoft R ha fornito un nuovo pacchetto R, **sqlrutils**. Per ulteriori informazioni, vedere [come creare una stored procedure utilizzando sqlrutils](../r/how-to-create-a-stored-procedure-using-sqlrutils.md).

## <a name="use-r-utility-functions-for-troubleshooting"></a>Usare funzioni di utilità R per la risoluzione dei problemi

Per impostazione predefinita, un'installazione di R include il `utils` pacchetto, che offre un'ampia gamma di funzioni di utilità per esaminare l'ambiente R corrente. Questo può essere utile se si riscontrano discrepanze nel modo in cui il codice R viene eseguito in SQL Server e in ambienti esterni.

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

Molti utenti come utilizzare le funzioni di sistema temporizzazione in R, ad esempio `system.time` e `proc.time`, per acquisire il tempo utilizzato dai processi R e analizzare i problemi di prestazioni.

Per un esempio, vedere questa esercitazione: [Creare funzionalità di dati](../tutorials/walkthrough-create-data-features.md). In questa procedura dettagliata vengono incorporate funzioni di temporizzazione R nella soluzione per confrontare le prestazioni di due metodi per la creazione di funzionalità dai dati: funzioni R e funzioni T-SQL.

## <a name="next-lesson"></a>Lezione successiva

Il passaggio successivo consiste nella creazione di un modello predittivo tramite R in SQL Server.

[Creare un modello predittivo](../tutorials/rtsql-create-a-predictive-model-r.md)
