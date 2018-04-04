---
title: Come creare una stored procedure con sqlrutils | Microsoft Docs
ms.custom: ''
ms.date: 12/16/2016
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- R
ms.assetid: 5ba99b49-481e-4b30-967a-a429b855b1bd
caps.latest.revision: ''
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: fe1e05ee854fb6a094a66d88981d74287aa96beb
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2018
---
# <a name="create-a-stored-procedure-using-sqlrutils"></a>Creare una Stored Procedure utilizzando sqlrutils
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo articolo vengono descritti i passaggi per la conversione del codice R per l'esecuzione di una stored procedure T-SQL archiviate. Per ottenere i migliori risultati possibili, può essere necessario modificare il codice per garantire che tutti gli input possano essere parametrizzati.

## <a name="bkmk_rewrite"></a>Passaggio 1. Riscrivere lo Script R

Per ottenere risultati ottimali, è necessario riscrivere il codice R per incapsularlo come una singola funzione.

Tutte le variabili usate dalla funzione devono essere definite all'interno della funzione o devono essere definite come parametri di input. Vedere la [con codice di esempio](#samples) in questo articolo.

Inoltre, poiché i parametri di input per la funzione di R diventerà stored procedure di parametri di input dell'istruzione SQL, è necessario assicurarsi che l'input e output siano conformi ai requisiti del tipo seguente:

### <a name="inputs"></a>Input

Tra i parametri di input può esistere al massimo un frame di dati.

Gli oggetti nel frame di dati e altri parametri di input della funzione devono essere dei tipi di dati R seguenti:
- POSIXct
- numeric
- character
- integer
- logical
- raw

Se un tipo di input non è uno dei tipi elencati in precedenza, deve essere serializzato e passato alla funzione come *raw*. In questo caso, la funzione deve inoltre includere il codice per deserializzare l'input.

### <a name="outputs"></a>Output

La funzione può restituire uno degli elementi seguenti:

- Un frame di dati contenente i tipi di dati supportati. Tutti gli oggetti nel frame di dati devono usare uno dei tipi di dati supportati.
- Un elenco denominato contenente al massimo un frame di dati. Tutti i membri dell'elenco devono usare uno dei tipi di dati supportati.
- Un valore NULL, se la funzione non restituisce alcun risultato

## <a name="step-2-generate-required-objects"></a>Passaggio 2. Generare oggetti necessari

Dopo il codice R è stato pulito e può essere chiamato come una singola funzione, utilizzare le funzioni di **sqlrutils** pacchetto per preparare gli input e output in un formato che può essere passato al costruttore che crea il stored procedure.

**sqlrutils** sono disponibili funzioni che definiscono lo schema di dati di input e un tipo, nonché definiscono lo schema di dati di output e tipo. Include inoltre funzioni che è possono convertire il tipo di output richiesto oggetti R. È possibile rendere più chiamate di funzione per creare gli oggetti necessari, a seconda dei tipi di dati che utilizza il codice.

### <a name="inputs"></a>Input

Se la funzione accetta l'input, per ogni input, chiamare le funzioni seguenti:

- `setInputData` Se l'input è un frame di dati
- `setInputParameter` per tutti gli altri tipi di input

Quando si esegue ogni funzione chiamata, viene creato un oggetto di R in un secondo momento si passerà come argomento di `StoredProcedure`, per creare la stored procedure completa.

### <a name="outputs"></a>Output

**sqlrutils** fornisce più funzioni di conversione R oggetti quali elenchi di a data.frame richiesti da SQL Server.
Se la funzione restituisce un frame di dati direttamente, senza prima eseguirne il wrapping in un elenco, è possibile ignorare questo passaggio.
È anche possibile ignorare la conversione in questo passaggio se la funzione restituisce NULL.

Quando la conversione di un elenco o per ottenere un determinato elemento da un elenco, scegliere tra queste funzioni:

- `setOutputData` Se la variabile per ottenere l'elenco è un frame di dati
- `setOutputParameter` per tutti gli altri membri dell'elenco

Quando si esegue ogni funzione chiamata, viene creato un oggetto di R in un secondo momento si passerà come argomento di `StoredProcedure`, per creare la stored procedure completa.

## <a name="step-3-generate-the-stored-procedure"></a>Passaggio 3. Generare la Stored Procedure

Quando tutti i parametri di input e outpui sono pronti, effettuare una chiamata al `StoredProcedure` costruttore.

**Utilizzo**

`StoredProcedure (func, spName, ..., filePath = NULL ,dbName = NULL, connectionString = NULL, batchSeparator = "GO")`

Per illustrare questo concetto, si supponga di voler creare una stored procedure denominata **sp_rsample** con i seguenti parametri:

- Utilizza una funzione esistente **foosql**. La funzione è stata basata sul codice esistente nella funzione R **foo**, ma è stato riscritto la funzione in modo conforme ai requisiti come descritto in [in questa sezione](#bkmk_rewrite)e la funzione aggiornata come denominato  **foosql**.
- Usa il frame di dati **queryinput** come input
- Genera come output un frame di dati con il nome di variabile R **sqloutput**
- Per creare il codice T-SQL come file in cui si desidera il `C:\Temp` cartella, in modo che sia possibile eseguire utilizzando SQL Server Management Studio in un secondo momento

```R
StoredProcedure (foosql, sp_rsample, queryinput, sqloutput, filePath = "C:\\Temp")
```

> [!NOTE]
> Poiché si sta creando il file nel file System, è possibile omettere gli argomenti che definiscono la connessione al database.

L'output della funzione è una T-stored procedure SQL che può essere eseguita in un'istanza di SQL Server 2016 (richiede R Services) o SQL Server 2017 (richiede servizi di Machine Learning con R). 

Per ulteriori esempi, vedere la Guida di pacchetto, chiamando `help(StoredProcedure)` da un ambiente di R.

## <a name="step-4-register-and-run-the-stored-procedure"></a>Passaggio 4. Registrare ed eseguire la Stored Procedure

Esistono due modi, che è possibile eseguire la stored procedure:

- Utilizzando T-SQL, da qualsiasi client che supporta le connessioni all'istanza di SQL Server 2016 o 2017 di SQL Server
- Da un ambiente di R

Entrambi i metodi richiedono che sia stata registrata la stored procedure nel database in cui si intende utilizzare la stored procedure.

### <a name="register-the-stored-procedure"></a>Registrare la stored procedure

È possibile registrare la stored procedure con R oppure è possibile eseguire l'istruzione CREATE PROCEDURE in T-SQL.

- Utilizzo di T-SQL.  Se si preferiscono con T-SQL, aprire SQl Server Management Studio (o qualsiasi altro client che è possibile eseguire comandi SQL DDL) ed eseguire l'istruzione CREATE PROCEDURE utilizzando il codice preparato la `StoredProcedure` (funzione).
- Con R. Mentre si è ancora R nell'ambiente in uso, è possibile utilizzare il `registerStoredProcedure` funzionare in **sqlrutils** per registrare la stored procedure con il database.

  Ad esempio, è possibile registrare la stored procedure **sp_rsample** nell'istanza di database definiti in *sqlConnStr*, eseguendo questa chiamata R:

  ```R
  registerStoredProcedure(sp_rsample, sqlConnStr)
  ```


> [!IMPORTANT]
> Sia che si utilizzi R o SQL, è necessario eseguire l'istruzione utilizzando un account che dispone delle autorizzazioni per creare nuovi oggetti di database.

### <a name="run-using-sql"></a>Eseguire l'utilizzo di SQL

Dopo aver creata la stored procedure, aprire una connessione al database SQL utilizzando qualsiasi client che supporta T-SQL e passare i valori per i parametri richiesti dalla stored procedure.

### <a name="run-using-r"></a>Eseguire l'uso di R

Alcune attività di preparazione aggiuntivi è necessaria se si desidera eseguire la stored procedure dal codice R, anziché da SQL Server. Ad esempio, se la stored procedure richiede valori di input, è necessario impostare i parametri di input prima che la funzione può essere eseguita e quindi passa tali oggetti per la stored procedure nel codice R.

Il processo generale di chiamata di preparata stored procedure SQL è il seguente:

1. Chiamare `getInputParameters` per ottenere un elenco di oggetti parametro di input.
2. Definire `$query` o impostare `$value` per ogni parametro di input.
3. Usare `executeStoredProcedure` per eseguire la stored procedure dall'ambiente di sviluppo R, passando l'elenco di oggetti parametro di input impostato.

## <a name = "samples"></a>Esempio

Questo esempio mostra la prima e dopo le versioni di uno script R che ottiene dati da un database di SQL Server, esegue alcune trasformazioni dei dati di e viene salvato in un database diverso.

Questo semplice esempio viene utilizzato solo per illustrare come è possibile riorganizzare codice R per rendere più semplice convertire una stored procedure.

### <a name="before-code-preparation"></a>Prima della preparazione di codice


```R
sqlConnFrom <- "Driver={ODBC Driver 13 for SQL Server};Server=MyServer01;Database=AirlineSrc;Trusted_Connection=Yes;"
  
sqlConnTo <- "Driver={ODBC Driver 13 for SQL Server};Server=MyServer01;Database=AirlineTest;Trusted_Connection=Yes;"
  
sqlQueryAirline <- "SELECT TOP 10000 ArrDelay, CRSDepTime, DayOfWeek FROM [AirlineDemoSmall]"
  
dsSqlFrom <- RxSqlServerData(sqlQuery = sqlQueryAirline, connectionString = sqlConnFrom)
  
dsSqlTo <- RxSqlServerData(table = "cleanData", connectionString = sqlConnTo)
  
xFunc <- function(data) {
    data$CRSDepHour <- as.integer(trunc(data$CRSDepTime))
    return(data)
    }
  
xVars <- c("CRSDepTime")
  
sqlCompute <- RxInSqlServer(numTasks = 4, connectionString = sqlConnTo)
  
rxOpen(dsSqlFrom)
rxOpen(dsSqlTo)
  
if (rxSqlServerTableExists("cleanData", connectionString = sqlConnTo))   {
    rxSqlServerDropTable("cleanData")}
  
rxDataStep(inData = dsSqlFrom, 
     outFile = dsSqlTo,
     transformFunc = xFunc,
     transformVars = xVars,
     overwrite = TRUE)
```

> [!NOTE]
> 
> Quando si utilizza una connessione ODBC invece di richiamare il *RxSqlServerData* funzione, è necessario aprire la connessione mediante *rxOpen* prima di eseguire le operazioni nel database.


### <a name="after-code-preparation"></a>Dopo la preparazione di codice

Nella versione aggiornata, la prima riga definisce il nome della funzione. Tutto l'altro codice dalla soluzione R originale diventa una parte di tale funzione.

```R
myetl1function <- function() { 
   sqlConnFrom <- "Driver={ODBC Driver 13 for SQL Server};Server=MyServer01;Database=Airline01;Trusted_Connection=Yes;"
   sqlConnTo <- "Driver={ODBC Driver 13 for SQL Server};Server=MyServer02;Database=Airline02;Trusted_Connection=Yes;"
    
   sqlQueryAirline <- "SELECT TOP 10000 ArrDelay, CRSDepTime, DayOfWeek FROM [AirlineDemoSmall]"

   dsSqlFrom <- RxSqlServerData(sqlQuery = sqlQueryAirline, connectionString = sqlConnFrom)
  
   dsSqlTo <- RxSqlServerData(table = "cleanData", connectionString = sqlConnTo)
  
   xFunc <- function(data) {
     data$CRSDepHour <- as.integer(trunc(data$CRSDepTime))
     return(data)}
  
   xVars <- c("CRSDepTime")
  
   sqlCompute <- RxInSqlServer(numTasks = 4, connectionString = sqlConnTo)
  
   if (rxSqlServerTableExists("cleanData", connectionString = sqlConnTo)) {rxSqlServerDropTable("cleanData")}
  
   rxDataStep(inData = dsSqlFrom, 
        outFile = dsSqlTo,
        transformFunc = xFunc,
        transformVars = xVars,
        overwrite = TRUE)
   return(NULL)
}
```

> [!NOTE]
> 
> Anche se non è necessario aprire la connessione ODBC in modo esplicito come parte del codice, è comunque necessaria una connessione ODBC per usare **sqlrutils**.

## <a name="see-also"></a>Vedere anche

[Generating a Stored Procedure using sqlrutils](../../advanced-analytics/r-services/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)


