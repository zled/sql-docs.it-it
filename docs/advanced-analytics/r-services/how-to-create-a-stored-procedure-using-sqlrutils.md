---
title: "Come creare una stored procedure con sqlrutils | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "R"
ms.assetid: 5ba99b49-481e-4b30-967a-a429b855b1bd
caps.latest.revision: 10
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 10
---
# Come creare una stored procedure con sqlrutils
Questo argomento descrive i passaggi per la conversione del codice R per l'esecuzione come stored procedure T-SQL. Per ottenere i migliori risultati possibili, può essere necessario modificare il codice per garantire che tutti gli input possano essere parametrizzati.

## <a name="step-1-format-your-r-script"></a>Passaggio 1. Formattare lo script R

1. Eseguire il wrapping di tutto il codice in una singola funzione.

   Tutte le variabili usate dalla funzione devono essere definite all'interno della funzione oppure devono essere definite come parametri di input. Vedere il [codice di esempio](#samples) in questo argomento.

## <a name="step-2-standardize-the-inputs-and-outputs"></a>Passaggio 2. Standardizzare i parametri di input e output

I parametri di input della funzione diventeranno parametri di input della stored procedure SQL e pertanto devono essere conformi ai requisiti del tipo seguente:
- Tra i parametri di input può esistere al massimo un frame di dati.
- Gli oggetti nel frame di dati e altri parametri di input della funzione devono essere dei tipi di dati R seguenti:
    - POSIXct
    - numeric
    - character
    - integer
    - logical
    - raw

- Se un tipo di input non è uno dei tipi elencati in precedenza, deve essere serializzato e passato alla funzione come *raw*. In questo caso, la funzione deve inoltre includere il codice per deserializzare l'input.

La funzione può restituire uno degli elementi seguenti:

- Un frame di dati contenente i tipi di dati supportati. Tutti gli oggetti nel frame di dati devono usare uno dei tipi di dati supportati.
- Un elenco denominato contenente al massimo un frame di dati. Tutti i membri dell'elenco devono usare uno dei tipi di dati supportati. 
- Un valore NULL, se la funzione non restituisce alcun risultato

## <a name="step-3-make-calls-to-the-sqlrutils-package-to-generate-the-stored-procedure"></a>Passaggio 3. Eseguire chiamate al pacchetto sqlrutils per generare la stored procedure

Dopo che il codice R è stato pulito e può essere chiamato come singola funzione, è possibile iniziare il processo d'uso delle funzioni in **sqlrutils** per convertire il codice di una stored procedure.

A seconda dei tipi di dati dei parametri, si useranno diverse funzioni per acquisire i dati e creare un oggetto parametro.

1. Se la funzione accetta parametri di input per ogni parametro, creare uno degli oggetti seguenti: 
    - Se il parametro di input è un frame di dati, usare `setInputData`.
    - Per tutti gli altri parametri di input, usare `setInputParameter`.

2. Se la funzione restituisce un elenco, creare un oggetto per gestire i dati desiderati dall'elenco nel modo seguente: 
    - Se la variabile nell'elenco è un frame di dati, usare `setOutputData`.
    - Per tutti gli altri membri dell'elenco, usare `setOutputParameter`.
    - Se la funzione restituisce un frame di dati direttamente, senza prima eseguirne il wrapping in un elenco, è possibile ignorare questo passaggio. 
    - Ignorare questo passaggio se la funzione restituisce NULL.

3. Quando tutti i parametri di input e output sono pronti, eseguire una chiamata al costruttore `StoredProcedure` per generare la stored procedure contenente la funzione R.
4. Per registrare immediatamente la stored procedure con il database, usare `registerStoredProcedure`.

## <a name="step-4-execute-the-stored-procedure"></a>Passaggio 4. Eseguire la stored procedure

1. Se si vuole eseguire la stored procedure dal codice R, piuttosto che da SQL Server, e la stored procedure richiede l'input, è necessario impostare i parametri di input prima che la funzione possa essere eseguita: 
    - Chiamare `getInputParameters` per ottenere un elenco di oggetti parametro di input.
    - Definire `$query` o impostare `$value` per ogni parametro di input. 

2. Usare `executeStoredProcedure` per eseguire la stored procedure dall'ambiente di sviluppo R, passando l'elenco di oggetti parametro di input impostato.

## <a name="a-name-samplesaexamples-prepare-your-code"></a><a name = "samples"></a>Esempi: preparare il codice 

In questo esempio, il codice R legge da un database, esegue alcune trasformazioni sui dati e li salva in un altro database. Questo semplice esempio viene usato solo per illustrare come è possibile riordinare il codice R per fornire un'interfaccia più semplice per la conversione della stored procedure.

**Prima della formattazione**


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
Si noti che quando si usa una connessione ODBC, anziché richiamare la funzione *RxSqlServerData* è necessario aprire la connessione usando *rxOpen* prima di poter eseguire le operazioni nel database.



**Dopo la formattazione**

Nella versione riformattata, la prima riga definisce il nome della funzione.

Il resto del codice dalla soluzione R originale diventa parte di tale funzione. 

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
Anche se non è necessario aprire la connessione ODBC in modo esplicito come parte del codice, è comunque necessaria una connessione ODBC per usare **sqlrutils**. 


## <a name="see-also"></a>Vedere anche

[Generating a Stored Procedure using sqlrutils](../../advanced-analytics/r-services/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md) (Generazione di una stored procedure con sqlrutils)

