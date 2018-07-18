---
title: Creare oggetti di dati di SQL Server utilizzando RxSqlServerData (SQL e R approfondimento) | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: e15c3e7c13c1be4f524c25bb1cec6da3c8e20c7e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="create-sql-server-data-objects-using-rxsqlserverdata-sql-and-r-deep-dive"></a>Creare oggetti di dati di SQL Server utilizzando RxSqlServerData (SQL e R approfondimento)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo fa parte dell'esercitazione approfondimento di analisi scientifica dei dati, su come usare [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) con SQL Server.

A questo punto è stato creato il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] del database e di disporre delle autorizzazioni necessarie per lavorare con i dati. In questo passaggio è creare alcuni oggetti R che consentono di lavorare con i dati.

## <a name="create-the-sql-server-data-objects"></a>Creare gli oggetti di dati di SQL Server

In questo passaggio è usare funzioni di **RevoScaleR** pacchetto per creare e popolare le due tabelle. Una tabella viene usata per il training dei modelli e l'altra per l'assegnazione dei punteggi. Entrambe le tabelle contengono dati sulle frodi con simulazione delle carte di credito.

Per creare tabelle in remoto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer, chiamare il **RxSqlServerData** (funzione).

> [!TIP]
> Se si usa Strumenti R per Visual Studio, selezionare **R Tools** (Strumenti R) dalla barra degli strumenti e fare clic su **Windows** per visualizzare le opzioni per il debug e la visualizzazione delle variabili R.

### <a name="create-the-training-data-table"></a>Creare la tabella di dati di training

1. Salvare la stringa di connessione di database in una variabile di R. Di seguito sono riportati due esempi di stringhe di connessione ODBC valide per SQL Server: uno con un account di accesso SQL e uno per l'autenticazione integrata di Windows.

    **Account di accesso SQL**
    ```R
    sqlConnString <- "Driver=SQL Server;Server=instance_name; Database=DeepDive;Uid=user_name;Pwd=password"
    ```

    **Autenticazione di Windows**
    ```R
    sqlConnString <- "Driver=SQL Server;Server=instance_name;Database=DeepDive;Trusted_Connection=True"
    ```

    Assicurarsi di modificare il nome dell'istanza, il nome del database, il nome utente e la password in modo appropriato.
  
2. Specificare il nome della tabella che si vuole creare e salvarlo in una variabile R.
  
    ```R
    sqlFraudTable <- "ccFraudSmall"
    ```
  
    Poiché l'istanza e il nome del database sono già specificati come parte della stringa di connessione, quando si combinano le due variabili, il nome *completo* della nuova tabella diventa _instance.database.schema.ccFraudSmall_.
  
3.  Prima di creare un'istanza dell'oggetto origine dati, aggiungere una riga specificando un parametro aggiuntivo, *rowsPerRead*.  Il parametro *rowsPerRead* controlla il numero di righe di dati lette in ogni blocco.
  
    ```R
    sqlRowsPerRead = 5000
    ```
  
    Sebbene sia facoltativo, questo parametro è importante per la gestione dell'utilizzo della memoria e l'ottimizzazione dei calcoli.  La maggior parte delle funzioni analitiche avanzate nel [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] elaborare i dati in blocchi e archiviare i risultati intermedi, restituendo i calcoli finali dopo che tutti i dati sono stati letti.
  
    Se il valore di questo parametro è troppo alto, l'accesso ai dati potrebbe risultare lento perché la memoria disponibile non è sufficiente a elaborare in modo efficiente un blocco troppo grande di dati.  In alcuni sistemi, se il valore di *rowsPerRead* è troppo piccolo, le prestazioni potrebbero risultare inferiori. Pertanto, è consigliabile provare utilizzare con questa impostazione nel sistema in uso quando si lavora con grandi set di dati.
  
    Questa procedura dettagliata, utilizzare le dimensioni del processo batch predefinito definita per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza per controllare il numero di righe in ogni blocco. Salvare tale valore nella variabile `sqlRowsPerRead`.
  
4.  Infine, definire una variabile per il nuovo oggetto origine dati e passare gli argomenti definiti in precedenza al costruttore RxSqlServerData. Si noti che l'oggetto viene creato ma non popolato.
  
    ```R
    sqlFraudDS <- RxSqlServerData(connectionString = sqlConnString,
       table = sqlFraudTable,
       rowsPerRead = sqlRowsPerRead)
    ```

#### <a name="to-create-the-scoring-data-table"></a>Per creare la tabella dei dati dei punteggi

Utilizzando la stessa procedura, creare la tabella che contiene i dati di punteggio usando lo stesso processo.

1. Creare una nuova variabile R, *sqlScoreTable*, per archiviare il nome della tabella usata per l'assegnazione dei punteggi.
  
    ```R
    sqlScoreTable <- "ccFraudScoreSmall"
    ```
  
2. Specificare la variabile come argomento alla funzione RxSqlServerData per definire un secondo oggetto di origine dati, *sqlScoreDS*.
  
    ```R
    sqlScoreDS \<- RxSqlServerData(connectionString = sqlConnString,
       table = sqlScoreTable, rowsPerRead = sqlRowsPerRead)
    ```

Poiché si sono già state definite come variabili nell'area di lavoro R la stringa di connessione e altri parametri, è facile creare nuove origini dati per diverse tabelle, viste o query.

> [!NOTE]
> La funzione utilizza argomenti diversi per la definizione di un'origine dati basata su un'intera tabella di per un'origine dati basata su una query. Questo avviene perché il motore di database di SQL Server è necessario preparare le query in modo diverso. Più avanti in questa esercitazione imparare a creare un oggetto origine dati basato su una query SQL.

## <a name="load-data-into-sql-tables-using-r"></a>Caricare i dati in tabelle SQL con R

Ora che sono state create le tabelle di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , è possibile caricare dati nelle tabelle usando la funzione **Rx** appropriata.

Il **RevoScaleR** pacchetto contiene funzioni che supportano molte origini dati diverse: per i dati di testo, utilizzare [RxTextData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxtextdata) per generare l'oggetto origine dati. Sono disponibili funzioni aggiuntive per la creazione di oggetti origine dati da dati Hadoop, dati ODBC e così via.

> [!NOTE]
> Per questa sezione, è necessario disporre **Esegui DDL** autorizzazioni sul database.

### <a name="load-data-into-the-training-table"></a>Caricare dati nella tabella di training

1. Creare una variabile di R, *ccFraudCsv*e assegnare alla variabile il percorso del file per il file CSV contenente i dati di esempio.
  
    ```R
    ccFraudCsv <- file.path(rxGetOption("sampleDataDir"), "ccFraudSmall.csv")
    ```
  
    Si noti la chiamata a **rxGetOption**, il metodo GET associato [rxOptions](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxoptions) in **RevoScaleR**. Utilizzare questa utilità per impostare ed elencate le opzioni relative a contesti di calcolo locali e remoti, ad esempio la directory condivisa predefinita o il numero di processori (Core) da utilizzare nei calcoli.
    
    Questo particolare chiamata ottiene gli esempi della libreria di corretto, indipendentemente dal quale viene eseguito il codice. Ad esempio, provare a eseguire la funzione in SQL Server e nel computer di sviluppo e osservare i percorsi diversi.
  
2. Definire una variabile per archiviare i nuovi dati e usare la funzione **RxTextData** per specificare l'origine dati di testo.
  
    ```R
    inTextData <- RxTextData(file = ccFraudCsv,      colClasses = c(
        "custID" = "integer", "gender" = "integer", "state" = "integer",
        "cardholder" = "integer", "balance" = "integer",
        "numTrans" = "integer",
        "numIntlTrans" = "integer", "creditLine" = "integer",
        "fraudRisk" = "integer"))
    ```
  
    L'argomento *colClasses* è importante. Usarlo per indicare il tipo di dati da assegnare a ogni colonna di dati caricati dal file di testo. In questo esempio, tutte le colonne vengono gestite come testo, tranne le colonne denominate, che vengono gestite come valori interi.
  
3. A questo punto, si consiglia di sospendere qualche minuto e visualizzare il database in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  Aggiornare l'elenco delle tabelle del database.
  
    È possibile vedere che, anche se gli oggetti di dati R sono stati creati nell'area di lavoro locale, le tabelle non create nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database. Inoltre, nessun dato è stato caricato dal file di testo nella variabile R.
  
4. Chiamare ora la funzione [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) per inserire i dati nella tabella [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
  
    ```R
    rxDataStep(inData = inTextData, outFile = sqlFraudDS, overwrite = TRUE)
    ```
  
    Supponendo che non si verifichino problemi con la stringa di connessione, dopo una breve pausa, verranno visualizzati risultati simili ai seguenti:
  
      *Totale righe scritte: 10000, Tempo totale: 0.466*

      *Righe lette: 10000, Totale Righe elaborate: 10000, Totale tempo blocco: 0.577 secondi*
  
5. Aggiornare con [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]l'elenco delle tabelle. Per verificare che ogni variabile include i tipi di dati corretto e sia stata importata correttamente, è anche possibile fare doppio clic nella tabella in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] e selezionare **seleziona le prime 1000 righe**.

### <a name="load-data-into-the-scoring-table"></a>Caricare dati nella tabella di assegnazione dei punteggi

1. Ripetere i passaggi per caricare il set di dati utilizzato per l'assegnazione dei punteggi nel database.
  
    Iniziare indicando il percorso del file di origine.
  
    ```R
    ccScoreCsv <- file.path(rxGetOption("sampleDataDir"), "ccFraudScoreSmall.csv")
    ```
  
2. Usare la funzione **RxTextData** per ottenere i dati e salvarli nella variabile *inTextData*.
  
    ```R
    inTextData <- RxTextData(file = ccScoreCsv,      colClasses = c(
        "custID" = "integer", "gender" = "integer", "state" = "integer",
        "cardholder" = "integer", "balance" = "integer",
        "numTrans" = "integer",
        "numIntlTrans" = "integer", "creditLine" = "integer"))
    ```
  
3.  Chiamare la funzione **rxDataStep** per sovrascrivere la tabella corrente con il nuovo schema e i nuovi dati.
  
    ```R
    rxDataStep(inData = inTextData, sqlScoreDS, overwrite = TRUE)
    ```
  
    - L'argomento *inData* definisce l'origine dati da usare.
  
    - L'argomento *outFile* specifica la tabella di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in cui verranno salvati i dati.
  
    - Se la tabella esiste già e non si utilizza il *sovrascrivere* opzione risultati vengono inseriti senza troncamenti.
  
Anche in questo caso, se la connessione ha avuto esito positivo, verrà visualizzato un messaggio che indica il completamento e il tempo necessario per scrivere i dati nella tabella:

*Totale righe scritte: 10000, Tempo totale: 0.384*

*Righe lette: 10000, Totale Righe elaborate: 10000, Totale tempo blocco: 0.456 secondi*

## <a name="more-about-rxdatastep"></a>Altre informazioni su rxDataStep

[rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) è un potente strumento che può eseguire più trasformazioni su un frame di dati R. È inoltre possibile utilizzare rxDataStep per convertire la rappresentazione richiesta dalla destinazione di dati: in questo caso, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

Facoltativamente, è possibile specificare trasformazioni dei dati, utilizzando le funzioni R negli argomenti di **rxDataStep**. Più avanti in questa esercitazione vengono forniti esempi di queste operazioni.

## <a name="next-step"></a>Passaggio successivo

[Eseguire query e modificare i dati SQL Server](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)

## <a name="previous-step"></a>Passaggio precedente

[Utilizzo dei dati di SQL Server mediante R](../../advanced-analytics/tutorials/deepdive-work-with-sql-server-data-using-r.md)
