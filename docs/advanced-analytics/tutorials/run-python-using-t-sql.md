---
title: Eseguire Python con T-SQL in SQL Server | Microsoft Docs
description: Informazioni di base per l'esecuzione di codice Python con T-SQL e stored procedure in un'istanza di motore di database di SQL Server per cui è abilitata l'integrazione di Python.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: e22b280c4fea395f8c7cf7c4b559d5ff5a22d6c1
ms.sourcegitcommit: 3cd6068f3baf434a4a8074ba67223899e77a690b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2018
ms.locfileid: "49461917"
---
# <a name="run-python-using-t-sql"></a>Eseguire Python con T-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo illustra come è possibile eseguire il codice Python in SQL Server 2017. Vengono illustrate le nozioni di base dello spostamento dei dati tra SQL Server e Python: requisiti, le strutture di dati, gli input e output. Viene inoltre spiegato come eseguire il wrapping di codice Python in formato corretto in una stored procedure [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) per compilare, eseguire il training e usare modelli di machine learning in SQL Server.

## <a name="prerequisites"></a>Prerequisiti

Per eseguire l'esempio di codice in questi esercizi, è innanzitutto necessario installare SQL Server 2017 e abilitare Servizi di Machine Learning nell'istanza, come descritto in [installare SQL Server 2017 Machine Learning Services (In-Database)](../install/sql-machine-learning-services-windows-install.md). 

È consigliabile installare anche [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms). In alternativa, è possibile utilizzare un'altra query o gestione strumento di database, purché possa connettersi a un server e database ed eseguire una query T-SQL o una stored procedure.

Quando l'ambiente è pronto, tornare a questa pagina per informazioni su come eseguire codice Python nel contesto di una stored procedure. 

## <a name="verify-python-exists"></a>Verificare il che esistenza di Python

La procedura seguente conferma che Python sia abilitato e il servizio Launchpad di SQL Server è in esecuzione.

1. Controllare se l'integrazione di Python è installato nell'istanza del motore di database. È possibile trovarne **python.exe** in una cartella denominata **PYTHON_SERVICES** in C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\. Si tratta dell'eseguibile Python che SQL Server usa per eseguire il codice Python.

2. Controllare se è abilitata la creazione di script esterni. In Management Studio, eseguire l'istruzione seguente:

    ```sql
    sp_configure 'external scripts enabled'
    ```

    Se **run_value** è 1, la funzionalità di machine learning viene installata e pronta all'uso.

    Una causa comune degli errori è che il [Launchpad di SQL Server service](../concepts/extensibility-framework.md#launchpad), che gestisce la comunicazione tra Server SQL e Python, è stato arrestato. È possibile visualizzare lo stato della finestra di avvio utilizzando il Windows **Services** pannello oppure aprendo Gestione configurazione SQL Server. Se il servizio è arrestato, riavviarlo.

3. Verificare che il runtime di Python funziona e comunica con SQL Server. A tale scopo, aprire una nuova **Query** finestra in SQL Server Management Studio e connettersi all'istanza in cui è stato installato Python.

    ```sql
    EXEC sp_execute_external_script @language = N'Python', 
    @script = N'print(3+4)'
    ```

    Se tutto funziona correttamente, verrà visualizzato un messaggio di risultato simile alla seguente

    ```text
    STDOUT message(s) from external script: 
    7
    ```

3. Se si verificano errori, sono disponibili un'ampia gamma di operazioni che è possibile eseguire per assicurarsi che il server e Python possono comunicare. 

    È necessario aggiungere il gruppo di utenti Windows `SQLRUserGroup` come account di accesso nell'istanza, per assicurarsi che Launchpad può fornire la comunicazione tra codice Python e SQL Server. (Lo stesso gruppo viene usato per entrambi R e l'esecuzione di codice Python). Per altre informazioni, vedere [abilitato l'autenticazione implicita](../security/add-sqlrusergroup-to-database.md).
    
    Inoltre, è necessario abilitare i protocolli di rete che sono stati disabilitati o aprire il firewall in modo che SQL Server può comunicare con client esterni. Per altre informazioni, vedere [risoluzione dei problemi di installazione](../common-issues-external-script-execution.md).

## <a name="basic-python-interaction"></a>Interazione di Python di base

Esistono due modi per eseguire il codice Python in SQL Server:

+ Aggiungere uno script di Python come argomento delle stored procedure di sistema [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

+ Da un [client Python remoto](../python/setup-python-client-tools-sql.md), connettersi a SQL Server ed eseguire codice che Usa SQL Server come contesto di calcolo. Questa operazione richiede [revoscalepy](../python/what-is-revoscalepy.md).

L'esercizio seguente è incentrata sul modello di interazione prima: come passare il codice Python a una stored procedure.

1. Eseguire codice semplice per vedere come i dati vengono passati avanti e indietro tra SQL Server e Python.

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

2. Supponendo che si dispone di tutto è configurato correttamente e Python e SQL Server comunichino tra loro, viene calcolato il risultato corretto e di Python `print` funzione restituisce il risultato per il **messaggi** windows.

    **Risultati**

    ```text
    STDOUT message(s) from external script: 
    0.5 2
    ```
    
    Durante il recupero **stdout** messaggi risulta utile quando il test del codice, più spesso è necessario restituire i risultati in formato tabulare, in modo che è possibile usarlo in un'applicazione o scriverlo in una tabella. 

Per il momento, tenere presenti queste regole:

+ Tutti gli elementi all'interno di `@script` argomento deve essere il codice Python valido. 
+ Il codice deve seguire tutte le regole Python riguardanti il rientro, i nomi delle variabili e così via. Quando si verifica un errore, verificare di spazi vuoti e maiuscole e minuscole.
+ Se si usa le eventuali librerie che non vengono caricate per impostazione predefinita, è necessario utilizzare un'istruzione import all'inizio dello script per caricarli. SQL Server aggiunge diverse librerie specifici del prodotto. Per altre informazioni, vedere [librerie Python](../python/python-libraries-and-data-types.md).
+ Se la libreria non è già installata, interrompere e installare il pacchetto di Python all'esterno di SQL Server, come descritto qui: [installare nuovi pacchetti di Python in SQL Server](../python/install-additional-python-packages-on-sql-server.md)

## <a name="inputs-and-outputs"></a>Input e output

Per impostazione predefinita [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) accetta un singolo set di dati input, che in genere è fornire sotto forma di una query SQL valida. 

Altri tipi di input possono essere passati come variabili SQL: ad esempio, è possibile passare un modello con training come una variabile, usando una funzione di serializzazione, ad esempio [pickle](https://docs.python.org/3.0/library/pickle.html) oppure [rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) per scrivere il modello un formato binario.

La stored procedure restituisce un singolo Python [pandas](http://pandas.pydata.org/pandas-docs/stable/index.html) frame di dati come output, ma è anche possibile restituire valori scalari e i modelli come variabili. Ad esempio, è possibile restituire un modello con training come una variabile binaria e che passare a un'istruzione T-SQL INSERT, per scrivere tale modello in una tabella. È anche possibile generare grafici (in formato binario) o valori scalari (valori singoli, ad esempio la data e ora, il tempo trascorso per il training del modello e così via).

Per ora, esaminiamo l'impostazione predefinita le variabili di input e outpue di sp_execute_external_script: `InputDataSet` e `OutputDataSet`. 

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

2. Viene visualizzato un errore, perché il codice Python genera un valore scalare, non un frame di dati.

    **Risultati**

    ```text
    line 43, in transform
        raise TypeError('OutputDataSet should be of type pandas.DataFrame')
    ```

3. Ora che cosa accade quando si passa un set di dati tabulare per Python, usando la variabile di input predefinito `InputDataSet`. 

    ```sql
    EXECUTE sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    OutputDataSet = InputDataSet
    ',
    @input_data_1 = N'SELECT 1 as Col1'
    ```

    La stored procedure restituisce un frame di dati automaticamente, senza dover eseguire alcuna operazione aggiuntiva nel codice Python.

    **Risultati**

    | Nessun columnname|
    |------|
    | 1|

    Per impostazione predefinita, l'unico input set di dati tabulare con il nome, `InputDataSet`. Tuttavia, è possibile modificare questo nome mediante l'aggiunta di una riga simile alla seguente: `@input_data_1_name = N'myResultName'`.

    Nomi di colonna usati Python mai vengono mantenuti nell'output. Anche se la query di input specificato il nome della colonna `Col1`, tale nome non viene restituito, né sarebbe eventuali intestazioni di colonna usate dallo script Python. Per specificare un colonna nome e tipo di dati quando si restituiscono i dati a SQL Server, usare l'istruzione T-SQL `WITH RESULT SETS` clausola.

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

    La clausola SET di risultati con definisce lo schema per l'output, poiché i nomi delle colonne di Python non vengono mai restituiti con il frame di dati.

    **Risultati**

    | ResultValue|
    |------|
    | 1|

5. Ora esaminiamo un tipico errore Python. Modificare la riga dell'esempio precedente dalla `@input_data_1_name = N'MyInput'` a `@input_data_1_name = N'myinput'`.

    Errori di Python vengono passati all'utente sotto forma di messaggi, per il servizio satellite usato da SQL Server. I messaggi possono essere lunghi e includono errori di SQL Server o di Launchpad oltre a errori di Python, pertanto è necessario paziente in esplorare il funzionamento interno del testo. Il messaggio chiave è in questa riga:

    ```text
    MyOutput = MyInput
    NameError: name 'MyInput' is not defined
    ```

    È importante ricordare che Python, ad esempio R, sia tra maiuscole e minuscole. Pertanto, quando si riceve alcun tipo di errore, assicurarsi di controllare i nomi delle variabili e per individuare i problemi con rientro, spaziatura e tipi di dati.

## <a name="python-data-structures"></a>Strutture di dati Python

SQL Server si basa su Python **pandas** pacchetto, che è ideale per l'utilizzo di dati tabulari. Tuttavia, abbiamo già visto che non è possibile passare un valore scalare da Python a SQL Server e aspettarsi che "funzionano". In questa sezione verranno esaminate alcune definizioni dei tipi di dati di base, per prepararti per altri problemi che possono verificarsi quando si passano dati tabulari tra codice Python e SQL Server.

+ Un frame di dati è una tabella con _più_ colonne.
+ Una singola colonna di un frame di dati, è un oggetto di tipo elenco denominato una serie.
+ Un singolo valore è una cella di un frame di dati e deve essere chiamata in base all'indice.

In che modo si esporrà il singolo risultato di un calcolo come frame di dati, se un frame di dati richiede una struttura tabulare? Una risposta è per rappresentare il valore scalare singolo come una serie, che viene facilmente convertita in un frame di dati. 

1. In questo esempio esegue alcuni calcoli matematici semplici e converte un valore scalare in una serie. Una serie richiede un indice, che è possibile assegnare manualmente, come illustrato di seguito, o a livello di codice.

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

2. Poiché la serie non è stata convertita in un frame di dati, vengono restituiti i valori nella finestra dei messaggi, ma è possibile notare che i risultati sono in formato tabulare più.

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

    Se non si specifica un indice, viene generato un indice che dispone di valori a partire da 0 e termina con la lunghezza della matrice.

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

### <a name="convert-series-to-data-frame"></a>Convertire serie in frame di dati

Visto convertito risultati matematici scalari in una struttura tabulare, è comunque necessario convertirli in un formato che può gestire SQL Server. 

1. Per convertire una serie in un frame di dati, chiamare il pandas [DataFrame](http://pandas.pydata.org/pandas-docs/stable/dsintro.html#dataframe) (metodo).

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

2. Si noti che i valori di indice non generate, anche se si usa l'indice per ottenere valori specifici dal frame di dati.

    **Risultati**

    |ResultValue|
    |------|
    |0,5|
    |2|

### <a name="output-values-into-dataframe-using-an-index"></a>Valori di output in frame di dati usando un indice

Di seguito viene illustrato come la conversione in un frame di dati funziona con due serie che contiene i risultati delle operazioni matematiche semplici. Il primo ha un indice di valori sequenziali generati da Python. Il secondo Usa un indice di valori di stringa arbitrario.

1. In questo esempio Ottiene un valore dalla serie che utilizza un indice integer.

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

    Tenere presente che l'indice generato automaticamente inizia da 0. Provare a usare un valore di indice di intervallo fuori e vedere cosa succede.

2. A questo punto è possibile ottenere un singolo valore da altri frame di dati che include un indice stringa. 

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

    Se si prova a usare un indice numerico per ottenere un valore di questa serie, viene visualizzato un errore.

Questo esercizio è stato progettato per dare un'idea di come lavorare con diverse strutture di dati di Python e assicurarsi di che ottenere il risultato corretto come frame di dati. Si potrebbe aver concluso che l'output un singolo valore come un frame di dati è più complicata rispetto a vale! Fortunatamente, è possibile passare facilmente tutti i tipi di valori da e verso la stored procedure come variabili. Questa procedura è descritta nella lezione successiva.

## <a name="tips"></a>Suggerimenti

+ Tra i linguaggi di programmazione Python è uno dei più flessibile per quanto riguarda le virgolette singole e virgolette doppie. si tratta sostanzialmente intercambiabili. 

    Tuttavia, T-SQL vengono utilizzate le virgolette solo determinati aspetti e il `@script` argomento vengono utilizzate le virgolette per racchiudere il codice Python come una stringa Unicode. Pertanto, si potrebbe essere necessario esaminare il codice Python e cambiare alcuni tra virgolette singole in virgolette doppie.

+ Impossibile trovare la stored procedure, `sp_execute_external_script`? Significa che probabilmente non è stata completata la configurazione di istanza per supportare l'esecuzione dello script esterno. Dopo aver eseguito il programma di installazione di SQL Server 2017 e selezione di Python come il linguaggio di machine learning, è necessario abilitare in modo esplicito la funzionalità tramite `sp_configure`e quindi riavviare l'istanza. 

    Per informazioni dettagliate, vedere [installare SQL Server 2017 Machine Learning Services (In-Database)](../install/sql-machine-learning-services-windows-install.md).

## <a name="next-steps"></a>Passaggi successivi

[Configurare il set di dati Iris demo](demo-data-iris-in-sql.md)