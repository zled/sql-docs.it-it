---
title: Eseguire Python con T-SQL | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: db959c9d8802ad3d3d2f7e8bdb64e194130dfeba
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="run-python-using-t-sql"></a>Eseguire Python con T-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questa esercitazione viene illustrato come eseguire codice Python in SQL Server 2017. Viene illustrato il processo di spostamento dei dati tra SQL Server e Python e viene spiegato come eseguire il wrapping di codice Python corretto in una stored procedure [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) per compilare, eseguire il training e utilizzare modelli di machine learning in SQL Server.

## <a name="prerequisites"></a>Prerequisiti

Per completare questa esercitazione, è necessario installare SQL Server 2017 e abilitare Servizi di Machine Learning nell'istanza, come descritto in [installare SQL Server 2017 Machine Learning Services (In-Database)](../install/sql-machine-learning-services-windows-install.md). 

È inoltre necessario installare [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms). In alternativa, è possibile utilizzare un altro database Gestione strumento o di query, a condizione che può connettersi a un server e database ed eseguire una query T-SQL o stored procedure.

Dopo aver completato l'installazione, tornare a questa esercitazione, per informazioni su come eseguire il codice Python nel contesto di una stored procedure. 

## <a name="overview"></a>Panoramica

In questa esercitazione include quattro lezioni:

+ Le nozioni di base di spostamento dei dati tra SQL Server e Python: ulteriori requisiti di base, strutture di dati, input e output.
+ Provare a utilizzare le stored procedure per eseguire semplici operazioni di Python, ad esempio il caricamento dei dati di esempio.
+ Utilizzare le stored procedure per creare un modello di apprendimento Python e generare punteggi dal modello.
+ Una lezione facoltativa per gli utenti che intendono eseguire Python da un client remoto, l'utilizzo di SQL Server come il _contesto di calcolo_. Include il codice per la creazione di un modello. Tuttavia, richiede che sono già una certa familiarità con gli ambienti Python e gli strumenti Python.

In questo caso, vengono forniti esempi di Python aggiuntivi specifici di SQL Server 2017: [esercitazioni di SQL Server Python](../tutorials/sql-server-python-tutorials.md)

## <a name="verify-that-python-is-enabled-and-the-launchpad-is-running"></a>Verificare che Python è abilitato e la finestra di avvio è in esecuzione

1. In Management Studio, eseguire questa istruzione per assicurarsi che il servizio è stato abilitato.

    ```sql
    sp_configure 'external scripts enabled'
    ```

    Se **run_value** è 1, la funzione di machine learning è installato e pronto all'uso.

    Una causa comune di errori è che la finestra di avvio, che gestisce la comunicazione tra SQL Server e Python, è stato arrestato. È possibile visualizzare lo stato della finestra di avvio con Windows **servizi** pannello oppure aprendo Gestione configurazione SQL Server. Se il servizio è arrestato, riavviarlo.

2. Successivamente, verificare che il runtime di Python utilizzo e la comunicazione con SQL Server. A tale scopo, aprire una nuova **Query** finestra in SQL Server Management Studio e connettersi all'istanza in cui è stato installato Python.

    ```sql
    EXEC sp_execute_external_script @language = N'Python', 
    @script = N'print(3+4)'
    ```

    Se tutto funziona correttamente, si verrà visualizzato un messaggio di risultato simile a questo

    ```text
    STDOUT message(s) from external script: 
    7
    ```

3. Se si verificano errori, sono disponibili un'ampia gamma di operazioni da eseguire per verificare che il server e Python possa comunicare. 

    È necessario aggiungere il gruppo di utenti Windows `SQLRUserGroup` come account di accesso nell'istanza, per garantire che Launchpad consente la comunicazione tra SQL Server e Python. (Viene utilizzato il gruppo stesso per entrambi R ed esecuzione di codice Python). Per ulteriori informazioni, vedere [autenticazione implicita abilitato](../r/add-sqlrusergroup-to-database.md).
    
    Inoltre, si potrebbe essere necessario abilitare i protocolli di rete che sono stati disabilitati o aprire il firewall in modo che SQL Server può comunicare con client esterni. Per ulteriori informazioni, vedere [risoluzione dei problemi di installazione](../common-issues-external-script-execution.md).

## <a name="basic-python-interaction"></a>Interazione di base Python

Esistono due modi per eseguire il codice Python in SQL Server:

+ Aggiungere uno script Python come un argomento della stored procedure di sistema, **sp_execute_external_script**
+ Da un client remoto di Python, connettersi a SQL Server ed eseguire codice utilizzando SQL Server come contesto di calcolo. Questa operazione richiede [revoscalepy](../python/what-is-revoscalepy.md).

L'obiettivo principale di questa esercitazione è per garantire che è possibile utilizzare Python in una stored procedure.

1. Esecuzione di codice semplice per vedere come i dati vengono passati avanti e indietro tra SQL Server e Python.

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    a = 1
    b = 2
    c = a/b
    d = a*b
    print(c, d)
    '
    ```

2. Presupponendo che si dispone di tutto è configurato correttamente e Python e SQL Server sono in comunicazione, viene calcolato il risultato corretto, la versione di Python e `print` funzione restituisce il risultato per il **messaggi** windows.

    **Risultati**

    ```text
    STDOUT message(s) from external script: 
    0.5 2
    ```
    
    Durante il recupero **stdout** messaggi è utile quando il test del codice, molto spesso è necessario restituire i risultati in formato tabulare, in modo che sia possibile utilizzarlo in un'applicazione o scriverlo in una tabella. 

Per il momento, tenere presente queste regole:

+ Tutti gli elementi all'interno di `@script` l'argomento deve essere valido codice Python. 
+ Il codice deve seguire tutte le regole Pythonic relativi rientri, i nomi delle variabili e così via. Quando si verifica un errore, controllare le maiuscole e minuscole spazi vuoti.
+ Se si utilizza le eventuali librerie che non vengono caricate per impostazione predefinita, è necessario utilizzare un'istruzione di importazione all'inizio dello script per caricarli. 
+ Se la libreria non è già installata, arrestare e installare il pacchetto di Python all'esterno di SQL Server, come descritto qui: [installare i nuovi pacchetti Python in SQL Server](../python/install-additional-python-packages-on-sql-server.md)

## <a name="inputs-and-outputs"></a>Input e output

Per impostazione predefinita, [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) accetta un singolo input set di dati, in genere è fornire sotto forma di una query SQL valida. Altri tipi di input possono essere passati come variabili SQL: ad esempio, è possibile passare un modello con training come una variabile, utilizzando una funzione di serializzazione, ad esempio [pickle](https://docs.python.org/3.0/library/pickle.html) o [rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) per scrivere il modello un formato binario.

La stored procedure restituisce un singolo Python [pandas](http://pandas.pydata.org/pandas-docs/stable/index.html) frame di dati come output. È tuttavia può restituire valori scalari e i modelli come variabili. È possibile ad esempio, un modello con training come valore binario di output e di passare a un'istruzione T-SQL INSERT, per scrivere tale modello in una tabella. È anche possibile generare grafici (in formato binario) o valori scalari (valori singoli, ad esempio la data e l'ora, il tempo trascorso per il training del modello e così via).

Per Ora esaminiamo solo l'impostazione predefinita le variabili di input e outpue, `InputDataSet` e `OutputDataSet`. 

1. Eseguire il codice seguente per eseguire alcuni calcoli matematici e restituire i risultati.

        ```sql
        execute sp_execute_external_script 
        @language = N'Python', 
        @script = N'
        a = 1
        b = 2
        c = a/b
        print(c)
        OutputDataSet = c
        '
        WITH RESULT SETS ((ResultValue float))
        ```

2. È necessario ottenere un errore, perché il codice Python genera un valore scalare, non un frame di dati.

        **Results**

        ```text
        line 43, in transform
            raise TypeError('OutputDataSet should be of type pandas.DataFrame')
        ```

3. Ora vedere cosa succede quando si passa un set di dati tabulare Python, utilizzando la variabile di input predefinito `InputDataSet`. 

    ```sql
    EXECUTE sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    OutputDataSet = InputDataSet
    ',
    @input_data_1 = N'SELECT 1 as Col1'
    ```

    La stored procedure restituisce un data.frame automaticamente, senza che sia necessario eseguire alcuna operazione aggiuntiva nel codice Python.

    **Risultati**

    | Nessun nome di colonna|
    |------|
    | 1|

    Per impostazione predefinita, il singolo tabulare input set di dati con il nome `InputDataSet`. Tuttavia, è possibile modificare tale nome aggiungendo una riga simile alla seguente: `@input_data_1_name = N'myResultName'`.

    Nomi di colonna usati da Python mai vengono mantenuti nell'output. Anche se la query di input specificato il nome della colonna `Col1`, tale nome non viene restituito, né sarebbe le intestazioni di colonna utilizzate da script Python. Per specificare un tipo di dati e nome di colonna quando viene nuovamente i dati di SQL Server, utilizzare l'istruzione T-SQL `WITH RESULT SETS` clausola.

4. In questo esempio fornisce nuovi nomi per le variabili di input e outpue.

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    MyOutput = MyInput
    ',
    @input_data_1_name = N'MyInput',
    @input_data_1 = N'SELECT 1 as Col1',
    @output_data_1_name = N'MyOutput'
    WITH RESULT SETS ((ResultValue int))
    ```

    La clausola SET di risultati con definisce lo schema per l'output, poiché i nomi delle colonne di Python non vengono mai restituiti con la data.frame.

    **Risultati**

    | ResultValue|
    |------|
    | 1|

5. Ora esaminiamo un tipico errore Python. Modificare la riga dell'esempio precedente da `@input_data_1_name = N'MyInput'` a `@input_data_1_name = N'myinput'`.

    Errori di Python vengono passati all'utente come messaggi, per il servizio satellite utilizzato da SQL Server. I messaggi possono richiedere tempi lunghi e può includere errori di SQL Server o finestra di avvio a errori di Python, pertanto è necessario paziente informazioni dettagliate che attraverso il testo. Il messaggio chiave è in questa riga:

    ```text
    MyOutput = MyInput
    NameError: name 'MyInput' is not defined
    ```

    Tenere presente che Python, ad esempio R, sia tra maiuscole e minuscole. Pertanto, quando si otterrà qualsiasi tipo di errore, assicurarsi di controllare i nomi delle variabili e cercare i problemi con spaziatura, rientri e tipi di dati.

## <a name="python-data-structures"></a>Strutture di dati di Python

SQL Server si basa su Python **pandas** pacchetto, è molto utile per l'utilizzo di dati tabulari. Tuttavia, abbiamo già visto che non è possibile passare un valore scalare da Python a SQL Server e si aspettano che "funzioni". In questa sezione verrà esaminato alcune definizioni di tipo di dati di base, preparazione per altri problemi che è possibile eseguire in quando si passano dati tabulari tra Python e SQL Server.

+ Un frame di dati è una tabella con _più_ colonne.
+ Una singola colonna di un frame di dati, è un oggetto elenco chiamato una serie.
+ Un singolo valore è una cella di un frame di dati e deve essere chiamato in base all'indice.

In che modo si espone il singolo risultato di un calcolo come frame di dati, se un data.frame richiede una struttura tabulare? Una risposta è per rappresentare il valore scalare singolo come una serie, che viene facilmente convertita in un frame di dati. 

1. In questo esempio esegue alcune semplici operazioni matematiche e converte un valore scalare in una serie. Una serie richiede un indice, che è possibile assegnare manualmente, come illustrato di seguito, o a livello di codice.

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    a = 1
    b = 2
    c = a/b
    print(c)
    s = pandas.Series(c, index =["simple math example 1"])
    print(s)
    '
    ```

2. Poiché la serie non è stata convertita in un data.frame, vengono restituiti i valori nella finestra di messaggi, ma è possibile vedere che i risultati sono in formato tabulare più.

    **Risultati**

    ```text
    STDOUT message(s) from external script: 
    0.5
    simple math example 1    0.5
    dtype: float64
    ```

3. Per aumentare la lunghezza della serie, è possibile aggiungere nuovi valori, utilizzando una matrice. 

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    a = 1
    b = 2
    c = a/b
    d = a*b
    s = pandas.Series([c,d])
    print(s)
    '
    ```

    Se non si specifica un indice, viene generato un indice che dispone di valori a partire da 0 e terminando con la lunghezza della matrice.

    **Risultati**

    ```text
    STDOUT message(s) from external script: 
    0    0.5
    1    2.0
    dtype: float64
    ```

4. Se si aumenta il numero di **indice** valori, ma non aggiungere nuovi **dati** valori, i valori dei dati vengono ripetuti per riempire la serie.

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    a = 1
    b = 2
    c = a/b
    s = pandas.Series(c, index =["simple math example 1", "simple math example 2"])
    print(s)
    '
    ```

    **Risultati**

    ```text
    STDOUT message(s) from external script: 
    0.5
    simple math example 1    0.5
    simple math example 2    0.5
    dtype: float64
    ```

### <a name="convert-series-to-data-frame"></a>Convertire una serie di frame di dati

Con convertire i risultati di matematica scalare in una struttura tabulare, è comunque necessario convertirli in un formato che può gestire SQL Server. 

1. Per convertire una serie in un data.frame, chiamare il pandas [DataFrame](http://pandas.pydata.org/pandas-docs/stable/dsintro.html#dataframe) metodo.

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    import pandas as pd
    a = 1
    b = 2
    c = a/b
    d = a*b
    s = pandas.Series([c,d])
    print(s)
    df = pd.DataFrame(s)
    OutputDataSet = df
    '
    WITH RESULT SETS (( ResultValue float ))
    ```

2. Si noti che i valori di indice non sono output, anche se si utilizza l'indice per ottenere i valori specifici dal data.frame.

    **Risultati**

    |ResultValue|
    |------|
    |0,5|
    |2|

### <a name="output-values-into-dataframe-using-an-index"></a>Valori di output in data.frame tramite un indice

Di seguito viene illustrato il funzionamento di conversione in un data.frame con due serie che contiene i risultati di operazioni matematiche semplici. Il primo ha un indice dei valori sequenziali generati da Python. La seconda Usa un indice arbitrario di valori stringa.

1. In questo esempio Ottiene un valore di serie che utilizza un indice intero.

    ```sql
    EXECUTE sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    import pandas as pd
    a = 1
    b = 2
    c = a/b
    d = a*b
    s = pandas.Series([c,d])
    print(s)
    df = pd.DataFrame(s, index=[1])
    OutputDataSet = df
    '
    WITH RESULT SETS (( ResultValue float ))
    ```

    Tenere presente che l'indice generato automaticamente inizia in corrispondenza di 0. Provare a utilizzare un timeout del valore di indice di intervallo e verificare il risultato.

2. Ora consente di ottenere un valore singolo da altri frame di dati che dispone di un indice stringa. 

    ```sql
    EXECUTE sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    import pandas as pd
    a = 1
    b = 2
    c = a/b
    s = pandas.Series(c, index =["simple math example 1", "simple math example 2"])
    print(s)
    df = pd.DataFrame(s, index=["simple math example 1"])
    OutputDataSet = df
    '
    WITH RESULT SETS (( ResultValue float ))
    ```

    **Risultati**

    |ResultValue|
    |------|
    |0,5|

    Se si tenta di utilizzare un indice numerico per ottenere un valore di questa serie, viene visualizzato un errore.

Questo esercizio è stato progettato per dare un'idea di come usare diverse strutture di dati di Python e assicurarsi di ottenere il risultato corretto come frame di dati. Potrebbe aver concluso che l'output un singolo valore come un frame di dati è più complicata rispetto al relativo valore. Fortunatamente, è possibile passare facilmente tutti i tipi di valori da e verso la stored procedure come variabili. Che è trattata nella lezione successiva.

## <a name="tips"></a>Suggerimenti

+ Tra i linguaggi di programmazione Python è uno dei più flessibile per quanto riguarda le virgolette singole e virgolette doppie. si tratta piuttosto intercambiabili. 

    Tuttavia, T-SQL vengono utilizzate le virgolette per solo alcuni aspetti e `@script` argomento vengono utilizzate le virgolette per racchiudere il codice Python come stringa Unicode. Di conseguenza, potrebbe essere necessario esaminare il codice Python e modificare alcune virgolette le virgolette doppie.

+ Impossibile trovare la stored procedure, `sp_execute_external_script`? Significa che probabile che non è stata completata la configurazione di istanza per supportare l'esecuzione dello script esterno. Dopo l'installazione di SQL Server 2017 e selezionando Python come di machine learning language, è necessario abilitare anche in modo esplicito la funzionalità mediante `sp_configure`e quindi riavviare l'istanza. 

    Per informazioni dettagliate, vedere [installare SQL Server 2017 Machine Learning Services (In-Database)](../install/sql-machine-learning-services-windows-install.md).

## <a name="next-steps"></a>Passaggi successivi

[Eseguire il wrapping di codice Python in una stored procedure SQL](wrap-python-in-tsql-stored-procedure.md)