---
title: Creare oggetti dati di SQL Server usando RxSqlServerData | Microsoft Docs
ms.custom: 
ms.date: 05/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: bcf5f7ff-795b-4815-b163-bcddd496efce
caps.latest.revision: "18"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 7eecfb2ce8a6cfe525b07aa8c6636c7dd77b0d30
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="create-sql-server-data-objects-using-rxsqlserverdata"></a>Creare oggetti dati di SQL Server usando RxSqlServerData

Ora che è stato creato il database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e si hanno le autorizzazioni necessarie per lavorare con i dati, è possibile creare oggetti in R che consentono di lavorare con i dati, sia nel server che nella workstation.

## <a name="create-the-sql-server-data-objects"></a>Creare gli oggetti dati di SQL Server

In questo passaggio, verrà usato R per creare e popolare due tabelle. Entrambe le tabelle contengono dati sulle frodi con simulazione delle carte di credito. Una tabella viene usata per il training dei modelli e l'altra per l'assegnazione dei punteggi.

Per creare tabelle nel computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] remoto si userà la funzione **RxSqlServerData** inclusa nel pacchetto **RevoScaleR** .

> [!TIP]
> Se si usa Strumenti R per Visual Studio, selezionare **R Tools** (Strumenti R) dalla barra degli strumenti e fare clic su **Windows** per visualizzare le opzioni per il debug e la visualizzazione delle variabili R.

### <a name="create-the-training-data-table"></a>Creare la tabella di dati di training

1. Inserire la stringa di connessione del database in una variabile R. Di seguito sono riportati due esempi di stringhe di connessione ODBC per SQL Server valide: una per un account di accesso SQL e una per l'autenticazione integrata di Windows (consigliata).

    **Uso di un account di accesso SQL**
    ```R
    sqlConnString <- "Driver=SQL Server;Server=instance_name; Database=DeepDive;Uid=user_name;Pwd=password"
    ```

    **Uso dell'autenticazione di Windows**
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
  
    Sebbene sia facoltativo, questo parametro è importante per la gestione dell'utilizzo della memoria e l'ottimizzazione dei calcoli.  La maggior parte delle funzioni analitiche avanzate in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] elabora i dati in blocchi e raggruppa risultati intermedi, restituendo i calcoli finali dopo che tutti i dati sono stati letti.
  
    Se il valore di questo parametro è troppo alto, l'accesso ai dati potrebbe risultare lento perché la memoria disponibile non è sufficiente a elaborare in modo efficiente un blocco troppo grande di dati.  In alcuni sistemi, se il valore di *rowsPerRead* è troppo piccolo, le prestazioni potrebbero risultare inferiori.
  
    Per questa procedura dettagliata, si userà la dimensione del processo batch definita dall'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per controllare il numero di righe in ogni blocco e il valore verrà salvato nella variabile *sqlRowsPerRead*.  Si consiglia di provare questa impostazione nel sistema quando si lavora con set di dati di grandi dimensioni.
  
4.  Infine, definire una variabile per il nuovo oggetto origine dati e passare gli argomenti definiti in precedenza al costruttore RxSqlServerData. Si noti che l'oggetto viene creato ma non popolato.
  
    ```R
    sqlFraudDS <- RxSqlServerData(connectionString = sqlConnString,
       table = sqlFraudTable,
       rowsPerRead = sqlRowsPerRead)
    ```

#### <a name="to-create-the-scoring-data-table"></a>Per creare la tabella dei dati dei punteggi

La tabella che contiene i dati dei punteggi verrà creata usando lo stesso processo.

1. Creare una nuova variabile R, *sqlScoreTable*, per archiviare il nome della tabella usata per l'assegnazione dei punteggi.
  
    ```R
    sqlScoreTable <- "ccFraudScoreSmall"
    ```
  
2. Specificare la variabile come argomento alla funzione RxSqlServerData per definire un secondo oggetto di origine dati, *sqlScoreDS*.
  
    ```R
    sqlScoreDS \<- RxSqlServerData(connectionString = sqlConnString,
       table = sqlScoreTable, rowsPerRead = sqlRowsPerRead)
    ```

Poiché la stringa di connessione e altri parametri sono già stati definiti come variabili nell'area di lavoro di R, è facile creare nuove origini dati per diverse tabelle, viste o query; è sufficiente specificare un nome di tabella diverso.

Più avanti in questa esercitazione si apprenderà come creare un oggetto origine dati basato su una query SQL.

## <a name="load-data-into-sql-tables-using-r"></a>Caricare i dati in tabelle SQL con R

Ora che sono state create le tabelle di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , è possibile caricare dati nelle tabelle usando la funzione **Rx** appropriata.

Il **RevoScaleR** pacchetto contiene funzioni che supportano molte origini dati diverse: per i dati di testo, si userà RxTextData per generare l'oggetto origine dati. Sono disponibili funzioni aggiuntive per la creazione di oggetti origine dati da dati Hadoop, dati ODBC e così via.

> [!NOTE]
> Per questa sezione, è necessario avere le autorizzazioni Esegui DDL per il database.

### <a name="load-data-into-the-training-table"></a>Caricare dati nella tabella di training

1. Creare una variabile di R, *ccFraudCsv*e assegnare alla variabile il percorso del file per il file CSV contenente i dati di esempio.
  
    ```R
    ccFraudCsv <- file.path(rxGetOption("sampleDataDir"), "ccFraudSmall.csv")
    ```
  
    Si noti la funzione di utilità **rxGetOption**. Questa funzione è inclusa nel pacchetto **RevoScaleR** per consentire l'impostazione e la gestione delle opzioni relative a contesti di calcolo locali e remoti, ad esempio la directory condivisa predefinita, il numero di processori (core) da usare nei calcoli e così via.  Questa chiamata è utile perché gli esempi di recupera dalla libreria indipendentemente dal quale viene eseguito il codice corretta. Ad esempio, provare a eseguire la funzione in SQL Server e nel computer di sviluppo e osservare i percorsi diversi.
  
2. Definire una variabile per archiviare i nuovi dati e utilizzare la funzione RxTextData per specificare l'origine dati di testo.
  
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
  
    Si noterà che anche se gli oggetti di dati R sono stati creati nell'area di lavoro locale, le tabelle non sono ancora state create nel database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Inoltre, nessun dato è stato caricato dal file di testo nella variabile R.
  
4. Chiamare ora la funzione **rxDataStep** per inserire i dati nella tabella [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
  
    ```R
    rxDataStep(inData = inTextData, outFile = sqlFraudDS, overwrite = TRUE)
    ```
  
    Supponendo che non si verifichino problemi con la stringa di connessione, dopo una breve pausa, verranno visualizzati risultati simili ai seguenti:
  
      *Totale righe scritte: 10000, Tempo totale: 0.466*

      *Righe lette: 10000, Totale Righe elaborate: 10000, Totale tempo blocco: 0.577 secondi*
  
5. Aggiornare con [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]l'elenco delle tabelle. Per verificare che ogni variabile include i tipi di dati corretto e sia stata importata correttamente, è anche possibile fare doppio clic nella tabella in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] e selezionare **seleziona le prime 1000 righe**.

### <a name="load-data-into-the-scoring-table"></a>Caricare dati nella tabella di assegnazione dei punteggi

1. Verrà seguita la stessa procedura per caricare il set di dati usato per l'assegnazione dei punteggi nel database.
  
    Iniziare indicando il percorso del file di origine.
  
    ```R
    ccScoreCsv <- file.path(rxGetOption("sampleDataDir"), "ccFraudScoreSmall.csv")
    ```
  
2. Utilizzare la funzione RxTextData per ottenere i dati e salvarlo nella variabile *inTextData*.
  
    ```R
    inTextData <- RxTextData(file = ccScoreCsv,      colClasses = c(
        "custID" = "integer", "gender" = "integer", "state" = "integer",
        "cardholder" = "integer", "balance" = "integer",
        "numTrans" = "integer",
        "numIntlTrans" = "integer", "creditLine" = "integer"))
    ```
  
3.  Chiamare la funzione rxDataStep per sovrascrivere la tabella corrente con il nuovo schema e dati.
  
    ```R
    rxDataStep(inData = inTextData, sqlScoreDS, overwrite = TRUE)
    ```
  
    - L'argomento *inData* definisce l'origine dati da usare.
  
    - L'argomento *outFile* specifica la tabella di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in cui verranno salvati i dati.
  
    - Se la tabella esiste già e non si usa l'opzione *overwrite* , i risultati verranno inseriti senza troncamenti.
  
Anche in questo caso, se la connessione ha avuto esito positivo, verrà visualizzato un messaggio che indica il completamento e il tempo necessario per scrivere i dati nella tabella:

*Totale righe scritte: 10000, Tempo totale: 0.384*

*Righe lette: 10000, Totale Righe elaborate: 10000, Totale tempo blocco: 0.456 secondi*

## <a name="more-about-rxdatastep"></a>Altre informazioni su rxDataStep

Il **rxDataStep** è un potente strumento che può eseguire più trasformazioni su un frame di dati R, per convertire i dati nella rappresentazione richiesta dalla destinazione. In questo caso la destinazione è [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

Inoltre, è possibile specificare trasformazioni dei dati, utilizzando funzioni R negli argomenti di rxDataStep. Si noterà che gli esempi di queste operazioni in un secondo momento.

## <a name="next-step"></a>Passaggio successivo

[Eseguire una query e modificare i dati SQL Server](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)

## <a name="previous-step"></a>Passaggio precedente

[Lavorare con i dati di SQL Server con R](../../advanced-analytics/tutorials/deepdive-work-with-sql-server-data-using-r.md)

